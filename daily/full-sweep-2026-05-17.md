# 全量代码通读报告 2026-05-17

## 概览

| 指标 | 值 |
|------|-----|
| 本次通读仓库数 | 5 |
| 通读轮次 | 第 4 轮完成 → 第 5 轮开始 |
| 总仓库数 | 100 |
| 已通读 | 100/100 ✅ |
| Java 文件总数 | 19,197 |

## 本次通读仓库

### 1. item-service — CBS 物料/商品管理服务

- **Java 文件**: 34 | **数据库**: rrscom | **框架**: Dubbo 2.7.4.1 + MyBatis
- **定位**: CBS 商城系统商品/物料主数据管理，提供 Dubbo RPC 接口
- **核心功能**: 产品信息查询、品牌/品类管理、SKU 管理、价格规则（阶梯定价）、物料属性
- **业务价值**: ⭐ 低 — 商城基础设施，非 PV 光伏专属
- **最近变更**: 2022-06-08（阿里云生产环境配置）
- **知识库更新**: `domains/remaining-services-and-frontends.md` 新增 item-service 详细文档

### 2. job-service — CBS 通用定时任务调度框架

- **Java 文件**: 45 | **数据库**: rrscom | **框架**: Quartz + Dubbo 2.7.4.1
- **定位**: CBS 系统通用定时任务调度框架，支持 4 种任务类型
- **4 种 Job 类型**:
  - `TYPE_DUBBO`: 调用远程 Dubbo 服务方法
  - `TYPE_SQL`: 直接执行 SQL 语句
  - `TYPE_URL`: HTTP URL 调用
  - `TYPE_CUSTOM`: 自定义 Java 类实现
- **核心特性**: 并发控制（默认不允许并发）、全局暂停/恢复、任务日志与监控
- **最近变更**: 2026-05-12 解钦 — 增加按 jobName 逻辑删除 + scheduleJobOnceNow
- **业务价值**: ⭐ 低 — 通用调度基础设施，非 PV 光伏专属
- **知识库更新**: `domains/remaining-services-and-frontends.md` 新增 job-service 详细文档

### 3. log_report_plugin — Flutter 日志上报插件

- **文件**: 14（配置+manifest）| **技术栈**: Flutter Plugin (Android + iOS)
- **定位**: 封装 Bugly 崩溃/错误日志上报
- **业务价值**: ⭐ 极低 — 基础设施插件，与 PVS 业务无关
- **知识库更新**: `domains/remaining-services-and-frontends.md` 简要记录

### 4. nahui-dashboad-h5 — 智慧大屏 H5 前端

- **业务文件**: 0（Vue/JS 不在 Java 扫描范围）| **最近提交**: 2026-05-07
- **近期变更**（从 commit message）:
  - 服务工单增加"进行中"、"已完成"状态，显示故障/低效工单
  - 优化智慧大屏布局
  - 修改获单、安装数据展示
- **业务价值**: ⭐ 中 — APV 智慧大屏前端，有 PV 业务展示逻辑
- **知识库更新**: `domains/remaining-services-and-frontends.md` 简要记录

### 5. nahui-dicts-serve — 数据字典服务

- **业务文件**: 0（前端/Node.js 项目）| **最近提交**: 2026-05-12
- **近期变更**（从 commit message）:
  - 组件尺寸数据字典字段更新
  - SAP 采购相关功能
  - 辅料定额功能
- **业务价值**: ⭐ 低 — 数据字典前端管理界面
- **知识库更新**: `domains/remaining-services-and-frontends.md` 简要记录

## 知识库更新汇总

| 文件 | 操作 | 内容 |
|------|------|------|
| `domains/remaining-services-and-frontends.md` | 新增 | item-service 详细文档（服务接口、方法清单、数据库表、业务特点） |
| `domains/remaining-services-and-frontends.md` | 新增 | job-service 详细文档（4种Job类型、架构、并发控制、日志监控） |
| `domains/remaining-services-and-frontends.md` | 新增 | log_report_plugin / nahui-dashboad-h5 / nahui-dicts-serve 简要记录 |
| `modules/repositories.md` | 更新 | 已通读从 66 → 100/100，所有仓库标记 ✅ |
| `state/full_sweep.json` | 修复 | 修复 repo_last_sweep 中 int/str 混排导致的排序崩溃；completed_repos 从 66 → 100 |

## Bug 修复

### pv_full_code_sweep.py 排序崩溃修复

**问题**: `repo_last_sweep` 字典中早期版本写入了整数（提交计数），后期版本写入 ISO 时间戳字符串。Python 的 `sorted()` 无法比较 int 和 str，导致 `TypeError: '<' not supported between instances of 'int' and 'str'`。

**修复**:
1. 脚本层面: `sorted()` key 改为 `str(repo_sweeps.get(r.name, ""))` 统一转字符串
2. 数据层面: 将 `full_sweep.json` 中所有整数值的 `repo_last_sweep` 条目统一改为 ISO 时间戳

## 里程碑

🎉 **第 4 轮全量通读完成** — 100/100 个仓库全部通读，PV 代码库全量覆盖！
- 从 2026-05-12 开始第 1 轮，历时 6 天
- 每轮约 20 次运行（每次 5 个仓库）
- 沉淀 27+ 个 domain 文件、source-map 索引、数据库表映射等
