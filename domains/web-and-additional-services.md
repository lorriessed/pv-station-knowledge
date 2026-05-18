# PVS Web & Additional Services Analysis

> 分析时间: 2026-05-17
> 分析仓库: hds-web, appapi-web, mobile-web, energystorage-service, cms-service, echannel-service

---

## 1. rrsjk-hds-web（华帝山/HDS 后台管理系统）

### 1.1 服务定位和职责

**华帝山(HDS)项目的后台管理 Web 层**，为光伏电站业务提供完整的运营管理界面。是整个 PVS 系统中功能最丰富的管理后台，涵盖电站管理、运维管理、报表统计、服务商结算、工作流审批、备件管理等。

- **架构**: Spring Boot + Dubbo Consumer（纯消费者，不暴露 Dubbo 服务）
- **认证**: OAuth2 + AccessTokenCheckFilter
- **数据格式**: `ExecuteResult<T>` 统一返回，Swagger 文档

### 1.2 Controller/API 完整列表

#### 电站管理 (`/light/station`)
| API | 方法 | 说明 |
|-----|------|------|
| `/light/station/getCurrentUser` | GET | 获取当前登录用户 |
| `/light/station/getByStationCode.do` | GET | 按电站编码查询电站信息 |
| `/light/station/getWaitCompanySignZhStation.do` | GET | 查询待项目公司签署的中核电站 |
| `/light/station/signZhMaster.do` | GET | 中核合同签署 |
| `/light/station/getContractUrl.do` | GET | 查看合同URL |
| `/light/station/queryLightStationCommon` | GET | 中核电站主列表查询 |
| `/light/station/queryLightStationForCnnAuditList` | GET | 中核电站审核列表 |
| `/light/station/exportLightStationForCnnAuditList` | GET | 导出审核列表 |
| `/light/station/queryLightStationView` | GET | 按项目公司查看电站 |
| `/light/station/updateStation.do` | POST | 更新电站信息 |
| `/light/station/firstSubmit.do` | POST | 首次提交电站 |
| `/light/station/submitCheck.do` | POST | 提交审核 |
| `/light/station/auditStation.do` | POST | 审核电站 |
| `/light/station/submitComplete.do` | POST | 提交竣工 |
| `/light/station/completeAudit.do` | POST | 竣工审核 |
| `/light/station/uploadGridInfo.do` | POST | 上传并网信息 |
| `/light/station/offLineCheck.do` | POST | 线下审核 |
| `/light/station/finalSubmitAudit.do` | POST | 终审提交 |
| `/light/station/finalAudit.do` | POST | 终审 |
| `/light/station/exportLightStationDataCommon` | GET | 导出电站数据 |

#### 逆变器管理 (`/light/inverter`)
| API | 说明 |
|-----|------|
| `/light/inverter/queryInverter.do` | 查询逆变器列表 |
| `/light/inverter/getInverterDetail.do` | 逆变器详情 |

#### 运维收入管理 (`/light/operationMaintenance`)
| API | 说明 |
|-----|------|
| `/light/operationMaintenance/findParams.do` | 查询运维收入管理信息 |
| `/light/operationMaintenance/confirmSettle` | POST 确认暂估 |
| `/light/operationMaintenance/confirmSettleHistory` | POST 确认暂估历史 |
| `/light/operationMaintenance/confirmIncome` | POST 确认收入 |
| `/light/operationMaintenance/confirmIncomeHistory` | POST 确认收入历史 |
| `/light/operationMaintenance/confirmSk` | POST 确认收款 |
| `/light/operationMaintenance/mergeInvoice` | POST 合并开票 |
| `/light/operationMaintenance/invoiceByOne` | POST 单独开票 |
| `/light/operationMaintenance/doExport.do` | GET 导出运维收入 |
| `/light/operationMaintenance/stationDetails` | GET 电站详情列表 |
| `/light/operationMaintenance/doExportStation.do` | GET 导出电站详情 |
| `/light/operationMaintenance/downTemplate` | GET 下载A48模板 |
| `/light/operationMaintenance/downTemplateA51` | GET 下载A51模板 |
| `/light/operationMaintenance/importData.do` | POST 导入数据 |

#### 服务商结算账单 (`/lightSpOpsSettle`)
| API | 说明 |
|-----|------|
| `/lightSpOpsSettle/findByPage` | GET 服务商结算账单列表 |
| `/lightSpOpsSettle/doExport` | GET 导出服务商账单 |
| `/lightSpOpsSettle/confirmSpLedger` | POST 审核操作 |
| `/lightSpOpsSettle/billPdf` | POST 查看账单PDF |
| `/lightSpOpsSettle/checkConfirm` | POST 确认按钮校验 |
| `/lightSpOpsSettle/showDetails` | GET 账单电站详情 |
| `/lightSpOpsSettle/doExportDetails` | GET 导出账单电站详情 |
| `/lightSpOpsSettle/createPdfUrl` | GET 查看账单 |

#### 服务商正/负激励
| Controller | 说明 |
|------------|------|
| `LightSpOpsPositiveExcitationController` | 正激励管理 |
| `LightSpOpsNegativeExcitationController` | 负激励管理 |
| `LightSpOpsPositiveIacController` | 正激励IAC |
| `LightSpOpsNegativeIacController` | 负激励IAC |
| `LightSpOpsSettleIacController` | 结算IAC |

