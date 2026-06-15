# PVS 全量通读报告 — 2026-06-15 (第 31 轮, 第 32 轮启动)

## 通读概览
- **通读轮次**: 第 31 轮（122/122 ✅ 100%覆盖, 本轮为第 32 轮首日）
- **本次通读仓库**: 5 个
- **知识库更新文件**: 0 个（零 delta, 全部跳过）
- **策略**: 重扫模式 — delta discovery

## 仓库分析

### 1. nhpv_usercenter — Flutter 用户中心组件包 (零变更 ✅)
- **类型**: Flutter package（`pubspec.yaml`, name: `nhpv_usercenter`）
- **业务定位**: 用户中心 UI 组件库，依赖 `nhpv_common` 核心包
- **最后业务提交**: 2026-01-08（登录新增管理员角色）+ 2025-12-31（新增结算单跳转）
- **最近提交**: 2026-03-04（仅 branch rename: chore_pub 分支合并）
- **delta**: 零业务变更。上次重扫（~2026-06-14）之后无新提交。
- **处理**: 跳过。已更新 `repo_last_sweep` 时间戳。

### 2. nhpv_watermark_camera — Flutter 水印相机插件 (仅 SDK 版本更新 ✅)
- **类型**: Flutter plugin（`pubspec.yaml`, name: `nhpv_camera`, version 2.0.6）
- **业务定位**: 光伏安装现场拍照水印相机（支持 Android/iOS）
- **核心能力**: 相机拍照 + 高德地图定位 + 存储权限适配（Android 10/11/12/13+）
- **Android 组件**: `WatermarkCameraActivity` + 高德定位 `APSService`
- **最近提交**: 2026-06-04~09（SDK 更换 + revert + 版本号更新）
- **delta**: 仅 chore 类 SDK 版本操作，无业务逻辑变更。
- **处理**: 跳过。已更新 `repo_last_sweep` 时间戳。

### 3. order-service — CBS 订单服务 (零变更 ✅)
- **类型**: Spring Boot + MyBatis + Dubbo 后端服务
- **包路径**: `com.haier.cbs.order`
- **模块**: `order-impl`（806 个业务文件）
- **业务定位**: CBS 电商平台的**订单核心服务** — 管理订单全生命周期
- **核心 DAO 覆盖**（已知业务）:
  - 订单管理: Orders, OrderProducts, GroupOrders
  - 发票管理: Invoices, InvoiceLine, InvoiceQueue, InvoicePost, InvoiceSAPLogs
  - 退货/退款: OrderRepairs, OrderRepairLogs, ApplyReturnGood
  - 快递物流: Express, ExpressRecord, ExpressRegister, ExpressAbort
  - SAP/JDE 集成: OrderToJDERecord, JdeQueues, InvoiceElectric2Out
  - 采购/预算: AssetPurchaseOrder, Budget, ForecastOrder, PurchaseApplySettle
  - 惠普派工: HpDispatch, HpOrder, HpBccPay
  - 收入管理: IncomeRecord, IncomeForecast, IncomeActual
  - 会员企业: MemberCorpHpAmount, MemberCorpSale, MemberCorpStock
- **最后提交**: 2025-11-27（SAP 集成优化: FI_COSMO_POST 接口 + GVS 环境支持）
- **delta**: 自 2025-11-27 以来零提交。上次重扫之后无新变更。
- **处理**: 跳过。已更新 `repo_last_sweep` 时间戳。

### 4. pv-certificates — iOS 证书管理 (零业务代码 ✅)
- **类型**: iOS 证书/fastlane 管理仓库
- **业务定位**: 管理 iOS 应用的开发/测试/发布证书（via fastlane match）
- **全部提交**: 3 次 fastlane 自动更新（development/adhoc/appstore 证书，2026-03-28）
- **delta**: 零业务代码。此仓库不包含任何应用源代码。
- **处理**: 跳过。已更新 `repo_last_sweep` 时间戳。

### 5. pv.osp-uni — 运维服务平台 uni-app 小程序 (零变更 ✅)
- **类型**: uni-app（Vite + Vue3 + TypeScript）
- **业务定位**: OSP（运维服务平台）移动端小程序
- **页面模块**: 巡检(inspect)、租金(rent)、服务(service)、方案(solution)、消息(message)、监控(monitor)、设置(setting)
- **API 模块**: address, service, message, exam, workorder, station, inspect, user, solution, dict
- **最后提交**: 2026-05-14（添加共享支付账单查询）+ 2026-04-28（运维工单超期申诉优化）
- **delta**: git log `--since=2026-05-25` 返回空。上次重扫（~2026-06-10）已覆盖这些提交。
- **处理**: 跳过。已更新 `repo_last_sweep` 时间戳。

## 知识库更新
**本次无更新。** 5 个仓库均为重扫，全部零 delta，按重扫策略直接跳过。

## 通读进度
- **已完成**: 122/122 仓库（100%）
- **本轮进度**: 5/122（第 32 轮开始, 当日完成）
- **下次通读**: 2026-06-16 22:00（下一批 5 个仓库）
