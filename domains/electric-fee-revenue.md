# domains/electric-fee-revenue

更新时间: 2026-05-18

## 电费收益（非户用工商业）菜单

**菜单定位**: 非户用（工商业/分布式）光伏项目的电费订单管理、发票处理、SAP 记账全流程。

**代码来源**: `rrsjk-admin-web` → `LightProjectElectricOrderController.java` + `rrsjk-light-service` → `LightProjectElectricOrderServiceImpl.java`

---

### 核心数据表

| 表名 | 说明 | 数据库 |
|---|---|---|
| `light_project_electric_order` | 电费收益主表 | rrsjk_light |

**注意：此表实际数据构成（2026-05-18 数据库实测 135万条）**：
| project_type | 含义 | 占比 |
|---|---|---|
| YL（银联模式/公司备案） | 电站可能建在个人屋顶，但由公司统一备案结算，电网打款到项目公司账户 | ~99.3% |
| PUB_BUILD（公共租赁） | 公司投资的公共建筑项目 | ~0.6% |
| MIX（混合模式） | 多种电站共用一个发电户号 | 极少 |
| WHOLE_VILLAGE（整村推进） | 整村推进项目 | 极少 |
| CM（工商业） | 纯工商业项目 | 仅54条，几乎可以忽略 |

**旧知识库标注"非户用"不够准确**——YL 模式本质是公司代持的户用电站，工商业反而是边角料。
| `light_project_electric_order_owner` | 分账明细表 | rrsjk_light |
| `light_project_electric_order_temporarily` | 临时表 | rrsjk_light |
| `light_project_electric_order_change` | 变更记录表 | rrsjk_light |
| `light_project_electric_invoice_reverse_record` | 发票冲销记录表 | rrsjk_light |

---

### 完整业务流程

```
1. 数据导入/生成 → 状态 WAIT_CONFIRM（待确认）
   ↓
2. 业务上传影像/确认 → 状态 WAIT（待审核）
   ↓
3. 财务审核确认(confirm) → 状态 CONFIRMED（已审核）
   ├── 如果 invoiceStatus=WAIT + 系统开具 → 自动创建发票 → PUSH
   └── 如果 incomeStatus=NO + 金额>0 → 调用 confirmIncomeToSap → SAP 收入记账
   ↓
4. 收款确认(confirmPaid) → confirmPaymentStatus: UNCONFIRMED → CONFIRM
   └── 调用 SAP 收款记账模型，记录 accountVoucher
```

---

### 状态枚举

**订单状态 (Status):**
- `WAIT_CONFIRM` → 待确认（业务侧）
- `WAIT` → 待审核（财务侧）
- `CONFIRMED` → 已审核
- `REJECTED` → 业务驳回
- `DELETED` → 已删除

**发票状态 (InvoiceStatus):**
- `WAIT` → 待传发票
- `PUSH` → 已传发票
- `SUCCESS` → 已开票
- `WAIT_INVALID` → 待作废
- `INVALID` → 已作废

**SAP 记账状态 (SapStatus) - 收入/收款共用:**
- `NO` → 未对账
- `SAPING` → 对账中
- `YES` → 已对账
- `REVERSE` → 已冲销
- `WAIT_REVERSE` → 待冲销
- `WAIT_REVERSE_AND_SAP` → 待冲销和记账

**收款确认状态 (ConfirmPaymentStatus):**
- `UNCONFIRMED` → 未确认
- `CONFIRM` → 已确认

---

### 核心业务逻辑

#### 1. 审核确认 (confirm)
**入口**: `POST /lightProjectElectricOrder/confirm.do`
**权限**: `lightProjectElectricOrder:write:confirm`

**前置校验**:
- 状态必须是 `WAIT`
- 越秀电费（stationType=YX/HR 且 specialFlag=YX）不允许此操作
- 资方公司下的项目公司不允许此操作

