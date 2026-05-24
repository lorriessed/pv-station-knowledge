# 电站成本与政策体系

更新时间: 2026-05-24

本文档梳理电站正向流程及方案变更中涉及的所有**成本维度**和**政策激励体系**。

---

## 一、成本维度

### 1.1 物料成本

| 成本类型 | 计算方式 | 记账环节 | 说明 |
|---------|---------|---------|------|
| **组件成本** | 功率(W) × 数量 | 配货占用额度 → 领用扣减库存 → GVS 出库记账 | 核心成本，主料 |
| **逆变器成本** | SKU 单价 × 数量 | 同上 | 不占额度，走同样出库链路 |
| **辅材成本（四件套）** | SKU 价格 × 数量 | 同左 | 辅料，额度计算方式不同 |
| **配电箱成本** | SKU 单价 × 数量 | 同左 | 定时任务汇总生成采购单 |

### 1.2 额度体系（核心管控机制）

| 额度类型 | 计算公式 | 流水节点 |
|---------|---------|---------|
| **组件配货额度** | `功率(W) × 数量` | S8 下单：可用↓ 冻结↑；配货：USED 占用 |
| **辅材额度** | `实际金额 ÷ 0.5` | S8 下单：可用↓ 冻结↑；S11 签收：冻结↓ 签收↑；D13 核销：可用↑ 已核销↑ |
| **发货额度释放** | 领用出库时释放 | `LightQuotaChange.type=RELEASE`，主料=功率×数量，辅料=金额÷0.5 |

**代码路径**: `LightUseOrderServiceImpl.createQuotaChange()`, `LightMakeStockServiceImpl`

### 1.3 财务记账成本

| 记账项 | 接口/服务 | 说明 |
|-------|----------|------|
| **GVS SO 出库凭证** | `GvsOrderApi.soDeliver()` | 移动类型 291，返回 MBLNR 凭证号 + DMBTR 金额（无税成本总额） |
| **SAP 记账队列** | `SyncFinanceToSapService`（Dubbo 外部服务） | 组件预付款、领用出库、辅材费、服务费等 |
| **SAP 会计凭证** | `SapRecordService` | GVS 返回的 EX_BKPF（BELNR/GJAHR） |

**GVS 调用细节**:
- 移动类型: `BWART=291`（库存管理 - 工程领用出库）
- 请求: 领用单号(BSTKD)、工厂(WERKS)、服务商 V 码(XREF2)、电站编号(XREF3)、物料号(MATNR)、数量(ERFMG)
- 返回: MBLNR(凭证号)、DMBTR(金额)、EX_BKPF(会计凭证)

### 1.4 业主租金

- **触发时机**: 电站启用（ENABLE）后
- **计算依据**: 组件规格、数量、屋顶类型
- **重算触发**: 方案变更时若组件规格/数量/屋顶类型任一变化，触发 `STATION_RENT_RECREATE`

### 1.5 运维商成本

- **触发时机**: 完工审核通过时自动划转
- **依据**: 电站 regionId → 查询该区域已中标运维区域 → 取最新运维商 memberId
- **代码**: `LightOpAuthorityZoneServiceImpl.autoTransferStationOp()`

---

## 二、政策激励体系

### 2.1 基础政策（所有电站始终触发）

**代码**: `AbstractPolicyIncomeHandler.java`

| 政策项 | 说明 | SAP 记账类型 |
|-------|------|------------|
| **辅材费** | 四件套辅材费用结算 | A40 |
| **前 50% 服务费** | 前期服务费（安装前） | — |
| **后 50% 服务费** | 后期服务费（并网后） | — |
| **A88 领用** | 领用环节的 A88 记账 | A88 |

### 2.2 营销类政策

**代码**: `SpInspirePolicyIncomeHandlerImpl.java`

| 政策 | 触发条件 | 说明 |
|------|---------|------|
| **营销政策** | 服务商营销活动 | 按活动规则发放激励 |

### 2.3 并网时效政策

**代码**: `GridPolicyToDoStrategy` 等

| 政策 | 触发条件 | 说明 |
|------|---------|------|
| **并网时效激励** | 在规定时间内完成并网 | 鼓励快速并网，按时效等级发放 |
| **月度规模政策** | `LightAnnualScalePolicyMonthlyDetailIncomeHandlerImpl` | 按月度装机规模阶梯激励 |
| **安装提升政策** | `GridPolicyIncomeInstallAdvanceToDoStrategy` | 安装量提升激励 |

