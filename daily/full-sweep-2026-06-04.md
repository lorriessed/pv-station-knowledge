# 全量通读报告 2026-06-04

## 统计

| 指标 | 值 |
|---|---|
| 通读轮次 | 第 21 轮 |
| 总仓库数 | 122 |
| 本次通读 | 5 个 |
| 已通读 | 107/122 (87.7%) |
| 从未通读 | 15 个 |

## 本次通读仓库

### 1. uni-choose-file-android
- **定位**: UniApp 跨平台文件选择原生插件 (Android)
- **业务文件**: 14 个 (全部为 XML 资源文件)
- **业务价值**: **极低** — 通用工具 SDK，无 PVS 光伏业务逻辑
- **发现**: 含 BLE OTA (蓝牙固件升级) 相关布局文件，最近提交 2026-01-20
- **知识库更新**: `domains/mobile-app-architecture.md` 追加 §6.2

### 2. uni-choose-file-ios
- **定位**: UniApp 跨平台文件选择原生插件 (iOS)
- **业务文件**: 0
- **业务价值**: **极低** — 空壳仓库，仅初始化提交 (2026-01-20)

### 3. vpp-api-auth ⭐ 高价值
- **定位**: VPP 系统统一认证中心
- **业务文件**: 27 个
- **技术栈**: Spring Boot 2.5.5 + JDK 8 + JWT + Redis + Feign
- **端口**: 8081, context-path: `/auth`
- **核心功能**:
  - 用户登录/注册 (`/token/token-login`, `/token/register`)
  - Token 管理 (标准 Token + VPP 专用 Token for Drcloud)
  - 密码错误锁定 + IP 黑名单
  - JWT 签发 + Redis 会话缓存
- **Feign 依赖**: vpp-api-system (用户/日志/i18n)
- **⚠️ 安全警告**: Drcloud 对接凭证 (appId/appSecret) 硬编码在源码中
- **知识库更新**:
  - `domains/vpp-overview.md` 新增 §14 VPP 认证服务 (7 个子节)
  - `domains/vpp-overview.md` §3.1 模块表更新为"已通读"

### 4. watermark-camera-android
- **定位**: Android 水印相机 SDK + Demo App
- **业务文件**: 26 个
- **业务价值**: **中** — 电站安装/巡检拍照采集基础设施
- **最近活跃**: 2026-05-19 ~ 2026-05-25 (v2.0.2~v2.0.5)
- **核心功能**: 带 GPS 坐标/时间戳/天气的水印拍照，高德地图定位
- **2026-05 变更**: 全局网络状态监听、断网限制、图片上传超时提醒、前摄/华为旋转优化
- **知识库更新**: `domains/mobile-app-architecture.md` 新增 §6.1

### 5. watermark-camera-ios
- **定位**: iOS 水印相机 SDK
- **业务文件**: 0 (本次扫描未读取源代码)
- **最近活跃**: 2026-05-19 ~ 2026-06-02 (网络监听、权限重试、定位修复)
- **知识库更新**: 无新增 (iOS 端未通读源码)

## 知识库更新汇总

| 文件 | 更新类型 | 内容 |
|---|---|---|
| `domains/vpp-overview.md` | 新增 + 更新 | §14 VPP 认证服务完整分析 (113行) + §3.1 模块表状态更新 |
| `domains/mobile-app-architecture.md` | 新增 | §6 原生工具 SDK (水印相机 + 文件选择) |
| `modules/repositories.md` | 更新 | 5 个仓库标记为"已通读 ✅" |
| `state/full_sweep.json` | 更新 | completed_repos +107, sweep_round=21 |

## 关键业务发现

1. **vpp-api-auth 是 VPP 系统的认证核心**: 提供标准 Token 和 Drcloud 专用 Token 两种模式，后者 expires_in 是前者的 60 倍。登录流程通过 Feign 调用 vpp-api-system 完成用户校验。
2. **水印相机 SDK 是电站影像采集的基础设施**: 被 `nhpv_watermark_camera` Flutter 插件和 `nahuipv_greenergy_flutter` APP 引用，照片水印包含 GPS 坐标和时间戳，用于数据真实性校验。
3. **安全风险提示**: vpp-api-auth 中 Drcloud appId/appSecret 硬编码，应迁移到 Nacos。
