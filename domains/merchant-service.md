# 商户服务域 (rrsjk-merchant-service + rrsjk-merchant-web)

更新时间: 2026-05-27 (第14轮全量通读)

## 概述

商户服务是 PVS 光伏平台中**独立于光伏核心业务**的电商/商城体系，源自日日顺乐农(rrsjk)商城系统。它提供企业客户管理、店铺管理、商品交易、供应商管理、驿站(自提点)管理等功能。

光伏业务通过该体系实现：
- 企业客户(服务商/安装商)注册与审核
- 零碳适家企业客户押金管理
- 服务商物料领用(领用单/领用队列)
- 工商业客户管理
- 牛人(专业)客户额度与合同管理

---

## 1. rrsjk-merchant-service (Dubbo 服务提供者)

**技术架构**: Spring Boot 2.2.4 + Dubbo 2.7.4.1 + MyBatis 3.5.3 + MySQL + Redis + Zookeeper
**部署**: JSW daemon 模式，appassembler-maven-plugin 打包

### 1.1 企业客户管理 (CorporateClient)

**来源**: `rrsjk-merchant-service` → `CorporateClientServiceImpl.java` + `CorporateClientDao.java` (代码明确证明)

企业客户是光伏服务商/安装商在平台中的主体身份。注册时**必须通过 MDM 建户校验**。

#### 注册流程 (`regist`)
1. **MDM 建户校验**: 调用 `TransMdmCustomerAndSupplierService.getMdmCustomer()` 验证公司是否已在 MDM 系统中建户
   - 税号 + 公司名称必须与 MDM 一致，否则拒绝注册
2. **税号/名称查重**: 检查 `merchant` 表中是否存在相同税号的已启用商户
3. **创建商户** (`Merchant`):
   - `member_id` → 关联会员
   - `tax_code` → 税号(唯一)
   - `customer_code` → MDM 客户编号
   - `type` → OUTSIDE_CORP(外部企业)
   - 如果是零碳适家流程(`sourceFlag=2`): `company_code="1QJ0"`
4. **创建商户扩展信息** (`MerchantExtras`): 省市区、营业执照、资质图片、银行信息等
5. **创建企业客户记录** (`CorporateClient`):
   - `merchant_id` → 关联商户
   - `status` → WAIT_AUDIT(待审核)
   - `source_flag` → "1"(老流程) 或 "2"(零碳适家)
   - `business_type` → 1(销服一体) 或 2(销售商)
   - `deposit` → 初始为 0
6. **授权区域** (仅零碳适家): 在 `merchant_region` 中创建 MASTER 类型授权记录(省+市)
7. **创建流程日志** (`CorporateClientProcessLog`): 节点 REGISTER

#### 审核流程
- **审核通过** (`auditOk`): 状态变更为 ENABLE
- **审核驳回** (`auditFail`): 状态变更为 AUDIT_FAIL
- 审核信息包括: 审核人、审核时间、审核备注、分中心信息

#### 零碳适家企业客户 vs 老流程
| 维度 | 老流程(sourceFlag=1) | 零碳适家(sourceFlag=2) |
|---|---|---|
| company_code | 不设置 | "1QJ0" |
| 授权区域 | 不设置 | 创建 merchant_region(MASTER) |
| 额外字段 | 基本注册信息 | 营业执照、资质图片、银行信息等 |

#### 涉及表
| 表名 | 说明 |
|---|---|
| `corporate_client` | 企业客户主表 (id, merchant_id, status, source_flag, business_type, deposit, login_id) |
| `merchant` | 商户表 (id, member_id, name, tax_code, customer_code, company_code, type, invoice_type, status) |
| `merchant_extras` | 商户扩展信息 (merchant_id, province/city/region, licence_url, qualifications, bank_info) |
| `merchant_region` | 商户授权区域 (merchant_id, region_type=MASTER, province/city) |
| `corporate_client_process_log` | 企业客户流程日志 (corporate_client_id, node, created_by) |
| `corporate_client_deposit` | 零碳适家企业客户押金/保证金表 |

