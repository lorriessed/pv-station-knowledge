# rrsjk-pvbusiness-job-service — 光伏业务定时任务服务

> 光伏业务的**定时任务专用服务**，负责资产推送(HSCC)、超期库存管控报表、GVS库龄分析等后台批处理任务。提供自定义分布式锁框架 `@SingleJob`，支持看门狗自动续期。

**仓库**: `rrsjk-pvbusiness-job-service` → `/data/pvcode/rrsjk-pvbusiness-job-service`
**分支**: master | HEAD: fa67f619c672
**最后提交**: 2025-06-16 (锁续期优化)
**证据等级**: 代码明确证明 (2026-07-01 全量通读)

---

## 项目结构

- **模块**: `rrsjk-pvbusiness-job-api` (接口/DTO) + `rrsjk-pvbusiness-job-impl` (实现)
- **包路径**: `com.rrsjk.pvbusinessjob`
- **技术栈**: Spring Boot 2.2 + Dubbo 2.7.4 + MyBatis + Redis + Guava EventBus
- **部署方式**: JSW daemon (appassembler-maven-plugin)

### 多数据源架构 (7个数据源)

| Bean名 | 配置前缀 | 用途 |
|--------|---------|------|
| `local` | `spring.local.datasource` | 本地业务库 (资产申请日志等) |
| `light` | `spring.light.datasource` | 光伏核心库 (light_company_info, light_own_asset) |
| `report` | `spring.report.datasource` | 报表库 (库存管控、库龄分析) |
| `elec` | `spring.elec.datasource` | 电力数据库 |
| `operation` | `spring.operation.datasource` | 运维数据库 |
| `shop` | `spring.shop.datasource` | 商城数据库 |
| `finance` | `spring.finance.datasource` | 财务数据库 |

**生产环境数据库实例**:
- local/light/report/operation/shop/finance → `db003.rrsjk.internal` (rrscom)
- elec → `db006.rrsjk.internal` (rrscom)
- Redis → `r-m5e18tcq2ibkvys7t6.redis.rds.aliyuncs.com:6379`

**来源**: `MybatisConfig.java`, `application-prod.yml` (代码明确证明)

---

## @SingleJob 分布式锁框架

### 注解定义
**来源**: `annotation/SingleJob.java`

```java
@Target(ElementType.METHOD)
@Retention(RetentionPolicy.RUNTIME)
public @interface SingleJob {
    String jobName() default "defaultJob";
    long maxLockTimeMilliSeconds() default -1;  // 默认3分钟
    boolean skipOnLockFail() default true;       // true=跳过, false=降级执行
}
```

### 切面逻辑
**来源**: `aspect/SingleJobAspect.java`

**执行流程**:
1. 尝试获取 Redis 分布式锁 (`RedisLockUtil.tryGetDistributedLock`)
2. 获取成功 → 启动**看门狗续期任务** (间隔 = maxLockTime/3)
3. 异步提交到 `jobExecutor` 线程池执行
4. 执行完毕 → 取消续期 + 释放锁
5. 获取失败 → 根据 `skipOnLockFail` 决定跳过或降级执行

**关键设计**:
- **看门狗续期**: `ScheduledExecutorService` 单线程守护线程池，每 maxLockTime/3 刷新一次 TTL
- **续期失败检测**: 如果续期返回 false (锁已被其他节点释放)，打 warn 日志
- **日志防刷屏**: 按 jobName 控制，60秒内只打一次"跳过"日志
- **降级模式**: `skipOnLockFail=false` 时，即使获取锁失败也执行任务 (无锁模式)
- **全局开关**: `single-job.enabled` 配置项可禁用所有分布式锁校验

**来源**: `SingleJobAspect.java` (代码明确证明, 2026-07-01 通读)

---

## 光伏自有资产管理 (LightOwnAssetService)

### 业务概述
管理光伏**自有资产**（使用权资产/租赁资产）的全生命周期：导入 → 推送HSCC → 跟踪审批状态。

### 核心数据表

| 表名 | 数据源 | 用途 |
|------|--------|------|
| `light_own_asset` | light | 自有资产主表 |
| `light_own_asset_status` | light | 资产审批状态变更记录 |
| `light_asset_application_log` | local | HSCC接口调用日志 |
| `light_company_info` | light | 项目公司信息 |

### light_own_asset 关键字段

| 字段 | 说明 |
|------|------|
| `cbs_id` | CBS主键 (LOA+日期+6位序号, 如 LOA20260701000001) |
| `contract_number` | 合同编号 |
| `contract_name` | 合同名称 |
| `lessor_code` | 出租方编码 |
| `lessee_code` | 承租方编码 (关联 light_company_info.company_code) |
| `asset_type` | 资产类型 (AssetTypeEnum) |
| `cbs_type` | CBS类型 (固定 STATION) |
| `status` | 状态 (StatusEnum: IMPORTED→TRANSFERRED→WAIT_AUDIT→...) |
| `uuid` | 租赁系统主键 (HSCC返回) |
| `serial_number` | 单据号 (HSCC返回) |
| `belnr` | SAP记账凭证号 |
| `rent_total` | 租金合计 |
| `tax_flag` | 是否保税 |
| `invoice_method` | 发票选项 |
| `invoice_type` | 发票类型 |
| `payment_type` | 付款类型 |
| `lease_type` | 付款周期 |

