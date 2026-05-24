# 云效驱动代码学习补漏报告 — 第8期 (2026-04-13 ~ 2026-04-27)

## 扫描范围
- **云效需求**: 41 个 (createdAfter=2026-04-13, createdBefore=2026-04-27)
- **涉及人员**: 20+ (有Git提交: 14人: sunzn/代继宁/yumiao/tn_wangb/龙龙/德/majinhu/解钦/baoxin/laowang/wangxiran/dengqiu/mabin/张硕文/李培龙)
- **Git 提交**: 981 个 (2026-04-13 ~ 2026-04-27)
- **涉及仓库**: 16+ (rrsjk-light-service 446, rrsjk-admin-web 233, rrsjk-finance-service 75, rrsjk-merchant-web 59, rrsjk-trade-service 29, rrsjk-hds-web 26, rrsjk-light-data-service 23, rrsjk-light-operation-service 22, rrsjk-light-report-service 14)

## 需求 → 代码关联

| 需求号 | 标题 | 状态 | 负责人 | 参与人(开发) | 相关提交 | 涉及仓库 |
|---|---|---|---|---|---|---|
| TAEI-2990 | 【股转】乐道、统众增加租金支付明细 | 已完成 | 杨越越 | 王斌 | ~20 | rrsjk-admin-web |
| TAEI-2992 | 【越秀】2026年保险推送 | 已完成 | 杨越越 | 于淼 | ~30 | rrsjk-admin-web, rrsjk-light-service |
| TAEI-2993 | 【合同】服务商合同更新 | 已完成 | 杨越越 | 包鑫 | ~5 | rrsjk-admin-web, rrsjk-light-service |
| TAEI-2994 | 电站业主银行卡信息变更管理 | 已完成 | 高媛 | 孙志男,魏秋阳,李培龙 | ~20 | rrsjk-light-service, rrsjk-admin-web |
| TAEI-2995 | 【政策】辅材政策切换为辅材额度 | 已完成 | 杨越越 | 于淼,王斌,包鑫,解钦等 | ~40 | rrsjk-light-service, rrsjk-admin-web, rrsjk-finance-service |
| TAEI-2996 | 解决上能逆变器数据延迟 | 已完成 | 于淼 | 马金虎 | ~3 | rrsjk-light-data-service |
| TAEI-3002 | 【质保金】质保金审批流变动 | 已完成 | 徐晓凤 | 王斌,张硕文 | ~5 | rrsjk-finance-service, rrsjk-admin-web |
| TAEI-3003 | 【建站】电站状态名称优化、方案驳回暂存 | 已完成 | 徐晓凤 | 杨辉,王希然,张硕文,付凯善,姜廷 | ~15 | rrsjk-admin-web, nahui-pv.hds-h5 |
| TAEI-3005 | 【股转】金蝶总账接口开发 | 待测试 | 杨越越 | 马斌,包鑫,商轶龙 | ~10 | rrsjk-light-service, rrsjk-finance-service |
| TAEI-3007 | 【合同】业主合同更新(共建+非共建) | 已完成 | 杨越越 | 包鑫 | ~5 | rrsjk-light-service, rrsjk-admin-web |
| TAEI-3008 | 【资方】华融EPC流程搭建 | 已完成 | 杨越越 | 姜传德,杨辉,马斌,李培龙等 | ~40 | rrsjk-light-service, rrsjk-admin-web |
| TAEI-3015 | 已终止工商业电站运维承接更正 | 已完成 | 高媛 | 孙志男 | ~2 | rrsjk-light-service |
| TAEI-3016 | 【户用光伏】广发过程进件-附件改造 | 已完成 | 刘艺 | 马金虎,王金浩,付凯善,袁睿林 | ~15 | rrsjk-light-service, rrsjk-admin-web |
| TAEI-3017 | 【户用光伏】广发过程进件-审核、进件 | 已完成 | 刘艺 | 马金虎,王希然,王金浩,袁睿林 | ~10 | rrsjk-light-service |
| TAEI-3018 | 【户用光伏】广发主合同签署/落章/作废 | 已完成 | 刘艺 | 于淼,马金虎,付凯善,袁睿林 | ~10 | rrsjk-light-service |
| TAEI-3025 | 【户用光伏】BT报表项目 | 测试中 | 刘艺 | 于淼,包鑫,李龙 | ~5 | rrsjk-light-service, rrsjk-admin-web |
| TAEI-3033 | 【建站】发电户号变更优化 | 已完成 | 徐晓凤 | 王金浩 | ~3 | rrsjk-light-service |
| TAEI-3034 | 【智光宝】施工队小程序新增照片节点 | 已完成 | 徐晓凤 | 张硕文,王金浩,付凯善 | ~5 | rrsjk-admin-web, nahui-pv.construction-mini |
| TAEI-3035 | 【政策】CBS增加领用/成本记账时间 | 已完成 | 杨越越 | 商轶龙,魏秋阳 | ~5 | rrsjk-light-service, rrsjk-admin-web |
| TAEI-3036 | 【电站】APP商户通电站列表优化 | 已完成 | 徐晓凤 | 姜廷,王希然,张硕文,付凯善 | ~10 | nahui-pv.hds-h5, nahui-pv.greenenergy-mini |
| TAEI-3040 | 超期申诉功能优化&运维政策兑现优化 | 已完成 | 高媛 | 孙志男,魏秋阳,李培龙 | ~15 | rrsjk-light-service, nahui-pv.hds-h5 |
| TAEI-3041 | 【报表】成本核算报表优化 | 已完成 | 杨越越 | 解钦 | ~10 | rrsjk-admin-web, rrsjk-light-service |
| TAEI-3042 | 【政策】大商政策暂估及兑现监控报表 | 已完成 | 杨越越 | 商轶龙 | ~10 | rrsjk-light-service, rrsjk-admin-web |
| TAEI-3043 | 【工商业】自持电站损益报表 | 已完成 | 徐晓凤 | 王斌 | ~10 | rrsjk-admin-web, rrsjk-light-service |
| TAEI-3046 | 【户用光伏】广发合规进件附件增加 | 已完成 | 刘艺 | 马金虎,付凯善,袁睿林 | ~5 | rrsjk-light-service |
| TAEI-3053 | 【建站】一商做全国 | 测试中 | 杨越越 | 于淼,姜传德,解钦,商轶龙,袁睿林,包鑫 | ~50 | cbs-web, rrsjk-admin-web, rrsjk-light-service |

