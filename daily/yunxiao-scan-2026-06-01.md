# 云效驱动代码学习报告 — 2026-06-01

## 扫描范围
- **云效需求**: 20 个 (updateStatusAt >= 2026-05-25，分页1/2，共30条)
- **涉及人员**: 代继宁、王斌、解钦、杨辉、李龙、马斌、魏秋阳、王希然、孙志男、于淼、马金虎、王金浩(laowang)、陈国栋、姜传德、商轶龙、包鑫、高媛、徐晓凤、张硕文、袁睿林、杨越越、刘艺、薛荣基
- **Git 提交**: 801 个 (2026-05-25 ~ 2026-06-01)
- **活跃仓库 TOP10**: rrsjk-admin-bff (297), rrsjk-admin-web-next (133), rrsjk-light-service (70+), rrsjk-async-import-export (26), rrsjk-admin-web (72), rrsjk-light-data-service (19), rrsjk-hds-web (12), rrsjk-finance-service (9), he-vpp.admin-h5 (10), rrsjk-merchant-web (6)

## 需求 → 代码关联

| 需求号 | 标题 | 负责人 | 参与人 | 状态 | 相关提交 | 涉及仓库 |
|---|---|---|---|---|---|---|
| TAEI-3092 | 【租金】农户租金类个税报表及记账 | 杨越越 | 代继宁, 薛荣基 | 测试中 | 18+ | rrsjk-light-service, rrsjk-admin-web, branch: featrue-20260525-rentTaxReport/TAEI-3092 |
| TAEI-3129 | 【仓储】商户通入库管理导出物流信息 | 徐晓凤 | 王希然, 袁睿林 | 开发中 | BFF层新增 | rrsjk-admin-bff |
| TAEI-3159 | 【工商业】放开产值确认法的收入闸口 | 杨越越 | 王斌 | 已完成 | 1 | rrsjk-light-service (CmProductionValueIncomeServiceImpl) |
| TAEI-3107 | 【风电】风电产值法兼容1.0 | 杨越越 | 王斌, 解钦, 杨辉, 薛荣基 | 已完成 | 18+ | rrsjk-light-service, rrsjk-admin-web, branch: feature-cm-wind-electric |
| TAEI-3101 | 【户用光伏】招银组件功率匹配价格 | 刘艺 | 薛荣基, 李龙 | 已完成 | 1 | rrsjk-admin-web (yumiao代提交) |
| TAEI-3084 | 【户用光伏】中银租后接口对接 | 刘艺 | 薛荣基, 马斌 | 已完成 | - | 本周无提交 |
| TAEI-3123 | 【建站】完工后方案变更验收驳回 | 徐晓凤 | 魏秋阳, 王希然, 薛荣基 | 已完成 | BFF层 | rrsjk-admin-bff |
| TAEI-3163 | 项目公司股转后A51/A48账单处理 | 高媛 | 魏秋阳, 孙志男 | 已完成 | BFF+admin-web | rrsjk-admin-bff, rrsjk-admin-web |
| TAEI-3044 | 【户用光伏】华融上收入多1个账B43 | 刘艺 | 于淼, 薛荣基 | 已完成 | - | 本周无提交（早前完成） |
| TAEI-3102 | 【户用光伏】CBS招投标流程 | 刘艺 | 魏秋阳, 薛荣基, 王金浩 | 测试中 | 23+ | rrsjk-light-service, rrsjk-admin-web, branch: 20260515-wjh-toubiaogl |
| TAEI-3145 | 商务验收页面跳转逆变器详情速度优化 | 于淼 | 马金虎 | 已完成 | BFF层 | rrsjk-admin-bff, rrsjk-admin-web-next |
| TAEI-3141 | 优化电站连续三天发电刷新逻辑 | 于淼 | 马金虎 | 已完成 | 2 | rrsjk-light-data-service, branch: 20260525-santianfadian |
| TAEI-3157 | 金蝶冲销接口优化 | 马斌 | 薛荣基, 马斌 | 开发中 | 8+ | rrsjk-finance-service, rrsjk-light-service, branch: 20250525-jindieRepeatFix, 20260527-jindieFix |
| TAEI-3070 | 【户用光伏】招银接口6.5故障 6.6工单 6.7租金 | 刘艺 | 薛荣基, 马斌 | 开发中 | - | 本周无提交 |
| TAEI-2728 | 【AI】AI识别房产证 | 杨越越 | 魏秋阳, 陈国栋, 马斌 | 测试完成 | 2 | rrsjk-light-service, rrsjk-admin-web, branch: 20260518-fangchanzhengOCR |
| TAEI-3130 | 【建站】技术部巡检需求 | 徐晓凤 | 王金浩 | 开发中 | - | 本周无代码提交 |
| TAEI-3082 | 【仓储】调拨入库展示仓库名称 | 徐晓凤 | 薛荣基, 王希然, 袁睿林 | 开发中 | - | 本周无提交 |
| TAEI-3057 | 【建站】审核驳回支持按单张图片驳回 | 徐晓凤 | 杨辉, 王希然, 薛荣基, 张硕文 | 开发中 | 7+ (前端) | rrsjk-admin-web (wangxiran), branch: feature-wxr-20260521-audit |
| TAEI-3146 | 发电数据取数逻辑切换大数据平台 | 于淼 | 于淼, 马金虎 | 开发中 | 9 | rrsjk-light-data-service, branch: feature/202605/ods_electroc_data |
| TAEI-3053 | 【建站】一商做全国 | 杨越越 | 于淼, 姜传德, 解钦, 商轶龙, 袁睿林, 包鑫 | 测试完成 | 转单相关 | rrsjk-light-service (德), rrsjk-async-import-export (解钦) |

