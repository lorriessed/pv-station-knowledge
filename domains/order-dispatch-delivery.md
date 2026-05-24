# 电站下单-配货-发货全链路

更新时间: 2026-05-24

## 业务全景

电站方案审核通过后，物料从下单到送达的完整链路：

```
方案审核通过 → 电站变 WAIT_ORDER(待下单) → 备货申请下单(创建 LightMakeOrder)
→ 配货(WAIT → FINISHED, 生成 LightPurchaseOrder) → 关联采购单(LightPreOrder)
→ 发货(WAIT_SEND_GOODS → WAIT_DELIVERY → FINISHED) → 签收入库(inStore)
```

## 一、方案审核通过 → 待下单

### 触发入口

| 模式 | 代码路径 | 触发条件 |
|------|---------|---------|
| 广发模式 | `GfQueryInputPieceStateModel.dealFirstInputPieceResponseInfo()` | 广发首次进件审核通过 (FirstStatus.SUCCESS) |
| 顶好模式 | `DhQueryInputPieceStateModel` | 顶好首次进件审核通过 |
| 合同签署完成 | `DccSignedCallbackServiceImpl` | 电子合同签订完成回调 |
| 待下单审核确认 | `LightConfirmOrderServiceImpl` | 待下单审核确认后 |

### 电站状态变更

审核通过后，电站状态变更为 **WAIT_ORDER（待下单）**，此时可以发起备货申请。

## 二、备货申请下单 (LightMakeOrder)

### 核心 Service

**代码路径**: `rrsjk-light-service` → `LightMakeOrderServiceImpl.java`

### 下单前置校验

| 校验项 | 规则 | 代码位置 |
|--------|------|---------|
| 电站状态 | 必须是 `WAIT_ORDER`，否则报错"不是待下单状态" | L182-184 |
| 合同状态 | 必须 `FINISHED`（已签订完成） | L202-204 |
| 服务商退商 | 服务商不能处于退商状态 | L164-173 |
| 重复下单 | 同一电站不能重复创建主料备货单 | L333-337 |
| 共建模式合同 | 共建费合同 + 专项合同必须都签完 | L208-233 |
| 顶好模式 | 首次进件必须审核通过 | L187-192 |

### 备货单状态机

```
TO_BE_SUBMITTED(待提交) → WAIT_CONFIRM(下单待审核) → WAIT(待配货) → FINISHED(已配货)
                                              ↘ RETURNED(被退回)
                                              ↘ STOP(已终止)
```

### 下单流程核心逻辑

1. 创建主料备货单 `LightMakeOrder`（初始状态 `TO_BE_SUBMITTED`）
2. 如有辅料（FourItemFlag=YES），同时创建辅料备货单 `LightAuxiliaryMakeOrder`
3. 更新电站状态为 **ROADWORKING（施工中）**，记录下单时间 `orderAt`
4. **领用提前功能**：创建待领用领用单 `LightUseOrder`（UseStatus=PENDING, UseNode=BEFORE_COMPLETE）
5. 记录操作日志："备货申请下单"

### 领用提前功能 (LightUseOrder)

**代码路径**: `LightMakeOrderServiceImpl.preparePendingUseOrdersData()` + `createPendingUseOrdersInTransaction()`

- 备货下单时自动按方案配置(`LightStationPlanConfig`)创建待领用单
- 按主料/辅料关联到不同的备货单号
- 领用单号格式: `B` + 备货单号 + 序号（B 表示 BEFORE，如 BLS20260524000001-1）

### 仓库分配逻辑

- **VIP 模式**：通过二级子账号授权区域 (`LightSubSpRegion`) → 二级仓库 (`LightSpAuclonStore`) → 主仓库 (`LightSpStore`)
- **普通模式**：已注释掉授权区域逻辑，仓库在配货阶段选择

### 相关表

| 表名 | 用途 |
|------|------|
| `light_make_order` | 主料备货单 |
| `light_auxiliary_make_order` | 辅料备货单 |
| `light_use_order` | 完工前领用单 |
| `light_station` | 电站（状态更新为 ROADWORKING） |
| `light_station_operate_log` | 电站操作日志 |

## 三、配货 (MakeStock)

### 核心 Service

**代码路径**: `rrsjk-light-service` → `LightMakeStockServiceImpl.java`

### 配货前置校验

