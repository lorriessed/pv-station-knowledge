# 招银租赁租后数据查询 API

最后更新: 2026-05-16

## 1. 概述

**来源**: `rrsjk-openapi-web` 全量通读 (2026-05-16, 代码明确证明)

`rrsjk-openapi-web` 是 PVS 光伏系统的**外部 API 网关服务**，专门面向第三方系统（如招银租赁）提供租后数据查询能力。通过 OAuth2 认证 + QPS 限流保护，向资方开放电站运行数据。

## 2. 服务基本信息

| 配置项 | 值 | 来源 |
|---|---|---|
| 服务名 | `rrsjk-openapi-web` | `application.yml` |
| 端口 | 8083 | `application.yml` |
| Context Path | `/openapi` | `application.yml` |
| Spring Boot 版本 | 2.2.4.RELEASE | `pom.xml` |
| Dubbo 版本 | 2.7.4.1 | `pom.xml` |
| JDK | 1.8 | `pom.xml` |
| 日志路径 | `/data/output/logs/javalog/nor` | `application.yml` |

## 3. 招银租赁 API 接口

**Controller**: `ZhaoYinLeaseController.java`
**路由前缀**: `/openapi/zhaoyin`

| 接口 | 方法 | 功能 | 限流 QPS | 状态 |
|---|---|---|---|---|
| `/api/v1/plant/daily-power` | POST | 电站日发电量查询 | 7 | ✅ 启用 |
| `/api/v1/plant/status` | POST | 电站状态查询 | 7 | ✅ 启用 |
| `/api/v1/electricity/bill` | POST | 电站电费账单查询 | 7 | ✅ 启用 |
| `/api/v1/inverter/real-time-power` | POST | 逆变器发电功率查询 | 7 | ❌ 已注释 |

### 3.1 电站日发电量查询

- **请求**: `DaliyPowerRequest` — `orderNos`(电站编号列表), `startDate`, `endDate`
- **响应**: `List<DaliyPowerResponse>` — `orderNo`, `electricityDate`, `dailyElectricity`, `electricityHours`, `updateTime`
- **限流 Key**: `rrsjk-openapi-web:rate_limit:{clientId}:stationDailyPowerQuery`

### 3.2 电站状态查询

- **请求**: `StationStatusRequest` — `orderNos`(电站编号列表)
- **响应**: `List<StationStatusResponse>` — 包含电站编号、名称、状态、装机容量、逆变器列表、发电户号、地址、实时功率、经纬度、更新时间、逆变器功率明细
- **限流 Key**: `rrsjk-openapi-web:rate_limit:{clientId}:stationStatusQuery`

### 3.3 电站电费账单查询

- **请求**: `DaliyPowerRequest` — `orderNos`, `startDate`, `endDate` (复用日发电量请求体)
- **响应**: `List<ElectricityBillResponse>` — `orderNo`, `electricityAmount`, `feedInElectricity`, `electricityMonth`
- **限流 Key**: `rrsjk-openapi-web:rate_limit:{clientId}:electricityBillQuery`

### 3.4 电站状态枚举

**来源**: `StationStatusResponse.PowerStationStatusEnum` (代码明确证明)

| 状态码 | 含义 |
|---|---|
| 0 | 正常 |
| 1 | 故障 |
| 2 | 离线 |
| 3 | 待机 |
| 4 | 异常 |

## 4. 安全与限流机制

### 4.1 OAuth2 JWT 认证

**来源**: `Oauth2Config.java`, `MvcConfig.java` (代码明确证明)

- 使用 `JwtTokenStore` + RSA 公钥验证
- 密钥文件: `{profile}/key/rsa_public_key.pem` (classpath)
- 全局 Filter: `AccessTokenCheckFilter` (order=100)
- Session Cookie: maxAge=259200s (3天), httpOnly=false

### 4.2 QPS 限流

**来源**: `RequestLimiter.java`, `RequestLimiterAspect.java` (代码明确证明)

- **注解**: `@RequestLimiter(key="...", qps=N)`
- **限流维度**: 按 clientId (OAuth2 client) + key 维度限流
- **限流 Key 格式**: `{serverName}:rate_limit:{clientId}:{key}`
- **拒绝响应**: HTTP 429 + `ReturnCodeEnum.CODE_S429`
- **依赖**: 使用 Guava `RateLimiter` (通过 `rateLimiter` Bean)

```java
@RequestLimiter(key = "stationDailyPowerQuery", qps = 7)
@PostMapping("/api/v1/plant/daily-power")
```

### 4.3 XSS 防护

**来源**: `XssConfig.java`, `XssHttpServletRequestWrapper.java` (代码明确证明)

