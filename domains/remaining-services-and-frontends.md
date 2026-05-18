# 剩余后端服务和前端项目文档

> 本文件记录了 PVS 光伏电站系统中剩余后端服务和前端项目的详细分析。

---

## 一、后端服务

### 1. base-service — CBS基础服务（EAI企业应用集成）

**路径**: `/data/pvcode/base-service`  
**Java文件数**: 272  
**模块结构**: `base-api/` (接口+实体) + `base-impl/` (实现)

#### 服务定位
CBS 系统的基础服务层，核心职责是通过 **EAI（企业应用集成）中间件** 与外部企业系统对接，采用 **SOAP/WebService** 协议。所有 WSDL 文件放在 `/wsdl/` 资源目录下。

#### Dubbo 服务暴露
所有 Service 接口通过 Dubbo 暴露给其他内部服务调用：

| 服务接口 | 实现类 | 功能 |
|---------|--------|------|
| `LESService` | `LESServiceImpl` | LES物流系统对接 |
| `InvoiceToSAPService` | `InvoiceToSAPServiceImpl` | SAP发票推送 |
| `InvoiceToEAIService` | `InvoiceToEAIServiceImpl` | EAI发票服务 |
| `InvoiceToTaxService` | `InvoiceToTaxServiceImpl` | 金税系统对接 |
| `EaiProductInfoService` | `EaiProductInfoServiceImpl` | AWS产品主数据查询 |
| `ExtendWarrantyToHpService` | `ExtendWarrantyToHpServiceImpl` | 延保卡推送HP |
| `HpToDispatchingService` | `HpToDispatchingImpl` | HP派工推送 |
| `MdmDataService` | `MdmDataServiceImpl` | MDM主数据同步 |
| `OrderToHpService` | `OrderToHpServiceImpl` | 订单推送HP |
| `YanBaoCardHPService` | `YanBaoCardHPServiceImpl` | 延保卡HP查询 |
| `ElectricInvoiceService` | `ElectricInvoiceServiceImpl` | 4300电子发票系统 |
| `WsdlPositionService` | `WsdlPositionServiceImpl` | WSDL路径定位 |

#### EAI 对接外部系统详细清单

##### 1.1 LES（物流执行系统）
- **开提单接口**: `orderToLes()` / `orderToLesXhaier()` — 通过 EAI 中间件或 xHaier API 开放平台向 LES 推送提单数据
- **付款时间接口**: `paytimeToLes()` / `paytimeToLesXhaier()` — 向物流系统推送定金/尾款付款时间
- WSDL: `QueryDNFromLEStoAPP.wsdl`
- SOAP 方法: `queryDNFromLEStoAPP`

##### 1.2 SAP 系统
- **普通开票推送**: `invoiceToSapForNORMAL()` → `TransInvoiceInfoToEhaierSAP` (ZSDS0005)
- **作废/冲红推送**: `invoiceToSapForINVALID()` → `PushLoanDataToEhaierSAP` (ZSDS0010)
- **二次开票推送**: `invoiceToSapForVOUCHER()` → `PushVoucherInfoToEhaierSAP` (ZSDS0012)
- **差异订单推送**: `sendOrder2thsToSap()` → `TransOrderInfoFromEhaierToGVS` (ZSDS0001)
- WSDL 文件: `TransInvoiceInfoToEhaierSAP.wsdl`, `PushLoanDataToEhaierSAP.wsdl`, `PushVoucherInfoToEhaierSAP.wsdl`, `TransOrderInfoFromEhaierToGVS.wsdl`

##### 1.3 金税系统
- **开票**: `createInvoiceToTaxSys()` — 通过 EAI 向金税系统发送开票请求
- **查询**: `queryInvoiceToTaxSys()` — 查询金税开票结果
- **修改**: `modifyInvoiceToTaxSys()` — 修改发票信息
- **作废**: `invalidInvoiceToTaxSys()` — 发票强制作废
- 涉及 WSDL: `TransInvoiceInfoFromEHaierToGoldenTax.wsdl`, `Modifyinvoiceinfotogoldentax.wsdl`, `Billinfocancel.wsdl`

##### 1.4 EAI 发票中转
- **普通发票头部/明细**: `createInvoiceHeadToEAISys()`, `createInvoiceItemToEAISys()`
- **增值税发票头部/明细**: `createVatInvoiceHeadToEAISys()`, `createVatInvoiceItemToEAISys()`（批量）
- **修改/查询/作废**: `modifyInvoiceToEAISys()`, `queryInvoiceToEAISys()`, `invalidInvoiceToEAISys()`
- 涉及 WSDL: `InsertXwsqZssHead.wsdl`, `InsertXwsqZssItem.wsdl`, `InsertLSMallZssHead.wsdl`, `InsertLSMallZssItem.wsdl`, `InsertXwsqZssZF.wsdl`

##### 1.5 HP（海尔派工系统）
- **订单信息推送**: `dispatchingByHP()` — 派工数据推送
- **延保卡推送**: `sendYbkToHp()` — 延保卡网单信息推送
- **发票信息推送**: `invoiceInfoToHpSys()` — 电子发票开票成功后通知 HP
- **发票信息推送（新）**: `TransInvoiceInfoFromEhaierToHP`

