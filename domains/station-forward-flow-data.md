# 电站正向流程数据积累全景

更新时间: 2026-05-24

本文档梳理电站从录单到 ENABLE（并网启用）完整生命周期中，每个环节**积累的数据/资产**。这是理解**完工后方案变更为什么要做逆向冲销**的基础。

---

## 一、正向流程全景图

```
录单(INIT) → 方案审核(WAIT_AUDIT) → 资方审核(WAIT_THIRD_AUDIT) → 方案配置(WAIT_CONFIG)
  → 待下单(WAIT_ORDER) → 下单(ROADWORKING) → 施工(ROADWORK_CONFIRM)
  → 完工审核(COMPLETE_WAIT_AUDIT) → 技术审核(WAIT_TECH_CHECK)
  → 商务审核(WAIT_FIRST_AUDIT) → 并网启用(ENABLE)
```

---

## 二、每个环节积累的数据/资产

### 2.1 录单环节 → INIT

**代码**: 各 StationModel 的 register 方法（`LightOrdinaryStationModel`, `LightHouseholdStationModel`, `LightChdStationModel` 等）

| 数据 | 表 | 说明 |
|------|-----|------|
| 电站主记录 | `light_station` | 电站编码、业主信息、地址、屋顶类型、安装方式、装机容量 |
| 草稿记录 | `light_staging_records` | 保存录单草稿 |
| 合同记录 | `light_station_contract_record` | 电子合同初始记录（contractStatus=WAIT_CONFIRM, signStatus=NO_SIGN） |
| 审核记录 | `light_station_audit` | 初始审核记录（状态 WAIT_AUDIT） |
| 方案配置 | `light_station_plan_config` | 初始方案配置（组件/逆变器 SKU、数量、功率） |
| 业主图片 | `light_station_confirm_img` | 身份证、房产证等业主图片 |
| 银行卡信息 | `light_station_bank` | 业主银行账户 |
| 保姆/运维用户 | `light_station_nanny_user` | 如有关联 |

**积累的资产**: 电站主数据（电站编码是后续所有环节的关联键）

---

### 2.2 方案审核环节 → WAIT_AUDIT → WAIT_THIRD_AUDIT → WAIT_CONFIG

**代码**: `LightStationServiceImpl.auditInfoOk()`, `DhQueryInputPieceStateModel`, `GfQueryInputPieceStateModel`

| 数据 | 表 | 说明 |
|------|-----|------|
| 审核通过记录 | `light_station_audit` | 更新审核人、审核时间、审核意见 |
| 资方商机状态 | `dh_business_opportunity` / `gf_business_opportunity` | DH/GF 模式下资方审核通过后更新商机状态 |
| DH/GF 电站关联记录 | `dh_light_station` / `gf_light_station` | 首次进件状态（WAIT_PUSH 等） |
| 操作日志 | `light_station_operate_log` | 记录审核动作 |

**积累的资产**: 资方审核通过的资质证明（无资方审核通过，不能进入下单）

---

### 2.3 方案配置环节 → WAIT_CONFIG → WAIT_ORDER

**代码**: `LightConfirmOrderServiceImpl` 等

| 数据 | 表 | 说明 |
|------|-----|------|
| 方案配置确认 | `light_station_plan_config` | 方案审核通过后的最终配置 |
| 待下单确认 | `light_confirm_order` | 待下单审核确认记录 |

**积累的资产**: 确认的方案配置（组件/逆变器型号、数量、功率，后续下单的依据）

---

### 2.4 下单环节 → ROADWORKING

**代码**: `LightMakeOrderServiceImpl.java`

| 数据 | 表 | 说明 |
|------|-----|------|
| **主料备货单** | `light_make_order` | 创建主料备货单（初始 TO_BE_SUBMITTED） |
| **辅料备货单** | `light_auxiliary_make_order` | 四件套时创建辅料备货单 |
| **待领用单** | `light_use_order` | 创建领用单（UseStatus=PENDING, UseNode=BEFORE_COMPLETE） |
| 下单时间 | `light_station.orderAt` | 记录下单时间 |
| 操作日志 | `light_station_operate_log` | "备货申请下单" |

**积累的资产**:
- 备货单（供应链起点）
- 领用单（后续出库记账的前置条件）

详见 `domains/order-dispatch-delivery.md`

---

### 2.5 配货环节

**代码**: `LightMakeStockServiceImpl.java`

