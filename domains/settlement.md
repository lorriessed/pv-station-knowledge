# 结算、租金、财务与 SAP

更新时间: 2026-05-16

## 已确认知识

### 租金结算
固定租金模式适用于 HOUSEHOLD、PUB_BUILD、WHOLE_VILLAGE。流程为 ENABLE -> 生成租金队列 -> 租金确认 -> 租金支付。

### CM 工商业电费结算
CM 工商业为电费折扣模式，不是固定租金模式。存在共享账单概念，并涉及电费漏斗日发电快照、账单审核等流程。

### OSP UniApp 共享支付账单查询 (前端确认)
**来源**: `pv.osp-uni` → `src/pages/rent/detail.vue`, `src/types/api/Station.ts` (commit 67c7647, 李培龙, 2026-05-14)
- 租金详情页新增共享支付账单查询功能
- `Station.ts` 新增类型定义 13 行
- **证据等级**: 配置明确证明

### 辅材额度流水
辅材额度已知 4 类流水：S3 保证金总额和可用额度增加；S8 下单时可用额度减少、冻结额度增加；S11 签收时冻结额度减少、签收额度增加；D13 核销时可用额度增加、已核销额度增加。

### D13 真实释放链路
D13 释放链路为 InvoiceCheckUppHandle 回调 -> light_auxiliary_material_quota_exchange -> 定时任务 accountJob -> A92 记账 -> addD13FlowBySpCode。Admin 的 /release.do 存在但不被调用。

### pendingWrittenOffAmount
pendingWrittenOffAmount 是签收金额减已核销金额的隐式计算值，不是独立维护字段。

### 辅材额度改造 (2026-04-23~04-27)
- **来源**: rrsjk-finance-service, `LightAuxiliaryMaterialQuotaExchangeServiceImpl`/`InvoiceCheckUppHandle`, commits 36cb830/e2cde23 等 (tn_wangb)
- UPP发票核销完成后直接标记为支付成功 (`InvoiceCheckUppHandle`)

### 中银交易收益结算 (2025-12-23, TAEI-2753 电费管理模块迭代)
- **来源**: `rrsjk-light-service`, `ZhongYinTradeIncomeSettleService.java` + service.xml (commit d9858ee, 龙龙, 2025-12-23)
- **Dubbo服务**: `zhongYinTradeIncomeSettleService` 接口 `com.rrsjk.light.service.zhongyin.ZhongYinTradeIncomeSettleService`
- **功能**:
  - `importSettleData` — 数据导入(批量)
  - `confirmIncome(batchNo, confirmBy)` — 确认上收入(按批次)
  - `deleteByBatchNo(batchNo)` — 未确认批次可删除
  - `reverseAfter(List<IncomeReverseResult>)` — 冲销后数据处理
  - `incomeSapJob()` — 中银上收入定时任务(自动推送SAP)
  - `checkIncomeByStationCode(stationCode)` — 校验电站是否已上收入
  - `incomeReverse(stationCode)` — 收入冲销
- **关联**: 越秀农户收益异常支付查询(解钦, 2025-12-15~19), 新增246行Mapper SQL

### 合同撤销恢复 (2025-12-22~25, TAEI-2760)
- **来源**: `rrsjk-light-service`, `LightContractRevocateAndRestoreLog.java` + Mapper XML (commits 6db25d6/c760aec/473434e等, 22081194/包鑫)
- **实体**: `LightContractRevocateAndRestoreLog`
  - 字段: relateId, relateCode, contractType, operateType(REVOCATE/RESTORE), contractNo, contractUrl, remark, operateBy, operateAt
  - **操作类型枚举**: `OperateTypeEnum` — REVOCATE("撤销"), RESTORE("恢复")
- **业务逻辑**: 合同撤销和恢复操作需记录原因(remark)和操作人日志, 支持追溯

### 运维收入成本记账 (2025-12-18, TAEI-2792)
- **来源**: `rrsjk-light-service` + `rrsjk-finance-service` (commits by sunzn, 实际工时16h)
- 运维收入成本管理记账逻辑迭代, 涉及采购申请结算无纸化服务优化
|- 新增 `SyncSapDeliverHandle` (2026-04-23)

### 商城采购成本价锁定 (TAEI-3175, 代码明确证明, 2026-06-03)
**来源**: `rrsjk-finance-service/SyncSapDeliverHandle.java` (包鑫, commit: 3e43d054ac)
- **变更**: SAP 发货记账从使用 `ProductPrice` (实时查询价格) 改为 `OrderItemCost` (下单时锁定的成本价)
- **影响**:
  - `SyncSapDeliverHandle` 构造函数注入从 `ProductPriceService` 改为 `OrderItemCostService`
  - `A77ToSap()` 和 `A05ToSap()` 方法参数从 `ProductPrice` 改为 `OrderItemCost`
  - 金额计算: `dmbtr3 = orderItemCost.getCostPriceUnTax() × quantity` (原为 `productPrice.getUnTaxPrice() × quantity`)
- **业务意义**: 采购价格锁定为下单时，避免后续价格波动影响 SAP 记账
- 辅材额度支付相关改造涉及 `SapFinanceAndOrderServiceImpl`、`SyncOrderToSapHandle`

### 退质保金审核流程优化 (2026-04-22)
- **来源**: rrsjk-finance-service, `PurchaseApplySettleDepositRefundServiceImpl`, commits 0fb64f2/71a2418 (tn_wangb)
- 增加修改对账单接口
- 退质保金记账如果没有发票凭证，去请款单上查询并保存

### SAP 服务商查询改为编码 (2026-04-21)
- **来源**: rrsjk-finance-service, `SapPurchaseRecordService`, commit 223a54d (龙龙)
- 服务商ID参数替换为服务商编码参数

### 辅材押金收款 SAP 逻辑强化 (2026-04-18)
- **来源**: rrsjk-finance-service, `SapClient.java`, commit 4326ee5 (yumiao)
- 强校验 1PG0/JHDH/TRANSFER

### 零碳适家安装费结算 (ZeroCarbon)
**来源**: rrsjk-finance-service → `zerocarbon/service/impl/ZeroCarbonApplySettleServiceImpl.java`, `ZeroCarbonInstallBillServiceImpl.java`

#### 预算占用流程
1. 创建请款单 → 状态为初始
2. 调用预算中心 API (`zeroCarbonBudgetHsccApi.syncBudgetOccupy`) 进行预算占用
   - 费用项目编码: `66660404` (零碳安装费)
   - 业务场景: `CBS-PAY-LTAZ`
   - 系统编码: CBS (`S00693`) → 预算中心 (`S03085`)
   - 税额计算: `actualSettleAmount / 1.09` (9%税率)
3. 预算占用状态: 1=成功, 2=申请中, 3=失败
4. 占用成功后状态更新为 10 (预算占用申请中)

#### 云报账 (Ybz) 出款流程
1. 预算占用成功后发起云报账单 (`ybzSending`)
2. 组装报账请求报文 (`InstallFeeYbzRequestBody`):
   - expenseId: `66660404`, expenseCategory: `DG`
   - 发票校验: 发票总额与结算金额比较，决定 `isInvoiceInstalment` (是否分期)
   - payType: `1` (网上付款)
3. 报账单申请中状态: 11，ybzPayStatus: 2
4. 调用 `ZeroCarbonYbzApi` 发起报账
5. 记录请求/响应流水到 `ybz_bill_request_param_record`, `ybz_bill_main_response_record`

#### 安装费对账单
**来源**: `ZeroCarbonInstallBillServiceImpl.java`
- `createBillAndDeposit()`: 事务性创建安装费对账单 + 押金记录
- 关联表: `zero_carbon_install_bill`, `zero_carbon_deposit_record`

#### 请款单状态流转
| 状态码 | 含义 |
|---|---|
| 10 | 预算占用申请中 |
| 11 | 报账单申请中 |

#### 操作日志类型
| operateType | 含义 |
|---|---|
| 10 | 预算占用成功 |
| 22 | 预算占用失败 |

### 电站收入上收限制策略工厂 (TAEI-3085, 2026-05-12~05-16 代码明确证明)
**来源**: `rrsjk-light-service` → `StationIncomeModeCheckStrategyFactory.java`, `StationModeEnum.java`, 8个策略实现类 (解钦)

#### 背景
电站有多种资方模式（越秀、中核、浦银、招银、华电、华融、中银、基金），导入收入时需要校验电站是否已在其他模式下上了收入，避免重复。

#### 策略工厂架构
```
StationIncomeModeCheckStrategyFactory (工厂)
    ↓ 自动注入所有 StationIncomeModeCheckStrategy 实现
    ├── YxIncomeModeCheckStrategy (越秀)
    ├── ZhIncomeModeCheckStrategy (中核)
    ├── PyIncomeModeCheckStrategy (浦银)
    ├── ZyIncomeModeCheckStrategy (招银)
    ├── HdIncomeModeCheckStrategy (华电)
    ├── HrIncomeModeCheckStrategy (华融)
    ├── ZhongYinIncomeModeCheckStrategy (中银)
    └── FundIncomeModeCheckStrategy (基金)
```

#### 核心方法
- `batchFindConflictModes(stationCodes, currentMode)` — 批量查询电站在其他模式下的收入冲突
- `getModeByLatestIncomeTime(stationCode)` — 根据最近收入时间判断电站当前所属模式
- 重构后：将原来硬编码的 if-else 改为工厂+策略模式，新增资方只需添加策略实现

#### 收入处理策略（handle 层）
```
StationIncomeHandleStrategyFactory
    ├── YxStationIncomeHandleStrategy (越秀)
    ├── ZhStationIncomeHandleStrategy (中核)
    ├── PuYinStationIncomeHandleStrategy (浦银)
    ├── ZyStationIncomeHandleStrategy (招银)
    ├── HdStationIncomeHandleStrategy (华电)
    ├── HrStationIncomeHandleStrategy (华融)
    ├── ZhongYinStationIncomeHandleStrategy (中银)
    └── FundStationIncomeHandleStrategy (基金)
```
两层工厂分离：`mode` 层负责模式校验/查询，`handle` 层负责具体收入处理逻辑。

### 越秀A88流程屏蔽 (2026-05-09)
- **来源**: rrsjk-finance-service, `LightSapLedgerUseServiceModel.java`, commit d29ccde (龙龙, 2026-05-09)
- 注释了越秀模式下的A88流程处理逻辑（临时屏蔽，原因待确认）

### FAP 记录体系 — 保证金/电费/采购订单覆盖 (代码明确证明, 2026-04-28~05-07)
**来源**: `rrsjk-light-service` → `LightDepositServiceImpl.java`, `LightSparePartsDepositServiceImpl.java`, `ZeroCarbonSpDepositServiceImpl.java`, `rrsjk-trade-service` → 订单FAP相关 (commits b4d16db7/2ade7d1d/c014b8b2/cbc285bb/c82b7fdc/a4dcb786/414880c0, 代继宁, 2026-04-28~05-07)
**关联需求**: FAP财务系统对接持续迭代
- **保证金取消逻辑修复**: 
  - 新增 FAP 记账状态检查 — 已记账的订单不允许取消 (`AccountStatusEnum.YES`)
  - 修复空指针问题 — FAP记录不存在时不抛异常，改为跳过作废流程
  - 三个保证金服务同步修复: `LightDepositServiceImpl`, `LightSparePartsDepositServiceImpl`, `ZeroCarbonSpDepositServiceImpl`
- **FAP记录创建优化**:
  - 统一 FAP 记录创建流程 (`cbc285bb`)
  - 修复 FAP 状态设置逻辑错误 (`414880c0`)
  - 修复 FAP 记录检查逻辑错误 (`a4dcb786`)
- **FAP查询定时任务**: 更新FAP查询定时任务逻辑 (`d2505003/d7449276`)
- **电费单据**: 更新电费单据作废摘要并添加凭证状态枚举 (`2ade7d1d`)
- **Trade Service FAP集成**: 
  - 移除 `LightFapRecordService` 的 Dubbo 服务配置 (`c487affb`)
  - 修复轻采购销售订单FAP收款创建逻辑 (`e0a6927b/56040ceb`)
  - 添加订单项目同步到FAP功能 (`68f6c7fc`)
  - 修复线下转账支付流程中的FAP记录创建逻辑 (`944d1684`)
- **证据等级**: 代码明确证明

### TAEI-3023 经营性租赁回款接FAP（开发中, 2026-06-04 确认风险）
**来源**: `rrsjk-light-service` (代继宁, branch: origin/20260602-fapPart2, commit: fb0c4c5b48, 2026-06-02)
- **负责人**: 刘艺(PM) | **实际开发**: 代继宁 | **参与人**: 薛荣基
- **变更**: `LightFapRecordServiceImpl` 中注释掉经营性租赁资产FAP状态同步逻辑
  - `syncOperationalAssetFapSentStatus()` — 注释掉更新 FAP 发送状态
  - `syncOperationalAssetFapResult()` — 注释掉 FAP 查询结果自动确认
  - **Dubbo 配置新增**: `service.xml` 新增 `operationalAssetManagementService` 引用 → `com.rrsjk.report.service.OperationalAssetManagementService`
- **⚠️ 2026-06-04 风险确认**: `grep -rn "operationalAssetManagementService" --include="*.java"` 返回空
  - **结论**: 旧同步逻辑已停，新服务仅在 service.xml 声明但未 @Autowired 使用
  - **影响**: 经营性租赁回款的FAP状态同步功能当前处于**不可用状态**
  - **建议**: 确认是否有意暂停，或需要补充 @Autowired 注入 + 调用逻辑
- **证据等级**: 代码明确证明

