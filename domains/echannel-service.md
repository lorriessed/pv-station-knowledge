# 电商渠道订单聚合服务 (Echannel Service)

更新时间: 2026-05-24

> **来源**: `rrsjk-echannel-service` 全量通读 (2026-05-24)
> **证据等级**: 代码明确证明

## 服务定位

`rrsjk-echannel-service` 是一个**多渠道电商订单聚合服务**，负责从多个外部电商平台拉取订单、同步状态、处理退款，并将订单转换到内部交易体系。

与光伏核心业务的关系：这是一个**遗留/边缘服务**，最初为海尔电商业务（乐农商城、快递、水站等）设计，不直接处理光伏电站业务。但在财务结算 (`rrsjk-finance-service`) 中，其订单数据会被引用用于佣金结算、对账等。

## 技术架构

- **框架**: Spring Boot 2.2.1 + Dubbo 2.7.4.1 + MyBatis 3.5.2
- **部署**: appassembler-maven-plugin 打包为 JSW daemon
- **依赖**: rrsjk-trade-api, rrsjk-pay-api, rrsjk-member-api, rrsjk-merchant-api, rrsjk-item-api, rrsjk-system-api
- **父 POM**: rrs-parent 7.0.2（较老，大部分其他服务用 8.0.5）

## 接入的电商平台

### 1. 贝店 (Beibei)

| 项目 | 值 |
|---|---|
| API 网关 | `http://api.open.beibei.com/outer_api/out_gateway/route.html` |
| 签名方式 | TreeMap 排序 + BeibeiSdk.getSign |
| 订单查询 | `tradeOrderGet` — 按时间范围分页拉取订单 |
| 发货 | `tradeLogisticsShip` — 推送快递公司和单号 |
| 订单状态 | 1:待发货, 2:已发货, 3:已完成, 4:已关闭 |

**业务流程**:
```
定时拉取 → BeibeiApiModel.tradeOrderGet() → BeibeiEchannelTradeModel.invoke()
  ├── 新订单 → BeibeiTradeCreateModel.create() → echannel_trade + echannel_trade_order + echannel_trade_promotion
  └── 已有订单 → BeibeiTradeUpdateModel.update() → 更新状态
  └── 生成队列 → echannelOrderQueueModel.echannelOrderQueue()
```

**实体表**: `echannel_trade`, `echannel_trade_order`, `echannel_trade_promotion`

### 2. 建行善融商务 (CCB)

| 项目 | 值 |
|---|---|
| 协议 | SOAP/XML + AES 加密 (CcbBuyAesUtils) |
| WSDL | `IntegrationServiceImplService` (Apache CXF 2.7.16 生成) |
| 交易码 | T0005(物流推送), T0007(单笔查询), T0008(批量查询) |
| 返回码 | `000000` = 成功 |

**订单状态映射** (`OrderInfo.Status`):
- `WAIT_SELLER_SEND_GOODS` — 待发货
- `WAIT_BUYER_CONFIRM_GOODS` — 待收货
- `TRADE_FINISHED` — 交易完成
- `WAIT_SELLER_REFUND_SEND_GOODS` — 待卖家退款发货
- `WAIT_SELLER_REFUND_CONFIRM_GOODS` — 待卖家退款确认
- `TRADE_CLOSED` — 交易关闭

**退款逻辑** (`CcbEchannelRefundModel`):
- 状态为退款中 → 创建 `echannel_refund` 记录 + 进入退款队列
- 状态为正常交易 → 取消已有退款

**特殊规则**:
- 电子券金额 > 0 → 标记为手工处理（自动流程不支持）
- 商户优惠金额 > 0 → 标记为手工处理
- 运费 > 0 → 标记为手工处理
- `TRADE_CLOSED` 状态 → 不生成/不更新订单

**拉取策略** (`PullCcbOrderModel`):
- 从 `echannel_api` 表读取执行策略（延迟分钟、开始/结束时间、间隔分钟）
- 分页拉取（pageNo 递增，hasNext 判断）
- 每次执行后更新 beginAt/endAt 为下一个时间窗口

### 3. 城村通 (CCT)

城村通是海尔农村物流平台，提供快递价格查询和配送下单功能。

**主要接口** (`EchannelCctService`):
- `getExpressPrice(tradeOrderId)` — 查询快递价格
- 快递配送下单 — `CctShipperExpressRequest`
- 出库配送单 — `CctOrderHanderRequest`

