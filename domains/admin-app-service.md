# Admin App Service (分中心移动端后台服务)

更新时间: 2026-06-20
证据等级: 代码明确证明
通读仓库: rrsjk-admin-app-bff, rrsjk-admin-app-service, rrsjk-admin-operation-log-service

## 架构概览

分中心移动端（subcenter app）的后端服务栈，与 Web 端 admin-bff/admin-authz 平行但独立：

```
分中心 APP (Flutter/原生)
  → rrsjk-admin-app-bff (BFF, port 8082, OAuth2 Resource Server)
    → rrsjk-admin-app-service (Dubbo, 会话/推送/配置/电站查询)
    → rrsjk-admin-authz-service (Dubbo, 权限快照)
    → rrsjk-admin-auth-server (OAuth2 Token 签发/刷新)
    → rrsjk-admin-operation-log-service (Dubbo, 操作日志持久化)
```

**与 Web 端对比**:
- Web 端: rrsjk-admin-bff (port 8081) + rrsjk-admin-web-next (Vue3)
- App 端: rrsjk-admin-app-bff (port 8082) + 分中心 APP
- 共享: rrsjk-admin-auth-server (9000), rrsjk-admin-authz-service

**负责人**: 于淼 (yumiao), 2026-06-01 初始化; alone (lilong) 参与数据源集成

## 1. rrsjk-admin-app-bff (BFF 层)

**来源**: rrsjk-admin-app-bff 全量通读 (2026-06-20)
**技术栈**: Spring Boot 3.5.14, Java 17, OAuth2 Resource Server, Dubbo 2.7.4.1
**端口**: 8082

### 1.1 API 端点

| 路由 | 方法 | 功能 | 认证 |
|---|---|---|---|
| `/api/app/auth/login-config` | GET | 获取 OAuth2 登录配置 (端点/clientId/scope) | 公开 |
| `/api/app/auth/login-url` | POST | 生成 PKCE 授权 URL | 公开 |
| `/api/app/auth/login` | POST | 密码登录 (→ auth-server /api/app/auth/password-token) | 公开 |
| `/api/app/auth/code-exchange` | POST | 授权码换 Token | 公开 |
| `/api/app/auth/token-refresh` | POST | 刷新 Token | 公开 |
| `/api/app/auth/current-user` | GET | 获取当前用户信息+权限+组织 | JWT |
| `/api/app/auth/logout` | POST | 登出 (销毁 session) | JWT |
| `/api/app/client/context` | POST | 更新客户端上下文 (设备/推送Token) | JWT |
| `/api/app/online-users` | GET | 查询在线用户列表 (分页) | JWT |
| `/api/app/permission/snapshot` | GET | 获取权限快照 (菜单+页面/按钮/API权限) | JWT |
| `/api/app/menus` | GET | 获取菜单树 | JWT |

### 1.2 认证流程

**密码登录**:
```
APP → POST /api/app/auth/login (username, password, deviceId)
  → BFF → POST auth-server/api/app/auth/password-token
  → 获得 access_token + refresh_token
  → BFF → Dubbo AppSessionService.createSession(tokenHash=SHA256(access_token))
  → 返回 sessionId + tokens
```

**PKCE 授权码登录**:
```
APP → GET /api/app/auth/login-config (获取端点)
APP → POST /api/app/auth/login-url (codeChallenge, redirectUri)
  → 返回 authorizationUrl
APP → 用户浏览器跳转 → auth-server /oauth2/authorize
APP → POST /api/app/auth/code-exchange (code, codeVerifier, redirectUri)
  → BFF → POST auth-server/oauth2/token (grant_type=authorization_code)
  → 返回 tokens
```

**Token 刷新**:
```
APP → POST /api/app/auth/token-refresh (refreshToken)
  → BFF → POST auth-server/oauth2/token (grant_type=refresh_token)
```

