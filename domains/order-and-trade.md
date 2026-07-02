# 订单与交易服务

> 本文档分析了 PVS 光伏电站系统中两个核心订单相关服务：`order-service` 和 `rrsjk-trade-service` 的业务逻辑、架构分工和数据库设计。

## 1. order-service

### 1.1 服务定位

**order-service** 是海尔 CBS（Commerce Business System）电商平台的**订单核心后端服务**，是一个传统的 Dubbo RPC 服务，主要面向 B2B/B2B2C 电商业务场景。它是整个电商系统的订单中枢，负责订单的全生命周期管理、物流配送调度、发票处理、以及与 SAP/JDE 等 ERP 系统的对接。

- **技术栈**: Java + Spring + Dubbo + MyBatis + JMS
- **模块结构**: `order-service/` (接口/实体层) + `order-impl/` (实现层)
- **代码规模**: 1217 个 Java 文件，165 个 MyBatis Mapper XML
- **包路径**: `com.haier.cbs.order`

> **注意**: order-service 是一个传统电商订单服务，与光伏电站业务**没有直接关联**。rrsjk-trade-service 才是光伏业务（乐农/顺逛等渠道）的交易核心。

### 1.2 核心 API（Dubbo Service 接口）

order-service 通过 Dubbo 暴露以下服务接口（`com.haier.cbs.order.service.*`）：

#### 订单核心服务
| 服务接口 | 说明 |
|---------|------|
| `OrderService` | 订单主服务：创建、查询、取消、确认订单 |
| `OrderProductsService` | 网单（Order Product）服务：网单级操作 |
| `OrderStatusService` | 订单状态管理服务 |
| `OrderPubService` | 订单公共服务 |
| `OrderRelationService` | 订单关联关系服务 |
| `OrderOperateLogsService` | 订单操作日志服务 |
| `OrderHpService` | 订单 HP（售后服务）服务 |
| `OrderCosmoService` | 卡奥斯（COSMO）订单服务 |

#### 订单类型服务
| 服务接口 | 说明 |
|---------|------|
| `CompanyOrderService` | 企业订单服务 |
| `ShopOrderService` | 商城订单服务 |
| `SimpleOrderService` | 简单订单服务 |
| `ForecastOrderService` | 预测订单服务 |
| `EchannelOrderService` | 电子渠道订单服务（天猫/京东等第三方） |
| `EchannelReshuiTradeService` | 热水交易平台服务 |
| `RrsjkOrderService` | 日日顺家居订单服务 |

#### 物流与配送
| 服务接口 | 说明 |
|---------|------|
| `ExpressService` | 快递服务 |
| `ExpressRegisterService` | 快递登记服务 |
| `ExpressRecordService` | 快递记录服务 |
| `HpDispatchService` | 售后服务派工服务 |
| `StorageNotifyService` | 仓储通知服务 |
| `VOMTransferOrderService` | VOM 调拨订单服务 |

#### VOM（仓储管理）相关
| 服务接口 | 说明 |
|---------|------|
| `VOMProductAndOrderService` | VOM 产品与订单服务 |
| `VomAllocateOrderService` | VOM 调拨订单服务 |
| `VOMReturnFactoryProductAndOrderService` | VOM 返厂产品服务 |
| `V3StockService` | V3 库存服务 |
| `V3StoreService` | V3 仓库服务 |

#### 财务与发票
| 服务接口 | 说明 |
|---------|------|
| `InvoiceService` | 发票服务 |
| `InvoicePostService` | 发票邮寄服务 |
| `IncomeActualService` | 实际收入服务 |
| `IncomeForecastService` | 预测收入服务 |
| `BudgetService` | 预算服务 |
| `TransBudgetToBCCService` | 预算同步到 BCC 服务 |

#### SAP/ERP 集成
| 服务接口 | 说明 |
|---------|------|
| `SyncSelfOrderToSapService` | 自营订单同步到 SAP |
| `SyncFinanceToSapService` | 财务数据同步到 SAP |
| `SyncInvoiceToSapService` | 发票同步到 SAP |
| `SapFinanceAndOrderService` | SAP 财务与订单综合服务 |

#### 其他
| 服务接口 | 说明 |
|---------|------|
| `RrsCctOrderService` | 日日顺 CCT 订单服务 |
| `RrsRepairService` | 日日顺维修服务 |
| `RrsRecommendService` | 日日顺推荐服务 |
| `RegionsService` | 区域服务 |
| `SuppliersService` | 供应商服务 |
| `ChangePriceService` | 改价服务 |
| `ApplyReturnGoodService` | 退货申请服务 |

### 1.3 订单流程

order-service 的订单流程围绕 **"订单(Orders) → 网单(OrderProducts)"** 两级模型展开：

```
用户下单 → 创建订单(Orders) → 拆分网单(OrderProducts) → 支付 → 同步到LES/WMS → 
出库 → 物流配送 → 用户签收 → 完成
```

#### 详细流程

1. **创建订单**
   - 通过 `SaveOrderFactory` 工厂创建不同类型的订单
   - 支持多种下单模式：`SCSaveOrder`（顺逛）、`TaobaoSaveOrder`（淘宝）、`TSShopSaveOrder`（天猫店铺）
   - 订单创建时同时生成网单（OrderProducts），一个订单可包含多个网单

