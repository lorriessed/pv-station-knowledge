# 移动端应用架构

最后更新: 2026-05-15

## 1. Cordova H5 桥接应用体系

### 1.1 定位

海尔 H5 桥接应用是一套跨平台方案，通过 **Cordova WebView 容器** 承载 H5 业务页面，同时提供**原生能力插件**供 H5 页面调用（设备信息、相机、存储、网络请求、文件选择、电话等）。

**来源**: `esp-mag-haier-android-main`, `esp-mag-haier-ios-main`, `esp-mag-haier-h5-portal` (代码明确证明, 2026-05-15)

### 1.2 三端架构

| 端 | 仓库 | 技术 | 包名 | 最近提交 |
|---|---|---|---|---|
| Android | esp-mag-haier-android-main | Java + Cordova + WebView | com.trade.center.main | 2026-05-12 朗新一期交付代码 |
| iOS | esp-mag-haier-ios-main | Objective-C + Cordova + WKWebView | com.trade.mainapp | 2026-05-12 朗新交付源码一期 |
| H5 Portal | esp-mag-haier-h5-portal | H5 (空壳) | - | 2026-05-12 朗新交付源码一期 |

### 1.3 应用入口流程

```
启动 → SplashActivity → 登录 → MainActivity(WebView加载H5)
```

**Android**:
- `SplashActivity` → 启动页
- `LoginAct` → 登录页面 (用户名/密码)
- `HomeAct` → 主页 (Cordova WebView)
- `PrivacyWebAct` → 隐私协议 WebView

### 1.4 后端 API 接口

| 接口 | 用途 | 来源 |
|---|---|---|
| `/eunomia-server/pf_auth/restfulapi/authen/login` | 登录认证 | ApiConfig.java |
| `/allinone-server/member/streamUpload/uploadSimpleFile` | 文件上传 | ApiConfig.java |
| `/allinone-server/member/desk/getUserInfo` | 获取用户信息 | ApiConfig.java |

**说明**: 这些接口指向 `eunomia-server` 和 `allinone-server`，属于海尔统一认证/会员体系，**不属于 PVS 光伏业务系统**。

### 1.5 Cordova 插件体系 (Android)

所有插件通过 `cordova.exec()` 从 H5 调用，Java 端继承 `CordovaPlugin` 实现：

| 插件名 | Java 类 | 功能 |
|---|---|---|
| HaierDevice | DevicePlugin | 设备信息获取 |
| HaierStorage | StoragePlugin | 本地存储 (SharedPreferences) |
| HaierNetwork | NetworkPlugin | 网络状态检测 |
| HaierHttp | HttpPlugin | HTTP 网络请求封装 |
| HaierCamera | CameraPlugin | 拍照/相册选择 |
| HaierFilePicker | FilePickerPlugin | 文件选择器 |
| HaierPhone | DockPhonePlugin | 拨打电话 |
| HaierNativeServer | NativeServerPlugin | 原生服务调用 |

### 1.6 Cordova 插件体系 (iOS)

与 Android 对称的 iOS 插件实现：

| 插件名 | iOS 类 | 功能 |
|---|---|---|
| HaierDevice | HaierDevicePlugin | 设备信息 |
| HaierStorage | HaierStoragePlugin | 本地存储 |
| HaierNetwork | HaierNetworkPlugin | 网络状态 |
| HaierHttp | HaierHttpPlugin | HTTP 请求 |
| HaierCamera | HaierCameraPlugin | 相机/相册 |
| HaierPhone | HaierPhonePlugin | 电话 |
| HaierFilePicker | HaierFilePickerPlugin | 文件选择 |
| HaierNativeServer | HaierNativeServerPlugin | 原生服务 |

### 1.7 网络层封装 (Android)

**来源**: `esp-mag-haier-android-main/libNetwork/src/main/java/.../HttpRequest.java` (代码明确证明)

- **技术栈**: OkHttp + RxJava3
- **支持请求方式**: GET, POST (JSON/Form), PUT, DELETE
- **调用方式**: 回调方式 (HttpCallback) + RxJava Observable
- **默认服务器**: `http://192.168.1.102:8080/` (开发环境)
- **基础响应**: `BaseDO` (returnCode, returnMsg)

### 1.8 安全配置

