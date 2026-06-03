# Admin 认证授权体系 (新一代 OAuth2/OIDC 架构)

更新时间: 2026-06-01
证据等级: 代码明确证明

## 架构概览

管理后台（CBS）正在从旧版 `rrsjk-admin-web`（Spring MVC + EasyUI + FTL + Shiro）迁移到基于 OAuth2/OIDC 的新架构。

```
新架构: rrsjk-admin-web-next (Vue3 前端)
      → rrsjk-admin-bff (BFF 层, port 8081, OAuth2 Client)
      → rrsjk-admin-auth-server (认证服务器, port 9000, OIDC Provider)
      → rrsjk-admin-authz-service (授权服务, Dubbo, 权限/角色/菜单)
```

**旧架构**: `rrsjk-admin-web` (Shiro + FTL) → 用户直接访问

**负责人**: 于淼 (yumiao), 2026-05-27 初始化

## 1. rrsjk-admin-auth-server (认证服务器)

**来源**: `rrsjk-admin-auth-server` 全量通读 (2026-05-30) + 增量更新 (2026-06-02~03)

- **技术栈**: Spring Boot 3.5.14, Spring Security 6, OAuth2 Authorization Server, Java 17
- **端口**: 9000
- **Session Cookie**: `ADMIN_AUTH_SESSION`
- **部署**: JSW (Java Service Wrapper) tar.gz 打包

### 1.0 认证用户加载方式变更 (2026-06-02~03)

**来源**: commits by yumiao (2026-06-02~03), `AuthzUserDetailsService.java` 新增
**证据等级**: 代码明确证明

认证服务器从 **Spring Security 内置用户** 迁移到 **通过 Dubbo 调用 authz-service 加载用户凭据**：

- **移除**: `application.yml` 中硬编码的 `spring.security.user.name: admin / password: admin123`
- **新增**: `AuthzUserDetailsService` — 实现 `UserDetailsService`，通过 Dubbo 调用 `AuthzUserService.getPasswordCredential()` 获取密码凭据
- **新增**: `DubboReferenceFactory` — 管理 Dubbo Reference 的创建和发现，强制接口发现 (`force Dubbo interface discovery for authz`)
- **新增**: `bootstrap-admin` 配置 (环境变量 `BOOTSTRAP_ADMIN_ENABLED`/`USERNAME`/`PASSWORD`) — 应急本地管理员，默认关闭
- **新增**: ZK 3.4 兼容层 (`Zk34CompatibleCuratorZookeeperClient`, `Zk34CompatibleCuratorZookeeperTransporter`)
- **新增依赖**: Dubbo 3.2.15, Curator 4.2.0, Zookeeper 3.5.9, rrsjk-admin-authz-api 1.0.1-SNAPSHOT

**认证加载流程**:
```
OAuth2 登录 → AuthzUserDetailsService.loadUserByUsername(username)
  → DubboReferenceFactory.get(AuthzUserService.class).getPasswordCredential(username)
  → 返回 password_hash (Spring Security delegating encoder 格式)
  → 如果 authz-service 不可用 → 降级到 bootstrap-admin (如启用)
  → 如果都没有 → UsernameNotFoundException
```

**环境配置** (新增 authz.dubbo 配置):
| 环境 | ZK 注册中心地址 |
|---|---|
| dev | `10.2.192.154:2181?timeout=60000` |
| prod | `10.2.160.242:2181,10.2.160.243:2181,10.2.160.244:2181` |

### 1.1 安全过滤器链 (SecurityConfig.java)

**两条 SecurityFilterChain**:

| 优先级 | 匹配路径 | 功能 |
|---|---|---|
| HIGHEST | `/.well-known/**`, `/oauth2/**`, `/connect/**`, `/userinfo`, `/api/mobile/**` | OAuth2 Authorization Server + Resource Server (JWT) |
| Order 2 | 其他所有请求 | Form Login (`/login`) + 默认安全链 |

**关键配置**:
- `/.well-known/appspecific/` → 返回 404（防浏览器探测）
- 登录成功处理: `SavedRequestAwareAuthenticationSuccessHandler`，无 saved request 时重定向到 `frontendBaseUrl + "/"`
- 登录页面: `/login` → Thymeleaf 模板 `login`
- 根路径 `/` → 重定向到 `frontendBaseUrl + "/login"`
- 异常处理: HTML 请求 → 重定向到 `/login`；API 请求 → JWT 认证

### 1.2 OAuth2 客户端配置

**admin-bff 客户端** (管理后台 BFF):