### TAEI-3117 运维商押金/备件押金上线集团FAP（开发中, 2026-06-05 新增FAP集成）
**来源**: `rrsjk-light-service` (孙志男 sunzn, commit 1a5e72e8b3, 2026-06-05) + `rrsjk-admin-web` (sunzn) + `rrsjk-light-report-service` (sunzn)
- **负责人**: 高媛(PM) | **实际开发**: 孙志男 | **参与人**: 魏秋阳、孙志男
- **状态**: 开发中
- **核心变更**:
  - `LightFapRecord.BizTypeEnum` 新增 `OPERATION_DEPOSIT("运维保证金", "TY010031", "收-保证金-其他应付款（先收后退）")` — 与 SPARE_PARTS_DEPOSIT 使用相同业务编码
  - `LightOperationDeposit` 实体新增 `fapStatus` 字段 + `FapStatusEnum` (WAIT_SENT/SENT/CANCEL)
  - `LightOperationDeposit.Status` 新增 `CANCEL("已作废")` 状态
  - `LightOperationDepositService` 新增 `cancelDepositOrder()` 作废订单 + `fapRecordCreate()` 手动创建FAP汇总
  - `LightFapRecordServiceImpl` 新增 `syncOperationDepositFapSentStatus()` 和 `syncOperationDepositFapResult()` 双向同步
  - **调用链**: FAP回调 → `LightFapRecordServiceImpl.syncOperationDepositFapResult()` → 更新 `LightOperationDeposit` status=CONFIRMED + accountStatus=YES + accountVoucher/accountAt/confirmAt/thirdTradeNo
  - **业务意义**: 运维商押金/备件保证金正式接入集团FAP财务制证平台，实现从"线下确认"到"FAP自动记账"的升级
- **关键文件**: `LightFapRecord.java:272`, `LightOperationDeposit.java:72/102/148`, `LightOperationDepositServiceImpl.java`
- **证据等级**: 代码明确证明
- **扫描日期**: 2026-06-06

### TAEI-3103 电站业主租金停付管理（测试中, 2026-06-04 大量bugfix）
**来源**: `rrsjk-light-service` (孙志男, branch: origin/szn_rent_stop_20260525, 2026-05-28~06-03)
- **负责人**: 高媛(PM) | **实际开发**: 孙志男 | **参与人**: 魏秋阳、孙志男、李培龙
- **状态**: 测试中 (updateStatusAt 2026-06-05)
- **提交量**: 20+ 条提交，集中在 2026-06-01~03
- **核心变更**:
  - 新增 `RentSuspendApplication` 租金停付申请实体 + 相关DAO/Mapper
  - `RentSuspendApplicationRecord` 停付申请记录
  - 租金暂停/恢复申请的完整状态机校验逻辑
  - 多次迭代修复：工单状态验证、空指针异常、重复校验、恢复原因验证
  - 新增枚举: 租金停付申请恢复原因枚举
  - **本周修复**: b8930b7(恢复申请状态检查: 添加 RESUME_AUDIT_REJECTED 状态允许重新提交), 789e3dd(恢复原因验证逻辑), 4fabced(工单状态验证和扣除月数校验)
- **关键提交**: 4fabced(工单状态验证修复), 7876ae1(空指针修复), b8930b7(恢复申请状态检查), 789e3dd(恢复原因验证), c71e58c(恢复原因枚举), b58c338(电站状态字段)
- **证据等级**: 代码明确证明

### TAEI-3079 电费收益相关优化（测试中, 2026-06-01）
**来源**: `rrsjk-light-service` (tn_wangb/王斌, commits: fcc3f015/0cb5e245ba/60cd5f1b1a, 2026-06-01)
- **负责人**: 徐晓凤 | **实际开发**: 王金浩(laowang/tn_wangb) | **参与人**: 薛荣基、商轶龙
- **变更**:
  - `LightProjectElectricOrder.xml`: 批量更新 `fap_cancel_status` 字段（CASE WHEN 批量更新模式）
  - `CmLightProject.java`: 工商业电站写入工商业项目编码
  - `LightSpOrder` 分支: 传SAP记出库、收入取主数据逻辑优化（不判断物料状态，取最后一条数据）
- **关联表**: `light_project_electric_order` (新增 fap_cancel_status 批量更新)
- **证据等级**: 代码明确证明

### 零碳适家安装费 — 服务重构 (代码明确证明, 2026-04-30)
**来源**: `rrsjk-light-service` → `ZeroCarbonSpDepositServiceImpl.java` (commits 0fafc048/298da120/3a301b8d, 代继宁, 2026-04-30, branch: master_pre_prod_20260206-ZeroCarbonInstallFee)
- 优化零碳安装费用服务实现
- 修复零碳适家保证金FAP记录创建和状态同步问题
- 零碳FAP状态设置逻辑修复
- **证据等级**: 代码明确证明

## 待确认
- CM 共享账单完整审批流。
- SAP A88、A92 等凭证业务含义和资方差异。
- 越秀A88流程屏蔽的原因和恢复计划。
- 零碳适家结算中预算占用失败后的重试机制。
- 云报账回调处理逻辑和支付结果同步机制。
- 各资方收入结算时xref3字段传递电站编码的具体用途。
- **工商业自持电站损益报表完整数据流**: 充电桩数据从"于川清大数据库"获取的具体接口和表结构。
- **电站收入上收限制的8种模式**: 每种模式的收入表、校验逻辑、冲突处理规则。

### FAP凭证补偿机制 (代码明确证明, 2026-05-19~20)
**来源**: `rrsjk-light-service` → 代继宁 commits 34fc750/597db04/0e7e2f5, branch 20260416-FapRecordOfReceipts
**关联需求**: TAEI-3021/3022 保证金收款接FAP、订单收款接FAP
- **凭证补偿**: 新增FAP凭证补偿机制，用于FAP推送失败后的重试和补偿
- **11种业务类型覆盖**: MATERIAL_REPURCHASE(物料回购), STATION_REPURCHASE(站点回购), SERVICE_DEPOSIT(服务押金), SPARE_PARTS_DEPOSIT(备件押金), INVERTER_SALE(逆变器销售), MALL_ORDER(商城订单), ZERO_CARBON_DEPOSIT(零碳押金), ZERO_CARBON_ORDER(零碳订单), VPP_ORDER(VPP订单), EPC_RECEIPT(EPC收款), ELECTRIC_ORDER(电费订单)
- **补偿任务**: `LightFapRecordService.compensationVoucherJob()` — 扫描 `compensationStatus=WAIT` 的记录，按业务类型分发处理
- **客户信息保护**: 更新凭证时不再覆盖已有的 `accountCustomerCode`/`accountCustomerName`
- **确认人信息**: 统一使用 `getConfirmBy()` 方法，从FAP查询结果中提取确认人
- **DAO新增**: `LightSpOrderItemDao.getByOrderItemNo(String)` — 按订单项目编号查询
- **状态常量**: 修复FAP收款记录状态常量，移除补偿状态相关代码
- **客户信息更新**: 优化客户信息更新逻辑
- **逆变器销售场景**: 确认收款逻辑更新
- **批次号**: 安装费对账单签署回调地址修改
- **导出功能**: FAP收款记录导出功能
- **查询优化**: FAP增加查询字段，优化分页查询逻辑
- **记账状态**: 订单记账状态显示优化
- **证据等级**: 代码明确证明

## 来源
- Hermes MEMORY.md，2026-05-09 迁移。
- rrsjk-finance-service 代码扫描 2026-05-10。

---

## 租金个税记账批量确认接口优化 (代码明确证明, 2026-05-29)
**来源**: `rrsjk-admin-web` → `RentTaxRecordController.java`, `RentTaxAmountRecordExcel.java`, `RentTaxAmountSummaryExcel.java`, `rentTaxAmountSummaryList.ftl` (commits: 代继宁, 2026-05-29, TAEI-3092)
- 优化租金个税记账批量确认接口，多次迭代修复
- 增加记账信息相关字段到Excel导出
- `rentTaxAmountSummaryList.ftl` 大幅更新（133行变更）
- **证据等级**: 代码明确证明

---

## SAP记账接口多次更新 (代码明确证明, 2026-05-29)
**来源**: `rrsjk-light-service` → `RentTaxAmountServiceImpl.java` (commits: 代继宁, 2026-05-29, TAEI-3092)
- 记账成功后错误信息置空 (`.sapSentResult("")`)
- 更新SAP记账接口字段传参，修改交易类型等传参
- 多次迭代：更新→Revert→再次更新
- 优化租金个税批量确认错误返回、保存逻辑
- 租金个税批量任务统计逻辑优化，添加中间表分批处理
- 暴露租金个税接口
- 租金个税报表统计、各类查询接口、财务确认代码发SAP接口提交
- **证据等级**: 代码明确证明

### 租金个税定时任务执行月份优化 (TAEI-3092, 代码明确证明, 2026-05-29)
**来源**: `rrsjk-light-service` → `RentTaxAmountServiceImpl.java` (commit 70fde56f, 代继宁)
- 修改定时任务执行月份计算公式
- 修复执行不存在的SQL导致报错的问题

### 租金个税中间表分批处理优化 (TAEI-3092, 代码明确证明, 2026-06-04 扫描发现)
**来源**: `rrsjk-light-service` → `RentTaxAmountServiceImpl.java` (commit 6a1bd48, 代继宁, 2026-05-28)
- **核心重构**: `executeTaxCalculation()` 从内存批处理改为中间表分批处理
- **旧逻辑**: 查询10万+条支付成功记录到内存 → 每500条查库校验 → 批量插入底表
- **新逻辑**:
  1. 清空中间表 `tax_amount_calculate_source_data_temp`
  2. `INSERT INTO` 中间表（从 `light_share_bill_record` 直接导入，区分首月/普通月）
  3. 按公司编码维度迭代：`findDistinctCompanyCodes()` → 逐公司处理
  4. 唯一校验键从 `billRecordNo` 改为 `rentDate_stationCode` 组合
  5. 新增 `updateInvalidStatus()` — 重复执行时标记未财务确认公司的数据为作废
  6. 事务管理从 `@Transactional` 改为编程式 `transactionManager.getTransaction()`
- **新增依赖**: `SapRecordService` 注入、`TaxAmountCalculateSourceDataTempDao`
- **新增实体**: `TaxAmountCalculateSourceDataTemp`（中间表实体，64行）
- **影响**: 税务计算性能优化（减少内存占用）+ 幂等性改进（唯一键变更）

### 电站方案变更暂停状态逻辑调整 (2026-06-04 扫描发现)
**来源**: `rrsjk-light-service` → `LightStationPlanChangeServiceImpl.java` (commits: 解钦, 2026-06-01~03)
- **变更**: 电站暂停状态(`pauseStatus`)在方案变更流程中的管理逻辑
- **旧逻辑**: 申请方案变更时无条件冻结电站状态(`PAUSED`)
- **新逻辑**: 按条件分支处理 — 特定场景下不冻结，驳回时恢复暂停状态
- **涉及提交**: b19ca01(冻结状态), 28be144(上收入导入判断暂停), bb0ed4c(移除驳回拦截), 2c55163(移除线下验收拦截), 97a648b(驳回恢复暂停)
- **影响**: 电站状态机在方案变更/驳回流程中的行为变化，可能影响并发操作

### TAEI-3174: 硬编码生产数据预警 ⚠️ (2026-06-04 扫描发现)
**来源**: `rrsjk-light-service` → `LightStationYuexiuAccountServiceImpl.java` (commit e6fdd67, 解钦, 2026-06-02, TAEI-3174)
- **问题**: 14个生产手机号硬编码在代码中做项目公司映射
  - 广州越晖光伏科技有限公司(lessorCode=3093): 6个手机号
  - 郑州华耀顺绿色新能源有限公司(lessorCode=3390): 4个手机号
- **风险**: 业主手机号变更需重新发版，硬编码数据可能随时间过期
- **建议**: 应改为数据库配置表或配置中心管理
- **证据等级**: 代码明确证明

---

## AI智能对账 — 多模板选择逻辑精简 (代码明确证明, 2026-05-29)
**来源**: `rrsjk-admin-web` → `AiReconciliationHandler.java` (commits: lilong, 2026-05-29, TAEI-3110)
- **变更**: 注释掉一个发电户号映射多个发票模板时的多模板选择逻辑（~30行注释掉）
- **原因**: 模板映射功能有导入校验，从页面操作不会出现一个发电户号映射多个模板
- **移除依赖**: 移除 `LightProjectElectricOrderService` 注入
- **证据等级**: 代码明确证明

---

## 电费发票查询新增条件 (代码明确证明, 2026-05-29)
**来源**: `rrsjk-admin-web` → `LightCapitalProjectElectricOrderInvoiceController.java`, `lightCapitalProjectElectricOrderInvoiceList.ftl` (commits: laowang/王金浩, 2026-05-29)
- `doList.do` 接口新增查询条件: `invoiceStatus`(发票状态), `purchaserName`(购销方名称), `companyName`(公司名称)
- **证据等级**: 代码明确证明

## 电站租金查询与账单 (代码明确证明)
**来源**: `rrsjk-light-operation-service` → `StationRentDto.java`, `LightOperationStationServiceImpl.java`, `LightOperationStationElecBill.java`, `LightOperationElecBillTaskService.java` (commits afbccaf/ffc8b32, 2026-05-12)

### 租金记录字段扩展
- `StationRentDto` 新增 `remark`（备注）和 `billDate`（账单日期）字段
- 电费管理添加定时任务同步发电量、项目公司、电站分组信息
- 修复银联租金查询无账号问题
- 修复租金查询接口电站图片不正确问题