### 资产状态流转 (StatusEnum)

| 状态值 | 含义 | 说明 |
|--------|------|------|
| `IMPORTED` | 已导入 | 批量导入后初始状态 |
| `TRANSFERRED` | 已推送 | 成功推送到HSCC后 |
| `WAIT_AUDIT` | 待审核 | HSCC接收后进入审批 |
| `ERROR` | 异常 | 状态查询返回空值时 |

**来源**: `LightOwnAssetServiceImpl.java`, `LightOwnAsset.xml` (代码明确证明)

### 资产导入流程 (batchInsert)

**来源**: `LightOwnAssetServiceImpl.batchInsert()` (代码明确证明)

1. **校验合同编号唯一性**: 查 `light_own_asset` 是否已存在相同 contract_number
2. **校验合同编号不重复**: 本次导入列表内不能有重复
3. **校验项目公司**: lessee_code 必须在 `light_company_info` (status=ENABLE) 中存在
4. **校验枚举值**: asset_type, tax_flag, invoice_method, invoice_type, payment_type, lease_type 必须是合法枚举值
5. **填充成本中心**: 从 light_company_info 获取 cost_center_code → use_department_code + mgr_cost_center
6. **生成CBS编号**: `LOA` + yyyyMMdd + 6位序号
7. **逐条插入**: 写入 `light_own_asset` (status=IMPORTED)
8. **异步推送HSCC**: 提交到 `pushAssetExecutor` 线程池

### HSCC 资产接口集成

**来源**: `LightAssetInterfaceServiceImpl.java` (代码明确证明)

#### 接口地址
| 环境 | 推送 (ApplicationInterface) | 查询 (QueryInterface) |
|------|---------------------------|---------------------|
| 测试 | `http://hscapi.haier.net/Test/CBS-RightOfUseAsset/ApplicationInterface` | `http://hscapi.haier.net/Test/CBS-RightOfUseAsset/QueryInterface1` |
| 生产 | `http://hscapi.haier.net/Product/CBS-RightOfUseAsset/ApplicationInterface` | `http://hscapi.haier.net/Product/CBS-RightOfUseAsset/QueryInterface` |

#### 认证机制
```
Header: application-key = {applicationKey}
Header: x-yx-nonce = {UUID}
Header: x-yx-timestamp = {currentTimeMillis}
Header: x-yx-signature = HMAC-SHA256("Application-Key={key}&X-Yx-Nonce={nonce}&X-Yx-Timestamp={ts}", applicationSecret)
```

**配置值** (生产/测试相同):
- applicationKey: `f7407fc21263e50f8a197df8ea7fb7bf`
- applicationSecret: `5b4a4b47e3a3bb09dc27e2eacd747f98`

#### 推送请求格式
```json
{
  "INPUT": [
    {
      "cbsId": "LOA20260701000001",
      "contractNumber": "HT-xxx",
      "lesseeCode": "xxx",
      "assetType": "...",
      "rentTotal": 100000,
      ...
    }
  ]
}
```

#### 查询请求/响应
- 请求: `{"INPUT": ["cbsId1", "cbsId2", ...]}`
- 响应: `AssetQueryResponseDataDto` 包含 status, uuid, serialNumber, belnr, approver, rejectReason 等

### 资产状态定时查询 (queryAssetStatusJob)

**来源**: `LightOwnAssetServiceImpl.queryAssetStatusJob()` (代码明确证明)

1. 查询 status 为 TRANSFERRED 或 WAIT_AUDIT 的资产
2. 批量调用 HSCC 查询接口
3. 将查询结果写入 `light_own_asset_status` (每次查询新增一条记录，保留历史)
4. 更新 `light_own_asset` 的 uuid/serialNumber/belnr/status

---

## 超期库存管控报表 (EnergyOverdueInventoryControlService)

### 业务概述
从 GVS (全球价值流) 系统获取库存库龄数据，按分中心/SKU/汇总维度生成超期库存管控报表。

### 数据表

| 表名 | 维度 | 说明 |
|------|------|------|
| `energy_overdue_inventory_control_summary` | 总表 | 按日汇总，含 overdue_stock_amount 排序 |
| `energy_overdue_inventory_control_center` | 分中心 | 按分中心+服务商维度，含组件/逆变器各库龄段 |
| `energy_overdue_inventory_control_sku` | 物料 | 按SKU维度 |
| `energy_overdue_inventory_control_data_base` | 基础数据 | 原始数据 |

### 库龄分段 (Center表字段)

