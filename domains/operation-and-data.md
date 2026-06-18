# PVS 光伏电站系统 - rrsjk-light-operation-service & rrsjk-light-data-service 详细分析

---

## 一、rrsjk-light-operation-service（光伏运维服务）

### 1. 服务职责
**光伏电站运维管理平台核心服务**，负责：
- 工单全生命周期管理（创建→下发→指派→处理→完工→审核→关闭）
- 故障诊断与故障码管理
- 运维商/运维人员管理
- 巡检计划与巡检工单
- 电站电费账单管理
- 招投标/招商管理
- 运维培训中心（题库/考试/练习）
- 报表与Dashboard
- 保险管理（一切险、公众责任险）
- 资产运维管理
- 社会化电站管理

### 2. 核心 Dubbo 服务暴露（无 HTTP Controller）
本服务是纯 Dubbo 服务提供者，无 REST Controller。所有接口通过 Dubbo RPC 暴露。

**v1 服务（44 个 Dubbo Service）：**
| 服务接口 | 职责 |
|---------|------|
| LightWorkOrderService | 工单管理（老版本） |
| LightFaultCodeService | 故障码管理 |
| LightFaultLevelService | 故障等级管理 |
| LightFaultDictionaryService | 故障字典 |
| LightFaultFreeConfigService | 免故障配置 |
| LightFaultCodeRuleService | 故障码规则 |
| LightOpStaffService | 运维人员管理 |
| LightOpContractService | 运维合同管理 |
| LightRepairOrderService | 维修工单 |
| LightSettleBillsService | 结算账单 |
| LightCsOrderService | 客服工单 |
| LightNefficientService | 低效电站 |
| LightTrippingOperationService | 跳闸运维 |
| LightStationInverterChangeService | 电站逆变器变更 |
| LightWorkOrderProcessService | 工单流程 |
| LightOperationAdminService | 运维管理员 |
| OperationMaintenanceConfigService | 运维配置 |
| OperationFaultDetailReportService | 故障明细报表 |
| LightElectricUnusualService | 电量异常 |
| LightOperationCertificationService | 运维认证 |
| OperationAlarmRateService | 报警率 |
| AllRisksInsuranceService | 一切险 |
| PublicLiabilityInsuranceService | 公众责任险 |
| LightOperationCapitalService | 资本方运维 |
| LightOperationProviderService | 运维商管理 |
| LightOperationProviderExpandService | 运维商扩展 |
| LightZeroCarbonOperationProviderService | 零碳运维商 |
| LightOperationLossManagementService | 运维买损 |
| SocializationStationService | 社会化电站 |
| SocializationContractInfoService | 社会化合同 |
| SpecialFlagObjectService | 特殊标识对象 |
| LightOperationScheduledJobService | 定时任务 |
| LightOperationZeroScheduledJobService | 零碳定时任务 |
| ErrorLogService | 错误日志 |
| HdsMemberRoleService | 会员角色 |

**Bidding 招商管理（7 个）：**
| 服务接口 | 职责 |
|---------|------|
| LightOperationRegionBlockService | 区域地块管理 |
| LightOperationBiddingProjectService | 招标项目管理 |
| LightOperationRatingTableService | 评分表管理 |
| LightOperationBiddingRegistrationService | 投标报名 |
| LightOperationBiddingCompanyService | 投标公司 |
| LightOperationBiddingRatingService | 招标评分 |
| LightOperationRatingItemService | 评分项 |

**v2 服务（28 个 Dubbo Service）：**
| 服务接口 | 职责 |
|---------|------|
| LightOperationWorkOrderService | 工单管理（新版，含状态机） |
| LightOperationDashboardService | 运维Dashboard |
| LightOperationFaultService | 故障管理（新版） |
| LightOperationFaultSolutionService | 故障解决方案 |
| LightOperationSolutionService | 解决方案 |
| LightOperationSolutionCategoryService | 解决方案分类 |
| LightOperationStationService | 电站管理（运维视角） |
| LightOperationExternalStationService | 外部电站 |
| LightOperationStationElecBillService | 电站电费账单 |
| LightOperationStationGuaranteeTargetService | 电站保障目标 |
| LightOperationStationTagService | 电站标签 |
| LightOperationWorkOrderConfigService | 工单配置 |
| LightOperationWorkOrderStatisticsService | 工单统计 |
| LightOperationWorkOrderProcessRecordService | 工单处理记录 |
| LightOperationInspectionConfigService | 巡检配置 |
| LightOperationInspectionPlanService | 巡检计划 |
| LightOperationInspectionWorkOrderService | 巡检工单 |
| LightOperationReportConfigService | 报表配置 |
| LightOperationCustomReportService | 自定义报表 |
| LightOperationElecPriceService | 电价管理 |
| LightOperationDictService | 字典管理 |
| LightOperationDictItemService | 字典项 |
| LightOperationMessageService | 消息推送 |
| LightOperationWoPartService | 工单备件 |
| LightOperationTaskService | 定时任务 |
| LightOperationExportTaskService | 导出任务 |
| LightOperationExternalDiagnosisTaskService | 外部诊断任务 |