### 资方收入结算 - xref3传递电站编码 (代码明确证明)
**来源**: `rrsjk-light-service` → `HuaRongTradeIncomeSettleServiceImpl.java`, `PuYinSettleQueueJobServiceImpl.java`, `ZhaoYinTradeIncomeSettleServiceImpl.java`, `ZhongYinTradeIncomeSettleServiceImpl.java`, `LightYuexiuSettleModel.java` (commit 72283a8, 2026-05-12)
- 上收入时传递xref3字段传递电站编码，覆盖华融、普银、招银、中银、越秀等资方

### VPP回款凭证校验记账 (代码明确证明)
**来源**: `vpp-api-gect` → `OrderManagementInfo.java`, `EntityOrderManagementInfo.java`, `NormalOrderManagementInfo.java`, `AutoCreateOrderManagementInfo.java`, `PaybackManagementInfo.java` (commit 65988f6, 2026-05-13)
- `checkCompanyTypeAndUppBack()` 方法参数从依赖 `toDataAndValidate().getUppUrl()` 改为直接传入 `payVoucherUrl`（回款凭证URL）
- 使用传入的回款凭证校验记账条件，而不是从订单数据内部获取
- 手动上传凭证场景：如果没有上传凭证则不能记账

### BT资产管理报表 (代码明确证明)
**来源**: `rrsjk-admin-web`, `rrsjk-light-report-service`, `rrsjk-light-service` → `BtAssetManagementController.java`, `BtFundAssetAllocateDetailController.java`, `BtProjectTransactionController.java` 等 (多个commit, 2026-05-12)
- BT模式需求变更适配：字段调整、Excel导出错误提示
- 导入功能新增失败数据列表生成（`BtAssetManagementErrorExcel.java`, `BtFundAssetAllocateDetailErrorExcel.java`, `BtProjectTransactionErrorExcel.java`）
- BT股转模式及中核报表导入校验BT和中核模式

### SAP收款对账逻辑精简 (代码明确证明)
**来源**: `rrsjk-finance-service` → `SapClient.java` (commit fbb3b655, baoxin, 2026-05-15)
- `rrsjk-finance-impl/src/main/java/com/rrsjk/finance/sap/component/collection/SapClient.java` 删除31行代码，仅保留2行
- 修改对账(reconciliation)相关逻辑，具体业务语义需进一步读取完整diff确认
- **证据等级**: 代码明确证明（commit message描述为"修改对账"，文件大幅精简）

### 报表电站模式筛选与日期参数优化 (代码明确证明, 2026-05-15)
**来源**: `rrsjk-light-report-service` → `ReportScreenMapServiceImpl.java`, `LightStation.xml` (commits 52c0c5b6/1120866e/269d62f3/b8130daf, 代继宁, 2026-05-15)
- 大屏地图报表(`ReportScreenMapService`)新增**电站模式筛选**功能，可按电站模式(ModeEnum)过滤统计数据
- 修复给定时间参数为空时的处理逻辑：经历了三轮迭代修复，最终移除多余的空值检查，优化日期参数处理
- MyBatis Mapper `LightStation.xml` 新增模式筛选相关SQL片段
- **影响范围**: 智慧大屏 `/dashboard/apv` 地图统计报表，支持按资方模式维度查看数据
- **证据等级**: 代码明确证明

### 共享支付完整业务流程 (代码明确证明, 2026-05-18 历史补漏第1期)
**来源**: `rrsjk-light-service` → `LightShareBill.java`, `LightShareBillPayFailRecord.java`, `LightShareBillServiceImpl.java`, `LightShareBillRecordServiceImpl.java`, `ShareProjectPaymentAccount.java` (TAEI-2716/2724/2727, 2025-11-17~2025-12-07)
- **共享账单(light_share_bill)**: 按项目公司+分中心维度汇总的账单。包含金额、服务费、总金额、确认状态等
- **共享支付明细(light_share_bill_record)**: 每笔支付明细，关联电站和业主信息
- **支付失败记录(light_share_bill_pay_fail_record)**: 记录打款失败的明细，包含银行账号、业主姓名、身份证号等，支持重新支付处理
- **支付账户(share_project_payment_account)**: 项目公司支付账户。TAEI-2716要求创建支付明细时取电站上的银行卡、联行号、支行名称
- **商户通/小程序展示(TAEI-2724)**: 增加显示电站由共享支付的成功明细/支付失败记录
- **退汇处理(TAEI-2727)**: 退汇和退回处理功能
- **初审退回状态**: rrsjk-admin-web 新增共享租金支付初审退回状态

### 越秀租金收益拉取重构 (2026-05-18)
**来源**: TAEI-3089, `rrsjk-light-service` → `LightYuexiuIncomeBillJobServiceImpl.java` (commit c0935ef2, 解钦, 2026-05-14)
**代码明确证明**

#### 新旧版对比
| 维度 | 旧版 (pullIncomeBillV0) | 新版 (pullIncomeBill) |
|---|---|---|
| 状态 | 保留备用，注释掉@override | 当前生产使用 |
| 数据范围 | 逐月拉取 | 本月 + 补拉缺失期数 |
| 缺失检测 | 无 | `fillMissingPeriods()` — 对比已有账单列表，找出缺失期数 |
| 公共逻辑 | 内嵌在循环中 | 抽取为 `doPullAndInsert()` — 拆分日期范围、调用越秀接口、批量入库 |

#### 新版流程
```
拉取本月数据(rangeStart=月初, rangeEnd=月末)
    ↓
检测缺失期数(fillMissingPeriods):
    1. 查询已有账单列表(partnersContractNumber)
    2. 按期数排序，找出连续的缺失区间
    3. 对每个缺失期数调用 pullMissingPeriodData()
    ↓
doPullAndInsert():
    1. 日期范围拆分为最多10个月一段
    2. 调用越秀远程API(remoteApi)
    3. 批量入库(batchInsert)
```

### SAP 对账单查询精细化条件修复 (代码明确证明, 2026-05-18)
**来源**: `rrsjk-merchant-web` → `LightSapPurchaseRecordController.java` (commit b6eb03f9ca, yumiao, 2026-05-18)

**问题**: 对账单查询时，当使用 skuName/regionId/cityId/provinceId/houseType 等电站维度条件筛选时，`stationParam` 缺少 `spMemberId`（服务商会员ID），导致可能跨服务商查询到其他服务商的电站数据。

**修复**: `buildCondition()` 方法中，在调用 `lightStationService.findStationCodeBy(stationParam)` 之前，新增：
```java
stationParam.put("spMemberId", spMemberId);
```

**影响范围**: `GET /light/lightSapPurchaseRecord/list.do` 和导出接口，所有涉及电站多维度条件筛选的对账单查询。

**同时变更**: 移除未使用的 `org.apache.curator.shaded.com.google.common.collect.ImmutableMap` import。

---

## 自持电站损益报表 (代码明确证明, 2026-05-19)
**来源**: `rrsjk-light-service` → `CmOwnerStationReportServiceImpl.java`, `CmOwnerStationReportDao.java` (commits dd0926551c, b13ce495, c9616c63, 0a42ed04, tn_wangb, 2026-05-12~18)
**需求**: TAEI-3100 【报表】自持电站损益报表

- **Service 层**: `CmOwnerStationReportServiceImpl` — 报表查询与生成逻辑
- **DAO**: `CmOwnerStationReportDao` — findBy, getById, batchInsert, findReportBy
- **Entity**: `CmOwnerStationReport` — 报表数据实体
- **Entity**: `CmOwnerStationReportThirdLog` — 第三方推送日志
- **Service**: `CmOwnerStationWhiteListService` — 白名单控制 (注入 CmOwnerStationReportDao 和 CmOwnerStationReportService)
- **业务逻辑**: 
  - 发电来源字段非必填，兼容1PG0公司导入
  - 高压电费查询逻辑特殊处理
  - 二期需求扩展字段和查询条件
- **推断表**: `cm_owner_station_report`, `cm_owner_station_report_third_log`, `cm_owner_station_white_list`

---

### 金蝶记账失败状态处理 (代码明确证明, 2026-05-19)
**来源**: `rrsjk-light-service` → `LightProjectElectricOrderServiceImpl.java`, `LightProjectElectricOrder.java` (commits 92fcbf81, 85bbef82, mabin, 2026-05-14~15)

- 新增 `JINDIE_FAIL` 枚举值 — 标识金蝶记账失败状态
- 股转公司5月份历史已收款收入数据重传逻辑 (282行新增)
- 金蝶返回凭证为空时正确设置失败状态和原因
- 发票冲销失败原因保存优化 (`LightProjectElectricInvoiceReverseRecordServiceImpl`)
- FAP查询流程优化，移除过时代码

---

### 金蝶SAP记账 budat 历史数据修复 (代码明确证明, 2026-06-02)
**来源**: `rrsjk-finance-service` → `JinSapClientModel.java` (commit 0ea0e96, mabin, branch `20250525-jindieRepeatFix`, 2026-06-02)

- **问题**: `syncFinanceToSap()` 原逻辑无条件覆盖 `budat` 字段为当前日期 (`sapRecord.setBudat(format.format(new Date()))`)
- **修复**: 改为仅在 `budat` 为空时设置默认值
  ```java
  if (StringUtils.isBlank(sapRecord.getBudat())) {
      sapRecord.setBudat(format.format(new Date()));
  }
  ```
- **业务影响**: 修复5月18日之前的历史记账数据异常，保留原始记账日期而不是被覆盖为当天
- **关联**: 同分支此前已加金蝶分布式锁并发控制

---

### 退质保金申请驳回后不释放已选择的单据 (代码明确证明, 2026-06-02)
**来源**: `rrsjk-finance-service` → `PurchaseApplySettleDepositRefundServiceImpl.java` (commit dab8d8d, tn_wangb, 2026-06-02)

- **applyDepositRefund 新增校验**: 错误信息从"请选择可结算的保证金明细"改为精确提示"电站XXX质保金非可结算状态，已被单号XXX占用"
- **editDepositRefund 逻辑重构**:
  - 计算新增和删除的质保金明细ID列表 (`addDepositIds` / `deleteDepositIds`)
  - 新增的明细才修改为 `APPLY_SETTLE` 状态
  - **删除的明细修改为 `ENABLE_SETTLE` 状态并清空 `applyNo`** — 释放占用，允许其他申请选中
  - 异常分支新增错误返回（此前rollback后无错误提示）
- **业务意义**: 修改质保金退款申请时，移除的明细应释放可结算状态，避免其他申请无法选中

---

## FAP凭证补偿机制 (代码明确证明, 2026-05-19)
**来源**: `rrsjk-light-service` → `LightFapRecordServiceImpl.java`, `LightFapRecord.java` (commits 34fc750e, 597db042, 代继宁, 2026-05-18)

- `LightFapRecord` 新增 compensationStatus 字段 (54行)
- 补偿状态枚举: PENDING(待确认), CONFIRMED(已确认), COMPENSATED(已补偿), PENDING_MANUAL(待人工确认)
- 支持业务类型: 物料回购补偿、站点回购补偿、服务押金补偿
- FAP记账仅对转账类型订单执行，避免非转账订单误记账
- `LightSpOrderItemDao` 新增按订单项目编号查询方法
- `LightFapRecordService.compensationVoucherJob()` — 补偿任务接口

---

## 运维收入A51冲销暂估 (代码明确证明, 2026-01-18 扫描补漏第3期)
**来源**: `rrsjk-light-service` (commits by sunzn, 2026-01-12~16, TAEI-2812 运维收入成本管理模块)

- `OperationMaintenanceServiceImpl.coverOperationMaintenanceA51()` — A51数据暂估冲销入口
- `coverA51()` — 执行A51类型数据冲销，从记账数据取数计算冲销金额
- 允许确认实际时同步集团内项目公司A58成本信息
- 项目公司客户编码查询验证机制
- 冲销凭证生成和状态更新
- 涉及文件: `LightSapService.java`, `OperationMaintenanceService.java`, `LightSapServiceImpl.java`, `OperationMaintenanceServiceImpl.java`
- **关联需求**: TAEI-2812 (运维收入成本管理模块-集团内项目公司记账优化, 孙志男负责)

## 基金模式上收入 (代码明确证明, 2026-01-18 扫描补漏第3期)
**来源**: `rrsjk-light-service` (commits by 解钦, 2025-12-29~12-31, TAEI-2804 基金模式上收入)

- 资金结算表重命名: `light_zh_settle` → `light_fund_settle`
- 基金收入结算功能: `FundSettlementService` 实现
- 基金收入冲销功能 (`reverseFundIncome`)
- 基金结算类型字段新增
- 收入确认时添加确认时间和确认人信息
- 资金结算收入检查功能
- SAP记账队列重试计数字段初始化 (finance-service, 解钦 2025-12-29)
- 收入处理策略重构: 华融模式电站收入校验策略、结算数据创建和SAP调用逻辑优化
- **关联需求**: TAEI-2804 (基金模式上收入, 杨越越/姜传德/解钦参与)

## 采购申请结算重构 (代码明确证明, 2026-01-18 扫描补漏第3期)
**来源**: `rrsjk-light-service` + `rrsjk-finance-service` + `rrsjk-admin-web` (commits by yumiao/sunzn, 2026-01-12~17)

- 采购申请结算编辑功能数据提交方式重构 (admin-web)
- 采购单ID类型修改 (finance-service)
- 发票核销流程优化，添加采购单ID字段
- 采购记录状态列表查询功能 (SAP)
- 按采购类型查询采购记录
- 无纸化服务中运维商合同查询修复
- Guava缓存优化路灯电站数据查询性能
- 电表状态数据显示修复
- **关联需求**: TAEI-2805 (2025-12-31合同及基础政策升级)

