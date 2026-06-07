# 光伏逆变器 收入溯源

## 收入项基本信息
- **链群名称**: 3.1-光伏逆变器（智控器行业下）
- **月收入**: ~2,674万（2026-05-31月末值 2,818.35万；最新日 2026-06-06 月累计 8,258.95万）
- **日收入**: 200-600万/日（取决于SAP记账节奏）
- **责任人**: 熊伟
- **行业**: 智控器（产业编码 ZN）
- **公司编码**: 1TP0（海尔新能源）

## 计算逻辑

### 总体架构
光伏逆变器收入属于**智控器产业**，分为**国内**和**海外**两条计算链路。收入计算在报表服务的定时任务中每日执行，结果写入 MySQL 中间表，再通过 ETL 同步到 Doris 报表库。

### 定时任务入口
- **Service**: `EnergyJobServiceImpl.updateSubchainRecord()` (`rrsjk-light-report-service/.../EnergyJobServiceImpl.java:869`)
- **核心调用**: `subchainGroupDayControllerModel.create(dateTime, userName)` (L877)
- **执行频率**: 手动触发（也可通过定时任务调用 `autoCreate...` 方法）

### 国内收入计算（主力）
- **Model**: `SubchainGroupDayControllerModel.create()` (`rrsjk-light-report-service/.../SubchainGroupDayControllerModel.java:44`)
- **核心方法**: `sapToReportService.find1TP0Income(startTime, endTime)` (L100/L104/L108)
- **公式**: `SUM(sap_self_account.sdaexp) / 1.13 / 10000`
  - `sdaexp` = SAP含税总金额（来自SAP记账）
  - `/1.13` = 去除13%增值税，得到未税收入
  - `/10000` = 元转万元
- **过滤条件**: `corpCode = '1TP0'`（海尔新能源），按 `addTime` 时间范围聚合
- **时间粒度**:
  - 当日收入: `find1TP0Income(昨天0点, 今天0点)`
  - 月度收入: `find1TP0Income(本月1日, 今天0点)`
  - 年度收入: `find1TP0Income(本年1月1日, 今天0点)`

### 海外收入计算
- **来源1**: `energyOverseasIncomeMonthDao.findByStartTime("1TP0", ...)` (L129)
  - 从 `energy_overseas_income_month` 表获取 1TP0 公司月度海外收入
  - 该表由 `EnergyOverseasIncomeServiceImpl` 手动录入或API写入
- **来源2**: `obsOrderDao.findDsoIncome("MQ", ...)` (L136)
  - 从 `obs_order` + `obs_order_item` 表查询 DSO 订单收入
  - `prod_type = 'MQ'`（MQ = 逆变器产品大类）
  - `order_type = 'dso_order'`
  - 按 `send_gvs_date` 过滤
  - 聚合: `SUM(obs_order_item.non_tax_amount)`（未税金额）
- **来源3**: `obsOrderDao.findNoDsoIncome("MQ", ...)` (L143)
  - 非 DSO 订单收入
  - `order_type != 'dso_order'`
  - 聚合: `SUM(obs_order.amount_cny)`（人民币金额）

### 智控器小计聚合
- **公式**（`EnergyChainGroupIncomeServiceImpl.recursionChange()` L248-252）:
  ```
  新能源合计 = 绿能小计 + 储能小计 + 智控器小计 - 智控器列示:内单
  ```
- **智控器小计** = 国内 + 海外（子链群累加）
- **列示:内单** 需要减去，避免内部交易重复计算

### 数据流到 Doris
1. `SubchainGroupDayControllerModel` 计算结果写入 MySQL: `energy_subchain_group_target_reach`
2. ETL 同步: MySQL → Doris (ads 库) → `energy_chain_group_income`
3. Doris 中链群名称映射: "能源控制器-国内" → "3.1-光伏逆变器"（industry='智控器'）

## 数据源表

