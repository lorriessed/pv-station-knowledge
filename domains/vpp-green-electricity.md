# VPP 绿电收益管理

最后更新: 2026-05-14

## 1. 服务概述

**来源**: `vpp-api-gpower` (全量通读 ✅ 2026-05-14)

绿电收益管理模块，负责绿电交易收益的全生命周期管理，包含收益录入→结算单上传→财务审核→发票管理→SAP记账→收款确认完整流程。

### 1.1 技术栈

- Spring Boot 2.5.5 + JDK 8 + Spring Cloud 2020.0.4
- MyBatis-Plus 3.5.3.1 + Druid 1.2.23
- Nacos 配置中心
- XXL-JOB 定时任务 (发票相关，代码中注释掉了)
- MDM 主数据 SOAP 集成 (TransCustomerInfoXDToMDM, TransSupplierInfoRRSToMDM)
- SAP 财务记账集成

## 2. 核心业务流程

### 2.1 绿电收益状态机 (代码明确证明)

**来源**: `vpp-api-gpower/vpp-gpower-biz/src/main/java/com/nahui/energy/enums/GreenElectricityStatusEnum.java`

```
DRAFT (待提交审核) → PENDING_FINANCE (待财务审核) → APPROVED (已审核)
                                              ↓
                                     FINANCE_REJECTED (财务驳回)
```

- 新增时默认 `DRAFT`
- 上传结算单后状态变为 `PENDING_FINANCE`
- 财务审核通过 → `APPROVED`，驳回 → `FINANCE_REJECTED`

### 2.2 完整业务流程

1. **收益录入**: 手动新增或 Excel 导入绿电收益记录
2. **结算单上传**: 上传结算单附件，触发状态流转至待财务审核
3. **财务审核**: 财务人员进行审核（通过/驳回）
4. **发票管理**: 发票上传（PDF/XML/OFD），状态流转 PENDING → SENT → ISSUED
5. **SAP 记账**: 调用 SAP 接口进行财务记账
6. **收款确认**: 确认收款，更新收款状态 UNPAID → PAID

### 2.3 单号生成规则 (代码明确证明)

**来源**: `vpp-api-gpower/vpp-gpower-biz/src/main/java/com/nahui/energy/controller/GreenElectricityRevenueController.java`

格式: `DL + yyMMddHHmmss` (如 `DL260514103045`)

## 3. 数据库表 (代码明确证明)

**来源**: `vpp-api-gpower/vpp-gpower-biz/src/main/java/com/nahui/energy/pojo/Do/`

| 表名 | DO类 | 说明 |
|---|---|---|
| `green_electricity_revenue` | GreenElectricityRevenueDO | 绿电收益主表 |
| `green_electricity_audit_log` | GreenElectricityAuditLogDO | 绿电收益审核日志表 |
| `power_grid_company` | PowerGridCompanyDO | 电网公司主数据表 |
| `power_grid_contract` | PowerGridContractDO | 电网公司合同表 |
| `sap_record` | SapRecordDO | SAP财务记账记录表 |
| `sap_item_record` | SapItemRecordDO | SAP财务记账子记录表 |

### 3.1 green_electricity_revenue 核心字段

| 字段 | 说明 |
|---|---|
| order_no | 单号 (DL+时间戳) |
| batch_no | 批次号 |
| invoice_no | 开票序号 |
| invoice_number | 发票号 |
| power_company_id | 电网公司ID |
| power_company_code | 电网客户码 |
| power_company_name | 电网公司名称 |
| project_company_code | 项目公司代码 |
| project_company_name | 项目公司名称 |
| month | 月份 (2025-07格式) |
| amount | 金额(元) |
| tax_amount | 税额(元) |
| business_type | 类型：收入/成本 |
| status | DRAFT/PENDING_FINANCE/FINANCE_REJECTED/APPROVED |
| invoice_status | PENDING/SENT/ISSUED |
| accounting_status | NOT_POSTED/POSTING/POSTED |
| payment_status | UNPAID/PAID |
| settlement_doc_url | 结算单附件URL |
| invoice_url_pdf/xml/ofd | 发票文件链接 |
| payment_account_type | 收款账户类型 |
| payment_flow_no | 交易流水号 |