## 统众资方接入 (代码明确证明, 2026-01-18 扫描补漏第3期)
**来源**: `rrsjk-light-service` + `rrsjk-finance-service` + `rrsjk-admin-web` (commits by tn_wangb, 2026-01-05~16)

- 统众资方项目公司主数据管理
- 统众资方发票模板菜单
- 电站回购成本增加合作共建费
- 请款申请预算体编码增加农村服务
- 原材料回购成本价格计算更改
- 租金支付批次标识处理
- 租金支付传云报账是否直付字段更改
- 影像推送更改
- 退质保金备注修改
- **关联需求**: 内部资方接入系列

## 共建费模式 (代码明确证明, 2026-01-18 扫描补漏第3期)
**来源**: `rrsjk-light-service` + `rrsjk-admin-web` (commits by majinhu, 2025-12-29~2026-01-16, TAEI-2805/2814)

- **联合建设费模式枚举** (`JointConstructionFeeModelEnum`): SUPPORT/NOT_SUPPORT
- **共建专项合同类型**: `TP_PAYMENT_AGENCY` (合同类型值33)
- 共建费主合同模板配置 (`jonitConstructionFeeMasterTemplate`)
- 共建费主合同签署成功回调 (`gjfMasterStationSignSuccess`)
- 合同模板区分: 主合同 vs 专项合同
- 租金模式设置: `BaseLightStationMode.setRentalMode()` — 根据项目公司+共建费用模式确定租金模式
- 施工审批通过添加电站逆变器绑定功能 (`/merchant/light/workOrder/auditOk.do`)
- 4种模式统一重构合同记录创建逻辑
- 共建费模式判断: 项目公司代码 → `LightCompanyInfo.jointConstructionFeeModel` → 是否创建共建专项合同
- 电站新建时租金模式设置功能
- 公司联合建设费模式支持判断
- **关联需求**: TAEI-2805 (2025-12-31合同及基础政策升级), TAEI-2814 (微信小程序银行卡变更)

## 自持电站报表 Controller 按年/月拆分 (代码明确证明, 2026-05-19)
**来源**: `rrsjk-admin-web` → `CmOwnerStationReportController.java` (commits tn_wangb, 2026-05-15~19, commit af9a454c6)
**需求**: TAEI-3100 【报表】自持电站损益报表

- **API 拆分**: 原单一 `doList.do` 拆分为两个独立接口：
  - `doYearList.do` — 按年度查询（参数 `year`，Service 调用 `findPageByYear()`）
  - `doMonthList.do` — 按月度查询（参数 `yearMonth`，Service 调用 `findPageByMonth()`）
- **导出拆分**: 原单一 `doExport.do` 拆分为：
  - `doYearExport.do` — 年度导出，文件名含年份
  - `doMonthExport.do` — 月度导出，文件名含月份
- **列表页**: `list.html` 移除了 `queryCondition` 参数传递
- **分页导出**: 月度导出使用每页 5000 条分页循环导出（EasyExcel），年度导出同理
- **前端模板**: `cmOwnerStationReportList.ftl` 大规模更新（393行变更）

---

## 电费收益订单导入月份去重校验移除 (代码明确证明, 2026-05-19)
**来源**: `rrsjk-admin-web` → `LightProjectElectricOrderController.java` (commit 龙龙 d9158c52f, 2026-05-18)
**需求**: TAEI-3079 【电费】电费收益相关优化

- **变更**: 导入数据时的"发电户号+月份"重复校验逻辑被**全部注释掉**
- **原逻辑**: 遍历开始月份到结束月份之间的每个月，检查 `elecNo_monthKey` 是否在 `importMonthMap` 中已存在，防止同一户号同一月份在导入数据中重复
- **影响**: 导入时不再阻止同一发电户号在同一月份出现多条记录，重复校验可能改由后端 Service 层或数据库唯一约束处理

---

## 金蝶财务同步并发控制 (代码明确证明, 2026-05-19; 2026-05-25 更新)
**来源**: `rrsjk-finance-service` → `JinDieSyncFinanceModel.java` (commits: mabin 08f696150 2026-05-19, 3d94616 2026-05-25)

- **分布式锁**: 使用 `StringRedisTemplate.opsForValue().setIfAbsent()` 实现 Redis 分布式锁
- **锁 key**: `jinDie:sync:finance:{bid}:{ywms}`（正向同步和冲销共用 `CONCURRENT_LOCK_PREFIX`）
- **超时时间**: 1 分钟自动释放（防止死锁）
- **锁冲突处理**: 获取锁失败时设置 flag="E"，message="金蝶财务同步正在执行中"，直接返回
- **释放锁**: finally 块中调用 `stringRedisTemplate.delete(lockKey)` 确保释放
- **幂等保护不变**: 锁检查在幂等检查之前，已有成功记录（有 belnr）的仍直接返回
- **~~影响范围: syncFinance() 方法，不影响 reverseFinanceToSap() 冲销方法~~** → **2026-05-25 更新**: `reverseFinanceToSap()` 冲销方法也加了相同的分布式锁保护（commit 3d94616, branch `20250525-jindieRepeatFix`），防止冲销并发导致重复记账

---

## 绿证交易库存调整 (代码明确证明, 2026-01-18 扫描补漏第3期)
**来源**: `cbs-web` (commits by yumiao/德, 2026-01-04~15, TAEI-2800)

- 手动调整库存生成流水记录
- 库存流水操作类型: `库存调整-覆盖`, `库存调整-删除`
- 消息通知功能添加 (系统消息优先级字段映射)
- 品牌名称更新: 日日顺 → 海尔
- CBS通知面板功能
- 品牌名/首页标题更新
- **关联需求**: TAEI-2800 (绿证交易手动调整库存)

---

## 华融B43模式上收入记质保金逻辑 (代码明确证明, 2026-05-20)
**来源**: `rrsjk-light-service` → `HuaRongIncomeQualityGuaranteeServiceImpl.java` (commits: yumiao 23846b5, 08debe1e, 2026-05-18)
**需求**: TAEI-3044 【户用光伏】华融上收入的时候再多1个账，业务模式B43，DMBTR=收入金额(应收账款)*质量保证金比例

- **核心逻辑**: 华融业务模式 B43（融资租赁）在收入结算时，需要额外记一笔质量保证金账
- **计算公式**: DMBTR = 收入金额(应收账款) × 质量保证金比例
- **防御性校验修复**: `findLatestByStationCode(entity.getStationCode())` 改为 `findLatestByStationCode(existsHrflcywmlB43.getStationCode())` — 使用B43记录的电站码而非entity的，避免空指针
- **涉及服务**: 
  - `HuaRongIncomeQualityGuaranteeServiceImpl` — 华融收入质保金服务
  - `HuaRongTradeIncomeSettleDao.findLatestByStationCode()` — 查询最新收入结算记录
- **关联文件**: `rrsjk-admin-web` → 华融质保金页面权限点复用华融交易收入 (commit yumiao, 2026-05-18)

---

## 收入导入Assert懒加载优化 (代码明确证明, 2026-05-20)
**来源**: `rrsjk-light-service` → 多个SettleServiceImpl (commits: 解钦 880f3d1, 2c23886, 2026-05-19)
**需求**: TAEI-3085 【收入】增加上收限制

- **性能优化**: 将 `Assert.isTrue(condition, "error message")` 改为 `Assert.isTrue(condition, () -> "error message")`
- **原因**: 原始写法在 Assert 之前就会拼接字符串（即使 condition 为 true），改为 lambda 懒加载后，仅在条件不满足时才拼接错误消息
- **涉及8个服务类**:
  - `HuaRongTradeIncomeSettleServiceImpl` (华融)
  - `LightFundSettleServiceImpl` (基金)
  - `LightHdIncomeServiceImpl` (弘德)
  - `LightStationYuexiuSettleServiceImpl` (越秀)
  - `LightZhSettleServiceImpl` (中核)
  - `PuYinTradeIncomeSettleServiceImpl` (普银)
  - `ZhaoYinTradeIncomeSettleServiceImpl` (招银)
  - `ZhongYinTradeIncomeSettleServiceImpl` (中银)
- **业务语义**: 收入导入时检查电站是否已在其他业务模式下存在收入记录，防止重复上收入
- **冲突检测**: `incomeConflicts.containsKey(stationCode)` — 跨业务模式的收入冲突检测

---

## 电站回退领用兼容完工前领用 (代码明确证明, 2026-05-20)
**来源**: `rrsjk-light-service` → `CompleteConfirmServiceImpl.java` (commits: 解钦 e5c0361, 2fbdd00, 789fff6, eb8bd38, 2026-05-15~19)
**需求**: TAEI-3083 【建站】完工前变更方案审批流变更

- **核心修复**: 电站回退重新领用时，需要兼容「完工前领用」的特殊场景
- **完工前领用特点**: 不创建SO出库队列（Sales Order Outbound Queue），因此冲销时不需要处理出库队列
- **基金收入科目修复**: A40 → A41，基金重上收入安装费科目调整
- **状态流转优化**: `CompleteConfirmServiceImpl` 中审核逻辑增加 `stationCode` 字段设置 (`updateStation.setStationCode(dbStation.getStationCode())`)
- **BusinessStatusMode 变更**: `offLineChoose` 参数从必传改为 `@Nullable`，支持线下验收结合技术商务并行
- **影响链**: 电站回退 → 冲销领用事项 → 不创建SO出库队列（完工前场景） → 基金科目A40→A41

---

## 微智慧发票系统集成 (代码明确证明, 2026-01-19~2026-02-08 补漏第4期)
**来源**: `rrsjk-trade-service` (解钦, commits: 83635f0~de3a12d, 2026-02-02~02-05)
**需求**: TAEI-2860 【发票】股转公司对接微智慧 开发票 + TAEI-2859 【电费】电费发票红冲模块针对股转公司下电站优化

- **集成系统**: 微智慧(WZH)票税云平台 — 全电发票开票 + 红冲
- **核心类**:
  - `WzhCloudInvoiceApi` — 微智慧发票API接口封装
  - `WzhCloudInvoiceResponse` — 响应DTO(数据类型改为字符串)
  - `WzhCloudInvoiceCreateResultQueryModel` — 开票结果查询模型
  - `WzhCloudInvoiceReverseResultQueryModel` — 红冲结果查询模型
  - `InvoiceJobServiceImpl` — 发票定时任务服务
- **功能**:
  - 微智慧全电开票 → 查询开票结果 → 红冲 → 查询红冲结果
  - 支持环境切换(生产/测试)，配置在代码中通过开关控制
  - 红冲功能: 支持对已开具的微智慧发票执行红冲操作
- **配置文件**: `bootstrap.yml` 中新增微智慧发票服务配置项
- **关联需求**: TAEI-2850 【绿证交易】自动开票改手动开票 — 绿证交易发票从自动改为手动触发

## 运维商服务费结算无纸化合同影像匹配 (代码明确证明, 2026-01-19~2026-02-08)
**来源**: `rrsjk-finance-service` (孙志男, commits: cacec6c, 72236e9, 2026-02-04~02-05) + `rrsjk-light-operation-service`
**需求**: TAEI-2861 运维商服务费结算无纸化合同影像匹配逻辑优化 + TAEI-2852 HDS-新增社会化运维合同管理模块

- **重构内容**: 运维服务合同查询逻辑重构，支持条件性必填字段
- **合同编号**: 采购申请结算中合同编号获取逻辑修复
- **终止协议**: 添加终止协议合同编号参数 (`c555fff`, 2026-02-04)
- **合同验证**: 更新合同验证逻辑以支持条件性必填字段 (`be2bb56`, 2026-02-05)
- **社会化合同**: 添加社会化合同信息管理功能 (`df15b54`, 2026-01-30)

## 运维商买损冲销管理 (代码明确证明, 2026-01-19~2026-02-08)
**来源**: `rrsjk-light-operation-service` (孙志男, 30+ commits, 2026-01-21~2026-02-05)
**需求**: TAEI-2852 HDS社会化运维合同管理 + TAEI-2853 社会化服务"非自建电站"模块迭代

- **买损冲销申请**: 完整的买损冲销流程，包括申请、审核、SAP冲销凭证
- **关键字段**: 建站保证金单号、建站商登录账号、冲销申请原因、核销金额=损失金额
- **SAP集成**: 三审通过后自动触发SAP冲销流程 (`7652f6f`, 2026-02-02)
- **冲销凭证**: 添加冲销凭证保存功能 (`16b326c`, 2026-02-03)
- **保证金余额**: 更新损失管理中的保证金余额字段，注释掉旧的余额更新逻辑
- **运维商分级**: 实现运维商分级功能 + 月及时闭环率查询 + 等级计算性能优化

## 运维商月度账单(户用)模块优化 (代码明确证明, 2026-01-19~2026-02-08)
**来源**: `rrsjk-hds-web` + `nahui-pv.hds-h5` (李培龙, commits: bf8a631, 2026-01-27)
**需求**: TAEI-2830 运维商月度账单（户用）模块优化

- **HDS页面**: 运维商月度账单模块优化，更新搜索项、样式调整
- **账单状态**: 添加历史导入数据明细账单状态字段

## 质保金明细表已作废状态 (代码明确证明, 2026-02-05)
**来源**: `rrsjk-finance-service` (王斌/tn_wangb, commit: 2c9e483, 2026-02-05)

- 质保金明细表新增"已作废"状态标识
- 租金支付明细: 支付成功二次确认逻辑 (`5d2b6e3`, 2026-01-22)
- 租金查凭证逻辑更改 (`acfd95b`, 2026-01-21)
- 26年之前的请款单走老影像接口 (3 commits, 2026-01-19)

