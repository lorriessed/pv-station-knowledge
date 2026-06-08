# 全量代码通读报告 — 第 24 轮 (2026-06-08)

## 概况

| 指标 | 数值 |
|---|---|
| 仓库总数 | 122 |
| 本轮通读 | 5 个 |
| 累计已通读 | 122/122 ✅ |
| 从未通读 | 0 个 |

## 本轮通读仓库清单

| # | 仓库 | 分支 | HEAD | 业务文件数 | 业务价值 |
|---|---|---|---|---|---|
| 1 | esp-mag-haier-android-main | master | 4e49cfb | 34 | 低 (Cordova H5 桥接) |
| 2 | esp-mag-haier-h5-portal | master | b2c5149 | 0 | 低 (Vue 2 空壳) |
| 3 | esp-mag-haier-ios-main | master | 19bcf58 | 2 | 低 (Cordova H5 桥接) |
| 4 | nahuipv_business_flutter | main | c238ac8 | 13 | 中 (Flutter 纳光宝) |
| 5 | nhpv_common_business | main | 1811e11 | 3 | 低 (Flutter 通用组件库) |

## 逐仓库分析

### 1. esp-mag-haier-android-main — 海尔售电决策辅助系统 Android

**类型**: Android + Cordova H5 桥接应用
**最近提交**: `feat: 初始化海尔售电决策辅助系统 Android 项目` (chufh, 2026-05-26)

**核心架构** (已在 2026-05-15 通读中完整记录):
- 三端架构: Android (com.trade.center.main) / iOS (com.trade.mainapp) / H5 Portal
- 应用入口: SplashActivity → LoginAct → HomeAct(Cordova WebView) → PrivacyWebAct
- 后端 API: eunomia-server (登录) + allinone-server (文件上传/用户信息) — **非 PVS 光伏业务**
- Cordova 插件: HaierDevice/Storage/Network/Http/Camera/FilePicker/Phone/NativeServer (8个)
- 网络层: OkHttp + RxJava3 (GET/POST/PUT/DELETE, 回调 + Observable)
- 安全配置: 明文传输允许、H5 白名单全开放、Android 13+ 媒体权限

**本轮变化**: 无新业务逻辑。34 个文件全部为基础设施代码 (AndroidManifest、Cordova 配置、UI 布局、网络封装)。

### 2. esp-mag-haier-h5-portal — Vue 2 + Cordova H5 门户

**类型**: H5 空壳项目
**最近提交**: `chore: init project with Vue 2 + Cordova H5 portal` (chufh, 2026-05-26)
**业务文件数**: 0
**结论**: 纯初始化空壳，无实际业务代码。

### 3. esp-mag-haier-ios-main — 海尔售电决策辅助系统 iOS

**类型**: iOS + Cordova H5 桥接
**最近提交**: `chore: 精简 .gitignore` / `feat: 初始化海尔售电决策辅助系统 iOS 项目` (chufh, 2026-05-26)

**核心架构** (与 Android 对称):
- Cordova config.xml: WKWebView 引擎、8个 Haier 桥接插件 (与 Android 一一对应)
- 网络权限: 全开放白名单 (`access origin="*"`)
- **非 PVS 光伏业务**

**本轮变化**: 仅 config.xml 配置，无新业务逻辑。

### 4. nahuipv_business_flutter — 纳光宝 Flutter APP

**类型**: Flutter 移动应用
**最近提交**: 2025-03-05 (Android 14 版本兼容) — 距今已 15 个月无变更

**核心架构** (已在 2026-05-15 通读中完整记录):
- 应用名: 纳光宝 (光伏终端用户 APP)
- 版本: 1.1.0+202****0401
- 技术栈: Flutter + Riverpod + Dio + Retrofit + Fluro
- 模块化依赖: nhpv_common_business + nhpv_usercenter_business + log_report_plugin (Git 子仓库)
- 签名配置: ⚠️ 密码明文存储在 key.properties 中

**本轮变化**: 无新业务逻辑。13 个文件全部为配置/build 文件 (pubspec.yaml、AndroidManifest、gradle 配置等)，无 Dart 业务源码。

### 5. nhpv_common_business — Flutter 通用业务组件库

**类型**: Flutter package (被纳光宝等多端复用)
**最近提交**: 2025-03-05 (Android 14 版本兼容) — 距今已 15 个月无变更

**核心架构** (已在 2026-05-15 通读中完整记录):
- 版本: 0.0.3
- 功能: 通用 UI 组件、网络请求封装、图片处理、版本更新 (r_upgrade 自研)
- 依赖: flutter_inappwebview、retrofit、dio、permission_handler 等

**本轮变化**: 无新业务逻辑。仅 3 个配置文件 (pubspec.yaml、analysis_options.yaml、local.properties)。

## 知识库更新

### 更新的文件

| 文件 | 操作 | 说明 |
|---|---|---|
| `state/full_sweep.json` | 更新 | sweep_round → 25, completed_repos 补全 (122/122), repo_last_sweep 更新 5 个仓库时间戳 |
| `modules/repositories.md` | 重新生成 | 从 full_sweep.json 同步，122 个仓库全部标记"已通读 ✅" + 最新日期 |
| `index.md` | 更新 | 轮次 23 → 24，更新通读日期和仓库列表 |

### 未更新的文件

- `domains/mobile-app-architecture.md`: 已有完整覆盖 (2026-05-15 首次通读 + 后续增量更新)，本轮无新内容需要追加
- 其他 domain 文件: 本轮仓库均为移动端/框架代码，无 PVS 后端业务逻辑

## 结论

本轮通读的 5 个仓库全部为**移动端/前端框架仓库**，不含 PVS 后端业务逻辑 (Java/Spring/MyBatis/Dubbo)。

- `esp-mag-haier-*` 三端: 海尔通用 Cordova H5 桥接框架，对接 eunomia-server/allinone-server (统一认证/会员)，**与 PVS 光伏业务无关**
- `nahuipv_business_flutter` / `nhpv_common_business`: Flutter 移动端应用，最后变更在 2025-03-05，已 15 个月无新业务代码

**知识库覆盖状态**: `domains/mobile-app-architecture.md` (775 行) 已完整覆盖所有移动端架构，无需追加。
