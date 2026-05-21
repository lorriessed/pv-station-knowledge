# 审核、审批与派单

更新时间: 2026-05-17

## 已确认知识

### 通用要求
分析业务逻辑时必须列出涉及的数据表、关键字段、字段变更路径、枚举值实际存储值。

---

## CBS 电站三审流程（2026-05-17 代码通读确认）

> **来源**: `rrsjk-admin-web` + `rrsjk-light-service` 代码通读，2026-05-17
> **证据等级**: 代码明确证明

所谓"三审"实际上跨越电站生命周期的不同阶段，并非连续三次审核：
- **方案审核**：电站创建后，审核业主信息和方案配置（施工前）
- **技术审核**：完工确认后，审核施工质量和并网资料（施工后）
- **商务审核**：技术审核通过后，审核商务验收和合同签署（并网前）

### 三审对比表

| 审核节点 | 页面路径 | 主要 Controller | 审核内容 | 通过后状态变更 | 权限 |
|---------|---------|----------------|---------|---------------|------|
| 方案审核(第一审) | `/lightStation/list.html` → `audit.html` | `LightStationController` | 电站基本信息、方案配置(SKU+数量)、逆变器配置 | `WAIT_AUDIT` → `WAIT_ORDER`(普通) / `WAIT_THIRD_AUDIT`(顶好/广发) | `lightStation:audit` |
| 技术审核(第二审) | `/lightStationSkill/list.html` → `audit.html` | `LightStationSkillController` | 完工确认资料：组件照片、逆变器SN、倾角、并网资料等 | `WAIT_TECH_CHECK` → `WAIT_UPLOAD_GRID_INFO` 或 `WAIT_FIRST_AUDIT` | `lightStationSkill:audit` |
| 商务审核(第三审) | `/lightStationBusiness/list.html` → `audit.html` | `LightStationBusinessController` | 商务验收资料：合同签署、并网信息、发电数据等 | `WAIT_FIRST_AUDIT` → `ENABLE`(已完成) | `lightStationBusiness:audit` |

### 完整审核流程

```
电站创建(INIT) → 服务商提交方案 → [待审核 WAIT_AUDIT]
    │
    ├─── 方案审核(第一审) ───┤
    │   审核人: 分中心/服务商管理员
    │   审核内容: 业主信息、方案配置、逆变器配置
    │   
    ├── 通过 ──→ [待下单 WAIT_ORDER] 或 [待三方审核 WAIT_THIRD_AUDIT]
    │   │           │
    │   │           ▼
    │   │       下单 → 施工中 ROADWORKING → 完工确认 → [完工确认审核 COMPLETE_WAIT_AUDIT]
    │   │               │
    │   │               └── 分中心完工审核通过 ──→ [待技术审核 WAIT_TECH_CHECK]
    │   │
    └── 驳回 ──→ [驳回 AUDIT_REJECT] → 服务商修改后重新提交


[待技术审核 WAIT_TECH_CHECK]
    │
    ├─── 技术审核(第二审) ───┤
    │   审核人: 总部技术人员
    │   审核内容: 完工确认图片、逆变器SN、倾角、并网资料
    │   共享入口: CompleteConfirmServiceImpl.auditOk(auditType=TECH_CHECK)
    │   
    ├── 通过 ──→ 判断并网资料
    │   ├── 已上传并网资料 → [待商务审核 WAIT_FIRST_AUDIT]
    │   │                      │
    │   │                      ├── 传递光E宝(sendToGYX)
    │   │                      └── 传递银联(sendToYL)
    │   │
    │   └── 未上传并网资料 → [待提交并网资料 WAIT_UPLOAD_GRID_INFO]
    │                           │
    │                           ▼ (上传并网资料后)
    │                       [待商务审核 WAIT_FIRST_AUDIT]
    │
    └── 驳回 ──→ [技术审核驳回 TECH_CHECK_REJECT]


[待商务审核 WAIT_FIRST_AUDIT]
    │
    ├─── 商务审核(第三审) ───┤
    │   审核人: 总部商务人员
    │   审核内容: 合同签署状态、发电数据(firstThreePowerAt)、商务验收资料
    │   前置条件: firstThreePowerAt 不为空(连续三天发电)
    │   共享入口: CompleteConfirmServiceImpl.auditOk(auditType=WAIT_FIRST_AUDIT)
    │   
    ├── 通过 ──→ [已完成 ENABLE]
    │   │
    │   ├── 电站完成后执行:
    │   │   ├── 上收入记录
    │   │   ├── 公司备案/能源币
    │   │   ├── 生成服务费采购单
    │   │   ├── 创建电费补贴
    │   │   ├── 创建租金队列
    │   │   ├── 生成核验记录
    │   │   ├── 同步中核数据
    │   │   └── 发放电站完成奖励
    │   │
    │   └── 自动划转运维商
    │
    └── 驳回 ──→ [商务审核驳回 FIRST_AUDIT_REJECT]
```