| 配置项 | 值 |
|---|---|
| client-id | `admin-bff` |
| client-secret | `{noop}secret` |
| 认证方式 | `client_secret_basic` |
| 授权类型 | `authorization_code`, `refresh_token` |
| redirect-uri | `${app.bff-base-url}/login/oauth2/code/admin-bff` |
| 登出重定向 | `${app.frontend-base-url}/` |
| scopes | `openid`, `profile` |
| Access Token TTL | **24 小时** (PT24H) |
| Refresh Token TTL | **7 天** (P7D) |
| 复用 Refresh Token | false |

**admin-mobile 客户端** (移动端):

| 配置项 | 值 |
|---|---|
| client-id | `admin-mobile` |
| 认证方式 | `none` (Public Client) |
| 授权类型 | `authorization_code`, `refresh_token` |
| redirect-uri | `rrsjkadmin://oauth/callback`, `com.rrsjk.admin://oauth/callback`, `${app.frontend-base-url}/mobile/callback` |
| scopes | `openid`, `profile` |
| PKCE | **必须** (require-proof-key: true) |
| Access Token TTL | **2 小时** (PT2H) |
| Refresh Token TTL | **30 天** (P30D) |
| 复用 Refresh Token | false |

### 1.3 环境配置

| 环境 | auth-server-base-url | frontend-base-url | bff-base-url |
|---|---|---|---|
| local | `http://10.2.192.146:9000` | `http://127.0.0.1:8848` | `http://127.0.0.1:8081` |
| dev | `https://cbstest.haier-energy.com` | `https://cbstest.haier-energy.com` | `https://cbstest.haier-energy.com` |
| prod | `https://cbs.haier-energy.com` | `https://cbs.haier-energy.com` | `https://cbs.haier-energy.com` |

## 2. rrsjk-admin-authz-service (授权服务)

**来源**: `rrsjk-admin-authz-service` 全量通读 (2026-05-30)

- **技术栈**: Spring Boot 2.3.3, Dubbo 2.7.4.1, MyBatis 3.5.2, Zookeeper 注册中心
- **Java 版本**: Java 8 (构建时 strip Java 9 wrapper args)
- **模块**: `rrsjk-admin-authz-api` (接口) + `rrsjk-admin-authz-impl` (实现)
- **数据库**: `rrsjk_admin_authz` (生产: `rm-m5ebm056ct14p18zu.mysql.rds.aliyuncs.com`)
- **部署**: JSW, dev: 1024M-2048M, prod: 1024M-2048M

### 2.1 Dubbo 服务接口

#### AuthzMenuService (菜单管理)
```
listMenusByUser(userId)          → List<AuthzMenuDTO>    用户可见菜单
listAllMenus()                    → List<AuthzMenuDTO>    所有菜单
saveMenu(menu)                    → void                  新增/更新菜单
deleteMenu(menuKey)               → void                  删除菜单
```

#### AuthzPermissionService (权限管理)
```
listPermissionsByRole(roleCode)   → List<AuthzPermissionDTO>  角色权限
listAllPermissions()              → List<AuthzPermissionDTO>  所有权限
listByPermissionKeys(keys)        → List<AuthzPermissionDTO>  按 key 批量查询
createPermission(permission)      → AuthzPermissionDTO        创建权限
updatePermission(permission)      → void                      更新权限
deletePermission(permissionKey)   → void                      删除权限
grantRolePermissions(roleCode, keys) → void                   批量授权
```

#### AuthzRoleService (角色管理)
```
listRolesByUser(userId)           → List<AuthzRoleDTO>    用户角色
listAllRoles()                    → List<AuthzRoleDTO>    所有角色
createRole(role)                  → AuthzRoleDTO          创建角色
updateRole(role)                  → void                  更新角色
deleteRole(roleCode)              → void                  删除角色
assignRoles(userId, roleCodes)    → void                  分配角色
```

#### AuthzSnapshotService (权限快照 — 核心接口)
```
getSnapshot(userId)               → AuthzSnapshotDTO      用户完整权限快照
getSnapshotForClient(userId, clientType) → AuthzSnapshotDTO  按客户端类型过滤
```

#### AuthzUserService (用户管理)
```
getUserIdentity(userId)           → AuthzUserIdentityDTO  用户身份
listAllUsers()                    → List<AuthzUserIdentityDTO>
saveUser(user)                    → void                  保存用户
getPasswordCredential(loginIdOrUserId) → AuthzPasswordCredentialDTO  查询密码凭据 (2026-06-02 新增)
resetPassword(userId, rawPassword, operatorUserId) → void  重置密码 (2026-06-02 新增)
listRoleCodesByUser(userId)       → List<String>          用户角色编码列表
assignRolesToUser(userId, roleCodes) → void               分配角色
listPermissionKeysByUser(userId)  → List<String>          用户权限 key 列表
assignPermissionsToUser(userId, keys) → void              直接分配权限
```

