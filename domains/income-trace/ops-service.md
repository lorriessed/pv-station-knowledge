# 运维服务收入溯源

## 收入项基本信息
- **Doris 链群名**: ①运维收入
- **月实际收入**: 875.83万（2026-06-18），月目标 1,050万，完成率 83%
- **年累计收入**: 5,660.27万，年目标 15,000万，完成率 107%
- **责任人**: 方雪鹏
- **行业**: 绿能
- **排序**: 12

## 计算逻辑

### 核心公式
```
运维收入 = findOpsIncome(正向) - findOpsIncomeCx(冲销)
         = SUM(sap_record.ywms='A48' AND kunnr LIKE '88%' AND gjahr!='0000') 
           - SUM(sap_record.ywms='A48' AND kunnr LIKE '88%' AND gjahr='0000')
```

单位：原始数据为**元**，报表层 `/10000` 转为**万元**，保留 2 位小数。

### 涉及服务

| 服务 | 角色 | 代码路径 |
|------|------|----------|
| `rrsjk-finance-service` | SAP 记账数据查询 | `SapToReportServiceImpl.findOpsIncome()` |
| `rrsjk-light-report-service` | 报表聚合 + Doris 写入 | `EteOpsIncomeModel.create()` |
| `rrsjk-light-service` | 运维管理单创建 + A48 记账触发 | `OperationMaintenanceServiceImpl` / `OperationInstallServiceImpl` |
| `data_platform` (ETL) | Doris `energy_chain_group_income` 同步 | 非 Java 代码，由数据平台定时同步 |

### 核心方法链

```
1. EnergyJobServiceImpl.autoCreateEteIncomeDay()          [定时任务入口]
   ↓
2. EteOpsIncomeModel.create(dateTime, userName)           [运维收入模型]
   ↓
3. SapToReportServiceImpl.findOpsIncome(startTime, endTime)  [查询 SAP 记账]
   ↓
4. SapRecordDao.findOpsIncome() / findOpsIncomeCx()       [MyBatis DAO]
   ↓
5. SapRecordMapper.xml: findOpsIncome / findOpsIncomeCx   [SQL 执行]
   ↓
6. EnergyEteIncomeDayDao → energy_ete_income_day 表       [结果写入]
   ↓
7. data_platform ETL → Doris energy_chain_group_income    [最终报表]
```

### SQL 详情

**findOpsIncome（正向）**：
```sql
SELECT SUM(i.dmbtr - i.dmbtr2)
FROM sap_record r 
LEFT JOIN (SELECT * FROM sap_item_record GROUP BY row_id) i ON r.row_id = i.row_id
WHERE r.ywms IN ('A48')
  AND r.vouched_at >= #{startTime}
  AND r.vouched_at < #{endTime}
  AND i.kunnr LIKE '88%'
  AND r.gjahr != '0000'
```

**findOpsIncomeCx（冲销）**：
```sql
-- 同上，但 r.gjahr = '0000'
```

关键字段说明：
- `ywms = 'A48'`：运维收入和成本暂估（业务模式代码）
- `kunnr LIKE '88%'`：客户编码以 88 开头（特定运维客户）
- `gjahr != '0000'`：非冲销凭证（正向记账）
- `gjahr = '0000'`：冲销凭证（逆向冲销）
- `dmbtr - dmbtr2`：本币借方金额 - 本币贷方金额2（净额）
- `vouched_at`：凭证日期（按日期范围过滤）

## 数据源表

| 表名 | 数据库 | 角色 |
|------|--------|------|
| `sap_record` | rrsjk_finance | SAP 记账主记录（ywms、vouched_at、gjahr、row_id） |
| `sap_item_record` | rrsjk_finance | SAP 记账行项目（dmbtr、dmbtr2、kunnr） |
| `operation_maintenance` | rrsjk_light | 运维管理单（A48/A51 记账类型、状态机） |
| `operation_maintenance_station` | rrsjk_light | 运维管理单电站明细（按电站拆分成本） |
| `energy_ete_income_day` | rrsjk_light_report | ETE 日收入报表中间表 |
| `energy_chain_group_income` | ads (Doris/SelectDB) | 最终链群收入报表 |
| `light_sp_ops_settle` | rrsjk_light | SP 运维商月度结算账单 |

## 业务触发流

### A48 记账触发链路
```
运维管理单创建（手动/定时任务）
  → OperationMaintenanceServiceImpl 按项目公司+资产所属+电站模式分组
  → 生成 A48 记账类型记录（运维收入和成本暂估）
  → 写入 operation_maintenance 表
  → 保存电站明细到 operation_maintenance_station
  → SAP 记账队列 → sap_record 写入
  → 报表服务定时查询 sap_record → 聚合到 energy_ete_income_day
  → data_platform ETL → Doris energy_chain_group_income
```

