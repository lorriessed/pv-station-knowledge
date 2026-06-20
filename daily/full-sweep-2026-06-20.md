# PVS 全量代码通读报告 2026-06-20

## 通读概况

- **轮次**: 第 36 轮
- **本次通读**: 5 个仓库
- **仓库列表**: rrs-dispenser-operator-android3, rrs-dispenser-operator-ios3, rrsjk-admin-app-bff, rrsjk-admin-app-service, rrsjk-admin-operation-log-service

## 仓库分类

### 核心业务仓库 (3个，首次通读)

| 仓库 | 业务职责 | 技术栈 | 状态 |
|---|---|---|---|
| rrsjk-admin-app-bff | 分中心 APP 的 BFF 层 (OAuth2 Resource Server) | Spring Boot 3.5.14, Java 17, Dubbo 2.7.4.1 | ✅ 活跃 (2026-06-02) |
| rrsjk-admin-app-service | 分中心 APP 后端服务 (会话/推送/电站查询) | Spring Boot 3.5.14, Java 17, Redis, MyBatis 多数据源 | ✅ 活跃 (2026-06-05) |
| rrsjk-admin-operation-log-service | 集中操作日志服务 (登录/操作/正文) | Spring Boot 2.7.18, Java 8, MyBatis | ✅ 活跃 (2026-06-02) |

### 外围遗留仓库 (2个，快速分类)

| 仓库 | 分类 | 原因 |
|---|---|---|
| rrs-dispenser-operator-android3 | 非 PVS 业务 | 水站买家端 Android App (com.rrs.waterstationbuyer)，最后提交 2024-07-08 |
| rrs-dispenser-operator-ios3 | 非 PVS 业务 | 水站买家端 iOS App，最后提交 2024-07-08 |

## 关键业务发现

### 1. 分中心 APP 后端架构 (代码明确证明)

分中心移动端形成完整的认证-授权-会话-推送体系:

```
分中心 APP → rrsjk-admin-app-bff (port 8082)
  ├── 认证: rrsjk-admin-auth-server (port 9000, OAuth2/OIDC)
  ├── 授权: rrsjk-admin-authz-service (Dubbo, 权限/菜单快照)
  ├── 会话: rrsjk-admin-app-service (Redis, Token hash 存储)
  ├── 推送: Redis Pub/Sub (admin:push:event channel)
  └── 审计: rrsjk-admin-operation-log-service (MySQL)
```

与 Web 端 (rrsjk-admin-bff port 8081) 平行但独立，共享 auth-server 和 authz-service。

### 2. 会话管理 (AppSessionService) (代码明确证明)

- **Token 安全**: BFF 只存 SHA-256 hash，不存原文
- **状态机**: ONLINE → LOGOUT / KICKED
- **Token 轮换**: rotateToken 支持原子替换 tokenHash/refreshTokenHash
- **踢下线**: kickSession → 标记 KICKED + Redis Pub/Sub 通知客户端
- **审计**: 所有认证事件 (登录成功/失败/登出/踢下线) 记录到 admin_login_log / admin_oper_log

### 3. 推送事件机制 (AdminPushEventService) (代码明确证明)

通过 Redis Pub/Sub 推送事件到 APP 客户端:
- `KICKED` (auth:kicked) — 被踢下线
- `MENU_CHANGED` (menu:changed) — 菜单变更
- `SYSTEM_NOTICE` (system:notice) — 系统公告
- `HOME_DATA_CHANGED` (home:summary) — 首页数据变更

Payload 严格限制: 最多 12 entry, key≤64, value≤512, total≤2048

### 4. 电站数据查询 (代码明确证明)

admin-app-service 提供 3 个电站查询 Dubbo 服务，供 APP 首页使用:
- `LightStationService` — 电站列表/详情 (rrsjk_light 库)
- `LightStationElecService` — 发电数据 (rrsjk_light_data 库)
- `ElecWarningStationService` — 电站预警 (SelectDB ADS, 生产 only)

### 5. 操作日志表结构 (代码明确证明)

3 张表:
- `admin_oper_log` — 操作日志 (title/method/url/params/result/cost_time)
- `admin_login_log` — 登录日志 (user/status/ip/browser/os/login_type)
- `admin_log_body_detail` — 日志正文 (request_body/response_body, 支持截断标记)

数据库: `rrsjk_admin_operation_log`

### 6. LightStationDTO 完整状态枚举 (代码明确证明)

从 `LightStationDTO.java` 注释中提取 26+ 个电站状态值，包括 3 个已废弃状态:
- 已废弃: `APPLY_CHECK`, `WAIT_CHECK`, `WAIT_FINAL_AUDIT`, `FINAL_AUDIT_REJECT`
- 核心流程: INIT → WAIT_AUDIT → WAIT_CONFIG → WAIT_ORDER → ROADWORKING → COMPLETE_WAIT_AUDIT → WAIT_TECH_CHECK → WAIT_UPLOAD_GRID_INFO → WAIT_FIRST_AUDIT → ENABLE

## 知识库更新

| 文件 | 操作 | 内容 |
|---|---|---|
| `domains/admin-app-service.md` | **新建** | Admin App 完整架构: BFF/API/会话/推送/日志/电站查询 |
| `domain-router.md` | 追加 | Admin App 移动端服务路由条目 |
| `data/api-endpoints.md` | 追加 | 11 个 Admin App BFF API 端点 |
| `state/full_sweep.json` | 更新 | 5 个仓库标记为已完成, 轮次→36 |

## 统计

- 总仓库数: 138
- 已通读: 137/138 (99.3%)
- 从未通读: 6 个 (可能包含重命名后的新目录)
- 本次新建 domain 文件: 1 个
- 本次更新 KB 文件: 3 个