### 2.2 数据模型 (DTO)

#### AuthzSnapshotDTO (权限快照)
```
user: AuthzUserIdentityDTO          用户身份信息
roles: List<AuthzRoleDTO>           用户角色列表
menus: List<AuthzMenuDTO>           用户菜单树
pagePermissions: List<String>       页面权限 key 列表 (PAGE + MENU 类型)
buttonPermissions: List<String>     按钮权限 key 列表 (BUTTON 类型)
apiPermissions: List<String>        API 权限 key 列表 (API 类型)
```

#### AuthzUserIdentityDTO (用户身份)
```
userId, loginId, username, displayName, email, phone, mobile
company, chainGroup, subChainGroup, relateCompany
source, enabled, centerCode, organizationCode
roleCodes: List<String>
permissionKeys: List<String>
```

#### AuthzMenuDTO (菜单)
```
menuId, menuKey, parentKey, title, path, routeName, component
icon, menuType (AuthzMenuType), sortNo, legacyUrl
children: List<AuthzMenuDTO>    树形结构
```

#### AuthzPermissionDTO (权限)
```
permissionId, permissionKey, permissionName
permissionType (AuthzPermissionType)
resourceKey, enabled
```

### 2.3 权限类型 (枚举)

**AuthzPermissionType** — 四种权限粒度:
- `PAGE` — 页面级权限（前端路由可见性）
- `MENU` — 菜单级权限（与 PAGE 归入 pagePermissions）
- `BUTTON` — 按钮级权限（操作按钮显隐）
- `API` — 接口级权限（BFF 层权限校验）

**AuthzMenuType** — 菜单类型（具体枚举值待进一步扫描）

### 2.4 数据库表 (MyBatis)

**Mapper**: `AuthzRepositoryMapper.java` → `AuthzRepositoryMapper.xml`

| 表名 | 用途 |
|---|---|
| `authz_user` | 用户主表 |
| `authz_role` | 角色表 |
| `authz_menu` | 菜单树 |
| `authz_permission` | 权限定义 |
| `authz_user_role` | 用户-角色关联 (多对多) |
| `authz_role_permission` | 角色-权限关联 (多对多, 含 clientType 维度) |
| `authz_user_permission` | 用户-直接权限关联 (含 clientType 维度) |
| `authz_user_password` | 用户认证密码凭据 (2026-06-02 新增) |

#### 2.4.1 authz_user_password 表 (2026-06-02 新增)

**来源**: `rrsjk-admin-authz-impl/src/main/resources/db/migration_20260602_authz_user_password_reset.sql` (commit d9827ae, yumiao, 2026-06-02)
**证据等级**: 代码明确证明

密码不放入 `authz_user` 主表，独立存储认证凭据：

| 字段 | 类型 | 说明 |
|---|---|---|
| `user_id` | varchar(64) PK | 统一用户ID，FK → authz_user(user_id) |
| `password_hash` | varchar(255) NOT NULL | 密码哈希，禁止明文 |
| `updated_by` | varchar(64) | 最后重置人 |
| `updated_at` | datetime | 最后重置时间 |

- **密码编码**: Spring Security delegating password encoder 格式，例如 `{bcrypt}...`
- **新增权限**: `authz:user:password`（重置用户密码），仅授予 `ADMIN_AUTHZ_SUPER` 角色
- **新增 Dubbo API**:
  - `AuthzUserService.getPasswordCredential(loginIdOrUserId)` → `AuthzPasswordCredentialDTO`
  - `AuthzUserService.resetPassword(userId, rawPassword, operatorUserId)` → void
- **AuthzPasswordCredentialDTO**: userId, loginId, username, displayName, enabled, passwordHash

**关键查询逻辑**:
- 用户权限 = 角色权限 (`authz_role_permission`) + 直接权限 (`authz_user_permission`)
- 支持 `clientType` 维度隔离（不同客户端类型的权限独立管理）
- Snapshot 构建: 用户 → 角色 → 菜单 → 权限（按类型分类到 page/button/api）

### 2.5 Dubbo 注册中心

| 环境 | Zookeeper 地址 |
|---|---|
| dev | `10.2.192.154:2181` |
| prod | `10.2.160.242:2181, 10.2.160.243:2181, 10.2.160.244:2181` |
| local | `10.2.192.154:2181` |

## 3. rrsjk-admin-bff (BFF 层)

**来源**: `rrsjk-admin-bff` 全量通读 (2026-05-30)

- **技术栈**: Spring Boot 3.5.14, OAuth2 Client, Dubbo 3.2.15, Java 17
- **端口**: 8081 → **18092** (2026-05-30 生产部署调整)
- **Session Cookie**: `ADMIN_BFF_SESSION`
- **依赖**: `rrsjk-admin-authz-api` (Dubbo 客户端)