| 数据 | 表 | 说明 |
|------|-----|------|
| **配货单** | `light_purchase_order` | 生成配货单（WAIT_SEND_GOODS） |
| **采购单关联** | `light_purchase_pre` | 配货单 ↔ 采购单关联 |
| **额度占用** | `light_quota_change` | type=USED，组件配货占用额度 |
| 方案配货状态 | `light_station_plan_config.distributionStatus=YES` | 标记已配货 |
| SAP/PCS 推送队列 | `light_order_to_pcs_queue` | 组件预付款推 SAP 记账 |

**积累的资产**:
- 配货单（物料从仓库发出的依据）
- 额度占用记录（服务商额度管理）

---

### 2.6 库存扣减 & 领用出库

**代码**: `LightUseOrderServiceImpl.outStock()`

| 数据 | 表 | 说明 |
|------|-----|------|
| **出库记录** | `light_store_out_record` | 类型 USED（工程用料出库），数量、SKU、仓库 |
| **库存扣减** | `light_stock` | stock = stock - number（扣减仓库库存） |
| **库存变动流水** | `light_stock_change` | 记录每次库存变动 |
| **额度释放** | `light_quota_change` | type=RELEASE，领用出库释放发货额度 |
| **GVS SAP 凭证** | `light_use_order.voucher` | 调用 GVS SO 发货接口（移动类型 291），返回 MBLNR 凭证号、DMBTR 金额 |
| **SAP 会计凭证** | `light_use_order` 的 sapAccountVoucher/sapAccountYear | GVS 返回的 EX_BKPF 中的 BELNR/GJAHR |

**GVS 接口调用细节**:
- 接口: `gvsOrderApi.soDeliver()`
- 移动类型: `BWART=291`（库存管理 - 工程领用出库）
- 请求包含: 领用单号（BSTKD）、工厂（WERKS）、服务商 V 码（XREF2）、电站编号（XREF3）、物料号（MATNR）、数量（ERFMG）
- 返回: MBLNR（凭证号）、DMBTR（金额）、EX_BKPF（会计凭证）

**积累的资产（关键！）**:
- **仓库库存已扣减**（实物层面物料已出库）
- **SAP 凭证已生成**（财务层面已记账）
- **额度已释放**（财务层面发货额度已处理）
- **出库记录已创建**（追溯链路）

---

### 2.7 施工环节 → ROADWORK_CONFIRM

**代码**: `LightWorkOrderServiceImpl.completeConfirm()`

| 数据 | 表 | 说明 |
|------|-----|------|
| 工单 | `light_work_order` | 派工单、施工队信息、施工状态 |
| 施工图片 | `light_station_complete_img` | 完工确认图片组（必填项） |
| 方案完成状态 | `light_station_plan_config.status=COMPLETE` | 方案标记为已完成 |
| 操作日志 | `light_station_operate_log` | 施工完成记录 |

**积累的资产**:
- 施工完成证明（图片 + 工单）
- 方案完成标记

---

### 2.8 完工审核环节 → COMPLETE_WAIT_AUDIT

**代码**: `CompleteConfirmServiceImpl.submitCompleteConfirm()`, `LightStationCompleteImgServiceImpl.completePro()`

| 数据 | 表 | 说明 |
|------|-----|------|
| 完工图片 | `light_station_complete_img` | 完工确认图片（组件、逆变器、全景等） |
| 组件数量确认 | `light_station.completeConfirmQuantity` | 完工确认组件数量 |
| 组件容量确认 | `light_station.completeConfirmCapacity` | 完工确认组件容量 |
| 逆变器数量/容量 | `light_station.inverterCompleteConfirmQuantity/Capacity` | 逆变器完工数据 |
| 组件编码 | `light_module_sn` | 组件 SN 码录入 |
| 逆变器信息 | `light_station_inverter` | 逆变器铭牌信息 |
| OCR 识别结果 | `light_station_inverter_ocr` | 逆变器铭牌 AI 识别 |
| 备案证信息 | `light_station` 的备案编码 | 特定模式下的备案编码 |
| 经纬度 | `light_station` 的经纬度字段 | 地理编码服务获取 |
| 银行卡照片 | `light_station_confirm_img` | 更新银行卡照片 |
| 技术审核记录 | `light_station_audit` | 创建技术审核待审核记录 |

**积累的资产**:
- 完整的完工确认数据（组件数量/容量/SN、逆变器信息、图片）
- 这些是后续**电站收入结算、政策激励发放**的核心依据

---

### 2.9 技术审核环节 → WAIT_TECH_CHECK

