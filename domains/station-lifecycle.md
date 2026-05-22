# 电站生命周期

更新时间: 2026-05-09

## 已确认知识

### 主流程
录单 -> 审核 -> 方案 -> 下单 -> 施工 -> 完工 -> 技术审核 -> 可选线下验收 -> 商务审核 -> 启用。

### 电站状态机
已确认状态包括：INIT、WAIT_AUDIT、WAIT_THIRD_AUDIT、WAIT_CONFIG、WAIT_ORDER、ROADWORKING、ROADWORK_CONFIRM、COMPLETE_WAIT_AUDIT、WAIT_TECH_CHECK、WAIT_OFF_LINE_CHECK、WAIT_UPLOAD_GRID_INFO、WAIT_FIRST_AUDIT、ENABLE、DISABLE、STOP、REPURCHASE。驳回后可重新提交，异常终止包括 DISABLE、STOP、REPURCHASE。

### 电站模式 (ModeEnum)
**来源**: rrsjk-light-service → `YuexiuFileEnum.java`, `entity/LightStation.java`
| 模式 | 含义 | 对应公司 |
|---|---|---|
| YX | 越秀模式 | 1Q10 (青岛海尔绿色能源科技有限公司) |

### 电站类型 (StationTypeEnum)
**来源**: rrsjk-light-service → `YuexiuFileEnum.java`
| 类型 | 含义 |
|---|---|
| COMMON | 普通户用 |
| HOUSEHOLD | 户用 |
| PUB_BUILD | 公共建筑/B端电站 |

### 资方附件体系
**来源**: rrsjk-light-service → `constant/YuexiuFileEnum.java`

#### 越秀模式 (1Q10) 附件编码规则
- 户用电站: RRS_A_01 ~ RRS_C_13 (信息授权、身份证、房产证明、踏勘设计、租赁物照片等)
- B端电站: RRS_FR_A_01 ~ RRS_FR_B_17 (营业执照、法人身份证、村委决议、竣工材料等)
- 按审核阶段分类: 承租人预审 → 风险审查 → 农户投放审查

#### 股转电站附件 (海昕顺/华耀顺)
| 项目公司 | 编码前缀 | 公司编码 |
|---|---|---|
| 青岛海昕顺新能源 | HXS_ | 1Q10 |
| 郑州华耀顺绿色新能源 | ZZHY_ | 1RM0 |

### 逆变器品牌枚举
**来源**: rrsjk-light-service → `constant/baidu/BrandEnum.java`
| 枚举值 | 含义 |
|---|---|
| GINLONG | 锦浪 |
| AISWEI / AI1 | 爱士惟 |
| HOPEWIND | 禾望 |
| SINENG | 上能 |
| NAHUI | 纳晖 |
| GOODWE | 固德威 |
| HAIER | 海尔 |

### 合作方进件体系
**来源**: rrsjk-light-service → `constant/dh/DhFileEnum.java`, `constant/gf/GfFileEnum.java`

#### 顶好 (Dinghao) 进件
- 商机注册阶段 (business_opportunity): BS_0_10 ~ DHBS_0_680
  - 业主信息: 身份证、营业执照、法人身份证、银行卡、共签人信息
  - 区分自然人(NATURE)和非自然人(NOT_NATURE)客户类型
- 首次进件阶段 (first_input_piece): FS_前缀
  - 勘察信息: 房屋整体、周边、内部照片
  - 设计信息: 组件排布、支架、接线图、电气图

#### 广发 (Guangfa) 进件
- 商机注册阶段: BS_0_10 ~ DHBS_0_680 (类似顶好但编码略有差异)
- 首次进件阶段: FS_前缀 + GZFZ 前缀
  - 房屋整体类: 包含VR全景图 (FR_200020_60)
  - 房屋屋顶类: 东南西北各方向照片
  - 过程进件 (施工验收): CP_GZFZCP_200020_3750 ~ 4290
    - 施工安全类、基础安装、支架安装、组件安装、逆变器安装、并网箱安装、线缆类、接地极、防水措施