## 业务链分析

### 1. TAEI-3159 + TAEI-3107: 工商业风电产值收入法（重大影响）
**仓库**: rrsjk-light-service, rrsjk-admin-web
**开发者**: 王斌(tn_wangb), 解钦
**关键变更**:
- **TAEI-3159 收入闸口放开**: `CmProductionValueIncomeServiceImpl` 注释掉三项收入金额校验（材料收入/施工服务收入/设计收入超限检查），只保留成本超限检查
- **TAEI-3107 风电产值法**: 20+ commits 大量实现，涉及 `CmGvsServiceImpl`, `CmLightUseServiceImpl`, `CmConstructionProgressAuditServiceImpl`
- **字段解耦**: 将主料/辅料/施工服务/设计服务的专用进度字段统一为 `nodeFinishPct`
- **终验法**: admin-web 新增终验法相关页面和接口
- **分支**: `origin/feature-cm-wind-electric`
- **知识库更新**: `domains/cm-business.md` ✅ (已有)

### 2. TAEI-3157: 金蝶冲销接口优化
**仓库**: rrsjk-finance-service, rrsjk-light-service
**开发者**: 马斌(mabin), 孙志男(sunzn)
**关键变更**:
- **凭证过账功能**: 冲销前先调用金蝶凭证过账接口 (`postingVoucherForReverse`)，过账成功才执行冲销
- **新增接口**: `/xfd6/gl/gl_voucher/PostingVoucher`
- **错误处理增强**: 消息长度限制防溢出、重复校验修复、BUKRS映射修复(7CQ0→9002)、异常处理优化
- **关联变更**: rrsjk-light-service 放开发票金蝶冲销、修复冲销状态判断
- **分支**: `origin/20250525-jindieRepeatFix`, `origin/20260527-jindieFix`
- **知识库更新**: `domains/kingdie-sap-dual-architecture.md` ✅ (新增)

### 3. TAEI-3102: CBS招投标流程迭代
**仓库**: rrsjk-light-service, rrsjk-admin-web
**开发者**: 王金浩(laowang)
**关键变更**:
- **价值链审核回传材料**: 新增 `vcatmAuditDetail` 字段
- **审核备注**: 各阶段新增审核备注字段（107行新增）
- **待提交状态修复**: 修复WAIT状态误生成审核日志
- **前端弹窗**: 15+ commits 修复弹窗高度/滚动/尺寸问题
- **知识库更新**: `domains/cbs-management.md` ✅ (新增迭代详情)

### 4. TAEI-3092: 农户租金个税报表及记账
**仓库**: rrsjk-light-service, rrsjk-admin-web
**开发者**: 代继宁
**关键变更**:
- **SAP记账接口**: 多次迭代（更新→Revert→再更新），记账成功后错误信息置空
- **批量确认优化**: 中间表分批处理，统计逻辑优化
- **定时任务**: 执行月份计算公式优化
- **分支**: `origin/featrue-20260525-rentTaxReport/TAEI-3092`
- **知识库更新**: `domains/settlement.md` ✅ (已有+补充)

### 5. TAEI-3146 + TAEI-3141: 发电数据 ADS 迁移 + 三天发电优化
**仓库**: rrsjk-light-data-service
**开发者**: 马金虎(majinhu), 于淼(yumiao)
**关键变更**:
- **ADS数据源**: 新增独立 ADS 数据源 + `AbstractAdsDao` 基类
- **5张ADS报表表**: 替换原DWS层逆变器图表查询（无id字段）
- **电站报表迁移**: `AdsLightStationElec` → `DwsLightStationElec` + 4个ADS报表服务
- **三天发电优化**: `isContinueThreeDayElec` 定时任务重构，去掉线程池逐条查询
- **字段修正**: `inveter_sn` → `inverter_sn` 拼写修正
- **分支**: `origin/feature/202605/ods_electroc_data`, `origin/20260525-santianfadian`
- **知识库更新**: `domains/inverter-data.md` ✅ (已有)

