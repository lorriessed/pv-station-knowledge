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
- 新增 `SyncSapDeliverHandle` (2026-04-23)
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

## 待确认
- CM 共享账单完整审批流。
- SAP A88、A92 等凭证业务含义和资方差异。
- 越秀A88流程屏蔽的原因和恢复计划。
- 零碳适家结算中预算占用失败后的重试机制。
- 云报账回调处理逻辑和支付结果同步机制。
- 各资方收入结算时xref3字段传递电站编码的具体用途。
- **工商业自持电站损益报表完整数据流**: 充电桩数据从"于川清大数据库"获取的具体接口和表结构。
- **电站收入上收限制的8种模式**: 每种模式的收入表、校验逻辑、冲突处理规则。

## 来源
- Hermes MEMORY.md，2026-05-09 迁移。
- rrsjk-finance-service 代码扫描 2026-05-10。

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