**处理逻辑**:
1. 如果是"待传发票 + 系统开具"，自动创建发票并推送，更新 invoiceStatus→PUSH
2. 如果收入未确认（incomeStatus=NO）且金额>0，调用 `confirmIncomeToSap` 进行 SAP 记账
3. 更新状态→CONFIRMED，记录 auditBy/auditAt/auditIp

#### 2. SAP 收入记账 (confirmIncomeToSap)
**入口**: `POST /lightProjectElectricOrder/confirmIncomeToSap.do`

**公司类型判断**:

| 类型 | 判断条件 | SAP 处理 |
|---|---|---|
| 普通项目公司 | `stockTransfer != 1` | `projectElectricOrderSapModel.incomeToSap()` |
| 股转公司-乐道/统众 | `stockTransfer == 1` + `lightCapitalCompanyInfo != null` | **不传 SAP**，只改状态为 WAIT_SAP |
| 股转公司-其他 | `stockTransfer == 1` + `lightCapitalCompanyInfo == null` | `incomeToJinDieSap()` 传金蝶 SAP |

**成功后**: 更新 `incomeStatus=YES`，记录 `incomeVoucher`（SAP 凭证号）、`incomeAt`

#### 3. 收款确认 (confirmPaid)
**入口**: `POST /lightProjectElectricOrder/confirmPaid.do`

**逻辑**:
- 校验收款状态必须是 `UNCONFIRMED`
- 查询收款账户信息（`LightProjectCompanyAccount`）
- 调用 SAP 收款记账
- 更新 `confirmPaymentStatus=CONFIRM`，记录收款凭证号

#### 4. 发票冲销
发电户号变更时需要先冲销原凭证，再重新记账。状态流转：`WAIT_REVERSE_AND_SAP` → 冲销 → 重新记账。

---

### 关键字段

| 字段 | 说明 |
|---|---|
| `order_no` | 订单号（唯一标识） |
| `batch_no` | 批次号（一批订单共享） |
| `invoice_no` | 开票序号 |
| `elec_no` | 发电户号 |
| `amount` | 电费金额 |
| `tax_amount` | 税额 |
| `rent_amount` | 租金金额（成本侧） |
| `start_month` | 电费所属开始月份 |
| `month_at` | 电费所属月份 |
| `project_company_code` | 项目公司编码 |
| `customer_code` | 电网客户编码 |
| `income_voucher` | 收入 SAP 凭证号 |
| `account_voucher` | 收款 SAP 凭证号 |
| `invoice_template_code` | 发票模板编码 |
| `re_send_count` | 换开次数（换开发票标识 RE{count}） |

---

### 服务调用链

```
rrsjk-admin-web (Controller)
    ↓
rrsjk-light-service (Dubbo Service)
    ↓
├─ LightProjectElectricOrderService (订单管理)
├─ ProjectElectricOrderSapModel (SAP 记账模型)
├─ InvoiceService (发票服务)
├─ MdmCustomerService (MDM 客户信息)
└─ SyncFinanceToSapService (财务同步 SAP)
```

**导出逻辑** (2026-05-07 重构):
- 导出接口已切换到 `report-service` ODS 数据源
- 增加导出限制（@LimitationExport）
- 线程池优化（16 线程，每页 1000 条，CSV 最大 50 万行）
- 保留原有 light-service 用于其他 CRUD 操作

---

### 电费收益导入月份区间校验优化 (代码明确证明, 2026-05-19)
**来源**: `rrsjk-admin-web` → `LightProjectElectricOrderController.java` (commit d9158c52, 龙龙, 2026-05-18)
**需求**: TAEI-3079 【电费】电费收益相关优化

- **重构**: 移除控制器中导入数据月份重复校验逻辑，改用数据库批量查询验证
- **新增**: `listByElecNoAndMonthRange()` 方法支持月份区间数据查询
- **废弃**: 旧的按月份查询方法标记为 `@Deprecated`，统一使用区间查询
- **优化**: 
  - 工商业电站ID查询逻辑简化
  - 临时数据查询方法从单月改为区间查询
  - 多个业务流程中的查询方法调用适配
  - 服务层参数格式化和注释文档更新
- **性能提升**: 从N次单月查询 → 1次批量区间查询

