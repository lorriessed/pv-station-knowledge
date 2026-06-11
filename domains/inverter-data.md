# 逆变器与发电数据

更新时间: 2026-05-23

## 已确认知识

### 双重绑定
逆变器存在两套绑定关系：完工绑定和发电绑定。

完工绑定记录在 light_station_inverter，完工确认时人工填写 SN，核心流程在 CompleteConfirmServiceImpl。

发电绑定记录在 light_inveter_data，首次拉取发电数据时自动绑定，核心流程在 LightInveterListener 及数据服务。

### 数据处理主线
拉取逆变器数据 -> 保存日数据和明细数据 -> 绑定电站 -> 去重 -> 计算日/月/年/累计图表 -> 计算电站发电 -> 生成或更新功率曲线。

### 数据源
已知逆变器数据源包括 AISWEI、GINLOG、SINENG、HOPEWIND、KSOLAR。

### 锦浪特殊逻辑
锦浪早上 5 点可能返回昨晚离线数据；当 e_today=0 时不能覆盖真实发电数据，需要跳过。

### 锦浪逆变器数据修复 (2026-05-12)
**来源**: `rrsjk-light-data-service` → `GinlongPullMessageClient.java`, `GinlongService.java`, `LightInveterServiceImpl.java`, `LightInverterCommon.java`, `GinlongProperties.java`, `ThreadPoolConfig.java`, `LightInveter.xml` (commits 30f4636~c50bee6, yumiao, 2026-05-12)
- 锦浪逆变器数据采集链路集中修复：涉及消息拉取客户端、服务层实现、事件监听器、线程池配置、MyBatis Mapper
- 修正查询计数逻辑（`LightInveter.xml`）
- 修复后数据拉取和存储链路已稳定

### 逆变器更换与绑定 (代码明确证明)
**来源**: `rrsjk-light-operation-service` → `LightStationInverterChangeServiceImpl.java`, `LightInverterModelServiceImpl.java`, `LightInverterModel.xml`, `OperationModelStation.java` (commits 2234151/da160d5/4253355/6eb928c, 2026-05-12)
- 修复新逆变器重复绑定问题
- 修复电站逆变器关系绑定逻辑
- 优化逆变器更换逻辑并添加健康等级枚举
- 修复逆变器数据查询的时间戳排序和当天数据过滤问题

### 国电投(GDT)逆变器管理 (前端确认)
**来源**: `nahui-pv.hds-h5` → `src/views/pvEnergy/gdt/invertList.vue`, `src/views/pvEnergy/gdt/invertListDetail.vue`, `src/router/pvEnergy.js`, `src/api/pvEnergy.js` (commit 73fb00af / faf3cfc8, 李培龙, 2026-05-14)
- HDS 平台新增国电投(GDT)逆变器列表和详情页
- 路由路径: `pvEnergy/gdt/invertList` (列表), `pvEnergy/gdt/invertListDetail` (详情)
- API 定义在 `src/api/pvEnergy.js` 中
- 其他资方逆变器列表路径: `pvEnergy/acq/invertList` (中核?), `pvEnergy/chd/invertList` (华电?), `pvEnergy/cmb/cmbInvertList` (招银), `pvEnergy/pv/invertList` (户用?), `pvEnergy/kva/inverter` (KVA?)
- **证据等级**: 配置明确证明（前端路由/API 层面确认）

### HDS 平台多资方逆变器矩阵 (前端确认, 2026-05-18)
**来源**: `nahui-pv.hds-h5` → `src/router/pvEnergy.js`, `src/api/pvEnergy.js` (2026-05-18 全量通读)
- HDS 光伏能源模块按资方拆分了多套独立的逆变器管理页面:
  - `/cmbEnergy/cmbInvertList` — 招银逆变器列表/详情
  - `/pvEnergy/pvInvertList` — 户用光伏逆变器列表/详情
  - `/acqEnergy/acqInvertList` — 收购能源逆变器列表/详情
  - `/kvaEnergy/inverter` — KVA 逆变器列表/详情
  - `/chdEnergy/chdInvertList` — 华电逆变器列表/详情
  - `/gxEnergy` — 协鑫逆变器列表/详情
  - `/cqGdtEnergy` — 重庆国电投逆变器列表/详情
- 每个资方的逆变器列表对应后端不同的查询链路（如 CQ_GDT 使用 `findCqGdtByPage()` 专用 SQL）
- **证据等级**: 配置明确证明

