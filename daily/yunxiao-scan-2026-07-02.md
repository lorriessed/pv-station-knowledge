# 云效驱动代码学习报告 — 2026-07-02

## 扫描范围
- 云效需求状态变更: 20+ 个 | 涉及人员: 代继宁, 龙龙, majinhu, baoxin, wangxiran, 商轶龙, 潘乃华, yumiao, laowang, liuchunwei, tn_wanb
- Git 提交: 90+ (核心后端仓库, 2026-06-30~07-02)
- 上次报告: 2026-07-01

## 云效需求状态变更

### 已发版 (3)
- TAEI-3194 电费收益增加分中心 → 已发版-测试验证通过 (李龙, AI 70%)
- TAEI-3284 招银大屏 → 已发版-测试验证通过 (马金虎, AI 60%)
- TAEI-3283 华容大屏 → 已发版-测试验证通过 (马金虎, AI 60%)

### 已完成 (2)
- TAEI-3206 light-service核心类加@Lazy → 已完成 (商轶龙)
- TAEI-3255 租金个税系统 → 已完成 (代继宁, AI 96%)

### 测试完成待发版 (1)
- TAEI-3266 统众导入发票号 → 测试完成-待发版 (代继宁, AI 93%)

### 测试中 (2)
- TAEI-3221 调拨入库 → 测试中 (姜传德, AI 50%)
- TAEI-3190 营销政策预测报表 → 测试中 (商轶龙, AI 60%) ⚠️ 超期6天

### 待测试 (4)
- TAEI-3380 户号拆分电费 → 待测试 (商轶龙)
- TAEI-3267 工商业政策兼容 → 待测试 (王斌, AI 30%)
- TAEI-3355 招银组件功率匹配优化 → 待测试 (李龙)
- TAEI-3348 逆变器列表切换 → 待测试 (马金虎, AI 60%)

### 开发中 (2)
- TAEI-3246 零碳退安装质保金 → 开发中 (代继宁)
- TAEI-3332 电网问题备案 → 开发中 (孙志男, AI 50%) ⚠️ 明天截止

### 新建 (5)
- TAEI-3393 主政策/合同/租金优化 → 待处理 (包鑫) 🔴 紧急
- TAEI-3390 A段政策增加模式 → 待处理 (商轶龙, 高优)
- TAEI-3391 电费暂估冲暂估重构 → 待处理 (潘乃华)
- TAEI-3392 E2E并网数据重构存储 → 待处理 (潘乃华)
- TAEI-3365 股权穿刺报表 → 待处理 (于淼)

## 核心业务变更

### 1. 租金个税计算事务拆分 (代继宁, rrsjk-light-service)
- RentTaxAmountServiceImpl: @Transactional(300s)大事务 → 按公司维度编程式事务(90s/company)
- 失败回滚范围缩小到单个公司，避免全量重跑
- 中间表未清空从 return → throw RuntimeException（快速失败）

### 2. 零碳质保金退款审核流程重构 (代继宁, rrsjk-finance-service)
- 960+/276- 行, 8 文件
- 新增: 预算占用逻辑 + 云报账定时任务
- 质保金退款从简单审核扩展为多步骤流程

### 3. ADS大数据迁移 — 大屏系列 (majinhu, rrsjk-light-report-service)
- 12 commits, 招银/华容/浦银三个资方大屏全部切换到ADS
- 电站资产管理/发电数据查询/电站详情等也切换

### 4. 单商单区模式枚举 (潘乃华, rrsjk-light-service)
- 新增 AccurateToRegionEnum: 单商单省/单商单县/单商单区
- 替换硬编码字符串判断

### 5. 账单查询批量优化 (龙龙, rrsjk-light-service)
- getByStationIds 批量查询 + 分片处理

## 知识库更新
- domains/zero-carbon-station.md: 新增质保金退款审核流程重构
- domains/policy.md: 新增 AccurateToRegionEnum 单商单区模式枚举
- domains/inverter-data.md: 新增大屏系列 ADS 迁移记录
- domains/settlement.md: 已由23:00扫描更新(事务拆分)

## 风险预警
- 🔴 TAEI-3393 紧急需求未启动 (截止07-09)
- 🟡 TAEI-3332 高优开发中明天截止 (07-03)
- 🟡 TAEI-3190 超期6天仍在测试中
- 🟡 ADS迁移复杂度持续上升

## HTML报告
https://cdn01.rrsjk.com/reports/5ac56d43-1f3a-4792-98c2-fd6ec5bd6629.html
