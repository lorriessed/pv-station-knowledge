# 支付服务域 (Payment Domain)

> 统一支付网关，对接多渠道支付（微信、支付宝、建行、百度、转账汇款、乐农钱包），支持商城订单支付、水站支付、光伏押金支付、水控机支付等场景。
> 更新时间: 2026-06-02 (全量通读补充)

---

## 1. 服务架构

### 1.1 服务拆分

| 仓库 | 角色 | 端口 | 上下文路径 |
|---|---|---|---|
| `rrsjk-pay-service` | 支付 Dubbo 服务（业务逻辑层） | N/A | N/A |
| `rrsjk-pay-web` | 支付 Web 网关（REST Controller → Dubbo） | 8093 | `/payapi` |

### 1.2 架构图

```
前端/小程序
  │
  ▼
rrsjk-pay-web (REST API, port 8093, context: /payapi)
  │  ├─ PaymentController         /payapi/pay/*         支付单管理
  │  ├─ PayController             /payapi/pay/pay.do    拉起支付
  │  ├─ PayDispenserController    /payapi/payDispenser/* 水站支付
  │  ├─ PayWaterControlController /payapi/payWaterControl/* 水控机支付
  │  └─ Notify Controllers        /payapi/notify/*      支付回调
  │
  ▼ (Dubbo RPC)
rrsjk-pay-service (Dubbo Provider, application: rrsjk-pay-service)
  │  ├─ PaymentService             支付单CRUD、创建
  │  ├─ PayService                 发起支付/查询结果
  │  ├─ PayNotifyService           支付回调处理
  │  ├─ RefundService              退款发起
  │  ├─ RefundNotifyService        退款回调/审核
  │  ├─ PayDispenserService        水站支付
  │  └─ PayDispenserNotifyService  水站支付回调
  │
  ▼ (Dubbo Consumer)
rrsjk-member-service   会员信息/注销状态
rrsjk-trade-service    订单状态/退款/日志
rrsjk-finance-service  云智慧钱包
rrsjk-light-service    光伏押金
rrs-dispenser-service  水卡充值
rrsjk-system-service   各支付渠道账号配置
shoppingmall-order     JK商城支付单据
```

**来源**: `rrsjk-pay-service` → `spring-config/service.xml`, `rrsjk-pay-web` → `spring-config/service.xml` (代码明确证明, 2026-06-02)

---

## 2. 支付场景枚举 (PayScene)

**来源**: `rrsjk-pay-service` → `rrsjk-pay-api/src/main/java/com/rrsjk/pay/payment/entity/PayScene.java` (代码明确证明, 2026-06-02)

| 场景ID | 场景名 | 说明 | 对应业务 |
|---|---|---|---|
| `01` | ORDER_PAY | 商城订单支付 | 主订单合并支付 |
| `02` | ORDER_ITEM_PAY | 商城子订单支付 | 单个商品订单支付 |
| `03` | LIGHT_DEPOSIT_PAY | 光伏押金支付 | 电站建设押金 |
| `04` | DISPENSER_PAY | 水站支付 | 水站充值/购水 |

**支付单号生成**: 不同环境(prod/dev)使用不同的 PaymentNoGenerator 和 PaySceneExtractor（通过 `@Profile` 切换），prod 使用 Redis 生成唯一单号。

---

## 3. 支付渠道枚举 (PayChannel)

**来源**: `rrsjk-pay-service` → `rrsjk-pay-api/src/main/java/com/rrsjk/pay/payment/entity/PayChannel.java` (代码明确证明, 2026-06-02)

| 渠道 | 说明 |
|---|---|
| `WECHAT` | 微信支付 |
| `ALIPAY` | 支付宝 |
| `CCB` | 建行龙支付 |
| `CCB_WALLET` | 建行钱包支付(乐农支付) |
| `BAIDU` | 百度支付 |
| `TRANSFER` | 转账汇款 |
| `OFFLINE` | 线下付款 |
| `COD` | 货到付款 |
| `LN_WALLET` | 乐农钱包支付（需短信验证码） |

---

## 4. 支付状态

