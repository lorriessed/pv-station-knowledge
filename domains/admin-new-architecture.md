# Admin 新一代认证架构

更新时间: 2026-05-30

## 详细说明已迁移

本文档为概览索引，完整认证授权体系知识详见 **`domains/admin-authz.md`** (2026-05-30 全量通读创建)。

## 背景

管理后台（CBS）正在从旧版的 `rrsjk-admin-web`（Spring MVC + EasyUI + FTL + Shiro）迁移到基于 OAuth2/OIDC 的新架构。

## 新架构组件

### 1. rrsjk-admin-auth-server
- **角色**: OAuth2/OIDC 认证服务器（Authorization Server）
- **技术栈**: Spring Boot 3.5.14, **Java 21** (2026-06-15 升级)
- **端口**: 9000
- **Session 存储**: Redis (spring-session-data-redis)
- **负责人**: 于淼 (yumiao)
- **详见**: `domains/admin-authz.md` → 第 1 节

### 2. rrsjk-admin-authz-service
- **角色**: 授权服务（Authorization Service）
- **技术栈**: Spring Boot 3.5.14, Dubbo 3.2.15, MyBatis 3.5.19, Zookeeper
- **Java 版本**: **Java 21** (2026-06-15 升级)
- **端口**: Dubbo 服务（-1 随机端口）
- **数据库**: `rrsjk_admin_authz` @ pv-mysql-prod (rm-m5ebm056ct14p18zu)
- **10 张表**: authz_user, authz_role, authz_menu, authz_permission, authz_user_role, authz_role_permission, authz_user_permission, authz_user_password, authz_sub_center, authz_user_sub_center
- **负责人**: 于淼 (yumiao)
- **详见**: `domains/admin-authz.md` → 第 2 节

### 3. rrsjk-admin-bff
- **角色**: Backend for Frontend（BFF 层）
- **技术栈**: Spring Boot 3.5.14, **Java 21**, OAuth2/OIDC Client, Dubbo 2.7.4.1
- **端口**: 8081
- **Session Cookie**: `ADMIN_BFF_SESSION`
- **业务模块**: **48 个模块, 376 个 Controller** — 资产管理、结算、仓储、电站、自有财务、商品、财务、越秀、零碳、招银、中银、华电、华融、工商业EPC 等
- **API 前缀**: `/api/admin/` (2026-06 从 `/api/app/` 统一改为 `/api/admin/`)
- **负责人**: 于淼 (yumiao)
- **详见**: `domains/admin-authz.md` → 第 3、5、10 节

### 4. rrsjk-admin-biff (已废弃)
- **状态**: 拼写错误目录，pom.xml artifactId 也是 `rrsjk-admin-bff`
- **处理**: 扫描时忽略，不纳入统计

## 迁移路径

```
旧架构: rrsjk-admin-web (Shiro + FTL) → 用户直接访问
新架构: rrsjk-admin-web-next (前端) → rrsjk-admin-bff (OAuth2 Client) → rrsjk-admin-auth-server (认证) + rrsjk-admin-authz-service (授权)
```

## 数据库

| 服务 | 数据库 | 实例 |
|------|--------|------|
| rrsjk-admin-authz-service | rrsjk_admin_authz | pv-mysql-prod (rm-m5ebm056ct14p18zu) |
| rrsjk-admin-auth-server | 无独立数据库 | OAuth2 配置内嵌 |
| rrsjk-admin-bff | 无独立数据库 | 纯代理层 |

## OAuth2 客户端配置

### admin-bff (管理后台 BFF)
- client-id: `admin-bff`
- Access Token TTL: **24 小时**
- Refresh Token TTL: **7 天**
- redirect-uri: `${app.bff-base-url}/login/oauth2/code/admin-bff`

### admin-mobile (移动端)
- client-id: `admin-mobile`
- Access Token TTL: **2 小时**
- Refresh Token TTL: **30 天**
- PKCE: 必须 (require-proof-key: true)
- redirect-uri: `rrsjkadmin://oauth/callback`, `com.rrsjk.admin://oauth/callback`

## 权限类型 (AuthzPermissionType)
- `PAGE` — 页面级权限
- `MENU` — 菜单级权限（与 PAGE 同归 pagePermissions）
- `BUTTON` — 按钮级权限
- `API` — 接口级权限

## BFF 权限校验模式

所有业务 Controller 统一使用 `requirePermission(auth, permKey)` → `AuthzSnapshotService.getSnapshot(userId)` via Dubbo → 匹配 pagePermissions/buttonPermissions/apiPermissions → fail-closed（authz-service 不可达时拒绝访问）。
