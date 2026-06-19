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

## 待确认

- `dtyunxi` 包的具体对接平台 (推测为抖音云玺 IoT 平台)
- Kafka 消费的具体 topic 和业务场景
- 与现有 `rrsjk-light-service` 逆变器数据模块的关系
- 是否承接新增的 IoT 设备接入需求

## 来源
- `rrsjk-light-iot-service` 初始化扫描 (commit: 7dcf95b, 2026-06-19)
