# 工商业(CM)业务域

更新时间: 2026-05-26

## 概述

工商业(CM = Commercial)是独立于户用光伏的另一条业务线，涉及项目立项、方案设计、施工进度管理、收入政策配置、投决审核等全流程管理。

## 核心Controller与入口

### CmConstructionProgressAuditController — 施工进度审核 (代码明确证明, 2026-05-26)
**来源**: `rrsjk-admin-web` → `CmConstructionProgressAuditController.java` (commit 012b6f14, tn_wangb, 2026-05-26)
- **路径前缀**: `/cmConstructionProgress`
- **权限**: `cmConstructionProgress:list`, `cmConstructionProgress:audit`, `cmConstructionProgress:export`
- **接口列表**:
  - `list.html` — 施工进度完工列表页面
  - `doList.do` — 分页查询，支持: projectCode, projectName, finishAuditStatus, createdStart/End, auditStart/End
  - `detail.html` — 审核详情页面，展示附件模板、历史附件(按进度百分比分组)
  - `audit.html` — 审核操作页面
  - `audit.do` — 提交审核，`BaseAuditRequset` 入参
  - `projectTrack.html` — 项目跟踪页面，展示项目详情+节点记录+方案计划
  - `doExport.do` — 导出Excel，使用 EasyExcel 分页导出(每页5000条)
- **导出实体**: `CmConstructionProgressExcel` — 包含状态、项目编码、名称、地址、工程类型、进度阶段、节点名称、总进度、新增进度、完工时间/人、审核时间/人、备注
- **附件展示**: 按 `CmNodeAttachmentTemplate` 模板分组展示，支持多文件模式(`ModeEnum.MULTI`)
- **历史附件**: 按 `processStage`(进度百分比) 分组，如 "项目进度50%"

### CmLightProjectIncomePolicyController — 收入政策配置 (代码明确证明, 2026-05-26)
**来源**: `rrsjk-admin-web` → `CmLightProjectIncomePolicyController.java` (解钦, 多个commit, 2026-05-18~26)
- **路径前缀**: `/cmLightProjectIncomePolicy/`
- **权限**: `cmLightProjectIncomePolicy:list`, `cmLightProjectIncomePolicy:update`
- **接口列表**:
  - `list.html` / `doList.do` — 列表查询，支持 policyCode, **policyType**, **status** 筛选
  - `detail.html` — 政策详情，展示政策明细项(CmLightProjectIncomePolicyItem)
  - `update.html` — 政策修改页面
- **导入功能** (2026-05-26 新增):
  - 导入增加表头校验
  - 下载模板增加对业务类型的判断
  - 导入增加对项目的校验
- **新增依赖**: `CmLightProjectService`, `CmNodeService`, `CmIncomePolicyTemplateExcel`
- **并行审核方案** (2026-05-21): 新增 `cmLightProjectIncomePolicyAudit.ftl`

### CmLightProjectSignInfoController — 项目签约信息 (代码明确证明, 2026-05-26)
**来源**: `rrsjk-admin-web` → `CmLightProjectSignInfoController.java` (tn_wangb, commit 012b6f14, 2026-05-26)
- 工商业风电项目终验法相关

### CmLightUseController — 工商业项目使用 (代码明确证明, 2026-05-26)
**来源**: `rrsjk-admin-web` → `CmLightUseController.java` (tn_wangb, commit 012b6f14, 2026-05-26)
- 4行变更，配合终验法功能

### CmNodeController — 节点管理 (代码明确证明, 2026-05-26)
**来源**: `rrsjk-admin-web` → `CmNodeController.java` (解钦, commit 08e979f8, 2026-05-18)
- 3行变更，配合工商业兼容风电

## 关键实体

### CmConstructionProgressAudit — 施工进度审核
- **字段**: projectCode, projectName, address, engineeringType, processStage, processStageName, nodeId, nodeName, totalProgress, addProgress, finishAuditStatus, status, remark, createdAt, createdBy, auditAt, auditBy
- **状态枚举**: `StatusEnum` (通过代码推断，具体值待确认)
- **关联**: `CmLightProject`(项目信息), `CmNodeAttachmentTemplate`(附件模板), `CmConstructionProgressHisAtchDto`(历史附件)

### CmLightProjectIncomePolicy — 收入政策
- **关联**: `CmLightProjectIncomePolicyItem`(政策明细项)
- **筛选维度**: policyType, status

## 前端模板