### 重庆国电投(CQ_GDT)逆变器查询与导出 (代码明确证明)
**来源**: `rrsjk-hds-web` → `InverterController.java` (commit 732c84e4, wangxiran, 2026-05-15); `rrsjk-light-data-service` → `LightInveterDataService.java`, `LightInveterDataDao.java`, `LightInveterDataServiceImpl.java`, `LightInveterData.xml` (commit 60a7882d, wangxiran, 2026-05-15); `rrsjk-light-data-service` (commits: e8d818ac, d1acd5ee, 2026-05-14); `rrsjk-hds-web` (commit: df302d2a, 2026-05-15)
- 新增 `LightStation.ModeEnum.CQ_GDT` 模式的逆变器专用查询链路
- Controller: `queryCqGdtInverterList()` 接口，调用 `findCqGdtByPage()` 而非通用的 `findByPage()`；同时提供导出功能
- **关键SQL差异**: `findCqGdtByPage` 使用 `INNER JOIN light_station ls ON ls.station_code = lid.station_code`，而通用查询 `newFindByCbs` 使用 `LEFT JOIN light_station_elec lse`
- **字段差异**: CQ_GDT 查询返回 `ls.first_three_power_at`（从 light_station 表），通用查询原从 `light_station_elec` 表获取
- DAO 新增方法: `findCqGdtByPage()`, `queryCqGdtCountByPage()`
- 新增 `<sql id="conditionCqGdt">` 条件片段，过滤条件 `ls.mode = #{stationMode}` 作为必选条件（非可选）
- 通用查询的 `conditionCbs` 未改动，两条查询链路并行存在
- **新增字段**: `firstThreePowerAt`（首次功率记录时间）— 从 `light_station.first_three_power_at` 获取，2026-05-14 由 wangxiran 添加到数据服务和HDS前端
- **HDS前端**: 2026-05-15 添加重庆国电投逆变器查询和导出功能 (commit df302d2a, branch: featrue-wxr-20260513-cqgdt)
- **证据等级**: 代码明确证明

### 锦浪逆变器图表保存日志优化 (代码明确证明, 2026-05-18)
**来源**: `rrsjk-light-data-service` → `LightInverterChartCommon.java`, `ThreadPoolExecutorConfig.java` (commit 218c66c0, yumiao, 2026-05-18)

- `LightInverterChartCommon.java` 新增日志记录（+26行），用于排查锦浪逆变器图表保存问题
- `ThreadPoolExecutorConfig.java` 线程池配置微调（-3行）
- 这是对 2026-05-12 锦浪逆变器数据采集链路集中修复的后续优化，增加可观测性
- **证据等级**: 代码明确证明

### 逆变器列表导出排序修复 (代码明确证明, 2026-05-23)
**来源**: `rrsjk-admin-web` → `LightInveterController.java` (commit a132fbeb, yumiao, 2026-05-23); `rrsjk-light-data-service` → `LightInveterDataService.java`, `LightInveterDataDao.java`, `LightInveterDataServiceImpl.java`, `LightInveterData.xml` (commit 03d26bf8, yumiao, 2026-05-23)
- **问题**: 逆变器列表导出原使用 `findByPage()` (排序 `data_time_at DESC`)，分页导出时数据顺序与页面不一致
- **修复方案**: 新增专用导出方法链:
  - Controller: `doExport()` 中 `lightInveterDataService.findByPage()` → `lightInveterDataService.exportPage()`
  - Service: 新增 `exportPage()` 方法，调用 `lightInveterDataDao.exportByCbs()`
  - DAO: 新增 `exportByCbs()` 方法，复用 `newFindByCbs` 同名 SQL 但排序改为 `ORDER BY id DESC`
  - Mapper XML: `exportByCbs` 与 `newFindByCbs` 查询字段完全相同（27列），仅排序子句不同
- **排序差异**: 页面列表 `newFindByCbs` 按 `data_time_at DESC`（最新数据优先），导出 `exportByCbs` 按 `id DESC`（最新插入记录优先）
- **影响范围**: 仅影响 `rrsjk-admin-web` 逆变器列表导出功能，不影响页面列表展示 (`doList.do`)
- **pom.xml**: rrsjk-admin-web 父版本 8.0.5 → 8.0.6
- **证据等级**: 代码明确证明

## 待确认
|- 各数据源的字段映射差异。
- 发电告警的触发条件和业务口径。
- `rrsjk-light-iot-service` IoT 服务的具体职责和数据流 (commit 7dcf95b, 2026-05-14 初始化项目基础结构和配置)
- CQ_GDT 模式的首次并网时间(`first_three_power_at`)从 `light_station` 而非 `light_station_elec` 获取的业务原因

### DWS数据源接入 — 逆变器数据查询 (代码明确证明, 2026-05-20)
**来源**: `rrsjk-light-data-service` → MybatisConfig.java, DwsInveterData.java, DwsInveterDataService.java, DwsInveterDataServiceImpl.java, DwsInveterData.xml, DwsDataConverter.java, LightInveterDataServiceImpl.java (commits a00044b/f451e9a/523d7a1/5925c64/f030e67, yumiao, 2026-05-20, branch: feature/202605/ods_electroc_data)
**关联需求**: Epic2 (逆变器列表DWS查询)
- **架构变更**: MybatisConfig 新增第4个 SqlSessionFactory — `sqlSessionDwsFactory`，使用 `spring.dws.datasource` 数据源，mapper 路径 `classpath*:/mybatis/mapper/dws/**/*.xml`
- **已有数据源**: local (spring.local.datasource), query (spring.query.datasource), ods (spring.ods.datasource), **dws (新增)**
- **实体**: `DwsInveterData` 映射 DWS 表，字段包括 inverterSn, spId, stationCode, stationName, brandId, brandName, inverterState(1在线/2离线/3报警), collectorSn, pac(实时功率KW), fullHour(满发小时数), power(装机容量KW), elecDay/Month/Year/Total(发电量), dataTimeAt, bindStatus, usageStatus, firstLinkAt, stationSubmitter, dataSource
- **服务接口**: `DwsInveterDataService.findByPage()` — 返回 `Page<LightInveterData>`，字段已映射为通用格式
- **代理模式**: `LightInveterDataServiceImpl.findByPageDws()` 代理调用 `DwsInveterDataService.findByPage()`，对外统一接口
- **前端**: `rrsjk-admin-web` 新增 `lightInveterListDws.ftl` 页面，调用 `doListDws.do` 接口 → `findByPageDws`
- **关键修复**: DWS表无id字段 → COUNT(id)改为COUNT(1)；字段拼写inverter(非inveter)；开启mapUnderscoreToCamelCase映射
- **DwsDataConverter**: DWS字段到LightInveterData的转换器，处理字段名差异和类型转换
- **证据等级**: 代码明确证明