### 1.2 零碳适家企业客户押金管理 (CorporateClientDeposit)

**来源**: `rrsjk-merchant-service` → `CorporateClientDepositServiceImpl.java` (代码明确证明)

零碳适家企业客户需要缴纳保证金才能开展业务。

#### 押金状态机
| 状态 | 说明 |
|---|---|
| WAIT | 待确认 (刚提交转账凭证) |
| CONFIRMED | 已确认收款 |

#### 对账状态
| 状态 | 说明 |
|---|---|
| NO | 未对账 |
| YES | 已对账 |

#### 业务流程
1. **提交押金** (`addDeposit`):
   - 校验企业客户状态必须为 ENABLE(已审核通过)
   - 生成押金单号(前缀: CORPORATE_CLIENT_DEPOSIT_ADD)
   - 记录: 会员信息、金额、支付渠道、转账凭证、zoneId
   - 初始状态: WAIT, NO
2. **修改押金** (`modifyDeposit`): 仅 CONFIRMED 状态不可修改
3. **确认收款** (`confirmPay`):
   - 更新支付信息(payId, payNo, thirdTradeNo, tradeAt)
   - 状态变更为 CONFIRMED
   - **事务内**: 更新押金状态 + `corporate_client.addDeposit()`(累加保证金额)
   - **转账渠道**: 调用 `financeIncomeModel.corporateClientDepositToSap()` 进行 SAP 记账
   - SAP 记账失败会返回错误但收款已确认(需手动重试)
4. **SAP 记账** (`corporateClientDepositToSap`):
   - 校验状态必须为 CONFIRMED
   - 防重复: 检查 account_status=YES 或 account_voucher 已有值
   - 调用 `FinanceIncomeModel` 的 Dubbo 接口记账

#### 涉及表
| 表名 | 说明 |
|---|---|
| `corporate_client_deposit` | 押金记录 (deposit_no, corporate_client_id, amount, type, status, account_status, pay_channel, transfer_voucher, account_voucher) |

### 1.3 牛人(专业)客户管理 (ExpertCustomer)

**来源**: `rrsjk-merchant-service` → `ExpertCustomerService.java` (代码明确证明)

牛人客户是有额度和账期管理的专业客户，支持授信、合同管理。

#### 核心功能
- **创建牛人客户**: 关联会员、商户、店铺
- **额度管理**: `setCredit(id, totalCredit, accountPeriod)` — 设置总额度和账期
- **额度变更**: `changeCredit()` — 增减额度，记录变更订单明细
- **合同管理**: 保存/查询/删除合同图片
- **店铺关联**: 一个牛人客户可有多个店铺(`ExpertShopDto`)
- **状态管理**: enabled/disabled/deleted

#### 涉及表
| 表名 | 说明 |
|---|---|
| `expert_customer` | 牛人客户主表 |
| `expert_customer_contacts` | 联系人 |
| `expert_customer_contract` | 合同 |
| `expert_customer_contract_image` | 合同图片 |
| `expert_customer_credit_use_detail` | 额度使用明细 |

### 1.4 工商业客户管理 (IndustryCommerce)

**来源**: `rrsjk-merchant-service` → `IndustryCommerceService.java` (代码明确证明)

工商业客户分三种类型: 01=安装商, 02=设计院, 03=甲方客户

#### 业务流程
- 注册 → 待审核 → 审核通过/驳回
- 审核通过后查询有效客户列表(`findValidByType`)

### 1.5 驿站(自提点)管理 (Posthouse)

**来源**: `rrsjk-merchant-service` → `PosthouseService.java` (代码明确证明)

驿站是物流自提点/社区团取货点。

#### 核心功能
- **个人申请** (`oneselfApply`): 个人申请成为驿站
- **店铺申请** (`shopApply`): 店铺申请驿站
- **批量导入** (`shopImport`): Excel 批量导入驿站
- **审核**: auditOk / auditReject
- **启用/禁用**: enabled / disabled
- **经纬度更新**: 用于距离计算
- **门头照片更新**: 审核用
- **分组管理**: `PosthouseGroupService` — 驿站分组(社区团)