### 发电户号电费模板映射 (代码明确证明, 2026-05-20)
**来源**: `rrsjk-light-service` → LightStationElecTemplateMapping.java, LightStationElecTemplateMappingService/Impl, LightStationElecTemplateMappingDao, LightStationElecTemplateMapping.xml (commits f24108f/2194b02/b322dc4/e5429ef/3769fb3, lilong, 2026-05-20, branch: 20260519-alone-electricAI)
**关联需求**: 发电户号电费模板映射
- **实体**: `LightStationElecTemplateMapping` — 映射表 `light_station_elec_template_mapping`
  - 用途: 建立发电户号(elec_no)与电费模板之间的映射关系
- **服务**: `LightStationElecTemplateMappingService` — 增删改查 + 批量操作
  - `LightStationElecTemplateMappingBatchDeleteCommand`: 批量删除命令
  - `LightStationElecTemplateMappingDto`: 数据传输对象
- **接口**: 新增根据发电户号批量查询电站信息接口
- **前端**: `rrsjk-admin-web` → lilong commits 添加基础服务代码和接口
- **Dao**: `LightStationElecTemplateMappingDao` + Mapper XML
- **证据等级**: 代码明确证明

### 工商业自持电站损益报表 (代码明确证明, 2026-05-14~19)
**来源**: `rrsjk-admin-web` → `CmOwnerStationReportController.java`, `CmOwnerStationReportExcel.java`, `cmOwnerStationReportList.ftl` (commits a9393c1/198c335/5acd5c6, tn_wangb, 2026-05-14~19, branch: 20260506-wb-cmOwnerStationReport)
- **报表功能**: 新增工商业自持电站损益报表，包含列表展示和导出功能
- **字段**: 报表包含收入、成本、利润等损益相关字段
- **列表页**: `cmOwnerStationReportList.ftl` 重构（393行变更）
- **导出**: `CmOwnerStationReportExcel.java` 定义导出格式
- **关联**: 与 TAEI-3025 BT报表项目可能有重叠（同一批开发人员）
- **证据等级**: 代码明确证明

### 电费发票列表查询增强 (2026-05-29~06-04)
**来源**: `rrsjk-admin-web` → `LightCapitalProjectElectricOrderInvoiceController.java` / `LightProjectElectricOrderController.java` (commits by laowang, 2026-05-29~06-03)
**证据等级**: 代码明确证明

- **LightCapitalProjectElectricOrderInvoiceController** 新增查询条件:
  - `invoiceStatus` — 发票状态筛选
  - `purchaserName` — 购销方名称筛选
  - `companyName` — 公司名称筛选
- **多列表新增资方(capital)筛选**:
  - `LightProjectElectricInvoiceReverseRecordController` — 发票冲销记录
  - `LightProjectRentController` / `LightProjectRentRecordController` — 租金/租金记录
  - `LightWvRentController` / `LightWvRentRecordController` — 瓦沃租金
- **业务影响**: 财务/租金列表支持按资方维度过滤，满足多资方场景下的数据隔离需求

### 电费发票冲销查询方法变更 (2026-06-05)
**来源**: `rrsjk-admin-web` → `LightProjectElectricInvoiceReverseRecordController.java` (commit by laowang, 2026-06-05)
**证据等级**: 代码明确证明

- `LightCapitalCompanyInfoService.findProjectCompanyCodesByCapital(capital)` → `findProjectCompanyNamesByCapital(capital)`
- 列表查询和导出均从按"项目公司编码"改为按"项目名称"过滤
- 可能是资方筛选逻辑优化，更适配用户界面的名称展示

### 原材料财务审核 FAP 校验变更 (2026-06-05)
**来源**: `rrsjk-admin-web` → `LightSpOrderFinanceController.java` / `lightSpOrderFinanceList.ftl` (commit by 代继宁, 2026-06-05)
**证据等级**: 代码明确证明