### 3.1 认证流程

```
用户访问 BFF → /api/app/auth/login?redirect=/xxx
  → 保存 redirect 到 session
  → 302 重定向到 /oauth2/authorization/admin-bff
  → auth-server 认证 (表单登录)
  → OAuth2 callback → AuthRedirectSuccessHandler
  → 读取 session redirect → 302 到 frontendBaseUrl + redirect
```

### 3.2 BFF API 端点

| 路径 | 方法 | 说明 |
|---|---|---|
| `/api/app/auth/login?redirect=xxx` | GET | 触发 OAuth2 登录 |
| `/api/app/auth/current-user` | GET | 获取当前用户 + 权限快照 |
| `/api/app/auth/logout` | POST | 登出 (清除 SecurityContext) |
| `/api/app/authz/snapshot` | GET | 获取权限快照 (roles, menus, page/button/api permissions) |

### 3.3 权限校验模式

所有业务 Controller 统一使用 `requirePermission(auth, permKey)` 模式:
```java
AuthzSnapshotDTO snapshot = snapshotClient.getSnapshot(userId);
if (snapshot 包含 permKey in pagePermissions|buttonPermissions|apiPermissions) → 放行
else → 403 FORBIDDEN
```

**降级策略**: authz-service 不可达时 → 拒绝访问（fail-closed）

### 3.4 CORS 配置

- 允许源: `${app.frontend-base-url}` + `http://localhost:8848`
- 允许方法: GET, POST, OPTIONS
- 允许路径: `/api/**`
- 允许凭证: true

## 4. rrsjk-admin-biff (拼写错误, 已废弃)

**来源**: `rrsjk-admin-biff` 全量通读 (2026-05-30)

- pom.xml 的 artifactId 也是 `rrsjk-admin-bff`
- Java 包名也是 `com.rrsjk.adminbff.*`
- 内容与 rrsjk-admin-bff 完全相同
- **结论**: 目录名拼写错误 (`biff` → `bff`), 扫描时应忽略

## 5. BFF 资产管理模块详细 API

**来源**: `rrsjk-admin-bff` 全量通读 (2026-05-30)

### 5.1 招银租赁 (CmbLeasingStationController)

**路径前缀**: `/api/app/asset-management/cmb-leasing-stations`

| 路径 | 方法 | 说明 | 权限 |
|---|---|---|---|
| `GET /` | 分页查询 | 招银金租电站列表 | `asset-management.cmb-leasing-stations.view` |
| `GET /{stationCode}` | 详情 | 电站详情 + 推送文件 + 操作日志 | 同上 |
| `GET /export` | 导出 | Excel 导出 (3000/页) | 同上 |
| `POST /close-order` | 关单 | 批量关闭订单 | 同上 |
| `POST /batch-audit-ok` | 批量审核通过 | 推送到招银 | 同上 |
| `POST /rework-files/import` | 导入返工文件 | 电站编码+文件名+文件链接 | 同上 |
| `POST /pull-up-status` | 拉取状态 | 异步线程执行 fourthSyncStationInfo | 同上 |

**导出字段** (多层级表头): 进件基本信息/融资方案/出租人信息/项目公司信息/房屋信息/电站信息 共 31 个字段

### 5.2 BT 资产管理 (BtAssetManagementController)

**路径前缀**: `/api/app/asset-management/bt-asset-management`

| 路径 | 说明 | 权限 |
|---|---|---|
| `GET /` | 分页查询 BT 股转模式及中核资产 | `asset-management.bt-asset-management.view` |
| `GET /export` | Excel 导出 | `asset-management.bt-asset-management.export` |
| `GET /template` | 下载导入模板 (.xls) | `asset-management.bt-asset-management.export` |
| `POST /import` | 导入数据 (.xls) | `asset-management.bt-asset-management.import` |
| `GET /import-failures` | 导出导入失败数据 | `asset-management.bt-asset-management.import` |

**导入模板字段**: 电站编码*, 交易单价(瓦/元)*, 运维单价(瓦/元)*

### 5.3 BT 基金资产投放明细 (BtFundAssetAllocateDetailController)

**路径前缀**: `/api/app/asset-management/bt-fund-asset-allocate-details`

| 路径 | 说明 | 权限 |
|---|---|---|
| `GET /` | 分页查询 | `asset-management.bt-fund-asset-allocate-details.view` |
| `GET /export` | Excel 导出 | `asset-management.bt-fund-asset-allocate-details.export` |
| `GET /template` | 导入模板 | `asset-management.bt-fund-asset-allocate-details.import` |
| `POST /import` | 导入数据 | `asset-management.bt-fund-asset-allocate-details.import` |
| `GET /import-failures` | 导出失败数据 | `asset-management.bt-fund-asset-allocate-details.import` |

