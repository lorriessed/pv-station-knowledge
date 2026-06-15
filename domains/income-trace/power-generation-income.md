# 发电收入 收入溯源

## 收入项
- **链群名称**: ②发电收入
- **所属产业**: 绿能 → 1.4-资产运营
- **月实际收入**: 872.61万（2026-06-14）
- **月目标**: 200万
- **月完成率**: 934.95%（大幅超额）
- **责任人**: /（总），户用子类：类成伟，自持子类：奚亚青
- **子项拆分**:
  - -户用: 855.98万（占 98.1%）
  - -自持: 16.63万（占 1.9%）

## 核心计算公式

```
发电收入 = (发电量 × 省份电价 - 租金成本) / 1.13
```

- **发电量**: 从 `light_inveter_data` 表按电站编号汇总（elec_day/elec_month），过滤 bind_status='YES' AND station_status!='STOP'
- **省份电价**: 河北省固定 0.3644 元/kWh；其他省份从 `light_city_elec_price` 表取
- **租金成本**: 从 `light_rent` 表取（after_year_price=日成本，before_year_price=月成本）
- **/1.13**: 去除 13% 增值税

## 计算逻辑

### 涉及服务
| 服务类 | 方法 | 作用 |
|--------|------|------|
| `IncomeDayHouseHoldModel` | `createElec()` | 户用发电收入计算（主路径） |
| `IncomeDaySocialModel` | `createElec()` | 多场景/社会化发电收入计算 |
| `SubchainGroupDayLightRecordModel` | `getHouseHoldElec()` | 子链群维度户用发电收入 |
| `LightEstimateRecordModel` | `createData()` | 按项目公司维度的发电估算 |
| `ReportScreenGridServiceImpl` | `getElectricIncome()` | 大屏展示用发电收益（独立路径） |

### 核心方法详解（IncomeDayHouseHoldModel.createElec）
1. 按省份获取户用备案电站列表 → `lightStationDao.findHouseHoldProvince()` + `findHouseHoldStation()`
2. 按省份汇总日/月发电量 → `lightInveterDataDao.findDayPower()` + `findMonthPower()`
3. 乘以省份电价 → `lightCityElecPriceDao.findElecPrice()`（河北省硬编码 0.3644）
4. 计算租金成本 → `lightRentDao.findCostByStationCode()`
5. 最终：`(发电收益 - 租金成本) / 1.13`

### SQL 核心逻辑
```sql
-- 日发电量汇总 (LightInveterData.xml:findDayPower)
SELECT sum(elec_day) as elec_day
FROM light_inveter_data
WHERE station_code IN (#{list})
  AND bind_status = 'YES'
  AND station_status != 'STOP'
  AND data_time_at >= #{startTime}

-- 月发电量汇总 (LightInveterData.xml:findMonthPower)
SELECT sum(elec_month) as elec_month
FROM light_inveter_data
WHERE station_code IN (#{list})
  AND bind_status = 'YES'
  AND station_status != 'STOP'
  AND data_time_at >= #{startTime}

-- 省份电价 (LightCityElecPrice.xml:findElecPrice)
SELECT elec_price FROM light_city_elec_price
WHERE province_name = #{provinceName}
```

## 数据源表

| 表名 | 数据库 | 角色 |
|------|--------|------|
| light_inveter_data | rrsjk_light_data | 逆变器发电数据（日/月/年发电量，核心数据源） |
| light_station | rrsjk_light | 电站主表（省份、备案类型HOUSEHOLD/COMPANY、项目公司） |
| light_city_elec_price | rrsjk_light | 省份电价配置（河北省除外，硬编码0.3644） |
| light_rent | rrsjk_light | 电站租金成本（after_year_price=日，before_year_price=月） |
| light_station_inverter | rrsjk_light | 电站-逆变器SN关联 |
| light_inveter | rrsjk_light_data | 逆变器日发电数据（按SN+日期查询，大屏路径使用） |
| light_station_plan_config | rrsjk_light | 电站方案配置（组件块数，用于成本计算） |
| light_company_policy | rrsjk_light | 项目公司政策（租金单价，用于成本计算） |
| light_station_elec | rrsjk_light_data | 电站发电汇总（大屏路径使用） |
| light_operation_elec_price | rrsjk_light_operation | 运营电价（大屏路径使用） |
| energy_income_day | local MySQL | 收入日报中间表（HOUSEHOLD/SOCIAL/INDUSTRY等type） |
| energy_subchain_group_target_reach | local MySQL | 子链群目标达成表 |
| green_energy_chain_group_income | local MySQL | 绿能链群收入快照 |
| energy_chain_group_income | Doris/ads | **最终收入报表**（data_platform ETL 写入） |

