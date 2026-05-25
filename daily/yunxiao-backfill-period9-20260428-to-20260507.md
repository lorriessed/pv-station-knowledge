# 云效驱动代码学习报告 — 第9期: 4月底-5月初 (2026-04-28 ~ 2026-05-07)

**扫描日期**: 2026-05-25
**期数**: 9/10

## 扫描范围
- 云效需求: 12 个 (TAEI-3056 ~ TAEI-3070)
- 涉及人员: 解钦、于淼、代继宁、马金虎、王斌、孙志男、王希然、马斌、杨辉、付凯善、姜传德(德)、王金浩(laowang)、徐晓凤
- Git 提交: 330 条
- 涉及仓库: rrsjk-light-service(134), rrsjk-light-data-service(87), rrsjk-admin-web(41), rrsjk-light-operation-service(21), rrsjk-finance-service(13), rrsjk-trade-service(10), rrsjk-hds-web(10), rrsjk-merchant-web(9), rrsjk-light-report-service(6)

## 需求 → 代码关联

| 需求号 | 标题 | 状态 | 参与开发 | 相关提交数 | 主要变更 |
|---|---|---|---|---|---|
| TAEI-3056 | 零碳适家建站方案登记支持不同品牌不同规格组件混用 | 已完成 | 姜传德(德) | 23+ | 零碳容量计算修正、华融EPC电站处理、电站状态编辑检查、房屋类型字段修复 |
| TAEI-3057 | 审核驳回支持按单张图片驳回 | 待评审 | 杨辉、王希然、张硕文 | 18+ | 图片更改验证逻辑修复、技术整改工单图片确认 |
| TAEI-3058 | 电站支持转移 | 待处理 | 姜廷、姜传德、于淼等 | - | 本期未开始开发 |
| TAEI-3059 | 建站相关优化 | 已完成 | 杨辉、王希然、张硕文、付凯善 | 28+ | 组件库导入性能优化、银行卡号格式化修复 |
| TAEI-3060 | 大屏新增告警 | 开发中 | 于淼 | 94+ | 逆变器写入数据压力测试、发电消费速度优化、告警码缓存 |
| TAEI-3061 | 己完工电站方案变更逻辑优化 | 已完成 | 付凯善、马金虎 | 28+ | 广发并网/回退字段、业主信息更新接口、Kafka消费参数优化 |
| TAEI-3062 | 审核派单「闭环率报表」优化 | 已完成 | 王金浩、付凯善 | 16+ | 闭环率从累积区间改为分段区间(≤3/4-7/8-15/16-30/31-60/61-180/181-365/>365天) |
| TAEI-3063 | 广发过程进件-APP附件改造 | 已完成 | 杨辉、付凯善、董学强 | 16+ | 完工进件状态/时间字段、采集器信息&VR链接展示 |
| TAEI-3066 | 展会-运维大屏 | 开发中 | 魏秋阳、孙志男、李培龙 | 37+ | 固定电站模块、业务合作意向、电站标签、年度保发、储能电站管理 |
| TAEI-3068 | 广发业主信息更正接口 | 开发中 | 付凯善、袁睿林、马金虎 | 10+ | customerInfoUpdate接口、商机修改后推送、并网回退字段 |
| TAEI-3069 | 招银接口6.1/6.3/6.4 | 已完成 | 薛荣基、马斌 | 16+ | 金蝶SAP接口扩展、设备匹配状态、FAP回调空指针修复 |
| TAEI-3070 | 招银接口6.5/6.6/6.7 | 待处理 | 姜传德、薛荣基、马斌 | - | 本期未开始开发 |

## 业务链分析

### 1. 审核闭环率报表优化 (TAEI-3062)
**开发者**: laowang (王金浩)
**仓库**: rrsjk-light-report-service, rrsjk-admin-web, rrsjk-light-service
**完整业务链**:
- 前端: `dispatchReportClosedList.ftl` — 表头从4个区间扩展为8个分段区间
- 实体: `LightTechAuditClosedReport.java` — 新增 closedLte30/60/180/365Days + closedGt365Days 字段
- 服务: `LightTechAuditClosedReportServiceImpl.java` — 新增5个区间的聚合计算和占比公式
- SQL: `LightAuditDispatchLog.xml` — CASE WHEN 从累积改为分段，基于 `pass_audit_at - IFNULL(reject_audit_at, dispatch_at)` 的 DATEDIFF
- **业务意义**: 从"≤X天累计"改为"X-Y天分段"，更精确地反映审核效率分布

