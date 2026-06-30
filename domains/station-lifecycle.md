# 电站生命周期全链路状态流转

更新时间: 2026-05-24

## 一、双状态字段设计

电站同时维护两个状态字段，并行推进、互不阻塞：

### 主状态 (status) — LightStation.Status 枚举

| 状态值 | 含义 | 阶段 |
|--------|------|------|
| INIT | 待提交审核 | 录单阶段 |
| WAIT_AUDIT | 待审核 | 方案审核 |
| WAIT_THIRD_AUDIT | 待三方审核 | 资方投件审核 |
| AUDIT_REJECT | 驳回 | 审核驳回 |
| WAIT_CONFIG | 审核完成待配方案 | 方案配置 |
| WAIT_ORDER | 待下单 | 备货前 |
| ROADWORKING | 施工中 | 下单后 |
| ROADWORK_CONFIRM | 施工信息待确认 | 施工确认 |
| ROADWORK_REJECT | 施工信息驳回 | 施工驳回 |
| COMPLETE_WAIT_AUDIT | 完工确认审核 | 完工审核 |
| COMPLETE_AUDIT_REJECT | 完工确认审核驳回 | 完工驳回 |
| WAIT_TECH_CHECK | 待技术审核 | 技术审核 |
| TECH_CHECK_REJECT | 技术审核驳回 | 技术驳回 |
| WAIT_OFF_LINE_CHECK | 待线下验收 | 线下验收（可选） |
| OFF_LINE_CHECK_REJECT | 线下验收驳回 | 线下驳回 |
| WAIT_UPLOAD_GRID_INFO | 待提交并网验收资料 | 并网资料 |
| WAIT_FIRST_AUDIT | 待商务审核 | 商务审核 |
| FIRST_AUDIT_REJECT | 商务审核驳回 | 商务驳回 |
| ENABLE | 已完成 | 并网启用 ✅ |
| DISABLE | 删除 | 终止 |
| STOP | 已终止 | 终止 |
| REPURCHASE | 已回购 | 资方回购 |
| SUSPENDING | 暂停 | 信息变更中冻结 |
- **⚠️ 2026-05-29**: 龙龙在 `20260310_longlong_station_pause_status_fix` 分支移除了 LightStation 中的暂停状态枚举（commit 9b3ca19）。SUSPENDING 状态从枚举中删除，具体替代方案待确认。

### 商务状态 (businessStatus) — 独立并行字段

| 状态值 | 含义 |
|--------|------|
| WAIT_UPLOAD_GRID_INFO | 待上传并网资料 |
| BUSINESS_INFO_UPLOADED | 已上传并网资料 |
| WAIT_BUSINESS_AUDIT | 待商务审核 |
| BUSINESS_AUDIT_APPROVAL | 商务审核通过 |
| BUSINESS_AUDIT_REJECT | 商务审核驳回 |

### 核心调度器

**`BusinessStatusMode.java`** — 同时控制 status 和 businessStatus 的联动，是双状态流转的总调度器。

---

## 二、完整状态流转详解

### [节点1] 创建电站 → INIT（待提交审核）

**触发入口**:
- 各模式 StationModel 的 register 方法：
  - `LightOrdinaryStationModel.registerOrdinaryStation()` → `POST /light/station/register`
  - `LightHouseholdStationModel.registerHouseholdStation()`
  - `LightChdStationModel.registerChdStation()`
  - `LightWholeVillageStationModel.submitWholeVillageStation()`
  - **EPC模式跳过INIT**: `LightEpcStationModel.registerEpcStation()` → 直接设为 WAIT_AUDIT
- 各 HandleStrategy: `OrdinaryStationHandleStrategy`, `YxStationHandleStrategy`, `DhStationHandleStrategy`, `GfStationHandleStrategy`, `EpcStationHandleStrategy`
- `CacheStationServiceImpl` 的 confirmAndSubmit 方法（草稿保存）

**前置校验**:
- 业主姓名、联系方式、身份证号必填（校验合法性）
- 省市区地址必填
- 业主信息图片（userImgList）必填
- 银行账户信息必填
- 服务商信息存在且有效

**状态变更**:
- `status` = `INIT`（EPC模式直接到 WAIT_AUDIT）
- `contractStatus` = `WAIT_CONFIRM`
- `signStatus` = `NO_SIGN`
- `stopStatus` = `INIT`
- `yuexiuStatus` = `INIT`
- `provideMaterial` = `ALL`

**副作用（创建大量关联记录）**:
- 创建电站主记录 `light_station`
- 创建草稿记录 `light_staging_records`
- 创建合同记录 `light_station_contract_record`
- 创建审核记录 `light_station_audit`（状态 WAIT_AUDIT）
- 创建方案配置 `light_station_plan_config`
- 保存业主信息图片 `light_station_confirm_img`
- 记录操作日志 `light_station_operate_log`
- 创建电站银行卡 `light_station_bank`
- 创建保姆/运维用户 `light_station_nanny_user`（如有）

**相关表**: `light_station`, `light_staging_records`, `light_station_contract_record`, `light_station_audit`, `light_station_plan_config`, `light_station_confirm_img`, `light_station_operate_log`, `light_station_bank`, `light_station_nanny_user`

---

### [节点2] INIT → WAIT_AUDIT（提交方案审核）

**触发入口**:
- 各 HandleStrategy 的 `updateStation` / 提交审核方法
- 从 INIT 状态主动提交审核

**前置校验**:
- 电站状态为 INIT
- 资料完整性校验

**状态变更**:
- `status` = `WAIT_AUDIT`

**副作用**:
- 更新电站状态
- 记录操作日志

**相关表**: `light_station`, `light_station_operate_log`

---

### [节点3] WAIT_AUDIT → INIT（撤回）

**触发入口**:
- 各 HandleStrategy 的 `withdrawal` 方法
- 服务商在审核前撤回修改

**前置校验**:
- 电站状态为 WAIT_AUDIT（才能撤回回到INIT）
- INIT 状态下无法审核（auditInfoReject 中校验）

**状态变更**:
- `status` = `INIT`
- `auditReason` 清空

**副作用**:
- 更新电站状态
- 记录操作日志

---

### [节点4] WAIT_AUDIT → WAIT_THIRD_AUDIT（进入三方资方审核）

**触发入口**:
- `LightStationServiceImpl.auditInfoOk()` → `POST /light/station/auditInfoOk`
- DH模式: 商机审核通过后自动流转
- GF模式: 商机审核通过后自动流转

**前置校验**:
- 电站状态为 WAIT_AUDIT
- DH模式: 商机状态为 `DhBusinessOpportunity.BusinessStatus.SUCCESS`
- GF模式: 商机状态为 `GfBusinessOpportunity.BusinessStatus.SUCCESS`

**状态变更**:
- `status` = `WAIT_THIRD_AUDIT`
- `contractStatus` = `WAIT_CONFIRM`
- `auditAt` = 当前时间

**副作用**:
- 更新电站状态
- 更新DH/GF电站的首次状态为 `WAIT_PUSH`
- 更新 DH/GF 商机表状态
- 创建审核记录
- 更新方案信息
- HRFLC_EPC模式: 同步PV信息

