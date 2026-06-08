# 云效驱动代码学习日报 — 2026-06-08

## 扫描范围
- 云效需求: 36 个 | Git 提交: 354 个 | 涉及人员: 15 人
- 扫描窗口: 2026-06-01 ~ 2026-06-08
- 核心仓库: light-service(100+), light-data-service(20+), light-report-service(30+), finance-service(11), trade-service(17), light-operation-service(3)

## 人员→提交分布
| 人员 | 提交数 | 核心仓库 |
|---|---|---|
| yumiao | 67 | cbs-web, admin-web, light-data-service |
| 代继宁 | 37 | light-service, light-report-service, trade-service |
| majinhu | 36 | light-data-service |
| 龙龙(tn_wangb) | 25+11 | light-service |
| mabin | 25 | light-service, finance-service |
| sunzn | 24 | light-service, light-data-service |
| baoxin | 24 | trade-service, light-service |
| 解钦 | 21 | light-service |
| wangxiran | 20 | light-service, admin-web |
| 张硕文 | 16 | nahui-dashboad-h5, nahui-dicts-serve |
| laowang | 15 | light-service, cbs-web |
| 德(姜传德) | 13 | light-service |
| lilong | 12 | admin-web, light-service |
| 李培龙 | 8 | nahui-dicts-serve |

## 重点业务链分析

### 1. 发电数据 ADS 迁移 + 解绑定时任务 (TAEI-3184)
- **开发者**: majinhu (36 commits) | **仓库**: rrsjk-light-data-service
- 新增 `UnbindStationCandidate` 实体和两个定时任务
- 发电列表从 DWS 切换到 ADS 报表
- Doris 兼容修复：`sum(elec_today)` → `ANY_VALUE`

### 2. FAP 集成加速 (TAEI-3023/3022/3021/3117)
- **开发者**: 代继宁 (37 commits)
- 基金对接FAP: `BtFundAssetRepaymentRecordService` 新增双向同步
- 商城FAP: trade-service 记账凭证/记账时间
- 电费收益作废: FAP状态枚举 `WAIT_SENT` → `SENT`

### 3. 图片审核驳回 + flag 颠倒 Bug (TAEI-3057/3126)
- **开发者**: 王希然 (20 commits)
- 按单张图片驳回功能
- ✅ Bug修复: reject_flag 逻辑颠倒 (commit 05e32c106e)

### 4. 电站转移功能 (TAEI-3058)
- **开发者**: 姜传德 (13 commits)
- 分中心权限、人员信息授权、华融授权协议随电站转移

### 5. 越秀二类卡 — 硬编码预警 (TAEI-3174)
- **开发者**: 解钦 (21 commits)
- ⚠️ 14个生产手机号硬编码在 `LightStationYuexiuAccountServiceImpl`

### 6. 施工队报表 (light-report-service)
- 施工队列表查询 + 工单运营报表 + 分中心周转

## 风险预警
1. **🔴 硬编码生产数据**: TAEI-3174 中14个手机号硬编码
2. **🟡 flag 逻辑颠倒**: 已修复，但需确认历史数据是否受影响
3. **🟡 FAP 解耦模式**: trade-service 注释/放开代码模式，需验证回调链路

## 知识库更新
- `domains/approval.md`: 新增图片审核驳回 + 电站转移功能
- `domains/electric-fee-revenue.md`: 新增 FAP 作废状态枚举变更

## 详细报告
https://cdn01.rrsjk.com/reports/d3001c72-b31b-4d06-98cb-6b70689e1aaa.html