| 配置项 | 值 | 说明 |
|---|---|---|
| 明文传输 | 允许 (`cleartextTrafficPermitted=true`) | 开发/内网环境 |
| H5 白名单 | `*` (全开放) | 允许加载任意 H5 页面 |
| FileProvider | `${applicationId}.fileprovider` | 相机拍照文件共享 |
| 存储权限 | READ_EXTERNAL_STORAGE (maxSdkVersion=32) | Android 13 以下 |
| 媒体权限 | READ_MEDIA_IMAGES/VIDEO/AUDIO | Android 13+ |

### 1.9 H5 入口配置

```xml
<!-- config.xml -->
<content src="index.html" />
<!-- 开发环境 H5 地址 -->
<allow-navigation href="http://10.105.165.237:8081/*" />
<allow-navigation href="http://10.105.165.237:8080/*" />
<allow-navigation href="http://192.168.31.184:8080/*" />
<allow-navigation href="*" />
```

## 2. Flutter 移动应用体系

### 2.1 纳光宝 APP (nahuipv_business_flutter)

**来源**: `nahuipv_business_flutter` (代码明确证明, 2026-05-15)

- **应用名**: 纳光宝 (光伏终端用户 APP)
- **版本**: 1.1.0+202****0401
- **技术栈**: Flutter + Riverpod (状态管理) + Dio (网络) + Retrofit (API) + Fluro (路由)
- **SDK 版本**: Dart >=3.0.1 <4.0.0

#### 2.1.1 核心依赖

| 依赖 | 版本 | 用途 |
|---|---|---|
| flutter_riverpod | ^2.3.6 | 状态管理 |
| dio | ^5.2.0 | HTTP 客户端 |
| retrofit | ^4.0.1 | REST API 声明式调用 |
| fluro | ^2.0.5 | 路由管理 |
| flutter_inappwebview | ^6.0.0 | WebView 容器 |
| image_picker | ^0.8.7+5 | 图片选择 |
| cached_network_image | ^3.2.3 | 图片缓存 |
| shared_preferences | ^2.1.1 | 本地存储 |

#### 2.1.2 模块化依赖 (Git 子仓库)

| 模块 | Git URL | 版本 |
|---|---|---|
| nhpv_common_business | mobile/business/packages/nhpv_common_business.git | >=0.0.3 |
| nhpv_usercenter_business | mobile/business/packages/nhpv_usercenter_business.git | >=0.0.4 |
| log_report_plugin | mobile/common/log_report_plugin.git | >=0.0.2 |

#### 2.1.3 历史业务变更

| 日期 | 变更内容 | 提交信息 |
|---|---|---|
| 2025-03-05 | Android 14 版本更新兼容 | fix：版本更新兼容android14 |
| 2025-03-04 | 图片防盗链设置 | feat: 图片防盗链设置/设置2 |
| 2025-02-24 | VPP 电站列表接口修改 | chore：修改vpp电站列表接口 |
| 2025-01-20 | 个人中心迁移至 usercenter 库 | refactor: 个人中心相关功能迁移 |

### 2.2 通用业务库 (nhpv_common_business)

**来源**: `nhpv_common_business` (代码明确证明, 2026-05-15)

- **定位**: Flutter 通用业务组件库，被纳光宝等多端复用
- **版本**: 0.0.3
- **功能**: 通用 UI 组件、网络请求封装、图片处理、版本更新

#### 2.2.1 核心依赖

| 依赖 | 版本 | 用途 |
|---|---|---|
| r_upgrade (自研) | git ref:main | 版本更新/APK 下载 |
| flutter_inappwebview | ^6.0.0 | WebView 容器 |
| retrofit | ^4.0.1 | REST API |
| dio | ^5.2.0 | HTTP 客户端 |
| permission_handler | ^9.2.0 | 权限管理 |
| image_gallery_saver | ^2.0.3 | 图片保存到相册 |

#### 2.2.2 历史业务变更

| 日期 | 变更内容 | 提交信息 |
|---|---|---|
| 2025-03-05 | Android 14 版本更新兼容 | fix：版本更新兼容android14 |
| 2025-02-24 | 修改测试环境域名 | chore: 修改测试环境域名 |
| 2025-01-24 | 新增 APK 测试下载地址 | feat: 版本更新功能新增apk测试下载地址 |
| 2025-01-21 | 个人中心迁移至 usercenter | refactor: 个人中心相关功能迁移至usercenter库 |
| 2025-01-16 | 更换 APP 协议地址 | refactor：更换app相关协议地址 |
| 2025-01-13 | 新增 VPP 账号类型 | feat：新增vpp账号类型 |
| 2024-12-20 | WebView 改为 inappwebview | feat: webview容器改为inappwebview |

### 2.3 登录业务模块 (nhpv_login_business)