### 审核记录表

统一使用 `light_station_audit` 表，通过 `audit_type` 区分：
- `PLAN_AUDIT` - 电站方案审核
- `TECH_CHECK` - 技术审核
- `WAIT_FIRST_AUDIT` - 商务审核
- `COMPLETE_WAIT_AUDIT` - 完工确认审核（分中心）
- `OFF_LINE_AUDIT` - 线下验收
- `SP_PLAN_AUDIT` / `SP_TECH_CHECK` / `SP_WAIT_FIRST_AUDIT` - 服务商端审核

审核状态: `WAIT_AUDIT`(待审核)、`AUDIT_OK`(通过)、`AUDIT_REJECT`(驳回)

### 电站状态枚举 (LightStation.Status)

| 状态值 | 说明 | 所属阶段 |
|--------|------|---------|
| INIT | 待提交审核 | 创建 |
| WAIT_AUDIT | 待方案审核 | 方案审核 |
| WAIT_THIRD_AUDIT | 待三方审核(顶好/广发) | 方案审核 |
| AUDIT_REJECT | 方案审核驳回 | 方案审核 |
| WAIT_CONFIG | 审核完成待配方案 | 方案审核 |
| WAIT_ORDER | 待下单 | 下单 |
| ROADWORKING | 施工中 | 施工 |
| ROADWORK_CONFIRM | 施工信息待确认 | 施工 |
| COMPLETE_WAIT_AUDIT | 完工确认审核 | 完工审核 |
| COMPLETE_AUDIT_REJECT | 完工确认审核驳回 | 完工审核 |
| WAIT_TECH_CHECK | 待技术审核 | 技术审核 |
| TECH_CHECK_REJECT | 技术审核驳回 | 技术审核 |
| WAIT_OFF_LINE_CHECK | 待线下验收 | 线下验收 |
| WAIT_UPLOAD_GRID_INFO | 待提交并网验收资料 | 并网资料 |
| WAIT_FIRST_AUDIT | 待商务审核 | 商务审核 |
| FIRST_AUDIT_REJECT | 商务审核驳回 | 商务审核 |
| OFF_LINE_CHECK_REJECT | 现场验收驳回 | 线下验收 |
| ENABLE | 已完成 | 完成 |
| DISABLE | 已删除 | 终态 |
| STOP | 已终止 | 终态 |
| REPURCHASE | 已回购 | 终态 |

### 商务状态枚举 (LightStation.BusinessStatus)

| 状态值 | 说明 |
|--------|------|
| WAIT_UPLOAD_GRID_INFO | 待提交并网验收资料 |
| BUSINESS_INFO_UPLOADED | 已提交并网资料 |
| WAIT_BUSINESS_AUDIT | 待商务验收 |
| BUSINESS_AUDIT_REJECT | 商务验收驳回 |
| BUSINESS_AUDIT_APPROVAL | 商务验收通过 |

### 商务审核并行模式 (TAEI-2857, 2026-01-19~2026-02-08 补漏第4期)
- **来源**: `rrsjk-light-service/rrsjk-light-impl/src/main/java/com/rrsjk/light/service/model/BusinessStatusMode.java` (于淼, commit: b9a4566 + 系列提交)
- **需求**: TAEI-2857 【建站】商务验收技术验收并行审核
- **核心变更**: 引入 `businessStatus` 字段到 `light_station` 表，实现技术审核和商务审核的双轨并行状态机