**培训中心（7 个）：**
| 服务接口 | 职责 |
|---------|------|
| LightOperationQuestionCategoryService | 题目分类 |
| LightOperationQuestionBankService | 题库 |
| LightOperationQuestionService | 题目 |
| LightOperationExamService | 考试 |
| LightOperationExamPaperService | 试卷 |
| LightOperationExamAnswerService | 答卷 |
| LightOperationPracticeService | 练习 |
| LightOperationChatHistoryService | AI对话历史 |

### 3. 核心 Service 层

**工单状态机（v2）：**
```
CREATE（创建）
  → TO_HEAD_DISPATCH（待总部下发）
  → TO_SUB_CENTER_DISPATCH（待分中心下发）
  → TO_ASSIGN（待指派）
  → TO_PROCESS（处理中）
  → HANDLED（已完工）
  → TO_SUB_CENTER_AUDIT（待分中心审核）
  → TO_HEAD_AUDIT（待总部审核）
  → FINISHED（已关闭/完成）

任何状态 → CLOSED（已取消）
```

**工单暂停状态：**
- NORMAL：正常进行中
- APPLY_PART：申请备件
- WAIT_PART：备件中
- WAIT_BORROW：借件中
- PART_ARRIVED：备件到货
- BORROW_ARRIVED：借件到货

**故障工单自动创建流程：**
1. 逆变器故障码通过 Kafka 推送
2. LightInverterRecordKafkaConsumer 接收
3. 匹配故障码规则 → 创建故障工单
4. 根据故障权限配置自动下发或待审核

**核心业务规则：**
- 工单超时自动计算（deadline = createdAt + timeoutDays）
- 暂停时截止时间自动顺延
- 申诉流程：运维商提交 → 分中心审核 → 总部二审
- 频繁故障检测：完工后仍有故障码则驳回重处理

### 4. 数据模型/DTO

**v1 核心实体：**
- `LightWorkOrder` - 工单
- `LightFaultCode` - 故障码
- `LightFaultDictionary` - 故障字典
- `LightFaultLevel` - 故障等级
- `LightOpStaff` - 运维人员
- `LightOperationProvider` - 运维商
- `LightRepairOrder` - 维修工单
- `LightCsOrder` - 客服工单
- `AllRisksInsurance` - 一切险
- `PublicLiabilityInsurance` - 公众责任险
- `LightOperationCapitalLog` - 资本日志

**v2 核心实体：**
- `LightOperationWorkOrder` - 工单（新版，含状态机）
- `LightOperationFault` - 故障（树形结构）
- `LightOperationFaultSolution` - 故障解决方案
- `LightOperationWorkOrderConfig` - 工单配置
- `LightOperationInspectionPlan` - 巡检计划
- `LightOperationInspectionWorkOrder` - 巡检工单
- `LightOperationStation` - 电站（运维视角）
- `LightOperationStationElecBill` - 电费账单
- `LightOperationStationGuaranteeTarget` - 保障目标
- `LightOperationQuestion/Exam/ExamPaper` - 培训相关
- `LightOperationMessagePush` - 消息推送
- `LightOperationExportTask` - 导出任务

**Bidding 实体：**
- `LightOperationBiddingProject` - 招标项目
- `LightOperationRegionBlock` - 区域地块
- `LightOperationRatingTable` - 评分表
- `LightOperationBiddingRegistration` - 投标报名

### 5. Dubbo 服务引用