**导入模板字段**: 电站编码*, 融资对象*, 交易时间*, 施工服务单价*, 设备单价*

### 5.4 BT 基金报表 (BtFundReportController)

**路径前缀**: `/api/app/asset-management/bt-fund-reports`

| 路径 | 说明 | 权限 |
|---|---|---|
| `GET /` | 分页查询回款报表 | `asset-management.bt-fund-reports.view` |
| `GET /options` | 下拉选项 | 同上 |
| `GET /{repaymentNo}/allocate-details` | 查询分配明细 | 同上 |
| `GET /{id}/records` | 回款记录 | 同上 |
| `POST /voucher-file` | 上传回款凭证 (OSS, 图片) | `asset-management.bt-fund-reports.upload` |
| `POST /{id}/voucher` | 提交回款凭证 | `asset-management.bt-fund-reports.upload` |
| `POST /{id}/sync-fap-status` | 同步 FAP 状态 | `asset-management.bt-fund-reports.view` |

**回款类型选项**: 服务费 (SERVICE_FEE), 设备费 (EQUIPMENT_FEE)
**回款状态选项**: 待回款 (PENDING), 部分回款 (PARTIAL), 待确认 (PENDING_CONFIRM), 已回款 (REPAID)

### 5.5 BT 项目公司交易主数据 (BtProjectTransactionController)

**路径前缀**: `/api/app/asset-management/bt-project-transactions`

| 路径 | 说明 | 权限 |
|---|---|---|
| `GET /` | 分页查询 | `asset-management.bt-project-transactions.view` |
| `GET /export` | Excel 导出 | `asset-management.bt-project-transactions.export` |
| `GET /template` | 导入模板 (含下拉校验) | `asset-management.bt-project-transactions.import` |
| `POST /import` | 导入数据 | `asset-management.bt-project-transactions.import` |
| `GET /import-failures` | 导出失败数据 | `asset-management.bt-project-transactions.import` |

**资产所属下拉**: 浦银, 招银, 中银, 越秀, 中核, LZ基金
**交易类型下拉**: 股转, 金租, 基金, REITS

### 5.6 EAM 资产 (LightEamAssetsController)

**路径前缀**: `/api/app/asset-management/eam-assets`

| 路径 | 说明 | 权限 |
|---|---|---|
| `GET /` | 分页查询 EAM 资产详情 | `asset-management.eam-assets.view` |
| `GET /export` | Excel 导出 | `asset-management.eam-assets.export` |
| `GET /project-company-options` | 项目公司下拉选项 | `asset-management.eam-assets.view` |

**导出字段 41 个**: 公司代码、汇总号、供应商、资产类型、电站编码、装机瓦数、含税价/未税价、发票号、EAM项目号/预算/科目/合同/跟踪码/行号/固定资产编号/转资金额/发票号/核销时间/收货单号、SAP采购单号/在建工程编号/采购订单行号/凭证号、业主信息、服务商信息

### 5.7 EAM 年度预算 (LightEamYearBudgetController)

**路径前缀**: `/api/app/asset-management/eam-year-budgets`

| 路径 | 说明 | 权限 |
|---|---|---|
| `GET /` | 分页查询 | `asset-management.eam-year-budgets.view` |
| `POST /sync` | 同步年度预算数据 | `asset-management.eam-year-budgets.sync` |

### 5.8 合同管理 (LightContractInfoController)

**路径前缀**: `/api/app/asset-management/contracts`

| 路径 | 说明 | 权限 |
|---|---|---|
| `GET /` | 分页查询合同 | `asset-management.contracts.view` |
| `POST /` | 创建合同 | `asset-management.contracts.add` |
| `GET /project-company-options` | 项目公司下拉 | contracts.view 或 contracts.add |
| `POST /upload-pdf` | 上传合同 PDF (OSS) | `asset-management.contracts.add` |
| `GET /files/download` | 下载合同文件 | `asset-management.contracts.view` |
| `GET /files/preview` | 预览合同文件 | `asset-management.contracts.view` |

### 5.9 经营性租赁资产 (EnergyLeasedStationAssetManagementController)

**路径前缀**: `/api/app/asset-management/energy-leased-station-asset-reports`