2. **支付**
   - 支付状态通过 `PaymentStatus` 枚举管理
   - 支持货到付款（COD）、在线支付等
   - 支付成功后触发订单确认

3. **订单确认与拆分**
   - 订单确认后，网单按商品/仓库拆分为独立的配送单元
   - 同步到 LES（物流执行系统）或 VOM（仓储管理系统）

4. **仓储出库（LES/VOM 流程）**
   - 网单状态流转：`处理中(0) → 占用库存(1) → 同步到HP/VOM(2) → 待出库(8) → 待审核(10)`
   - LES 开提单后，网单进入待出库状态
   - 支持转运模式：第一次出库 → 转运入库 → 第二次出库

5. **物流配送**
   - 出库后生成快递单号
   - 通过 Express 相关服务跟踪物流
   - VOM/TMS 系统跟踪配送状态

6. **签收与完成**
   - 用户签收 → 网单状态变为 `用户签收(140)`
   - 订单状态变为 `已完成(203)`
   - 触发发票开具流程

### 1.4 订单状态

#### 订单状态（OrderStatus）- 订单级别

| Code | 状态 | 说明 |
|------|------|------|
| 200 | OS_UN_CONFIRM | 未确认 |
| 201 | OS_CONFIRM | 已确认 |
| 202 | OS_CANCEL | 已取消 |
| 203 | OS_COMPLETE | 已完成 |
| 204 | OS_NOSTOCK | 部分缺货 |
| -100 | UNDEFINED | 未定义 |

#### 网单状态（OrderProductStatus）- 网单级别

| Code | 状态 | 说明 |
|------|------|------|
| 0 | START_STATUS | 处理中 |
| 1 | USE_STORE | 占用库存 |
| 2 | SYNC_HP / SYNC_VOM | 同步到 HP/VOM |
| 4 | DISPATCH_NET_POINT | 已分配到网点 |
| 8 | LES_SHIPPING | 待出库 |
| 10 | WAIT_VERIFY | 待审核 |
| 11 | WAIT_TRANS_SHIP_IN | 待转运入库 |
| 12 | WAIT_TRANS_SHIP_OUT | 待转运出库 |
| 40 | WAIT_DELIVERY | 待发货 |
| 70 | WAIT_DELIVER | 待交付 |
| 101 | STATUS_VOM_ACCEPT | VOM 接单 |
| 102 | STATUS_VOM_DELIVERY | 网点交付 |
| 103 | STATUS_VOM_OUT | 已出库 |
| 104 | STATUS_VOM_DELIVERING | 网点派送 |
| 105 | STATUS_VOM_SIGN | 用户签收 |
| 106 | STATUS_VOM_CHANGE | 用户改约 |
| 107 | STATUS_VOM_COD_SUCCESS | 到付收款成功 |
| 110 | CANCEL_CLOSE | 取消关闭 |
| 111 | STATUS_VOM_FAILED | VOM 拒单 |
| 112 | STATUS_VOM_SIGN_FAILED | 用户拒收 |
| 113 | STATUS_VOM_RETURN | 拒收入库 |
| 130 | COMPLETED_CLOSE | 完成关闭 |
| 140 | USER_SIGN | 用户签收 |
| 150 | NET_POINT_REFUSE | 网点拒单 |
| 160 | USER_REJECTION | 用户拒收 |

#### VOM TMS 物流状态

| Code | 状态 | 说明 |
|------|------|------|
| 201 | TMS_ACCEPT | 揽收 |
| 202 | TMS_REJECT | 揽收失败 |
| 203 | TMS_STATION_IN | 分站进 |
| 204 | TMS_STATION_OUT | 分站出 |
| 205 | TMS_FAILED_IN | 转运入库 |
| 206 | TMS_FAILED_OUT | 转运出库 |
| 208 | TMS_DB_CREATE | 调拨单生成 |
| 211 | TMS_RESULT | 退货单推送到 VOM |
| 301 | TMS_DB_OUT | 调拨单出库 |
| 302 | TMS_DB_IN | 调拨单入库 |
| 303 | TMS_ERROR | 异常 |

#### 支付状态（PaymentStatus）

| Code | 状态 | 说明 |
|------|------|------|
| 100 | PS_UNPAID | 未付款 |
| 101 | PS_PAID | 买家已付款 |
| 102 | PS_REFUNDING | 待退款 |
| 103 | PS_REFUNDED | 已退款 |

#### 订单类型（OrderType）

| Value | 类型 | 说明 |
|-------|------|------|
| 0 | TYPE_NORMAL | 普通订单 |
| 1 | TYPE_GROUP_ADVANCE | 团购预付款订单 |
| 2 | TYPE_GROUP_TAIL | 团购尾款订单 |
| 3 | TYPE_GROUP | 普通团购订单 |
| 4 | TYPE_GROUP_ADVANCE_TAIL | 定金-尾款订单 |

### 1.5 订单与电站的关系

**order-service 与光伏电站没有直接关系**。这是一个通用的海尔电商 CBS 订单服务，主要处理家电等商品的电商订单。光伏电站相关的订单交易逻辑在 `rrsjk-trade-service` 中。

