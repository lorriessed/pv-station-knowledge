# 电站方案变更 — 完工前与完工后全流程

更新时间: 2026-05-24

## 一、功能概述

电站方案变更允许在电站生命周期中修改方案配置（组件数量/型号、逆变器、屋顶类型等）。根据电站所处阶段，分为**完工前变更**和**完工后变更**。

**核心差异**：
- 完工前变更：同步事务，直接更新方案配置
- 完工后变更：多级审核 + 异步待办链（逆向冲销正向流程积累的资产 → 重建），复杂度差一个数量级

**代码路径**: `rrsjk-light-service` → `LightStationPlanChangeServiceImpl.java`（3153行）

---

## 二、完工前 vs 完工后的判定

**`LightStationPlanChangeServiceImpl.decideStationChangeNode()` L2100**

| 完工前状态 | 完工后状态 |
|-----------|-----------|
| INIT | WAIT_TECH_CHECK |
| WAIT_AUDIT | TECH_CHECK_REJECT |
| WAIT_THIRD_AUDIT | WAIT_OFF_LINE_CHECK |
| AUDIT_REJECT | WAIT_UPLOAD_GRID_INFO |
| WAIT_CONFIG | WAIT_FIRST_AUDIT |
| WAIT_ORDER | FIRST_AUDIT_REJECT |
| ROADWORKING | OFF_LINE_CHECK_REJECT |
| ROADWORK_CONFIRM | ENABLE |
| ROADWORK_REJECT | |
| COMPLETE_WAIT_AUDIT | |
| COMPLETE_AUDIT_REJECT | |

**判定逻辑**：`LightStation.Status.stationCompleteBefore()` vs `stationCompleteAfter()`

---

## 三、完工前变更流程

### 3.1 发起变更

**接口**: `addChangePlan()`

**前置校验**:
- 电站状态必须在完工前状态列表中
- 不能有正在审核中的变更方案
- 四件套电站不允许屋顶类型变更
- 技术审核通过后不允许更换屋顶类型

### 3.2 审核通过后执行

**`executePlanChangeCompleteBefore()`**:
1. 更新组串图
2. 更新房产证/房产证明
3. 更新荷载报告
4. 原方案状态标记为 `CHANGE`
5. 创建新方案配置（设置 planQuantity、planCapacity、inverterPlanQuantity、inverterPlanCapacity）
6. 更新电站基本信息和四件套设计方案
7. 变更状态直接设为 `CHANGE_FINISH`

### 3.3 涉及表

| 表 | 操作 |
|----|------|
| `light_station` | 更新电站图片、数量、容量 |
| `light_station_plan_config` | 原方案标记为 CHANGE，新方案插入为 INIT |
| `light_station_confirm_img` | 更新组串图等 |
| `light_station_plan_design` | 四件套设计方案更新 |
| `light_station_plan_change` | 变更主表 |
| `light_station_plan_change_detail` | 变更明细 |
| `light_spc_operate_log` | 操作日志 |
| `light_station_plan_change_audit_log` | 审核日志 |

---

## 四、完工后变更 — 完整 6 阶段流程

### 阶段 1: 发起变更

**接口**: `addChangePlan()`

**前置校验**:
- 电站状态在完工后状态列表中
- 组件数量必须与方案一致
- **库存校验**（差额校验：新方案数量 > 原方案数量时才检查差额）
- 不能有正在审核中的变更方案

**创建记录**:
- `light_station_plan_change`（status=WAIT_AUDIT）
- `light_station_plan_change_detail`（变更明细）
- `light_station_plan_config`（方案配置关联）

---

### 阶段 2: 技术审核

**通过**: `techAuditPass()` → `status = TECH_AUDIT_PASS`
**驳回**: `techAuditReject()` → `status = TECH_AUDIT_REJECT`

**完工后独有**: 审核通过时再次校验库存（`checkNewPlanStockForAuditPassPro`）

---

### 阶段 3: 资产审核（完工后独有）

**通过**: `assetAuditPass()` → `status = WAIT_UPLOAD_COMPLETE_INFO`
**驳回**: `assetAuditReject()` → `status = ASSET_AUDIT_REJECT`

