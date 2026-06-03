# 农村户用 收入溯源

## 收入项基本信息
- **月实际**：~55,935万（5月），月目标 60,000万，完成率 ~95%
- **责任人**：类成伟
- **链群枚举**：`GreenEnergyChainGroupIncome.ChainGroupEnum.HOUSE_HOLD`
- **Doris 表名**：`ads.energy_chain_group_income`，字段 `chain_group = '农村户用'`
- **代码扫描日期**：2026-06-03

## 收入构成公式

```
农村户用收入 = Σ(各省电站发电量 × 该省电价) - Σ(各省电站租金成本)
```

### 电价规则
- **河北省**：固定电价 0.3644 元/kWh（硬编码）
- **其他省份**：从 `light_city_elec_price` 表按省份查询

### 成本规则
- **日成本**：`light_rent.after_year_price`（过了第一年后的日租金）
- **月成本**：`light_rent.before_year_price`（第一年内的月租金）
- 成本按电站绑定时间（`light_inveter_data.bind_at`）与当月/当年首日比较计算天数

## 计算逻辑

### 核心服务
| 服务类 | 路径 | 角色 |
|--------|------|------|
| `SubchainGroupDayLightRecordModel` | `rrsjk-light-report-service/.../service/model/SubchainGroupDayLightRecordModel.java` | 收入计算核心（845行） |
| `GreenEnergyChainGroupIncomeServiceImpl` | `rrsjk-light-report-service/.../service/impl/GreenEnergyChainGroupIncomeServiceImpl.java` | 报表展示层，从 Doris 读取并格式化 |
| `EnergyChainGroupIncomeServiceImpl` | `rrsjk-light-report-service/.../service/impl/EnergyChainGroupIncomeServiceImpl.java` | 报表查询 + 手工调账（recursionChange 向上递归汇总） |

### 核心方法
```
SubchainGroupDayLightRecordModel.createData()         -- 光伏链群日/月/年达标计算入口 (L82)
  → getHouseHoldElec(dateTime)                        -- 户用收入计算核心 (L603-707)
    → lightRentDao.findProvince()                     -- 获取所有省份
    → lightRentDao.findStationIdByProvince()           -- 按省获取电站ID
    → lightStationInverterDao.findByStationId()        -- 获取逆变器SN列表
    → lightInveterDao.findByFetchAt()                  -- 获取当日/月/年发电量
    → lightCityElecPriceDao.findElecPrice()            -- 获取省份电价
    → lightRentDao.findCostByStationCode()             -- 获取租金成本
```

### 关键代码片段（L603-707）
```java
// 遍历每个省份 → 每个电站 → 每个逆变器
province.forEach(s -> {
    stationIdList.forEach(stationId -> {
        inverterSNList.forEach(inverterSN -> {
            LightInveter elec = lightInveterDao.findByFetchAt(inverterSN, date);
            power.setDay(power.getDay().add(elec.getEToday()));   // 日发电量累加
            power.setMonth(power.getMonth().add(elec.getEMonth())); // 月发电量累加
            power.setYear(power.getYear().add(elec.getEYear()));    // 年发电量累加
        });
        // 成本计算
        LightRent rent = lightRentDao.findCostByStationCode(param);
        cost.setDay(cost.getDay().add(rent.getAfterYearPrice()));
        cost.setMonth(cost.getMonth().add(rent.getBeforeYearPrice()));
    });
    // 收入 = 发电量 × 电价
    income.setMonth(income.getMonth().add(power.getMonth().multiply(elecPrice)));
});
// 最终：收入 = 发电收益 - 成本
income.setMonth(income.getMonth().subtract(cost.getMonth()));
```

## 数据源表

| 表名 | 数据库 | 角色 | 关键字段 |
|------|--------|------|----------|
| `light_rent` | rrsjk_light | 屋顶租赁合同/成本 | `province_name`, `station_code`, `before_year_price`(月成本), `after_year_price`(日成本), `status` |
| `light_station` | rrsjk_light | 电站基本信息 | `station_code`, `station_id` |
| `light_station_inverter` | rrsjk_light | 电站-逆变器绑定关系 | `station_id`, `inveter_sn` |
| `light_inveter` | rrsjk_light_data | 逆变器发电量日快照 | `inveter_sn`, `fetch_at`, `e_today`, `e_month`, `e_year` |
| `light_inveter_data` | rrsjk_light_data | 逆变器绑定时间 | `station_code`, `bind_at` |
| `light_city_elec_price` | rrsjk_light | 省份电价配置 | `province_name`, `elec_price` |
| `energy_subchain_group_target_reach` | rrsjk_light_report (本地MySQL) | 链群达标中间表 | `chain_group='光伏'`, `subchain_group='户用'`, `month_actual`, `year_actual` |
| `energy_chain_group_income` | Doris/ads | 链群收入报表（最终展示） | `chain_group='农村户用'`, `month_actual_income`, `year_actual_income` |
| `green_energy_chain_group_income` | rrsjk_light_report (本地MySQL) | 绿能报表本地缓存 | 从 Doris 读取后写入本地 |
| `energy_chain_group_income_change` | rrsjk_light_report (本地MySQL) | 手工调账记录 | `old_report_value`, `new_report_value`, `report_difference` |

