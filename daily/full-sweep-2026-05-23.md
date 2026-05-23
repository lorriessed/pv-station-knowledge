# 全量通读报告 2026-05-23 (第11轮)

## 概要

- **通读日期**: 2026-05-23
- **轮次**: 第 11 轮
- **本轮通读仓库**: 5 个
- **从未通读仓库**: 0 个（全部 100 个仓库已完成）

## 本轮通读仓库清单

| # | 仓库 | 分支 | HEAD | 业务文件数 | 备注 |
|---|---|---|---|---|---|
| 1 | rrsjk-admin-web | master | a132fbeb100d | 604 | CBS管理后台，已有大量知识覆盖 |
| 2 | rrsjk-app-web | master | 221bf0a5770b | 25 | 健康水站H5（非PVS核心） |
| 3 | rrsjk-appapi-web | master | 62125d3c0439 | 103 | 健康水站API网关（非PVS核心） |
| 4 | rrsjk-async-import-export | master | a762cdf9a17f | 30 | 异步导入导出服务 |
| 5 | rrsjk-cms-service | master | 06614f56a111 | 136 | CMS内容管理服务 |

## 知识库更新

### 新增 API 端点 (data/api-endpoints.md)

1. **用户问题管理 API** — `/userProblemManagement` (rrsjk-admin-web)
2. **BT股转模式及中核资产管理 API** — `/btAssetManagement/` (rrsjk-admin-web)
3. **BT资金资产分配明细 API** — `/btFundAssetAllocateDetail/` (rrsjk-admin-web)
4. **异步导入导出任务 API** — `/task` (rrsjk-async-import-export)

### 更新文件

| 文件 | 更新内容 |
|---|---|
| `data/api-endpoints.md` | 新增 4 个 API 端点组 |
| `modules/repositories.md` | 更新 5 个仓库通读日期为 2026-05-23 |
| `index.md` | 修正通读进度为 100/100，更新时间戳 |

## 各仓库核心发现

### 1. rrsjk-admin-web (CBS管理后台)

**已覆盖度**: 高（此前已通读多次）

**新发现**:
- `UserProblemManagementController` — 用户问题管理，支持按用户账号/分中心/时间范围查询，EasyExcel导出
- `BtAssetManagementController` — BT股转模式资产管理，支持导入/导出/分页查询，导入时关联 light_station 和 BtProjectCompanyMasterData
- `BtFundAssetAllocateDetailController` — BT资金资产分配明细
- `BtFundReportController` / `BtFundAssetManagementReportController` — BT资金资产管理报表
- `LightAssetInProgressReportController` / `LightAssetManagementReportController` — 资产在途/资产管理报表

**关键业务逻辑** (已确认):
- Shiro安全配置: VPP调用CBS请款采购流程的白名单接口 (`/invoiceCheck/getInvoiceInfoForVpp.do` 等)
- 异步导出线程池: CPU核数×2核心线程，CPU核数×4最大线程
- 电站迁移三级审核: 片长 → 市场总监 → 资产部

### 2. rrsjk-app-web (健康水站H5)

**PVS业务价值**: 低（健康水站/饮水机业务，非光伏）

**核心职责**:
- 健康水站扫码打水 (`/h5/fetchWater`)
- 水卡充值微信支付 (`/h5/wxpay`)
- 海尔招聘报名 (`/haierRecuit`)
- 微店主加盟流程 (`/shopkeeperJoin`)
- 文章/评论系统 (`/article`)

**技术栈**: Spring Boot 2.2.4, Freemarker, Shiro(未启用), Redis session, 微信SDK

### 3. rrsjk-appapi-web (健康水站API网关)

**PVS业务价值**: 低（健康水站/饮水机业务，非光伏）

**核心职责**:
- 水站App接口 (`/1/water/app/*`) — 轮播图、银行卡绑定、电站数据、积分兑换、抽奖等
- 外部系统对接:
  - 车小微云仓 (`/cxw/postShopData`) — MD5签名验证
  - 消费金融 (`/xfjr/getInfoForConsumerFinance`) — MD5签名验证
  - 光伏数据上传 (`/1/water/powerStationData/sendUserAllData`) — 雨丁等供应商上传发电数据