**BusinessStatusMode 状态机逻辑**:
```
技术审核 + 商务审核 双轨并行，通过 StationStatusCombine 组合状态:
- businessStatus: 商务审核独立状态 (5种)
- stationStatus: 电站整体状态

审核类型 (audit_type):
- TECH_CHECK: 技术审核
- WAIT_FIRST_AUDIT: 商务审核
- UPLOAD_GRID_INFO: 提交并网资料

关键分支逻辑:
1. 技术审核驳回 + 容量变化(changeRoofOrHouseType=YES):
   → 商务审核回退 (BUSINESS_AUDIT_APPROVAL → BUSINESS_INFO_UPLOADED)
   → 撤销商务派单记录
2. 技术审核驳回 + 容量未变化(changeRoofOrHouseType=NO):
   → 商务审核可独立推进 (BUSINESS_INFO_UPLOADED → WAIT_BUSINESS_AUDIT)
3. 技术审核通过:
   → 若商务已通过 → ENABLE (电站完成)
   → 校验快照: 房屋类型/容量与快照不一致则回退商务审核
4. 提交并网资料:
   → 技术已通过 → WAIT_BUSINESS_AUDIT
   → 技术驳回 + 容量未变 → WAIT_BUSINESS_AUDIT (并行)
   → 技术驳回 + 容量变化 → BUSINESS_INFO_UPLOADED (等待)

商务审核快照校验 (business_audit_snapshot 表):
- 技术审核通过时，对比 snapshotHouseType vs 最新houseType
- 对比 snapshotCompleteConfirmCapacity vs 最新CompleteConfirmCapacity
- 不一致时自动回退商务审核状态并记录操作日志
```

**LightStation.BusinessStatus 枚举** (代码明确证明):
| 状态值 | 说明 | 触发条件 |
|--------|------|---------|
| WAIT_UPLOAD_GRID_INFO | 待提交并网验收资料 | 完工确认审核通过 |
| BUSINESS_INFO_UPLOADED | 已提交并网资料 | 上传并网资料后，或技术驳回容量变化时回退 |
| WAIT_BUSINESS_AUDIT | 待商务验收 | 已提交资料且技术通过/容量未变驳回 |
| BUSINESS_AUDIT_REJECT | 商务验收驳回 | 商务审核驳回 |
| BUSINESS_AUDIT_APPROVAL | 商务验收通过 | 商务审核通过且技术也通过 |

**涉及表字段变更**:
- `light_station.business_status` — 新增商务审核状态字段
- `light_station_audit` — 新增 `change_roof_or_house_type` 字段记录容量是否变化
- `business_audit_snapshot` — 商务审核快照表，保存审核时的房屋类型和容量快照

### 核心 Service 汇总

| Service | 职责 | 关键方法 |
|---------|------|---------|
| `LightStationServiceImpl` | 方案审核 | `auditInfoOk()`, `auditInfoRejection()` |
| `CompleteConfirmServiceImpl` | 技术审核+商务审核 | `auditOk()`, `auditReject()` |
| `LightStationAuditServiceImpl` | 审核记录管理 | `updateOrCreateAudit()` |
| `BusinessAuditSnapShotService` | 商务审核快照保存 | 保存快照到 `business_audit_snapshot` 表 |

### 关键业务规则

1. **暂停保护**: 所有审核节点检查电站不能处于暂停状态(PAUSED)
2. **冻结保护**: 技术审核和商务审核检查电站不能处于冻结状态
3. **撤回保护**: 方案审核检查电站不能已撤回(INIT)
4. **防重复提交**: 审核接口使用 `@RepeatSubmit` 注解（间隔60秒）
5. **合同签署**: 商务审核必须检查所有合同是否已签署完成
6. **发电校验**: 商务审核要求电站必须有连续三天发电记录(firstThreePowerAt)
7. **多模式分支**: 不同模式(YX/HR/DH/GF/HRFLC_EPC等)有不同审核流程
8. **审核快照**: 商务审核通过后会保存快照到 `business_audit_snapshot` 表
9. **驳回图片缓存**: 驳回图片暂存 Redis(`station:tech:reject:images:{stationId}`)

### 涉及数据库表

| 表名 | 用途 |
|------|------|
| `light_station` | 电站主表，status/business_status 等核心状态字段 |
| `light_station_audit` | 审核记录表，audit_type 区分审核类型 |
| `light_station_plan_config` | 方案配置表，方案审核涉及 |
| `light_station_confirm_img` | 完工确认图片表 |
| `light_station_inverter` | 逆变器表 |
| `light_grid_cert` | 并网证表 |
| `light_station_contract_record` | 合同记录表 |
| `business_audit_snapshot` | 商务审核快照表 |
| `light_station_operate_log` | 操作日志表 |
| `gf_light_station` | 广发电站表（广发模式） |
| `light_station_yuexiu` | 越秀电站表（越秀模式） |