order-service 中的 `RrsjkOrderService` 提供了日日顺家居相关订单的查询和发货操作，但这是电商业务，不是光伏业务。

### 1.6 与 SAP 的交互

order-service 与 SAP 通过 WebService (WSDL) 进行深度集成：

#### SAP 交互方式
- 使用 WSDL SOAP 协议调用 SAP 接口
- WSDL 文件位于 `order-impl/src/main/resources/wsdl/sap/`

#### 主要 SAP 交互场景

| 交互场景 | 服务/模块 | 说明 |
|---------|----------|------|
| 销售订单同步 | `SyncSelfOrderToSapService` | 将自营订单同步为 SAP 销售订单（Sale Order） |
| 采购订单同步 | `SyncSelfOrderToSapService` | 将 VOM 采购订单同步到 SAP |
| 发货通知 | `sap/delivery` | 向 SAP 同步发货信息（Delivery） |
| 财务同步 | `SyncFinanceToSapService` | 向 SAP 同步财务数据 |
| 发票同步 | `SyncInvoiceToSapService` | 向 SAP 同步发票数据 |
| 开票凭证 | `sap/invoiceVoucher` | SAP 发票凭证同步 |
| 发票校验 | `sap/invoiceVerification` | SAP 发票校验 |
| 账单订单 | `sap/billingOrder` | SAP 账单订单同步 |

#### SAP 交互队列
- `SapQueueMapper` - SAP 同步队列
- `SapRecordMapper` - SAP 同步记录
- `SapOrderRecordMapper` - SAP 订单记录
- `SapPurchaseRecordMapper` - SAP 采购记录
- `SapReverseRecordMapper` - SAP 冲销记录
- `InvoiceSAPLogsMapper` - SAP 发票日志

### 1.7 主要数据库表

通过 Mapper XML 分析，order-service 涉及的核心数据库表：

#### 核心订单表
| 表名 (Mapper) | 说明 |
|--------------|------|
| `OrdersMapper` | 订单主表 - 订单基本信息、金额、地址、状态 |
| `OrderProductsMapper` | 网单表 - 订单行项目、商品、物流、状态 |
| `OrderWorkflowsMapper` | 订单全流程监控表 |
| `OrderOperateLogsMapper` | 订单操作日志表 |
| `OrderStatisticMapper` | 订单统计表 |
| `OrderRelationMapper` | 订单关联关系表 |
| `OrderQueueExtendMapper` | 订单扩展队列 |
| `OrderQueuesMapper` | 订单队列 |
| `OrderAndOPExtAttr` | 订单及网单扩展属性 |
| `OrderCancelLogsMapper` | 订单取消日志 |
| `Order2thsMapper` | 订单与第三方系统映射 |

#### 发票相关
| 表名 | 说明 |
|------|------|
| `InvoicesMapper` | 发票表 |
| `InvoicesReadyMapper` | 待开发票表 |
| `InvoiceQueueMapper` | 发票队列 |
| `InvoiceLineMapper` | 发票行表 |
| `InvoicePostMapper` | 发票邮寄表 |
| `InvoiceElectricLogsMapper` | 电子发票日志 |
| `InvoiceSAPLogsMapper` | SAP 发票日志 |

#### 物流与快递
| 表名 | 说明 |
|------|------|
| `ExpressMapper` | 快递表 |
| `ExpressCompany` | 快递公司表 |
| `ExpressRecordMapper` | 快递记录表 |
| `ExpressRegisterMapper` | 快递登记表 |
| `ExpressAbortMapper` | 快递中止表 |

#### 仓储与 VOM
| 表名 | 说明 |
|------|------|
| `V3StockMapper` | V3 库存表 |
| `V3StoreMapper` | V3 仓库表 |
| `V3StoreCityMapper` | V3 城市仓库表 |
| `VOMQueuesMapper` | VOM 队列 |
| `VomAllocateOrderMapper` | VOM 调拨订单 |
| `VOMTransferOrderMapper` | VOM 转运订单 |
| `VomPoSapQueueMapper` | VOM 采购订单 SAP 队列 |

#### SAP/ERP 集成
| 表名 | 说明 |
|------|------|
| `SapQueueMapper` | SAP 同步队列 |
| `SapRecordMapper` | SAP 同步记录 |
| `SapOrderRecordMapper` | SAP 订单记录 |
| `SapPurchaseRecordMapper` | SAP 采购记录 |
| `SapReverseRecordMapper` | SAP 冲销记录 |
| `JdeQueuesMapper` | JDE 队列 |
| `LesQueuesMapper` | LES 队列 |

#### 财务与收入
| 表名 | 说明 |
|------|------|
| `IncomeActualMapper` | 实际收入 |
| `IncomeForecastMapper` | 预测收入 |
| `IncomeRecordMapper` | 收入记录 |
| `BudgetMapper` | 预算表 |
| `HPBccPayMapper` | HP BCC 支付 |

#### 售后维修
| 表名 | 说明 |
|------|------|
| `OrderRepairsMapper` | 订单维修表 |
| `OrderRepairLogsMapper` | 维修日志 |
| `HpOrder` | HP 工单 |
| `HpWorkMapper` | HP 工作单 |
| `HpDispatchMapper` | HP 派工单 |