**来源**: `rrsjk-pay-service` → `Payment.java` (代码明确证明, 2026-06-02)

| 常量 | 值 | 说明 |
|---|---|---|
| `Payment.PayStatus.WAIT_TO_PAY` | — | 待支付 |
| `Payment.PayStatus.PAID` | — | 已支付 |

---

## 5. 支付流程

### 5.1 创建支付单

**入口**: `PaymentController.createPayment()` → `PaymentService.createPayment()`

**流程**:
1. 前端传入场景号(sceneNo，逗号分隔的订单ID)、支付渠道、支付方式、支付场景
2. `PaymentService` 根据 PayScene 查询订单/子订单信息：
   - `01`(ORDER_PAY): 查询 Orders 列表，校验公司代码一致、memberId匹配（含代下单人 proxyMemberId）
   - `02`(ORDER_ITEM_PAY): 查询 OrderItem，关联 Orders 校验
3. 根据 PayScene 生成支付单号（`paymentNoGenerator.generate()`）
4. 创建 Payment 记录，状态 WAIT_TO_PAY，写入 payment 表
5. 返回 paymentId + payNo

**防重复支付**: 创建前查询 sceneNo 对应的已有 Payment，若存在已支付(PAID)记录则返回 "PAID" 错误。

**来源**: `rrsjk-pay-web` → `PaymentController.java`, `rrsjk-pay-service` → `PaymentServiceImpl.java`

### 5.2 发起支付

**入口**: `PayController.pay(payNo)` → `PayService.pay(payNo)` → 策略模式

**流程**:
1. 根据 payNo 查询 Payment 记录
2. 若已支付(PAID)，拒绝
3. 根据 payChannel 选择对应支付策略（`ThirdPay` 包装器 + 具体策略实现）
4. 调用第三方支付平台，返回 payBody（请求报文/支付链接/二维码等）

**策略映射**:
- WECHAT → `wechatPayStrategy`
- ALIPAY → `aliPayStrategy`
- CCB → `ccbPayStrategy`
- CCB_WALLET → `ccbWalletPayStrategy`
- TRANSFER → `transferPayStrategy`
- BAIDU → `baiduPayStrategy`
- OFFLINE → `offlinePayStrategy`
- LN_WALLET → `lnWalletPayStrategy`

**来源**: `rrsjk-pay-service` → `PayServiceImpl.java`

### 5.3 支付回调

**入口**: `XxxNotifyController.payNotify()` → `PayNotifyService.payNotify()` → `PaidModel.paid()`

**流程**:
1. 第三方支付平台回调 notify 接口（微信/支付宝/建行/百度）
2. `PayNotifyService` 根据 payChannel 路由到对应策略（wechatPayNotifyStrategy 等）
3. 解析回调参数，更新 `payment` 表：thirdTradeNo, paidAt, payStatus=PAID, appid, mchId, openId
4. `PaidModel.paid()` 根据 payScene 更新场景单：
   - `01`(ORDER_PAY) → `orderPaid.paid()` → 调用 OrderStatusService 更新订单状态
   - `02`(ORDER_ITEM_PAY) → `orderItemPaid.paid()` → 更新子订单状态
   - `03`(LIGHT_DEPOSIT_PAY) → `lightDepositPaid.paid()` → 更新押金状态
5. 若场景单更新失败，抛出 BusinessException("付款成功,更新交易状态失败") 并记录 orderLog
6. 回调成功/失败返回给第三方支付平台

**水站回调独立**: `PayDispenserNotifyService` → `DispenserPaidModel.paid()` → 更新 PaymentDocument(JK商城) + 调用 `WaterCardMultiPaidService.paid()` 更新水卡充值记录

**来源**: `rrsjk-pay-web` → `WechatNotifyController.java` 等, `rrsjk-pay-service` → `PaidModel.java`, `DispenserPaidModel.java`

### 5.4 退款流程

**入口**: `RefundService.refund()` → 策略模式