---

### 派单时间规则待复核
旧 cron 输出 2026-05-09 提到派单时间规则 3.1：工作日正常时间直接放行，非正常时间查配置，并新增时间段重叠校验。该知识需要从 /data/pvcode 中复核后固化。

### 审核派单时间配置 (2026-05-10 新增)
- **来源**: rrsjk-admin-web, `LightAuditDispatchTimeConfigController.java` (新增文件, 211行)
- 路径: `/dispatch/time/config/`
- 功能: 非工作日派单时间配置管理
- 权限: `dispatch:timeConfig:read`
- 支持列表查询 (`doList.do`) 和导出功能 (`LightAuditDispatchTimeConfigExcel`)
- 涉及实体: `LightAuditDispatchTimeConfig`、`LightStationAudit`、`LightTechAuditor`

### 故障工单审核 (2026-04-28)
- **来源**: nahui-pv.hds-h5, `faultWorkOrder/list/audit.vue` (commit 105c389, 李培龙)
- 恢复审核条件（之前可能临时放开）
- `AuditAppeal.vue` 运维商取值更新、超期申诉功能优化

### 储能安装维修评价体系 (2026-05-11 新增，代码证明)
- **来源**: rrsjk-energystorage-service, commits 2023-06-08 ~ 2023-06-15, jiazhenyu
- **实体**: `InstallMaintenanceInfo` (entity/installMaintenance/InstallMaintenanceInfo.java)
- **关键枚举**:
  - `InstallMaintenanceInfo.Status`: `WAIT_RATE` (待评价), `COMPLETED` (已完成)
  - `InstallMaintenanceInfo.RateStatus`: `AUTO` (自动评价)
- **关键字段**:
  - `rateStar`: 评分星级 (1-5)
  - `rateStatus`: 评价状态 (AUTO=自动好评)
  - `processAt`: 处理完成时间 (LocalDateTime)
- **自动好评定时任务**: `InstallMaintenanceInfoModel.favorableComment()`
  - 查询条件: status = `WAIT_RATE`
  - 判断逻辑: processAt 距今 > 15天 且 rateStar 为空
  - 执行操作: rateStar=5, status=COMPLETED, rateStatus=AUTO
  - 服务注册: `InstallMaintenanceInfoJobService` → `InstallMaintenanceInfoJobServiceImpl`
  - 调度配置: spring-config/service.xml 中注册
- **关联文件**:
  - Service: `InstallMaintenanceInfoService`, `InstallMaintenanceInfoJobService`
  - Dao: `InstallMaintenanceInfoDao`
  - MyBatis: `mybatis/mapper/InstallMaintenanceInfo.xml`
  - Job: `InstallMaintenanceInfoModel` (jobModel/installMaintenanceInfo/)

### 储能项目咨询管理 (2026-05-11 新增，代码证明)
- **来源**: rrsjk-energystorage-service, commit 2023-06-02, jiazhenyu
- **实体**: `ConsultationDetail` (entity/installMaintenance/ConsultationDetail.java)
- **功能**: 项目咨询详情信息的增删改查
- **关联文件**:
  - Service: `ConsultationDetailService`, `ConsultationDetailServiceImpl`
  - Dao: `ConsultationDetailDao`
  - MyBatis: `mybatis/mapper/ConsultationDetail.xml`

### 配货申诉审核
**来源**: rrsjk-admin-web → `PurchaseAppealsAuditController.java`
- 路径: `/purchaseAppealsAudit/`
- 权限: `purchaseAppealsAudit:read:list`, `purchaseAppealsAudit:read:export`, `purchaseAppealsAudit:read:audit`
- 接口:
  - `doList.do` - 分页查询申诉记录 (flag=1过滤)
  - `doExport.do` - 导出Excel (3000条/页)
  - `batchAudit.do` - 批量审核 (通过/驳回 + 驳回原因)
  - `auditSingle.do` - 单条审核
- 审核结果通过 `LightPurchaseAppealsService.batchAudit()` 处理