#### 其他
| 表名 | 说明 |
|------|------|
| `BookLogsMapper` | 缺货记录表 |
| `BookProductsMapper` | 预定产品表 |
| `CompanyOrderMapper` | 企业订单表 |
| `ShopOrderMapper` | 商城订单表 |
| `RrsjkOrderMapper` | 日日顺家居订单 |
| `RrsCctOrderMapper` | 日日顺 CCT 订单 |
| `GroupOrdersMapper` | 团购订单表 |
| `EchannelTmallTrade` | 天猫交易表 |
| `MembersMapper` | 会员表 |
| `SuppliersMapper` | 供应商表 |
| `RegionsMapper` | 区域表 |

---

## 2. rrsjk-trade-service

### 2.1 服务定位

**rrsjk-trade-service** 是日日顺家居（RRSJK）的**交易核心服务**，专注于 B2B2C 电商交易链路。它是一个现代化的 Dubbo 微服务，采用 Spring Boot 架构，负责：

- **购物车管理**
- **订单创建**（完整的下单流程）
- **支付处理**（网银支付、银联等）
- **优惠券/活动管理**
- **发货与交易状态管理**
- **光伏电站相关订单**（包含 `lightStationId` 字段）

- **技术栈**: Java + Spring Boot + Dubbo + MyBatis + EventBus
- **模块结构**: `rrsjk-trade-api/` (接口/DTO/Entity) + `rrsjk-trade-impl/` (实现)
- **代码规模**: 912 个 Java 文件
- **包路径**: `com.rrsjk.trade`

### 2.2 核心 API（Dubbo Service 接口）

#### 交易与订单核心
| 服务接口 | 说明 |
|---------|------|
| `OrderCreateService` | 创建订单：`createOrder(OrderCreateRequest)` |
| `OrderService` | 订单管理：查询、修改、支付、退款 |
| `OrderTradeService` | 交易管理：发货、交易查询 |
| `OrderStatusService` | 订单状态服务 |
| `OrderSearchService` | 订单搜索服务 |
| `OrderItemService` | 订单项（Order Item）服务 |

#### 购物车
| 服务接口 | 说明 |
|---------|------|
| `CartService` | 购物车服务：添加、更新、查询、删除购物车商品 |

#### 优惠券与活动
| 服务接口 | 说明 |
|---------|------|
| `CouponService` | 优惠券服务：领取、查询、使用 |
| `CouponUseService` | 优惠券使用服务 |
| `ActivityService` | 活动服务 |
| `LottoryService` | 抽奖服务 |
| `RedPackageService` | 红包服务 |
| `LuckyWheelPrizeService` | 转盘奖品服务 |

#### 支付
| 服务接口 | 说明 |
|---------|------|
| `NetPayCallBackService` | 网银支付回调服务 |
| `NetPayLogService` | 网银支付日志 |
| `PayJobService` | 支付定时任务 |
| `FtpService` | FTP 服务（支付对账文件） |

#### 发票
| 服务接口 | 说明 |
|---------|------|
| `InvoiceService` | 发票服务 |
| `InvoiceJobService` | 发票定时任务 |

#### 光伏电站相关
| 服务接口 | 说明 |
|---------|------|
| `PhotovoltaicService` | 光伏服务 |
| `EnergyStorageProjectService` | 储能项目服务 |
| `HroisOrderService` | HROIS 订单服务 |
| `HroisOrderCreateService` | HROIS 订单创建 |
| `LightPurchaseSalesOrderService` | 光储采销订单服务 |
| `LightMaterialManageService` | 光储物料管理 |

#### 会员权益
| 服务接口 | 说明 |
|---------|------|
| `BenefitService` | 权益服务 |
| `MemberRankService` | 会员等级服务 |
| `CardOrderService` | 卡订单服务 |
| `RankCardService` | 等级卡服务 |

#### 其他
| 服务接口 | 说明 |
|---------|------|
| `ExpressRecordService` | 快递记录服务 |
| `BudgetService` | 预算服务 |
| `OrderCartService` | 订单购物车服务 |
| `OrderCartPurchaseService` | 采购购物车服务 |
| `OrderGroupService` | 团购服务 |
| `OrderRepairService` | 订单维修服务 |
| `OrderPriceService` | 订单价格服务 |
| `MerchantEvaluateService` | 商家评价服务 |
| `InternalPurchaseService` | 内部采购服务 |
| `CnOrderService` | 菜鸟订单服务 |

### 2.3 交易流程

rrsjk-trade-service 的交易流程采用**链式处理模式**（Chain of Responsibility）：

```
购物车 → 结算页 → 创建订单 → 支付 → 发货 → 确认收货 → 完成
```

#### 订单创建流程

订单创建通过 `OrderCreateServiceImpl` 实现，采用**操作链模式**：

