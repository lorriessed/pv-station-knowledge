# CBS 电站三审流程分析

## 1. 三个审核页面对比

| 审核节点 | 页面路径 | 主要 Controller | 审核内容 | 通过后状态变更 |
|---------|---------|----------------|---------|---------------|
| 方案审核(第一审) | `/lightStation/list.html` → `audit.html` | `LightStationController` | 审核服务商提交的电站基本信息、方案配置(SKU+数量)、逆变器配置 | `WAIT_AUDIT` → `WAIT_ORDER`(普通模式) / `WAIT_THIRD_AUDIT`(顶好/广发模式) |
| 技术审核(第二审) | `/lightStationSkill/list.html` → `audit.html` | `LightStationSkillController` | 审核完工确认资料：组件照片、逆变器SN、倾角、并网资料等 | `WAIT_TECH_CHECK` → `WAIT_UPLOAD_GRID_INFO` 或 `WAIT_FIRST_AUDIT` |
| 商务审核(第三审) | `/lightStationBusiness/list.html` → `audit.html` | `LightStationBusinessController` | 审核商务验收资料：合同签署状态、并网信息、发电数据等 | `WAIT_FIRST_AUDIT` → `ENABLE`(已完成) |

> **重要发现**：所谓"三审"实际上是跨不同阶段的审核：
> - **方案审核**：电站创建后，审核业主信息和方案配置（施工前）
> - **技术审核**：完工确认后，审核施工质量和并网资料（施工后）
> - **商务审核**：技术审核通过后，审核商务验收和合同签署（并网前）

---

## 2. 方案审核（第一审）

### 2.1 前端页面
- **Controller**: `LightStationController` (`/lightStation`)
- **API 列表接口**: `doList.do` (通过 `lightStationService.queryBy` 查询)
- **审核页面**: `audit.html`
- **审核通过接口**: `POST /lightStation/auditOk.do`
- **审核驳回接口**: `POST /lightStation/auditFail.do`
- **权限**: `lightStation:audit`
- **查询条件**:
  - 电站编码(stationCode)、电站名称(name)
  - 状态(status): `WAIT_AUDIT`(待审核)、`AUDIT_REJECT`(驳回)
  - 服务商名称(spName)、分中心编码(subCenterCode)
  - 省份/市/区(provinceId/cityId/regionId)
  - 模式(mode)、电站类型(stationType)
  - 提交时间范围、审核时间范围
  - 合同状态(contractStatus)

### 2.2 后端逻辑
- **Service 方法**: `LightStationServiceImpl.auditInfoOk()` / `auditInfoRejection()`
- **核心校验逻辑**:
  1. 检查电站状态必须为 `WAIT_AUDIT`
  2. 检查电站不能处于暂停状态(PAUSED)
  3. 检查电站不能已撤回(INIT)
  4. 检查逆变器是否已配置（方案配置表）
  5. 校验不同模式的前置条件：
     - 顶好(DH)模式：检查商机是否审核通过
     - 广发(GF)模式：检查商机是否审核通过
- **状态变更**:
  - 普通模式/越秀(YX): `WAIT_AUDIT` → `WAIT_ORDER`(待下单)
  - 顶好(DH)/广发(GF)/华融EPC(HRFLC_EPC): `WAIT_AUDIT` → `WAIT_THIRD_AUDIT`(待三方审核)
- **审核类型**: `LightStationAudit.AuditTypeEnum.PLAN_AUDIT`

### 2.3 数据库
- **主要表**: `light_station`(电站表)、`light_station_audit`(审核记录表)、`light_station_plan_config`(方案配置表)
- **字段变更**:
  - `light_station.status`: WAIT_AUDIT → WAIT_ORDER/WAIT_THIRD_AUDIT
  - `light_station.contract_status`: INIT → WAIT_CONFIRM
  - `light_station_audit`: 新增审核记录(auditType=PLAN_AUDIT, auditStatus=AUDIT_OK)

---

## 3. 技术审核（第二审）

### 3.1 前端页面
- **Controller**: `LightStationSkillController` (`/lightStationSkill`)
- **API 列表接口**: `doList.do` (通过 `lightStationService.querySkillBy` 查询)
- **审核页面**: `audit.html`
- **审核通过接口**: `POST /lightStationSkill/materialAuditOk.do`
- **审核驳回接口**: `POST /lightStationSkill/materialAuditFail.do`
- **权限**: `lightStationSkill:audit`
- **查询条件**:
  - 电站编码、电站名称、服务商名称
  - 状态(status): `WAIT_TECH_CHECK`(待技术审核)
  - 审核状态(auditStatus)
  - 分中心编码、省份/市/区
  - 模式(mode)、电站类型
  - 提交时间范围、审核时间范围
  - 审核人(auditBy)
  - 光e宝标识(gybFlag)
  - 派单信息(dispatchType, taskType, dispatchAt)
  - 商务状态(businessStatus)

