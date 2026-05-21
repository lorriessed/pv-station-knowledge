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

### 广发并网进件完整流程 (代码明确证明, 2026-05-19~20)
**来源**: `rrsjk-light-service` → GfMergeGridInputPiece.java, GfApiUrlEnum.java, GfMergeGridInputPieceService/Impl, GfMergeGridInputPieceApi, GfBusinessOpportunityService/Impl, GfStationHandleStrategy, GfCompleteInputPieceProcess (commits 75ffdaa/cfb1bbd/ae366a8/2390ffa, majinhu, 2026-05-19~20, branch: 20260508-guangfa-binwang)
**关联需求**: TAEI-3073 【户用光伏】广发并网进件-附件改造、提交、电站详情
- **对接接口**: GfApiUrlEnum 定义15+个广发对接接口，前缀 `/inputpiece-plant/`
  - LOGIN → OPEN_ACCOUNT → OPEN_ACCOUNT_QUERY → BUSINESS_INPUT_PIECE → FIRST_INPUT_PIECE → QUERY_INPUT_PIECE_STATE
  - PROPERTY_CONTRACT_SIGN/PREVIEW/QRY/RUSH_CONTRACT/COMPANY_SEAL_CONTRACT/TERMINATE_CONTRACT
  - COMPLETE_INPUT_PIECE(过程进件) → CORRECTION_INPUT_PIECE(信息更正) → QUERY_STATION_INFO
  - QUERY_GRID_RESULT(并网结果查询) → SYNC_STATION_INFO(电站信息同步)
- **核心实体**:
  - `GfMergeGridInputPiece`: 并网进件，字段 stationCode, inputPieceId, voltageLevel, mergeType, feecollectType, elecAccountNum, eleFactoryNum
  - `GfBusinessOpportunity`: 商机注册
  - `GfFirstInputPiece`: 首次进件
  - `GfCompleteInputPiece`: 过程进件（施工验收阶段）
  - `GfLightStation`: 广发电站
  - `GfLightStationConfirmImg`: 电站确认影像
- **服务架构**:
  - `GfMergeGridInputPieceService`: 并网进件服务，包含列表查询、详情查询、信息更正
  - `GfMergeGridInputPieceApi`: Dubbo API 接口
  - `GfBusinessOpportunityService`: 商机注册服务
  - `GfStationHandleStrategy`: 电站处理策略（strategy模式）
  - `GfModeJob`: 广发模式定时任务
  - `GfCompleteInputPieceProcess`: 过程进件流程模型
- **前端页面**: `rrsjk-admin-web` → gf/GfMergeGridInputPieceList.ftl(列表), gf/GfMergeGridInputPieceDetail.ftl(详情+设计信息), gf/GfLightStationList.ftl, gf/GfCompleteInputPieceList.ftl
- **电站信息更正**: 2026-05-20 新增 `GfLightStation` 信息更正功能，支持同步更新广发电站信息修改结果
- **证据等级**: 代码明确证明

### 广发资方 — 项目公司配置/产品配置/项目公司政策/商机注册/营销政策 (TAEI-2884/2885/2891, 2026-03-02~16 代码明确证明)
**来源**: `rrsjk-light-service` (majinhu, 10+ commits; baoxin, 6 commits), `rrsjk-admin-web` (龙龙/majinhu, 5 commits)
**关联需求**: TAEI-2884 (广发资方项目公司配置/产品配置/项目公司政策), TAEI-2885 (广发商机注册对接), TAEI-2891 (广发营销政策配置)

- **广发EPC模式支持**: 新增广发EPC模式 (`龙龙`, commit 633daaa, 2026-03-03)
- **广发展信息授权协议**: 多次修复协议逻辑 (包鑫, 6 commits, 2026-03-02~04)
- **广发首次进件**: 添加广发首次进件功能模块 (马金虎, commit cdfbac5, 2026-03-09)
  - 广发电站详情页面图片展示功能更新 (马金虎, commit 240e83b, 2026-03-09)
  - 广发模式屋顶结构相关字段添加 (马金虎, commit b64125b, 2026-03-02)
  - 重构广发首片流程中的基础信息验证和产品筛选逻辑 (马金虎, commit 3135dcc, 2026-03-02)
  - 更新广发电站首次进件功能 (马金虎, commit 7bbfbca, 2026-03-02)
  - 修复广发商机推送逻辑，添加个人信息合同状态过滤条件 (马金虎, commit 1dfb10e, 2026-03-02)
- **广发合同支持**:
  - 广发合同预览和签署地址获取修复 (马金虎, commit 5a5f77e, 2026-03-11)
  - 广发合同作废功能 (马金虎, commit c167020, 2026-03-11)
  - 广发合同支持功能添加 (马金虎, commit 753da9c, 2026-03-11)
  - 广发二维码查询功能 (马金虎, commit 84a3515, 2026-03-12)
- **广发营销政策**: 广发展信息授权协议类型支持 (马金虎, commit b7e67f7, 2026-03-16)
- **广发模式图片处理**: 添加广发模式图片处理功能 (马金虎, commit ab2acf7, 2026-03-03)
- **商机注册推送**: `GfBusinessOpportunityProcess.businessInputPiece()` 定时任务推送商机到广发
  - 查询条件: `businessStatus=WAIT_PUSH` AND `personInfoContractStatus=SIGNED`
  - 推送失败处理: 状态改为 INTERCEPTION，记录驳回原因
- **涉及文件**: `GfBusinessOpportunityProcess.java`, `GfContractProcess.java`, `GfFirstInputPieceProcess.java`, `GfDict.java`
- **证据等级**: 代码明确证明

## 来源
- 每日代码扫描 2026-05-13，nahui-pv.mobile-h5, nahuipv_greenergy_flutter, rrsjk-light-service
- 历史补漏第6期扫描 2026-05-22 (2026-03-02~2026-03-22)
