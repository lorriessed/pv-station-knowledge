# PVS 全量代码通读报告 — 2026-06-14 (第30轮)

## 通读概况

| 指标 | 值 |
|---|---|
| 仓库总数 | 122 |
| 本轮通读 | 5 个 |
| 从未通读 | 0 个 (100% 覆盖) |
| 通读模式 | 重扫 (delta discovery) |
| 有增量仓库 | 1 个 (nahuipv_greenergy_flutter) |
| 零增量跳过 | 4 个 |

## 通读仓库清单

### 1. nahuipv-hnzc-app-android — 零增量 ⏭️
- **业务定位**: 慧能智充 EV 充电桩 Android APP (非光伏业务)
- **上次通读**: 2026-05-20
- **自上次以来提交**: 0 (唯一提交 2025-10-13 init project)
- **结论**: 跳过，无新知识

### 2. nahuipv-hnzc-app-ios — 零增量 ⏭️
- **业务定位**: 慧能智充 EV 充电桩 iOS APP (非光伏业务, 仅 AMap SDK 配置)
- **上次通读**: 2026-05-20
- **自上次以来提交**: 0 (唯一提交 2025-10-14 init project)
- **结论**: 跳过，无新知识

### 3. nahuipv-vpp-hnzl-rn — 零增量 ⏭️
- **业务定位**: VPP 湖南智绿 React Native 应用 (空壳仓库)
- **上次通读**: 2026-05-20
- **自上次以来提交**: 0 (唯一提交 2025-08-01 仓库初始化)
- **结论**: 跳过，无新知识

### 4. nahuipv_greenergy_flutter — ✅ 有增量
- **业务定位**: 海尔绿能现场运维 Flutter APP
- **上次通读**: 2026-05-20
- **自上次以来提交**: 33 个
- **版本演进**: 2.2.2 → 2.2.4

#### 🆕 核心发现: 电站转单功能 (feature-station-transfer)

**业务含义**: 电站管理权在分中心之间转移的完整流程。

**状态机** (5 个状态):
```
待确认转出(WAIT_OUT_CONFIRM) → 待确认转入(WAIT_IN_CONFIRM) → 转单完成(COMPLETED)
         ↓                                    ↓
    拒绝转出(OUT_REJECTED)              拒绝转入(IN_REJECTED)
```

**后端 API** (5 个端点, merchant-web 域名):
- `GET /merchant/lightStationTransferOrder/list.do` — 列表查询
- `POST /merchant/lightStationTransferOrder/confirmOut.do` — 确认转出
- `POST /merchant/lightStationTransferOrder/rejectOut.do` — 拒绝转出
- `POST /merchant/lightStationTransferOrder/confirmIn.do` — 确认转入
- `POST /merchant/lightStationTransferOrder/rejectIn.do` — 拒绝转入

**数据模型关键字段**:
- 转出方分中心: outSubSpMemberId / outSubSpName
- 转入方分中心: inSubSpMemberId / inSubSpName
- 电站信息: stationId, stationCode, ownerName, installedPower
- 驳回原因: outRejectReason, inRejectReason

**来源**: `nahuipv_greenergy_flutter/lib/model/enum/station_transfer_status.dart`, `lib/model/station_transfer_model.dart`, `lib/http/nh_api.dart` (代码明确证明)

#### 其他增量
- 电站列表优化 (功能指引/筛选/默认模式)
- 电站监控功能位置调整
- 图片预览旋转/缩放
- 相机 SDK 更换/回滚
- 组件时间选择范围优化
- 搜索历史标签适配

### 5. nhpv_common — 零增量 ⏭️
- **业务定位**: Flutter 公共组件库 (被 greenergy APP 依赖)
- **上次通读**: 2026-05-20
- **自上次以来提交**: 0 (最近提交 2026-05-07 在上次通读之前)
- **结论**: 跳过，无新知识

## 知识库更新

| 文件 | 操作 | 内容 |
|---|---|---|
| `domains/mobile-app-architecture.md` | 追加 §2.6.2a | 电站转单功能完整记录 (状态机/API/数据模型/UI) |
| `domains/mobile-app-architecture.md` | 更新 §2.6 标题 | 版本 2.2.2→2.2.4, 日期更新至 2026-06-14 |
| `modules/repositories.md` | 更新 5 条 | 标记 5 个仓库为 2026-06-14 已通读 ✅ |

## 待跟进

1. **电站转单后端实现**: API 路径指向 `/merchant/lightStationTransferOrder/*`，对应后端服务应为 `rrsjk-merchant-web`。需在下一次通读 rrsjk-merchant-web 时验证后端实现逻辑、涉及的数据库表（可能是 `light_station_transfer_order`）、以及与电站主状态机的关联。
2. **电站转单与电站生命周期的关系**: 转单是否改变电站的 `spMemberId` 归属？是否触发状态变更？需结合后端代码确认。