## 业务触发流

```
逆变器硬件 → 数据采集服务 → light_inveter_data 表更新
                                    ↓
定时任务（EnergyJobService）
    ├── autoCreateEnergyIncomeDay() → IncomeDayHouseHoldModel.createElec()
    ├── autoCreateSubchainGroupDayLightRecord() → SubchainGroupDayLightRecordModel.getHouseHoldElec()
    └── autoCreateLightEstimate() → LightEstimateRecordModel.createData()
                                    ↓
energy_income_day (local MySQL)
energy_subchain_group_target_reach (local MySQL)
                                    ↓
Doris ETL (data_platform 定时同步)
                                    ↓
energy_chain_group_income (Doris/ads) → "②发电收入" 行
                                    ↓
GreenEnergyChainGroupIncomeServiceImpl.create() → green_energy_chain_group_income (local MySQL 绿能子集)
```

## 关键发现

1. **发电收入远超目标**：月实际 872.61万 vs 月目标 200万（完成率 934.95%），说明发电量或电价假设远优于年初预算
2. **户用占绝对主体**：户用发电 855.98万 占 98.1%，自持仅 16.63万
3. **河北省特殊处理**：电价硬编码 0.3644 元/kWh，不从表取
4. **两条独立计算路径**：
   - 收入报表路径：`IncomeDay*Model.createElec()` → `energy_income_day` → Doris
   - 大屏展示路径：`ReportScreenGridServiceImpl.getElectricIncome()` → `report_screen_dashboard`
   - 两条路径使用不同的电价表（`light_city_elec_price` vs `light_operation_elec_price`），可能导致数据不一致
5. **去税处理**：所有发电收入都除以 1.13（13% VAT），这是不含税收入
6. **成本扣除**：户用电站需扣除租金成本（按组件块数×单价/365天），自持电站（COMPANY备案类型）无租金成本
7. **数据过滤条件**：发电量只统计 bind_status='YES' AND station_status!='STOP' 的电站，即已绑定且未停机的电站
8. **Doris 写入方**：`energy_chain_group_income` 的 `created_by = 'data_platform'`，说明是 Doris ETL 写入，非 Java 服务直接写入

## 来源
- 代码路径: `/data/pvcode/rrsjk-light-report-service/rrsjk-light-report-impl/src/main/java/com/rrsjk/report/service/model/IncomeDayHouseHoldModel.java` (line 249-389, createElec方法)
- 代码路径: `/data/pvcode/rrsjk-light-report-service/rrsjk-light-report-impl/src/main/java/com/rrsjk/report/service/model/IncomeDaySocialModel.java` (line 226-369, createElec方法)
- 代码路径: `/data/pvcode/rrsjk-light-report-service/rrsjk-light-report-impl/src/main/java/com/rrsjk/report/service/model/SubchainGroupDayLightRecordModel.java` (line 603-700, getHouseHoldElec方法)
- 代码路径: `/data/pvcode/rrsjk-light-report-service/rrsjk-light-report-impl/src/main/java/com/rrsjk/report/service/impl/ReportScreenGridServiceImpl.java` (line 386-411, getElectricIncome方法)
- SQL: `LightInveterData.xml` (findDayPower:169, findMonthPower:186)
- SQL: `LightCityElecPrice.xml` (findElecPrice:21)
- Doris 查询: `ads.energy_chain_group_income` (2026-06-14 数据)
- 扫描日期: 2026-06-15