```java
// 1. 初始化上下文
contextList = initContext.init(orderCreateRequest);

// 2. 遍历每个订单上下文，执行一系列操作
for (OrderCreateContext context : contextList) {
    orderOperate.operate(context, orders);           // 创建订单主记录
    orderExtrasOperate.operate(context, orders);     // 创建订单扩展属性
    orderItemOperate.operate(context, orders);       // 创建订单项
    orderInvoiceOperate.operate(context, orders);    // 创建发票信息
    cartOperate.operate(context);                    // 清空购物车
    orderItemPrepayOperate.operate(context, orders); // 创建预付款
    discountUseOperate.operate(context, orders);     // 使用优惠券
    internalPurchaseOperate.operate(context, orders);// 内部采购处理
    expertCustomerCreditOperate.operate(context, orders); // 专家客户信用
    yzzGuideOperate.operate(context, orders);        // 云智妆引导
    budgetOperate.operate(context, orders);          // 预算处理
    lightCoinOperate.operate(context, orders);       // 光伏能源币抵扣
}

// 3. 提交事务
transactionManager.commit(transactionStatus);

// 4. 异步发送事件
eventBus.post(new OrderCreateEvent(orderResultDtoList));
```

#### 支付流程

1. 用户下单后进入 `WAIT_BUYER_PAY` 状态
2. 调用 `toNetPay()` 跳转到网银支付
3. 支付成功后通过 `NetPayCallBackService` 回调更新状态
4. 状态变更为 `WAIT_SELLER_SEND_GOODS`

#### 发货流程

1. 商家调用 `outerDeliver()` 执行发货
2. 通过 `StrategyDelivedOrder` 策略模式变更状态
3. 状态变更为 `WAIT_BUYER_CONFIRM_GOODS`

### 2.4 订单状态

#### 交易状态（OrderStatus）

| 状态枚举 | 说明 |
|---------|------|
| WAIT_BUYER_PAY | 等待买家付款 |
| WAIT_GOODS_CONFIRM | 等待货物确认 |
| WAIT_SELLER_SEND_GOODS | 等待卖家发货 |
| WAIT_BUYER_CONFIRM_GOODS | 等待买家确认收货 |
| TRADE_BUYER_SIGNED | 买家已签收（货到付款专用） |
| TRADE_FINISHED | 交易成功 |
| TRADE_CLOSED | 交易关闭 |
| BUYER_CANCELED | 买家取消关闭 |

#### 订单类型（type 字段）

| 类型 | 说明 |
|------|------|
| normal | 普通订单 |

#### 渠道类型（channelType 字段）

| 类型 | 说明 |
|------|------|
| MALL | 商城订单 |
| PURCHASE | 采购订单 |
| GROUP | 团购订单 |

#### 支付周期（payPeriod 字段）

| 类型 | 说明 |
|------|------|
| period | 账期 |
| cash | 现款 |

#### 店铺类型（shopType 字段）

| 类型 | 说明 |
|------|------|
| 1 | 自营 |
| 2 | 县域 |
| 3 | 三方店 |

### 2.5 主要数据库表

通过 MyBatis Mapper XML 分析：

#### 核心订单表
| 表名 | 说明 |
|------|------|
| `Orders` | 订单主表（含 `lightStationId` 光伏电站ID字段） |
| `OrderItem` | 订单项表 |
| `OrderTrade` | 交易记录表 |
| `OrderExtras` | 订单扩展属性 |
| `OrderInvoice` | 订单发票信息 |
| `OrderBuyer` | 订单买家信息 |
| `OrderAttribute` / `OrderAttributeValue` | 订单自定义属性 |
| `OrderOperateLog` | 订单操作日志 |
| `OrderErrorLog` | 订单错误日志 |
| `OrderRetryQueue` | 订单重试队列 |
| `OrderSapQueue` | SAP 同步队列 |

#### 订单项扩展
| 表名 | 说明 |
|------|------|
| `OrderItemShop` | 订单项店铺信息 |
| `OrderItemBuyer` | 订单项买家信息 |
| `OrderItemCbs` | 订单项 CBS 关联 |
| `OrderItemEnomatic` | 订单项 Enomatic 信息 |
| `OrderItemFee` | 订单项费用 |
| `OrderItemFinance` | 订单项财务 |
| `OrderItemGroup` | 订单项团购信息 |
| `OrderItemJointVenture` | 订单项合资信息 |
| `OrderItemPrepay` | 订单项预付款 |

#### 购物车
| 表名 | 说明 |
|------|------|
| `Cart` | 购物车表 |

#### 优惠券
| 表名 | 说明 |
|------|------|
| `Coupon` | 优惠券表 |
| `CouponItem` | 优惠券商品关联 |
| `CouponUse` | 优惠券使用记录 |

#### 支付
| 表名 | 说明 |
|------|------|
| `NetPayLog` | 网银支付日志 |

#### 发票
| 表名 | 说明 |
|------|------|
| `Invoice` | 发票表 |
| `InvoiceFinance` | 发票财务表 |
| `InvoiceQueue` | 发票队列 |