**来源**: `nhpv_login_business` (代码明确证明, 2026-05-16)

- **定位**: Flutter 登录功能模块
- **版本**: 0.0.5
- **依赖**: `nhpv_common_business` (git ref: dev)
- **最近提交**: 2025-02-08 (Merge branch 'dev')
- **业务价值**: 低，仅为 Flutter package 包装层，实际登录逻辑在 nhpv_common_business 中
- ⚠️ 仓库中无业务 Dart 源码，仅有 pubspec.yaml 和配置文件

### 2.4 个人中心业务模块 (nhpv_usercenter_business)

**来源**: `nhpv_usercenter_business` (代码明确证明, 2026-05-16)

- **定位**: Flutter 个人中心功能模块
- **版本**: 0.0.4
- **依赖**: `nhpv_common_business` (git ref: main)
- **最近提交**: 2025-03-04 (feat：账号类型默认vpp账号)
- **关键业务变更**:
  - 2025-02-17: 账号类型默认改为 VPP 账号
  - 2025-01-24: 版本更新功能新增 APK 测试下载地址
  - 2025-01-21: 个人中心相关功能从 common 库分离
  - 2025-01-17: 修改注销须知内 App 名字
  - 2025-01-16: 更换 App 相关协议地址
  - 2025-01-15: 版本更新接口新增 appType 字段
- ⚠️ 仓库中无业务 Dart 源码，仅有 pubspec.yaml 和配置文件，实际代码在 nhpv_common_business 中

### 2.5 签名配置

**来源**: `nahuipv_business_flutter/android/key.properties` (代码明确证明)

```properties
storePassword=123456
keyPassword=123456
keyAlias=business
storeFile=key.jks
```

⚠️ **安全警告**: 签名密码明文存储在仓库中，存在安全风险。

### 2.6 海尔绿能 Flutter APP (nahuipv_greenergy_flutter) 2026-05-20 更新

**来源**: `nahuipv_greenergy_flutter` (代码明确证明, 2026-05-20 第7轮全量通读)

- **应用名**: 海尔绿能
- **版本**: 2.2.2+202****1901 (上次记录为 2.2.1+202****1401)
- **技术栈**: Flutter + Riverpod (状态管理) + Dio (网络) + Retrofit (API) + Fluro (路由)
- **SDK 版本**: Dart >=3.3.4 <4.0.0

#### 2.6.1 新增发现: DJI 无人机 SDK 集成

**⚠️ 新发现 (2026-05-20 通读)**: `nahuipv_greenergy_flutter` 集成了 **DJI Mobile SDK**，用于无人机飞控。这在之前通读中未被发现。

- **USB 配件支持**: `android/app/src/main/res/xml/accessory_filter.xml` 定义了 4 种 DJI 设备:
  - T600 (农业无人机)
  - AG410 (农业无人机)
  - com.dji.logiclink (DJI 逻辑链路)
  - WM160 (遥控器)
- **AndroidManifest.xml**: 
  - `android.hardware.usb.host` 和 `android.hardware.usb.accessory` 权限
  - `com.dji.sdk.API_KEY` meta-data 配置
  - MainActivity 监听 `android.hardware.usb.action.USB_ACCESSORY_ATTACHED` USB 事件
- **Splash Activity**: `activity_aplsh.xml` 包含"点击调用飞控"和"切换App"按钮
- **UXSDK 组件**: styles.xml 中大量 DJI UX SDK 样式 (UXSDKBatteryWidget, UXSDKFlightModeListItem, UXSDKObstacleAvoidanceListItem 等)
- **签名配置**: `android/key.properties` 中 `dji.api.key=d38d5408aa93389e40d53b11`

**⚠️ 安全警告**: DJI API Key 明文存储在 `key.properties` 中。

#### 2.6.2 近期活跃开发 (2026-05-14 ~ 2026-05-19)

| 日期 | 提交信息 | 作者 |
|---|---|---|
| 2026-05-19 | chore: v2.2.2+202****1901 | dongxueqiang |
| 2026-05-18 | chore: 更换水印相机Android SDK(二维码白边,logo) | dongxueqiang |
| 2026-05-14 | Merge #50 into master from chore-map-key | 褚福贺 |
| 2026-05-14 | Merge #51 into master from feat_gf | 褚福贺 |
| 2026-05-14 | Merge #49 into master from opt-station-list-item | 褚福贺 |