### 3.2 sap_record 核心字段

| 字段 | 说明 |
|---|---|
| row_id | 业务单据号 |
| bid | 业务主键 (与 ywms 联合主键) |
| ywms | 业务模式 |
| jylx | 交易类型 |
| bukrs | 公司代码 |
| budat | 过帐日期 |
| belnr | 会计凭证编号 |
| flag | 消息类型: S成功/E错误/W警告/I信息/A中断 |

### 3.3 sap_item_record 核心字段

| 字段 | 说明 |
|---|---|
| row_id | 业务单据号 |
| zhc | 行次 |
| kunnr | 客户编号 |
| lifnr | 供应商编号 |
| dmbtr | 应收/应付总额 |
| dmbtr1 | 手续费金额 |
| dmbtr2 | 税金 |
| dmbtr3 | 成本金额 |
| dmbtr4 | 收款金额 |
| prctr | 利润中心 |
| kostl | 成本中心 |

### 3.4 power_grid_company 核心字段

| 字段 | 说明 |
|---|---|
| company_name | 电网公司名称 |
| supplier_code | 供应商编码 |
| customer_code | 客户编码 |
| unified_social_credit_code | 统一社会信用代码 |
| tax_classification_code | 税收分类编码 |
| status | 1=正常, 0=已冻结 |
| contract_file_path | 合同影像文件路径 |

## 4. Controller/API 路由 (代码明确证明)

**来源**: `vpp-api-gpower/vpp-gpower-biz/src/main/java/com/nahui/energy/controller/`

### 4.1 绿电收益管理 `/greenElectricityRevenue`

| 路径 | 方法 | 说明 |
|---|---|---|
| /queryByPage | GET | 分页查询绿电收益列表 |
| /export | GET | 电费收益导出 (Excel) |
| /add | POST | 新增绿电收益 (自动生成DL单号) |
| /getImportTemplate | GET | 获取导入模板 |
| /importDataNew | POST | 导入绿电收益数据 (Excel) |
| /uploadSettlementDoc | POST | 上传结算单 |
| /financeAudit | POST | 财务审核 |

### 4.2 MDM 主数据管理 `/mdm`

| 路径 | 方法 | 说明 |
|---|---|---|
| /customer | GET | 查询MDM客户信息 (税码/88码/公司名) |
| /supplier | GET | 查询MDM供应商信息 (税码/V码/公司名) |
| /query-by-tax-code | GET | 根据税码同时查询客户和供应商 |
| /companies | GET | 查询MDM公司列表 |
| /customers-real | GET | 调用真实MDM API查询客户 |

### 4.3 电网公司管理 `/PowerGridCompany`

| 路径 | 方法 | 说明 |
|---|---|---|
| /add | POST | 新增电网公司 |
| /remove/{id} | DELETE | 删除电网公司 |
| /queryByPage | GET | 分页查询电网公司列表 |
| /queryById | GET | 根据ID查询电网公司详情 |
| /export | GET | 电网公司导出 |
| /enable/{id} | POST | 解冻电网公司 |
| /disable/{id} | POST | 禁用电网公司 |

### 4.4 电网合同管理 `/PowerGridContract`

| 路径 | 方法 | 说明 |
|---|---|---|
| /add | POST | 新增电网合同 |
| /remove/{id} | DELETE | 删除电网合同 |
| /queryByPage | GET | 分页查询电网合同列表 |
| /queryById | GET | 根据ID查询电网合同详情 |

## 5. 枚举定义 (代码明确证明)

**来源**: `vpp-api-gpower/vpp-gpower-biz/src/main/java/com/nahui/energy/enums/`

### 5.1 收益相关

| 枚举 | 值 | 说明 |
|---|---|---|
| GreenElectricityStatusEnum | DRAFT, PENDING_FINANCE, FINANCE_REJECTED, APPROVED | 绿电收益状态 |
| AccountingStatusEnum | NOT_POSTED, POSTING, POSTED | 记账状态 |
| PaymentStatusEnum | UNPAID, PAID | 收款状态 |
| InvoiceStatusEnum | PENDING, SENT, ISSUED | 发票状态 |
| AuditResultEnum | APPROVED, REJECTED | 审核结果 |
| AuditEnum | COMMIT(提交), AUDIT_PASS(通过), AUDIT_REJECT(驳回) | 审核操作 |