- 原材料订单确认收款校验从 `PayTypeEnum.TRANSFER` 判断改为 `fapStatus` 非空判断
- 旧逻辑: 转账汇款订单提示"FAP自动处理，无需确认收款"
- 新逻辑: `fapStatus` 非空则提示"FAP处理，无需手动确认"
- 前端模板同步修改回购确认收款按钮权限
- 反映 FAP 自动化流程持续推进，从单一支付方式覆盖到更广泛的订单状态

### FAP 作废状态枚举变更 (2026-06-05)
**来源**: `rrsjk-light-service` → `LightProjectElectricOrderServiceImpl.java` (commit e6de280, tn_wangb/龙龙, 2026-06-05)
**证据等级**: 代码明确证明
**关联需求**: TAEI-3079 电费收益相关优化

- **枚举值变更**:
  - `FapStatusEnum.WAIT_SENT_OLD` → `FapStatusEnum.SENT_OLD` (旧集团FAP已发送)
  - `FapStatusEnum.WAIT_SENT` → `FapStatusEnum.SENT` (新FAP已发送)
- **影响**: 电费收益作废流程中，判断条件从 `WAIT_SENT_OLD`/`WAIT_SENT` 改为 `SENT_OLD`/`SENT`
- **业务意义**: FAP 状态语义从"待发送"改为"已发送"，更准确反映实际状态

### 电费发票批量异步导入 (TAEI-3266, 2026-07-01)
**来源**: `rrsjk-admin-web` → `LightCapitalProjectElectricOrderInvoiceController.java` (代继宁, commits c055f98~0a20c7f, 2026-06-25~07-01)
**证据等级**: 代码明确证明

新增 4 个接口支持电费发票 Excel 批量异步导入:
- `POST /lightProjectElectricOrderInvoice/downloadImportTemplate.do` — 下载导入模板 (EasyExcel)
- `POST /lightProjectElectricOrderInvoice/importInvoiceAsync.do` — 异步导入发票 (MultipartFile → InvoiceImportDTO)
- `GET /lightProjectElectricOrderInvoice/getImportProgress.do` — 查询导入进度 (ImportProgressDTO)
- `GET /lightProjectElectricOrderInvoice/getImportFailList.do` — 查询导入失败列表 (分页, ImportFailDTO)

模板 DTO: `LightInvoiceImportTemplateDTO` — 字段: batchNo, relationNo, invoiceNumber, invoiceAt, fileUrl
Service: `LightProjectElectricOrderInvoiceService.importInvoiceAsync()` / `getImportProgress()` / `getImportFailList()`
前端: `lightCapitalProjectElectricOrderInvoiceList.ftl` (+400行交互)

### 电费收益筛选增强 — 确认收款时间 (TAEI-3194, 2026-07-01)
**来源**: `rrsjk-admin-web` → `LightProjectElectricOrderController.java`, `LightProjectElectricOrderStationController.java` (lilong, commits b393392~43a395a, 2026-06-22~06-23)
**证据等级**: 代码明确证明

- 电费收益列表和电站维度列表新增 `accountAtStart`/`accountAtEnd` 筛选条件（确认收款时间范围）
- `fillOutParams()` 方法新增两个参数，映射到 SQL `accountAtStart`/`accountAtEnd`
- 电站维度调整分中心权限查询逻辑
- 新增"重置筛选条件"按钮
- Excel 导出新增确认收款时间列 (`LightProjectElectricOrderStationExcel.java` +3行)

### AI 对账日期解析容错 (TAEI-3110, 2026-07-01)
**来源**: `rrsjk-admin-web` → `AiReconciliationHandler.java` (lilong, commit ecedaac, 2026-07-01)
**证据等级**: 代码明确证明

- 旧逻辑: AI 识别日期格式错误时抛出 `BusinessException("对账单日期识别失败")` 阻断整个对账流程
- 新逻辑: 日期解析出错不阻断，startDate/endDate 变量提到 try 外部，解析失败后日期字段留空继续展示
- 产品经理明确要求: 日期识别失败不应影响整体对账流程
- 税额自动计算规则不变: 含税价 ÷ 1.13 × 0.13