### 电站迁移多级审核
**来源**: rrsjk-admin-web → `SwitchModeController.java`
- 路径: `/switchMode/`
- 三级审核流程:
  1. 片长审核: `confirm` → `switchLightModeService.confirmData()`
  2. 市场总监审核: `confirmMarketing` → `switchLightModeService.auditMarketingDirector()`
  3. 资产部审核: `confirmAsset` → `switchLightModeService.auditAsset()`
- 数据导入: `importData.do` (xls格式，6列: 批次号/电站编码/类型/迁出公司/迁入公司/区位)
- 导出限制: `@LimitationExport(allowExport = 1, periodTime = 50)` - 50秒内最多导出1次

### 资方主数据审核
**来源**: rrsjk-admin-web → `InvestorMasterDataAuditController.java`
- 路径: `/investor/`
- 权限: `investor:read:list`, `investor:write:create`, `investor:write:update`, `investor:write:delete`, `investor:write:rating`, `investor:write:cooperation`
- 支持资方信息CRUD、评级变更、合作状态更新
- 导出: 1000条/页分页导出

### 华融FLC审核页面 (代码明确证明, 2026-05-15)
**来源**: `rrsjk-admin-web` → `src/main/resources/templates/hrflc/hrflcAuditOwnerList.ftl` (commits 06e1916c, f81eac4f, 5afc7fdf, 德, 2026-05-15)
- 修复审核状态值拼写错误
- 修正审核状态枚举值和显示逻辑
- 添加华融EPC选项和合同状态格式化功能
- **证据等级**: 代码明确证明

### 金蝶记账失败状态显示 (代码明确证明, 2026-05-15)
**来源**: `rrsjk-admin-web` → `src/main/resources/templates/light/lightProjectElectricOrderList.ftl` (commit 49c1dfa6, mabin, 2026-05-15)
- 电费订单列表页面新增金蝶记账失败状态展示
- **证据等级**: 代码明确证明

## 待确认
- 派单规则 3.1 的完整代码来源、配置表、审核类型枚举。
- 技术审核、商务审核、线下验收的触发和驳回规则。
- 储能安装维修评价表的具体数据库表名和完整字段结构。
- 电站迁移审核中各审核角色的权限模型。
- 资方主数据审核流程的具体审核节点。

---

## 完工前变更方案审批流变更 (代码明确证明, 2026-05-19)
**来源**: `rrsjk-admin-web` → `planChangeList.ftl` (commit 84e2b58, tn_wangb, 2026-05-14)
**来源(后端)**: `rrsjk-light-service` → `LightStationPlanChangeServiceImpl.java`, `LightStationPlanChange.xml`, `LightStationPlanChangeAuditLog.xml`
**需求**: TAEI-3083 【建站】完工前变更方案审批流变更

- **新增状态**: `NO_NEED_AUDIT` (无需审核) — 第六种审批状态
- **原有状态**: CHECK_PASS(验收通过), CHECK_REJECT(验收驳回), CHANGE_FINISH(变更完成), DISABLE(删除), ENABLE(审核通过)
- **相关表**: `light_station_plan_change` (主表), `light_station_plan_change_audit_log` (审批日志), `light_station_plan_change_detail` (变更明细), `light_station_epc_plan_change` (EPC变更), `light_station_epc_plan_change_log` (EPC变更日志)
- **推断**: 新增"无需审核"状态简化了特定场景下的审批流程，跳过审核环节直接进入变更完成


## 来源
- Hermes MEMORY.md，2026-05-09 迁移。
- rrsjk-admin-web/nahui-pv.hds-h5 代码扫描 2026-05-10。
- rrsjk-energystorage-service 代码扫描 2026-05-11。
- 云效补漏第3期 (2025-12-29~2026-01-18) 代码扫描 2026-01-18。

---

## 审核派单系统 (代码明确证明, 2026-01-18 扫描补漏第3期)
**来源**: `rrsjk-light-service` (commits by 解钦, 2026-01-06~17, TAEI-2815 二级商管理/TAEI-2808 建站变更)

### 核心实体
- `LightAuditDispatchLog` — 派单日志实体
  - 审核类型枚举: `PLAN_AUDIT`(方案审核), `TECH_AUDIT`(技术审核), `BUSINESS_AUDIT`(商务审核)
  - 派单类型枚举: `MANUAL`(人工派单), `AUTO`(自动派单)
  - 任务类型枚举: `AUDIT_TASK`(审核任务)
  - 处理标识枚举: `SELF_AUDIT`(主动审核), `SNAP_INVALID`(抢单作废), `RE_DISPATCH`(人工改派)
