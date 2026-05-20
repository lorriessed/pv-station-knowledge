# 全量通读报告 2026-05-20

## 概览

| 指标 | 值 |
|---|---|
| 通读轮次 | 第7轮 |
| 本次通读仓库数 | 5 |
| 总仓库数 | 100 |
| 已通读 | 100/100 (100%) |
| 通读日期 | 2026-05-20 |

## 本次通读仓库

| # | 仓库 | 分支 | HEAD | 业务文件数 | 类型 | 业务价值 |
|---|---|---|---|---|---|---|
| 1 | nahuipv-hnzc-app-android | master | 4ba8284 | 146 | 原生 Android | ⚠️ 非光伏 (充电桩) |
| 2 | nahuipv-hnzc-app-ios | master | 1a668aa | 3 | 原生 iOS (仅SDK配置) | ⚠️ 非光伏 (充电桩) |
| 3 | nahuipv-vpp-hnzl-rn | main | e6916d9 | 0 | React Native | 空壳仓库 |
| 4 | nahuipv_greenergy_flutter | master | bb4e192 | 18 | Flutter | 绿能运营 (活跃开发) |
| 5 | nhpv_common | master | 3d52f76 | 2 | Flutter 公共包 | 基础设施 |

## 关键发现

### 1. 湖南智充 APP 属于充电桩业务 (非光伏)

**nahuipv-hnzc-app-android** 是"慧能智充"电动汽车充电桩 APP：
- 面向用户：充电桩使用者
- 后端 API 指向 `ykccn.com`，不是 `rrsjk.com` 光伏后端
- 核心功能：充电站搜索、扫码充电、路线规划、微信/支付宝支付
- 第三方集成：高德地图、ZXing 扫码、七鱼客服
- **结论**：与 PVS 光伏业务无关，标记为低 PVS 业务价值

**nahuipv-hnzc-app-ios** 仅有 AMap NaviKit SDK 的 3 个 XML 配置文件，无实际业务代码。

### 2. nahuipv_greenergy_flutter 集成 DJI 无人机 SDK

**新发现**：海尔绿能 Flutter APP 集成了 DJI Mobile SDK 用于无人机飞控：
- USB 配件支持 4 种 DJI 设备 (T600, AG410, com.dji.logiclink, WM160)
- `activity_aplsh.xml` 包含"点击调用飞控"按钮
- 大量 DJI UX SDK 样式 (电池/飞行模式/避障等)
- DJI API Key: `d38d5408aa93389e40d53b11` (⚠️ 明文存储)
- 版本：2.2.2+202****1901

**近期活跃开发** (2026-05-14 ~ 2026-05-19)：
- 更换水印相机 Android SDK (修复二维码白边/logo)
- 地图 Key 更新
- 电站列表项优化
- 广发业务 (feat_gf 分支)

### 3. nahuipv-vpp-hnzl-rn 为空壳仓库

- 唯一提交：`feat: 代码交付仓库初始化20250801`
- 业务文件数：0
- 自 2025-08 初始化以来无实际业务代码

### 4. nhpv_common 仅含配置文件

- 仅 `pubspec.yaml` 和 `analysis_options.yaml`
- 实际 Dart 代码在 Git 仓库 `mobile/greenergy/packages/nhpv_common.git`
- 被 greenergy_flutter 作为 Git 依赖引入

## 知识库更新

| 文件 | 操作 | 说明 |
|---|---|---|
| `domains/mobile-app-architecture.md` | 新增 §3 | 湖南智充 APP 详细分析 (非光伏业务) |
| `domains/mobile-app-architecture.md` | 新增 §2.6 | greenergy_flutter DJI SDK 集成/近期开发 |
| `domains/mobile-app-architecture.md` | 新增 §2.7 | nhpv_common 组件库 |
| `domains/mobile-app-architecture.md` | 新增 §2.8 | vpp-hnzl-rn 空壳仓库 |
| `domains/mobile-app-architecture.md` | 更新 §4 | 移动应用关系表 (标注非光伏/空壳) |
| `domains/vpp-overview.md` | 更新 | 移动端列表标注非光伏/空壳状态 |
| `modules/repositories.md` | 全量重建 | 从 full_sweep.json 同步通读状态 |

## 安全警告

| 仓库 | 问题 | 详情 |
|---|---|---|
| nahuipv_greenergy_flutter | DJI API Key 明文 | `dji.api.key=d38d5408aa93389e40d53b11` |
| nahuipv_greenergy_flutter | 高德 API Key 明文 | `amap.api.key=82b736d8df82ec508bb37fab882314f4` |
| nahuipv_greenergy_flutter | 签名密码明文 | `storePassword=123456` |
| nahuipv_greenergy_flutter | Mapbox Token | `sk.eyJ...` (已部分脱敏) |