## 重点业务链分析

### 1. TAEI-2995: 辅材政策切换为辅材额度 (大, 紧急)
**业务变更**: 从辅材押金模式切换为辅材额度模式，涉及流水类型重命名、额度管理逻辑变更
- **辅材额度流水重命名**: S7(下单冻结) → S8，涉及 LightAuxiliaryMaterialDepositFlowServiceImpl
- **新增额度查询接口**: `AuxiliaryMaterialCreditLimitDto` 包含总额/可用/冻结/核销四项
- **pendingWrittenOffAmount 逻辑变更**: S11签收和D13核销时不再更新该字段（代码注释掉）
- **新增快照逻辑**: snapshotAfterFreeze, snapshotAfterRelease 用于额度变更追溯
- **涉及文件**: `LightAuxiliaryMaterialDepositFlowService`, `LightServiceProviderService`, `AuxiliaryMaterialCreditLimitDto`
- **前端**: rrsjk-admin-web 新增辅材额度流水管理页面（于淼, 包鑫）

### 2. TAEI-2994: 电站业主银行卡信息变更管理
**业务变更**: 新增电站业主银行卡变更申请、初审、终审完整流程
- **后端实体**: `LightStationBankCardChange` (230行) + `LightBankChangeDto` (128行)
- **Service**: `LightStationBankCardChangeServiceImpl` (360行) — 申请/初审/终审/取消/查询
- **Mapper XML**: 531行，覆盖所有CRUD操作
- **工单集成**: 银行卡变更关联工单系统，状态联动
- **OCR集成**: 银行卡图片OCR识别
- **前端**: rrsjk-admin-web operationbank 模块 (孙志男, ~15 commits)
- **关联字典**: bankInfoStatus.js, bankBentPaymentMode.js, bankFieldMethod.js

