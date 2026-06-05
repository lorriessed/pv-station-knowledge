# greenergy-management — 海尔绿能通（分中心 App）

> 扫描日期: 2026-06-05
> 仓库: `mobile/greenergy-management/greenergy-management.git`
> 本地路径: `/root/greenergy-management`
> 包名: `com.haier.greenergy.management`
> iOS App ID: `6742817613`

## 项目概况

- **技术栈**: Flutter 3.27.4（通过 fvm 管理），Dart SDK `>=3.5.0 <4.0.0`
- **架构**: MVVM + Riverpod + GoRouter，目录按 feature 组织
- **包名**: `greenergy` (pubspec name)
- **版本格式**: `0.0.1+202****2501`
- **本地依赖**: `app_upgrader_flutter` (path: `../app_upgrader_flutter`)

## 技术选型

| 领域 | 技术 |
|---|---|
| 状态管理 | Riverpod 2.6.1 + riverpod_generator |
| 路由 | GoRouter 14.6.2（StatefulShellRoute.indexedStack） |
| 网络 | Dio 5.7.0 + Retrofit 4.4.1 |
| 数据模型 | Freezed 2.5.7 + json_serializable |
| 图表 | fl_chart 0.70.2 |
| 屏幕适配 | flutter_screenutil 5.9.3（设计稿 375×812） |
| 日志 | logger 2.5.0（封装在 `lib/utils/app_logger.dart`） |
| 国际化 | intl 0.19.0 + flutter_localizations |
| WebView | flutter_inappwebview 6.1.5 |

## 项目结构

```
lib/
├── config/          依赖注入（dependencies.dart + providers/）
├── core/            跨模块基础设施
│   ├── platform/    原生能力抽象（camera, device_info, location, permission）
│   └── webview/     WebView 容器 + JS Bridge
├── data/            数据层
│   ├── repositories/<feature>/   Repository 抽象 + Remote/Mock 实现
│   └── services/
│       ├── api/     Dio + Retrofit API 服务（含 Interceptor）
│       └── local/   本地存储（TokenStorage, SavedAccounts）
├── domain/          业务域模型（跨层共享）
│   └── models/      ApiResponse, Result, AsyncState, Auth 模型等
├── routing/         GoRouter 配置（router.dart, routes.dart）
├── ui/              UI 层（MVVM）
│   ├── auth/        登录模块（LoginPage, FaceLoginPage, AccountAutocomplete）
│   ├── core/        公共组件（themes, widgets, mixins）
│   ├── home/        首页（HomePage + ViewModel）
│   ├── workspace/   工作台（WorkspacePage）
│   ├── profile/     我的页（ProfilePage, EnvSwitchBottomSheet, UpdateViewModel）
│   └── devtools/    开发者工具展示页（各种 Demo）
├── utils/           通用工具（debounce_throttle, app_logger）
├── i18n/            ARB 翻译文件
└── main.dart        入口
```

依赖方向：`ui → domain ← data`

## API 接口

### 环境配置

| 环境 | Base URL |
|---|---|
| 测试 | `https://apitest.nahuipv.com` |
| 生产 | `https://api.nahuipv.com` |

- 环境切换：通过 `SharedPreferences` 持久化，Profile 页面可运行时切换
- 默认：debug 模式 → 测试环境，release 模式 → 生产环境

### OAuth2 登录

- **接口**: `POST /oauth2/oauth/login`
- **认证方式**: OAuth2 Password Grant
- **Client ID**: `nh_app`
- **Scope**: `app`
- **Grant Type**: `password`
- **User-Agent**: `NH_APP_GREENERGY/ANDROID`

### 路由路径

| 路径 | 说明 |
|---|---|
| `/login` | 登录页 |
| `/` | 首页（Home） |
| `/workspace` | 工作台 |
| `/profile` | 我的页 |
| `/analytics` | 数据分析（规划中） |
| `/check-in` | 签到（规划中） |
| `/warning` | 告警（规划中） |
| `/project-funnel` | 项目漏斗（规划中） |
| `/acceptance` | 验收（规划中） |
| `/station` | 电站（规划中） |
| `/watermark-camera` | 水印相机（规划中） |
| `/webview` | WebView 容器 |

### Retrofit API 服务

| 服务 | 文件 | 接口 |
|---|---|---|
| AuthApiService | `data/services/api/auth/auth_api_service.dart` | `POST /oauth2/oauth/login` |
| VersionApiService | `data/services/api/version/version_api_service.dart` | 版本检查/更新 |

## 核心模块

### 1. 鉴权流

```
LoginPage → AuthViewModel.login()
              ↓
        AuthRepository（abstract → Remote/Mock）
              ↓
        AuthState.authenticated → AuthRefreshListenable → GoRouter redirect
```

- `AuthViewModel`: `@Riverpod(keepAlive: true)`
- Token 存储：`TokenStorage`（SharedPreferences）
- 循环依赖解决：`config/auth_callbacks.dart` 全局回调注入
- 账号自动补全：`SavedAccountsService` + `AccountAutocomplete` 组件