**流程**:
1. 校验 payNo 对应 Payment 存在
2. 校验 thirdTradeNo（支付流水）存在
3. 校验 refundAmount ≤ payAmount
4. 根据 payChannel 选择退款策略：
   - WECHAT → `wechatRefundStrategy`
   - ALIPAY → `alipayRefundStrategy`
   - CCB → `ccbRefundStrategy`
   - CCB_WALLET → `ccbWalletRefundStrategy`
   - BAIDU → `baiduRefundStrategy`
   - LN_WALLET → `lnWalletRefundStrategy`
5. 调用第三方退款接口，返回 ThirdRefundResponse

**百度退款审核异步回调**: `RefundNotifyService.queryRefundAudit()` → `BaiduQueryRefundAuditModel`:
- 百度第三方主动查询业务方退款审核结果
- 验证签名、校验 payNo + thirdTradeNo 一致
- 查询 OrderRepair（退款申请），返回审核状态 AGREE/REJECT/FAIL

**百度退款结果通知**: `RefundNotifyService.refundNotify()` → `BaiduRefundNotifyModel`:
- 退款成功(refundStatus=1) → OrderItem.RefundStatus.REFUND_SUCCESS
- 退款失败(refundStatus=2) → OrderItem.RefundStatus.REFUND_CANCEL

**来源**: `rrsjk-pay-service` → `RefundServiceImpl.java`, `BaiduQueryRefundAuditModel.java`, `BaiduRefundNotifyModel.java`

### 5.5 支付结果查询

**入口**: `PayService.queryThirdPayResult(payNo)` → 策略模式

调用第三方支付平台查询接口，验证支付单当前状态。用于前端轮询或支付页面跳转时确认支付结果。

---

## 6. 乐农钱包支付

**特殊流程**: LN_WALLET 渠道需要短信验证码验证。

1. `PaymentService.createPayment()` 中校验: 获取会员手机号 → 从 Redis 读取验证码 → 比对输入验证码
2. Redis key: `RedisKeyUtil.lnWalletSmsCodeKey(mobile)`
3. 验证码不匹配/失效则拒绝创建支付单

**来源**: `rrsjk-pay-service` → `PaymentServiceImpl.java` (代码明确证明)

---

## 7. 水控机支付

**独立 Controller**: `PayWaterControlController`

- `createPayment.do`: 创建水控机支付单，关联 `RechargeOrder`（水控机充值订单）
- 公司代码固定为 `CODE4300`
- 场景号修改为 rechargeOrder.orderNo（而非原始ID）
- 通过 `RechargeOrderService` 查询充值订单信息

**来源**: `rrsjk-pay-web` → `PayWaterControlController.java` (代码明确证明)

---

## 8. 数据库表

### 8.1 payment 表

**来源**: `rrsjk-pay-service` → `rrsjk-pay-impl/src/main/resources/mybatis/mapper/payment/Payment.xml` (代码明确证明)

| 字段 | 说明 |
|---|---|
| id | 自增主键 |
| pay_no | 支付单号 |
| pay_amount | 支付金额 |
| pay_status | 支付状态(WAIT_TO_PAY/PAID) |
| pay_channel | 支付渠道 |
| pay_type | 支付方式 |
| pay_scene | 支付场景 |
| third_trade_no | 第三方支付流水号 |
| paid_at | 付款时间 |
| scene_no | 关联场景单(逗号分隔) |
| subject | 商品标题 |
| ip | 客户端IP |
| open_id | 微信openId |
| form_id | 微信小程序formId |
| auth_code | 微信付款码 |
| svc_id | 建行钱包支付服务编号 |
| verify_code | 乐农钱包验证码 |
| mobile | 乐农钱包手机号 |
| member_id | 会员ID |
| client | 客户端(WAP/XSAPP/LNAPP) |
| client_id | 客户端ID |
| company_code | 公司代码 |
| appid | 第三方应用号 |
| mch_id | 第三方商户号 |
| transfer_type | 转账方式(ONLINE/CASH/CARD/ATM) |
| account_name | 转账方账户名 |
| bank_name | 转账方银行 |
| transfer_date | 汇款时间 |
| voucher | 转账凭证 |
| platform | 下单平台 |

---

## 9. REST API 端点 (rrsjk-pay-web)

