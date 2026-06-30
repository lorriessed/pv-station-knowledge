# 云效驱动代码学习报告 — 2026-06-30

## 扫描范围
- 云效需求状态变更: 11 个
- Git 提交: 170 个 (18 个仓库有活动)
- 核心后端提交: rrsjk-light-service(30), rrsjk-light-report-service(9), rrsjk-light-data-service(4), rrsjk-admin-app-service(4)
- 涉及人员: 龙龙(王斌), 孙志男, 王金浩, 马金虎, 李龙, 包鑫, 代继宁, 姜传德, 于淼, wangxiran

## 已发版/已完成
- TAEI-3293 各资方大屏发电量单位调整 → 已发版 (张硕文)
- TAEI-3317 大屏-资产大屏 → 已发版 (马金虎, AI 50%)
- TAEI-3025 BT报表项目 → 已发版 (包鑫, AI 40%)
- TAEI-3251 广发模式重庆奉节暂停结算 → 已完成 (商轶龙, AI 60%)

## 核心代码变更
1. TAEI-3080 公建/整村租金请款二期 (龙龙, ~1200行新增)
2. 运维商合同查询重构-主表切换 (孙志男)
3. TAEI-3206 @Lazy循环依赖优化 (龙龙, 8个Service)
4. 资方大屏排除EPC工商业 (代继宁)
5. 发电户号绑定验证修复 (wangxiran)
6. TAEI-3171 审批中心待办+脱敏 (李龙)
7. 商户通逆变器DWS查询 (马金虎)
8. 巡检报告上传 (王金浩)
9. 中转仓调中转仓 (姜传德)

## 知识库更新
- domains/settlement.md — TAEI-3080 租金请款二期
- domains/station-lifecycle.md — 合同查询重构
- domains/inverter-data.md — 商户通逆变器+大屏排除EPC
- domains/approval.md — TAEI-3171 审批中心
- domains/inventory.md — 中转仓调中转仓

## 风险预警
- TAEI-3206 超期12天 (计划06-18)
- TAEI-3234 超期4天 (计划06-26)
- TAEI-3193 超期5天 (计划06-25)
- TAEI-3130/TAEI-3266 今日到期

## 详细报告
https://cdn01.rrsjk.com/reports/905b9b60-ea15-4994-bb85-4181cdf46804.html
