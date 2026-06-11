# 微慕户储 收入溯源

## 收入项基本信息
- **月实际**：~725.83万（2026-06-10 Doris 数据），占户储总 742.41万的 97.8%
- **年累计**：27,758.92万（2026-06-10）
- **月目标**：11,470万，月完成率 18.98%（预实大差）
- **年目标**：120,000万，年完成率 69.02%（预实大差）
- **责任人**：王敏
- **业务分类**：储能 → 户储 → 微慕（并购渠道）
- **Doris 链群名**：`chain_group = '微慕'`, `industry = '储能'`
- **代码扫描日期**：2026-06-11

## 收入构成公式

```
微慕户储收入 = Σ(vm_order_bill.total_money WHERE kind='户储' AND voucher_time >= 统计起始日) / 10000
```

- 单位：元 → 万元（除以 10000）
- 时间窗口：从 `2024-07-01 00:00:00` 起（硬编码下限）
- 2024年1月查询时额外追加历史收入：户储 +1,905万（硬编码，见 L651）

### 微慕收入四分类
| kind 中文名 | kind 代码 | 对应收入项 | 月实际(万) |
|------------|----------|-----------|-----------|
| 户储 | HC | 微慕户储 | ~725.83 |
| 工商储 | GSC | 微慕工商储 | （包含在储能并购中） |
| 通信备电 | TXBD | 微慕通信备电 | （包含在储能并购中） |
| 多场景 | DCJ | 微慕多场景 | （包含在储能并购中） |

## 计算逻辑

### 核心服务
| 服务类 | 路径 | 角色 |
|--------|------|------|
| `VmOrderServiceImpl` | `rrsjk-light-report-service/.../service/impl/VmOrderServiceImpl.java` | 从微慕外部系统拉取订单和凭证数据（211行） |
| `EnergyStatisticIncomeModel` | `rrsjk-light-report-service/.../service/model/EnergyStatisticIncomeModel.java` | 储能收入按市场划分自动统计（665行），含微慕收入计算 |
| `SubchainGroupDayStorageModel` | `rrsjk-light-report-service/.../service/model/SubchainGroupDayStorageModel.java` | 储能链群达标计算，含"储能并购"子链群（780行） |
| `GreenEnergyChainGroupIncomeServiceImpl` | `rrsjk-light-report-service/.../service/impl/GreenEnergyChainGroupIncomeServiceImpl.java` | 绿能报表展示层，从 Doris 读取并格式化 |

### 核心方法链路
```
[数据拉取]
VmOrderServiceImpl.findOrderFromVm()           -- 定时任务入口 (L44-64)
  → getVmVoucherInfo(token, startDate, endDate) -- 拉取记账凭证 (L157-196)
    → POST {vm.url}/admin/login                 -- 获取 token (L86-105)
    → GET {vm.url}/pmc/pmcPingzheng/queryPing   -- 拉取凭证数据，分页 (L157-196)
    → vmOrderBillDao.batchInsert()              -- 写入 vm_order_bill 表
  → getVmOrder(token)                            -- 拉取订单详情 (L107-155)
    → GET {vm.url}/pmc/pmcSale/querySale         -- 拉取订单数据，分页 (L107-155)
    → vmOrderDao.batchInsert()                   -- 写入 vm_order 表

[收入统计]
EnergyStatisticIncomeModel.autoStatistic(now)    -- 储能收入自动统计 (L65-327)
  → findVmIncomeByScope(startTime, endTime)      -- 并购渠道收入 (L602-638)
    → vmOrderBillDao.getOrderIncomeByTime()      -- SQL: 按 kind 分组汇总 total_money
    → 按 kind 映射: DCJ/GSC/HC/TXBD
    → ÷ 10000 转换为万元
    → addVmHistoryIncomeByScope()                -- 2024年1月追加历史收入 (L640-663)
    → incomeReports[14].setMonthIncome(HC)       -- 微慕户储 (sort=14)
    → incomeReports[11].setMonthIncome(total)    -- 微慕合计 (sort=11, scope='微慕')
  → energyStatisticIncomeReportDao.batchInsert() -- 写入 energy_statistic_income_report

[链群达标]
SubchainGroupDayStorageModel.create()            -- 储能链群达标计算 (L88+)
  → "储能并购"子链群 (L308-352)
    → vmOrderBillDao.findSumByTime()             -- SQL: SUM(total_money) 不分 kind
    → ÷ 10000 转换为万元
    → 日/月/年累计计算
```

