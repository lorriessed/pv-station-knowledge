# Admin 新一代认证架构

更新时间: 2026-05-29

## 背景

管理后台（CBS）正在从旧版的 `rrsjk-admin-web`（Spring MVC + EasyUI + FTL + Shiro）迁移到基于 OAuth2/OIDC 的新架构。

## 新架构组件

### 1. rrsjk-admin-auth-server
- **角色**: OAuth2/OIDC 认证服务器（Authorization Server）
- **技术栈**: Spring Boot 3.5.14, Java 17
- **负责人**: 于淼 (yumiao)
- **功能**: 处理管理后台用户的登录认证、Token 签发

### 2. rrsjk-admin-authz-service
- **角色**: 授权服务（Authorization Service）
- **技术栈**: Spring Boot 3.5.14, Java 17
- **负责人**: 于淼 (yumiao)
- **功能**: 处理权限校验、角色管理、资源访问控制

### 3. rrsjk-admin-bff
- **角色**: Backend for Frontend（BFF 层）
- **技术栈**: Spring Boot 3.5.14, Java 17, OAuth2/OIDC Client
- **负责人**: 于淼 (yumiao)
- **功能**: 作为前端代理，处理 OAuth2 登录回调、Token 管理、API 路由转发

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
| rrsjk-admin-auth-server | 待确认 | 可能无独立数据库 |
| rrsjk-admin-bff | 待确认 | 可能无独立数据库 |

## 相关仓库

| 仓库 | 状态 |
|------|------|
| `rrsjk-admin-web` | 旧版管理后台（EasyUI + FTL） |
| `rrsjk-admin-web-next` | 新版管理后台前端 |
| `rrsjk-oauth2-web` | OAuth2 Web 客户端（可能相关） |
| `rrsjk-admin-auth-server` | 认证服务器（新） |
| `rrsjk-admin-authz-service` | 授权服务（新） |
| `rrsjk-admin-bff` | BFF 层（新） |
