# 全量通读报告 — 2026-06-11 (第28轮)

## 通读概览

| 指标 | 值 |
|---|---|
| 通读日期 | 2026-06-11 |
| 轮次 | 第 28 轮 |
| 本次通读仓库 | 5 个 |
| 从未通读仓库 | 0 个 |
| 总仓库数 | 122 |
| 已通读 | 122/122 (100%) |

## 本次通读仓库清单

| # | 仓库 | 最后提交 | 业务价值 | 变更 |
|---|---|---|---|---|
| 1 | item-service | 2022-06-08 | ⭐ 低 — CBS 老电商商品服务 | 零提交 |
| 2 | job-service | 2026-05-12 | ⭐ 中 — CBS 通用定时任务框架 | 零提交 |
| 3 | log_report_plugin | 2024-12-09 | ⭐ 低 — Flutter Bugly 日志插件 | 零提交 |
| 4 | nahui-dashboad-h5 | 2026-06-01 | ⭐ 中 — APV 智慧大屏 H5 前端 | 零业务文件 |
| 5 | nahui-dicts-serve | 2026-06-11 | ⭐ 中 — 前端数据字典 | 新增 7 个字典文件 |

## 仓库分析

### 1. item-service — CBS 老电商商品服务

**定位**: `com.haier.cbs.item` 包，旧 CBS 电商平台商品/物料管理 Dubbo 服务。
**与 rrsjk-item-service 的区别**: 这是老 CBS 系统的商品服务，非 PV 光伏专属。`rrsjk-item-service` 是 PV 系统的商品服务，包路径为 `com.rrsjk.item`。

**核心能力**:
- Dubbo 接口: `ItemService` (标注 `@Deprecated`)
- 数据表: `Brands`, `ProductTypes`, `ProductCates`, `Products`, `item_attribute`, `item_base`, `NetPoints`, `Payments`, `LesFiveYards`, `PriceRules`
- 阶梯价规则: `PriceRules` 表支持商品多价规则（新增/编辑/发布/终止/删除）
- 产品上架/下架: `onSale` 字段控制
- 淘宝同步: `taobaoId`, `stockToTaotao`, `lastSyncTime` 字段
- 外部服务: 依赖 `shoppingmall-core` (ehaier 电商平台)

**状态**: 最后提交 2022-06-08，零新提交。已有表映射在 `data/sql-table-refs.md`。**无需更新知识库。**

### 2. job-service — CBS 通用定时任务调度框架

**定位**: `com.haier.cbs.job` 包，基于 Quartz + Zookeeper 的通用定时任务调度框架。

**4 种 Job 类型**:
- `dubbo` — 通过 Dubbo 泛化调用远程服务方法
- `sql` — 执行 SQL 语句（未实现 `NotImplementedJobException`）
- `url` — 调用 HTTP URL（未实现）
- `custom` — 自定义 Java 类（继承 `AbstractJob`）

**分布式协调**:
- `JobMainWorker` — 主节点通过 ZK 锁 (`/job/jobLock`) 选举，负责任务分发
- `JobCommWorker` — 工作节点通过 ZK 注册，领取任务执行
- 任务分配: `maxWorks = totalJobs / workers + totalJobs % workers`

**数据库**: `sys_job`, `sys_job_log`, `sys_job_monitor`

**状态**: 2026-05-12 新增 `logicDeleteByJobName` 逻辑删除功能，2025-07 新增 `scheduleJobOnceNow` 一次性触发功能。本次零新提交。已有详细文档在 `domains/remaining-services-and-frontends.md` §5。**无需更新知识库。**

### 3. log_report_plugin — Flutter Bugly 日志上报插件

**定位**: `com.haier.nahui.log_report_plugin`，Flutter 插件封装 Bugly 崩溃日志上报。

**平台**: Android + iOS
**版本**: 0.0.3
**提交**: feat: 完成 Bugly iOS 日志上报 (2024-01-26)

**状态**: 纯基础设施插件，无 PV 业务逻辑。已有简要记录在 `domains/remaining-services-and-frontends.md` §3。**无需更新知识库。**

### 4. nahui-dashboad-h5 — APV 智慧大屏 H5 前端

**定位**: `/dashboard/apv` 智慧大屏 H5 前端页面。
**扫描**: 0 个业务文件（源码可能为构建输出或未包含在扫描中）。

**近期 commit 线索** (2026-04~06):
- `fix:修复资方数据运算` (2026-06-01, 张硕文)
- `feat:服务工单增加进行中、已完成。故障、低效工单显示` (2026-05-07, 张硕文)
- `style:优化智慧大屏布局` (2026-04-22)
- `feat:修改获单、安装单位` (2026-04-21)

**后端依赖**: 调用 `rrsjk-light-report-service` 的 `/dashboard/apv/getGrid.do` 接口获取大屏数据。

**状态**: 已有详细记录在 `domains/remaining-services-and-frontends.md` §7。**无需更新知识库。**

### 5. nahui-dicts-serve — 前端数据字典

**定位**: 前端数据字典仓库，包含大量 `export default [{value, label}]` 格式的 `.js` 文件。

**本次新增字典文件** (2026-06-01~08 提交):

| 文件 | 说明 | 对应后端枚举 |
|---|---|---|
| `osp/general/stopPayOwnerReason.js` | 业主申请停付原因 | `SuspendReasonEnum` (OWNER_CHANGE/BLACK_ACCOUNT/OTHER) |
| `osp/general/stopPayOwnerR.js` | 业主申请恢复原因 | TRANSFER_SUCCESSFUL/OTHER |
| `osp/general/stopPayReason.js` | 停付原因 | 空文件 |
| `osp/general/stopPayRecoverReason.js` | 停付恢复原因 | 空文件 |
| `osp/general/stopPayStatus.js` | 租金停付状态 | `StatusEnum` (9个状态) |
| `osp/general/stopPayType.js` | 租金停付类型 | `RentSuspendTypeEnum` (OWNER_APPLY/DISPUTE_SUSPEND) |
| `apv/station/transStationstatus.js` | 电站转单状态 | `StatusEnum` (5个状态) |

**状态**: ✅ 已更新 `data/enums.md`，新增 7 个前端字典文件索引。后端枚举已在 `data/enums.md` 的"租金停付管理枚举"和"电站转移状态"章节记录。

## 知识库更新

| 文件 | 操作 | 内容 |
|---|---|---|
| `data/enums.md` | 追加 | 新增 osp/general 停付管理字典 6 个文件索引 + apv/station/transStationstatus.js |
| `modules/repositories.md` | 全量重新生成 | 从 full_sweep.json 重新生成，确保 122/122 状态一致 |
| `state/full_sweep.json` | 自动更新 | sweep_round=28, completed_repos=122 |

## 备注

- 本轮 5 个仓库均为**重扫**（非首扫），采用 delta discovery 策略
- item-service 和 job-service 自上次通读以来零新提交，按"零提交跳过优化"直接更新时间戳
- nahui-dicts-serve 是唯一有实质更新的仓库（7 个新字典文件）
- 知识库 100% 覆盖：122/122 仓库已通读
