     1|# PVS 知识索引
     2|
更新时间: 2026-06-07

## 概况

| 指标 | 数值 |
|---|---|
| 总仓库数 | 122 (PVS 97 + VPP/其他 25) |
| 已通读 | 122/122 (第23轮) |
| 知识库文件 | 70+ 个 |
| 知识库大小 | 6.8MB+ |
| Domain 业务文件 | 45+ 个 |
| Source-map 索引 | 47,009+ 行 |

## 仓库通读进度

### 全部 122/122 个仓库已通读 (第23轮，2026-06-07)
- 本轮通读 5 个: vpp-crawler, vpp-data-platform, vpp-openapi, vpp-pv-oversea, vpp-template
- **重扫发现**: 
  - **vpp-data-platform**: 时序数据新增 toNameList 设备名称筛选; TsKvServiceImpl 支持三组外部 API 凭证降级 (zhijia@haier/qdsg@shougang/zhjt2025@cnnc); TsKvDO 改为 BaseDO 不再需要租户隔离
  - **vpp-pv-oversea**: SAP 发票记账凭证功能; 即采即销单付款计划验证; SAP 销售订单计费作业优化(空指针修复/重试调整); 电站信息并发安全修复
  - **vpp-crawler/openapi/template**: 无新提交，知识库已完整覆盖

## 目录

### domains/ — 业务域知识 (45+ 个文件)
- **电站与运维**: station-lifecycle, inverter-data, investor-management, operation-and-data, zero-carbon-station
- **审核审批**: approval ⭐ (CBS 三审流程完整 + Flowable 流程引擎)
- **交易订单**: order-and-trade, settlement, inventory, policy, **order-dispatch-delivery** ⭐ (下单-配货-发货全链路)
- **核心服务**: additional-core-services, web-and-additional-services, frontend-and-misc-services, remaining-services-and-frontends
- **基础系统**: **system-infra-service** ⭐ (银行/地区/OCR/日历/字典/短信/定时任务/支付账号)
- **CBS管理**: cbs-management ⭐ (用户/角色/菜单/权限/团体组织架构)
- **资方对接**: zhaoyin-lease, guangfa-business
- **派单管理**: dispatch-order-scheduled-tasks
- **收入策略**: income-mode-strategies
- **移动端**: mobile-app-architecture
- **渠道电商**: echannel-service ⭐ (多渠道订单聚合)
- **储能服务**: energy-storage-service ⭐ (收益测算/充放电策略)
- **HDS Web**: hds-web ⭐ (EPC项目/电站管理/API入口)
- **VPP 项目**: vpp-overview, vpp-data, vpp-gec, vpp-green-electricity, vpp-system-management, vpp-thai-dashboard, vpp-knowledge-management, vpp-product-shipment

### modules/ — 代码仓库索引
- repositories.md: PVS 100 个仓库索引 (100/100 已通读 ✅)
- vpp-repositories.md: VPP 仓库索引
    40|
    41|### data/ — 表/枚举/API
    42|- tables.md: 数据库表结构
    43|- enums.md: 枚举值定义
    44|- java-enums.md: Java 枚举文件索引
    45|- api-endpoints.md: API 端点映射
    46|- sql-table-refs.md: SQL 表名到 Mapper 引用
    47|- db-schema-index.md: 数据库 Schema 索引 (228KB)
    48|- business-table-mapping.md: **业务概念 → 数据库表映射** (3,402 Mapper XML扫描生成)
    49|- query-templates.md: 生产 MySQL 高频查询模板
    50|
    51|### source-map/ — 代码索引 (47K 行)
    52|- controllers.md: Controller/API 静态入口 (16,955 行, 803KB)
    53|- java-symbols.md: Java 类/接口/枚举 (19,776 行, 3.4MB)
    54|- mybatis-mappers.md: MyBatis XML statement (10,278 行, 761KB)
    55|- files.md: 文件到业务域映射 (65 行)
    56|
    57|### ops/ — 运维
    58|- deployment-map.md: 生产部署拓扑
    59|- nginx-route-map.md: Nginx/H5 路由
    60|
    61|### daily/ — 每日报告
    62|- daily/YYYY-MM-DD.md: 每日学习报告
    63|- daily/raw/YYYY-MM-DD.md: 原始扫描材料
    64|
    65|### 其他
    66|- domain-router.md: 业务域到知识库/代码/表/MCP 路由表
    67|- evals/qa-regression-set.md: 业务问答回归问题集
    68|- decisions/index.md: 决策索引
    69|- runbooks/hermes-gateway.md: Hermes 网关运维手册
    70|
    71|## VPP 项目知识库
    72|- domains/vpp-overview.md: VPP 项目概述与架构 (31KB)
    73|- domains/vpp-data.md: VPP 数据平台与爬虫 (9KB)
    74|- domains/vpp-gec.md: VPP GECT 服务 (18KB)
    75|- domains/vpp-green-electricity.md: VPP 绿电 (12KB)
    76|- domains/vpp-system-management.md: VPP 系统管理 (10KB)
    77|- domains/vpp-thai-dashboard.md: VPP 泰国 Dashboard (8KB)
    78|- domains/vpp-knowledge-management.md: VPP 知识管理 (6KB)
    79|- domains/vpp-product-shipment.md: VPP 产品发货 (3KB)
    80|
    81|## 关键业务域覆盖
    82|
    83|| 业务域 | 覆盖程度 | 核心文件 |
    84||---|---|---|
    85|| 电站生命周期 | ✅ 完整 | station-lifecycle.md |
    86|| CBS 三审流程 | ✅ 完整 | approval.md |
    87|| 运维运营 | ✅ 完整 | operation-and-data.md |
    88|| 订单与交易 | ✅ 完整 | order-and-trade.md |
    89|| 核心服务(维修/商品/支付等) | ✅ 完整 | additional-core-services.md |
    90|| Web层与附加服务 | ✅ 完整 | web-and-additional-services.md |
    91|| 前端与杂项 | ✅ 完整 | frontend-and-misc-services.md |
    92|| 剩余服务 | ✅ 完整 | remaining-services-and-frontends.md |
    93|| 招银租赁 | ✅ 完整 | zhaoyin-lease.md |
    94|| 广发业务 | ✅ 完整 | guangfa-business.md |
    95|| 资方管理 | ✅ 完整 | investor-management.md |
    96|| 逆变器数据 | ✅ 完整 | inverter-data.md |
    97|| 结算/财务 | ✅ 完整 | settlement.md |
    98|| 政策/奖励 | ✅ 完整 | policy.md |
    99|| 仓储/调拨 | ✅ 完整 | inventory.md |
|| **下单-配货-发货** | ✅ 完整 | order-dispatch-delivery.md ⭐ |
   100|| VPP 整体架构 | ✅ 完整 | vpp-overview.md |
   101|
   102|- source-map/controllers.md：Controller/API 静态入口索引。
   103|- source-map/java-symbols.md：Java 类、接口、枚举到文件路径索引。
   104|- source-map/mybatis-mappers.md：MyBatis XML statement 和表引用索引。
   105|- data/sql-table-refs.md：SQL 表名到 Mapper 文件引用索引。
   106|- data/java-enums.md：Java 枚举文件索引。
   107|