## 超期考核电站驳回考核附加表 (代码明确证明, 2026-01-30)
**来源**: `rrsjk-finance-service` (王斌/龙龙, commit: 89f4e81, 2026-01-30)

- 新增超期考核电站驳回考核附加表功能
- 涉及 Dubbo 服务配置优化和日志级别调整

### 运维收入管理合并开票优化 (代码明确证明, 2026-05-20)
**来源**: `rrsjk-trade-service` → `CloudInvoiceCreateModel.java`, `InvoiceServiceImpl.java`
**Commits**: 76a29a7a/cf86a40e, 开发者: sunzn, 2026-05-19~20
**需求分支**: `szn_merge_invoice_20260519`

- **合并逻辑**: `CloudInvoiceCreateModel.cloudInvoiceHeadItemListByOperation()` 新增运维收入合并开票明细合并 — 当 `relationNoAll` 以 "OM" 开头且 `relationType` 为 `OperationMaintenance` 时，将多条发票明细合并为一条传参给票税云
- **金额规则**: `InvoiceServiceImpl` 中运维收入(`OperationMaintenance`)新增数据允许单条金额小于0，但合并开票总金额必须大于0（非运维收入仍要求单条金额≥0）
- **跳过验证**: BREAK(合同解约)、PEO开头(电费订单)、LightElec开头(工商业电费)的单据跳过含税单价×数量与含税金额的平衡验证(容差0.5元)
- **发票明细合并方法**: `handelInvoices()` — 取第一条发票的元数据，累加所有发票的 amount/untaxAmount/taxAmount 作为合并后单条明细的价格和金额

### 发票红冲 — 股权转移判断逻辑替换 (2026-02-12 代码明确证明)
**来源**: `rrsjk-trade-service` → `InvoiceJobServiceImpl.java` (commits 3b60c259/0e964698/f4630827, 解钦)
- **变更原因**: 原来通过 `invoice.getSystemCode()` 判断调用票税云(TAX_INVOICE_CLOUD)还是微智慧(WZH)，但股权转移后判断逻辑不准确
- **新逻辑**: 通过 `LightCompanyInfoService.isStockTransfer(companyCode)` 查询项目公司是否股权转移
  - 未股转(`false`) → 调用票税云(`cloudInvoiceReverseModel.reverse`)
  - 已股转(`true`) → 调用微智慧(`wzhCloudInvoiceReverseModel.reverse`)
- **影响范围**: 发票红冲执行(`reverseInvoiceResult`) + 发票红冲结果查询(`queryInvoiceReverseResult`) 两处
- **涉及表**: `invoice` 表（红冲状态管理）
- **依赖服务**: `LightCompanyInfoService`（Dubbo远程调用，查询项目公司股转状态）
- **证据等级**: 代码明确证明

### 电量账单统计 — DISTINCT去重修复 (2026-02-27 代码明确证明)
**来源**: `rrsjk-light-operation-service` → `LightOperationStationElecBill.xml` (commit d3909faf, sunzn)
- **问题**: JOIN操作导致同一电站被多次关联，COUNT/SUM 出现重复计算
- **修复**: 三个统计维度全部改用 `DISTINCT`:
  1. 子中心维度: `count(DISTINCT s.station_code)`, `sum(DISTINCT s.complete_confirm_capacity)`
  2. 项目公司维度: `count(DISTINCT s.station_code)`, `sum(DISTINCT s.complete_confirm_capacity)`
  3. 省份维度: `count(DISTINCT s.station_code)`, `sum(DISTINCT s.complete_confirm_capacity)`
- **影响**: 电站总数(total_station_num)和装机容量(total_power)统计数据准确性提升
- **证据等级**: 代码明确证明

### 电费结算查询 — NULL值判断修复 (2026-02-25 代码明确证明)
**来源**: `rrsjk-light-operation-service` (commit 5d4fb615, sunzn)
- 修复电费结算查询条件缺失NULL值判断的问题
- 优化电费结算任务查询逻辑 (commit bcd2f119)
- **证据等级**: 代码明确证明

### 工商业风电产值收入法 (代码明确证明, 2026-05-18~22)
**来源**: `rrsjk-light-service`, `rrsjk-admin-web`, `rrsjk-merchant-web` (tn_wangb/王斌, TAEI-3085/3100, 分支 origin/feature-cm-wind-electric + origin/20260506-wb-cmOwnerStationReport)
- **工商业自持电站损益报表二期**: 前端页面+后端报表逻辑+商户端数据
- **工商业风电项目产值收入法**: 风电项目上收入的产值法计算逻辑
- **工商业风电项目终验法**: 风电项目终验法计算逻辑
- **工商业收款切换FAP**: 工商业收款流程切换至FAP系统
- **方案变更修改**: 方案变更相关逻辑适配
- **证据等级**: 代码明确证明

### 招银组件功率匹配价格 (代码明确证明, 2026-05-18~23)
**来源**: `rrsjk-light-service`, `rrsjk-admin-web` (lilong/李龙, TAEI-3112, 分支 origin/20260515-alone-zhaoyin-price)
- **需求变更**: 改用 `createAt` 作为新旧数据的区分逻辑
- **取值方式变化**: 组件功率匹配价格的取值逻辑调整，区分新老数据
- **证据等级**: 代码明确证明

### 发电户号电费模板映射 (代码明确证明, 2026-05-20~22)
**来源**: `rrsjk-light-service`, `rrsjk-admin-web` (lilong/李龙, TAEI-3112, 分支 origin/20260519-alone-electricAI)
- **后端接口**: 按发电户号批量查询电站信息、按ID列表批量获取数据
- **前端功能**: 页面本地调试、导出Excel样式调整、添加按钮shiro权限控制
- **证据等级**: 代码明确证明

### AI识别对账单导入电费收益开票 (代码明确证明, 2026-05-21~26)
**来源**: `rrsjk-admin-web` (lilong/李龙, TAEI-3110, 分支 origin/20260519-alone-electricAI)
- **页面跳转接口**: 新增页面跳转接口及修改
- **映射关系**: 金额和税额从映射关系中取值，项目公司名称映射成销方名称
- **AI接口参数**: 调整AI接口返回参数类型 (commit 59b22a6b, 2026-05-26)
- **aiTotalAmount字段**: "AI识别对账单总计金额"字段从接口返回实体的 `aiTotalAmount` 字段中取值 (commit df78daf4/e2447d98, 2026-05-25)
- **月份逻辑**: 调整开始月份和结束月份的处理逻辑 (commit a332f605, 2026-05-25)
- **Mock测试**: AI识别添加mock数据用于本地测试 (commit 232d1d5c, 2026-05-25)
- **页面样式**: 调整页面展示样式 (commit d4cf8216, 2026-05-26)
- **后端关联**: `rrsjk-light-service` 提供发电户号电费模板映射接口 (commits 1473adc9/ad0e5bad, lilong)
- **注意**: 此需求号在云效中实际为 TAEI-3110，非 TAEI-3112
- **证据等级**: 代码明确证明

### FAP收款记录全链路 (TAEI-3021/3022/3092, 2026-05-18~21 代码明确证明)
**来源**: 代继宁 25个提交, 跨4个后端仓库 + 1个前端仓库, 分支 `origin/20260416-FapRecordOfReceipts`, `origin/20260416-fap`
- **业务语义**: FAP(财务核算平台)收款记录的全链路功能，覆盖零碳适家保证金收款(TAEI-3021)、绿证交易订单收款(TAEI-3022)、农户租金类个税报表及记账(TAEI-3092)
- **跨服务链路**:
  - `rrsjk-light-service`: FAP凭证补偿机制、凭证更新补偿、优化FAP接口响应处理、优化订单推送结果消息、修复取消FAP记录时状态丢失、线下金蝶记账功能
  - `rrsjk-finance-service`: FAP回调重复创建现金订单项目修复
  - `rrsjk-trade-service`: 添加订单发票号设置、修正订单同步日期范围、修复轻采购销售订单凭证处理、解决FAP凭证重复更新、添加订单编号设置、添加订单记账状态字段
  - `rrsjk-merchant-web`: 修复FAP订单取消逻辑、修复订单取消时FAP状态检查、FAP收款记录导出功能
  - `rrsjk-admin-web`: FAP收款记录导出、修复FAP状态显示和订单推送确认提示、修复FAP推送条件判断、添加记账状态显示
- **关键逻辑**:
  - FAP凭证补偿: 确保FAP接口调用失败时可补偿重试
  - 订单记账状态: 新增字段跟踪订单是否已记账
  - 取消FAP记录: 修复状态丢失问题 (commit dd2ef5c80e)
  - 线下金蝶记账: 新增功能 (commit 2f4a94b99b)
- **涉及需求**: TAEI-3021(零碳适家保证金收款接FAP), TAEI-3022(绿证交易订单收款接FAP), TAEI-3092(农户租金类个税报表及记账), TAEI-3093(电站图片模板组数据库存储)
- **证据等级**: 代码明确证明

### 运维收入成本管理 — 批量导入/批量删除/电站详情明细 (TAEI-2871/2876, 2026-03-02~20 代码明确证明)
**来源**: `rrsjk-hds-web` (sunzn, 12 commits), `rrsjk-light-service` (sunzn, 10+ commits), `nahui-pv.hds-h5` (李培龙, 8 commits)

- **批量导入**: `OperationMaintenanceController` 新增 Excel 批量导入功能，支持全空行过滤、模板下载、删除导入模板
  - 导入时校验: 按开票序号分组校验金额总和 (`龙龙`, commit c029fbd, 2026-03-10)
  - 允许单条负数但批次总金额必须大于0 (`龙龙`, commit 8a1f462, 2026-03-10)
  - HDS前端: `OperationMaintenanceController` 添加导入导出功能 (sunzn, commit d684828, 2026-03-12)
- **批量删除**: 支持批量删除运维收入账单记录
  - 前端: `nahui-pv.hds-h5` 运维收入管理列表增加批量导入/批量删除功能 (李培龙, commit 90da666, 2026-03-12)
- **电站详情明细**: 新增批量导入/批量删除账单的电站详情明细展示
  - 前端: 电站收入成本明细新增子管理单号 (李培龙, commit 275488e, 2026-03-13)
  - HDS前端: 运维收入成本管理历史导入数据明细新增传参 (李培龙, commit c87162f, 2026-03-20)
- **冲销功能增强**:
  - A51暂估冲销: `LightSapServiceImpl.coverOperationMaintenanceA51()` 新增 opCode 参数，支持按记账类型区分A48和A51冲销处理 (sunzn, commit eb9bba4, 2026-03-19)
  - 冲销队列管理: `OperationMaintenanceQueueServiceImpl` 根据记账类型区分冲销处理 (sunzn, commit eb9bba4)
  - 重复冲销修复: 解决重复冲销导致的数据异常问题 (sunzn, commit 81d600b/bbfd083, 2026-03-03)
  - 冲销账单数据变更修复 (sunzn, commit 759ea82, 2026-03-10)
  - 历史账单冲销任务: 保留原数据状态为"已冲销"，创建新管理单号数据及电站详情 (sunzn, 2026-03-17)
- **涉及表**: `operation_maintenance` (新增 isReverse/reverseBy/reverseAt 字段), `operation_maintenance_station`, `operation_maintenance_queue`
- **关联需求**: TAEI-2871 (运维收入成本管理模块迭代), TAEI-2876 (运维收入成本管理列表：增加批量导入/批量删除账单的电站详情明细)
- **证据等级**: 代码明确证明

### 运维维护逻辑删除与修复 (2026-05-28 代码明确证明)
**来源**: `rrsjk-light-service` (sunzn, branch: origin/szn_om51_20260527)
- **OperationMaintenance**: 新增逻辑删除功能 (`isDeleted` 字段)
- **OperationMaintenanceServiceImpl**: 修复冲销逻辑状态判断、维护日志关联ID设置错误、反向标识值修正、数据查询过滤逻辑删除记录
- **HDS-Web**: `CreateOperationMaintenanceStationController` 批量更新A51数据导入、修正导入数据订单号索引错误 (TAEI-3163, 项目公司股转后A51/A48账单数据处理)
- **HDS-Web**: `BusinessCooperationIntentionController` 逆变器数据查询功能扩展
- **HDS-Web**: `EnergyJobController` 新增手动生成报表接口
- **证据等级**: 代码明确证明

### 零碳适家请款结算 — 对账单确认回调/云报账支付状态/安装费列表 (TAEI-2883, 2026-03-02~20 代码明确证明)
**来源**: `rrsjk-finance-service` (代继宁, 20+ commits), `rrsjk-admin-web` (代继宁, 7 commits), `rrsjk-finance-service` (魏秋阳, sunzn)

- **对账单确认回调**: `ZeroCarbonApplySettleService.zeroCarbonConfrimCallBack()` 新增回调接口，对接无纸化结算确认状态
  - 回调参数: `ZeroCarbonApplySettleNoPaper` + `ZeroCarbonApplySettleLog`
  - 逻辑: 对账单确认后更新请款单状态，触发后续结算流程 (代继宁, commit 74ffa56, 2026-03-19)
- **云报账支付状态**: 新增云报账支付状态字段 `ybzPayStatus`，优化状态更新逻辑
  - 状态流转: 初始 → 预算占用申请中(10) → 报账单申请中(11) → 支付成功/失败
  - 定时查询出款状态: `queryYbzStatusList()` 定时查询云报账出款结果 (代继宁, commit 4869126, 2026-03-19)
