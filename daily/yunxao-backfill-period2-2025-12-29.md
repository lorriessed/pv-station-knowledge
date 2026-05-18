# 云效驱动代码学习报告 — 补漏第3期 (2025-12-29 ~ 2026-01-18)

## 扫描范围
- **云效需求**: 15 个 (TAEI-2800 ~ TAEI-2821)
- **涉及人员**: 于淼, 解钦, 包鑫, 马斌, 孙志男, 马金虎, 王希然, 王斌, 代继宁, 李培龙, 徐晓凤, 付凯善, 杨辉, 王金浩, 姜传德(德), 22081194(CBS)
- **Git 提交**: 811 个 (去重后, 23 个仓库)
- **扫描日期**: 2026-05-19

## 需求 → 代码关联

| 需求号 | 标题 | 负责人 | 参与开发 | 涉及仓库 | 关键提交数 |
|---|---|---|---|---|---|
| TAEI-2800 | 绿证交易手动调整库存生成流水 | 刘艺(PM) | 商轶龙 | cbs-web, system-service | ~43 |
| TAEI-2801 | 工商业采购单问题处理 | 杨越越(PM) | 无 | - | - |
| TAEI-2804 | 基金模式上收入 | 杨越越(PM) | 姜传德/解钦 | rrsjk-light-service, rrsjk-finance-service | ~35 |
| TAEI-2805 | 2025-12-31合同及基础政策升级 | 杨越越(PM) | 于淼/解钦/商轶龙/包鑫 | rrsjk-light-service, rrsjk-finance-service, rrsjk-admin-web | ~100 |
| TAEI-2807 | 华融整村推进电站进件开发 | 杨越越(PM) | 于淼/姜传德/马斌 | rrsjk-light-service, rrsjk-light-report-service, rrsjk-merchant-web | ~40 |
| TAEI-2808 | 完工后变更方案/房型+房产证明荷载报告 | 杨越越(PM) | 解钦/袁睿林 | rrsjk-light-service, rrsjk-merchant-web, rrsjk-admin-web | ~80 |
| TAEI-2809 | HDS/商户通/APP运维工单超期申诉优化 | 高媛(PM) | 孙志男/李培龙 | rrsjk-light-operation-service, rrsjk-hds-web, nahui-pv.hds-h5, nahui-pv.merchant-micro.osp, repairs | ~60 |
| TAEI-2810 | 共享支付明细增加分中心权限控制 | 杨越越(PM) | 商轶龙 | rrsjk-light-service | ~5 |
| TAEI-2812 | 运维收入成本管理模块-集团内项目公司记账优化 | 高媛(PM) | 孙志男 | rrsjk-light-service, rrsjk-hds-web | ~30 |
| TAEI-2813 | 逆变器序列号变更逻辑优化 | 徐晓凤 | 付凯善/马金虎 | rrsjk-light-service, rrsjk-light-operation-service, repairs, nahui-pv.merchant-micro.osp, pv.osp-uni | ~30 |
| TAEI-2814 | 微信小程序银行卡变更 | 徐晓凤 | 王希然/付凯善/袁睿林 | rrsjk-light-service, rrsjk-admin-web, rrsjk-hds-web | ~50 |
| TAEI-2815 | 二级商管理 | 徐晓凤 | 李培龙/付凯善/马斌 | rrsjk-light-service, rrsjk-light-report-service, rrsjk-admin-web, rrsjk-merchant-web | ~50 |
| TAEI-2816 | 二级商信息反馈列表 | 徐晓凤 | 杨辉/王金浩/付凯善 | rrsjk-light-service | ~10 |
| TAEI-2820 | CBS系统-新增运维买损管理模块 | 高媛(PM) | 孙志男/李培龙 | - | - |
| TAEI-2821 | 采购原材料核算成本时逻辑变更 | 杨越越(PM) | 王斌 | rrsjk-admin-web | ~10 |

## 业务链分析

### 1. 共建费模式 (核心变更, TAEI-2805/2814)
**涉及仓库**: rrsjk-light-service, rrsjk-admin-web
**开发人员**: majinhu (马金虎), yumiao (于淼)

- **新枚举**: `JointConstructionFeeModelEnum` (SUPPORT/NOT_SUPPORT) — 项目公司是否支持共建费
- **新合同类型**: `TP_PAYMENT_AGENCY` (共建专项合同, 值33) — 区别于主合同
- **业务链**: 项目公司配置 → 电站新建时判断共建模式 → 自动生成共建专项合同 → DCC电子签回调 → `gjfMasterStationSignSuccess()` 处理共建费主合同签署
- **关联**: 租金模式设置 (`setRentalMode()`) — 与共建费模式联动
- **影响范围**: `BaseLightStationMode`, `LightSpicStationModel`, `LightWholeVillageStationModel`, `LightYuexiuStationModel` 等4种电站模式

