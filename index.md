# PVS 知识索引

更新时间: 2026-05-17 (整合)

## 概况

| 指标 | 数值 |
|---|---|
| 总仓库数 | 100 (PVS 72 + VPP/其他 28) |
| 已通读 | 66/100 (66%) |
| 知识库文件 | 65 个 |
| 知识库大小 | 6.4MB |
| Domain 业务文件 | 25 个 (326KB) |
| Source-map 索引 | 47,009 行 |

## 仓库通读进度

### Java 后端（46/60 已通读）
- **未通读 14 个**: cbs-web(438 Java), nahuipv-hnzc-app-android(220), vpp-api-auth(92), rrs-dispenser-server(63), system-service(54), rrsjk-light-common(50), rrsjk-migration-member(48), job-service(41), item-service(34), rrsjk-activity-service(31), rrsjk-app-web(30), rrsjk-light-iot-service(29), rrsjk-pay-web(29), r_upgrade(25)

### 前端/移动端/其他（20/40 已通读）
- 主要为 Flutter 包装层、iOS 原生、微信小程序、H5 页面等

## 目录

### domains/ — 业务域知识 (25 个文件)
- **电站与运维**: station-lifecycle, inverter-data, investor-management, operation-and-data, zero-carbon-station
- **审核审批**: approval ⭐ (CBS 三审流程完整)
- **交易订单**: order-and-trade, settlement, inventory, policy
- **核心服务**: additional-core-services, web-and-additional-services, frontend-and-misc-services, remaining-services-and-frontends
- **资方对接**: zhaoyin-lease, guangfa-business
- **派单管理**: dispatch-order-scheduled-tasks
- **收入策略**: income-mode-strategies
- **移动端**: mobile-app-architecture
- **VPP 项目**: vpp-overview, vpp-data, vpp-gec, vpp-green-electricity, vpp-system-management, vpp-thai-dashboard, vpp-knowledge-management, vpp-product-shipment

### modules/ — 代码仓库索引
- repositories.md: PVS 100 个仓库索引 (66/100 已通读 ✅)
- vpp-repositories.md: VPP 仓库索引

### data/ — 表/枚举/API
- tables.md: 数据库表结构
- enums.md: 枚举值定义
- java-enums.md: Java 枚举文件索引
- api-endpoints.md: API 端点映射
- sql-table-refs.md: SQL 表名到 Mapper 引用
- db-schema-index.md: 数据库 Schema 索引 (228KB)
- business-table-mapping.md: **业务概念 → 数据库表映射** (3,402 Mapper XML扫描生成)
- query-templates.md: 生产 MySQL 高频查询模板

### source-map/ — 代码索引 (47K 行)
- controllers.md: Controller/API 静态入口 (16,955 行, 803KB)
- java-symbols.md: Java 类/接口/枚举 (19,776 行, 3.4MB)
- mybatis-mappers.md: MyBatis XML statement (10,278 行, 761KB)
- files.md: 文件到业务域映射 (65 行)

### ops/ — 运维
- deployment-map.md: 生产部署拓扑
- nginx-route-map.md: Nginx/H5 路由

### daily/ — 每日报告
- daily/YYYY-MM-DD.md: 每日学习报告
- daily/raw/YYYY-MM-DD.md: 原始扫描材料

### 其他
- domain-router.md: 业务域到知识库/代码/表/MCP 路由表
- evals/qa-regression-set.md: 业务问答回归问题集
- decisions/index.md: 决策索引
- runbooks/hermes-gateway.md: Hermes 网关运维手册

## VPP 项目知识库
- domains/vpp-overview.md: VPP 项目概述与架构 (31KB)
- domains/vpp-data.md: VPP 数据平台与爬虫 (9KB)
- domains/vpp-gec.md: VPP GECT 服务 (18KB)
- domains/vpp-green-electricity.md: VPP 绿电 (12KB)
- domains/vpp-system-management.md: VPP 系统管理 (10KB)
- domains/vpp-thai-dashboard.md: VPP 泰国 Dashboard (8KB)
- domains/vpp-knowledge-management.md: VPP 知识管理 (6KB)
- domains/vpp-product-shipment.md: VPP 产品发货 (3KB)

## 关键业务域覆盖

| 业务域 | 覆盖程度 | 核心文件 |
|---|---|---|
| 电站生命周期 | ✅ 完整 | station-lifecycle.md |
| CBS 三审流程 | ✅ 完整 | approval.md |
| 运维运营 | ✅ 完整 | operation-and-data.md |
| 订单与交易 | ✅ 完整 | order-and-trade.md |
| 核心服务(维修/商品/支付等) | ✅ 完整 | additional-core-services.md |
| Web层与附加服务 | ✅ 完整 | web-and-additional-services.md |
| 前端与杂项 | ✅ 完整 | frontend-and-misc-services.md |
| 剩余服务 | ✅ 完整 | remaining-services-and-frontends.md |
| 招银租赁 | ✅ 完整 | zhaoyin-lease.md |
| 广发业务 | ✅ 完整 | guangfa-business.md |
| 资方管理 | ✅ 完整 | investor-management.md |
| 逆变器数据 | ✅ 完整 | inverter-data.md |
| 结算/财务 | ✅ 完整 | settlement.md |
| 政策/奖励 | ✅ 完整 | policy.md |
| 仓储/调拨 | ✅ 完整 | inventory.md |
| VPP 整体架构 | ✅ 完整 | vpp-overview.md |

- source-map/controllers.md：Controller/API 静态入口索引。
- source-map/java-symbols.md：Java 类、接口、枚举到文件路径索引。
- source-map/mybatis-mappers.md：MyBatis XML statement 和表引用索引。
- data/sql-table-refs.md：SQL 表名到 Mapper 文件引用索引。
- data/java-enums.md：Java 枚举文件索引。