##### 1.6 MDM（主数据管理系统）
同步以下 MDM 主数据表：
- `HhclRow` — HRRRSBTB_HM_CUSTOMERS_LES（客户数据）
- `HcsRow` — HRRRSBTB_CUST_SP2SH2IMB
- `HcscsRow` — HRRRSBTB_CUST_SUB_COMPANY_SH（子公司）
- `HcscRow` — HRRRSBTB_CUST_SUB_COMPANY
- `VcapRow` — VIEW_CUST_ACCOUNT_PY2SP（客户账户）
- `HvsRow` — HM_VALUE_SET（值集）
- `VcbaRow` — VIEW_CUST_BASE_ALL（客户基础全量）
- WSDL: `TransGeneraDataReleaseFromMDM.wsdl`

##### 1.7 AWS（产品主数据）
- **产品主数据查询**: `getProductInfo()` — 从 AWS 查询产品主数据信息
- WSDL: `QueryProductInfoFromAWSToRRS.wsdl`

#### 数据库表（base-service 实体类对应）
| 实体类 | 对应表/用途 |
|-------|-----------|
| `EisInterfaceDataLog` | 接口调用日志表 |
| `EAIInvoiceHead` | EAI发票头部数据 |
| `EAIInvoiceItem` | EAI发票明细数据 |
| `EAIInvoiceZF` | EAI发票作废数据 |
| `EAIInvoiceZFHX` | EAI发票作废核销 |
| `EAIVatInvoiceKPHX` | 增值税发票开票核销 |
| `InvoiceEntity` | 发票实体 |
| `InvoiceOutType` | 发票输出类型 |
| `AWSProductinfo` | AWS产品主数据 |
| `HPYbCard` | HP延保卡信息 |
| `QueryPayTimeToLes` | 付款时间查询LES参数 |

#### 核心业务逻辑
- 所有外部系统调用统一使用 `WriteLogProxy.writeLog()` 记录接口调用日志
- 使用 `IExecute` 回调模式封装外部调用，统一异常处理
- SOAP 调用通过 `javax.xml.ws.Holder` 传递出参
- xHaier 平台通过 `XHaierModel.getXReturn()` 发起 HTTP 请求（Token + URL 双地址模式）
- 电子发票（4300系统）通过 `HttpElectricInvoiceUtil` 发起 JSON HTTP 调用
- 多线程工具类: `ThreadPool`, `MultiThreadTool`

---

### 2. rrsjk-migration-mix — 数据迁移服务

**路径**: `/data/pvcode/rrsjk-migration-mix`  
**Java文件数**: 195  
**模块结构**: `rrsjk-migration-mix-api/` (接口+实体) + `rrsjk-migration-mix-impl/` (实现)

#### 服务定位
用于旧系统（LN/RRS）数据迁移到新 PVS 平台的混合迁移服务，通过 Dubbo 提供迁移 RPC 接口。

#### Dubbo 服务清单

| 服务域 | 服务接口 | 功能 |
|-------|---------|------|
| **shop（商城）** | `BreakevenPricesService` | 盈亏价迁移 |
| | `WarehouseStraightProductsService` | 仓直产品迁移 |
| | `VOMProductDataService` | VOM产品数据迁移 |
| | `VOMProductPriceService` | VOM产品价格迁移 |
| **merchant（商户）** | `SupplierService` | 供应商迁移 |
| | `ProfessionalCustomerService` | 专业客户迁移 |
| | `LnShopService` | LN店铺迁移 |
| | `MerchantResourceService` | 商户资源迁移 |
| | `CorporateClientService` | 企业客户迁移 |
| | `ShopService` | 店铺迁移 |
| **item（商品）** | `CommentService` | 评论迁移 |
| | `ItemService` | 商品迁移 |
| | `SyncHistoryService` | 同步历史迁移 |
| | `ShopSpuPlateformRateService` | 店铺SPU平台费率迁移 |
| | `SpuService` | SPU迁移 |
| **ln（旧系统）** | `ProductOrderAppraiseService` | 订单评价迁移 |
| | `LnProductService` | LN产品迁移 |
| | `LnService` | LN通用迁移 |
| | `SysUserService` | 系统用户迁移 |
| | `ReceiveAddressService` | 收货地址迁移 |
| **member（会员）** | `MemberRoleService` | 会员角色迁移 |
| **portal（门户）** | — | 业务合同/费用/申请迁移 |
| **mdm** | — | 组织数据迁移 |

#### 数据库表（迁移涉及的实体）
- **商城域**: `ShopMembers`, `ShopMemberAddress`, `ShopSupplier`, `BreakevenPrices`, `WarehouseStraightProducts`, `VOMProductPrice`, `VOMProductData`, `ShopMemberLoginInfo`
- **商户域**: `Merchant`, `MerchantResource`, `Shop`, `ShopExtras`, `MerchantExtras`, `Supplier`, `ProfessionalCustomer`, `CorporateClient`
- **商品域**: `Item`, `Spu`, `Sku`, `Brand`, `CategoryAttribute`, `CategoryAttributeValue`, `SpuAttributeValue`, `ItemExtras`, `ItemImage`, `Comment`, `CommentType`, `CommentImage`, `CommentShow`, `ItemSaleChannel`, `SaleChannel`, `ProductBreakevenPrice`, `ProductPurchaseCost`, `ProductData`, `ProductPrice`
- **LN域**: `LnProduct`, `Mdm`, `ProductImgs`, `ProductCategory`, `ProductUnit`, `ProductBrand`, `ProductStock`, `ProductOrderAppraise`, `ProductOrderAppraiseImgs`, `SalesOrganization`, `ProductCategoryCommission`, `ReceiveAddress`, `SysUser`
- **会员域**: `Role`, `MemberRole`, `LoginInfo`
- **门户域**: `BusinessContract`, `BusinessFee`, `BusinessApply`

