# 云效驱动代码学习报告 — 2026-05-10 ~ 2026-05-17

**扫描时间**: 2026-05-17
**扫描范围**: updateStatusAt >= 2026-05-10 的所有云效需求

## 扫描统计

| 指标 | 数值 |
|---|---|
| 云效需求 | 30 个 |
| 涉及开发人员 | 10+ 人 |
| 识别相关提交 | 100+ 个 |
| 知识库更新文件 | 3 个 |

## 需求 → 代码关联

| 需求号 | 标题 | 负责人 | 开发 | 状态 | 相关仓库 |
|---|---|---|---|---|---|
| TAEI-3101 | 招银组件功率匹配价格 | 刘艺 | 李龙 | 开发中 | rrsjk-light-service |
| TAEI-3100 | 自持电站报表优化 | 徐晓凤 | 徐晓凤+王斌+薛荣基 | 开发中 | rrsjk-light-report-service |
| TAEI-3098 | 图片验真唯一码重复检查 | 于淼 | 马斌 | 已完成 | rrsjk-light-service |
| TAEI-3095 | 业主合同去掉质押类条款 | 杨越越 | 包鑫 | 已完成 | rrsjk-light-service |
| TAEI-3089 | A端政策结算逻辑调整 | 杨越越 | 商轶龙 | 开发中 | rrsjk-light-service |
| TAEI-3088 | 云南能源局合同扩展区域 | 杨越越 | 包鑫 | 已完成 | rrsjk-light-service |
| TAEI-3087 | 国电投账号 | 杨越越 | 于淼+王希然 | 测试完成 | 多个 |
| TAEI-3086 | HDS/商户通/APP共享支付账单查询 | 高媛 | 孙志男 | 已完成 | 移动端+后端 |
| TAEI-3085 | 增加上收限制 | 杨越越 | 解钦 | 测试中 | rrsjk-light-service, rrsjk-admin-web |
| TAEI-3084 | 中银租后接口对接 | 刘艺 | 马斌 | 开发中 | rrsjk-light-service |
| TAEI-3081 | 完工节点增加字段 | 杨越越 | 徐晓凤 | 已完成 | rrsjk-light-service |
| TAEI-3078 | 派单3.1优化 | 杨越越 | 解钦 | 已完成 | rrsjk-light-service, rrsjk-admin-web |
| TAEI-3076 | 政策传SAP记账带电站编码和订单号 | 杨越越 | 解钦+商轶龙 | 已完成 | rrsjk-finance-service |
| TAEI-3074 | 商机管理支持页面弃置流程 | 刘艺 | 付凯善+马金虎 | 已完成 | rrsjk-light-service |
| TAEI-3073 | 广发并网进件-附件改造 | 刘艺 | 付凯善+马金虎 | 开发中 | 多个 |
| TAEI-3063 | 广发过程进件-APP附件改造 | 刘艺 | 付凯善 | 已完成 | 移动端 |
| TAEI-3062 | 审核派单闭环率报表优化 | 杨越越 | 徐晓凤 | 已完成 | rrsjk-light-report-service |
| TAEI-3061 | 己完工电站方案变更逻辑优化 | 杨越越 | 徐晓凤+马金虎 | 已完成 | rrsjk-light-service |
| TAEI-3059 | 建站相关优化 | 杨越越 | 徐晓凤 | 已完成 | 多个 |
| TAEI-3043 | 工商业自持电站损益报表 | 徐晓凤 | 王斌 | 已完成 | rrsjk-light-service, rrsjk-admin-web |
| TAEI-3025 | BT报表项目 | 刘艺 | 于淼+包鑫+李龙 | 测试中 | rrsjk-light-service, rrsjk-admin-web, rrsjk-light-report-service |

| TAEI-3005 | 金蝶总账接口开发 | 杨越越 | 马斌 | 待测试 | finance+light+report+admin-web |

## 关键业务链分析

### 0. TAEI-3005 金蝶总账接口开发 (马斌, 04-15 ~ 05-16)
- **核心结论**: 非"SAP切换金蝶"，而是"双系统并行"，按 stockTransfer=1 路由
- **完整业务链**: CBS前端 → light-service(Dubbo消费) → finance-service(Dubbo提供) → 金蝶HTTP API → king_die_sap_record 落库
- **业务模式**: H01(收入)/H05(成本)/H06(盈利)/A02(收款)，仅覆盖股转公司
- **数据库**: 新增 king_die_sap_record + king_die_sap_record_item
- **Dubbo接口**: `JinDieSapRecordService` — sapLedger/reverseFinanceToSap/stockTransElecOrderIncomeToJinDie
- **风险**: 05-12误删后Revert；token线程安全已修复；rowId幂等规则 R+ywms+18位bid
- **已写入**: `domains/kingdie-sap-dual-architecture.md`（新建）