**代码**: `BusinessStatusMode.handleTechAuditPass()`, `CompleteConfirmServiceImpl.stationCompletedPassed()`

| 数据 | 表 | 说明 |
|------|-----|------|
| 技术审核通过记录 | `light_station_audit` | 审核状态更新 |
| 整改工单 | `light_work_order` | 如驳回则创建整改单 |
| 运维商划转 | `light_station.opMemberId` / `opTime` | 自动划转运维商 |

**积累的资产**:
- 技术审核通过的资质
- 运维商绑定（后续运维收入归属）

---

### 2.10 商务审核环节 → WAIT_FIRST_AUDIT

**代码**: `BusinessStatusMode.handleBusinessAudit()`

| 数据 | 表 | 说明 |
|------|-----|------|
| 商务审核快照 | `business_audit_snap_shot` | 屋顶类型、装机容量快照 |
| 并网资料 | `light_station` 相关字段 | 并网验收资料 |
| 商务审核通过记录 | `light_station_audit` | 商务审核状态更新 |

**积累的资产**:
- 商务审核通过的资质
- 商务审核快照（用于后续一致性校验）

---

### 2.11 并网启用环节 → ENABLE

**代码**: 各资方收入结算服务、政策激励服务、合同服务等

这是正向流程中**数据积累最密集**的环节。

#### 2.11.1 合同生效

| 数据 | 表 | 说明 |
|------|-----|------|
| 主合同生效 | `light_station_contract_record` | contractStatus=FINISHED, signStatus=SIGNED |
| 业主合同 | `light_station_contract_record` | 业主合同记录 |

#### 2.11.2 电站收入结算开始

**各资方收入结算服务**（通过 Dubbo 调用 SAP 相关服务）:

| 资方 | 服务类 | 说明 |
|------|--------|------|
| 越秀 | `LightStationYuexiuSettleServiceImpl` | 越秀模式电站收入结算 |
| 中核 | `ZhongYinTradeIncomeSettleServiceImpl` | 中核模式电站收入结算 |
| 浦银 | `PuYinTradeIncomeSettleServiceImpl` | 浦银模式电站收入结算 |
| 招银 | `ZhaoYinTradeIncomeSettleServiceImpl` | 招银模式电站收入结算 |
| 华电 | `HuaDianTradeIncomeSettleServiceImpl` | 华电模式电站收入结算 |
| 华融 | `HuaRongTradeIncomeSettleServiceImpl` | 华融模式电站收入结算 |

这些服务调用 `SyncFinanceToSapService` 和 `SapRecordService`（外部 Dubbo 服务）进行 SAP 记账。

| 数据 | 表 | 说明 |
|------|-----|------|
| SAP 记账队列 | `light_sap_queue` / 外部 SAP 系统 | 电站收入 SAP 记账记录 |
| 收入结算记录 | 各资方对应的结算表 | 电站收入明细 |

#### 2.11.3 政策激励发放

**代码**: `policyIncome/` 包下的各种 Handler

| 政策类型 | Handler | 说明 |
|---------|---------|------|
| 基础政策 | `AbstractPolicyIncomeHandler` | 辅材费、前50%服务费、后50%服务费、A88领用 |
| 营销政策 | `SpInspirePolicyIncomeHandlerImpl` | 服务商营销激励 |
| 并网时效政策 | `GridPolicyToDoStrategy` 等 | 并网时效激励 |
| 月度规模政策 | `LightAnnualScalePolicyMonthlyDetailIncomeHandlerImpl` | 月度规模激励 |
| 安装提升政策 | `GridPolicyIncomeInstallAdvanceToDoStrategy` | 安装量提升激励 |
| 新商政策 | `NewMerchantPolicyToDoStrategy` | 新服务商激励 |
| A段/B段奖励 | `APolicyToDoStrategy` / `BPolicyToDoStrategy` | A段/B段激励 |
| 启用政策 | `EnablePolicyToDoStrategy` | 电站启用时的激励 |

| 数据 | 表 | 说明 |
|------|-----|------|
| 政策激励记录 | 各政策对应的记录表 | 政策类型、金额、发放状态 |
| SAP 记账 | 通过 `SyncFinanceToSapService` | 政策激励 SAP 记账 |
| SAP 记录 | `sap_record` / 外部 SAP 系统 | 已记账的政策记录 |

#### 2.11.4 业主租金计算

| 数据 | 表 | 说明 |
|------|-----|------|
| 业主租金记录 | 租金计算相关表 | 按组件数量、功率、屋顶类型计算 |