**相关表**: `light_station`, `light_station_audit`, `light_station_plan_config`, `dh_light_station`, `gf_light_station`, `dh_business_opportunity`, `gf_business_opportunity`

---

### [节点5] WAIT_THIRD_AUDIT → WAIT_CONFIG（三方审核通过，待配方案）

**触发入口**:
- `DhQueryInputPieceStateModel.dealFirstInputPieceResponseInfo()` — DH投件结果回调
- `GfQueryInputPieceStateModel` — GF投件结果回调

**前置校验**:
- 电站状态为 WAIT_THIRD_AUDIT
- 投件审核状态为成功（FirstStatus.SUCCESS）

**状态变更**:
- `status` = `WAIT_CONFIG`

**副作用**:
- 更新电站状态
- 更新商务机会状态
- 记录操作日志

**相关表**: `light_station`, `dh_business_opportunity`, `gf_business_opportunity`, `light_station_operate_log`

---

### [节点6] WAIT_CONFIG → WAIT_ORDER（方案配置完成）

**触发入口**:
- 方案配置完成后，通过审核确认操作触发
- `LightConfirmOrderServiceImpl` 待下单审核确认

**前置校验**:
- 方案配置完成
- 合同状态确认

**状态变更**:
- `status` = `WAIT_ORDER`

**副作用**:
- 更新电站状态
- 确认方案配置

**相关表**: `light_station`, `light_station_plan_config`

---

### [节点7] WAIT_AUDIT / WAIT_ORDER → AUDIT_REJECT（方案审核驳回）

**触发入口**:
- `LightStationServiceImpl.auditInfoReject()` → `POST /light/station/auditInfoReject`
- `LightStationServiceImpl.auditInfoRejection()` → `POST /light/station/auditInfoRejection`（带驳回类型）

**前置校验**:
- 电站状态为 WAIT_AUDIT 或 WAIT_ORDER（且合同状态在特定列表中）
- 驳回类型不能为空

**状态变更**:
- `status` = `AUDIT_REJECT`
- `auditAt` = 当前时间
- `auditBy` = 操作人
- `auditReason` = 驳回原因
- `rejectionType` = 拒绝类型（PROPERTY_DOCUMENT_ISSUE 等8种）

**副作用**:
- 更新电站状态
- 创建操作日志（标注"业主信息审核"或"待下单节点驳回"）
- 记录驳回类型和描述

**拒绝类型**（仅原因分类，不改变状态）:
| 类型 | 含义 |
|------|------|
| PROPERTY_DOCUMENT_ISSUE | 房屋证明/辅助材料问题 |
| DRAWING_DESIGN_ISSUE | 图纸标注及设计问题 |
| SHADING_ISSUE | 遮挡问题 |
| PHOTO_UPLOAD_ISSUE | 拍照、图片上传问题 |
| EQUIPMENT_SELECTION_ISSUE | 设备选型问题 |
| SYSTEM_INFO_ENTRY_ISSUE | 系统信息录入问题 |
| LOCATION_SELECTION_ISSUE | 房屋选址问题 |

---

### [节点8] WAIT_ORDER → ROADWORKING（下单→施工中）

**触发入口**:
- `LightMakeOrderServiceImpl.confirmInbound()` → `POST /light/makeOrder/confirmInbound`
- `LightMakeOrderServiceImpl.create()` — 备货申请下单

**前置校验**:
- 电站状态必须为 WAIT_ORDER
- 合同状态必须 FINISHED（已签订完成）
- 服务商不能处于退商状态
- 同一电站不能重复创建主料备货单
- 共建模式: 共建费合同 + 专项合同必须都签完
- 顶好模式: 首次进件必须审核通过

**状态变更**:
- `status` = `ROADWORKING`
- `orderAt` = 当前时间（下单时间）

**副作用（核心供应链触发点）**:
- 创建主料备货单 `light_make_order`（初始 TO_BE_SUBMITTED）
- 如有辅料（FourItemFlag=YES），创建辅料备货单 `light_auxiliary_make_order`
- 创建待领用领用单 `light_use_order`（UseStatus=PENDING, UseNode=BEFORE_COMPLETE）
  - 领用单号格式: `B` + 备货单号 + 序号（如 BLS20260524000001-1）
- 记录操作日志："备货申请下单"

**相关表**: `light_station`, `light_make_order`, `light_auxiliary_make_order`, `light_use_order`, `light_station_operate_log`

详见 `domains/order-dispatch-delivery.md`

---

### [节点9] WAIT_ORDER → AUDIT_REJECT（待下单驳回）

**触发入口**:
- `LightConfirmOrderServiceImpl.quitOrder()` → `POST /light/confirmOrder/quitOrder`
- `LightStationServiceImpl.auditInfoRejection()` 中 WAIT_ORDER + 特定合同状态

**前置校验**:
- 电站状态为 WAIT_ORDER
- 合同状态在 contractStatusList 中

**状态变更**:
- `status` = `AUDIT_REJECT`（退回待审核）

**副作用**:
- 更新待下单确认记录状态
- 更新备货单状态为 RETURNED
- 记录操作日志

---

### [节点10] ROADWORKING → ROADWORK_CONFIRM（施工完成→待确认）

**触发入口**:
- `LightWorkOrderServiceImpl.completeConfirm()` → `POST /light/workOrder/completeConfirm`

**前置校验**:
- 电站状态不为 TECH_CHECK_REJECT 或 WAIT_TECH_CHECK（非整改单）
- 必填图片组校验（required=1的必填项）
- 实际用料数量不能超过方案数量
- 整改单提交时复用原状态

**状态变更**:
- `status` = `ROADWORK_CONFIRM`

**副作用**:
- 更新方案配置完成状态 `light_station_plan_config`（status=COMPLETE）
- 更新派工单审核状态为 WAIT_SP_AUDIT
- 更新工单施工状态为 ROADWORK_CONFIRM
- 创建操作日志

**相关表**: `light_station`, `light_station_plan_config`, `light_work_order`, `light_station_complete_img`, `light_work_order_operate_log`

---

### [节点11] ROADWORK_CONFIRM → ROADWORK_REJECT（施工信息驳回）

**触发入口**:
- `LightStationCompleteImgServiceImpl.roadWorkReject()` → `POST /light/completeImg/roadWorkReject`

**前置校验**:
- 电站状态为 ROADWORK_CONFIRM

**状态变更**:
- `status` = `ROADWORK_REJECT`

**副作用**:
- 更新电站状态
- 记录操作日志
- 通知施工队重新提交

---

### [节点12] ROADWORK_CONFIRM → COMPLETE_WAIT_AUDIT（完工确认审核）

**触发入口**:
- `CompleteConfirmServiceImpl.submitCompleteConfirm()` → `POST /light/completeConfirm/submitCompleteImg`
- `LightStationCompleteImgServiceImpl.completePro()` → `POST /light/completeImg/completePro`

**前置校验**:
- 图片必填项校验（完工确认图片组）
- 组件数量与方案数量校验（OCR识别数量比对）
- 逆变器信息校验
- 备案编码校验（特定模式）
- 无待审核的方案变更申请

**状态变更**:
- `status` = `COMPLETE_WAIT_AUDIT`
- `completeApplyAt` = 当前时间
- 更新组件数量、倾角、配电箱等信息
- 更新并网证URL、载荷报告图片

