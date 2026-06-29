# PVS 全量代码通读报告 — 2026-06-29

## 通读概况

- **轮次**: 第 43 轮（重扫，无知识产出）
- **通读仓库**: 5 个
- **知识库更新**: 0 个文件
- **sweep_round**: 保持 43 不变（无新知识沉淀）

## 仓库分析

### 1. rrsjk-admin-web-next
- **最后提交**: 2026-05-27 (`feat: complete admin authz web migration`)
- **技术栈**: Vue 3.5.22 + PureAdmin + Element Plus 2.11.5 + Tailwind CSS 4 + TypeScript 5.9 + Vite 7
- **文件数**: 147 个 Vue/TS 源文件
- **KB 覆盖**: 已在 7 个 KB 文件中引用（admin-authz.md, admin-new-architecture.md, admin-app-service.md 等）
- **结论**: ✅ 已有充分覆盖。自 5/27 以来零提交。本轮无新知识。

### 2. usher-common
- **最后提交**: 2026-01-25（版本号更新）
- **定位**: usher 开源框架公共模块（top.uhyils.usher groupId）
- **内容**: BaseDO/BaseDTO/BaseService/AbstractDoService 等基础架构类，ES/Mongo/Redis 数据层支持，EventBus，日志框架，MQ 封装，优雅上下线，热点发现
- **KB 覆盖**: 已在 `domains/usher-rpc-framework.md` 中记录（20 行引用）
- **结论**: ⭐ 基础设施层，零 PVS 业务逻辑。5 个月无提交。跳过。

### 3. usher-dependencies
- **最后提交**: 2026-01-25
- **定位**: usher 生态版本管理 POM（parent 项目）
- **内容**: 纯 pom.xml，管理所有 usher 子模块版本号 + 第三方依赖版本（Spring Boot 2.6.1, Netty 4.1.54, Nacos 2.4.3, RocketMQ 5.3.1 等）
- **结论**: ⭐ 纯版本管理，零业务逻辑。跳过。

### 4. usher-groovy-flex
- **最后提交**: 2026-01-25
- **定位**: Groovy 动态脚本执行框架（Spring Boot Starter）
- **内容**: 运行时动态修改业务逻辑的规则引擎，适用于工作流条件判断等场景
- **KB 覆盖**: 已在 usher-rpc-framework.md 中提及
- **结论**: ⭐ 框架依赖，PVS 可能使用其做动态规则但无 PVS 特定逻辑。跳过。

### 5. usher-protofuse
- **最后提交**: 2026-01-25
- **定位**: 多协议融合框架 — 支持 MySQL 协议和 HTTP 协议接入
- **内容**: 自研 MySQL 协议服务端（Netty 实现，支持 COM_QUERY/COM_STMT_PREPARE 等全部 MySQL 命令），SQL 解析执行计划引擎，HTTP 协议接入层
- **KB 覆盖**: 已在 usher-rpc-framework.md 中提及
- **结论**: ⭐ 框架依赖。protofuse 是 usher 的"数据库网关"能力，PVS 本身不使用此协议层。跳过。

## 本轮结论

**全部 5 个仓库均为零提交或已有充分覆盖，无新知识产出。**

- usher-* 4 个仓库：开源框架依赖，最后提交在 2026-01-25，零 PVS 业务逻辑，已在 `usher-rpc-framework.md` 中记录
- rrsjk-admin-web-next：Vue 3 新管理后台，已在多个 domain 文件中覆盖，5/27 后零提交

**sweep_round 保持 43 不变**（按规范：无知识产出时不递增轮次）。