**校验库存**: 审核通过时再次校验

---

### 阶段 4: 上传完工信息（完工后独有）

**接口**: `uploadCompleteInfo()`

**上传内容**:
- 组件编码（moduleSn）→ `light_station_change_plan_module_sn`
- 组件照片（moduleImg）→ `light_station_change_plan_module_img`
- 逆变器信息（inverter）→ `light_station_change_plan_inverter`

**额外动作**:
- 组件数量必须与方案数量一致
- **异步执行逆变器图片 AI 识别**（`lightStationInverterOcrService`）→ `light_station_inverter_ocr`

**状态变更**: `status = WAIT_COMPLETE_CHECK`（待完工验收）

---

### 阶段 5: 完工验收审核

**通过**: `acceptanceAuditPass()` → `status = CHECK_PASS`
**驳回**: `acceptanceAuditReject()` → `status = CHECK_REJECT`

**核心动作**:
- 校验库存
- **批量创建待办任务 `batchCreateToDo()`** → 写入 `light_station_change_plan_todo` 表

---

### 阶段 6: 定时任务执行待办链（核心！完工后独有）

**定时任务**: `LightStationChangePlanToDoJobServiceImpl.executeToDo()`

**执行逻辑**:
1. 扫描 `successFlag=0` 的待办
2. 按依赖关系分批次执行（DAG 拓扑排序）
3. 所有待办成功后：
   - `unSuspendStationStatus()` — 恢复电站状态（从 SUSPENDING 回到 ENABLE）
   - `updateStationPlan()` — 更新电站方案
   - `status = CHANGE_FINISH`

---

## 五、完工后待办任务链详解

### 5.1 完整的 DAG 依赖图

```
STATION_INFO_CHANGE（电站冻结为 SUSPENDING）
    └── RECOVER_STOCK（回滚库存）
        └── REVERSE_USE（冲销领用 → SAP GVS 冲销）
            ├── PLAN_CONFIG_CHANGE（方案更新 → 创建新方案）
            ├── REVERSE_BASE_POLICY_INCOME（冲销基础政策记账）
            ├── HOUSE_TYPE_CHANGE（屋顶类型更新，仅 ALL 类型变更）
            │       ↓ 以上并行批次完成后
            └── STATION_MATERIAL_CHANGE（逆变器/组件编码/SN 替换）
                    ↓
                RE_USE（重新领用 → 核心节点）
                    ↓
            RE_BASE_POLICY_INCOME（基础政策重新记账 → 生成 SAP 队列）
                    ↓
            REVERSE_STATION_INCOME（冲销电站收入 → 按资方类型）
                    ↓
            RE_STATION_INCOME（重上电站收入 → 按资方类型）
                    ↓
        ┌─── OWNER_CONTRACT_DEAL（业主合同处理）
        ├─── STATION_RENT_RECREATE（业主租金重新计算）
        └─── [9 个政策激励策略]（并行）
                ├── 营销政策
                ├── 并网时效政策
                ├── 月度规模政策
                ├── 安装提升政策
                ├── 新商政策
                └── ...
```

### 5.2 每个待办的完整说明

