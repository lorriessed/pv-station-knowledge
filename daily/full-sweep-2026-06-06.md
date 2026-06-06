# 全量通读日报 — 2026-06-06 (第 23 轮)

## 统计

- **仓库总数**: 122
- **本轮通读**: 5 个仓库 (vpp-api-gpower, vpp-api-km, vpp-api-meta, vpp-api-system, vpp-api-template)
- **从未通读仓库**: 0 个
- **本轮性质**: 重扫 (delta discovery) — 所有仓库均已通读过

## 各仓库变更分析

### 1. vpp-api-gpower ⭐ 重点变更

- **上次通读**: 2026-05-14 (首扫) → 2026-06-06 (重扫)
- **新增提交**: 2026-05-28 ~ 2026-05-29 (约 23 个 commits)
- **核心变更**: **电价数据报表模块** — 全新业务功能

#### 新增功能: 电价数据报表

| 组件 | 文件 | 说明 |
|---|---|---|
| Controller | ElectricityPriceDataReportController | /electricityPriceDataReport 路由, 5个API端点 |
| DTO | ElectricityHourlyAvgReportBaseDTO | 24小时电价列 (hour0~hour23) |
| DTO | ElectricityNodeHourlyAvgReportDTO | 节点小时均价 (含城市/节点/区域/价格类型) |
| DTO | ElectricitySpotHourlyAvgReportDTO | 出清小时均价 |
| DTO | ElectricityPriceDataFilterOptionDTO | 筛选项 (区域/价格类型/城市/节点) |
| Config | AdsMapperConfig | **ADS 独立数据源** (spring.ads.datasource) |
| Mapper | ElectricityPriceDataReportMapper | 11个查询方法, ADS数据源 |

**业务含义**: 电力市场电价数据查询与导出，支持日前/实时两种价格类型，节点级和出清级两种报表维度。使用 ADS (AnalyticDB for MySQL) 作为独立数据源，与主业务库分离。

#### 其他变更

- MdmController 新增 `query-by-tax-code` 端点 (同时查询客户和供应商)
- GreenElectricityRevenueController 新增发票相关字段和验证
- 修复票税云开票结果查询逻辑

### 2. vpp-api-km — 技术栈升级

- **上次通读**: 2026-05-14 (首扫) → 2026-06-06 (重扫)
- **新增提交**: 2026-05-21 (2 个 commits)
- **核心变更**: **JDK 8 → JDK 17 升级**

| 变更项 | 旧值 | 新值 |
|---|---|---|
| JDK | 1.8 | 17 |
| Spring Boot | 2.5.5 | 3.2.2 |
| Spring Cloud | 2020.0.4 | 2023.0.0 |
| javax.* | javax.servlet-api 等 | jakarta.servlet-api, jakarta.validation-api, jakarta.xml.ws-api |
| MyBatis-Plus | 3.5.3.1 | 3.5.5 |
| 二级缓存 | 开启 | 关闭 (JDK17反射权限限制) |
| MPJ 插件 | 单参数 | 数组封装 (修复类型异常) |

**业务逻辑无变化** — 纯技术栈升级。

### 3. vpp-api-meta — 无变更

- **上次通读**: 2026-05-14 → 2026-06-06 (重扫)
- **最后提交**: 2024-12-20
- **结论**: 无新增代码，业务逻辑与上次通读一致

### 4. vpp-api-system — 无变更

- **上次通读**: 2026-05-14 → 2026-06-06 (重扫)
- **最后提交**: 2026-04-17 (Dockerfile JVM 参数更新)
- **结论**: 无业务代码变更

### 5. vpp-api-template — 无变更

- **上次通读**: 2026-05-14 → 2026-06-06 (重扫)
- **最后提交**: 2024-12-20
- **结论**: 纯模板项目，无业务逻辑

## 知识库更新

| 文件 | 操作 | 内容 |
|---|---|---|
| `domains/vpp-green-electricity.md` | 新增 Section 9 | 电价数据报表完整文档 (ADS数据源/Controller/DTO/Mapper) |
| `domains/vpp-knowledge-management.md` | 新增 Section 8 | JDK 17 升级变更清单 |
| `domains/vpp-overview.md` | 更新 | gpower/km 模块描述和技术栈标注 |
| `modules/vpp-repositories.md` | 更新 | 5个仓库重扫日期和备注 |
| `data/api-endpoints.md` | 追加 | VPP 电价数据报表 API 端点 |
| `state/full_sweep.json` | 更新 | sweep_round=23, repo_last_sweep 时间更新 |