## 业务触发流

```
[逆变器采集] 逆变器定时上报发电量
    → light_inveter 表写入 e_today/e_month/e_year
    → fetch_at = 采集日期

[定时任务] EnergyJobService.updateSubchainRecord() 触发
    → SubchainGroupDayLightRecordModel.createData() 执行
    → getHouseHoldElec() 遍历 省份→电站→逆变器
    → 计算：发电量 × 电价 - 租金成本
    → 写入 energy_subchain_group_target_reach (本地MySQL)

[数据同步] 数据管道 (Flink/DataX) 同步到 Doris
    → energy_subchain_group_target_reach → ads.energy_chain_group_income

[报表展示] GreenEnergyChainGroupIncomeService.findList()
    → 从 Doris 读取 ads.energy_chain_group_income
    → 按 ChainGroupEnum 映射到绿能报表
    → 农村户用 = HOUSE_HOLD 枚举 (sort=2)

[手工调账] EnergyChainGroupIncomeService.changeReport()
    → 运营人员手动调整收入值
    → recursionChange() 递归向上汇总父链群（小计→新能源合计）
    → 记录到 energy_chain_group_income_change 表
    → 发送 Kafka 消息通知更新
```

## 关键发现

1. **收入本质是"发电净收益"而非"SAP 结算收入"**：农村户用收入 = 发电量 × 电价 - 屋顶租金。这是一个估算/统计值，不是基于 SAP 实际记账的财务收入。

2. **电价有省份差异**：河北固定 0.3644 元/kWh（可能是脱硫煤标杆电价），其他省份从配置表读取。这意味着收入计算强依赖 `light_city_elec_price` 表的配置准确性。

3. **成本按年度分段**：`before_year_price` 用于第一年（月成本），`after_year_price` 用于后续年份（日成本）。这反映了屋顶租赁合同的不同阶段定价策略。

4. **逆变器粒度计算**：收入计算遍历到每个逆变器级别，按 `station → inverter → fetch_at` 三级查询。电站数量多时性能开销大（N² 查询模式）。

5. **年度数据有 BUG**：L153 处 `entity.setYearActual(monthHouseHoldElec)` — 年度实际值直接使用了月度值，`year` 计算结果被注释掉了（L151-152）。这意味着年度累计收入可能不准确。

6. **Doris 表只有 UPDATE 没有 INSERT**：`EnergyChainGroupIncomeDao` 只有 `update` 和 `findBy` 方法，初始数据由外部数据管道写入，应用层只能更新。

7. **手工调账支持递归汇总**：修改某个子链群收入后，`recursionChange()` 会自动向上递归更新父链群（如修改"农村户用"→ 自动更新"绿能小计"→ "新能源合计"）。

## 来源
- 代码路径：`/data/pvcode/rrsjk-light-report-service/rrsjk-light-report-impl/src/main/java/com/rrsjk/report/`
- 核心文件：
  - `service/model/SubchainGroupDayLightRecordModel.java` (L82-178, L603-707)
  - `service/impl/GreenEnergyChainGroupIncomeServiceImpl.java` (L47-84)
  - `service/impl/EnergyChainGroupIncomeServiceImpl.java` (L56-358)
  - `entity/local/GreenEnergyChainGroupIncome.java` (ChainGroupEnum L46-98)
- Mapper：
  - `mybatis/mapper/light/LightRent.xml`
  - `mybatis/mapper/light/LightCityElecPrice.xml`
  - `mybatis/mapper/elec/LightInveter.xml`
  - `mybatis/mapper/local/EnergySubchainGroupTargetReach.xml`
  - `mybatis/mapper/ads/EnergyChainGroupIncome.xml`
- Doris 查询验证：2026-06-03 确认最新月收入 55,935.71万（5/29）