#### 配置开关 (`PosthouseConfig`)
| 配置项 | 说明 |
|---|---|
| shopShowShopItem | 店铺是否展示店铺商品 |
| shopShowSelfItem | 店铺是否展示自营商品 |
| shopShowAllItem | 店铺是否展示全部商品 |
| plateformShowSelfItem | 平台是否展示自营商品 |
| plateformShowAllItem | 平台是否展示全部商品 |

### 1.6 配送线路管理 (DriverDelivery)

**来源**: `rrsjk-merchant-service` → `DriverDeliveryService.java` (代码明确证明)

- 配送线路的增删改查
- 线路关联驿站(`addLinePosthouse` / `deleteLinePosthouse`)
- 配送区域管理(已标记 @Deprecated)
- 启用/禁用

### 1.7 店铺管理 (Shop)

**来源**: `rrsjk-merchant-service` → `ShopService.java` (代码明确证明)

- 店铺查询(按授权区域、会员ID)
- 社区团启用/取消
- **云智妆(YZZ)**: enabledYzz / disabledYzz — 开启/取消云智妆店铺
- CBS 分页查询(`findForCbsPage`)

### 1.8 云智妆(YZZ)店铺体系

**来源**: `rrsjk-merchant-service` → `YzzShopService.java` + `YzzGuideService.java` + `YzzShopMemberService.java` (代码明确证明)

云智妆是独立的店铺业务线:
- **YzzShop**: 云智妆店铺，支持经纬度查询、启用/禁用、关联上级总代
- **YzzGuide**: 云智妆导购员，支持启用/禁用、CBS 列表查询
- **YzzShopMember**: 下单会员与店铺导购员关系绑定

### 1.9 供应商管理 (Supplier)

**来源**: `rrsjk-merchant-service` → `SupplierService.java` (代码明确证明)

- 供应商注册、审核(状态: 0=待审核, 1=正常, 2=驳回, -1=冻结)
- 供应商服务公司管理(`SupplierCompanyService`)
- MDM 供应商同步(`TransMdmCustomerAndSupplierService.getMdmSupplier`)

### 1.10 园区评价 (Park)

**来源**: `rrsjk-merchant-service` → `ParkService.java` (代码明确证明)

园区服务评价系统(非光伏核心业务):
- 三版评价模型: `ParkAppraise` / `ParkAppraiseUp` / `ParkAppraiseTwo`
- 评价维度: 居住、维修、清洁、出行、市场、咖啡、餐饮、安全
- 配置: 允许提交次数、时间窗口

### 1.11 MDM 集成

**来源**: `rrsjk-merchant-service` → `TransMdmCustomerAndSupplierService.java` (代码明确证明)

MDM(主数据管理)系统同步:
- **客户同步**: 按税号/外部编码/公司名称查询
- **供应商同步**: 按税号/供应商编码/供应商名称查询
- 支持模糊查询

### 1.12 外部服务调用

| 外部服务 | 调用方式 | 用途 | 来源文件 |
|---|---|---|---|
| MDM 系统 | Dubbo (TransMdmCustomerAndSupplierService) | 客户/供应商主数据校验 | `TransMdmCustomerAndSupplierService.java` |
| SAP 系统 | Dubbo (FinanceIncomeModel) | 企业客户押金记账 | `CorporateClientDepositServiceImpl.java` |
| 顺丰 BKind | HTTP POST | 同步牛人客户信息 (transactionType=6110001) | `AddExpertCustomerListener.java` |
| 短信服务 | Dubbo (MessageService) | 发送短信验证码 | `SendSmsListener.java` |
| 快递100 | HTTP SDK | 物流快递查询 | `Kuaidi100ClientConfig.java` (key: ihWUQDje4078) |

### 1.13 事件驱动架构

**来源**: `rrsjk-merchant-service` → `EventBusConfig.java` + `AbstractSendSmsListener.java` (代码明确证明)