- **地图 Key 更新**: `chore-map-key` 分支
- **水印相机 SDK 更换**: 修复二维码白边和 logo 问题
- **电站列表项优化**: `opt-station-list-item` 分支
- **广发业务**: `feat_gf` 分支 (与 domains/guangfa-business.md 相关)

#### 2.6.3 Git 依赖模块

| 模块 | Git URL | 用途 |
|---|---|---|
| nhpv_common | mobile/greenergy/packages/nhpv_common.git | 公共组件库 (网络/状态/工具) |
| nhpv_usercenter | mobile/greenergy/packages/nhpv_usercenter.git | 个人中心模块 |
| log_report_plugin | mobile/common/log_report_plugin.git | 日志上报 |
| nhpv_camera | mobile/greenergy/plugins/nhpv_watermark_camera.git | 水印相机插件 |

#### 2.6.4 第三方服务

| 服务 | 配置 | 说明 |
|---|---|---|
| 高德地图 | AMap API Key (key.properties) | 定位服务 |
| DJI SDK | DJI API Key (key.properties) | 无人机飞控 |
| Mapbox | MAPBOX_DOWNLOADS_TOKEN (gradle.properties, 脱敏) | 地图服务 |
| 微信分享 | WXEntryActivity | 微信SDK集成 |

### 2.7 通用组件库 (nhpv_common)

**来源**: `nhpv_common` (代码明确证明, 2026-05-20 第7轮全量通读)

- **定位**: Flutter 公共组件库，被 nahuipv_greenergy_flutter 等 APP 通过 Git 依赖引入
- **版本**: 1.1.0+202****0701
- **业务价值**: **中** — 提供网络封装、状态管理、路由、图片处理等基础设施，但本身不包含光伏业务逻辑
- **仓库结构**: 仅有 `pubspec.yaml` 和 `analysis_options.yaml` 配置文件，实际 Dart 代码在 Git 依赖中或通过其他仓库引用
- **⚠️ 注意**: 通读仅发现配置文件，无 Dart 源码文件。实际代码需从其 Git 仓库 `mobile/greenergy/packages/nhpv_common.git` 获取

### 2.8 VPP 湖南智绿 RN 应用 (nahuipv-vpp-hnzl-rn)

**来源**: `nahuipv-vpp-hnzl-rn` (代码明确证明, 2026-05-20 第7轮全量通读)

- **定位**: VPP 湖南智绿 React Native 应用
- **业务文件数**: 0
- **唯一提交**: `feat: 代码交付仓库初始化20250801` (chufh, 2025-08-01)
- **状态**: 空壳仓库，自初始化以来无实际业务代码
- **业务价值**: **极低** — 模板/骨架项目，尚未开始业务开发

### 2.4 纳光宝与 VPP 后端的关系

根据代码分析，纳光宝 APP 通过以下方式与 VPP 后端交互：

| 前端功能 | 后端服务 | 数据来源 |
|---|---|---|
| 电站列表 | vpp-api-elecbusiness | 大屏/电站数据接口 |
| 发电/储能/负载数据 | vpp-api-elecbusiness | 时序数据 |
| 电站收入 | vpp-api-elecbusiness | 收入统计 |
| VPP 账号管理 | vpp-api-system | 用户/租户管理 |
| 绿证相关 | vpp-api-gect | 绿证交易 |
| 绿电收益 | vpp-api-gpower | 绿电收益管理 |

**来源推断**: 基于 API 路由对应关系推断

## 2.5 微信小程序矩阵

### 2.5.1 施工小程序 (nahui-pv.construction-mini)

**来源**: `nahui-pv.construction-mini` (代码明确证明, 2026-05-18 全量通读)

- **定位**: 施工/安装流程微信小程序
- **技术栈**: 微信小程序 + Vant WeApp 组件库
- **核心功能**:
  - 相机拍照: 逆变器铭牌图拍摄 + 验真逻辑（隐藏验真逻辑、水印验真优化）
  - 水印管理: 唯一码增加渠道标识、水印像素优化、方位节流效果
  - 图片处理: 原图保存信息、相册预览模式、二维码大小调整
- **关键 API**: `miniprogram/wxapi/main.js`, `miniprogram/wxapi/request.js`, `miniprogram/utils/_data.js`
- **业务价值**: 中 — 施工环节影像采集，逆变器铭牌验真涉及数据真实性校验

### 2.5.2 绿能小程序 (nahui-pv.greenenergy-mini)

**来源**: `nahui-pv.greenenergy-mini` (代码明确证明, 2026-05-18 全量通读)