| 模板文件 | 用途 |
|---|---|
| `cmConstructionProgressAuditList.ftl` | 施工进度审核列表 (326行) |
| `cmConstructionProgressAuditDetail.ftl` | 施工进度审核详情 (296行) |
| `cmConstructionProgressAuditAudit.ftl` | 施工进度审核操作页面 (367行) |
| `cmLightProjectIncomePolicyList.ftl` | 收入政策列表 (515行，大幅修改) |
| `cmLightProjectIncomePolicyDetail.ftl` | 收入政策详情 (140行) |
| `cmLightProjectIncomePolicyUpdate.ftl` | 收入政策修改 (303行) |
| `cmLightProjectIncomePolicyAudit.ftl` | 收入政策审核页面 (187行) |
| `cmLightProjectSimpleDetail.ftl` | 项目简易详情 (947行) |
| `cmLightProjectSetAdd.ftl` | 项目立项新增 |
| `cmLightProjectSetDetail.ftl` | 项目立项详情 |
| `cmLightProjectSetAudit.ftl` | 项目立项审核 |
| `cmLightProjectSetTrack.ftl` | 项目立项跟踪 |
| `cmLightProjectVoteTrack.ftl` | 投决审核跟踪 (含账务信息) |
| `cmLightProjectVoteAdd.ftl` | 投决新增 (含账务信息) |
| `cmLightProjectVoteAudit.ftl` | 投决审核 (含账务信息) |
| `cmLightProjectVoteDetail.ftl` | 投决详情 (含账务信息) |
| `cmLightProjectVoteUpdate.ftl` | 投决修改 (含账务信息) |
| `cmConstructionProgressAudit.ftl` | 施工进度审核 |
| `cmConstructionProgressDetail.ftl` | 施工进度详情 |
| `cmConstructionPlanAudit.ftl` | 施工计划审核 |
| `cmConstructionPlanDetail.ftl` | 施工计划详情 |
| `cmChangeAudit.ftl` | 变更审核 |
| `cmChangeDetail.ftl` | 变更详情 |
| `cmLightUseList.ftl` | 工商业使用列表 |
| `cmNodeList.ftl` | 节点管理列表 |
| `cmLightProjectSignInfoList.ftl` | 项目签约信息列表 |

## 业务特征

### 风电与光伏区分
- 2026-05-26 前端 `nahui-pv.epcb-mini` 增加风电与光伏项目区分
- 收入政策配置、收款里程碑等页面兼容风电业务类型
- 工程类型(`engineeringType`)字段用于区分风电/光伏

### 终验法
- 工商业风电项目采用终验法确认收入
- 涉及 `CmConstructionProgressAuditController` 新增和多个模板文件

### 账务信息模块
- 投决审核页面(Add/Audit/Detail/Update)增加账务信息模块
- EPC项目跟踪页面增加账务信息

### 并行审核
- 收入政策配置支持并行审核方案
- 新增审核页面 `cmLightProjectIncomePolicyAudit.ftl`

### 收款里程碑兼容风电 (TAEI-3107, 代码明确证明, 2026-05-21~26)
**来源**: `rrsjk-light-service` + `rrsjk-admin-web` (解钦, 7+ commits, branch: origin/feature-cm-wind-electric)
- 收款里程碑导入收入政策要求是工程经理
- 收入政策修改兼容新老逻辑
- 导入收入政策增加表头校验、项目校验、业务类型判断
- 下载模板增加对业务类型的判断

### 产值收入法与终验法 (TAEI-3107, 代码明确证明, 2026-05-21~27)
**来源**: `rrsjk-light-service` + `rrsjk-merchant-web` + `rrsjk-admin-web` + `rrsjk-finance-service` (tn_wangb/王斌, 25+ commits, branch: origin/feature-cm-wind-electric)
- 工商业风电项目产值收入法大量实现（rrsjk-light-service 20+ commits）
- 工商业风电项目终验法（rrsjk-admin-web, rrsjk-finance-service）
- 产值法上收入时收入限制放开（commit 0f5c5422）
- 工商业收款切换FAP（commit 51731715）
- 退质保金申请驳回后不释放已选择单据（rrsjk-finance-service）
- 新增FAP异步通知接口（rrsjk-light-service, branch: origin/20260416-fap）
- 无纸化列表补充发票已核销状态（rrsjk-admin-web）
|- **方案变更修改**: 方案变更逻辑适配（branch: origin/20260514-wb-planChange）

