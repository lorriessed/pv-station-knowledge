# PVS 全量通读报告 2026-06-23 (第38轮)

## 概览
- **通读仓库**: 5 个 (rrsjk-item-service, rrsjk-light-common, rrsjk-light-data-service, rrsjk-light-iot-service, rrsjk-light-message-service)
- **总仓库数**: 138
- **本轮性质**: 重扫 (所有仓库均已通读过)
- **策略**: Delta discovery — 仅关注新增提交和新增业务逻辑

## 各仓库分析

### 1. rrsjk-item-service (商品服务)
- **HEAD**: bad1823d6b20 | 最后提交: 2026-04-08
- **业务文件**: 227 个
- **新增提交**: 0 (自上次通读以来无变更)
- **结论**: 无需更新 KB。已有完整文档 `domains/item-service.md` (322行)

### 2. rrsjk-light-common (公共基础库)
- **HEAD**: f6ab440a63ef | 最后提交: 2026-06-18
- **业务文件**: 13 个
- **新增提交**: 1 (feat(trace): 新增 Spring Boot 3 入口 traceId 过滤器与 logback converter, 解钦, 2026-06-17)
- **KB 更新**: 
  - ✅ `domains/operation-and-data.md` — 追加 WebTraceAutoConfiguration 文档 (SB3 jakarta.servlet 兼容)

### 3. rrsjk-light-data-service (发电数据服务)
- **HEAD**: c446b670cd4f | 最后提交: 2026-06-23
- **业务文件**: 318 个
- **新增提交**: 6 (2026-06-12~23)
  - fix: 修复爱士惟图表实时写入延迟 (yumiao)
  - fix: increase inverter data dubbo payload (yumiao)
  - fix: optimize aiswei energy fill under backlog (yumiao)
  - feat: 新增三天发电量作业到大数据DWS相关表 (majinhu)
  - feat: calculateFirstDayDws同步相关逻辑 (majinhu)
  - feat: 只更新大数据的表 / 新增类型 type 区分日志 (majinhu)
- **KB 更新**:
  - ✅ `domains/inverter-data.md` — 追加 `sn_province_config` 表文档 (SN→省份编码映射)
  - ✅ `domains/inverter-data.md` — 追加爱士惟数据处理线程池架构 (5个专用线程池)
  - ✅ `data/tables.md` — 追加 `sn_province_config` 表结构

### 4. rrsjk-light-iot-service (IoT 服务)
- **HEAD**: 7dcf95b5137c | 最后提交: 2025-12-01
- **业务文件**: 23 个
- **新增提交**: 0 (自初始化以来无变更)
- **KB 更新**:
  - ✅ `domains/iot-service.md` — 追加 Dubbo 服务依赖分析 (22个 Dubbo reference)
  - ✅ `domains/iot-service.md` — 追加 Kafka 消费配置

### 5. rrsjk-light-message-service (消息服务)
- **HEAD**: a4310b963354 | 最后提交: 2026-05-28
- **业务文件**: 56 个
- **新增提交**: 0 (最近提交为 JVM heap 优化, 2026-05-28)
- **结论**: 无需更新 KB。已有完整文档 `domains/message-service.md` (309行)

## 知识库更新汇总

| 文件 | 操作 | 新增内容 |
|---|---|---|
| `domains/inverter-data.md` | patch 追加 | SN-省份编码映射表 (sn_province_config) + 爱士惟线程池架构 |
| `domains/iot-service.md` | patch 追加 | Dubbo 服务依赖 (22个) + Kafka 消费配置 |
| `domains/operation-and-data.md` | patch 追加 | WebTraceAutoConfiguration (SB3 兼容) |
| `data/tables.md` | patch 追加 | sn_province_config 表结构 |

## 关键发现

1. **sn_province_config 表**: 新增的逆变器SN→省份编码映射表，用于 Kafka 省份 Topic 路由。此前 KB 只记录了省份 Topic 双写的概念，但未记录支撑该功能的配置表结构。

2. **爱士惟线程池架构**: 5个专用线程池 (aishiweiHandleElectricData/aishiweiRealtimeDataExecutor/aisweiInveterHistoryBatch*/aisweiInveterDataBuild*/aisweiInveterHistoryJob*) 体现了数据流水线的分阶段设计，最大线程池 `aisweiInveterDataBuildThreadPoolExecutor` 配置 4096/8192 线程 + 65K 队列。

3. **IoT 服务定位更新**: 通过 service.xml 的 22 个 Dubbo reference 分析，IoT 服务不仅是设备接入层，更是运维+零碳+合同的聚合服务入口。

4. **Spring Boot 3 迁移信号**: `WebTraceAutoConfiguration` 是 rrsjk-light-common 为 SB3 项目提供的首个兼容组件，使用 jakarta.servlet-api 5.0.0 + 条件装配，表明团队正在为 SB2→SB3 迁移做准备。