### 1. TAEI-3101 招银组件功率匹配价格 (李龙, 5/15)
- **完整业务链**: 电站进件推送 → 技术方案映射(V2) → 租赁屋顶类型映射(V2) → 电价表查询(5维) → 融资产品编号
- **涉及表**: `cmb_electric_price` (电价配置表)
- **新旧对比**: V1(省+市+技术方案描述) → V2(省+市+区县+租赁屋顶类型+组件类型)
- **枚举**: `TechnicalSchemeEnumV2` (5种), `LeaseRoofTypeEnumV2` (3种)
- **调用链**: `CmbLeasingPushApiServiceImpl.buildLeaseScheme()` → `CmbLeasingStationDao.getPriceV2()` → `CmbLeasingStation.xml.getPriceV2`
- **已写入**: `domains/zhaoyin-lease.md` 第9章

### 2. TAEI-3043 工商业自持电站损益报表 (王斌, 5/11-5/15)
- **涉及仓库**: rrsjk-light-service (后端), rrsjk-admin-web (前端), rrsjk-light-report-service (报表)
- **核心实体**: `CmOwnerStationReport` — 102行实体，包含装机量、发电量(总/上网/自发自用)、收入(电费/充电服务费)、成本(折旧/运维/屋顶租金/高压电费/保险)、毛利
- **数据来源**:
  - 普通电站: `light_project_electric_order` 电费收益表
  - 充电桩电站: 于川清大数据库 (`chargingStationService.getPvGenerationByMonth()`)
- **关键逻辑**: 按电网购电客户/业主购电客户编码过滤电费收益数据，分别计算上网电量和自发自用电量
- **定时任务**: `queryElectricityCost(yearMonth)` 定期查询电费成本
- **二期新增**: 高压电费查询修改、发电来源字段非必填兼容1PG0公司
- **待深入**: 充电桩数据库接口完整链路、报表前端页面

### 3. TAEI-3085 增加上收限制 (解钦, 5/11-5/16)
- **完整业务链**: 导入收入 → 校验电站模式 → 检查其他模式收入冲突 → 阻止/允许上收
- **涉及仓库**: rrsjk-light-service (策略工厂), rrsjk-admin-web (前端交互)
- **策略架构**: 两层工厂分离
  - `StationIncomeModeCheckStrategyFactory` — 模式校验/查询
  - `StationIncomeHandleStrategyFactory` — 收入处理逻辑
- **8种资方模式**: 越秀(YX)、中核(ZH)、浦银(PY)、招银(ZY)、华电(HD)、华融(HR)、中银(ZHY)、基金(FUND)
- **核心方法**: `batchFindConflictModes()` 批量检查冲突, `getModeByLatestIncomeTime()` 获取电站当前模式
- **关联需求**: TAEI-3076 (政策传SAP带电站编码和订单号) — xref3字段传递电站编码

### 4. TAEI-3098 图片验真唯一码重复检查 (马斌, 5/13-5/16)
- **变更**: `CmbLeasingPushApiServiceImpl` 中新增图片重复上传检查
- **关联**: TAEI-3084 中银租后接口对接 — 图片上传是进件流程的一部分
- **金蝶记账**: 同期修复金蝶历史记录放开限制、历史数据优化、股转公司电费发票冲销

### 5. TAEI-3078 派单3.1优化 (解钦, 5/11-5/16)
- **涉及仓库**: rrsjk-light-service (后端), rrsjk-admin-web (前端)
- **关键变更**:
  - 列表查询增加新状态
  - 积压派单数据在新增非工作日时间配置时同时增加定时任务
  - 终止时删除定时任务 (`station-complete-stop`)
  - 修复审核问题、完工审核校验电站信息异常
  - 定时任务执行错误问题修复
- **关联表**: `light_audit_dispatch_log` (派单日志), 非工作日时间配置表

### 6. TAEI-3025 BT报表项目 (于淼/包鑫/李龙, 5/11-5/14)
- **涉及仓库**: rrsjk-light-service, rrsjk-admin-web, rrsjk-light-report-service
- **关键变更**:
  - 需求变更适配：字段调整、Excel导出错误提示 (11次迭代提交)
  - 导入功能新增失败数据列表生成 (`BtAssetManagementErrorExcel` 等)
  - BT股转模式及中核报表导入校验
  - BT基金模式电站资产管理报表接口编码
  - FAP状态映射逻辑调整
  - 基金模式回款单管理状态编码修正

## 新发现

### Git Author 映射更新
- **李龙**: 确认使用 `lilong` + `HAIER\26027356` (工号) 两个别名
- **包鑫**: `baoxin` (之前映射表已有)

### 业务逻辑遗漏
1. **工商业自持电站损益报表** — 充电桩数据从"于川清大数据库"获取，具体接口和表结构需要进一步追踪 `chargingStationService`
2. **电站收入上收限制** — 8种资方模式的收入表和校验逻辑，每种模式对应不同的收入处理策略
3. **派单3.1** — 定时任务与派单数据的关联机制，非工作日时间配置如何触发定时任务

## 知识库更新

| 操作 | 文件 | 内容摘要 |
|---|---|---|
| 🆕 新增 | `domains/settlement.md` 第9章 | 电站收入上收限制策略工厂 (8种模式、两层工厂) |
| 🆕 新增 | `domains/zhaoyin-lease.md` 第9章 | 招银进件电价匹配 V2 (技术方案/屋顶类型/电价表) |
| ✏️ 更新 | `domains/settlement.md` 待确认 | 补充工商业报表和收入限制的待确认项 |