| 校验项 | 规则 |
|--------|------|
| 备货单状态 | 必须是 `WAIT`（待配货）或 `WAIT_CONFIRM`（下单待审核） |
| 服务商一致性 | 所有备货单必须同一服务商 |
| 项目一致性 | 所有电站必须同一项目 |
| 仓库启用 | 仓库状态必须 `ENABLE` |
| 服务商运营中 | 服务商状态必须 `ENABLE` |
| 采购单关联 | 组件类物料必须先有采购单(LightPreOrder)才能配货 |
| 额度校验 | 组件配货额度 = 功率(W) × 数量，不能超出服务商可用额度 |

### 配货流程

1. 选择备货单列表 + 物料 SKU 清单
2. 校验采购单关联（组件需先录入采购单，逆变器/配电箱自动关联）
3. 校验额度（组件占用额度，逆变器/配电箱不占额度）
4. 事务内：
   - 生成配货单 `LightPurchaseOrder`（状态 `WAIT_SEND_GOODS`）
   - 关联采购单 `LightPurchasePre`（配货单 ↔ 采购单关联表）
   - 更新备货单状态为 `FINISHED`，记录配货时间 `makeAt`
   - 更新方案配货状态 `LightStationPlanConfig.distributionStatus = YES`
   - 组件配货创建额度占用记录 `LightQuotaChange`（type=USED）

### 采购单自动关联策略

| 物料类型 | 关联策略 |
|---------|---------|
| 组件(预付款) | 必须手动录入采购单，配货时关联 |
| 组件(后付款) | 自动生成采购单，标记 `createPreOrderFlag=NO` |
| 逆变器 | 定时任务日汇总生成采购单 |
| 配电箱 | 定时任务日汇总生成采购单 |

### 配货方式

**代码路径**: `LightMakeStockServiceImpl.makeStockDirectly()`

| 方式 | 说明 |
|------|------|
| 自有仓库配货 (SELF_OWNED) | 从自有仓库发货 |
| 主仓库配货 (MAIN) | 从服务商主仓库发货 |
| 中转仓直配 (TRANSIT) | 从中转仓库直接发 |
| 第三方仓发 (FROM_THIRD_PARTY) | 从第三方供应商仓库发货 |
| 中转仓调拨 (TRANSIT_ALLOCATION) | 先调拨到中转仓再发 |

### 额度管理

- 额度单位: W（瓦）
- 组件额度计算: `quota = skuPower(W) × number`
- 额度流水: `LightQuotaChange`，type=USED 表示占用
- 项目维度: 某些项目不占额度 (`LightProjectManagement.occupyQuota = NO`)

### 相关表

| 表名 | 用途 |
|------|------|
| `light_purchase_order` | 配货单/采购发货单 |
| `light_pre_order` | 采购单（采购需求） |
| `light_purchase_pre` | 配货单与采购单关联关系 |
| `light_quota_change` | 额度变动流水 |
| `light_station_plan_config` | 方案配置（配货状态） |
| `light_order_to_pcs_queue` | SAP/PCS 订单推送队列 |

## 四、发货与签收

### 配货单状态机 (LightPurchaseOrder)

```
WAIT_SEND_GOODS(待发货) → WAIT_DELIVERY(发货中) → PART_IN(部分签收) → FINISHED(已签收)
```

### 发货流程

**接口**: `lightPurchaseOrderService.deliver()`

- 发货方式: `express`(快递)、`factory_direct`(工厂直发)
- 需要填写: 快递公司名称、编码、单号
- 发货后状态变为 `WAIT_DELIVERY` / `WAIT_IN`

### 签收入库

**接口**: `lightPurchaseOrderService.inStore()`

- 上传签收凭证 (signVoucherList，图片 URL 列表)
- 更新已签收数量 `inStoreNumber`
- 触发库存变更

### SAP 对接

- 组件预付款: 配货时创建 `LightSapPoQueue`（PO 记账队列）
- 日日顺对接: 配货单推送 WMS 系统出库（部分 SN 码逻辑已注释）

## 五、仓库体系

### 仓库类型

| 类型 | 实体类 | 说明 |
|------|--------|------|
| 主仓库 | `LightSpStore` (StoreType=MAIN) | 服务商一级仓库 |
| 二级仓库 | `LightSpAuclonStore` | 奥客隆仓库/子账号仓库 |
| 中转仓 | `LightSpStore` (StoreType=TRANSIT) | 中转仓库 |
| 三方仓 | `LightSpStore` (StoreType=THIRD_PARTY) | 第三方供应商仓库 |