#### 2.11.5 零碳/财务收入

**代码**: `zerocarbon/FinanceIncomeModel.java`

| 数据 | 表 | 说明 |
|------|-----|------|
| 财务收入记录 | 财务收入相关表 | 零碳相关收入 |

---

## 三、ENABLE 状态下的完整数据资产清单

电站达到 ENABLE 状态时，系统中已积累了以下数据：

### 3.1 电站主数据

| 表 | 关键字段 |
|-----|---------|
| `light_station` | 电站编码、业主信息、地址、屋顶类型、安装方式、装机容量、状态=ENABLE、完工时间、运维商ID |
| `light_station_confirm_img` | 业主身份证、房产证、完工图片、银行卡照片 |
| `light_station_bank` | 业主银行账户 |
| `light_station_audit` | 完整的审核记录链 |
| `light_station_operate_log` | 完整的操作日志链 |

### 3.2 方案与配置数据

| 表 | 关键字段 |
|-----|---------|
| `light_station_plan_config` | 方案配置（组件/逆变器 SKU、数量、功率、状态=COMPLETE/ACCEPTANCE） |
| `light_station_plan_design` | 四件套设计方案（安装配置、组件尺寸、悬挑等） |

### 3.3 供应链数据

| 表 | 关键字段 |
|-----|---------|
| `light_make_order` | 主料备货单 |
| `light_auxiliary_make_order` | 辅料备货单 |
| `light_purchase_order` | 配货单 |
| `light_pre_order` | 采购单 |
| `light_purchase_pre` | 配货单与采购单关联 |

### 3.4 库存与领用数据

| 表 | 关键字段 |
|-----|---------|
| `light_stock` | **仓库库存已扣减** |
| `light_stock_change` | **库存变动流水** |
| `light_store_out_record` | **出库记录**（USED 类型，已出库完成） |
| `light_use_order` | **领用单**（已完成，带 SAP 凭证号 MBLNR） |
| `light_quota_change` | **额度变动流水**（USED + RELEASE） |

### 3.5 组件与逆变器数据

| 表 | 关键字段 |
|-----|---------|
| `light_module_sn` | **组件 SN 码**（已录入） |
| `light_station_inverter` | **逆变器信息**（铭牌型号、功率等） |
| `light_station_inverter_ocr` | **逆变器 AI 识别结果** |

### 3.6 工单数据

| 表 | 关键字段 |
|-----|---------|
| `light_work_order` | 工单（施工队信息、施工状态） |

### 3.7 合同数据

| 表 | 关键字段 |
|-----|---------|
| `light_station_contract_record` | **合同记录**（已签署生效） |

### 3.8 财务数据

| 表/服务 | 关键字段 |
|-----|---------|
| `light_sap_queue` | **SAP 记账队列**（组件预付款、领用出库等） |
| 外部 SAP 系统（通过 `SyncFinanceToSapService`） | **SAP 财务记账** |
| `sap_record`（通过 `SapRecordService`） | **SAP 记录** |
| 各资方结算表 | **电站收入结算记录** |
| 各政策激励记录表 | **政策激励发放记录** |

### 3.9 运维数据

| 表 | 关键字段 |
|-----|---------|
| `light_station` | `opMemberId`（运维商ID）、`opTime`（划转时间） |
| `light_op_authority_zone` | 运维区域信息 |

---

## 四、完工后变更为什么要逆向冲销

电站达到 ENABLE 后，上述所有数据都已经"固化"。当方案变更时：

1. **方案配置变了** → 组件数量/型号/功率不同
2. **屋顶类型变了** → 合同需要重新签署
3. **组件 SN 变了** → 需要替换 SN 码和逆变器铭牌

这些变化会直接影响：

| 变化 | 影响的数据 |
|------|-----------|
| 组件数量变化 | 库存、领用、额度、SAP 记账、电站收入、政策激励 |
| 组件型号变化 | 功率变化 → 电站收入、政策激励、业主租金 |
| 屋顶类型变化 | 合同、业主租金、资方审核快照 |
| 逆变器变化 | 逆变器信息、AI 识别结果 |

所以完工后变更的待办链必须**先逆向冲销所有这些已固化的数据，再按新方案正向重建**。这就是为什么完工后变更需要 18 个待办任务、分 6 个审核阶段、走异步 DAG 执行链。

---

## 五、正向流程与完工后变更待办链的完整映射