使用 Google Guava `AsyncEventBus` 实现异步事件:
- 线程池: core=10, max=200, queue=10000
- 事件: `AddExpertCustomerEvent` → `AddExpertCustomerListener` → 调用顺丰接口
- 事件: `SendSmsEvent` → `SendSmsListener` → 发送短信

---

## 2. rrsjk-merchant-web (HTTP 网关)

**技术架构**: Spring Boot 2.2.4 + Spring MVC + Dubbo 消费者 + OAuth2 + Swagger
**角色**: 前端/API 调用的 HTTP 网关，通过 Dubbo 调用 merchant-service、light-service、trade-service 等

### 2.1 核心过滤器链 (order 从小到大)

| Order | 过滤器 | 功能 |
|---|---|---|
| 90 | CorsFilter | 跨域过滤器(允许所有 origin) |
| 95 | IpWhitelistFilter | IP 白名单过滤器 |
| 100 | AccessTokenCheckFilter | OAuth2 Token 校验 |
| 105 | ActuatorEndpointFilter | Actuator 端点保护 |
| 110 | ShopStatusCheckFilter | 店铺状态检查 |

### 2.2 会员注册

**来源**: `rrsjk-merchant-web` → `MemberRegistController.java` (代码明确证明)

#### 注册流程
1. `check_and_send_sms.do` — 检查手机号是否已注册，发送验证码(模板ID: 167)
2. `check_sms_code.do` — 校验验证码，最多5次
3. `do_regist.do` — 手机号+密码注册

#### 限流策略 (Redis)
| 维度 | 限制 | 窗口 |
|---|---|---|
| 同一手机号 | 20次 | 10分钟 |
| 同一IP | 100次 | 10分钟 |
| 验证码校验 | 5次 | 10分钟 |

#### 白名单 IP
- 127.0.0.1, localhost
- 202.65.206.130 (集团办公)
- 219.146.*.* (集团电信)
- 223.80.102.* (集团移动)
- 27.223.78.* (集团联通)

### 2.3 AI 助手集成

**来源**: `rrsjk-merchant-web` → `ChatMessageController.java` + `UserProblemManagementController.java` (代码明确证明)

#### 聊天消息接收
- **路由**: `POST /api/chat/messages`
- **参数**: systemSource, memberId, chatId, historyMessages
- **服务**: `ChatMessageService` → 调用 Dify API

#### Dify 配置
- 配置项: `light.operation.dify.api.base-url`, `light.operation.dify.api.key`
- Session 超时: 1800秒
- 最大历史: 50条
- 限流: 60次/分钟

#### 用户问题管理
- **路由**: `/api/assistant/userProblemManagement`
- **功能**: 分页查询、创建、更新、解决状态管理
- **分类**: 三级问题分类(primaryCategory/secondaryCategory/tertiaryCategory)

### 2.4 领用单管理 (LightUseOrder)

**来源**: `rrsjk-merchant-web` → `LightUseOrderController.java` (代码明确证明)

- **完工前领用列表**: `GET /lightUseOrder/completeBeforeDoList.do`
- **完工前领用导出**: `GET /lightUseOrder/completeBeforeExport.do`
- **服务商手动出库**: `POST /lightUseOrder/manualOutStock.do` (防重复提交: 10秒间隔)

### 2.5 领用异常列表 (LightUseQueue)

**来源**: `rrsjk-merchant-web` → `LightUseQueueController.java` (代码明确证明)

- **列表**: `GET /lightUseQueue/doList.do`
- **导出**: `GET /lightUseQueue/doExport.do`
- 按电站编码、创建时间、处理状态查询

### 2.6 垂杨对接

**来源**: `rrsjk-merchant-web` → `ChuiYangController.java` (代码明确证明)

- **获取电站基本信息**: `GET /chuiyang/getStationBaseInfo.do`
- **接收出图数据**: `POST /chuiyang/addImageData.do`
- **接收踏勘数据**: `POST /chuiyang/addInvestigateData.do`
- 所有请求记录到 `ChuiYangRequestLog`

### 2.7 百度 AI 图片识别

**来源**: `rrsjk-merchant-web` → `ImageRecognizeController.java` (代码明确证明)

