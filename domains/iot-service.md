# IoT 设备管理服务

更新时间: 2026-06-19

## 概述

`rrsjk-light-iot-service` 是光伏 IoT 设备管理的新服务，2026-06-19 初始化基础结构和配置。

## 服务信息

| 属性 | 值 |
|---|---|
| 仓库 | `rrsjk-light-iot-service` |
| 包路径 | `com.rrsjk.light.iot` |
| 服务名 | `rrsjk-light-iot-service` |
| 模块 | `rrsjk-light-iot-api` + `rrsjk-light-iot-impl` |
| 状态 | 初始化阶段 (仅基础结构和配置) |
| 证据等级 | 代码明确证明 (2026-06-19 增量扫描) |

## 基础架构

- **Spring Boot** + **Dubbo** (服务注册发现)
- **Kafka Consumer** (消息消费)
- **Redis** (缓存)
- **OSS** (对象存储)
- **Prometheus** (监控, pushgateway: 10.1.132.87:9091)
- **EventBus** (事件总线)
- **MyBatis** (数据访问)
- **线程池** (ThreadPoolExecutor 配置)
- **ID 生成器** (IdGenerator)

## 工具类

| 工具类 | 模块 | 用途 |
|---|---|---|
| `DictConverter.java` | api | 字典转换 |
| `SpecialFlagConverter.java` | api | 特殊标志转换 |
| `DateTimeUtil.java` | api | 日期时间工具 |
| `ChToEnUtil.java` | impl | 中文转英文 |
| `ElecNoUtils.java` | impl | 电表编号工具 |
| `MessageUtils.java` | impl | 消息工具 |
| `ParamsUtils.java` | impl/dtyunxi | 参数工具 (抖音云玺?) |
| `SignatureUtil.java` | impl/dtyunxi | 签名工具 (抖音云玺?) |

## 配置

- `application.yml` — 基础配置 (允许 bean 覆盖, profile 激活)
- `application-dev.yml` — 开发环境
- `application-prod.yml` — 生产环境

## Dubbo 服务依赖 (代码明确证明, 2026-06-23 通读)

**来源**: `rrsjk-light-iot-service` → `spring-config/service.xml`

service.xml 揭示了 IoT 服务的业务定位 — 它被设计为**运维+零碳+合同**的聚合服务:

### 调用的基础服务
| 服务 | 接口 | 用途 |
|---|---|---|
| rrsjk-system-service | `MessageService`, `RegionService`, `SubCenterInfoService` | 短信/地区/分中心 |
| rrsjk-member-service | `MemberService`, `MemberRoleService` | 会员/角色 |
| rrsjk-merchant-web | `MerchantService` | 商户信息 |

### 调用的光伏核心服务 (rrsjk-light-api)
| 接口 | 业务域 |
|---|---|
| `LightStationService` | 电站基础 |
| `LightServiceProviderService` | 服务商管理 |
| `LightStationInverterService` | 电站逆变器关联 |
| `LightStationPlanConfigService` | 电站配货方案 |
| `LightElecContractService` | 电子合同 |
| `LightOpContractRecordService` | 运维合同记录 |
| `LightStationCopy1Service` | 电站复制 |
| `LightSubSpService` | 二级服务商 |
| `LightOpAuthorityZoneService` | 运维授权区域 |
| `LightSpAuthorityZoneService` | 服务商授权区域 |
| `LightOpContractConfigService` | 运维合同配置 |
| `LightOperationDepositService` | 运维保证金 |

### 调用的零碳服务
| 接口 | check | 用途 |
|---|---|---|
| `ZeroCarbonServiceProviderService` | false | 零碳服务商 |
| `ZeroCarbonSpAuthRegionService` | false | 零碳服务商授权区域 |
| `LightZeroCarbonStationService` | false | 零碳电站 |
| `LightOpAuthorityZoneRemoveService` | false | 运维区域移除 |

**分析**: IoT 服务的 Dubbo 依赖覆盖了电站/逆变器/合同/服务商/零碳等核心域，表明它不仅仅是一个 IoT 设备接入层，更可能是**运维工单+设备管理**的综合服务入口。Kafka 消费端配置了 `LightInverterRecordKafkaEvent` 反序列化，说明它消费发电数据 Kafka 消息用于运维场景。

## Kafka 消费配置 (代码明确证明, 2026-06-23 通读)

**来源**: `rrsjk-light-iot-service` → `KafkaConsumerConfig.java`, `application-prod.yml`

- **Topic**: `light-data-topic` (发电数据)
- **Consumer Group**: `light-operation-prod-group`
- **反序列化**: `JsonDeserializer<LightInverterRecordKafkaEvent>`
- **可信包**: `com.rrsjk.light.data.entity.local`
- **并发**: 3 线程
- **重试**: 3次, 间隔1000ms
- **ACK模式**: MANUAL (手动确认)
- **错误处理**: `SeekToCurrentErrorHandler` + `FixedBackOff` — 失败后跳过并记录日志

## 待确认

- `dtyunxi` 包的具体对接平台 (推测为抖音云玺 IoT 平台)
- 与现有 `rrsjk-light-service` 逆变器数据模块的职责边界
- 是否承接新增的 IoT 设备接入需求
- 零碳服务依赖的实际使用场景（check=false 表示非强依赖）

## 来源
- `rrsjk-light-iot-service` 初始化扫描 (commit: 7dcf95b, 2026-06-19)
- `rrsjk-light-iot-service` 重扫 (2026-06-23, 零新增提交)
