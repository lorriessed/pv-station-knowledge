# VPP 数据平台与爬虫

最后更新: 2026-06-07

## 1. vpp-data-platform (数据平台) — 全量通读更新

### 1.1 定位
VPP 数据平台是连接爬虫数据与业务系统的中间层，负责接收爬虫推送数据、提供动态查询能力、管理数据白名单，并将数据分发到下游 Kafka。

### 1.2 技术栈
- Spring Boot 2.5.5 + JDK 8
- Spring Cloud 2020.0.4 + Alibaba 2021.1
- MyBatis-Plus + mybatis-plus-join
- Druid 连接池
- Kafka (Haier Energy 公网 Kafka)
- SelectDB (分析型数据库)
- Aliyun OSS
- XXL-JOB 定时任务
- Nacos (多环境)

### 1.3 核心功能模块

| 模块 | 说明 |
|---|---|
| **爬虫数据接收** | 接收爬虫推送数据，经 Kafka 转发到光伏数据流 |
| **动态查询** | 支持指定数据库(test/ods/dwd/dwt/ads/metadata/ai)和表名进行动态分页查询 |
| **白名单校验** | 操作人必须配置白名单才能查询指定库表 |
| **时序数据查询** | 基于 SelectDB 的 ts_kv_cf 表查询设备时序数据 |
| **文件上传** | CSV/TXT 文件上传，自动解析写入 SelectDB ODS 库 |
| **电价查询** | 查询日前电价和实时电价数据 |
| **绿能报表** | 绿能分时发电量日报表查询 |
| **爬虫数据查询** | 发电企业、电力用户基本信息查询(四川电力交易中心) |

### 1.4 Controller 路由

| 路由 | 方法 | 功能 |
|---|---|---|
| `/platform/crawlScMembersGeneration/findByPage` | GET | 发电企业分页查询 |
| `/platform/crawlScMembersGeneration/export` | GET | 发电企业导出 |
| `/platform/crawlScMembersUsersDetail/findByPage` | GET | 电力用户分页查询 |
| `/platform/crawlScMembersUsersDetail/export` | GET | 电力用户导出 |
| `/crawlerData/pushData` | POST | 接收爬虫推送数据 → Kafka |
| `/platform/electricityPrice/query` | POST | 电价数据查询 (dayAhead/realTime) |
| `/platform/upload_file/upload_file` | POST | 文件上传(写入SelectDB ODS) |
| `/platform/dynamic/queryByPage` | POST | 动态分页查询 (白名单校验) |
| `/platform/tskv/queryByPageWithTimeRange` | POST | 时序数据分页查询 |
| `/platform/greenEnergyReportStationCityDay/findByPage` | GET | 绿能分时发电量日报表 |

### 1.5 多数据源配置

| 数据源 | Bean 名 | 用途 |
|---|---|---|
| ODS | `odsDataSource` / `odsSqlSessionFactory` | 操作数据层 (MyBatis-Plus Mapper) |
| ADS | `adsDataSource` / `adsSqlSessionFactory` | 应用数据层 (MyBatis-Plus Mapper) |
| SelectDB | `selectDbDataSource` / `selectDbJdbcTemplate` | SelectDB 分析型数据库 |
| Test | `testDataSource` / `testJdbcTemplate` | 测试数据库 |
| DWD | `dwdDataSource` / `dwdJdbcTemplate` | 数据仓库明细层 |
| DWT | `dwtDataSource` / `dwtJdbcTemplate` | 数据仓库主题层 |
| Metadata | `metadataDataSource` / `metadataJdbcTemplate` | 元数据库 (白名单/审计) |
| AI | `aiDataSource` / `aiJdbcTemplate` | AI 数据 |

### 1.6 动态查询安全机制 (代码明确证明)