- **路由**: `POST /light/imageRecognize/imageNum.do`
- **功能**: AI 识别太阳板数量
- **服务**: `LightStationBaiduAILogService.imagePredict()`

### 2.8 保外记账

**来源**: `rrsjk-merchant-web` → `SpSettlementDataController.java` (代码明确证明)

- **路由**: `POST /repairs/spSettlementData/getPage`
- **服务**: `SpSettlementDataService` (来自 repairs 模块)

### 2.9 商户用户信息 (含 AES 加密)

**来源**: `rrsjk-merchant-web` → `MerchantUserInfoController.java` (代码明确证明)

- **路由**: `POST /merchantUserInfo/getMemberId`
- 返回: 角色集合、分中心名称、memberId、AES 加密数据
- 分中心分组:
  - 组1 (sourceId=749): 上海、成都、南宁、广州、长沙等 17 个分中心
  - 组2 (sourceId=748): 青岛、济宁、济南、徐州、石家庄等 20 个分中心

### 2.10 QPS 限流

**来源**: `rrsjk-merchant-web` → `RequestLimiter.java` + `RequestLimiterAspect.java` (代码明确证明)

- 自定义注解 `@RequestLimiter(key, qps, warning)`
- Redis 实现令牌桶
- 限流返回: "接口请求过多，请稍后再试"

---

## 3. rrsjk-migration-member (历史数据迁移)

**来源**: `rrsjk-migration-member` (代码明确证明, 标注 @Deprecated)

基于 Canal 的会员数据实时迁移服务:
- **源库**: Shop 数据库(老系统)
- **目标库**: rrscom 数据库(新系统)
- **迁移表**: Members, MemberAddresses, LoginInfo, member_modify_password_record
- **架构**: Canal 监听 binlog → `DealCanalEventListener` → 策略模式处理 → 写入新库

---

## 4. rrsjk-migration-mix (混合数据迁移)

**来源**: `rrsjk-migration-mix` (代码明确证明, 标注 @Deprecated)

基于 Canal 的多域数据实时迁移服务:

### 4.1 监听数据库和表

| 数据库 | 表 | 处理器 |
|---|---|---|
| Shop | VOMProductData | ProductDataHandler — 产品主数据 |
| Shop | vom_product_price | ProductPriceHandler — 产品价格 |
| Shop | BreakevenPrices | ProductBreakevenPriceHandler — 保本价 |
| Shop | WarehouseStraightProducts | ProductPurchaseCostHandler — 外仓直发 |
| Shop | Suppliers | SupplierHandler — 供应商 |
| ln_shoptv | receive_address | ShopMemberAddressHandler — 收货地址 |
| ln_shoptv | product | ItemHandler — 乐农商品 |
| ehaier_system | sys_user | SystemSysUserHandler — 系统用户 |

### 4.2 多数据源配置

| 数据源 | 用途 |
|---|---|
| item | 商品域(item/brand/category/spu/sku) |
| shop | 商城域(ShopMembers/ShopMemberAddress) |
| merchant | 商户域(Merchant/Supplier/Shop) |
| ln | 乐农域(LnProduct/ProductCategory/ReceiveAddress) |
| mdm | MDM 主数据 |
| system | 系统域 |
| member | 会员域 |
| portal | 门户域 |
| rrs | 日日顺域 |

### 4.3 历史数据同步

**SyncHistoryService** 提供批量同步方法:
- `syncProductDataHistoryData` — 产品主数据(VOMProductData → ProductData)
- `syncProductPriceHistoryData` — 产品价格(VOMProductPrice → ProductPrice)
- `syncBreakevenPriceHistoryData` — 保本价(BreakevenPrices → ProductBreakevenPrice)
- `syncPurchaseCostHistoryData` — 外仓直发(WarehouseStraightProducts → ProductPurchaseCost)
- `syncAddressData` — 乐农收货地址(ReceiveAddress → ShopMemberAddress)

### 4.4 乐农商品迁移

**来源**: `ItemServiceImpl.java` (代码明确证明)

