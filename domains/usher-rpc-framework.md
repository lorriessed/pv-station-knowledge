# usher RPC 框架

> `usher-rpc` 是 PVS 光伏系统底层使用的**自定义轻量级 RPC 框架**（非 Dubbo），基于 Netty + Nacos 构建。
> 属于 `top.uhyils.usher` 开源生态（Gitee: opentech_usher/usher-rpc），由开发者 uhyils（龙龙）维护。
> **业务价值**: ⭐ 基础设施层 — 不是 PVS 业务逻辑，但理解它有助于排查 RPC 调用、超时、熔断等问题。

## 框架概览

- **版本**: 2.1.2.1.usher
- **最后提交**: 2026-01-25（chore: 更新项目版本号）
- **技术栈**: Java 8 + Netty 4.1.54 + Nacos 2.4.3 + Fastjson2 2.0.59
- **协议**: 自定义二进制协议（非 HTTP/gRPC/Dubbo）
- **注册中心**: Nacos（Naming Service）
- **SPI 机制**: 自定义 SPI 扩展点（`RpcSpi` 注解 + `RpcSpiManager`）

## 模块结构

| 模块 | 职责 |
|------|------|
| `usher-rpc-common` | 配置类、枚举、注解、异常处理 |
| `usher-rpc-exchange` | RPC 协议定义（请求/响应体、Content 格式） |
| `usher-rpc-netty` | Netty 网络层（ProviderHandler/ConsumerHandler、拦截器链） |
| `usher-rpc-cluster` | 集群管理（负载均衡策略） |
| `usher-rpc-registry` | 注册中心适配（Nacos 实现） |
| `usher-rpc-proxy` | 动态代理（GenericService、RpcProxyDefaultHandler） |
| `usher-rpc-spring-start` | Spring Boot 自动配置集成 |

## RPC 协议

### 请求体格式 (RpcRequestContent)

请求内容按 `\n` 分隔的文本行：
```
serviceName\n           # 接口全限定类名
serviceVersion\n        # 版本号（固定为 "1"）
methodName\n            # 方法名
paramType1;paramType2;\n # 参数类型（分号分隔）
[args JSONArray]\n      # 参数 JSON 数组
[others...]             # 预留字段
```

### 响应体格式 (RpcResponseContent)

```
responseType\n    # 0=无返回值, 1=字符串返回, 2=异常
responseContent\n # 返回内容 JSON
```

### 响应状态码 (RpcStatusEnum)

| 状态码 | 名称 | 含义 |
|--------|------|------|
| 0 | NULL | 无 |
| 20 | OK | 成功 |
| 30 | CONSUMER_TIMEOUT | 消费者超时 |
| 31 | PROVIDER_TIMEOUT | 生产者超时 |
| 32 | CONSUMER_FUSING | 消费者熔断 |
| 40 | BAD_REQUEST | 请求失败 |
| 50 | BAD_RESPONSE | 回应失败 |
| 60 | SERVICE_NOT_FOUND | 未找到接口 |
| 70 | SERVICE_ERROR | 接口错误 |
| 80 | PROVIDER_ERROR | 生产者错误 |
| 90 | CONSUMER_ERROR | 消费者错误 |
| 100 | SERVER_THREADPOOL_EXHAUSTED_ERROR | 服务器线程池已耗尽 |

**来源**: `usher-rpc/usher-rpc-common/src/main/java/top/uhyils/usher/rpc/enums/RpcStatusEnum.java` (2026-06-01 全量通读)

## 负载均衡策略 (LoadBalanceEnum)

| Code | 策略 | 说明 |
|------|------|------|
| 0 | IP_HASH | 按 IP 哈希分配 |
| 1 | MANUAL_ASSIGNMENT | 手动分配权重 |
| 2 | RANDOM | 随机 |
| 3 | POLLING | 轮询 |
| 4 | LEAST_ACTIVE | 最少活跃 |
| 5 | FASTEST_RETURN_SPEED | 最快返回速度 |

**来源**: `usher-rpc/usher-rpc-cluster/src/main/java/top/uhyils/usher/rpc/cluster/enums/LoadBalanceEnum.java`

