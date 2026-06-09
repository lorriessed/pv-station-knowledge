# 中银租赁(BOC)租后数据查询 API

最后更新: 2026-05-18

## 1. 概述

**来源**: `rrsjk-openapi-web` + `rrsjk-light-openapi-service` (TAEI-3084, 马斌, 2026-05-11 ~ 2026-05-16, 代码明确证明)

TAEI-3084: **【户用光伏】中银租后接口对接**
- 负责人: 刘艺
- 参与人: 薛荣基, 马斌 (git: mabin)
- 状态: 开发中
- 分支: `20260511-zhongYinLease` (rrsjk-openapi-web, rrsjk-light-openapi-service)

`rrsjk-openapi-web` 是 PVS 光伏系统的**外部 API 网关服务**，面向第三方系统（如中银租赁）提供租后数据查询能力。中银租赁 API 与招银租赁 API 共享相同的架构模式（OAuth2 认证 + QPS 限流），但提供独立的路由和数据查询。

## 2. API 接口

**Controller**: `ZhongYinLeaseController.java`
**路由前缀**: `/zhongyin` (独立于招银的 `/zhaoyin`)

| 接口 | 方法 | 功能 | 限流 QPS | 状态 |
|---|---|---|---|---|
| `/powerStationList` | POST | 电站日发电量查询（按电站维度） | 7 | ✅ 启用 |
| `/queryDailyGenerationSummary` | POST | 电站总发电量查询（汇总） | 7 | ✅ 启用 |

### 2.0 响应加密 (ReponseEncrypt)

**来源**: `rrsjk-openapi-web` → `ReponseEncrypt.java`, `ZhongYinLeaseController.java` (2026-05-25 通读, 代码明确证明)

中银租赁 API 的所有接口都标注了 `@ReponseEncrypt(clientId = "zhong_yin_lease")` 注解, 对响应数据进行加密后返回:

```java
@ReponseEncrypt(clientId = "zhong_yin_lease")
@RequestLimiter(key = "powerStationQuery", qps = 7)
@PostMapping("/powerStationList")
public ZhongYinReturn<List<ZhongYinElecByStationDto>> stationDailyPowerQuery(...)
```

- **加密切面**: `ReponseEncryptAspect` (`com.rrsjk.openapi.aspect.ReponseEncryptAspect`)
- **clientId**: `zhong_yin_lease` (用于标识加密密钥)
- **招银租赁 API 未使用此加密**, 仅中银租赁启用
- 相关提交: `feat(openapi): 添加响应数据加密功能` (mabin, 2026-05-25), `fix(security): 修复响应加密功能中的参数错误和逻辑缺陷` (mabin, 2026-06-02)

### 2.1 电站日发电量查询

- **请求**: `powerStationRequest` — `powerNo`(电站编号, 逗号分隔), `date`(YYYYMMDD格式)
- **响应**: `ZhongYinReturn<List<ZhongYinElecByStationDto>>`
- **限流 Key**: `rrsjk-openapi-web:rate_limit:{clientId}:powerStationQuery`
- **返回字段**: 电站编号、日发电量、满发小时数、电站状态、逆变器列表

### 2.2 电站总发电量查询

- **请求**: `powerStationRequest` — `date`(YYYYMMDD格式)
- **响应**: `ZhongYinReturn<List<ZhongYinElecTotalDto>>`
- **限流 Key**: `rrsjk-openapi-web:rate_limit:{clientId}:queryDailyGenerationSummary`
- **返回字段**: 总发电量汇总数据

### 2.3 统一响应格式

```java
public class ZhongYinReturn<T> {
    private boolean success;
    private String msg;
    private T data;
    
    public static <T> ZhongYinReturn<T> success(T data);
    public static <T> ZhongYinReturn<T> error(String msg);
}
```

## 3. Dubbo 服务层

**服务**: `ZhongYinBocLeaseService` (在 rrsjk-light-openapi-service 中实现)
**Dubbo 引用**: `zhongYinBocLeaseService` — 在 `service.xml` 中配置

| 方法 | 功能 |
|---|---|
| `findZhongYinElecByStation(params)` | 查询电站维度日发电量 + 逆变器数据 |
| `findZhongYinTotalElec(params)` | 查询总发电量汇总 |

### 3.1 电站日发电量查询业务逻辑

```
ZhongYinLeaseController.stationDailyPowerQuery()
    ↓ 参数校验(powerNo, date格式YYYYMMDD)
    ↓ QPS限流(7次/秒)
ZhongYinBocLeaseServiceImpl.findZhongYinElecByStation()
    ↓
    1. OdsLightStationElecDao.findZhongYinStation() — 查询电站日发电量
    2. OdsLightStationElecDao.findZhongYinInverterDataBySation() — 查询逆变器数据
    3. 按电站编码聚合逆变器数据:
       - 计算满发小时数 = Σinveter.fullHour
       - 计算电站状态 = max(逆变器状态)
       - 特殊规则: 日发电量>0 且状态=2(故障) → 状态修正为3(待机)
    ↓
    返回 List<ZhongYinElecByStationDto>
```

### 3.2 逆变器状态映射

| 状态码 | 含义 |
|---|---|
| 1 | 离线 |
| 2 | 故障 |
| 3 | 待机/运行 |

**特殊规则**: 如果电站有日发电量(>0) 但逆变器状态为故障(2)，则状态修正为待机(3)。

## 4. 数据库查询

**表**: ODS 层电站发电数据表（通过 MyBatis Mapper `OdsLightStationElec.xml` 访问）

### 4.1 电站日发电量查询 (findZhongYinStation)

- 查询条件: `powerNoList` + `date`
- 返回: `ZhongYinElecByStationDto` (电站编号、日发电量等)

### 4.2 逆变器数据查询 (findZhongYinInverterDataBySation)

- 查询条件: `powerNoList` + `date`
- 返回: `ZhongYinInverterData` (电站编号、逆变器状态、满发小时数)

### 4.3 总发电量查询 (findZhongYinTotalElec)

- 查询条件: `date`
- 返回: `ZhongYinElecTotalDto` (总发电量汇总)

## 5. 与招银租赁 API 对比

| 维度 | 招银租赁 (zhaoyin) | 中银租赁 (zhongyin) |
|---|---|---|
| 路由前缀 | `/zhaoyin` | `/zhongyin` |
| Controller | `ZhaoYinLeaseController` | `ZhongYinLeaseController` |
| Dubbo Service | `zhaoYinLeaseService` | `zhongYinBocLeaseService` |
| 接口数量 | 4个(日发电量/状态/电费账单/逆变器功率) | 2个(日发电量/总发电量) |
| 逆变器状态 | 5种(正常/故障/离线/待机/异常) | 3种(离线/故障/待机) |
| 响应格式 | 各自 Response 类 | 统一 `ZhongYinReturn<T>` 包装 |
| 限流 | 7 QPS/client | 7 QPS/client |
| 分支 | `20260302-ZYPostLease` | `20260511-zhongYinLease` |

## 6. 关联需求

- **TAEI-3084**: 中银租后接口对接 (主需求)
- **TAEI-3098**: 图片验真唯一码入库前增加重复检查 (马斌同期提交，涉及 CmbLeasingPushApiServiceImpl)
- **TAEI-3099**: 部分中核电站发电户号重推 (魏秋阳+王斌，与中银租后发电数据相关)