### 百度AI识别
**来源**: rrsjk-merchant-web → `baidu/ImageRecognizeController.java`
- 接口: `/light/imageRecognize/imageNum.do`
- 功能: 图像AI识别太阳板数量
- 使用百度OCR服务，记录识别日志到 `LightStationBaiduAILogService`

## 待确认
- 各资方模式下状态机是否存在专用跳转。
- WAIT_OFF_LINE_CHECK 的触发条件。

## 来源
- Hermes MEMORY.md，2026-05-09 迁移。
- 代码来源待每日扫描补充：/data/pvcode/rrsjk-light-service。

## 华融EPC电站模式 (代码明确证明)
**来源**: `rrsjk-light-service` → `HrflcEpcStationMode.java`, `CompleteConfirmServiceImpl.java`, `LightStationHrflcServiceImpl.java`, `HrflcFirstProjectJobServiceImpl.java`, `HrflcSecondProjectJobServiceImpl.java` (commits 7ecb846/223a41d/efaa535/663a20d/ac59815, 2026-05-12)

### 华融EPC状态管理
- 华融EPC模式有独立的状态管理链路，通过 `HrflcEpcStationMode` 建模
- `CompleteConfirmServiceImpl` 中包含华融EPC电站状态更新逻辑，修复了状态更新问题
- `HrflcFirstProjectJobServiceImpl` 和 `HrflcSecondProjectJobServiceImpl` 负责华融EPC项目状态管理的定时任务
- `LightStationHrflcServiceImpl` 处理华融EPC电站核心业务逻辑
- 新增主行联行号字段支持（`LightStationRequest`, `LightStationConfirmRequest`）

### 主行联行号
- **来源**: `rrsjk-light-service` → `LightStationRequest.java`, `LightStationConfirmRequest.java`, `LightStationServiceImpl.java` (commit fd8aea1, 2026-05-12)
- 电站确认和录单时支持传递主行联行号字段，用于HRFLC-EPC模式确认逻辑

### 广发模式前端完工确认 (前端确认)
**来源**: `nahui-pv.mobile-h5` → `src/views/apv/completeAffirmGf/` 目录 (commits b01daf0/81f3652/698782d, yanghui, 2026-05-12~2026-05-14)
- 广发模式(H5端)完工确认详情页面: `completeAffirmGf/index.jsx`, `components/videoDatum.jsx`
- 广发详情页面新增 VR 链接展示: `src/views/apv/stationDetailsGf/StationInfoGF.jsx`
- VR 链接样式优化: `src/utils/app.js`, `completeAffirmGf/index.less`
- 路由定义: `src/router/modules/apv.jsx`
- **证据等级**: 配置明确证明（前端组件/路由层面确认）

### Flutter App 电站列表与导航
**来源**: `nahuipv_greenergy_flutter` → 多个文件 (commits 2026-05-08~2026-05-14, jiangting/dongxueqiang)
- 电站列表新增字段: 经销商(`dealer`)和装机功率(`installCapacity`)
- 地图导航: 支持高德/百度/腾讯地图 (`map_utils.dart`, `map_dialog.dart`)
- 电话拨打组件: `phone_call.dart`
- 功能指引: 电站列表功能引导页面 (`station_feature_guide.dart`)
- API Key 外部化: 高德/大疆 key 从硬编码改为 `android/key.properties` + Gradle 占位符

### 电站完工后自动划转运维商 (代码明确证明, 2026-05-18 历史补漏第1期)
**来源**: `rrsjk-light-service` → `LightOpAuthorityZoneServiceImpl.autoTransferStationOp()`, `CompleteConfirmServiceImpl`, `LightStationEpcServiceImpl`, `HrflcEpcStationMode`, `OffLineStationFlowServiceImpl` (TAEI-2698/2699/2700, 2025-11-17~2025-12-07)
- **触发时机**: 电站完工确认审核通过(auditOk)、EPC模式下单、华润模式确认、线下电站流程审核通过时
- **核心方法**: `LightOpAuthorityZoneService.autoTransferStationOp(LightStation)`
- **划转逻辑**:
  1. 获取电站的 regionId(区域ID)
  2. 查询该区域下已中标的运维区域: status=ENABLE 且 isInvestment=0(非投资)
  3. 取最新一条匹配记录，获取其 memberId(运维商ID)
  4. 更新电站的 opMemberId 为新的运维商ID
  5. 更新运维承接时间(opTime)
  6. 同步更新 LightOperationStation 的运维承接时间和成员ID