### 状态机（operation_maintenance.status）
```
TO_BE_CONFIRMED(待确认) 
  → CONFIRMED(确认暂估) 
  → CONFIRM_INCOME(确认实际) 
  → CONFIRMED_SK(确认收款)
  
任何状态 → COVER_CONFIRMED / COVERED(冲销暂估)
```

### 记账类型（bookkeeping_type）
| 类型 | 含义 | 是否计入运维收入 |
|------|------|-----------------|
| A48 | 运维收入和成本暂估 | ✅ 是（核心） |
| A51 | 项目公司运维成本暂估 | ❌ 否（仅集团内成本） |
| BF | 保发收入 | ❌ 否（单独核算） |

### 定时任务
1. **`autoCreateEteIncomeDay()`** — 每日执行，调用 `EteOpsIncomeModel.create()` 生成当日运维收入
2. **`updateOperationMaintenanceStationCost()`** — 更新 A48 电站明细成本（检查运维商月度账单、新政策判定、基础费用 25 元/站）

## 资产所属分类（special_flag）
运维管理单按资产所属分组生成 A48 记录：
- 浦银（PF_1th / PY_ALL）
- 中核（ZH_1th / ZH_ALL / ZH_PHASE_1 / ZH_PHASE_2）
- 越秀（YX_EPC / YX_ALL / YX_GZ）
- 华电（CHD_EPC）
- 客户回购（CLIENT_BUY_BACK）
- 海尔新能源（NH）
- 顶好（DH_EPC）
- 广发 EPC（GF_EPC）

## 关键发现

1. **运维收入 = SAP A48 记账净额**：收入不是从业务表直接聚合，而是从 SAP 记账凭证（sap_record + sap_item_record）反查。这意味着收入确认依赖 SAP 记账成功，而非运维管理单创建。

2. **正向 - 冲销 双轨计算**：`findOpsIncome`（gjahr!='0000'）减 `findOpsIncomeCx`（gjahr='0000'），确保冲销记录被正确扣减。

3. **kunnr LIKE '88%'** 过滤条件：只统计客户编码以 88 开头的 SAP 行项目，这是运维收入的特定客户范围标识。

4. **ETE 报表 vs Doris 报表 双通道**：
   - ETE 通道：`EteOpsIncomeModel` → `energy_ete_income_day`（MySQL，分户用/多场景）
   - Doris 通道：`data_platform` ETL → `energy_chain_group_income`（最终展示）
   - 两个通道独立计算，可能存在差异

5. **历史数据修正**：`IncomeDayHouseHoldModel.createOps()` 中有 `2024-03-01` 之前的数据加 `533572.46` 的硬编码修正，说明早期数据存在口径差异。

6. **电站明细成本定时刷新**：`LightOperationScheduledJobServiceImpl.updateOperationMaintenanceStationCost()` 负责更新 A48 电站明细的成本（基础费用默认 25 元/站），有运维商的需要检查月度账单是否为新政策。

7. **运维服务(集团外) vs 运维服务**：`SapPurchaseRecord.PurchaseType` 枚举中 `LIGHT_OP_SERVER(18, "运维服务(集团外)")` 和 case 24 "运维服务" 是两个不同的采购类型，分别对应集团外和集团内运维。

## 来源
- `rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/sap/SapRecordMapper.xml` L443-461
- `rrsjk-finance-service/rrsjk-finance-impl/src/main/java/com/rrsjk/finance/sap/service/impl/SapToReportServiceImpl.java` L107-119
- `rrsjk-light-report-service/rrsjk-light-report-impl/src/main/java/com/rrsjk/report/service/model/EteOpsIncomeModel.java` 全文
- `rrsjk-light-report-service/rrsjk-light-report-impl/src/main/java/com/rrsjk/report/service/impl/EnergyJobServiceImpl.java` L1059-1070
- `rrsjk-light-report-service/rrsjk-light-report-impl/src/main/java/com/rrsjk/report/service/impl/GreenEnergyChainGroupIncomeServiceImpl.java` 全文
- `rrsjk-light-report-service/rrsjk-light-report-api/src/main/java/com/rrsjk/report/entity/local/GreenEnergyChainGroupIncome.java` L58
- `rrsjk-light-service/rrsjk-light-api/src/main/java/com/rrsjk/light/entity/OperationMaintenance.java` L206-247
- `rrsjk-light-service/rrsjk-light-impl/src/main/java/com/rrsjk/light/service/impl/OperationMaintenanceServiceImpl.java` L1824-1842
- `rrsjk-light-service/rrsjk-light-impl/src/main/java/com/rrsjk/light/service/impl/OperationInstallServiceImpl.java` L675-684
- `rrsjk-light-service/rrsjk-light-impl/src/main/java/com/rrsjk/light/service/job/LightOperationScheduledJobServiceImpl.java` L200-264
- Doris: `ads.energy_chain_group_income` WHERE chain_group='①运维收入' (2026-06-18)
- 扫描日期: 2026-06-19