**副作用（信息大量更新）**:
- 更新电站状态
- 更新方案配置为 COMPLETE 状态
- 创建技术审核待审核记录 `light_station_audit`
- 保存完工图片 `light_station_complete_img`
- 调用地理编码服务获取经纬度
- 逆变器变更OCR识别
- 组件倾角变更OCR识别
- 备案证OCR识别
- 更新银行卡照片

**相关表**: `light_station`, `light_station_plan_config`, `light_station_audit`, `light_station_complete_img`, `light_station_confirm_img`, `light_station_bank`, `light_work_order`

---

### [节点13] COMPLETE_WAIT_AUDIT → ROADWORKING / COMPLETE_AUDIT_REJECT（撤回）

**触发入口**:
- `CompleteConfirmServiceImpl.withdrawalOfComplete()` → `POST /light/completeConfirm/withdrawalOfComplete`

**前置校验**:
- 电站状态为 COMPLETE_WAIT_AUDIT
- 未派工（orderTeamId 为空）

**状态变更**:
- 有历史驳回记录: `status` = `COMPLETE_AUDIT_REJECT`
- 无历史驳回记录: `status` = `ROADWORKING`
- `expectedStatus` = `COMPLETE_WAIT_AUDIT`

**副作用**:
- 乐观锁更新（updateStatusWithCheck）
- Redis 存入撤回标记
- 创建操作日志

---

### [节点14] COMPLETE_WAIT_AUDIT / COMPLETE_AUDIT_REJECT → WAIT_TECH_CHECK（完工审核通过→技术审核）

**触发入口**:
- `LightStationCompleteImgServiceImpl.editConfirmImg()` → `POST /light/completeImg/editConfirmImg`
- `CompleteConfirmServiceImpl.stationCompletedPassed()` L3482

**前置校验**:
- 图片必填项校验
- 组件数量与方案数量校验
- 逆变器信息校验
- 备案编码校验
- 无待审核的方案变更申请

**状态变更**:
- `status` = `WAIT_TECH_CHECK`
- `businessStatus` = `WAIT_UPLOAD_GRID_INFO`
- `completeAt` = 当前时间

**副作用**:
- 更新电站状态
- 创建技术审核记录 `light_station_audit`（状态 WAIT_AUDIT）
- 更新整改工单状态（如有）
- 保存图片变更
- 更新银行卡照片

**运维商自动划转**: `LightOpAuthorityZoneServiceImpl.autoTransferStationOp()`
1. 获取电站 regionId
2. 查询该区域下已中标运维区域（status=ENABLE, isInvestment=0）
3. 取最新一条，获取 memberId（运维商ID）
4. 更新电站 opMemberId 和 opTime

**相关表**: `light_station`, `light_station_audit`, `light_station_complete_img`, `light_station_confirm_img`, `light_station_bank`, `light_work_order`, `light_op_authority_zone`

---

### [节点15] TECH_CHECK_REJECT → WAIT_TECH_CHECK（技术驳回后重新提交）

**触发入口**:
- `CompleteConfirmServiceImpl.updateStationByEdit()` → `POST /light/completeConfirm/updateStationByEdit`

**前置校验**:
- 电站状态为 TECH_CHECK_REJECT
- 图片必填项校验

**状态变更**:
- `status` = `WAIT_TECH_CHECK`（原状态 TECH_CHECK_REJECT）
- `status` = `COMPLETE_WAIT_AUDIT`（原状态 ROADWORK_REJECT 或 COMPLETE_AUDIT_REJECT）

**副作用**:
- 更新电站状态
- 更新方案配置
- 更新审核记录
- 记录操作日志
- 如果技术审核驳回且勾选容量/房型变化，商务审核状态可能回退

---

### [节点16] 技术审核通过 → 双状态联动（BusinessStatusMode.handleTechAuditPass）

**核心调度器**: `BusinessStatusMode.java`

| 当前商务状态 | 主状态变为 | 商务状态变为 |
|-------------|-----------|-------------|
| WAIT_UPLOAD_GRID_INFO | WAIT_UPLOAD_GRID_INFO | 不变 |
| WAIT_BUSINESS_AUDIT | WAIT_FIRST_AUDIT | 不变 |
| BUSINESS_INFO_UPLOADED | WAIT_FIRST_AUDIT | WAIT_BUSINESS_AUDIT |
| **BUSINESS_AUDIT_APPROVAL** | **ENABLE** ✅ | 不变 |

**快照校验**: 技术审核通过时，对比商务审核快照中的屋顶类型和装机容量。不一致则回退商务审核状态为 WAIT_BUSINESS_AUDIT。

**线下验收分支**: 如果 `offLineChoose = YES`，主状态变为 WAIT_OFF_LINE_CHECK（而非直接ENABLE）

---

### [节点17] 技术审核驳回 → 商务状态联动（BusinessStatusMode.handleTechReject*）

**容量发生变化（changeRoofOrHouseType=YES）— 商务状态回退**:

| 原商务状态 | 驳回后 |
|-----------|--------|
| BUSINESS_AUDIT_APPROVAL | BUSINESS_INFO_UPLOADED |
| WAIT_BUSINESS_AUDIT | BUSINESS_INFO_UPLOADED（撤销派单） |
| WAIT_UPLOAD_GRID_INFO | 不变 |
| BUSINESS_INFO_UPLOADED | 不变 |
| BUSINESS_AUDIT_REJECT | 不变 |

**容量未发生变化（changeRoofOrHouseType=NO）— 商务状态不回退**:

| 原商务状态 | 驳回后 |
|-----------|--------|
| WAIT_BUSINESS_AUDIT | 不变（商务继续审） |
| BUSINESS_INFO_UPLOADED | WAIT_BUSINESS_AUDIT（主动派单） |
| BUSINESS_AUDIT_APPROVAL | 不变 |

---

### [节点18] 商务审核驳回 → 主状态联动

**触发入口**: `BusinessStatusMode.handleBusinessAudit()` + 驳回
**触发入口**: `CompleteConfirmServiceImpl.rejectAuditBySp()` 服务商驳回

| 技术审核状态 | 主状态变为 |
|-------------|-----------|
| 技术审核已通过 (AUDIT_OK) | FIRST_AUDIT_REJECT |
| 技术审核待审核 (WAIT_AUDIT) | WAIT_TECH_CHECK（打回技术审核） |
| 技术审核已驳回 (AUDIT_REJECT) | TECH_CHECK_REJECT |

**状态变更**: `businessStatus` = `BUSINESS_AUDIT_REJECT`

---

### [节点19] 商务审核通过 → 主状态联动

**触发入口**: `BusinessStatusMode.handleBusinessAudit()` + 通过
**触发入口**: `LightStationServiceImpl.auditInfoOkBySubStaff()` 中审核类型为 WAIT_FIRST_AUDIT

| 技术审核状态 | 主状态变为 |
|-------------|-----------|
| 技术审核已通过 (AUDIT_OK) | **ENABLE** ✅ |
| 技术审核待审核 (WAIT_AUDIT) | WAIT_TECH_CHECK（等技术审完） |
| 技术审核已驳回 (AUDIT_REJECT) | TECH_CHECK_REJECT |

