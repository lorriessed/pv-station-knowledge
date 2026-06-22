# PVS 全量代码通读报告 — 2026-06-22 (第38轮)

## 通读概况
- **通读仓库数**: 5
- **本轮策略**: Delta discovery (重扫) — 138/138 仓库已全覆盖，仅关注近期有变更的仓库
- **活跃仓库**: 2 (rrsjk-finance-service, rrsjk-hds-web)
- **零提交跳过**: 3 (rrsjk-echannel-service, rrsjk-energystorage-service, rrsjk-flowable-service)

## 仓库分类

### 零提交跳过 (最后提交 > 30天)
| 仓库 | 最后提交 | 分类 |
|---|---|---|
| rrsjk-echannel-service | 2022-08-30 | 电商渠道集成(贝店/建行/城村通/抖音/顺逛)，非PVS核心业务，已归档 |
| rrsjk-energystorage-service | 2025-04-07 (fastjson升级) | 储能收益测算，业务逻辑最后更新2023-06，已完整覆盖 |
| rrsjk-flowable-service | 2025-07-28 | Flowable BPM审批流引擎，已完整覆盖 |

### 活跃仓库 — Delta 发现

#### 1. rrsjk-finance-service (最后提交: 2026-06-18)

**变更1: SAP记账队列全局暂停结算服务商** (commit: 893fab29, 龙龙)
- 在 6 个 SAP 总账记账 Model 中统一新增 `TempConstants.stopCostSpIdList` 拦截
- 影响范围: 主材辅材服务费、能源币、电费补贴、服务费前半部分成本、临时任务、服务费领用
- 新增枚举值: `LightSapLedgerQueue.Success.STOP(-1, "临时暂停处理")`
- 暂停服务商ID (8个): 702, 719, 2544, 2557, 2649, 2659, 2669, 2672
- **⚠️ 重要**: 此前暂停机制仅存在于安装费采购单结算，本次扩展到所有SAP记账队列

**变更2: 质保金退款申请审核逻辑修复** (commits: 65fd1ca3/50d1b633, tn_wangb)
- 质保金明细状态更新范围从"仅新增"扩大到"所有关联明细"
- 删除退款申请时增加占用检查，提示被哪个退款申请占用

#### 2. rrsjk-hds-web (最后提交: 2026-06-22 今天)

**变更1: 运维租金停付 Controller** (sunzn, 2026-05-27创建 → 2026-06-22合入master)
- 路由: `/rentSuspendApplication/*`
- 功能: 业主租金停付申请管理 (列表/导入/导出)
- 依赖: `RentSuspendApplicationService` (Dubbo)

**变更2: 分中心数据源切换** (commit: dda2b48b, yumiao, 2026-06-22)
- AbstractController 新增 `getSubCenterCodesNewVersion()` 方法
- 使用 `SysSubCenterService` (system-service) 替代旧查询方式
- 空关联返回 `["-1"]` 标记

**变更3: 手动生成签约与并网规模报表** (commit: e140c26d, baoxin, 2026-06-18)

## 知识库更新

| 文件 | 操作 | 内容 |
|---|---|---|
| `domains/settlement.md` | 追加 | SAP记账队列全局暂停结算服务商 + 质保金退款审核修复 |
| `domains/hds-web.md` | 追加 | 运维租金停付Controller + 分中心数据源切换 + 签约并网报表 |
| `state/full_sweep.json` | 更新 | sweep_round → 38, 5个仓库 repo_last_sweep 更新 |