- **定位**: 绿能业务微信小程序
- **技术栈**: 微信小程序 + wxParse 富文本解析
- **核心功能**:
  - **银行卡变更管理**: 云管家光伏管理新增银行卡变更管理按钮、申请流程、变更记录列表（packageB/pages/bankChange/）
  - ARMS 监控: 只允许生产环境执行 ARMS 监听
  - 充值/水卡: packageC 包含充值、充值记录、水卡管理等功能
- **关键页面路径**:
  - `pages/bankCard/` — 银行卡管理
  - `packageB/pages/bankChange/bankChangeList/` — 银行卡变更列表
  - `packageB/pages/bankChange/bankChangeInfo/` — 银行卡变更详情
  - `packageB/pages/changeRecord/` — 变更记录
  - `packageD/pages/wineSale/bankCard/` — 酒类销售银行卡
- **业务价值**: 中 — 银行卡变更直接影响结算流程

### 2.5.3 EPCB 小程序 (nahui-pv.epcb-mini)

**来源**: `nahui-pv.epcb-mini` (代码明确证明, 2026-05-18 全量通读)

- **定位**: EPCB (工程总承包) 微信小程序
- **技术栈**: 微信小程序 + Vant WeApp + ARMS 监控
- **核心功能**:
  - ARMS 监控接入: 系统评价入口、ARMS 环境配置（只允许生产环境）
  - 登录校验: 去除登录校验（2026-01-28）
- **业务价值**: 低 — 主要是监控和基础设施配置

## 3. H5 Web 应用矩阵

### 3.1 HDS 管理平台 (nahui-pv.hds-h5)

**来源**: `nahui-pv.hds-h5` (代码明确证明, 2026-05-18 全量通读)

- **定位**: 综合运维管理 H5 平台（含 OSP、EPC、光伏能源、运维、租金等模块）
- **技术栈**: Vue 3 + Vue Router + Element Plus（推测）
- **路由模块**:

| 路由前缀 | 模块名称 | 核心功能 |
|---|---|---|
| `/osp` | OSP 运维服务商 | 运维商管理 |
| `/epc` | EPC 工程管理 | 工程承包管理 |
| `/pvEnergy` | 光伏能源管理 | 多资方电站管理（CMB/ACQ/KVA/CHD/ZY/GX/CQ_GDT 等）|
| `/rent` | 支付租金管理 | 银联付款合计、结算明细、租金扣除 |
| `/maintainance` | 运维管理 | 方案库、故障库、电站运维、工单管理、巡检管理 |
| `/sparePartsManage` | 备件管理 | 备件库存、调拨 |
| `/sparePartMonitor` | 备件监控 | 备件使用监控 |
| `/sparePartsSettlement` | 备件结算 | 备件费用结算 |
| `/dataBoard` | 数据大屏 | 数据可视化 |
| `/baseData` | 基础数据 | 组织架构、属性配置、仓储管理 |
| `/socialization` | 社会化 | 社会化功能 |
| `/bidding` | 招投标 | 招投标管理 |
| `/automaticDrawing` | 自动出图 | 自动图纸生成 |
| `/workManage` | 工作管理 | 日常工作管理 |
| `/processManage` | 流程管理 | 审批流程管理 |

- **运维管理子模块** (`/maintainance`, 765 行路由配置):
  - 方案库 (`solution/`) — 解决方案列表
  - 故障库 (`faultCategory/`) — 故障分类及解决措施
  - 电站运维 (`station/`) — 零碳家庭/零碳E家庭/光储业务等多类型电站运维
  - 故障工单 (`faultWorkOrder/`) — 招银工单/中信工单/协鑫工单/工单审核/工单效率
  - 巡检管理 (`inspect/`) — 巡检计划、执行、记录
  - 运维配置 (`config/`) — 巡检/工单/报表/字典配置

- **光伏能源多资方路由** (`/pvEnergy`):
  - `/cmbEnergy` — 招银能源（电站列表、逆变器列表、收入明细、结算明细、保险）
  - `/pvEnergy` — 户用光伏（合同列表、电站列表、审核列表、逆变器列表）
  - `/acqEnergy` — 收购能源（电站列表、逆变器列表）
  - `/kvaEnergy` — KVA（逆变器列表及详情）
  - `/chdEnergy` — 华电能源（电站列表、逆变器列表）
  - `/zyEnergy` — 中银能源
  - `/gxEnergy` — 协鑫能源
  - `/cqGdtEnergy` — 重庆国电投能源

