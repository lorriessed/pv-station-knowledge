# 全量通读报告 2026-05-21

## 基本信息

- **轮次**: 第 8 轮（完成后进入第 9 轮）
- **通读仓库数**: 5
- **仓库列表**: nhpv_usercenter, nhpv_watermark_camera, order-service, pv-certificates, pv.osp-uni
- **从未通读仓库**: 0 个（全部 100 个仓库已覆盖）

## 仓库分析

### 1. nhpv_usercenter — Flutter 个人中心包装包

- **分支**: dev | **HEAD**: 84568fb | **业务文件数**: 3
- **类型**: Flutter package 包装层
- **PVS 业务价值**: 低

**分析**: 仅包含 `pubspec.yaml`、`analysis_options.yaml`、`android/local.properties` 三个配置文件。依赖 `nhpv_common` (git: mobile/greenergy/packages/nhpv_common.git) 获取实际业务代码。

**近期提交中的业务信号** (来自 commit message):
- `feat：登录新增管理员` (2026-01-08)
- `feat:新增结算单跳转` (2026-12-31)
- `feat：新增仓库管理员角色` (2025-12-30)
- `feat：我的页面新增账房管理` (2025-12-19)

**结论**: 这是薄包装层，实际业务逻辑在 `nhpv_common` 和 `nhpv_usercenter_business` 中。已在 `domains/mobile-app-architecture.md` 中记录。本次无需新增知识。

---

### 2. nhpv_watermark_camera — 水印相机 Flutter 插件

- **分支**: main | **HEAD**: 17213a7 | **业务文件数**: 15
- **类型**: Flutter 原生插件 (Android)
- **PVS 业务价值**: 低（基础设施）

**分析**: 15 个文件全是配置文件（AndroidManifest.xml, gradle, pubspec.yaml, styles.xml），无 Dart 业务代码。

**AndroidManifest 关键权限**:
- 相机: `CAMERA` + `camera.autofocus`
- 存储: `READ_MEDIA_IMAGES` (Android 13+), `READ_EXTERNAL_STORAGE` (maxSdkVersion=32)
- 定位: `ACCESS_FINE_LOCATION`, `ACCESS_COARSE_LOCATION`, `ACCESS_BACKGROUND_LOCATION`
- 高德定位服务: `APSService`
- 网络: `INTERNET`, `ACCESS_NETWORK_STATE`, `ACCESS_WIFI_STATE`

**Activity 注册**: `com.haier.watermarkcamera.sdk.activity.WatermarkCameraActivity` (竖屏)

**结论**: 纯原生相机插件包装层，无 PVS 业务逻辑。已在 `domains/mobile-app-architecture.md` 中记录为 Flutter 依赖包。

---

### 3. order-service — CBS 电商订单核心服务 ⭐

- **分支**: dev | **HEAD**: 9f39ee9 | **业务文件数**: 806
- **类型**: Java + Spring + Dubbo + MyBatis + JMS 传统电商订单服务
- **PVS 业务价值**: 中（传统电商订单履约，非光伏核心但支撑物流/发票/财务）

**已有覆盖**: `domains/order-and-trade.md` 已有 733 行详细文档（服务定位、Dubbo API、订单流程、状态机、数据库表、两服务对比等）

**本次通读新发现 — ESAP 服务集成**:

order-service 在 2025-11 新增了 **ESAP 服务**集成（SAP 接口新一代实现）:

| 变更 | 提交 | 说明 |
|---|---|---|
| 新增 SAP FI_COSMO_POST 接口 | 1f534f4 (majinhu, 2025-11-27) | 卡奥斯(COSMO)平台财务过账 |
| 更新 SAP 客户端模型属性转换 | a08e535 (majinhu, 2025-11-27) | 优化类型转换调用 |
| GVS 环境 SAP 接口配置 | dcbd277 (majinhu, 2025-11-27) | 支持 GVS 环境 |
| ESAP 测试类 | 25e3549 + 07dff43 (majinhu, 2025-11-27) | 单元测试 + 日期解析 |

**DAO 层补遗**（从本次通读的 Dao 接口列表中确认）:

order-service 的 `order-impl/src/main/java/com/haier/cbs/order/dao/` 包含 **100+ 个 DAO 接口**，覆盖以下业务域：