#### 核心业务逻辑
- 按域拆分迁移逻辑（shop/merchant/item/ln/member/portal/mdm）
- 使用 `RequestVo` 封装迁移请求参数
- 每个迁移服务通过 Dubbo 暴露 `ExecuteResult<T>` 返回值
- 涉及从旧 LN 系统读取数据并转换到新 PVS 模型

---

### 3. rrsjk-member-service — 会员服务

**路径**: `/data/pvcode/rrsjk-member-service`  
**Java文件数**: 79  
**模块结构**: `rrsjk-member-api/` + `rrsjk-member-impl/`

#### 服务定位
统一会员管理服务中心，负责会员注册、登录、地址、角色、扩展信息等核心会员数据的 CRUD。

#### Dubbo 服务清单

| 服务接口 | 实现类 | 功能 |
|---------|--------|------|
| `MemberService` | `MemberServiceImpl`, `OldMemberServiceImpl` | 会员核心服务（注册、登录、绑定） |
| `MemberAddressService` | `MemberAddressServiceImpl` | 会员地址管理 |
| `MemberRoleService` | `MemberRoleServiceImpl` | 会员角色管理 |
| `MemberEnergyService` | `MemberEnergyServiceImpl` | 会员能源管理 |
| `MemberFitnessService` | `MemberFitnessServiceImpl` | 会员健身/健康 |
| `MemberFitnessSignService` | `MemberFitnessSignServiceImpl` | 健身签到 |
| `MemberSignInLogService` | `MemberSignInLogServiceImpl` | 签到日志 |
| `MemberTestMealService` | `MemberTestMealServiceImpl` | 体验餐 |
| `MemberVatInvoiceQualificationService` | `MemberVatInvoiceQualificationServiceImpl` | 会员增值税发票资质 |
| `LoginHistoryService` | `LoginHistoryServiceImpl` | 登录历史 |
| `LightLogOffService` | `LightLogOffServiceImpl` | 光伏注销服务 |

#### 数据库表
| 实体 | 用途 |
|------|------|
| `Member` | 会员主表 |
| `MemberExtras` | 会员扩展信息 |
| `MemberAddress` | 会员收货地址 |
| `LoginInfo` | 登录账号信息（支持手机/微信/QQ/百度等多类型） |
| `LoginHistory` | 登录历史 |
| `MemberRole` | 会员角色关联 |
| `Role` | 角色定义 |
| `MemberEnergy` | 会员能源 |
| `MemberFitness` | 会员健身 |
| `MemberFitnessSign` | 健身签到 |
| `MemberSignInLog` | 签到日志 |
| `MemberTestMeal` | 体验餐 |
| `MemberVatInvoiceQualification` | 增值税发票资质 |
| `LightLogOff` | 光伏注销申请 |

#### 核心业务逻辑
- **多方式注册**: 微信/QQ/百度/手机号+密码/手机号+验证码
- **多账号绑定**: `bindLoginInfo()` 支持为一个会员绑定多个登录账号（不同 type）
- **Security**: Spring Security 配置（`SecurityConfig.java`）
- **配置**: DubboConfig, MybatisConfig, HttpClientConfig, EventBusConfig, IdGeneratorConfig

---

### 4. rrsjk-oauth2-web — OAuth2 统一认证服务

**路径**: `/data/pvcode/rrsjk-oauth2-web`  
**Java文件数**: 100

#### 服务定位
基于 Spring Security OAuth2 的统一认证中心，为所有前端应用（小程序/H5/APP）提供认证和授权服务。

#### Controller 端点

| Controller | 路径 | 功能 |
|-----------|------|------|
| `AuthController` | `/oauth/login` | 手机号密码登录 |
| | `/oauth/sms_login` | 短信验证码登录 |
| | `/oauth/loginOut` | 退出登录 |
| | `/oauth/convertToken` | Token 转换 |
| | `/oauth/hds_idmlogin` | HDS 统一登录（海尔IDM） |
| `UserController` | — | 用户信息查询 |
| `KaptchaController` | — | 验证码生成 |
| `OpsAuthController` | — | 运维认证 |
| `RevokeTokenEndpoint` | — | Token 撤销 |
| `SmsController` | — | 短信验证码 |
| `MiniController` | — | 微信小程序认证 |
| `SmartController` | — | 百度小程序认证 |

#### 认证方式（TokenGranter 实现）