### 工商业风电产值收入法更新 (2026-05-28 追加)
**来源**: `rrsjk-light-service` + `rrsjk-admin-web` (tn_wangb/王斌, branch: origin/feature-cm-wind-electric + origin/20260416-fap)
- **CmGvsServiceImpl / CmLightUseServiceImpl**: 工商业风电项目产值收入法实现 (5/28 commits 0cd9f84/e851d42)
- **CmConstructionPlanServiceImpl**: 产值收入法进度管控 (5/28 commit 1e66818)
- **CmProductionValueIncomeServiceImpl**: 产值收入计算逻辑 (5/28 commit e851d42)
- **CmLightUseController** (admin-web): 工商业风电项目终验法 (5/27 commit 66e3172)
- **FAP异步回调**: 接收集团FAP异步回调方法 (5/28 commit 1ad8908)
|- **证据等级**: 代码明确证明

### 产值法收入限制放开 (TAEI-3159, 代码明确证明, 2026-05-27)
**来源**: `rrsjk-light-service` (tn_wangb/王斌, commit 0f5c5422)
- **需求**: 放开产值确认法的收入闸口，杨越越负责，参与人: 王斌
- **核心变更**: 注释掉 `CmProductionValueIncomeServiceImpl` 中的三项收入金额校验：
  - `curMaterialIncome + hisMaterialIncome > pvMaterialIncome` → 注释掉（材料收入超限检查）
  - `curConstructionIncome + hisConstructionIncome > pvConstructionIncome` → 注释掉（施工服务收入超限检查）
  - `curDesignIncome + hisDesignIncome > pvDesignIncome` → 注释掉（设计收入超限检查）
- **保留**: 成本超限检查仍然生效 (`curMaterialCost + hisMaterialCost > pvMaterialCost - materialUseDoneAmount`)
- **业务含义**: 产值确认法不再限制收入金额不能超过产值设计值，允许超额上报收入
- **状态**: 已完成 (2026-05-29)

### 工商业风电字段解耦: nodeFinishPct 统一进度标识 (代码明确证明, 2026-05-29)
**来源**: `rrsjk-light-service` (tn_wangb/王斌, commit 0cd9f84, branch: origin/feature-cm-wind-electric)
- **核心变更**: `CmGvsServiceImpl` 和 `CmLightUseServiceImpl` 中将多种材料/服务类型的专用进度字段统一为 `nodeFinishPct`
  - `majorMaterialUsePct` → `nodeFinishPct` (主料领用占比)
  - `auxiliaryMaterialUsePct` → `nodeFinishPct` (辅料领用占比)
  - `constructionServiceUsePct` → `nodeFinishPct` (施工服务占比)
  - `designServiceUsePct` → `nodeFinishPct` (设计服务占比)
- **业务含义**: 风电项目不再按材料/服务类型分别追踪进度占比，改用统一的节点完成百分比(`nodeFinishPct`)计算收入
- **关联需求**: TAEI-3107 (风电产值法兼容1.0) / TAEI-3159 (放开产值确认法收入闸口)
- **⚠️ 跨仓库变更模式**: 这是一个字段解耦(field decoupling)类型变更，需同时检查 `CmLightUse` 实体类中 `nodeFinishPct` 字段定义及所有引用处

### 收款里程碑兼容风电 (TAEI-3107, 代码明确证明, 2026-05-23)
**来源**: `rrsjk-light-service` (解钦, commit b167a0f5, branch: origin/feature-cm-wind-electric)
- **核心变更**: `CmLightProjectServiceImpl` 收款里程碑预付校验增加风电业务类型排除
  - 旧逻辑: `projectCode.startsWith("U") && PREPAY` → 执行预付校验
  - 新逻辑: `projectCode.startsWith("U") && !WIND_POWER && PREPAY` → 风电项目跳过预付校验
- **业务含义**: 风电项目的收款里程碑不执行预付款金额校验，与光伏项目区分处理

### 工商业电站写入工商业项目编码 (代码明确证明, 2026-06-01)
**来源**: `rrsjk-light-service` → `CmLightProject.java` + `LightEpcStationModel.java`, commit 0cb5e24 (tn_wangb, 2026-06-01)
- `CmLightProject.cmProjectCode` 字段: 在工商业电站创建时写入对应的工商业项目编码
- `LightEpcStationModel` 中增加对 `cmProjectCode` 的赋值逻辑
- 用途: 关联工商业电站与工商业项目，便于跨业务查询

## 待确认

- `CmConstructionProgressAudit` 的 `StatusEnum` 完整枚举值
- `engineeringType` 的完整枚举值(WIND/SOLAR等)
- 收入政策 `policyType` 和 `status` 的枚举定义
- 施工进度审核与户用电站完工确认的关系
- 终验法的具体业务规则和触发条件
- `CmConstructionProgressAuditService` 的完整接口定义
- 工商业项目(`CmLightProject`)与户用电站(`LightStation`)的数据模型关系