### 配货单中的三个仓库字段

配货单 (`LightPurchaseOrder`) 同时涉及三个仓库，角色不同：

| 字段 | 实体类 | 作用 | 说明 |
|------|--------|------|------|
| `store_id` | `LightSpStore` | **收货主仓库** | 物料目的地，属于服务商 |
| `sub_store_id` | `LightSpAuclonStore` | **二级/奥客隆仓库** | VIP 模式下最终送达地址 |
| `delivery_store_id` | `LightSpStore` | **发货仓库** | 仅第三方仓/中转仓模式填写，实际发出物料的仓库 |

配货方式与仓库字段的关系：

| 配货方式 | delivery_store_id | store_id | sub_store_id |
|---------|-------------------|----------|-------------|
| 自有仓库 (SELF_OWNED) | 不适用 | 主仓库 | ✅ 需要 |
| 主仓库 (MAIN) | 不适用 | 主仓库 | ❌ 不需要 |
| 中转仓直配 (TRANSIT) | 不适用 | 中转仓 | ❌ 不需要 |
| 第三方仓发 (FROM_THIRD_PARTY) | ✅ 第三方仓 | 主仓库 | ✅ 需要 |
| 中转仓调拨 (TRANSIT_ALLOCATION) | ✅ 中转仓 | 主仓库 | ✅ 需要 |

### 仓库选择流程

1. 配货时调用 `LightMakeOrderService.getStoreList()` 获取可用仓库
2. 按仓库类型分组: 主仓库 (MAIN) / 二级仓库 (SECOND_CLASS)
3. 过滤条件: 仓库状态=ENABLE 且有有效收货地址

### 仓库地址

- `LightStoreAddress`：仓库收货地址表
- 配货时需选择有效地址作为送达地址

## 六、库存管理

### 库存 Service

**代码路径**: `rrsjk-light-service` → `LightStockService`, `SpStoreageService`

| 方法 | 功能 |
|------|------|
| `getStoreageList()` | 查询仓库可用库存 |
| `getStoreageTotalList()` | 查询仓库总库存 |
| `delete()` / `deleteBatchnum()` | 删除库存/按批次删除 |

### 出库规则

- 2026-04-29 变更：下发日日顺的组件订单**不再指定 SN 码出库**，SN 传递逻辑被整体注释
- 原因：20260429 韩程需求

### 安全库存

- `SpWarehouseAttachService.SynchronizeJob()` 定时同步安全库存

## 七、调拨

详见 `domains/inventory.md`，已知 5 种调拨类型：

| 类型 | 说明 |
|------|------|
| ORDINARY_TRANSFER | 普通调拨 |
| FROM_TRANSIT | 中转仓发货 |
| FROM_TRANSIT_TO_TRANSIT | 中转仓调中转仓 |
| REPAIR_TRANSFER | 备件调拨 |
| INTERNAL_TRANSFER | 商内调拨 |

调拨状态机：`WAIT_AUDIT → WAIT_TRANSFER → TRANSFERED → COMPLETED`

## 八、关键业务规则

1. **电站状态不可逆**：ROADWORKING（施工中）之后的电站不允许再走下单流程
2. **服务商退商拦截**：退商中的服务商无法下单
3. **额度控制**：只有组件占用配货额度，逆变器/配电箱不占
4. **采购单先行**：组件（预付款）必须先有采购单才能配货
5. **定时任务汇总**：逆变器、配电箱类配货单由定时任务日汇总后统一生成采购单
6. **领用提前**：备货下单同时创建领用单，完工前可提前领料
7. **项目维度管控**：同一批次配货的电站必须属于同一项目

## 来源

- `rrsjk-light-service`: `LightMakeOrderServiceImpl.java` (1063行)
- `rrsjk-light-service`: `LightMakeStockServiceImpl.java` (2612行)
- `rrsjk-light-service`: `LightConfirmOrderServiceImpl.java`
- `rrsjk-light-service`: `LightStation.java` (状态枚举)
- `rrsjk-light-service`: `LightPurchaseOrder.java` (配货单实体)
- `rrsjk-light-service`: `LightMakeOrder.java` (备货单实体)
- 代码扫描日期: 2026-05-24