| 认证方式 | TokenGranter | AuthenticationProvider |
|---------|-------------|----------------------|
| 手机号密码 | `EnhancedResourceOwnerPasswordTokenGranter` | — |
| 短信验证码 | `SmsTokenGranter` | `SmsAuthenticationProvider` |
| 微信小程序code | `MiniProgramCodeTokenGranter` | `MiniProgramCodeAuthenticationProvider` |
| 微信小程序手机号 | `MiniProgramPhoneTokenGranter` | `MiniProgramPhoneAuthenticationProvider` |
| 微信公众号 | `WechatMpTokenGranter` | `WechatMpAuthenticationProvider` |
| 微信APP | `WechatAppTokenGranter` | `WechatAppAuthenticationProvider` |
| QQ APP | `QqAppTokenGranter` | `QqAppAuthenticationProvider` |
| 百度小程序code | `SmartProgramCodeTokenGranter` | `SmartProgramCodeAuthenticationProvider` |
| 百度小程序手机 | `SmartProgramPhoneTokenGranter` | `SmartProgramPhoneAuthenticationProvider` |
| HDS | `HdsTokenGranter` | `HdsAuthenticationProvider` |
| HDS IDM | `HdsIdmTokenGranter` | `HdsIdmAuthenticationProvider` |
| RRS Live | `RrsLiveTokenGranter` | `RrsLiveAuthenticationProvider` |

#### 核心业务逻辑
- 基于 **Spring Security OAuth2** 构建
- 使用 **Redis** 存储 Token 和授权码（`RedisAuthorizationCodeServices`, `RedisKeyUtils`）
- `TokenStore` 使用 `publicKeyTokenStore` 配置
- 登录成功后通过 **ActiveMQ** 发送登录事件消息（`LoginSuccessSendMQEventListener`）
- **VPP 集成**: 登录时检查用户是否有 vpp 角色，自动向 VPP 系统获取 Token
- **HDS SSO**: 支持海尔统一身份认证 IDM 登录
- **安全**: XSS 过滤（`XssFilter`, `XssJsoupUtil`），RSA 解密（`RSADecryptor`）

#### 数据库表
- `oauth2_client` — OAuth2 客户端配置表（`rrsjk_system.oauth2_client`）

---

### 5. rrsjk-flowable-service — Flowable 工作流服务

**路径**: `/data/pvcode/rrsjk-flowable-service`  
**Java文件数**: 36  
**模块结构**: `rrsjk-flowable-api/` + `rrsjk-flowable-impl/`

#### 服务定位
基于 **Flowable** 工作流引擎的统一审批流程服务，通过 Dubbo 暴露给业务系统调用。

#### Dubbo 服务清单

| 服务接口 | 实现类 | 功能 |
|---------|--------|------|
| `StartEventService` | `StartEventServiceImpl` | 流程启动/查询/终止 |
| `ProcessTaskService` | `ProcessTaskServiceImpl` | 流程任务审批/查询 |

#### API 接口详细

**StartEventService**:
- `startEvent(StartEventParamsRequest)` — 启动流程实例
- `findBy(PageRequest, QueryRequest)` — 分页查询流程实例
- `showProcessDiagram(String processId)` — 获取流程图（PNG 字节流）
- `findUserTaskData(String processDefinitionId)` — 获取用户任务节点数据
- `stopProcessInstance(EndRequest)` — 终止流程实例

**ProcessTaskService**:
- `audit(AuditRequest)` — 审批单个任务
- `batchAudit(BatchAuditRequest)` — 批量审批
- `solve(SolveRequest)` — 解决问题
- `findBy(PageRequest, QueryRequest)` — 分页查询任务

#### 核心组件
- **Delegate**: `AssignToAuditorDelegate`（自动分配审核人）, `AutoAuditDelegate`（自动审批）
- **Listener**: `AuditEndListener`（审批结束监听）, `FirstAuditEndListener`（首次审批结束）, `SolveListener`（解决监听）
- **Handler**: `IdentityUserHandler`（身份用户处理）, `AbtainUserMethod`（获取用户方法）
- **配置**: `FlowableConfig`, `MybatisConfig`, `DubboConfig`

#### Flowable 数据库表（标准 Flowable 表）
- `ACT_RE_*` — 流程定义
- `ACT_RU_*` — 运行时数据
- `ACT_HI_*` — 历史数据（`HistoricProcessInstanceDao`, `HistoricVariableInstanceDao`）
- `ACT_ID_*` — 身份数据

#### 核心业务逻辑
- 基于 Flowable 6.x 工作流引擎
- DAO 层查询历史流程实例和变量（`HistoricProcessInstanceDao`, `HistoricVariableInstanceDao`）
- 支持自动审批（`AutoAuditDelegate`）和人工审批
- 支持批量审批和流程终止

---

### 6. rrsjk-async-import-export — 异步导入导出服务

**路径**: `/data/pvcode/rrsjk-async-import-export`  
**Java文件数**: 56

#### 服务定位
统一的异步 Excel 导入导出服务，基于 **RocketMQ** 异步处理，支持大数据量导出和 OSS 文件存储。

#### Controller 端点

| Controller | 路径 | 功能 |
|-----------|------|------|
| `AsyncImportExportTaskController` | — | 异步导入导出任务管理 |

#### 核心组件

**Excel 导出**:
- `ExcelExportService` — Excel 导出服务
- `ExcelExportOfTemplateUtil` — 模板导出
- `ExcelBatchExportService` — 批量导出
- `ExportBigExcelService` — 大数据量导出
- `BaseExportService` — 基础导出
- `ExcelLangUtils` — 多语言导出