- **调用链路**:
  - `CompleteConfirmServiceImpl.auditOk()` → 完工确认审核通过 → `autoTransferStationOp()`
  - `LightStationEpcServiceImpl` → EPC模式电站创建 → `autoTransferStationOp()`
  - `HrflcEpcStationMode` → 华润模式 → `autoTransferStationOp()`
  - `OffLineStationFlowServiceImpl` → 线下电站审核流程 → `autoTransferStationOp()`
- **相关表**: light_op_authority_zone(运维商授权区域), light_op_contract_record(运维合同), light_station(电站主表opMemberId字段)
- **合同生成**: 运维商区域授权每5个区域生成一份"服务区域授权补充协议"，状态为WAIT_SIGN(待签署)

### 运维商入驻流程 (代码明确证明, 2026-05-18 历史补漏第1期)
**来源**: `rrsjk-light-service` → `LightOpAuthorityZone.java`, `LightOpAuthorityZoneService.java` (TAEI-2699, 2025-11-18)
- 运维商入驻流程优化: 涉及运维商授权区域管理
- 运维商入驻后需要授权区域(Region)才能承接电站运维
- 授权区域有状态(ENABLE/DISABLE)和投资属性(isInvestment)区分

### 第三方社会化电站逆变器数据对接 (代码明确证明, 2026-05-18 历史补漏第1期)
**来源**: `rrsjk-light-service` → `CompleteConfirmServiceImpl`, `LightStationConfirmImg.java` (TAEI-2700, 2025-11-18)
- 第三方社会化电站的逆变器数据通过确认图片服务对接
- 涉及实体: LightStationConfirmImg(电站确认图片), LightStationAudit(电站审核)

### 线下电站审核流程 (代码明确证明, 2026-05-18 历史补漏第1期)
**来源**: `rrsjk-light-service` → `OffLineStationFlowServiceImpl.java` (TAEI-2704, 2025-11-20)
- 线下电站审核流程完善: 方案审核、完工分中心审核、技术审核、商务审核
- 审核记录审核人IP地址(TAEI-2704)
- 审核通过后触发运维商自动划转

### 分中心编码(subCenterCode)支持 (代码明确证明, 2026-05-18)
**来源**: TAEI-3053【建站】一商做全国, `rrsjk-light-service` (commits 1a83966b/ee595c18, 姜传德/德, 2026-05-14)

#### 实体变更
- **City**: 新增 `subCenterCode` 字段（分中心编码）
- **LightSpStore**: 新增 `subCenterCode` + `subCenterName` 字段（服务商仓库分中心信息）
- **LightPurchaseAppeals**: 新增分中心信息字段

#### MyBatis Mapper 变更
- **City.xml**: 查询/插入/更新/条件筛选逻辑中增加 `sub_center_code` 字段
- **LightSpStore.xml**: 字段映射和查询条件处理逻辑中增加分中心字段
- **LightPurchaseAppeals.xml**: 查询逻辑中增加分中心字段

#### 业务逻辑变更
- `LightConfirmOrderServiceImpl`: 分中心代码赋值来源从服务商改为门店（`spStore` → `store`）
- `LightServiceProviderServiceImpl`: 注入 `CityDao`，根据城市ID获取分中心信息设置到仓库对象
- `LightTransferSpApplyServiceImpl`: 调拨申请中增加分中心信息传递

#### 业务语义
- **一商做全国**: 一个服务商可以做全国业务，需要通过分中心编码来区分不同区域的业务归属
- 分中心信息关联: 城市 → 分中心编码 → 服务商仓库