### 三天连续发电状态刷新 — 性能优化 (代码明确证明, 2026-05-22)
**来源**: `rrsjk-light-data-service` → `LightInveterDataServiceImpl.java`, `LightInveterDao.java` (commits 030fa75d/73850ff6/7db3df5e, yumiao+majinhu, TAEI-3141)
- **优化前**: 逐条查询+逐条更新，每批20个逆变器，线程池并发执行，数据库查询次数 = 逆变器数量
- **优化后**: 
  - 新增 `findContinuousElecSns()` 批量查询方法，一次SQL获取所有满足连续发电条件的逆变器SN集合
  - 改为内存判断 `continuousSns.contains(data.getInveterSn())`
  - 批量大小从20提升到500，减少数据库往返
  - 增加锦浪拉取数据重试机制 (`73850ff6`)
- **性能影响**: 从 O(N) 次查询降为 O(1) 次查询 + O(N) 内存判断
- **elecStatus字段**: 新增 `fix:elecStatus字段不跟随发电流写入` (`42379cbc`)，防止状态字段被错误的流式写入覆盖
- **证据等级**: 代码明确证明

### 逆变器变更服务校验逻辑 (2026-02-10 代码明确证明)
**来源**: `rrsjk-light-operation-service` → `LightStationInverterChangeServiceImpl.java` (commit 9c83ff00, sunzn, TAEI-2868)
- 创建逆变器变更申请时的多维度校验:
  1. 旧逆变器必须存在绑定关系（`LightStationInverter` 表查询）
  2. 旧逆变器绑定关系必须唯一（防止一条SN绑定多个电站）
  3. 旧逆变器必须与报警电站存在绑定关系（stationCode 匹配校验）
  4. 新逆变器不能已存在绑定关系（防止误绑定到已有电站的逆变器）
- 不同状态处理: 已有变更记录时，区分验收通过(`TECHNICAL_ACCEPTANCE_OK`)和流程终止(`STOP`)状态
- **证据等级**: 代码明确证明

### 逆变器变更验证与品牌校验优化 (2026-02-11 代码明确证明)
**来源**: `rrsjk-light-operation-service` (commits 77fc1b04/0b11b674/9e230c7f, sunzn)
- 优化逆变器变更服务逻辑，添加品牌校验
- 重构验证逻辑提升代码可维护性
- **证据等级**: 代码明确证明

### 工单备件登记 — 不创建变更信息的场景 (2026-02-11 代码明确证明)
**来源**: `repairs` → `WoPartServiceImpl.java` (commit 6f1a2484, sunzn, TAEI-2868)
- 新增常量 `NO_CREATE_REGISTER = -1L` 标识不需要创建变更信息的场景
- 工单备件电站数据创建返回ID为-1时，跳过逆变器变更创建流程
- 保持原有SN一致性验证逻辑，只在需要时执行验收通过操作
- 场景: 工单备件登记时允许不触发电站逆变器变更流程
- **证据等级**: 代码明确证明

### 逆变器新字段 — 过压保护阈值和功率输出限制 (2026-02-13 代码明确证明)
**来源**: `rrsjk-light-data-service` → `LightInveter.java`, `LightInveterData.java`, `LightInveterRecord.java`, `AisweiInveterResponse.java`, `LightInverterCommon.java`, `HighPerformanceNengKongCloudFixThread.java`, MyBatis Mapper XML (commit 49a8e581, sunzn)
- 新增字段:
  - `overvoltageThresholdStage1`: 电网过压一级保护阈值(V) — 爱仕维
  - `outputLimit`: 有功功率输出限制 — 爱仕维
- 覆盖实体: `LightInveter`, `LightInveterData`, `LightInveterRecord`（3个表同步新增字段）
- 数据源: 爱仕维(AISWEI)接口和能控云数据拉取
- 映射: `acOverVol1` → `overvoltageThresholdStage1`, `activePowerSet` → `outputLimit`
- 数据处理: `LightInverterCommon` 中新增字段传递逻辑，确保 Record→Data 转换时不丢失
- **Mapper XML 映射补充 (2026-06-01)**: `rrsjk-light-data-impl/.../LightInveter.xml` 的 `<sql id="columns">` 新增 `overvoltage_threshold_stage1`, `output_limit` 两列 (commit c362e8e5b4, sunzn)。此前 Java 实体已有字段但 local Mapper 的 columns 片段缺少映射，本次补齐。
- **证据等级**: 代码明确证明