- 使用 Jsoup 进行 XSS 过滤
- 排除路径: `/css/*`, `/js/*`, `/fonts/*`, `/images/*`
- 支持富文本: `isIncludeRichText=true`
- 过滤范围: `getParameter`, `getParameterValues`, `getHeader`

### 4.4 跨域配置

**来源**: `MvcConfig.java` (代码明确证明)

- 允许所有源 (`*`)
- 允许所有方法、所有请求头
- Max-Age: 3600 秒
- CORS Filter order=99 (最高优先级)

## 5. Dubbo 服务配置

**来源**: `DubboConfig.java`, `service.xml` (代码明确证明)

| 配置 | 值 |
|---|---|
| 注册中心 | Zookeeper |
| 超时 | 10000ms |
| 提供者重试 | 0 |
| 提供者超时 | 9000ms |
| 消费者重试 | 0 |
| 消费者超时 | 9000ms |
| 本地缓存 | `/tmp/rrsjk-openapi-web` |

**Dubbo 引用**:
- `accessTokenService` — `com.rrsjk.system.token.service.AccessTokenService` (timeout=10000)
- `zhaoYinLeaseService` — `com.rrsjk.openapi.service.ZhaoYinLeaseService`

## 6. 依赖的外部 API 服务

**来源**: `pom.xml` (代码明确证明)

| 依赖 API | 用途 |
|---|---|
| rrsjk-system-api | 系统服务/Token验证 |
| rrsjk-member-api | 会员服务 |
| rrsjk-item-api | 商品/评论服务 |
| rrsjk-trade-api | 交易服务 |
| rrsjk-merchant-api | 商户服务 |
| rrsjk-light-api | 光伏核心服务 |
| rrsjk-light-operation-api | 光伏运营服务 |
| rrsjk-light-data-api | 光伏数据服务 |
| rrsjk-energystorage-api | 储能服务 |
| rrs-dispenser-api | 配货服务 |
| nh-business-forecast-api | 业务预测服务 |
| rank-service-api | 排名服务 |

## 7. 部署配置

### 7.1 开发环境

**来源**: `application-dev.yml` (代码明确证明)

- Redis: `r-m5eq4pig7ft2rykqwb.redis.rds.aliyuncs.com:6379` (db=0)
- Dubbo Zookeeper: `10.2.192.154:2181`
- Tomcat: max-threads=1000, accept-count=300

### 7.2 生产环境

**来源**: `application-prod.yml` (代码明确证明)

- Redis: `r-m5e18tcq2ibkvys7t6.redis.rds.aliyuncs.com:6379` (db=0, pool max-active=10)
- Dubbo Zookeeper: `10.2.160.242:2181,10.2.160.243:2181,10.2.160.244:2181` (3节点)
- Tomcat: max-connections=1000, max-threads=1000

## 8. 外部调用链路

```
招银租赁系统 → rrsjk-openapi-web (:8083/openapi/zhaoyin/*)
    ↓ OAuth2 JWT 认证
    ↓ QPS 限流 (7次/秒/client)
    ↓ XSS 过滤
    ↓
ZhaoYinLeaseService (Dubbo 消费者)
    ↓
rrsjk-light-service / rrsjk-light-data-service (Dubbo 提供者)
    ↓
逆变器数据 / 电站数据 / 发电数据
```

## 9. 招银进件电价匹配逻辑 V2（TAEI-3101）

**来源**: `rrsjk-light-service` — `CmbLeasingPushApiServiceImpl.java`, `CmbPushOrderInfoRequest.java`, `CmbElectricPriceV2.java`, `CmbLeasingStation.xml` (2026-05-15 提交 d6bfcb34, 代码明确证明)

### 9.1 需求背景

**TAEI-3101: 【户用光伏】招银组件功率匹配价格**
- 负责人: 刘艺
- 参与人: 薛荣基, 李龙 (git: lilong)
- 状态: 开发中 (2026-05-15 首次提交)

招银租赁进件时，需要根据电站的**省市区+屋顶类型+组件类型**匹配对应的电价和产品编号。旧版电价查询维度不足（只按省+市+屋顶类型），新版增加了**区县（region）**和**租赁屋顶类型（leaseRoofType）**维度。

### 9.2 电价匹配数据流

```
电站进件推送 (CmbLeasingPushApiServiceImpl.buildLeaseScheme)
    ↓
1. 根据电站 houseType + install 匹配 TechnicalSchemeEnumV2 (技术方案)
    例: FLAT → A001(阵列式), DOUBLE_SLOPE → A002(双面坡)
    ↓
2. 根据技术方案匹配 LeaseRoofTypeEnumV2 (租赁屋顶类型)
    例: A001 → A(阵列式), B001 → B(阳光房)
    ↓
3. 根据 省+市+区县+租赁屋顶类型+组件类型 查询电价表
    表: cmb_electric_price
    查询方法: CmbLeasingStationDao.getPriceV2()
    ↓
4. 匹配到唯一电价 → productNo → leaseCode (融资产品编号)
```