**状态变更**: `businessStatus` = `BUSINESS_AUDIT_APPROVAL`

---

### [节点20] WAIT_TECH_CHECK → WAIT_OFF_LINE_CHECK（开启线下验收）

**触发入口**: `BusinessStatusMode.handleTechAuditPass()` 中 offLineChoose=YES

**前置校验**:
- 技术审核通过
- 开启了线下验收流程

**状态变更**:
- `status` = `WAIT_OFF_LINE_CHECK`
- `offLineStatus` = `OFF_LINE_INIT`

---

### [节点21] WAIT_OFF_LINE_CHECK → ENABLE（线下验收通过→已完成）

**触发入口**: `OffLineStationFlowServiceImpl.passAudit()` → `POST /light/offLine/passAudit`

**前置校验**:
- offLineStatus 在允许操作的状态列表中
- 线下审核报告必填
- 完工合影照片必填

**状态变更**:
- `status` = `ENABLE`
- `offLineStatus` = `FINISHED_OFF_LINE_PROCESS`
- `yuexiuStatus` = `ENABLE`
- `finishAt` = 当前时间

**副作用（电站启用核心动作）**:
- 保存线下审核报告和完工合影
- 创建审核记录
- 调用 `completeConfirmService.dealAfterCompleted()` 处理完成后逻辑
- 发送电站完成奖励发放消息
- 自动划转运维商
- 记录操作日志

**相关表**: `light_station`, `light_station_confirm_img`, `light_station_audit`, `light_station_operate_log`, `light_op_authority_zone`

---

### [节点22] WAIT_OFF_LINE_CHECK → OFF_LINE_CHECK_REJECT（线下验收驳回）

**触发入口**: `OffLineStationFlowServiceImpl.rejectAudit()` → `POST /light/offLine/rejectAudit`

**状态变更**:
- `offLineStatus` = `OFF_LINE_CHECK_REJECT`
- `offLineRejectReason` = 驳回原因
- 商务审核已完成: `status` = `OFF_LINE_CHECK_REJECT`

---

## 三、终止状态流转

### [节点23] 任意有效状态 → DISABLE（删除）

**触发入口**: `LightStationServiceImpl.removeStation()` → `DELETE /light/station/remove`

**状态变更**: `status` = `DISABLE`

**副作用**:
- 所有方案配置设为 DISABLE
- 合同记录设为 DISABLE
- 事务提交

---

### [节点24] 任意有效状态 → STOP（终止）

**触发入口**:
- `LightStopStationServiceImpl.stopedLightStation()` → `POST /light/stopStation/stop`
- `LightStopStationServiceImpl.auditOk()` 终止审核通过

**前置校验**:
- 电站不在终止流程中
- 合同状态校验（HR模式下S开头非SN开头的合同需FINISHED才能直接终止）

**状态变更**:
- `status` = `STOP`
- `stopStatus` = `STOP`
- HR模式S合同非FINISHED: `stopStatus` = `WAIT_SIGN`

**副作用**:
- 合同记录设为 DISABLE
- 越秀模式: 清空投放审查状态
- DH模式: 删除关联信息，电站编码加前缀
- 发送完工前领用逆向消息（MQ）

---

### [节点25] ENABLE → REPURCHASE（已回购）

**触发入口**: `LightStationRepurchaseServiceImpl` 回购审核通过方法（auditPass 等）

**前置校验**:
- 回购审核通过
- 电站已完成

**状态变更**: `status` = `REPURCHASE`

**副作用**:
- 创建回购记录
- 更新相关财务记录

---

### [节点26] 任意有效状态 → SUSPENDING（暂停）

**触发入口**:
- `StationChangeStrategy.process()` — 信息变更中电站冻结
- `LightStationChangePlanToDoJobServiceImpl` 定时任务

**前置校验**:
- 电站信息变更流程进行中
- 当前状态不是 SUSPENDING

**状态变更**: `status` = `SUSPENDING`

**副作用**:
- 创建操作日志（"信息变更中电站为暂时冻结状态，不可审批"）

---

## 四、驳回与整改工单体系

### 驳回时创建整改工单

**代码路径**: `CompleteConfirmServiceImpl.auditReject()` + `LightWorkOrderServiceImpl.createRectifyOrder()`

| 驳回节点 | 工单类型 (docType) | 工单初始状态 |
|---------|-------------------|-------------|
| 完工审核驳回 | COMPLETE_RECTIFY（完工验收整改单） | RECTIFY_WAIT_SUBMIT |
| 技术审核驳回 | TECH_RECTIFY（技术验收整改单） | RECTIFY_WAIT_SUBMIT |

### 整改单逻辑
- 继承主工单的施工队信息（施工队长、团队等）
- 同类型整改单只保留一条（已存在则重置状态，不新建）
- 通过 `parentOrderId` 关联到主工单
- 用户重新修改完工信息提交时，整改单被取消 `cancelRectifyOrders()`
- 技术审核通过时，整改单审核状态被更新为 AUDIT_OK

### 工单状态流转
```
主工单（MAIN）派单 → 施工队承接 → 提交施工信息 → 完工审核
  → 驳回 → 创建整改单（RECTIFY_WAIT_SUBMIT）
  → 施工队修改后重新提交 → 整改单被取消，重新进入审核
  → 通过 → 电站状态流转
```

---

## 五、双状态并行汇总图

```
录单 → INIT → [提交审核] → WAIT_AUDIT
                          ↘ [方案审核通过/资方通过] → WAIT_THIRD_AUDIT → WAIT_CONFIG → WAIT_ORDER
                          ↘ [审核驳回] → AUDIT_REJECT → [重新提交] → WAIT_AUDIT

WAIT_ORDER → [下单] → ROADWORKING → [施工完成] → ROADWORK_CONFIRM
                                           ↘ [驳回] → ROADWORK_REJECT → [重新提交] → ROADWORK_CONFIRM

ROADWORK_CONFIRM → [完工审核] → COMPLETE_WAIT_AUDIT
                                ↘ [撤回] → ROADWORKING / COMPLETE_AUDIT_REJECT

COMPLETE_WAIT_AUDIT → [完工通过] → WAIT_TECH_CHECK + businessStatus=WAIT_UPLOAD_GRID_INFO

                          status（技术审核）                    businessStatus（商务审核）
                          ┌─────────────────────┐              ┌────────────────────────────┐
WAIT_TECH_CHECK ────────→ │ [技术审核通过]       │              │ WAIT_UPLOAD_GRID_INFO      │
                          │ → 根据商务状态联动   │              │   ↓ [提交并网资料]         │
TECH_CHECK_REJECT ←────── │ [技术审核驳回]       │              │ BUSINESS_INFO_UPLOADED     │
                          │ → 商务状态可能回退   │              │   ↓                        │
                          └─────────────────────┘              │ WAIT_BUSINESS_AUDIT        │
                                                               │   ↓ [商务审核]             │
WAIT_FIRST_AUDIT ←──────────────────────────────────────────── │   ↓                        │
  ↓ [商务审核通过]                                             │ BUSINESS_AUDIT_APPROVAL    │
  → 技术也通过 → ENABLE ✅                                     │   ↓                        │
  → 技术未通过 → WAIT_TECH_CHECK / TECH_CHECK_REJECT           │ 与技术审核联动 → ENABLE ✅ │
  ↓ [商务审核驳回]                                             └────────────────────────────┘
  → FIRST_AUDIT_REJECT / WAIT_TECH_CHECK / TECH_CHECK_REJECT

ENABLE ✅ → [线下验收（可选）] → OFF_LINE_CHECK_REJECT
        → [回购] → REPURCHASE
        → [终止] → STOP / DISABLE
        → [信息变更中] → SUSPENDING
```