- **近期业务变更** (2026-04~05):
  - 国电投(GDT)逆变器列表新增（与后端 rrsjk-hds-web `InverterController.java` CQ_GDT 查询链路对应）
  - 电站租金查询详情: 兼容中文状态和类型、添加账单生成时间
  - 新增电站数据变更过程信息查询接口
  - 工商业项目运维商管理弹框更新
  - 超期申诉功能优化 + 运维政策兑现功能优化
  - 电费管理: 新增报表、估算电费修复、应收电量新增
  - 交易账号: 中信一般户去除、优化建行基本户
- **业务价值**: **高** — HDS 是运维商/分中心的核心管理平台

### 3.2 商户微前端 OSP (nahui-pv.merchant-micro.osp)

**来源**: `nahui-pv.merchant-micro.osp` (代码明确证明, 2026-05-18 全量通读)

- **定位**: 商户端微前端 OSP 应用（基于 Qiankun 微前端架构）
- **技术栈**: Vue 2 + Qiankun 微前端 + Vue Router
- **微前端配置**: `base: /mch/{subName}` (微前端模式) 或 `/sub/{subName}` (独立模式)
- **路由模块**:

| 模块文件 | 模块名称 | 核心功能 |
|---|---|---|
| `osp.js` | OSP 运维管理 | 在线签约、备件保证金、服务商清欠、人员管理、上岗资格 |
| `commercial.js` | 工商业管理 | 工商业项目相关 |
| `ospSpare.js` | OSP 备件管理 | 订单执行、借货订单、服务调拨、服务商订单、呆滞备件、库存管理、备件结算 |
| `ospSupplier.js` | OSP 供应商管理 | 供应商相关 |

- **OSP 运维管理核心页面**:
  - `ospReg` — 在线签约
  - `depositList` — 备件保证金列表
  - `bailPay` — 支付保证金
  - `advanceClear` — 服务商清欠
  - `personnelList` — 人员管理
  - `jobQualification` — 上岗资格管理
  - 权限码: `light_osp`, `light_osp_warranty`

- **OSP 备件管理核心页面**:
  - 订单管理: 订单执行视图、借货订单、服务调拨、服务商订单、呆滞备件
  - 库存管理: 当前库存视图、库存调整、库存设置
  - 备件结算: 备件费用结算
  - 地址管理

- **近期业务变更** (2026-04~05):
  - 电站租金查询详情: 添加账单生成时间、更新状态反显
  - 运维工单超期申诉: 新增判断逻辑 + 新增提示 + 恢复超期申诉条件 + 去除审核人脱敏
  - 业主银行卡变更: 新增模块、状态变更、上传新银行卡号照片新增 OCR 识别、撤销展示条件
  - 超期申诉功能优化 + 运维政策兑现功能优化
  - 特殊费用列表: 添加导出、设置审核和脱敏
  - 光e宝: 取消下载模板、新增截图示例模版
- **业务价值**: **高** — 商户端核心运维/备件/结算管理平台

### 3.3 零碳适家商户微前端 (nahui-pv.merchant-micro.zch)

**来源**: `nahui-pv.merchant-micro.zch` (代码明确证明, 2026-05-19 全量通读)

- **定位**: 零碳适家(ZCH)商户端微前端应用
- **技术栈**: Vue.js (微前端架构)
- **最近业务活动** (2026-04~05):
  - **零碳适家建站**: 支持不同组件混用 (yuanruilin, 2026-04-28)
  - **结算申请**: 调整结算申请页面选择明细接口请求参数 (yuanruilin, 2026-04-16)
  - **关联发票页面**: 注释部分提示 (yuanruilin, 2026-04-27)
  - **异常处理**: 优化异常处理逻辑并补充登录过期提示 (yuanruilin, 2026-04-21)
  - **CSS构建**: 修改CSS提取配置 (开发/生产环境统一) (yuanruilin, 2026-04-21)
  - **全局样式**: 调整全局样式导入方式 (yuanruilin, 2026-04-21)
- **⚠️ 注意**: 脚本检测到 0 个业务文件（可能是文件扩展名过滤导致），但 commit message 表明有实际业务变更
- **业务价值**: **中** — 零碳适家是独立于PVS核心光伏业务的子品牌，但结算申请等逻辑可能共享后端服务

### 3.4 移动端 H5 门户 (nahui-pv.mobile-h5)

**来源**: `nahui-pv.mobile-h5` (代码明确证明, 2026-05-19 全量通读)