### 2. 数据层模式

```
View → ref.watch → ViewModel → ref.read → Repository → Domain 模型
```

- Repository 返回 `Result<DomainModel>`（非直接抛出异常）
- Provider 根据 `useMockApiProvider` 注入 Remote/Mock 实现
- 错误处理：`error_interceptor.dart` + `error_response_classifier.dart`
- 日志拦截器：`logging_interceptor.dart`
- 认证拦截器：`auth_interceptor.dart`（自动附加 token）

### 3. 主题系统

- `AppColorsData` → `AppColorsTokens`（ThemeExtension）
- `AppDimens`: 集中封装 ScreenUtil，UI 代码直接使用 `AppDimens.paddingL` 等
- `AppTextStyles`: 集中字体样式
- 暗色主题：token 已预留，一期只实现亮色

### 4. 加载系统

- `AsyncState<T>`: 统一异步状态模型（initial/loading/success/error）
- `LoadingButton`: 带 loading 状态的按钮
- `LoadingStateHandler`: 全局 loading 状态处理
- `SkeletonListView/Box`: 骨架屏组件
- `AppLoading`: 应用级 loading 对话框

### 5. WebView 容器

- 基础组件：`webview_page.dart`, `webview_widget.dart`
- JS Bridge：`js_bridge_controller.dart`
- 配置模型：`webview_config.dart`
- 服务层：`webview_service.dart`

### 6. 原生能力抽象

| 能力 | 抽象类 | 实现 |
|---|---|---|
| 相机 | `CameraPlatform` | `CameraPlatformImpl` |
| 设备信息 | `DeviceInfoPlatform` | `DeviceInfoPlatformImpl` |
| 定位 | `LocationPlatform` | `LocationPlatformImpl` |
| 权限 | `PermissionPlatform` | `PermissionPlatformImpl` |

### 7. 应用更新

- 使用 `app_upgrader_flutter`（本地依赖）
- `UpdateViewModel`: 版本检查 + 下载 + 安装
- APK 本地缓存机制

## OpenSpec 变更记录

| 日期 | 变更 | 说明 |
|---|---|---|
| 2026-04-15 | app-architecture | 搭建项目基础框架（脚手架、数据模型、网络层、主题、权限、平台抽象、i18n） |
| 2026-04-15 | logging-system | 日志框架 |
| 2026-04-15 | startup-device-info | 启动设备信息 |
| 2026-04-24 | flatten-project-structure | 扁平化目录结构 |
| 2026-04-25 | auth-feature-complete | 完成模拟登录和真实 API 登录 |
| 2026-04-25 | real-login-api | 真实登录 API 对接 |
| 2026-04-29 | add-main-tabbar | 添加首页 TabBar |
| 2026-05-08 | env-switch-ui | 环境切换 UI |
| 2026-05-08 | improve-login-api | 登录流程改进（异常处理、用户信息持久化） |
| 2026-05-11 | fix-layer-dependencies | 修复分层依赖 |
| 2026-05-12 | align-compass-architecture | 对齐 compass_app 架构（MVVM + Riverpod + Result 类型） |
| 2026-05-12 | debounce-throttle-utility | 防抖/节流工具类 |
| 2026-05-16 | loading-system | 统一加载系统（AsyncState + Skeleton + LoadingButton） |
| 2026-05-19 | auth-persistence-to-viewmodel | 鉴权持久化到 ViewModel |
| 2026-05-19 | dev-showcase | 开发者工具展示页 |
| 2026-05-19 | retrofit-migration | Retrofit 迁移 |
| 2026-05-21 | apk-local-cache | APK 本地缓存 |
| 2026-05-22 | self-update-apk | 应用自更新 |
| 2026-05-23 | app-update-package | 应用更新包 + 国际化 |
| 2026-05-30 | webview-container | WebView 容器 + JS Bridge |
| 2026-06-01 | saved-accounts | 登录账号自动补全/历史记录 |

## 规划中功能

根据路由定义，以下功能页面已注册但尚未实现完整业务逻辑：

- 数据分析（analytics）
- 签到（check-in）
- 告警（warning）
- 项目漏斗（project-funnel）
- 验收（acceptance）
- 电站（station）
- 水印相机（watermark-camera）

## 开发规范

- **禁止魔法值**：尺寸走 `AppDimens`，字体走 `AppTextStyles`，颜色走 `AppColorsTokens`
- **ScreenUtil**: 集中在 `AppDimens` getter 中，禁止在页面中调用 `.w`/`.r`
- **GoRouter only**: 禁止 Flutter 原生 Navigator
- **生成文件进 git**: `*.g.dart`、`*.freezed.dart`
- **OpenSpec 工作流**: 跨模块任务先 `openspec/changes/` 规划
- **日志**: 使用 `lib/utils/app_logger.dart`，避免 `print()`
- **所有命令走 fvm**: `fvm flutter run` / `fvm flutter test` / `fvm flutter build apk`