**Token 轮换 (Rotate)** (2026-06-04 新增):
```
DubboAppSessionService.rotateToken(oldRefreshTokenHash, newTokenHash, newRefreshTokenHash, newExpiresIn)
  → 查找旧 session → 更新 tokenHash/refreshTokenHash → Redis 原子替换
```

### 1.3 安全配置

- **Session 策略**: STATELESS (无 HTTP Session)
- **CSRF**: 禁用
- **CORS**: 可配置 (默认 http://localhost:8848)
- **JWT 验证**: issuer-uri 指向 auth-server
- **Token 存储**: BFF 只存 SHA-256 hash，不存原文

### 1.4 Dubbo 依赖

| 服务接口 | 来源 | 用途 |
|---|---|---|
| `AppSessionService` | rrsjk-admin-app-api | 会话管理 |
| `AppAuthEventLogService` | rrsjk-admin-app-api | 认证事件审计 |
| `AuthzSnapshotService` | rrsjk-admin-authz-api | 权限/菜单快照 |

### 1.5 异常处理

- `SESSION_KICKED` → 401 "当前登录已被踢下线，请重新登录"
- `SESSION_EXPIRED` → 401 "登录已过期，请重新登录"
- `UNAUTHORIZED` → 401 "未认证或登录已过期"
- `FORBIDDEN` → 403 "无权访问该资源"
- `BAD_REQUEST` → 400 "请求参数错误"
- `SYSTEM_ERROR` → 500 "系统异常，请稍后重试"

## 2. rrsjk-admin-app-service (核心服务)

**来源**: rrsjk-admin-app-service 全量通读 (2026-06-20)
**技术栈**: Spring Boot 3.5.14, Java 17, Dubbo Provider, Redis (Lettuce), MyBatis, 多数据源
**模块**: rrsjk-admin-app-api (接口+DTO) + rrsjk-admin-app-impl (实现)

### 2.1 Dubbo 服务接口

#### AppSessionService (会话管理)

**存储**: Redis (StringRedisTemplate)
**Key 模式**: 通过 AppSessionStore 管理

| 方法 | 功能 |
|---|---|
| `createSession(CreateAppSessionRequest)` | 创建会话，生成 sessionId (UUID)，存 Redis，记录登录成功事件 |
| `validateSession(ValidateAppSessionRequest)` | 通过 tokenHash 查找会话，返回有效性 |
| `updateClientContext(UpdateClientContextRequest)` | 更新设备信息/推送Token/客户端版本 |
| `logout(LogoutAppSessionRequest)` | 标记会话为 LOGOUT 状态，记录登出事件 |
| `queryOnlineSessions(QueryOnlineSessionsRequest)` | 分页查询在线会话 (支持 userId/keyword/deviceId/status/时间范围过滤) |
| `kickSession(KickAppSessionRequest)` | 踢下线：标记 KICKED + Redis Pub/Sub 通知 + 记录审计事件 |
| `rotateToken(RotateAppSessionRequest)` | Token 轮换：原子替换 tokenHash/refreshTokenHash |

**会话状态机** (`AppSessionStatus`):
- `ONLINE` → 正常在线
- `LOGOUT` → 已登出
- `KICKED` → 被踢下线

**会话记录字段** (`AppSessionRecord`):
sessionId, tokenHash, refreshTokenHash, userId, userName, clientType, deviceId, clientVersion, os, deviceModel, pushToken, sourceIp, userAgent, loginTime, lastActiveTime, expiresAt, status, traceId

#### AdminPushEventService (推送事件)

**机制**: Redis Pub/Sub
**Channel**: `admin:push:event` (可配置)

| 事件类型 (PushEventType) | 主题 (PushTopic) | 功能 |
|---|---|---|
| `KICKED` | `auth:kicked` | 踢下线通知 (必须带 sessionId) |
| `MENU_CHANGED` | `menu:changed` | 菜单变更通知 |
| `SYSTEM_NOTICE` | `system:notice` | 系统公告 |
| `HOME_DATA_CHANGED` | `home:summary` | 首页数据变更 (必须带 targetDataScopes/targetOrgCodes + payload) |

**Payload 限制**:
- 最多 12 个 entry
- Key 最长 64 字符, Value 最长 512 字符
- 总长度不超过 2048 字符
- HOME_DATA_CHANGED 允许的 key: module, refreshHint, summary, hint, businessId, businessType, occurredReason

#### AppConfigService (应用配置)

返回运行时配置:
- `featureFlags`: menuEnabled=true, sseEnabled=true
- `grayConfig`: 空
- `versionCompatibility`: minSupportedVersion=1.0.0, recommendedVersion=1.0.0

#### AppAuthEventLogService (认证审计日志)

| 方法 | 功能 |
|---|---|
| `recordAuthEvent(RecordAuthEventRequest)` | 记录认证事件 (登录成功/失败/登出/踢下线) |
| `queryAuthEventLogs(QueryAuthEventLogsRequest)` | 分页查询审计日志 (合并 login_log + oper_log) |

**事件类型** (`AuthEventType`):
- `LOGIN_SUCCESS` / `LOGIN_FAILURE` → 写入 admin_login_log
- `LOGOUT` / `KICK` → 写入 admin_oper_log (title="App 安全审计")

### 2.2 光伏电站查询服务

**来源**: rrsjk-admin-app-service/impl/service/light/

#### LightStationService (电站列表查询)

**数据源**: `spring.light.datasource` → rrsjk_light 库
**Mapper**: `LightStationMapper` (mybatis/mapper/light/*.xml)

| 方法 | 功能 |
|---|---|
| `getStationById(Long id)` | 按 ID 查电站 |
| `getStationByCode(String stationCode)` | 按电站编码查 |
| `queryStationList(param, status, name, pageNo, pageSize)` | 分页查询 (分中心+状态+姓名过滤) |
| `countStations(param, status, name)` | 计数 |

**LightStationDTO 字段** (关键):
- 基础: id, stationCode, vCode, elecNo
- 业主: name, idCardNumber, phone
- 地址: provinceName, cityName, regionName, streetName, address
- 房屋: houseType (平顶屋flat/斜屋顶slope), roofArea
- 服务商: spId, spName, spMemberId, spMemberName, spLoginId
- 分中心: subCenterCode, subCenterName
- 电站信息: stationType, projectName, mode (HR华润/YX越秀), assetOwnership
- 时间: applyAt, completeAt, finishAt, createdAt, updatedAt
- **status**: 26+ 枚举值 (详见下方状态机)

**LightStationDTO.status 枚举值** (代码注释明确证明):
```
INIT: 待提交审核
WAIT_AUDIT: 待审核
WAIT_THIRD_AUDIT: 待审核
AUDIT_REJECT: 驳回
WAIT_CONFIG: 审核完成待配方案
WAIT_ORDER: 待下单
ROADWORKING: 施工中
ROADWORK_CONFIRM: 施工信息待确认
ROADWORK_REJECT: 施工信息驳回
COMPLETE_WAIT_AUDIT: 完工确认审核
COMPLETE_AUDIT_REJECT: 完工确认审核驳回
WAIT_TECH_CHECK: 待技术审核
APPLY_CHECK: 施工完成待申请并网验收 (已废弃)
TECH_CHECK_REJECT: 技术审核驳回
WAIT_OFF_LINE_CHECK: 待线下验收
WAIT_CHECK: 待验收 (已废弃)
WAIT_UPLOAD_GRID_INFO: 待提交并网验收资料
WAIT_FIRST_AUDIT: 待商务审核
FIRST_AUDIT_REJECT: 商务审核驳回
OFF_LINE_CHECK_REJECT: 现场验收驳回
WAIT_FINAL_AUDIT: 待终审二验 (已废弃)
FINAL_AUDIT_REJECT: 终审二验驳回 (已废弃)
ENABLE: 已完成
DISABLE: 删除
STOP: 已终止
REPURCHASE: 已回购
```

#### LightStationElecService (电站发电数据)

**数据源**: `spring.elec.datasource` → rrsjk_light_data 库
**Mapper**: `LightStationElecMapper` (mybatis/mapper/elec/*.xml)

| 方法 | 功能 |
|---|---|
| `getById(Long id)` | 按 ID 查发电数据 |
| `getByStationCode(String stationCode)` | 按电站编码查 |
| `queryList(param, state, pageNo, pageSize)` | 分页查询 (分中心+在线状态过滤) |
| `count(param, state)` | 计数 |

**LightStationElecDTO 字段**:
- 电站: stationCode, stationName, mobile, stationProvinceName/CityName/RegionName/Address
- 状态: stationStatus, state (1:在线, 2:离线, 3:报警)
- 功率: power(装机功率kW), modulePower(组件总容量kW), pac(实时功率kW)
- 电量: elecDay(当日kWh), elecMonth(当月kWh), elecYear(当年kWh), elecTotal(累计kWh)
- 其他: fullHour(满发小时数), dataTimeAt(最后更新时间)
- 归属: subCenterCode/Name, spId/Name, projectCompanyName

#### ElecWarningStationService (电站预警)

**数据源**: `spring.ads.datasource` → SelectDB (ADS, 生产环境 only, 本地无法访问)
**Mapper**: `ElecWarningStationMapper` (mybatis/mapper/ads/*.xml)
**注意**: 该数据源标记为 `@Lazy`，因测试环境连接的是生产库

| 方法 | 功能 |
|---|---|
| `getByKey(stationCode, inverterSn, dayAt)` | 按三要素查预警记录 |
| `queryList(param, status, pageNo, pageSize)` | 分页查询预警列表 |
| `count(param, status)` | 计数 |

**ElecWarningStationDTO 字段**:
stationCode, inverterSn, dayAt, provinceName, cityName, regionName, streetName, address, spName, name, phone, status, houseType, completeConfirmCapacity(装机功率kW), eToday(当日能量), subCenterNameNew, stationCreatedAt, createdAt

### 2.3 多数据源配置

| 数据源 | Bean | 数据库 | 用途 |
|---|---|---|---|
| light | lightDataSource | rrsjk_light (rm-m5edyjcbrjfek8ufp) | 电站主数据 |
| elec | elecDataSource | rrsjk_light_data (rm-m5edyjcbrjfek8ufp) | 发电数据 |
| ads | adsDataSource | SelectDB (selectdb-cn-1wy4d12u002) | 分析/预警 (生产 only) |

Redis: r-m5eq4pig7ft2rykqwb.redis.rds.aliyuncs.com:6379

### 2.4 首页服务 (占位)

以下服务接口已定义但实现为空 (占位):
- `AssetManagementService` — 资产管理
- `BusinessAnalysisService` — 经营分析 (subCenterOverviewData 方法体为空)
- `WarnManagementService` — 预警管理

## 3. rrsjk-admin-operation-log-service (操作日志服务)

**来源**: rrsjk-admin-operation-log-service 全量通读 (2026-06-20)
**技术栈**: Spring Boot 2.7.18, Java 8, Dubbo Provider, MyBatis
**数据库**: rrsjk_admin_operation_log

### 3.1 数据库表

#### admin_oper_log (操作日志)

| 字段 | 类型 | 说明 |
|---|---|---|
| log_id | varchar(64) PK | 日志ID (UUID) |
| title | varchar(128) | 模块标题 |
| business_type | varchar(32) | 业务类型 |
| operator_type | varchar(32) | 操作人类别 |
| method | varchar(256) | 方法名 |
| request_method | varchar(16) | HTTP 方法 |
| oper_name | varchar(64) | 操作人 |
| user_id | varchar(64) | 用户ID |
| oper_url | varchar(512) | 请求URL |
| oper_ip | varchar(64) | IP地址 |
| oper_location | varchar(255) | 操作地点 |
| oper_param | longtext | 请求参数 |
| json_result | longtext | 返回结果 |
| status | char(1) | 状态 (0成功 1失败) |
| error_msg | varchar(2000) | 错误消息 |
| cost_time | bigint | 耗时毫秒 |
| trace_id | varchar(64) | 链路ID |
| oper_time | datetime | 操作时间 |

索引: idx_oper_time, idx_user_id, idx_status

#### admin_login_log (登录日志)

| 字段 | 类型 | 说明 |
|---|---|---|
| info_id | varchar(64) PK | 日志ID (UUID) |
| user_id | varchar(64) | 用户ID |
| user_name | varchar(64) | 用户名 |
| status | char(1) | 状态 (0成功 1失败) |
| ipaddr | varchar(64) | 登录IP |
| login_location | varchar(255) | 登录地点 |
| browser | varchar(255) | 浏览器 |
| os | varchar(255) | 操作系统 |
| msg | varchar(2000) | 提示消息 |
| login_type | varchar(32) | 登录类型 (APP/WEB) |
| trace_id | varchar(64) | 链路ID |
| login_time | datetime | 登录时间 |

索引: idx_login_time, idx_login_user, idx_login_status

#### admin_log_body_detail (日志正文详情)

| 字段 | 类型 | 说明 |
|---|---|---|
| detail_id | varchar(64) PK | 详情ID |
| parent_type | varchar(32) | 父日志类型 (LOGIN/OPERATION) |
| parent_id | varchar(64) | 父日志ID |
| trace_id | varchar(64) | 链路ID |
| request_body | longtext | 请求正文 |
| response_body | longtext | 响应正文 |
| request_body_size | int | 原始请求正文长度 |
| response_body_size | int | 原始响应正文长度 |
| request_truncated | tinyint(1) | 请求正文是否截断 |
| response_truncated | tinyint(1) | 响应正文是否截断 |
| created_at | datetime | 创建时间 |

唯一索引: uk_parent_log(parent_type, parent_id)
索引: idx_trace_id, idx_created_at

### 3.2 Dubbo 服务

**AdminOperationLogService**:
| 方法 | 功能 |
|---|---|
| `saveOperationLog(AdminOperationLogDTO)` | 保存操作日志 |
| `saveLoginLog(AdminLoginLogDTO)` | 保存登录日志 |
| `saveLogBody(AdminLogBodyDTO)` | 保存日志正文 (请求/响应体) |
| `getLogBody(parentType, parentId)` | 查询日志正文 |
| `queryLoginLogs(AdminLoginLogQueryDTO)` | 分页查询登录日志 |
| `queryOperationLogs(AdminOperationLogQueryDTO)` | 分页查询操作日志 |

### 3.3 部署配置

- ZK 注册中心: 10.2.192.154:2181 (dev), 10.2.160.242:2181,10.2.160.243:2181,10.2.160.244:2181 (prod)
- 数据库: rm-m5edyjcbrjfek8ufp (dev), rm-m5ebm056ct14p18zu (prod)
- 生产连接池: initialSize=100, maxActive=3000, keep-alive=true

## 4. 外围仓库分类

### rrs-dispenser-operator-android3

**分类**: 外围遗留 (非 PVS 业务)
**原因**: 
- 包名 `com.rrs.waterstationbuyer` — 水站买家端
- 业务内容: 水卡充值、滤芯更换申请、打水记录、BBS论坛、积分任务、建行钱包支付
- 最后提交: 2024-07-08 (近2年无更新)
- 与光伏/新能源业务无关

### rrs-dispenser-operator-ios3

**分类**: 外围遗留 (非 PVS 业务)
**原因**: 同上，iOS 版本。最后提交 2024-07-08。
