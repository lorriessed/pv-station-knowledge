# VPP 泰国大屏系统

最后更新: 2026-05-16

## 1. 概述

**来源**: `vpp-thai-dashboard` 全量通读 (2026-05-16, 代码明确证明)

`vpp-thai-dashboard` 是 VPP 项目面向泰国市场的智慧能源管理大屏系统，通过调用**华为 FusionSolar 北向 API** 获取电站实时数据，在前端大屏展示光伏运营指标、功率曲线、碳减排等数据。

## 2. 服务基本信息

| 配置项 | 值 | 来源 |
|---|---|---|
| 服务名 | `vpp-thai-dashboard` | `bootstrap.yml` |
| 端口 | 7089 | `bootstrap.yml` |
| Context Path | `/vpp-thai-dashboard` | `bootstrap.yml` |
| Spring Boot 版本 | 2.5.5 | `pom.xml` |
| JDK | 1.8 | `pom.xml` |
| 注册中心 | Nacos | `bootstrap.yml` |
| 配置中心 | Nacos | `bootstrap.yml` |
| Jasypt 加密密钥 | `ldajlf974qljdfaj` | `bootstrap.yml` |

## 3. 华为 FusionSolar 北向 API 集成

### 3.1 Token 管理

**来源**: `HuaweiTokenService.java` (代码明确证明)

- **登录接口**: `POST https://{domain}/thirdData/login`
- **请求体**: `{"username":"账号名","systemCode":"密码"}`
- **Token 位置**: 响应头 `xsrf-token`
- **Token 有效期**: 30 分钟
- **会话限制**: 一个账号只能有一个在线会话，重复登录会使先前 Token 失效
- **自动续期**: 每 25 分钟检查一次，剩余时间 < 5 分钟时自动续期
- **线程安全**: 使用 `ReentrantLock` 防止并发获取 Token

### 3.2 北向 API 接口调用

**来源**: `HuaweiNorthboundApiService.java` (代码明确证明)

| API 路径 | 功能 | 请求参数 |
|---|---|---|
| `/thirdData/getStationRealKpi` | 电站实时数据 | `stationCodes` (逗号分隔) |
| `getDevRealKpi` | 设备实时数据 | `devIds`, `devTypeId` |
| `getKpiStationDay` | 电站日数据 | `stationCodes`, `collectTime` (yyyy-MM-dd) |
| `getKpiStationMonth` | 电站月数据 | `stationCodes`, `collectTime` (yyyy-MM) |
| `getKpiStationYear` | 电站年数据 | `stationCodes`, `collectTime` (yyyy) |

**请求头**: `xsrf-token: {token}`, `Content-Type: application/json`

### 3.3 配置项

**来源**: `application-huawei.yml` (代码明确证明)

```yaml
huawei:
  northbound:
    domain: xxx.fusionsolar.huawei.com
    username: your-api-username
    system-code: your-system-code  # 注意是 systemCode，不是 password
    login-path: /thirdData/login
    token-expire-minutes: 30
    station-codes: station001,station002,station003
```

## 4. 定时任务

**来源**: `StationDataCollectionJob.java`, `TokenRenewalJob.java` (代码明确证明)

| 任务 | Cron | 功能 |
|---|---|---|
| 电站实时数据采集 | `0 0/5 * * * ?` | 每 5 分钟采集电站实时数据 |
| 设备实时数据采集 | `0 0/5 * * * ?` | 每 5 分钟采集设备实时数据 |
| 电站月数据采集 | `0 0 12 * * ?` | 每天中午 12 点采集月数据 |
| 40 天数据清理 | `0 0 0 * * ?` | 每天清理 40 天前历史数据 |
| Token 续期检查 | fixedDelay=1500000ms (25分钟) | 检查 Token 有效期，<5分钟自动续期 |
| Token 状态日报 | `0 0 2 * * ?` | 每天凌晨 2 点生成 Token 状态报告 |

## 5. API 接口

### 5.1 能源仪表板

**来源**: `DashboardController.java` (代码明确证明)

| 接口 | 方法 | 功能 |
|---|---|---|
| `/dashboard` | GET | 获取完整能源仪表板数据 |

返回数据包含:
- `pvOperation`: 光伏运营数据 (累计收益、当月收益、昨日收益、总发电量、当月发电量、昨日/今日发电量)
- `pvPowerGraph`: 光伏功率曲线图 (15 分钟粒度)
- `loadGraph`: 负荷曲线图
- `gateGraph`: 关口表曲线图
- `gateChart`: 关口表数据 (累计购电费用、总购电量、光伏自给率、饼图)
- `carbonIndicators`: 碳指标 (节约标准煤、CO2 减排、种树数量)
- `topologyDiagram`: 拓扑图数据

### 5.2 电站数据采集

**来源**: `StationDataController.java` (代码明确证明)

| 接口 | 方法 | 功能 |
|---|---|---|
| `/api/station-data/collect-realtime` | POST | 手动触发电站实时数据采集 |

## 6. 数据库表 (MyBatis-Plus)

**来源**: Mapper 接口文件 (代码明确证明)