### 关键 SQL

**微慕收入按类型统计** (`VmOrderBill.xml` L194-202)：
```sql
SELECT sum(total_money) as incomeCny,
       CASE kind 
         WHEN '多场景' THEN 'DCJ' 
         WHEN '工商储' THEN 'GSC' 
         WHEN '户储' THEN 'HC' 
         WHEN '通信' THEN 'TXBD' 
         ELSE '' 
       END as kind
FROM vm_order_bill
WHERE enabled = 1 
  AND voucher_time >= '2024-07-01 00:00:00'
  AND voucher_time >= #{startTime}
  AND voucher_time < #{endTime}
GROUP BY kind
```

**微慕总收入（不分类型）** (`VmOrderBill.xml` L185-192)：
```sql
SELECT sum(total_money)
FROM vm_order_bill
WHERE voucher_time >= #{startTime}
  AND voucher_time < #{endTime}
```

## 数据源表

| 表名 | 数据库 | 角色 | 关键字段 |
|------|--------|------|----------|
| `vm_order_bill` | rrsjk_light_report (本地MySQL) | 微慕记账凭证表（收入核心来源） | `bill_id`, `order_num`, `voucher_num`, `voucher_type`, `voucher_time`, `total_money`(收入金额), `kind`(户储/工商储/通信/多场景) |
| `vm_order` | rrsjk_light_report (本地MySQL) | 微慕订单明细表（补充信息） | `order_num`, `order_create_time`, `status`, `customer_name`, `tax_price`, `tax_total`, `not_tax_price`, `not_tax_total`, `quantity`, `sku`, `kind` |
| `energy_statistic_income_report` | rrsjk_light_report (本地MySQL) | 储能收入统计报表中间表 | `scope`(全球/国内/海外/微慕), `product_category`, `month_income`, `year_income`, `close_date` |
| `energy_statistic_income_target` | rrsjk_light_report (本地MySQL) | 储能收入目标表 | `year`, `month`, `scope`, `product_category`, `target_value` |
| `energy_subchain_group_target_reach` | rrsjk_light_report (本地MySQL) | 链群达标中间表 | `chain_group='储能'`, `subchain_group='储能并购'` |
| `energy_chain_group_income` | Doris/ads | 链群收入报表（最终展示） | `industry='储能'`, `chain_group='微慕'`, `month_actual_income`, `year_actual_income` |
| `green_energy_chain_group_income` | rrsjk_light_report (本地MySQL) | 绿能报表本地缓存 | 从 Doris 读取后写入 |

## 业务触发流

```
[外部系统] 微慕(VM)系统产生销售订单和记账凭证
    ↓
[定时拉取] VmOrderServiceImpl.findOrderFromVm()
    ├─ Step1: 获取 token → POST {vm.url}/admin/login
    ├─ Step2: 拉取凭证 → GET {vm.url}/pmc/pmcPingzheng/queryPing
    │     → 解析: id, order_num(num), voucher_num(code), voucher_type(type), 
    │             voucher_time(time), total_money(money), kind(kind), digest(digest)
    │     → 写入 vm_order_bill 表
    └─ Step3: 拉取订单 → GET {vm.url}/pmc/pmcSale/querySale
          → 解析: code, date, state, vendorname, vendornum, taxprice, sum, price, money, 
                  typename, quantity, bom, inventoryname, invstd, kind
          → 写入 vm_order 表
    ↓
[定时统计] EnergyJobService.autoStatistic() → EnergyStatisticIncomeModel.autoStatistic()
    → findVmIncomeByScope(firstDayOfMonth, endOfDay)
    → vmOrderBillDao.getOrderIncomeByTime(): 按 kind 分组汇总 total_money
    → kind 映射: 户储→HC, 工商储→GSC, 通信→TXBD, 多场景→DCJ
    → 金额 ÷ 10000 转万元
    → 写入 energy_statistic_income_report 表
    ↓
[链群达标] EnergyJobService.updateSubchain() → SubchainGroupDayStorageModel.create()
    → "储能并购"子链群: vmOrderBillDao.findSumByTime() 汇总全部微慕收入
    → 写入 energy_subchain_group_target_reach 表
    ↓
[数据同步] 数据管道 (Flink/DataX) 同步到 Doris
    → 本地 MySQL → Doris ads.energy_chain_group_income
    → 由 data_platform 用户写入（Doris 数据源标识）
    ↓
[报表展示] GreenEnergyChainGroupIncomeService.findList()
    → 从 Doris 读取 ads.energy_chain_group_income
    → 按 ChainGroupEnum 映射到绿能报表
    → 微慕 = 独立链群 (sort=23)
```