#### 电站电费管理 (`/light/operation/station-elec-bill`)
| API | 说明 |
|-----|------|
| `/light/operation/station-elec-bill/page` | GET 分页查询电站电费账单 |
| `/light/operation/station-elec-bill/bill-only/page` | GET 仅查询账单 |
| `/light/operation/station-elec-bill/detail` | GET 账单详情 |
| `/light/operation/station-elec-bill/update` | POST 更新账单 |
| `/light/operation/station-elec-bill/summary` | GET 电费汇总 |
| `/light/operation/station-elec-bill/export/count` | GET 导出数据量 |
| `/light/operation/station-elec-bill/export` | GET 同步导出(≤2万条) |
| `/light/operation/station-elec-bill/export/async` | GET 异步导出(>2万条) |
| `/light/operation/station-elec-bill/export/list` | GET 我的导出任务 |
| `/light/operation/station-elec-bill/export/cancel` | POST 取消导出任务 |
| `/light/operation/station-elec-bill/import` | POST 批量导入更新 |
| `/light/operation/station-elec-bill/import/template` | GET 下载导入模板 |
| `/light/operation/station-elec-bill/subCenterPage` | GET 电费报表(分中心) |
| `/light/operation/station-elec-bill/exportSunCenter.do` | GET 分中心导出 |
| `/light/operation/station-elec-bill/projectCompanyPage` | GET 电费报表(项目公司) |
| `/light/operation/station-elec-bill/exportProjectCompany.do` | GET 项目公司导出 |
| `/light/operation/station-elec-bill/project-company/search` | GET 项目公司搜索 |
| `/light/operation/station-elec-bill/substation/search` | GET 电所名称搜索 |
| `/light/operation/station-elec-bill/importSpecialFlagGroup` | POST 导入特殊标识分组 |
| `/light/operation/station-elec-bill/station-migration` | POST 电站迁移 |

#### 报表统计 (`/report`)
| Controller | 说明 |
|------------|------|
| `HdsStationElecReportController` (`/report/hds/elec`) | HDS发电管理报表(累计/年/月维度) |
| `EnergyJobController` (`/energyJob`) | 能源任务报表 |
| `ReportDeliveryStationController` | 电站交付报表 |
| `EnergySpDayController` | 服务商日度报表 |
| `EnergySummaryDayController` | 汇总日度报表 |
| `EnergyStationElecIncomeController` | 电站电费收入报表 |
| `EnergyYuexiuSpDataController` | 越秀服务商数据 |
| `EnergyYuexiuSubCenterDataController` | 越秀分中心数据 |
| `EnergySubchainGroupTargetReachController` | 子链组目标达成 |
| `GreenEnergyDayReportController` | 绿色能源日报 |
| `ReportCmIncomeController` | 工商业收入报表 |
| `ReportBtModeDayController` | BT模式日报 |
| `ReportStationEchartsController` | 电站图表 |
| `ReportCmSignGuaranteeRateController` | 工商业签约保障率 |
| `ReportSpStationDevelopWarningController` | 服务商开发预警 |
| `ReportStationProcessWarningController` | 电站流程预警 |
| `ReportZhModelStationController` | 中核模式电站 |
| `ReportStationDevelopWarningController` | 电站开发预警 |
| `LightStationAuditReportController` | 电站审核报表 |
| `zeroCarbonDayReportController` | 零碳日报 |

#### 工作流管理 (`/workflow`)
| Controller | 说明 |
|------------|------|
| `WfCategoryController` | 流程分类管理 |
| `WfDeployController` | 流程部署 |
| `WfFormController` | 流程表单 |
| `WfInstanceController` | 流程实例 |
| `WfModelController` | 流程模型 |
| `WfProcessController` | 流程处理 |
| `WfTaskController` | 流程任务 |

#### 焱图工商业项目管理 (`/yantuAutomaticallyDesignTemporaryStorage`)
| API | 说明 |
|-----|------|
| `/yantuAutomaticallyDesignTemporaryStorage/find.do` | GET 工商业项目暂存列表 |

#### 三方合作外部接口 (`/nahui/station/api`)
| API | 说明 |
|-----|------|
| `/nahui/station/api/queryStation` | GET 越秀电站查询(需hds-key) |
| `/nahui/station/api/inverterQueryByPage` | GET 越秀逆变器查询 |
| `/nahui/station/api/realtimeInverterQueryByPage` | GET 实时逆变器查询 |
| `/nahui/station/api/workOrderQueryByPage` | GET 越秀工单查询 |
| `/nahui/station/api/queryInvertersp` | GET 卡泰驰逆变器查询(需hdsproc header) |

#### 其他
| Controller | 说明 |
|------------|------|
| `SellLightStationController` | 电站出售管理 |
| `CreateOperationMaintenanceStationController` | 创建运维电站 |
| `SocializationStationController` | 社会化电站管理 |
| `LightStationInverterChangeController` | 逆变器更换 |
| `OperationHistorySettleController` | 历史结算管理 |
| `ScheduledTasksController` | 定时任务管理 |
| `MenuController` | 菜单管理 |

### 1.3 核心 Service 业务逻辑

HDS-web **不实现业务逻辑**，全部通过 Dubbo 远程调用下游服务：
- **LightStationService**: 电站CRUD、状态流转(待审核→审核通过→并网→运行)
- **OperationMaintenanceService**: 运维收入确认(暂估→收入确认→收款→开票)
- **LightSpOpsSettleService**: 服务商月度账单生成、正负激励计算
- **LightOperationStationElecBillService**: 电站电费账单管理、异步导出任务
- **HdsReportService**: HDS专用发电报表(累计/年/月维度，动态表头)

### 1.4 Dubbo 服务引用（Consumers Only）

HDS-web 是 **纯 Dubbo 消费者**，不暴露任何 Dubbo 服务。引用约 **150+ 个远程服务**：