- OAuth2 JWT认证 (`Oauth2Config`)
- Swagger/Knife4j API文档

**⚠️ 注意**: 虽然名为 "appapi"，但主要服务健康水站业务。光伏数据上传接口 (`PowerStationDataController`) 是早期光伏数据的采集入口，已迁移至 rrsjk-light-data-service。

### 4. rrsjk-async-import-export (异步导入导出服务)

**PVS业务价值**: 中（基础设施服务）

**核心职责**: 大数量导出异步化处理

**技术架构**:
- **RocketMQ 5.0.7**: 消息队列，Topic `ASYNC_EXPORT_TOPIC`，消费者 `AsyncExportMqListener`
- **双数据源**:
  - `lightDataSource` (Primary): 光伏库 rrsjk_light，Mapper: `LightStationMapper`
  - `localDataSource`: 本地任务库，Mapper: `AsyncImportExportTaskMapper`
- **OSS上传**: 导出文件上传至 `rrslnfile` bucket，路径 `async-import-export/prod/`
- **系统保护**: 导出前检查 CPU空闲率<30% 或 JVM使用率>95% 则拒绝
- **防重机制**: Redis分布式锁 `export_lock:{user}{taskCode}`，20分钟超时

**任务状态流转**: `0 待执行 → 1 执行中 → 2 成功/3 失败`

**当前导出任务**:
| taskCode | 名称 | Domain Bean | Service Bean |
|---|---|---|---|
| light_station_export | 电站列表导出 | LightStationExport | lightStationExportService |

**关键文件**:
- `AsyncImportExportTaskController.java` — 任务提交接口
- `AsyncExportMqListener.java` — MQ消费者，执行导出
- `AsyncExcelUtilService.java` — Excel导出 + OSS上传
- `ExportBeanEnum.java` — 导出任务枚举注册
- `LightDataSourceConfig.java` / `LocalDataSourceConfig.java` — 双数据源配置

### 5. rrsjk-cms-service (CMS内容管理)

**PVS业务价值**: 低（内容管理基础设施）

**核心职责**: 为乐农App/H5提供内容管理Dubbo服务

**主要Dubbo接口**:
| 接口 | 功能 |
|---|---|
| AppImageService | 乐农App轮播图 |
| CarouselService | M站首页轮播图 |
| ArticleItemService | 美好生活定制文章 |
| BulletinService | App快报 |
| CustomizedItemService | 乐农定制商品 |
| LiveInfoService | 微信直播信息同步 |
| LiveGoodsService | 直播商品 |
| LjCarouselService | 乐家诚品轮播图 |
| LjCategoryService | 乐家诚品分类 |
| HomePageFloorImageService | 首页楼层图片 |
| HomePageHotItemService | 首页热销商品 |
| HomePageRecommendService | 首页推荐商品 |

**技术特点**:
- 多模块: `rrsjk-cms-api` (接口定义) + `rrsjk-cms-impl` (实现)
- Guava Cache 缓存 (10分钟过期)
- Dubbo + Zookeeper 注册中心
- MyBatis + MySQL

## 证据等级

- **代码明确证明**: 所有 Controller 路由、Service 方法、数据源配置、MQ 消费者
- **配置明确证明**: application-dev.yml / application-prod.yml 中的数据库连接、RocketMQ 配置、OSS 配置
- **推断**: rrsjk-app-web 和 rrsjk-appapi-web 的健康水站业务与 PVS 光伏无直接关联

## 总结

本轮为第 11 轮全量通读，所有 100 个仓库已完成通读。5 个重扫仓库中：
- **rrsjk-admin-web**: 补充了 3 个之前遗漏的 Controller API 端点
- **rrsjk-async-import-export**: 首次完整记录了异步导出服务的架构和流程
- **rrsjk-app-web / rrsjk-appapi-web**: 标注为非PVS核心业务（健康水站）
- **rrsjk-cms-service**: 内容管理基础设施，已补充完整 Dubbo 接口列表
