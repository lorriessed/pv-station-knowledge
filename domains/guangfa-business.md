# 广发（Guangfa）业务模式

更新时间: 2026-05-13

## 已确认知识

### 广发模式概述
**来源**: 多个前端仓库 (nahui-pv.mobile-h5, nahuipv_greenergy_flutter) (commits 65c66a6/a608856, 2026-05-12)

广发是新增的资方/业务模式，与华融(HR)模式并列。前端通过 `station_mode_util` 区分不同模式展示不同UI。

### 广发完工确认模块
**来源**: `nahui-pv.mobile-h5` → `src/views/apv/completeAffirmGf/` (commit 65c66a6, yanghui, 2026-05-12)
- 新增独立广发完工确认页面 `completeAffirmGf/`，包含组件：
  - `basic.jsx` — 基本信息
  - `distributionBox.jsx` — 配电箱信息
  - `inverter.jsx` — 逆变器信息
  - `moduleInfo.jsx` — 组件信息
  - `powerMaterial.jsx` — 电力材料
  - `videoDatum.jsx` — 视频资料
- 新增广发逆变器维护页面 `inverterMaintenanceGf/`

### 广发模式前端行为
**来源**: `nahuipv_greenergy_flutter` → `station_mode_util.dart`, `home_functional_area.dart` (commits a608856/befafdd, dongxueqiang, 2026-05-12)
- 新增 `station_mode_util.dart` 工具类，用于电站模式判断和切换
- 广发模式优化完工确认，修改电站影像操作
- 华融模式隐藏基本信息变更菜单
- 解决电站列表优化和华融模式冲突

### 广发商机管理
**来源**: `rrsjk-light-service` → `GfBusinessOpportunity.java`, `GfBusinessOpportunityServiceImpl.java` (commit 46f208a, majinhu, 2026-05-12)
- `GfBusinessOpportunity` 实体：广发商机管理
- 默认弃置状态为 0

### 广发进件附件体系
**来源**: `rrsjk-light-service` → `constant/gf/GfFileEnum.java` (历史扫描)
- 商机注册阶段: BS_0_10 ~ DHBS_0_680
- 首次进件阶段: FS_前缀 + GZFZ 前缀
- 过程进件（施工验收）: CP_GZFZCP_200020_3750 ~ 4290

### 广发相关后端服务
**来源**: `rrsjk-light-service` (历史扫描 + 本次扫描)
- 广发模式相关代码位于 `rrsjk-light-service` 的 `gf/` 包下
- 分支 `20260424-guangfa`, `20260506-guangfa-tuisongbohui`, `20260508-guangfa-qizhi`, `20260511-guangfa-heguizhaopian` 均涉及广发功能

## 待确认
- 广发模式的完整电站状态机（是否与现有状态机有差异）
- 广发模式的结算/记账规则
- 广发与其他资方的审核流程差异
- 广发模式下完工确认的后端服务实现类

## 来源
- 每日代码扫描 2026-05-13，nahui-pv.mobile-h5, nahuipv_greenergy_flutter, rrsjk-light-service