## 关键发现

1. **收入本质是"外部系统记账凭证汇总"**：微慕户储收入不是从电站发电量或 SAP 结算计算出来的，而是直接从微慕外部 ERP/PMC 系统的记账凭证（`pmcPingzheng`）拉取 `total_money` 字段汇总。这是一个**订单级收入**，不是电站运营级收入。

2. **两条收入统计链路并行存在**：
   - `EnergyStatisticIncomeModel.autoStatistic()` → `findVmIncomeByScope()` → 按 kind 分四类（HC/GSC/TXBD/DCJ），写入 `energy_statistic_income_report`
   - `SubchainGroupDayStorageModel.create()` → `findSumByTime()` → 不分 kind，汇总全部微慕收入到"储能并购"子链群
   
   两者计算逻辑不同（一个分类型，一个不分），但底层数据源都是 `vm_order_bill.total_money`。

3. **数据时间下限硬编码**：`getOrderIncomeByTime` SQL 中 `voucher_time >= '2024-07-01 00:00:00'`（L198），这意味着 2024-07-01 之前的凭证不会被自动计入，需依赖 `addVmHistoryIncomeByScope()` 中的硬编码历史数据补偿。

4. **历史收入硬编码**：2024年1月统计全年时，硬编码追加：户储 +1,905万、工商储 +3,484万、通信备电 +9,161万、多场景 +989万、合计 +15,539万（L649-653）。之前有另一套注释掉的数值（L644-648），说明历史数据口径有过调整。

5. **微慕 API 依赖**：收入计算完全依赖外部微慕系统的 3 个 API（登录、凭证查询、销售查询）。如果微慕系统不可用或 API 变更，收入数据将中断。当前使用分页拉取（pageSize=50），数据量大时可能较慢。

6. **未税/含税双金额**：`vm_order` 表同时存储含税金额（`tax_total`/`sum`）和未税金额（`not_tax_total`/`money`），但收入计算使用的是 `vm_order_bill.total_money`（来自凭证的 `money` 字段），对应未税金额。

7. **kind 映射不一致**：微慕原始 `kind` 值是中文（"户储"/"工商储"/"通信"/"多场景"），SQL 中 CASE WHEN 映射为代码（HC/GSC/TXBD/DCJ），但 `vm_order` 和 `vm_order_bill` 实体中 `kind` 字段仍存储中文。需注意报表展示时的映射关系。

8. **Doris 数据由 data_platform 写入**：`energy_chain_group_income` 表的 `created_by = 'data_platform'`，说明数据通过数据管道同步，应用层不直接写入 Doris。

## 来源
- 代码路径：`/data/pvcode/rrsjk-light-report-service/rrsjk-light-report-impl/src/main/java/com/rrsjk/report/`
- 核心文件：
  - `service/impl/VmOrderServiceImpl.java` (全文件 211行)
  - `service/model/EnergyStatisticIncomeModel.java` (L65-327 autoStatistic, L602-663 findVmIncomeByScope)
  - `service/model/SubchainGroupDayStorageModel.java` (L308-352 储能并购)
  - `service/impl/GreenEnergyChainGroupIncomeServiceImpl.java` (L47-84)
  - `entity/local/VmOrder.java` (全文件 90行)
  - `entity/local/VmOrderBill.java` (全文件 64行)
- Mapper：
  - `mybatis/mapper/local/VmOrderBill.xml` (L194-202 getOrderIncomeByTime, L185-192 findSumByTime)
  - `mybatis/mapper/local/VmOrder.xml` (全文件)
  - `mybatis/mapper/ads/EnergyChainGroupIncome.xml`
- Doris 查询验证：2026-06-11 确认微慕月实际 725.83万（06-10），年累计 27,758.92万