- **定位**: 光伏移动端 H5 页面集合
- **近期业务活动** (2026-05):
  - **数据字典优化**: 获取数据字典优化调整 (yanghui, 2026-05-15)
  - **二维码识别**: 二维码识别优化 (yanghui, 2026-05-14)
  - 持续活跃: 2026-05-19 仍有合并提交
- **业务价值**: **高** — 移动端核心H5入口，日常活跃开发

### 3.5 OSP 运维服务小程序 (nahui-pv.osp-mini)

**来源**: `nahui-pv.osp-mini` (代码明确证明, 2026-05-19 全量通读)

- **定位**: 运维服务(OSP)微信小程序
- **技术栈**: 微信小程序
- **最近业务活动**:
  - **备件申请**: 增加备件规格展示 (徐勇, 2024-12-31)
  - **备件查询**: 取消备件描述字段，改为备件名称 (徐勇, 2024-12-31)
  - **逆变器详情**: 直流/交流展示更改 (李培龙, 2024-09-10)
  - **故障字典**: 新增过程记录和故障字典优化 (李培龙, 2024-08-27)
- **最后业务提交**: 2025-01-08 (合并)
- **业务价值**: **中** — 运维服务商移动端入口，涉及备件申请和逆变器数据展示，但近半年无新业务提交

### 3.6 绿能管理 Flutter 骨架 (nahuipv-greenergy-management-flutter)

**来源**: `nahuipv-greenergy-management-flutter` (代码明确证明, 2026-05-19 全量通读)

- **定位**: 分中心 APP (app_sub_center)
- **技术栈**: Flutter
- **⚠️ 骨架项目**: 仅包含 Android 项目骨架配置（AndroidManifest.xml、styles.xml、gradle.properties、pubspec.yaml），**无实际 Dart 业务代码**
- **唯一提交**: `init project` (chufh, 2026-04-07)
- **pubspec.yaml**: 应用名 `app_sub_center`，描述"分中心app"，仅依赖 flutter SDK 和 cupertino_icons
- **业务价值**: **低** — 初始化的空壳项目，实际业务逻辑可能在后续迭代中通过依赖包引入或直接在 lib/ 目录下开发
- **⚠️ 注意**: 与已通读的 `nahuipv_greenergy_flutter`（绿能管理Flutter）是**不同的仓库**，需后续关注此骨架项目是否开始填充业务代码

## 3. 湖南智充 APP (nahuipv-hnzc-*)

### 3.1 定位

**⚠️ 非光伏业务**: 这是"慧能智充" **电动汽车充电桩** APP，与 PVS 光伏业务**完全无关**。虽然仓库前缀为 `nahuipv-`（组织命名空间），但业务域属于充电桩运营，不是光伏电站。

**来源**: `nahuipv-hnzc-app-android` (代码明确证明, 2026-05-20 全量通读)

### 3.2 技术架构

| 端 | 仓库 | 技术 | 最后提交 | 业务文件数 |
|---|---|---|---|---|
| Android | nahuipv-hnzc-app-android | Java 原生 Android | 2025-10-13 (chufh) | 146 |
| iOS | nahuipv-hnzc-app-ios | 原生 iOS (仅有 AMap SDK 配置) | 2025-10-14 (chufh) | 3 |

### 3.3 核心功能 (Android)

- **充电站查询**: 地图搜索附近充电站 (`/api/omp/mt/powerStation/queryStationListForLXGH`)
- **电站详情**: 站点信息、充电桩状态、价格 (`/api/omp/mt/powerStation/queryStationInfoForShare`)
- **路线规划**: 高德地图驾车导航到充电站 (DriveRouteActivity, AMapNavActivity)
- **扫码充电**: ZXing 扫码识别充电桩 SN (`/api/omp/mt/pile/getGunNoByGunName`)
- **用户登录**: 手机号一键登录 (`/mt/security/login`)
- **支付**: 微信/支付宝 H5 支付 (WXPayEntryActivity, AliH5PayActivity)
- **广告/营销**: 开屏广告 (`/mt/route/marketing/app/advertisement/queryAdvertisementList`)
- **版本更新**: APP 升级检测 (`/mt/route/support/app/sys/upgrade/queryUpgradeInfo`)

### 3.4 后端 API (非 PVS)