### 6. TAEI-3057: 审核驳回支持按单张图片驳回
**仓库**: rrsjk-light-service, rrsjk-admin-web
**开发者**: 王希然(wangxiran)
**关键变更**:
- **后端**: `AuditImageRejectDto` 新增 rejectFlag/targetName/targetUrl，`LightAuditImageRejectServiceImpl` 扩展现场图片类型
- **前端**: rrsjk-admin-web 7+ commits 单图驳回面板、拖拽功能、样式修复
- **变更方案驳回**: 支持驳回到方案审核 (CHECK_REJECT/TECH_AUDIT_REJECT)
- **分支**: `origin/feature-wxr-audit-20260519`, `origin/feature-wxr-20260521-audit`
- **知识库更新**: `domains/approval.md` ✅ (已有)

### 7. TAEI-2728: AI识别房产证
**仓库**: rrsjk-light-service, rrsjk-admin-web
**开发者**: 马斌(mabin)
**关键变更**:
- **生产URL配置**: `LightUseModel.java` 新增房产证OCR识别生产URL
- **前端**: 修复房产证状态图片显示问题
- **分支**: `origin/20260518-fangchanzhengOCR`
- **知识库更新**: `domains/ai-extraction-services.md` ✅ (新增)

### 8. rrsjk-admin-bff 大规模活跃（非业务逻辑变更）
- yumiao 贡献 297 commits，覆盖 pv-settlement(30+ endpoint)、warehouse、reconciliation、huadian、fund-settlement 等模块
- **⚠️ BFF层变更不是业务逻辑变更**: 这些都是薄REST Controller + Dubbo Client代理，真正业务逻辑在底层 Dubbo 服务中
- 新增 endpoint 包括: warehouse transfer/confirm/auxiliary、offline acceptance、unionpay rent deduction、high voltage ammeter、zhongyin-trade income reverse 等
- **处理方式**: 仅记录，不深入分析（按 skill 规定追踪到 Dubbo 层）

## 知识库更新

| 操作 | 文件 | 内容摘要 |
|---|---|---|
| 追加 | `domains/kingdie-sap-dual-architecture.md` | TAEI-3157 金蝶凭证过账功能（冲销前过账、错误处理增强、关联变更） |
| 追加 | `domains/cbs-management.md` | TAEI-3102 CBS招投标最新迭代（回传材料、审核备注、待提交修复、前端弹窗、放开销方校验） |
| 追加 | `domains/settlement.md` | TAEI-3092 租金个税补充（批量任务统计优化、定时任务月份计算、SQL修复） |
| 追加 | `domains/ai-extraction-services.md` | TAEI-2728 AI房产证OCR识别（生产URL配置、前端图片显示修复） |

## 新发现

### Git Author 别名确认
- **laowang 身份确认**: `laowang` (1162359451@qq.com) = 王金浩，分支名 `origin/20260515-wjh-toubiaogl` 中 `wjh` = 王金浩拼音首字母
- **分支名直接暴露需求号**: `origin/feature/TAEI-3150_大商政策监控报表1.5期优化`、`origin/featrue-20260525-rentTaxReport/TAEI-3092` 等

### PM 无提交模式确认
- **刘艺** (TAEI-3101/3102/3044/3070 负责人): 零Git提交，开发由参与人(李龙/王金浩/于淼/马斌)执行
- **杨越越** (TAEI-3159/3107/2728/3053 负责人): 零Git提交，开发由参与人(王斌/解钦/马斌等)执行
- **徐晓凤** (TAEI-3129/3123/3130/3082/3057 负责人): 零Git提交，开发由参与人(王希然/魏秋阳/杨辉等)执行
- **高媛** (TAEI-3163 负责人): 零Git提交，开发由参与人(孙志男/魏秋阳)执行

### 跨仓库架构变更模式
- **TAEI-3157 金蝶冲销**: `rrsjk-finance-service` 新增过账功能 → `rrsjk-light-service` 放开发票金蝶冲销 → `CmChangeServiceImpl` 修复冲销状态判断
- **TAEI-3146 ADS迁移**: `rrsjk-light-data-service` 创建ADS数据源 → `rrsjk-admin-web` 新增ADS查询接口 → `rrsjk-admin-web-next` 新增前端页面

## BFF 层变更汇总（2026-05-25~30）
| 模块 | 新增 Endpoint | 说明 |
|---|---|---|
| warehouse | 10+ | 仓储调拨/确认/辅助采购/第三方库存/材料包等 |
| pv-settlement | 30+ | 结算相关（已在之前扫描中记录） |
| station | 5+ | 离线验收/逆变器详情/图片驳回等 |
| zhongyin-trade | 1 | 中银交易收入反查 |
| unionpay | 1 | 银联租金扣款 |
| fund-settlement | 若干 | 资金结算 |
| reconciliation | 若干 | 对账 |

> ⚠️ 以上 BFF 层变更均为 REST Controller + Dubbo Client 代理，业务逻辑在底层 Dubbo 服务（rrsjk-light-service 等）中。