- **安装费列表优化**:
  - 安装费列表增加对账和支付状态字段 (代继宁, commit 9777dc0, 2026-03-19)
  - 修复零碳申请结算页面权限和数据显示问题 (代继宁, commit f7c452b, 2026-03-11)
  - 修复零碳申请结算中的支付类型筛选和时间精度问题 (代继宁, commit d51ef8c, 2026-03-20)
  - 完善零碳适家请款结算单合同状态处理逻辑 (代继宁, commit f6beaa79, 2026-03-17)
  - 修复零碳申请结算状态更新逻辑 (代继宁, commit aa58333, 2026-03-17)
  - 重构零碳申请结算审批记录处理逻辑 (代继宁, commit f2296bd, 2026-03-17)
- **发票校验**: 新增服务商ID支持并优化发票校验流程 (代继宁, commit 7abda1d, 2026-03-20)
- **预算占用**: 重构零碳预算占用相关实体和配置 (代继宁, commit f6db0cd, 2026-03-02)
- **无纸化结算**: 更新无纸化结算状态并优化账单更新逻辑 (代继宁, commit 3300760, 2026-03-20)
- **关联需求**: TAEI-2883 (零碳适家安装费结算，商户通及CBS对账单、发票、请款，对接HBC和云报账系统)
- **证据等级**: 代码明确证明

### 零碳适家智投配货申请 — 配货额度占用 (TAEI-2933, 2026-03-03~20 代码明确证明)
**来源**: `rrsjk-admin-web` (德/姜传德, 2 commits), `rrsjk-merchant-h5` (李培龙, 2 commits), `rrsjk-finance-service` (代继宁)

- **智投订单管理**: 新增智投订单详情和列表页面，实现审核功能 (德, commit 15c404b, 2026-03-02)
- **配货申请**: 商户通新增零碳智投配货申请功能
  - 智投备货申请列表展示变更 (李培龙, commit 44c7fdb, 2026-03-03)
  - 逆变器详情变更当日功率数据展示，添加tooltip提示 (李培龙, commit 64bac06, 2026-03-17)
- **发货额度占用**: 智投订单发货后需要占用服务商发货额度
- **防重复提交**: `lightConfirmOrder` 添加防重复提交功能 (德, commit 0681ef2, 2026-03-19)
- **关联需求**: TAEI-2933 (零碳智投商户通新增零碳智投配货申请，智投订单发货后需要占用服务商发货额度)
- **证据等级**: 代码明确证明

### 零碳适家分中心更新 (TAEI-2886, 2026-03-04 代码明确证明)
**来源**: `rrsjk-light-service` (代继宁/姜传德/包鑫)

- 分中心数据更新 (2026-03-04)
- 关联需求: TAEI-2886 (零碳适家分中心更新0304)
- **证据等级**: 代码明确证明

### 运维收入冲销 — 重复冲销修复与历史账单冲销 (TAEI-2871, 2026-03-02~20 代码明确证明)
**来源**: `rrsjk-light-service` (sunzn, multiple commits)

- **重复冲销防护**: `isReverse` 字段默认值设置为"1"（未冲销），创建运维数据时初始化冲销状态
  - 冲销前检查: `!"0".equals(oldData.getIsReverse())` 防止已冲销数据再次冲销
  - 已确认收款无法冲销: `!OperationMaintenance.Status.CONFIRMED_SK.value().equals(oldData.getStatus())`
- **历史账单冲销任务**:
  - 逻辑变更: 保留原数据状态为"已冲销"，创建新的管理单号数据及电站详情 (而非直接修改原数据)
  - 冲销完成后: 插入新电站明细数据，更改账单编码换新
  - 账单主数据: 主状态更新为待确认，暂估凭证/冲销凭证/确认实际凭证/确认收款凭证全部置空
  - 循环冲销: 每种业务类型都需要冲掉 (`reverseFinanceToSap(rowId, "C_" + bid)`)
- **冲销凭证前缀**: `C_` + rowId (标准冲销前缀规则)
- **已冲销数据保护**: 账单已冲销后不允许变更数据
- **证据等级**: 代码明确证明

### 审核列表 — 最近一次审核人信息展示 (TAEI-2878, 2026-03-09~16 代码明确证明)
**来源**: `rrsjk-light-service` (yumiao, commit 76c35f9), `rrsjk-admin-web` (yumiao, commit 4285803)

- **新增字段**: `lastAuditBy` (最近审核人), `lastAuditAt` (最近审核时间)
- **审核列表页面**: 显示最近一次审核人信息 (yumiao, commit 4285803, 2026-03-16)
- **方案/技术/商务审核驳回意见**: 数据来源更改为从审核记录表获取 (解钦, commit ef217d7, 2026-03-12)
- **电站技术审核回显**: 修复 `changeRoofOrHouseType` 回显问题 (yumiao, 6 commits, 2026-03-09)
- **关联需求**: TAEI-2878 (商户通菜单精简优化) 及审核相关优化
- **证据等级**: 代码明确证明

### 机制电价管理 — 批量审核功能 (2026-03-13 代码明确证明)
**来源**: `rrsjk-admin-web` (mabin, commits 7b14446/5429dfa, 2026-03-13)

- 机制电价管理增加批量审核功能
- 导入导出增加批次号字段
- 增加批量审核弹窗
- 修复机制电量管理导出入围比例不显示问题 (mabin, commit 621ada2, 2026-03-11)
- **证据等级**: 代码明确证明

---

## 备件运维财务结算 (repairs, 2026-05-22 代码明确证明)
**来源**: `repairs` → finance/ 目录下各 Service 接口

### 服务商清欠三级审批
- **流程**: 运维商提交 → 中心审批 → 业务部审批 → 财务审批
- **状态机**: 初始(0) → 已提交(1) → 中心通过(2)/驳回(3) → 业务部通过(4)/驳回(5) → 财务通过(6)/驳回(7) / 取消(8)
- **Service**: `SpAdvanceClearEntityService` — `centerApproval()` / `businessDepartmentApproval()` / `financeApproval()`

### 预付/交款管理
- **状态机**: 初始(0) → 已提交(1) → 交款成功(2)/失败(3) → 审批通过(4)/驳回(5) → 退款成功(6)/失败(7)
- **Service**: `SpAdvancePaymentService` — `receivePayStatus()` 接收服务商收款状态

### 应付账款
- `monthStartAccountsPayableJob()` — 月初统计应付账款定时任务
- `confirmSettle()` — 确认账单
- `saveContractInfo()` / `updateContractInfo()` — 应付账单合同信息管理（DCC 电签）
- `getSignUrl()` — 获取电签链接
- `signCallback()` — 签章回调流程
- `requestPayment()` — 应付账单请款
- `updateSettleStatus()` — 定时更新付款状态

### 应收账款
- `monthStartAccountsReceivableJob()` — 月初统计应收账款定时任务
- `confirm()` — 确认账单
- `signCallback()` — 签章回调流程

### SAP 记账 (repairs 服务)
- **业务类型**: B07=入库记账, B25=领用记账, B23=扣除押金记账(运维商责任), B24=厂家责任记账(供应商责任)
- `addSpSapAccountTranSn()` — 调拨/服务订单新增 SAP
- `addSpSapAccountTranSnDetailSh()` — 货损插销新增 SAP
- `addSpSapAccountOldbackListsDetail()` — 旧件回退作废新增 SAP
- `synchronizationSapAccountJob()` — 同步 SAP 信息定时任务

### 保外收入统计
- `warrantIncomeCountJob()` — 保外收入数据统计定时任务

---

### 业主银行卡变更管理 (代码明确证明 + 前端配置证明)
**后端来源**: `rrsjk-light-service` → `LightStationBankCardChange.java` + `LightBankChangeDto.java` + `LightStationBankCardChangeServiceImpl.java` + Mapper XML (commit f832bee6bb + 后续修复, sunzn, 2026-04-15~22, TAEI-2994 电站业主银行卡信息变更管理)
**前端来源**: `nahui-pv.greenenergy-mini` → `packageB/pages/bankChange/` + `nahui-dicts-serve` → `src/data/osp/merchant/bankInfoStatus.js` 等 (袁睿林, 2026-02)

#### 后端实现
- **实体**: `LightStationBankCardChange` (230行) — 存储银行卡变更记录
  - 关键字段: ownerName, subCenterCode, specialFlag, fieldMethod, signStatus, rentPaymentMode, bankAccount, bankName, bankNo, bankProvinceCode/CityCode/RegionCode, houseBankCode/Name, stationType, old/new bank info, status, workOrderNo
- **DTO**: `LightBankChangeDto` (128行) — 银行卡变更申请数据传输对象
- **DAO**: `LightStationBankCardChangeDao` (46行) + Mapper XML (531行)
- **Service**: `LightStationBankCardChangeService` (79行接口) → `LightStationBankCardChangeServiceImpl` (360行)
  - 核心方法: 申请创建、初审、终审、取消、查询列表、详情
  - **工单集成**: 关联工单系统实现状态联动
  - **OCR集成**: 银行卡图片OCR识别 (commit aa8554f01c)
  - **租金支付模式自动计算**: 根据电站资方属性自动判断
- **前端**: 云管家光伏管理新增银行卡变更管理入口
- **功能流程**: 申请 → 初审 → 终审 → 变更记录列表 → 审核
- **相关数据字典**:
  - `bankInfoStatus.js` — 业主银行卡变更状态
  - `bankBentPaymentMode.js` — 银行卡变更打款模式
  - `bankFieldMethod.js` — 银行卡变更字段方法

### HDS 运维收入导入任务 (前端配置证明, 2026-05-22 扫描)
**来源**: `nahui-dicts-serve` → `src/data/osp/hds/importTaskOperation.js` (李培龙, 2026-04-08)
- 导入任务操作类型:
  - `CONFIRMED` — 确认暂估
  - `CONFIRM_INCOME` — 确认实际
  - `BATCH_COVER` — 批量覆盖（冲销）
  - `ALL_STATION_DETAIL` — 导入电站详情
  - `A48_STATION_DETAIL` — A48导入电站详情（运维政策兑现）
  - `A51_STATION_DETAIL` — A51导入电站详情（暂估记账）
- 导入任务状态: `PROCESSING` 处理中 → `COMPLETED` 已完成 / `FAILED` 处理失败

### 请款申请审核状态 (前端配置证明, 2026-05-22 扫描)
**来源**: `nahui-dicts-serve` → `src/data/apv/finance/purchaseAuditStatus.js` (袁睿林, 2026-04-28)
- 新增请款申请审核状态字典文件（曾被删除后恢复，commit 4e20c548）

### 零碳适家业务模式 (前端配置证明, 2026-05-22 扫描)
**来源**: `nahui-dicts-serve` → `src/data/zch/base/` (袁睿林, 2026-04-17)
- `businessModelTypeList.js`: `LIGHT_STORAGE`=零碳适家-光储, `E_STATION`=零碳E站
- `businessModelStatus.js`: `WAIT_AUDIT`待审核 → `AUDIT_REJECT`审批不通过 → `WAIT_SIGN`待签署 → `ENABLE`已授权

### 运维收入合并收款功能 (代码明确证明, 2026-05-23 补漏第7期)
**来源**: `rrsjk-light-api/.../entity/OperationMaintenance.java`, `rrsjk-light-api/.../entity/OperationMaintenanceSapLog.java` (TAEI-2984, sunzn, commit 2982b61, 2026-04-08)
- `OperationMaintenance` 新增 `allOrderNo` 字段 — 合并收款总单号，将多条运维收入记录合并为一笔收款
- 新增 `OperationMaintenanceSapLog` 实体 — 运维收入管理记账日志表，记录SAP记账凭证、记账状态、凭证号等
- `OperationMaintenanceService.mergeSk(List<Long> ids, String operateBy)` — 合并收款核心方法
- 对应需求: TAEI-2953/2969/2972/2984 (HDS运维收入成本管理系列)

### 暂估电价独立表 (代码明确证明, 2026-05-23 补漏第7期)
**来源**: `rrsjk-light-report-api/.../entity/local/LightEstimateCityElecPrice.java` (TAEI-2959, baoxin, commit daf77a1, 2026-04-08)
- 暂估电价查询从 `LightCityElecPrice` (通用城市电价表) 改为 `LightEstimateCityElecPrice` (独立暂估电价表)
- `LightEstimateCityElecPrice`: id, provinceId, provinceName, cityId, cityName, elecPrice
- 按省市区维度维护暂估电价，河北省硬编码为 0.3644
- `LightEstimateStationServiceImpl` 电价Map构建逻辑变更

### 统众乐道租金支付管理 (代码明确证明, 2026-04-23)
**来源**: `rrsjk-admin-web` → commits by tn_wangb (王斌, 2026-04-23, branch `20260423-wb-tzld`, TAEI-2990 【股转】乐道、统众增加租金支付明细菜单 只能看乐道下项目公司数据 支持导出、导入支付结果)
- CBS新增租金支付明细菜单，仅展示乐道项目公司数据
- 支持导出和导入支付结果功能
- 共享支付明细增加支付状态导入接口 (tn_wangb, 2026-04-14~17, branch `20260414-wb-shareBill`)

### 辅材额度新增页面 (代码明确证明, 2026-04-22)
**来源**: `rrsjk-light-api` → `AuxiliaryMaterialCreditLimitDto.java` + `LightServiceProviderService.java` (commit f7ca3f7916, baoxin, TAEI-2995 【政策】辅材政策切换为辅材额度)
- 新增 DTO `AuxiliaryMaterialCreditLimitDto`: auxiliaryDepositAmount(总额), auxiliaryDepositBalance(可用余额), auxiliaryDepositFreezeAmount(冻结金额), auxiliaryDepositWrittenOffAmount(核销金额)
- Dubbo 接口新增 `getAuxiliaryMaterialCreditLimit(Long memberId)` 方法
- 辅材额度流水类型从 S7→S8 重命名 (commit 741ce0be9b, yumiao)
  - S7 原为下单冻结流水 → 改名为 S8
  - S11 签收时不再更新 pendingWrittenOffAmount (注释掉)
  - D13 核销时不再扣减 pendingWrittenOffAmount (注释掉)
  - 新增快照生成逻辑: snapshotAfterFreeze, snapshotAfterRelease