### 3. TAEI-3008: 华融EPC流程搭建 (大)
**业务变更**: 华融EPC模式电站进件全流程
- **新增策略类**: `HrflcEpcStationHandleStrategy` — 华融EPC电站处理策略
- **新增 DAO**: `HrflcSyncPvInfoDao`, `HrflcPvPriceConfigDao` — 华融PV信息同步和价格配置
- **Token服务**: 华融云Token刷新机制重构 (多个 commit)
- **进件信息处理**: `AbstractStationHandleStrategy` 新增 fillOutPvInfo 方法
- **审核业主**: 新增华融审核业主响应DTO和服务接口
- **前端**: rrsjk-admin-web hrflc 模块 (姜传德/德)

### 4. TAEI-3005: 金蝶总账接口开发
**业务变更**: 股转公司收入记账区分乐道/统众/其他，非乐道非统众走金蝶SAP
- **核心逻辑**: `LightProjectElectricOrderServiceImpl.confirmIncome()` 增加公司类型判断
  - 乐道/统众 → 不改SAP，只改状态为 WAIT_SAP
  - 其他股转公司 → 调 `jinDieSapRecordService` 传金蝶
- **新增服务**: `JinDieSapRecordService` (Dubbo接口) + `KingDieSapRecord` 实体
- **配置文件**: service.xml 新增 Dubbo reference

### 5. TAEI-3016/3017/3018: 广发系列进件
**业务变更**: 广发银行过程进件、审核、合同签署全链路
- **过程进件**: 列表查询、推送处理、附件改造
- **合同相关**: 广发合同信息查询、状态枚举、项目公司合同签章
- **新增字段**: xml电站合并相关字段
- **开发者**: 马金虎 (majinhu), ~35 commits

### 6. TAEI-3035: CBS领用/成本记账时间
**业务变更**: CBS安装及并网、营销、超期考核和新商界面增加领用时间和成本记账时间展示
- **新增字段**: `voucherAt` (领用时间), `costVoucherAt` (成本记账时间)
- **填充逻辑**: 所有填充点自动回填时间
- **前端**: CBS列表页和Excel导出新增两列
- **开发者**: 商轶龙(德baoxin商轶龙), 龙龙

### 7. 光伏年度规模阶梯奖励政策 (TAEI-2989 延续)
- **第二期**: 月度暂估自动核算，新增三个表全套代码
- **第三期**: 实际兑现+冲销+采购单+报表
- **开发者**: 龙龙 (tn_wangb龙龙), ~70 commits

## 知识库更新
| 操作 | 文件 | 内容摘要 |
|---|---|---|
| 更新 | domains/settlement.md | 业主银行卡变更管理补充后端实现详情 |
| 新增 | domains/settlement.md | 统众乐道租金支付管理 (TAEI-2990) |
| 新增 | domains/settlement.md | 辅材额度新增页面 + S7→S8重命名详情 (TAEI-2995) |
| 新增 | domains/cbs-management.md | CBS领用/成本记账时间字段 (TAEI-3035) |

## 未找到Git提交的需求/人员
- 徐晓凤 (TAEI-2997/2998/3000/3001/3002等负责人): 0 commits — 前端需求，代码由参与人提交
- 王金浩: 0 commits — 可能使用其他 author 名
- 杨辉: 0 commits — 可能使用其他 author 名
- 付凯善: 0 commits — 可能使用其他 author 名
- 魏秋阳: 0 commits — 可能使用其他 author 名
- 姜廷: 0 commits — 可能使用其他 author 名
- 董学强: 0 commits — 可能使用其他 author 名
- 袁睿林: 0 commits — 可能使用其他 author 名