**引用的外部服务：**
| 服务 | 来源 | 用途 |
|------|------|------|
| MessageService | rrsjk-system-api | 消息通知 |
| RegionService | rrsjk-system-api | 区域信息 |
| MemberService/MemberRoleService | rrsjk-member-api | 会员管理 |
| MerchantService | rrsjk-merchant-api | 商户管理 |
| LightStationService | rrsjk-light-api | 电站基础信息 |
| LightServiceProviderService | rrsjk-light-api | 服务商管理 |
| LightStationInverterService | rrsjk-light-api | 电站逆变器 |
| LightInveterDataService | rrsjk-light-data-api | 逆变器数据 |
| LightInveterRecordService | rrsjk-light-data-api | 逆变器记录 |
| ReportInveterChartDayService | rrsjk-light-data-api | 逆变器日发电报表 |
| LightStationElecDayReportService | rrsjk-light-data-api | 电站日发电报表 |
| SpTranSnService | repairs-api | 备件流转 |
| WoPartService | repairs-api | 工单备件 |
| SapRecordService | rrsjk-finance-api | SAP财务 |
| ZeroCarbonServiceProviderService | rrsjk-light-api | 零碳服务商 |

### 6. 数据库相关

**5 个数据源：**
| 数据源名称 | 用途 |
|-----------|------|
| spring.datasource.light-operation | 运维主库（主数据源 @Primary） |
| spring.datasource.light-data | 光伏数据库（只读查询） |
| spring.datasource.light | 光伏基础库 |
| spring.datasource.data-center | 数据中心库 |
| spring.datasource.light-report | 报表库 |

**技术栈：**
- MyBatis（多数据源配置）
- Druid 连接池
- Redis（缓存）
- ClickHouse（大数据分析，AiDiagnosisConfig）
- Kafka（逆变器故障记录消费）

### 7. 与其他服务的依赖关系
```
rrsjk-light-operation-service
├── Dubbo Consumer → rrsjk-system-api（消息、区域）
├── Dubbo Consumer → rrsjk-member-api（会员）
├── Dubbo Consumer → rrsjk-merchant-api（商户）
├── Dubbo Consumer → rrsjk-light-api（电站基础）
├── Dubbo Consumer → rrsjk-light-data-api（逆变器数据）
├── Dubbo Consumer → rrsjk-finance-api（财务SAP）
├── Dubbo Consumer → repairs-api（备件系统）
├── Kafka Consumer → 逆变器故障记录
├── Redis → 缓存
└── Dubbo Provider → 向 Web 层提供运维服务
```

### 8. 业务规则/状态机

**工单状态机：**
```
CREATE → TO_HEAD_DISPATCH / TO_SUB_CENTER_DISPATCH → TO_ASSIGN → TO_PROCESS
  → HANDLED → TO_SUB_CENTER_AUDIT → TO_HEAD_AUDIT → FINISHED
  → CLOSED (取消，可从任何状态)
```

**故障码处理规则：**
- 故障码按等级分类，不同等级对应不同处理流程
- 自动工单创建基于故障码规则匹配
- 故障恢复后自动关闭工单

**运维商业务类型：**
- 1 = 户用
- 2 = 工商业
- 3 = 户+工

---

## 二、rrsjk-light-data-service（光伏数据服务）

### 1. 服务职责
**光伏电站数据采集与处理核心服务**，负责：
- 多厂商逆变器数据采集（固德威、锦浪、阳光电源、能科云、科士达等）
- 逆变器实时数据处理与存储
- 电站日/月/年发电量统计
- 逆变器功率曲线（Pac Chart）
- 数据采集器管理
- 电站收益计算
- 成本配置
- 问题电站识别
- HDS 报表服务
- 电力推送服务

### 2. 核心 Dubbo 服务暴露

**数据采集与逆变器（15 个）：**
| 服务接口 | 职责 |
|---------|------|
| LightInveterService | 逆变器数据管理（含handlerData/m1-m4等多阶段处理） |
| LightInveterDataService | 逆变器运行数据 |
| LightInveterRecordService | 逆变器电流电压记录 |
| LightInveterAlarmService | 逆变器告警 |
| LightInveterJobService | 逆变器定时任务 |
| LightInveterSmallService | 小型逆变器 |
| LightCollectorService | 数据采集器管理 |
| LightInverterOriginalDataProviderService | 逆变器原始数据提供 |
| LightStationInveterService | 电站逆变器关联 |
| LightStationElecService | 电站电量 |
| LightStationElecDayReportService | 电站日发电报表 |
| LightStationElecDayReportNewService | 电站日发电报表（新版） |
| LightStationElecMonthReportNewService | 电站月发电报表（新版） |
| ReportInveterPacChartDayService | 逆变器日功率曲线 |