#### 光伏与储能
| 表名 | 说明 |
|------|------|
| `Photovoltaic` | 光伏订单表 |
| `EnergyStorageProject` | 储能项目表 |
| `HroisOrder` | HROIS 订单 |
| `HroisOrderItem` | HROIS 订单项 |
| `HroisOrderBox` | HROIS 订单箱 |
| `HroisOrderCbs` | HROIS 订单 CBS 关联 |
| `HroisPurchaseOrder` | HROIS 采购订单 |
| `HroisSendInfoUpdate` | HROIS 发货信息更新 |
| `LightPurchaseSalesOrder` | 光储采销订单 |
| `LightPurchaseSalesPurchaseOrder` | 光储采购订单 |
| `LightMaterialManage` | 光储物料管理 |
| `LightOrderToEnergyStorageQueue` | 光储订单队列 |
| `LightOrderToPcsQueue` | PCS 订单队列 |
| `DsStockOrder` | 分布式库存订单 |
| `DsWarehouse` | 分布式仓库 |
| `DsPredictionOrder` | 分布式预测订单 |

#### 活动与权益
| 表名 | 说明 |
|------|------|
| `Activity` | 活动表 |
| `LottoryRecord` | 抽奖记录 |
| `ClaimPrizeRecord` | 领奖记录 |
| `LuckyWheelPrize` | 转盘奖品 |
| `Benefit` | 权益表 |
| `BenefitConsumer` | 权益消费 |
| `BenefitPackage` | 权益包 |
| `MemberRank` | 会员等级 |
| `CardOrder` | 卡订单 |
| `RankCard` | 等级卡 |

#### 其他
| 表名 | 说明 |
|------|------|
| `Budget` | 预算表 |
| `BudgetFeedback` | 预算反馈 |
| `InnerOrder` | 内部订单 |
| `InternalPurchase` | 内部采购 |
| `InternalPurchaseOrder` | 内部采购订单 |
| `ExpertOrder` | 专家订单 |
| `OrderRepair` | 订单维修 |
| `OrderCountyOperator` | 县域运营商 |
| `ExpressRecord` | 快递记录 |
| `HhOrder` | 户户通订单 |
| `BarCodeApply` | 条码申请 |
| `BarCodeDetail` | 条码明细 |

### 2.6 业务模式

rrsjk-trade-service 采用 **B2B2C** 混合业务模式：

- **B2C（商城模式）**: 普通用户通过商城下单，支持 M 站/PC/微信小程序等渠道
- **B2B（采购模式）**: 企业/县域运营商采购，支持账期支付
- **C2B2C（团购模式）**: 社区团长组织团购，有提货码机制
- **光伏特色**: 支持光伏电站关联下单，使用光伏能源币（LightCoin）抵扣

关键特征：
- `Orders` 表中有 `lightStationId`（光伏电站ID）和 `lightStationCode`（光伏电站编号）字段
- 支持 `useLightCoinQuantity`（使用光伏能源币数量）和 `useLightCoinAmount`（使用光伏能源币金额）
- 多店铺模式：自营店、县域店、三方店
- 多渠道：乐农(LN)、顺逛(SG) 等平台
- 公司实体：涉及多家公司（青岛海尔新能源、青岛海尔光伏新能源、日日顺科技等）

---

## 3. 两服务对比

| 维度 | order-service | rrsjk-trade-service |
|-----|--------------|---------------------|
| **服务定位** | 海尔 CBS 电商订单核心服务（传统架构） | 日日顺家居交易服务（现代微服务） |
| **业务领域** | 通用家电电商订单（B2B/B2C） | 光伏+乐农+顺逛交易（B2B2C 混合） |
| **与电站关系** | **无直接关系** | **直接关联**，订单绑定电站 |
| **技术架构** | Spring + Dubbo + MyBatis + JMS | Spring Boot + Dubbo + MyBatis + EventBus |
| **暴露方式** | Dubbo RPC 服务 | Dubbo RPC 服务 |
| **下单模式** | 工厂模式（SCSaveOrder、TaobaoSaveOrder 等） | 链式操作模式（OrderCreateContext + 多个 Operate） |
| **订单模型** | 订单(Orders) → 网单(OrderProducts) | 订单(Orders) → 订单项(OrderItem) |
| **支付处理** | 集成外部支付系统 | 内置网银支付（NetPay）+ 回调 |
| **购物车** | 无（依赖其他服务） | 有（CartService） |
| **优惠券** | 无 | 有（CouponService） |
| **SAP 集成** | **深度集成**，通过 WSDL SOAP 同步订单、发货、财务、发票 | 轻量集成，通过 OrderSapQueue 队列异步同步 |
| **物流集成** | 深度集成 LES/VOM/TMS 系统 | 简化物流，ExpressRecord 记录 |
| **订单状态** | 订单状态（5种）+ 网单状态（30+种 VOM 状态） | 交易状态（8种），简洁明了 |
| **订单类型** | 普通/团购预付款/团购尾款/普通团购/定金尾款 | 普通/采购/团购/光伏 |
| **发票** | 完整的发票开具、邮寄、SAP 同步 | 发票管理 + 定时任务 |
| **售后** | 完整的维修、工单、派工体系 | 简化的订单维修 |
| **数据库表数量** | 165 个 Mapper XML | 约 80 个 Mapper XML |
| **主要实体表** | Orders, OrderProducts, OrderWorkflows | Orders, OrderItem, OrderTrade |
| **公司实体** | 无明确公司实体字段 | 多公司支持（1Q80/1PG0/0LC0/0W50 等） |
| **光伏特色** | 无 | 光伏电站关联、光伏能源币抵扣 |