- `LightTechAuditor` — 技术审核人员管理实体

### 派单服务
- `LightAuditDispatchLogService.dispatchOrder(DispatchOrderRequest)` — 派单入口
- 时间范围验证: 审核人员需在有效时间范围内
- 审核人员选择: 按审核类型查询有效审核人员
- 等量分配: 按待办数量等量分配到审核人员
- 重新派单功能: 支持人工改派

### 审核人员管理
- 光伏技术审核人员管理功能 (`LightTechAuditor` CRUD)
- 审核后更新派单信息功能
- 组件照片上传校验功能

### 前端
- `rrsjk-admin-web`: 技术审核人员管理页面 (解钦 2026-01-13~14)
- **关联需求**: TAEI-2815 (二级商管理), TAEI-2808 (建站变更方案/房型增加处理结果跟踪)

## 电站方案/完工撤回 (代码明确证明, 2026-01-18 扫描补漏第3期)
**来源**: `rrsjk-light-service` + `rrsjk-merchant-web` + `rrsjk-admin-web` (commits by wangxiran, 2026-01-04~16, TAEI-2808)

- 电站方案撤回功能 (`LightStationService.withdrawPlan()`)
- 电站完工撤回功能 (`LightStationService.withdrawComplete()`)
- 撤回操作中审核字段设置修复
- 光伏申报记录详情查询功能
- 方案审核报表开发
- 电站审核报表开发
- **前端**: `rrsjk-merchant-web` 添加撤回接口, `rrsjk-admin-web` 添加撤回按钮和报表
- **关联需求**: TAEI-2808 (完工后变更电站方案/房型增加处理结果跟踪)

## 安全节点照片组 (代码明确证明, 2026-01-18 扫描补漏第3期)
**来源**: `rrsjk-light-service` + `rrsjk-admin-web` (commits by wangxiran, 2026-01-11~16, TAEI-2808)

- 完工/修改完工增加安全节点照片组
- 商务审核增加照片状态
- 技术审核增加照片状态
- 审核页面照片展示优化
- **关联需求**: TAEI-2808 (申请增加房产证明、荷载报告影像收集)

## 房产证和荷载报告 (代码明确证明, 2026-01-18 扫描补漏第3期)
**来源**: `rrsjk-light-service` (commits by 解钦, 2026-01-06~07, TAEI-2808)

- 房产证和荷载报告图片功能
- 电站变更实体添加房产证和荷载报告字段
- 组件照片上传校验功能
- 方案变更待办事项查询接口
- 电站完工变更方案待办事项功能
- **关联需求**: TAEI-2808 (完工后变更电站方案/房型增加处理结果跟踪 + 申请增加房产证明、荷载报告影像收集)

## 零碳商户公告 (代码明确证明, 2026-01-18 扫描补漏第3期)
**来源**: `rrsjk-light-service` + `rrsjk-merchant-web` + `rrsjk-admin-web` (commits by 代继宁, 2026-01-07~16, TAEI-2813)

### 核心功能
- `LightZeroMerchantNotice` — 商户公告实体
- `LightZeroMerchantNoticeEvent` — 事件驱动公告发送
- `LightZeroMerchantNoticeListener` — 监听器实现公告发送逻辑
- 合同签署成功后自动触发商户公告发送
- 商户公告列表分页查询 (支持时间范围筛选)
- 商户公告审核功能 (待审核 → 审核通过/驳回)
- 商户公告操作日志查询

### 枚举
- `LightZeroMerchantNoticeEnum` — 零碳商户通知枚举值
- 招商银行租赁电站实体类 (`LightCmbLeaseStation`)

### 前端
- `rrsjk-admin-web`: 商户公告列表/添加/审核页面
- `rrsjk-merchant-web`: 商户公告列表接口
- **关联需求**: TAEI-2813 (微信小程序银行卡变更)

## 逆变器序列号变更 (代码明确证明, 2026-01-18 扫描补漏第3期)
**来源**: `rrsjk-light-service` + `rrsjk-light-operation-service` + `repairs` + `nahui-pv.merchant-micro.osp` (commits by sunzn/付凯善/马金虎, 2026-01-04~16, TAEI-2813)