**核心依赖服务**:
| 服务组 | 服务数量 | 说明 |
|--------|----------|------|
| `com.rrsjk.light.service.*` | ~60 | 光伏建站核心服务 |
| `com.rrsjk.light.operation.service.*` | ~40 | 光伏运维服务(v1+v2) |
| `com.rrsjk.report.service.*` | ~30 | 报表服务 |
| `com.pvs.ops.repairs.*` | ~30 | 备件/维修服务(group="hds") |
| `com.rrsjk.light.data.service.*` | ~10 | 数据服务(逆变器/发电数据) |
| `com.rrsjk.member.service.*` | ~3 | 会员服务 |
| `com.rrsjk.system.*` | ~3 | 系统服务(短信/区域) |
| `com.haier.cbs.system.*` | ~2 | CBS系统服务 |

### 1.5 数据模型/DTO

主要在 `vo/` 和 `controller/*/dto/` 包中：
- `LightStationCnnChnDto` - 中核电站展示DTO
- `StationElecBillDto` - 电站电费账单DTO
- `HdsStationElecTotalDto/YearDto/MonthDto` - HDS发电报表DTO
- `StationElecBillExportDto` - 电费账单导出DTO
- `StationElecBillImportDto` - 电费账单导入DTO
- `OperationMaintenanceExcel` - 运维收入Excel导出

### 1.6 数据库相关

HDS-web **无直接数据库操作**，全部通过 Dubbo 调用下游服务完成数据访问。

### 1.7 与其他服务的依赖关系

```
hds-web (Consumer)
├── light-service (电站核心)
├── light-operation-service (运维)
├── light-data-service (发电数据/逆变器)
├── report-service (报表)
├── repairs-service (备件维修, group=hds)
├── member-service (会员)
├── system-service (短信/区域/字典)
├── finance-service (财务SAP)
└── cbs-system (海尔CBS)
```

---

## 2. rrsjk-appapi-web（APP API 网关/水站 APP）

### 2.1 服务定位和职责

**水站(净水器)APP 的 API 网关**，为小顺管家（运营商）和水站用户提供移动端接口。注意：这个模块与光伏业务无关，属于海尔净水器/水站业务线，与 PVS 光伏系统共享同一套基础设施。

- **架构**: Spring MVC + Dubbo Consumer + Redis + MongoDB
- **认证**: OAuth2 + Token检查拦截器
- **数据格式**: 自定义 JSON 响应（非 ExecuteResult）

### 2.2 Controller/API 完整列表

#### 用户登录注册 (`/1/water/appLogin`)
| API | 方法 | 说明 |
|-----|------|------|
| `/1/water/appLogin/sendSmsValidateCodeNew` | GET | 发送手机验证码(注册) |
| `/1/water/appLogin/sendSmsFastLoginUserCenter` | GET | 短信验证码登录-发送验证码 |
| `/1/water/appLogin/fastLoginUserCenter` | POST | 短信验证码登录 |

#### 水站管理 (`/1/water/app/waterDispenser`)
| API | 说明 |
|-----|------|
| `/1/water/app/waterDispenser/queryDispenser` | GET 查询运营商管理的水站列表 |
| `/1/water/app/waterDispenser/dispenserInfo` | GET 水站基本信息查询 |
| `/1/water/app/waterDispenser/newDispenser` | POST 新建水站 |
| `/1/water/app/waterDispenser/updateAlias` | POST 更新水站别名 |

#### 水站APP核心功能
| Controller | 说明 |
|------------|------|
| `WaterStationIncomeController` | 水站收入管理 |
| `WaterStationNewIncomeController` | 新收入管理 |
| `WaterDispenserOperatorController` | 运营商管理 |
| `WaterCardController` | 水卡管理 |
| `WaterPointsController` | 积分管理 |
| `WaterFilterController` | 滤芯管理 |
| `WaterFetchRecordController` | 打水记录 |
| `WaterCommentController` | 评论管理 |
| `WaterDispenserRepairController` | 维修管理 |
| `WaterCommunityController` | 社区管理 |
| `WaterAppMessageController` | APP消息 |
| `WaterPostMessagesController` | 帖子消息 |
| `WaterMemberInfoController` | 会员信息 |
| `WaterQuestionController` | 问答 |
| `WaterLearningController` | 学习培训 |
| `WaterShopkeeperController` | 店长管理 |
| `SewageProjectController` | 污水项目 |
| `PrizeController` | 奖品管理 |
| `UserCenterController` | 用户中心 |
| `WaterStationKnowledgeController` | 知识库 |
| `WaterStationContractController` | 合同管理 |
| `WaterSharePointsController` | 分享积分 |
| `WaterPointsOperatorController` | 运营商积分 |
| `WaterPointProductController` | 积分商品 |
| `WaterReportOperatorInfoController` | 运营商报告 |
| `WaterReportUserMultiplierController` | 用户倍增报告 |
| `WaterOperatorWalletRecordController` | 运营商钱包 |
| `WaterOperatorExpressInfoController` | 运营商快递 |
| `WaterOperatorLikeNumController` | 运营商点赞 |
| `WaterEarnPointsController` | 赚积分 |
| `WaterFetchByAppController` | APP打水 |
| `WaterDispenserAgentController` | 代理商 |
| `WaterDispenserRuntimeStatusController` | 运行状态 |
| `WaterDispenserRepairHccController` | HCC维修 |
| `WaterBacklogController` | 积压管理 |
| `WaterAdvertiseDetailController` | 广告详情 |
| `PowerStationRelationController` | 电站关联 |

#### 会员相关
| Controller | 说明 |
|------------|------|
| `MemberLoginController` | 会员登录 |
| `MemberAddressController` | 会员地址 |

