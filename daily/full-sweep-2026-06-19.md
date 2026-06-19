# PVS 全量通读详细报告 2026-06-19 (第35轮)

## 通读概况
- **时间**: 2026-06-19 22:00
- **仓库数**: 5 个
- **总完成**: 132/138 (95.7%)

## 仓库详情

### nh-business-forecast-service (⭐ 重要业务发现)
- **路径**: /data/pvcode/nh-business-forecast-service
- **分支**: master | HEAD: 857a713a5606
- **最后提交**: 2024-04-20 (haier47@aliyun.com)
- **业务文件数**: 56
- **业务域**: 工商业(CM) — 项目收益预测/投资测算
- **核心Service**:
  - `ForecastProjectDetailServiceImpl` — 预测项目管理 (CRUD + PDF生成)
  - `ElectricityGenerationDetailServiceImpl` — 发电量计算 (25年衰减)
  - `ProjectCostInfoDetailServiceImpl` — 建站成本管理 (参数校验)
  - `ProjectInvestmentIncomeServiceImpl` — 投资收益计算 (3种模式)
  - `ElectricityPriceOfCoalServiceImpl` — 脱硫煤电价导入
  - `TouElectricityPriceServiceImpl` — 分时电价导入
  - `ElectricityPriceSummaryDiffPeriodServiceImpl` — 分时电价时段汇总
  - `InstallDipAngleInfoRegionServiceImpl` — 安装倾角光照信息
- **数据库**: db003.rrsjk.internal (生产)
- **Dubbo 依赖**: rrsjk-system-api, system-service, rrsjk-energystorage-api, rrsjk-member-api
- **外部服务**: Aliyun OSS (pvs-public bucket)

### recipt_extraction (新 AI 服务)
- **路径**: /data/pvcode/recipt_extraction
- **分支**: master | HEAD: 32043ad5e4d8
- **最后提交**: 2026-06-17 (maverick100)
- **类型**: Python Flask AI 微服务
- **端口**: 2664
- **模型**: qwen3-vl-30b-a3b-instruct
- **功能**: 电费结算单图片 → 表格数据提取

### recipt_extraction_pdf (新 AI 服务)
- **路径**: /data/pvcode/recipt_extraction_pdf
- **分支**: master | HEAD: 3947db9a9a48
- **最后提交**: 2026-06-04 (haier47)
- **类型**: Python Flask AI 微服务
- **端口**: 2606
- **模型**: qwen3-vl-30b-a3b-instruct
- **功能**: 多页PDF电费结算单 → 表格数据提取

### haier-energy-job-service (基础设施)
- **路径**: /data/pvcode/haier-energy-job-service
- **分支**: master | HEAD: 34434a52c8b5
- **最后提交**: 2026-06-12 (解钦, JDK17改造)
- **类型**: SnailJob 分布式任务调度平台 (开源框架定制)
- **PVS业务价值**: 低 — 纯基础设施

### nahui-itd-docs (文档仓库)
- **路径**: /data/pvcode/nahui-itd-docs
- **分支**: main | HEAD: 9e89b025943d
- **最后提交**: 2025-03-25 (刘飞)
- **类型**: 前端文档 (月报/BA商城)
- **PVS业务价值**: 无