### 3.2 后端逻辑
- **Service 方法**: `CompleteConfirmServiceImpl.auditOk()` / `auditReject()`
  - `auditType` 参数: `LightStationAudit.AuditTypeEnum.TECH_CHECK`
- **核心校验逻辑** (`techCheckPassed` 方法):
  1. 检查电站状态必须为 `WAIT_TECH_CHECK`
  2. 检查电站不能处于冻结状态
  3. 根据电站模式(Mode)执行不同逻辑：
     - **越秀(YX)模式**: 
       - 推送越秀完工信息
       - 更新越秀合同状态
     - **其他模式**(HR/EPC/ZH/CHD_EPC/DH/CQ_GDT/GF/HRFLC_EPC):
       - 执行 `techPassedUpdateLightStation` 更新电站状态
       - 检查是否已上传并网信息
       - 如已上传 → `WAIT_FIRST_AUDIT`(待商务审核)
       - 如未上传 → `WAIT_UPLOAD_GRID_INFO`(待提交并网资料)
  4. 广发(GF)模式：更新完工进件状态为 WAIT_PUSH
  5. 开启线下验收流程（如果需要）
  6. 创建业主建户队列
  7. 如果状态变为 `WAIT_FIRST_AUDIT`，则：
     - 传递光E宝(sendToGYX)
     - 传递银联(sendToYL)
  8. 如果是 ENABLE 状态（技术审核直接完成）：
     - 设置电站完成时间(finishAt)
     - 执行电站完成后步骤(dealAfterCompleted)
- **状态变更**:
  - 有并网资料: `WAIT_TECH_CHECK` → `WAIT_FIRST_AUDIT`(待商务审核)
  - 无并网资料: `WAIT_TECH_CHECK` → `WAIT_UPLOAD_GRID_INFO`(待提交并网资料)
  - 直接完成: `WAIT_TECH_CHECK` → `ENABLE`(已完成)
  - 驳回: `WAIT_TECH_CHECK` → `TECH_CHECK_REJECT`(技术审核驳回)
- **审核记录**: 创建/更新 `LightStationAudit`(auditType=TECH_CHECK)

### 3.3 数据库
- **主要表**: 
  - `light_station`(电站表)
  - `light_station_audit`(审核记录表)
  - `light_station_confirm_img`(完工确认图片表)
  - `light_station_inverter`(逆变器表)
  - `light_station_plan_config`(方案配置表)
  - `light_grid_cert`(并网证表)
  - `gf_light_station`(广发电站表)
  - `light_station_yuexiu`(越秀电站表)
- **字段变更**:
  - `light_station.status`: WAIT_TECH_CHECK → WAIT_FIRST_AUDIT/WAIT_UPLOAD_GRID_INFO/ENABLE
  - `light_station.business_status`: 通过 BusinessStatusMode 计算
  - `light_station.tech_passed_time`: 设置技术审核通过时间
  - `light_station_audit`: 新增/更新审核记录(auditType=TECH_CHECK)
  - `gf_light_station.complete_status`: 广发模式更新为 WAIT_PUSH

---

## 4. 商务审核（第三审）

### 4.1 前端页面
- **Controller**: `LightStationBusinessController` (`/lightStationBusiness`)
- **API 列表接口**: `doList.do` (通过 `lightStationService.queryBusinessBy` 查询)
- **审核页面**: `audit.html`
- **详情页面**: `detail.html` / `detailNew.html`
- **审核通过接口**: `POST /lightStationBusiness/materialAuditOk.do`
- **审核驳回接口**: `POST /lightStationBusiness/materialAuditFail.do`
- **权限**: `lightStationBusiness:audit`
- **查询条件**:
  - 电站编码、电站名称、服务商名称
  - 状态(status)、审核状态(auditStatus)
  - 分中心编码、省份/市/区
  - 模式(mode)、电站类型
  - 项目公司(projectCompanyId)
  - 提交时间、审核时间、更新时间范围
  - 光e宝标识(gybFlag)
  - 合同状态(contractStatus)
  - 派单信息(dispatchType, taskType)
  - 商务状态(businessStatus)
  - 验收人(acceptByName)

### 4.2 后端逻辑
- **Service 方法**: `CompleteConfirmServiceImpl.auditOk()` / `auditReject()`
  - `auditType` 参数: `LightStationAudit.AuditTypeEnum.WAIT_FIRST_AUDIT`