| 路径 | 说明 | 权限 |
|---|---|---|
| `GET /` | 分页查询 | `asset-management.energy-leased-station-asset-reports.view` |
| `GET /export` | Excel 导出 | `asset-management.energy-leased-station-asset-reports.export` |
| `GET /template` | 模板下载链接 (CDN) | `asset-management.energy-leased-station-asset-reports.view` |
| `POST /import` | 导入数据 (.xls) | `asset-management.energy-leased-station-asset-reports.import` |
| `PATCH /{id}` | 更新资产状态 | `asset-management.energy-leased-station-asset-reports.update` |
| `DELETE /{id}` | 删除记录 | `asset-management.energy-leased-station-asset-reports.delete` |

**导入字段**: 电站编码, 交易价格, 交易对象客户编码, 交易时间, 租赁开始时间, 租赁期限, 交易合同编码, 租赁合同编码

## 6. 权限体系完整映射

```
用户登录 (auth-server, port 9000)
  ↓ OAuth2 Authorization Code Flow
BFF (port 8081) 获取 token
  ↓ BFF 调用 /api/app/auth/current-user
AuthzSnapshotService.getSnapshot(userId) via Dubbo
  ↓ authz-service 查询 7 张表
返回 AuthzSnapshotDTO:
  - user: 用户身份 (userId, company, chainGroup, centerCode...)
  - roles: 角色列表
  - menus: 菜单树 (支持嵌套 children)
  - pagePermissions: 页面/菜单权限 keys
  - buttonPermissions: 按钮权限 keys
  - apiPermissions: API 权限 keys
  ↓
BFF 在每个业务 Controller 用 requirePermission(auth, permKey) 校验
```

## 7. BFF 生产部署配置 (2026-05-30)

**来源**: `rrsjk-admin-bff` commits by yumiao (2026-05-30)
**证据等级**: 配置明确证明

### 7.1 端口变更
- BFF 默认端口从 **8081** 调整为 **18092**
- 影响文件: `application-dev.yml`, `application-prod.yml`

### 7.2 Zookeeper 3.4 兼容性
- 生产注册中心使用 ZK 3.4，与 Dubbo 默认 Curator 不兼容
- 新增自定义实现:
  - `Zk34CompatibleCuratorZookeeperClient` — ZK 3.4 兼容的 Curator 客户端
  - `Zk34CompatibleCuratorZookeeperTransporter` — SPI 注册为 Dubbo 默认 ZookeeperTransporter
  - `META-INF/dubbo/internal/org.apache.dubbo.remoting.zookeeper.ZookeeperTransporter` — SPI 配置文件
- 通过 `pom.xml` 调整依赖版本实现兼容

### 7.3 生产配置对齐
- **Redis**: 生产环境默认 Redis 配置 (`application-prod.yml`)
- **Dubbo 注册**: authz-service Dubbo 注册 URL 对齐，含备用注册中心 URL
- **Trade API 依赖**: pom.xml 声明 trade API 依赖

### 7.4 电站管理 API 变更
- **移除**: `AuditImageRejectRequest` — 图片驳回开发环境专用 API 已删除
- **修改**: `BusinessAcceptanceAuditRequest`、`TechnicalAcceptanceAuditRequest` — 审核请求结构调整
- **新增**: 电站详情记录功能 (`LightStationDetailView`)
- **对齐**: `LightStopStationController` 停电站字段与 master API 对齐

## 8. BFF 操作日志审计 (2026-06-01 新增)

**来源**: `rrsjk-admin-bff` commits by yumiao (2026-06-01), commit `ec6742755987115ab2bde240c85a22ab7869b45`
**证据等级**: 代码明确证明

BFF 层新增了完整的操作日志审计体系，通过 Dubbo 调用后端服务记录管理后台用户操作。

### 8.1 架构

```
AuthController/AuthzAdminController
  ↓ @OperationLog AOP 切面
OperationLogAspect
  ↓ 异步提交
OperationLogAsyncConfig (线程池)
  ↓
AdminOperationLogClient → DubboAdminOperationLogClient
  ↓ Dubbo
rrsjk-light-service / rrsjk-admin-authz-service (后端记录)
```

### 8.2 核心组件

| 组件 | 说明 |
|---|---|
| `OperationLog` | 自定义注解，标注在 Controller 方法上 |
| `OperationLogAspect` | AOP 切面，拦截 @OperationLog 注解方法 |
| `OperationBusinessType` | 业务类型枚举 (INSERT/UPDATE/DELETE/GRANT/OTHER 等) |
| `OperationOperatorType` | 操作人类型枚举 |
| `OperationLogSanitizer` | 日志内容脱敏/清理工具 |
| `AdminLogRecordService` | 日志记录业务服务 |
| `LoginLogRecorder` | 登录/登出日志记录器 |
| `DubboAdminOperationLogClient` | Dubbo 客户端，调用后端日志服务 |
| `OperationLogDubboConfig` / `OperationLogDubboProperties` | Dubbo 共享配置 |

### 8.3 登录审计

