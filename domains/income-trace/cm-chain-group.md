# 工商业链群 收入溯源

## 收入项基本信息

| 项目 | 值 |
|------|-----|
| 链群名 | 1.2-工商业链群 |
| 月目标 | 32,000万（Doris 报表） |
| 月实际（6月22日） | 877.29万 |
| 月完成率 | 3.74%（预实大差） |
| 责任人 | 奚亚青（工商业一体化） |
| 环比 | +755.6%（上月仅102.53万） |
| 同比 | -189.78%（去年同期为负） |

### 子项构成（Doris 2026-06-22）

| 子项 | 责任人 | 月目标 | 月实际 | 是否计入合计 |
|------|--------|--------|--------|------------|
| 工商业一体化 | 奚亚青 | 25,000万 | 877.29万 | ✅ 是 |
| 列示：工商储 | 刘毕成 | 10,000万 | 0万 | ❌ 否（仅列示） |
| 风电 | 李凡凡 | 7,000万 | 0万 | ✅ 是 |

> **关键发现**：当前工商业链群收入 100% 来自"工商业一体化"子项。风电和工商储本月均为 0。

## 计算逻辑

### 体系一：SAP 收入成本拆分（新体系，SapRevenueCostSplitConfig）

**核心配置类**：`rrsjk-light-report-service/.../incomecost/SapRevenueCostSplitConfig.java`（2026-06-19 创建）

工商业链群在 SAP 拆分体系中的节点树：

```
GONGSHANG（工商业链群, level=2, parent=NEW_ENERGY, source=SUM_CHILDREN）
├── GS_1_11 工商业一体化（level=3, source=SAP）
│   收入规则：
│     - 科目 6001*（主营业务收入）+ 6051*（其他业务收入）
│     - 利润中心：1PG002, 1PG003, 1PG004, 1PG005, 1PG011
│     - 或按业务类型(ywms)：A63/A64/A65/A84/A85/A86/A94-A99/Z23-Z28/B30-B39/B03/A41/A46
│   成本规则：
│     - 科目 6401* + 6402*
│     - 利润中心：1PG002, 1PG003, 1PG004, 1PG005, 1PG011
├── GS_1_12 工商业电费（level=3, source=SKIP — CBS联动待接入）
├── GS_1_13 风电（level=3, source=SAP）
│   收入/成本规则：
│     - 公司代码：1PG0
│     - 利润中心：1PG006
└── GS_GONGSHANGCHU 列示：工商储（level=3, source=SAP, includeInParent=false）
    收入/成本规则：
      - 公司代码：1Q80
      - 利润中心：8600043
```

**收入计算方式**：从 SAP 凭证（rrsjk_finance.sap_record）按公司代码(bukrs)、利润中心(prctr)、科目(hkont)、业务类型(ywms)等维度过滤，收入=科目6001/6051开头（贷-借），成本=科目6401/6402开头（借-贷）。

### 体系二：旧版报表模型（IncomeDayIndustryModel）

**核心类**：`rrsjk-light-report-service/.../model/IncomeDayIndustryModel.java`（471行）

旧版"工商业-物流园"收入由 5 部分构成：

```
totalMonthSumAmount = pstDayAmount + elecMonthSumAmount + opsMonthSumAmount + projectMonthSumAmount
```

| 收入组成 | 方法 | 数据来源 | 当前状态 |
|---------|------|---------|---------|
| 电站交易收入 | createPst() | 无（硬编码返回0） | ⚠️ 未实现 |
| 发电收入 | createElec() | light_inveter_data × 省份电价 - 租金成本 | ✅ 活跃 |
| 运维收入 | createOps() | 无（硬编码返回0） | ⚠️ 未实现 |
| 项目收入 | createProject() | cm_light_project + cm_simple_project + light_manual_income → SapToReportService | ✅ 活跃 |
| 并网收入 | energy_offline_income + light_station | energy_offline_income(subchain='02') + 电站并网容量×3.8/1.13 | ✅ 活跃 |

**项目收入详细逻辑**（createProject 方法）：
1. 从 `cm_light_project` 取 type='INDUSTRY' 的收入编码列表
2. 从 `cm_simple_project` 取 type='INDUSTRY' 的收入编码列表
3. 从 `light_manual_income` 取 subchain='02' 的手工收入编码列表
4. 调用 `SapToReportService.findNewEPCIncome()` 计算 EPC 收入
5. 调用 `SapToReportService.findWholeIncome()` 计算整站收入
6. 合计 = 手工收入 + 新EPC收入 + 整站收入 + 简单项目收入 + 第三方项目收入

**发电收入详细逻辑**（createElec 方法）：
1. 按省份分组获取工商业电站
2. 从 `light_inveter_data` 取日/月发电量
3. 乘以省份电价（`light_city_elec_price`）
4. 减去租金成本：`light_station_plan_config.quantity × light_company_policy.price / 365 × 天数`
5. 除以 1.13 去税

## 数据源表

