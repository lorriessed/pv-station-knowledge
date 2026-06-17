# PVS 全量代码通读报告 — 2026-06-17 (第34轮)

## 通读概要

| 指标 | 数值 |
|---|---|
| 本轮通读仓库 | 5 个 |
| 零提交跳过 | 5 个 (100%) |
| 知识库文件更新 | 1 个 (modules/repositories.md) |
| Domain 文件更新 | 0 个 |
| 新增业务知识 | 0 条 |

## 通读仓库详情

### 1. rrsjk-admin-web (活跃度排名 #1)
- **最后提交**: 2026-06-12 (Merge #635 szn_rent_stop_20260525)
- **自上次通读以来新提交**: 0
- **KB 覆盖**: 20+ 文件 (admin-authz.md, cbs-management.md, settlement.md, policy.md, station-lifecycle.md 等)
- **策略**: 零提交跳过 ✅
- **最近提交摘要** (已在上轮捕获):
  - `refactor(lightoperationbank): 优化分中心权限校验逻辑` (sunzn, 06-12)
  - `Merge #634 fapSentRevocation` (代继宁, 06-12) — FAP发送撤销
  - `Merge #632 feature-wxr-20260521-audit` (于淼, 06-11) — 审核功能
  - `chore(frontend): 临时禁用图片驳回功能` (wangxiran, 06-11)
  - `fix(light): 修正负荷报告链接地址` (wangxiran, 06-11)

### 2. rrsjk-app-web (活跃度排名 #71)
- **最后提交**: 2025-04-07 (fastjson版本升级)
- **业务定位**: 健康水站 H5 应用 (WaterDispenser/WaterCard/水站打水/水卡充值)
- **PVS 相关性**: ❌ 非光伏业务，属于日日顺乐农健康水站项目
- **策略**: 外围陈旧跳过 ✅ (最后提交 > 14个月前)
- **技术栈**: Spring Boot 2.2 + Freemarker FTL + Dubbo + Shiro + Redis Session
- **关键依赖**: rrs-dispenser-api (水站服务), wechat-sdk, shoppingmall-core

### 3. rrsjk-appapi-web (活跃度排名 #37)
- **最后提交**: 2025-05-16 (fastjson/rrs-parent版本升级)
- **业务定位**: 健康水站 App API 网关 (OAuth2 + 水站运营/积分/直播/光伏数据上传)
- **PVS 相关性**: ❌ 非光伏业务 (虽有 PowerStationDataController 但是早期水站App的光伏数据透传接口，非PVS核心)
- **策略**: 外围陈旧跳过 ✅ (最后提交 > 13个月前)
- **技术栈**: Spring Boot 2.2 + OAuth2 JWT + Swagger/Knife4j + Dubbo + Redis + ActiveMQ
- **关键接口路径**: `/1/water/app/*` (水站App), `/xfjr/*` (消金数据), `/cxw/*` (车小微)

### 4. rrsjk-async-import-export (活跃度排名 #55)
- **最后提交**: 2025-10-17 (RocketMQ日志增强)
- **业务定位**: 异步导入导出工具服务 (RocketMQ + EasyExcel + OSS)
- **PVS 相关性**: ✅ 光伏相关 (LightStationExportService 电站列表导出)
- **策略**: 零提交跳过 ✅ (最后提交 > 8个月前)
- **架构**: HTTP API → RocketMQ → AsyncExportMqListener → EasyExcel大数据导出 → OSS上传 → 返回CDN链接
- **数据源**: 双数据源 (lightDataSource 光伏库 + localDataSource 任务库)
- **当前导出任务**: `LIGHT_STATION_EXPORT` (电站列表导出) — 枚举 ExportBeanEnum

### 5. rrsjk-cms-service (活跃度排名 #38)
- **最后提交**: 2025-04-08 (fastjson版本升级)
- **业务定位**: 乐农CMS内容管理服务 (轮播图/文章/直播/菜谱/商品推荐)
- **PVS 相关性**: ❌ 非光伏业务，属于日日顺乐农电商平台内容管理
- **策略**: 外围陈旧跳过 ✅ (最后提交 > 14个月前)
- **技术栈**: Spring Boot 2.3 + MyBatis + Dubbo + Guava Cache + 微信小程序SDK
- **主要模块**: AppImage(轮播图), ArticleItem(美好生活定制), LiveInfo(直播), Carousel(M站导航), CustomizedItem(乐农定制)

## 知识库更新记录

### 更新的文件
1. `modules/repositories.md` — 5 个仓库标记为 2026-06-17 通读，附跳过原因

### 未更新 Domain 文件的原因
所有 5 个仓库自上次通读以来均无新提交，无新业务逻辑需要沉淀。

## 备注

- 本轮是第34轮全量通读（122/122 100%覆盖后的第9轮重扫）
- 3 个外围陈旧仓库 (app-web, appapi-web, cms-service) 均为健康水站/乐农电商项目，与光伏业务无关
- rrsjk-admin-web 是核心CBS管理后台，最近活跃提交已在上一轮（~2026-06-12~16）捕获并沉淀到知识库
- rrsjk-async-import-export 是光伏相关的异步导出工具，当前仅支持电站列表导出，架构清晰
