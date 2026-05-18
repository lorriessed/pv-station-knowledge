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