**报表与统计（10 个）：**
| 服务接口 | 职责 |
|---------|------|
| ReportInveterChartDayService | 逆变器日图表 |
| ReportInveterChartMonthService | 逆变器月图表 |
| ReportInveterChartYearService | 逆变器年图表 |
| ReportInveterChartTotalService | 逆变器总图表 |
| ReportStationChartDayService | 电站日图表 |
| ReportStationChartMonthService | 电站月图表 |
| ReportStationChartYearService | 电站年图表 |
| ReportStationChartTotalService | 电站总图表 |
| HdsReportService | HDS报表 |
| ReportProblemStationService | 问题电站报告 |

**业务服务（5 个）：**
| 服务接口 | 职责 |
|---------|------|
| LightStationService | 电站数据管理 |
| LightStationPlanConfigService | 电站计划配置 |
| LightProfitService | 收益计算 |
| LightCostConfigService | 成本配置 |
| LightStationJobService | 电站定时任务 |
| LightStationFirstElecDayCalService | 电站首次日发电计算 |

**第三方厂商接口（6 个）：**
| 服务接口 | 厂商 |
|---------|------|
| KsolarService | 科士达 |
| SunGrowService | 阳光电源 |
| SiNengService | 思能 |
| NengKongCloudService | 能科云 |
| GsyStationPowerInfoService | GSY电站功率 |
| AisweiApi | 艾斯威 |

**定时任务：**
| 服务接口 | 职责 |
|---------|------|
| LightOperationScheduledJobService | 运维定时任务（异步） |

### 3. 核心 Service 层

**逆变器数据处理流程（LightInveterService）：**
- `handlerData()` - 总入口
- `m1()` - 阶段1：数据拉取
- `m2()` - 阶段2：数据处理
- `m2_1()` - 阶段2.1：增量处理
- `m3()` - 阶段3：报表生成
- `m4()` - 阶段4：数据修正
- `correctData()` - 数据矫正
- `occupyTodayInveterRecord()` - 预占位今日记录（防并发重复写入）

**定时任务（LightOperationScheduledJobServiceImpl）：**
- `generateStationDailyElectricityData()` - 生成电站日电量数据（旧版）
- `generateStationDailyElectricityDataNew()` - 生成电站日电量数据（新版）
- `generateStationMonthlyElectricityDataNew()` - 生成月电量
- 多个厂商数据采集定时任务

### 4. 数据模型/DTO

**核心实体（local 库）：**
- `LightInveter` - 逆变器基础信息
- `LightInveterData` - 逆变器运行数据（功率、电流、电压、发电量等）
- `LightInveterDataRecord` - 逆变器记录
- `LightStationElec` - 电站电量
- `LightStationElecDayReport` - 电站日发电报表
- `LightStationElecMonthReport` - 电站月发电报表
- `ReportInveterChartDay` - 逆变器日图表
- `ReportStationChartDay` - 电站日图表
- `LightProfit` - 收益
- `LightCostConfig` - 成本配置
- `LightCollector` - 采集器

**查询实体（query 库 - 只读）：**
- `LightStation` - 电站
- `LightStationInverter` - 电站逆变器关联

### 5. Dubbo 服务引用

| 服务 | 来源 | 用途 |
|------|------|------|
| LightFaultCodeService | rrsjk-light-operation-api | 故障码匹配 |
| LightStationInverterChangeService | rrsjk-light-operation-api | 逆变器变更 |
| LightOperationWorkOrderService | rrsjk-light-operation-api | 故障工单创建 |
| LightStationService | rrsjk-light-api | 电站信息 |
| LightStationInverterService | rrsjk-light-api | 逆变器信息 |
| LightStationPlanConfigService | rrsjk-light-api | 计划配置 |
| ZeroCarbon 相关服务 | rrsjk-light-api | 零碳电站 |

### 6. 数据库相关

**3 个数据源：**
| 数据源名称 | 用途 |
|-----------|------|
| spring.local.datasource | 本地库（主库，写操作） |
| spring.query.datasource | 查询库（只读，跨库查询） |
| spring.ods.datasource | ODS库（操作数据存储） |

**MyBatis Mapper 路径：**
- `classpath*:/mybatis/mapper/local/**/*.xml` → local 库
- `classpath*:/mybatis/mapper/query/**/*.xml` → query 库
- `classpath*:/mybatis/mapper/ods/**/*.xml` → ods 库

**性能配置：**
- Dubbo 线程池：cached，5000 线程
- IO 线程：32
- 超时：90000ms（90秒，数据查询量大）
- 负载均衡：leastactive（最少活跃调用）