### 锦浪逆变器数据修复 (2026-02-10~11 代码明确证明)
**来源**: `rrsjk-light-data-service` → `GinlongPullMessageClient.java`, `GinlongService.java` (commits fdcbcdfb/e23ee8e3/a2bced29/f9beab7d/ee7f9a89, sunzn)
- 修复锦浪逆变器数据采集问题
- 解决锦浪API响应数据解析异常
- 解决锦浪接口调用超时问题
- 修复逆变器数据分页查询逻辑
- 添加 GinlongPullMessageClient 查询日志记录功能
- **证据等级**: 代码明确证明

## 来源
- Hermes MEMORY.md，2026-05-09 迁移。
- 代码来源待每日扫描补充：/data/pvcode/rrsjk-light-data-service。

### DWS逆变器列表数据源 (2026-05-20 代码明确证明)
**来源**: `rrsjk-light-service` (commits a00044b205/f451e67, yumiao), `rrsjk-light-data-service` (commits a00044b205/f451e67/5925c64/544d4f2/523d7a1, yumiao), `rrsjk-admin-web` (commits c9d923c359/8f64a70aa5, yumiao), 分支 `origin/feature/202605/ods_electroc_data`
- **DWS数据源接入**: 新增独立DWS多数据源配置，用于逆变器列表查询
- **新实体**: `DwsInveterData` (注意拼写: DwsInveterData 非 DwsInverterData)
- **DAO/Service**: DwsInveterDataService + 字段映射转换器 `DwsDataConverter`
- **新接口**: `LightInveterDataService.findByPageDws()` 代理调用 `DwsInveterDataService`
- **前端页面**: 复制 `lightInveterList.ftl` 为 `lightInveterListDws.ftl`，调用 `doListDws.do` 接口
- **DWS表字段**: `inverter_sn`, `inverter_state` (非 inveter 拼写，修正了 mapper/实体中的拼写错误)
- **问题修复**:
  - DWS SqlSessionFactory 开启 `mapUnderscoreToCamelCase` (下划线→驼峰映射)
  - DWS表无id字段: 移除实体和mapper中的id引用，`COUNT(id)` 改为 `COUNT(1)`
  - 修正 `DwsDataConverter` 引用已删除的 `getId()` 方法
- **证据等级**: 代码明确证明

### DWS逆变器列表导出排序修复 (代码明确证明, 2026-05-23)
**来源**: `rrsjk-light-data-service` (commits 7e16693/03d26bf, yumiao), `rrsjk-admin-web` (commits e9aecc7/a132fbe/edc3ec0/a6aaac5, yumiao)
- **问题**: 逆变器列表DWS数据源导出时排序不正确
- **修复**: 修复DWS查询的排序逻辑，确保导出结果与页面展示一致
- **关联需求**: TAEI-3145 商务验收页面跳转逆变器详情速度优化
- **证据等级**: 代码明确证明

### 组件串线图 (推断, 2026-05-20)
**来源**: `rrsjk-light-service` (commit d3c26bf829, mabin, `fix(config): 组件串线图不加验真`)
- 组件串线图展示功能，图片验真跳过处理
- 关联需求: TAEI-3128 逆变器列表新增展示「实际组件串线图」在逆变器详情页
- **证据等级**: 推断

### 逆变器维修流程 (repairs, 2026-05-22 代码明确证明)
**来源**: `repairs` → `SpInverterInfoService.java`, `InverterStatusEnum.java`, `SpInverterSnInfoService.java`
- **独立于发电数据绑定**的逆变器维修业务流程，在 `repairs` 服务中管理
- **状态机**: 初始(0) → 已提交(1) → 供应商通过(2)/驳回(3) → 运维商寄回(4) → 供应商签收(5) → 供应商发货(6) → 运维商签收(7) / 取消(8)
- **业务实体**: `sp_inverter_info`(维修申请主表), `sp_inverter_sn_info`(SN明细)
- **审批流程**: 运维商创建 → 供应商审批（维修措施+维修价格+预计完成时间）→ 运维商寄回（物流单号）→ 供应商签收 → 供应商发货 → 运维商签收
- **Service**: `SpInverterInfoService` — save/submitOrder/supplierApproval/operationAndMaintenanceVendorsPost/supplierSign/supplierDelivery/operationAndMaintenanceVendorsSign
- **证据等级**: 代码明确证明

### 锦浪逆变器数据重试机制 (代码明确证明, 2026-05-22)
**来源**: `rrsjk-light-data-service` → `GinlongService.java` (commits 9b6d7da~73850ff, yumiao, 2026-05-22)
- 锦浪逆变器数据采集增加重试机制，解决连续三天发电数据拉取不稳定问题
- 使用多线程处理连续三天发电数据拉取
- 增加状态日志排查 (`feat: 增加状态日志`, `feat: 增加连续3天有发电数据日志排查`)
- **证据等级**: 代码明确证明

### 逆变器解绑替换 — 采集器信息透传 (代码明确证明)
**来源**: `rrsjk-light-data-service` → `LightInveterDataService.java` (2026-05-25 全量通读)
- `unBindStationAndReplace()` 方法扩展：新增采集器信息透传参数
  - `collectorSn` — 采集器序列号（GF 模式使用）
  - `collectorImageUrl` — 采集器影像 URL（GF 模式使用）
  - `collectorCaptcha` — 采集器验证码（GF 模式下爱士惟品牌使用）