#### 多功能控制器
| Controller | 说明 |
|------------|------|
| `WaterDispenserMultiController` | 多功能水站 |
| `WaterDispenserOperatorMultiController` | 多功能运营商 |
| `WaterDispenserWineOrderController` | 红酒订单 |
| `WaterDispenserPointsController` | 积分 |
| `EnomaticController` | Enomatic设备 |

#### 其他
| Controller | 说明 |
|------------|------|
| `WechatShareController` | 微信分享 |
| `WithOutTokenController` | 免Token接口 |

### 2.3 核心 Service 业务逻辑

通过 Dubbo 调用下游服务，自身主要通过 **Adapter 模式** 转换数据：
- `WaterDispenserAdapter` - 水站数据适配
- `WaterDispenserOperatorAdapter` - 运营商数据适配
- `WaterCardAdapter` - 水卡数据适配
- `WaterActivityAdapter` - 活动数据适配
- `WaterFetchRecordAdapter` - 打水记录适配
- `WaterCommentAdapter` - 评论数据适配
- 等 20+ 个 Adapter

### 2.4 Dubbo 服务引用

- **会员**: MemberService, MemberRoleService
- **水站**: WaterDispenserService, WaterDispenserOperatorService, WaterCardService, WaterDispenserElecContractService
- **系统**: MessageService, RegionService
- **电商**: ProductService, Brands

### 2.5 与其他服务的依赖关系

```
appapi-web (Consumer + Adapter)
├── dispenser-service (水站服务)
├── member-service (会员)
├── shoppingmall-service (商城商品/品牌)
├── system-service (短信/区域)
├── Redis (缓存)
└── MongoDB (文件存储)
```

---

## 3. rrsjk-mobile-web（移动端 Web/商城）

### 3.1 服务定位和职责

**乐农/顺逛移动商城的 Web 层**，同时包含光伏专区入口。面向 C 端用户和 B 端采购，提供商品浏览、订单创建、电站管理、会员管理、直播带货等功能。

- **架构**: Spring Boot + Dubbo Consumer + OAuth2
- **认证**: AccessTokenCheckFilter + OAuth2
- **渠道**: M站、微信小程序

### 3.2 Controller/API 完整列表

#### 电站管理 (`/station`)
| API | 说明 |
|-----|------|
| `/station/stationList.do` | GET 电站列表(按会员手机号) |
| `/station/getStationDetail.do` | GET 电站详情 |
| `/station/getStationAccount.do` | GET 光伏账单 |
| `/station/findElectricOrder.do` | GET 光伏账单明细 |
| `/station/findRentRecord.do` | GET 总收益明细 |
| `/station/yxAccountBill.do` | GET 越秀到账收益 |
| `/station/ylAccountBill.do` | GET 银联到账收益 |
| `/station/ylRentList.do` | GET 银联收益 |
| `/station/getMiniProgramTemplateByModeAndHouseType.do` | GET 小程序图片模板 |

#### 光伏运维 (`/light`)
| Controller | 说明 |
|------------|------|
| `LightDataController` | 光伏数据查询 |
| `LightRoadWorkController` | 施工管理 |
| `LightUniqueImageController` | 唯一图片 |
| `LightStationController` | 电站管理(移动端) |
| `LightVisitController` | 电站走访 |
| `LightStationYuexiuAccountController` | 越秀账户 |
| `LightStationNannyController` | 电站保姆 |
| `LightGreenEnergyController` | 绿色能源 |
| `LightForwardController` | 转发 |
| `LightCommodityController` | 光伏商品 |
| `LightStationInfoUpdateController` | 电站信息更新 |

#### 光伏运维操作 (`/lightoperation`)
| Controller | 说明 |
|------------|------|
| `LightModuleInfoController` | 组件信息 |
| `LightRepairOrderController` | 维修工单 |
| `LightWorkOrderController` | 运维工单 |
| `LightFaultDictionaryController` | 故障字典 |
| `DatabaseManagementOpController` | 数据库管理 |

#### 商城相关 (`/shop`)
| Controller | 说明 |
|------------|------|
| `ShopController` | 店铺管理 |
| `ShopProductController` | 店铺商品 |
| `YzzShopController` | 云智妆店铺 |
| `PosthouseController` | 社区驿站 |

#### 订单管理 (`/order`)
| Controller | 说明 |
|------------|------|
| `OrderCreateController` | 创建订单(支持商城/光伏/储能/采购等多渠道) |
| `OrderController` | 订单查询/管理 |
| `OrderItemController` | 订单项 |
| `OrderSettleController` | 订单结算 |
| `OrderPosthouseController` | 驿站订单 |

#### 会员管理 (`/member`)
| Controller | 说明 |
|------------|------|
| `MemberController` | 会员信息查询/注册 |
| `MemberAddressController` | 会员地址 |
| `MemberEnergyController` | 能源会员 |
| `MemberFitnessController` | 健身会员 |
| `MemberVatInvoiceQualificationController` | 增票资质 |
| `MemberTestMealController` | 测试套餐 |
| `FindPasswordController` | 找回密码 |

#### 会员权益 (`/rank`)
| Controller | 说明 |
|------------|------|
| `CardController` | 会员卡 |
| `BenefitConsumerController` | 权益消费 |
| `BenefitPackageController` | 权益套餐 |
| `MemberBenefitController` | 会员权益 |

#### 优惠券 (`/coupon`)
| Controller | 说明 |
|------------|------|
| `CouponController` | 优惠券管理 |

#### 直播 (`/live`)
| Controller | 说明 |
|------------|------|
| `LiveController` | 直播管理 |

#### 首页内容 (`/index`)
| Controller | 说明 |
|------------|------|
| `HotNewsController` | 热点新闻 |