### 运维电站承接时间 (2025-12-19~23, TAEI-2782/TAEI-2784)
- **来源**: `rrsjk-light-operation-service` (commits 62bcfe9/d1c9d46/035aa8f, sunzn)
- **需求背景**: 商户通/HDS运维服务电站列表需展示"承接运维时间"，电站数据变更流程升级需区分建站商与运维商身份
- **实体变更** (`LightOperationStation`):
  - `spMemberId` — 建站商会员ID(新增)
  - `opMemberId` — 运维商会员ID(已有, 新增赋值逻辑)
  - `opCode` — 运维商编码
  - `opName` — 运维商名称
  - `opType` — 运维商身份类型(identityType)
  - `specialTime` — 承接运维时间(LocalDateTime, 核心新增字段)
- **Service新增方法** (`LightOperationStationService`):
  - `updateStationOpTimeAndMemberId(memberId, stationCode, opTime)` — 运维招商区域, 电站已完成节点时更新承接时间及运维商会员ID
    - 逻辑: 校验运维商存在且状态为"运营中"(ENABLE) → 查询电站 → 批量更新opMemberId/opCode/opName/opType/specialTime → insertOrUpdateBatch
  - `updateStationOpTime(memberId)` — 建站运维商签署主合同后更新自有电站的承接时间
- **定时任务** (`LightOperationScheduledJobService`):
  - `refreshHistoryOpSpecialTime` — 历史电站承接时间刷新Job(异步执行)
- **查询条件扩展** (`StationQuery`):
  - 新增 `spMemberId` 查询字段
- **服务商身份类型** (`LightOperationProviderServiceImpl`, commit 65eb67f):
  - 区分建站商与运维商, 优化名称重复同步逻辑(避免同一公司名被重复识别)
- **Mapper变更**:
  - `LightOperationStation.xml` — 新增承接时间相关SQL
  - `LightStation.xml` — 查询条件增加spMemberId

### 逆变器替换/变更优化 (2025-12-08~23, TAEI-2748)
- **来源**: `rrsjk-light-service` + `rrsjk-light-data-service` (commits by majinhu/yumiao)
- **解绑重新绑定逻辑简化** (`LightInveterDataServiceImpl.unbindAndReBindInverter`):
  - 旧逻辑: 复杂的分支处理(id有无/发电绑定有无/运维变更判断), 包含零碳适家电站禁止解绑的限制
  - 新逻辑: 统一流程 — 电站存在性校验 → 有id且有发电绑定则解绑 → 查找旧逆变器记录 → updateStationInverter → 创建新逆变器绑定
  - **删除的限制**: 移除了"零碳适家电站暂不支持解绑同时更换新逆变器"的硬编码限制
  - 简化后代码从 ~80行 减少到 ~35行
- **逆变器替换校验** (`LightInveterDataService`):
  - 新增 `validateInverterReplace` 方法
  - 新增新逆变器占用校验(inverterSnNotBindByStation)
- **CompleteConfirmService优化** (`CompleteConfirmServiceImpl`):
  - 逆变器序列号更新和解绑逻辑重构
  - 事务处理优化
  - 移除逆变器OCR验证相关代码(yumiao, 2025-12-24)
- **BOM与OCR一致性校验**: 2025-12-08 启用逆变器BOM与OCR数据一致性校验(majinhu)
- **单元测试**: 新增逆变器绑定功能单元测试(71行)

### GF 模式完工确认施工照片字段 (代码明确证明, 2026-05-18)
**来源**: `rrsjk-merchant-web` → `LightStationController.java` (commit 1ca6373da, wangxiran, 2026-05-18)

在完工确认缓存接口 (`completeConfirmCache.do`) 中，从 cache 对象向 result 返回新增 8 个 GF 模式专有施工照片字段：
| 字段 | 含义 | 对应施工阶段 |
|---|---|---|
| basicPhotoList | 基础照片 | 施工安全类 |
| bracketImgList | 支架照片 | 支架安装 |
| moduleImgList | 组件照片 | 组件安装 |
| inverterInstallImgList | 逆变器安装照片 | 逆变器安装 |
| gridTableImgList | 并网箱照片 | 并网箱安装 |
| wireImgList | 线缆照片 | 线缆类 |
| connectGroundImgList | 接地极照片 | 接地极 |
| waterproofImgList | 防水照片 | 防水措施 |