| 正向环节 | 积累的数据 | 完工后变更的逆向待办 | 完工后变更的重建待办 |
|---------|-----------|---------------------|---------------------|
| 方案配置 | plan_config | PLAN_CONFIG_CHANGE（创建新方案） | — |
| 屋顶信息 | 电站屋顶类型 | HOUSE_TYPE_CHANGE（更新屋顶） | — |
| 库存扣减 | light_stock | RECOVER_STOCK（回滚库存） | — |
| 领用出库 | use_order + GVS 凭证 | REVERSE_USE（SAP 冲销） | RE_USE（重新领用） |
| 组件/SN | module_sn | STATION_MATERIAL_CHANGE（SN 替换） | — |
| 逆变器 | station_inverter + OCR | STATION_MATERIAL_CHANGE（逆变器替换） | — |
| 基础政策 | SAP 记账 | REVERSE_BASE_POLICY_INCOME（冲销） | RE_BASE_POLICY_INCOME（重建） |
| 电站收入 | 各资方收入结算 | REVERSE_STATION_INCOME（冲销） | RE_STATION_INCOME（重建） |
| 政策激励 | 各政策记录 | 各政策策略的冲销步骤 | 各政策策略的重建步骤 |
| 业主合同 | contract_record | OWNER_CONTRACT_DEAL（合同处理） | — |
| 业主租金 | 租金记录 | STATION_RENT_RECREATE（租金重算） | — |
| 电站状态 | ENABLE | STATION_INFO_CHANGE（冻结） | unSuspend（解冻恢复） |

---

## 六、核心服务清单

| 服务 | 文件 | 正向流程职责 |
|------|------|------------|
| 电站主服务 | `LightStationServiceImpl.java` | 方案审核 |
| 方案变更服务 | `LightStationPlanChangeServiceImpl.java` | 变更发起/审核 |
| 领用出库服务 | `LightUseOrderServiceImpl.java` | 出库 + GVS 调用 + 库存扣减 |
| 配货服务 | `LightMakeStockServiceImpl.java` | 配货 + 采购单关联 + 额度占用 |
| 完工确认服务 | `CompleteConfirmServiceImpl.java` | 完工审核 + 双状态调度 |
| 状态调度器 | `BusinessStatusMode.java` | 技术/商务双状态联动 |
| 越秀收入结算 | `LightStationYuexiuSettleServiceImpl.java` | 越秀模式电站收入 |
| 中核收入结算 | `ZhongYinTradeIncomeSettleServiceImpl.java` | 中核模式电站收入 |
| 浦银收入结算 | `PuYinTradeIncomeSettleServiceImpl.java` | 浦银模式电站收入 |
| 招银收入结算 | `ZhaoYinTradeIncomeSettleServiceImpl.java` | 招银模式电站收入 |
| 华电收入结算 | `HuaDianTradeIncomeSettleServiceImpl.java` | 华电模式电站收入 |
| 华融收入结算 | `HuaRongTradeIncomeSettleServiceImpl.java` | 华融模式电站收入 |
| GVS 接口 | `GvsOrderApi.java` | SAP SO 发货接口（移动类型 291） |
| SAP 记账服务 | `SyncFinanceToSapService`（Dubbo 外部服务） | SAP 财务记账 |
| SAP 记录服务 | `SapRecordService`（Dubbo 外部服务） | SAP 记录管理 |
| 政策激励基类 | `AbstractPolicyIncomeHandler.java` | 政策激励 9 步流程模板 |
| 合同服务 | `LightStationContractServiceImpl.java` | 合同管理 |
| 组件 SN 服务 | `LightModuleSnServiceImpl.java` | 组件 SN 码管理 |

---

## 来源

- `rrsjk-light-service` → `LightStationPlanChangeServiceImpl.java`
- `rrsjk-light-service` → `LightUseOrderServiceImpl.java`
- `rrsjk-light-service` → `LightMakeStockServiceImpl.java`
- `rrsjk-light-service` → `CompleteConfirmServiceImpl.java`
- `rrsjk-light-service` → `BusinessStatusMode.java`
- `rrsjk-light-service` → 各资方收入结算服务
- `rrsjk-light-service` → `policyIncome/` 包
- `rrsjk-light-service` → `zerocarbon/FinanceIncomeModel.java`
- `rrsjk-light-service` → `LightStationContractServiceImpl.java`
- `rrsjk-light-service` → `LightModuleSnServiceImpl.java`
- 代码扫描日期: 2026-05-24