- 逆变器变更重复数据校验功能 (`LightInveterService`)
- 逆变器铭牌OCR识别功能 (后端接口 + 前端支持)
- 空逆变器SN号重复绑定问题修复
- 逆变器解绑逻辑重构
- 工单备件逆变器变更状态处理逻辑修复 (repairs)
- 逆变器序列号字段支持 (数据库 + Mapper)
- SN码OCR识别 (merchant-micro.osp 前端)
- 变更备件登记支持SN码OCR识别
- **关联需求**: TAEI-2813 (逆变器序列号变更逻辑优化)

## 运维工单超期申诉优化 (代码明确证明, 2026-01-18 扫描补漏第3期)
**来源**: `rrsjk-light-operation-service` + `rrsjk-hds-web` + `nahui-pv.hds-h5` + `nahui-pv.merchant-micro.osp` (commits by sunzn/李培龙, 2026-01-04~16, TAEI-2809)

- 申诉功能时间限制校验 (测试环境移除, 生产环境激活)
- 审核备注字段添加并优化超时逻辑
- 申诉审核弹窗信息返现功能
- 工单超期天数计算逻辑修复
- 工单申诉导出功能 (含审核备注字段)
- 扩展运维商提交申诉时的见证性资料附件类型
- 运维商提交申诉判断条件暂时取消 (HDS页面)
- **前端**: nahui-pv.hds-h5 (超期申诉页面), nahui-pv.merchant-micro.osp (申诉提交)
- **关联需求**: TAEI-2809 (HDS/商户通/APP运维工单超期申诉优化)

## 华融整村推进 (代码明确证明, 2026-01-18 扫描补漏第3期)
**来源**: `rrsjk-light-service` (commits by yumiao, 2026-01-05~16, TAEI-2807)

- 整村汇流模式支持 (`HrflcStationModel`)
- 整村推进电站类型处理逻辑修复
- 整村电站逆变器信息同步模块类型修正 (dev环境 P→N)
- 整村推进电站限制检查移除
- 项目同步中进件模式设置修复
- 子服务商成员ID字段支持
- 模块序列号权限控制功能
- 方案审核列表查询功能
- **关联需求**: TAEI-2807 (华融整村推进电站进件开发)

## 日历工作日节假日 (代码明确证明, 2026-01-18 扫描补漏第3期)
**来源**: `rrsjk-system-service` (commits by yumiao, 2026-01-13~16)

- 日历表工作日节假日功能
- 日历天服务引用配置
- 短信发送服务签名配置
- Guava依赖添加
- **关联需求**: 基础服务升级

### AI房产证识别 (代码明确证明, 2026-05-18~20)
**来源**: `rrsjk-light-service` → LightStationHouseCertificateOcr.java, LightStationHouseCertificateOcrService.java, LightImageVerification.java, CompleteConfirmServiceImpl.java (commits ee04e9f/323540e/cf7e5c4, mabin, 2026-05-18~20, branch: 20260518-fangchanzhengOCR)
**关联需求**: TAEI-2728 【AI】AI识别房产证
- **实体**: `LightStationHouseCertificateOcr` — 映射表 `light_station_house_certificate_ocr`
  - 字段: stationCode, houseCertificateUrl, ocrStatus, ocrResult(JSON), sourceStationName(原业主姓名), ocrStationName(OCR识别业主名), sourceIdNo(原身份证号), ocrIdNo(OCR身份证号), sourceAddress(原地址), ocrAddress(OCR识别地址)
- **触发时机**: 并网确认(CompleteConfirm)和电站影像修改时，自动触发房产证OCR识别
- **技术实现**: 调用阿里云AI大模型接口进行房产证图片OCR识别
  - 接口参数和URL配置: 2026-05-20 修正了房产证OCR接口参数和URL配置
- **线程池**: 新增/调整线程池配置支持异步OCR处理
- **影像验证**: `LightImageVerification` 新增房产证相关字段
- **证据等级**: 代码明确证明

### 派单2.0 — 审核通过后清空审核字段 (2026-02-27 代码明确证明)
**来源**: `rrsjk-light-service` → `BaseLightStationMode.java`, `LightStationAuditDao.java`, `LightStationAudit.xml`, `LightAuditDispatchLogDao.java`, `LightAuditDispatchLog.xml` (commits c94236d/7cd8e3e/7688d73, 解钦, TAEI-2869)
- **背景**: 修改电站方案后需要重新走审核流程，但旧审核信息(audit_by, audit_at, reject_reson等)会残留
- **变更逻辑**: `BaseLightStationMode` 中电站更新时将审核状态重置为 `WAIT_AUDIT`，同时清空以下字段:
  - `audit_by` = null, `audit_at` = null, `reject_reson` = null
  - `audit_remark` = null, `rejection_type` = null, `rejection_type_description` = null
