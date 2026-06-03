# 云效驱动代码学习报告 — 2026-06-03

## 扫描范围
- **云效需求**: 27 个（updateStatusAt >= 2026-05-27）
- **涉及开发人员**: 16 人（代继宁、马斌、王斌(tn_wangb/龙龙)、马金虎、解钦、李龙、laowang/王金浩、包鑫、李培龙、张硕文、杨辉、魏秋阳、孙志男、于淼、德(syj)、sunzn）
- **Git 提交**: 921 条（含 BFF 层约 423 条噪音）
- **核心业务提交**: ~498 条（排除 BFF 后）

## 需求 → 代码关联（今日新增/更新）

| 需求号 | 标题 | 负责人 | 实际开发 | 相关提交数 | 涉及仓库 | 状态 | 今日变化 |
|---|---|---|---|---|---|---|---|
| TAEI-3168 | 零碳适家退商材料申请流程 | 刘艺 | **代继宁** | 5 | light-service | 阻塞 | ⚠️ 核心逻辑开始开发 |
| TAEI-3023 | 经营性租赁回款接FAP | 刘艺 | **代继宁** | 4 | light-service | 开发中 | 🆕 新增提交 |
| TAEI-3079 | 电费收益相关优化 | 徐晓凤 | **laowang/tn_wangb** | 5 | light-service | 测试中 | 🆕 新增提交 |
| TAEI-3174 | 10户业主变更开通二类卡 | 高媛 | **解钦** | 2 | light-service | 测试完成 | 🆕 新增提交 |
| TAEI-3173 | 招商中标与运维入驻 | 高媛 | 魏秋阳/孙志男 | - | admin-web, light-data-service | 测试完成 | 持续开发 |
| TAEI-3102 | CBS招投标流程 | 刘艺 | laowang | 7 | light-service | 测试完成 | 🆕 重复校验2.0 |
| TAEI-3089 | A端政策结算逻辑调整 | 杨越越 | **龙龙(王斌)** | 2 | light-service | 测试完成 | 🆕 批处理重构 |
| TAEI-3157 | 金蝶冲销接口优化 | 马斌 | 马斌 | 9 | finance-service | 已完成 | 凭证过账功能 |
| TAEI-3005 | 金蝶总账接口开发 | 杨越越 | 马斌/包鑫 | 10 | finance-service, light-report-service | 测试完成 | 报表修改 |
| TAEI-3146 | 发电数据取数切换大数据 | 于淼 | 马金虎 | 15 | light-data-service | 开发中 | ADS迁移持续 |

## 重点业务链分析（今日新增）

### 1. TAEI-3168 零碳适家退商材料 — 核心逻辑开始（重大进展）
**开发**: 代继宁 | **提交**: 40cd05611e | **分支**: origin/20260601-zeroCarbonMerchantQuit/TAEI-3168

**完整业务链**：
```
零碳服务商退商流程:
  1. 调用 withdrawalCheck(spId) — Dubbo接口, ZeroCarbonServiceProviderService
     ├─ 检查未签收采购订单 → light_zero_carbon_purchase_order → 阻塞(blockMsg)
     ├─ 检查未结算安装费 → light_zero_carbon_installation_fee → 阻塞(blockMsg)
     └─ 检查未消耗库存 → light_zero_material_manage.countOfUnUseStockBySpu → 警告(warnMsg, 提示5秒)
  2. 返回 ZeroCarbonSpWithdrawalCheckResult(pass/blockMsg/warnMsg)
  3. 外部依赖: ZeroCarbonInstallBillService (finance-service Dubbo)
```

**关键变更**：
- 新增 DTO: `ZeroCarbonSpWithdrawalCheckResult` (rrsjk-light-api)
- 新增 Dubbo 接口: `withdrawalCheck(spId)`
- 新增 DAO 方法: `findDistinctOrderNos()`, `countOfUnUseStockBySpu()`
- **涉及 3 张核心表**: `light_zero_carbon_purchase_order`, `light_zero_carbon_installation_fee`, `light_zero_material_manage`

### 2. TAEI-3023 经营性租赁回款接FAP — FAP状态同步解耦
**开发**: 代继宁 | **分支**: origin/20260602-fapPart2

**变更核心**：
- `LightFapRecordServiceImpl` 中**注释掉**经营性租赁资产FAP状态同步：
  - `syncOperationalAssetFapSentStatus()` — 不再更新FAP发送状态
  - `syncOperationalAssetFapResult()` — 不再FAP查询结果自动确认
- `service.xml` 新增 Dubbo 引用: `operationalAssetManagementService` → `com.rrsjk.report.service.OperationalAssetManagementService`
- **推断**: FAP同步逻辑正在迁移到 `OperationalAssetManagementService`，当前暂时禁用旧路径
- **风险**: 注释掉同步逻辑可能导致FAP状态不一致，需确认新服务何时启用

### 3. TAEI-3079 电费收益相关优化 — FAP取消状态批量更新
**开发**: laowang(tn_wangb/王金浩)

**变更**：
- `LightProjectElectricOrder.xml`: 批量更新 `fap_cancel_status` 字段（CASE WHEN 模式）
- `CmLightProject.java`: 工商业电站写入工商业项目编码
- `LightSpOrder` 分支: SAP取主数据逻辑优化（不判断物料状态）