### 2.4 新商/区域政策

**代码**: `NewMerchantPolicyToDoStrategy.java`, `APolicyToDoStrategy.java`, `BPolicyToDoStrategy.java`

| 政策 | 触发条件 | 说明 |
|------|---------|------|
| **新商政策** | 新服务商入驻 | 新服务商扶持激励 |
| **A 段奖励** | A 段业务达成 | A 段业务激励 |
| **B 段奖励** | B 段业务达成 | B 段业务激励 |

### 2.5 启用政策

**代码**: `EnablePolicyToDoStrategy.java`

| 政策 | 触发条件 | 说明 |
|------|---------|------|
| **启用政策** | 电站状态变为 ENABLE | 电站并网启用时的一次性激励 |

### 2.6 政策策略统一流程（9 步标准流程）

每个政策策略都走相同的 9 步标准流程（`AbstractPolicyToDoStrategy` 模板方法 + `AbstractCollectionPolicyToDoStrategy` 基类）：

```
冲销阶段（6步）：
1. 获取原政策记录
2. 冲销政策记账（SAP 逆向）
3. 冲销政策金额（财务回滚）
4. 标记原记录失效
5. [空]
6. [空]

重建阶段（3步）：
7. 重新计算政策（按新方案）
8. 生成新政策记录
9. 生成新 SAP 记账 + 更新断点位图
```

**断点续传机制**: 政策策略用位图（bitmap）记录进度，失败可从中断点恢复，避免重复冲销。

**代码路径**: `AbstractPolicyToDoStrategy.java`, `AbstractCollectionPolicyToDoStrategy.java`, `reverse/strategy/policy/` 包下各实现

---

## 三、成本与政策在正向/变更流程中的流转

### 3.1 正向流程积累

```
物料出库 → 成本产生（GVS 凭证 DMBTR）
领用完成 → 基础政策记账（A40/A88）
电站启用 → 收入结算开始 + 各类政策激励发放
```

### 3.2 完工后方案变更冲销与重建

| 变更动作 | 冲销待办 | 重建待办 | 影响层面 |
|---------|---------|---------|---------|
| 库存回滚 | `RECOVER_STOCK` | — | 成本（库存层面） |
| 领用冲销 | `REVERSE_USE`（GVS 冲销） | `RE_USE`（重新领用） | 财务凭证 + 成本 |
| 基础政策 | `REVERSE_BASE_POLICY_INCOME` | `RE_BASE_POLICY_INCOME` | 辅材费/服务费/A88 |
| 电站收入 | `REVERSE_STATION_INCOME` | `RE_STATION_INCOME` | 资方收入结算 |
| 政策激励 | 各策略冲销步骤（1-6） | 各策略重建步骤（7-9） | 9 大类政策 |

---

## 四、核心服务清单

| 服务 | 文件 | 职责 |
|------|------|------|
| 领用出库 | `LightUseOrderServiceImpl.java` | 出库 + GVS 调用 + 额度释放 |
| 配货 | `LightMakeStockServiceImpl.java` | 配货 + 采购单关联 + 额度占用 |
| SAP 记账 | `SyncFinanceToSapService`（Dubbo） | 财务记账外部服务 |
| SAP 记录 | `SapRecordService`（Dubbo） | SAP 记录管理 |
| GVS 接口 | `GvsOrderApi.java` | SO 发货接口（移动类型 291） |
| 基础政策 | `AbstractPolicyIncomeHandler.java` | 基础政策 9 步流程 |
| 营销政策 | `SpInspirePolicyIncomeHandlerImpl.java` | 营销激励 |
| 并网政策 | `GridPolicyToDoStrategy` 等 | 并网时效/月度规模/安装提升 |
| 新商政策 | `NewMerchantPolicyToDoStrategy.java` | 新商/A段/B段激励 |
| 启用政策 | `EnablePolicyToDoStrategy.java` | 电站启用激励 |

---

## 来源

- `rrsjk-light-service` → `LightUseOrderServiceImpl.java`
- `rrsjk-light-service` → `LightMakeStockServiceImpl.java`
- `rrsjk-light-service` → `AbstractPolicyIncomeHandler.java`
- `rrsjk-light-service` → `AbstractCollectionPolicyToDoStrategy.java`
- `rrsjk-light-service` → `policyIncome/` 包
- `rrsjk-light-service` → `reverse/strategy/policy/` 包
- `rrsjk-light-service` → `GvsOrderApi.java`
- 代码扫描日期: 2026-05-24