#### 光伏专区 (`/photovoltaic`)
| Controller | 说明 |
|------------|------|
| `PhotovoltaicController` | 光伏专区首页 |

#### 乐享CP (`/ljcp`)
| Controller | 说明 |
|------------|------|
| `LjcpController` | 乐享CP |

#### 维修备件 (`/repairs`)
| Controller | 说明 |
|------------|------|
| `WoPartController` | 工单备件 |
| `CdWarehouseAddressController` | 仓库地址 |
| `CdDictDateController` | 数据字典 |
| `CdMaterialController` | 物料管理 |

#### 驿站/公园
| Controller | 说明 |
|------------|------|
| `ParkController` | 公园管理 |

#### 微信相关 (`/wechat`)
| Controller | 说明 |
|------------|------|
| `WechatShareController` | 微信分享 |
| `MiniProgramT1Controller` | 小程序T1 |

#### OSS (`/oss`)
| Controller | 说明 |
|------------|------|
| `OssController` | OSS文件上传 |

### 3.3 核心 Service 业务逻辑

Mobile-web **不实现业务逻辑**，通过 Dubbo 调用：
- **OrderCreateService**: 订单创建，支持多种渠道类型(MALL/PURCHASE/GROUP/LIGHT/CN_MALL)
- **LightStationService**: 电站查询
- **ShopService**: 店铺管理
- **MemberService**: 会员管理
- **LiveInfoService**: 直播信息(CMS提供)

### 3.4 Dubbo 服务引用

- `OrderCreateService` (trade.order)
- `LightStationService` (light)
- `LightElectricOrderService` (light)
- `LightRentService` (light)
- `ShopService` (merchant)
- `MemberService` (member)
- `OssService` (oss)

### 3.5 与其他服务的依赖关系

```
mobile-web (Consumer)
├── trade-service (订单/购物车)
├── light-service (光伏电站)
├── merchant-service (店铺/商品)
├── member-service (会员)
├── cms-service (直播/内容)
├── oss-service (文件存储)
└── repairs-service (备件)
```

---

## 4. rrsjk-energystorage-service（储能服务）

### 4.1 服务定位和职责

**光伏+储能混合系统的核心后端服务**，提供储能相关的安装维护咨询、收益计算（峰谷电价/充电基础）、内容展示(案例/新闻/合作信息)等功能。采用 api + impl 分离架构。

- **架构**: Dubbo Provider + Consumer，api/impl 分离
- **框架**: Spring + MyBatis + Dubbo
- **数据库**: MySQL (通过 MyBatis)

### 4.2 Dubbo 服务暴露（Provider）

| 服务接口 | 实现类 | 说明 |
|----------|--------|------|
| `CnTouElecPriceService` | CnTouElecPriceServiceImpl | 峰谷电价服务 |
| `CnPeriodDivisionDetailService` | CnPeriodDivisionDetailServiceImpl | 时段划分明细 |
| `CnChargeBaseDetailService` | CnChargeBaseDetailServiceImpl | 充电基础明细 |
| `CnIncomeCalcInfoService` | CnIncomeCalcInfoServiceImpl | 收益计算信息 |
| `DataDictService` | DataDictServiceImpl | 数据字典 |
| `BaseUrlDictService` | BaseUrlDictServiceImpl | 基础URL字典 |
| `InstallMaintenanceInfoService` | InstallMaintenanceInfoServiceImpl | 安装维修信息 |
| `ConsultationDetailService` | ConsultationDetailServiceImpl | 咨询详情 |
| `InstallMaintenanceInfoJobService` | InstallMaintenanceInfoJobServiceImpl | 安装维修定时任务 |
| `HotNewsService` | HotNewsServiceImpl | 热点新闻 |
| `EnergyCaseService` | EnergyCaseServiceImpl | 能源案例 |
| `CooperationInfoService` | CooperationInfoServiceImpl | 合作信息 |

### 4.3 核心 Service 业务逻辑

#### 收益计算模块 (`incomecalc`)
- **CnIncomeCalcService**: 收益计算核心
- **CnIncomeCalcInfoService**: 收益计算信息管理
- **CnIncomeCalcElecCountService**: 电量计算
- **CnChargeBaseHourService**: 充电基础小时
- **CnChargeBaseDetailService**: 充电基础明细
- **CnPeriodDivisionHourService**: 时段划分小时
- **CnPeriodDivisionDetailService**: 时段划分明细
- **CnTouElecPriceService**: 峰谷电价(TOU - Time of Use)

**核心 Model**:
- `CnIncomeCalcModel` - 收益计算模型
- `CnIncomeCalcInfoModel` - 收益计算信息模型
- `CnIncomeCalcHourPriceModel` - 小时价格模型
- `CnIncomeCalcElecCountModel` - 电量计算模型
- `CnTouElecPriceModel` - 峰谷电价模型
- `CnPeriodDivisionHourModel` - 时段划分模型

#### 安装维护模块 (`installMaintenance`)
- **InstallMaintenanceInfoService**: 安装维修信息的 CRUD
- **ConsultationDetailService**: 咨询详情管理
- **InstallMaintenanceInfoJobService**: 安装维护定时任务

**实体**:
- `InstallMaintenanceInfo` - 安装维修信息
- `ConsultationDetail` - 咨询详情

#### 首页内容模块 (`index`)
- **HotNewsService**: 热点新闻
- **EnergyCaseService**: 能源案例
- **CooperationInfoService**: 合作信息

### 4.4 数据模型/DTO