| 表名 | 数据库 | 角色 |
|------|--------|------|
| sap_record | rrsjk_finance | SAP 记账凭证，收入成本拆分的原始数据源 |
| energy_chain_group_income | ads (Doris) | 最终报表展示表，按链群汇总收入 |
| green_energy_chain_group_income | rrsjk_light_report (local) | 绿能大屏链群收入快照 |
| energy_offline_income | rrsjk_light_report (local) | 离线录入的工商业项目收入（subchain='02'） |
| cm_light_project | rrsjk_light | 工商业项目主表，含收入编码 |
| cm_simple_project | rrsjk_light | 工商业简单项目表 |
| cm_construction_plan | rrsjk_light | 工商业施工方案（并网验收统计） |
| cm_construction_plan_item | rrsjk_light | 施工方案节点（并网验收状态） |
| light_station | rrsjk_light | 电站主表（工商业电站过滤） |
| light_inveter_data | rrsjk_light_data | 逆变器发电数据 |
| light_city_elec_price | rrsjk_light | 省份电价配置 |
| light_station_plan_config | rrsjk_light | 电站方案配置（组件数量） |
| light_company_policy | rrsjk_light | 公司政策（租金价格） |
| light_manual_income | rrsjk_light | 手工收入录入 |
| light_station_epc | rrsjk_light | 电站EPC关联 |

## 业务触发流

### SAP 收入链路（新体系）

```
SAP 过账 → sap_record 写入 → SapRevenueCostSplitConfig 规则匹配
→ GS_1_11 工商业一体化（按利润中心 1PG002/3/4/5/11 + 科目 6001/6051/6401/6402 过滤）
→ 汇总到 GONGSHANG 节点
→ energy_chain_group_income 写入 Doris
```

### 旧版报表链路

```
工商业项目签约 → cm_light_project (type='INDUSTRY')
→ 项目完工/并网 → cm_construction_plan_item (finish_audit_status='AUDIT_OK')
→ SapToReportService 计算 EPC 收入
→ IncomeDayIndustryModel.createProject() 汇总
→ energy_income_day (type='INDUSTRY') 写入

离线收入录入 → energy_offline_income (subchain='02', status='审核通过')
→ IncomeDayIndustryModel 并网收入汇总

逆变器数据 → light_inveter_data → 发电量 × 电价 - 租金成本
→ IncomeDayIndustryModel.createElec() 发电收入
```

### 定时任务调度

```
EnergyJobServiceImpl.autoCreateEnergyIncomeDay()
├── IncomeDayHouseHoldModel → 户用收入
├── IncomeDayMultiModel → 多场景收入
├── IncomeDayIndustryModel → 工商业收入 ← 本次分析目标
├── IncomeDaySocialModel → 社会责任收入
├── IncomeDayWholeModel → 整站收入
└── IncomeDayTotalModel → 汇总
```

## 关键发现

1. **双体系并存**：工商业链群收入存在 SAP 拆分新体系和旧版报表模型两套计算逻辑。新体系（SapRevenueCostSplitConfig）2026-06-19 才创建，直接读 SAP 凭证按利润中心+科目+业务类型拆分；旧体系（IncomeDayIndustryModel）通过 SapToReportService 间接获取 EPC/整站收入。

2. **收入高度集中**：当前月实际 877.29万 100% 来自"工商业一体化"子项，风电和工商储本月均为 0。

3. **利润中心矩阵复杂**：工商业一体化涉及 5 个利润中心（1PG002/3/4/5/11），业务类型覆盖 30+ 种（A63-A86, A94-A99, Z23-Z28, B30-B39, B03, A41, A46），是 SAP 拆分规则中最复杂的节点之一。

4. **工商储不参与合计**：`GS_GONGSHANGCHU`（列示：工商储）设置了 `includeInParent=false`，仅在报表中列示，不计入工商业链群合计。

5. **旧版部分收入未实现**：`createPst()`（电站交易）和 `createOps()`（运维收入）在 IncomeDayIndustryModel 中硬编码返回 0。

6. **CBS 联动待接入**：工商业电费（GS_1_12）在 SAP 拆分体系中标记为 SKIP，等待 CBS（合同账单系统）联动。

7. **环比大幅增长**：本月 877.29万 vs 上月 102.53万，环比增长 755.6%，说明工商业项目收入具有明显的月度波动性（可能与项目完工节点集中有关）。

## 来源

- `rrsjk-light-report-service/.../incomecost/SapRevenueCostSplitConfig.java` — SAP 收入成本拆分规则配置（2026-06-19）
- `rrsjk-light-report-service/.../incomecost/SplitNode.java` — 拆分节点模型
- `rrsjk-light-report-service/.../model/IncomeDayIndustryModel.java` — 旧版工商业收入计算（471行）
- `rrsjk-light-report-service/.../impl/EnergyJobServiceImpl.java` — 定时任务调度（1790行）
- `rrsjk-light-report-service/.../impl/GreenEnergyChainGroupIncomeServiceImpl.java` — 链群收入快照生成
- `rrsjk-light-report-service/.../entity/local/GreenEnergyChainGroupIncome.java` — ChainGroupEnum 枚举定义
- `rrsjk-light-report-service/.../mapper/light/CmConstructionPlan.xml` — 工商业施工方案查询
- `rrsjk-light-report-service/.../mapper/local/EnergyOfflineIncome.xml` — 离线收入查询
- Doris `ads.energy_chain_group_income` — 2026-06-22 数据验证
- 扫描日期：2026-06-23
