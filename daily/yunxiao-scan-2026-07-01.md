# 云效驱动代码学习报告 — 2026-07-01

## 扫描范围
- 时间窗口: 2026-06-30 ~ 2026-07-01
- 核心后端仓库: rrsjk-light-service (29), rrsjk-light-report-service (13), rrsjk-light-data-service (2)
- Git 提交总计: 44
- 云效近期更新需求: 35

## 需求状态变更
- 已发版: TAEI-3206(@Lazy注解), TAEI-3293(资方大屏发电量单位)
- 已完成: TAEI-3255(租金个税, AI 96%)
- 待发版: TAEI-3194(电费收益分中心)
- 阻塞: TAEI-3080(公建整村租金支付)
- 新创建: TAEI-3380(电费拆分), TAEI-3365(股权穿刺), TAEI-3364(电价报表优化)

## 核心代码变更
1. TAEI-3355 招银组件功率匹配: CmbElectricPrice新增5个租金区间字段, RentPhaseUtil新工具类
2. 工商风险接口对接: 包鑫9次提交, service.xml + LightElecSealUse.xml
3. 大屏ADS迁移: 马金虎替换招银/华容/浦银大屏数据源
4. 低效电站报表: 新增EnergyLowEfficiencyStationService
5. EventBus线程池优化: allowCoreThreadTimeOut(true)
6. 租金个税事务超时: @Transactional(timeout=300)

## 知识库更新
- domains/zhaoyin-lease.md: TAEI-3355 招银功率区间匹配
- domains/operation-and-data.md: 低效电站报表 + 大屏ADS迁移
- domains/system-infra-service.md: EventBus优化 + 工商风险

## 风险预警
- TAEI-3080 阻塞状态
- TAEI-3130 计划完成06-30已过期，仍在"前端对接中"
- TAEI-3190 计划完成06-25已过期5天，仍在"测试中"

## HTML报告
https://cdn01.rrsjk.com/reports/8a25248a-9c3a-440a-9060-78fa0b03b10e.html
