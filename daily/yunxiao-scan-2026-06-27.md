# 云效驱动代码学习报告 — 2026-06-27

## 扫描范围
- 时间窗口: 2026-06-26 03:00 ~ 2026-06-27 03:00（增量扫描）
- Git 提交: 92 个 | 活跃开发者: 14 人 | 活跃仓库: 20 个
- 云效需求: 20 个近期状态变更

## 重点业务变更
1. 收入成本报表完善 (解钦, 14 commits): 成本报表月累计+目标数据+明细汇总+下钻累计
2. 政策预测报表终模块 (龙龙, TAEI-3190): ReportPolicyForecastFinal 实体+区县三级联动+导入导出
3. SAP总账记账模型重构 (龙龙): 移除TempConstants.stopCostSpIdList临时暂停结算逻辑
4. 发票批量导入优化 (代继宁, TAEI-3266): OSS文件后缀修复+导入交互优化
5. 资方大屏替换大数据 (majinhu/yumiao, TAEI-3282/3317): Doris语法修复
6. 巡检报告扩展 (laowang, TAEI-3130): detailAddress字段+巡检报告汇总(+458行)
7. 调拨审核接口 (lilong, TAEI-3171): 基础信息变更审核+仓库下拉选
8. 大光伏产值法上收入 (tn_wangb): CmPolicyDto新增policyGroup(GF/CN/CDZ)
9. 华融发电量推送重构 (mabin): 多日期批量处理模式
10. 并网验收发电户号校验 (wangxiran)

## 云效状态追踪
- 已发版: TAEI-3290/3282/3264/3255/3251/3207 (6个)
- 测试中: TAEI-3193/3168 (2个)
- 待测试: TAEI-3266/3234/3221 (3个)
- 开发中: TAEI-3317/3304/3265/3246/3223 (5个)

## 知识库更新
- 待更新: domains/settlement.md (SAP TempConstants清理)
- 待更新: domains/cm-business.md (CmPolicyDto.policyGroup)
- 待更新: domains/operation-and-data.md (ReportPolicyForecastFinal)
- 待更新: domains/inspection.md (巡检报告汇总扩展)

## HTML报告
https://cdn01.rrsjk.com/reports/4b82a261-279d-4a26-9745-e87e4641653e.html