- 注释明确说明：非 GF 模式这些字段为 null/空 list，覆盖无影响
- 这些字段与广发模式过程进件（施工验收 CP_GZFZCP_200020_3750~4290）的编码体系对应
- **证据等级**: 代码明确证明

---

## 线下验收结合技术商务并行状态流转优化 (代码明确证明, 2026-05-20)
**来源**: `rrsjk-light-service` → `BusinessStatusMode.java` (commit: yumiao f4c1f22, 2026-05-19)
**需求**: TAEI-3044/TAEI-3087 【户用光伏】华融相关优化

- **参数变更**: `BusinessStatusMode.updateStationBusinessStatus()` 方法中 `offLineChoose` 参数从必传改为 `@Nullable`
- **业务语义**: 支持线下验收与技术/商务审核并行处理，不再强制要求线下验收选择
- **审核流程**: `CompleteConfirmServiceImpl.stationAudit()` 增加 `stationCode` 字段设置，确保审核更新时电站编码正确传递
- **状态流转影响**: 允许电站在技术审核和商务审核并行时独立推进状态，不阻塞于线下验收环节
- **关联枚举**: `LightStation.ModeEnum` 控制不同业务模式下的状态流转策略

---

## 电站新增屋顶类型和电网类型 (代码明确证明, 2026-01-19~2026-02-08 补漏第4期)
**来源**: `rrsjk-light-service` (解钦/商轶龙/于淼) + `nahui-dicts-serve` (李培龙)
**需求**: TAEI-2863 【建站】增加新的屋顶类型 + TAEI-2866 【建站】增加电网类型

- **屋顶类型**: LightStation.houseType 字段扩展，新增屋顶类型枚举值
  - 原有: `flat`(平顶屋), `slope`(斜屋顶)
  - 变更涉及多个 Station Mode 类: `BaseLightStationMode`, `LightHouseholdStationMode`, `LightOrdinaryStationMode`, `LightCorpStationMode`, `LightGovStationMode`, `LightSpicStationMode`, `LightWholeVillageStationMode`, `LightChdStationModel`, `LightCnnChnStationModel`, `LightDhStationMode`
  - 计划审核流程功能 (`e0ad9e0`, 解钦, 2026-01-22)
- **电网类型**: 新增电网类型配置，影响电站并网资料提交
- **数据字典**: `nahui-dicts-serve` 同步更新相关字典数据
- **变更影响**: 屋顶类型/房型变化在审核流程中标记为 `changeRoofOrHouseType`，影响技术/商务审核并行状态流转

## 运维APP新增"所属建站商"字段 (代码明确证明, 2026-01-19~2026-02-08)
**来源**: `pv.osp-uni` (李培龙, commits: 88f32f8, 8181b35, 2026-01-27~28)
**需求**: TAEI-2854 海尔绿能运维APP新增"所属建站商"字段

- UniApp 端电站信息新增 `建站商名称` 字段展示
- 修改角色名称、版本号更新等配套变更

## 逆变器相关优化 (代码明确证明, 2026-01-19~2026-02-08)
**来源**: `rrsjk-light-service` (于淼, commits: b388392, 9e17796, d3b4185 等)
**需求**: TAEI-2862 获取逆变器一级过压保护值和有功控制百分比值

- **逆变器功率处理**: 优化逆变器功率计算逻辑，修复设备功率提取问题 (cmbleasing)
- **逆变器数据查询**: 优化逆变器数据查询逻辑 (2 commits, 2026-02-02)
- **一级过压保护值**: 新增获取逆变器一级过压保护值和有功控制百分比值功能
- **关联服务**: `rrsjk-light-iot-service` 逆变器数据服务同步更新