### 质保金退款新增出款公司 (代码明确证明, 2026-05-21)
**来源**: `rrsjk-finance-service`, commit 9d9fca1 (tn_wangb, 2026-05-21, branch `20260521-wb-depositRefund`)
- 推质保金增加 1QJ0 出款公司
- 影响采购单请款、质保金退款申请流程

### 服务商保证金退款 operatorId 修复 (代码明确证明, 2026-06-01)
**来源**: `rrsjk-light-service` → `LightDepositServiceImpl.java`, commit 25f4c69336 (龙龙, 2026-06-01)
- `LightMerchantDepositChange.setOperatorId()` 从 `Long.valueOf(opUser)` 改为 `null`
- 原因: `opUser` 在退押金场景中可能是服务商名称等非数字字符串，直接 `Long.valueOf()` 会导致 `NumberFormatException`
- 影响: `LightDepositServiceImpl.refundDeposit()` 方法中的保证金变更记录
- 操作人名称(`operatorName`)仍正常记录，仅 `operatorId` 设为 null

### rrsjk-finance-service 核心业务模块速览 (2026-05-24 通读确认)
**来源**: `rrsjk-finance-service` 全量通读

#### 账单与对账模块
- `BillService` — 统一账单服务，支持支付宝/微信/建行/转账汇款等多渠道流水拉取
- `BillAlipayService` / `BillWechatService` / `BillCcbService` / `BillNetPayService` — 各渠道账单查询
- `FinanceJobService` — 财务定时任务集（拉账单、对账、结算汇总、SAP同步等80+任务类型）

#### SAP 集成模块
- `SapFinanceAndOrderService` — SAP采购单请款管理（创建/更新/删除/审核/确认）
- `SapRecordService` — SAP总账记账、系统发票号获取
- `SapPurchaseRecordService` — SAP采购单CRUD，含VPP系统专用接口 `createForVpp()`
- `LightIncomeRecordService` — 光伏收入SAP记账（辅材押金、运维保证金、备件款、零碳保证金、电费月汇总等）
- `JinDieSapRecordService` — 金蝶SAP记录（股转公司电费收益收入记账）
- `DepositRecordService` — 质保金管理（推送SAP、更新发票凭证、历史数据处理）
- `LightSapJobService` — 光伏SAP定时任务集（总账记账、能源币记账、冲销、发票归档等）

#### 请款与结算模块
- `PurchaseApplySettleService` — 请款申请单管理
- `PurchaseApplySettleDepositRefundService` — 质保金退款申请/审核/支付
- `PurchaseApplySettleNoPaperService` — 无纸化请款（含运维请款）
- `PurchaseApplySettleQuotaAuditService` — 预算额度审核（市场部长→技术→供应链→小微主四级审核）
- `PurchaseApplySettleAttachmentService` — 请款单附件上传管理（定时推送影像）
- `PurchaseApplySettleDeductionService` — 应付扣除生成与记账

#### 账户额度管理
- `PayAccountQuotaConfigService` — 出款账户配置（创建/修改/冻结/解冻/作废）
- 额度占用: `occupy(payCompany, payBankAccount, payType, occupyAmount, applyNo)`
- 每日额度占用报表定时任务: `payAccountQuotaReportJob()`
- 默认支付方式配置: `setDefaultPayType()`

#### 发票校验 (UPP)
- `InvoiceCheckService` — 发票校验信息管理（批量OCR识别、票验平台查询/占用/释放）
- `InvoiceCheckUppService` — UPP票验平台对接（OCR→状态查询→发票占用→释放）
- `UppRecordService` — UPP调用记录

#### 云报账 (YBZ)
- `YbzRecordService` — 云报账出款申请/查询定时任务
- `LightRentPaymentRecordService` — 租金支付请求云报账/查询结果/回调

#### 第三方店铺结算
- `SettlementThirdOrderItemCommissionService` — 第三方店铺分佣结算
- `SettlementThirdOrderItemCommissionDailySumService` — 第三方店铺结算日汇总
- `CustomRebateThirdService` — 第三方店铺返款明细
- `CashThirdOrderService` — 第三方店铺提现客户日汇总

#### 海尔招聘财务
- `HaierRecruitPayDetailService` — 订单收款明细（关联采购单、确认收款、开发票）
- `HaierRecruitSettleDetailService` — 订单结算明细
- `HaierRecruitXsSummaryService` — 小顺佣金汇总/返款

#### 客户与额度管理
- `MdrCustomerService` — MDR客户信息（建户查询、APP下单校验、额度更新、快递白条）
- `MdrCustomerContractService` — MDR客户合同录入
- `MdrCustomerOrderDetailsService` — MDR客户订单/逾期订单查询
- `MdrFinancialSolutionsService` — MDR客户金融解决方案
- `CreditCustomerService` — 360客户信息查询
- `CustomerFinanceService` — 根据法人公司编码和税号查询逾期金额

#### 定时任务类型 (TaskType, 81种)
覆盖：创建任务、更新凭证、结算汇总、SAP同步、支付宝/微信/建行/银联对账、MPC/GTMS返款、MDR客户拉取、UPP发票核销、海尔招聘对账、云智妆对账等

### SAP 记账 xref3 字段变更 — 电站编码替代 bid (TAEI-3076, 2026-05-12)

**来源**: `rrsjk-light-service` (解钦, commit: 72283a8, 2026-05-12)
**代码明确证明**

**变更**: SAP 记账时 `xref3` 字段从传 `bid`（业务ID）改为传 `stationCode`（电站编码）。

**涉及服务**（全部为各资方收入结算服务）:
- `HuaRongTradeIncomeSettleServiceImpl.java` — 华融
- `LightYuexiuSettleModel.java` — 越秀
- `PuYinSettleQueueJobServiceImpl.java` — 普音
- `ZhaoYinTradeIncomeSettleServiceImpl.java` — 招银
- `ZhongYinTradeIncomeSettleServiceImpl.java` — 中银

**旧代码**: `sapItemRecord.setXref3(bid);`
**新代码**: `sapItemRecord.setXref3(huaRongTradeIncomeSettle.getStationCode());`

**业务含义**: xref3 是 SAP 记账凭证的参考字段，用于关联业务单据。改为电站编码后，SAP 侧可以通过电站编码直接追溯光伏电站的收入记录，提升了业务可追溯性。

### 共享支付账单查询 — 后端实现 (TAEI-3086, 2026-05-11~05-14)

**来源**: `rrsjk-light-service`, `rrsjk-light-operation-service`, `rrsjk-hds-web` (孙志男, 2026-05-11~05-14)
**代码明确证明**

**变更**: 租金账单明细查询新增 `source=4` 分支，支持共享账单记录查询。

**涉及文件**:
- `LightRentServiceImpl.java` — 新增 `LightShareBillRecordDao` 注入，`source=4` 时调用共享明细查询
- `LightShareBillRecordDao.java` — 新增 `countOfDetail()` 和 `findByDetail()` 方法
- `LightShareBillRecord.xml` — 新增 UNION ALL 查询支持共享账单记录

**查询参数**: `stationCode` + `payDate`（支付日期范围筛选）

**共享支付查询参数修复** (TAEI-3080, 2026-05-14):
- `e82b223`: 修复共享支付查询参数传递错误
- `e08e2d3`/`01411e2`: 修正共享支付查询中的租用月份参数
|- `30d657e`: 优化共享账单记录查询逻辑

### 金蝶SAP BUKRS字段映射修复 (代码明确证明, 2026-05-26)
**来源**: `rrsjk-finance-service` → `JinSapClientModel.java` (commit e44ebe80, mabin, 2026-05-26)
- `financeInputTransferNew()` 方法中新增规则: 当 `header_item.getBUKRS()` 为 `"7CQ0"` (忽略大小写) 时，替换为 `"9002"`
- **业务含义**: 7CQ0 公司代码在金蝶SAP记账时需要映射到 9002，解决BUKRS字段映射错误导致记账失败的问题
- **证据等级**: 代码明确证明

### 对账单update方法判空改造 (代码明确证明, 2026-05-26)
**来源**: `rrsjk-finance-service` → `PurchaseApplySettleMapper.xml` (commit cdc415b8, yumiao, 2026-05-26)
- update SQL 从全字段SET改为 MyBatis `<set>` + `<if test="field != null">` 动态更新模式
- 62行变更: 67行删除(全量更新) → 62行新增(动态更新)
- **影响**: 防止null值覆盖已有数据，部分字段更新时不会将未传字段置空
- **涉及表**: `purchase_apply_settle` (请款结算表)
- **证据等级**: 代码明确证明

### 商品类型新增"高端场景工程安装" (代码明确证明, 2026-05-25)
**来源**: `rrsjk-admin-web` → `finance/self/purchaseApplyConfirm.ftl` (commit 9b2ff71f, 代继宁, 2026-05-25)
- 财务自助请款确认页面新增商品类型选项
- **证据等级**: 配置明确证明

### 零碳适家企业客户押金结算 (代码明确证明, 2026-05-27 全量通读第14轮)
**来源**: `rrsjk-merchant-service` → `CorporateClientDepositServiceImpl.java` + `CorporateClientDepositDao.java`
- 零碳适家企业客户需缴纳保证金(sourceFlag=2, companyCode="1QJ0")
- **押金状态**: WAIT(待确认) → CONFIRMED(已确认收款)
- **对账状态**: NO(未对账) → YES(已对账)
- **确认收款流程**: 更新支付信息 → 状态改为 CONFIRMED → 事务内累加 corporate_client.deposit → 转账渠道触发 SAP 记账
- **SAP 记账**: 调用 FinanceIncomeModel.corporateClientDepositToSap() (Dubbo)，失败不影响收款确认
- **防重复**: 检查 account_status=YES 或 account_voucher 非空
- **涉及表**: `corporate_client_deposit`, `corporate_client`

### 华融质保金收入管理 Admin Controller (代码明确证明, 2026-05-27 增量扫描)
**来源**: `rrsjk-admin-web` → `HuaRongIncomeQualityGuaranteeController.java`, `HuaRongIncomeQualityGuaranteeExcel.java` (commit c48f8260, yumiao, 2026-04-28 分支合并至master 2026-05-27)
- **路径**: `/huaRongIncomeQualityGuarantee/*`
- **权限**: 复用 `huaRongTradeIncomeSettle:*` 权限点
- **功能**:
  - `list.html` — 华融收入质保金列表页面
  - `doList.do` — 分页查询(批次号、电站编码、姓名、房屋类型、业务名称、确认日期范围)
  - `downTemplate.do` — 下载导入模板(批次号,电站编码,质保金比例)
  - `importData.do` — Excel导入质保金数据，校验: 批次号非空、电站编码非空、质保金比例>0且<1(如2%填0.02)
  - `doExport.do` — 导出华融收入质保金结算表(EasyExcel, 每页3000条)
  - `countBatch.do` — 按批次号统计: 电站数量 + 质保金总额
  - `confirm.do` — 按批次确认上收入(`HuaRongIncomeQualityGuaranteeService.confirmIncome`)
  - `delete.do` — 按批次删除未确认数据
  - `reverse/downTemplate.do` — 下载冲销模板(仅电站编码)
  - `reverse/importData.do` — 批量冲销: 校验FINISH状态记录 → 查找sap_record记账信息 → 调用`syncFinanceToSapService.reverseFinanceToSap()` → 执行`reverseAfter()`后处理
- **实体**: `HuaRongIncomeQualityGuarantee` (含 StatusEnum.FINISH 状态)
- **关联**: `rrsjk-light-service` → `HuaRongIncomeQualityGuaranteeService`(B43模式质保金服务)
- **证据等级**: 代码明确证明

### 金蝶凭证过账冲销流程改造 (代码明确证明, 2026-05-27 增量扫描)
**来源**: `rrsjk-finance-service` → `JinDieSyncFinanceModel.java`, `JinSapClientModel.java` (commits: mabin 9b888ae4, f4bf864a, 2026-05-27)
- **核心变更**: `reverseFinanceToSap()` 冲销流程改造为先过账再冲销
  - 新增调用 `jinSapClientModel.postingVoucherForReverse(rowId, record)` 
  - 过账成功(`postResult=true`)后才执行 `syncFinanceToSap(record)` 冲销
  - 过账失败则记录错误日志，不执行冲销
- **新增接口**: `postingVoucherForReverse(String rowId, KingDieSapRecord sapRecord)`
  - 请求参数: `{"data": {"xfd6_row_id": rowId}}`
  - 调用金蝶过账接口 `postVoucherUrl` (配置项 `kingdie.postVoucherUrl`)
  - 返回 `true`(errorCode="0")或 `false`(记录错误信息)
- **防溢出修复**: `syncFinanceToSap()` 异常处理中限制 `message` 长度≤199字符，防止数据库字段溢出
  - 影响 `JinSapClientModel.syncFinanceToSap()` 和 `postingVoucherForReverse()` 的 BusinessException/Exception 分支
- **日志优化**: `JinDieSapRecordServiceImpl.stockTransElecOrderIncomeToJinDie()` 日志中 `orderId` 替换为 `lightProjectElectricOrder.getOrderNo()`
- **涉及配置**: `application-dev.yml`, `application-prod.yml` 新增 `kingdie.postVoucherUrl`
- **证据等级**: 代码明确证明