---

## 六、不同模式的生命周期差异

| 模式 | 创建入口 | 特殊差异 |
|------|---------|---------|
| 普通模式 | LightOrdinaryStationModel | 标准流程 |
| 户用模式 | LightHouseholdStationModel | 标准流程 |
| EPC模式 | LightEpcStationModel | 跳过INIT，直接WAIT_AUDIT |
| 顶好模式 | LightStationDhMode | 需DH商机审核通过，有WAIT_THIRD_AUDIT |
| 广发模式 | LightStationGfMode | 需GF商机审核通过，有WAIT_THIRD_AUDIT |
| 越秀模式 | LightYuexiuStationModel | 有yuexiuStatus独立状态 |
| 整县模式 | LightWholeVillageStationModel | 整县批量流程 |
| 华润模式 | LightChdStationModel | 特殊合同状态校验 |

---

## 七、核心 Service 清单

| 服务 | 文件 | 职责 |
|------|------|------|
| 方案审核 | LightStationServiceImpl.java | auditInfoOk/auditInfoReject |
| 下单 | LightMakeOrderServiceImpl.java | 备货申请下单 |
| 完工确认 | CompleteConfirmServiceImpl.java | 完工审核、双状态调度 |
| 状态调度器 | BusinessStatusMode.java | 技术/商务双状态联动 |
| 施工工单 | LightWorkOrderServiceImpl.java | 工单管理、整改单 |
| 线下验收 | OffLineStationFlowServiceImpl.java | 线下验收流程 |
| 终止 | LightStopStationServiceImpl.java | 电站终止 |
| 回购 | LightStationRepurchaseServiceImpl.java | 电站回购 |
| 运维划转 | LightOpAuthorityZoneServiceImpl.java | 自动划转运维商 |

### 电站终止管理 — 完工后终止策略体系 (代码明确证明, 2026-04-28~05-07)
**来源**: `rrsjk-light-service` → `LightStopStationServiceImpl.java`, `StopToDoJobService.java`, `ReverseBasePolicyIncomeStrategy.java`, `ReverseStationIncomeStrategy.java`, `StationFinalizeStrategy.java`, `LightStopStationTodo.java` (commits 2e693e20/7b57c94a/c2c1009b/367b020f/b8013b36/b0974e3a/dbae1aa/d2ef4974/cb9b43f6/f969b395/4fa6b4c4/9838517d/86029e57, 解钦, 2026-04-28~05-07)
**关联需求**: 电站终止管理功能（多迭代开发）
- **核心架构**: 基于策略模式的电站终止待办系统 (DAG依赖顺序执行)
  - `StopToDoJobService`: 定时任务服务，按DAG依赖顺序执行待办
  - `StopToDoStrategyFactory`: 策略工厂，根据待办类型路由到具体策略
  - 策略类: `StationFinalizeStrategy` (电站完工), `ReverseBasePolicyIncomeStrategy` (回退基础政策收益), `ReverseStationIncomeStrategy` (回退电站收益)
- **关键变更**:
  - 新增 `StationFinalizeStrategy`: 电站完工后终止的策略实现
  - `ReverseBasePolicyIncomeStrategy`: 大幅重构 (183行+), 新增回退政策收益逻辑
  - `ReverseStationIncomeStrategy`: 新增回退电站收益逻辑 (52行+)
  - `LightStopStationTodo`: 新增待办事项实体
  - **状态控制**: 待完工审核的电站不允许申请方案变更
  - **功率字段**: 电站终止管理中的功率由 Integer 改为 BigDecimal
  - **初始状态**: 修复电站终止时的初始状态问题
  - **撤回接口**: 电站终止的撤回接口修复
  - **参数改造**: 电站终止管理所有流程的传参改造
- **旧逻辑移除**: 资产审核通过后，不再自动创建终止待办和冻结电站（从 `LightStopStationServiceImpl` 中移除原有操作日志和冻结逻辑）
- **前端**: `rrsjk-admin-web` → 终止管理列表增加待办事项 (`eaf55080`, 解钦, 2026-05-07)
- **商户通**: `rrsjk-merchant-web` → 电站终止流程接口改造 (`f20e7424`, 解钦, 2026-04-30)
- **证据等级**: 代码明确证明

---

### 超期未完工提醒通知 (代码明确证明, 2026-05-25)
**来源**: `rrsjk-light-message-service` → `OverdueStationNotifyJob.java` (2026-05-25 全量通读)

电站从首次签约到完工（`complete_at IS NULL`）超过 40 天触发自动提醒：
- **40 ≤ days < 50**: 仅通知一次（Redis 去重，Key: `overdue_notify_40:spId:{spId}`, TTL=5 天）
- **50 ≤ days ≤ 60**: 每天通知一次
- **days > 60**: 停止通知

**权限隔离**: 一级商收到所有超期电站，二级商只收到自己建的站
**消息渠道**: APP + MER（商户通）各写一条
**发送方**: 系统自动 (`sendBy="SYSTEM"`)
**调度方式**: Dubbo 暴露 `OverdueStationNotifyJobService.execute()`，外部 XXL-Job 调用

---

## 来源

- `rrsjk-light-service` → `LightStation.java`（状态枚举）
- `rrsjk-light-service` → `CompleteConfirmServiceImpl.java`（审核逻辑）
- `rrsjk-light-service` → `BusinessStatusMode.java`（状态调度器）
- `rrsjk-light-service` → `LightWorkOrderServiceImpl.java`（工单管理）
- `rrsjk-light-service` → `LightMakeOrderServiceImpl.java`（下单逻辑）
- `rrsjk-light-service` → `LightStationServiceImpl.java`（方案审核）
- `rrsjk-light-service` → `OffLineStationFlowServiceImpl.java`（线下验收）
- `rrsjk-light-service` → `LightStopStationServiceImpl.java`（终止）
- `rrsjk-light-service` → `LightStationRepurchaseServiceImpl.java`（回购）
- `rrsjk-light-service` → 各 StationModel 类（不同模式入口）
- 代码扫描日期: 2026-05-24

### 图片验真唯一码重复检查 (TAEI-3098, 2026-05-13)

**来源**: `rrsjk-light-service` → `LightImageVerificationServiceImpl.java` (马斌, commit: 4a2c17ba, 2026-05-13)
**代码明确证明**

**问题**: 图片验真唯一码入库前缺少重复检查，导致唯一键冲突异常（`DuplicateKeyException`）。

**修复**: 在 `insertSelective()` 前增加 `queryLastedByUniqueKey()` 查询，如果已存在相同 `uniqueImageKey` 的记录，直接返回错误"该图片已上传过，请勿重复上传"，阻止重复插入。