**白名单校验流程** (`DynamicQueryWhitelistServiceImpl`):
1. 校验操作人 (auditUser) 是否在 `dynamic_query_user_whitelist` 表中
2. 校验用户状态 is_active = 1
3. 加载用户规则 `dynamic_query_user_whitelist_rule`
4. 校验规则是否启用、是否过期
5. 匹配数据库名和表名 (支持 `*` 通配符)
6. 无权限则抛出 `IllegalArgumentException`

**审计日志** (`DynamicQueryAuditServiceImpl`):
- 每次查询(成功/失败)都记录到 `dynamic_query_audit_log` 表
- 记录: trace_id, audit_user, database_name, table_name, 查询条件、分页参数、耗时

**SQL 注入防护**:
- 表名/字段名校验: `^[a-zA-Z_][a-zA-Z0-9_]*$`
- 所有参数使用 PreparedStatement (?)

### 1.7 文件上传功能 (`FileUploadService`)

**流程**:
1. 文件上传 → OSS 备份 (`upload_file/data/ods/{table}/yyyy/MM/dd/uuid_filename`)
2. 解析 CSV/TXT 文件内容
3. 智能建表: 表存在则校验元数据，不存在则自动创建 (DUPLICATE 模型)
4. 批量插入 SelectDB ODS 库

**限制**:
- 文件大小 ≤ 100MB
- 支持 CSV 和 TXT (每行一个 JSON)
- 表名从文件名提取 (去除扩展名)

### 1.8 时序数据查询 (`TsKvService`)

- 表: `ts_kv_cf` (SelectDB)
- 字段: entity_id, entity_type, key, ts, bool_v, str_v, long_v, dbl_v, json_v
- 支持按 entity_id + 时间范围分页查询
- **2026-06-01 新增**: 支持 `toNameList` 设备名称筛选 — 先通过外部设备关系 API 按设备名称过滤，再查询时序数据 (commit 4619d59, 宋欣儒)
- 通过外部 API (hnzliot.nahuipv.com) 获取设备关系和名称映射
- **三组凭证降级**: `zhijia@haier.com` → `qdsg@shougang.com` → `zhjt2025@cnnc.com`，逐级尝试获取设备信息
- **2026-05-26 变更**: `TsKvDO` 继承基类从 `AbstractTenantDO` 改为 `BaseDO`，时序数据不再需要租户隔离

### 1.9 Kafka 配置

- Kafka 生产者 Topic: `${kafka.producer.topic}`
- SSL/SASL 认证 (SCRAM 或 PLAIN)
- 异步发送，线程池 `kafkaProducerExecutor` (CPU核数核心线程)
- 幂等性: `enable.idempotence = true`

### 1.10 电价查询 (`ElectricityPriceService`)

- 表: `ods.electricity_price_data_clearing` (SelectDB)
- type: `dayAhead` → 日前电价列 (day_ahead)
- type: `realTime` → 实时电价列 (real_time)
- 返回字段: data_region_name, info_date, info_time, 电价, regulate
- **2026-05-15 更新**: `ElectricityPriceQueryDTO` 新增区域参数支持，`ElectricityPriceServiceImpl` 适配区域维度的电价查询 (commit b229befe, 宋欣儒)

## 2. vpp-crawler (爬虫) — 全量通读更新

### 2.1 定位
Python 爬虫系统，从四川电力交易中心爬取市场主体数据和电力市场曲线数据。

### 2.2 技术栈
- Python 3.x
- MySQL + Apache Doris 双写
- RocketMQ 5.1.4 (消息队列)
- 自定义任务调度系统

### 2.3 项目结构
```
vpp-crawler/
├── docker/rocketmq/         # RocketMQ docker-compose
├── scripts/
│   ├── init_mysql_tables.sql    # MySQL 建表脚本
│   ├── add_detail_tables.sql    # 明细表追加
│   └── scheduler/
│       └── config.example.yaml  # 调度器配置
└── src/crawler/
    └── db/
        ├── migrations/
        │   ├── 001_create_task_scheduler_tables.sql
        │   └── 002_create_token_renewal_log_table.sql
        └── schema.sql       # Doris 建表脚本 (crawl_sc_ 前缀)
```