### 2. 电站终止管理策略体系
**开发者**: 解钦
**仓库**: rrsjk-light-service, rrsjk-admin-web, rrsjk-merchant-web
**完整业务链**:
- 策略模式: `StopToDoStrategyFactory` → `StationFinalizeStrategy` / `ReverseBasePolicyIncomeStrategy` / `ReverseStationIncomeStrategy`
- 定时任务: `StopToDoJobService` 按 DAG 依赖顺序执行待办
- 核心变更: 资产审核通过后不再自动冻结电站和创建终止待办（旧逻辑移除）
- 状态控制: 待完工审核的电站不允许申请方案变更
- 前端: 终止管理列表增加待办事项、商户通电站终止流程接口改造

### 3. 广发业主信息更正接口 (TAEI-3068)
**开发者**: majinhu (马金虎)
**仓库**: rrsjk-light-service
**完整业务链**:
- API端点: `GfApiUrlEnum.CUSTOMER_INFO_UPDATE` → `/inputpiece-plant/propertyStationUpdate/customerInfoUpdate`
- 请求: `GfCustomerInfoUpdateRequest` (191行) — 进件序号、变更单号、变更原因、业主基本信息
- 响应: `GfCustomerInfoUpdateResponse` — showmsg/state/msg
- 服务: `GfInfoUpdateApi.java` (58行)
- 商机修改后推送 customerInfoUpdate 到广发系统

### 4. FAP 财务记录体系持续迭代
**开发者**: 代继宁
**仓库**: rrsjk-light-service, rrsjk-finance-service, rrsjk-trade-service
**完整业务链**:
- 保证金取消: 新增FAP记账状态检查，已记账不允许取消；修复空指针
- FAP记录创建: 统一创建流程，修复状态设置和检查逻辑
- FAP查询定时任务: 更新查询逻辑
- Trade Service: 移除LightFapRecordService的Dubbo配置，修复订单FAP收款创建
- 零碳适家安装费: 服务重构，FAP记录创建和状态同步修复

### 5. 展会-运维大屏 (TAEI-3066)
**开发者**: sunzn (孙志男), dengqiu (马斌)
**仓库**: rrsjk-light-operation-service, rrsjk-hds-web
**完整业务链**:
- OperationModelStation: 固定电站实体 + 完整CRUD + 装机功率/累计发电量查询
- 业务合作意向功能
- 电站标签服务: OperationLabelService, OperationLabelDefinitionService
- 电站年度保发功能: 接口 + 统计
- 储能电站管理功能
- 逆变器变更过程信息查询

### 6. 逆变器数据服务优化 (TAEI-3060)
**开发者**: yumiao (于淼)
**仓库**: rrsjk-light-data-service, rrsjk-light-service
**关键变更**:
- 高并发模拟器: HighConcurrencySimulator 压力测试组件
- 发电消费速度优化: 多线程优化电站日电报表处理
- 告警码加缓存
- 逆变器图表功能
- 发电数据延迟修复
- EventBus线程扩容、熔断策略优化
- 三天发电计算逻辑修复

### 7. 零碳适家容量计算修正 (TAEI-3056)
**开发者**: 德 (姜传德)
**仓库**: rrsjk-light-service
**关键变更**:
- Bug修复: 电站容量计算从 `planQuantity * planPower` 改为 `planPower`
- 华融EPC电站处理策略异常修复
- 电站状态编辑检查逻辑更新（支持审核拒绝状态编辑）
- 华融项目同步: 发电户号/并网时间/设备清单/组件数量修复

## 知识库更新

| 操作 | 文件 | 内容摘要 |
|---|---|---|
| 追加 | domains/approval.md | 审核闭环率报表时间区间分段优化、技术审计关闭报表时间字段扩展 |
| 追加 | domains/station-lifecycle.md | 电站终止管理完工后终止策略体系（策略模式、DAG执行、旧逻辑移除） |
| 追加 | domains/guangfa-business.md | 广发业主信息更正接口体系（API端点、请求/响应实体、商机推送） |
| 追加 | domains/settlement.md | FAP记录体系覆盖（保证金/电费/采购订单）、零碳适家安装费服务重构 |
| 追加 | domains/zero-carbon-station.md | 零碳能源电站容量计算修正 |
| 追加 | domains/operation-and-data.md | 运维展会大屏固定电站模块、电站标签服务、年度保发功能、储能电站管理 |

## 未完成/待观察
- TAEI-3058 电站转移: 状态为"待处理"，本期无代码提交
- TAEI-3070 招银接口6.5/6.6/6.7: 状态为"待处理"，本期无代码提交
- TAEI-3057 审核驳回按图片驳回: 状态为"待评审"，前端图片验证逻辑有变更但后端逻辑待确认

## 下期计划
- 执行第10期（最后一期）: 2026-05-08 ~ 2026-05-17
- 关注电站转移和招银接口的开发进展
- 补充审核驳回按图片驳回的后端逻辑