```java
LightImageVerification exist = lightImageVerificationMapper.queryLastedByUniqueKey(imageRequest.getUniqueImageKey());
if (exist != null) {
    log.info("{}该图片已上传过，请勿重复上传", imageRequest.getUniqueImageKey());
    return ExecuteResult.newErrorResult("该图片已上传过，请勿重复上传");
}
```

**关联需求**: TAEI-3104 (`light_unionpay_rent` 表 `uni_station_id` 唯一键冲突修复，商轶龙处理) 也涉及类似的唯一键冲突问题。

### 房产证OCR识别功能 (代码明确证明, 2026-05-19~05-26)
**来源**: `rrsjk-admin-web` → `LightStationBusinessController.java` (mabin, commits aa91dd59/d742a926/272c10e9/13302acc/241a78bc, 2026-05-19~05-26)
- 添加房产证AI识别功能，支持在商务审核环节自动识别房产证信息
- 涉及模板: `lightStationBusinessAudit.ftl`, `purchaseSaleContractView.ftl`, `userInfoImageView.ftl`
- 2026-05-26 连续修复OCR状态判断逻辑(3次commit)
- 同时修复日期格式化: givenTime 从 `"2026-5-26"` 改为 `"2026-05-26"`，防止 `DateTimeParseException`
- **证据等级**: 代码明确证明

### 电站转移 (TAEI-3058, 代码明确证明, 2026-05-26~28 追加)
**来源**: `rrsjk-light-service` (德/姜传德 + yumiao/于淼, branch: origin/station-transfer-sub-account-20260525)
- **需求**: 电站支持在不同子账号之间转移，杨越越负责，参与人: 姜廷、姜传德、于淼、杨辉、张硕文、袁睿林
- **核心实体**: `LightStationTransferOrder` — 转单订单
  - 字段: stationId, stationCode, ownerName, installedPower
  - 服务商: spId, spMemberId, spName
  - 转出方: outSubSpMemberId, outSubSpName, outRejectReason（拒绝转出原因）
  - 转入方: inSubSpMemberId, inSubSpName, inRejectReason（拒绝转入原因）
  - 状态: status, transferApplyAt
  - 日志: `LightStationTransferOrderLog` — 转单操作日志表
- **状态机** (5个状态 + 5个动作):
  ```
  发起转单(SUBMIT) → 待确认转出(WAIT_OUT_CONFIRM)
    ├─ 确认转出(CONFIRM_OUT) → 待确认转入(WAIT_IN_CONFIRM)
    │   ├─ 确认转入(CONFIRM_IN) → 转单完成(COMPLETED) ✅
    │   └─ 拒绝转入(REJECT_IN) → 拒绝转入(IN_REJECTED)
    └─ 拒绝转出(REJECT_OUT) → 拒绝转出(OUT_REJECTED)
  ```
- **前置条件**: 电站状态必须在 stationCompleteBefore() 范围内（完工前的电站才能转移）
- **2026-06-09~12 更新** (commits aa781069/15ccb908/7474e39e/14e25ceace, 德/商轶龙):
  - 电站转单派工单转移逻辑修改 (`LightStationTransferOrderServiceImpl` +24行)
  - 电站转单派工单取消功能
  - 服务商直接转出功能
  - 电站转移完工状态校验逻辑修改
  - 修改转出商信息展示 + 新增日志和事务
- **数据表**: `light_station_transfer_order`, `light_station_transfer_order_log`
- **Dubbo 服务**: `LightStationTransferOrderService` (rrsjk-light-api)
  - `create(LightStationTransferOrderCreateDto)` — 创建转单
  - `confirmOut(LightStationTransferOrderConfirmDto)` — 确认转出
  - `confirmIn(LightStationTransferOrderConfirmDto)` — 确认转入
  - `reject(LightStationTransferOrderRejectDto)` — 拒绝转单
- **商户端**: `rrsjk-merchant-web` 新增 `LightStationTransferOrderController` — 转单详情和二级账号查询
- **导出**: `LightStationTransferOrderExcel` 新增
- **最新进展** (2026-05-28):
  - 新增字段 (commit 24129c2)
  - 移除 `@Transactional` 注解 (commit e1ea839)
  - 单元测试新增 (commit 0f53159)
  - 权限和校验完善 (commit 836c5a1)
- **状态**: 开发中（功能分支，未合并到 master）
- **证据等级**: 代码明确证明

### 电站转单功能模块更新 (代码明确证明, 2026-05-28 追加)
**来源**: `rrsjk-light-service` + `rrsjk-merchant-web` (德, branch: origin/station-transfer-sub-account-20260525)
- **LightStationTransferOrder**: 新增字段 (5/28 commits 24129c2)
- **LightStationTransferOrderServiceImpl**: 移除 `@Transactional` 注解 (commit e1ea839)
- **单元测试**: `LightStationTransferOrderServiceImplTest` 新增 (commit 0f53159)
- **商户端接口**: `LightStationTransferOrderController` (rrsjk-merchant-web) 新增转单详情和二级账号查询接口 (commit 1f6c580/da8dc80)
- **导出**: `LightStationTransferOrderExcel` 新增
- **证据等级**: 代码明确证明

### 电站转单持续迭代 (代码明确证明, 2026-05-29~06-01 追加)
**来源**: `rrsjk-light-service` + `rrsjk-merchant-web` (德, branch: origin/station-transfer-sub-account-20260525)
- **新增街道字段**: `c7387433` (2026-06-01)
- **按负责人/承接商名称查询**: `dfb49780` (2026-05-29)
- **商户端权限校验**: 转出转入接口权限校验 (commit 0348069, merchant-web, 2026-06-01)
- **转单新参数传递**: 修改入参 (commit 7b10552)
- **ID 获取**: 添加获取转单ID功能 (commit a864ece)
- **证据等级**: 代码明确证明

### 电站业主租金停付管理 (TAEI-3103, 代码明确证明, 2026-05-25~27)
**来源**: `rrsjk-light-service` dev 分支 (sunzn/孙志男, 5+ commits, branch: origin/szn_rent_stop_20260525)
- **需求**: 高媛负责，参与人: 魏秋阳、孙志男、李培龙
- **核心实体**: `RentSuspendApplication` — 租金停付申请表（dev 分支新增）
  - 字段: id, memberId, applicationNo, stationCode, ownerName, stationStatus, subCenterCode, subCenterName
  - 业务: specialFlag(资产所属), stationType, fieldMethod(备案方式), rentSuspendType, workOrderNo
  - 原因: suspendReason, reasonDetail, suspendDescFileUrl, ownerPhotoFileUrl
  - 审核: firstAuditorId/Name/At/Remark, finalAuditorId/Name/At/Remark
  - 恢复: resumeAuditorId/Name/At/Remark, deductMonthCount(扣除月数)
  - 撤销: cancelBy, cancelAt
- **状态机**（9个状态）:
  ```
  申请停付待初审 → 初审驳回/待终审 → 终审驳回/终审通过
  终审通过 → 申请恢复待审核 → 恢复驳回/恢复通过
  任意非终审通过 → 已撤销（终审通过后不可撤销）
  ```
