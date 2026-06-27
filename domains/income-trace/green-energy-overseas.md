# 绿能海外 收入溯源

## 收入项
- **链群名称**: 1.3-绿能海外
- **所属行业**: 绿能
- **月实际收入**: 47.46万（2026-06-26），月目标 4,860万，完成率 1.13%（预实大差）
- **年累计**: 3,660.49万，年目标 60,000万，完成率 24.61%
- **责任人**: 类成伟
- **Doris 表**: `ads.energy_chain_group_income`，`chain_group = '1.3-绿能海外'`，`industry = '绿能'`
- **数据写入方**: `data_platform`（ETL 定时任务，非 Java 应用直接写入）

## 数据全景

```
绿能海外收入 = 光伏组件出口(BW/SAP) + 光伏采销(SAP A57) + OBS海外订单(DSO) + 储能海外(BW+OBS) + 能源控制器海外
```

收入来源涉及 **5 个数据通道**，跨 **3 个业务系统**，最终由 data_platform ETL 汇总写入 Doris ADS 表。

## 计算逻辑

### 核心收入组成（按业务线拆分）

#### 1. 光伏组件海外（公司代码 1PG0）

**数据源 A — BW 推送明细**
- 入口: `POST /report/overseasIncome/create1Q80OverseaIncomeDetail.do`
- Service: `EnergyOverseasIncomeServiceImpl.createDetail()`
- 写入表: `energy_overseas_income_detail`（rrsjk_light_report 本地库）
- 数据来自 SAP BW，按年月批量覆盖（先 disable 旧数据再 batchInsert）
- 关键字段: `hdivision=62`, `netval_inv`(原币金额), `exchangerate`(汇率), `income_cny`(人民币金额)
- 产品分类匹配: 通过 `getProductCategoryBySkuCode()` 接口按 SKU 匹配产品分类

**数据源 B — 月度累计**
- 表: `energy_overseas_income_month`
- 字段: `data_date`, `month_amount`, `company_code`（1PG0/1TP0/1Q80）
- 用途: 计算日收入 = 昨日月累 - 前日月累

**数据源 C — SAP 采销收入**
- Service: `SapToReportServiceImpl.findLightPSIncome()`
- DAO: `SapRecordDao.findLightPSIncomeByTime()`
- SQL: `SELECT sum(i.dmbtr) FROM sap_record r JOIN sap_item_record i ... WHERE ywms='A57' AND kunnr IN ('9100000411','9100001470')`
- 含义: 业务模式 A57（集团内正向），客户为海外关联公司，取本位币金额
- 报告时除以 1.13 去除增值税

**数据源 D — OBS 海外订单**
- DAO: `ObsOrderDao.findDsoIncome()` / `ObsOrderDao.findNoDsoIncome()`
- 表: `obs_order` + `obs_order_item`
- 过滤: `order_type = 'dso_order'`, `prod_type = 'MN'`
- 按 `product_category` 分组汇总 `non_tax_amount`

#### 2. 能源控制器海外（公司代码 1TP0）

- 月累: `energy_overseas_income_month` WHERE `company_code = '1TP0'`
- OBS 订单: `obs_order` WHERE `order_type` 匹配 MQ 维度
- 计算逻辑: `SubchainGroupDayControllerModel` 中 `"海外".equals(s.getSubchainGroup())` 分支

#### 3. 储能海外自有渠道

- Service: `EnergyStatisticIncomeModel.findHwIncomeByScope()`
- 收入 = BW明细(`energy_overseas_income_detail`) + OBS订单(`obs_order_item`)
- 按产品分类: HCHaier(户储海尔), HCNahui(户储纳晖), GSYQY(工商业), GSYDKH(代工), BXS(便携式)
- 单位转换: 原始金额 ÷ 10000 → 万元

### 最终汇总到 Doris

`energy_chain_group_income` 表中 `1.3-绿能海外` 行由 `data_platform` ETL 任务写入，非 Java 应用直接 INSERT。ETL 从上述多个中间表/接口汇总数据。

`GreenEnergyChainGroupIncomeServiceImpl.create()` 是**读取**该表数据后映射到绿能子视图（`GreenEnergyChainGroupIncome` 本地表），按 `ChainGroupEnum.OVER_SEA("5.海外","1.3-绿能海外","类成伟", 8)` 匹配。

## 数据源表

| 表名 | 数据库 | 角色 | 关键字段/过滤 |
|------|--------|------|--------------|
| `energy_chain_group_income` | ads (Doris/SelectDB) | 最终报表 | `chain_group='1.3-绿能海外'`, `industry='绿能'` |
| `energy_overseas_income_detail` | rrsjk_light_report (本地 MySQL) | BW 推送的海外收入明细 | `hdivision=62`, `enable=1`, `income_cny` |
| `energy_overseas_income_month` | rrsjk_light_report (本地 MySQL) | 海外月度累计收入 | `company_code IN ('1PG0','1TP0','1Q80')` |
| `energy_overseas_income` | rrsjk_light_report (本地 MySQL) | 海外收入发票级记录 | `company_code`, `invoice_number` |
| `sap_record` + `sap_item_record` | rrsjk_finance | SAP 记账凭证 | `ywms='A57'`, `kunnr IN ('9100000411','9100001470')` |
| `obs_order` + `obs_order_item` | rrsjk_light_report (本地 MySQL) | OBS 海外订单 | `order_type='dso_order'`, `prod_type='MN'` |
| `green_energy_chain_group_income` | rrsjk_light_report (本地 MySQL) | 绿能子视图（从 ADS 读取后写入） | `chain_group='5.海外'` |
| `energy_ete_income_day` | rrsjk_light_report (本地 MySQL) | ETE 端到端日收入 | `node='OVERSEAS'/'MODULE'`, `type='OVERSEAS'` |