### 收入政策并行审核方案 (TAEI-3083/TAEI-3085, 代码明确证明, 2026-05-19~21)
**来源**: `rrsjk-light-service` (解钦, branch: origin/feature-cm-wind-electric)
- **CmLightProjectIncomePolicy**: 实体修改支持并行审核方案 (`eb6bb79b`, 3行变更)
- **收入政策导入校验**: 新增导入时的校验逻辑 (`37a61acc`)
- **政策编码生成**: 项目定制类型的政策编码生成 (`8a9d967c`)
- **节点查询方法**: 提供根据业务类型查询节点的方法 (`0a5fe895`)
- **状态修改**: 收入政策状态修改和生成的子政策字段设置 (`99e3aa9e`)
- **设计方案修改**: 工商业风电项目扩展计收方法字段 (`db257231`, CmLightProject +10/-5行, CmLightProjectNewRequest +2行)
- **证据等级**: 代码明确证明

### 电站回退冲销兼容完工前领用 (TAEI-3083, 代码明确证明, 2026-05-19~21)
**来源**: `rrsjk-light-service` (解钦, branch: origin/feature-cm-wind-electric)
- **核心场景**: 电站回退重新领用时区分"完工前领用"和"完工后领用"
- **旧逻辑缺陷**: 完工前领用不创建SO出库队列，回退冲销时未处理
- **修复提交**: `eb8bd383`/`789fff6c`/`2fbdd007`/`e5c03619` (4次迭代修复)
- **证据等级**: 代码明确证明

### 工商业自持电站损益报表 (TAEI-3043, 代码明确证明, 2026-05-11~17)
**来源**: `rrsjk-light-service` → `CmOwnerStationReportServiceImpl.java` + `CmOwnerStationWhiteListServiceImpl.java` (王斌/龙龙, 13+ commits)

**核心变更**:
- **新增实体**: `CmOwnerStationReportThirdLog` — 第三方日志记录表（从大数据库查询发电量的日志）
  - Mapper XML: `CmOwnerStationReportThirdLog.xml` (214行新增)
  - DAO: `CmOwnerStationReportThirdLogDao` (40行新增)
- **报表核心逻辑重构**: `CmOwnerStationReportServiceImpl` 经历多次迭代（159+/47+ 行变更）
  - 充电桩发电量查询优化：从 for 循环逐个查 `chargingStationService.getPvGenerationByMonth` 改为批量查询
  - 新增 `queryMonth` 参数过滤高压电费查询 (`LightHighElec.xml`)
  - 毛利率除零保护：`totalIncomeAmount == 0` 时毛利率设为 0
- **新增枚举**: `LightStationPlanChange.StatusEnum.NO_NEED_AUDIT`（完工前方案变更，仅品牌变更无需审核）
- **方案变更逻辑**: `LightStationPlanChangeServiceImpl` 增加 skipAudit 逻辑（仅品牌变更时自动审核通过，审核人"王红凯"硬编码）
- **白名单扩展**: `cm_owner_station_white_list` 表扩展字段支持报表二期需求
- **PCS 接口**: 开发环境地址更新为测试环境
- **前端**: `rrsjk-admin-web` 新增自持电站损益报表页面 (`tn_wangb`, 6+ commits)

**涉及表**: `cm_owner_station_report`, `cm_owner_station_white_list`, `cm_owner_station_report_third_log` (新), `light_high_elec`, `light_station_plan_change`

**⚠️ 代码质量风险**:
1. 审核人"王红凯"硬编码在 `LightStationPlanChangeServiceImpl` 中
2. PCS 接口地址在 application-dev.yml 中改为了测试环境，需确认 prod 配置
3. 毛利率除零保护是事后修复，需确认上线前是否充分测试

---

## 工商业项目收益预测服务 (nh-business-forecast-service)

**代码明确证明** | 通读日期: 2026-06-19 | 最后提交: 2024-04-20

### 概述
**来源**: `nh-business-forecast-service` (com.nahui.businessforecast)
独立微服务，为**工商业光伏项目**提供投资可行性预测和收益测算。通过 Dubbo 暴露接口给前端 (rrsjk-mobile-web 的 businessforecast Controller) 调用。

**技术栈**: Spring Boot + MyBatis + Dubbo (Zookeeper) + Redis + Aliyun OSS + iTextPDF
**数据库**: `db003.rrsjk.internal` (生产), MySQL
**包路径**: `com.nahui.businessforecast`

### 三种投资模式 (代码明确证明)
**来源**: `nh-business-forecast-api/.../enums/InvestmentModelEnum.java`