- **登录成功**: `AuthRedirectSuccessHandler.onAuthenticationSuccess()` → `loginLogRecorder.recordLoginSuccess()`
- **登录失败**: `AuthRedirectFailureHandler.onAuthenticationFailure()` → `loginLogRecorder.recordLoginFailure()`
- **登出**: `AuthController.logout()` → `loginLogRecorder.recordLogout()`

### 8.4 权限管理操作日志

`AuthzAdminController` 所有写操作已标注 `@OperationLog`:

| 接口 | @OperationLog 标注 |
|---|---|
| `POST /roles` | `title="权限管理-新增角色", businessType=INSERT, saveResponseData=true` |
| `PUT /roles/{roleCode}` | `title="权限管理-修改角色", businessType=UPDATE` |
| `DELETE /roles/{roleCode}` | `title="权限管理-删除角色", businessType=DELETE` |
| `PUT /roles/{roleCode}/permissions` | `title="权限管理-角色授权", businessType=GRANT` |

### 8.5 依赖

- `pom.xml` 新增: `spring-boot-starter-aop`、`rrsjk-admin-operation-log-api` (1.0.0-SNAPSHOT)、`rrsjk-light-data-api`

## 9. BFF 数据大屏报表模块 (2026-06-01 新增)

**来源**: `rrsjk-admin-bff` datadashboard 模块, commits by yumiao (2026-05-31 ~ 2026-06-01)
**证据等级**: 代码明确证明

### 9.1 报表 Controller 列表

| Controller | 路径前缀 | 说明 |
|---|---|---|
| `EnergyCenterIncomeDayController` | `/api/app/data-dashboard/energy-center-income-days` | 能源中心收入日报 |
| `EnergySummaryDayController` | `/api/app/data-dashboard/energy-summary-days` | 能源汇总日报 |
| `StationReportController` | `/api/app/data-dashboard/station-reports` | 电站报表 |
| `StationCostReportController` | `/api/app/data-dashboard/station-cost-reports` | 电站成本报表 |
| `WarningStationDetailController` | `/api/app/data-dashboard/warning-station-details` | 超期电站详情 |
| `SaleOrderCompanySwitchController` | `/api/app/data-dashboard/sale-order-company-switch` | 销售订单公司切换 |
| `CustomerOperationController` | `/api/app/data-dashboard/customer-operations` | 客户运营 |
| `CapitalTradeReportController` | `/api/app/data-dashboard/capital-trade-reports` | 资方交易报表 |
| `CapitalTradeProjectCompanyReportController` | `/api/app/data-dashboard/capital-trade-project-company-reports` | 资方交易项目公司报表 |
| `JointInventoryReportController` | `/api/app/data-dashboard/joint-inventory-reports` | 联合库存报表 |
| `SubBaseDataController` | `/api/app/data-dashboard/sub-base-data` | 分中心基础数据 |
| `SubBuildDataController` | `/api/app/data-dashboard/sub-build-data` | 分中心建设数据 |
| `SubOperationDataController` | `/api/app/data-dashboard/sub-operation-data` | 分中心运营数据 |

### 9.2 标准模式

每个报表模块遵循统一的 Client/Controller/Request/View 四层结构：
- `*Client`: Dubbo 客户端，调用后端微服务
- `*Controller`: REST 端点，接收查询请求
- `*QueryRequest`: 查询参数 DTO
- `*View`: 返回视图 DTO

## 10. BFF 服务商与派单管理模块 (2026-06-01 新增)

**来源**: `rrsjk-admin-bff` partnermanagement 模块, commits by yumiao (2026-06-01)
**证据等级**: 代码明确证明

### 10.1 Controller 列表

| Controller | 路径前缀 | 说明 | 依赖 Client |
|---|---|---|---|
| `ConstructionTeamController` | `/api/app/partner-management/construction-teams` | 施工队管理 | `LightConstructionTeamClient` |
| `DispatchWorkOrderController` | `/api/app/partner-management/dispatch-work-orders` | 派单管理 | `LightWorkOrderClient` |
| `OrderUserController` | `/api/app/partner-management/order-users` | 订单用户 | `LightOrderUserClient` |
| `PartnerController` | `/api/app/partner-management/partners` | 合作方管理 | `LightProjectPartnerClient` |
| `ServiceProviderStaffController` | `/api/app/partner-management/service-provider-staff` | 服务商员工 | `LightSpStaffClient` |
| `SubServiceProviderController` | `/api/app/partner-management/sub-service-providers` | 子服务商管理 | `LightSubSpClient` |

### 10.2 调用链

```
rrsjk-admin-bff (BFF, REST)
  ↓ Dubbo Client
rrsjk-light-service (Dubbo 服务提供者)
  → 调用现有 light 模块的 Service 层
```