## 消费者配置 (ConsumerConfig)

| 配置项 | 默认值 | 说明 |
|--------|--------|------|
| check | true | 启动时是否检查服务可用性 |
| timeout | 30000ms | 调用超时时间 |
| retries | 3 | 重试次数 |
| inConnection | false | 集群内联（发现本地 bean 时直接使用） |

**来源**: `usher-rpc/usher-rpc-common/src/main/java/top/uhyils/usher/rpc/config/ConsumerConfig.java`

## 服务提供者配置 (ProviderConfig)

| 配置项 | 默认值 | 说明 |
|--------|--------|------|
| enable | false | 是否开启生产者（setPort/ setTimeout 后自动启用） |
| elegant | false | 是否开启优雅上下线 |
| timeout | 30000ms | 超时时间 |

**来源**: `usher-rpc/usher-rpc-common/src/main/java/top/uhyils/usher/rpc/config/ProviderConfig.java`

## 注册中心（Nacos 集成）

### Provider 注册流程
1. `NacosProviderRegistryCenterHandler.doRegistry()` → `nacosNaming.registerInstance()`
2. 注册时使用接口全限定类名作为 serviceName
3. 元数据包含 `RegistryMetadata` JSON

### Consumer 订阅流程
1. `NacosConsumerRegistryCenterHandler.initRegistryInfo()` → `nacosNaming.getAllInstances()`
2. `addConsumerListener()` → `nacosNaming.subscribe()` 监听服务变更
3. 过滤不健康（!isHealthy）和未启用（!isEnabled）的实例

**来源**: `usher-rpc/usher-rpc-registry/src/main/java/top/uhyils/usher/rpc/registry/mode/nacos/NacosConsumerRegistryCenterHandler.java`

## 核心调用链路

```
Consumer 调用 → RpcProxyDefaultHandler.invoke()
  → initRpcData() 构建请求体
  → Registry.invoke() → Nacos 获取服务列表
  → Netty 发送请求字节流
  → RpcConsumerHandler.channelRead0() 接收响应
  → parseResult() 解析返回值

Provider 接收 → RpcProviderHandler.channelRead0()
  → invokeRequestBytes() 经过拦截器链
  → RpcDefaultRequestCallBack.invoke() → execute()
    → 反射查找 Bean 和方法
  → 执行方法 → 序列化返回
  → RpcDefaultRequestCallBack.assembly() 构建响应
```

## SPI 扩展点

| 扩展接口 | 用途 |
|----------|------|
| `ProviderRequestByteExtension` | 生产者接收请求字节拦截 |
| `ProviderRequestDataExtension` | 生产者请求数据拦截 |
| `ProviderResponseByteExtension` | 生产者响应字节拦截 |
| `ProviderResponseDataExtension` | 生产者响应数据拦截 |
| `ProviderResponseObjExtension` | 生产者返回对象拦截（序列化前） |
| `ProviderResponseExceptionExtension` | 异常处理扩展 |
| `ConsumerRequestByteExtension` | 消费者请求字节拦截 |
| `ConsumerRequestDataExtension` | 消费者请求数据拦截 |
| `ConsumerResponseByteExtension` | 消费者响应字节拦截 |
| `ConsumerResponseDataExtension` | 消费者响应数据拦截 |
| `ConsumerResponseObjectExtension` | 消费者响应对象拦截（反序列化后） |

## 与 Dubbo 的关系

PVS 系统**同时使用 Dubbo 和 usher-rpc 两套 RPC 框架**：
- **Dubbo**: 主要业务服务间通信（rrsjk-light-service、rrsjk-finance-service 等）
- **usher-rpc**: 部分服务/模块使用的替代 RPC 方案（如 `rrsjk-async-import-export` 的 MQ 封装迁移到 usher 框架，见 remaining-services-and-frontends.md）

当排查 RPC 相关故障时，需确认目标服务使用的是 Dubbo 还是 usher-rpc 框架。

## 来源
- **代码明确证明**: `usher-rpc/` 全量通读 (2026-06-01)
- **无 PVS 业务逻辑**: 此仓库为通用 RPC 框架，不包含电站、审核、结算等业务逻辑
