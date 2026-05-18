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

## 来源
- Hermes MEMORY.md，2026-05-09 迁移。
- rrsjk-admin-web/nahui-pv.hds-h5 代码扫描 2026-05-10。
- rrsjk-energystorage-service 代码扫描 2026-05-11。