### 3.1 分工总结

```
┌─────────────────────────────────────────────────────────────┐
│                    前端应用层                                  │
│         商城/小程序/APP/PC/H5                                 │
└─────────────────────────┬───────────────────────────────────┘
                          │
           ┌──────────────┼──────────────┐
           ▼              ▼              ▼
┌─────────────────┐ ┌─────────────────┐ ┌────────────────┐
│  rrsjk-trade-   │ │  其他前端网关    │ │ 第三方平台      │
│  service        │ │                 │ │ (天猫/京东等)   │
│                 │ │                 │ └────────┬───────┘
│  - 购物车        │ │                 │          │
│  - 创建订单      │ │                 │          ▼
│  - 支付         │ │                 │ ┌────────────────┐
│  - 优惠券       │ │                 │ │  order-service │
│  - 交易状态     │ │                 │ │                │
│  - 发货         │ │                 │ │ - 订单同步      │
│  - 退款         │ │                 │ │ - 物流调度      │
└────────┬────────┘ └─────────────────┘ │ - SAP 集成      │
         │                              │ - 发票开具      │
         │ 调用订单履约                   │ - 售后维修      │
         ▼                              └────────┬───────┘
┌─────────────────┐                              │
│  订单履约层       │◄─────────────────────────────┘
│  (LES/VOM/WMS)  │   SAP WebService (SOAP)
└─────────────────┘
```

- **rrsjk-trade-service**: 面向**前端交易**，处理用户从加购物车到支付完成的完整交易链路
- **order-service**: 面向**后端履约**，处理订单确认后的物流调度、仓储出库、SAP 同步、发票开具等

两个服务通过 Dubbo RPC 相互调用，rrsjk-trade-service 创建订单后可能通过 Dubbo 调用 order-service 进行后续的物流和财务处理。

---

### 1.10 ESAP 服务集成 (代码明确证明, 2026-05-21 全量通读补遗)
**来源**: `order-service` (majinhu, commits: 07dff43, 25e3549, a08e535, dcbd277, 1f534f4, 2025-11-27)

order-service 在 2025-11 新增了 **ESAP 服务**集成，这是 SAP 接口的新一代实现:

- **新增 SAP FI_COSMO_POST 接口支持**: 用于卡奥斯(COSMO)平台的财务过账
- **SAP 客户端模型优化**: 重构属性转换调用，提升 SAP 客户端代码的可维护性
- **GVS 环境 SAP 接口配置**: 更新 SAP 接口配置以支持 GVS (Global Verification Service?) 环境
- **ESAP 测试类**: 添加了 ESAP 服务的单元测试，修改日期解析方式

**技术细节**:
- ESAP 相关代码位于 `order-impl/src/test/java/com/haier/cbs/order/` 测试目录
- 涉及 `DubboConfig.java` 中 zookeeper 注册中心配置 (timeout=10000ms)
- SAP 客户端模型属性转换优化减少了类型转换错误

---

### 1.11 rrsjk-trade-service 补充: Hrois 海外订单/发票Job/条码/FTP支付 (代码明确证明, 2026-06-03)
**来源**: `rrsjk-trade-service` 全量通读 (566个业务文件)

#### Hrois 海外订单流程
**来源**: `trade/order/` 下的 Hrois* 系列 Service/DTO/Entity

- **创建**: `HroisOrderCreateService.create()` — 接收 HroisOrderCreateRequest (含订单明细+装箱明细) → 返回 CBS订单号+Hrois订单号
- **状态处理**: `HroisOrderCreateService.status()` — 处理 Hrois 订单状态变更 (CANCELED/NEGOTIATE)
- **子订单操作**: `HroisOrderItemService.operate()` — 备货(MAKE)/发货(DELIVER)
- **装箱管理**: `HroisOrderBoxService` — 装箱信息查询/创建/更新
- **发货修改申请**: `HroisSendInfoUpdateService` — 修改集装箱号/铅封号 → 审核(PASS/REJECT)
- **采购单**: `HroisPurchaseOrderService` — 海外 GVS 采购单管理
- **CBS 映射**: `HroisOrderCbsService` — Hrois 订单与 CBS 订单的关联
- **操作日志**: `HroisOperationLogService` — 海外订单操作记录

#### 发票处理 Job 体系 (InvoiceJobService)
**来源**: `trade/job/invoice/service/InvoiceJobService.java` (20+ Job方法)