### 7. 与其他服务的依赖关系
```
rrsjk-light-data-service
├── 第三方厂商 API → 固德威、锦浪、阳光电源、科士达、能科云、艾斯威
├── Dubbo Consumer → rrsjk-light-api（电站/逆变器基础信息）
├── Dubbo Consumer → rrsjk-light-operation-api（故障码、工单）
├── Kafka → 逆变器数据消费/生产
├── EventBus → 内部事件驱动（LightInveterEvent 等）
├── Dubbo Provider → 向 operation-service/web 层提供数据服务
└── Redis → 缓存
```

**数据流向：**
```
逆变器设备 → 厂商云平台 → rrsjk-light-data-service(采集) 
  → LightInveterData(存储) 
  → 报表计算(日/月/年) 
  → rrsjk-light-operation-service(工单触发)
  → rrsjk-light-report-service(报表展示)
```

### 8. 业务规则/状态机

**逆变器数据处理：**
- 多阶段处理：拉取 → 解析 → 存储 → 报表 → 修正
- 预占位机制：每日凌晨预写入 e_today=0 记录，降低白天并发写入冲突
- 数据矫正：处理异常数据（负值、突增等）

**发电量计算：**
- 日发电量 = 今日累计发电 - 昨日累计
- 支持多厂商逆变器数据归一化
- 首次发电量计算（>5度视为正式发电）

**问题电站识别：**
- 连续零发电检测
- 逆变器离线检测
- 发电量异常波动检测

---

## 三、两服务协同关系

```
┌─────────────────────────────────────────────────────────────┐
│                    Web 层 (rrsjk-merchant-web)               │
└──────────────────────┬──────────────────────────────────────┘
                       │ Dubbo RPC
        ┌──────────────┴──────────────┐
        ▼                             ▼
┌───────────────────┐     ┌────────────────────────┐
│ rrsjk-light-      │     │ rrsjk-light-           │
│ operation-service │◄───►│ data-service           │
│ (运维管理)         │     │ (数据采集与处理)         │
└────────┬──────────┘     └────────┬───────────────┘
         │                         │
         │ Dubbo RPC               │ 厂商 API
         ▼                         ▼
┌───────────────────┐     ┌────────────────────────┐
│ rrsjk-light-api   │     │ 逆变器厂商云平台         │
│ (电站/逆变器基础)  │     │ (固德威/锦浪/阳光等)     │
└───────────────────┘     └────────────────────────┘
```

**协同流程 - 故障工单自动创建：**
1. data-service 从厂商云平台拉取逆变器数据
2. 检测到故障码 → 通过 Kafka 发送 `LightInverterRecordKafkaEvent`
3. operation-service 的 `LightInverterRecordKafkaConsumer` 接收
4. 匹配故障码规则 → 调用 `LightOperationWorkOrderService.createFaultWorkOrder()`
5. 工单进入状态机流转（待下发 → 待指派 → 处理中 → 完工 → 审核 → 关闭）

---

## 四、技术架构总结

| 维度 | rrsjk-light-operation-service | rrsjk-light-data-service |
|------|------|------|
| 技术栈 | Spring Boot 2.2.4 + Dubbo 2.7.4 + MyBatis | Spring Boot 2.2.4 + Dubbo 2.7.4 + MyBatis |
| 语言 | Java | Java |
| 文件数 | ~774 Java 文件 | ~371 Java 文件 |
| 通信 | Dubbo RPC (Zookeeper 注册中心) | Dubbo RPC (Zookeeper 注册中心) |
| 数据库 | 5 数据源 (Druid + MyBatis) | 3 数据源 (Druid + MyBatis) |
| 消息 | Kafka Consumer (故障记录) | Kafka Producer/Consumer + EventBus |
| 缓存 | Redis | Redis |
| 定时任务 | @EnableScheduling + 独立Job服务 | @EnableScheduling + 线程池 |
| 端口 | -1 (纯 Dubbo 服务) | -1 (纯 Dubbo 服务) |

---

## 运维会展大屏数据模型 (代码明确证明, 2026-05-20)
**来源**: `rrsjk-light-operation-service` → `OperationScreenModel.java` (commits: sunzn 1f378fb, 0f55e41, 63f206e, 2026-05-18~19)
**需求**: TAEI-3066 展会-运维大屏