- **新SQL**: 新增 `updateForClearAuditInfo` 方法，与原有 `updateSimple` 不同，它显式设置上述字段为null
- **派单逻辑优化**: `LightAuditDispatchLogDao.findWaitDispatchLogByStationIdAndAuditType` 替换了 `findLatestDispatchLogByStationIdAndAuditType`，只查询 `deal_flag = 'WAIT'` 的待派单记录
- **证据等级**: 代码明确证明

### 派单2.0 — 提交订单时技术审核状态检查 (2026-02-10 代码明确证明)
**来源**: `rrsjk-light-service` → `DispatchOrderAspect.java` (commit a414dd62c8, 解钦)
- **变更**: `SUBMIT` 场景从静态返回 `WAIT_FIRST_AUDIT` 改为调用 `getAuditTypeForSubmit()` 动态判断
- **逻辑**: 检查电站是否已有 `TECH_CHECK` 类型审核且状态为 `AUDIT_OK`
  - 技术审核通过 → 返回 `WAIT_FIRST_AUDIT`（允许派单）
  - 技术审核未通过 → 返回 `null`（阻止派单）
- **证据等级**: 代码明确证明

### 并网资料提交校验 & 审核类型动态支持 (2026-02-10 代码明确证明)
**来源**: `rrsjk-light-service` (commits 058d2c9b/b6f3b1f3/0a466d0c, 解钦)
- 修复并网资料提交校验逻辑
- 验收确认服务添加动态审核类型支持
- 添加审核类型校验逻辑
- **证据等级**: 代码明确证明

### 方案变更 — 审核校验与变更次数统计 (TAEI-2869, 2026-02-25 代码明确证明)
**来源**: `rrsjk-light-service` → `LightStationPlanChangeServiceImpl.java`, `LightStationPlanChange.xml`, `LightPlanChangeDetail.java`, `LightStationPlanChangeExtra.java` (commits f5705d68/807b8116/d4ce5147, 解钦)
- **审核校验**: 创建变更方案前调用 `checkAuditProcessingPlan()`，防止并发变更
- **变更次数统计**: 新增 `completeBeforeChangeNum`（完工前变更次数）和 `completeAfterChangeNum`（完工后变更次数）
  - SQL子查询: `COUNT(*) FROM light_station_plan_change WHERE status='CHANGE_FINISH' AND change_node='COMPLETE_BEFORE/COMPLETE_AFTER' AND id < a.id`
  - 变更节点枚举: `ChangeNodeEnum` — `COMPLETE_BEFORE`(完工前变更), `COMPLETE_AFTER`(完工后变更)
- **SQL优化**: `findStationCountByDifferNode` 的 `changeId` 参数改为可选
- **证据等级**: 代码明确证明

### 方案变更驳回 — 完工后方案变更验收驳回 (TAEI-3123, 2026-05-21 代码明确证明)
**来源**: `rrsjk-light-service` (commit 67a86bd279, wangxiran), `rrsjk-admin-web` (commit b571944e7f, wangxiran), `rrsjk-light-data-service` (commit d1e6cc7431, wangxiran)
- **变更方案驳回目标**: 完工后方案变更的验收驳回支持驳回到方案审核节点
- **审核驳回图片附件**: 驳回时可上传图片附件，记录驳回原因
- **电站影像审核驳回**: 电站影像审核也支持驳回功能
- **完整业务链**:
  - `rrsjk-light-service`: `feat(plan): 添加变更方案驳回目标功能` + `feat(audit): 添加审核驳回图片附件功能`
  - `rrsjk-admin-web`: `feat(light): 添加验收审核驳回节点选择功能` + `feat(audit): 添加图片审核驳回功能`
  - `rrsjk-light-data-service`: `feat(audit): 实现电站影像审核驳回功能`
- **分支**: `origin/feature-wangxiran-changePlan`, `origin/feature-wxr-audit-20260519`
- **证据等级**: 代码明确证明