- **核心校验逻辑** (`businessCheck` 方法):
  1. 检查商务状态必须为 `WAIT_BUSINESS_AUDIT`
  2. 检查电站不能处于冻结状态
  3. 检查首次连续三天发电时间必须存在(`firstThreePowerAt`)
  4. **合同签署校验**:
     - 越秀(YX)模式: 检查装机补充协议或主合同是否已签署
     - 华融(HR)模式(2024-10-21后创建): 检查信息授权协议是否签署
     - 其他模式: 检查所有合同是否已签署
  5. 检查是否存在正在进行的信息变更流程
- **审核通过后逻辑** (`businessCheckPassed` + `updateLightStationForBusiness`):
  1. 更新电站状态为 `ENABLE`(已完成)
  2. 设置电站完成时间 `finishAt`
  3. 更新方案配置状态为 `ACCEPTANCE`(已验收)
  4. 保存商务审核快照(`businessAuditSnapShotService`)
  5. 执行电站完成后步骤(`dealAfterCompleted`):
     - 上收入记录
     - 公司备案/创建能源币
     - 生成服务费请款采购单
     - 创建服务商电站电费补贴
     - 创建租金队列(公共租赁/整村推进)
     - 生成核验记录
     - 同步中核电站数据
  6. 更新小顺管家逻辑
  7. 发送电站完成奖励发放消息
  8. 自动划转运维商
- **状态变更**:
  - `WAIT_FIRST_AUDIT` → `ENABLE`(已完成)
  - 驳回: `WAIT_FIRST_AUDIT` → `FIRST_AUDIT_REJECT`(商务审核驳回)

### 4.3 数据库
- **主要表**:
  - `light_station`(电站表)
  - `light_station_audit`(审核记录表)
  - `light_station_plan_config`(方案配置表)
  - `light_station_contract_record`(合同记录表)
  - `light_station_yuexiu`(越秀电站表)
  - `business_audit_snapshot`(商务审核快照表)
  - `light_station_operate_log`(操作日志表)
- **字段变更**:
  - `light_station.status`: WAIT_FIRST_AUDIT → ENABLE
  - `light_station.business_status`: WAIT_BUSINESS_AUDIT → BUSINESS_AUDIT_APPROVAL
  - `light_station.finish_at`: 设置完成时间
  - `light_station_plan_config.status`: ACCEPTANCE
  - `light_station_plan_config.acceptance_confirm_quantity`: 验收确认数量
  - `light_station_plan_config.acceptance_confirm_at`: 验收确认时间
  - `light_station_audit`: 新增/更新审核记录(auditType=WAIT_FIRST_AUDIT)

---

## 5. 完整流程图

```
电站创建(INIT)
    │
    ▼
服务商提交方案 → [待审核 WAIT_AUDIT]
    │
    ├─── 方案审核(第一审) ───┤
    │   审核人: 分中心/服务商管理员
    │   审核内容: 业主信息、方案配置、逆变器配置
    │   权限: lightStation:audit
    │   
    ├── 通过 ──→ [待下单 WAIT_ORDER] 或 [待三方审核 WAIT_THIRD_AUDIT]
    │               │
    │               ▼
    │           下单 → 施工中 ROADWORKING
    │               │
    │               ▼
    │           完工确认 → [完工确认审核 COMPLETE_WAIT_AUDIT]
    │               │
    │               ├── 分中心完工审核通过 ──→ [待技术审核 WAIT_TECH_CHECK]
    │               │
    │               └── 驳回 ──→ [完工确认审核驳回 COMPLETE_AUDIT_REJECT]
    │
    └── 驳回 ──→ [驳回 AUDIT_REJECT] → 服务商修改后重新提交


[待技术审核 WAIT_TECH_CHECK]
    │
    ├─── 技术审核(第二审) ───┤
    │   审核人: 总部技术人员
    │   审核内容: 完工确认图片、逆变器SN、倾角、并网资料
    │   权限: lightStationSkill:audit
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
    └── 驳回 ──→ [技术审核驳回 TECH_CHECK_REJECT] → 服务商整改后重新提交


[待商务审核 WAIT_FIRST_AUDIT]
    │
    ├─── 商务审核(第三审) ───┤
    │   审核人: 总部商务人员
    │   审核内容: 合同签署状态、发电数据、商务验收资料
    │   前置条件: firstThreePowerAt 不为空(连续三天发电)
    │   权限: lightStationBusiness:audit
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
    └── 驳回 ──→ [商务审核驳回 FIRST_AUDIT_REJECT] → 服务商整改后重新提交
```

---

## 6. 关键发现