### 5.2 审批角色

**来源**: `ApproveRolesEnum.java`

| 角色 | code | 步骤 |
|---|---|---|
| 发起人 | fqr | 0 |
| 业务负责人 | ye_wu_fu_ze_ren | 1 |
| 副总经理 | fu_zong_jing_li | 2 |
| 总经理 | zong_jing_li | 3 |

**来源**: `PaybackManagementApproveRolesEnum.java` (回款管理审批)

| 角色 | code | 步骤 |
|---|---|---|
| 业务负责人 | ye_wu_fu_ze_ren | 1 |
| 财务 | cai_wu | 2 |
| 税务负责人 | shui_wu_fu_ze_ren | 3 |

### 5.3 订单阶段

| 阶段 | value | stage | 说明 |
|---|---|---|---|
| UPDATE_CUSTOMER_INFO | 1 | 完善客户信息 |
| CHOOSE_TRADE_GC | 2 | 选择交易绿证 |
| UPLOAD_CONTRACT_ATTACHMENT | 3 | 上传合同附件 |
| UPLOAD_VOUCHER_ATTACHMENT | 4 | 上传划证凭证 |
| ORDER_COMPLETED | 5 | 已完成 |
| ORDER_CANCELED | 6 | 订单作废 |

### 5.4 发票相关 (invoice/ 子包)

| 枚举 | 关键值 |
|---|---|
| InvoiceStatusEnum | NONE(无需), WAIT(待开票), INVOICING, SUCCESS(已开票), FAIL, WAIT_INVALID, INVALID(已作废), CANCEL, WAIT_RED(待红冲), RED(已红冲) |
| InvoiceTypeEnum | VAT(1,专票), NORMAL(2,普票), ELEC_GENERAL_INVOICE(3,电普票), ALL_ELEC_SPECIAL_INVOICE(81,全电专票), ALL_ELEC_NORMAL_INVOICE(82,全电普票) |
| InvoiceActionTypeEnum | CREATED(开具), RED(红冲), INVALID(作废) |
| ArchiveStatusEnum | NONE(无需), WAIT(待归档), ARCHIVE(已归档) |
| PostStatusEnum | NONE(无需), WAIT(待邮寄), POSTED(已邮寄) |
| BuyerDeductEnum | NO(未抵扣), YES(已抵扣) |
| ChannelTypeEnum | TECH(技术服务费), Vpp_Agent(中介费), Vpp_Agent_Haier(海尔中介费), Vpp_Company_Sell(项目公司卖出) |
| CompanyCodeEnum | 1Q80(青岛海尔新能源), 1PG0(青岛海尔光伏), 0LC0(日日顺科技), 0W50(日日顺乐农), 4300(小天将), 4110(乐农物联网), 1TP0(海尔智能), 1QJ0(海尔绿色能源) |
| ResponseCodeEnum | 200(成功), 201(校验不通过), 202(正在审批中), 203(审批不通过), 204(正在开票中), 205(开票失败), 211(单号已存在) |
| SystemCodeEnum | TAX_INVOICE_CLOUD(税票云), GOLDEN_TAX(金税), BEST_WONDER(百旺金赋) |

### 5.5 其他