## 超期申诉审核功能 (代码明确证明, 2026-01-19~2026-02-08)
**来源**: `nahui-pv.hds-h5` + `pv.osp-uni` + `nahui-pv.merchant-micro.osp` (李培龙, 2026-01-23~27)

- **HDS页面**: 超期申诉审核添加音频展示 (`184ce4f`, 2026-01-26)
- **音频功能**: 申诉审核支持音频上传、展示和播放
  - 设置音频类型、音频展示样式、音频格式支持
  - 商户端(`merchant-micro.osp`)添加音频播放和上传文件类型优化
- **审核按钮**: 超期申诉审核按钮校验恢复 (`0697d62`, 2026-01-27)
- **申诉描述**: 修复工单申诉审核申诉描述溢出问题 (`45c4f5d`, 2026-01-26)
- **审核备注**: 新增审核备注限制200字符 (`8bb4602`, 2026-01-27)

## 完工确认模块优化 (代码明确证明, 2026-01-19~2026-02-08)
**来源**: `rrsjk-light-service` (于淼, 20+ commits, 2026-01-23~2026-02-06)

- **模块序列号**: 优化模块序列号批量操作方法 (`1f11335`, 2026-02-02)
- **序列号批量删除**: 修复完工确认模块序列号批量删除保存逻辑 (`bddb5e7`, 2026-02-03)
- **参数验证**: 修复模块序列查询参数验证逻辑 (3 commits, 2026-02-02)
- **事务管理**: 移除完工确认服务中的冗余手动事务管理，优化事务控制
- **草稿码**: 修复草稿码生成时的空指针异常 (`800bf49`, 2026-01-31)
- **状态过滤**: 更新查询条件排除状态值5 (`c6e2019`, 2026-02-06)
- **数据库连接**: 添加数据库连接保活配置 (`7dcf51d`, `405cb2c`, 2026-01-26)
- **light_staging_records**: 修复表插入语句字段数量不匹配问题 (4 commits, 2026-01-26)

## 银联签约状态优化 (代码明确证明, 2026-01-29~2026-01-30)
**来源**: `rrsjk-light-service` (于淼, commits: b593e7f, 8cacf87, cb56e64)

- **签约状态**: 更新银联签约状态逻辑以应对暂停情况
- **重推功能**: 移除银联重推功能代码 (4 commits, refactor switch-light-mode)
- **用户数据导入**: 修复银联用户数据导入时间过滤问题 (`cb56e64`, 2026-01-30)

## 绿能分时发电量报表 (代码明确证明, 2026-01-19~2026-02-08)
**来源**: `he-vpp.admin-h5` (张硕文, commits: 12700f4, 65c7c61, 2026-02-02~02-04)
**需求**: TAEI-2856 【电力交易】四川报表管理 + TAEI-2844/2845 越秀/中核大屏

- **电力交易报表**: 新增电力交易报表页面 (`65c7c61`, 2026-02-04)
- **分时发电量**: 绿能分时发电量报表 (`12700f4`, 2026-02-02)
- **查询优化**: 销售订单、意向管理、采购管理查询优化 (`51c3ee4`, 2026-01-29)
- **回款管理**: 回款管理增加手动开票功能 (`6c927e8`, 2026-01-21)

### 华融质保金防御性校验 (代码明确证明, 2026-05-18~19)
**来源**: `rrsjk-light-service` → HuaRongIncomeQualityGuaranteeServiceImpl.java, HrflcEpcStationMode.java, HrflcFirstProjectJobServiceImpl.java, HrflcSecondProjectJobServiceImpl.java (commits cb67fb3/98f808b/23846b5/08debe1, yumiao, 2026-05-18~19)
- **防御性校验新增**: 华融收入质保金定时任务(`HuaRongIncomeQualityGuaranteeServiceImpl`) 增加三重校验：
  1. 检查电站是否已有记账凭证(`voucher`)，已有则跳过（防止重复记账）
  2. 检查华融收入结算数据是否存在，不存在则跳过
  3. 检查华融收入结算数据是否已记账(`voucher`非空)，未记账则跳过（必须先记收入再记质保金）