### 6.1 审核表设计
- **`light_station_audit`** 是统一的审核记录表，通过 `audit_type` 区分不同审核节点：
  - `PLAN_AUDIT` - 电站方案审核
  - `TECH_CHECK` - 技术审核
  - `WAIT_FIRST_AUDIT` - 商务审核
  - `COMPLETE_WAIT_AUDIT` - 完工确认审核（分中心）
  - `OFF_LINE_AUDIT` - 线下验收
  - `SP_PLAN_AUDIT` - 服务商方案审核
  - `SP_TECH_CHECK` - 服务商技术审核
  - `SP_WAIT_FIRST_AUDIT` - 服务商商务审核

- 审核状态: `WAIT_AUDIT`(待审核)、`AUDIT_OK`(通过)、`AUDIT_REJECT`(驳回)

### 6.2 电站状态枚举 (LightStation.Status)
```
INIT → 待提交审核
WAIT_AUDIT → 待方案审核
WAIT_THIRD_AUDIT → 待三方审核(顶好/广发)
AUDIT_REJECT → 方案审核驳回
WAIT_CONFIG → 审核完成待配方案
WAIT_ORDER → 待下单
ROADWORKING → 施工中
ROADWORK_CONFIRM → 施工信息待确认
COMPLETE_WAIT_AUDIT → 完工确认审核
COMPLETE_AUDIT_REJECT → 完工确认审核驳回
WAIT_TECH_CHECK → 待技术审核
TECH_CHECK_REJECT → 技术审核驳回
WAIT_OFF_LINE_CHECK → 待线下验收
WAIT_UPLOAD_GRID_INFO → 待提交并网验收资料
WAIT_FIRST_AUDIT → 待商务审核
FIRST_AUDIT_REJECT → 商务审核驳回
OFF_LINE_CHECK_REJECT → 现场验收驳回
ENABLE → 已完成
DISABLE → 删除
STOP → 已终止
REPURCHASE → 已回购
```

### 6.3 商务状态枚举 (LightStation.BusinessStatus)
```
WAIT_UPLOAD_GRID_INFO → 待提交并网验收资料
BUSINESS_INFO_UPLOADED → 已提交并网资料
WAIT_BUSINESS_AUDIT → 待商务验收
BUSINESS_AUDIT_REJECT → 商务验收驳回
BUSINESS_AUDIT_APPROVAL → 商务验收通过
```

### 6.4 关键业务规则
1. **暂停保护**: 所有审核节点都检查电站不能处于暂停状态(PAUSED)
2. **冻结保护**: 技术审核和商务审核检查电站不能处于冻结状态
3. **撤回保护**: 方案审核检查电站不能已撤回(INIT)
4. **防重复提交**: 审核接口使用 `@RepeatSubmit` 注解防止重复提交（间隔60秒）
5. **合同签署**: 商务审核必须检查所有合同是否已签署完成
6. **发电校验**: 商务审核要求电站必须有连续三天发电记录
7. **多模式支持**: 不同模式(YX/HR/DH/GF/HRFLC_EPC等)有不同的审核流程分支
8. **审核快照**: 商务审核通过后会保存快照到 `business_audit_snapshot` 表

### 6.5 驳回后处理
- 技术审核驳回：保存驳回图片到 Redis(`station:tech:reject:images:{stationId}`)，服务商整改后可重新提交
- 商务审核驳回：保存驳回图片到 Redis(`station:business:reject:images:{stationId}`)，同时记录驳回类型(rejectionType)
- 所有驳回都通过 `LightStationOperateLog.RejectionTypeEnum` 枚举定义驳回类型
- 驳回后电站状态变更为对应的 REJECT 状态，服务商可修改后重新提交进入待审核状态

### 6.6 审核权限体系
| 审核节点 | 权限标识 | 审核角色 |
|---------|---------|---------|
| 方案审核 | `lightStation:audit` | 分中心/服务商管理员 |
| 完工确认审核 | (ReviewMaterialController) | 分中心人员 |
| 技术审核 | `lightStationSkill:audit` | 总部技术人员 |
| 商务审核 | `lightStationBusiness:audit` | 总部商务人员 |

### 6.7 关键 Service 汇总
| Service | 职责 |
|---------|------|
| `LightStationServiceImpl` | 方案审核(auditInfoOk/auditInfoRejection) |
| `CompleteConfirmServiceImpl` | 技术审核+商务审核(auditOk/auditReject) |
| `LightStationAuditServiceImpl` | 审核记录管理(updateOrCreateAudit) |
| `BusinessAuditSnapShotService` | 商务审核快照保存 |
| `LightStationService` | 电站状态查询(queryBy/querySkillBy/queryBusinessBy) |
