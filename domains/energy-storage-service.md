# 储能服务 (Energy Storage Service)

更新时间: 2026-05-24

> **来源**: `rrsjk-energystorage-service` 全量通读 (2026-05-24)
> **证据等级**: 代码明确证明

## 服务定位

`rrsjk-energystorage-service` 是**储能项目收益测算与管理服务**，为工商业储能项目提供收益测算、充放电策略配置、时段划分、电价管理等能力。与光伏业务并行，属于海尔新能源的另一条业务线。

## 技术架构

- **框架**: Spring Boot 2.2.4 + Dubbo 2.7.4.1 + MyBatis 3.5.2
- **父 POM**: rrs-parent 8.0.5
- **依赖**: rrsjk-system-api, system-service, rrsjk-member-api
- **模块**: rrsjk-energystorage-api + rrsjk-energystorage-impl

## 核心业务模块

### 1. 收益测算 (IncomeCalc)

储能收益测算的核心逻辑：根据用户输入的用电数据、电价信息、充放电策略，计算储能项目的投资收益。

#### 测算流程

```
用户提交测算请求 (CnIncomeCalcInfoRequest)
  ├── 校验参数
  ├── 获取分时电价 (CnTouElecPriceModel)
  ├── 获取时段划分 (CnPeriodDivisionHourModel)
  ├── 计算时段功率 = 电量 / 小时数
  ├── 校验需量值 (需量值 > min(尖峰平谷时功率))
  ├── 计算充放小时数 (CnChargeBaseHourModel)
  ├── 计算储能充放电容量:
  │   ├── 储能放电容量0 = if(尖时电量>0, 尖段功率×尖小时数, 0)
  │   ├── 储能放电容量1 = if(尖段功率=0, 峰段功率×放1小时数, 尖段功率×尖小时数)
  │   ├── 储能放电容量2 = if(尖段功率=0, 峰段功率×放2小时数, 尖段功率×尖小时数)
  │   ├── 储能充电容量1 = (需量值或变压器容量×0.8 - 平段功率) × 充2小时数
  │   ├── 储能充电容量2 = (需量值或变压器容量×0.8 - 谷段功率) × 充1小时数
  │   └── 储能设计容量 = MIN(放电容量0,1,2, 充电容量1,2)
  ├── 计算装机功率 = 储能设计容量 / 2
  ├── 计算日收益:
  │   ├── 峰谷套利日收益 = 策略启用 ? (峰价-谷价) × 设计容量 × 次数 : 0
  │   ├── 峰平套利日收益
  │   ├── 尖谷套利日收益
  │   ├── 尖平套利日收益
  │   └── 平谷套利日收益
  └── 计算总投资、总收益、IRR
```

#### 关键枚举

**用电类型1** (`elecTyp1`):
- `CN` — 一般工商业
- `BI` — 大工业

**用电类型2** (`elecType2`):
- `UNITARY` — 单一制
- `TWOP` — 两部制

**用电类型3** (`elecType3`):
- `DEMAND` — 需量
- `CAPACITY` — 容量

**盈利模式** (`profitModel`):
- `EMC` — 合同能源管理
- `SHARE` — 共享
- `FINANCIAL` — 融资租赁

**套利策略开关** (0=不启用, 1=启用):
- `peakValleyArbitrage` — 峰谷套利
- `peakFlatArbitrage` — 峰平套利
- `pointValleyArbitrage` — 尖谷套利
- `pointFlatArbitrage` — 尖平套利
- `flatValleyArbitrage` — 平谷套利

**测算状态** (`CnIncomeCalcInfo.Status`):
- `TEMP` — 暂存
- `SUBMIT` — 提交

#### 数据表

| 表名 | 说明 |
|---|---|
| `cn_income_calc_info` | 测算信息主表 |
| `cn_income_calc` | 收益计算结果（总投资、总收益、IRR等） |
| `cn_income_calc_elec_count` | 电量分布计算值（各时段功率、充放电容量） |
| `cn_income_calc_hour_price` | 时段分布（24小时每小时的电价和时段类型） |
| `cn_tou_elec_price` | 分时电价配置（按省份+用电类型+电压等级） |
| `cn_period_division_detail` | 时段划分详情（每小时的时段类型，按月区分） |
| `cn_period_division_hour` | 时段划分小时数汇总 |
| `cn_charge_base_detail` | 充放策略基础配置（每小时的充放电类型，按月区分） |
| `cn_charge_base_hour` | 充放基础小时数汇总 |

### 2. 分时电价配置 (TOU Electric Price)

**导入逻辑** (`CnTouElecPriceServiceImpl.createList`):
- 按省份 + 用电类型1 + 用电类型2 + 电压等级 四维组合
- 导入新数据前，将同组合的历史数据置为失效 (`disabled`)
- 尖/峰/平/谷电价必须为有效数字

**查询维度**: 省份 → 用电类型 → 电压等级 → 四时段电价

### 3. 时段划分 (Period Division)

按省份配置每小时的时段类型（尖/峰/平/谷），不同月份可以不同。

**导入校验**:
- 每个省份必须覆盖 0-24 全部小时
- 时间格式: `HH:mm-HH:mm`，间隔必须为1小时
- 每月数据不能为空

**定时任务**: `hourCount()` — 每年一次统计所有省份数据

### 4. 充放策略配置 (Charge Base)

按省份配置每小时的充放电类型，不同月份可以不同。

**充放电类型** (`cn_charge_type` 字典):
- 充1 — 充电策略1
- 充2 — 充电策略2
- 放1 — 放电策略1
- 放2 — 放电策略2

**导入校验**: 同省份必须覆盖0-24全部小时

### 5. 安装维修管理 (InstallMaintenance)

**定时任务** (`InstallMaintenanceInfoModel.favorableComment`):
- 查询状态为 `WAIT_RATE`（待评价）的工单
- 如果 `process_at` 距今超过15天且未评分 → 自动给5星好评
- 评分状态设为 `AUTO`（自动评价）

**状态枚举** (`InstallMaintenanceInfo.Status`):
- `COMPLETED` — 已完成

**评价状态** (`InstallMaintenanceInfo.RateStatus`):
- `AUTO` — 自动评价

### 6. 数据字典服务 (DataDict)

通用数据字典服务，提供按类型查询、Map转换、编码/名称互查功能。

## Dubbo 服务接口

| 接口 | 方法 | 说明 |
|---|---|---|
| `CnIncomeCalcInfoService` | findTemp/findById/submit/checkNeedCount | 收益测算 |
| `CnTouElecPriceService` | createList/findBy | 分时电价配置 |
| `CnPeriodDivisionDetailService` | createList/findProvinces/getDetail | 时段划分 |
| `CnChargeBaseDetailService` | createList/findProvinces/getDetail | 充放策略 |
| `InstallMaintenanceInfoService` | findBy/updateBy/create/getById | 安装维修信息 |
| `InstallMaintenanceInfoJobService` | favorableComment() | 15天自动好评 |
| `EnergyCaseService` | findByPage/update/create | 案例管理 |
| `HotNewsService` | getHotNewsList | 热点资讯 |
| `ConsultationDetailService` | findBy/updateBy/create | 项目咨询 |

## 与光伏业务的关系

储能服务与光伏服务是**并行但独立**的业务线，共享部分基础设施（会员体系、系统服务等），但有独立的收益测算逻辑和数据模型。
