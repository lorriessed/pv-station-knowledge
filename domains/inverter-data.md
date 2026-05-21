# 逆变器与发电数据

更新时间: 2026-05-16

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
**来源**: `rrsjk-hds-web` → `InverterController.java` (commit 732c84e4, wangxiran, 2026-05-15); `rrsjk-light-data-service` → `LightInveterDataService.java`, `LightInveterDataDao.java`, `LightInveterDataServiceImpl.java`, `LightInveterData.xml` (commit 60a7882d, wangxiran, 2026-05-15)
- 新增 `LightStation.ModeEnum.CQ_GDT` 模式的逆变器专用查询链路
- Controller: `queryCqGdtInverterList()` 接口，调用 `findCqGdtByPage()` 而非通用的 `findByPage()`；同时提供导出功能
- **关键SQL差异**: `findCqGdtByPage` 使用 `INNER JOIN light_station ls ON ls.station_code = lid.station_code`，而通用查询 `newFindByCbs` 使用 `LEFT JOIN light_station_elec lse`
- **字段差异**: CQ_GDT 查询返回 `ls.first_three_power_at`（从 light_station 表），通用查询原从 `light_station_elec` 表获取
- DAO 新增方法: `findCqGdtByPage()`, `queryCqGdtCountByPage()`
- 新增 `<sql id="conditionCqGdt">` 条件片段，过滤条件 `ls.mode = #{stationMode}` 作为必选条件（非可选）
- 通用查询的 `conditionCbs` 未改动，两条查询链路并行存在
- **证据等级**: 代码明确证明

### 锦浪逆变器图表保存日志优化 (代码明确证明, 2026-05-18)
**来源**: `rrsjk-light-data-service` → `LightInverterChartCommon.java`, `ThreadPoolExecutorConfig.java` (commit 218c66c0, yumiao, 2026-05-18)

- `LightInverterChartCommon.java` 新增日志记录（+26行），用于排查锦浪逆变器图表保存问题
- `ThreadPoolExecutorConfig.java` 线程池配置微调（-3行）
- 这是对 2026-05-12 锦浪逆变器数据采集链路集中修复的后续优化，增加可观测性
- **证据等级**: 代码明确证明

## 待确认
- 各数据源的字段映射差异。
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

### 组件串线图 (推断, 2026-05-20)
**来源**: `rrsjk-light-service` (commit d3c26bf829, mabin, `fix(config): 组件串线图不加验真`)
- 组件串线图展示功能，图片验真跳过处理
- 关联需求: TAEI-3128 逆变器列表新增展示「实际组件串线图」在逆变器详情页
- **证据等级**: 推断