| Job 方法 | 功能 | 执行方式 |
|---|---|---|
| `generatorInvoice()` | 生成发票信息 | 定时 |
| `elecInvoice()` | 电子发票处理 | 定时 |
| `vatInvoice()` | 增值税专用发票处理 | 定时 |
| `vatInvoiceQueryResult()` | 专票结果查询 | 定时 |
| `cloudInvoiceInvalid()` | 票税云作废红冲 | 定时 |
| `cloudInvoiceInvalidQueryResult()` | 票税云红冲结果查询 | 定时 |
| `elecInvoiceQueryResult()` | 电子发票结果查询 | 定时 |
| `cloudInvoiceSapVoucherArchive()` | 票税云发票SAP凭证归档 | 定时 |
| `vatInvoiceByOperation()` | 运维收入增值税专票合并 | 定时 |
| `vatInvoiceByLightElec()` | 电费收益增值税专票 | **@Async** |
| `vatInvoiceQueryResultByLightElec()` | 电费收益专票结果查询 | **@Async** |
| `cloudInvoiceSapVoucherArchiveByLightElec()` | 电费收益SAP凭证归档 | **@Async** |
| `vatInvoiceByMerge()` | 增值税专票合并开票 | 定时 |
| `vatInvoiceQueryResultByMerge()` | 合并开票结果查询 | 定时 |
| `cloudInvoiceSapVoucherArchiveByMerge()` | 合并开票SAP凭证归档 | 定时 |
| `electricInvoiceReverse()` | 电费收益发票红冲(票税云/全电票) | 定时 |
| `electricInvoiceReverseResultQuery()` | 电费收益红冲结果查询 | 定时 |

#### 条码申请管理 (BarCodeApplyService)
**来源**: `trade/order/service/BarCodeApplyService.java`, `BarCodeDetailService.java`

- `BarCodeApply` — 条码申请主表 (申请单号/状态)
- `BarCodeDetail` — 条码明细表 (条码号/申请单关联)
- 功能: 条码申请 → 生码 → 单条/批量作废

#### FTP 支付对账 (FtpService)
**来源**: `trade/pay/service/FtpService.java`

- `download1PG0(dateTime)` — 下载1PG0支付文件
- `download1QJ0(dateTime)` — 下载1QJ0收款文件
- `download4110(dateTime)` — 下载4110文件
- `checkPayment(dateTime)` — 支付对账
- `checkRefund(dateTime)` — 退款对账

#### 零碳采购单 (LightPurchaseSalesOrderService)
**来源**: `trade/order/service/LightPurchaseSalesOrderService.java`

- `createOrder()` — 创建零碳适家采购订单
- `confirmPay()` / `batchConfirmPay()` — 确认收款
- `confirmReceipt()` — 确认收货 (零碳适家用)
- `incomeToSap()` / `zeroCarbonIncomeToSap()` — 收入推 SAP
- `uploadReceipt()` — 上传签收单
- `confirmReceiptUrl()` — 签收单审核
- `findSalesRevenue()` — 零碳适家销售收入报表
- `findTouchpoint()` — 触点统计查询

#### 订单推送队列
**来源**: `LightOrderToPcsQueueService`, `LightOrderToEnergyStorageQueueService`, `PcsOrderDeliveryToLightQueueService`

- `LightOrderToPcsQueue` — 订单推送到 PCS 队列
- `LightOrderToEnergyStorageQueue` — 订单推送到储能队列
- `PcsOrderDeliveryToLightQueue` — PCS发货回推光伏队列 (自动发货)

**储能订单推送触发条件** (代码明确证明, 2026-07-01):
- **来源**: `rrsjk-trade-service` → `LightPurchaseSalesPurchaseOrderServiceImpl.java` (commit: 03a0b6e0, laowang, 2026-07-01)
- **规则**: 采购单确认时，同时满足 `supplierCode == "V99694"` AND `companyCode == "1QJ0"` 才推送到储能系统
- **变更**: 此前仅检查供应商代码 V99694，2026-07-01 增加公司代码 1QJ0 校验，避免不符合条件的订单被错误推送
- **推送内容**: 订单号、子订单号、订单类型、SKU编码、价格、数量、公司信息、收货地址等 → `LightOrderToEnergyStorageQueue` 表

**与现有 SAP 集成的关系**: order-service 已有成熟的 SAP 同步体系 (SyncSelfOrderToSapService, SyncFinanceToSapService, SyncInvoiceToSapService)，ESAP 是对现有 SAP 集成能力的扩展，专门面向卡奥斯平台。

---

## 子订单退款定时任务和订单状态管理 (代码明确证明, 2026-01-20)
**来源**: `rrsjk-trade-service` (代继宁, commits: 04e251b, 19b16f4, 5f45c1f, 870329e, 0caf480, 2026-01-20)

- 添加子订单退款定时任务功能
- 修复退款申请处理异常问题
- 修复退款申请处理失败时的异常处理逻辑
- 添加订单项退款作业服务配置
- 修正订单退款任务服务引用配置

## 绿证交易相关 (代码明确证明, 2026-01-19~2026-02-08)
**来源**: `rrsjk-light-report-service` + `rrsjk-light-service` (张硕文/商轶龙/王金浩)
**需求**: TAEI-2846 【绿证交易】绿证进度管理 + TAEI-2850 【绿证交易】自动开票改手动开票 + TAEI-2855 【绿证交易】意向管理/销售管理搜索项

- 绿证进度管理: 新增绿证进度管理页面和接口
- 自动开票改手动开票: 绿证交易发票从自动触发改为手动触发
- 意向管理: 新增搜索项"审批节点"
- 销售管理: 新增搜索项"合同节点"、"划证节点"
- 回款管理: 增加手动开票功能 (he-vpp.admin-h5, 张硕文)