| 值 | 模式 | 模板名 | 核心计算逻辑 |
|---|---|---|---|
| 0 | EMC (合同能源管理) | EMC_TEMPLATE | 折扣电价或固定电价 → 年节能收益 |
| 1 | 业主自投 | SELF_INVESTMENT_TEMPLATE | 发电收入 - 投资成本 → 回本时间 |
| 2 | 融资租赁 | FINANCIAL_LEASE_TEMPLATE | 融资金额(=开发成本) × 利率 × 年限 → 每年本息 → 累计结余 |

### 发电量计算 (代码明确证明)
**来源**: `nh-business-forecast-impl/.../ElectricityGenerationDetailServiceImpl.java`

**核心公式**: `年发电量 = 装机容量(kW) × 光照时长(h) × 年效率系数`

**25年效率衰减曲线**:
```
Year 1: 100%, Year 2: 98%, Year 3: 97.4%, Year 4: 96.8%, Year 5: 96.2%
Year 6: 95.6%, Year 7: 95%, Year 8: 94.4%, Year 9: 93.8%, Year 10: 93.2%
... 每年递减 0.6% ... Year 25: 86.6%
```

**光照时长来源**: `install_dip_angle_info_region` 表，按省+市+倾角类型(最佳倾角/平铺)查询

### 电价体系 (代码明确证明)

**分时电价类型** (`ElectricityPriceTypeEnum`): 尖(POINT)、峰(PEAK)、平(FLAT)、谷(VALLEY)、深谷(DEEP_VALLEY)

**用电类型1** (`TouElectricityPriceTypeOneEnum`): CN=一般工商业, BI=大工业

**用电类型2** (`TouElectricityPriceTypeTwoEnum`): UNITARY=单一制, TWOP=两部制

**电压等级** (`VoltageLevelEnum`): 不满1kV / 1-10(20)kV / 35-110kV / 110-220kV / 220kV以上

**EMC电价模式** (`ElectrictiyPriceModelEnum`):
- 0=折扣电价: `实际电价 = 平均电价 × (1 - 折扣比例/100)`
- 1=固定电价: `实际电价 = 固定电价`

### 节能减排系数 (代码明确证明)
**来源**: `nh-business-forecast-api/.../EmissionReductionEnum.java`

每 MWh 发电量对应的减排量:
| 指标 | 系数 | 单位 |
|---|---|---|
| 标准煤 | 300.7 kg | 每MWh |
| 烟尘 | 0.017 kg | 每MWh |
| SO₂ | 0.083 kg | 每MWh |
| CO₂ | 824 kg | 每MWh |
| NOx | 0.133 kg | 每MWh |

### 项目建站成本校验规则 (代码明确证明)
**来源**: `nh-business-forecast-impl/.../ProjectCostInfoDetailServiceImpl.java`

| 参数 | 范围 |
|---|---|
| 项目运行年限 | 1~25年 |
| 每瓦电力成本 | 2.5~5 元 |
| 每瓦运维成本单价 | 0.03~0.05 元 |
| 配储比例 | 0~20% |
| 配储价格 | 1~2.5 元/瓦 |

### PDF 项目规划书生成 (代码明确证明)
**来源**: `nh-business-forecast-impl/.../ForecastProjectDetailServiceImpl.java` + `OssPdfFileUtil.java`

**流程**: 查询项目详情 → 反射填充字段到 Map → 根据投资模式选模板(EMC_TEMPLATE/SELF_INVESTMENT_TEMPLATE/FINANCIAL_LEASE_TEMPLATE) → iTextPDF 渲染 → 上传 OSS → 返回 CDN URL

**OSS 配置**: `oss-cn-qingdao.aliyuncs.com`, bucket=`pvs-public`, CDN=`cdn01.rrsjk.com`

### 核心数据库表

| 表名 | 用途 |
|---|---|
| `forecast_project_detail` | 预测项目主表 (projectCode, 地址, 装机容量, 投资模式, 发电量, 成本, 规划书URL) |
| `electricity_generation_detail` | 发电量详情 (year1~year25 发电量字段, 总/年均发电量) |
| `project_cost_info_detail` | 建站成本 (电力成本/运维/配储/开发成本/总投资) |
| `project_investment_income` | 投资收益 (EMC折扣/自投回本时间/融资租赁利率) |
| `electricity_price_of_coal` | 脱硫煤标杆电价 (按省份) |
| `tou_electricity_price` | 分时电价 (按省份+用电类型+电压等级, 尖/峰/平/谷/深谷) |
| `electricity_price_summary_diff_period` | 分时电价时段汇总 (按省份+小时+月份, 12个月×24时段) |
| `install_dip_angle_info_region` | 各地区安装倾角光照信息 (省/市/最佳倾角/平铺光照时长) |
