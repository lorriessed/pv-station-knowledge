# 云效驱动代码学习日报 2026-06-12

## 扫描范围
- **时间窗口**: 2026-06-05 ~ 2026-06-12
- **云效需求**: 20个（updatedAfter=2026-06-05）
- **Git 提交**: 416个（排除rrsjk-admin-bff后核心业务350个）
- **涉及人员**: 王希然(94), yumiao(68), majinhu(41), baoxin(41), 代继宁(32), 龙龙(31), 李培龙(21), sunzn(20), laowang(16), mabin(12)

## 核心需求与代码关联

### TAEI-3190 营销政策预测报表（龙龙/王斌, 28 commits）
- 分支: `origin/20260610_longlong_taei_3190_report_config`
- 四期迭代: 配置管理 → 发电汇总 → 预测核心 → 导出权限
- 新增实体: ReportPolicyForecast, ReportConfigQueryDao, PolicyForecastJob
- 架构: ODS读 + local写
- 仓库: light-report-service, light-service, admin-web

### TAEI-3092 租金个税报表 + FAP集成（代继宁, 12+ commits）
- 分支: `featrue-20260525-rentTaxReport/TAEI-3092`
- FAP保证金自动确认 (20260609-fapDepositAutoConfirm)
- FAP撤销推送 (20260609-fapSentRevocation)
- 租金个税只查询>0数据
- 使用注解事务

### TAEI-3127 完工/技术驳回暂存（王希然等, 18+ commits）
- **核心**: 三态驳回 → 二态驳回重构（删除116行白名单代码）
- **Bug**: reject_flag值颠倒修复（5文件20行）
- 新增: 单张驳回、驳回原因回填、技术影像暂存同步
- 仓库: light-service, merchant-web

### TAEI-3058 电站转移（姜传德/王希然, 10+ commits）
- 分支: `station-transfer-sub-account-20260525`
- 电站转单派工单转移/取消
- 完工状态校验（10种允许状态）
- 调入列表团队下拉选项
- 状态: 测试完成 ✅

### TAEI-3023 经营性租赁FAP（代继宁/魏秋阳）
- FAP回调路由完善
- 状态: 测试中

### TAEI-3186 一级商审（解钦, 6 commits）
- 方案审核/完工审核新增一级商审
- 状态: 开发中

## 其他变更
- **爱士惟发电数据修复** (yumiao, 14 commits): light-data-service
- **暂估逻辑修复** (baoxin, 24 commits): EnergyJobServiceImpl日期参数修改
- **逆变器串线图** (sunzn/wangxiran): TAEI-3128
- **仓储相关** (王希然): 入库导出物流信息、调拨入库仓库名称
- **退商流程优化** (majinhu): TAEI-3185

## 知识更新
1. `domains/policy.md` — TAEI-3190 营销政策预测报表
2. `domains/settlement.md` — TAEI-3092 FAP集成 + FAP回调路由
3. `domains/station-lifecycle.md` — TAEI-3127 三态→二态重构 + TAEI-3058 电站转移
4. `daily/yunxiao-2026-06-12.md` — 本报告

## 风险预警
1. 🔴 reject_flag值颠倒Bug — 需排查历史数据
2. 🔴 FAP校验条件反复修改 — 确认最终版本
3. 🟡 三态→二态重构影响面 — 前端适配确认
4. 🟡 暂估日期硬编码 — 建议改为动态计算