**实体 (`entity` 包)**:
- `incomecalc/CnIncomeCalc` - 收益计算
- `incomecalc/CnIncomeCalcInfo` - 收益计算信息
- `incomecalc/CnTouElecPrice` - 峰谷电价
- `incomecalc/CnChargeBaseHour` - 充电基础小时
- `incomecalc/CnChargeBaseDetail` - 充电基础明细
- `incomecalc/CnPeriodDivisionHour` - 时段划分小时
- `incomecalc/CnPeriodDivisionDetail` - 时段划分明细
- `incomecalc/CnIncomeCalcHourPrice` - 收益计算小时价格
- `incomecalc/CnIncomeCalcElecCount` - 收益计算电量
- `installMaintenance/InstallMaintenanceInfo` - 安装维修信息
- `installMaintenance/ConsultationDetail` - 咨询详情
- `index/HotNews` - 热点新闻
- `index/EnergyCase` - 能源案例
- `index/CooperationInfo` - 合作信息
- `dict/DataDict` - 数据字典
- `dict/BaseUrlDict` - 基础URL字典

### 4.5 数据库相关

**MyBatis Mapper 文件** (18个):
- `CnIncomeCalc.xml`, `CnIncomeCalcInfo.xml`, `CnIncomeCalcElecCount.xml`
- `CnIncomeCalcHourPrice.xml`
- `CnTouElecPrice.xml`
- `CnChargeBaseHour.xml`, `CnChargeBaseDetail.xml`
- `CnPeriodDivisionHour.xml`, `CnPeriodDivisionDetail.xml`
- `InstallMaintenanceInfo.xml`, `ConsultationDetail.xml`
- `HotNews.xml`, `EnergyCase.xml`, `CooperationInfo.xml`
- `DataDict.xml`, `BaseUrlDict.xml`

### 4.6 Dubbo 服务引用

- `MemberService` - 会员服务
- `MemberRoleService` - 会员角色服务
- `RegionService` - 区域服务

### 4.7 与其他服务的依赖关系

```
energystorage-service (Provider + Consumer)
├── [暴露] CnTouElecPriceService → 被其他服务调用
├── [暴露] CnIncomeCalcInfoService → 被其他服务调用
├── [暴露] InstallMaintenanceInfoService → 被其他服务调用
├── [暴露] HotNewsService → 被其他服务调用
├── [暴露] EnergyCaseService → 被其他服务调用
├── [暴露] CooperationInfoService → 被其他服务调用
├── [暴露] DataDictService → 被其他服务调用
├── [暴露] BaseUrlDictService → 被其他服务调用
├── [依赖] member-service (会员)
├── [依赖] system-service (区域)
└── [依赖] MySQL (自身数据库)
```

---

## 5. rrsjk-cms-service（CMS 内容管理）

### 5.1 服务定位和职责

**内容管理系统**，为乐农/顺逛移动商城提供内容支撑。包括轮播图、文章、直播、菜谱、视频、问卷、首页布局等。采用 api + impl 分离架构。

- **架构**: Dubbo Provider + Consumer，api/impl 分离
- **框架**: Spring + MyBatis + Dubbo
- **特色**: 支持直播带货(直播商品/直播接力/直播数据同步)

### 5.2 Dubbo 服务暴露（Provider）

| 服务接口 | 说明 |
|----------|------|
| `CarouselService` | M站首页轮播图管理 |
| `LjCarouselService` | 乐享轮播图 |
| `ArticleItemService` | 美好生活定制文章管理 |
| `BulletinService` | 公告管理 |
| `HomePageRecommendService` | 首页推荐 |
| `HomePageHotItemService` | 首页热门商品 |
| `HomePageFloorItemService` | 首页楼层商品 |
| `HomePageFloorImageService` | 首页楼层图片 |
| `HomePageCustomZoneService` | 首页自定义区域 |
| `CustomizedItemService` | 定制商品 |
| `GroupCustomizedItemService` | 团购定制商品 |
| `LjCategoryService` | 乐享分类 |
| `LjCategoryItemService` | 乐享分类商品 |
| `LjHotItemService` | 乐享热门 |
| `LjNewItemService` | 乐享新品 |
| `LjSeckillItemService` | 乐享秒杀 |
| `LjHomePageService` | 乐享首页 |
| `LnWechatItemService` | 乐农微信商品 |
| `LiveInfoService` | 直播信息管理 |
| `LiveRelayService` | 直播接力 |
| `LiveGoodsService` | 直播商品 |
| `LiveDataJobService` | 直播数据定时任务 |
| `CookbookService` | 菜谱管理 |
| `CookDayService` | 每日菜谱 |
| `VideoService` | 视频管理 |
| `WeeklyProductService` | 每周推荐商品 |
| `QuestionnaireService` | 问卷调查 |
| `SubMessageService` | 订阅消息(微信小程序) |
| `AppImageService` | APP图片管理 |
| `AppStatisticService` | APP统计 |

### 5.3 核心 Service 业务逻辑

#### 首页布局模块
- **CarouselService**: M站轮播图 CRUD + 启用/禁用
- **HomePageFloorItemService**: 首页楼层商品配置
- **HomePageHotItemService**: 首页热门商品推荐
- **HomePageCustomZoneService**: 首页自定义区域

#### 乐享商城模块 (`Lj*`)
- **LjHomePageService**: 乐享首页配置
- **LjCategoryService/Item**: 分类及分类商品
- **LjHotItemService**: 热门商品
- **LjNewItemService**: 新品推荐
- **LjSeckillItemService**: 秒杀商品
- **LjCarouselService**: 乐享轮播图

#### 直播模块
- **LiveInfoService**: 直播信息 CRUD + 云智妆专属直播管理
- **LiveRelayService**: 直播接力(回放)
- **LiveGoodsService**: 直播关联商品
- **LiveDataJobService**: 直播数据同步定时任务
- **SyncLiveData/SyncReplayData/SyncYzzLiveData**: 直播数据同步实现