### 9.3 技术方案枚举 V2

**来源**: `CmbPushOrderInfoRequest.java` — `TechnicalSchemeEnumV2` (2026-05-15 新增)

| 代码 | 描述 | 对应屋顶类型(houseType) |
|---|---|---|
| A001 | 阵列式 | FLAT(平面), SLOPE(斜面) |
| A002 | 双面坡 | DOUBLE_SLOPE |
| B001 | 阳光房 | YGF(阳光房) |
| C001 | 院内地面 | GROUND |
| D001 | 院落式桁架15度方案 | GROUND_DOUBLE_SLOPE |

匹配逻辑: `getByHouseType(stationCode, houseType, install)` — 通过屋顶类型反查技术方案，要求唯一匹配。

### 9.4 租赁屋顶类型枚举 V2

**来源**: `CmbPushOrderInfoRequest.java` — `LeaseRoofTypeEnumV2` (2026-05-15 新增)

| 代码 | 描述 | 对应技术方案 |
|---|---|---|
| A | 阵列式 | A001, A002 |
| B | 阳光房 | B001 |
| C | 庭院房 | C001, D001 |

### 9.5 电价实体 V2

**来源**: `CmbElectricPriceV2.java` (2026-05-15 新增实体)

| 字段 | 类型 | 说明 |
|---|---|---|
| id | Long | 主键 |
| provinceName | String | 省份 |
| cityName | String | 城市 |
| regionName | String | 区县（V2 新增） |
| leaseRoofType | String | 租赁屋顶类型（V2 新增） |
| moduleType | String | 组件类型（电池型号） |
| price | BigDecimal | 电价/单价 |
| productNo | String | 产品编号（融资产品编码） |

### 9.6 数据库查询

**表**: `cmb_electric_price`

**V1 查询条件** (旧版): provinceName + cityName + leaseRoofType(技术方案描述)

**V2 查询条件** (新版): provinceName + cityName + regionName + leaseRoofType + moduleType

**Mapper**: `CmbLeasingStation.xml` — `getPriceV2` (2026-05-15 新增)

### 9.7 旧版 vs 新版对比

| 维度 | 旧版 | V2 新版 |
|---|---|---|
| 技术方案 | TechnicalSchemeEnum (4种) | TechnicalSchemeEnumV2 (5种) |
| 屋顶类型 | LeaseRoofTypeEnum | LeaseRoofTypeEnumV2 (3种) |
| 电价查询维度 | 省+市+技术方案描述 | 省+市+区县+租赁屋顶类型+组件类型 |
| 电价实体 | CmbElectricPrice | CmbElectricPriceV2 (新增 regionName, leaseRoofType) |
| 匹配精度 | 较粗 | 更细（增加了区县和屋顶类型维度） |

### 9.8 关键变更说明

- 旧版 `TechnicalSchemeEnum` 和 `LeaseRoofTypeEnum` 被注释掉但保留（回退兼容）
- 新枚举类名为 `TechnicalSchemeEnumV2` / `LeaseRoofTypeEnumV2`，避免冲突
- 电价查询方法从 `getPrice()` 改为 `getPriceV2()`
- 查询参数增加了 `regionName`（区县）和 `leaseRoofType`（租赁屋顶类型）

### 9.9 需求变更 — 新旧数据区分逻辑 (2026-05-22~23 代码明确证明)
**来源**: `CmbLeasingPushApiServiceImpl.java`, `CmbLeasingStationDao.java`, `CmbLeasingStation.xml` (commits: f1a84bb3, ba806d00, lilong, branch: 20260515-alone-zhaoyin-price)
- **新旧数据区分**: 使用 `pushTime` 字段（电站推送时间）与配置项 `cmbLeasing.fixDate`（默认 2026-05-26）比较，而非 `createAt`
  - `pushTime > fixDate`: 使用**旧版**匹配逻辑（电池类型 battery_type 维度，TechnicalSchemeEnum）
  - `pushTime <= fixDate`: 使用**新版**匹配逻辑（功率 power 维度，TechnicalSchemeEnumV2）
- **取值方式回退**: 新数据（fixDate 之后推送）从 V2 回退到原始枚举映射：
  - `TechnicalSchemeEnumV2` → `TechnicalSchemeEnum`
  - `LeaseRoofTypeEnumV2` → `LeaseRoofTypeEnum`
  - `CmbElectricPriceV2` → `CmbElectricPrice`
  - `getPriceV2()` → `getPrice()`
- **原因推断**: 功率匹配方式可能在实际业务中不如电池类型匹配稳定，需求变更后对新增电站回退到电池类型匹配
- **证据等级**: 代码明确证明