- **关联实体**: `RentSuspendApplicationRecord` — 关联租金计划记录（新表）
- **租金状态**: `LightUnionpayRentRecord` 新增 `SUSPEND` 支付状态枚举值
- **业务规则**: 分中心经理初审→总部终审两级审批；终审通过后不可撤销；恢复审核需计算扣除月数
- **停付类型**: OWNER_APPLY(业主申请), DISPUTE_SUSPEND(纠纷停付)
- **停付原因**: OWNER_CHANGE(业主变更), BLACK_ACCOUNT(黑户), INITIAL_INSTALL_FEE(初装费), RENT(租金), DISPUTE(纠纷), OTHER(其他)
- **状态**: 开发中（功能分支 dev，未合并到 master）
- **证据等级**: 代码明确证明

### 完工前方案变更自动审核 (TAEI-3061, 代码明确证明, 2026-05-14)
**来源**: `rrsjk-light-service` → `LightStationPlanChangeServiceImpl.java` + `LightStationPlanChange.java` (王斌/龙龙)

**业务规则**：
- 完工前方案变更（`changeNode = COMPLETE_BEFORE`），如果仅变更品牌（组件型号未变），可跳过审核流程
- 判断条件：`changeType = STATION_PLAN_CHANGE 或 ALL` + `changeNode = COMPLETE_BEFORE` + `checkNeedAudit(oriConfigList, planConfigList) == true`（仅品牌变更）
- 自动审核通过：`status = NO_NEED_AUDIT`, `auditBy = "王红凯"` (硬编码), `auditAt = LocalDateTime.now()`
- 直接执行 `executePlanChangeCompleteBefore(change, auditBy)` 完成变更

**新增枚举**: `LightStationPlanChange.StatusEnum.NO_NEED_AUDIT("无需审核")`

**⚠️ 代码质量风险**: 审核人"王红凯"硬编码在代码中，未通过配置或系统账号管理

### 共享支付账单查询 (TAEI-3086, 代码明确证明, 2026-05-11~15)
**来源**: `rrsjk-light-operation-service` (孙志男), `rrsjk-light-service` (孙志男), `pv.osp-uni` (李培龙)

**变更链路**：
- `light-operation-service`: 共享账单记录查询逻辑重构 + 修正租用月份参数
- `light-service`: 新增共享账单记录明细查询功能 (`LightRentBillService`)
- `pv.osp-uni` (UniApp): 前端添加共享支付账单查询入口
- `light-operation-service`: 电站租金记录新增备注和账单日期字段
- `hds-web`: 修复 A51 暂估业务逻辑

**涉及表**: `light_project_rent_record` (租金记录), `light_share_bill` (共享账单)

### 电站转移权限与数据迁移 (TAEI-3058, 代码明确证明, 2026-06-02~05)
**来源**: `rrsjk-light-service` (姜传德/德, branch: origin/20260515-de-stationTransfer)
**关联需求**: TAEI-3058 【电站转移】电站支持转移 | 负责人: 徐晓凤 | 参与人: 姜廷、姜传德、于淼、杨辉、张硕文、袁睿林
- **核心变更**:
  - `LightStationPersonInfoAuth` 授权信息随电站转移（新增字段支持）
  - 华融授权协议随电站转移
  - 电站转单调整转出商逻辑
  - 合同列表权限调整 + 待下单/逆变器列表/终止管理/基本信息更改/逆变器变更/派工单管理数据权限逻辑变更
  - 新增字段：街道
- **业务意义**: 电站转移涉及多个业务模块的权限迁移，确保转出/转入方数据权限正确切换
- **证据等级**: 代码明确证明

### 科士达逆变器数据拉取延迟修复 (TAEI-3184, 代码明确证明, 2026-06-05)
**来源**: `rrsjk-light-data-service` (于淼/yumiao + 孙志男/sunzn)
- **负责人**: 于淼 | **参与人**: 孙志男
- **变更**: DWS/ADS 数据取数逻辑优化（majinhu 同时期提交），修复数据时间为空导致的图表处理异常
- **证据等级**: 代码明确证明

### TAEI-3183 电站变更审核通过后暂停状态修复 (代码明确证明, 2026-06-05)
**来源**: `rrsjk-light-service/LightStationPlanChangeServiceImpl.java` (解钦, commits: 20f0499d/bb947c75, 2026-06-05)
**关联需求**: TAEI-3183 电站变更未卡住审核导致完工后变更方案，业务数据异常处理 | 负责人: 解钦 | 参与人: 解钦, 商轶龙
- **核心变更**:
  - 方案审核通过后，新增电站暂停状态更新为 `NORMAL`（`LightStation.PauseStatusEnum.NORMAL.value()`）
  - 技术审核通过后，同步新增电站暂停状态更新为 `NORMAL`
  - 涉及 `LightStationPlanChangeServiceImpl` 两处审核通过分支（line 2304, line 2392）
- **业务意义**: 修复完工前变更审核通过后电站暂停状态未更新的问题，确保方案变更完成时电站状态恢复正常
- **证据等级**: 代码明确证明

### 电站转移分中心权限与派工单取消（德/姜传德, TAEI-3058, 2026-06-04~10）
**来源**: `rrsjk-light-service` (德/jiangchuande@haier.com, commits: 14e25cea/b4cb1599/15ccb908/7474e39e, 2026-06-04~10)
**证据等级**: 代码明确证明
- **分中心权限**: `LightStationTransferOrder.xml` 新增 `sub_center_code IN (branchList)` 过滤条件
- **完工状态校验**: 新增 `LightStation.stationCompleteAuditBefore()` 静态方法，返回10种允许转移的电站状态（INIT/WAIT_AUDIT/WAIT_THIRD_AUDIT/AUDIT_REJECT/WAIT_CONFIG/WAIT_ORDER/ROADWORKING/ROADWORK_CONFIRM/ROADWORK_REJECT）
- **派工单取消**: 新增 `LightStationDao.deleteOrderTeam()` + 注入 `LightWorkOrderDao`/`LightWorkOrderOperateLogDao`，转单时取消原派工单
- **服务商直接转出**: 支持服务商直接转出流程
- **扫描日期**: 2026-06-11

### 电站转单管理 CBS 后台页面 (2026-06-04~11)
**来源**: `rrsjk-admin-web` (德/jcd, commits: 71878d1/1c52ce4/c77a95d, 2026-06-04~08)
**证据等级**: 代码明确证明
- **新增 Controller**: `LightStationTransferOrderController.java` → 路由 `/light/lightStationTransferOrder/`
- **新增页面**: `lightStationTransferOrderList.ftl` (124行) — 电站转单管理列表页
- **新增 Excel 导出**: `LightStationTransferOrderExcel.java` (40行)
- **spring-config/service.xml**: 新增转单相关 service bean 注册
- **前端配套**: `nahui-pv.mobile-h5` → `src/views/apv/transferOrder/index.jsx` (193行) + 路由注册
- **Flutter 配套**: `nahuipv_greenergy_flutter` → `feature-station-transfer` 分支，日期选择器优化
- **前端字典**: `nahui-dicts-serve/src/data/apv/station/transStationstatus.js` (41行，5个状态)
- **扫描日期**: 2026-06-11

---

