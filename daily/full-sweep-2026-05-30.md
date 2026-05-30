# 全量通读报告 2026-05-30

## 统计

- **本轮**: 第 15 轮
- **本次通读仓库**: 5 个 (rrs-parent, rrsjk-admin-auth-server, rrsjk-admin-authz-service, rrsjk-admin-bff, rrsjk-admin-biff)
- **从未通读仓库**: 12 个 (本轮后 7 个)
- **已通读总数**: 112/122

## 仓库详情

### 1. rrs-parent
- **业务文件数**: 0
- **类型**: Maven 父 POM
- **说明**: 纯基础设施，版本 8.0.6，所有 rrsjk-* 子模块的 parent。无业务逻辑。

### 2. rrsjk-admin-auth-server ⭐ (重大发现)
- **业务文件数**: 10
- **类型**: OAuth2/OIDC 认证服务器
- **技术栈**: Spring Boot 3.5.14, Java 17, Spring Security OAuth2 Authorization Server
- **端口**: 9000
- **Session Cookie**: `ADMIN_AUTH_SESSION`
- **安全过滤器链**: 两条 — OAuth2 endpoint 链 (HIGHEST) + 默认表单登录链 (Order 2)
- **OAuth2 客户端**:
  - `admin-bff`: access_token 24h, refresh_token 7d, authorization_code + refresh_token
  - `admin-mobile`: access_token 2h, refresh_token 30d, PKCE 必须, 自定义 URI scheme
- **关键文件**: `SecurityConfig.java`, `LoginController.java`, `application.yml`
- **知识库更新**: `domains/admin-authz.md` (新建)

### 3. rrsjk-admin-authz-service ⭐ (重大发现)
- **业务文件数**: 30
- **类型**: Dubbo 授权服务
- **技术栈**: Spring Boot 2.3.3, Dubbo 2.7.4.1, MyBatis 3.5.2, Zookeeper
- **数据库**: rrsjk_admin_authz @ pv-mysql-prod
- **7 张表**: authz_user, authz_role, authz_menu, authz_permission, authz_user_role, authz_role_permission, authz_user_permission
- **5 个 Dubbo 服务**: AuthzMenuService, AuthzPermissionService, AuthzRoleService, AuthzSnapshotService, AuthzUserService
- **权限类型**: PAGE, MENU, BUTTON, API (四级粒度)
- **核心逻辑**: getSnapshot(userId) → 聚合用户+角色+菜单+权限 → 按类型分类到 pagePermissions/buttonPermissions/apiPermissions
- **知识库更新**: `domains/admin-authz.md` (新建)

### 4. rrsjk-admin-bff ⭐ (重大发现)
- **业务文件数**: 130+ (从源码中提取)
- **类型**: Admin Backend-for-Frontend
- **技术栈**: Spring Boot 3.5.14, Java 17, OAuth2 Client, Dubbo 3.2.15
- **端口**: 8081
- **认证流程**: /api/app/auth/login → 保存 redirect → 302 到 OIDC → 回调 → AuthRedirectSuccessHandler → 重定向到 frontendBaseUrl + redirect
- **权限校验**: requirePermission(auth, permKey) → AuthzSnapshotService.getSnapshot() via Dubbo → fail-closed
- **17+ 业务模块**: 资产管理(13), 结算(32), 仓储(35), 电站(19), 自有财务(21) 等
- **资产管模块详细 API** (本次全量通读重点):
  - 招银租赁: `/api/app/asset-management/cmb-leasing-stations` (7 个接口)
  - BT 资产管理: `/api/app/asset-management/bt-asset-management` (5 个接口)
  - BT 基金明细: `/api/app/asset-management/bt-fund-asset-allocate-details` (5 个接口)
  - BT 基金报表: `/api/app/asset-management/bt-fund-reports` (7 个接口, 含回款凭证上传 OSS)
  - BT 项目公司: `/api/app/asset-management/bt-project-transactions` (5 个接口)
  - EAM 资产: `/api/app/asset-management/eam-assets` (3 个接口, 41 字段导出)
  - EAM 年度预算: `/api/app/asset-management/eam-year-budgets` (2 个接口)
  - 合同管理: `/api/app/asset-management/contracts` (6 个接口, PDF 上传 OSS)
  - 经营性租赁: `/api/app/asset-management/energy-leased-station-asset-reports` (6 个接口)
- **知识库更新**: `domains/admin-authz.md`, `data/api-endpoints.md`

### 5. rrsjk-admin-biff
- **业务文件数**: 11
- **类型**: 拼写错误 (同 rrsjk-admin-bff)
- **说明**: pom.xml artifactId 也是 `rrsjk-admin-bff`，Java 包名也是 `com.rrsjk.adminbff.*`，内容与 bff 完全相同。确认目录名拼写错误，忽略。

## 知识库更新文件

| 文件 | 操作 | 说明 |
|---|---|---|
| `domains/admin-authz.md` | **新建** | 认证授权体系完整文档 (17.8KB) |
| `domains/admin-new-architecture.md` | **更新** | 改为概览索引，指向 admin-authz.md |
| `data/api-endpoints.md` | **追加** | BFF 资产管理 9 个 Controller 完整 API 列表 |
| `data/tables.md` | **追加** | authz 7 张表结构 |
| `domain-router.md` | **更新** | Admin 认证授权路由指向 admin-authz.md |
| `modules/repositories.md` | **更新** | 5 个仓库标记为已通读 |

## 关键业务发现

1. **新一代 Admin 认证架构已成型**: auth-server (OIDC) + authz-service (Dubbo 授权) + bff (BFF 层) 三件套已完成基础建设，BFF 层已覆盖 17+ 业务模块
2. **权限模型**: 四级粒度 (PAGE/MENU/BUTTON/API)，支持 clientType 维度隔离
3. **Token 策略**: BFF 端 24h access + 7d refresh，移动端 2h access + 30d refresh + PKCE
4. **回款凭证管理**: BT 基金报表支持回款凭证图片上传 OSS，含金额校验（回款金额 ≤ 待回款金额）
5. **招银租赁**: 支持批量审核推送到招银、返工文件导入、异步状态拉取
6. **EAM 资产**: 41 字段导出覆盖 SAP 采购单、在建工程、固定资产编号、转资金额等完整 EAM 链路