- 解绑次数统计: `getUnbindCountByInveterSn()`
- 解绑记录: `recordUnbindLog()`
- 新旧逆变器验证: `validateNewInverter()`, `validateOldAndNewInverter()`, `getNewInveterSnValidResult()`
- **证据等级**: 代码明确证明

### 发电数据预占位机制 (代码明确证明)
**来源**: `rrsjk-light-data-service` → `LightInveterService.java` (2026-05-25 全量通读)
- `occupyTodayInveterRecord()` — 查询昨天活跃的 SN，预写入 `e_today=0` 记录
- **目的**: 降低白天高并发时 create 操作的重复写入风险
- **证据等级**: 代码明确证明

### Kafka 双写机制 (代码明确证明)
**来源**: `rrsjk-light-data-service` → `KafkaProducerService.java`, `KafkaDoubleWriteProperties` (2026-05-25 全量通读)
|- 逆变器数据发送 Kafka 时支持按 SN 码配置双写到新队列
- `KafkaDoubleWriteProperties.isEnabled()` — 开关控制
- `shouldDoubleWrite(inveterSn)` — 过滤需要双写的 SN
- 使用同一个 `kafkaTemplate3` 实例，发送到不同 topic
- **证据等级**: 代码明确证明

### Kafka 省份 Topic 路由机制 (代码明确证明, TAEI-3198/TAEI-3146, 2026-06-08)
**来源**: `rrsjk-light-data-service` → `KafkaDoubleWriteProperties.java`, `application-prod.yml` (commits: dc429d6f/09422568/majinhu, 2026-06-08)
- 发电数据按逆变器SN对应的省份code区分不同Kafka topic发送
- `KafkaDoubleWriteProperties.enableProvinceTopic` — 开关（生产环境已设为 true）
- `provinceTopicSuffix` — 省份 Topic 后缀，默认 `-vpp-electric`，生产环境改为 `-vpp-electric-prod`
- `fallbackTopic` — 兜底 Topic（SN未配置省份编码时使用），生产环境为 `unknown-vpp-electric-prod`
- 注释掉 `unknownRecords` 处理逻辑，改为不发送并记录日志
- 新增 `DwsLightStationElecDayReportNewService` 服务
- 新增 `AdsReportInveterChartMonthMap.findByStationCode()` 方法
- **分支**: `origin/20260608-kafka`
- **⚠️ 风险**: 下游消费者需按省份订阅新topic，如只订阅旧topic将收不到数据
- **逻辑调整** (commit 7a2f3bda, 2026-06-09): 省份 Topic 双写从 `doubleWriteProperties.isEnabled()` 条件块内移出，改为独立判断 `enableProvinceTopic`，即使未开启双写也发送省份 Topic
- **证据等级**: 代码明确证明

### 逆变器列表异步数据获取与缓存 (代码明确证明, 2026-05-26)
**来源**: `rrsjk-admin-web` → `LightInveterController.java` (commit b644eafd/majinhu, 2026-05-26)
- 逆变器详情页实现异步数据获取和缓存机制 (267行变更)
- 涉及天气数据异步拉取，减少页面加载时间
- 按钮5秒防重复点击置灰处理 (commit 24c23807)
- 日期格式化修复: givenTime 从 `"2026-5-26"` 改为 `"2026-05-26"`，防止 `DateTimeParseException` (commit edbdc609)
- 涉及 Controller: `LightInveterController`, `LightStationElecController`, `LightZeroCarbonInverterController`
- 模板修改: `inveterDetail.ftl`, `lightInveterList.ftl`
- **证据等级**: 代码明确证明

### 逆变器接口超时修复与redWarning空值修复 (代码明确证明, 2026-05-27 增量扫描)
**来源**: `rrsjk-admin-web` → `LightInveterController.java`, `inveterDetail.ftl` (commits: d388a965/e536c9c2/73cece3b, majinhu/yumiao, 2026-05-27)
- 超时时间改为3秒 (修复请求超时问题)
- redWarning 空值异常修复 (防止空指针)
- inveterDetail.ftl 线上问题修复
- **证据等级**: 代码明确证明

### 三天连续发电状态刷新 — 定时任务优化 (代码明确证明, 2026-05-25)
**来源**: `rrsjk-light-data-service` → `LightInveterDataServiceImpl.java`, `LightInveterDao.java`, `LightInveter.xml` (commit dd37b6df, majinhu, 2026-05-25)
- `isContinueThreeDayElec()` 定时任务优化，134行变更
- 涉及 DAO 新增查询方法、Mapper XML 新增 SQL 片段、Service 层逻辑重构
- **证据等级**: 代码明确证明

### 问题电站规则计算 (代码明确证明)
**来源**: `rrsjk-light-data-service` → `LightOperationScheduledJobService.java`, `ReportProblemStationService.java` (2026-05-25 全量通读)
- `calcProblemStation()` — 每小时执行，合并计算 rule1/rule2/rule3
- 批量写入 `report_problem_station` 表（ON DUPLICATE KEY UPDATE）
- `calcStationYearSummary()` — 每天凌晨 1:30 执行，写入 `report_station_year_summary_YYYY` 分表
- **证据等级**: 代码明确证明

