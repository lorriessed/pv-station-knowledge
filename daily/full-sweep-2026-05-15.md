# PVS 全量代码通读报告 2026-05-15

## 通读概览

- **通读日期**: 2026-05-15
- **本轮第几轮**: 第 1 轮
- **本次通读仓库数**: 5
- **累计已通读**: 24 个 (PVS 5 + VPP 后端 15 + 移动端 4)

## 通读仓库清单

| # | 仓库 | 分支 | HEAD | 业务文件数 | 性质 |
|---|---|---|---|---|---|
| 1 | esp-mag-haier-android-main | master | 511ce2f | 30 | Android Cordova H5 桥接 |
| 2 | esp-mag-haier-h5-portal | master | ef49e0b | 0 | H5 空壳 |
| 3 | esp-mag-haier-ios-main | master | bbb750a | 2 | iOS Cordova H5 桥接 |
| 4 | nahuipv_business_flutter | main | c238ac8 | 13 | Flutter 纳光宝 APP |
| 5 | nhpv_common_business | main | 1811e11 | 3 | Flutter 通用组件库 |

## 业务发现总结

### 仓库 1-3: esp-mag-haier-* (Cordova H5 桥接体系)

**业务价值**: 低 — 这些是**海尔通用 H5 桥接框架**，非光伏/VPP 业务代码。

- **Android**: 30 个业务文件，包含 Cordova 配置、登录页面、WebView 容器、8 个原生插件
- **iOS**: 2 个配置文件 (config.xml)，与 Android 对称的 8 个 Cordova 插件
- **H5 Portal**: 0 个业务文件，空壳交付

**关键发现**:
1. Cordova 插件体系完整 (设备/存储/网络/HTTP/相机/文件/电话/原生服务)
2. 网络层基于 OkHttp + RxJava3
3. 登录接口指向 `eunomia-server`(统一认证) 和 `allinone-server`(会员体系) — **与 PVS/VPP 无关**
4. 最近提交: 2026-05-12 "朗新一期交付代码"

### 仓库 4: nahuipv_business_flutter (纳光宝 APP)

**业务价值**: 高 — 纳光宝是 VPP 终端用户 APP

- **技术栈**: Flutter + Riverpod + Dio + Retrofit + Fluro
- **版本**: 1.1.0
- **核心功能**: VPP 电站列表、图片防盗链、Android 14 兼容
- **模块化**: 依赖 nhpv_common_business、nhpv_usercenter_business、log_report_plugin
- **签名密码**: 明文存储在仓库中 (安全风险)

### 仓库 5: nhpv_common_business (通用组件库)

**业务价值**: 中 — 被纳光宝等多端复用的基础组件

- **版本**: 0.0.3
- **核心功能**: 通用 UI 组件、网络封装、版本更新 (r_upgrade 自研库)
- **历史变更**: 2025-01-13 新增 VPP 账号类型、2024-12-20 WebView 改为 inappwebview

## 知识库更新

### 新增文件

| 文件 | 内容 |
|---|---|
| `domains/mobile-app-architecture.md` | 移动端应用架构完整文档 (Cordova 桥接 + Flutter 纳光宝) |

### 更新文件

| 文件 | 变更内容 |
|---|---|
| `modules/repositories.md` | 新增 5 个已通读仓库标记 |
| `modules/vpp-repositories.md` | 新增移动端和 Cordova H5 桥接分类 |
| `domains/vpp-overview.md` | 新增纳光宝 APP 和 Cordova 桥接应用章节 |
| `state/full_sweep.json` | 更新 completed_repos 数组 |

## 未通读仓库 (剩余)

- **PVS**: 67 个 (以 rrsjk-light-operation-service, nahui-pv.hds-h5 等高活跃度优先)
- **VPP**: 9 个 (vpp-api-auth, vpp-api-template, he-vpp.admin-h5 等)

## 备注

本次通读的 5 个仓库全部为**移动端前端代码**，不包含后端业务逻辑、数据库操作或 Dubbo 服务。
业务规则的理解仍需依赖后端仓库 (rrsjk-*, vpp-api-*) 的通读。
纳光宝 APP 是 VPP 业务的重要终端入口，其数据来源于 vpp-api-elecbusiness 等服务。