| 枚举 | 说明 |
|---|---|
| SapFlagEnums | S(成功), E(错误), W(警告), I(信息), A(中断) |
| ChangeTypeEnum | ADD(入库), OCCUPY(占用), RELEASE(释放), OUT(出库) |
| ContractAuditEnum | WAIT_UPLOAD(待提交), WAIT_AUDIT(待审核), AUDIT_PASS(已签署), AUDIT_REJECT(已驳回), CANCEL(已作废) |
| CustomerTypeEnum | endCustomer(最终客户), intermediaryClients(中介客户) |
| CustomerIsAgentEnum | 0(是), 1(否) — ⚠️ 注意与 CustomerAreAgentEnum 相反 |
| CustomerAreAgentEnum | 0(否), 1(是) |
| PayStatusEnum | WAIT_PAY(未支付), PAY_WAIT_AUDIT(支付待审核), PAID_REJECT(已驳回), PAID_CONFIRM(已确认), PAY_CANCEL(支付取消) |
| PayTypeEnum | OFFLINE_PAY(线下支付), NET_PAY(网银支付) |
| VoucherAuditEnum | WAIT_UPLOAD(待提交), WAIT_AUDIT(待审核), AUDIT_PASS(已完成), AUDIT_REJECT(已驳回) |
| IntendCustomerStatusEnum | INIT(待提交), WAIT_AUDIT(待审批), AUDIT_OK(审批通过) |
| BlackListStatusEnum | 1(进入黑名单), 0(未进入) |
| SubmitRolesEnum | zong_bu_shang_wu(总部商务), fen_zhong_xin_fu_ze_ren(分中心负责人), fen_zhong_xin_ying_xiao_yuan(分中心营销员) |

## 6. MDM 主数据集成 (代码明确证明)

**来源**: `vpp-api-gpower/vpp-gpower-biz/src/main/java/com/nahui/energy/pojo/TransCustomerInfoXDToMDM/`, `MdmController.java`, `TransMdmCustomerAndSupplierService.java`

- **客户查询**: 通过税码(统一社会信用代码)、客户88码、公司名称查询 MDM 客户信息
- **供应商查询**: 通过税码、供应商V码、公司名称查询 MDM 供应商信息
- **集成方式**: SOAP Web Service (Apache CXF 生成的 WSDL 客户端)
- **WSDL 服务**:
  - `TransCustomerInfoXDToMDM` — 客户信息同步
  - `TransSupplierInfoRRSToMDM` — 供应商信息同步

## 7. SAP 财务记账集成 (代码明确证明)

**来源**: `vpp-api-gpower/vpp-gpower-biz/src/main/java/com/nahui/energy/dao/sap/`

- **SAP 记录表**: `sap_record` + `sap_item_record`
- **SAP URL 配置** (pom.xml profile):
  - local/dev: `http://58.56.128.84:9001/12CTEST/EAI/...`
  - jk-prod: `http://58.56.128.10:19001/GVS/GVS/TransInternetFromCBSToGVS/TransInternetFromCBSToGVS`
- **关键字段**: `bid`(业务主键) + `ywms`(业务模式) 联合唯一, `flag`(S/E/W/I/A) 表示SAP返回结果

## 8. 定时任务 (代码中存在但已注释)

**来源**: `vpp-api-gpower/` (代码中无活跃定时任务，vpp-api-km 中有注释掉的 InvoiceJobSchedule 和 TaskSchedule)

- `sendInvoiceJobHandler` — 发票发送定时任务 (已注释)
- `queryInvoiceResultJobHandler` — 发票查询定时任务 (已注释)
- `queryAndIncomeToSapHandler` — 上收入定时任务 (已注释)

## 9. 电价数据报表 (2026-05-28 新增)

**来源**: `vpp-api-gpower/vpp-gpower-biz/src/main/java/com/nahui/energy/controller/ElectricityPriceDataReportController.java`
**代码证明**: 2026-05-28 ~ 2026-05-29 期间新增 (commits: dcd33ba, 24b150d, dd643f7, 7fba4ca 等)

### 9.1 功能概述

电价数据报表模块，用于查询和导出**电力市场电价数据**，包括：
- **节点小时均价报表** (Node Hourly Average Price Report) — 各电力节点的小时均价
- **出清小时均价报表** (Spot Hourly Average Price Report) — 市场出清价格的小时均价

### 9.2 数据源 — ADS 独立数据源

**来源**: `vpp-api-gpower/vpp-gpower-biz/src/main/java/com/nahui/energy/config/AdsMapperConfig.java`