- **精度修复**: `BigDecimal.ROUND_HALF_UP` → `RoundingMode.HALF_UP`（弃用旧API）
- **异常日志**: 堆栈信息改为只记录 `e.getMessage()`，避免日志过长
- **变量命名**: `entity` → `existsHrflcywmlB43`，`incomeSettle` → `existsHrflcywmlA55`（HRFLC业务命名规范）
- **证据等级**: 代码明确证明

### 线下验收+技术商务并行状态流转优化 (代码明确证明, 2026-05-19)
**来源**: `rrsjk-light-service` → CompleteConfirmServiceImpl.java, BusinessStatusMode.java (commits f4c1f22/759697e, yumiao, 2026-05-19)
- **业务变更**: 优化线下验收结合技术商务并行的电站状态流转
- `CompleteConfirmServiceImpl`: 完工确认服务新增/修改1行，支持线下验收流程
- `BusinessStatusMode`: 业务状态枚举变更1个值，支持技术商务并行
- **证据等级**: 代码明确证明

### 组件编码与电站型号一致性校验 (TAEI-2869, 2026-02-25 代码明确证明)
**来源**: `rrsjk-light-service` → `LightModuleSnServiceImpl.java` (commit 24c8a5b6, 解钦)
- 提交电站组件编码(SN)时，校验组件编码对应的物料号与新方案组件物料号是否匹配
- 校验逻辑: `lightComponentLibrary.getSkuCode().equals(planConfigList.getSku())`
- 不匹配时抛出: `"您提交的电站组件编码对应的型号{snCode}与电站不一致，请核实后提交"`
- **证据等级**: 代码明确证明

### 电站方案变更 — 新旧区域映射校验 (2026-02-25 代码明确证明)
**来源**: `rrsjk-light-service` → `LightStationChangeOperationServiceImpl.java`, `NewOldRegionDto.java` (commit 1cc0b4e2, sunzn)
- 电站变更时校验新旧区域是否在已知映射中，存储在Redis（key: `new_region_id_old_region_id`）
- 接口: `addNewOldAreaToRedis(oldRegionId, newRegionId)` — 添加新旧区域映射
- 不在映射中的区域变更会被拦截
- **证据等级**: 代码明确证明

### 社会化电站导入优化 (2026-02-09~11 代码明确证明)
**来源**: `rrsjk-hds-web` → `SocializationStationController.java` (commits 73d07853/c357fbfe 等, sunzn)
- 必填字段校验: 省市区地址、电站容量、运维承接/结束时间、合同编号、委托方全称
- 格式校验: 手机号、身份证格式
- ZIP文件中文编码兼容修复
- 枚举更新: `rrsjk-light-operation-service` 更新社会化电站实体枚举值
- 合同年限字段类型修改
- **证据等级**: 代码明确证明

### 资产所属分类 — SpecialFlag 生成 (2026-02-09 代码明确证明)
**来源**: `rrsjk-light-service` → `LightStation.java` (commit 60ea94de, 解钦)
- `SpecialFlagEnum.generateSpecialFlagOptions()` 生成CBS可用的资产所属分类
- 按 name 分组枚举值，过滤 NOT_DIS
- LightStation.xml 新增 `specialFlagList` 多值IN查询 + `firstThreePowerAtStart/End` 功率范围查询
- **证据等级**: 代码明确证明

### 工单申诉 — 超期状态重置修复 (2026-02-10 代码明确证明)
**来源**: `rrsjk-light-operation-service` → `LightOperationWorkOrderServiceImpl.java` (commit c85550eb, sunzn)
- 申诉审核通过时同步重置 `workOrder.setOverTime(false)`
- **证据等级**: 代码明确证明