### HdsReportService 发电管理报表 (代码明确证明)
**来源**: `rrsjk-light-data-service` → `HdsReportService.java` (2026-05-25 全量通读)
- Dubbo 服务，支持三个维度分页查询:
  - `queryTotalPage()` — 累计维度（每行=一个电站某年数据），需传 year
  - `queryYearPage()` — 年维度（每行=一个电站某年某月数据），需传 year
  - `queryMonthPage()` — 月维度（每行=一个电站某年某月某日数据），需传 year+month
- `submitExportTask()` — 提交异步导出任务，返回 taskNo
- `getExportTask(taskNo)` — 查询导出任务状态（PENDING/RUNNING/DONE/FAIL）
- 导出任务关联 `ReportExportTask` 表，包含 OSS 下载地址
- **证据等级**: 代码明确证明

### 浦银/中核发电数据推送 (代码明确证明)
**来源**: `rrsjk-light-data-service` → `ElecPushService.java`, `LightElectricDataService.java` (2026-05-25 全量通读)
- `doPushZH()` — 推送中核发电数据（重载：支持/不支持电站+逆变器数据）
- `doPushPF()` — 推送浦银发电数据
- `doHistoryPushZH()`, `doHistoryPushZH2()`, `doHistoryPushZHByDay()` — 历史数据推送
- 浦银发电量查询: `powerQuery()` — 接收 `SpdbRequestBody` (含 accessToken)，返回 `SpdbResponseBody` (respCode=0000 成功)
- **线程池**: `pyExecutor` (12-100000 线程), `zhExecutor` (12-100000 线程)
- **证据等级**: 代码明确证明

### 多品牌逆变器数据拉取线程池 (代码明确证明)
**来源**: `rrsjk-light-data-service` → `ThreadPoolExecutorConfig.java` (2026-05-25 全量通读)

| 线程池 Bean | 核心-最大 | 队列 | 用途 |
|---|---|---|---|
| `siNengHandleElectricData` | 32-50000 | 3000 | 上能发电数据处理 |
| `aishiweiHandleElectricData` | 12-30000 | 1000 | 爱士惟发电数据处理 |
| `nengkongHandleElectricData` | 12-30000 | 1000 | 能控云发电数据处理 |
| `commonHandleElectricData` | 6-30000 | 1000 | 通用发电数据处理 |
| `inveterHistoryBatchThreadPoolExecutor` | 500-4000 | 2000 | 分批次处理逆变器历史数据 |
| `inveterDataBuildThreadPoolExecutor` | 2000-20000 | 2000 | 逆变器 Data 构建 |
| `stationDayReportExecutor` | 30-30 | 300000 | 电站日发电量统计 |

- **证据等级**: 代码明确证明

### ADS 逆变器报表迁移 (代码明确证明, 2026-05-28)
**来源**: `rrsjk-light-data-service` + `rrsjk-admin-web` (majinhu, branch: origin/feature/202605/ods_electroc_data)
- **架构变更**: 逆变器图表查询从 DWS 层迁移到 ADS 报表层
- **新增 ADS 数据源**: `MybatisConfig` 新增 ADS 数据源配置，`AbstractAdsDao` 基类
- **5张 ADS 报表表** (ads schema, 无 id 字段):
  - `ads.green_energy_report_light_inverter_pac_chart_day` → 替换 `report_inverter_pac_chart_day`
  - `ads.green_energy_report_light_inverter_chart_day` → 替换 `report_inveter_chart_day`
  - `ads.green_energy_report_light_inverter_chart_month` → 替换 `report_inveter_chart_month`
  - `ads.green_energy_report_light_inverter_chart_year` → 替换 `report_inveter_chart_year`
  - `ads.green_energy_report_light_inverter_chart_total` → 替换 `report_inveter_chart_total`
- **新增实体**: `AdsReportInveterChartDay/Month/Year/Total/PacChartDay` (字段名修正: `inveter_sn` → `inverter_sn`)
- **新增 DAO + Mapper**: 5个 ADS DAO + 5个 MyBatis XML
- **新增 Service**: `AdsReportInveterChart*Service` 接口 + `AdsReportInveterChart*ServiceImpl` 实现 + `dwsInveterDataServiceImpl`
- **原 Service 迁移**: `ReportInveterChart*ServiceImpl` 改为调用 ADS 层
- **字段统一**: `inveter_sn` → `inverter_sn`, `inveterSn` → `inverterSn` (全链路拼写修正)
- **admin-web**: `LightInveterController` 新增 ADS 数据查询接口，`inveterDetailDws.ftl` / `lightInveterListDws.ftl` 前端页面
- **admin-web 新增接口**:
  - `dayChartAds.do` — 查询日图表 ADS 数据 (并行 CompletableFuture 查询 pac + elec)
  - `dayChartAdsIpvUpv.do` — 查询电压电流日图表 ADS 数据
  - 缓存: `admin:ads:inveter_day_chart:{inveterSn}:{givenTime}` (5分钟过期)
- **证据等级**: 代码明确证明

