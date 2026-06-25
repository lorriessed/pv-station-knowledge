# 云效驱动代码学习报告 — 2026-06-25

## 扫描范围
- 云效需求: 20 个（近期更新） | 涉及人员: 20+ | Git 提交: 198 个
- 扫描窗口: 2026-06-23 ~ 2026-06-25
- 涉及仓库: 14 个（rrsjk-light-service 67, rrsjk-admin-web 31, rrsjk-light-report-service 23, app_aiwork_flutter 13, ...）

## 知识覆盖分析

| 需求号 | 标题 | 图谱覆盖情况 | 学习深度 |
|---|---|---|---|
| TAEI-3218 | SAP确认收款记账凭证信息调整 | ✅ 已覆盖(Domain:结算/FAP) | 增量更新 |
| TAEI-3207 | HDS/电费管理：新增电费报表(电站) | ✅ 已覆盖(Domain:工商业) | 增量更新 |
| TAEI-3190 | 营销政策预测报表三期重构 | ✅ 已覆盖(Domain:政策) | 已有五期记录 |
| TAEI-3044 | 华融上收入多1个账 B43 | ✅ 已覆盖(Domain:结算/SAP) | 增量更新 |
| TAEI-3168 | 零碳适家退商材料申请流程 | ✅ 已覆盖(Domain:零碳) | 状态追踪 |
| TAEI-3280/3281/3282/3289 | 马金虎发电管理系列 | ✅ 已覆盖(Domain:发电数据) | 状态追踪 |

## 核心业务变更

### 1. FAP回调注销金蝶记账处理
- **来源**: rrsjk-light-service → LightProjectElectricOrderServiceImpl.java (tn_wangb, 416c930e)
- **变更**: 注释掉 `dealJinDieA02PayWithOldFapCallback` 调用
- **影响**: FAP回调不再触发金蝶A02收款记账，FAP与金蝶记账进一步解耦

### 2. 自持电站损益报表成本取数重构
- **来源**: rrsjk-light-service → CmOwnerStationReportServiceImpl.java (tn_wangb, f29bacff)
- **变更**: 成本从单表LightSpOpsSettleIac改为3表联合(OperationSettlementData + PositiveIac + NegativeIac)
- **新增**: 价税分离(÷1.06)、月中月初定时刷新历史数据

### 3. TAEI-3190 三期重构（已记录为"五期"）
- **来源**: rrsjk-light-report-service → ReportPolicyForecastServiceImpl.java (龙龙, 172fa6cdd)
- **变更**: 维度来源改为light_company_policy，房型行按有值生成，租金4列/辅材费按房型区分

### 4. 电网奖励订单采购功能
- **来源**: rrsjk-light-service → LightSapServiceImpl.java (龙龙, f7164cae)
- **变更**: 新增 lightSpGridAwardMakePurchase 方法，复用 spBwAndInstallRequestFund 请款流程

### 5. EventBus线程池监控 + 连接泄漏检测超时调整
- **来源**: rrsjk-light-service (lilong)
- **变更**: 增加EventBus线程池监控日志，连接泄漏检测超时30min→1h

## 风险预警

1. **FAP金蝶记账路径停用**: 需确认新SAP记账路径(TAEI-3218)已完全替代
2. **自持电站成本计算大改**: 3表联合数据一致性需验证，价税分离精度需财务确认

## 知识库更新
- `domains/cm-business.md`: 新增自持电站损益报表成本取数逻辑重构记录
- `domains/settlement.md`: FAP回调金蝶记账已记录（前次扫描）
- `domains/policy.md`: TAEI-3190五期已记录（前次扫描）

## AI编码占比
- TAEI-3168 零碳退商: 96% (代继宁)
- TAEI-3207 HDS电费报表: 85% (孙志男)
- TAEI-3044 华融B43: 70% (于淼)
- TAEI-3281/3280 发电管理: 50% (马金虎)
- TAEI-3263 商城订单: 40% (包鑫)