### 房产证OCR识别 (TAEI-2728, 2026-05-18~20 代码明确证明)
**来源**: `rrsjk-light-service` → `LightStationHouseCertificateOcr.java` (rrsjk-light-api), `LightStationHouseCertificateOcrServiceImpl.java` (commit ee04e9fa73, mabin), `AcceptanceConfirmServiceImpl.java`
- **触发时机**: 并网确认 (`gridConfirm`) 和电站影像修改 (`modifyStationImg`) 时自动调用
- **新表**: `light_station_house_certificate_ocr` (MyBatis XML 243行)
- **Dubbo服务**: `LightStationHouseCertificateOcrService` (service.xml line 808)
- **OCR流程**:
  1. `createData()`: 创建记录, ocrStatus=`running` (AliStatusEnum)
  2. `alibabaApi.houseCertificateOcr()`: 调用阿里云大模型API识别房产证
  3. 成功: ocrStatus=`success`, 解析 JSON 提取 name/id/add 字段
  4. 失败: ocrStatus=`failed`, 记录错误信息
- **去重机制**: `checkIfExist(stationCode, houseUrl, userName, idNo, address)` 按5个字段组合去重
- **实体字段**: stationCode, houseCertificateUrl, ocrStatus, ocrResult(JSON), sourceStationName/ocrStationName, sourceIdNo/ocrIdNo, sourceAddress/ocrAddress
- **配套变更**: admin-web 添加房产证AI识别页面、图片验真优化、OSS图片查看器压缩加速
- **分支**: `origin/20260518-fangchanzhengOCR`, `origin/20260520-fix`
- **证据等级**: 代码明确证明

### 并网节点 — 220KV变电站名称字段 (TAEI-2880, 2026-03-04~12 代码明确证明)
**来源**: `rrsjk-light-service` (wangxiran, 6 commits), `rrsjk-admin-web` (wangxiran, 4 commits)
**关联需求**: TAEI-2880 (建站并网节点增加字段：220KV变电站名称)

- **后端字段**: `LightStation` / `LightStationConfirmDto` / `AcceptanceConfirmService` 新增 `substation220kvName` (220KV变电站名称) 字段
  - 实体: `LightStation.java` 添加字段 (wangxiran, commit 179f4d9, 2026-03-04)
  - DTO: `LightStationConfirmDto` 添加字段 (wangxiran, commit 1b09eba, 2026-03-04)
  - 验收服务: `AcceptanceConfirmService` 添加字段到验收确认 (wangxiran, commits 03a53cd/31790b3, 2026-03-04)
  - 长度校验: 220KV变电站名称长度校验 (wangxiran, commits 3813bdc/54772db, 2026-03-06)
- **前端显示**: 电站详情页面显示220KV变电站名称 (wangxiran, commits 1b84d09/1903d2f/445027e, 2026-03-04~12)
- **报表**: 工商业电站并网统计功能新增 (wangxiran, commit 079bb0e, 2026-03-10)
- **证据等级**: 代码明确证明

### 发电户号变更优化 (TAEI-2879, 2026-03-02~09 代码明确证明)
**来源**: `rrsjk-light-service` (yumiao, 4 commits)
**关联需求**: TAEI-2879 (建站发电户号变更优化)

- 并网资料提交事务优化: 去掉不必要的事务包裹 (yumiao, commits 9b1dd31/df26f5e, 2026-03-05~06)
- 上传过并网资料传参问题修复 (yumiao, commit 05d063a, 2026-03-09)
- 完工审核通过后赋值商务审核状态为"待提交并网资料" (yumiao, commit fe3e60a, 2026-03-02)
- **证据等级**: 代码明确证明

### 电站状态字典扩展 (前端配置证明, 2026-05-22 扫描)
**来源**: `nahui-dicts-serve` → `src/data/apv/station/` (2026-03~2026-05, 袁睿林/杨辉)
- 新增电站状态"待三方审核"（`statusList.js`）
- 新增备案类型（`beiAnType.js`）、项目类型（`proTypeList.js`）
- 新增合同类型扩展：广发主合同、华融EPC业主主合同（`contractTypeList.js`）
- 新增华融EPC合同类型（`contractTypeList.js`, 李培龙, 2026-04-27）
- 安装方式字典大更新（`installList.js`, 310行）
- 新增配送列表（`distributionList.js`）