### 9.1 支付单管理 `/payapi/pay`

| 方法 | 路径 | 说明 |
|---|---|---|
| POST | `/pay/createPayment.do` | 创建支付单（商城订单/子订单） |
| POST | `/pay/pay.do` | 拉起第三方支付 |
| GET | `/pay/getPayResult.do` | 查询支付结果 |
| GET | `/pay/getMicroPayTradeState.do` | 查询付款码支付结果 |
| GET | `/pay/getMicroPayTradeStateByScene.do` | 按场景号查询付款码结果 |

### 9.2 水站支付 `/payapi/payDispenser`

| 方法 | 路径 | 说明 |
|---|---|---|
| POST | `/payDispenser/pay.do` | 水站支付 |
| GET | `/payDispenser/getPayResult.do` | 查询水站支付结果 |

### 9.3 水控机支付 `/payapi/payWaterControl`

| 方法 | 路径 | 说明 |
|---|---|---|
| POST | `/payWaterControl/createPayment.do` | 创建水控机支付单 |
| POST | `/payWaterControl/pay.do` | 水控机支付 |
| GET | `/payWaterControl/getPayResult.do` | 查询水控机支付结果 |

### 9.4 支付回调 `/payapi/notify/*`

| 路径 | 渠道 | 说明 |
|---|---|---|
| `/notify/wechat/payNotify.do` | 微信 | 微信支付成功回调 |
| `/notify/alipay/payNotify.do` | 支付宝 | 支付宝支付成功回调 |
| `/notify/ccb/payNotify.do` | 建行 | 建行龙支付回调 |
| `/notify/baidu/payNotify.do` | 百度 | 百度支付成功回调 |
| `/notify/baidu/refundAuditNotify.do` | 百度 | 百度退款审核回调 |
| `/notify/baidu/refundNotify.do` | 百度 | 百度退款结果回调 |
| `/notify/alipay/payNotifyDispenser.do` | 支付宝 | 水站支付宝回调 |
| `/notify/ccb/payNotifyDispenser.do` | 建行 | 水站建行回调 |
| `/notify/wechat/payNotifyDispenser.do` | 微信 | 水站微信回调 |

### 9.5 微信授权回调

| 路径 | 说明 |
|---|---|
| `/notify/wechat/authorize.do` | 微信网页授权回调(从 m.rrsjk.com 转过来) |
| `/notify/wechat/accessToken.do` | 接收微信授权码获取 openId |
| `/notify/wechat/accessTokenDev.do` | 测试环境授权回调 |

---

## 10. 下单平台 (Platform)

| 值 | 说明 |
|---|---|
| `LN` | 乐农 |
| `LJCP` | 乐家诚品 |
| `DISPENSER` | 水站 |
| `WATER_CONTROL` | 水控机 |

---

## 11. 外部依赖服务

| 服务 | Dubbo 接口 | 用途 |
|---|---|---|
| rrsjk-system-service | `AccountAlipayService` | 支付宝账号配置 |
| rrsjk-system-service | `AccountWechatService` | 微信账号配置 |
| rrsjk-system-service | `AccountCcbService` | 建行账号配置 |
| rrsjk-system-service | `AccountBaiduService` | 百度账号配置 |
| rrsjk-system-service | `AccountTransferService` | 转账账号配置 |
| rrsjk-system-service | `AccountKjtService` | 快检通账号配置 |
| rrsjk-trade-service | `OrderService` | 订单查询 |
| rrsjk-trade-service | `OrderRepairService` | 退款申请查询 |
| rrsjk-trade-service | `OrderLogService` | 错误日志记录 |
| rrsjk-trade-service | `OrderStatusService` | 订单状态更新 |
| rrsjk-light-service | `LightDepositService` | 光伏押金支付 |
| rrsjk-finance-service | `CloudWisdomUserWalletChangeService` | 云智慧钱包变更 |
| rrs-dispenser-service | `WaterCardMultiPaidService` | 水卡多支付 |
| shoppingmall-order | `PaymentDocumentService` | JK商城支付单据 |
| rrsjk-member-service | `MemberService` | 会员信息/手机号 |