### 2. 审核派单系统 (新功能, TAEI-2815/2808)
**涉及仓库**: rrsjk-light-service, rrsjk-admin-web
**开发人员**: 解钦

- **核心**: 电站审核(方案/技术/商务)自动派单到审核人员
- **派单策略**: 按审核类型查询有效审核人员 → 按待办数量等量分配
- **新实体**: `LightAuditDispatchLog`, `LightTechAuditor`
- **前端**: 技术审核人员管理页面
- **业务链**: 审核任务触发 → 派单服务 → 审核人员接收 → 审核完成/改派 → 记录日志

### 3. 运维收入A51冲销 (TAEI-2812)
**涉及仓库**: rrsjk-light-service
**开发人员**: sunzn (孙志男)

- A51数据暂估冲销: `coverOperationMaintenanceA51()` → `coverA51()`
- 同步集团内项目公司A58成本信息
- 冲销凭证生成和状态更新

### 4. 基金模式上收入 (TAEI-2804)
**涉及仓库**: rrsjk-light-service, rrsjk-finance-service
**开发人员**: 解钦, 姜传德(德)

- 表重命名: `light_zh_settle` → `light_fund_settle`
- 基金收入结算 + 冲销功能
- 收入处理策略重构 (华融/基金)

### 5. 零碳商户公告 (新功能, TAEI-2813)
**涉及仓库**: rrsjk-light-service, rrsjk-merchant-web, rrsjk-admin-web
**开发人员**: 代继宁

- 事件驱动公告发送: `LightZeroMerchantNoticeEvent` → `LightZeroMerchantNoticeListener`
- 合同签署成功后自动触发
- 审核流: 待审核 → 通过/驳回

### 6. 逆变器SN变更 (TAEI-2813)
**涉及仓库**: rrsjk-light-service, rrsjk-light-operation-service, repairs, nahui-pv.merchant-micro.osp
**开发人员**: sunzn, 付凯善, majinhu

- SN重复校验 + OCR识别 + 空SN处理
- 工单备件SN变更 (repairs)
- 前端SN码OCR (merchant-micro.osp)

### 7. 二级商管理 (TAEI-2815/2816)
**涉及仓库**: rrsjk-light-service, rrsjk-light-report-service, rrsjk-admin-web, rrsjk-merchant-web
**开发人员**: mabin (马斌)

- 二级商基础数据看板 (CBS页面 + API + 报表)
- 二级商建站能力评估表
- 定时任务每日生成二级商基础数据

### 8. 运维工单超期申诉 (TAEI-2809)
**涉及仓库**: rrsjk-light-operation-service, rrsjk-hds-web, nahui-pv.hds-h5, nahui-pv.merchant-micro.osp
**开发人员**: sunzn, 李培龙

- 申诉时间限制: 测试环境移除, 生产环境激活
- 审核备注 + 导出功能
- 见证性资料附件类型扩展

### 9. 华融整村推进 (TAEI-2807)
**涉及仓库**: rrsjk-light-service, rrsjk-light-report-service, rrsjk-merchant-web
**开发人员**: yumiao (于淼), mabin (马斌)

- 整村汇流模式支持
- 进件模式设置 + 逆变器同步修复
- 模块序列号权限控制

### 10. CBS绿证交易 + 品牌更新 (TAEI-2800)
**涉及仓库**: cbs-web, system-service
**开发人员**: yumiao (于淼), 德 (姜传德), 22081194

- 手动调整库存 → 库存流水记录
- 消息通知系统 (系统消息优先级)
- 品牌名称: 日日顺 → 海尔

## 知识库更新

| 操作 | 文件 | 内容摘要 |
|---|---|---|
| 追加 | domains/settlement.md | 运维收入A51冲销、基金模式上收入、采购申请结算重构、统众资方接入、共建费模式、绿证交易库存调整 |
| 追加 | domains/approval.md | 审核派单系统、电站方案/完工撤回、安全节点照片组、房产证和荷载报告、零碳商户公告、逆变器SN变更、运维工单超期申诉、华融整村推进、日历工作日节假日 |
| 追加 | data/enums.md | 审核类型枚举、派单类型枚举、处理标识枚举、共建费模式枚举、共建专项合同类型 |

## 关键发现

1. **共建费模式**是本期最大的业务变更之一，涉及合同签署、租金模式、电站创建等多个环节，与TAEI-2805(合同政策升级)和TAEI-2814(银行卡变更)都有关联。

2. **审核派单系统**是全新的业务功能，引入了审核人员管理和自动分配机制，后续可能影响所有审核类业务。

3. **海尔工号 `22081194`** 是CBS/零碳团队开发人员的Git author，在多个仓库有活跃提交，之前映射表未收录。

4. **22081194** 主要涉及：政策变更数据刷新、零碳消息通知、报表修改、SAP单号重传、爬虫推送数据等。

5. **代继宁** 的商户公告功能使用事件驱动架构，合同签署成功后自动发送公告，是PVS中较少使用的事件驱动模式。