从乐农系统(ln_shoptv)迁移商品到 JK 商城:
- LnProduct → Item + ItemExtras + ItemImage + ItemSaleChannel + Sku
- 品牌映射: ln 品牌名称 → JK 品牌 ID
- 类目映射: 乐农四级类目 → JK SPU + 三级类目
- 店铺映射: 乐农销售组织 → JK 店铺
- 图片 URL 替换: ln.rrsjk.com → CDN URL

### 4.5 乐农评价迁移

**来源**: `CommentServiceImpl.java` (代码明确证明)

ProductOrderAppraise → Comment + CommentImage:
- 评分映射: star → itemCommentScore, serviceStar → serviceQualityScore, distributionStar → shipmentScore
- 图片 URL 替换和协议修正(http→https)
- 买家信息: 乐农 SysUser → ShopMembers → Comment.buyerId/buyerName

---

## 5. 关键业务规则总结

### 5.1 企业客户注册必须先通过 MDM 建户
**证据等级**: 代码明确证明
企业客户注册时，系统调用 MDM 接口验证公司名称和税号，未建户或信息不一致则拒绝注册。

### 5.2 零碳适家企业客户押金确认收款后自动累加保证金
**证据等级**: 代码明确证明
`confirmPay` 在同一事务中: 更新押金状态 + `corporate_client.addDeposit()` 累加企业客户的 deposit 字段。

### 5.3 零碳适家押金收款成功后触发 SAP 记账
**证据等级**: 代码明确证明
转账渠道收款确认后，调用 `FinanceIncomeModel.corporateClientDepositToSap()` 进行 SAP 记账。SAP 记账失败不影响收款确认状态，但会返回错误提示。

### 5.4 企业客户与商户是一对一关系
**证据等级**: 代码明确证明
注册逻辑中检查: 同一 memberId 不能对应多个 companyCode 已启用的商户。

### 5.5 商户注册时的 IP 白名单
**证据等级**: 代码明确证明
集团办公网 IP(电信/联通/移动/固定 IP)在短信发送限流中被豁免。

---

## 6. 涉及数据库表总览

| 表名 | 所属服务 | 用途 |
|---|---|---|
| `corporate_client` | merchant-service | 企业客户主表 |
| `corporate_client_deposit` | merchant-service | 零碳适家企业客户押金 |
| `corporate_client_process_log` | merchant-service | 企业客户流程日志 |
| `merchant` | merchant-service | 商户表 |
| `merchant_extras` | merchant-service | 商户扩展信息 |
| `merchant_region` | merchant-service | 商户授权区域 |
| `merchant_resource` | merchant-service | 商户资源(登录账号关联) |
| `expert_customer` | merchant-service | 牛人客户 |
| `expert_customer_contacts` | merchant-service | 牛人客户联系人 |
| `expert_customer_contract` | merchant-service | 牛人客户合同 |
| `expert_customer_credit_use_detail` | merchant-service | 额度使用明细 |
| `industry_commerce` | merchant-service | 工商业客户 |
| `posthouse` | merchant-service | 驿站/自提点 |
| `posthouse_config` | merchant-service | 驿站配置开关 |
| `posthouse_group` | merchant-service | 驿站分组 |
| `driver_delivery` | merchant-service | 配送线路 |
| `driver_delivery_region` | merchant-service | 配送区域(Deprecated) |
| `shop` | merchant-service | 店铺 |
| `yzz_shop` | merchant-service | 云智妆店铺 |
| `yzz_guide` | merchant-service | 云智妆导购员 |
| `yzz_shop_member` | merchant-service | 下单会员-导购关系 |
| `supplier` | merchant-service | 供应商 |
| `supplier_company` | merchant-service | 供应商服务公司 |
| `park_appraise` | merchant-service | 园区评价(v1) |
| `park_appraise_up` | merchant-service | 园区评价(v2) |
| `park_appraise_two` | merchant-service | 园区评价(v3) |
| `shop_carousel` | merchant-service | 店铺轮播图 |
| `shop_customer` | merchant-service | 店铺客户 |
| `shop_express` | merchant-service | 店铺快递设置 |