### 4. TAEI-3174 二类卡变更 — 越秀开户硬编码修复
**开发**: 解钦 | **提交**: e6fdd675a4

**变更**：`LightStationYuexiuAccountServiceImpl` 中新增手机号→项目公司硬编码映射：
- 10个手机号 → `lessorCode=3093`（广州越晖光伏科技有限公司）
- 4个手机号 → `lessorCode=3390`（郑州华耀顺绿色新能源有限公司）
- **风险提示**: 硬编码方式不灵活，后续需改为配置化

### 5. TAEI-3089 A端政策结算 — 批处理重构
**开发**: 龙龙(王斌) | **提交**: 3e7fd0baa8

**核心变更**：
- 政策收入处理器从 `AbstractPolicyIncomeHandler` → `AbstractPolicyBatchIncomeHandler`
- 新增批处理方法: `reverseIncomeSapRecord()`, `findByOrderNo()`, 批量查询方法
- `LightStationEnableReward.xml` 新增 22 行批量查询 SQL
- **关联修复**: `ed4cec51d5` — 方案变更时营销政策回退兼容负向正常政策奖励

### 6. TAEI-3102 CBS招投标 — 重复校验2.0 + 审核状态修复
**开发**: laowang/王金浩

**变更**：
- `TenderManagmentAuditServiceImpl`: 项目名称重复校验 2.0
- 修复审核状态及日志记录逻辑 (commit 9fd1d414)
- 修复待提交状态误生成审核日志 (commit 87219c04)

### 7. TAEI-3157/3005 金蝶接口 — 凭证过账功能
**开发**: 马斌 | **分支**: origin/20250525-jindieRepeatFix

**关键变更**：
- 新增金蝶凭证过账功能: `postingVoucherForReverse()` — 先过账再冲销
- 新增 `postVoucherUrl` 配置
- SAP同步: 日志 orderId → orderNo, 消息长度限制防溢出
- `rrsjk-light-report-service`: 财务报表修改同期逻辑、容量取数源修改

## 知识覆盖分析

### 已覆盖（图谱已有，今日增量更新）
| 需求号 | 标题 | 图谱覆盖情况 | 今日学习深度 |
|---|---|---|---|
| TAEI-3168 | 零碳退商材料 | ✅ 已有零碳域知识 | 新增核心退商校验逻辑 |
| TAEI-3023 | FAP经营性租赁 | ✅ 已有FAP体系知识 | 新增解耦/迁移模式 |
| TAEI-3079 | 电费收益优化 | ✅ 已有电费域 | 新增fap_cancel_status批量更新 |
| TAEI-3089 | A端政策结算 | ✅ 已有政策域 | 新增批处理重构 |
| TAEI-3102 | CBS招投标 | ✅ 已有招投标域 | 新增重复校验2.0 |
| TAEI-3146 | 发电数据切换 | ✅ 已有ADS迁移 | 持续ADS报表新增 |
| TAEI-3092 | 租金个税报表 | ✅ 已有结算域 | 代继宁持续开发 |

### 未覆盖/需关注
| 类型 | 名称 | 原因 |
|---|---|---|
| 业务风险 | TAEI-3023 FAP同步解耦 | 注释掉同步逻辑，新服务未启用，可能导致状态不一致 |
| 代码质量 | TAEI-3174 手机号硬编码 | 14个手机号硬编码在代码中，需改为配置化 |
| 需求 | TAEI-3125/3126 商户通自定义+图片旋转 | 袁睿林零提交，待确认是否已合入 |

## 知识库更新

| 文件 | 操作 | 内容 |
|---|---|---|
| `domains/zero-carbon-station.md` | 更新 | TAEI-3168 退商校验完整业务链（DTO+接口+规则+表） |
| `domains/settlement.md` | 追加 | TAEI-3023 FAP解耦 + TAEI-3079 电费收益优化 |
| `domains/policy.md` | 追加 | TAEI-3089 政策结算批处理重构 |
| `domains/cbs-management.md` | 追加 | TAEI-3102 招投标重复校验2.0 + 审核状态修复 |

## 新发现

### Git 行为模式
1. **代继宁角色切换**: TAEI-3168 中从 PM 转为实际开发者（此前被认为是PM），零碳退商核心逻辑由其开发
2. **laowang 多分支并行**: 同时在 `20260529-wjh-dev`（招投标）和 `20260529-wjh-fdss`（电费收益）两个分支开发
3. **龙龙 = 王斌确认**: `龙龙` (uhyils@qq.com) 的 policy 重构提交与 tn_wangb 是同一人，使用不同署名

### 业务风险预警
1. **TAEI-3023 FAP同步注释**: `LightFapRecordServiceImpl` 中注释掉 2 个同步方法，但新 Dubbo 服务 `operationalAssetManagementService` 仅声明未使用。如果旧逻辑已被注释而新逻辑未启用，FAP状态将不同步
2. **TAEI-3174 硬编码风险**: 手机号直接硬编码在 `LightStationYuexiuAccountServiceImpl` 中，业主手机号变更需重新发版
3. **TAEI-3168 退商校验**: 当前仅实现校验接口，完整的退商申请流程（提交→审核→执行）尚未开发
