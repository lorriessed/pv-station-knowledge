# Admin BFF 与权限服务

更新时间: 2026-06-10

## Admin BFF 分中心权限重构 (2026-06-03~04，于淼/yumiao)
**来源**: `rrsjk-admin-bff` + `rrsjk-admin-authz-service` + `rrsjk-admin-web` (yumiao, 2026-06-03~04, 40+ commits)
**证据等级**: 代码明确证明

### BFF 层变更 (`rrsjk-admin-bff`)
- **Current User 接口**: 新增当前用户分中心范围 (`include sub centers in current user`)
- **电站鉴权集中化**: `centralize station authz checks` — 统一电站权限校验入口
- **Web/App 认证分离**: `separate web auth endpoints from app auth` — 独立 Web 端和 App 端认证端点
- **管理 BFF API 权限检查**: `add admin bff api permission checks`
- **分中心用户管理 BFF**: `add party user management bff` / `add party management bff`
- **Home Summary**: 新增首页汇总 + App 在线用户数接口
- **系统字典管理 API**: `add system dictionary admin APIs`
- **回购管理**: `repurchasemanagement` 模块新增 validation dependency
- **API 前缀重命名**: `rename admin bff api prefix`
- **Current User 上下文集中化**: `centralize current user sub center scope`
- **移除废弃 auth 参数**: `remove unused auth parameters`

### Authz Service 变更 (`rrsjk-admin-authz-service`)
- **分中心范围授权**: `add authz sub center scope` — 新增分中心粒度的权限控制
- **Web API 权限资源对齐**: `align web api permission resources`

### Admin Web 配套变更 (`rrsjk-admin-web`)
- **电站方案审核分中心查询**: 修复电站方案审核的分中心查询逻辑
- **终止管理状态映射**: 修复终止管理的状态映射
- **分中心人员关系**: 多次修复分中心对应人员的关系映射 (7+ commits)
- **电费收益分中心回退**: 多次回退/调整分页大小
- **越秀管理/终止管理适配新分中心**
- **Dubbo XML 合并冲突修复**: 解决 `service.xml` 中的 git merge markers (commit 7c9448c9)

### 业务意义
- 旧版分中心权限 (`SysPartyService`) 正在逐步被新版 `SysSubCenterService` + BFF 层鉴权替代
- BFF 层 (rrsjk-admin-bff) 作为 `rrsjk-admin-web-next` (Vue3 前端) 的 API Gateway，集中处理分中心权限和电站鉴权
- **架构方向**: CBS 旧版管理 → BFF 新架构 (Dubbo 代理 + REST API)

---