### 农户租金个税报表及记账 (TAEI-3092, 代码明确证明, 2026-05-25~27)
**来源**: `rrsjk-light-service` + `rrsjk-admin-web` + `rrsjk-trade-service` (代继宁, 10+ commits, branch: origin/featrue-20260525-rentTaxReport/TAEI-3092)
- **需求**: 杨越越负责，参与人: 代继宁、薛荣基
- **新增实体**（1710行代码）:
  - `RentTaxAmountRecord` — 租金个税明细记录
  - `RentTaxAmountSummary` — 租金个税汇总
  - `TaxAmountCalculateSourceData` — 个税计算源数据
- **新服务**: `RentTaxAmountService` — 租金个税计算与报表服务（441行实现）
- **报表功能**: 租金个税明细页面、查询列表、合计导出优化
- **SAP记账**: 财务确认后发SAP接口
- **前端**: `rrsjk-admin-web` 增加租金个税明细/合计页面及查询列表
- **涉及表**: `rent_tax_amount_record`, `rent_tax_amount_summary`, `tax_amount_calculate_source_data`
- **证据等级**: 代码明确证明

### 金蝶冲销接口补充优化 (TAEI-3157, 代码明确证明, 2026-05-27)
**来源**: `rrsjk-light-service` + `rrsjk-finance-service` (mabin, 6+ commits, branch: origin/20260527-jindieFix)
- **放开发票冲销**: `ProjectElectricInvoiceReverseRecordServiceImpl` 冲销逻辑调整
- **回调修复**: `dealJinDieA02PayWithOldFapCallback` 方法改为传订单号，处理前重新查询订单
- **SAP BUKRS修复**: 金蝶SAP客户端BUKRS字段映射问题解决
- **SAP订单号日志**: orderId参数替换为orderNo显示

### 金蝶凭证过账功能 (代码明确证明, 2026-05-27)
**来源**: `rrsjk-finance-service` (mabin, commit f4bf864, branch: origin/20250525-jindieRepeatFix)
- **JinDieSyncFinanceModel**: 实现过账验证逻辑，先调用过账接口再执行冲销
- **JinSapClientModel**: 新增 `postVoucherUrl` 配置注入，新增 `postingVoucherForReverse` 方法
- **配置**: `application-dev.yml` / `application-prod.yml` 新增 `kingdie.postVoucherUrl`
- **证据等级**: 代码明确证明

### 租金个税报表(TAEI-3092) 持续推进 (2026-05-28 追加)
**来源**: `rrsjk-light-service` + `rrsjk-admin-web` (代继宁, 5+ commits, branch: origin/featrue-20260525-rentTaxReport/TAEI-3092)
- **RentTaxRecordController** (rrsjk-admin-web): 新增Controller，提供租金个税明细/合计页面查询和记账按钮显示逻辑
- **TaxAmountCalculateSourceDataTemp**: 新增中间临时表实体+DAO+Mapper，用于批量任务分批处理优化
- **RentTaxAmountServiceImpl**: 确认记账接口逻辑更新
- **LightShareJobServiceImpl**: 定时任务执行月份计算公式修正
- **RentTaxAmountSummary**: 汇总实体字段更新
- **前端页面**: `rentTaxAmountRecordList.ftl` (明细列表), `rentTaxAmountSummaryList.ftl` (合计列表)
- **导出VO**: `RentTaxAmountRecordExcel`, `RentTaxAmountSummaryExcel`
- **证据等级**: 代码明确证明

### 华融上收入多1个账 (TAEI-3044, 代码明确证明, 2026-05-26)
**来源**: `rrsjk-finance-service` (yumiao/于淼, commit cdc415b)
- **需求**: 华融上收入时再多1个账，业务模式B43，DMBTR=收入金额(应收账款)*质量保证金比例
- **变更**: 对账单update方法增加判空校验
- **关联**: 于淼负责，参与人: 薛荣基
- **状态**: 已完成
- **证据等级**: 代码明确证明（需进一步追踪 B43 业务模式下的质量保证金记账逻辑）

### 工商业风电项目终验法 (TAEI-3107, 代码明确证明, 2026-05-22~27)
**来源**: `rrsjk-admin-web` (tn_wangb/王斌, branch: origin/feature-cm-wind-electric)
- **需求**: 风电产值法兼容1.0，杨越越负责，参与人: 王斌、解钦、杨辉、薛荣基
- **核心变更**: 工商业项目领用报表从4个独立比例字段合并为1个节点完成比例
  - 移除: `majorMaterialUsePct` (领用主材比例), `auxiliaryMaterialUsePct` (领用辅材比例), `constructionServiceUsePct` (施工服务领用比例), `designServiceUsePct` (设计领用比例)
  - 新增: `nodeFinishPct` (本次节点比例)
  - Excel 导出列名从"领用主材比例"改为"本次节点比例"
- **收款切换**: 工商业收款从旧模式切换为 FAP 模式 (`5173171`, 2026-05-22)
- **发票核销**: 无纸化列表补充发票已核销状态 (`9b6f0a4`, 2026-05-27)
- **状态**: 测试中
- **证据等级**: 代码明确证明

### 租金个税报表SAP记账状态与批量确认优化 (TAEI-3092, 代码明确证明, 2026-05-28~29)
**来源**: `rrsjk-light-service` + `rrsjk-admin-web` (代继宁, branch: origin/featrue-20260525-rentTaxReport/TAEI-3092)
- **SAP记账状态追踪**: `RentTaxAmountSummary` 新增 `syncSapStatus` (记账状态) 和 `sapSentResult` (记账失败原因) 字段
- **记账成功后清理**: SAP记账成功后将 `sapSentResult` 置空（commit e1861c71）
- **批量确认接口优化**: `RentTaxRecordController.batchConfirmRecord()` 简化返回结构，统一使用 `ExecuteResult.newSuccessResult()`，区分成功/失败列表
- **前端记账按钮**: `rentTaxAmountSummaryList.ftl` 记账按钮文案改为"批量确认记账"，增加"记账状态"和"记账失败原因"列
- **失败重试**: 记账状态为 `WAIT` 或 `FAIL` 时均可再次点击记账
- **SAP记账接口**: 交易类型等传参多次迭代修改（commit fd26cff/c2d171bb/009ea421）
- **错误信息**: 批量确认错误从 `result.getMessage()` 改为 `result.getError()`
- **证据等级**: 代码明确证明

### 金蝶冲销接口优化 (TAEI-3157, 代码明确证明, 2026-05-27)
**来源**: `rrsjk-light-service` (mabin/马斌)
- **放开发票金蝶冲销**: `payment` 模块修复放开发票金蝶冲销逻辑（commit 4ee999f3）
- **金蝶收款记账回调**: 修复订单查询问题（commit 558367d2）
- **FAP回调优化**: 优化FAP回调处理逻辑并添加线程池配置（commit e7fc4302）
- **证据等级**: 代码明确证明

### 金蝶冲销接口补充优化 (TAEI-3157, 代码明确证明, 2026-05-28 追加)
**来源**: `rrsjk-finance-service` (mabin/马斌, branch: origin/20250525-jindieRepeatFix)
- **SAP同步日志修复**: `orderId` 替换为 `lightProjectElectricOrder.getOrderNo()`（commit 5d31ec4c）
- **消息长度限制**: 限制金蝶SAP同步消息长度防止数据库字段溢出（commit 9b888ae4）
- **重复校验优化**: 解决金蝶SAP同步中的重复校验和错误处理问题（commit beadf50/c233685）
- **异常处理**: 优化金蝶SAP同步财务记账接口异常处理（commit e7e2c37）
- **证据等级**: 代码明确证明

### SAP 收入重传修复 (2026-05-30)
**来源**: `rrsjk-finance-service` → `rrsjk-finance-impl/src/main/java/com/rrsjk/finance/sap/component/income/SyncSapIncomeHandle.java`
**Commit**: 479ab28b/bc30a632, 开发者: baoxin, 2026-05-30
- `SyncSapIncomeHandle` 收入重传逻辑修复（commit message: "fix:重传收入"）
- 涉及 SAP 收入同步处理组件的收入数据重传场景
- **证据等级**: 历史扫描推断（diff 未展示具体代码变更，仅从 commit message 和变更文件推断）

### 发票重传修复 (2026-05-30)
**来源**: `rrsjk-trade-service` → `rrsjk-trade-impl/src/main/java/com/rrsjk/trade/invoice/model/CloudInvoiceCreateModel.java`, `CloudInvoiceQueryModel.java`
**Commit**: fc0502ec, 开发者: baoxin, 2026-05-30
- `CloudInvoiceCreateModel`/`CloudInvoiceQueryModel` 发票重传逻辑修复（commit message: "fix:重传发票"）
- 与 `SyncSapIncomeHandle` 同开发者同一天提交，可能为关联修复
- **证据等级**: 历史扫描推断（diff 未展示具体代码变更）

### FAP凭证集成与补偿机制 (TAEI-3021/TAEI-3022, 代码明确证明, 2026-05-18~24)
**来源**: `rrsjk-light-service/LightFapRecordServiceImpl.java`, `rrsjk-trade-service`, `rrsjk-admin-web`, `rrsjk-merchant-web` (代继宁)
**需求**: TAEI-3021 零碳适家保证金/订单收款接FAP, TAEI-3022 绿证交易订单收款接FAP
- **核心实体**: `LightFapRecord` — FAP凭证记录表 (rrsjk_light库)
- **凭证补偿机制**: 新增物料回购、站点回购、服务押金等多种业务类型的补偿处理 (`34fc750e`, +137行)
- **补偿状态移除**: 从 `LightFapRecord` 实体删除补偿状态枚举及字段 (`0e7e2f5e`, -54行)
- **实时查询**: 新增 `queryFapInfoFromFapSys()` 方法从FAP系统实时查询制证状态
- **取消逻辑优化**: 增加状态检查和本地标记机制，防止重复取消 (`dd2ef5c8`)
- **批量处理**: FAP推送和查询定时任务增加批量处理和异常处理
- **业务类型识别**: `isCancelProneBizType()` 识别易取消业务类型
- **前端支持**: admin-web 新增 FAP收款记录导出、状态显示修复
- **订单同步**: trade-service 移除未使用的FAP同步查询方法，新增凭证更新日志
- **⚠️ 风险**: 旧补偿逻辑已完全移除，新实时查询机制需验证覆盖所有补偿场景
- **涉及Service**: LightFapRecordService, LightSpOrderItemDao, rrsjk-trade-service订单项目同步
- **证据等级**: 代码明确证明

### 资方结算服务性能优化 (TAEI-3085, 代码明确证明, 2026-05-19)
**来源**: `rrsjk-light-service` (解钦) — 8个资方结算ServiceImpl
**需求**: TAEI-3085 增加上收限制
- **优化方式**: `Assert.isTrue(msg)` → `Assert.isTrue(() -> msg)` (eager字符串拼接改为lazy Supplier)
- **涉及Service**: HuaRongTradeIncomeSettleServiceImpl, LightFundSettleServiceImpl, LightHdIncomeServiceImpl, LightStationYuexiuSettleServiceImpl, LightZhSettleServiceImpl, PuYinTradeIncomeSettleServiceImpl, ZhaoYinTradeIncomeSettleServiceImpl, ZhongYinTradeIncomeSettleServiceImpl
- **影响**: 避免断言通过时的无谓字符串拼接，提升批量导入性能
- **证据等级**: 代码明确证明

### 工商业收款 cancel 作废接口 (2026-06-04 合并到 master)
**来源**: `rrsjk-admin-web` → `CmLightProjectReceiptController.java` (分支 preProd_20260416-FapRecordOfReceipts 合并)
**证据等级**: 代码明确证明
- **新增接口**: `POST /cmLightProjectReceipt/cancel.do`
- **权限**: `cmLightProjectReceipt:add`
- **入参**: `Long id`, `HttpServletRequest`
- **调用**: `cmLightProjectReceiptService.cancel(id, user)`
- **业务影响**: 工商业收款记录支持独立作废操作，此前仅有 create/update/delete/audit/confirmReceipt
- **注意**: delete 与 cancel 的区分逻辑待确认（可能 delete 是物理删除，cancel 是状态变更）

### FAP 回调与现金自订单集成 (2026-04~06 持续迭代)
**来源**: `rrsjk-finance-service` → `CashSelfOrderItemService.java` / `CashSelfOrderItemServiceImpl.java` / `SyncSapHandleSelf.java` (commits by 代继宁/mabin, 2026-04~06)
**证据等级**: 代码明确证明

- **新增接口**: `CashSelfOrderItemService.createCashSelfOrderItemForFapCallBack(Orders, OrderItem)` — FAP 回调时自动创建现金自订单项目
  - 逻辑: 检查 `isExist(orderItemId, BillType.PAYMENT)` → 不存在则调用 `selfPaymentCheck.createCashSelfOrderItem()`
  - 依赖: rrsjk-finance-api 新增对 rrsjk-trade-api 的依赖（引入 `Orders`/`OrderItem` 实体）
- **新增方法**: `updateCashSelfOrderItemByOrderItemNo(CashSelfOrderItem)` — 按 orderItemNo 更新（此前只能按 id 更新）
  - Mapper: `CashSelfOrderItem.xml` 新增 `<update id="updateByOrderItemNo">`
- **新增 ServiceError 枚举**: `SYNC_TO_FAP("syncToFap", "同步FAP")` — 标记 FAP 同步服务的错误记录
- **业务影响**: FAP 回调流程现在可以自动创建现金自订单记录，打通 FAP→财务对账链路
- **关联**: `SelfPaymentCheck` 组件负责实际的现金自订单创建逻辑