- **OperationScreenModel 实体**: 运维会展大屏核心数据模型，包含以下指标：
  - `specialFlag` — 资方标识
  - `comprehensiveHealthLevel` / `comprehensiveHealthScore` — 综合健康等级/分值
  - `operationStationCount` — 运维电站数量
  - `priorityRatio` / `healthRatio` / `goodRatio` / `subHealthRatio` / `unhealthyRatio` — 各健康等级占比
  - `onlineCount` / `onlineRatio` / `offlineCount` / `offlineRatio` / `abnormalCount` / `abnormalRatio` — 在线/离线/异常统计
  - `totalPowerGeneration` — 总发电量（万度）
  - `cumulativeIncome` — 累计收益（万元）
  - `totalCapacityMwp` — 总容量（Mwp）
  - `realTimePowerMw` — 实时功率（MW）
- **ComprehensiveHealthScore 枚举**: 健康等级枚举，用于大屏展示
- **OperationModelStation 扩展**: 新增 `specialFlag` 字段（资产所属标识），支持按资方筛选
- **MyBatis映射**: `OperationScreenModel.xml` — 完整 CRUD + 分页查询

---

## 资方年月发电量统计表 (代码明确证明, 2026-05-20)
**来源**: `rrsjk-light-operation-service` → `OperationElecMonthModel.java` (commit: sunzn 0f55e41, 2026-05-19)
**需求**: TAEI-3066 展会-运维大屏

- **OperationElecMonthModel**: 资方年月发电量统计实体
- **表结构**: 记录各资方按年月的发电量统计数据
- **Service**: `OperationElecMonthModelService` — 分页查询、新增、修改、删除完整 CRUD
- **DAO**: `OperationElecMonthModelDao` + MyBatis `OperationElecMonthModel.xml` (114行映射)
- **用途**: 为运维会展大屏提供资方维度的年月发电量统计数据

### 运维展会大屏 — 固定电站模块与业务合作意向 (代码明确证明, 2026-05-06~07)
**来源**: `rrsjk-light-operation-service` → `OperationModelStation.java`, `OperationModelStationService/Impl`, `OperationModelStationDao`, `OperationModelStation.xml` (commits 60c99ad5/e59376d5, sunzn, 2026-05-06~07)
**关联需求**: TAEI-3066 展会-运维大屏
- **OperationModelStation 实体**: 运维展会大屏固定电站实体 (76行)
  - 字段: id, stationCode, stationName, province/city/region/address, healthLevel, reportCode, generateTime 等
- **OperationModelStationService**: 固定电站服务接口
  - 按区域查询固定电站列表
  - 查询电站装机功率和累计发电量
- **OperationModelStationDao** + **MyBatis映射** (234行): 完整 CRUD + 装机功率/累计发电量查询
- **业务合作意向功能**: `e59376d5` (sunzn, 2026-05-06) — 运维会展商务合作功能
- **逆变器变更过程信息查询**: `d4a8b61b` (sunzn, 2026-05-07, branch: szn_shensu_duixian_20260422)
- **HDS Web**: 新增逆变器变更过程信息查询、电站项目查询功能
- **证据等级**: 代码明确证明

### 运维会展大屏 HDS Controller 与新增模型 (代码明确证明, 2026-05-25)
**来源**: `rrsjk-hds-web` → `BusinessCooperationIntentionController.java` + `rrsjk-light-operation-service` 新增模型 (commits: sunzn 051de90/213b7e5/a7a192dd/df66f67/0f55e41, 2026-05-21~25)
**关联需求**: TAEI-3066 展会-运维大屏

- **HDS Web 新增 `BusinessCooperationIntentionController`**: `/light/operation/businessCooperationIntention`
  - `POST /insert` — 联系我们(商务合作意向提交)
  - `GET /findStation` — 查询电站项目(支持 specialFlag 资方筛选)
  - `GET /getDetail` — 查询电站详情
  - `GET /findWeather` — 根据电站位置查询未来晴天日期
  - `GET /findInverterData` — 查询逆变器数据柱状图(含特殊SN演示数据逻辑 + 非当日数据取去年同期)
  - `GET /findScreenData` — 查询大屏数据(支持 specialFlag)
  - `GET /findMonthElecData` — 查询月电量柱状图数据(支持 specialFlag)
  - `GET /findMapData` — 查询地图省市电站数量信息(支持 specialFlag)
- **Dubbo 服务引用新增**(service.xml):
  - `businessCooperationIntentionService` — 商务合作意向
  - `operationModelStationService` — 运维展会固定电站
  - `lightInverterModelService` — 逆变器数据模型
  - `operationScreenModelService` — 运维会展大屏数据
  - `operationElecMonthModelService` — 资方年月发电量统计
  - `reportScreenMapModelService` — 报表地图模型(新增)