### 2.4 数据库表

**MySQL 表 (MySQL)**:
| 表名 | 说明 |
|---|---|
| `crawl_sc_members_users` | 电力用户列表 |
| `crawl_sc_members_users_detail` | 电力用户明细 (完整信息) |
| `crawl_sc_members_generation` | 发电企业列表 |
| `crawl_sc_members_generation_detail` | 发电企业明细 (机组信息) |
| `crawl_sc_members_sales` | 售电公司列表 |
| `crawl_sc_members_sales_detail` | 售电公司明细 (资产/人员/股权) |
| `crawl_sc_curve_load_forecast` | 负荷预测曲线 (96点) |
| `crawl_sc_curve_load_actual` | 负荷实际曲线 |
| `crawl_sc_curve_hydro_forecast` | 水电出力预测曲线 |
| `crawl_sc_curve_hydro_actual` | 水电出力实际曲线 |
| `crawl_sc_curve_power_forecast` | 火电出力预测曲线 |
| `crawl_sc_curve_power_actual` | 火电出力实际曲线 |
| `crawl_sc_curve_renewable_forecast` | 新能源出力预测曲线 |
| `crawl_sc_curve_renewable_actual` | 新能源出力实际曲线 |
| `crawl_sc_curve_nonmarket_forecast` | 非市场机组出力预测曲线 |
| `task_template` | 任务模板表 |
| `task_instance` | 任务实例表 |
| `crawl_sc_token_renewal_log` | Token 续约日志 |
| `crawl_sc_login_session` | 登录会话 (60分钟有效期) |

**Doris 表 (Apache Doris)**:
| 表名 | 说明 | 分桶 |
|---|---|---|
| `crawl_sc_members_users` | 电力用户列表 | BUCKETS 8 |
| `crawl_sc_members_users_detail` | 电力用户明细 | BUCKETS 8 |
| `crawl_sc_members_generation` | 发电企业列表 | BUCKETS 4 |
| `crawl_sc_members_sales` | 售电公司列表 | BUCKETS 4 |
| `crawl_sc_task_status` | 任务执行状态 | BUCKETS 4 |
| `crawl_sc_task_logs` | 任务执行日志 | BUCKETS 4 |
| `crawl_sc_login_session` | 登录会话 | BUCKETS 1 |

### 2.5 任务调度系统

**调度配置** (`config.example.yaml`):
- 任务生成: 每天凌晨 0:05 (Asia/Shanghai)
- 轮询间隔: 30 秒
- 最大并发: 3 个任务
- 文件锁超时: 60 秒

**任务模板 (task_template)**:
- task_type: `download` / `push`
- task_category: `users` / `generation` / `curves` 等
- schedule_rule: `daily` / `monthly_1st` / `weekly_mon`
- 支持任务依赖 (`depends_on` JSON 数组)
- 省份级别隔离 (`province_code`)

**任务实例 (task_instance)**:
- 状态: `PENDING` → `RUNNING` → `SUCCESS` / `FAILED` / `SKIPPED`
- 支持依赖关系 (depends_on 实例ID列表)
- 重试机制 (max_retry_times, retry_count)
- 进度追踪 (progress, total_records, processed_records)

### 2.6 数据推送流程
```
爬虫抓取 → MySQL/Doris存储 → 推送API → vpp-data-platform (/crawlerData/pushData)
  → Kafka → 下游消费 (光伏业务系统)
```

### 2.7 Token 管理
- 登录会话表: `crawl_sc_login_session`
- 字段: username, x_ticket, admin_token, cookies_json
- 有效期: 60 分钟
- 自动续约: 记录到 `crawl_sc_token_renewal_log` 表

## 3. 待深入

- [ ] 爬虫具体数据源 URL 和认证方式
- [ ] VPP 数据平台的 XXL-JOB 任务列表
- [ ] 爬虫与 Doris 的同步频率
- [ ] 电价数据的来源系统
- [ ] SelectDB 的集群部署信息
