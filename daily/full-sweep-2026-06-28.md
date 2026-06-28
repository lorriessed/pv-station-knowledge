# PVS 全量代码通读报告 2026-06-28 (第43轮)

## 概览
- **通读仓库**: 5 个 (rrs-parent, rrsjk-admin-auth-server, rrsjk-admin-authz-service, rrsjk-admin-bff, rrsjk-admin-biff)
- **本轮性质**: 重扫 (所有仓库均已通读过)
- **自上次通读以来新提交**: 0 个 (所有仓库最后提交均早于 2026-06-27)
- **但发现前轮遗漏的重要功能**: 6 项 (详见下方)

## 各仓库状态

| 仓库 | 最后提交 | 自上次扫描新提交 | 业务文件数 | 状态 |
|---|---|---|---|---|
| rrs-parent | N/A (非 git 仓库) | - | 0 | 父 POM，无业务逻辑 |
| rrsjk-admin-auth-server | 2026-06-23 | 0 | 15 | OAuth2 认证服务器 |
| rrsjk-admin-authz-service | 2026-06-23 | 0 | 119 | 授权服务 (Dubbo) |
| rrsjk-admin-bff | 2026-06-25 | 0 | 1194 | BFF 层 (376 Controller) |
| rrsjk-admin-biff | 2026-05-23 | 0 | 11 | 已废弃 (拼写错误目录) |

## 本轮发现 (前轮遗漏的重要功能)

虽然自上次扫描以来无新提交，但通过完整源代码通读发现以下功能在之前的 KB 中**未记录或记录错误**：

### 1. JDK 21 升级 (2026-06-15)
- **涉及仓库**: rrsjk-admin-auth-server, rrsjk-admin-authz-service
- **证据**: pom.xml `<java.version>21</java.version>`
- **KB 修正**: 原文档记录为 "Java 17" / "Java 8"，已更正为 Java 21
- **commit**: `f4b7f66` "build: migrate auth server to jdk21"

### 2. Redis OAuth2 Authorization Store
- **来源**: `rrsjk-admin-auth-server/.../config/RedisOAuth2AuthorizationService.java`
- **功能**: OAuth2 Authorization 对象（code/token/refresh token）存储在 Redis
- **Key 前缀**: `rrsjk:admin-auth-server:oauth2:authorization:`
- **安全**: token 值经 SHA-256 哈希后作为 Redis key

### 3. App Password Token 接口
- **来源**: `rrsjk-admin-auth-server/.../controller/AppPasswordTokenController.java`
- **端点**: `POST /api/app/auth/password-token`
- **功能**: App 端用户名密码换 OAuth2 token（供 app-bff 内部调用）
- **自定义 grant type**: `urn:rrsjk:params:oauth:grant-type:app_password`

### 4. 海尔 IDM 员工登录
- **来源**: `rrsjk-admin-auth-server/.../haier/HaierIdmLoginController.java`
- **端点**: `GET /login?provider=haier` → 海尔 IdM OAuth2 回调
- **功能**: 海尔集团员工通过 iama.haier.net 统一认证登录 CBS
- **流程**: IdM code → employeeNo → AuthzUserService.getUserIdentity() → CBS 账号

### 5. Session 共享 (Redis)
- **来源**: commit `7b751d7` "fix(auth): share login sessions through redis"
- **配置**: `spring.session.store-type: redis`, namespace: `rrsjk:admin-auth-server:session`, TTL: 24h

### 6. BFF API 前缀变更
- **变更**: 所有 BFF API 从 `/api/app/` 统一改为 `/api/admin/`
- **影响**: 资产管理等所有模块的路由前缀
- **KB 修正**: 已更新 admin-authz.md 中所有路径前缀

## 知识库更新

| 文件 | 操作 | 内容 |
|---|---|---|
| `domains/admin-authz.md` | 更新 | +JDK 21 修正, +Redis OAuth2 Store, +App Password Token, +Haier IDM 登录, +Session 共享, +API 前缀修正, +Vue3 迁移进度, +BFF 模块全景 (48 模块 376 Controller) |
| `domains/admin-new-architecture.md` | 更新 | +Java 版本修正 (17→21), +authz 表数量 (7→10), +BFF 规模修正 (17→48 模块) |

## 统计
- 知识库文件行数: admin-authz.md 817→1005 行 (+188 行), admin-new-architecture.md 83→86 行
- 新增业务规则: 8 项
- 修正错误: 4 项 (Java 版本、API 前缀、表数量、模块数量)