- **rrsjk-light-operation-service 新增 `ReportScreenMapModel`**: 地图省市电站数量信息模型
  - Entity + Service + Dao + MyBatis Mapper (ReportScreenMapModel.xml)
  - **用途**: 为运维会展大屏提供地图维度的省市电站分布数据
- **逆变器数据查询时间逻辑修复** (2026-05-25): `LightInverterModelServiceImpl` 修正数据过滤逻辑
- **OperationModelStation 字段扩展**: 新增 `specialFlag`(资产所属标识)、性能指标字段等

### 电站标签服务 (代码明确证明, 2026-05-06)
**来源**: `rrsjk-light-operation-service` + `rrsjk-hds-web` (commits 5b6805ba/0a26821f/74a70ebb/2eca92f2/5b6eaf7d, dengqiu/马斌, 2026-05-06)
- 新增电站标签功能: `OperationLabelService`, `OperationLabelDefinitionService`
- 标签服务配置和标签定义服务配置
- 修复标签对象字段为空问题
- **证据等级**: 代码明确证明

### 电站年度保发功能 (代码明确证明, 2026-05-06~07)
**来源**: `rrsjk-light-operation-service` + `rrsjk-hds-web` (commits fcfc067b/613bd02c/aff6b111/5811c51a, dengqiu/马斌, 2026-05-06~07)
- 电站年度保发功能接口和统计接口
- 修复多月一条对账单电量错误更新问题
- **证据等级**: 代码明确证明

### 储能电站管理 (代码明确证明, 2026-04-29)
**来源**: `rrsjk-light-operation-service` + `rrsjk-hds-web` (commits d82a9acb/c355499a, dengqiu, 2026-04-29)
- 添加储能电站管理功能接口
- **证据等级**: 代码明确证明

---

### CBS 日志框架 (rrsjk-light-common, 代码明确证明, 2026-05-25)
**来源**: `rrsjk-light-common` → `rrsjk-light-base` 模块 (2026-05-25 全量通读)

`rrsjk-light-common` 是所有 `rrsjk-light-*` 服务的基础依赖库，提供：

#### 日志拦截框架
- **ControllerLogFilter**: Servlet Filter，自动拦截所有 HTTP 请求（排除 .css/.js/.png 等静态资源），记录请求 URI 和 IP，注入 TraceId 到 Response Header
- **DbLogFilter**: Druid Filter (注册在 `META-INF/druid-filter.properties` 为 `druid.filters.dbLogFilter`)，拦截所有 SQL 执行，记录 SQL 语句和参数
- **日志输出**: 按级别分文件输出（debug.log, info.log, warn.log, error.log, app.log），业务错误独立输出（business_error.log），系统日志独立输出（link.log, sql.log, sql-body.log, mq.log, rpc.log, task.log）
- **日志保留**: app.log 保留 120 天，其他保留 2 天，单文件最大 100MB

#### Trace 上下文
- **TraceContext**: 线程本地存储，管理 `thraceId` (Long) 和 `rpcId` (List<Integer>)
- **RPC Header**: `RPC_HEADER_TRACE_ID` 和 `RPC_HEADER_RPC_ID`，通过 HTTP Header 传递链路追踪 ID
- **防共享**: `TraceContext.clean()` 在每个请求开始时清空，防止线程池复用导致 traceId 污染

#### Manifold 编译期扩展
- 使用 Manifold 2025.1.9 实现 Java 编译期元编程（运算符重载、属性扩展等）
- 编译参数: `-Xplugin:Manifold no-bootstrap`
- 三个模块: `rrsjk-light-base` (基础), `rrsjk-light-manifold` (Manifold 扩展), `rrsjk-light-rocketmq` (RocketMQ 封装)

#### RocketMQ 封装
- `rrsjk-light-rocketmq` 独立模块，基于 RocketMQ 4.8.0 + Spring Boot Starter 2.1.1
- 与 `rrsjk-light-message-service` 的 RocketMQ 5.0.7 (Usher) 是两套不同实现

---

### rrsjk-light-iot-service IoT 服务 (代码明确证明, 2026-05-25)
**来源**: `rrsjk-light-iot-service` (2026-05-25 全量通读)

**状态**: 初始化阶段（2025-12-01 创建，仅基础结构）