- 电价报表使用**独立的 ADS (AnalyticDB for MySQL) 数据源**，与主业务库分离
- 配置前缀: `spring.ads.datasource`
- Mapper 扫描路径: `com.nahui.energy.mapper.ads`
- XML 映射: `classpath*:/mapper/ElectricityPriceDataReportMapper.xml`
- 主数据源仍使用 `spring.datasource.druid` (MyBatis-Plus 默认)

### 9.3 Controller 路由 `/electricityPriceDataReport`

| 路径 | 方法 | 说明 |
|---|---|---|
| /nodeHourlyAvg/page | GET | 分页查询节点小时均价报表 |
| /nodeHourlyAvg/export | GET | 导出节点小时均价报表 (Excel) |
| /spotHourlyAvg/page | GET | 分页查询出清小时均价报表 |
| /spotHourlyAvg/export | GET | 导出出清小时均价报表 (Excel) |
| /filterOptions | GET | 查询筛选项 (区域/价格类型/城市/节点) |

### 9.4 核心 DTO

**ElectricityHourlyAvgReportBaseDTO** — 24小时电价列:
| 字段 | 说明 |
|---|---|
| hour0Price ~ hour23Price | 0-1点 ~ 23-24点均价 |

**ElectricityNodeHourlyAvgReportDTO** (继承 BaseDTO):
| 字段 | 说明 |
|---|---|
| dataRegionName | 数据区域名称 |
| priceType | 价格类型: day_ahead(日前), real_time(实时) |
| city | 城市 |
| nodeName | 节点名称 |
| infoDate | 日期 |

**ElectricitySpotHourlyAvgReportDTO** (继承 BaseDTO):
| 字段 | 说明 |
|---|---|
| dataRegionName | 数据区域名称 |
| priceType | 价格类型: day_ahead(日前), real_time(实时) |
| infoDate | 日期 |

**ElectricityPriceDataFilterOptionDTO** — 筛选项:
| 字段 | 说明 |
|---|---|
| dataRegionNames | 数据区域名称列表 |
| priceTypes | 价格类型列表 |
| cities | 城市列表 (节点小时均价使用) |
| nodeNames | 节点名称列表 (节点小时均价使用) |

### 9.5 Mapper 层

**来源**: `vpp-api-gpower/vpp-gpower-biz/src/main/java/com/nahui/energy/mapper/ads/ElectricityPriceDataReportMapper.java`

| 方法 | 说明 |
|---|---|
| queryNodeHourlyAvgPage | 分页查询节点小时均价 |
| querySpotHourlyAvgPage | 分页查询出清小时均价 |
| queryLatestNodeInfoDate | 查询节点小时均价最新有效日期 |
| queryLatestSpotInfoDate | 查询出清小时均价最新有效日期 |
| queryDataRegionNames | 查询数据区域名称列表 |
| queryPriceTypes | 查询价格类型列表 |
| querySpotDataRegionNames | 查询出清数据区域名称列表 |
| querySpotPriceTypes | 查询出清价格类型列表 |
| countAvailableNodeCities | 查询当前条件下真实城市数量 |
| queryCities | 查询城市列表 |
| queryNodeNames | 查询节点名称列表 |

### 9.6 导出优化历程 (2026-05-28 迭代)

- 初始实现 → 发现性能问题 → 优化导出逻辑
- 添加 Redis 分布式锁防止重复提交 → 后续移除 (可能因为锁粒度过大或不必要)
- 异常处理优化: 导出失败时检查响应是否已提交，避免无法返回 JSON 错误

### 9.7 与绿电收益模块的关系

- 电价数据报表是**独立的数据展示模块**，读取 ADS 数据源
- 绿电收益管理 (`green_electricity_revenue`) 使用主数据源，处理业务交易流程
- 两者**不共享数据库表**，电价报表纯粹是查询/导出功能，不涉及状态流转

## 10. 知识库更新记录

| 日期 | 更新内容 | 来源 |
|---|---|---|
| 2026-05-14 | 创建绿电收益管理完整业务文档 | vpp-api-gpower 全量通读 |
| 2026-06-06 | 新增第9节：电价数据报表模块 (ADS数据源/Controller/DTO/Mapper/导出优化) | vpp-api-gpower 重扫 delta (commits 2026-05-28~29) |
