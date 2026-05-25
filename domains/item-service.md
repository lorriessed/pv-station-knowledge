# 商品服务 (rrsjk-item-service)

更新时间: 2026-05-25

## 服务概述

**来源**: `rrsjk-item-service` 全量通读 (2026-05-25)

`rrsjk-item-service` 是光伏业务的统一商品/产品管理中心，负责 SPU/SKU 管理、类目体系、品牌管理、价格体系、套餐管理、商品搜索（ElasticSearch）等功能。

### 技术栈
- Spring Boot 2.2.4 + Dubbo 2.7.4.1 (Zookeeper 注册中心)
- MyBatis + MySQL
- ElasticSearch 6.5.1 (商品全文检索)
- Redis
- Prometheus + Micrometer 监控
- Snowflake ID 生成

### 架构
- `rrsjk-item-api` — Dubbo 接口定义 + DTO
- `rrsjk-item-impl` — 服务实现 + 配置

---

## 核心业务域

### 1. 商品管理 (Item/SKU/SPU)

**来源**: `rrsjk-item-api` → `ItemService.java`, `SkuService.java`, `SpuService.java` (代码明确证明)

#### 商品实体关系
- **SPU (Standard Product Unit)**: 标准商品单元，一个 SPU 下有多个 Item
- **Item**: 店铺级别的商品，一个 SPU 可被多个店铺发布为 Item
- **SKU**: 商品的最小库存单位，一个 Item 下有多个 SKU

#### 商品状态管理
- **审核状态** (`auditStatus`): 商品上架前需审核
- **显示状态**: `markShow()`, `markOperatorHide()`, `markUserHide()`, `markAllHide()`, `markGroupHide()` — 按角色维度控制可见性
- **上下架**: SKU 级别的上下架操作 (`skuOnOffShelf`)

#### 商品发布流程

**来源**: `rrsjk-item-api` → `ReleaseItemService.java` (代码明确证明)

1. **初始化**: `ReleaseItemInitService.getReleaseItemInit(spuId, shopType, shopId)` — 获取发布初始化数据
2. **SKU 价格校验**: `releaseSkuValidate()` — 验证 SKU 价格有效性
3. **商品信息校验**: `releaseShopItemValidate()` — 验证商品完整信息
4. **发布**: `releaseShopItem()` — 店铺发布商品
5. **编辑**: `modifyShopItem()` — 商品编辑
6. **复制**: `copyShopItem()` / `copyItemSku()` — 商品复制

#### 销售渠道体系

**来源**: `rrsjk-item-api` → `ReleaseItemRequest.java` (代码明确证明)

商品发布支持多种销售渠道，每种渠道有不同字段：

| 销售渠道 | 关键字段 |
|---|---|
| 零售 | `countySale` (县域代卖 0/1) |
| 零碳 | `zcMinType` (起购类型: 0普通/1倍数), `zcMinNumber` (起购量) |
| 企业客户 | `minNumber` (起购量) |
| 专业客户/批发 | `valueAddedShare` (增值分享), `xiaoweiId` (小小微), `bizRoleId` (业务角色编号) |

#### 辅材额度渠道

**来源**: `rrsjk-item-api` → `ItemService.java` (代码明确证明)

```java
List<Long> findShopForQuota();
```
查询计入辅材额度的下单店铺列表（电站并网设备、电站支架、电站线缆）。

---

### 2. 类目体系 (Category)

**来源**: `rrsjk-item-api` → `CategoryService.java`, `FrontCategoryService.java` (代码明确证明)

#### 后台类目 (Category)
- 树形结构: `findChildren(parentId)` — 查询子类目
- 属性管理: `findAttributeByCategoryId()`, `findValueByCateIdAndAttrId()`
- 三级类目体系，关联 SPU

#### 前台类目 (FrontCategory)
- 面向前端展示的类目，与后台类目通过 `CategoryMapping` 绑定
- `FrontCategoryCarousel` — 前台类目轮播图
- `FrontCategoryTopItem` — 前台类目置顶商品
- 支持启用/禁用/删除

---

### 3. 价格体系

**来源**: `rrsjk-item-api` → `ProductPriceService.java`, `ProductBreakevenPriceService.java`, `ProductPurchaseCostService.java` (代码明确证明)