| 表名 | 数据库 | 角色 | 关键字段 |
|------|--------|------|----------|
| `sap_self_account` | rrsjk_finance (MySQL) | 国内SAP记账数据源 | corpCode='1TP0', sdaexp(含税总额), addTime |
| `energy_subchain_group_target_reach` | rrsjk_light_report (MySQL) | 日/月/年目标达成中间表 | chainGroup, subchainGroup, monthActual, yearActual |
| `energy_subchain_group_target` | rrsjk_light_report (MySQL) | 目标配置表 | chainGroup='能源控制器', monthTarget, yearTarget |
| `energy_overseas_income_month` | rrsjk_light_report (MySQL) | 海外月收入（手动/API录入） | companyCode='1TP0', monthAmount |
| `obs_order` | rrsjk_light_report (MySQL) | 海外订单（OBS系统） | prod_type='MQ', order_type, send_gvs_date, amount_cny |
| `obs_order_item` | rrsjk_light_report (MySQL) | 海外订单明细 | obs_order_id, non_tax_amount |
| `energy_chain_group_income` | ads (Doris/SelectDB) | 最终报表展示 | industry='智控器', chain_group='3.1-光伏逆变器', month_actual_income |
| `energy_chain_group_income_change` | rrsjk_light_report (MySQL) | 收入变更审计日志 | oldReportValue, newReportValue, reportDifference |

## 业务触发流

```
[SAP记账] → sap_self_account 插入记录 (corpCode='1TP0', sdaexp含税金额)
    ↓
[定时任务: EnergyJobServiceImpl.updateSubchainRecord]
    ↓
[SubchainGroupDayControllerModel.create]
    ├── 国内: sapToReportService.find1TP0Income() → SUM(sdaexp)/1.13/10000
    └── 海外: energy_overseas_income_month + obs_order(DSO+非DSO)
    ↓
[写入 MySQL] energy_subchain_group_target_reach (chainGroup='能源控制器')
    ↓
[ETL同步] MySQL → Doris (ads.energy_chain_group_income)
    ↓
[报表展示] industry='智控器', chain_group='3.1-光伏逆变器'
    ↓
[手动调整] EnergyChainGroupIncomeServiceImpl.changeReport() → recursionChange() 级联更新父级
```

## 关键发现

1. **收入本质是SAP产品销售记账**: 光伏逆变器收入不是发电收入，而是**设备销售收入**。通过SAP销售订单记账到 `sap_self_account` 表，`sdaexp` 字段记录含税总金额。

2. **税率处理**: 国内收入统一按 ÷1.13 去除13%增值税后计入报表，体现的是**未税收入**。

3. **国内是主力**: 国内收入占比远高于海外（从日数据看国内单日可达200-600万，海外仅20-30万/日）。

4. **海外收入双来源**: 海外收入 = 手动录入月报表(`energy_overseas_income_month`) + OBS系统订单(`obs_order`的DSO和非DSO订单)，prod_type='MQ' 对应逆变器品类。

5. **内单冲销机制**: `列示:内单` 在汇总到"新能源合计"时被减去，避免集团内部交易重复计算。

6. **手动调整支持**: `EnergyChainGroupIncomeServiceImpl.changeReport()` 支持手动修正报表值，并通过 `recursionChange()` 级联更新从子链群到父链群（智控器小计 → 新能源合计）的所有层级。

7. **代码与报表名称不完全一致**: 代码中使用"能源控制器"作为 chainGroup，但 Doris 报表中显示为"3.1-光伏逆变器"、"3.2-储能PCS"等编号名称，中间通过 `energy_subchain_group_target` 配置表映射。

## 来源
- 代码扫描日期: 2026-06-07
- 核心代码路径:
  - `rrsjk-light-report-service/.../SubchainGroupDayControllerModel.java` (397行)
  - `rrsjk-finance-service/.../SapToReportServiceImpl.java` (L59-68)
  - `rrsjk-finance-service/.../OrderToSapSelfAccountDao.java` + `OrderToSapSelfAccountMapper.xml`
  - `rrsjk-light-report-service/.../EnergyJobServiceImpl.java` (L869-886)
  - `rrsjk-light-report-service/.../EnergyChainGroupIncomeServiceImpl.java` (L238-358)
  - `rrsjk-light-report-service/.../ObsOrder.xml` (findDsoIncome/findNoDsoIncome SQL)
- Doris 数据验证: `ads.energy_chain_group_income` WHERE industry='智控器' (2026-06-06)