| 序号 | 待办类型 | 触发条件 | 策略类 | 正向流程对应环节 | 本质操作 |
|------|---------|---------|--------|----------------|---------|
| 1 | **STATION_INFO_CHANGE** | 始终触发 | `StationChangeStrategy` | 电站运行 | 电站状态冻结为 SUSPENDING，操作日志记录"信息变更中电站为暂时冻结状态，不可审批" |
| 2 | **RECOVER_STOCK** | 始终触发 | `RecoverStockStrategy` | 配货发货/库存管理 | 回滚库存：原方案物料释放回仓库，新方案物料从仓库扣除 |
| 3 | **REVERSE_USE** | 始终触发 | `ReverseUseStrategy` | 完工前领用 | SAP GVS 冲销：逆向冲销已领用的物料记账记录 |
| 4 | **PLAN_CONFIG_CHANGE** | 始终触发 | `PlanConfigChangeStrategy` | 方案设计 | 创建新方案配置：插入新的 light_station_plan_config 记录，状态设为 INIT |
| 5 | **HOUSE_TYPE_CHANGE** | changeType=ALL | `HouseTypeChangeStrategy` | 屋顶信息采集 | 更新电站屋顶类型，重置主合同（`resetMasterContract()`） |
| 6 | **REVERSE_BASE_POLICY_INCOME** | 始终触发 | `ReverseBasePolicyIncomeStrategy` | 基础政策结算 | 冲销基础政策记账：辅材费、前50%服务费、后50%服务费、A88领用 |
| 7 | **STATION_MATERIAL_CHANGE** | 依赖 1-3 完成 | `StationMaterialChangeStrategy` | 完工确认 | 组件 SN 码替换、逆变器铭牌图替换、逆变器信息更新 |
| 8 | **RE_USE** | 依赖 7 完成 | `ReUseStrategy` | 完工前领用 | **重新领用**：按新方案重新创建领用记录，同步 SAP |
| 9 | **RE_BASE_POLICY_INCOME** | 依赖 8 完成 | `ReBasePolicyIncomeStrategy` | 基础政策结算 | 重新生成基础政策 SAP 记账队列（辅材费、服务费等） |
| 10 | **REVERSE_STATION_INCOME** | 依赖 9 完成 | `ReverseStationIncomeStrategy` | 电站收入结算 | 按资方类型冲销电站收入（越秀/中核/浦银/招银/华电/华融等） |
| 11 | **RE_STATION_INCOME** | 依赖 10 完成 | `ReStationIncomeStrategy` | 电站收入结算 | 按资方类型重上电站收入 |
| 12 | **OWNER_CONTRACT_DEAL** | changeType=ALL 或 moduleSpecChangeFlag=1 | `OwnerContractDealStrategy` | 业主合同签订 | 重置业主合同 |
| 13 | **STATION_RENT_RECREATE** | 组件规格/数量/屋顶类型任一变化 | `StationRentRecreateStrategy` | 业主租金计算 | 重新生成业主租金 |
| 14-22 | **9 个政策激励** | 组件变更时触发 | 各 PolicyStrategy | 政策激励发放 | 每个策略按统一 9 步流程：冲销 6 步 + 重建 3 步 |

### 5.3 政策激励策略的 9 步标准流程

**基类**: `AbstractPolicyToDoStrategy`

每个政策策略（营销政策、并网时效、月度规模、安装提升、新商、A段/B段奖励等）都遵循统一的 9 步流程：

| 步骤 | 操作 | 说明 |
|------|------|------|
| 1 | 获取原政策记录 | 查询该电站已发放的政策激励 |
| 2 | 冲销政策记账 | 生成 SAP 逆向记账 |
| 3 | 冲销政策金额 | 财务金额回滚 |
| 4 | 标记原记录失效 | 将原政策记录标记为已冲销 |
| 5 | 重新计算政策 | 按新方案重新计算应发政策 |
| 6 | 生成新政策记录 | 创建新的政策激励记录 |
| 7 | 生成新 SAP 记账 | 正向生成 SAP 记账队列 |
| 8 | 更新断点位图 | 记录执行进度（支持断点续传） |
| 9 | 标记完成 | `successFlag=1` |

**断点续传机制**: 政策策略用位图（bitmap）记录进度，失败可从中断点恢复，避免重复冲销。

### 5.4 待办任务的触发条件矩阵

| 变更类型 | STATION_INFO_CHANGE | RECOVER_STOCK | REVERSE_USE | PLAN_CONFIG_CHANGE | HOUSE_TYPE_CHANGE | REVERSE_BASE_POLICY | STATION_MATERIAL | RE_USE | RE_BASE_POLICY | REVERSE_INCOME | RE_INCOME | OWNER_CONTRACT | STATION_RENT | 政策激励 |
|---------|---------------------|---------------|-------------|-------------------|-------------------|-------------------|-----------------|--------|---------------|---------------|----------|---------------|-------------|---------|
| 方案变更 | ✅ | ✅ | ✅ | ✅ | ❌ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ | ✅ | ✅ |
| 屋顶变更 | ✅ | ✅ | ✅ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ✅ | ❌ |
| 全部变更 | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |

---

## 六、正向流程 ↔ 完工后变更待办链 完整映射

这是理解完工后变更的核心：**每个待办任务都是对正向流程中某个环节的逆向冲销和重建**。

### 6.1 电站正向流程全景

```
录单(INIT) → 方案审核(WAIT_AUDIT) → 资方审核(WAIT_THIRD_AUDIT) → 方案配置(WAIT_CONFIG)
  → 待下单(WAIT_ORDER) → 下单(ROADWORKING) → 施工(ROADWORK_CONFIRM)
  → 完工审核(COMPLETE_WAIT_AUDIT) → 技术审核(WAIT_TECH_CHECK)
  → 商务审核(WAIT_FIRST_AUDIT) → 并网启用(ENABLE)
```

### 6.2 正向流程每个环节积累的数据

| 正向环节 | 状态流转 | 核心动作 | 积累的数据/资产 |
|---------|---------|---------|---------------|
| **录单** | → INIT | 创建电站 | 电站主记录、业主信息、合同记录 |
| **方案审核** | → WAIT_AUDIT → WAIT_CONFIG | 审核方案 | 审核记录、方案配置 |
| **资方审核** | → WAIT_THIRD_AUDIT | 资方投件审核 | DH/GF 商机状态 |
| **方案配置** | → WAIT_ORDER | 配置组件/逆变器方案 | light_station_plan_config、四件套设计方案 |
| **下单** | → ROADWORKING | 触发供应链 | 备货单、领用单、仓库分配 |
| **施工** | → ROADWORK_CONFIRM | 施工完成 | 工单、施工图片、实际用料 |
| **完工审核** | → COMPLETE_WAIT_AUDIT | 完工确认 | 完工图片、OCR 识别、组件数量 |
| **技术审核** | → WAIT_TECH_CHECK | 技术审核 | 审核记录、整改工单、运维商划转 |
| **商务审核** | → WAIT_FIRST_AUDIT | 商务审核 | 并网资料、商务审核快照 |
| **并网启用** | → ENABLE | 电站启用 | **电站收入开始计算、政策激励发放、SAP 记账、库存扣减、领用完成、合同生效** |

### 6.3 完工后变更：逆向冲销 → 正向重建

完工后变更时，电站已经经历了从录单到并网的完整流程，积累了大量数据和资产。变更需要**先逆向冲销，再正向重建**。