## 11. BFF 发电管理模块 (2026-06-01 恢复)

**来源**: `rrsjk-admin-bff` generationmanagement 模块, commits by yumiao (2026-06-01)
**证据等级**: 代码明确证明

- **恢复**: `InverterChartClient` — 逆变器图表数据 Dubbo 客户端
- **恢复**: `LightInveterClient` — 逆变器数据 Dubbo 客户端
- **新增**: `WeatherClient` — 天气数据 Dubbo 客户端
- **修改**: `InverterController` — 空状态文本处理
- **修改**: `StationElectricityController` — 电站发电状态空值处理

## 12. BFF 分中心管理迁移 (2026-06-03 新增)

**来源**: `rrsjk-admin-bff` subcentermanagement 模块, commits by yumiao (2026-06-03), merge `feature/202606/subcenter-management-migration`
**证据等级**: 代码明确证明

旧 CBS 分中心管理 (`cbs-web` → `SysSubCenterController`) 正在迁移到新一代 BFF 架构。

### 12.1 模块结构

```
src/main/java/com/rrsjk/adminbff/subcentermanagement/
├── client/
│   ├── SysSubCenterClient.java      — Dubbo 调用 system-service (分中心 CRUD)
│   ├── SystemUserClient.java        — Dubbo 调用 system-service (用户查询)
│   ├── SysPartyClient.java          — Dubbo 调用 system-service (团体/组织架构)
├── controller/
│   ├── SubCenterController.java     — 分中心管理 REST 端点
│   ├── PartyController.java         — 团体管理 REST 端点
│   └── PartyUserController.java     — 团体用户管理 REST 端点
├── request/
│   ├── SubCenterQueryRequest.java
│   ├── SubCenterUserAddRequest.java
│   ├── SubCenterUserRemoveRequest.java
│   ├── PartyQueryRequest.java
│   ├── PartySaveRequest.java
│   ├── PartyStatusRequest.java
│   ├── PartyUserQueryRequest.java
│   ├── PartyUserSaveRequest.java
│   └── PartyUserStatusRequest.java
└── view/
    ├── SubCenterView.java
    ├── SubCenterUserView.java
    ├── SubCenterSelectableUserView.java
    ├── PartyView.java
    ├── PartySelectableUserView.java
    ├── PartyUserView.java
    └── PartyUserOptionsView.java
```

### 12.2 调用链

```
rrsjk-admin-web-next (Vue3 前端)
  ↓ REST
rrsjk-admin-bff (subcentermanagement Controller)
  ↓ Dubbo Client
system-service (SysPartyService, SystemService, V3BranchRegionService)
```

### 12.3 管理范围

- **分中心 (SubCenter)**: 查询、分中心用户添加/移除、可选用户列表
- **团体 (Party)**: 查询、新增/编辑、启用/禁用
- **团体用户 (PartyUser)**: 查询、新增/编辑、启用/禁用、可选用户列表

### 12.4 BFF 管理员密码重置 API (2026-06-02)

**来源**: `rrsjk-admin-bff` → `AuthzAdminController.java` (commit f1a969b, yumiao, 2026-06-02)

- **新增端点**: `POST /api/admin/authz/users/{userId}/password-reset`
- **权限**: `authz:user:password` (仅 `ADMIN_AUTHZ_SUPER` 角色)
- **请求体**: `UserPasswordResetRequest` (rawPassword)
- **调用链**: BFF → Dubbo → `AuthzUserService.resetPassword(userId, rawPassword, operatorUserId)`
- **安全**: BFF 强制当前登录主体必须为 admin

### 12.5 登录日志改造 (2026-06-02)

**来源**: `rrsjk-admin-bff` operationlog 模块, commits by yumiao (2026-06-02)

- **移除**: `LoginLogRecorder` (旧登录日志记录器)
- **新增**: `@OperationLog` 注解标注在登录/登出 Controller 方法上
  - `AuthController.logout()` → `@OperationLog(title="后台退出", loginType="LOGOUT", loginResult=SUCCESS)`
  - `AuthRedirectSuccessHandler.onAuthenticationSuccess()` → `@OperationLog(title="后台登录", loginType="LOGIN", loginResult=SUCCESS)`
  - `AuthRedirectFailureHandler.onAuthenticationFailure()` → `@OperationLog(title="后台登录", loginType="LOGIN", loginResult=FAILURE)`
- **新增**: `OperationLogTarget.LOGIN` — 登录审计目标类型
- **新增**: `LoginLogResult` — 登录结果枚举 (SUCCESS/FAILURE)
- **新增**: `OperationLogAdminController` — 操作日志查询管理端点