**MQ 异步处理**:
- `AsyncExportMqListener` — 导出 MQ 消费者
- `AbstractRocketMqConsumer` — RocketMQ 消费者基类
- `MqProducer` — MQ 生产者
- `TopicConstant` — Topic 常量

**业务实现**:
- `LightStationExportService` — 光伏电站导出
- `AsyncImportExportTaskServiceImpl` — 任务管理
- `LightStationExport` — 光伏电站导出实体

**OSS 存储**:
- `OssFileUtils` — OSS 文件上传工具
- `OssConfig` — OSS 配置

**系统监控**:
- `Server`, `Cpu`, `Mem`, `Jvm`, `SysFile` — 系统资源监控

#### 数据库表
| 实体 | 用途 |
|------|------|
| `AsyncImportExportTask` | 异步导入导出任务 |
| `LightStationExport` | 光伏电站导出实体 |

#### 核心业务逻辑
- 双数据源配置: `LightDataSourceConfig` (光伏库) + `LocalDataSourceConfig` (本地库)
- 通过 RocketMQ 解耦导入导出任务
- 导出文件上传至 OSS 并返回下载链接
- 任务状态: 通过 `TaskStatusEnum` 管理（TODO/DOING/SUCCESS/FAILED）
- 任务类型: 通过 `TaskTypeEnum` 区分导出/导入
- 支持大数据量分批次导出

---

## 二、前端项目

### 7. nahui-pv.greenenergy-mini — 绿能小程序

**路径**: `/data/pvcode/nahui-pv.greenenergy-mini`  
**技术栈**: 微信小程序原生 + Vant Weapp UI 组件库