| 表名 (推断) | Mapper | Entity | 功能 |
|---|---|---|---|
| `device_realtime` (推断) | `DeviceRealtimeMapper` | `DeviceRealtime` | 设备实时数据 |
| `station_month` (推断) | `StationMonthMapper` | `StationMonth` | 电站月数据 |
| `station_real_time` (推断) | `StationRealTimeDataMapper` | `StationRealTime` | 电站实时数据 |

**电站实时数据字段** (`StationRealTime`):
- `stationCode`: 电站编号
- `dayPower`: 日发电量
- `monthPower`: 月发电量
- `totalPower`: 总发电量
- `dayIncome`: 日收益
- `totalIncome`: 总收益
- `dayOnGridEnergy`: 日上网电量
- `dayUseEnergy`: 日用电量
- `realHealthState`: 健康状态

## 7. 枚举定义

### 7.1 电站健康状态

**来源**: `StationHealthStateEnum.java` (代码明确证明)

| 状态码 | 含义 |
|---|---|
| 1 | 断连 |
| 2 | 故障 |
| 3 | 健康 |

### 7.2 设备类型

**来源**: `DeviceTypeEnum.java` (代码明确证明)

| 类型ID | 设备名称 |
|---|---|
| 1 | 组串式逆变器 |
| 2 | 数采 |
| 8 | 箱变 |
| 10 | 环境监测仪 |
| 13 | 通管机 |
| 16 | 通用设备 |
| 17 | 关口电表 |
| 22 | PID |
| 37 | 品联数采 |
| 38 | 户用逆变器 |
| 39 | 储能 |
| 40 | 并离网控制器 |
| 41 | ESS |
| 45 | PLC |
| 46 | 优化器 |
| 47 | 户用电表 |
| 62 | Dongle |
| 63 | 分布式数采 |
| 70 | 安全关断盒 |
| 60001 | 市电 |
| 60003 | 发电机 |
| 60014 | 锂电簇 |
| 60043 | 太阳能模块组 |
| 60044 | 太阳能模块 |
| 60092 | 功率转换器 |
| 60010 | 交流输出配电 |
| 23070 | EMMA |

### 7.3 数据权限

**来源**: `PrivilegeEnum.java` (代码明确证明)

| 编码 | 含义 |
|---|---|
| 100 | 自己 |
| 200 | 本级 |
| 300 | 本级及以下 |

## 8. 碳指标计算规则

**来源**: `DashboardServiceImpl.java` (代码明确证明)

| 指标 | 计算公式 |
|---|---|
| 节约标准煤 (t) | 总发电量 × 0.00032 |
| CO2 减排 (t) | 总发电量 × 0.00085 |
| 种树 (万棵) | 总发电量 × 0.0000085 |

## 9. 技术栈

**来源**: `pom.xml` (代码明确证明)

| 组件 | 版本 | 用途 |
|---|---|---|
| Spring Cloud | 2020.0.4 | 微服务框架 |
| Spring Cloud Alibaba | 2021.1 | Nacos 注册/配置 |
| MyBatis-Plus | 3.5.3.1 | ORM 框架 |
| Druid | 1.2.24 | 连接池 |
| Hutool | 5.8.26 | 工具库 |
| Fastjson2 | 2.0.52 | JSON 序列化 |
| Jasypt | 3.0.5 | 配置加密 |
| JWT (jjwt) | 0.9.1 | Token |
| Swagger | 3.0.0 | API 文档 |
| PageHelper | 1.4.7 | 分页 |
| IAM Auth SDK | 1.1.7 | 海尔统一认证 |
| POI | 4.1.2 | Excel 处理 |
| Guava | 32.1.2-jre | 工具库 |
| Feign | — | 服务间调用 |

## 10. 外部服务依赖

**来源**: `RemoteI18nService.java`, `pom.xml` (代码明确证明)

| 服务 | 用途 | 调用方式 |
|---|---|---|
| 华为 FusionSolar 北向 API | 电站/设备数据采集 | HTTPS REST |
| SYSTEM_SERVICE (VPP) | i18n 国际化消息 | Feign (`/i18nMessage/getAllMessageSource`) |
| Nacos | 服务注册与配置管理 | 内网 10.162.105.9:8848 |
| MySQL | 数据存储 | Druid 连接池 |

## 11. 仪表板默认值

**来源**: `DashboardServiceImpl.java` (代码明确证明)

以下指标通过 Spring `@Value` 注入配置文件默认值 (非实时计算):

| 配置项 | 说明 |
|---|---|
| `dashboard.yesterdayIncome` | 昨日收益 |
| `dashboard.monthIncome` | 当月收益 |
| `dashboard.yesterdayPower` | 昨日发电量 |
| `dashboard.yesterdayCost` | 昨日购电费用 |
| `dashboard.yesterdayPurchased` | 昨日购电量 |
| `dashboard.pvSelfSufficiencyRate` | 光伏自给率 |

**光伏装机容量硬编码**: `1799.9999037718776 kW`

## 12. 国际化

**来源**: `messages_zh_CN.properties` (代码明确证明)

支持中文、英文双语:
- `system.success` = 操作成功 / Success
- `system.error` = 操作失败 / Error
- `user.login.success` = 登录成功 / Login successful
- `station.data.loaded` = 电站数据加载成功 / Station data loaded successfully