| API 路径 | 用途 | 所属系统 |
|---|---|---|
| `/mt/security/login` | 用户登录 | 慧能智充后端 |
| `/mt/route/user/app/charging/user/chargeUserInfo` | 用户信息 | 慧能智充后端 |
| `/api/omp/mt/powerStation/queryStationInfoForShare` | 电站详情 | 慧能智充后端 |
| `/api/omp/mt/powerStation/queryStationListForLXGH` | 电站列表 | 慧能智充后端 |
| `/api/omp/mt/pile/getGunNoByGunName` | SN 校验 | 慧能智充后端 |
| `/mt/route/marketing/app/advertisement/queryAdvertisementList` | 广告列表 | 慧能智充后端 |
| `/mt/route/support/app/sys/upgrade/queryUpgradeInfo` | 版本升级 | 慧能智充后端 |

**⚠️ 这些 API 指向慧能智充 (ykccn.com) 后端，不是 rrsjk.com 光伏后端。**

### 3.5 第三方服务集成

| 服务 | 用途 | 配置位置 |
|---|---|---|
| 高德地图 | 定位、导航、充电站搜索 | AndroidManifest.xml (GD_MAP_APP_ID) |
| 百度定位 | 辅助定位 | AndroidManifest.xml |
| 微信支付 | 充电费用支付 | WXPayEntryActivity |
| 支付宝 H5 | 充电费用支付 | AliH5PayActivity |
| 七鱼客服 | 在线客服 | AndroidManifest.xml (com.qiyusf.sentry) |
| ZXing | 二维码扫描 | tools/scan/zxing/ |
| 百度统计 | 数据统计 | AndroidManifest.xml 注释中提及 |

### 3.6 应用入口流程

```
启动 → SplashActivity (广告加载) → PrivacyActivity (隐私协议)
  → SNInputActivity (可选) → LoadingActivity (H5下载) → MainActivity(WebView)
```

### 3.7 结论

**nahuipv-hnzc-app-android 和 nahuipv-hnzc-app-ios 属于充电桩业务线，不是光伏业务。** 通读了解其架构即可，不需要提取光伏业务规则或写入光伏业务 domain 文件。标记为低 PVS 业务价值。

## 4. 移动端应用与 PVS/VPP 业务的关系

| 应用 | 面向用户 | 关联后端 | 业务域 |
|---|---|---|---|
| Cordova H5 桥接 App | 海尔内部 (运维/业务) | eunomia-server, allinone-server | 通用管理 |
| 纳光宝 APP | 光伏终端用户 | VPP 后端服务 (elecbusiness, gect, gpower) | 电站运营/绿证/绿电 |
| 施工小程序 | 施工/安装人员 | 待确认 (可能对接 rrsjk-light-service) | 施工/完工确认 |
| 绿能小程序 | 绿能用户/云管家 | 待确认 | 绿能运营/银行卡变更 |
| EPCB 小程序 | EPC 工程人员 | 待确认 | 工程承包 |
| HDS 管理平台 | 运维商/分中心 | rrsjk-hds-web, rrsjk-light-operation-service | 运维/工单/租金/逆变器 |
| 商户微前端 OSP | 商户/运维商 | rrsjk-merchant-service, rrsjk-light-operation-service | 运维/备件/结算 |
| 海尔绿能 Flutter | 绿能管理用户 | VPP 后端 + rrsjk-light-service | 绿能运营/无人机巡检 |
| 湖南智充 Android | ⚠️ 非光伏业务 | ykccn.com 后端 | 充电桩运营 |
| 湖南智充 iOS | ⚠️ 非光伏业务 | ykccn.com 后端 | 充电桩运营 |
| 湖南 RN (vpp-hnzl) | ⚠️ 空壳 | 待开发 | VPP 移动端 |
| 分中心APP (greenergy-management) | ⚠️ 骨架项目 | 待确认 | 待开发 |
| 零碳适家商户端 (nahui-pv.merchant-micro.zch) | 零碳适家商户 | 待确认 | 零碳适家/结算 |
| OSP运维小程序 (nahui-pv.osp-mini) | 运维服务人员 | 待确认 | 运维/备件 |
| 移动端H5 (nahui-pv.mobile-h5) | 移动用户 | 待确认 | 综合 |

## 5. 知识库更新记录

| 日期 | 更新内容 | 来源 |
|---|---|---|
| 2026-05-15 | 创建: Cordova H5 桥接架构/Flutter 纳光宝 APP/插件体系 | 全量通读5个移动端仓库 |
| 2026-05-19 | 新增: merchant-micro.zch 零碳适家微前端/osp-mini 小程序/greenergy-management-flutter 骨架 | 全量通读第6轮 |
| 2026-05-20 | 新增: 湖南智充APP (非光伏业务)/nahuipv_greenergy_flutter DJI无人机SDK集成/nhpv_common | 全量通读第7轮 |