```
┌─────────────────────────────────────────────────────────────────┐
│ 正向流程积累的数据（ENABLE 状态）                                    │
│                                                                  │
│  ① 电站状态：ENABLE（已完成，正常运行）                               │
│  ② 方案配置：light_station_plan_config（COMPLETE/ACCEPTANCE）      │
│  ③ 库存：仓库库存已扣减                                             │
│  ④ 领用：已完成领用，SAP GVS 已记账                                  │
│  ⑤ 组件/SN：已录入组件编码、逆变器铭牌                                │
│  ⑥ 基础政策：辅材费/服务费已记账（SAP 队列）                           │
│  ⑦ 电站收入：按资方类型已结算（越秀/中核/浦银/招银/华电/华融...）        │
│  ⑧ 政策激励：9 个政策已发放                                          │
│  ⑨ 合同：主合同/业主合同已生效                                       │
│  ⑩ 业主租金：已计算生成                                              │
└─────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────┐
│ 逆向冲销阶段（待办任务 1-6）                                         │
│                                                                  │
│  1. STATION_INFO_CHANGE: 冻结电站（SUSPENDING）                     │
│     → 防止审批期间电站状态被其他流程修改                               │
│                                                                  │
│  2. RECOVER_STOCK: 回滚库存                                        │
│     → 原方案物料释放回仓库（逆向）                                    │
│                                                                  │
│  3. REVERSE_USE: 冲销领用                                         │
│     → SAP GVS 逆向冲销已领用的物料记账                                │
│                                                                  │
│  4. PLAN_CONFIG_CHANGE: 创建新方案                                  │
│     → 正向：插入新的 light_station_plan_config                      │
│                                                                  │
│  5. HOUSE_TYPE_CHANGE: 更新屋顶类型                                 │
│     → 正向：更新电站屋顶类型 + 重置主合同                              │
│     → 仅 changeType=ALL 时触发                                      │
│                                                                  │
│  6. REVERSE_BASE_POLICY_INCOME: 冲销基础政策                         │
│     → SAP 逆向冲销：辅材费、前 50% 服务费、后 50% 服务费、A88 领用      │
└─────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────┐
│ 正向重建阶段（待办任务 7-22）                                        │
│                                                                  │
│  7. STATION_MATERIAL_CHANGE: 替换组件/逆变器                         │
│     → 正向：更新组件 SN 码、逆变器铭牌图、逆变器信息                     │
│                                                                  │
│  8. RE_USE: 重新领用 ★核心节点★                                     │
│     → 正向：按新方案重新创建领用记录，同步 SAP                         │
│     → 这是变更的核心：领用数据必须与新方案一致                           │
│                                                                  │
│  9. RE_BASE_POLICY_INCOME: 重新生成基础政策                           │
│     → 正向：生成新的 SAP 记账队列（辅材费、服务费等）                    │
│                                                                  │
│ 10. REVERSE_STATION_INCOME: 冲销电站收入                             │
│     → SAP 逆向冲销：按资方类型冲销已结算的电站收入                       │
│                                                                  │
│ 11. RE_STATION_INCOME: 重上电站收入                                  │
│     → 正向：按资方类型重新结算电站收入                                 │
│                                                                  │
│ 12. OWNER_CONTRACT_DEAL: 处理业主合同                                │
│     → 正向：重置业主合同                                             │
│     → 仅 changeType=ALL 或 moduleSpecChangeFlag=1 时触发              │
│                                                                  │
│ 13. STATION_RENT_RECREATE: 重新计算业主租金                           │
│     → 正向：按新方案重新生成业主租金                                   │
│     → 组件规格/数量/屋顶类型任一变化时触发                              │
│                                                                  │
│ 14-22. 9 个政策激励策略（并行）                                      │
│     → 每个策略：冲销 6 步 + 重建 3 步（统一 9 步流程）                   │
│     → 营销政策、并网时效、月度规模、安装提升、新商、A 段/B 段奖励...       │
│                                                                  │
│ 最后: unSuspendStationStatus() + updateStationPlan()                │
│     → 恢复电站状态（SUSPENDING → ENABLE）                             │
│     → 更新电站方案（数量/容量/图片）                                   │
│     → status = CHANGE_FINISH                                        │
└─────────────────────────────────────────────────────────────────┘
```

### 6.4 为什么需要这样的依赖顺序？

**依赖链设计原则**:

1. **先冻结电站**：防止审批期间其他流程修改电站状态
2. **先冲销库存，再冲销领用**：领用依赖库存，必须先回滚库存才能冲销领用
3. **先冲销旧数据，再创建新数据**：避免数据冲突（如方案配置、SAP 记账）
4. **领用必须在物料替换之后**：领用需要绑定实际的组件 SN 和逆变器信息
5. **基础政策重新记账必须在重新领用之后**：领用数据是基础政策记账的前置条件
6. **电站收入必须在基础政策之后**：收入结算依赖基础政策的完成状态
7. **政策激励并行执行**：各政策之间无依赖，可并行处理

### 6.5 完工后变更 vs 完工前变更 差异汇总