#### 商品价格 (ProductPrice)
- 按 `skuCode` + `companyCode` + `purchaseType` 唯一标识
- 审核状态: `0` 待审核, `-1` 审核驳回, `1` 生效
- 查询方法: `getUnchecked()` (待审核/驳回), `getChecked()` (已生效)
- **@Deprecated**: 旧方法仅按 `skuCode` + `purchaseType` 查询（不区分公司代码），已废弃

#### 保本价 (ProductBreakevenPrice)
- 按 `skuCode` + `companyCode` 唯一标识
- **定时任务**: `updateNoticeObsFailRetry()` — 保本价修改通知 NH-OBS 失败重试
- **历史数据处理**: `noticeObsHistory()` — 历史数据补发

#### 采购成本 (ProductPurchaseCost)
- 按 `skuCode` + `companyCode` 查询最新有效记录: `getLastEffectiveByCompanyCode()`
- 支持批量插入 `batchInsert()`

---

### 4. 套餐管理 (SkuMeal)

**来源**: `rrsjk-item-api` → `SkuMealService.java` (代码明确证明)

- 套餐 SKU 关联子商品 SKU 列表
- 按 `skuId` 或 `itemId` 查询套餐关系

---

### 5. 零碳套餐 (ZeroCarbonItemSetMeal)

**来源**: `rrsjk-item-api` → `ZeroCarbonItemSetMealService.java`, `ZeroCarbonItemSetMealStockService.java` (代码明确证明)

#### 零碳套餐管理
- `createSetMeal()` — 创建套餐
- `updateSelfStatus()` — 更新套餐状态
- `updateToDelete()` — 标记删除
- `findAllByShop()` — 查询门店下所有套餐

#### 零碳套餐库存

**来源**: `rrsjk-item-api` → `ZeroCarbonItemSetMealStockService.java` (代码明确证明)

- `save()` — 保存库存
- `updateStock()` — 扣减库存
- `recoverStock()` — 恢复库存（退单场景）
- `getAvailableStockByCode()` — 查询可用库存
- **库存变更流水**: `ZeroCarbonItemSetMealStockChangeLogService` — 记录每次库存变更

---

### 6. 商品搜索 (ElasticSearch)

**来源**: `rrsjk-item-api` → `ItemSearchService.java`, `NewItemSearchService.java` (代码明确证明)

#### 旧搜索服务 (@Deprecated)
`ItemSearchService` 已标记为 `@Deprecated`，被 `NewItemSearchService` 替代。

#### 新搜索服务
`NewItemSearchService` 提供多种搜索场景：
- `findFavorate()` — 猜你喜欢（分未登录/小顺登录/用户登录）
- `findHomePage()` — 首页搜索
- `findCategory()` — 分类搜索
- `findPurchaseItem()` — 采购商品搜索
- `findGroupPurchaseItem()` — 团购商品搜索
- `findYzzItem()` — 云智妆商品搜索
- `findRuralShopsItem()` — 农村商店商品搜索
- `findLightCategory()` — 光伏分类搜索

#### 搜索索引

**来源**: `rrsjk-item-api` → `ItemIndexService.java` (代码明确证明)

- `index(itemId)` — 单个商品索引生成/更新
- `indexAll()` — 全量索引
- `indexRecently()` — 最近 7 天更新的商品索引

---

### 7. 定制饮品 (CustomDrinks)

**来源**: `rrsjk-item-api` → `CustomDrinksService.java` (代码明确证明)

- 非光伏核心业务，似乎是海尔其他业务的遗留功能
- 支持定制文字/图片详情
- 场景类型 (`usesType`): 定制场景分类
- 关联订单号: `linkOrderNo()`
- 取消定制: `cancelCustom()`

#### 定制语音 (CustomDrinksVoice)
- 按 `code` 查询语音配置

---

### 8. 云智妆 (Yzz)

**来源**: `rrsjk-item-api` → `YzzCategoryService.java`, `YzzCategoryItemService.java`, `YzzOptItemService.java` (代码明确证明)

- `YzzCategory` — 云智妆类目
- `YzzCategoryItem` — 云智妆类目-商品关联
- `YzzOptItem` — 云智妆优选商品
- 支持启用/禁用操作

---

### 9. 销售区域 (SaleArea)

**来源**: `rrsjk-item-api` → `SaleAreaService.java` (代码明确证明)

- 店铺可配置多个销售区域
- 支持设置默认区域: `defaultSaleArea()`, `defaultSaleAreaByShop()`
- 区域树查询: `findAreaTreeById()`
- 按省份查询: `findByProvince()`