#### 内容模块
- **ArticleItemService**: 文章/美好生活定制内容
- **BulletinService**: 公告管理
- **CookbookService/CookDayService**: 菜谱管理
- **VideoService**: 视频管理

#### 营销模块
- **WeeklyProductService**: 每周推荐
- **QuestionnaireService**: 问卷调查
- **SubMessageService**: 微信小程序订阅消息

### 5.4 数据模型/DTO

**实体 (`entity` 包)**:
- `Carousel` - 轮播图
- `ArticleItem` - 文章项
- `GoodlifeClass` - 美好生活分类
- `LiveInfo` - 直播信息
- `LiveGoods` - 直播商品
- `Bulletin` - 公告
- `Cookbook` - 菜谱
- `CookDay` - 每日菜谱
- `Video` - 视频
- `WeeklyProduct` - 每周商品
- `Questionnaire` - 问卷
- `AppImage` - APP图片
- `HomePageFloorItem` - 首页楼层项
- `HomePageHotItem` - 首页热门项
- `HomePageCustomZone` - 首页自定义区域
- `CustomizedItem` - 定制商品
- `GroupCustomizedItem` - 团购定制
- `LnWechatItem` - 乐农微信商品
- `LjCategory` - 乐享分类
- `LjHotItem` - 乐享热门
- `LjNewItem` - 乐享新品
- `LjSeckillItem` - 乐享秒杀
- `SubMessage` - 订阅消息

### 5.5 数据库相关

CMS 服务通过 MyBatis 访问 MySQL，每个 Service 对应一个 Mapper XML 文件。

### 5.6 Dubbo 服务引用

CMS 服务可能依赖：
- `MemberService` - 会员信息
- `ProductService` - 商品信息
- `ShopService` - 店铺信息

### 5.7 与其他服务的依赖关系

```
cms-service (Provider + Consumer)
├── [暴露] CarouselService → mobile-web, appapi-web
├── [暴露] LiveInfoService → mobile-web
├── [暴露] ArticleItemService → mobile-web
├── [暴露] BulletinService → mobile-web
├── [暴露] HomePageFloorItemService → mobile-web
├── [暴露] LjHomePageService → mobile-web
├── [暴露] 等30+服务 → mobile-web, appapi-web
├── [依赖] shoppingmall-service (商品/店铺)
├── [依赖] member-service (会员)
└── [依赖] MySQL (自身数据库)
```

---

## 6. rrsjk-echannel-service（电商渠道服务）

### 6.1 服务定位和职责

**电商渠道对接服务**，负责从各大电商平台拉取订单/退款/售后数据，并同步到内部系统。支持多渠道：天猫、顺逛、抖音、建行善融商务、CCT等。采用 api + impl 分离架构。

- **架构**: Dubbo Provider + Consumer，api/impl 分离
- **框架**: Spring + MyBatis + Dubbo
- **模式**: 定时任务拉取 + Webhook回调

### 6.2 Dubbo 服务暴露（Provider）

| 服务接口 | 说明 |
|----------|------|
| `EchannelOrderService` | 电商平台订单转换 |
| `EchannelStatusService` | 订单状态管理 |
| `EchannelSkuService` | SKU映射管理 |
| `EchannelChangeService` | 变更管理 |
| `EchannelDeliverService` | 发货管理 |
| `EchannelRefundService` | 退款管理 |
| `EchannelRefundHandleService` | 退款处理 |
| `EchannelRefundPullService` | 退款拉取 |
| `EchannelOrderPullService` | 订单拉取 |
| `EchannelAftersalePullService` | 售后拉取 |
| `MerchantTradeService` | 商户交易管理 |
| `SgOrderService` | 顺逛订单拉取 |
| `DouyinOrderService` | 抖音小店订单/退款/售后拉取 |
| `CcbOrderService` | 建行善融商务订单拉取 |
| `EchannelCctService` | CCT快递价格查询 |

### 6.3 核心 Service 业务逻辑

#### 平台对接模块 (`platform`)
- **EchannelOrderPullService**: 统一订单拉取调度
- **EchannelRefundPullService**: 统一退款拉取调度
- **EchannelAftersalePullService**: 统一售后拉取调度
- **EchannelOrderService**: 订单转换(平台→内部)
- **EchannelStatusService**: 订单状态同步
- **EchannelDeliverService**: 发货信息同步
- **EchannelRefundService/HandleService**: 退款流程管理
- **MerchantTradeService**: 商户交易记录管理

#### 天猫渠道 (`tmall`)
- **TmallEchannelTradeModel**: 天猫交易模型
- **TmallTradeCreateModel/UpdateModel**: 天猫订单创建/更新
- **TmallEchannelRefundModel**: 天猫退款模型
- **StrategyPullRefundTmall**: 天猫退款拉取策略
- **JdpTbTradeDao/JdpTbItemDao/JdpTbRefundDao**: 聚水潭数据访问

#### 顺逛渠道 (`sg`)
- **SgOrderService**: 顺逛订单/退款拉取
- **SgEchannelTradeModel**: 顺逛交易模型
- **SgTradeCreateModel**: 顺逛订单创建
- **SgEchannelRefundModel**: 顺逛退款模型
- **SgRefundAuditModel/SgRefundSuccessModel**: 退款审核/成功模型
- **StrategyPullRefundSg**: 顺逛退款拉取策略

#### 抖音渠道 (`douyin`)
- **DouyinOrderService**: 抖音订单/退款/售后拉取
- **DouyinApiModel**: 抖音API模型