- 仅包含基础配置（Dubbo、MyBatis、Kafka、Redis、OSS、线程池）
- 一个示例 EventBus Listener (`LightDemoListener`)
- Kafka 消费者配置：消费 `LightInverterRecordKafkaEvent`，重试 3 次，间隔 1s
- Dubbo 引用大量服务：rrsjk-light-api, rrsjk-light-data-api, repairs-api, zero-carbon 等
- **当前无实际业务逻辑**，是 `rrsjk-light-operation-service` 的拆分/迁移目标
- **AI 诊断配置**: 内网地址 `http://10.2.160.220:5000/api/diagnosis/start`（prod）/ `http://121.40.121.163:5000`（dev）
- **天气 API**: `http://api.xiaoxianglink.com/v1/weather/weather`
- **工单异步处理**: `workOrderTaskExecutor` (5-20 线程，队列 500)
- **证据等级**: 代码明确证明

### 电站收益计算电网容量维度扩展 (代码明确证明, 2026-05-27 增量扫描)
**来源**: `rrsjk-light-data-service` → `LightProfitServiceImpl.java`, `LightStationDao.java`, `LightStation.xml` (commits: baoxin 9927a3cd/6ee377a1, 2026-05-27)
- **新增电网容量维度**: `findSocialGridQuota`(社会化电网容量) 和 `findWholeGridQuota`(整村电网容量)
- **收入计算变更**: 多场景收入从 `multiGridQuota + industryGridQuota` 扩展为 `multiGridQuota + industryGridQuota + socialGridQuota + wholeGridQuota`
- **单价**: 户用 3.45 元/度(去税÷1.13)，多场景(含社会化/整村) 3.8 元/度(去税÷1.13)
- **废弃API替换**: `BigDecimal.ROUND_DOWN` → `RoundingMode.DOWN`
- **证据等级**: 代码明确证明

### 巡检计划按资方和运维商筛选 (代码明确证明, 2026-06-02)
**来源**: 
- `rrsjk-hds-web` → `LightOperationInspectionPlanController.java` (commit 43de7a3, dengqiu, 2026-06-02)
- `rrsjk-light-operation-service` → `LightOperationStationDao.java`, `LightOperationInspectionPlanServiceImpl.java`, `StationQuery.java`, `StationOperatorOptionDto.java` (commit 05587d8, dengqiu, 2026-06-02)
- `nahui-pv.hds-h5` → `src/views/maintainance/inspect/plan/components/operatePlan.vue`, `src/api/maintainance.js` (commit 729e7ad, 聂晓博, 2026-06-02)

- **新增接口**: `GET /light/operation/inspection/plan/operator/search` — 查询全部运维商列表（电站表去重、按名称升序）
- **新增 DTO**: `StationOperatorOptionDto` — 运维商选项
- **StationQuery 扩展**: 新增资方和运维商筛选字段
- **前端**: 年度巡检计划新增资方和运维商多选功能
- **电站中心/运维工单**: 字段调整
- **证据等级**: 代码明确证明

### 巡检工单运维商一致性刷新 + 招银电站故障/工单查询 (代码明确证明, 2026-06-18 扫描)
**来源**: `rrsjk-light-operation-service` (commit range: 4b69cc6..d5ad67a, 7 commits)

**新增定时任务**: `refreshUnfinishedInspectionWorkOrdersOperator()`
- 每天凌晨执行，刷新运维商与电站不一致的未完成巡检工单
- 新增 `findUnfinishedWithOperatorMismatch` DAO 方法（分页查询，minId 游标）
- **业务场景**: 电站更换运维商后，历史未完成的巡检工单运维商字段未同步更新

**不运维电站过滤**:
- 新增 `isNoOpStation(stationCode)` 方法 — 判断电站是否属于不运维电站
- 系统创建工单时跳过不运维电站
- Dubbo 调用异常时返回 false（按不过滤处理，保证容错）

**招银接口（6.5/6.6）**:
- `findStationFaultInfo(WorkOrderQuery)` — 电站故障信息查询（招银对接）
- `findStationWorkOrderInfo(WorkOrderQuery)` — 电站工单信息查询（招银对接）
- WorkOrderQuery 新增 `stationCodeList` (Set<String>) 字段 — 支持批量电站查询

**工单查询修复**:
- 修正同步巡检工单资方字段的问题
- 工单查询中订单编号拼接逻辑修复

**线程栈内存调优**:
- report-service: `-Xss` 从 20m 调整为 10m（金租大屏栈溢出修复后）
- operation-service: `-Xss` 从 5m 调整为 2m（观察两天无异常后）