## TAEI-3127 完工/技术驳回「修改技术影像」暂存 — 三态→二态重构 (代码明确证明, 2026-06-04~11)
**来源**: `rrsjk-light-service`, `rrsjk-merchant-web` (王希然/wangxiran, 杨辉, 姜廷, 顾祥娣)
- **负责人**: 徐晓凤 | **实际开发**: 王希然, 杨辉, 姜廷, 顾祥娣
- **参与人**: 姜廷, 魏秋阳, 杨辉, 王希然, 顾祥娣, 袁睿林

### 核心重构：三态驳回 → 二态驳回
**commit 930ffb2dae (王希然, 2026-06-08)**:
- 移除审核影像的三态白名单逻辑，简化为：`null=未驳回, 0=驳回`
- 删除 `AcceptanceConfirmServiceImpl.applyConfirmImgWhitelist` (31行)
- 删除 `CompleteConfirmServiceImpl.applyConfirmImgWhitelist` (36行)
- 重构 `LightStationServiceImpl` 中的三态处理逻辑 (-64行 → +15行)
- 涉及 `initRelateFileRejectFlags`, `fillStationFieldImageRejectInfo`, `resolveStationFieldReject` 方法
- 影响 `getYxStationById` confirmImg list 处理

### ⚠️ Bug修复：reject_flag 值颠倒
**commit 855dca0451 (王希然, 2026-06-04)**:
- `LightStationRelateFile.resolveRejectFlag()`: Boolean.TRUE 从映射 "1" 改为映射 "0"
- `AcceptanceConfirmServiceImpl.isRejectedConfirmImg()`: 从 `"1".equals()` 改为 `"0".equals()`
- `CompleteConfirmServiceImpl`: 同样修正
- `LightStationCompleteImgServiceImpl`: 同样修正
- 涉及 5 个文件 20 行修改

### 新增功能
- 技术审核驳回重提图片同步 (`feat(confirm): 添加技术审核驳回重提图片同步功能`)
- 施工图纸单张驳回 + 驳回原因回填 (`feat(audit): 施工图纸单张驳回支持`)
- 非驳回图片允许编辑 (`fix: allow editing non-rejected confirm images`)
- 越秀业务字段驳回信息填充 (`fix: include yuexiu business field rejects`)
- 完工/验收驳回草稿缓存 (`fix: handle complete reject draft cache`)
- 电站提交后清除审核驳回缓存

### 前端实现细节 (2026-06-08~11 补充)
**来源**: `nahui-pv.mobile-h5` (杨辉/yanghui, 代码明确证明)

#### techRejectFlag 字段
- **触发条件**: 当 `lightStation.status === 'TECH_CHECK_REJECT'` 时，前端设置 `techRejectFlag: 1`
- **用途**: 标识当前电站处于技术审核驳回状态，用于前端UI控制和数据提交
- **位置**: `completeAffirm/index.jsx` 和 `completeAffirmGf/index.jsx` 的 `getInfo` 方法

#### cacheEnable 缓存策略变更
- **旧逻辑**: `cacheEnable: edit ? 0 : 1` — 编辑模式不读缓存
- **新逻辑**: `cacheEnable: orderId ? 0 : 1` + `if (edit) cacheEnable = 1` — 编辑模式强制读缓存
- **业务含义**: 驳回后编辑时，始终从缓存（草稿）加载数据，确保用户之前暂存的内容不丢失
- **影响页面**: 完工确认（户用 + 工商业版）、验收确认

#### 存草稿按钮权限变更
- **旧逻辑**: `{edit != '1' && <Button>存草稿</Button>}` — 编辑模式下不显示存草稿按钮
- **新逻辑**: `{<Button>存草稿</Button>}` — 始终显示；在 orderTeamId 模式下，编辑时也显示存草稿按钮
- **业务含义**: 驳回后修改技术影像时，支持中途暂存，避免大量图片上传过程中数据丢失

### 风险预警
- reject_flag 语义从三态(0/1/null)变为二态(null/0)，历史数据中的 "1" 值需确认是否正确迁移
- 前端页面需要适配新的驳回标记语义
- **证据等级**: 代码明确证明

### 电站审核图片校验 — 新增逆变器OCR和组件倾角OCR (代码明确证明, 2026-06-24)
**来源**: `rrsjk-admin-bff` → `LightStationController.java` (yumiao, commit c58a8bdd, 2026-06-24)

- **新增OCR客户端注入**:
  - `LightStationInverterOcrClient` — 逆变器OCR识别客户端，实体 `com.rrsjk.light.entity.baiduAI.LightStationInverterOcr`
  - `LightStationModuleAngleOcrClient` — 组件倾角OCR识别客户端，实体 `com.rrsjk.light.entity.baiduAI.LightStationModuleAngleOcr`
- **业务含义**: 电站详情页(`LightStationDetailImageView`)现在暴露逆变器OCR和组件倾角OCR的校验元数据，用于审核图片验证
- **已有OCR**: 房产证OCR (`LightStationHouseCertificateOcr`)、电表OCR (`LightElecOcr`)、并网证OCR (`LightGridCert`)
- **证据等级**: 代码明确证明

### 电站列表新增"三天发电时间"查询条件 (代码明确证明, 2026-06-25)
**来源**: `rrsjk-admin-web` → `LightStationController.java`, `StationListExport.java`, `lightStationList.ftl` (wangxiran, commit 27506189, 2026-06-25)
- **新增参数**: `firstThreePowerAtStart` / `firstThreePowerAtEnd` — 按"首次三天发电时间"范围筛选
- **影响接口**:
  - `doListRefactor.do` — 电站列表查询（重构版）新增两个参数
  - `doExport.do` — 电站列表导出新增两个参数
- **buildParams 方法**: 签名从 6 参数扩展为 8 参数，新增 `firstThreePowerAtStart/End` 的时间解析逻辑
- **业务含义**: 支持按电站首次实现连续三天发电的时间范围进行筛选和导出
- **证据等级**: 代码明确证明

### 电站列表导出新增租赁模式+营业状态筛选 (代码明确证明, 2026-06-26)
**来源**: `rrsjk-admin-web` → `StationListExport.java` (wangxiran, commit fa22487d, 2026-06-26)
- **新增参数**: 租赁模式(leaseMode) + 营业状态 — 电站列表导出支持按资方模式和营业状态筛选
- **证据等级**: 代码明确证明

### 运维商合同查询重构 — 主表切换 (代码明确证明, 2026-06-29)
**来源**: `rrsjk-light-service` → `LightStationContractRecord.xml` (孙志男/sunzn, commits 4974eda91a/eb9b783fd9, 分支 szn_sht_contract_20260624, 2026-06-29)

**变更内容**:
- **查询主表从 `light_station` 改为 `light_station_contract_record`** — 合同查询不再以电站表为主表
- **INNER JOIN → LEFT JOIN** — 避免电站记录缺失导致合同数据丢失
- 新增 `opContractColumn` SQL 片段定义查询字段列表
- 业主名/电站编码搜索字段来源改为合同记录表
- 移除多余的 `sr.type = 0` 条件，保留合同类型/状态筛选
- 数据权限隔离策略通过注释说明

**业务影响**: 此前合同查询依赖电站表存在记录，如果电站数据缺失则合同记录也会丢失。重构后以合同记录表为主，确保合同数据完整性。
