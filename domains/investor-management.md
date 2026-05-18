# 资方主数据与投资者管理

更新时间: 2026-05-12

## 已确认知识

### 资方主数据管理 (InvestorMasterData)
**来源**: `rrsjk-admin-web` → `InvestorMasterDataController.java`, `InvestorMasterDataAuditController.java`
**API路径**: `/investor/`

#### 资方基本信息字段
- `companyName` - 公司名称
- `taxNumber` - 税号
- `registrationAddress` - 注册地址
- `contactPerson` / `contactPhone` - 联系人/电话
- `legalPersonName` - 法人姓名
- `registeredCapital` - 注册资本
- `investmentScale` - 投资规模
- `selfStationScale` - 自投电站规模
- `status` - 状态 (StatusEnum)
- `cooperationStatus` - 合作状态: 0=未合作, 1=已合作

#### 引入渠道 (introductionChannel)
**来源**: `InvestorMasterDataController.java` → `convertIntroductionChannelToText()`
| 代码 | 含义 |
|---|---|
| industrial_commercial | 工商业一体化 |
| industrial_park | 产业园 |
| logistics_park | 物流园 |
| household | 户用 |
| wind_power | 风电 |

#### 投资类型 (investableType) - 多选，用 "/" 分隔
**来源**: `InvestorMasterDataController.java` → `convertInvestableTypeToText()`
| 代码 | 含义 |
|---|---|
| centralized_photovoltaic | 集中式光伏 |
| distributed_photovoltaic | 分布式光伏 |
| energy_storage | 储能 |
| source_grid_load_storage | 源网荷储 |
| wind_power | 风电 |

#### 合作方式 (cooperationMode) - 多选，用 "/" 分隔
**来源**: `InvestorMasterDataController.java` → `convertCooperationModeToText()`
| 代码 | 含义 |
|---|---|
| epc | EPC |
| small_epc | 小EPC |
| finished_station_acquisition | 成品电站收购 |

输出顺序固定为: EPC → 小EPC → 成品电站收购 → 其他

#### 评级体系 (rating)
**来源**: `InvestorMasterDataController.java` → `convertRatingToText()`
| 代码 | 含义 |
|---|---|
| level1 | 一级 |
| level2 | 二级 |
| level3 | 三级 |
| level4 | 四级 |

#### 资方统计信息 (InvestorStatisticsDto)
包含: total(总数), cooperated(已合作数), notCooperated(未合作数)

#### 数据格式约定
- 多选字段分隔符: 前端传逗号，后端统一转换为斜杠 `/` (见 `convertCommaToSlash()`)
- 创建/更新人: 通过 `WebUtil.currentUserName(request)` 获取

### 公司税号映射表
**来源**: `rrsjk-finance-service` → `ZeroCarbonApplySettleServiceImpl.java` (硬编码 map)
| 公司名称 | 税号 | 公司编码 |
|---|---|---|
| 青岛海尔光伏新能源有限公司 | 91371421MA947NEK0G | 1PG0 |
| 青岛海尔绿色能源科技有限公司 | 91370282MAC1TEXD2E | 1QJ0 |
| 青岛海尔智能科技有限公司 | 91370282MACM8NFU6U | 1TP0 |
| 乐农物联网有限公司 | 91330206309079212Q | 4110 |
| 五常市日日顺千禾商贸有限公司 | 91230184MA1BPDGR3U | 4110 |
| 寻甸日日顺万宸农业发展有限公司 | 91530129MA6P21PE8U | 4110 |
| 成都日日顺乐农大炳农业开发有限公司 | 91510131MA6CW63T65 | 4110 |
| 山西日日顺达济天下科技有限公司 | 91140122MA0KXAAG7P | 4110 |
| 广州市日日顺仁品农业发展有限公司 | 91440101MA5D4QAUX1 | 4110 |
| 河南日日顺遇鉴农业发展有限公司 | 91411502MA481C8Y9W | 4110 |
| 陕西日日顺君惠农业发展有限公司 | 91610502MA6YA0WU2T | 4110 |
| 山东日日顺文诚农业有限公司 | 91370783MA3RKTTK3M | 4110 |

### 资方客户信息枚举
**来源**: `rrsjk-light-service` → `CustomerInfoEnum.java`
| 枚举值 | businessCode | 公司名称 |
|---|---|---|
| PU_YIN | 8800521696 | 浦银金融租赁股份有限公司 |
| ZHAO_YIN | 8800501395 | 招银金融租赁有限公司 |
| HUA_DIAN | 8800581916 | 四川广元华电新能源有限公司 |
| HUA_RONG | 8800561754 | 华融金融租赁股份有限公司 |
| ZHONG_YIN | 8800656958 | 中银金融租赁有限公司 |

## 待确认
- 资方主数据审核流程 (`InvestorMasterDataAuditController`) 的具体审核节点和规则
- 资方评级变更的审批流和触发条件
- 资方与合作方式的关联约束规则

## 来源
- rrsjk-admin-web → `controller/investor/InvestorMasterDataController.java`
- rrsjk-admin-web → `controller/investor/InvestorMasterDataAuditController.java`
- rrsjk-finance-service → `finance/zerocarbon/service/impl/ZeroCarbonApplySettleServiceImpl.java`
- rrsjk-light-service → `constant/puyin/CustomerInfoEnum.java`