### elecStatus 字段独立计算 (TAEI-3141, 代码明确证明, 2026-05-22)
**来源**: `rrsjk-light-data-service` → `LightInverterCommon.java`, `LightInveterDataServiceImpl.java` (yumiao)
|- **变更**: `elecStatus` 字段不再跟随发电数据流写入（`LightInverterCommon.java` 中注释掉相关代码）
|- **原因**: elecStatus 改为通过"连续三天发电检查"独立计算和更新
|- **连续三天发电检查** (`LightInveterDataServiceImpl`):
  - 在锦浪数据拉取流程中增加重试机制
  - 新增 `isContinue` 判断逻辑，检查逆变器连续三天发电状态
  - 通过 `LightInveterDataDao.update()` 单独更新 elecStatus 字段
  - 增加日志: `"逆变器三天数据，逆变器SN：{}，是否连续发电：{} ,elecStatus {}"`
|- **关联需求**: TAEI-3141 (优化电站连续三天发电刷新逻辑) + TAEI-3145 (商务验收页面跳转逆变器详情速度优化)
|- **证据等级**: 代码明确证明

### 电站发电报表迁移到ADS层 (代码明确证明, 2026-05-29)
**来源**: `rrsjk-light-data-service` (majinhu, branch: origin/feature/202605/ods_electroc_data)
- **架构变更**: 电站发电报表从ADS层(AdsLightStationElec)迁移到DWS层(DwsLightStationElec)
- **原ADS实体迁移**: `AdsLightStationElec` → `DwsLightStationElec` (R093重命名)
- **原ADS服务迁移**: `AdsLightStationElecService` → `DwsLightStationElecService`
- **新增DWS服务方法**:
  - `findByPage()` — 分页查询 DwsLightStationElec
  - `getByStationCode()` — 按电站编码查询
  - `getStationSum()` — state统计
  - `getStationSummary()` — status统计
  - `getElecSum()` — 发电汇总
- **新增ADS报表服务** (4个维度):
  - `AdsReportStationChartDayService` — 日图表 (`getDayChartAds`, `getMinFetchAtAds`)
  - `AdsReportStationChartMonthService` — 月图表 (`getMonthChartAds`)
  - `AdsReportStationChartYearService` — 年图表 (`getYearChartAds`)
  - `AdsReportStationChartTotalService` — 累计图表 (`getTotalChartAds`)
- **新增实体**: `AdsReportStationChartDay/Month/Year/Total` (ads schema)
- **新增DAO + Mapper**: 4个ADS报表DAO + MyBatis XML
- **Admin-web**: `LightInveterController` 新增 `DwsInveterDataService`, `AdsReportInveterChart*Service` 依赖注入
- **DWS查询切换**: `doListDws.do` 中 `lightInveterDataService.findByPageDws()` → `dwsInveterDataService.findByPage()`
- **green_energy_light_station_realtime_current** 映射原来的 `light_station_elec`
- **证据等级**: 代码明确证明

### ADS数据源创建与报表迁移 (TAEI-3146, 代码明确证明, 2026-05-28~29)
**来源**: `rrsjk-light-data-service` (majinhu/马金虎)
- **需求**: 发电数据取数逻辑切换大数据平台，于淼负责，参与人: 于淼、马金虎
- **多数据源架构**: 新增 ADS 独立数据源 (`spring.ads.datasource`)，与原有 DWS 数据源并行
  - `MybatisConfig` 新增 `getAdsDataSource()` 和 `sqlSessionAdsFactory()`
  - 新增 `AbstractAdsDao` 基类，指定使用 `sqlSessionAdsFactory`
  - Mapper 路径: `classpath*:/mybatis/mapper/ads/**/*.xml`
  - 实体包: `com.rrsjk.light.data.entity.ads.**`
- **ADS报表表映射** (6张表替换原DWS表):
  - `ads.green_energy_report_light_inverter_pac_chart_day` ← `report_inverter_pac_chart_day`
  - `ads.green_energy_report_light_inverter_chart_day` ← `report_inveter_chart_day`
  - `ads.green_energy_report_light_inverter_chart_month` ← `report_inverter_chart_month`
  - `ads.green_energy_report_light_inverter_chart_year` ← `report_inverter_chart_year`
  - `ads.green_energy_report_light_inverter_chart_total` ← `report_inverter_chart_total`
  - **注意**: ADS表没有 `id` 字段，其他字段与DWS一致
- **字段名修正**: `inveter_sn` → `inverter_sn`，`inveterSn` → `inverterSn` (拼写修正)
- **连续三天发电优化**: `isContinueThreeDayElec` 定时任务优化查询逻辑
- **容量取数源修改**: baoxin 多次修改容量取数源 (5/27~28, 3+ commits)
- **证据等级**: 代码明确证明

### ADS报表迁移后续优化 (TAEI-3146, 代码明确证明, 2026-06-01 追加)
**来源**: `rrsjk-light-data-service` (majinhu/马金虎, branch: origin/2026-06-01-datajiebang + origin/feature/202605/ods_electroc_data)
- **定时任务解绑**: 6 条提交解绑发电相关定时任务 (commits: e5a5d1e/2129c69/237a9cd/9ba3635/f3ed5d7/af417da)
- **发电列表取自 ADS**: `LightInveterDataServiceImpl` 中新增 `monthChartProNewAds` 方法
- **报表修改同步**: ADS 与 DWS 双数据源下的报表数据一致性维护
- **字段映射**: `green_energy_light_station_realtime_current` 映射原 `light_station_elec`
- **证据等级**: 代码明确证明