| 维度 | 完工前变更 | 完工后变更 |
|------|-----------|-----------|
| 审核流程 | 技术审核通过直接完成 | 技术审核 → 资产审核 → 上传完工信息 → 完工验收 → 待办链 |
| 电站冻结 | 不冻结 | **冻结为 SUSPENDING**，完成后恢复 |
| 库存校验 | 不校验 | 发起/技术审核/资产审核/完工验收 **4 次校验** |
| 组件编码/SN | 不涉及 | **上传 + AI 识别 + 替换** |
| 逆变器信息 | 不涉及 | **上传 + AI 铭牌识别 + 替换** |
| 财务冲销 | 不涉及 | **冲销领用 → 冲销基础政策 → 冲销收入 → 重上收入 → 重算政策激励** |
| 合同处理 | 屋顶变更时重置主合同 | 同左 + **业主合同重签** |
| 方案配置字段 | 只更新 planQuantity/capacity | **额外更新** completeConfirmQuantity/capacity、acceptanceConfirmQuantity/capacity |
| 新增表 | 6 张 | **13 张**（待办、组件编码、组件照片、逆变器、OCR 识别等） |
| 执行方式 | 同步事务 | **异步定时任务链**（按依赖顺序逐步执行，支持断点续传） |
| 待办任务 | 无 | **18 个待办任务**，分批次 DAG 执行 |

---

## 七、涉及的数据库表汇总

| 表 | 完工前 | 完工后 | 说明 |
|----|--------|--------|------|
| `light_station` | ✅ | ✅ | 电站主表 |
| `light_station_plan_config` | ✅ | ✅ | 方案配置表 |
| `light_station_plan_change` | ✅ | ✅ | 变更主表 |
| `light_station_plan_change_detail` | ✅ | ✅ | 变更明细 |
| `light_station_confirm_img` | ✅ | ✅ | 确认图片 |
| `light_station_plan_design` | ✅ | ✅ | 四件套设计方案 |
| `light_spc_operate_log` | ✅ | ✅ | 操作日志 |
| `light_station_plan_change_audit_log` | ✅ | ✅ | 审核日志 |
| `light_station_change_plan_todo` | ❌ | ✅ | **待办任务表** |
| `light_station_change_plan_module_sn` | ❌ | ✅ | **变更组件编码表** |
| `light_station_change_plan_module_img` | ❌ | ✅ | **变更组件照片表** |
| `light_station_change_plan_inverter` | ❌ | ✅ | **变更逆变器信息表** |
| `light_station_inverter_ocr` | ❌ | ✅ | **逆变器 AI 识别结果** |
| `light_make_order` | 读 | 读 | 主料配货订单 |
| `light_auxiliary_make_order` | 读 | 读 | 辅料配货订单 |
| `light_stock` | ❌ | ✅ 读 | 库存表 |
| `light_station_contract_record` | ✅ | ✅ | 合同记录 |

---

## 八、核心 Service 清单

| 服务 | 文件 | 职责 |
|------|------|------|
| 方案变更主服务 | `LightStationPlanChangeServiceImpl.java` | 变更发起、审核、执行 |
| 定时任务执行器 | `LightStationChangePlanToDoJobServiceImpl.java` | 扫描待办、DAG 执行 |
| 电站冻结策略 | `StationChangeStrategy.java` | 冻结电站状态 |
| 方案更新策略 | `PlanConfigChangeStrategy.java` | 创建新方案配置 |
| 屋顶变更策略 | `HouseTypeChangeStrategy.java` | 更新屋顶类型、重置合同 |
| 基础策略基类 | `AbstractPolicyToDoStrategy.java` | 政策策略 9 步流程模板 |
| 集合策略基类 | `AbstractCollectionPolicyToDoStrategy.java` | 集合策略通用逻辑 |
| 状态变更操作 | `StationChangeOperationService.java` | 电站状态变更操作 |

---

## 来源

- `rrsjk-light-service` → `LightStationPlanChangeServiceImpl.java`（3153 行）
- `rrsjk-light-service` → `LightStationChangePlanToDoJobServiceImpl.java`
- `rrsjk-light-service` → `AbstractPolicyToDoStrategy.java`
- `rrsjk-light-service` → `StationChangeStrategy.java` / `PlanConfigChangeStrategy.java` / `HouseTypeChangeStrategy.java`
- `rrsjk-light-service` → `LightStationChangePlanToDo.ToDoTypeEnum`
- 代码扫描日期: 2026-05-24
