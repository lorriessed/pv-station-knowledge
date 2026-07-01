# 储能PCS 收入溯源

## 收入项基本信息
- **链群名称**: 3.2-储能PCS
- **所属行业**: 智控器
- **月实际收入**: 1,413.51万 (2026-06-30)
- **月目标**: 2,447.50万
- **月完成率**: 57.75% (预实大差)
- **年实际收入**: 9,659.48万
- **年目标**: 30,000.00万
- **责任人**: 李继祖

## 智控器整体结构 (2026-06-30)

| 链群 | 月收入(万) | 月目标(万) | 完成率 |
|------|-----------|-----------|--------|
| 小计 | 4,435.51 | 5,957.50 | 74.45% |
| 3.1-光伏逆变器 | 3,022.00 | 3,510.00 | 86.10% |
| 3.2-储能PCS | 1,413.51 | 2,447.50 | 57.75% |
| 列示：内单 | 2,620.97 | 2,447.50 | 107.09% |
| 列示：外单 | 80.55 | 1,080.00 | 7.46% |
| 列示：海外 | 320.00 | 450.00 | 71.11% |
| 列示：星能链外单 | 1,413.00 | 1,980.00 | 71.36% |
| 列示：场景方案 | 198.54 | 450.00 | 44.12% |

## 计算逻辑

### 数据来源
**关键发现**: 储能PCS收入数据由 **数据平台(data_platform)** ETL 写入 Doris `ads.energy_chain_group_income` 表，**不是**由 Java 服务直接计算。

- `created_by = 'data_platform'` 确认数据来自外部数据管道
- Java 服务 `EnergyChainGroupIncomeServiceImpl` 仅提供：
  1. 读取展示 (`findBy`)
  2. 手工调整 (`changeReport` → `recursionChange`)
  3. 向上汇总到"新能源合计"

### 汇总逻辑 (Java 代码)
文件: `rrsjk-light-report-service/.../EnergyChainGroupIncomeServiceImpl.java:238-268`

```java
// 新能源合计 = 绿能小计 + 储能小计 + 智控器小计 - 智控器内单
newReportValue = lightIncome.getMonthActualIncome()
    .add(storageIncome.getMonthActualIncome())
    .add(pcsIncome.getMonthActualIncome())      // 智控器小计
    .subtract(pcsInIncome.getMonthActualIncome()); // 减去内单(避免重复计算)
```

### PCS 订单业务流 (Java 代码)
文件: `rrsjk-trade-service/.../PcsOrderDeliveryToLightQueueServiceImpl.java`

PCS 硬件发货通过队列处理，支持3种订单类型：
1. **EPC** (工商业) → `CmPreOrderService.deliver()`
2. **LIGHT_STATION** (户用) → `LightPurchaseOrderService.deliver()`
3. **普通销售订单** → `LightPurchaseSalesPurchaseOrderService.deliver()`

## 数据源表

| 表名 | 数据库 | 角色 |
|------|--------|------|
| `energy_chain_group_income` | ads (Doris/SelectDB) | 收入报表主表，data_platform ETL 写入 |
| `energy_chain_group_income_change` | rrsjk_light_report (local) | 手工调整变更记录 |
| `sap_self_account` | rrsjk_finance | SAP 自营账户记录，corpCode='1Q80'为国内储能 |
| `sap_record` | rrsjk_finance | SAP 记账凭证，ywms 业务模式区分收入类型 |
| `pcs_order_delivery_to_light_queue` | rrsjk_trade | PCS 发货队列 |

## SAP 收入代码映射 (参考)

| ywms 代码 | 收入类型 | 相关链群 |
|-----------|---------|---------|
| H01, W21 | 4110光伏收入 | 光伏逆变器 |
| A57 | 光伏采销收入 | 光伏逆变器 |
| A63-A65 | 工商业EPC新流程 | 工商业链群 |
| A94-A96 | 整机收入 | 工商业链群 |
| 1Q80 (corpCode) | 国内储能 | 储能 |
| 4300 (corpCode) | 其他储能 | 储能 |

**注意**: 储能PCS的具体 SAP ywms 代码未在 Java 代码中找到，推测由数据平台 ETL 直接配置。

## 业务触发流

```
PCS硬件订单创建 (rrsjk_trade)
    ↓
PCS系统回调发货请求 (/pcsOrderDeliveryQueue/create.do)
    ↓
写入 pcs_order_delivery_to_light_queue 表
    ↓
定时任务 autoDelivery() 消费队列
    ↓
根据订单类型调用对应 deliver() 方法
    ↓
SAP 记账 (sap_record / sap_self_account)
    ↓
数据平台 ETL 聚合 (data_platform)
    ↓
写入 Doris ads.energy_chain_group_income
    ↓
报表展示 / 手工调整
```

## 关键发现

1. **数据平台主导**: 储能PCS收入计算逻辑不在 Java 代码中，而是由外部数据平台 ETL 完成。Java 服务仅负责展示和手工调整。

2. **内单扣减逻辑**: 智控器"小计"包含内单和外单，但在汇总到"新能源合计"时需要减去"列示：内单"，避免集团内部交易重复计算。

3. **PCS 发货队列**: PCS 硬件发货通过异步队列处理，支持 EPC/户用/普通销售三种模式，由 PCS 系统回调触发。

4. **收入结构**: 储能PCS月收入1,413万中，星能链外单占1,413万（几乎全部），说明当前储能PCS收入主要来自星能链渠道的外单业务。

5. **完成率偏低**: 月完成率57.75%，评价为"预实大差"，需要关注业务进展。

## 待深入分析

- [ ] 数据平台 ETL 的具体 SQL/聚合逻辑（需要查看数据平台配置）
- [ ] 储能PCS对应的 SAP ywms 业务模式代码
- [ ] 星能链渠道的具体业务含义和收入确认时点

## 来源
- 代码路径: `/data/pvcode/rrsjk-light-report-service/`, `/data/pvcode/rrsjk-trade-service/`, `/data/pvcode/rrsjk-finance-service/`
- 扫描日期: 2026-07-01
- Doris 数据日期: 2026-06-30