### 电站解绑后发电绑定自动清理定时任务 (代码明确证明, 2026-06-02)
**来源**: `rrsjk-light-data-service` → `LightInverterDataJobServiceJob.java`, `LightInveterDataDao.java`, `LightInveterData.xml`, `UnbindStationCandidate.java` (commits e5a5d1e~9ba3635, majinhu, 2026-06-01)

- **新定时任务**: `flushUnbindStationInverterByNowDate()` — 每3小时执行，处理当天解绑
- **新定时任务**: `flushUnbindStationInverterByAllDate()` — 每3小时执行，处理全部数据
- **业务逻辑**:
  1. 查询电站状态为 `DISABLE`(已解绑) 但发电绑定状态仍为 `YES` 的逆变器候选记录
  2. 查询电站已重新绑定(`ENABLE`)且发电绑定(`YES`)的记录，构建排除配对集合 (stationCode|inveterSn)
  3. 对候选记录逐一解绑发电绑定 + 记录解绑日志
  4. 跳过当天重新绑定的逆变器（防止误解绑）
- **核心SQL**:
  - `findUnbindStationCandidates`: `light_station_inverter.status = 'DISABLE' AND light_inveter_data.bind_status = 'YES'`
  - `findReStationBoundCandidates`: `light_station_inverter.status = 'ENABLE' AND light_inveter_data.bind_status = 'YES'`
- **新实体**: `UnbindStationCandidate` — id, stationCode, inveterSn
- **业务意义**: 解决电站解绑后发电数据仍绑定的数据不一致问题，自动清理，无需人工干预
- **证据等级**: 代码明确证明

### DWS数据源接入 — 逆变器列表双数据源 (TAEI-3025, 代码明确证明, 2026-05-18~24)
**来源**: `rrsjk-admin-web/LightInveterController.java`, `rrsjk-light-data-service/LightInveterDataServiceImpl.java` (yumiao, majinhu)
**需求**: TAEI-3025 BT报表项目 (Epic2分支)
- **新增DWS查询接口**: `doListDws.do` → `findByPageDws` (参数与旧版MySQL查询一致)
- **新增前端页面**: `lightInveterListDws.ftl` (994行，复制自旧版 `lightInveterList.ftl`)
- **多数据源配置**: DWS多数据源接入，`DwsInveterDataService` 代理调用
- **三天发电优化**: `isContinueThreeDayElec` 定时任务优化，增加连续三天发电数据日志排查 (`030fa75d`, `8736e2c5`)
- **业务语义**: 逆变器列表同时支持MySQL和DWS两种数据源，DWS用于大数据量场景
- **⚠️ 双路径风险**: MySQL和DWS并存，需确认数据一致性和切换策略
- **证据等级**: 代码明确证明

### ⚠️ DWS报表回退 (代码明确证明, 2026-06-10)
**来源**: `rrsjk-admin-web/LightInveterController.java`, `LightStationElecDwsController.java`, `spring-config/service.xml` (commit ac97c90c, majinhu, 2026-06-10)
- **变更**: DWS逆变器列表和DWS电站发电报表被**整体回退** — 相关 `@Autowired` 服务注入被注释掉
  - `DwsInveterDataService` → 注释
  - `AdsReportInveterChartDayService/MonthService/YearService/TotalService` → 注释
  - `AdsReportInveterPacChartDayService` → 注释
  - `doListDws.do` 方法 → 整体注释
  - `LightStationElecDwsController` 整个 Controller → 1476行被注释/回退
  - `service.xml` 中 24 行 DWS 相关 bean 定义变更
- **影响**: 逆变器列表 DWS 查询入口 (`listDws.html` + `doListDws.do`) 虽然页面文件仍存在，但后端 Controller 方法已不可用
- **原因推断**: DWS 数据源可能存在问题或业务决策回退到纯 MySQL 查询
- **证据等级**: 代码明确证明

### AISWEI 历史数据优先级处理与 PAC Chart 内联同步（yumiao, TAEI-3198, 2026-06-10）
**来源**: `rrsjk-light-data-service/LightInverterCommon.java` (yumiao, commits 6de6029f/7ae22b7c/3f9156a3/df82257e, 2026-06-10)
**证据等级**: 代码明确证明
- **AISWEI 优先级**: 新增 `prioritizeAisweiReportRecords()` 方法 — 在处理批次记录前优先排序 AISWEI 历史报表记录
- **PAC Chart 内联同步**: AISWEI 历史数据的 `countInveterPacChartSync()` 从异步 subTaskFutures 改为 `runHistoryBatchSubTaskInline()` 内联同步执行
  - 原逻辑：PAC chart 通过 `submitHistoryBatchSubTask()` 异步提交到 `historyBatchExecutor`
  - 新逻辑：AISWEI 历史数据直接 inline 同步处理，非 AISWEI 数据仍走异步
- **常量**: 新增 `AISWEI_HISTORY_JOB_LOG_KEY = "AISWEI_HISTORY_JOB"`
- **业务意义**: 优化 AISWEI 逆变器数据入库顺序和 PAC 图表处理时序，确保历史报表数据优先处理且 PAC 图表同步完成
- **扫描日期**: 2026-06-11