| 分段 | 组件字段前缀 | 逆变器字段前缀 |
|------|-------------|---------------|
| 60天内 | `module_quantity_day_60/amount/process` | `inverter_quantity_day_60/...` |
| 90天内 | `module_quantity_day_90/...` | `inverter_quantity_day_90/...` |
| 120天内 | `module_quantity_day_120/...` | `inverter_quantity_day_120/...` |
| 150天内 | `module_quantity_day_150/...` | `inverter_quantity_day_150/...` |
| 180天内 | `module_quantity_day_180/...` | `inverter_quantity_day_180/...` |
| 360天内 | `module_quantity_day_360/...` | `inverter_quantity_day_360/...` |
| 1-2年 | `module_quantity_year_1/...` | `inverter_quantity_year_1/...` |
| 2-3年 | `module_quantity_year_2/...` | `inverter_quantity_year_2/...` |
| 3年以上 | `module_quantity_year_3/...` | `inverter_quantity_year_3/...` |

每个分段有 quantity(数量)、amount(金额)、process(占比/处理进度) 三个指标。

**来源**: `EnergyOverdueInventoryControlCenter.xml` (代码明确证明)

---

## GVS 仓库库龄分析 (GvsWarehouseAgeAnalysis)

### 业务概述
从 GVS 接口拉取仓库库龄分析数据，按物料+库存地点维度统计各库龄段库存数量和金额。

### GVS 响应结构
```json
{
  "FLAG": "S",           // S=成功, E=异常
  "MESSAGE": "...",
  "OUTPUT": [
    {
      "WERKS": "工厂",
      "MATNR": "物料号",
      "LGORT": "库存地点",
      "MAKTX": "物料描述",
      "BRAND": "品牌",
      "KCSL": 总数量,
      "KCSL30": "1-30天数量",
      "KCJE30": "1-30天金额",
      ... (同 Center 表分段)
    }
  ]
}
```

### 相关表
- `gvs_warehouse_age_analysis` — GVS库龄分析原始数据
- `sap_sp_center_relation` — SAP SP 与分中心关联映射

**来源**: `GvsWarehouseAgeAnalysisDao.java`, `GvsResponseDto.java` (代码明确证明)

---

## Dubbo 依赖关系

### 提供的服务 (Dubbo Provider)
- `SampleJobService` — 示例定时任务 (仅用于测试 @SingleJob 框架)

### 引用的服务 (Dubbo Reference)
**来源**: `spring-config/service.xml` (代码明确证明)

| 服务接口 | 来源系统 | 用途 |
|---------|---------|------|
| `MessageService` | rrsjk-system-service | 消息发送 |
| `XiaoweiService` | rrsjk-system-service | 小微部门查询 |
| `AccountAlipayService` | rrsjk-system-service | 支付宝账号 |
| `AccountWechatService` | rrsjk-system-service | 微信账号 |
| `AccountCcbService` | rrsjk-system-service | 建行账号 |
| `AccountKjtService` | rrsjk-system-service | 快捷通账号 |
| `AccountTransferService` | rrsjk-system-service | 转账汇款账号 |
| `AccountBaiduService` | rrsjk-system-service | 百度账号 |
| `MemberService` | rrsjk-member-service | 会员服务 |
| `OrderStatusService` | rrsjk-trade-service | 订单状态 |
| `OrderItemBuyerService` | rrsjk-trade-service | 子订单买家 |
| `OrderTransferService` | rrsjk-trade-service | 订单转让 |
| `OrderRepairService` | rrsjk-trade-service | 退款维修 |
| `OrderLogService` | rrsjk-trade-service | 订单日志 |
| `OrderService` | rrsjk-trade-service | 订单服务 |
| `OrderItemService` | rrsjk-trade-service | 子订单服务 |
| `CloudWisdomUserWalletChangeService` | rrsjk-finance-service | 云智钱包变更 |

---

## 线程池配置

| Bean名 | 核心/最大 | 队列 | 用途 |
|--------|----------|------|------|
| `pushAssetExecutor` | 2/20 | 1000 | 资产推送HSCC |
| `jobExecutor` | 8/40 | 1000 | 定时任务执行 (CallerRunsPolicy) |
| `scheduledJobExecutor` | CPU*2 | - | 定时/延迟任务调度 |
| `lightEventBus` (EventBus) | 10/100 | 10000 | 光伏报表事件总线 |

**来源**: `ThreadPoolExecutorConfig.java`, `EventBusConfig.java` (代码明确证明)

---

## 外部接口汇总

| 接口 | 协议 | 用途 | 认证方式 |
|------|------|------|---------|
| HSCC 资产推送 | HTTP POST | 推送使用权资产到HSCC | application-key + HMAC签名 |
| HSCC 资产查询 | HTTP POST | 查询资产审批状态 | 同上 |
| OBS (对象存储) | HTTP | 文件存储 | publicKey 签名 |
| VM (ERP) | HTTP | Vestwoods ERP 对接 | userName/password |

---

## 知识库更新记录

### 2026-07-01 首次通读
- 创建本文件
- 发现7个数据源架构
- 记录 @SingleJob 分布式锁框架设计
- 记录 HSCC 资产接口集成细节
- 记录超期库存管控报表4维度结构
- 记录 GVS 库龄分析数据结构