| 业务域 | DAO 数量 | 代表接口 |
|---|---|---|
| 订单核心 | 15+ | OrdersDao, OrderProductsDao, OrderQueuesDao, OrderWorkflowsDao |
| 退货/维修 | 10+ | OrderRepairsDao, ApplyReturnGoodDao, OrderRepairHPQueuesDao |
| 发票 | 12+ | InvoicesDao, InvoiceElectric2OutDao, InvoicePostDao, InvoiceQueueDao |
| 快递物流 | 8+ | ExpressDao, ExpressRecordDao, ExpressRegisterDao, ExpressAbortDao |
| HP 售后 | 10+ | HpDispatchDao, HpOrderDao, HpWorkDao, HpBccPayDao, HPQueuesDao |
| JDE 集成 | 5+ | JdeQueuesDao, OrderToJDERecordDao, JdeOffsetTaskDao |
| LES 集成 | 3+ | LesQueuesDao, EchannelDeliverQueueDao |
| 收入/预算 | 8+ | IncomeActualDao, IncomeForecastDao, BudgetDao, IncomeRecordDao |
| 公司/会员 | 6+ | CompanyDao, CompanyOrderDao, MembersDao, MemberCorpSaleDao |
| 区域/地址 | 4+ | RegionsDao, HpRegionsDao, RegionSmallMicroDao |
| VOM 仓储 | 8+ | AssetPurchaseOrderDao, EamAssetOrderDao, VOMProductData |

**结论**: order-service 是海尔 CBS 传统电商订单服务，与光伏电站业务**没有直接关联**，但支撑物流/发票/财务等后端履约能力。ESAP 集成是新增发现，已补充到 `domains/order-and-trade.md`。

---

### 4. pv-certificates — iOS 证书管理

- **分支**: master | **HEAD**: d5c4379 | **业务文件数**: 0
- **类型**: iOS 签名证书 + Provisioning Profiles
- **PVS 业务价值**: 无（纯基础设施）

**分析**: 仅包含 fastlane 自动更新的 iOS 证书文件（adhoc, development, appstore）。最近提交均为 `[fastlane] Updated ...` 类型的证书更新。无业务代码。

---

### 5. pv.osp-uni — 运维 UniApp 应用

- **分支**: dev | **HEAD**: 51a29a7 | **业务文件数**: 2
- **类型**: UniApp 跨平台移动应用
- **PVS 业务价值**: 中（运维工单/巡检/备件管理移动端）

**近期业务功能** (从 commit message 分析):

| 日期 | 功能 | 提交 |
|---|---|---|
| 2025-11-26 | 备品备件关单后1个月内可申请，超期申诉改为21-25号；巡检任务列表电站编码支持复制 | 51a29a7 (slx) |
| 2025-11-05 | 替换图标 + 集成 ARMS 监控 | 346b8ce (slx) |
| 2025-10-24 | 支持运维商在没有运维工程师的情况下处理工单 | 61da2ea (slx) |
| 2025-10-22 | 优化 Bugly 初始化逻辑 + 电话拨打 + 地址接口路径 + 工单页面逻辑 | 00edf73 (slx) |
| 2025-09-10 | 更新高德账号 | 2af2596 (slx) |
| 2025-09-03 | 超期申诉不做限制 + 备品备件申请 + 任务列表支持地址搜索 | 6f7ba69 (slx) |
| 2025-08-28 | 运维信息和巡检信息添加运维工程师 | 275d9b (slx) |

**技术集成**:
- `tx-bugly`: 腾讯 Bugly 崩溃上报 (AndroidManifest.xml)
- `uni_modules`: UniApp 原生模块扩展
- ARMS: 阿里云应用实时监控服务集成

**结论**: 这是光伏运维人员使用的移动端应用，核心功能包括运维工单处理、巡检任务管理、备品备件申请。已有 `nahui-pv.osp-mini`（OSP运维小程序）文档，此 UniApp 版本是另一套实现。建议后续深读完整源码补充到 `domains/mobile-app-architecture.md`。

---

## 知识库更新

| 文件 | 操作 | 内容 |
|---|---|---|
| `domains/order-and-trade.md` | 追加 | 1.10 ESAP 服务集成章节 |
| `daily/full-sweep-2026-05-21.md` | 新建 | 本报告 |
| `daily/2026-05-21.md` | 追加 | 全量通读摘要 |

## 统计

- 通读仓库: 5 个
- 有业务价值的仓库: 2 个 (order-service, pv.osp-uni)
- 纯基础设施仓库: 3 个 (nhpv_usercenter, nhpv_watermark_camera, pv-certificates)
- 知识库更新文件: 1 个 (order-and-trade.md)
- 新发现业务规则: 1 条 (ESAP SAP 集成)