#### 建行善融商务 (`ccb`)
- **CcbOrderService**: 建行订单拉取
- **CcbBuyAesUtils**: 建行AES加密工具
- **IntegrationService/IntegrationServiceImplService**: WebService WSDL集成

#### 通用策略模式
- **EchannelPullRefundStrategy**: 退款拉取策略接口
- **StrategyPullRefundTmall**: 天猫实现
- **StrategyPullRefundSg**: 顺逛实现

### 6.4 数据模型/DTO

**核心实体**:
- `platform/EchannelOrder` - 电商渠道订单
- `platform/EchannelRefund` - 退款
- `platform/EchannelSku` - SKU映射
- `platform/MerchantTrade` - 商户交易
- `platform/EchannelStatus` - 订单状态
- `platform/EchannelChange` - 变更记录
- `platform/EchannelDeliver` - 发货记录
- `tmall/JdpTbTrade` - 聚水潭天猫交易
- `tmall/JdpTbItem` - 聚水潭商品
- `tmall/JdpTbRefund` - 聚水潭退款
- `sg/SgOrder` - 顺逛订单
- `ccb/CcbOrder` - 建行订单
- `douyin/DouyinOrder` - 抖音订单

### 6.5 数据库相关

**MyBatis Mapper 文件**:
- `platform/MerchantTrade.xml` - 商户交易
- `platform/Echannel*.xml` - 各电商渠道表
- `tmall/*.xml` - 天猫相关表
- `sg/*.xml` - 顺逛相关表
- `ccb/*.xml` - 建行相关表

### 6.6 Dubbo 服务引用

- `MemberService` - 会员信息
- `OrderService` - 内部订单服务
- `ProductService` - 商品信息

### 6.7 与其他服务的依赖关系

```
echannel-service (Provider + Consumer)
├── [暴露] EchannelOrderPullService → 被定时任务/其他服务调用
├── [暴露] SgOrderService → 顺逛订单拉取
├── [暴露] DouyinOrderService → 抖音订单拉取
├── [暴露] CcbOrderService → 建行订单拉取
├── [暴露] EchannelCctService → CCT快递价格
├── [暴露] MerchantTradeService → 商户交易
├── [外部依赖] 天猫开放平台 API
├── [外部依赖] 顺逛 API
├── [外部依赖] 抖音开放平台 API
├── [外部依赖] 建行善融商务 WebService
├── [依赖] trade-service (内部订单)
├── [依赖] shoppingmall-service (商品)
├── [依赖] member-service (会员)
└── [依赖] MySQL (自身数据库)
```

---

## 总结：服务间依赖关系总览

```
┌─────────────────────────────────────────────────────────────────┐
│                        Web 层 (Consumer Only)                     │
├──────────────────┬──────────────────┬───────────────────────────┤
│   hds-web        │   appapi-web     │      mobile-web            │
│  (HDS管理后台)    │  (水站APP API)    │   (移动商城/光伏专区)       │
│  ~150 Dubbo refs │  ~20 Dubbo refs  │   ~15 Dubbo refs          │
└────────┬─────────┴────────┬─────────┴──────────────┬────────────┘
         │                  │                        │
         ▼                  ▼                        ▼
┌─────────────────────────────────────────────────────────────────┐
│                     Service 层 (Provider + Consumer)              │
├──────────────────┬──────────────────┬───────────────────────────┤
│ energystorage-   │   cms-service    │    echannel-service        │
│     service      │  (内容管理30服务) │   (电商渠道15服务)          │
│ (储能12服务)      │                  │                            │
└──────────────────┴──────────────────┴───────────────────────────┘
         │                  │                        │
         ▼                  ▼                        ▼
┌─────────────────────────────────────────────────────────────────┐
│                     基础服务层                                     │
├─────────────────────────────────────────────────────────────────┤
│  light-service │ light-operation │ trade-service │ member-service│
│  (电站核心)     │  (运维)          │  (订单)        │  (会员)       │
├─────────────────────────────────────────────────────────────────┤
│  report-service │ repairs-service │ system-service │ shoppingmall│
│  (报表)         │  (备件维修)      │  (短信/区域)    │  (商城)      │
└─────────────────────────────────────────────────────────────────┘
         │
         ▼
┌─────────────────────────────────────────────────────────────────┐
│                     数据层                                        │
├─────────────────────────────────────────────────────────────────┤
│  MySQL │ Redis │ MongoDB │ OSS │ 外部API(天猫/抖音/建行/顺逛)     │
└─────────────────────────────────────────────────────────────────┘
```

## 关键业务流程

### 1. 光伏电站全生命周期 (HDS)
```
建站商提交 → 待审核 → 技术审核 → 线下审核 → 终审 → 并网 → 运行
    ↓           ↓          ↓          ↓        ↓       ↓      ↓
  初审      合同签署    上传并网    终审     完成    首次三    发电
                                    驳回             电      收益
```

### 2. 运维收入结算 (HDS)
```
暂估 → 确认暂估 → 确认收入 → 确认收款 → 开票
(A51/A48两种记账类型，支持异步处理)
```

### 3. 储能收益计算 (Energystorage)
```
峰谷电价配置 → 时段划分 → 充电/放电量计算 → 收益汇总
     ↓              ↓              ↓             ↓
  CnTouElecPrice  CnPeriodDivision  CnIncomeCalc  收益报表
```

### 4. 电商订单同步 (Echannel)
```
天猫/顺逛/抖音/建行 → 订单拉取 → 数据转换 → 内部订单
                          ↓
                      退款拉取 → 退款处理
                          ↓
                      售后拉取 → 售后处理
```

### 5. CMS 内容管理流程
```
后台配置(轮播/文章/直播) → Dubbo暴露 → mobile-web调用 → APP/M站展示
```