#### 页面结构
**主包 pages/**（核心功能）:
| 页面 | 功能 |
|------|------|
| `pages/home/index` | 首页 |
| `pages/itemList/index` | 商品列表 |
| `pages/item/index` | 商品详情 |
| `pages/shopCart/index` / `pages/shoppingCart/index` | 购物车 |
| `pages/submitOrder/index` | 提交订单 |
| `pages/orderList/orderList` | 订单列表 |
| `pages/orderInfo/orderInfo` | 订单详情 |
| `pages/user/index` | 个人中心 |
| `pages/apv/stationList/index` | 光伏电站列表（TabBar） |
| `pages/couponCenter/index` / `pages/myCoupon/index` | 优惠券 |
| `pages/regTz/index` / `pages/tzInfo/index` | 推荐人注册/信息 |
| `pages/commission/index` | 佣金 |
| `pages/map/index` | 地图 |
| `pages/liveList/index` / `pages/liveVideoList/index` | 直播 |
| `pages/invoice/index` / `pages/qualification/index` | 发票/资质 |
| `pages/cases/caseList/index` / `caseDetail/index` | 案例展示 |

**分包 packageB/**（光伏管理核心）:
| 页面 | 功能 |
|------|------|
| `apvStore/index` | 光伏商城 |
| `apvCart/index` | 光伏购物车 |
| `submitOrder/index` | 光伏提交订单 |
| `stationDetail/index` | 电站详情 |
| `stationBill/index` | 电站账单 |
| `repair/index/index` / `detail/index` | 报修 |
| `yxmode/bank/index` | 越秀模式银行卡 |
| `dhmode/index` / `dhmodeDetail/index` | 顶好模式 |
| `apvBank/index/index` / `detail/index` | 光伏银行 |
| `bankChange/*` | 银行卡变更 |

**分包 packageC/**（水卡相关）: waterMulti, recharge, rechargeRecord 等  
**分包 packageD/**（积分商城）: integral/*, wineSale/*  
**分包 packageA/**（视频/直播）: video + live-player-plugin  
**分包 packageAct/**（营销活动）: luckyweel 抽奖, acts 活动  
**分包 packageE/**: doctor 页面

#### TabBar
首页 → 光伏管理 → 商城 → 我的

#### API 调用（wxapi/）
| 文件 | 功能域 |
|------|--------|
| `apv.js` | 光伏新能源（电站/账单/银行卡变更/越秀模式/顶好模式/OCR/预约） |
| `apvNew.js` | 光伏新版 API |
| `apiWine.js` | 酒水相关 API |
| `osp.js` | OSP 相关 API |
| `common.js` | 通用 API |
| `main.js` | 主入口（登录/商品/订单/支付/地址/购物车/评价/发票） |
| `config.js` | 环境配置 |
| `request.js` | 网络请求封装 |
| `utils.js` | 工具函数 |

主要 API 路径: `/mobileapi/*`, `/payapi/*`, `/oauth2/*`, `/merchant/*`

---

### 8. nahui-pv.osp-mini — OSP 小程序

**路径**: `/data/pvcode/nahui-pv.osp-mini`  
**技术栈**: 微信小程序 + TypeScript (`app.ts`, `tsconfig.json`)

#### 页面结构
| 页面 | 功能 |
|------|------|
| `pages/home/index/index` | 首页 |
| `pages/pool/index/index` / `detail/index` | 电站池管理 |
| `pages/pool/spareApply/index` | 备件申请 |
| `pages/pool/attachmentUpload/index` | 附件上传 |
| `pages/power/index/index` / `detail/index` / `inverter/index` | 发电量/逆变器 |
| `pages/discover/index/index` | 发现 |
| `pages/repair/index/index` / `detail/index` | 报修管理 |
| `pages/user/index/index` | 用户中心 |
| `pages/wisdom/index/index` / `detail/index` | 智慧运维 |

#### 业务功能
OSP（运营服务平台）小程序，主要面向运维人员，提供电站监控、备件管理、报修、智慧运维等功能。

---

### 9. nahui-pv.epcb-mini — EPCB 小程序

**路径**: `/data/pvcode/nahui-pv.epcb-mini`  
**技术栈**: 微信小程序

#### 页面结构
| 页面 | 功能 |
|------|------|
| `pages/home/index/index` | 首页 |
| `pages/home/newproject/*` | 新建项目（测算/发电量/收益/造价/详情） |
| `pages/home/desulfurizedcoalprice/index` | 脱硫煤价格 |
| `pages/home/electricpower/index` | 电力 |
| `pages/home/energyconservation/index` | 节能 |
| `pages/home/projectDation/index` | 项目备案 |
| `pages/home/planFormulation/*` | 方案制定（创建/选择） |
| `pages/home/progressManagement/*` | 进度管理（排程/维护/节点） |
| `pages/home/changeManagement/*` | 变更管理 |
| `pages/user/index/index` / `myproject/index` / `dationList/index` | 用户中心/项目/备案 |
| `pages/apply/join/index` | 加盟申请 |
| `pages/user/evaluate/index` | 评价 |

#### 业务功能
EPCB（Engineering Procurement Construction Business）工程采购施工业务小程序，面向 EPC 工程商，提供项目测算、方案制定、进度管理、变更管理、项目备案等工程全生命周期管理功能。

---

### 10. nahui-pv.merchant-monorepo-h5 — 商户 Monorepo H5

**路径**: `/data/pvcode/nahui-pv.merchant-monorepo-h5`  
**技术栈**: Vue 2.7 + Vue CLI + Vuex + View Design (iView) + qiankun 微前端

#### 项目结构
- **Monorepo 管理**: Yarn 4 Workspaces (`packages/*`)
- **主应用**: `packages/app-main/`（`@nahui/merchant-main`）
- **构建**: `vue-cli-service`
- **微前端**: qiankun 2.10
- **UI**: View Design 4.7
- **图表**: ECharts 5.3
- **其他**: vue-pdf, vue-barcode, qrcodejs2, wangeditor, xlsx

#### 路由模块
| 路由文件 | 功能域 |
|---------|--------|
| `router/apv.js` | 光伏管理 |
| `router/apvp.js` | 光伏运营 |
| `router/osp.js` | OSP 运维 |
| `router/ospSupplier.js` | OSP 供应商 |
| `router/ospSpare.js` | OSP 备件 |
| `router/purchase.js` | 采购管理 |
| `router/supply.js` | 供应链管理 |
| `router/thirdPartyStore.js` | 第三方仓库 |
| `router/epv.js` | 光伏设备 |
| `router/epc.js` | EPC 工程 |

#### API 模块
| API 文件 | 功能域 |
|---------|--------|
| `api/apv.js` | 光伏管理 API |
| `api/apvp.js` | 光伏运营 API |
| `api/osp.js` | OSP API |
| `api/osp/operation.js` | OSP 运维操作 |
| `api/ospSpare/*` | OSP 备件管理（库存/订单/地址） |
| `api/purchase.js` | 采购 API |
| `api/thirdPartyStore.js` | 第三方仓库 API |

#### 业务功能
商户管理后台 H5，涵盖：
- **光伏管理**: 电站管理、设备管理
- **OSP 运维**: 运维工单、备件管理（库存管理、订单执行、服务调拨）、供应商管理
- **采购管理**: 采购单、供应商订单
- **供应链**: 第三方仓库管理
- **EPC**: 工程管理

---

## 二、基础设施服务

### 4. item-service — CBS 物料/商品管理服务（Dubbo RPC）

**路径**: `/data/pvcode/item-service`  
**Java 文件数**: 约 34 个业务文件  
**模块结构**: `item-api/` (接口定义) + `item-impl/` (实现)  
**数据库**: `rrscom` (RDS: rm-m5edyjcbrjfek8ufp.mysql.rds.aliyuncs.com → db003.rrsjk.internal)  
**版本**: 1.1.11-SNAPSHOT | Dubbo 2.7.4.1 | 最后业务提交: 2022-06-08  

#### 服务定位
CBS（零碳适家/电商商城）系统的**商品/物料主数据管理**中心。提供 Dubbo RPC 接口供其他服务查询产品信息、品牌、品类、物料 SKU 等。**不涉及 PV 光伏业务逻辑**，是海尔商城基础设施。

#### Dubbo 服务接口

| 接口 | 实现 | 功能 |
|------|------|------|
| `ItemService` | `ItemServiceImpl` | 统一商品服务入口 |

#### ItemService 方法清单

| 方法 | 功能 |
|------|------|
| `getProductById(Integer id)` | 根据 ID 获取产品信息 |
| `getProductBySku(String sku)` | 根据 SKU 获取产品信息 |
| `getProductType(Integer typeId)` | 获取产品类型 |
| `getBrands(Integer brandId)` | 获取品牌信息 |
| `getProductCates(Integer id)` | 获取品类信息 |
| `getAllProductInfo()` | 获取所有产品 |
| `getAllProductsBysCode(String scode)` | 根据 scode 获取产品列表 |
| `getAllProductCates()` | 获取所有品类 |
| `getChildrenProductCates(Integer parentId)` | 获取子品类 |
| `saveItemAttribute(ItemAttribute)` | 保存/更新产品属性 |
| `saveItemBase(ItemBase)` | 保存/更新物料基本信息 |
| `getItemAttributeByValueSetIdAndValue(String, String)` | 按属性值+类别查属性 |
| `getItemBaseBySku(String sku)` | 按 SKU 查物料基本信息 |
| `getIncompleteItemBaseList()` | 查询信息不完整的物料 |
| `getProductListBySkus(List<String>)` | 按 SKU 列表批量查产品 |
| `getPorductBaseBySku(String sku)` | 按 SKU 查产品基础信息 |
| `getAllOnSaleProducts()` | 获取所有上架产品 |

#### 数据库表（rrscom 库）

| 实体类 | 用途 | Mapper |
|--------|------|--------|
| `Products` | 产品主表 | `ProductsMapper.xml` |
| `ProductBase` | 产品基础信息 | ProductsMapper |
| `ProductTypes` | 产品类型 | `ProductTypesMapper.xml` |
| `Brands` | 品牌 | `BrandsMapper.xml` |
| `ProductCates` | 品类分类 | `ProductCatesMapper.xml` |
| `ItemAttribute` | 产品属性（规格参数） | `ItemAttributeMapper.xml` |
| `ItemBase` | 物料基本信息（SKU 级） | `ItemBaseMapper.xml` |
| `Payments` | 支付方式 | `PaymentsMapper.xml` |
| `NetPoints` | 网点 | `NetPointsMapper.xml` |
| `LesFiveYardInfo` | LES 五码信息 | `LesFiveYardsMapper.xml` |
| `BriefPriceRule` | 价格规则（简要） | — |
| `DetailLadderPriceRule` | 阶梯价格规则（详细） | — |
| `PriceRuleLogs` | 价格规则日志 | — |
| `ExternalSku` | 外部 SKU 映射 | — |

#### 业务特点
- **纯 Dubbo RPC 服务**：无 REST Controller，所有接口通过 Dubbo 暴露
- **读写分离**：配置了 item（写）和 itemread（读）两个数据源
- **Upsert 模式**：`saveItemAttribute` 和 `saveItemBase` 都是"存在则更新，不存在则插入"
- **价格规则**：支持阶梯定价（DetailLadderPriceRule），有变更日志记录
- **业务价值**: ⭐ 低 — 商城商品管理基础设施，与 PV 光伏业务无关

---

### 5. job-service — CBS 通用定时任务调度框架

**路径**: `/data/pvcode/job-service`  
**Java 文件数**: 45 个业务文件  
**模块结构**: `job-api/` (接口+域模型) + `job-impl/` (实现)  
**数据库**: `rrscom`  
**版本**: 1.0.5-SNAPSHOT | Dubbo 2.7.4.1 | Quartz Scheduler  
**最近提交**: 2026-05-12 解钦 — feat: 增加按照 jobName 逻辑删除的方法  

#### 服务定位
CBS 系统的**通用定时任务调度框架**，基于 Quartz 构建，支持 4 种任务类型。可动态注册/管理定时任务，无需修改代码。是基础设施服务，**非 PV 光伏专属**。

#### 支持的 4 种 Job 类型

| 类型 | 常量 | 实现类 | Loader | 说明 |
|------|------|--------|--------|------|
| **Dubbo Job** | `TYPE_DUBBO` | `DubboJob` | `DubboJobLoader` | 调用远程 Dubbo 服务方法 |
| **SQL Job** | `TYPE_SQL` | `SqlJob` | `SqlJobLoader` | 直接执行 SQL 语句 |
| **URL Job** | `TYPE_URL` | `UrlJob` | `UrlJobLoader` | HTTP URL 调用 |
| **Custom Job** | `TYPE_CUSTOM` | 自定义实现 | `CustomJobLoader` | 自定义 Java 类实现 |

#### 核心架构

```
JobMainWorker (主工作线程)
    │
    ├── JobManager (任务管理器)
    │       ├── JobRepository (任务仓储 → DB)
    │       ├── JobLoader (任务加载器)
    │       └── JobProvider (任务提供者)
    │
    ├── JobCommWorker (公共工作线程)
    │
    └── AbstractJob (任务基类)
            ├── DubboJob
            ├── SqlJob
            ├── UrlJob
            └── CustomJob (demo)
```

#### 并发控制机制
- **默认不允许并发**：同一 jobId 的任务同时只能有一个实例运行
- `runningJobs` Set 追踪正在执行的任务 ID
- 尝试并发执行时记录 `SysJobLog.SYS_STATUS_ERROR` + "不允许并发执行"
- 可通过配置扩展：未来支持按任务配置是否允许并发

#### 暂停/恢复机制
- `JobManager.getIsSuspend()` 检查全局暂停状态
- 暂停时所有任务跳过执行，记录 warn 日志

#### 日志与监控

| 表 | 用途 |
|----|------|
| `sys_job` | 任务配置表（类型、cron、参数、状态） |
| `sys_job_log` | 任务执行日志（开始/结束时间、状态、消息） |
| `sys_job_monitor` | 任务监控配置 |

**SysJob 关键字段**:
- `jobId`: 任务 ID
- `jobName`: 任务名称
- `jobType`: 任务类型 (DUBBO/SQL/URL/CUSTOM)
- `cronExpression`: Cron 表达式
- `jobData`: 任务配置数据（JSON/序列化）
- `status`: 状态（启用/禁用）

**SysJobLog 关键字段**:
- `jobId`: 关联任务
- `startTime` / `endTime`: 执行时间
- `nextTime`: 下次触发时间
- `sysStatus`: 系统状态 (0=正常, 1=错误)
- `bizStatus`: 业务状态
- `message`: 执行结果消息

#### Dubbo 服务

| 接口 | 实现 | 功能 |
|------|------|------|
| `JobService` | `JobServiceImpl` | 任务管理（注册、查询、执行、删除） |

**最近新增功能 (2026-05)**:
- `scheduleJobOnceNow`: 立即执行一次任务（不创建定时调度）
- 按 jobName 逻辑删除方法

#### 配置文件
- `quartz.properties`: Quartz 调度器配置
- `application-dev.yml` / `application-prod.yml`: 环境配置
- `cbs-job-service-config.xml`: Spring Bean 配置
- `datasources.xml`: 数据源配置

#### 业务价值
- ⭐ 低 — 通用任务调度基础设施，非 PV 光伏专属
- 但 PV 系统的 `rrsjk-pvbusiness-job-service` 可能是基于此框架构建的光伏业务定时任务

---

## 三、前端/插件/低业务价值仓库

### 6. log_report_plugin — Flutter 日志上报插件

**路径**: `/data/pvcode/log_report_plugin`  
**文件**: 14 个（配置+manifest）| **最后提交**: 2024-12-09  
**技术栈**: Flutter Plugin (Android + iOS)  

- 封装 **Bugly** 崩溃/错误日志上报（腾讯 Bugly）
- Android 包名: `com.haier.nahui.log_report_plugin`
- 支持 iOS 和 Android 双平台
- **业务价值**: ⭐ 极低 — 基础设施插件，与 PVS 业务无关

### 7. nahui-dashboad-h5 — 智慧大屏 H5 前端

**路径**: `/data/pvcode/nahui-dashboad-h5`  
**业务文件数**: 0 (Vue/JS 不在 Java 扫描范围内)  
**最近提交**: 2026-05-07 李宁 — Merge #68 (feat/apv-opt)  

**近期变更** (从 commit message):
- 服务工单增加"进行中"、"已完成"状态，显示故障/低效工单
- 优化智慧大屏布局
- 修改获单、安装数据展示
- 调整区域宽高

**业务价值**: ⭐ 中 — APV 智慧大屏前端，有 PV 业务展示逻辑

### 8. nahui-dicts-serve — 数据字典服务

**路径**: `/data/pvcode/nahui-dicts-serve`  
**业务文件数**: 0 (前端/Node.js 项目)  
**最近提交**: 2026-05-12 李宁 — Merge #122 (feat/HREPC)  

**近期变更** (从 commit message):
- 组件尺寸数据字典字段更新
- SAP 采购相关功能
- 辅料定额功能
- HREPC 相关功能

**业务价值**: ⭐ 低 — 数据字典前端管理界面

---

## 四、服务间调用关系

```
前端小程序/H5
    │
    ├─ OAuth2 (rrsjk-oauth2-web) ── 认证/授权
    │        │
    │        ├─ Dubbo → member-service (会员信息)
    │        └─ VPP 外部系统
    │
    ├─ base-service (EAI) ── 外部系统桥接
    │        │
    │        ├─ SOAP/WSDL → SAP
    │        ├─ SOAP/WSDL → LES
    │        ├─ SOAP/WSDL → 金税
    │        ├─ SOAP/WSDL → HP
    │        ├─ SOAP/WSDL → MDM
    │        └─ SOAP/WSDL → AWS
    │
    ├─ member-service ── 会员管理
    │
    ├─ flowable-service ── 审批流程
    │
    ├─ migration-mix ── 数据迁移（一次性/增量）
    │
    └─ async-import-export ── 异步 Excel 导入导出
             │
             └─ RocketMQ + OSS
```

---

## 四、关键技术要点

1. **base-service 的 EAI 架构**: 所有外部系统集成均通过 EAI 中间件，采用 JAX-WS SOAP 协议，WSDL 文件统一放在 resources/wsdl/ 目录下，每个外部接口对应一组 JAX-WS 生成的客户端代码（`_*_Service`, `*_SOAP_Client` 等）
2. **OAuth2 多端认证**: 支持 12 种以上的登录方式（微信/小程序/QQ/百度/SMS/HDS等），通过 Spring Security 的 TokenGranter 扩展模式实现
3. **Flowable 工作流**: 使用 Flowable 引擎管理审批流程，支持自动审批和人工审批
4. **异步导入导出**: 基于 RocketMQ 解耦，Excel 分批导出 + OSS 存储
5. **前端架构**: 3 个微信小程序（绿电商城+光伏管理/OSP运维/EPC工程）+ 1 个 Vue H5 商户后台