---

### 10. 品牌管理 (Brand)

**来源**: `rrsjk-item-api` → `BrandService.java` (代码明确证明)

- `findAllBrand()` — 查询所有品牌
- `createBrand()` — 创建品牌
- `disabled()` / `enabled()` — 启用/禁用

---

### 11. 商品评价 (Comment)

**来源**: `rrsjk-item-api` → `CommentService.java` (代码明确证明)

- 首次评价: `addFirstComment()` (支持晒单图片)
- 追评: `addAdditionalComment()`
- 商家回复: `addReply()`, `addAdditionalReply()`
- 默认评价: `autoAddComment()` — 超时自动评价
- 展示控制: `markShow()`, `markHidden()`, `markAdditionalShow()`, `markAdditionalHidden()`

---

## 外部服务依赖

**来源**: `rrsjk-item-service` pom.xml (配置明确证明)

| 服务 | 依赖 |
|---|---|
| rrsjk-system-api | 系统基础服务 |
| rrsjk-merchant-api | 商户服务 |
| rrsjk-member-api | 会员服务 |
| rrsjk-trade-api | 交易服务 |
| rrs-dispenser-api | 老业务分发器（大量 exclusions） |

---

## 技术配置

### EventBus

**来源**: `rrsjk-item-impl` → `EventBusConfig.java` (代码明确证明)

- `itemEventBus` — 商品操作事件总线 (10-100 线程)
- `searchEventBus` — 搜索操作事件总线 (10-100 线程)
- `pointEventBus` — 积分操作事件总线 (10-100 线程)
- `smsEventBus` — 发送短信操作事件总线 (10-100 线程)

### Dubbo

**来源**: `rrsjk-item-impl` → `DubboConfig.java` (代码明确证明)

- 注册中心: Zookeeper
- 本地缓存: `/tmp/rrsjk-item-service`
- 超时: 10000ms

### 监控

**来源**: `rrsjk-item-impl` → `ActuatorConfig.java` (代码明确证明)

- Prometheus + Micrometer
- Instance tag: `{local_ip}:{profile}`

---

## 数据库表概要

| 表名 | 用途 |
|---|---|
| `item` | 商品主表 |
| `item_extras` | 商品扩展信息 |
| `item_image` | 商品图片 |
| `item_sale_channel` | 商品销售渠道关联 |
| `item_audit_apply` | 商品审核申请 |
| `item_audit_record` | 商品审核记录 |
| `item_operate_log` | 商品操作日志 |
| `item_page` | 商品分页信息 |
| `item_chuneng` | 储能商品 |
| `sku` | SKU 表 |
| `sku_meal` | 套餐关联表 |
| `sku_limited` | SKU 限购配置 |
| `sku_relate` | SKU 关联关系 |
| `spu` | 标准产品单元 |
| `spu_attribute_value` | SPU 属性值 |
| `spu_image` | SPU 图片 |
| `brand` | 品牌 |
| `category` | 后台类目 |
| `category_attribute` | 类目属性 |
| `category_attribute_value` | 属性值 |
| `category_mapping` | 前后台类目映射 |
| `front_category` | 前台类目 |
| `front_category_carousel` | 前台类目轮播图 |
| `front_category_top_item` | 前台类目置顶商品 |
| `sale_area` | 销售区域 |
| `sale_channel` | 销售渠道字典 |
| `settle_type` | 结算类型 |
| `shop_spu_plateform_rate` | 店铺 SPU 平台费率 |
| `product_price` | 商品价格 |
| `product_price_change_log` | 价格变更日志 |
| `product_breakeven_price` | 保本价 |
| `product_purchase_cost` | 采购成本 |
| `collect` | 商品收藏 |
| `comment` | 商品评价 |
| `comment_image` | 评价图片 |
| `custom_drinks` | 定制饮品 |
| `custom_drinks_detail` | 定制饮品详情 |
| `custom_drinks_voice` | 定制语音 |
| `zero_carbon_item_set_meal` | 零碳套餐 |
| `zero_carbon_item_set_meal_content` | 零碳套餐内容 |
| `zero_carbon_item_set_meal_stock` | 零碳套餐库存 |
| `zero_carbon_item_set_meal_stock_change_log` | 零碳套餐库存变更流水 |
| `yzz_category` | 云智妆类目 |
| `yzz_category_item` | 云智妆类目-商品关联 |
| `yzz_opt_item` | 云智妆优选商品 |