## 业务触发流

```
SAP BW 开票/过账
  → BW 定时推送海外收入明细 → POST /report/overseasIncome/create1Q80OverseaIncomeDetail.do
  → EnergyOverseasIncomeServiceImpl.createDetail()
  → 匹配产品分类 → 写入 energy_overseas_income_detail

SAP 凭证记账（A57 集团内正向）
  → sap_record + sap_item_record 写入
  → SapToReportServiceImpl.findLightPSIncome() 按时间汇总

OBS 海外 DSO 订单发货
  → obs_order + obs_order_item 写入
  → ObsOrderDao.findDsoIncome() / findNoDsoIncome() 按时间汇总

vpp-pv-oversea 海外电站系统
  → SAP 销售订单创建/交货/开票 定时任务
  → SapSaleOrderCreateJob → SapSaleOrderDeliveryJob → SapSaleOrderBillingJob
  → 产生 sap_record 记账

data_platform ETL 定时汇总
  → 从上述各数据源聚合
  → 写入 Doris ads.energy_chain_group_income（chain_group='1.3-绿能海外'）

GreenEnergyChainGroupIncomeServiceImpl.create() 定时读取
  → 映射到绿能子视图 → 写入 green_energy_chain_group_income 本地表
```

## 关键代码路径

| 组件 | 路径 |
|------|------|
| 海外收入 Controller | `rrsjk-merchant-web/.../controller/report/EnergyOverseasIncomeController.java` |
| 海外收入 Service | `rrsjk-light-report-service/.../service/impl/EnergyOverseasIncomeServiceImpl.java` |
| 绿能链群映射 | `rrsjk-light-report-service/.../service/impl/GreenEnergyChainGroupIncomeServiceImpl.java` |
| 链群枚举定义 | `rrsjk-light-report-service/.../entity/local/GreenEnergyChainGroupIncome.java` → `ChainGroupEnum.OVER_SEA` |
| 光伏海外子链群 | `rrsjk-light-report-service/.../service/model/LightSubchainTradeModel.java` → `createOverseasData()` |
| ETE 组件海外 | `rrsjk-light-report-service/.../service/model/EteOverSeasIncomeModel.java` |
| 储能海外统计 | `rrsjk-light-report-service/.../service/model/EnergyStatisticIncomeModel.java` → `findHwIncomeByScope()` |
| 能源控制器海外 | `rrsjk-light-report-service/.../service/model/SubchainGroupDayControllerModel.java` → `"海外"` 分支 |
| SAP 采销查询 | `rrsjk-finance-service/.../sap/service/impl/SapToReportServiceImpl.java` → `findLightPSIncome()` |
| SAP 凭证 SQL | `rrsjk-finance-service/.../mybatis/mapper/sap/SapRecordMapper.xml` → `findLightPSIncomeByTime` |
| BW 明细 SQL | `rrsjk-light-report-service/.../mybatis/mapper/local/EnergyOverseasIncomeDetail.xml` → `orderGroupByProductCategory` |
| OBS 订单 SQL | `rrsjk-light-report-service/.../mybatis/mapper/local/ObsOrderItem.xml` → `orderGroupByProductCategory` |
| 海外电站系统 | `vpp-pv-oversea/vpp-pv-oversea-biz/.../schedule/sap/` (SAP 定时任务集) |
| Doris 报表 DAO | `rrsjk-light-report-service/.../mybatis/mapper/ads/EnergyChainGroupIncome.xml` |

## 关键发现

1. **收入金额极低（月仅 47 万 vs 目标 4860 万）**：完成率仅 1.13%，评价"预实大差"。去年同期仅 8-9 万，今年同比增长约 4-5 倍，但距目标差距极大。

2. **多数据源、多公司代码**：海外收入涉及 3 个公司代码（1PG0 光伏、1TP0 能源控制器、1Q80 储能），每个有独立的月度累计表和 BW 明细。

3. **data_platform ETL 是黑盒**：最终写入 Doris 的是 `data_platform` 用户，不是 Java 应用。Java 应用只负责写入中间表（`energy_overseas_income_detail`、`energy_overseas_income_month` 等），ETL 如何聚合这些中间表到最终报表的逻辑不在代码仓库中。

4. **BW 推送是核心数据通道**：海外收入明细通过 BW 系统推送，字段结构与 SAP 发票一致（60+ 字段），按 `calmonth` 年月覆盖。关键过滤条件：`hdivision=62`（光伏事业部）、排除特定客户/材料/公司代码。

5. **SAP 采销收入需去税**：`findLightPSIncome()` 查 SAP A57 凭证，除以 1.13 去增值税后计入收入。

6. **vpp-pv-oversea 是独立海外业务系统**：纳晖能源海外光伏电站管理，有完整的 SAP 集成链路（销售订单创建→交货→开票→收款），但收入不直接写入报表，而是通过 SAP 凭证间接进入。

7. **产品分类体系**：HCHaier(户储海尔)、HCNahui(户储纳晖)、GSYQY(工商业区域)、GSYDKH(工商业代工)、BXS(便携式)。国内储能报表中，户储历史订单被划入工商业区域。

## 来源
- 代码扫描: 2026-06-27
- 主要仓库: rrsjk-light-report-service, rrsjk-finance-service, rrsjk-merchant-web, vpp-pv-oversea
- Doris 数据: `ads.energy_chain_group_income` WHERE `chain_group = '1.3-绿能海外'`
