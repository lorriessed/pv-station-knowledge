# 全量通读报告 2026-05-25

## 通读概览

- **轮次**: 第 12 轮
- **仓库数**: 5 个
- **仓库列表**: rrsjk-item-service, rrsjk-light-common, rrsjk-light-data-service, rrsjk-light-iot-service, rrsjk-light-message-service

---

## 各仓库分析

### 1. rrsjk-item-service (227 业务文件)

**核心职责**: 光伏商品/产品管理中心 — SPU/SKU 管理、类目体系、品牌、价格、套餐、ES 搜索、评价。

**关键发现**:
- **三级价格体系**: 商品售价 (ProductPrice) → 保本价 (ProductBreakevenPrice) → 采购成本 (ProductPurchaseCost)，三者按 `skuCode + companyCode` 唯一标识
- **商品发布流程**: 初始化 → SKU 价格校验 → 商品信息校验 → 发布，支持复制和编辑
- **销售渠道差异化**: 零售/零碳/企业客户/专业客户 各有专属字段（起购量、增值分享、县域代卖等）
- **零碳套餐库存**: 独立的库存管理 + 变更流水表，支持扣减/恢复/查询
- **搜索**: 旧搜索服务已标记 @Deprecated，新搜索服务支持 10+ 场景（猜你喜欢、首页、分类、采购、团购、云智妆、农村商店、光伏分类）
- **商品可见性控制**: 按角色维度 (operator/user/all/group) 控制商品显示/隐藏

**新增知识库文件**: `domains/item-service.md`

### 2. rrsjk-light-common (12 业务文件)

**核心职责**: 公共基础库 — 日志框架、Trace 上下文、Manifold 扩展、RocketMQ 集成。

**关键发现**:
- **自定义日志框架**: ControllerLogFilter + DbLogFilter，自动拦截 HTTP 请求和 SQL 执行，写入独立的 log 文件（app/debug/info/warn/error/business_error/link/sql/sql-body/mq/rpc/task）
- **Trace 上下文**: `TraceContext` 管理 thraceId 和 rpcId，支持 RPC 链路追踪，通过 HTTP Header 传递
- **LogDetailTypeEnum**: DETAIL(&) / LINK(^) / LOG(*) / SPECIAL($) — 四种日志表前缀
- **LogTypeEnum**: RPC_PROVIDER(0) / RPC(1) / MQ(2) / DB(3) / TASK(4) / CONTROLLER(5)
- **Manifold 编译期扩展**: 使用 Manifold 实现 Java 编译期元编程
- **RocketMQ 模块**: `rrsjk-light-rocketmq` 独立模块，基于 RocketMQ 4.8.0 + Spring Boot Starter

**知识库更新**: 已在 `domains/operation-and-data.md` 中补充日志框架知识

### 3. rrsjk-light-data-service (263 业务文件)

**核心职责**: 发电数据采集与报表服务 — 多品牌逆变器数据拉取、电站发电统计、外部数据推送。

**本次新增发现 (与已有知识对比)**:
- **锦浪数据重试机制** (2026-05-22, yumiao): 连续三天发电数据多线程处理 + 重试机制，解决锦浪数据拉取不稳定问题
- **逆变器解绑替换增强**: `unBindStationAndReplace()` 支持采集器信息透传（collectorSn, collectorImageUrl, collectorCaptcha），GF 模式扩展
- **逆变器导出排序修复** (2026-05-23, yumiao): 新增专用 `exportPage()` 方法链，解决分页导出排序不一致问题
- **问题电站规则计算**: `calcProblemStation()` 每小时执行，合并计算 rule1/rule2/rule3 写入 `report_problem_station`
- **年度发电汇总**: `calcStationYearSummary()` 每天凌晨 1:30 执行，写入 `report_station_year_summary_YYYY` 分表
- **发电管理报表 Dubbo 服务**: `HdsReportService` — 支持 TOTAL/YEAR/MONTH 三维度分页查询 + 异步导出任务（OSS 下载）
- **预占位机制**: `occupyTodayInveterRecord()` — 查询昨天活跃的 SN，预写入 `e_today=0` 记录，降低白天高并发重复写入风险
- **双写 Kafka**: `KafkaDoubleWriteProperties` — 支持按 SN 码配置双写到新 Kafka 队列
- **多数据源**: local (写) + query (读) + ods (外部数据源)，三个独立的 SqlSessionFactory

**知识库更新**: 已在 `domains/inverter-data.md` 追加上述新发现

### 4. rrsjk-light-iot-service (23 业务文件)

**核心职责**: IoT 设备管理服务 — **初始化阶段**（2025-12-01 创建，仅基础结构）。

**关键发现**:
- 仅包含基础配置（Dubbo、MyBatis、Kafka、Redis、OSS、线程池）
- 一个示例 EventBus Listener (`LightDemoListener`)
- Kafka 消费者配置：消费 `LightInverterRecordKafkaEvent`，重试 3 次，间隔 1s
- Dubbo 引用：依赖 rrsjk-light-api, rrsjk-light-data-api, repairs-api, zero-carbon 等
- **当前无实际业务逻辑**，是 `rrsjk-light-operation-service` 的拆分/迁移目标
- AI 诊断配置: 内网地址 `http://10.2.160.220:5000/api/diagnosis/start`
- 天气 API: `http://api.xiaoxianglink.com/v1/weather/weather`

**知识库更新**: 已在 `domains/operation-and-data.md` 中补充 IoT 服务初始化状态

### 5. rrsjk-light-message-service (56 业务文件)

**核心职责**: 统一消息中心 — 审批/资料/政策/紧急消息管理，已读状态追踪，超期未完工提醒。

**关键发现**:
- **5 种消息类型**: APPROVAL_MESSAGE, DOCUMENT_MESSAGE, POLICY_MESSAGE, URGENT_MESSAGE + 搜索历史
- **用户-消息关系表**: `user_message_relations` 追踪每个用户的已读/同意状态
- **紧急消息范围控制**: 按服务商 (SP) 或分中心 (SUB_CENTER) 维度配置接收范围
- **超期未完工提醒定时任务**:
  - 40-50 天：仅通知一次（Redis 去重，TTL 5 天）
  - 50-60 天：每天通知一次
  - 权限隔离：一级商收到所有超期电站，二级商只收到自己建的站
- **资料消息创建去重**: 按 `documentId` 查询，存在则更新而非新建
- **政策消息创建去重**: 按 `policyId` + `policyMessageType` 查询，但 `BASIC_POLICY` 类型每次都新建
- **RocketMQ 生产者**: Usher 框架封装，`producerName=light_service`
- **阿里云短信**: 支持短信模板发送
- **好签合同服务集成**: 新公司认证、PDF 上传、合同签署

**新增知识库文件**: `domains/message-service.md`

---

## 知识库更新汇总

| 操作 | 文件 | 内容 |
|---|---|---|
| 新增 | `domains/item-service.md` | 商品服务完整业务逻辑 (SPU/SKU/价格/套餐/搜索/评价) |
| 新增 | `domains/message-service.md` | 消息服务完整业务逻辑 (5种消息/超期提醒/范围推送) |
| 追加 | `domains/inverter-data.md` | 锦浪重试机制、逆变器解绑增强、预占位、问题电站规则 |
| 追加 | `domains/operation-and-data.md` | rrsjk-light-common 日志框架、rrsjk-light-iot-service 初始化状态 |

---

## 本次通读未涉及

- rrsjk-light-common 是纯基础设施库，无独立业务逻辑
- rrsjk-light-iot-service 仅基础结构，无业务代码
- 以上两个仓库已在相关 domain 文件中做了简要标注