**配送类型枚举** (`EchannelChangeRequest.DeliveryType`):
- `express` — 普通快递
- `cct` — 城村通
- `cct_express` — 城村通快递
- `cct_car` — 城村通车队

### 4. 抖音小店 (Douyin)

**主要接口** (`DouyinOrderService`):
- `pullDouyinOrder()` — 拉取订单
- `pullDouyinRefund()` — 拉取退款
- `pullDouyinAfterSale()` — 拉取售后

**售后处理枚举** (`DouyinBuyerReturnRequest.Type`):
- `1` — 同意客户发货
- `2` — 拒绝退货

**拒绝原因枚举** (`DouyinBuyerReturnRequest.Comment`):
1. 未收到货（未填写退货单号）
2. 退货与原订单不符
3. 退回商品影响二次销售 / 超出售后时效
4. 买家误操作/取消申请
5. 已与买家协商补偿
6. 已与买家协商补发/换货

**商家拆包收货审核** (`DouyinFirmReceiveRequest`):
- Type: 1=同意收货并退款, 2=拒绝并申请客服介入, 3=与客户和解
- 登记原因: 1=7天无理由退货, 2=产品质量问题, 3=发错货
- 包装状况: 1=无, 2=有但非新, 3=新
- 外观状况: 1=新, 2=破损
- 功能状况: 1=完好, 2=损坏, 3=待检查

### 5. 顺逛 (Shunguang)

**订单状态枚举** (`SgOrderRequest.OrderStatus`):
- `1` — 待发货
- `2` — 待收货（已发货）
- `3` — 已完成（已签收）
- `4` — 已取消（取消关闭）

**操作类型** (`SgOperateRequest.CbsStatus`):
- `CK` — 出库
- `QS` — 签收
- `GY` — 改约

**退款审核** (`SgRefundAuditRequest`):
- Type: 1=退货审核, 2=退款审核
- Agree: 1=同意, 2=拒绝

## 核心数据模型

### echannel_trade（渠道交易主表）
- channel — 渠道标识（BEIBEI/CCB/DOUYIN/SG等）
- tid — 平台订单号
- status — 平台交易状态
- original_status — 原子订单状态
- member_id — 会员ID
- pay_time — 支付时间

### echannel_trade_order（子交易表）
- trade_id — 关联主交易
- oid — 子订单号（格式: tid_skuId）
- status — 状态
- refund_status — 退款状态

### echannel_api（API执行策略表）
- channel — 渠道
- api — 接口类型（PULL_ORDER等）
- delay_minute — 执行延迟分钟
- begin_at / end_at — 执行时间窗口
- interval_minute — 间隔分钟

## Dubbo 服务接口

| 接口 | 方法 | 说明 |
|---|---|---|
| `CcbOrderService` | pullCcbOrder() | 拉取建行善融商务订单 |
| `DouyinOrderService` | pullDouyinOrder() | 拉取抖音小店订单 |
| `DouyinOrderService` | pullDouyinRefund() | 拉取抖音退款 |
| `DouyinOrderService` | pullDouyinAfterSale() | 拉取抖音售后 |
| `SgOrderService` | pullSgOrder() | 拉取顺逛订单 |
| `SgOrderService` | pullSgRefund() | 拉取顺逛退款 |
| `EchannelOrderPullService` | pullOrderDouyin/Ccb/Sg/Ln/Tmall/Beibei() | 统一拉取接口 |
| `EchannelChangeService` | change() | 交易改变（发货/关闭） |
| `EchannelDeliverService` | echannelDeliver() | 渠道订单发货 |
| `EchannelRefundService` | echannelRefundAudit() | 退款审核 |
| `EchannelStatusService` | echannelStatus() | 渠道订单状态同步 |
| `EchannelOrderService` | converOrder() | 转换订单 |

## 订单转换队列

所有渠道订单拉取后进入 `echannel_order_queue` 队列，由 `converOrder()` 方法消费，将平台订单转换为内部订单体系（rrsjk-trade）。

## 与光伏业务的关系

此服务**不直接处理光伏电站业务**。它是一个通用的电商渠道聚合层，主要服务于海尔乐农商城等非光伏电商业务。其订单数据在财务服务 (`rrsjk-finance-service`) 中被引用用于：
- 第三方店铺佣金结算 (`SettlementThirdOrderItemCommission`)
- 对账 (`CheckAccountError`)
- 收入报表 (`ReportIncomeRecord`)
