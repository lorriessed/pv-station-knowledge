# MyBatis Mapper 索引

来源: master XML 静态扫描。

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/SaleArea.xml
- namespace: `com.rrsjk.item.dao.SaleAreaDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByShopId`, `select:findByShopIdAndName`, `select:findByShopIdAndDefault`, `select:countOf`, `select:findBy`, `select:findByProvince`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/CustomDrinks.xml
- namespace: `com.rrsjk.item.dao.CustomDrinksDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findCount`, `select:find`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/SaleChannel.xml
- namespace: `com.rrsjk.item.dao.SaleChannelDao`
- statements: `select:get`, `select:findBy`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ItemAuditApply.xml
- namespace: `com.rrsjk.item.dao.ItemAuditApplyDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getLastByItemId`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/SettleType.xml
- namespace: `com.rrsjk.item.dao.SettleTypeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/productBreakevenPriceChangeNoticeObs.xml
- namespace: `com.rrsjk.item.dao.ProductBreakevenPriceChangeNoticeObsDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getNoticeFail`
- tables: `id`, `product_breakeven_price`, `product_breakeven_price_change_notice_obs`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ItemAuditRecord.xml
- namespace: `com.rrsjk.item.dao.ItemAuditRecordDao`
- statements: `insert:create`, `update:update`, `select:get`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/Collect.xml
- namespace: `com.rrsjk.item.dao.CollectDao`
- statements: `insert:insert`, `select:findByMemberIdAndItemId`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/Spu.xml
- namespace: `com.rrsjk.item.dao.SpuDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByCategoryId`, `select:findByParams`, `select:findCount`, `select:find`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ItemSearchRecord.xml
- namespace: `com.rrsjk.item.dao.ItemSearchRecordDao`
- statements: `insert:create`, `select:findByMemberId`, `select:getByMemberIdAndContent`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/SkuMeal.xml
- namespace: `com.rrsjk.item.dao.SkuMealDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByItemId`, `select:findBySkuId`, `select:countOf`, `select:findBy`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ItemImage.xml
- namespace: `com.rrsjk.item.dao.ItemImageDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByItemId`, `select:findByItemIdAndImageType`, `update:disableBannerByItemId`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/FrontCategory.xml
- namespace: `com.rrsjk.item.dao.FrontCategoryDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findCount`, `select:find`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/SkuLimited.xml
- namespace: `com.rrsjk.item.dao.SkuLimitedDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getBySkuId`, `select:countOf`, `select:findBy`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ZeroCarbonItemSetMealStockChangeLogMapper.xml
- namespace: `com.rrsjk.item.dao.ZeroCarbonItemSetMealStockChangeLogDao`
- statements: `insert:created`, `insert:batchInsert`, `update:updated`, `delete:deleteById`, `select:selectById`, `select:findList`, `select:selectByCondition`, `select:count`, `select:findCount`, `select:findPage`, `select:getAllBySetMealCode`, `select:countByOrderNoAndType`, `select:findByOrderNoAndType`
- tables: `id`, `zero_carbon_item_set_meal_stock_change_log`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/YzzOptItem.xml
- namespace: `com.rrsjk.item.dao.YzzOptItemDao`
- statements: `insert:insert`, `update:update`, `select:find`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/CustomDrinksDetail.xml
- namespace: `com.rrsjk.item.dao.CustomDrinksDetailDao`
- statements: `insert:create`, `update:update`, `select:findByCustomId`, `delete:deleteByPrimaryKey`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ItemSaleChannel.xml
- namespace: `com.rrsjk.item.dao.ItemSaleChannelDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByItemId`, `delete:deleteByItemId`, `select:findBySaleChannel`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ProductPrice.xml
- namespace: `com.rrsjk.item.dao.ProductPriceDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findCount`, `select:find`, `select:findSkuTaxRate`, `select:selectProductPriceByMultiCondition`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/CbsItemSku.xml
- namespace: `com.rrsjk.item.dao.CbsItemSkuDao`
- statements: `select:countOf`, `select:findBy`
- tables: `item`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ShopSpuPlateformRate.xml
- namespace: `com.rrsjk.item.dao.ShopSpuPlateformRateDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findCount`, `select:find`, `select:getByShopIdAndSpuId`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ProductBreakevenPrice.xml
- namespace: `com.rrsjk.item.dao.ProductBreakevenPriceDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findCount`, `select:find`, `select:getBySkuCode`, `select:getBySkuCodeAndCompanyCode`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/CustomDrinksVoice.xml
- namespace: `com.rrsjk.item.dao.CustomDrinksVoiceDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:getByCode`, `select:findCount`, `select:find`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/Category.xml
- namespace: `com.rrsjk.item.dao.CategoryDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findChildren`, `select:findCount`, `select:findMaxSort`, `select:findByName`
- tables: `category`, `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/SkuRelate.xml
- namespace: `com.rrsjk.item.dao.SkuRelateDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getEnableBySkuId`, `select:countOf`, `select:findBy`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ZeroCarbonItemSetMealStockMapper.xml
- namespace: `com.rrsjk.item.dao.ZeroCarbonItemSetMealStockDao`
- statements: `insert:created`, `insert:batchInsert`, `update:updated`, `delete:deleteById`, `select:selectById`, `select:findList`, `select:selectByCondition`, `select:count`, `select:findCount`, `select:findPage`, `select:getAvailableStockByCode`, `select:selectByPlanStockCode`, `update:updateStockById`, `update:recoverStock`, `select:findGroupByKeyword`
- tables: `id`, `zero_carbon_item_set_meal_stock`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ShopTypeSaleChannel.xml
- namespace: `com.rrsjk.item.dao.ShopTypeSaleChannelDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByShopType`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/CategoryAttributeValue.xml
- namespace: `com.rrsjk.item.dao.CategoryAttributeValueDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:find`, `select:findByAttributeId`, `update:delCateAttrValByCateId`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/Item.xml
- namespace: `com.rrsjk.item.dao.ItemDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:batchGet`, `select:countOf`, `select:findBy`, `select:findBySpuId`, `select:findBySaleAreaId`, `update:addSale`, `select:findByItemIdList`, `select:findCountByItemIdList`, `select:findByParam`, `select:findItemBrandName`, `select:findItemBrandNameForOther`, `select:findShopForQuota`
- tables: `category`, `id`, `item`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/FrontCategoryTopItem.xml
- namespace: `com.rrsjk.item.dao.FrontCategoryTopItemDao`
- statements: `insert:create`, `update:update`, `select:getByItemId`, `select:get`, `delete:del`, `select:findCount`, `select:find`
- tables: `front_category_top_item`, `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/Brand.xml
- namespace: `com.rrsjk.item.dao.BrandDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByParam`, `select:findCount`, `select:find`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/CategoryMapping.xml
- namespace: `com.rrsjk.item.dao.CategoryMappingDao`
- statements: `insert:create`, `update:update`, `select:findCount`, `select:find`, `select:findByParams`, `delete:delete`
- tables: `front_category`, `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/CategoryAttribute.xml
- namespace: `com.rrsjk.item.dao.CategoryAttributeDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:find`, `select:findCount`, `update:delCateAttrByCateId`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/YzzCategoryItem.xml
- namespace: `com.rrsjk.item.dao.YzzCategoryItemDao`
- statements: `insert:insert`, `update:update`, `select:findByCategoryId`, `select:findCount`, `select:find`, `select:getByItemId`, `select:getById`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ProductPriceChangeLog.xml
- namespace: `com.rrsjk.item.dao.ProductPriceChangeLogDao`
- statements: `insert:create`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/Comment.xml
- namespace: `com.rrsjk.item.dao.CommentDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/FrontCategoryCarousel.xml
- namespace: `com.rrsjk.item.dao.FrontCategoryCarouselDao`
- statements: `insert:create`, `update:update`, `select:findShowList`, `select:findCount`, `select:find`, `delete:delete`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/SpuAttributeValue.xml
- namespace: `com.rrsjk.item.dao.SpuAttributeValueDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:get`, `select:find`, `delete:delete`, `select:findBySpuIdAndType`, `update:updateStatusBySpuId`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ItemExtras.xml
- namespace: `com.rrsjk.item.dao.ItemExtrasDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByItemId`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ProductData.xml
- namespace: `com.rrsjk.item.dao.ProductDataDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getBySkuCode`, `select:getBySkuCodeAndCompanyCode`, `select:findCount`, `select:find`, `select:findByParams`, `select:findBySkus`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ItemSku.xml
- namespace: `com.rrsjk.item.dao.ItemSkuDao`
- statements: `select:countOf`, `select:findBy`, `select:sumPriceByMealSkuId`, `select:findByMealSkuId`
- tables: `item`, `sku`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ProductPurchaseCost.xml
- namespace: `com.rrsjk.item.dao.ProductPurchaseCostDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findCount`, `select:find`, `select:getLastEffective`, `select:getLastEffectiveByCompanyCode`, `insert:batchInsert`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/SpuImage.xml
- namespace: `com.rrsjk.item.dao.SpuImageDao`
- statements: `insert:create`, `update:update`, `select:get`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ZeroCarbonItemSetMeal.xml
- namespace: `com.rrsjk.item.dao.ZeroCarbonItemSetMealDao`
- statements: `insert:created`, `update:updated`, `select:get`, `select:findCount`, `select:findPage`, `update:updateToDelete`, `select:findAllByShop`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ItemOperateLog.xml
- namespace: `com.rrsjk.item.dao.ItemOperateLogDao`
- statements: `insert:create`, `update:update`, `select:get`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ZeroCarbonItemSetMealContent.xml
- namespace: `com.rrsjk.item.dao.ZeroCarbonItemSetMealContentDao`
- statements: `insert:created`, `insert:batchInsert`, `update:update`, `select:findList`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/YzzCategory.xml
- namespace: `com.rrsjk.item.dao.YzzCategoryDao`
- statements: `insert:insert`, `update:update`, `select:findCategoryList`, `select:findCount`, `select:find`, `select:findOtherCategoryList`, `select:getById`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ItemChuneng.xml
- namespace: `com.rrsjk.item.dao.ItemChunengDao`
- statements: `select:findBySort`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/Sku.xml
- namespace: `com.rrsjk.item.dao.SkuDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByItemId`, `select:findBySkuCode`, `select:findByItemIdAndStatus`, `select:findByItemIdAndAuditStatus`, `select:countOf`, `select:findBy`
- tables: `id`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ItemPage.xml
- namespace: `com.rrsjk.item.dao.ItemPageDao`
- statements: `select:countOf`, `select:findBy`
- tables: `item`

## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/CommentImage.xml
- namespace: `com.rrsjk.item.dao.CommentImageDao`
- statements: `insert:create`, `insert:batchInsert`, `select:findByCommentId`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/shop/VOMProductPriceMapper.xml
- namespace: `com.rrsjk.migration.shop.dao.VOMProductPriceDao`
- statements: `select:findInfo`, `select:batchGet`
- tables: `vom_product_price`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/shop/WarehouseStraightProductsMapper.xml
- namespace: `com.rrsjk.migration.shop.dao.WarehouseStraightProductsDao`
- statements: `select:findAddInfo`, `select:findDelInfo`, `select:batchGet`
- tables: `WarehouseStraightProducts`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/shop/ShopSupplier.xml
- namespace: `com.rrsjk.migration.shop.dao.ShopSupplierDao`
- statements: `select:batchGet`, `select:findInfo`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/shop/ShopMemberAddressMapper.xml
- namespace: `com.rrsjk.migration.shop.dao.ShopMemberAddressDao`
- statements: `insert:insert`, `insert:batchInsert`, `select:findByMemberId`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/shop/MemberLoginInfoMapper.xml
- namespace: `com.rrsjk.migration.shop.dao.ShopMemberLoginInfoDao`
- statements: `insert:insertLoginInfo`, `select:getMemberLoginInfo`, `select:getLoginInfoByLoginName`, `select:getLoginInfoByLoginNameAndMemberId`
- tables: `LoginInfo`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/shop/VOMProductDataMapper.xml
- namespace: `com.rrsjk.migration.shop.dao.VOMProductDataDao`
- statements: `select:findInfo`
- tables: `VOMProductData`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/shop/BreakevenPriceMapper.xml
- namespace: `com.rrsjk.migration.shop.dao.BreakevenPricesDao`
- statements: `select:findInfo`
- tables: `BreakevenPrices`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/shop/ShopMembersMapper.xml
- namespace: `com.rrsjk.migration.shop.dao.ShopMembersDao`
- statements: `insert:addMember`, `select:getMemberById`
- tables: `Members`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/merchant/MerchantResource.xml
- namespace: `com.rrsjk.migration.merchant.dao.MerchantResourceDao`
- statements: `insert:create`, `insert:batchInsert`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/merchant/Supplier.xml
- namespace: `com.rrsjk.migration.merchant.dao.SupplierDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByMerchantId`, `select:getBySupplierCode`
- tables: `id`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/merchant/Merchant.xml
- namespace: `com.rrsjk.migration.merchant.dao.MerchantDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByMemberId`, `select:getByTaxCode`, `select:getBySupplierCode`
- tables: `id`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/merchant/ProfessionalCustomer.xml
- namespace: `com.rrsjk.migration.merchant.dao.ProfessionalCustomerDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByMerchantId`
- tables: `id`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/merchant/ShopExtras.xml
- namespace: `com.rrsjk.migration.merchant.dao.ShopExtrasDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByShopId`
- tables: `id`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/merchant/MerchantExtras.xml
- namespace: `com.rrsjk.migration.merchant.dao.MerchantExtrasDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByMerchantId`
- tables: `id`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/merchant/CorporateClient.xml
- namespace: `com.rrsjk.migration.merchant.dao.CorporateClientDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByMerchantId`
- tables: `id`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/merchant/Shop.xml
- namespace: `com.rrsjk.migration.merchant.dao.ShopDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByLnShopId`, `select:findAll`
- tables: `id`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/rrs/RrsShopExtra.xml
- namespace: `com.rrsjk.migration.rrs.dao.RrsShopExtraDao`
- statements: `select:findByShopId`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/rrs/RrsShop.xml
- namespace: `com.rrsjk.migration.rrs.dao.RrsShopDao`
- statements: `select:batchGet`, `select:getById`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/portal/BusinessFee.xml
- namespace: `com.rrsjk.migration.portal.dao.BusinessFeeDao`
- statements: `select:getByApplyId`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/portal/BusinessContract.xml
- namespace: `com.rrsjk.migration.portal.dao.BusinessContractDao`
- statements: `select:getByApplyId`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/portal/BusinessApply.xml
- namespace: `com.rrsjk.migration.portal.dao.BusinessApplyDao`
- statements: `insert:insert`, `update:update`, `update:updateForce`, `select:getById`, `select:findProfessional`
- tables: `id`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/system/SystemSysUser.xml
- namespace: `com.rrsjk.migration.system.dao.SystemSysUserDao`
- statements: `select:getPasswordByLoginId`, `select:listInfo`
- tables: `sys_user`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/SaleChannel.xml
- namespace: `com.rrsjk.migration.item.dao.SaleChannelDao`
- statements: `select:get`, `select:findBy`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/Spu.xml
- namespace: `com.rrsjk.migration.item.dao.SpuDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:getMaxSpuId`
- tables: `id`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/ItemImage.xml
- namespace: `com.rrsjk.migration.item.dao.ItemImageDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:get`, `select:findByItemId`
- tables: `id`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/ItemSaleChannel.xml
- namespace: `com.rrsjk.migration.item.dao.ItemSaleChannelDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:get`, `select:findByItemId`, `delete:deleteByItemId`
- tables: `id`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/ProductPrice.xml
- namespace: `com.rrsjk.migration.item.dao.ProductPriceDao`
- statements: `insert:create`, `update:update`, `select:getBySkuAndPurchaseType`, `select:getCheckedBySkuAndPurchaseType`
- tables: `id`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/ShopSpuPlateformRate.xml
- namespace: `com.rrsjk.migration.item.dao.ShopSpuPlateformRateDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByShopIdAndSpuId`
- tables: `id`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/ProductBreakevenPrice.xml
- namespace: `com.rrsjk.migration.item.dao.ProductBreakevenPriceDao`
- statements: `insert:create`, `update:update`, `select:getBySkuCode`
- tables: `id`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/CategoryAttributeValue.xml
- namespace: `com.rrsjk.migration.item.dao.CategoryAttributeValueDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:find`, `select:findByAttributeId`, `update:delCateAttrValByCateId`
- tables: `id`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/Item.xml
- namespace: `com.rrsjk.migration.item.dao.ItemDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:get`, `select:batchGet`, `select:getMaxProductId`
- tables: `id`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/Brand.xml
- namespace: `com.rrsjk.migration.item.dao.BrandDao`
- statements: `select:getByBrandName`, `select:findAllBrand`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/CategoryAttribute.xml
- namespace: `com.rrsjk.migration.item.dao.CategoryAttributeDao`
- statements: `select:get`, `select:findByCategoryId`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/Comment.xml
- namespace: `com.rrsjk.migration.item.dao.CommentDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByParams`
- tables: `id`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/SpuAttributeValue.xml
- namespace: `com.rrsjk.migration.item.dao.SpuAttributeValueDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:get`, `select:findBy`
- tables: `id`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/ItemExtras.xml
- namespace: `com.rrsjk.migration.item.dao.ItemExtrasDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:get`, `select:getByItemId`
- tables: `id`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/ProductData.xml
- namespace: `com.rrsjk.migration.item.dao.ProductDataDao`
- statements: `insert:create`, `update:update`, `select:getBySkuCode`
- tables: `id`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/ProductPurchaseCost.xml
- namespace: `com.rrsjk.migration.item.dao.ProductPurchaseCostDao`
- statements: `insert:create`, `update:update`, `select:getBySkuCodeAndEffectTime`
- tables: `id`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/Sku.xml
- namespace: `com.rrsjk.migration.item.dao.SkuDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:get`, `select:getByItemId`
- tables: `id`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/CommentImage.xml
- namespace: `com.rrsjk.migration.item.dao.CommentImageDao`
- statements: `insert:create`, `insert:batchInsert`, `select:findByCommentId`, `delete:delete`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/ln/ProductOrderAppraiseImgs.xml
- namespace: `com.rrsjk.migration.ln.dao.ProductOrderAppraiseImgsDao`
- statements: `select:findBy`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/ln/ProductImgs.xml
- namespace: `com.rrsjk.migration.ln.dao.ProductImgsDao`
- statements: `select:findBy`, `select:getById`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/ln/LnProduct.xml
- namespace: `com.rrsjk.migration.ln.dao.LnProductDao`
- statements: `select:findBy`, `select:getBrandId`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/ln/ReceiveAddress.xml
- namespace: `com.rrsjk.migration.ln.dao.ReceiveAddressDao`
- statements: `select:findBy`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/ln/SalesOrganization.xml
- namespace: `com.rrsjk.migration.ln.dao.SalesOrganizationDao`
- statements: `select:batchGet`, `select:getBySoId`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/ln/ProductCategory.xml
- namespace: `com.rrsjk.migration.ln.dao.ProductCategoryDao`
- statements: `select:findBy`, `select:getByPcId`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/ln/SysUser.xml
- namespace: `com.rrsjk.migration.ln.dao.SysUserDao`
- statements: `select:getBySalesOrganizationId`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/ln/Mdm.xml
- namespace: `com.rrsjk.migration.ln.dao.MdmDao`
- statements: `select:listMdm`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/ln/ProductStock.xml
- namespace: `com.rrsjk.migration.ln.dao.ProductStockDao`
- statements: `select:findBy`, `select:getById`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/ln/ProductBrand.xml
- namespace: `com.rrsjk.migration.ln.dao.ProductBrandDao`
- statements: `select:findBy`, `select:getById`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/ln/ProductCategoryCommission.xml
- namespace: `com.rrsjk.migration.ln.dao.ProductCategoryCommissionDao`
- statements: `select:findBy`, `select:getByPccId`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/ln/ProductUnit.xml
- namespace: `com.rrsjk.migration.ln.dao.ProductUnitDao`
- statements: `select:findBy`, `select:getById`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/ln/ProductOrderAppraise.xml
- namespace: `com.rrsjk.migration.ln.dao.ProductOrderAppraiseDao`
- statements: `select:batchGet`, `select:getOrderNoByOrderId`
- tables: `product_order`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/member/LoginInfo.xml
- namespace: `com.rrsjk.migration.member.dao.LoginInfoDao`
- statements: `insert:create`, `select:getByLoginId`, `select:getMemberLoginInfos`, `update:changePassword`
- tables: `id`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/member/MemberRole.xml
- namespace: `com.rrsjk.migration.member.dao.MemberRoleDao`
- statements: `insert:create`, `select:getMemberRoles`, `update:cancelRole`, `update:enableRole`
- tables: `id`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/mdm/SecurityUser.xml
- namespace: `com.rrsjk.migration.mdm.dao.SecurityUserDao`
- statements: `select:getByPartyId`
- tables: `security_user`

## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/mdm/Organization.xml
- namespace: `com.rrsjk.migration.mdm.dao.OrganizationDao`
- statements: `select:getByPartyId`
- tables: `organization`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightOperationProviderExpandLog.xml
- namespace: `com.rrsjk.light.operation.dao.LightOperationProviderExpandLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/OperationModelStation.xml
- namespace: `com.rrsjk.light.operation.dao.OperationModelStationDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightWorkOrderImg.xml
- namespace: `com.rrsjk.light.operation.dao.LightWorkOrderImgDao`
- statements: `select:findBy`, `insert:create`, `insert:batchInsert`, `delete:deleteByWorkOrderSn`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/OperationFaultDetailReport.xml
- namespace: `com.rrsjk.light.operation.dao.OperationFaultDetailReportDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findCloseOrder`, `select:findCloseOrderXiaoXiang`
- tables: `id`, `light_operation_work_order`, `light_work_order`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightOperationCapital.xml
- namespace: `com.rrsjk.light.operation.dao.LightOperationCapitalDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightFaultLevel.xml
- namespace: `com.rrsjk.light.operation.dao.LightFaultLevelDao`
- statements: `insert:create`, `update:update`, `select:findBy`, `select:countOf`, `select:getById`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/OperationMaintenanceConfig.xml
- namespace: `com.rrsjk.light.operation.dao.OperationMaintenanceConfigDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightElectricUnusual.xml
- namespace: `com.rrsjk.light.operation.dao.LightElectricUnusualDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:updateDays`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightStationInsuranceLog.xml
- namespace: `com.rrsjk.light.operation.dao.LightStationInsuranceLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightTrippingOperation.xml
- namespace: `com.rrsjk.light.operation.dao.LightTrippingOperationDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightOperationCapitalPoily.xml
- namespace: `com.rrsjk.light.operation.dao.LightOperationCapitalPoilyDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:deleteByRelationId`, `select:getByRelationId`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightFaultDictionary.xml
- namespace: `com.rrsjk.light.operation.dao.LightFaultDictionaryDao`
- statements: `insert:create`, `select:get`, `select:findByParentId`, `select:findByParams`, `select:findByParamsThird`, `select:countOf`, `update:update`, `update:updateByParentId`, `select:findFirst`, `select:findSecondByParentId`, `select:findThirdByParentId`, `select:second`, `select:sortByAsc`, `select:sortByDesc`, `select:sortByAscSecond`, `select:sortByDescSecond`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightNefficient.xml
- namespace: `com.rrsjk.light.operation.dao.LightNefficientDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightOperationLossManagementLog.xml
- namespace: `com.rrsjk.light.operation.dao.LightOperationLossManagementLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/HdsMemberRole.xml
- namespace: `com.rrsjk.light.operation.dao.HdsMemberRoleDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightWorkOrderModule.xml
- namespace: `com.rrsjk.light.operation.dao.LightWorkOrderModuleDao`
- statements: `select:findBy`, `insert:create`, `insert:batchInsert`, `delete:deleteByWorkOrderSn`, `update:update`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/OperationScreenModel.xml
- namespace: `com.rrsjk.light.operation.dao.OperationScreenModelDao`
- statements: `insert:create`, `update:update`, `delete:delete`, `select:findBy`, `select:countOf`, `select:getById`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightWorkOrderProcess.xml
- namespace: `com.rrsjk.light.operation.dao.LightWorkOrderProcessDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightOperationAdmin.xml
- namespace: `com.rrsjk.light.operation.dao.LightOperationAdminDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightRepairOrderReason.xml
- namespace: `com.rrsjk.light.operation.dao.LightRepairOrderReasonDao`
- statements: `insert:create`, `select:findBy`, `select:countOf`, `select:getById`, `update:update`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/SocializationStation.xml
- namespace: `com.rrsjk.light.operation.dao.SocializationStationDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `insert:batchInsertOrUpdate`, `update:batchUpdate`
- tables: `id`, `socialization_station`, `station_code`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightOperationCapitalPartner.xml
- namespace: `com.rrsjk.light.operation.dao.LightOperationCapitalPartnerDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:deleteByRelationId`, `select:getByRelationId`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightOperationCertification.xml
- namespace: `com.rrsjk.light.operation.dao.LightOperationCertificationDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByMemberId`, `select:findByHds`, `select:countOfHds`, `select:findByMemberId`, `select:getByMemberIdZeroCarbon`
- tables: `id`, `light_operation_provider`, `light_zero_carbon_operation_provider`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightCloseReason.xml
- namespace: `com.rrsjk.light.operation.dao.LightCloseReasonDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightStationInverterChange.xml
- namespace: `com.rrsjk.light.operation.dao.LightStationInverterChangeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/OperationAlarmRate.xml
- namespace: `com.rrsjk.light.operation.dao.OperationAlarmRateDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:totalCount`, `select:getWrongList`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/SocializationContractInfo.xml
- namespace: `com.rrsjk.light.operation.dao.SocializationContractInfoDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/OperationMaintenancePolicy.xml
- namespace: `com.rrsjk.light.operation.dao.OperationMaintenancePolicyDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:delByRelationId`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightNefficientStation.xml
- namespace: `com.rrsjk.light.operation.dao.LightNefficientStationDao`
- statements: `select:findBy`, `select:findByNoClose`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightZeroCarbonOperationProvider.xml
- namespace: `com.rrsjk.light.operation.dao.LightZeroCarbonOperationProviderDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByMemberId`, `select:findByDto`, `select:countOfDto`, `select:getByMemberId`, `select:getByOpName`, `update:updateCallBack`
- tables: `id`, `rrsjk_light.light_elec_contract`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightOpStaff.xml
- namespace: `com.rrsjk.light.operation.dao.LightOpStaffDao`
- statements: `insert:create`, `update:update`, `select:findBy`, `select:hdsFindBy`, `select:countOf`, `select:hdsCountOf`, `select:getById`, `select:findByMobileList`, `select:findstaffByOpCodeList`, `select:getByStaffNo`, `select:getByMobile`, `select:getList`, `select:checkOverdue`, `select:findByMemberIdOrMobile`, `select:getOnJobStaffByMobile`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightStationPolicyNo.xml
- namespace: `com.rrsjk.light.operation.dao.LightStationPolicyNoDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:batchUpdateIsDelByIds`, `select:findBySht`, `select:countOfSht`, `select:findStationCodes`, `select:findByInCmb`, `select:countOfInCmb`
- tables: `cmb_leasing_station`, `id`, `light_station_policy_no`, `rrsjk_light.light_station`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightOperationCapitalLog.xml
- namespace: `com.rrsjk.light.operation.dao.LightOperationCapitalLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightWorkOrderZh.xml
- namespace: `com.rrsjk.light.operation.dao.LightWorkOrderZhDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteInvalidData`, `select:getByWorkOrderSn`
- tables: `id`, `light_work_order`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/OperationMaintenanceProcess.xml
- namespace: `com.rrsjk.light.operation.dao.OperationMaintenanceProcessDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightOperationProviderExpand.xml
- namespace: `com.rrsjk.light.operation.dao.LightOperationProviderExpandDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByMemberId`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightCsOrder.xml
- namespace: `com.rrsjk.light.operation.dao.LightCsOrderDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `update:updateByStatus`, `insert:batchInsert`, `select:getById`, `select:getBySn`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightWorkOrderType.xml
- namespace: `com.rrsjk.light.operation.dao.LightWorkOrderTypeDao`
- statements: `select:countOf`, `select:findBy`, `insert:create`, `select:get`, `select:findByParentId`, `update:update`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightOperationProvider.xml
- namespace: `com.rrsjk.light.operation.dao.LightOperationProviderDao`
- statements: `insert:create`, `insert:createByRemind`, `update:update`, `select:getById`, `select:getByMemberId`, `select:getByOpCode`, `select:getByMemberIds`, `select:getByName`, `select:findBy`, `select:getByCenterCode`, `select:getByCenterCodeList`, `select:countOf`, `update:addDeposit`, `update:substractDeposit`, `select:groupByName`
- tables: `id`, `light_operation_provider`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightFaultFreeConfig.xml
- namespace: `com.rrsjk.light.operation.dao.LightFaultFreeConfigDao`
- statements: `insert:create`, `update:update`, `select:findtimeConfig`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightFaultCodeRule.xml
- namespace: `com.rrsjk.light.operation.dao.LightFaultCodeRuleDao`
- statements: `select:findBy`, `select:countOf`, `select:getById`, `insert:batchInsert`, `update:update`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightWorkOrder.xml
- namespace: `com.rrsjk.light.operation.dao.LightWorkOrderDao`
- statements: `select:findBy`, `select:findByAll`, `select:findByPageExcel`, `select:findNotCloseOrder`, `select:countOf`, `insert:create`, `update:updateByStatus`, `update:update`, `select:getBySn`, `select:countOfSettle`, `delete:deleteInvalidData`, `select:findWorkOrderByUnEnableStation`, `update:updateByIsNull`, `select:findWorkOrderByFautReasonIsNull`
- tables: `id`, `light_cs_order`, `light_repair_order`, `light_work_order`, `rrsjk_light.light_station`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightOpStaffRegion.xml
- namespace: `com.rrsjk.light.operation.dao.LightOpStaffRegionDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteByStaffNo`, `select:getByStaffNoOrmemberId`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightOpContract.xml
- namespace: `com.rrsjk.light.operation.dao.LightOpContractDao`
- statements: `select:getByMemberId`, `insert:create`, `update:update`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/BusinessCooperationIntention.xml
- namespace: `com.rrsjk.light.operation.dao.BusinessCooperationIntentionDao`
- statements: `insert:create`, `select:getById`, `select:findBy`, `select:countOf`, `update:update`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightModuleInfo.xml
- namespace: `com.rrsjk.light.operation.dao.LightModuleInfoDao`
- statements: `insert:create`, `update:update`, `select:findBy`, `select:countOf`, `select:getById`, `insert:batchInsert`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightOperationLossManagement.xml
- namespace: `com.rrsjk.light.operation.dao.LightOperationLossManagementDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/AllRisksInsurance.xml
- namespace: `com.rrsjk.light.operation.dao.AllRisksInsuranceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightRepairOrderImg.xml
- namespace: `com.rrsjk.light.operation.dao.LightRepairOrderImgDao`
- statements: `select:findBy`, `insert:create`, `insert:batchInsert`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightOperationProviderBusinessType.xml
- namespace: `com.rrsjk.light.operation.dao.LightOperationProviderBusinessTypeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByReletionId`, `update:deleteByRelationId`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightStationInverterChangeLog.xml
- namespace: `com.rrsjk.light.operation.dao.LightStationInverterChangeLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightWorkOrderBefore.xml
- namespace: `com.rrsjk.light.operation.dao.LightWorkOrderBeforeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:updateByStatus`, `update:updateByStationId`, `delete:deleteById`, `delete:deleteByStationId`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightFaultCode.xml
- namespace: `com.rrsjk.light.operation.dao.LightFaultCodeDao`
- statements: `insert:batchInsert`, `select:groupBy`, `select:countOf`, `delete:deleteByGroupCondition`, `delete:deleteByInveterSns`, `select:selectMaxTime`, `select:groupByAndCreateAt`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/OperationMaintenanceRegion.xml
- namespace: `com.rrsjk.light.operation.dao.OperationMaintenanceRegionDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:delByRelationId`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/OperationElecMonthModel.xml
- namespace: `com.rrsjk.light.operation.dao.OperationElecMonthModelDao`
- statements: `insert:create`, `update:update`, `delete:delete`, `select:findBy`, `select:countOf`, `select:getById`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightOperationCapitalContract.xml
- namespace: `com.rrsjk.light.operation.dao.LightOperationCapitalContractDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:deleteByRelationId`, `select:getByRelationId`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightRepairOrder.xml
- namespace: `com.rrsjk.light.operation.dao.LightRepairOrderDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:updateByStatus`, `update:update`, `select:getBySn`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightSettleBills.xml
- namespace: `com.rrsjk.light.operation.dao.LightSettleBillsDao`
- statements: `select:findBy`, `select:countOf`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/ErrorLog.xml
- namespace: `com.rrsjk.light.operation.dao.ErrorLogDao`
- statements: `insert:create`, `update:update`, `select:get`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/ReportScreenMapModel.xml
- namespace: `com.rrsjk.light.operation.dao.ReportScreenMapModelDao`
- statements: `insert:create`, `update:update`, `delete:delete`, `select:findBy`, `select:countOf`, `select:getById`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightWorkOrderLog.xml
- namespace: `com.rrsjk.light.operation.dao.LightWorkOrderLogDao`
- statements: `select:findBy`, `insert:create`, `insert:batchInsert`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/LightInverterModel.xml
- namespace: `com.rrsjk.light.operation.dao.LightInverterModelDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/PublicLiabilityInsurance.xml
- namespace: `com.rrsjk.light.operation.dao.PublicLiabilityInsuranceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/report/EstimatedElecPriceSupportDao.xml
- namespace: `com.rrsjk.light.operation.dao.v2.report.LightOperationEstimatedElecPriceSupportDao`
- statements: `select:findProvinceBasePrices`, `select:findRegionReports`, `select:findProvinceReports`
- tables: `energy_elec_price_report_province`, `energy_elec_price_report_region`, `light_estimate_city_elec_price`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/data-center/LightZeroCarbonStation.xml
- namespace: `com.rrsjk.light.operation.dao.datacenter.LightZeroCarbonStationDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByStationCode`, `select:countOf`, `select:findBy`, `select:findByPhone`, `select:findByAuditType`, `select:countOfAuditType`, `select:findFinishedStation`, `select:getLightStationByDraftId`
- tables: `id`, `light_zero_carbon_station`, `light_zero_carbon_station_audit`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/light-data/LightOperationInverterInfo.xml
- namespace: `com.rrsjk.light.operation.dao.v2.data.LightOperationInverterInfoDao`
- statements: `select:findLargeStationInverterBasicInfo`, `select:findSmallStationInverterBasicInfo`
- tables: `light_inveter_data`, `light_station`, `light_station_inverter`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/light-data/LightOperationDashboard.xml
- namespace: `com.rrsjk.light.operation.dao.v2.data.LightOperationDashboardDao`
- statements: `select:queryYearElecByRegion`, `select:queryMonthlyElecByYear`, `select:queryDailyElecByMonth`, `select:getRegionCoverageStatistics`, `select:getConnectedStationStatistics`, `select:getElectricityStatistics`, `select:getTopCitiesByStationCount`, `select:getStationStateStatistics`, `select:getTopEfficiencyStationsByFullHours`, `select:getStationDetail`, `select:getStationDailyElectricityForLast30Days`, `select:searchStationsByKeyword`, `select:getStationCountByRegion`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/light-data/FaultCodeDescription.xml
- namespace: `com.rrsjk.light.operation.dao.v2.data.FaultCodeDescriptionDao`
- statements: `select:findAisweiDescription`, `select:findGinlongDescription`, `select:findSinengDescription`
- tables: `inverter_error_dict`, `light_inveter_alarm`, `light_inveter_err`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/light-data/LightInveterElecData.xml
- namespace: `com.rrsjk.light.operation.dao.v2.data.LightInveterElecDataDao`
- statements: `select:findByInverterSn`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/light-data/ReportStationChartYear.xml
- namespace: `com.rrsjk.light.operation.dao.v2.data.ReportStationChartYearDao`
- statements: `select:findBy`, `select:aggregateMonthElecFromDayReport`
- tables: `light_station_elec_day_report`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/light-data/LightInveterData.xml
- namespace: `com.rrsjk.light.operation.dao.v2.data.LightInveterDataDao`
- statements: `select:listInverterOffline24Hour`, `select:listInverterOfflineBySnList`, `select:listInverterBySnList`, `select:getInverterBySn`, `select:listInverterDataForSyncByPage`, `select:countInverterDataForSync`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/light-data/ReportInveterChartTotal.xml
- namespace: `com.rrsjk.light.operation.dao.v2.data.ReportInveterChartTotalDao`
- statements: `select:listSmallStationOfflineInverters24HourByChart`, `select:listLargeStationOfflineInverters2HourByChart`
- tables: `light_station`, `light_station_inverter`, `report_inveter_chart_total`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/light-data/ReportInveterChartMonth.xml
- namespace: `com.rrsjk.light.operation.dao.v2.data.ReportInveterChartMonthDao`
- statements: `select:getByInveterSnAndYearAndMonthAndDay`, `select:listByInveterSnsAndYearAndMonthAndDay`, `select:listByYearAndMonthAndDay`
- tables: `report_inveter_chart_month`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/light-data/ReportStationChartTotal.xml
- namespace: `com.rrsjk.light.operation.dao.v2.data.ReportStationChartTotalDao`
- statements: `select:findBy`, `select:getElecYearByStationCodeAndYear`
- tables: `report_station_chart_total`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/bidding/LightOperationBiddingEvaluator.xml
- namespace: `com.rrsjk.light.operation.dao.bidding.LightOperationBiddingEvaluatorDao`
- statements: `insert:create`, `insert:batchCreate`, `update:update`, `select:getById`, `select:findByProjectId`, `delete:deleteByProjectId`, `select:countByBiddingProjectId`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/bidding/LightOperationBiddingWinningAnnouncement.xml
- namespace: `com.rrsjk.light.operation.dao.bidding.LightOperationBiddingWinningAnnouncementDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:getByAnnouncementCode`, `select:findByProjectId`, `select:findBy`, `select:countOf`, `select:findByStatus`, `select:findByCreatorId`, `select:getMaxSequenceByYearMonth`, `update:publish`, `update:deleteById`, `update:updateStatus`, `select:findByProjectIds`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/bidding/LightOperationBiddingCompanyMapper.xml
- namespace: `com.rrsjk.light.operation.dao.bidding.LightOperationBiddingCompanyDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:getByMemberId`, `select:getListByMemberId`, `update:delete`, `select:countByBusinessLicenseNumber`, `select:getByMemberIdAndName`, `select:getByMemberIdAndBusinessLicense`, `select:findByParams`, `select:countOf`
- tables: `id`, `light_operation_bidding_company`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/bidding/LightOperationBiddingRatingSummary.xml
- namespace: `com.rrsjk.light.operation.dao.bidding.LightOperationBiddingRatingSummaryDao`
- statements: `select:findBy`, `select:countOf`, `select:getByRegistrationId`, `select:getByProjectAndRegistration`, `insert:create`, `update:update`, `select:findByProjectId`, `delete:deleteByProjectId`
- tables: `id`, `light_operation_bidding_registration`, `total_evaluators`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/bidding/LightOperationBiddingRegistrationEngineer.xml
- namespace: `com.rrsjk.light.operation.dao.bidding.LightOperationBiddingRegistrationEngineerDao`
- statements: `insert:create`, `insert:batchCreate`, `update:update`, `select:getById`, `select:findByRegistrationId`, `select:findByRegistrationIds`, `delete:deleteByRegistrationId`, `delete:deleteById`, `select:findByIdCards`, `update:batchUpdateIsValidByRegistrationId`, `update:batchUpdateIsValidByRegionId`
- tables: `id`, `light_operation_bidding_project`, `light_operation_bidding_registration`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/bidding/LightOperationBiddingResponseCondition.xml
- namespace: `com.rrsjk.light.operation.dao.bidding.LightOperationBiddingResponseConditionDao`
- statements: `insert:create`, `insert:batchCreate`, `update:update`, `select:getById`, `select:findByProjectId`, `delete:deleteByProjectId`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/bidding/LightOperationRatingTable.xml
- namespace: `com.rrsjk.light.operation.dao.bidding.LightOperationRatingTableDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findBy`, `select:countOf`, `update:delete`, `select:countByTableName`, `update:updateStatus`
- tables: `id`, `light_operation_rating_table`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/bidding/LightOperationBiddingProject.xml
- namespace: `com.rrsjk.light.operation.dao.bidding.LightOperationBiddingProjectDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findBy`, `select:countOf`, `select:getByProjectCode`, `select:countByProjectCode`, `select:findByStatus`, `select:findByCreatorId`, `select:findByCreatorIdValue`, `select:getMaxSequenceByYearMonth`, `select:findMyBiddingProjects`, `select:countMyBiddingProjects`, `select:findBiddingManagementProjects`, `select:countBiddingManagementProjects`, `select:findBiddingManagementProjectsForExport`, `update:updateInteractionDeadline`, `select:findPendingRatingProjects`, `select:countPendingRatingProjects`, `select:findCompletedRatingProjects`, `select:countCompletedRatingProjects`, `update:updateReviewProgress`, `select:findInteractionExpiredProjects`
- tables: `id`, `light_operation_bidding_company`, `light_operation_bidding_evaluator`, `light_operation_bidding_project`, `light_operation_bidding_rating_record`, `light_operation_bidding_registration`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/bidding/LightOperationRatingGrade.xml
- namespace: `com.rrsjk.light.operation.dao.bidding.LightOperationRatingGradeDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:findByRatingItemId`, `delete:deleteByRatingItemId`, `insert:copyGradesByItemId`
- tables: `id`, `light_operation_rating_grade`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/bidding/LightOperationBiddingProjectRatingTable.xml
- namespace: `com.rrsjk.light.operation.dao.bidding.LightOperationBiddingProjectRatingTableDao`
- statements: `select:getByProjectId`, `insert:create`, `update:update`, `delete:deleteByProjectId`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/bidding/LightOperationBiddingRegistration.xml
- namespace: `com.rrsjk.light.operation.dao.bidding.LightOperationBiddingRegistrationDao`
- statements: `insert:create`, `update:update`, `update:autoRejectExpiredPendingAudits`, `update:autoMarkExpiredPendingResponses`, `select:getById`, `select:findBy`, `select:countOf`, `select:getByRegistrationCode`, `select:countByRegistrationCode`, `select:findByProjectId`, `select:findApprovedByProjectId`, `select:findApprovedWithMyRecord`, `select:findByStatus`, `select:findByCreatorId`, `select:getBySocialCreditCode`, `select:getMaxSequenceByYearMonth`, `select:countByProjectId`, `select:countApprovedByProjectId`, `select:countByProjectIdAndMemberId`, `select:countPublishedProjectsNotRegisteredByMember`, `select:countMyRegisteredProjects`, `select:findPublishedProjectsNotRegisteredByMember`, `select:findMyRegisteredProjects`, `select:findMyRegisteredProjectsInResponse`, `select:countMyRegisteredProjectsInResponse`, `select:findAllMyRegisteredProjects`, `select:countAllMyRegisteredProjects`, `select:countMyInteractingProjects`, `select:countMyExposingProjects`, `select:countMyRespondingProjects`, `select:countMyReviewingProjects`, `select:findPendingAuditRegistrations`, `select:countPendingAuditRegistrations`, `select:findAuditedRegistrations`, `select:countAuditedRegistrations`, `select:getByIdWithEngineers`, `select:countWonBiddingByMemberId`, `select:findByMemberIdNotSigned`, `update:updateByOperationSigned`, `select:findAllWonBiddings`
- tables: `id`, `light_operation_bidding_project`, `light_operation_bidding_rating_record`, `light_operation_bidding_registration`, `light_operation_bidding_registration_engineer`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/bidding/LightOperationRegionBlockRelease.xml
- namespace: `com.rrsjk.light.operation.dao.bidding.LightOperationRegionBlockReleaseDao`
- statements: `insert:insert`, `select:selectById`, `select:selectByRegionBlockId`, `select:countByQuery`, `select:selectPageByQuery`
- tables: `light_operation_region_block_release`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/bidding/LightOperationBiddingRatingRecord.xml
- namespace: `com.rrsjk.light.operation.dao.bidding.LightOperationBiddingRatingRecordDao`
- statements: `select:findBy`, `select:countOf`, `select:getById`, `select:getByEvaluatorAndRegistration`, `insert:create`, `update:update`, `update:deleteById`, `select:findByProjectId`, `select:findByRegistrationId`, `select:countSubmittedByProject`, `insert:batchCreate`, `update:resetStatusToDraftByProjectId`
- tables: `id`, `light_operation_bidding_project`, `light_operation_bidding_rating_record`, `light_operation_bidding_registration`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/bidding/LightOperationBiddingRegistrationCondition.xml
- namespace: `com.rrsjk.light.operation.dao.bidding.LightOperationBiddingRegistrationConditionDao`
- statements: `insert:create`, `insert:batchCreate`, `update:update`, `select:getById`, `select:findByBiddingRegistrationId`, `select:findByRegistrationIds`, `select:findByBiddingResponseConditionId`, `delete:deleteById`, `delete:deleteByBiddingRegistrationId`, `select:countByBiddingRegistrationId`, `select:countMetConditionsByBiddingRegistrationId`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/bidding/LightOperationRatingPoint.xml
- namespace: `com.rrsjk.light.operation.dao.bidding.LightOperationRatingPointDao`
- statements: `insert:create`, `update:update`, `select:findByRatingItemId`, `delete:deleteByRatingItemId`, `insert:copyPointByItemId`
- tables: `id`, `light_operation_rating_point`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/bidding/LightOperationBiddingRatingDetail.xml
- namespace: `com.rrsjk.light.operation.dao.bidding.LightOperationBiddingRatingDetailDao`
- statements: `select:findByRecordId`, `select:findByRecordIds`, `insert:batchInsert`, `insert:batchCreate`, `delete:deleteByRecordId`, `insert:batchUpdateOrInsert`
- tables: `item_score`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/bidding/LightOperationRatingItem.xml
- namespace: `com.rrsjk.light.operation.dao.bidding.LightOperationRatingItemDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findBy`, `select:findByRatingTableId`, `select:findByRatingTableIdAndType`, `select:countOf`, `update:delete`, `update:batchUpdateSortOrder`, `insert:copyItemsByTableId`
- tables: `id`, `light_operation_rating_item`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/bidding/LightOperationRegionBlock.xml
- namespace: `com.rrsjk.light.operation.dao.bidding.LightOperationRegionBlockDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findBy`, `select:countOf`, `delete:delete`, `select:countByBlockCode`, `insert:batchInsertAreas`, `delete:deleteAreasByRegionBlockId`, `select:findAreasByRegionBlockId`, `select:countAreaConflict`, `select:countStationsByArea`, `select:findAllEnabledAreas`, `insert:batchInsert`, `select:findAreasByRegionBlockIds`, `update:batchUpdateRecruitmentStatus`, `update:updateRecruitmentStatus`, `update:batchUpdateOperatorAndStatus`
- tables: `id`, `light_operation_region_block`, `light_operation_region_block_area`, `light_operation_station`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/light/LightElectricOrder.xml
- namespace: `com.rrsjk.light.operation.dao.v2.light.LightElectricOrderDao`
- statements: `select:countOf`, `select:findBy`, `select:findByForBackfill`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/light/LightOperationInverter.xml
- namespace: `com.rrsjk.light.operation.dao.v2.light.LightOperationInverterDao`
- statements: `select:getById`, `select:findByInverterSn`, `select:findByStationCode`, `select:findBy`, `select:countOf`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/light/LightStationChangeOperation.xml
- namespace: `com.rrsjk.light.operation.dao.v2.light.LightStationChangeOperationDao`
- statements: `select:findByParams`
- tables: `light_station_change_operation`, `light_station_change_record`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/light/LightStation.xml
- namespace: `com.rrsjk.light.operation.dao.v2.light.LightStationDao`
- statements: `select:findByHds`, `select:countByHds`, `update:updateOpMemberIdByStationId`, `select:getByStationCode`, `select:count`, `select:findBasicByStationCodes`, `select:findEstimatedPriceStations`
- tables: `id`, `light_operation_provider`, `light_station`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/light/LightStationConfirmImg.xml
- namespace: `com.rrsjk.light.operation.dao.v2.light.LightStationConfirmImgDao`
- statements: `select:getLatestImageByStationAndType`, `select:getLatestImageByStationCodeAndType`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/light/LightProjectElectricOrder.xml
- namespace: `com.rrsjk.light.operation.dao.v2.light.LightProjectElectricOrderDao`
- statements: `select:countOf`, `select:findBy`, `select:findStationBy`, `select:countStationBy`, `select:findByForBackfill`, `select:findDeletedByUpdatedAtFrom`, `select:findElecPriceStation`
- tables: `light_project_electric_order`, `light_project_electric_order_owner`, `light_station`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/light/LightOperationMainDashboard.xml
- namespace: `com.rrsjk.light.operation.dao.v2.light.LightOperationMainDashboardDao`
- statements: `select:getRegionCoverageStatisticsFromReport`, `select:getElectricityStatisticsFromReport`, `select:getConnectedStationStatisticsFromReport`, `select:getWorkOrderStatisticsFromReport`, `select:getStationStateStatisticsFromReport`
- tables: `rrsjk_light_report.report_asset_screen_work_order`, `rrsjk_light_report.report_screen_county`, `rrsjk_light_report.report_screen_grid`, `rrsjk_light_report.report_screen_month_elec`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/light/LightDeposit.xml
- namespace: `com.rrsjk.light.operation.dao.light.LightDepositDao`
- statements: `update:update`, `select:findBy`, `insert:create`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/light/LightStationRent.xml
- namespace: `com.rrsjk.light.operation.dao.v2.light.LightStationRentDao`
- statements: `select:findYxRentMonths`, `select:findHouseholdRentMonths`, `select:findUnionpayRentMonths`, `select:findPubBuildRentMonths`, `select:findWholeVillageRentMonths`
- tables: `light_electric_order`, `light_project_rent_record`, `light_unionpay_bill_record`, `light_wv_rent_record`, `light_yuexiu_income_bill`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/light/YuexiuElectricityBill.xml
- namespace: `com.rrsjk.light.operation.dao.v2.light.YuexiuElectricityBillDao`
- statements: `select:findByStationCodesAndBillMonth`, `select:findByForBackfill`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationWorkOrderFaultInfo.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationWorkOrderFaultInfoDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findByWorkOrderId`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationStationGuaranteeTarget.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationStationGuaranteeTargetDao`
- statements: `insert:create`, `insert:batchCreate`, `update:update`, `select:getById`, `select:getByStationCodeAndYear`, `delete:delete`, `delete:deleteByStationCode`, `select:countByStationCode`, `select:countByStationCodeAndYear`, `select:findByStationCode`, `select:findByYear`, `select:findStationPageWithGuaranteeTarget`, `select:countStationWithGuaranteeTarget`, `select:findTargetsByStationCodes`, `select:getTotalTargetElecByStationCode`, `delete:deleteByStationCodes`, `update:batchUpdate`, `select:findMissingStationCodes`
- tables: `id`, `light_operation_station`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationExamPaper.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationExamPaperDao`
- statements: `insert:create`, `select:findByExamId`, `update:update`, `delete:deleteByExamId`
- tables: `id`, `light_operation_exam`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationWorkOrderAppeal.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationWorkOrderAppealDao`
- statements: `insert:create`, `insert:batchCreate`, `update:update`, `select:getById`, `select:findByWorkOrderId`, `select:findByOrderCode`, `select:findBy`, `select:countOf`, `select:findByParams`, `delete:deleteById`, `delete:deleteByWorkOrderId`
- tables: `id`, `light_operation_work_order`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationWorkOrder.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationWorkOrderDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:getByOrderCode`, `select:findBy`, `select:countOf`, `select:statisticsEfficiencyByOp`, `select:statisticsEfficiencyTotal`, `update:batchUpdateOverTimeStatus`, `select:findOpenOftenFaultWorkOrders`, `select:findHandledOftenFaultWorkOrders`, `select:hasOpenWorkOrder`, `select:findOpenWorkOrderDevices`, `select:countOfSettle`, `select:statisticHandlerWorkOrderStatsForLastWeek`, `select:statisticProviderWorkOrderStatsForLastWeek`, `select:statisticSubCenterWorkOrderStatsForLastWeek`, `select:statisticHeadquarterWorkOrderStatsForLastWeek`, `select:getYearlyStatsByOpName`, `select:findDtoBy`, `select:findByZhaoYin`, `select:countOfZhaoYin`, `select:queryWorkOrderStatistics`, `select:findEarliestWorkOrderDate`, `select:findStationFaultInfo`, `select:findStationWorkOrderInfo`
- tables: `id`, `light_operation_inspection_work_order`, `light_operation_station`, `light_operation_work_order`, `light_operation_work_order_fault_info`, `light_work_order`, `rrsjk_light.cmb_leasing_station`, `rrsjk_light_operation`.`light_operation_work_order`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationInspectionWorkOrder.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationInspectionWorkOrderDao`
- statements: `insert:create`, `insert:createBatch`, `update:update`, `update:updateWithNull`, `select:getById`, `select:findByOrderCode`, `select:findBy`, `select:findUnfinishedWithOperatorMismatch`, `select:countOf`, `select:findByPlanId`, `select:countByStatus`, `select:statisticsByOpAndSpecialFlag`, `select:statisticsByOp`, `select:statisticsByOpAndStaff`, `select:statisticsTotalByPlan`, `select:countOfStatisticsByOpAndSpecialFlag`, `select:countOfStatisticsByOp`, `select:countOfStatisticsByOpAndStaff`, `select:statisticsByPlan`, `select:countOfStatisticsByPlan`, `update:updateExpiredInspectionWorkOrders`, `select:findMonthlyCloseRate`
- tables: `id`, `light_operation_inspection_work_order`, `light_operation_station`, `light_operation_work_order_statistics`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationWorkOrderHandleCheckItem.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationWorkOrderHandleCheckItemDao`
- statements: `insert:create`, `insert:createBatch`, `update:update`, `select:getById`, `select:findByWorkOrderId`, `select:findByProcessRecordId`, `delete:deleteByIds`, `delete:deleteByWorkOrderId`, `delete:deleteByProcessRecordId`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationPractice.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationPracticeDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findByUserIdAndStatus`, `select:findByUserIdAndBankIds`, `select:findByUserId`, `update:updateStatus`, `update:updateProgress`, `delete:delete`, `delete:deleteByUserIdAndBankIds`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationExamBankRel.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationExamBankRelDao`
- statements: `insert:batchCreate`, `delete:deleteByExamId`, `select:findByExamId`, `select:countByBankId`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationReportConfigField.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationReportConfigFieldDao`
- statements: `insert:batchCreate`, `delete:deleteByReportConfigId`, `select:findByReportConfigId`
- tables: `light_operation_report_config`, `light_operation_report_data_field`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationQuestion.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationQuestionDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findBy`, `select:countOf`, `select:findByBankId`, `select:countByBankId`, `delete:delete`
- tables: `id`, `light_operation_question_bank`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationStationElecReport.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationStationElecReportDao`
- statements: `select:findByPage`, `select:countByQuery`, `select:listForExport`, `insert:saveOrUpdate`, `insert:saveOrUpdateBatch`
- tables: `station_id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationReportConfigRole.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationReportConfigRoleDao`
- statements: `insert:batchCreate`, `delete:deleteByReportConfigId`, `select:findByReportConfigId`, `select:findByRoleCode`, `select:findConfigIdsByRoleCode`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationWorkOrderConfigCheckItem.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationWorkOrderConfigCheckItemDao`
- statements: `insert:create`, `insert:batchCreate`, `update:update`, `select:getById`, `select:findByConfigId`, `delete:deleteByConfigId`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationStation.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationStationDao`
- statements: `insert:create`, `insert:createBatch`, `update:update`, `select:getById`, `select:getByStationCode`, `select:getSpNameByStationCode`, `select:findBy`, `select:findStationCodesByPage`, `select:countOf`, `select:findByIds`, `select:findByStationCodes`, `select:findExistingStationCodes`, `select:countByStatus`, `select:getAllCompanyStationElecNos`, `insert:insertOrUpdateBatch`, `update:batchUpdateStationScores`, `update:updateStationOp`, `select:countStationsByProvince`, `select:countStationsByCity`, `select:countStationsByRegion`, `select:findOpMemberMappingsByRegionIds`, `select:countStationsByGroupFields`, `select:listDistinctOperators`
- tables: `id`, `light_operation_station`, `name`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationWorkOrderConfig.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationWorkOrderConfigDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findBy`, `select:countOf`, `select:countBySolutionId`, `select:countByFaultId`, `select:countByOrderTypeAndFaultId`, `select:findByFaultId`, `select:findByOrderType`, `select:countByOrderTypeAndName`, `select:findLatestBy`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationInspectionPlan.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationInspectionPlanDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findBy`, `delete:delete`, `select:countByConfigId`
- tables: `id`, `light_operation_inspection_plan`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationInspectionConfigCheckItem.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationInspectionConfigCheckItemDao`
- statements: `insert:create`, `insert:batchCreate`, `update:update`, `select:getById`, `select:findByConfigId`, `delete:deleteByConfigId`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationExam.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationExamDao`
- statements: `insert:create`, `update:update`, `update:updateStatus`, `select:getById`, `select:findBy`, `select:countOf`, `select:countByName`, `update:batchUpdateExpiredExamsToEnded`, `select:findByUserExamStatus`, `select:countByUserExamStatus`
- tables: `id`, `light_operation_exam`, `light_operation_exam_answer`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationSolutionCategory.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationSolutionCategoryDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findAll`, `select:findByParentId`, `select:findAllTree`, `select:findByPath`, `delete:delete`, `select:countByName`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationFaultCode.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationFaultCodeDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findByFaultId`, `select:findBy`, `select:countOf`, `delete:deleteByFaultId`, `insert:batchCreate`, `select:findEnabledFaultCodes`, `update:batchUpdateStatusByFaultId`, `update:batchUpdateSecondStatusByFaultId`, `select:findByCodeAndManufacturerAndType`, `select:findByCodeAndManufacturer`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationStationElecBill.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationStationElecBillDao`
- statements: `insert:create`, `insert:createBatch`, `update:update`, `update:updateBatch`, `select:getById`, `select:findBy`, `select:countOf`, `select:findStationBillBy`, `select:findStationBill`, `select:getStationSummaryByStationCodes`, `select:countStationBillOf`, `select:findByStationIdAndBillDate`, `select:findByStationCodeAndBillDate`, `delete:delete`, `select:getLastPeriodElecBillSummary`, `select:getTotalElecBillSummary`, `select:getStationElecBillSummaryByStationCode`, `select:findByProvinceIdAndBillMonth`, `select:findZeroAmountElecNos`, `select:findZeroAmountBillsByElecNos`, `select:findStationsWithoutElecBills`, `select:findByBaseElecNoAndBillMonth`, `select:findExistingBillMonthsByStationCodes`, `select:findZeroAmountBillsByFieldMethod`, `select:findZeroAmountBillsBySpecialFlag`, `select:findByElecNosAndMonths`, `select:findFullByElecNoAndMonth`, `select:findByStationCodesAndMonths`, `select:findDistinctStationCodes`, `select:subCenterSummary`, `select:countOfSubCenter`, `select:projectCompanySummary`, `select:countOfProjectCompany`, `select:specialFlagSummary`, `select:countOfSpecialFlag`, `select:projectCompanySubstationGroupPage`, `select:countOfProjectCompanySubstation`, `select:projectCompanySubstationMonthlyByGroupKeys`, `select:listProjectCompanySubstationReportMonths`, `select:findZeroSettlementElecNos`, `select:findZeroSettlementByElecNos`, `select:findSubStationNameAndInvoiceNumber`, `select:findSubStationNameAndInvoiceNumberByElecNos`, `select:listAllSubstationNames`, `update:updateStationMigration`, `update:batchUpdateElecPrice`, `update:batchUpdateElec`, `update:syncProjectCompanyNameFromStationForUnconfirmedBills`, `update:syncStationGroupFromStationForUnconfirmedBills`, `select:findDistinctStationCodesByFieldMethod`, `select:findByStationCodeAndFieldMethod`, `select:aggregateReportMetrics`
- tables: `id`, `light_operation_station`, `light_operation_station_elec_bill`, `rrsjk_light_operation.light_operation_station`, `rrsjk_light_operation.light_operation_station_elec_bill`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationStationTag.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationStationTagDao`
- statements: `select:findStationTagsByStationCodes`, `select:findByParams`, `insert:create`, `insert:batchCreate`, `update:update`, `select:getById`, `select:findBy`, `select:countOf`, `update:removeByValue`, `update:removeByTagCode`, `update:updateCurrentToHistory`, `select:findStationCodesByTag`, `select:findStationCodesByTagCode`, `select:findAllStationTagValuesByTagCode`, `select:findStationCodesByTagValue`, `select:findStationCodesByTagValues`, `delete:cleanExpiredTags`, `select:findCurrentTagsByStationCodesAndTagCode`, `update:batchRemoveTagsByStationCodesAndTagCode`
- tables: `id`, `light_operation_station_tag`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationMessagePush.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationMessagePushDao`
- statements: `insert:batchCreate`, `select:findByMessageId`, `select:findVisibleMessageIds`, `delete:deleteByMessageId`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationWorkOrderProcessRecord.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationWorkOrderProcessRecordDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findByWorkOrderId`, `select:findFinalByWorkOrderId`, `select:findBy`, `select:countOf`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationMessage.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationMessageDao`
- statements: `insert:create`, `insert:batchCreate`, `update:update`, `select:getById`, `select:findBy`, `select:countOf`, `update:batchDelete`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationDictItem.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationDictItemDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findByDictCode`, `select:findByDictId`, `select:findBy`, `select:countOf`, `select:findByDictCodes`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationFaultSolutionCheckItem.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationFaultSolutionCheckItemDao`
- statements: `select:findByFaultSolutionId`, `delete:deleteByFaultSolutionId`, `insert:batchCreate`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationQuestionCategory.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationQuestionCategoryDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findBy`, `select:countOf`, `select:countByName`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationSolution.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationSolutionDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findBy`, `select:countOf`, `update:delete`, `select:countByName`, `select:countByCategoryId`
- tables: `id`, `light_operation_solution_category`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationFaultSolution.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationFaultSolutionDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findByFirstFaultId`, `select:findBySecondFaultId`, `select:findBy`, `select:countOf`, `select:countByName`
- tables: `id`, `light_operation_fault`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationExamPush.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationExamPushDao`
- statements: `insert:batchCreate`, `delete:deleteByExamId`, `select:findByExamId`, `select:findVisibleExamIds`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationExternalDiagnosisTask.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationExternalDiagnosisTaskDao`
- statements: `select:getById`, `select:findBy`, `select:countBy`, `insert:create`, `update:update`, `delete:deleteById`, `update:updateStatus`, `select:countByName`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationMessageRead.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationMessageReadDao`
- statements: `insert:create`, `insert:batchCreate`, `select:getByMessageAndUser`, `select:findReadMessageIdsByUser`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationReportDataField.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationReportDataFieldDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findByFieldCode`, `select:findBy`, `select:countOf`, `delete:delete`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationWorkOrderProcess.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationWorkOrderProcessDao`
- statements: `insert:create`, `insert:batchCreate`, `select:getById`, `select:findByWorkOrderId`, `delete:deleteByWorkOrderId`, `select:findByWorkOrderIdsAndProcessName`, `select:findByWorkOrderIds`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationElecPrice.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationElecPriceDao`
- statements: `insert:create`, `insert:createBatch`, `update:update`, `select:getById`, `select:findBy`, `select:countOf`, `select:findByProvinceIdAndYearMonth`, `delete:delete`, `select:findByYear`, `select:countByYear`, `select:findAll`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationInspectionConfig.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationInspectionConfigDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findBy`, `select:countOf`, `select:countBySolutionId`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationReportConfig.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationReportConfigDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findBy`, `select:countOf`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationInspectionWorkOrderCheckItem.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationInspectionWorkOrderCheckItemDao`
- statements: `insert:create`, `insert:createBatch`, `update:update`, `select:getById`, `select:findByWorkOrderId`, `delete:deleteByIds`, `delete:deleteByWorkOrderId`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationQuestionBank.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationQuestionBankDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findBy`, `select:countOf`, `select:countByName`, `update:updateQuestionCount`, `select:findByCategoryId`, `select:countByCategoryId`
- tables: `id`, `light_operation_question`, `light_operation_question_bank`, `light_operation_question_category`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationDict.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationDictDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:getByDictCode`, `select:findBy`, `select:countOf`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationExamAnswer.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationExamAnswerDao`
- statements: `insert:create`, `insert:batchCreate`, `update:update`, `update:updateStatus`, `select:getById`, `select:findByExamIdAndUserId`, `select:findByExamId`, `select:findBy`, `select:countOf`, `delete:deleteByExamId`, `select:findByExamIdsAndUserId`, `update:updateTimeoutAnswersToCompleted`, `update:updateUnansweredExamsToExpired`, `select:findTimeoutAnswersInProgress`, `select:getOverallStatistics`, `select:getExamPersonDetails`, `select:countExamPersonDetails`
- tables: `id`, `light_operation_exam`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationFault.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationFaultDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:countByName`, `select:countByNameAndWorkOrderType`, `select:countByNameAndParentId`, `select:findBy`, `select:findDirectChildrenByParentIds`, `select:countOf`, `select:getByName`
- tables: `id`, `light_operation_fault_code`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationQuestionOption.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationQuestionOptionDao`
- statements: `insert:batchCreate`, `delete:deleteByQuestionId`, `select:findByQuestionId`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationExportTask.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationExportTaskDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:getByTaskNo`, `select:findBy`, `select:countOf`, `select:findStuckTasks`, `select:findCompletedTasksBefore`
- tables: `id`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/v2/LightOperationWorkOrderStatistics.xml
- namespace: `com.rrsjk.light.operation.dao.v2.LightOperationWorkOrderStatisticsDao`
- statements: `insert:batchInsert`, `delete:deleteByStatDate`, `select:listByStatDate`
- tables: `light_operation_work_order_statistics`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/clickhouse/LightOperationFaultRecord.xml
- namespace: `com.rrsjk.light.operation.dao.v2.clickhouse.LightOperationFaultRecordDao`
- statements: `insert:batchInsert`, `insert:insert`, `select:countFaultDaysInPeriod`, `select:findFaultDatesInPeriod`, `select:findByDeviceAndDate`, `select:findLatestByDevice`, `select:findLatestFaultRecord`, `select:findLatestWarnRecord`, `select:countByDateRange`, `delete:deleteBeforeDate`, `select:findDevicesWithFaultDays`, `select:findDevicesWithWarnDays`, `select:countFaultDaysForRecovery`, `select:countWarnDaysForRecovery`, `select:findWarnDatesInPeriod`, `select:countFaultRecordsOnDate`, `select:countWarnRecordsOnDate`, `select:findFaultDatesWithCounts`, `select:findWarnDatesWithCounts`, `select:findFaultRecordsAfterTime`, `select:findWarnRecordsAfterTime`, `select:findLatestIn48Hours`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/clickhouse/ExternalDailyPshMetrics.xml
- namespace: `com.rrsjk.light.operation.dao.v2.clickhouse.ExternalDailyPshMetricsDao`
- statements: `select:findBy`, `select:countBy`, `select:findExternalTaskStatistics`, `select:findTaskBasicStatistics`, `select:selectStationAverageScoreByTaskIdAndStationCodes`
- tables: `light_operation_external_inverter_inefficiency_psh_results`, `station_stats`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/clickhouse/LightInverterDataCh.xml
- namespace: `com.rrsjk.light.operation.dao.v2.clickhouse.LightInverterDataChDao`
- statements: `insert:batchInsertInverterData`, `select:countTotal`, `delete:deleteAllInverterData`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/clickhouse/LightOperationExternalStation.xml
- namespace: `com.rrsjk.light.operation.dao.v2.clickhouse.LightOperationExternalStationDao`
- statements: `select:findByStationCode`, `select:findByProvinceName`, `select:findByCityName`, `select:findBy`, `select:countOf`, `select:countBy`, `select:findAll`, `insert:batchInsert`, `insert:insert`, `update:updateByStationCode`, `delete:deleteByStationCode`, `select:findByTaskId`, `select:countByTaskId`
- tables: `id`, `light_operation_external_inverter_inefficiency_psh_results`, `name`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/clickhouse/ExternalInverterInefficiencyDiagnosisResult.xml
- namespace: `com.rrsjk.light.operation.dao.v2.clickhouse.ExternalInverterInefficiencyDiagnosisResultDao`
- statements: `select:findBy`, `select:countBy`, `select:selectLatestByTaskIdAndStationCodes`, `select:countStationsByInefficiencyType`, `select:countStationsBySpecificInefficiencyType`, `select:selectDistinctInefficiencyTypes`, `select:countTotalInefficiencyStations`
- tables: `light_operation_external_inverter_inefficiency_diagnosis_results`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/clickhouse/SoilingDiagnosisResult.xml
- namespace: `com.rrsjk.light.operation.dao.v2.clickhouse.SoilingDiagnosisResultDao`
- statements: `select:findSoiledStations`, `select:findByStationCodeAndDate`, `select:findByDateRange`, `select:findBy`, `select:countOf`, `select:countBy`, `select:findSoiledStationsByQuery`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/clickhouse/LightOperationExternalInverterRecord.xml
- namespace: `com.rrsjk.light.operation.dao.v2.clickhouse.LightOperationExternalInverterRecordDao`
- statements: `select:findByInverterSnAndTimeRange`, `select:findBy`, `insert:batchInsert`, `select:findByTaskId`, `select:countByTaskId`, `select:selectDistinctDataDates`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/clickhouse/LightInverterData.xml
- namespace: `com.rrsjk.light.operation.dao.v2.clickhouse.LightInverterDataDao`
- statements: `select:findBaseData`, `select:findMpptData`, `select:countOf`, `select:queryTodayPowerTrend`, `select:findLatestDataByInverterSn`, `select:findTodayLatestRecordsByInverterSn`, `select:findLatestDataByInverterSnIn30Hours`, `select:findLatestDataByInverterSnListIn30Hours`, `select:findEarliestPowerData`
- tables: `mv_station_power_trend_daily`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/clickhouse/LightOperationExternalInverter.xml
- namespace: `com.rrsjk.light.operation.dao.v2.clickhouse.LightOperationExternalInverterDao`
- statements: `select:findByStationCode`, `select:findByInverterSn`, `select:findByInverterModel`, `select:findByBrandName`, `select:findBy`, `select:countOf`, `select:countBy`, `select:findAll`, `insert:batchInsert`, `insert:insert`, `update:updateByInverterSn`, `delete:deleteByInverterSn`, `select:findByTaskId`, `select:countByTaskId`
- tables: `id`, `station_code`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/clickhouse/ShadowDiagnosisResult.xml
- namespace: `com.rrsjk.light.operation.dao.v2.clickhouse.ShadowDiagnosisResultDao`
- statements: `select:findBy`, `select:countBy`, `select:findLatestByStation`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/clickhouse/InverterInefficiencyDiagnosisResult.xml
- namespace: `com.rrsjk.light.operation.dao.v2.clickhouse.InverterInefficiencyDiagnosisResultDao`
- statements: `select:findBy`, `select:countBy`, `select:findStationCodesWithOtherLowEfficiencyFor7Days`
- tables: `inverter_inefficiency_diagnosis_results`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/clickhouse/LightOperationInverterConfig.xml
- namespace: `com.rrsjk.light.operation.dao.v2.clickhouse.LightOperationInverterConfigDao`
- statements: `insert:insert`, `insert:insertBatch`, `select:findByInverterSn`, `select:findBy`, `select:findByInverterSnList`

## rrsjk-light-operation-service/rrsjk-light-operation-impl/src/main/resources/mybatis/mapper/clickhouse/DailyPshMetrics.xml
- namespace: `com.rrsjk.light.operation.dao.v2.clickhouse.DailyPshMetricsDao`
- statements: `select:findBy`, `select:countBy`, `select:findStationMonthlyStatistics`, `select:countStationMonthlyStatistics`, `select:findYesterdayZeroPowerInverters`
- tables: `daily_station_stats`, `monthly_station_stats`

## vpp-api-meta/vpp-biz/src/main/resources/mapper/ProductMapper.xml
- namespace: `com.nahui.energy.mapper.ProductMapper`
- statements: `delete:deleteProductImage`, `select:listByCriteria`, `select:listProductImage`, `select:queryByWdn`, `insert:insertBatchProductImage`
- tables: `t_product`, `t_product_image`

## vpp-api-meta/vpp-biz/src/main/resources/mapper/ShipmentLogMapper.xml
- namespace: `com.nahui.energy.mapper.ShipmentLogMapper`
- statements: `delete:deleteShipment`, `select:listByCriteria`
- tables: `t_product`, `t_shipment_log`

## rrsjk-activity-service/rrsjk-activity-impl/src/main/resources/mybatis/mapper/Orders.xml
- namespace: `com.rrsjk.activity.dao.OrdersDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByParams`, `select:findCount`, `select:find`
- tables: `id`

## rrsjk-activity-service/rrsjk-activity-impl/src/main/resources/mybatis/mapper/OrderItem.xml
- namespace: `com.rrsjk.activity.dao.OrderItemDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByParams`, `select:findCount`, `select:find`, `select:findItemTotalByParams`
- tables: `id`

## rrsjk-activity-service/rrsjk-activity-impl/src/main/resources/mybatis/mapper/Item.xml
- namespace: `com.rrsjk.activity.dao.ItemDao`
- statements: `insert:create`, `update:update`, `insert:batchInsert`, `select:get`, `select:findByParams`, `update:salesStock`, `update:refundStock`, `update:increaseStock`
- tables: `id`

## rrsjk-activity-service/rrsjk-activity-impl/src/main/resources/mybatis/mapper/Activity.xml
- namespace: `com.rrsjk.activity.dao.ActivityDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findCount`, `select:find`
- tables: `id`

## rrsjk-admin-app-service/rrsjk-admin-app-impl/src/main/resources/mybatis/mapper/report/EnergyAppOverdueInventoryMapper.xml
- namespace: `com.rrsjk.adminapp.mapper.report.EnergyAppOverdueInventoryMapper`
- statements: `select:findBySubCenter`, `select:findSpRank`, `select:countSpRank`, `select:findDetail`, `select:countDetail`
- tables: `energy_app_overdue_inventory`

## rrsjk-admin-app-service/rrsjk-admin-app-impl/src/main/resources/mybatis/mapper/light/LightStationMapper.xml
- namespace: `com.rrsjk.adminapp.mapper.light.LightStationMapper`
- statements: `select:selectById`, `select:selectByStationCode`, `select:selectList`, `select:count`, `insert:insert`, `update:updateById`, `select:findNoSignStationList`, `select:findNoSignStationCount`, `select:findNoInstallStationList`, `select:findNoInstallStationCount`, `select:findTechNoRectifiedStationList`, `select:findTechNoRectifiedStationCount`, `select:findBusinessNoRectifiedStationList`, `select:findBusinessNoRectifiedStationCount`, `select:findNoGridStationList`, `select:findNoGridStationCount`, `select:findOverdueSpRank`, `select:countOverdueSpRank`
- tables: `id`, `light_station`, `light_station_audit`

## rrsjk-admin-app-service/rrsjk-admin-app-impl/src/main/resources/mybatis/mapper/light/LightGridCertMapper.xml
- namespace: `com.rrsjk.adminapp.mapper.light.LightGridCertMapper`
- statements: `select:selectLatestByStationCodeAndImageUrl`
- tables: `light_grid_cert`

## rrsjk-admin-app-service/rrsjk-admin-app-impl/src/main/resources/mybatis/mapper/light/CompleteConfirmMapper.xml
- namespace: `com.rrsjk.adminapp.mapper.light.CompleteConfirmMapper`
- statements: `select:selectStationById`, `select:selectInverterByStationCode`, `select:selectMajorPlanConfig`, `select:selectConfirmImgByStationCode`, `select:selectModuleSnByStationId`, `select:selectEpcByStationId`, `select:selectEpcFilesByStationId`, `select:selectProjectByProjectCode`, `select:selectPlanDesignByStationId`, `select:selectLatestGridCertRejectRecord`, `select:getLatestRejectReason`
- tables: `light_audit_image_reject_record`, `light_module_sn`, `light_project_management`, `light_station`, `light_station_audit`, `light_station_confirm_img`, `light_station_epc`, `light_station_epc_file`, `light_station_inverter`, `light_station_plan_config`, `light_station_plan_design`

## rrsjk-admin-app-service/rrsjk-admin-app-impl/src/main/resources/mybatis/mapper/light/ApprovalReview.xml
- namespace: `com.rrsjk.adminapp.mapper.light.ApprovalReviewMapper`
- statements: `select:countReviewMaterials`, `select:selectReviewMaterials`
- tables: `light_station`, `light_station_audit`

## rrsjk-admin-app-service/rrsjk-admin-app-impl/src/main/resources/mybatis/mapper/light/GfConfirmImgMapper.xml
- namespace: `com.rrsjk.adminapp.mapper.light.GfConfirmImgMapper`
- statements: `select:selectByStationCode`, `select:selectByStationCodeAndType`
- tables: `gf_light_station_confirm_img`

## rrsjk-admin-app-service/rrsjk-admin-app-impl/src/main/resources/mybatis/mapper/light/InverterOcrMapper.xml
- namespace: `com.rrsjk.adminapp.mapper.light.InverterOcrMapper`
- statements: `select:selectLatestByInverter`
- tables: `light_station_inverter_ocr`

## rrsjk-admin-app-service/rrsjk-admin-app-impl/src/main/resources/mybatis/mapper/light/ShipGoodsApprovalMapper.xml
- namespace: `com.rrsjk.adminapp.mapper.light.ShipGoodsApprovalMapper`
- statements: `select:countConfirmOrders`, `select:findConfirmOrders`
- tables: `light_confirm_order`, `light_sp_auclon_store`

## rrsjk-admin-app-service/rrsjk-admin-app-impl/src/main/resources/mybatis/mapper/light/ModuleAngleOcrMapper.xml
- namespace: `com.rrsjk.adminapp.mapper.light.ModuleAngleOcrMapper`
- statements: `select:selectLatestByAngle`
- tables: `light_station_module_angle_ocr`

## rrsjk-admin-app-service/rrsjk-admin-app-impl/src/main/resources/mybatis/mapper/light/LightPurchaseOrderMapper.xml
- namespace: `com.rrsjk.adminapp.mapper.light.LightPurchaseOrderMapper`
- statements: `select:findOver7UnsignedSummary`, `select:findOver7UnsignedSpRank`, `select:countOver7UnsignedSpRank`, `select:findOver7UnsignedDetail`, `select:countOver7UnsignedDetail`
- tables: `light_purchase_order`, `light_service_provider`, `light_sp_store`

## rrsjk-admin-app-service/rrsjk-admin-app-impl/src/main/resources/mybatis/mapper/light/BusinessAnalysisMapper.xml
- namespace: `com.rrsjk.adminapp.mapper.light.BusinessAnalysisMapper`
- statements: `select:subCenterOverview`, `select:spRankList`, `select:spRankCount`, `select:cityRankList`, `select:cityRankCount`, `select:stationStatusOverview`, `select:stationSpRankList`, `select:stationSpRankCount`, `select:stationPageList`, `select:stationPageCount`
- tables: `light_station`

## rrsjk-admin-app-service/rrsjk-admin-app-impl/src/main/resources/mybatis/mapper/elec/LightStationElecMapper.xml
- namespace: `com.rrsjk.adminapp.mapper.elec.LightStationElecMapper`
- statements: `select:selectById`, `select:selectByStationCode`, `select:selectList`, `select:count`, `insert:insert`, `update:updateById`
- tables: `id`, `light_station_elec`

## rrsjk-admin-app-service/rrsjk-admin-app-impl/src/main/resources/mybatis/mapper/elec/AssetManagementMapper.xml
- namespace: `com.rrsjk.adminapp.mapper.elec.AssetManagementMapper`
- statements: `select:countByStatus`, `select:spRankByStatus`, `select:spRankByStatusCount`, `select:alarmStationList`, `select:alarmStationCount`, `select:stationChartDay`, `select:stationElecDayReport`, `select:countGroupBySpAndStatus`, `select:snapshotCountByStatus`, `select:snapshotBySpAndStatus`, `insert:batchUpsertSnapshot`, `select:inverterListByStationCode`, `select:inverterHistoryByStationCode`, `select:inverterElecAggregation`, `select:inverterAlarmsByStationCode`
- tables: `count`, `light_inveter`, `light_inveter_data`, `light_station`, `light_station_elec`, `light_station_elec_day_report`, `light_station_inverter`, `sp_station_status_snapshot`

## rrsjk-admin-app-service/rrsjk-admin-app-impl/src/main/resources/mybatis/mapper/ads/ElecWarningStationMapper.xml
- namespace: `com.rrsjk.adminapp.mapper.ads.ElecWarningStationMapper`
- statements: `select:selectByKey`, `select:selectList`, `select:count`, `select:findNoElecStationList`, `select:countNoElecStationPage`, `select:findNoElecSpRank`, `select:countNoElecSpRank`, `insert:insert`, `update:updateByKey`
- tables: `elec_warning_station`, `id`

## rrsjk-async-import-export/src/main/resources/mapper/task/AsyncImportExportTaskMapper.xml
- namespace: `com.rrsjk.async.mapper.task.AsyncImportExportTaskMapper`
- statements: `select:selectAsyncImportExportTaskList`, `select:selectAsyncImportExportTaskById`, `select:selectAsyncImportExportTaskByTaskCode`, `insert:insertAsyncImportExportTask`, `update:updateAsyncImportExportTask`, `delete:deleteAsyncImportExportTaskById`, `delete:deleteAsyncImportExportTaskByIds`, `select:findKeysStatus`
- tables: `id`

## rrsjk-async-import-export/src/main/resources/mapper/light/LightStationMapper.xml
- namespace: `com.rrsjk.async.mapper.light.LightStationMapper`
- statements: `select:countOf`, `select:findBy`, `select:findBySimple`
- tables: `light_sp_staff`, `light_staging_records`, `light_station_plan_config`, `light_station_white_list`, `light_sub_sp`

## rrsjk-energystorage-service/rrsjk-energystorage-impl/src/main/resources/mybatis/mapper/CnIncomeCalcHourPrice.xml
- namespace: `com.rrsjk.energystorage.dao.incomecalc.CnIncomeCalcHourPriceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteByInfoId`
- tables: `id`

## rrsjk-energystorage-service/rrsjk-energystorage-impl/src/main/resources/mybatis/mapper/HotNews.xml
- namespace: `com.rrsjk.energystorage.dao.index.HotNewsDao`
- statements: `select:findBy`, `select:countOf`
- tables: `hot_news`

## rrsjk-energystorage-service/rrsjk-energystorage-impl/src/main/resources/mybatis/mapper/CnPeriodDivisionDetail.xml
- namespace: `com.rrsjk.energystorage.dao.incomecalc.CnPeriodDivisionDetailDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getListByProvinceId`, `update:disabledByProvinceId`, `select:findProvincesCount`, `select:findProvinces`, `select:findProvinceIds`, `select:getDetail`
- tables: `cn_period_division_detail`, `id`

## rrsjk-energystorage-service/rrsjk-energystorage-impl/src/main/resources/mybatis/mapper/CnChargeBaseDetail.xml
- namespace: `com.rrsjk.energystorage.dao.incomecalc.CnChargeBaseDetailDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getListByProvinceId`, `update:disabledByProvinceId`, `select:findProvincesCount`, `select:findProvinces`, `select:findProvinceIds`, `select:getDetail`
- tables: `cn_charge_base_detail`, `id`

## rrsjk-energystorage-service/rrsjk-energystorage-impl/src/main/resources/mybatis/mapper/DataDict.xml
- namespace: `com.rrsjk.energystorage.dao.dict.DataDictDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-energystorage-service/rrsjk-energystorage-impl/src/main/resources/mybatis/mapper/InstallMaintenanceInfo.xml
- namespace: `com.rrsjk.energystorage.dao.installMaintenance.InstallMaintenanceInfoDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByParam`
- tables: `id`

## rrsjk-energystorage-service/rrsjk-energystorage-impl/src/main/resources/mybatis/mapper/CnIncomeCalc.xml
- namespace: `com.rrsjk.energystorage.dao.incomecalc.CnIncomeCalcDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteByInfoId`
- tables: `id`

## rrsjk-energystorage-service/rrsjk-energystorage-impl/src/main/resources/mybatis/mapper/ConsultationDetail.xml
- namespace: `com.rrsjk.energystorage.dao.installMaintenance.ConsultationDetailDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-energystorage-service/rrsjk-energystorage-impl/src/main/resources/mybatis/mapper/CnIncomeCalcInfo.xml
- namespace: `com.rrsjk.energystorage.dao.incomecalc.CnIncomeCalcInfoDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:updateAllProp`
- tables: `id`

## rrsjk-energystorage-service/rrsjk-energystorage-impl/src/main/resources/mybatis/mapper/CnChargeBaseHour.xml
- namespace: `com.rrsjk.energystorage.dao.incomecalc.CnChargeBaseHourDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:disabledByProvinceId`, `select:getByProvince`, `select:getProvinceIds`
- tables: `cn_charge_base_hour`, `id`

## rrsjk-energystorage-service/rrsjk-energystorage-impl/src/main/resources/mybatis/mapper/CnPeriodDivisionHour.xml
- namespace: `com.rrsjk.energystorage.dao.incomecalc.CnPeriodDivisionHourDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:disabledByProvinceId`, `select:getByProvince`, `select:getProvinceIds`
- tables: `cn_period_division_hour`, `id`

## rrsjk-energystorage-service/rrsjk-energystorage-impl/src/main/resources/mybatis/mapper/CnIncomeCalcElecCount.xml
- namespace: `com.rrsjk.energystorage.dao.incomecalc.CnIncomeCalcElecCountDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteByInfoId`
- tables: `id`

## rrsjk-energystorage-service/rrsjk-energystorage-impl/src/main/resources/mybatis/mapper/CnTouElecPrice.xml
- namespace: `com.rrsjk.energystorage.dao.incomecalc.CnTouElecPriceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:disabled`, `select:getProvinceIds`
- tables: `cn_tou_elec_price`, `id`

## rrsjk-energystorage-service/rrsjk-energystorage-impl/src/main/resources/mybatis/mapper/BaseUrlDict.xml
- namespace: `com.rrsjk.energystorage.dao.dict.BaseUrlDictDao`
- statements: `select:findByUseType`
- tables: `base_url_dict`

## rrsjk-energystorage-service/rrsjk-energystorage-impl/src/main/resources/mybatis/mapper/EnergyCase.xml
- namespace: `com.rrsjk.energystorage.dao.index.EnergyCaseDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `select:getById`, `select:getByOptionId`
- tables: `energy_case`, `id`

## rrsjk-energystorage-service/rrsjk-energystorage-impl/src/main/resources/mybatis/mapper/CooperationInfo.xml
- namespace: `com.rrsjk.energystorage.dao.index.CooperationInfoDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `cooperation_info`, `dual`, `id`

## rrsjk-echannel-service/rrsjk-echannel-impl/src/main/resources/mybatis/mapper/tmall/JdpTbItem.xml
- namespace: `com.rrsjk.echannel.tmall.dao.JdpTbItemDao`
- statements: `select:countOf`, `select:findBy`

## rrsjk-echannel-service/rrsjk-echannel-impl/src/main/resources/mybatis/mapper/tmall/JdpTbTrade.xml
- namespace: `com.rrsjk.echannel.tmall.dao.JdpTbTradeDao`
- statements: `select:countOf`, `select:findBy`

## rrsjk-echannel-service/rrsjk-echannel-impl/src/main/resources/mybatis/mapper/tmall/JdpTbRefund.xml
- namespace: `com.rrsjk.echannel.tmall.dao.JdpTbRefundDao`
- statements: `select:countOf`, `select:findBy`

## rrsjk-echannel-service/rrsjk-echannel-impl/src/main/resources/mybatis/mapper/platform/EchannelStatusQueue.xml
- namespace: `com.rrsjk.echannel.platform.dao.EchannelStatusQueueDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByChannelTypeTradeOrderId`, `select:findBySuccess`
- tables: `id`

## rrsjk-echannel-service/rrsjk-echannel-impl/src/main/resources/mybatis/mapper/platform/MerchantEchannelSg.xml
- namespace: `com.rrsjk.echannel.platform.dao.MerchantEchannelSgDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByAll`
- tables: `id`

## rrsjk-echannel-service/rrsjk-echannel-impl/src/main/resources/mybatis/mapper/platform/MerchantEchannel.xml
- namespace: `com.rrsjk.echannel.platform.dao.MerchantEchannelDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByType`, `select:findByMerchantId`
- tables: `id`

## rrsjk-echannel-service/rrsjk-echannel-impl/src/main/resources/mybatis/mapper/platform/MerchantEchannelDouyin.xml
- namespace: `com.rrsjk.echannel.platform.dao.MerchantEchannelDouyinDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByAll`
- tables: `id`

## rrsjk-echannel-service/rrsjk-echannel-impl/src/main/resources/mybatis/mapper/platform/MerchantEchannelBeibei.xml
- namespace: `com.rrsjk.echannel.platform.dao.MerchantEchannelBeibeiDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByAll`
- tables: `id`

## rrsjk-echannel-service/rrsjk-echannel-impl/src/main/resources/mybatis/mapper/platform/MerchantEchannelCcb.xml
- namespace: `com.rrsjk.echannel.platform.dao.MerchantEchannelCcbDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByAll`
- tables: `id`

## rrsjk-echannel-service/rrsjk-echannel-impl/src/main/resources/mybatis/mapper/platform/EchannelTradePromotion.xml
- namespace: `com.rrsjk.echannel.platform.dao.EchannelTradePromotionDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByTid`
- tables: `id`

## rrsjk-echannel-service/rrsjk-echannel-impl/src/main/resources/mybatis/mapper/platform/MerchantEchannelTmall.xml
- namespace: `com.rrsjk.echannel.platform.dao.MerchantEchannelTmallDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByAll`
- tables: `id`

## rrsjk-echannel-service/rrsjk-echannel-impl/src/main/resources/mybatis/mapper/platform/MerchantTrade.xml
- namespace: `com.rrsjk.echannel.platform.dao.MerchantTradeDao`
- statements: `select:countOf`, `select:findBy`
- tables: `echannel_trade_order`

## rrsjk-echannel-service/rrsjk-echannel-impl/src/main/resources/mybatis/mapper/platform/EchannelType.xml
- namespace: `com.rrsjk.echannel.platform.dao.EchannelTypeDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByEnabled`
- tables: `id`

## rrsjk-echannel-service/rrsjk-echannel-impl/src/main/resources/mybatis/mapper/platform/EchannelRefund.xml
- namespace: `com.rrsjk.echannel.platform.dao.EchannelRefundDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByChannelAndRefundNo`
- tables: `id`

## rrsjk-echannel-service/rrsjk-echannel-impl/src/main/resources/mybatis/mapper/platform/EchannelOrderQueue.xml
- namespace: `com.rrsjk.echannel.platform.dao.EchannelOrderQueueDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByChannelAndTradeId`, `select:findBySuccess`
- tables: `id`

## rrsjk-echannel-service/rrsjk-echannel-impl/src/main/resources/mybatis/mapper/platform/EchannelApi.xml
- namespace: `com.rrsjk.echannel.platform.dao.EchannelApiDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByChannelAndApi`
- tables: `id`

## rrsjk-echannel-service/rrsjk-echannel-impl/src/main/resources/mybatis/mapper/platform/EchannelTradeOrder.xml
- namespace: `com.rrsjk.echannel.platform.dao.EchannelTradeOrderDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByOid`, `select:getByOrderItemNo`, `select:findByTid`, `select:getByChannelAndOid`, `select:findByChannelAndTid`
- tables: `id`

## rrsjk-echannel-service/rrsjk-echannel-impl/src/main/resources/mybatis/mapper/platform/EchannelTrade.xml
- namespace: `com.rrsjk.echannel.platform.dao.EchannelTradeDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByTid`, `select:getByOrderNo`, `select:getByChannelAndTid`
- tables: `id`

## rrsjk-echannel-service/rrsjk-echannel-impl/src/main/resources/mybatis/mapper/platform/EchannelSku.xml
- namespace: `com.rrsjk.echannel.platform.dao.EchannelSkuDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByChannelAndOuterSku`, `select:findBySkuId`, `select:findBySkuCode`, `select:countOf`, `select:findBy`
- tables: `id`

## rrsjk-echannel-service/rrsjk-echannel-impl/src/main/resources/mybatis/mapper/platform/EchannelRefundQueue.xml
- namespace: `com.rrsjk.echannel.platform.dao.EchannelRefundQueueDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByChannelTypeRefundId`, `select:findBySuccess`
- tables: `id`

## haier-energy-job-service/snail-job-datasource/snail-job-dm8-datasource/src/main/resources/dm/mapper/RetrySummaryMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetrySummaryMapper`
- statements: `insert:insertBatch`, `update:updateBatch`, `select:selectRetryTask`, `select:selectRetryTaskBarList`, `select:selectRetryLineList`, `select:selectDashboardRankList`
- tables: `id`, `sj_retry_summary`

## haier-energy-job-service/snail-job-datasource/snail-job-dm8-datasource/src/main/resources/dm/mapper/JobTaskMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobTaskMapper`
- statements: `insert:insertBatch`
- tables: `sj_job_task`

## haier-energy-job-service/snail-job-datasource/snail-job-dm8-datasource/src/main/resources/dm/mapper/RetryTaskLogMessageMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetryTaskLogMessageMapper`
- statements: `insert:insertBatch`, `update:updateBatch`
- tables: `id`, `sj_retry_task_log_message`

## haier-energy-job-service/snail-job-datasource/snail-job-dm8-datasource/src/main/resources/dm/mapper/JobExecutorMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobExecutorMapper`
- statements: `insert:insertBatch`
- tables: `sj_job_executor`

## haier-energy-job-service/snail-job-datasource/snail-job-dm8-datasource/src/main/resources/dm/mapper/WorkflowMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.WorkflowMapper`
- statements: `update:updateBatchNextTriggerAtById`
- tables: `id`, `sj_workflow`

## haier-energy-job-service/snail-job-datasource/snail-job-dm8-datasource/src/main/resources/dm/mapper/JobSummaryMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobSummaryMapper`
- statements: `insert:insertBatch`, `update:updateBatch`, `select:selectJobLineList`, `select:selectJobTask`, `select:selectDashboardRankList`
- tables: `id`, `sj_job`, `sj_job_summary`, `sj_workflow`

## haier-energy-job-service/snail-job-datasource/snail-job-dm8-datasource/src/main/resources/dm/mapper/RetryMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetryMapper`
- statements: `insert:insertBatch`, `update:updateBatchNextTriggerAtById`, `update:updateBatchNextTriggerAndStatusAtById`
- tables: `id`, `sj_retry`

## haier-energy-job-service/snail-job-datasource/snail-job-dm8-datasource/src/main/resources/dm/mapper/JobLogMessageMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobLogMessageMapper`
- statements: `insert:insertBatch`
- tables: `sj_job_log_message`

## haier-energy-job-service/snail-job-datasource/snail-job-dm8-datasource/src/main/resources/dm/mapper/RetryDeadLetterMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetryDeadLetterMapper`
- statements: `insert:insertBatch`
- tables: `sj_retry_dead_letter`

## haier-energy-job-service/snail-job-datasource/snail-job-dm8-datasource/src/main/resources/dm/mapper/JobMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobMapper`
- statements: `update:updateBatchNextTriggerAtById`
- tables: `id`, `sj_job`

## haier-energy-job-service/snail-job-datasource/snail-job-dm8-datasource/src/main/resources/dm/mapper/ServerNodeMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.ServerNodeMapper`
- statements: `insert:insertBatch`, `update:updateBatchExpireAt`
- tables: `id`, `sj_server_node`

## haier-energy-job-service/snail-job-datasource/snail-job-datasource-template/src/main/resources/template/mapper/RetrySummaryMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetrySummaryMapper`
- statements: `select:selectRetryTaskList`, `select:selectRetryTaskListCount`
- tables: `sj_retry_scene_config`

## haier-energy-job-service/snail-job-datasource/snail-job-datasource-template/src/main/resources/template/mapper/WorkflowNodeMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.WorkflowNodeMapper`
- statements: `select:selectJobUsedInNonLatestWorkflow`
- tables: `sj_workflow`, `sj_workflow_node`

## haier-energy-job-service/snail-job-datasource/snail-job-datasource-template/src/main/resources/template/mapper/WorkflowTaskBatchMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.WorkflowTaskBatchMapper`
- statements: `select:selectWorkflowBatchPageList`, `select:selectWorkflowBatchList`
- tables: `sj_workflow`, `sj_workflow_task_batch`

## haier-energy-job-service/snail-job-datasource/snail-job-datasource-template/src/main/resources/template/mapper/JobSummaryMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobSummaryMapper`
- statements: `select:selectJobTaskList`, `select:selectJobTaskListCount`, `select:selectWorkflowTaskList`, `select:selectWorkflowTaskListCount`
- tables: `sj_job`, `sj_workflow`

## haier-energy-job-service/snail-job-datasource/snail-job-datasource-template/src/main/resources/template/mapper/RetryMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetryMapper`
- statements: `select:selectRetrySummaryList`
- tables: `sj_retry`, `sj_retry_scene_config`

## haier-energy-job-service/snail-job-datasource/snail-job-datasource-template/src/main/resources/template/mapper/JobTaskBatchMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobTaskBatchMapper`
- statements: `select:selectJobBatchPageList`, `select:selectJobBatchSummaryList`, `select:selectWorkflowTaskBatchSummaryList`, `select:selectJobBatchListByIds`
- tables: `sj_job`, `sj_job_task_batch`, `sj_workflow`, `sj_workflow_task_batch`

## haier-energy-job-service/snail-job-datasource/snail-job-datasource-template/src/main/resources/template/mapper/ServerNodeMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.ServerNodeMapper`
- statements: `select:selectActivePodCount`
- tables: `sj_server_node`

## haier-energy-job-service/snail-job-datasource/snail-job-postgres-datasource/src/main/resources/postgresql/mapper/RetrySummaryMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetrySummaryMapper`
- statements: `insert:insertBatch`, `update:updateBatch`, `select:selectRetryTask`, `select:selectRetryTaskBarList`, `select:selectRetryLineList`, `select:selectDashboardRankList`
- tables: `id`, `sj_retry_summary`

## haier-energy-job-service/snail-job-datasource/snail-job-postgres-datasource/src/main/resources/postgresql/mapper/JobTaskMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobTaskMapper`
- statements: `insert:insertBatch`
- tables: `sj_job_task`

## haier-energy-job-service/snail-job-datasource/snail-job-postgres-datasource/src/main/resources/postgresql/mapper/RetryTaskLogMessageMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetryTaskLogMessageMapper`
- statements: `insert:insertBatch`, `update:updateBatch`
- tables: `id`, `sj_retry_task_log_message`

## haier-energy-job-service/snail-job-datasource/snail-job-postgres-datasource/src/main/resources/postgresql/mapper/JobExecutorMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobExecutorMapper`
- statements: `insert:insertBatch`
- tables: `sj_job_executor`

## haier-energy-job-service/snail-job-datasource/snail-job-postgres-datasource/src/main/resources/postgresql/mapper/WorkflowMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.WorkflowMapper`
- statements: `update:updateBatchNextTriggerAtById`
- tables: `id`, `sj_workflow`

## haier-energy-job-service/snail-job-datasource/snail-job-postgres-datasource/src/main/resources/postgresql/mapper/JobSummaryMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobSummaryMapper`
- statements: `insert:insertBatch`, `update:updateBatch`, `select:selectJobLineList`, `select:selectJobTask`, `select:selectDashboardRankList`
- tables: `id`, `sj_job`, `sj_job_summary`, `sj_workflow`

## haier-energy-job-service/snail-job-datasource/snail-job-postgres-datasource/src/main/resources/postgresql/mapper/RetryMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetryMapper`
- statements: `insert:insertBatch`, `update:updateBatchNextTriggerAtById`, `update:updateBatchNextTriggerAndStatusAtById`
- tables: `id`, `sj_retry`

## haier-energy-job-service/snail-job-datasource/snail-job-postgres-datasource/src/main/resources/postgresql/mapper/JobLogMessageMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobLogMessageMapper`
- statements: `insert:insertBatch`
- tables: `sj_job_log_message`

## haier-energy-job-service/snail-job-datasource/snail-job-postgres-datasource/src/main/resources/postgresql/mapper/RetryDeadLetterMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetryDeadLetterMapper`
- statements: `insert:insertBatch`
- tables: `sj_retry_dead_letter`

## haier-energy-job-service/snail-job-datasource/snail-job-postgres-datasource/src/main/resources/postgresql/mapper/JobMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobMapper`
- statements: `update:updateBatchNextTriggerAtById`
- tables: `id`, `sj_job`

## haier-energy-job-service/snail-job-datasource/snail-job-postgres-datasource/src/main/resources/postgresql/mapper/ServerNodeMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.ServerNodeMapper`
- statements: `insert:insertBatch`, `update:updateBatchExpireAt`
- tables: `id`, `sj_server_node`

## haier-energy-job-service/snail-job-datasource/snail-job-oracle-datasource/src/main/resources/oracle/mapper/RetrySummaryMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetrySummaryMapper`
- statements: `insert:insertBatch`, `update:updateBatch`, `select:selectRetryTask`, `select:selectRetryTaskBarList`, `select:selectRetryLineList`, `select:selectDashboardRankList`
- tables: `DUAL`, `id`, `sj_retry_summary`

## haier-energy-job-service/snail-job-datasource/snail-job-oracle-datasource/src/main/resources/oracle/mapper/JobTaskMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobTaskMapper`
- statements: `insert:insertBatch`
- tables: `DUAL`, `sj_job_task`

## haier-energy-job-service/snail-job-datasource/snail-job-oracle-datasource/src/main/resources/oracle/mapper/RetryTaskLogMessageMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetryTaskLogMessageMapper`
- statements: `insert:insertBatch`, `update:updateBatch`
- tables: `id`, `sj_retry_task_log_message`

## haier-energy-job-service/snail-job-datasource/snail-job-oracle-datasource/src/main/resources/oracle/mapper/JobExecutorMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobExecutorMapper`
- statements: `insert:insertBatch`
- tables: `DUAL`, `sj_job_executor`

## haier-energy-job-service/snail-job-datasource/snail-job-oracle-datasource/src/main/resources/oracle/mapper/WorkflowMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.WorkflowMapper`
- statements: `update:updateBatchNextTriggerAtById`
- tables: `id`, `sj_workflow`

## haier-energy-job-service/snail-job-datasource/snail-job-oracle-datasource/src/main/resources/oracle/mapper/JobSummaryMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobSummaryMapper`
- statements: `insert:insertBatch`, `update:updateBatch`, `select:selectJobLineList`, `select:selectJobTask`, `select:selectDashboardRankList`
- tables: `id`, `sj_job`, `sj_job_summary`, `sj_workflow`

## haier-energy-job-service/snail-job-datasource/snail-job-oracle-datasource/src/main/resources/oracle/mapper/RetryMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetryMapper`
- statements: `insert:insertBatch`, `update:updateBatchNextTriggerAtById`, `update:updateBatchNextTriggerAndStatusAtById`
- tables: `DUAL`, `id`, `sj_retry`

## haier-energy-job-service/snail-job-datasource/snail-job-oracle-datasource/src/main/resources/oracle/mapper/JobLogMessageMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobLogMessageMapper`
- statements: `insert:insertBatch`
- tables: `sj_job_log_message`

## haier-energy-job-service/snail-job-datasource/snail-job-oracle-datasource/src/main/resources/oracle/mapper/RetryDeadLetterMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetryDeadLetterMapper`
- statements: `insert:insertBatch`
- tables: `DUAL`, `sj_retry_dead_letter`

## haier-energy-job-service/snail-job-datasource/snail-job-oracle-datasource/src/main/resources/oracle/mapper/JobMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobMapper`
- statements: `update:updateBatchNextTriggerAtById`
- tables: `id`, `sj_job`

## haier-energy-job-service/snail-job-datasource/snail-job-oracle-datasource/src/main/resources/oracle/mapper/ServerNodeMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.ServerNodeMapper`
- statements: `insert:insertBatch`, `update:updateBatchExpireAt`
- tables: `DUAL`, `id`, `sj_server_node`

## haier-energy-job-service/snail-job-datasource/snail-job-mariadb-datasource/src/main/resources/mariadb/mapper/RetrySummaryMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetrySummaryMapper`
- statements: `insert:insertBatch`, `update:updateBatch`, `select:selectRetryTask`, `select:selectRetryTaskBarList`, `select:selectRetryLineList`, `select:selectDashboardRankList`
- tables: `id`, `sj_retry_summary`

## haier-energy-job-service/snail-job-datasource/snail-job-mariadb-datasource/src/main/resources/mariadb/mapper/JobTaskMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobTaskMapper`
- statements: `insert:insertBatch`
- tables: `sj_job_task`

## haier-energy-job-service/snail-job-datasource/snail-job-mariadb-datasource/src/main/resources/mariadb/mapper/RetryTaskLogMessageMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetryTaskLogMessageMapper`
- statements: `insert:insertBatch`, `update:updateBatch`
- tables: `id`, `sj_retry_task_log_message`

## haier-energy-job-service/snail-job-datasource/snail-job-mariadb-datasource/src/main/resources/mariadb/mapper/JobExecutorMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobExecutorMapper`
- statements: `insert:insertBatch`
- tables: `sj_job_executor`

## haier-energy-job-service/snail-job-datasource/snail-job-mariadb-datasource/src/main/resources/mariadb/mapper/WorkflowMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.WorkflowMapper`
- statements: `update:updateBatchNextTriggerAtById`
- tables: `id`, `sj_workflow`

## haier-energy-job-service/snail-job-datasource/snail-job-mariadb-datasource/src/main/resources/mariadb/mapper/JobSummaryMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobSummaryMapper`
- statements: `insert:insertBatch`, `update:updateBatch`, `select:selectJobLineList`, `select:selectJobTask`, `select:selectDashboardRankList`
- tables: `id`, `sj_job`, `sj_job_summary`, `sj_workflow`

## haier-energy-job-service/snail-job-datasource/snail-job-mariadb-datasource/src/main/resources/mariadb/mapper/RetryMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetryMapper`
- statements: `insert:insertBatch`, `update:updateBatchNextTriggerAtById`, `update:updateBatchNextTriggerAndStatusAtById`
- tables: `id`, `sj_retry`

## haier-energy-job-service/snail-job-datasource/snail-job-mariadb-datasource/src/main/resources/mariadb/mapper/JobLogMessageMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobLogMessageMapper`
- statements: `insert:insertBatch`
- tables: `sj_job_log_message`

## haier-energy-job-service/snail-job-datasource/snail-job-mariadb-datasource/src/main/resources/mariadb/mapper/RetryDeadLetterMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetryDeadLetterMapper`
- statements: `insert:insertBatch`
- tables: `sj_retry_dead_letter`

## haier-energy-job-service/snail-job-datasource/snail-job-mariadb-datasource/src/main/resources/mariadb/mapper/JobMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobMapper`
- statements: `update:updateBatchNextTriggerAtById`
- tables: `id`, `sj_job`

## haier-energy-job-service/snail-job-datasource/snail-job-mariadb-datasource/src/main/resources/mariadb/mapper/ServerNodeMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.ServerNodeMapper`
- statements: `insert:insertBatch`, `update:updateBatchExpireAt`
- tables: `id`, `sj_server_node`

## haier-energy-job-service/snail-job-datasource/snail-job-kingbase-datasource/src/main/resources/kingbase/mapper/WorkflowWebConverter.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.ServerNodeMapper`
- statements: `insert:insertBatch`, `update:updateBatchExpireAt`
- tables: `id`, `sj_server_node`

## haier-energy-job-service/snail-job-datasource/snail-job-kingbase-datasource/src/main/resources/kingbase/mapper/RetrySummaryMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetrySummaryMapper`
- statements: `insert:insertBatch`, `update:updateBatch`, `select:selectRetryTask`, `select:selectRetryTaskBarList`, `select:selectRetryLineList`, `select:selectDashboardRankList`
- tables: `id`, `sj_retry_summary`

## haier-energy-job-service/snail-job-datasource/snail-job-kingbase-datasource/src/main/resources/kingbase/mapper/JobTaskMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobTaskMapper`
- statements: `insert:insertBatch`
- tables: `sj_job_task`

## haier-energy-job-service/snail-job-datasource/snail-job-kingbase-datasource/src/main/resources/kingbase/mapper/RetryTaskLogMessageMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetryTaskLogMessageMapper`
- statements: `insert:insertBatch`, `update:updateBatch`
- tables: `id`, `sj_retry_task_log_message`

## haier-energy-job-service/snail-job-datasource/snail-job-kingbase-datasource/src/main/resources/kingbase/mapper/JobExecutorMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobExecutorMapper`
- statements: `insert:insertBatch`
- tables: `sj_job_executor`

## haier-energy-job-service/snail-job-datasource/snail-job-kingbase-datasource/src/main/resources/kingbase/mapper/WorkflowMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.WorkflowMapper`
- statements: `update:updateBatchNextTriggerAtById`
- tables: `id`, `sj_workflow`

## haier-energy-job-service/snail-job-datasource/snail-job-kingbase-datasource/src/main/resources/kingbase/mapper/JobSummaryMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobSummaryMapper`
- statements: `insert:insertBatch`, `update:updateBatch`, `select:selectJobLineList`, `select:selectJobTask`, `select:selectDashboardRankList`
- tables: `id`, `sj_job`, `sj_job_summary`, `sj_workflow`

## haier-energy-job-service/snail-job-datasource/snail-job-kingbase-datasource/src/main/resources/kingbase/mapper/RetryMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetryMapper`
- statements: `insert:insertBatch`, `update:updateBatchNextTriggerAtById`, `update:updateBatchNextTriggerAndStatusAtById`
- tables: `id`, `sj_retry`

## haier-energy-job-service/snail-job-datasource/snail-job-kingbase-datasource/src/main/resources/kingbase/mapper/JobLogMessageMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobLogMessageMapper`
- statements: `insert:insertBatch`
- tables: `sj_job_log_message`

## haier-energy-job-service/snail-job-datasource/snail-job-kingbase-datasource/src/main/resources/kingbase/mapper/RetryDeadLetterMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetryDeadLetterMapper`
- statements: `insert:insertBatch`
- tables: `sj_retry_dead_letter`

## haier-energy-job-service/snail-job-datasource/snail-job-kingbase-datasource/src/main/resources/kingbase/mapper/JobMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobMapper`
- statements: `update:updateBatchNextTriggerAtById`
- tables: `id`, `sj_job`

## haier-energy-job-service/snail-job-datasource/snail-job-sqlserver-datasource/src/main/resources/sqlserver/mapper/RetrySummaryMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetrySummaryMapper`
- statements: `insert:insertBatch`, `update:updateBatch`, `select:selectRetryTask`, `select:selectRetryTaskBarList`, `select:selectRetryLineList`, `select:selectDashboardRankList`
- tables: `id`, `sj_retry_summary`

## haier-energy-job-service/snail-job-datasource/snail-job-sqlserver-datasource/src/main/resources/sqlserver/mapper/JobTaskMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobTaskMapper`
- statements: `insert:insertBatch`
- tables: `sj_job_task`

## haier-energy-job-service/snail-job-datasource/snail-job-sqlserver-datasource/src/main/resources/sqlserver/mapper/RetryTaskLogMessageMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetryTaskLogMessageMapper`
- statements: `insert:insertBatch`, `update:updateBatch`
- tables: `id`, `sj_retry_task_log_message`

## haier-energy-job-service/snail-job-datasource/snail-job-sqlserver-datasource/src/main/resources/sqlserver/mapper/JobExecutorMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobExecutorMapper`
- statements: `insert:insertBatch`
- tables: `sj_job_executor`

## haier-energy-job-service/snail-job-datasource/snail-job-sqlserver-datasource/src/main/resources/sqlserver/mapper/WorkflowMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.WorkflowMapper`
- statements: `update:updateBatchNextTriggerAtById`
- tables: `id`, `sj_workflow`

## haier-energy-job-service/snail-job-datasource/snail-job-sqlserver-datasource/src/main/resources/sqlserver/mapper/JobSummaryMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobSummaryMapper`
- statements: `insert:insertBatch`, `update:updateBatch`, `select:selectJobLineList`, `select:selectJobTask`, `select:selectDashboardRankList`
- tables: `id`, `sj_job`, `sj_job_summary`, `sj_workflow`

## haier-energy-job-service/snail-job-datasource/snail-job-sqlserver-datasource/src/main/resources/sqlserver/mapper/RetryMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetryMapper`
- statements: `insert:insertBatch`, `update:updateBatchNextTriggerAtById`, `update:updateBatchNextTriggerAndStatusAtById`
- tables: `id`, `sj_retry`

## haier-energy-job-service/snail-job-datasource/snail-job-sqlserver-datasource/src/main/resources/sqlserver/mapper/JobLogMessageMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobLogMessageMapper`
- statements: `insert:insertBatch`
- tables: `sj_job_log_message`

## haier-energy-job-service/snail-job-datasource/snail-job-sqlserver-datasource/src/main/resources/sqlserver/mapper/RetryDeadLetterMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetryDeadLetterMapper`
- statements: `insert:insertBatch`
- tables: `sj_retry_dead_letter`

## haier-energy-job-service/snail-job-datasource/snail-job-sqlserver-datasource/src/main/resources/sqlserver/mapper/JobMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobMapper`
- statements: `update:updateBatchNextTriggerAtById`
- tables: `id`, `sj_job`

## haier-energy-job-service/snail-job-datasource/snail-job-sqlserver-datasource/src/main/resources/sqlserver/mapper/ServerNodeMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.ServerNodeMapper`
- statements: `insert:insertBatch`, `update:updateBatchExpireAt`
- tables: `id`, `sj_server_node`

## haier-energy-job-service/snail-job-datasource/snail-job-mysql-datasource/src/main/resources/mysql/mapper/RetrySummaryMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetrySummaryMapper`
- statements: `insert:insertBatch`, `update:updateBatch`, `select:selectRetryTask`, `select:selectRetryTaskBarList`, `select:selectRetryLineList`, `select:selectDashboardRankList`
- tables: `id`, `sj_retry_summary`

## haier-energy-job-service/snail-job-datasource/snail-job-mysql-datasource/src/main/resources/mysql/mapper/JobTaskMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobTaskMapper`
- statements: `insert:insertBatch`
- tables: `sj_job_task`

## haier-energy-job-service/snail-job-datasource/snail-job-mysql-datasource/src/main/resources/mysql/mapper/RetryTaskLogMessageMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetryTaskLogMessageMapper`
- statements: `insert:insertBatch`, `update:updateBatch`
- tables: `id`, `sj_retry_task_log_message`

## haier-energy-job-service/snail-job-datasource/snail-job-mysql-datasource/src/main/resources/mysql/mapper/SnailHttpClient.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetryDeadLetterMapper`
- statements: `insert:insertBatch`
- tables: `sj_retry_dead_letter`

## haier-energy-job-service/snail-job-datasource/snail-job-mysql-datasource/src/main/resources/mysql/mapper/JobExecutorMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobExecutorMapper`
- statements: `insert:insertBatch`
- tables: `sj_job_executor`

## haier-energy-job-service/snail-job-datasource/snail-job-mysql-datasource/src/main/resources/mysql/mapper/WorkflowMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.WorkflowMapper`
- statements: `update:updateBatchNextTriggerAtById`
- tables: `id`, `sj_workflow`

## haier-energy-job-service/snail-job-datasource/snail-job-mysql-datasource/src/main/resources/mysql/mapper/JobSummaryMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobSummaryMapper`
- statements: `insert:insertBatch`, `update:updateBatch`, `select:selectJobLineList`, `select:selectJobTask`, `select:selectDashboardRankList`
- tables: `id`, `sj_job`, `sj_job_summary`, `sj_workflow`

## haier-energy-job-service/snail-job-datasource/snail-job-mysql-datasource/src/main/resources/mysql/mapper/RetryMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.RetryMapper`
- statements: `insert:insertBatch`, `update:updateBatchNextTriggerAtById`, `update:updateBatchNextTriggerAndStatusAtById`
- tables: `id`, `sj_retry`

## haier-energy-job-service/snail-job-datasource/snail-job-mysql-datasource/src/main/resources/mysql/mapper/JobLogMessageMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobLogMessageMapper`
- statements: `insert:insertBatch`
- tables: `sj_job_log_message`

## haier-energy-job-service/snail-job-datasource/snail-job-mysql-datasource/src/main/resources/mysql/mapper/JobMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.JobMapper`
- statements: `update:updateBatchNextTriggerAtById`
- tables: `id`, `sj_job`

## haier-energy-job-service/snail-job-datasource/snail-job-mysql-datasource/src/main/resources/mysql/mapper/ServerNodeMapper.xml
- namespace: `com.aizuda.snailjob.template.datasource.persistence.mapper.ServerNodeMapper`
- statements: `insert:insertBatch`, `update:updateBatchExpireAt`
- tables: `id`, `sj_server_node`

## rrsjk-light-message-service/rrsjk-light-message-impl/src/main/resources/mybatis/mapper/messageSearchHistory.xml
- namespace: `com.rrsjk.light.message.dao.MessageSearchHistoryDao`
- statements: `insert:create`, `select:getSearchHistory`, `delete:deleteById`, `delete:batchDelete`, `delete:deleteByParams`
- tables: `message_search_history`

## rrsjk-light-message-service/rrsjk-light-message-impl/src/main/resources/mybatis/mapper/approvalMessageService.xml
- namespace: `com.rrsjk.light.message.dao.approvalMessageServiceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `approval_message`, `id`, `user_message_relations`

## rrsjk-light-message-service/rrsjk-light-message-impl/src/main/resources/mybatis/mapper/documentMessageService.xml
- namespace: `com.rrsjk.light.message.dao.documentMessageServiceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `document_message`, `id`, `user_message_relations`

## rrsjk-light-message-service/rrsjk-light-message-impl/src/main/resources/mybatis/mapper/userMessageRelationService.xml
- namespace: `com.rrsjk.light.message.dao.userMessageRelationServiceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:countAllUnreadMessages`
- tables: `approval_message`, `document_message`, `id`, `user_message_relations`

## rrsjk-light-message-service/rrsjk-light-message-impl/src/main/resources/mybatis/mapper/urgentMessageService.xml
- namespace: `com.rrsjk.light.message.dao.urgentMessageServiceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByWithScopes`, `update:batchLogicDelete`, `select:getLatestForPopup`, `select:countOfWithScopes`, `select:getLatestForPopupWithScopes`, `select:getPopup`
- tables: `id`, `urgent_message`, `urgent_message_scope`, `user_message_relations`

## rrsjk-light-message-service/rrsjk-light-message-impl/src/main/resources/mybatis/mapper/policyMessageService.xml
- namespace: `com.rrsjk.light.message.dao.policyMessageServiceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByPolicyId`
- tables: `id`, `policy_message`, `user_message_relations`

## rrsjk-light-message-service/rrsjk-light-message-impl/src/main/resources/mybatis/mapper/urgentMessageScope.xml
- namespace: `com.rrsjk.light.message.dao.UrgentMessageScopeDao`
- statements: `insert:create`, `insert:batchInsert`, `select:findByMessageId`, `delete:deleteByMessageId`, `select:findBy`
- tables: `urgent_message_scope`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/PvSaleOrderMapper.xml
- namespace: `com.nahui.energy.mapper.PvSaleOrderMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/PvStationInfoHistoryMapper.xml
- namespace: `com.nahui.energy.mapper.PvStationInfoHistoryMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/PvSystemInteractionLogMapper.xml
- namespace: `com.nahui.energy.mapper.PvSystemInteractionLogMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/PvServiceProviderContractMapper.xml
- namespace: `com.nahui.energy.mapper.PvServiceProviderContractMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/PvStationPayPlanMapper.xml
- namespace: `com.nahui.energy.mapper.PvStationPayPlanMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/ServiceProviderDepositMapper.xml
- namespace: `com.nahui.energy.mapper.ServiceProviderDepositMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/PvPickingOrderMapper.xml
- namespace: `com.nahui.energy.mapper.PvPickingOrderMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/PvServiceProviderMapper.xml
- namespace: `com.nahui.energy.mapper.PvServiceProviderMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/PvSapInterfaceLogMapper.xml
- namespace: `com.nahui.energy.mapper.PvSapInterfaceLogMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/PvPurchaseOrderMapper.xml
- namespace: `com.nahui.energy.mapper.PvPurchaseOrderMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/PvStationMaterialMapper.xml
- namespace: `com.nahui.energy.mapper.PvStationMaterialMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/PvStationInvoiceMapper.xml
- namespace: `com.nahui.energy.mapper.PvStationInvoiceMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/PvStationInfoMapper.xml
- namespace: `com.nahui.energy.mapper.PvStationInfoMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/sap/SapPurchaseReceiptMapper.xml
- namespace: `com.nahui.energy.mapper.sap.SapPurchaseReceiptMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/sap/SapSaleOrderRecordMapper.xml
- namespace: `com.nahui.energy.mapper.sap.SapSaleOrderRecordMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/sap/SapSaleOrderBillingMapper.xml
- namespace: `com.nahui.energy.mapper.sap.SapSaleOrderBillingMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/sap/SapSaleOrderCreateMapper.xml
- namespace: `com.nahui.energy.mapper.sap.SapSaleOrderCreateMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/sap/SapQueueMapper.xml
- namespace: `com.nahui.energy.mapper.sap.SapQueueMapper`
- statements: `select:selectWaitConsume`, `update:lockAndUpdateStatusToProcessing`, `update:updateToSuccess`, `update:updateToFailureWithRetry`, `select:selectPendingProcess`
- tables: `id`, `sap_queue`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/sap/SapSaleOrderDeliveryMapper.xml
- namespace: `com.nahui.energy.mapper.sap.SapSaleOrderDeliveryMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/sap/SapPurchaseOrderMapper.xml
- namespace: `com.nahui.energy.mapper.sap.SapPurchaseOrderMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/sap/SapFinanceReceiptRecordingMapper.xml
- namespace: `com.nahui.energy.mapper.sap.SapFinanceReceiptRecordingMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/sap/SapChannelLogMapper.xml
- namespace: `com.nahui.energy.mapper.sap.SapChannelLogMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/mk/MkSettlementRelateConfirmationMapper.xml
- namespace: `com.nahui.energy.mapper.mk.MkSettlementRelateConfirmationMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/mk/MkInvoiceMapper.xml
- namespace: `com.nahui.energy.mapper.mk.MkInvoiceMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/mk/MkPvSettlementMapper.xml
- namespace: `com.nahui.energy.mapper.mk.MkPvSettlementMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/mk/MkHbcUsedBudgetRecordMapper.xml
- namespace: `com.nahui.energy.mapper.mk.MkHbcUsedBudgetRecordMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/mk/MkSettlementRelateInvoiceMapper.xml
- namespace: `com.nahui.energy.mapper.mk.MkSettlementRelateInvoiceMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/mk/MkPvSettlementAuditLogMapper.xml
- namespace: `com.nahui.energy.mapper.mk.MkPvSettlementAuditLogMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/mk/MkPvConfirmationMapper.xml
- namespace: `com.nahui.energy.mapper.mk.MkPvConfirmationMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/mk/MkHbcLogMapper.xml
- namespace: `com.nahui.energy.mapper.mk.MkHbcLogMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/mk/SettlementQueueMapper.xml
- namespace: `com.nahui.energy.mapper.mk.SettlementQueueMapper`
- statements: `select:selectWaitConsume`, `update:lockAndUpdateStatusToProcessing`, `update:updateToSuccess`, `update:updateToFailureWithRetry`, `select:selectPendingProcess`
- tables: `id`, `settlement_queue`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/mk/MkYbzLogMapper.xml
- namespace: `com.nahui.energy.mapper.mk.MkYbzLogMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/mk/MkYbzSettlementCallBackLogMapper.xml
- namespace: `com.nahui.energy.mapper.mk.MkYbzSettlementCallBackLogMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/mk/MkYbzQueryStatusLogMapper.xml
- namespace: `com.nahui.energy.mapper.mk.MkYbzQueryStatusLogMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/mk/MkHbcOccupyRecordMapper.xml
- namespace: `com.nahui.energy.mapper.mk.MkHbcOccupyRecordMapper`

## vpp-pv-oversea/vpp-pv-oversea-biz/src/main/resources/mapper/mk/MkYbzSettlementRecordMapper.xml
- namespace: `com.nahui.energy.mapper.mk.MkYbzSettlementRecordMapper`

## vpp-pv-oversea/vpp-pv-ex-api/src/main/resources/mapper/OverseaRequestLogMapper.xml
- namespace: `com.nahui.energy.mapper.OverseaRequestLogMapper`

## vpp-pv-oversea/vpp-pv-ex-api/src/main/resources/mapper/OverseaYbzSettlementCallbackMapper.xml
- namespace: `com.nahui.energy.mapper.OverseaYbzSettlementCallbackMapper`

## system-service/system-impl/src/main/resources/system-sql-mapper/SysUserRoleMapper.xml
- namespace: `com.haier.cbs.system.dao.SysUserRoleDao`
- statements: `select:get`, `insert:insert`, `update:update`
- tables: `id`, `sys_user_role`

## system-service/system-impl/src/main/resources/system-sql-mapper/SysPermissionMapper.xml
- namespace: `com.haier.cbs.system.dao.SysPermissionDao`
- statements: `select:find`, `select:findResourceIdsByOwnerId`, `select:findResourceIdsByOwnerIds`, `insert:create`, `update:update`, `select:findButtonpermissionByOwnerId`, `select:findButtonpermissionByOwnerIds`, `select:findResIdsByRoleIds`, `select:findByResId`
- tables: `id`, `sys_menu`, `sys_permission`

## system-service/system-impl/src/main/resources/system-sql-mapper/SysAccessLogMapper.xml
- namespace: `com.haier.cbs.system.dao.SysAccessLogDao`
- statements: `insert:create`, `select:find`, `select:findCount`, `update:update`
- tables: `id`, `sys_access_log`

## system-service/system-impl/src/main/resources/system-sql-mapper/SysUserMapper.xml
- namespace: `com.haier.cbs.system.dao.SysUserDao`
- statements: `select:findUserRoleIds`, `select:find`, `select:findCount`, `select:getByLoginId`, `select:get`, `update:update`, `insert:create`, `update:updatePasswordByUserId`, `select:getGmByUserId`, `select:findUserIdsByRoleId`
- tables: `id`, `sys_party`, `sys_party_user`, `sys_role`, `sys_user`, `sys_user_role`

## system-service/system-impl/src/main/resources/system-sql-mapper/SysPartyRelevanceMapper.xml
- namespace: `com.haier.cbs.system.dao.SysPartyRelevanceDao`
- statements: `insert:insert`, `select:count`, `select:findPartyRelevanceByPager`, `select:findPartyRelevanceByPartyId`
- tables: `sys_party_relevance`

## system-service/system-impl/src/main/resources/system-sql-mapper/SysActionMapper.xml
- namespace: `com.haier.cbs.system.dao.SysActionDao`
- statements: `select:find`, `select:findCount`, `select:findByUrl`, `select:findByActKey`, `select:get`, `insert:create`, `update:update`
- tables: `id`, `sys_action`, `sys_menu`

## system-service/system-impl/src/main/resources/system-sql-mapper/SysSubCenterMapper.xml
- namespace: `com.haier.cbs.system.dao.SysSubCenterDao`
- statements: `select:getById`, `select:getByIds`, `select:getByCode`, `select:findAll`, `select:count`, `select:findByPager`
- tables: `sys_sub_center`

## system-service/system-impl/src/main/resources/system-sql-mapper/V3BranchRegionMapper.xml
- namespace: `com.haier.cbs.system.dao.V3BranchRegionDao`
- statements: `select:getByRegionId`, `select:getRegionByBranchCode`, `select:getRegionByRegionList`, `select:getRegionByBranchCodeList`, `select:getByRegionCode`
- tables: `v3_branch_region`

## system-service/system-impl/src/main/resources/system-sql-mapper/SysSubCenterUserMapper.xml
- namespace: `com.haier.cbs.system.dao.SysSubCenterUserDao`
- statements: `insert:insert`, `update:update`, `select:count`, `select:findByPager`, `select:getById`, `select:getByUserId`, `select:getBySubCenterId`, `select:getUserIdsBySubCenterId`, `select:countBySubCenterIdAndUserId`, `update:batchDeleteBySubCenterIdAndUserIds`, `update:deleteByUserId`, `select:getBySubCenterIds`
- tables: `id`, `sys_sub_center_user`

## system-service/system-impl/src/main/resources/system-sql-mapper/SysMenuMapper.xml
- namespace: `com.haier.cbs.system.dao.SysMenuDao`
- statements: `select:loadMenus`, `select:findAllMenus`, `insert:create`, `update:update`, `select:get`, `select:findMenusByCode`, `select:findAllStatusMenuByCode`, `select:findMenuModuleIdBySys`, `select:findRelateMessageMenu`, `select:findByCode`
- tables: `id`, `sys_menu`

## system-service/system-impl/src/main/resources/system-sql-mapper/SysPartyMapper.xml
- namespace: `com.haier.cbs.system.dao.SysPartyDao`
- statements: `insert:insert`, `update:update`, `select:count`, `select:findPartyByPager`, `select:getById`, `select:getByIds`, `select:findParttListByType`, `select:getSysPartyByCode`, `select:findPartyByUserId`, `select:findAllParty`, `update:updateParentInfo`, `select:getByParentId`, `select:getByParentIds`
- tables: `id`, `sys_party`

## system-service/system-impl/src/main/resources/system-sql-mapper/RegionsMapper.xml
- namespace: `com.haier.cbs.system.dao.RegionsDao`
- statements: `select:get`, `select:getRegionByPidAndName`, `select:findAllByRegionType`, `select:findRegionLikeRegionName`, `select:findRegionByRegionName`, `select:getByParentId`, `select:getByParentCodeAndParentRegionType`, `select:getProvinces`, `select:getCities`, `select:getRegions`, `select:getRegionsByCodes`, `select:getCityIdsByRegions`, `select:getRegionsNameByIds`, `select:getDirectByRegionName`
- tables: `Regions`

## system-service/system-impl/src/main/resources/system-sql-mapper/SysPartyUserMapper.xml
- namespace: `com.haier.cbs.system.dao.SysPartyUserDao`
- statements: `insert:insert`, `update:update`, `select:count`, `select:findPartyUserByPager`, `select:getPartyUserById`, `select:getPartyUserByUserId`, `delete:delete`, `select:getPartyUserByPartyId`, `select:findPartyIdByUser`, `select:getPartyUserByPartyIds`, `select:countNew`, `select:findPartyUserNewByPager`, `select:findPartyUserByParams`, `select:getPartyUserByPartyCodes`
- tables: `id`, `sys_party`, `sys_party_user`, `sys_user`

## system-service/system-impl/src/main/resources/system-sql-mapper/SysMessagePermissionMapper.xml
- namespace: `com.haier.cbs.system.dao.SysMessagePermissionDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findMessageIdsByOwnerId`, `select:findByMessageIdsAndOwnerIds`, `select:findByMessageIdAndOwnerId`
- tables: `id`

## system-service/system-impl/src/main/resources/system-sql-mapper/SysMessageMapper.xml
- namespace: `com.haier.cbs.system.dao.SysMessageDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByIds`, `select:findByResId`, `select:findByResIds`, `select:findByRelateInfo`
- tables: `id`

## system-service/system-impl/src/main/resources/system-sql-mapper/SysSessionMapper.xml
- namespace: `com.haier.cbs.system.dao.SysSessionDao`
- statements: `select:get`, `insert:create`, `update:update`, `delete:delete`
- tables: `id`, `sys_session`

## system-service/system-impl/src/main/resources/system-sql-mapper/SysRoleMapper.xml
- namespace: `com.haier.cbs.system.dao.SysRoleDao`
- statements: `select:find`, `select:findCount`, `select:findUserRoleAssigned`, `select:findUserRoleUnAssigned`, `select:get`, `insert:create`, `update:update`, `insert:assignUserRoles`, `update:unassignUserRole`, `select:findUserIdByRoleIds`
- tables: `id`, `sys_role`, `sys_user_role`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/query/LightSpSettleConfig.xml
- namespace: `com.rrsjk.light.data.dao.query.LightSpSettleConfigDao`
- statements: `select:getById`, `select:getByProvinceId`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/query/LightStationInverter.xml
- namespace: `com.rrsjk.light.data.dao.query.LightStationInverterDao`
- statements: `select:getById`, `select:findByParams`, `select:findByUpdate`, `insert:create`, `select:findYxByParams`, `update:unBindInveter`, `select:findInverterMode`
- tables: `id`, `light_service_provider`, `light_station`, `light_station_inverter`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/query/LightSkuData.xml
- namespace: `com.rrsjk.light.data.dao.query.LightSkuDataDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findAll`
- tables: `id`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/query/LightStation.xml
- namespace: `com.rrsjk.light.data.dao.query.LightStationDao`
- statements: `select:get`, `select:getByStationCode`, `select:listStationSingle`, `select:listStation`, `select:listStationPlus`, `select:listStationValidPlus`, `select:findBy`, `select:countOf`, `update:updateLinkAt`, `update:updatefirstFetchGene`, `update:updatefirstValidFetchGene`, `select:findByStationCode`, `select:countOfYueXiu`, `select:findToYuexiuLightStation`, `select:findListByFirstThreePower`, `select:findHouseholdGridQuota`, `select:findPublicBuildingsGridQuota`, `select:findMultiGridQuota`, `select:findIndustryGridQuota`, `select:findSocialGridQuota`, `select:findWholeGridQuota`
- tables: `id`, `light_station`, `light_station_audit`, `light_station_yuexiu`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/query/LightStationWhiteList.xml
- namespace: `com.rrsjk.light.data.dao.query.LightStationWhiteListDao`
- statements: `select:getByStationCode`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/query/LightStationConfirmImg.xml
- namespace: `com.rrsjk.light.data.dao.query.LightStationConfirmImgDao`
- statements: `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:getByImaNameAndType`, `select:getByImaNameAndTypeAndStationCode`, `select:getByImaNameAndStationCode`, `select:getListByImaNameAndType`, `select:getListByImaNameAndTypeAndStationCode`, `select:findByStationCodeAndTypeNoFilter`, `select:getGsyAppStationImg`, `select:findByStationIdAndTypeNoFilter`, `select:getByIds`, `select:getByStationCode`
- tables: `id`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/query/LightServiceProvider.xml
- namespace: `com.rrsjk.light.data.dao.query.LightServiceProviderDao`
- statements: `select:getById`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/query/LightStationPlanConfig.xml
- namespace: `com.rrsjk.light.data.dao.query.LightStationPlanConfigDao`
- statements: `select:getById`, `select:findByParams`, `select:findPower`, `select:findInverter`
- tables: `light_station_plan_config`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/ads/AdsReportStationChartTotal.xml
- namespace: `com.rrsjk.light.data.dao.ads.AdsReportStationChartTotalDao`
- statements: `select:findChart`
- tables: `ads.green_energy_report_light_station_chart_total`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/ads/AdsReportInveterChartTotal.xml
- namespace: `com.rrsjk.light.data.dao.ads.AdsReportInveterChartTotalDao`
- statements: `select:findChart`
- tables: `ads.green_energy_report_light_inverter_chart_total`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/ads/AdsReportInveterChartYear.xml
- namespace: `com.rrsjk.light.data.dao.ads.AdsReportInveterChartYearDao`
- statements: `select:findChart`
- tables: `ads.green_energy_report_light_inverter_chart_year`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/ads/AdsReportStationChartYear.xml
- namespace: `com.rrsjk.light.data.dao.ads.AdsReportStationChartYearDao`
- statements: `select:findChart`
- tables: `ads.green_energy_report_light_station_chart_year`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/ads/AdsReportInveterChartDay.xml
- namespace: `com.rrsjk.light.data.dao.ads.AdsReportInveterChartDayDao`
- statements: `select:findChart`
- tables: `ads.green_energy_report_light_inverter_chart_day`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/ads/AdsReportStationChartMonth.xml
- namespace: `com.rrsjk.light.data.dao.ads.AdsReportStationChartMonthDao`
- statements: `select:findChart`
- tables: `ads.green_energy_report_light_station_chart_month`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/ads/AdsReportInveterPacChartDay.xml
- namespace: `com.rrsjk.light.data.dao.ads.AdsReportInveterPacChartDayDao`
- statements: `select:findChart`
- tables: `ads.green_energy_report_light_inverter_pac_chart_day`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/ads/AdsReportInveterChartMonth.xml
- namespace: `com.rrsjk.light.data.dao.ads.AdsReportInveterChartMonthDao`
- statements: `select:findChart`, `select:findChartPro`
- tables: `ads.green_energy_report_light_inverter_chart_month`, `dws.green_energy_inverter_current`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/ads/AdsReportStationChartDay.xml
- namespace: `com.rrsjk.light.data.dao.ads.AdsReportStationChartDayDao`
- statements: `select:findChart`, `select:getMinFetchAt`
- tables: `ads.green_energy_report_light_station_chart_day`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/LightStationElecMonthReportNew.xml
- namespace: `com.rrsjk.light.data.dao.local.LightStationElecMonthReportNewDao`
- statements: `select:findBy`, `select:countOfSum`, `select:findBySum`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByGroupByStationCode`, `update:updateByStationCode`
- tables: `id`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/LightStationInverter.xml
- namespace: `com.rrsjk.light.data.dao.local.LightStationInverterDao`
- statements: `select:getById`, `select:findByParams`, `select:findByUpdate`, `select:findYxByParams`, `update:unBindInveter`, `update:clearRelation`, `select:findInverterMode`
- tables: `id`, `light_service_provider`, `light_station`, `light_station_inverter`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/LightStationElecDayReportNew.xml
- namespace: `com.rrsjk.light.data.dao.local.LightStationElecDayReportNewDao`
- statements: `select:findBy`, `select:countOfSum`, `select:findBySum`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByGroupByStationCode`, `update:updateByStationCode`
- tables: `id`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/LightFirstThreePowerLog.xml
- namespace: `com.rrsjk.light.data.dao.local.LightFirstThreePowerLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/LightElecPush.xml
- namespace: `com.rrsjk.light.data.dao.local.LightElecPushDao`
- statements: `select:findBy`, `select:findLatestBySns`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/ReportStationYearSummary.xml
- namespace: `com.rrsjk.light.data.dao.local.ReportStationYearSummaryDao`
- statements: `select:queryByStationCodes`, `select:queryMonthsByStationCodes`, `select:queryDaysByStationCodes`, `select:queryYearTotalByStationCodes`, `insert:batchUpsert`, `select:countByTable`
- tables: `elec`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/ReportProblemStation.xml
- namespace: `com.rrsjk.light.data.dao.local.ReportProblemStationDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByStationCode`, `insert:batchUpsert`
- tables: `id`, `station_name`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/LightStationElecDayReport.xml
- namespace: `com.rrsjk.light.data.dao.local.LightStationElecDayReportDao`
- statements: `select:findBySum`, `select:findBy`, `select:findChartPro`, `select:countOfSum`, `insert:create`, `update:update`, `update:updateFirstAudit`, `insert:batchInsert`, `select:getById`, `select:getStationCode`, `select:getMonthElec`, `update:updateByStationCodeFetchAt`
- tables: `id`, `light_station_elec_day_report`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/ReportInveterChartDay.xml
- namespace: `com.rrsjk.light.data.dao.local.ReportInveterChartDayDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findByParams`, `select:findChart`, `select:getHourZero`, `select:getHourZeroSix`, `select:findDayElec`, `insert:batchInsert`
- tables: `id`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/LightInveterRecord.xml
- namespace: `com.rrsjk.light.data.dao.local.LightInveterRecordDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryListByIdAsc`, `select:queryCountBy`, `select:findByParams`, `select:findByTimes`, `select:findByParamsSpec`, `select:getMinDataTimeBySn`, `select:getMaxTodayElec`, `select:findElec`, `select:findMonthAndYear`, `select:findYear`, `select:findTotal`, `select:findByInverterSn`, `select:findLightInveterRecord`, `select:findHistoryRecord`, `select:findByMonth`, `update:updatePushAt`
- tables: `id`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/LightProfit.xml
- namespace: `com.rrsjk.light.data.dao.local.LightProfitDao`
- statements: `insert:create`, `update:update`, `select:findByParams`, `select:getByDataTime`
- tables: `id`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/LightStation.xml
- namespace: `com.rrsjk.light.data.dao.local.LightStationDao`
- statements: `select:get`, `select:getByStationCode`, `select:listStationSingle`, `select:listStation`, `select:listStationPlus`, `select:findBy`, `select:countOf`, `update:updateLinkAt`, `update:updatefirstFetchGene`, `select:findByStationCode`, `select:countOfYueXiu`, `select:findToYuexiuLightStation`, `select:findListByFirstThreePower`, `select:findHouseholdGridQuota`, `select:findPublicBuildingsGridQuota`, `select:findMultiGridQuota`, `select:findIndustryGridQuota`, `select:countForSync`, `select:findByForSync`
- tables: `id`, `light_station`, `light_station_audit`, `light_station_plan_config`, `light_station_yuexiu`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/LightInveterBase.xml
- namespace: `com.rrsjk.light.data.dao.local.LightInveterBaseDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getBySn`, `select:getBySns`
- tables: `id`, `light_inveter_base`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/LightCostConfig.xml
- namespace: `com.rrsjk.light.data.dao.local.LightCostConfigDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/ReportInveterPacChartDay.xml
- namespace: `com.rrsjk.light.data.dao.local.ReportInveterPacChartDayDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:findByParams`, `select:findChart`, `select:findChartPro`, `select:getHourZero`, `select:listRange`, `select:getPacCountByStationCode`
- tables: `id`, `light_inveter_data`, `pac`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/ReportStationChartYear.xml
- namespace: `com.rrsjk.light.data.dao.local.ReportStationChartYearDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:findChart`, `select:getElecReport`
- tables: `id`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/LightInveterData.xml
- namespace: `com.rrsjk.light.data.dao.local.LightInveterDataDao`
- statements: `insert:create`, `insert:batchInsert`, `insert:createRecord`, `insert:unBindLog`, `select:getUnbindCountByInveterSn`, `update:updateForStopStatus`, `update:update`, `update:unBindStation`, `update:updateBindedStatusBySn`, `update:unBindStation1`, `select:getById`, `select:getByInverterSn`, `select:listAllInveterSn`, `select:findBySns`, `select:queryListBy`, `select:findByOp`, `select:queryListProBy`, `select:queryCountProBy`, `select:queryCountBy`, `select:queryCountByOp`, `select:findByParams`, `select:findForProfit`, `select:findStationElec`, `select:listInveterError`, `select:listInveterErrorNow`, `select:listCodeBind`, `select:queryInverterDataForKTC`, `select:findGridStation`, `select:findTotalGridStation`, `select:getDeviceInfo`, `select:countDeviceInfo`, `select:findByPageBySht`, `select:countBySht`, `update:updateByOperationState`, `select:findByUpdate`, `select:findYxByParams`, `select:queryListDtoBy`, `select:queryListProByInProvince`, `select:queryListByInCmb`, `select:queryCountProByInProvince`, `select:queryCountByInCmb`, `select:getBindAt`, `select:queryChdStationCode`, `select:queryBocStationCode`, `select:findWaitHandleData`, `select:newFindCountByCbs`, `select:newFindByCbs`, `select:exportByCbs`, `select:queryCqGdtCountByPage`, `select:findCqGdtByPage`, `select:countDelayByBrand`, `select:findUnbindStationCandidates`, `select:findReStationBoundCandidates`
- tables: `boc_leasing_light_station`, `chd_light_station`, `cmb_leasing_station`, `id`, `light_inveter`, `light_inveter_data`, `light_inveter_data_record`, `light_station`, `light_station_elec`, `light_station_inverter`, `light_station_white_list`, `unbind_operation_log`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/LightCollector.xml
- namespace: `com.rrsjk.light.data.dao.local.LightCollectorDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:getLastData`
- tables: `id`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/ReportInveterChartTotal.xml
- namespace: `com.rrsjk.light.data.dao.local.ReportInveterChartTotalDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:findChart`
- tables: `id`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/LightStationPlanConfig.xml
- namespace: `com.rrsjk.light.data.dao.local.LightStationPlanConfigDao`
- statements: `select:getById`, `select:findByParams`, `select:findPower`, `select:findInverter`
- tables: `light_station_plan_config`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/LightCollectorRecord.xml
- namespace: `com.rrsjk.light.data.dao.local.LightCollectorRecordDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/ReportStationChartMonth.xml
- namespace: `com.rrsjk.light.data.dao.local.ReportStationChartMonthDao`
- statements: `insert:create`, `insert:batchCreateIfAbsent`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:getElecMonth`, `select:findChart`, `select:getElecReport`, `select:getElecCount`, `select:queryInvertersElectric`, `select:queryPowerDaysInRange`, `select:queryMonthlyElecIn12Months`, `select:queryLastPowerDate`, `select:queryYearTotalElec`, `select:queryMonthTotalElecByYear`, `select:queryDayElecByYearMonth`, `select:queryCityDayAvgElec`, `select:queryStationAvgFullHourInRange`, `select:queryStationMonthAvgFullHourByYear`
- tables: `id`, `report_problem_station`, `report_station_chart_month`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/LightInveterAlarm.xml
- namespace: `com.rrsjk.light.data.dao.local.LightInveterAlarmDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/LightStationLocal.xml
- namespace: `com.rrsjk.light.data.dao.local.LightStationLocalDao`
- statements: `select:get`, `select:getByStationCode`, `select:listStationSingle`, `select:listStation`, `select:listStationPlus`, `select:findBy`, `select:countOf`, `update:updateLinkAt`, `update:updatefirstFetchGene`, `select:findByStationCode`, `select:countOfYueXiu`, `select:findToYuexiuLightStation`, `select:findListByFirstThreePower`, `select:findHouseholdGridQuota`, `select:findPublicBuildingsGridQuota`, `select:findMultiGridQuota`, `select:findIndustryGridQuota`
- tables: `id`, `light_station`, `light_station_audit`, `light_station_plan_config`, `light_station_yuexiu`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/NengKongCloudInverterData.xml
- namespace: `com.rrsjk.light.data.dao.local.NengKongCloudInverterDataDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findLastedByDeviceSn`, `select:getNeedHandlerList`, `select:getNeedHandlerListHistory`, `update:batchHandlerFinish`
- tables: `id`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/LightInveter.xml
- namespace: `com.rrsjk.light.data.dao.local.LightInveterDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `update:batchUpdate`, `select:getById`, `select:queryListBy`, `select:inverterQueryByPage`, `select:inverterQueryByPagePro`, `select:inverterQueryCountOf`, `select:inverterQueryCountOfPro`, `select:queryCountBy`, `select:findByParams`, `select:findFirstThreePowerSource`, `select:findForHistory`, `select:queryInvertersElectric`, `select:findFirstThreePowerAtBySnList`, `select:findSampleByParams`, `select:findDeduplicateCandidatesByFetchAt`, `select:listDuplicateInveterSnByFetchAt`, `select:findDeduplicateCandidatesByFetchAtAndSn`, `delete:deleteByIds`, `select:findMonthAndYear`, `select:findYear`, `select:findTotal`, `select:findByParamsNow`, `select:getSum`, `select:getMinFetchAtBySn`, `select:getMaxFetchAtBySn`, `select:getSumFullHour`, `select:getErrMsg`, `select:getLastBySn`, `select:getLastBySnSimple`, `select:findContinueElec`, `select:findContinuousElecSns`, `select:listSnFetch`, `select:listSnFetchBySnList`, `select:listSnByElecZero`, `select:listToday`, `select:listTodayNotZero`, `select:querySeriesGenerateElec`, `select:doExportWithMonth`, `select:doExportWithDay`, `select:doExportWithMonthCount`, `select:powerQuery`, `select:powerQueryPro`, `select:powerQueryMin`, `select:findByToday`, `select:findByTodayCount`, `select:findStationElecByDay`, `select:getLatestOneByFetchAt`, `select:findCountByNotZero`, `select:findHistoryZero`, `select:findHistoryZeroCount`, `select:getElectricByFetchAtAndInverterSns`, `select:getElectricByFetchAtAndInverterSn`, `select:getElectricMonthByFetchAtAndInverterSns`, `update:updateByInverterAndFetchAt`, `select:listDistinctSnByDataSource`, `select:listLatestByFetchAt`, `select:listInveterSnByFetchAt`, `insert:batchInsertOccupy`
- tables: `id`, `light_inveter`, `light_inveter_data`, `light_inveter_err`, `light_station`, `light_station_elec`, `light_station_elec_day_report`, `light_station_elec_day_report_new`, `light_station_plan_config`, `light_station_white_list`, `rrsjk_light_data.light_inveter_data`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/InverterErrorDict.xml
- namespace: `com.rrsjk.light.data.dao.local.InverterErrorDictDao`
- statements: `select:findBy`, `select:findParams`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/ReportInveterChartMonth.xml
- namespace: `com.rrsjk.light.data.dao.local.ReportInveterChartMonthDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:findChart`, `select:findChartPro`
- tables: `id`, `light_inveter_data`, `report_inveter_chart_month`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/ReportExportTask.xml
- namespace: `com.rrsjk.light.data.dao.local.ReportExportTaskDao`
- statements: `insert:create`, `update:update`, `select:getByTaskNo`, `select:queryListBy`
- tables: `id`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/ReportInveterChartYear.xml
- namespace: `com.rrsjk.light.data.dao.local.ReportInveterChartYearDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:findChart`, `select:findChartPro`
- tables: `id`, `light_inveter_data`, `report_inveter_chart_year`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/ReportStationChartDay.xml
- namespace: `com.rrsjk.light.data.dao.local.ReportStationChartDayDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findByParams`, `select:findChart`, `select:getMinFetchAt`
- tables: `id`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/ReportStationChartTotal.xml
- namespace: `com.rrsjk.light.data.dao.local.ReportStationChartTotalDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:findChart`, `select:getElecReport`
- tables: `id`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/SnProvinceConfig.xml
- namespace: `com.rrsjk.light.data.dao.local.SnProvinceConfigDao`
- statements: `select:findByInverterSn`, `select:findByInverterSnList`, `select:findAll`, `insert:create`, `update:update`, `delete:deleteByInverterSn`
- tables: `id`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/LightStationElec.xml
- namespace: `com.rrsjk.light.data.dao.local.LightStationElecDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `update:updateElectricity`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:findByOpIdNull`, `select:getElecSum`, `select:findNoFirstThreePowerAt`, `select:findCount2StationCode`, `select:countOfForCBSExport`, `select:findByForCBSExport`, `select:countOfForHdsExport`, `select:findByForHdsExport`, `select:countOfForHdsExportInCmb`, `select:findByForHdsExportInCmb`, `update:makeZero`, `select:countOfForHdsExportNew`, `select:findByForHdsExportNew`, `select:getGroupByStationCode`, `delete:deleteInvalidData`
- tables: `cmb_leasing_station`, `id`, `light_inveter`, `light_inveter_data`, `light_station`, `light_station_elec`, `light_station_elec_day_report_new`, `light_station_plan_config`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/LightInveterSmall.xml
- namespace: `com.rrsjk.light.data.dao.local.LightInveterSmallDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `update:batchUpdate`, `select:findByParams`, `select:getMixFetchAtBySn`
- tables: `id`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/local/LightFirstValidThreePowerLog.xml
- namespace: `com.rrsjk.light.data.dao.local.LightFirstValidThreePowerLogDao`
- statements: `insert:create`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/dws/DwsLightStationElecDayReportNew.xml
- namespace: `com.rrsjk.light.data.dao.dws.DwsLightStationElecDayReportNewDao`
- statements: `select:findChartPro`, `select:countOfSum`, `select:findBySum`, `select:findBy`, `select:countOfSum`, `select:findBySum`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByGroupByStationCode`, `update:updateByStationCode`
- tables: `dws.green_energy_light_station_daily_current`, `id`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/dws/DwsLightStationElec.xml
- namespace: `com.rrsjk.light.data.dao.dws.DwsLightStationElecDao`
- statements: `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:getElecSum`, `update:updateFirstThreePowerAtByStationCode`, `update:updateFirstValidThreePowerAtByStationCode`
- tables: `dws.green_energy_light_station_realtime_current`, `id`, `ods.green_energy_light_station`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/dws/DwsInveterData.xml
- namespace: `com.rrsjk.light.data.dao.dws.DwsInveterDataDao`
- statements: `select:countByPage`, `select:findByPage`, `select:getBySn`, `select:findByParams`
- tables: `dws.green_energy_inverter_current`, `light_station_white_list`, `ods.green_energy_light_station`

## rrsjk-light-data-service/rrsjk-light-data-impl/src/main/resources/mybatis/mapper/ods/OdsLightStationElec.xml
- namespace: `com.rrsjk.light.data.dao.ods.OdsLightStationElecDao`
- statements: `select:countOfForHdsExportNew`, `select:findByForHdsExportNew`, `select:findHrflcPower`, `select:countHrflcHistoryPower`, `select:findHrflcHistoryPower`
- tables: `green_energy_light_station`, `green_energy_light_station_elec_day_report_new`

## rrsjk-migration-member/rrsjk-data-migration-impl/src/main/resources/mybatis/mapper/shop/ShopLoginInfoMapper.xml
- namespace: `com.rrsjk.data.shop.dao.ShopLoginInfoDao`
- statements: `select:listLoginInfo`, `select:queryListBy`, `select:getMaxId`

## rrsjk-migration-member/rrsjk-data-migration-impl/src/main/resources/mybatis/mapper/shop/ShopMemberPwd.xml
- namespace: `com.rrsjk.data.shop.dao.ShopMembersPwdDao`
- statements: `select:listMemberPwd`

## rrsjk-migration-member/rrsjk-data-migration-impl/src/main/resources/mybatis/mapper/shop/ShopMemberAddressMapper.xml
- namespace: `com.rrsjk.data.shop.dao.ShopMemberAddressDao`
- statements: `select:listMemberAddress`, `select:queryListBy`, `select:getMaxId`

## rrsjk-migration-member/rrsjk-data-migration-impl/src/main/resources/mybatis/mapper/shop/ShopMembersMapper.xml
- namespace: `com.rrsjk.data.shop.dao.ShopMembersDao`
- statements: `select:listMember`, `select:queryListBy`, `select:getMaxId`, `select:getPasswordById`

## rrsjk-migration-member/rrsjk-data-migration-impl/src/main/resources/mybatis/mapper/member/MemberMapper.xml
- namespace: `com.rrsjk.data.member.dao.MemberDao`
- statements: `insert:insert`, `insert:batchInsert`, `update:update`, `select:getById`, `select:getMaxId`
- tables: `id`

## rrsjk-migration-member/rrsjk-data-migration-impl/src/main/resources/mybatis/mapper/member/LoginInfoMapper.xml
- namespace: `com.rrsjk.data.member.dao.LoginInfoDao`
- statements: `insert:insert`, `insert:batchInsert`, `update:update`, `select:getLoginInfoCount`, `select:getLastInfo`, `select:getLoginInfoByMemberId`
- tables: `id`

## rrsjk-migration-member/rrsjk-data-migration-impl/src/main/resources/mybatis/mapper/member/MemberAddressMapper.xml
- namespace: `com.rrsjk.data.member.dao.MemberAddressDao`
- statements: `insert:insert`, `insert:batchInsert`, `select:getMaxId`

## rrsjk-migration-member/rrsjk-data-migration-impl/src/main/resources/mybatis/mapper/member/MemberExtras.xml
- namespace: `com.rrsjk.data.member.dao.MemberExtrasDao`
- statements: `insert:insert`, `insert:batchInsert`, `update:update`, `select:getById`, `select:getMaxId`
- tables: `id`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/message/SmsLog.xml
- namespace: `com.rrsjk.system.message.dao.SmsLogDao`
- statements: `insert:insert`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/message/EmailLog.xml
- namespace: `com.rrsjk.system.message.dao.EmailLogDao`
- statements: `insert:insert`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/message/SmsBlacklist.xml
- namespace: `com.rrsjk.system.message.dao.SmsBlacklistDao`
- statements: `select:get`, `select:getAll`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/message/EmailTemplate.xml
- namespace: `com.rrsjk.system.message.dao.EmailTemplateDao`
- statements: `select:selectByPrimaryKey`, `select:findPageable`, `select:findPageableCount`, `delete:delete`
- tables: `email_template`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/message/SmsTemplate.xml
- namespace: `com.rrsjk.system.message.dao.SmsTemplateDao`
- statements: `select:selectByPrimaryKey`, `select:findPageable`, `select:findPageableCount`, `delete:delete`
- tables: `sms_template`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/task/Job.xml
- namespace: `com.rrsjk.system.task.dao.JobDao`
- statements: `select:selectByPrimaryKey`, `select:findPageable`, `select:findPageableCount`, `insert:insert`
- tables: `job`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/account/AccountCcb.xml
- namespace: `com.rrsjk.system.account.dao.AccountCcbDao`
- statements: `insert:insert`, `select:getByCustomerId`, `select:findByCompanyCode`, `select:findAll`, `select:findByMerchantId`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/account/AccountWechat.xml
- namespace: `com.rrsjk.system.account.dao.AccountWechatDao`
- statements: `insert:create`, `select:getByAppid`, `select:findByCompanyCode`, `select:findAll`, `select:findByMerchantId`, `select:findByCompanyCodeAndClient`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/account/AccountTransfer.xml
- namespace: `com.rrsjk.system.account.dao.AccountTransferDao`
- statements: `select:getByAccount`, `select:findByCompanyCode`, `select:findAll`, `select:findByMerchantId`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/account/AccountKjt.xml
- namespace: `com.rrsjk.system.account.dao.AccountKjtDao`
- statements: `insert:insert`, `update:update`, `select:findByCompanyCodeAndKjtType`
- tables: `id`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/account/AccountAlipay.xml
- namespace: `com.rrsjk.system.account.dao.AccountAlipayDao`
- statements: `insert:create`, `select:getByAppid`, `select:findByCompanyCode`, `select:findAll`, `select:findByMerchantId`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/account/AccountBaidu.xml
- namespace: `com.rrsjk.system.account.dao.AccountBaiduDao`
- statements: `select:getByAppid`, `select:findByCompanyCode`, `select:findAll`, `select:findByMerchantId`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/basic/BankInfoMapper.xml
- namespace: `com.rrsjk.system.basic.dao.BankInfoDao`
- statements: `select:getMainBankInfo`, `select:getSubBankInfo`, `select:getHrflcMainBankInfo`
- tables: `bank_info`, `hrflc_bank_info`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/basic/SensitiveWordMapper.xml
- namespace: `com.rrsjk.system.basic.dao.SensitiveWordDao`
- statements: `select:findAll`
- tables: `sensitive_word`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/basic/Express.xml
- namespace: `com.rrsjk.system.basic.dao.ExpressDao`
- statements: `select:findAll`, `select:findByType`, `select:getByCode`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/basic/CalendarDay.xml
- namespace: `com.rrsjk.system.basic.dao.CalendarDayDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByCalDate`, `select:findByYearMonthDay`, `select:findByYearMonth`
- tables: `id`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/basic/ApiOpenMapper.xml
- namespace: `com.rrsjk.system.basic.dao.ApiOpenDao`
- statements: `select:getApiName`, `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `api_open`, `id`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/basic/BizRole.xml
- namespace: `com.rrsjk.system.basic.dao.BizRoleDao`
- statements: `select:get`, `select:findBySubType`, `select:findByType`, `select:findBy`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/basic/ChainGroup.xml
- namespace: `com.rrsjk.system.basic.dao.ChainGroupDao`
- statements: `select:get`, `select:findByParentId`, `select:findByLevel`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/basic/Xiaowei.xml
- namespace: `com.rrsjk.system.basic.dao.XiaoweiDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getAll`
- tables: `id`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/basic/BankAreaHistoryMapper.xml
- namespace: `com.rrsjk.system.basic.dao.BankAreaHistoryDao`
- statements: `select:get`, `select:findBy`, `update:update`, `select:queryCountBy`, `insert:insert`
- tables: `id`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/basic/HrflcBankInfoMapper.xml
- namespace: `com.rrsjk.system.basic.dao.HrflcBankInfoDao`
- statements: `select:getAll`, `select:getById`, `select:getByBankNumber`, `insert:insert`, `update:update`, `delete:deleteById`
- tables: `hrflc_bank_info`, `id`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/basic/CodeMapper.xml
- namespace: `com.rrsjk.system.basic.dao.CodeDao`
- statements: `select:getAll`, `select:getCode`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/basic/AreaInfoMapper.xml
- namespace: `com.rrsjk.system.basic.dao.AreaInfoDao`
- statements: `select:getProvinceInfo`, `select:getAreaInfoByParentCode`, `select:getCityInfoByProvinceCode`, `select:getAreaInfoByCityCode`
- tables: `area_info`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/basic/GfMatchRegion.xml
- namespace: `com.rrsjk.system.basic.dao.GfMatchRegionDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/basic/SubCenterInfo.xml
- namespace: `com.rrsjk.system.basic.dao.SubCenterInfoDao`
- statements: `select:findBy`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/basic/Oauth2Client.xml
- namespace: `com.rrsjk.system.basic.dao.Oauth2ClientDao`
- statements: `select:selectByPrimaryKey`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/basic/BankNumber.xml
- namespace: `com.rrsjk.system.basic.dao.BankNumberDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByCityIdAndHeadBankName`
- tables: `id`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/basic/OcrAnalyseRecord.xml
- namespace: `com.rrsjk.system.basic.dao.OcrAnalyseRecordDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/basic/DictTypeMapper.xml
- namespace: `com.rrsjk.system.basic.dao.DictTypeDao`
- statements: `select:listAll`, `insert:create`, `select:getById`, `update:updateById`, `select:getByCode`
- tables: `dict_type`, `id`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/basic/DhMatchRegion.xml
- namespace: `com.rrsjk.system.basic.dao.DhMatchRegionDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/basic/PageHtml.xml
- namespace: `com.rrsjk.system.basic.dao.PageHtmlDao`
- statements: `select:selectByPrimaryKey`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/basic/Regiog.xml
- namespace: `com.rrsjk.system.basic.dao.RegionDao`
- statements: `select:selectByPrimaryKey`, `select:getAll`, `select:findPageable`, `select:findPageableCount`, `select:getByRegionList`, `select:getByLevel`, `select:getByParentId`, `select:findBy`, `insert:batchInsert`, `delete:batchDeleteByLevel`, `delete:batchDeleteByParentId`, `delete:fullDeleteOld`, `insert:fullCopyToOld`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/basic/BankAreaMapper.xml
- namespace: `com.rrsjk.system.basic.dao.BankAreaDao`
- statements: `select:getBankInfoByAreaAndBank`, `select:getBankAreaByName`, `select:findBy`, `insert:addBankArea`, `update:updateBankArea`, `delete:deleteBankArea`, `select:getId`, `select:checkBankNumber`, `select:countOf`
- tables: `bank_area`, `bank_info`, `id`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/basic/DictValueMapper.xml
- namespace: `com.rrsjk.system.basic.dao.DictValueDao`
- statements: `insert:create`, `update:updateById`, `select:getById`, `select:getByTypeId`, `select:listByTypeId`
- tables: `dict_value`, `id`

## rrsjk-system-service/rrsjk-system-impl/src/main/resources/mybatis/mapper/token/AccessToken.xml
- namespace: `com.rrsjk.system.token.dao.AccessTokenDao`
- statements: `insert:insert`, `select:get`, `update:markError`, `update:markSuccess`
- tables: `id`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/ImportTaskMapper.xml
- namespace: `com.nahui.energy.dao.ImportTaskMapper`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/customer/CustomerInvoiceInfoMapper.xml
- namespace: `com.nahui.energy.dao.customer.CustomerInvoiceInfoDao`
- statements: `update:updateBatch`
- tables: `customer_invoice_info`, `id`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/customer/IntendCustomerItemMapper.xml
- namespace: `com.nahui.energy.dao.customer.IntendCustomerItemMapper`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/customer/IntendCustomerMapper.xml
- namespace: `com.nahui.energy.dao.customer.IntendCustomerDao`
- statements: `select:findLatestIntendCustomerNo`, `select:queryByCustomPage`
- tables: `customer`, `intend_customer`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/customer/CustomerMapper.xml
- namespace: `com.nahui.energy.dao.customer.CustomerDao`
- statements: `update:updateBatch`, `select:findLatestCustomerNo`
- tables: `customer`, `id`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/customer/IntendCustomerAuditLogMapper.xml
- namespace: `com.nahui.energy.dao.customer.IntendCustomerAuditLogDao`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/stock/GecStockChangeRecordMapper.xml
- namespace: `com.nahui.energy.dao.stock.GecStockChangeRecordDao`
- statements: `select:selectGecStockChangeRecordPage`, `select:selectStockChangeRecordDetailDTOList`, `select:selectStockChangeRecordDetailByJoin`, `select:selectGectCacheListByOrderNo`
- tables: `gec_stock`, `gec_stock_change_record`, `sub_project`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/stock/GecStockMapper.xml
- namespace: `com.nahui.energy.dao.stock.GecStockDao`
- statements: `select:selectByIdForUpdate`, `update:updateBatch`, `select:selectGecStockDetailList`, `select:selectGecStockDetailGroupByProjectDtoList`, `select:selectGecStockDetailGroupByProjectCompanyDTOList`, `select:selectGecStockDetailGroupBySubCenterDTOList`
- tables: `gec_stock`, `id`, `sub_project`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/purchase/GecPurchaseAuditLogMapper.xml
- namespace: `com.nahui.energy.dao.purchase.GecPurchaseAuditLogMapper`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/purchase/GecPurchaseOrderItemMapper.xml
- namespace: `com.nahui.energy.dao.purchase.GecPurchaseOrderItemDao`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/purchase/GecPurchaseOrderItemReceiptVoucherMapper.xml
- namespace: `com.nahui.energy.dao.purchase.GecPurchaseOrderItemReceiptVoucherMapper`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/purchase/GecPurchaseOrderMapper.xml
- namespace: `com.nahui.energy.dao.purchase.GecPurchaseOrderDao`
- statements: `select:queryByPage`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/purchase/GecPurchaseApplySettleMapper.xml
- namespace: `com.nahui.energy.dao.purchase.GecPurchaseApplySettleDao`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/purchase/GecPurchaseContractMapper.xml
- namespace: `com.nahui.energy.dao.purchase.GecPurchaseContractDao`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/order/OrderManagementItemGecDao.xml
- namespace: `com.nahui.energy.dao.order.OrderManagementItemGecDao`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/order/OrderContractAuditLogMapper.xml
- namespace: `com.nahui.energy.dao.order.OrderContractAuditLogDao`
- statements: `update:updateBatch`
- tables: `id`, `order_contract_audit_log`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/order/OrderManagementInfoMapper.xml
- namespace: `com.nahui.energy.dao.order.OrderManagementInfoDao`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/order/OrderManagementItemMapper.xml
- namespace: `com.nahui.energy.dao.order.OrderManagementItemDao`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/order/OrderVoucherAuditLogMapper.xml
- namespace: `com.nahui.energy.dao.order.OrderVoucherAuditLogDao`
- statements: `update:updateBatch`
- tables: `id`, `order_voucher_audit_log`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/project/ProjectCompanyTradeTypeMapper.xml
- namespace: `com.nahui.energy.dao.project.ProjectCompanyTradeTypeMapper`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/project/SalesEntityCompanyDao.xml
- namespace: `com.nahui.energy.dao.project.SalesEntityCompanyDao`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/project/SubProjectMapper.xml
- namespace: `com.nahui.energy.dao.project.SubProjectMapper`
- statements: `select:queryByPage`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/project/ProjectMapper.xml
- namespace: `com.nahui.energy.dao.project.ProjectMapper`
- statements: `select:queryByPage`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/sap/SapRecordMapper.xml
- namespace: `com.nahui.energy.dao.sap.SapRecordDao`
- statements: `update:updateByRowId`, `insert:insertSapRecord`, `select:findByBidAndYwms`
- tables: `id`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/sap/SapItemRecordMapper.xml
- namespace: `com.nahui.energy.dao.sap.SapItemRecordDao`
- tables: `sap_item_record`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/progressgreen/LightStationGreenCertificateMapper.xml
- namespace: `com.nahui.energy.dao.progressgreen.LightStationGreenCertificateProgressDao`
- statements: `select:queryByPage`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/invoice/InvoiceMapper.xml
- namespace: `com.nahui.energy.dao.invoice.InvoiceDao`
- statements: `update:updateBatch`
- tables: `id`, `invoice`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/invoice/InvoiceAttachmentDao.xml
- namespace: `com.nahui.energy.dao.invoice.InvoiceAttachmentDao`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/invoice/GecInvoiceCheckMapper.xml
- namespace: `com.nahui.energy.dao.invoice.GecInvoiceCheckDao`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/invoice/InvoiceItemMapper.xml
- namespace: `com.nahui.energy.dao.invoice.InvoiceItemMapper`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/fund/PaybackManagementInfoMapper.xml
- namespace: `com.nahui.energy.dao.fund.PaybackManagementInfoDao`
- statements: `update:updateBatch`, `select:findByQuery`, `select:queryToFap`
- tables: `id`, `invoice`, `payback_management_info`

## vpp-api-gect/vpp-gect-biz/src/main/resources/mapper/fund/PaybackConfirmAuditLogMapper.xml
- namespace: `com.nahui.energy.dao.fund.PaybackConfirmAuditLogDao`
- statements: `update:updateBatch`
- tables: `id`, `payback_confirm_audit_log`

## rrsjk-admin-operation-log-service/rrsjk-admin-operation-log-impl/src/main/resources/mybatis/mapper/AdminOperationLogMapper.xml
- namespace: `com.rrsjk.adminoplog.mapper.AdminOperationLogMapper`
- statements: `insert:insertOperationLog`, `insert:insertLoginLog`, `insert:insertLogBody`, `select:selectLogBody`, `select:countLoginLogs`, `select:selectLoginLogs`, `select:countOperationLogs`, `select:selectOperationLogs`, `insert:insertAssistantSession`, `update:updateAssistantSession`, `select:selectAssistantSession`, `select:countAssistantSessions`, `select:selectAssistantSessions`, `update:softDeleteAssistantSession`, `insert:insertAssistantMessage`, `select:selectAssistantMessages`
- tables: `admin_assistant_message`, `admin_assistant_session`, `admin_log_body_detail`, `admin_login_log`, `admin_oper_log`, `id`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/shop/YzzGuide.xml
- namespace: `com.rrsjk.merchant.shop.dao.YzzGuideDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:getByMemberId`, `select:queryListBy`, `select:queryCountBy`
- tables: `id`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/shop/YzzShop.xml
- namespace: `com.rrsjk.merchant.shop.dao.YzzShopDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByShopId`, `select:queryListBy`, `select:queryCountBy`
- tables: `id`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/shop/YzzShopMember.xml
- namespace: `com.rrsjk.merchant.shop.dao.YzzShopMemberDao`
- statements: `insert:create`, `update:update`, `select:getByParams`, `select:findByGuideId`, `select:findForCbs`, `select:findCountForCbs`
- tables: `id`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/shop/ShopCbs.xml
- namespace: `com.rrsjk.merchant.shop.dao.ShopCbsDao`
- statements: `select:findCountForCbs`, `select:findForCbs`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/shop/ShopCarousel.xml
- namespace: `com.rrsjk.merchant.shop.dao.ShopCarouselDao`
- statements: `insert:insert`, `update:update`, `select:findShowList`, `select:findCount`, `select:find`
- tables: `id`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/shop/ShopCustomer.xml
- namespace: `com.rrsjk.merchant.shop.dao.ShopCustomerDao`
- statements: `insert:insert`, `update:update`, `select:findCount`, `select:find`
- tables: `id`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/shop/ShopExpress.xml
- namespace: `com.rrsjk.merchant.shop.dao.ShopExpressDao`
- statements: `insert:insert`, `select:getById`, `select:getByShopId`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/shop/ShopExtras.xml
- namespace: `com.rrsjk.merchant.shop.dao.ShopExtrasDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByShopId`
- tables: `id`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/shop/YzzShopCbs.xml
- namespace: `com.rrsjk.merchant.shop.dao.YzzShopCbsDao`
- statements: `select:findForCbs`, `select:findCountForCbs`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/shop/YzzGuideCbs.xml
- namespace: `com.rrsjk.merchant.shop.dao.YzzGuideCbsDao`
- statements: `select:findForCbs`, `select:findCountForCbs`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/shop/Shop.xml
- namespace: `com.rrsjk.merchant.shop.dao.ShopDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findBy`, `select:findCountyShopBy`, `select:findByMemberId`
- tables: `id`, `shop`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/mix/OperatorShopRelation.xml
- namespace: `com.rrsjk.merchant.mix.dao.OperatorShopRelationDao`
- statements: `insert:create`, `update:update`, `select:countOf`, `select:findBy`, `delete:delete`, `select:findByShopMemberId`, `select:findByShopId`, `select:getByShopMemberIdAndMemberId`, `select:getMaxOperatorId`
- tables: `id`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/mix/UserOperatorRelation.xml
- namespace: `com.rrsjk.merchant.mix.dao.UserOperatorRelationDao`
- statements: `insert:create`, `update:update`, `select:getByMemberId`
- tables: `id`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/supplier/ParkAppraiseTwo.xml
- namespace: `com.rrsjk.merchant.supplier.dao.ParkAppraiseTwoDao`
- statements: `insert:create`, `select:countOf`, `select:findBy`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/supplier/ParkAppraise.xml
- namespace: `com.rrsjk.merchant.supplier.dao.ParkAppraiseDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByPreOrderNo`, `select:countOf`, `select:findBy`, `select:findByOpenidAndCreatedAt`
- tables: `id`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/supplier/SupplierContract.xml
- namespace: `com.rrsjk.merchant.supplier.dao.SupplierContractDao`
- statements: `insert:create`, `select:findBySupplierId`, `select:findByContractName`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/supplier/Park.xml
- namespace: `com.rrsjk.merchant.supplier.dao.ParkDao`
- statements: `insert:create`, `select:get`, `select:findByParentId`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/supplier/Supplier.xml
- namespace: `com.rrsjk.merchant.supplier.dao.SupplierDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getBySupplierCode`, `select:getByMemberId`, `select:findBy`, `select:findCount`
- tables: `id`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/supplier/SupplierCompany.xml
- namespace: `com.rrsjk.merchant.supplier.dao.SupplierCompanyDao`
- statements: `insert:create`, `select:findByMemberId`, `select:findByMerchantId`, `select:findBySupplierId`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/supplier/ParkAppraiseUp.xml
- namespace: `com.rrsjk.merchant.supplier.dao.ParkAppraiseUpDao`
- statements: `insert:create`, `select:countOf`, `select:upFindBy`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/mch/MerchantResource.xml
- namespace: `com.rrsjk.merchant.mch.dao.MerchantResourceDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByLoginId`, `select:findByLoginIdAndResourceTypeAndEnable`
- tables: `id`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/mch/MerchantRegion.xml
- namespace: `com.rrsjk.merchant.mch.dao.MerchantRegionDao`
- statements: `insert:create`, `insert:batchInsert`, `select:findByMerchantId`, `delete:deleteAllMasterRegion`, `select:findMasterRegion`
- tables: `merchant_region`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/mch/ExpertCustomerContract.xml
- namespace: `com.rrsjk.merchant.mch.dao.ExpertCustomerContractDao`
- statements: `insert:create`, `update:update`, `select:findByExpertCustomerId`, `select:getById`
- tables: `id`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/mch/MerchantBlackListNoticeRecord.xml
- namespace: `com.rrsjk.merchant.mch.dao.MerchantBlackListNoticeRecordDao`
- statements: `insert:insert`, `select:getLastRecordByShopId`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/mch/ExpertCustomer.xml
- namespace: `com.rrsjk.merchant.mch.dao.ExpertCustomerDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findCount`, `select:find`, `select:getByParams`, `select:findExpertShopBy`, `select:getCountByExpertMemberId`
- tables: `expert_customer`, `id`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/mch/CorporateClientProcessLog.xml
- namespace: `com.rrsjk.merchant.mch.dao.CorporateClientProcessLogDao`
- statements: `insert:create`, `select:findByClientId`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/mch/DriverDeliveryRegion.xml
- namespace: `com.rrsjk.merchant.mch.dao.DriverDeliveryRegionDao`
- statements: `insert:insert`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryByDriverId`, `delete:delete`
- tables: `id`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/mch/ExpertCustomerCreditUseDetail.xml
- namespace: `com.rrsjk.merchant.mch.dao.ExpertCustomerCreditUseDetailDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`
- tables: `id`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/mch/ExpertCustomerContractImage.xml
- namespace: `com.rrsjk.merchant.mch.dao.ExpertCustomerContractImageDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:findByContractId`
- tables: `id`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/mch/PosthouseConfig.xml
- namespace: `com.rrsjk.merchant.mch.dao.PosthouseConfigDao`
- statements: `insert:insert`, `update:update`, `select:getInfo`
- tables: `id`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/mch/Merchant.xml
- namespace: `com.rrsjk.merchant.mch.dao.MerchantDao`
- statements: `insert:create`, `update:update`, `update:updateBlackListStatus`, `select:get`, `select:findByParams`, `select:findCount`, `select:find`, `select:getByMemberId`, `select:getByCompanyCode`, `select:checkRegisterInfo`
- tables: `id`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/mch/ProfessionalCustomer.xml
- namespace: `com.rrsjk.merchant.mch.dao.ProfessionalCustomerDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByMerchantId`, `select:getRCodeByMemberId`, `select:findByMemberId`, `select:getRegionCodeByRCode`
- tables: `id`, `professional_customer`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/mch/MerchantExtras.xml
- namespace: `com.rrsjk.merchant.mch.dao.MerchantExtrasDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByMerchantId`, `select:findByMerchantIds`
- tables: `id`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/mch/DriverDelivery.xml
- namespace: `com.rrsjk.merchant.mch.dao.DriverDeliveryDao`
- statements: `insert:insert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`
- tables: `id`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/mch/CorporateClient.xml
- namespace: `com.rrsjk.merchant.mch.dao.CorporateClientDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findCount`, `select:find`, `select:getByMemberId`, `select:getMemberIdById`, `select:getRegionCodeById`, `select:getByMerchantId`, `select:getById`, `update:addDeposit`, `select:getByLoginId`
- tables: `corporate_client`, `id`, `merchant`, `merchant_extras`, `merchant_region`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/mch/ExpertCustomerContacts.xml
- namespace: `com.rrsjk.merchant.mch.dao.ExpertCustomerContactsDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:get`, `select:findByExpertCustomerId`
- tables: `id`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/mch/IndustryCommerce.xml
- namespace: `com.rrsjk.merchant.mch.dao.IndustryCommerceDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`, `industry_commerce`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/mch/CorporateClientDeposit.xml
- namespace: `com.rrsjk.merchant.mch.dao.CorporateClientDepositDao`
- statements: `insert:create`, `update:update`, `select:countOf`, `select:findBy`, `select:getByDepositNo`, `select:findByClientId`, `select:getById`
- tables: `id`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/mch/PosthouseGroup.xml
- namespace: `com.rrsjk.merchant.mch.dao.PosthouseGroupDao`
- statements: `insert:insert`, `update:update`, `select:getById`, `select:queryList`, `select:queryListBy`, `select:queryCountBy`
- tables: `id`

## rrsjk-merchant-service/rrsjk-merchant-impl/src/main/resources/mybatis/mapper/mch/Posthouse.xml
- namespace: `com.rrsjk.merchant.mch.dao.PosthouseDao`
- statements: `insert:insert`, `insert:batchInsert`, `update:update`, `select:getById`, `select:getByMemberId`, `select:queryListBy`, `select:queryCountBy`, `select:findAll`, `select:findPosthouseBy`
- tables: `id`

## rrsjk-member-service/rrsjk-member-impl/src/main/resources/mybatis/mapper/MemberVatInvoiceQualification.xml
- namespace: `com.rrsjk.member.dao.MemberVatInvoiceQualificationDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByMemberId`, `select:getEnabled`, `select:findCount`, `select:find`, `select:getByMemberTaxSuccess`, `select:getByParam`
- tables: `id`

## rrsjk-member-service/rrsjk-member-impl/src/main/resources/mybatis/mapper/MemberFitnessMapper.xml
- namespace: `com.rrsjk.member.dao.MemberFitnessDao`
- statements: `select:selectByPrimaryKey`, `delete:deleteByPrimaryKey`, `insert:insert`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `update:updateByPrimaryKey`, `select:checkFitnessByMemberId`
- tables: `id`, `member_fitness`

## rrsjk-member-service/rrsjk-member-impl/src/main/resources/mybatis/mapper/LoginInfo.xml
- namespace: `com.rrsjk.member.dao.LoginInfoDao`
- statements: `insert:create`, `select:getByLoginId`, `select:getMemberLoginInfos`, `update:changePassword`
- tables: `id`

## rrsjk-member-service/rrsjk-member-impl/src/main/resources/mybatis/mapper/Member.xml
- namespace: `com.rrsjk.member.dao.MemberDao`
- statements: `insert:create`, `update:update`, `select:get`
- tables: `id`

## rrsjk-member-service/rrsjk-member-impl/src/main/resources/mybatis/mapper/LoginHistory.xml
- namespace: `com.rrsjk.member.dao.LoginHistoryDao`
- statements: `insert:create`

## rrsjk-member-service/rrsjk-member-impl/src/main/resources/mybatis/mapper/MemberSignInLog.xml
- namespace: `com.rrsjk.member.dao.MemberSignInLogDao`
- statements: `insert:create`, `select:getByParams`, `select:getMemberSignInTimes`, `select:findByParams`

## rrsjk-member-service/rrsjk-member-impl/src/main/resources/mybatis/mapper/MemberTestMealMapper.xml
- namespace: `com.rrsjk.member.dao.MemberTestMealDao`
- statements: `select:selectByPrimaryKey`, `delete:deleteByPrimaryKey`, `insert:insert`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `update:updateByPrimaryKey`, `select:checkBy`, `select:getBy`, `select:getMaxCode`, `select:find`
- tables: `id`, `member_test_meal`

## rrsjk-member-service/rrsjk-member-impl/src/main/resources/mybatis/mapper/MemberFitnessSignMapper.xml
- namespace: `com.rrsjk.member.dao.MemberFitnessSignDao`
- statements: `select:selectByPrimaryKey`, `delete:deleteByPrimaryKey`, `insert:insert`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `update:updateByPrimaryKey`, `select:sumByMemberId`, `select:checkByMemberId`
- tables: `id`, `member_fitness_sign`

## rrsjk-member-service/rrsjk-member-impl/src/main/resources/mybatis/mapper/MemberAddress.xml
- namespace: `com.rrsjk.member.dao.MemberAddressDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByMemberId`, `select:findByMemberIdDefault`, `update:restoreByMemberId`
- tables: `id`

## rrsjk-member-service/rrsjk-member-impl/src/main/resources/mybatis/mapper/LightLogOff.xml
- namespace: `com.rrsjk.member.dao.LightLogOffDao`
- statements: `select:findBy`, `select:findAll`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`, `light_log_off`

## rrsjk-member-service/rrsjk-member-impl/src/main/resources/mybatis/mapper/MemberExtras.xml
- namespace: `com.rrsjk.member.dao.MemberExtrasDao`
- statements: `insert:create`, `update:update`, `select:get`
- tables: `id`

## rrsjk-member-service/rrsjk-member-impl/src/main/resources/mybatis/mapper/MemberRole.xml
- namespace: `com.rrsjk.member.dao.MemberRoleDao`
- statements: `insert:create`, `select:getMemberRoles`, `update:cancelRole`, `update:deleteRole`, `delete:enableRole`
- tables: `id`

## rrsjk-member-service/rrsjk-member-impl/src/main/resources/mybatis/mapper/MemberEnergyMapper.xml
- namespace: `com.rrsjk.member.dao.MemberEnergyDao`
- statements: `select:selectByPrimaryKey`, `delete:deleteByPrimaryKey`, `insert:insert`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `update:updateByPrimaryKey`, `select:selectByMemberEnergy`, `select:countByMemberEnergy`, `select:sumByEnergy`, `select:sumByMember`
- tables: `id`, `member_energy`

## nh-business-forecast-service/nh-business-forecast-impl/src/main/resources/mapper/TouElectricityPriceMapper.xml
- namespace: `com.nahui.businessforecast.mapper.base.TouElectricityPriceMapper`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:disabled`, `select:getProvinceIds`
- tables: `id`, `tou_electricity_price`

## nh-business-forecast-service/nh-business-forecast-impl/src/main/resources/mapper/ElectricityPriceOfCoalMapper.xml
- namespace: `com.nahui.businessforecast.mapper.base.ElectricityPriceOfCoalMapper`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `update:disabled`, `insert:batchInsert`, `select:getById`
- tables: `electricity_price_of_coal`, `id`

## nh-business-forecast-service/nh-business-forecast-impl/src/main/resources/mapper/ElectricityPriceSummaryDiffPeriodMapper.xml
- namespace: `com.nahui.businessforecast.mapper.base.ElectricityPriceSummaryDiffPeriodMapper`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getListByProvinceId`, `update:disabledByProvinceId`, `select:findProvincesCount`, `select:findProvinces`, `select:findProvinceIds`, `select:getDetail`
- tables: `electricity_price_summary_diff_period`, `id`

## nh-business-forecast-service/nh-business-forecast-impl/src/main/resources/mapper/ProjectCostInfoDetailMapper.xml
- namespace: `com.nahui.businessforecast.mapper.ProjectCostInfoDetailMapper`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `update:updateByProjectCode`, `update:disabled`, `insert:batchInsert`, `select:getById`, `select:getByProjectCode`
- tables: `id`

## nh-business-forecast-service/nh-business-forecast-impl/src/main/resources/mapper/ForecastProjectDetailMapper.xml
- namespace: `com.nahui.businessforecast.mapper.ForecastProjectDetailMapper`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `update:updateByProjectCode`, `update:updateElectricityInfoByProjectCode`, `update:updateCostInfoByProjectCode`, `update:updateInvestmentIncomeInfoByProjectCode`, `update:updateBusinessPlanUrlByProjectCode`, `insert:batchInsert`, `select:getById`, `select:getByProjectCode`
- tables: `id`

## nh-business-forecast-service/nh-business-forecast-impl/src/main/resources/mapper/ElectricityGenerationDetailMapper.xml
- namespace: `com.nahui.businessforecast.mapper.ElectricityGenerationDetailMapper`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `update:disabled`, `update:updateByProjectCode`, `insert:batchInsert`, `select:getById`, `select:getByProjectCode`
- tables: `id`

## nh-business-forecast-service/nh-business-forecast-impl/src/main/resources/mapper/ProjectInvestmentIncomeMapper.xml
- namespace: `com.nahui.businessforecast.mapper.ProjectInvestmentIncomeMapper`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `update:updateByProjectCode`, `update:disabled`, `insert:batchInsert`, `select:getById`, `select:getByProjectCode`, `select:getByProjectCodeList`
- tables: `id`

## nh-business-forecast-service/nh-business-forecast-impl/src/main/resources/mapper/InstallDipAngleInfoRegionMapper.xml
- namespace: `com.nahui.businessforecast.mapper.base.InstallDipAngleInfoRegionMapper`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/resources/mapper/NgbGenerationPowerMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.NgbGenerationPowerMapper`

## vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/resources/mapper/MeasureEleRealtimeDataMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.MeasureEleRealtimeDataMapper`

## vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/resources/mapper/NgbGenerationEnergyMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.NgbGenerationEnergyMapper`

## vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/resources/mapper/NgbStationIncomeYearMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.NgbStationIncomeYearMapper`

## vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/resources/mapper/DeviceStatisticMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.DeviceStatisticMapper`

## vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/resources/mapper/NgbOperationChargingStationMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.NgbOperationChargingStationMapper`

## vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/resources/mapper/MeasureWeRealtimeDataMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.MeasureWeRealtimeDataMapper`

## vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/resources/mapper/StationInfoMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.StationInfoMapper`

## vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/resources/mapper/StorageRealtimeDataMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.StorageRealtimeDataMapper`

## vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/resources/mapper/NgbOperationEnergyStorageMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.NgbOperationEnergyStorageMapper`

## vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/resources/mapper/NgbStationIncomeMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.NgbStationIncomeMapper`

## vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/resources/mapper/StationAlarmMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.StationAlarmMapper`

## vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/resources/mapper/DevForecastMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.DevForecastMapper`
- statements: `select:selectDistinctAndSum`, `delete:deleteByDate`
- tables: `dev_forecast`

## vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/resources/mapper/LanMapper.xml
- namespace: `com.nahui.energy.mapper.i18n.LanMapper`
- statements: `select:queryById`, `select:queryAllByLimit`, `select:count`, `insert:insert`, `insert:insertBatch`, `update:update`, `delete:deleteById`
- tables: `id`, `lan`

## vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/resources/mapper/NgbStationSocialContributionMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.NgbStationSocialContributionMapper`

## vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/resources/mapper/NgbStationIncomeDayMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.NgbStationIncomeDayMapper`

## vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/resources/mapper/I18nMessageMapper.xml
- namespace: `com.nahui.energy.mapper.i18n.I18nMessageMapper`
- statements: `select:queryById`, `select:queryAllByLimit`, `select:count`, `select:listAll`, `insert:insertBatch`, `select:selectAllLangAppMouduleGroups`, `insert:batchInsertOrUpdate`
- tables: `i18n_message`, `lan_id`

## vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/resources/mapper/NgbStationUserMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.NgbStationUserMapper`
- statements: `select:selectCustomPage`
- tables: `ngb_station_user`

## vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/resources/mapper/NgbStationRobotMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.NgbStationRobotMapper`

## vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/resources/mapper/GenRealtimeDataMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.GenRealtimeDataMapper`

## vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/resources/mapper/ChargeGunRealtimeDataMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.ChargeGunRealtimeDataMapper`

## vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/resources/mapper/NgbStationIncomeMonthMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.NgbStationIncomeMonthMapper`

## vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/resources/mapper/LoadRealtimeDataMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.LoadRealtimeDataMapper`

## vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/resources/mapper/DeviceInfoMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.DeviceInfoMapper`
- statements: `select:sumRatedPowerByStationIdAndDeviceTypes`, `select:devTypeByStationIdAndDeviceTypes`
- tables: `device_info`

## vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/resources/mapper/NgbOperationPhotovoltaicMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.NgbOperationPhotovoltaicMapper`

## vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/resources/mapper/NgbGenerationLoadMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.NgbGenerationLoadMapper`

## vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/resources/mapper/NgbStationBaseMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.NgbStationBaseMapper`

## vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/resources/mapper/StationStatisticMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.StationStatisticMapper`

## vpp-api-gpower/vpp-gpower-biz/src/main/resources/mapper/GreenElectricityAuditLogMapper.xml
- namespace: `com.nahui.energy.dao.GreenElectricityAuditLogMapper`

## vpp-api-gpower/vpp-gpower-biz/src/main/resources/mapper/PowerGridCompanyMapper.xml
- namespace: `com.nahui.energy.dao.PowerGridCompanyMapper`

## vpp-api-gpower/vpp-gpower-biz/src/main/resources/mapper/ElectricityPriceDataReportMapper.xml
- namespace: `com.nahui.energy.mapper.ads.ElectricityPriceDataReportMapper`
- statements: `select:queryNodeHourlyAvgPage`, `select:querySpotHourlyAvgPage`, `select:queryLatestNodeInfoDate`, `select:queryLatestSpotInfoDate`, `select:queryDataRegionNames`, `select:queryPriceTypes`, `select:querySpotDataRegionNames`, `select:querySpotPriceTypes`, `select:countAvailableNodeCities`, `select:queryCities`, `select:queryNodeNames`
- tables: `ads.electricity_price_data_node_hourly_avg`, `ads.electricity_price_data_spot_hourly_avg`

## vpp-api-gpower/vpp-gpower-biz/src/main/resources/mapper/PowerGridContractMapper.xml
- namespace: `com.nahui.energy.dao.PowerGridContractMapper`

## vpp-api-gpower/vpp-gpower-biz/src/main/resources/mapper/GreenElectricityRevenueMapper.xml
- namespace: `com.nahui.energy.dao.GreenElectricityRevenueMapper`

## vpp-api-gpower/vpp-gpower-biz/src/main/resources/mapper/sap/SapRecordMapper.xml
- namespace: `com.nahui.energy.dao.sap.SapRecordDao`
- statements: `update:updateByRowId`, `insert:insertSapRecord`, `select:findByBidAndYwms`
- tables: `id`

## vpp-api-gpower/vpp-gpower-biz/src/main/resources/mapper/sap/SapItemRecordMapper.xml
- namespace: `com.nahui.energy.dao.sap.SapItemRecordDao`
- statements: `insert:batchInsertItems`

## vpp-template/vpp-template-biz/src/main/resources/mapper/InvoiceMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.InvoiceMapper`

## job-service/job-impl/src/main/resources/job-sql-mapper/SysJobLogMapper.xml
- namespace: `com.haier.cbs.job.dao.SysJobLogDao`
- statements: `select:get`, `insert:insert`, `update:update`
- tables: `id`, `sys_job_log`

## job-service/job-impl/src/main/resources/job-sql-mapper/SysJobMonitor.xml
- namespace: `com.haier.cbs.job.dao.SysJobMonitorDao`
- statements: `insert:insert`
- tables: `sys_job_monitor`

## job-service/job-impl/src/main/resources/job-sql-mapper/SysJobMapper.xml
- namespace: `com.haier.cbs.job.dao.SysJobDao`
- statements: `select:find`, `select:findByJobId`, `insert:insert`, `update:updateStatus`, `update:logicDeleteByJobName`
- tables: `id`, `sys_job`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/cart/Cart.xml
- namespace: `com.rrsjk.trade.cart.dao.CartDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByParams`, `delete:clearCartById`, `select:findBy`, `select:findCountBy`, `select:findByOrderCart`, `delete:clearByParams`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/coupon/Coupon.xml
- namespace: `com.rrsjk.trade.coupon.dao.CouponDao`
- statements: `insert:insert`, `update:update`, `select:get`, `update:increaseClaimCount`, `select:countOf`, `select:findBy`, `select:findByPage`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/coupon/CouponUse.xml
- namespace: `com.rrsjk.trade.coupon.dao.CouponUseDao`
- statements: `insert:insert`, `select:get`, `select:getNumber`, `select:countOf`, `select:findBy`, `select:getByMemberIdAndCouponId`, `update:updateExpire`, `update:updateUsed`, `update:updateStatus`
- tables: `coupon`, `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/coupon/CouponItem.xml
- namespace: `com.rrsjk.trade.coupon.dao.CouponItemDao`
- statements: `insert:insert`, `insert:batchInsert`, `select:get`, `select:findBy`, `select:getByCouponId`, `delete:delete`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/energy/EnergyStorageProject.xml
- namespace: `com.rrsjk.trade.energy.dao.EnergyStorageProjectDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/OrderItemPrepay.xml
- namespace: `com.rrsjk.trade.order.dao.OrderItemPrepayDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByOrderItemId`, `select:findBySuccess`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/OrderItemShop.xml
- namespace: `com.rrsjk.trade.order.dao.OrderItemShopDao`
- statements: `select:countOf`, `select:findBy`, `select:findByGroupWaitPick`, `select:findByGroupWaitSms`, `select:countOrderItemGroup`, `select:findOrderSum`, `select:paidOrderSumCount`
- tables: `order_item`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/OrderTrade.xml
- namespace: `com.rrsjk.trade.order.dao.OrderTradeDao`
- statements: `select:countOf`, `select:findBy`
- tables: `order_item`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/StockReport.xml
- namespace: `com.rrsjk.trade.order.dao.StockReportDao`
- statements: `select:findList`
- tables: `stock_report`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/OrderBuyer.xml
- namespace: `com.rrsjk.trade.order.dao.OrderBuyerDao`
- statements: `select:countOf`, `select:findBy`
- tables: `orders`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/OrderItemEnomatic.xml
- namespace: `com.rrsjk.trade.order.dao.OrderItemEnomaticDao`
- statements: `select:findQuantity`, `select:findBy`, `select:findByOrderNo`
- tables: `orders`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/HroisToken.xml
- namespace: `com.rrsjk.trade.order.dao.HroisTokenDao`
- statements: `insert:create`, `update:update`, `select:get`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/DsPredictionOrder.xml
- namespace: `com.rrsjk.trade.order.dao.DsPredictionOrderDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `select:getById`, `select:findByMap`, `select:merFindBy`, `select:merCountOf`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/LightMaterialManageSerialMapper.xml
- namespace: `com.rrsjk.trade.order.mapper.LightZeroMaterialManageSerialMapper`
- statements: `select:selectByPrimaryKey`, `insert:insert`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `update:updateByPrimaryKey`
- tables: `id`, `rrsjk_light.light_zero_material_manage_serial`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/LightMaterialPurchaseOrderMapper.xml
- namespace: `com.rrsjk.trade.order.mapper.LightZeroMaterialPurchaseOrderMapper`
- statements: `select:selectByPrimaryKey`, `insert:insert`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `update:updateByPrimaryKey`
- tables: `id`, `rrsjk_light.light_zero_material_purchase_order`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/LightOrderToEnergyStorageQueue.xml
- namespace: `com.rrsjk.trade.order.dao.LightOrderToEnergyStorageQueueDao`
- statements: `insert:create`, `update:update`, `select:findNoToPcs`, `select:findCount`, `select:findList`, `select:findByOrderItemNo`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/OrderRepairLog.xml
- namespace: `com.rrsjk.trade.order.dao.OrderRepairLogDao`
- statements: `insert:create`, `update:update`, `select:get`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/OrderItemGroup.xml
- namespace: `com.rrsjk.trade.order.dao.OrderItemGroupDao`
- statements: `select:findBySkuSubtotal`, `select:findByLineSubtotal`, `select:findByDeliverSubtotal`, `select:findByPickSubtotal`, `select:findIdByPickUpCode`
- tables: `order_item`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/InternalPurchaseOrder.xml
- namespace: `com.rrsjk.trade.order.dao.InternalPurchaseOrderDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByOrderItemId`, `select:findBySettlementNum`, `select:countOf`, `select:findBy`
- tables: `id`, `internal_purchase_order`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/HroisPurchaseOrder.xml
- namespace: `com.rrsjk.trade.order.dao.HroisPurchaseOrderDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:findByOrderId`, `select:findByOrderNo`, `select:getByPurchaseOrderNo`, `select:findByWaitPoCreate`, `select:findByWaitPoSign`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/HroisOrderBox.xml
- namespace: `com.rrsjk.trade.order.dao.HroisOrderBoxDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:findByOrderItemId`, `select:findByOrderId`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/InnerOrder.xml
- namespace: `com.rrsjk.trade.order.dao.InnerOrderDao`
- statements: `insert:batchCreate`, `insert:create`, `select:countOf`, `select:findBy`, `update:update`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/HroisOrderItem.xml
- namespace: `com.rrsjk.trade.order.dao.HroisOrderItemDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:getByOrderItemNo`, `select:findByOrderId`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/OrderExtras.xml
- namespace: `com.rrsjk.trade.order.dao.OrderExtrasDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByOrderId`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/HroisOrder.xml
- namespace: `com.rrsjk.trade.order.dao.HroisOrderDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:getByOrderNo`, `select:getByHroisOrderNo`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/HroisLog.xml
- namespace: `com.rrsjk.trade.order.dao.HroisLogDao`
- statements: `insert:create`, `update:update`, `select:get`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/InternalPurchase.xml
- namespace: `com.rrsjk.trade.order.dao.InternalPurchaseDao`
- statements: `insert:create`, `update:update`, `select:countOf`, `select:findBy`, `select:get`, `select:getBySettlementNum`, `select:getInternalCompanyCodeByOrderId`, `update:updateBySettlementNum`
- tables: `id`, `internal_purchase_order`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/DsStockOrder.xml
- namespace: `com.rrsjk.trade.order.dao.DsStockOrderDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `select:getById`, `select:findByMap`, `select:merchantFindBy`, `select:merchantCountOf`, `select:getByDsStockOrder`, `select:countSupplierOrder`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/Orders.xml
- namespace: `com.rrsjk.trade.order.dao.OrdersDao`
- statements: `insert:create`, `update:update`, `update:updateOrdersByOrderNo`, `select:get`, `select:getByOrderNo`, `select:findByIdList`, `select:findByOrderNoList`, `select:findShopIdByDeliverTimeOut`, `select:getByPlatformAndTid`, `select:getLastGroupOrder`, `select:getPickUpCodeByMaxOrderId`, `select:getByPickUpCode`, `select:findByZeroWaitPay`, `select:findByCustomerName`, `select:findByMerOrderId`
- tables: `id`, `orders`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/OrderRetryQueue.xml
- namespace: `com.rrsjk.trade.order.dao.OrderRetryQueueDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findBySuccess`, `select:findByOrderItemIdType`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/EnsOrderDeliveryToLightQueue.xml
- namespace: `com.rrsjk.trade.order.dao.EnsOrderDeliveryToLightQueueDao`
- statements: `insert:create`, `update:update`, `select:findWaitDelivery`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/CbsHroisOrderBox.xml
- namespace: `com.rrsjk.trade.order.dao.CbsHroisOrderBoxDao`
- statements: `select:countOf`, `select:findBy`
- tables: `hrois_order_box`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/EnsOrderConfirmToLightQueue.xml
- namespace: `com.rrsjk.trade.order.dao.EnsOrderConfirmToLightQueueDao`
- statements: `insert:create`, `update:update`, `select:findWaitDelivery`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/OrderItem.xml
- namespace: `com.rrsjk.trade.order.dao.OrderItemDao`
- statements: `insert:create`, `update:update`, `update:updateByOrderItemNo`, `update:updateOrderItemRefundStatus`, `select:get`, `select:findByOrderId`, `select:getByOrderItemNo`, `select:findByThirdTradeNo`, `select:findByPayId`, `select:countOf`, `select:findBy`, `select:findByThirdTradeNoAndRefundStatus`, `select:findRefundOrderItem`, `select:findPaymentOrderItem`, `select:findByFinished`, `select:findByClosed`, `select:findOrderInfo`, `select:findByOrderItemNoList`, `select:findByOrderIdAndItemId`, `select:getByPlatformAndOid`, `select:getByPlatformAndTid`, `select:findByPlatformAndOuterid`, `select:findByOuterid`, `select:findByMemberSkuFlowStatus`, `select:findByCustomerCode`, `select:findIdByMemberItem`, `select:findIdByMemberSku`, `select:sumQuantityMemberSku`, `select:findMealOrderByWaitSms`, `select:getOrderNumberByCreatedAt`, `select:getOrderNumberByConfirmedAt`, `select:getPayAmountByPaidAt`, `select:getListByPaidOrRefundAt`, `select:sumPayAmount`, `select:findOrderItemsByRefundStatus`, `select:findOrderItemForSyncFap`
- tables: `id`, `order_item`, `orders`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/OrderInvoice.xml
- namespace: `com.rrsjk.trade.order.dao.OrderInvoiceDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByOrderId`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/BudgetFeedback.xml
- namespace: `com.rrsjk.trade.order.dao.BudgetFeedbackDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByBudgetCode`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/OrderItemFinance.xml
- namespace: `com.rrsjk.trade.order.dao.OrderItemFinanceDao`
- statements: `select:countOf`, `select:findBy`, `select:sumIncomeAmount`
- tables: `order_item`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/OrderAttribute.xml
- namespace: `com.rrsjk.trade.order.dao.OrderAttributeDao`
- statements: `select:get`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/LightPurchaseSalesPurchaseStoreOrderRelation.xml
- namespace: `com.rrsjk.trade.order.dao.LightPurchaseSalesPurchaseStoreOrderRelationDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByPurchaseOrderNo`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/OrderRepair.xml
- namespace: `com.rrsjk.trade.order.dao.OrderRepairDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByOrderItemId`, `select:getByRefundBatchId`, `select:getByOrderRepairNo`, `select:getByPlatformAndRefundNo`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/OrderLimitedMember.xml
- namespace: `com.rrsjk.trade.order.dao.OrderLimitedMemberDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findEnableByMemberId`, `select:findEnableByMemberSku`, `select:countOf`, `select:findBy`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/EnterpriseOrderIncomeAndInvoice.xml
- namespace: `com.rrsjk.trade.order.dao.EnterpriseOrderIncomeAndInvoiceDao`
- statements: `insert:create`, `update:update`, `select:findList`, `select:findOneByItemId`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/BarCodeApply.xml
- namespace: `com.rrsjk.trade.order.dao.BarCodeApplyDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:getByApplyNo`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/Budget.xml
- namespace: `com.rrsjk.trade.order.dao.BudgetDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByBudgetCode`, `select:countOf`, `select:findBy`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/DsInventoryManage.xml
- namespace: `com.rrsjk.trade.order.dao.DsInventoryManageDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `select:getById`, `select:findByMap`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/OrderErrorLog.xml
- namespace: `com.rrsjk.trade.order.dao.OrderErrorLogDao`
- statements: `insert:create`, `update:update`, `select:get`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/MerchantEvaluate.xml
- namespace: `com.rrsjk.trade.order.dao.MerchantEvaluateDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:findByParam`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/HroisOperationLog.xml
- namespace: `com.rrsjk.trade.order.dao.HroisOperationLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getByParam`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/HroisOrderCbs.xml
- namespace: `com.rrsjk.trade.order.dao.HroisOrderCbsDao`
- statements: `select:countOf`, `select:findBy`, `select:countSupplierOrder`
- tables: `hrois_order_item`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/OrderItemCbs.xml
- namespace: `com.rrsjk.trade.order.dao.OrderItemCbsDao`
- statements: `select:countOf`, `select:findBy`, `select:cnCountOf`, `select:cnFindBy`, `select:findByWaitReverseCost`
- tables: `order_item`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/HroisSendInfoUpdate.xml
- namespace: `com.rrsjk.trade.order.dao.HroisSendInfoUpdateDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getNeedCheckDeliverStatus`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/HroisQueue.xml
- namespace: `com.rrsjk.trade.order.dao.HroisQueueDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findBySuccess`, `select:getByOrderIdAndAction`, `update:rePushDeliverByHroisOrderNo`, `select:getByHroisOrderNoAndAction`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/OrderOperateLog.xml
- namespace: `com.rrsjk.trade.order.dao.OrderOperateLogDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByOrderItemId`, `select:findByOrderId`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/OrderCountyOperator.xml
- namespace: `com.rrsjk.trade.order.dao.OrderCountyOperatorDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findInfo`
- tables: `id`, `orders`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/DsWarehouse.xml
- namespace: `com.rrsjk.trade.order.dao.DsWarehouseDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `select:getById`, `select:findByMap`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/OrderItemCost.xml
- namespace: `com.rrsjk.trade.order.dao.OrderItemCostDao`
- statements: `insert:create`, `insert:batchCreate`, `select:getByOrderItemNo`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/LightPurchaseSalesItemOrder.xml
- namespace: `com.rrsjk.trade.order.dao.LightPurchaseSalesItemOrderDao`
- statements: `insert:create`, `update:update`, `update:updateByItemOrderNo`, `select:findDetail`, `select:findById`, `select:findByItemOrderNo`, `update:updateByOrderId`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/OrderAttributeValue.xml
- namespace: `com.rrsjk.trade.order.dao.OrderAttributeValueDao`
- statements: `insert:create`, `update:update`, `select:get`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/LightPurchaseSalesOrder.xml
- namespace: `com.rrsjk.trade.order.dao.LightPurchaseSalesOrderDao`
- statements: `insert:create`, `update:update`, `select:queryCountBy`, `select:findPage`, `select:findById`, `select:findByOrderNo`, `select:findByInvoiceStatus`, `select:findByMerOrderId`, `select:findByRefundOrderId`, `select:findNoToSap`, `select:countSubCenterIncome`, `select:querySubCenterIncome`, `select:countSpIncome`, `select:querySpIncome`, `select:findListForPolicyCash`, `select:findListForPolicyCashPlus`, `select:findSumPaidAmountList`, `select:findUnpaidOrdersBefore`, `select:findTestEnvDataForFap`
- tables: `id`, `light_purchase_sales_item_order`, `light_purchase_sales_order`, `rrsjk_light.zero_carbon_service_provider`, `rrsjk_light.zero_carbon_sub_new`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/AddressOperationLogMapper.xml
- namespace: `com.rrsjk.trade.order.mapper.AddressOperationLogMapper`
- statements: `select:selectByPrimaryKey`, `delete:deleteByPrimaryKey`, `insert:insert`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `update:updateByPrimaryKey`, `select:countOf`, `select:findBy`
- tables: `address_operation_log`, `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/BarCodeDetail.xml
- namespace: `com.rrsjk.trade.order.dao.BarCodeDetailDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:getByBarCode`, `select:findByApplyId`, `select:findByApplyNo`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/PcsOrderDeliveryToLightQueue.xml
- namespace: `com.rrsjk.trade.order.dao.PcsOrderDeliveryToLightQueueDao`
- statements: `insert:create`, `update:update`, `select:findWaitDelivery`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/OrderItemFee.xml
- namespace: `com.rrsjk.trade.order.dao.OrderItemFeeDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByOrderItemId`, `select:findByOrderItemNo`, `select:findByOrderItemNoAndType`, `select:findByOrderItemIdTypeFeeType`, `select:sumCommission`
- tables: `id`, `order_item_fee`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/OrderSapQueue.xml
- namespace: `com.rrsjk.trade.order.dao.OrderSapQueueDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findBySuccess`, `select:getByOrderItemIdAction`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/Photovoltaic.xml
- namespace: `com.rrsjk.trade.order.dao.PhotovoltaicDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByMemberId`, `select:countOf`, `select:findBy`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/OrderItemBuyer.xml
- namespace: `com.rrsjk.trade.order.dao.OrderItemBuyerDao`
- statements: `select:countOf`, `select:countOfOrder`, `select:findBy`, `select:findByNotPage`, `select:findByOrder`
- tables: `order_item`, `orders`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/LightOrderToPcsQueue.xml
- namespace: `com.rrsjk.trade.order.dao.LightOrderToPcsQueueDao`
- statements: `insert:create`, `update:update`, `select:findNoToPcs`, `select:findCount`, `select:findList`, `select:findByOrderItemNo`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/LightPurchaseSalesPurchaseOrder.xml
- namespace: `com.rrsjk.trade.order.dao.LightPurchaseSalesPurchaseOrderDao`
- statements: `insert:create`, `update:update`, `select:queryCountBy`, `select:findPage`, `select:findByPurchaseOrderNo`, `select:findByOrderId`, `select:findByItemOrderId`, `select:newFindPage`, `update:updateByOrderId`, `select:findByMasterOrderNo`, `select:findByItemOrderIdOp`, `select:queryCountByCBS`, `select:findPageByCBS`, `select:findWaitConfigList`
- tables: `id`, `light_purchase_sales_order`, `light_purchase_sales_purchase_order`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/LightMaterialManageMapper.xml
- namespace: `com.rrsjk.trade.order.mapper.LightZeroMaterialManageMapper`
- statements: `select:selectByPrimaryKey`, `insert:insert`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `update:updateByPrimaryKey`, `select:selectBySkuCodeAndSpId`, `update:updateBySkuCodeAndSpId`
- tables: `id`, `rrsjk_light.light_zero_material_manage`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/ExpertOrder.xml
- namespace: `com.rrsjk.trade.order.dao.ExpertOrderDao`
- statements: `insert:batchCreate`, `insert:create`, `select:countOf`, `select:findBy`, `update:update`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/order/OrderItemJointVenture.xml
- namespace: `com.rrsjk.trade.order.dao.OrderItemJointVentureDao`
- statements: `select:countOf`, `select:findBy`
- tables: `order_item`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/activity/LuckyWheelPrize.xml
- namespace: `com.rrsjk.trade.activity.dao.LuckyWheelPrizeDao`
- statements: `insert:insert`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `update:increaseLottoryCount`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/activity/LottoryRecord.xml
- namespace: `com.rrsjk.trade.activity.dao.LottoryRecordDao`
- statements: `insert:insert`, `update:update`, `select:get`, `select:getByParam`, `update:increaseLimitCount`, `update:increaseLottoryCount`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/activity/ClaimPrizeRecord.xml
- namespace: `com.rrsjk.trade.activity.dao.ClaimPrizeRecordDao`
- statements: `insert:insert`, `update:update`, `select:get`, `select:findByMemberId`, `select:findByActivityId`, `select:findByParams`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/activity/Activity.xml
- namespace: `com.rrsjk.trade.activity.dao.ActivityDao`
- statements: `insert:insert`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:selectBy`, `insert:insertByUrl`, `update:updateByUrl`, `update:updateStatus`
- tables: `activity`, `activity_pic`, `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/hhmedic/HhOrder.xml
- namespace: `com.rrsjk.trade.hhmedic.dao.HhOrderDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByMemberId`, `select:getByMemberId`, `select:getByMemberIds`, `update:updateExpire`, `update:updateUserInfo`, `select:getUserInfoByMobile`, `select:findByParams`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/hhmedic/HhFamily.xml
- namespace: `com.rrsjk.trade.hhmedic.dao.HhFamilyDao`
- statements: `insert:insert`, `update:update`, `select:getById`, `select:getByOwnerMemberId`, `select:getByFamilyMemberId`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/hhmedic/HhCard.xml
- namespace: `com.rrsjk.trade.hhmedic.dao.HhCardDao`
- statements: `insert:insert`, `update:update`, `select:get`, `select:getByInvitationCode`, `select:getForActive`, `select:findByMemberId`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/pay/NetPayLog.xml
- namespace: `com.rrsjk.trade.pay.dao.NetPayLogDao`
- statements: `insert:create`, `update:update`, `select:findOne`
- tables: `id`, `net_pay_log`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/ranks/CardStock.xml
- namespace: `com.rrsjk.trade.ranks.dao.CardStockDao`
- statements: `insert:insert`, `insert:batchInsert`, `update:update`, `update:updateSold`, `update:batchUpdateSold`, `select:getById`, `select:getByCode`, `select:getByCodeList`, `select:getByOrderSubNo`, `select:queryListBy`, `select:queryCountBy`, `select:getByBatch`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/ranks/BenefitConsumerExtra.xml
- namespace: `com.rrsjk.trade.ranks.dao.BenefitConsumerExtraDao`
- statements: `insert:insert`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/ranks/CardBatchRecord.xml
- namespace: `com.rrsjk.trade.ranks.dao.CardBatchRecordDao`
- statements: `insert:insert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:getByBatch`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/ranks/Benefit.xml
- namespace: `com.rrsjk.trade.ranks.dao.BenefitDao`
- statements: `insert:insert`, `update:update`, `select:getById`, `select:getByCode`, `select:queryListBy`, `select:queryOutBenefitList`, `select:queryCountBy`, `select:queryBenefitListByParams`, `select:getCountBySku`, `select:queryAllBenefitList`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/ranks/MemberRank.xml
- namespace: `com.rrsjk.trade.ranks.dao.MemberRankDao`
- statements: `insert:insert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:getByMemberId`, `update:updateExpired`, `select:findShouldExpiredMembers`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/ranks/MemberBenefit.xml
- namespace: `com.rrsjk.trade.ranks.dao.MemberBenefitDao`
- statements: `insert:insert`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:getSumUsefullyBenefit`, `update:activeCardBenefit`, `select:getByCardCode`, `select:getByCardAndCode`, `update:updateForConsumer`, `select:getUsefullyByCodeAndMember`, `update:expired`, `select:getListByMemberId`, `update:changeCardCode`, `update:updateOrderNo`, `select:getSumCount`, `select:getCardListDtoInfoByCardCodes`, `select:getCardBenefitByMember`, `select:getByOrderItemNo`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/ranks/MemberRankRecord.xml
- namespace: `com.rrsjk.trade.ranks.dao.MemberRankRecordDao`
- statements: `insert:insert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findUsefullRecord`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/ranks/BenefitOrderReportInfo.xml
- namespace: `com.rrsjk.trade.ranks.dao.BenefitOrderReportInfoDao`
- statements: `select:queryCountBy`, `select:queryListBy`
- tables: `benefit_consumer`, `member_benefit`, `order_invoice`, `order_item`, `orders`, `rank_card`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/ranks/BenefitPackageDetail.xml
- namespace: `com.rrsjk.trade.ranks.dao.BenefitPackageDetailDao`
- statements: `insert:insert`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:getByPackageCode`, `select:getBenefitCountInUse`, `update:batchDelete`, `delete:delByPackageCode`
- tables: `benefit`, `benefit_package_detail`, `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/ranks/CardOrder.xml
- namespace: `com.rrsjk.trade.ranks.dao.CardOrderDao`
- statements: `insert:insert`, `update:update`, `select:getById`, `select:getByLnOrderNo`, `select:getByCardCode`, `select:getByOrderSubNo`, `select:queryListBy`, `select:queryCountBy`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/ranks/BenefitConsumer.xml
- namespace: `com.rrsjk.trade.ranks.dao.BenefitConsumerDao`
- statements: `insert:insert`, `insert:batchInsert`, `update:update`, `select:getById`, `select:getByOrderSubNo`, `select:getByOutId`, `select:queryListBy`, `select:findList`, `select:queryCountBy`, `select:getUseSuccessCount`, `select:getListByMemberId`, `select:selectAllOrderSubNo`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/ranks/BenefitPackage.xml
- namespace: `com.rrsjk.trade.ranks.dao.BenefitPackageDao`
- statements: `insert:insert`, `update:update`, `select:getById`, `select:getByCode`, `select:queryListBy`, `select:querySelled`, `select:queryCountBy`, `select:queryAllList`, `select:getCountBySkuId`, `select:getBySkuId`, `select:getBySku`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/ranks/RankCard.xml
- namespace: `com.rrsjk.trade.ranks.dao.RankCardDao`
- statements: `insert:insert`, `insert:batchInsert`, `update:update`, `update:active`, `select:getByCode`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:selectCountByMemberId`, `select:selectListByMemberId`, `select:findShouldExpiredCards`, `update:expired`, `select:findWillExpiredCards`, `select:findByOrderNo`, `update:changeCardCode`, `update:updateSecretFail`, `select:getMemberCards`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/invoice/InvoiceFinance.xml
- namespace: `com.rrsjk.trade.invoice.dao.InvoiceFinanceDao`
- statements: `select:countOf`, `select:findBy`, `select:sumInvoiceAmount`
- tables: `invoice`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/invoice/InvoiceQueue.xml
- namespace: `com.rrsjk.trade.invoice.dao.InvoiceQueueDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByOrderItemId`, `select:findBySuccess`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/invoice/Invoice.xml
- namespace: `com.rrsjk.trade.invoice.dao.InvoiceDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByOrderItemId`, `select:findByRelationNo`, `select:findByRelationNos`, `select:findByRelationNoForLightEle`, `select:findByRelationNoAll`, `select:findByElecWait`, `select:findByVatWait`, `select:findByVatWaitResult`, `select:countOf`, `select:findBy`, `select:findByInvalidRedWait`, `select:findByInvalidRedWaitResult`, `select:findByElecWaitResult`, `select:findByArchiveStatusWait`, `select:findByVatWaitResultOperation`, `select:findByVatWaitOperation`, `select:findByArchiveStatusWaitByOperation`, `select:findByVatWaitResultLightElec`, `select:findByVatWaitLightElec`, `select:findByArchiveStatusWaitByLightElec`, `select:findByVatWaitByMerge`, `select:findByElecWaitByMerge`, `select:findByVatWaitResultByMerge`, `select:findByElecWaitResultByMerge`, `select:findByArchiveStatusWaitByMerge`, `select:findByInvoiceNumber`, `select:summaryInfoByInvoiceNumber`, `update:batchUpdateInvoiceStatus`, `select:findNeedReverseInvoiceByLightElec`, `select:findNeedQueryReverseInvoiceResultByElec`, `select:findByElecWaitOperation`, `select:findByElecWaitResultOperation`
- tables: `id`

## rrsjk-trade-service/rrsjk-trade-impl/src/main/resources/mybatis/mapper/express/ExpressRecord.xml
- namespace: `com.rrsjk.trade.express.dao.ExpressRecordDao`
- statements: `insert:insert`, `select:getByExpressSn`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightUnionpayMch.xml
- namespace: `com.rrsjk.light.dao.LightUnionpayMchDao`
- statements: `select:getByCompanyCode`, `select:getByMchId`, `select:findBy`, `select:countOf`, `select:getById`, `insert:create`, `update:update`, `delete:deleteById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStopStation.xml
- namespace: `com.rrsjk.light.dao.LightStopStationDao`
- statements: `select:countStopStationOf`, `select:findStopStationBy`
- tables: `light_station`, `light_station_audit`, `light_sub_sp`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightAuxiliaryMaterialDepositAdd.xml
- namespace: `com.rrsjk.light.dao.LightAuxiliaryMaterialDepositAddDao`
- statements: `select:findBy`, `select:countOf`, `select:getById`, `insert:create`, `update:update`, `update:resetForResubmit`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/StationUserOcrRecord.xml
- namespace: `com.rrsjk.light.dao.StationUserOcrRecordDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByIdCard`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStockTakingDetail.xml
- namespace: `com.rrsjk.light.dao.LightStockTakingDetailDao`
- statements: `insert:create`, `update:update`, `insert:batchInsert`, `select:get`, `select:getByTakingId`, `delete:deleteByTakingIdAndSkuCode`
- tables: `id`, `light_stock_taking_detail`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/HuaRongIncomeQualityGuarantee.xml
- namespace: `com.rrsjk.light.dao.HuaRongIncomeQualityGuaranteeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `insert:batchInsert`, `update:update`, `update:updateByBatchNo`, `delete:deleteByBatchNo`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationBank.xml
- namespace: `com.rrsjk.light.dao.LightStationBankDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:getByStationId`, `select:getByStationCode`, `select:getByStationCodes`, `update:deleteByStationCode`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:findStationBank`
- tables: `id`, `light_station`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmConstructionProgressAudit.xml
- namespace: `com.rrsjk.light.dao.CmConstructionProgressAuditDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByForNGB`, `select:countOfForNGB`
- tables: `cm_construction_plan`, `cm_construction_progress_audit`, `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightOverdueBlackList.xml
- namespace: `com.rrsjk.light.dao.LightOverdueBlackListDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/StationFileExchange.xml
- namespace: `com.rrsjk.light.dao.StationFileExchangeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByStationCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightPurchaseOrder.xml
- namespace: `com.rrsjk.light.dao.LightPurchaseOrderDao`
- statements: `insert:create`, `update:updateByAuxiliaryPurchaseOrderNo`, `update:updateFlagByPurchaseOrderNo`, `update:update`, `update:updateSignImageById`, `select:get`, `select:getWithLock`, `select:getByPurchaseOrderNo`, `select:getByAuxiliaryPurchaseOrderNo`, `select:findByMemberId`, `select:findByBatchNo`, `select:findByBatchNoList`, `select:countOf`, `select:countOfAuxiliary`, `select:countOfVerfyDeliverTimeByProviderId`, `select:findBy`, `select:findReceiveStoreOptions`, `select:findTeamOptions`, `select:findAuxiliaryPage`, `select:findByIds`, `select:sumNumberBySpSku`, `select:sumPlanNumberBySpSku`, `select:getByAuxiliaryPurchaseOrderNoAndSupplierCode`, `select:getByAuxiliaryPurchaseOrderNoAndNotFromSupplierCode`, `select:findMajorPurchaseOrderByFlagIsNO`, `select:findAuxiliaryPurchaseOrderByFlagIsNO`, `update:batchUpdateFlag`, `select:findList`, `select:findStockNumBerMonth`, `select:findStockNumWeek`, `select:findAllByMemberId`, `update:batchUpdateDelivery`
- tables: `id`, `light_purchase_order`, `light_sp_store`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightElectricOrder.xml
- namespace: `com.rrsjk.light.dao.LightElectricOrderDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByGfApplyDetailId`, `select:countOf`, `select:findBy`, `select:daySum`, `select:monthSum`, `update:updateDaySum`, `update:updateMonthSum`, `select:getTotalIncomeSum`, `select:findByDetail`, `select:countOfDetail`
- tables: `id`, `light_electric_order`, `light_station`, `light_station_white_list`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightBusinessCustomer.xml
- namespace: `com.rrsjk.light.dao.LightBusinessCustomerDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationDesignTypeDetail.xml
- namespace: `com.rrsjk.light.dao.LightStationDesignTypeDetailDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `delete:deleteByStationCode`, `insert:batchInsert`, `select:getById`, `select:getByStationCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmGvsPoSign.xml
- namespace: `com.rrsjk.light.dao.CmGvsPoSignDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findBySuccess`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightMakeOrderExport.xml
- namespace: `com.rrsjk.light.dao.LightMakeOrderExportDao`
- statements: `select:findBy`, `select:findByPage`, `select:countOf`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/HuarongIdCardInfo.xml
- namespace: `com.rrsjk.light.dao.HuarongIdCardInfoDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmPreOrder.xml
- namespace: `com.rrsjk.light.dao.CmPreOrderDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByPreOrderNo`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightAuditImageRejectRecord.xml
- namespace: `com.rrsjk.light.dao.LightAuditImageRejectRecordDao`
- statements: `insert:create`, `select:findByAuditId`, `delete:deleteByAuditId`, `delete:deleteByStationAuditType`, `delete:deleteByTarget`, `select:findLatestGridCertByStation`, `select:findLatestFieldImageByStation`, `select:findInverterImageRejects`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightOverduePolicyArea.xml
- namespace: `com.rrsjk.light.dao.LightOverduePolicyAreaDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpInspire.xml
- namespace: `com.rrsjk.light.dao.LightSpInspireDao`
- statements: `insert:create`, `update:update`, `update:doUpdate`, `update:updateByStatus`, `update:removeCostVoucher`, `select:findBy`, `select:countOf`, `select:getById`, `delete:deleteSpWABySpCode`, `delete:deleteById`, `select:findByWASpCode`, `select:findByNoIsWA`, `select:findBySpIdAndStatusInPendingStatus`, `select:findEffectiveByStationCodeList`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/HhRegister.xml
- namespace: `com.rrsjk.light.dao.HhRegisterDao`
- statements: `insert:create`, `update:update`, `select:findByMemberId`
- tables: `hh_register`, `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightWarningRegion.xml
- namespace: `com.rrsjk.light.dao.LightWarningRegionDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/YantuMonthlyElectricity.xml
- namespace: `com.rrsjk.light.dao.YantuMonthlyElectricityDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:updateByRelationId`, `select:findByRelationId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmOwnerStationReportThirdLog.xml
- namespace: `com.rrsjk.light.dao.CmOwnerStationReportThirdLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmLightProjectIncomeConfirm.xml
- namespace: `com.rrsjk.light.dao.CmLightProjectIncomeConfirmDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/ReportMOrderGoal.xml
- namespace: `com.rrsjk.light.dao.ReportMOrderGoalDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightInstantReward.xml
- namespace: `com.rrsjk.light.dao.LightInstantRewardDao`
- statements: `select:findBy`, `select:findOneBy`, `select:countOf`, `insert:create`, `update:update`, `update:removeCostVoucher`, `insert:batchInsert`, `select:getById`, `select:findByStationCode`, `select:findByNotConfirmWithStationCode`, `select:findByStationCodesWithNotCostVoucher`, `select:findByNotConfirm`
- tables: `id`, `light_instant_reward`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightShareBillRecordStatusImpRec.xml
- namespace: `com.rrsjk.light.dao.LightShareBillRecordStatusImpRecDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSubStock.xml
- namespace: `com.rrsjk.light.dao.LightSubStockDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:getByStoreIdAndSku`, `update:freezeStock`, `update:unFreezeStock`, `update:freezeSub`, `update:outStock`, `update:inStock`
- tables: `id`, `light_sub_sp_region`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmProductionValueIncome.xml
- namespace: `com.rrsjk.light.dao.CmProductionValueIncomeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByIncomeCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationEpcMapper.xml
- namespace: `com.rrsjk.light.mapper.LightStationEpcMapper`
- statements: `select:queryCount`, `select:queryPage`
- tables: `cm_contract_manage`, `cm_light_project`, `light_station`, `light_station_epc`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmConstructionPlanItem.xml
- namespace: `com.rrsjk.light.dao.CmConstructionPlanItemDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteByPlanId`, `select:findByPlanId`, `delete:delete`
- tables: `cm_construction_plan`, `cm_construction_plan_item`, `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightNewMerchantPolicyItem.xml
- namespace: `com.rrsjk.light.dao.LightNewMerchantPolicyItemDao`
- statements: `insert:create`, `insert:batchInsert`, `select:findBy`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmSignGuaranteeRateReport.xml
- namespace: `com.rrsjk.light.dao.CmSignGuaranteeRateReportDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteByDate`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationPersonInfoAuth.xml
- namespace: `com.rrsjk.light.dao.LightStationPersonInfoAuthDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByIdCardNumber`, `select:getByPersonCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSubSpRegion.xml
- namespace: `com.rrsjk.light.dao.LightSubSpRegionDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `select:getById`, `select:getBySubId`, `insert:batchInsert`, `delete:deleteBySubId`, `select:getBySubIdAndCityId`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/OperationInstall.xml
- namespace: `com.rrsjk.light.dao.OperationInstallDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByOrderNo`, `select:findHistory`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/BusinessAuditSnapShotMapper.xml
- namespace: `com.rrsjk.light.mapper.BusinessAuditSnapShotMapper`
- statements: `select:selectByPrimaryKey`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `select:selectByStationCode`
- tables: `business_audit_snap_shot`, `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/PyInvoice.xml
- namespace: `com.rrsjk.light.dao.PyInvoiceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:delete`
- tables: `id`, `py_invoice`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmPaymentMilestoneAudit.xml
- namespace: `com.rrsjk.light.dao.CmPaymentMilestoneAuditDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByProjectId`, `delete:deleteByProjectId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmPolicyAuditRecord.xml
- namespace: `com.rrsjk.light.dao.CmPolicyAuditRecordDao`
- statements: `select:findBy`, `select:findByPolicyIds`, `insert:create`, `update:update`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationYuexiuAccountOrder.xml
- namespace: `com.rrsjk.light.dao.LightStationYuexiuAccountOrderDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/lightOrderForecastService.xml
- namespace: `com.rrsjk.light.dao.LightOrderForecastServiceDao`
- statements: `select:findBy`, `select:findByLeftJoin`, `select:countFindByLeftJoin`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteByRelateId`
- tables: `id`, `light_order_forecast`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/UserProblemManagement.xml
- namespace: `com.rrsjk.light.dao.assistant.UserProblemManagementDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmOwnerStationReport.xml
- namespace: `com.rrsjk.light.dao.CmOwnerStationReportDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findReportBy`, `select:countReportOf`, `select:findByYear`, `select:countOfByYear`, `select:findByMonth`, `select:countOfByMonth`, `delete:deleteByProjectName`
- tables: `cm_owner_station_report`, `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/PushInsuranceLog.xml
- namespace: `com.rrsjk.light.dao.PushInsuranceLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightAuxiliaryMaterialDepositFlow.xml
- namespace: `com.rrsjk.light.dao.LightAuxiliaryMaterialDepositFlowDao`
- statements: `select:findBy`, `select:countOf`, `select:getById`, `select:findS8RollbackSourceForUpdate`, `select:findD13RollbackSourceForUpdate`, `insert:create`, `update:update`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationPolicy.xml
- namespace: `com.rrsjk.light.dao.LightStationPolicyDao`
- statements: `insert:create`, `update:update`, `select:findNewOne`, `select:findByStationCode`, `select:findByElecId`, `select:findRemark`
- tables: `id`, `light_station_policy`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStockChange.xml
- namespace: `com.rrsjk.light.dao.LightStockChangeDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByStockId`, `select:countOf`, `select:findBy`, `select:findExcludeInternalTransferByStockIds`, `select:countOfExcludeInternalTransferByStockIds`, `select:countOfJoinStore`, `select:findByJoinStore`, `select:findTotalInStockByStoreCodesAndSku`
- tables: `id`, `light_sp_store`, `light_stock_change`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CapitalDataParty.xml
- namespace: `com.rrsjk.light.dao.CapitalDataPartyDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `update:isDel`, `insert:batchInsert`, `select:getById`, `select:getByRelationId`
- tables: `capital_data_party`, `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSubStockChange.xml
- namespace: `com.rrsjk.light.dao.LightSubStockChangeDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByStockId`, `select:countOf`, `select:findBy`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpOpsNegativeExcitation.xml
- namespace: `com.rrsjk.light.dao.LightSpOpsNegativeExcitationDao`
- statements: `select:findBy`, `select:findDtoBy`, `select:findList`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:countOfSettle`, `select:findBySettle`
- tables: `id`, `light_sp_ops_settle`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightOrderForecast.xml
- namespace: `com.rrsjk.light.dao.LightOrderForecastDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getOrderForecastDetail`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightOpAuthorityZoneRemove.xml
- namespace: `com.rrsjk.light.dao.LightOpAuthorityZoneRemoveDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightImgsTemp.xml
- namespace: `com.rrsjk.light.dao.LightImgsTempDao`
- statements: `select:getByIdd`, `select:getByStationId`, `select:countOfParams`, `insert:createImgsInfo`, `update:updateImgsInfo`, `select:findByImgsParams`, `delete:delete`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/YuexiuInteractiveLog.xml
- namespace: `com.rrsjk.light.dao.YuexiuInteractiveLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `select:getByStationCode`, `select:getLastLog`, `select:getOneByStationCodeAndContent`
- tables: `id`, `yuexiu_interactive_log`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmPaymentMilestoneLog.xml
- namespace: `com.rrsjk.light.dao.CmPaymentMilestoneLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightFreezeSettleApplyMapper.xml
- namespace: `com.rrsjk.light.mapper.LightFreezeSettleApplyMapper`
- statements: `select:selectByPrimaryKey`, `insert:insert`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `update:updateByPrimaryKey`, `select:countOf`, `select:findByPage`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/OperationSettlementData.xml
- namespace: `com.rrsjk.light.dao.OperationSettlementDataDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `update:init`, `insert:batchInsert`, `select:getById`, `select:findByMemberId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmDepositAccount.xml
- namespace: `com.rrsjk.light.dao.CmDepositAccountDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmProductionValueIncomeItem.xml
- namespace: `com.rrsjk.light.dao.CmProductionValueIncomeItemDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteByIncomeCode`, `select:findByIncomeCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSubsidyMonth.xml
- namespace: `com.rrsjk.light.dao.LightSubsidyMonthDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:getByMonthOrderNo`, `select:getByProviderIdSumAt`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpUnionpayRentRecord.xml
- namespace: `com.rrsjk.light.dao.LightSpUnionpayRentRecordDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmPaymentMilestoneCheck.xml
- namespace: `com.rrsjk.light.dao.CmPaymentMilestoneCheckDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpOpsSettle.xml
- namespace: `com.rrsjk.light.dao.LightSpOpsSettleDao`
- statements: `select:findBy`, `select:findByOrder`, `select:findList`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByBillCode`, `select:findBySigned`, `select:findByLowHighIsNull`, `update:batchUpdate`, `select:findByIsDelOpName`, `select:findByBillCodes`, `select:findByStationCode`
- tables: `id`, `light_sp_ops_settle`, `light_sp_ops_settle_dcc`, `light_station_settle`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/OperationInstallStation.xml
- namespace: `com.rrsjk.light.dao.OperationInstallStationDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByRelationId`, `select:countOfByRelationId`, `select:countOfSum`, `select:findByPrams`, `select:countOfPrams`
- tables: `id`, `operation_maintenance`, `operation_maintenance_station`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightUseQueue.xml
- namespace: `com.rrsjk.light.dao.LightUseQueueDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findBySuccess`, `select:getByStationIdAndAction`, `select:findBy`, `select:countOf`, `select:findUniqueDataByStationIdAndAction`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpStaffRegion.xml
- namespace: `com.rrsjk.light.dao.LightSpStaffRegionDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteByStaffId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/NoOpStation.xml
- namespace: `com.rrsjk.light.dao.NoOpStationDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightProjectCompanyAccount.xml
- namespace: `com.rrsjk.light.dao.LightProjectCompanyAccountDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findValidByCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmInvoiceTaxClassificationData.xml
- namespace: `com.rrsjk.light.dao.CmInvoiceTaxClassificationDataDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightElecSealUse.xml
- namespace: `com.rrsjk.light.dao.LightElecSealUseDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByParams`, `select:findByParams`, `update:delete`, `update:deleteByStationId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightOrderUser.xml
- namespace: `com.rrsjk.light.dao.LightOrderUserDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/City.xml
- namespace: `com.rrsjk.light.dao.CityDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByCityId`, `select:getListByCityId`, `select:findAll`, `select:findDistinctSubCenters`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmLightProjectReceipt.xml
- namespace: `com.rrsjk.light.dao.CmLightProjectReceiptDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByReceiptCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpSettleConfig.xml
- namespace: `com.rrsjk.light.dao.LightSpSettleConfigDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationInverter.xml
- namespace: `com.rrsjk.light.dao.LightStationInverterDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `update:deleteByStationId`, `update:unStatusByStationCode`, `select:queryCountBy`, `select:findByParams`, `select:findByStationCode`, `select:findByInverterSn`, `select:findSingleMap`, `update:updateByStationCode`, `select:queryLastForOcr`
- tables: `id`, `light_station`, `light_station_inverter`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightElectricDaySum.xml
- namespace: `com.rrsjk.light.dao.LightElectricDaySumDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:getDayBySumAt`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpOrderInvoice.xml
- namespace: `com.rrsjk.light.dao.LightSpOrderInvoiceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByOrderId`, `delete:deleteByOrderId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationAudit.xml
- namespace: `com.rrsjk.light.dao.LightStationAuditDao`
- statements: `insert:create`, `update:update`, `update:updateForClearAuditInfo`, `update:updatePro`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:findFirstAuditByStationId`, `select:findByStationIdAndAuditType`, `select:findByStationCodeAndAuditType`, `select:findNeedDispatchByPlanAudit`, `select:findNeedDispatchByTechCheck`, `select:findNeedDispatchByWaitFirstAudit`, `update:cancelAudit`, `update:updateStationAuditForClearDispatchLog`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightElectTarget.xml
- namespace: `com.rrsjk.light.dao.LightElectTargetDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/TheoryElectHour.xml
- namespace: `com.rrsjk.light.dao.TheoryElectHourDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:updateSetNotNew`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightEpcSpAuthorityZone.xml
- namespace: `com.rrsjk.light.dao.LightEpcSpAuthorityZoneDao`
- statements: `insert:create`, `update:update`, `insert:batchInsert`, `select:findBySpIdAndProvinceId`, `select:findBySpId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/lightPushPyDictionary.xml
- namespace: `com.rrsjk.light.dao.LightPushPyDictionaryDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationProperty.xml
- namespace: `com.rrsjk.light.dao.LightStationPropertyDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationRentDeductMapper.xml
- namespace: `com.rrsjk.light.dao.LightStationRentDeductDao`
- statements: `select:findBy`, `select:findByBatchNo`, `select:count`, `insert:batchInsert`, `update:update`, `delete:delByBatchNo`, `select:countByBatchNo`, `select:countStationCodeAndDate`
- tables: `id`, `light_station`, `light_station_rent_deduct`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightProjectRent.xml
- namespace: `com.rrsjk.light.dao.LightProjectRentDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByStationId`, `update:updateElecNo`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightProjectAuthoritySp.xml
- namespace: `com.rrsjk.light.dao.LightProjectAuthoritySpDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:queryDtoListBy`, `select:queryDtoCountBy`, `select:queryOneBySpIdAndProjectId`, `delete:deleteSp`
- tables: `id`, `light_project_authority_sp`, `light_project_sp_partner`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/DbMonitor.xml
- namespace: `com.rrsjk.light.dao.DbMonitorDao`
- statements: `select:monitor`
- tables: `information_schema.INNODB_LOCKS`, `information_schema.INNODB_TRX`, `information_schema.PROCESSLIST`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSkuData.xml
- namespace: `com.rrsjk.light.dao.LightSkuDataDao`
- statements: `insert:create`, `update:update`, `update:updateNoCheck`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:findColumnsByParams`, `select:findDataListByDh`, `select:findByTypeListAndCity`, `select:getSkuDataBrandList`, `select:getInverterDataByBrandId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSapPoQueue.xml
- namespace: `com.rrsjk.light.dao.LightSapPoQueueDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findBySuccess`, `select:getByOrderIdAndAction`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpAuthorityZoneLog.xml
- namespace: `com.rrsjk.light.dao.LightSpAuthorityZoneLogDao`
- statements: `insert:create`, `update:update`, `select:findListByZoneId`
- tables: `id`, `light_sp_authority_zone_log`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmProjectFinalAcceptance.xml
- namespace: `com.rrsjk.light.dao.CmProjectFinalAcceptanceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationContractRecordLog.xml
- namespace: `com.rrsjk.light.dao.LightStationContractRecordLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightProjectManagement.xml
- namespace: `com.rrsjk.light.dao.LightProjectManagementDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:getByProjectCode`, `select:getByProjectCodes`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`, `light_project_funnel_management`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightOverduePolicy.xml
- namespace: `com.rrsjk.light.dao.LightOverduePolicyDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightBillFunnelData.xml
- namespace: `com.rrsjk.light.dao.LightBillFunnelDataDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmNode.xml
- namespace: `com.rrsjk.light.dao.CmNodeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByBizType`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightComponentLibrary.xml
- namespace: `com.rrsjk.light.dao.LightComponentLibraryDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:countOfAge`, `select:findAgeBy`, `update:freezeAssemblySn`, `update:disableAssemblySn`, `select:findAgeByInTransfer`, `select:countOfAgeTransfer`
- tables: `id`, `light_component_library`, `light_module_sn`, `light_purchase_order`, `light_transfer_order`, `light_transfer_order_sn`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightBenefitConversion.xml
- namespace: `com.rrsjk.light.dao.LightBenefitConversionDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:find`, `select:count`
- tables: `id`, `light_benefit_conversion`, `light_commodity`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightModulePartCompleteApply.xml
- namespace: `com.rrsjk.light.dao.LightModulePartCompleteApplyDao`
- statements: `insert:create`, `update:update`, `update:updateByStationCode`, `select:findBy`, `select:countOf`, `select:getById`
- tables: `id`, `light_sub_sp`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightCityElecPrice.xml
- namespace: `com.rrsjk.light.dao.LightCityElecPriceDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpOpGroupSum.xml
- namespace: `com.rrsjk.light.dao.LightSpOpGroupSumDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:getBySpAndRegion`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSparePartsDeposit.xml
- namespace: `com.rrsjk.light.dao.LightSparePartsDepositDao`
- statements: `select:findBy`, `select:getByDepositNo`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findTestEnv1PG0Data`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/YantuElectricityPriceTotal.xml
- namespace: `com.rrsjk.light.dao.YantuElectricityPriceTotalDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:updateByRelationId`, `select:findByRelationId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightRetryQueue.xml
- namespace: `com.rrsjk.light.dao.LightRetryQueueDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findBySuccess`, `select:getByOrderIdAndAction`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpAuthorityZone.xml
- namespace: `com.rrsjk.light.dao.LightSpAuthorityZoneDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:findListForCbs`, `select:findSpByCityIds`
- tables: `id`, `light_sp_authority_zone`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightTransferOrderImg.xml
- namespace: `com.rrsjk.light.dao.LightTransferOrderImgDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteByTransferNo`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightNewMerchantPolicy.xml
- namespace: `com.rrsjk.light.dao.LightNewMerchantPolicyDao`
- statements: `select:findByTimeCoincide`, `insert:create`, `update:update`, `select:findValidPolicy`, `select:countOf`, `select:findBy`, `select:getById`, `select:findByPolicyCode`
- tables: `id`, `light_new_merchant_policy`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmLightUseQueue.xml
- namespace: `com.rrsjk.light.dao.CmLightUseQueueDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpOperateLog.xml
- namespace: `com.rrsjk.light.dao.LightSpOperateLogDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightProjectElectricOrderFapCompany.xml
- namespace: `com.rrsjk.light.dao.LightProjectElectricOrderFapCompanyDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByCompanyAndOnlineAt`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightOpOrderSn.xml
- namespace: `com.rrsjk.light.dao.LightOpOrderSnDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteByOrderId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpQuota.xml
- namespace: `com.rrsjk.light.dao.LightSpQuotaDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmLightProjectFinishApply.xml
- namespace: `com.rrsjk.light.dao.CmLightProjectFinishApplyDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmInvoiceApplyImage.xml
- namespace: `com.rrsjk.light.dao.CmInvoiceApplyImageDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByApplyCode`, `delete:deleteByApplyCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpOpsSettleIac.xml
- namespace: `com.rrsjk.light.dao.LightSpOpsSettleIacDao`
- statements: `select:findBy`, `select:findByOrder`, `select:findList`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByBillCode`, `select:findBySigned`, `select:findByBillCodes`
- tables: `id`, `light_sp_ops_settle_dcc`, `light_sp_ops_settle_iac`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightOpOrderItem.xml
- namespace: `com.rrsjk.light.dao.LightOpOrderItemDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteByOrderId`, `update:updateByOrderId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationOperatorLog.xml
- namespace: `com.rrsjk.light.dao.LightStationOperateLogDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByParams`, `select:findAuditRejectInfo`, `select:findByParamsWithMax`, `select:findLatestByStationIdAndAuditType`, `select:countOf`, `select:countByStationAndOperate`, `select:getLastRejectReason`, `select:getFirstSubmitTime`, `select:hasAuditRecord`, `select:hasAuditPassRecord`, `select:findByFirstInputPiecePushFailed`
- tables: `id`, `light_station_operate_log`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationNannyUser.xml
- namespace: `com.rrsjk.light.dao.LightStationNannyUserDao`
- statements: `insert:create`, `update:update`, `select:findBy`, `select:countOf`, `select:getById`, `select:getByPhone`
- tables: `id`, `light_station`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightInvoiceTemplate.xml
- namespace: `com.rrsjk.light.dao.LightInvoiceTemplateDao`
- statements: `select:findBy`, `select:countOf`, `select:maxCount`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteByIds`, `select:findEnableTemplateByCode`
- tables: `LENGTH`, `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/WholeVillageTogetherDetail.xml
- namespace: `com.rrsjk.light.dao.WholeVillageTogetherDetailDao`
- statements: `select:findBy`, `select:findSingleColumnBy`, `select:findByWithJoin`, `select:countOf`, `insert:create`, `update:update`, `update:release`, `insert:batchInsert`, `select:getById`, `select:getByGroupNumber`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmOperateLog.xml
- namespace: `com.rrsjk.light.dao.CmOperateLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findLogs`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/HhVerificationCode.xml
- namespace: `com.rrsjk.light.dao.HhVerificationCodeDao`
- statements: `insert:create`, `update:update`, `select:findUnallocated`, `select:findByCode`, `select:queryListBy`, `select:queryCountBy`, `select:findByMemberIdAndChannel`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightCapitalOperateLog.xml
- namespace: `com.rrsjk.light.dao.LightCapitalOperateLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightCompanyPrice.xml
- namespace: `com.rrsjk.light.dao.LightCompanyPriceDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `update:updateAuditById`, `select:findBy`, `select:countOf`, `delete:deleteByIds`, `select:findByIds`, `select:getById`, `select:getByEnable`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightCoinDaySum.xml
- namespace: `com.rrsjk.light.dao.LightCoinDaySumDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:getByDayNo`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationTransferOrder.xml
- namespace: `com.rrsjk.light.dao.LightStationTransferOrderDao`
- statements: `insert:create`, `insert:batchCreate`, `update:update`, `select:get`, `select:getForUpdate`, `select:findProcessingByStationCodes`, `select:findBy`, `select:countOf`
- tables: `id`, `light_station_transfer_order`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightWorkOrderDto.xml
- namespace: `com.rrsjk.light.dao.LightWorkOrderDtoDao`
- statements: `select:queryListBy`, `select:queryCountBy`
- tables: `light_construction_team`, `light_station`, `light_station_plan_config`, `light_sub_sp`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/OperationMaintenanceSapLog.xml
- namespace: `com.rrsjk.light.dao.OperationMaintenanceSapLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightVersionInformation.xml
- namespace: `com.rrsjk.light.dao.LightVersionInformationDao`
- statements: `select:findBy`, `select:findByHds`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationEpcPlanChange.xml
- namespace: `com.rrsjk.light.dao.LightStationEpcPlanChangeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightPartnerOperateLog.xml
- namespace: `com.rrsjk.light.dao.LightPartnerOperateLogDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightEamConfig.xml
- namespace: `com.rrsjk.light.dao.LightEamConfigDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationSpecialDeal.xml
- namespace: `com.rrsjk.light.dao.LightStationSpecialDealDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightAuxiliaryMakeOrder.xml
- namespace: `com.rrsjk.light.dao.LightAuxiliaryMakeOrderDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:getByOrderNo`, `select:findByMemberId`, `select:getByStationId`, `select:findByBatchNo`, `select:countOf`, `select:countOfPro`, `select:findBy`, `select:findByPagePro`, `select:findByIdList`, `select:findGroupByOrderNo`, `select:countOfGroupByOrderNo`, `delete:deleteByOrderNo`, `select:getByConfirmId`, `select:findNotStopByConfirmId`, `select:findStopByConfirmId`, `select:getAllDisplayName`
- tables: `id`, `light_auxiliary_make_order`, `light_station`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/OperationMaintenanceStation.xml
- namespace: `com.rrsjk.light.dao.OperationMaintenanceStationDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByRelationId`, `select:countOfByRelationId`, `select:countOfSum`, `select:findByPrams`, `select:countOfPrams`, `update:updateByJob`, `update:updateByRelationId`, `select:getByOrderNo`, `update:batchDel`, `update:updateByRelationIdAndStationCode`, `update:batchDelByOrderNo`, `update:batchUpdateById`
- tables: `id`, `operation_maintenance`, `operation_maintenance_station`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpGridAwardOrderDetail.xml
- namespace: `com.rrsjk.light.dao.LightSpGridAwardOrderDetailDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByOrderId`, `select:getByStationCodeList`, `update:removeCostVoucher`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightFinanceRecord.xml
- namespace: `com.rrsjk.light.dao.LightFinanceRecordDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:getByStationId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationInfoExtension.xml
- namespace: `com.rrsjk.light.dao.LightStationInfoExtensionDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByStationId`, `select:getByStationCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightLendChange.xml
- namespace: `com.rrsjk.light.dao.LightLendChangeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightCompanyPolicy.xml
- namespace: `com.rrsjk.light.dao.LightCompanyPolicyDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:findByPagePro`, `select:findCountPro`, `select:getByCompanyPolicy`, `select:getByCompanyPolicySignAt`, `select:findByPage`, `select:findByPageCount`, `select:findByPageWithRegion`, `select:findByPageWithRegionCount`, `select:findByIds`, `select:findSpPolicy`, `select:queryPolicyDetail`, `select:findSpPolicyCount`, `update:logicDelete`
- tables: `id`, `light_company_manage_region`, `light_company_policy`, `light_sp_authority_zone`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmGvsPoCreate.xml
- namespace: `com.rrsjk.light.dao.CmGvsPoCreateDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findBySuccess`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightHighElec.xml
- namespace: `com.rrsjk.light.dao.LightHighElecDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByOrderNo`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightUnionpayRentQueue.xml
- namespace: `com.rrsjk.light.dao.LightUnionpayRentQueueDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findBySuccess`, `select:getByStationIdAndAction`, `select:getByStationCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightOperationProviderSlave.xml
- namespace: `com.rrsjk.light.dao.LightOperationProviderSlaveDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:getByMemberId`, `select:findBy`, `select:countOf`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmChangeItem.xml
- namespace: `com.rrsjk.light.dao.CmChangeItemDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteByChangeId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/SwitchLightMode.xml
- namespace: `com.rrsjk.light.dao.SwitchLightModeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:updateByBatchNo`, `update:update`, `insert:batchInsert`, `select:getById`, `select:queryByBatchNo`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightShareBillAuditLog.xml
- namespace: `com.rrsjk.light.dao.LightShareBillAuditLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationContractRecord.xml
- namespace: `com.rrsjk.light.dao.LightStationContractRecordDao`
- statements: `insert:create`, `update:update`, `update:updateStatusByStationId`, `update:updateByStationCode`, `select:getById`, `select:queryListBy`, `select:queryListByNew`, `select:queryListCountRefactor`, `select:queryListRefactor`, `select:queryListCount`, `select:queryListForExport`, `select:queryCountBy`, `select:findByParams`, `select:queryContractListBy`, `select:queryContractCountBy`, `select:queryMergeContractListBy`, `select:queryMergeContractCountBy`, `select:findByContractNo`, `select:findDhByContractNo`, `select:queryPfContractListBy`, `select:queryPfContractCountBy`, `select:findToUpdateContract`, `select:findToUpdateContractGf`, `select:getByStationCode`, `select:queryDHContractListBy`, `select:queryDHContractCountBy`, `select:getContractByStationCode`, `select:findMasterByStationCode`, `select:queryGfContractListBy`, `select:queryGfContractCountBy`, `select:queryHrflcContractListBy`, `select:queryHrflcContractCountBy`
- tables: `dh_business_opportunity`, `gf_business_opportunity`, `hrflc_audit_owner`, `id`, `light_sp_staff`, `light_station`, `light_station_contract_record`, `light_station_owner`, `light_station_person_info_auth`, `light_sub_sp`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightProjectElectricOrderTemporarily.xml
- namespace: `com.rrsjk.light.dao.LightProjectElectricOrderTemporarilyDao`
- statements: `delete:deleteAll`, `insert:insert`, `insert:batchInsert`, `select:findList`, `select:findListByRange`
- tables: `light_project_electric_order_temporarily`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightTransferSpApplyLog.xml
- namespace: `com.rrsjk.light.dao.LightTransferSpApplyLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByApplyId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightTransferSpApply.xml
- namespace: `com.rrsjk.light.dao.LightTransferSpApplyDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:updateByTransferNo`, `select:getByTransferNo`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmAttachment.xml
- namespace: `com.rrsjk.light.dao.CmAttachmentDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteAttachment`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightOverdueList.xml
- namespace: `com.rrsjk.light.dao.LightOverdueListDao`
- statements: `select:findBy`, `select:findNoVoucher`, `select:findNoVoucherByTargetDate`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByOrderNo`, `select:getSubCenterManger`
- tables: `id`, `rrsjk_light_report.energy_summary_target`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightContractInfo.xml
- namespace: `com.rrsjk.light.dao.LightContractInfoDao`
- statements: `insert:create`, `select:findBy`, `select:countOf`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmContractManage.xml
- namespace: `com.rrsjk.light.dao.CmContractManageDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationOwner.xml
- namespace: `com.rrsjk.light.dao.LightStationOwnerDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByOwnerNo`, `select:getByIdCardNumber`, `select:getByPhone`, `select:countOf`, `select:countOfNew`, `select:findBy`, `select:findByPushedAndWaitCheck`, `select:findByWaitPush`, `select:findNoPath`, `update:updatePath`, `update:delete`
- tables: `id`, `light_station_yuexiu_account`, `light_sub_sp`, `station_user_ocr_record`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightArea.xml
- namespace: `com.rrsjk.light.dao.LightAreaDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByProvinceId`, `select:countOf`, `select:findBy`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSapDnQueue.xml
- namespace: `com.rrsjk.light.dao.LightSapDnQueueDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findBySuccess`, `select:getByOrderIdAndAction`, `select:getByOrderIdAndCategory`, `select:findByOrderNoIsNull`, `select:findByOrderNo`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightInstantRewardPolicy.xml
- namespace: `com.rrsjk.light.dao.LightInstantRewardPolicyDao`
- statements: `select:findBy`, `select:findNoMergeEnableByTime`, `select:findMergeEnableByTime`, `select:checkCompleteAt`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByCode`, `update:logicDelete`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightUnionpayBill.xml
- namespace: `com.rrsjk.light.dao.LightUnionpayBillDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByBillBatchNo`, `select:getSendBill`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightGfyunLog.xml
- namespace: `com.rrsjk.light.dao.LightGfyunLogDao`
- statements: `insert:create`, `update:update`, `select:get`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmLightProjectSignInfo.xml
- namespace: `com.rrsjk.light.dao.CmLightProjectSignInfoDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmLightProjectIncomeAmount.xml
- namespace: `com.rrsjk.light.dao.CmLightProjectIncomeAmountDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteByIncomeId`, `select:findByProjectCode`
- tables: `cm_light_project_income`, `cm_light_project_income_amount`, `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpMaterialPrice.xml
- namespace: `com.rrsjk.light.dao.LightSpMaterialPriceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `update:batchUpdate`, `select:findById`, `select:findBySkuCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmDataSyncProject.xml
- namespace: `com.rrsjk.light.dao.CmDataSyncProjectDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpOrderItem.xml
- namespace: `com.rrsjk.light.dao.LightSpOrderItemDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByOrderItemNo`, `delete:deleteByOrderId`, `update:updateByOrderId`, `select:sumNumberBySpSku`
- tables: `id`, `light_service_provider`, `light_sp_order`, `light_sp_order_item`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationCopy1.xml
- namespace: `com.rrsjk.light.dao.LightStationCopy1Dao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByElecNo`, `select:getByStationCode`, `select:findByMemberId`, `select:countOf`, `select:queryLightStationViewCountOf`, `select:findBy`, `select:queryLightStationView`, `select:findByNoPage`, `select:countReviewMaterialOf`, `select:findReviewMaterialBy`, `select:countFinalFirstOf`, `select:findFinalFirstBy`, `select:getCheckByCode`, `select:findChangeStation`, `select:findStationSum`, `select:findBuildStationSum`, `select:findNoLonLatList`, `select:countReportData`, `select:listReportData`, `select:listReportDataBind`, `select:countReportDataBind`, `update:updateSignStatusByIdCardNumber`, `select:findByMobile`, `select:selectAllStationWithoutPs`, `update:updatePsById`, `select:findAuditOkFinalFirst`, `select:findByStationCode`, `select:findFirstAuditAt`
- tables: `change_station_tmp`, `id`, `light_limit_final_check`, `light_station`, `light_station_audit`, `light_station_white_list`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightNewMerchantRewardItem.xml
- namespace: `com.rrsjk.light.dao.LightNewMerchantRewardItemDao`
- statements: `select:findBy`, `select:findByStationCode`, `select:countOf`, `insert:batchInsert`, `update:update`, `update:removeCostVoucher`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightPlanDiagram.xml
- namespace: `com.rrsjk.light.dao.LightPlanDiagramDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `update:delDiagram`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpTarget.xml
- namespace: `com.rrsjk.light.dao.LightSpTargetDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/ChannelYuexiuProductParam.xml
- namespace: `com.rrsjk.light.dao.ChannelYuexiuProductParamDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByProductParamCode`, `select:findByProductCode`, `select:findByNeedProjectPush`, `select:countOf`, `select:findBy`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpQuotaConfig.xml
- namespace: `com.rrsjk.light.dao.LightSpQuotaConfigDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpServiceProvince.xml
- namespace: `com.rrsjk.light.dao.LightSpServiceProvinceDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:countOf`, `select:findBy`, `select:findApprovedList`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmNodeAttachmentTemplate.xml
- namespace: `com.rrsjk.light.dao.CmNodeAttachmentTemplateDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/DccRegistMobile.xml
- namespace: `com.rrsjk.light.dao.DccRegistMobileDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:getByMobile`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationAmmeter.xml
- namespace: `com.rrsjk.light.dao.LightStationAmmeterDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByStationCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpOpsPositiveExcitation.xml
- namespace: `com.rrsjk.light.dao.LightSpOpsPositiveExcitationDao`
- statements: `select:findBy`, `select:findDtoBy`, `select:findList`, `select:findListStatus`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByGroupBatchNo`, `select:countOfSettle`, `select:findDtoBySettle`
- tables: `id`, `light_sp_ops_settle`, `rrsjk_light.light_sp_ops_positive_excitation`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationInsurancePushQueue.xml
- namespace: `com.rrsjk.light.dao.LightStationInsurancePushQueueDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightFundSettle.xml
- namespace: `com.rrsjk.light.dao.LightFundSettleDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `update:updateZhSettleForReverse`, `insert:batchInsert`, `select:getById`, `select:getByStationCode`, `delete:deleteByBatchNo`, `update:batchUpdateInfoForReverse`, `select:existsByStationCode`, `select:findActiveStationCodes`, `select:getLatestIncomeTime`, `select:findLatestByStationCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CreateOperationMaintenanceStation.xml
- namespace: `com.rrsjk.light.dao.CreateOperationMaintenanceStationDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:updateHistory`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/ZhongYinTradeIncomeSettle.xml
- namespace: `com.rrsjk.light.dao.ZhongYinTradeIncomeSettleDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:updateByBatchNo`, `delete:deleteByBatchNo`, `select:existsByStationCode`, `select:findActiveStationCodes`, `select:getLatestIncomeTime`, `select:getLatestByStationCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmSimpleProject.xml
- namespace: `com.rrsjk.light.dao.CmSimpleProjectDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByCode`, `select:findSignGuaranteeRateReport`, `update:updateInvestor`, `select:findListByProjectLeader`
- tables: `cm_light_project_income`, `cm_light_project_income_amount`, `cm_simple_project`, `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightCompanyManageRegion.xml
- namespace: `com.rrsjk.light.dao.LightCompanyManageRegionDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:findByGroupBY`, `select:queryCountByGroupBY`, `select:findByCode`, `select:findByStreet`, `select:findByRegion`, `select:findByCity`, `select:findOneByStreet`, `select:findOneByRegion`, `select:findOneByCity`, `select:findByAddressAndCompanyCodeAndMode`, `select:checkCompany`, `select:findMatchRegionByParams`
- tables: `id`, `light_company_info`, `light_company_manage_region`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStoreOutRecord.xml
- namespace: `com.rrsjk.light.dao.LightStoreOutRecordDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByMemberId`, `select:countOf`, `select:findBy`, `select:countForMchOf`, `select:findForMchBy`, `select:findByStationIdAndStoreIdAndNumber`
- tables: `id`, `light_station`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/ChannelYuexiu.xml
- namespace: `com.rrsjk.light.dao.ChannelYuexiuDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByCompanyCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationChangeOperation.xml
- namespace: `com.rrsjk.light.dao.LightStationChangeOperationDao`
- statements: `select:findBy`, `select:findByParams`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`, `light_station_change_operation`, `light_station_change_record`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/RentTaxAmountSummary.xml
- namespace: `com.rrsjk.light.dao.RentTaxAmountSummaryDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:getByOrderNo`, `update:updateConfirmStatus`, `update:updateVoucher`, `select:queryUnConfirmCompanyCodeByRentMonth`, `select:queryConfirmCompanyCodeByRentMonth`
- tables: `id`, `rent_tax_amount_summary`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationRepurchaseLog.xml
- namespace: `com.rrsjk.light.dao.LightStationRepurchaseLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByRepurchaseId`
- tables: `id`, `light_station_repurchase_log`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightWvRent.xml
- namespace: `com.rrsjk.light.dao.LightWvRentDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByStationId`, `update:updateElecNo`
- tables: `id`, `light_station`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightGridAwardPolicyDetail.xml
- namespace: `com.rrsjk.light.dao.LightGridAwardPolicyDetailDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findByPolicyId`, `delete:deleteByPolicyId`, `insert:batichCreate`, `select:countOf`, `select:findByPolicyIds`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightElectricMonthSum.xml
- namespace: `com.rrsjk.light.dao.LightElectricMonthSumDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:getMonthBySumAt`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/lightModuleSn.xml
- namespace: `com.rrsjk.light.dao.LightModuleSnDao`
- statements: `select:findBy`, `select:findList`, `select:countOf`, `insert:create`, `update:update`, `update:updateBySn`, `update:disableModule`, `insert:batchInsert`, `select:getById`, `delete:batchDeleteByStationId`, `delete:batchDeleteByStationCode`, `delete:batchDeleteSpTypeByStationCode`, `delete:batchDeleteOpTypeByStationCode`, `delete:batchDeleteOutTypeByStationCode`, `update:updateByStationCode`
- tables: `id`, `light_station`, `light_sub_sp`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightCityRentPrice.xml
- namespace: `com.rrsjk.light.dao.LightCityRentPriceDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightElecOcrMapper.xml
- namespace: `com.rrsjk.light.mapper.LightElecOcrMapper`
- statements: `select:selectByPrimaryKey`, `insert:insert`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `update:updateByPrimaryKey`, `select:findByParam`, `select:getByStationCode`
- tables: `id`, `light_elec_ocr`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/HuaRongTradeIncomeSettle.xml
- namespace: `com.rrsjk.light.dao.HuaRongTradeIncomeSettleDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:updateByBatchNo`, `delete:deleteByBatchNo`, `select:findLatestByStationCode`, `select:existsByStationCode`, `select:findActiveStationCodes`, `select:getLatestIncomeTime`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationEnableRewardQueue.xml
- namespace: `com.rrsjk.light.dao.LightStationEnableRewardQueueDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findSuccessByStationCodes`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightRent.xml
- namespace: `com.rrsjk.light.dao.LightRentDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByStationId`, `select:getByStationCode`, `select:getByElecNo`, `select:findByStatus`, `select:findByAuthorisationStatus`, `select:countOf`, `select:findBy`, `update:updateElecNo`
- tables: `id`, `light_station`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmLightProjectIncomePolicy.xml
- namespace: `com.rrsjk.light.dao.CmLightProjectIncomePolicyDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/OperationSettlementDataConfig.xml
- namespace: `com.rrsjk.light.dao.OperationSettlementDataConfigDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/lightDccCompanyUpdateHistory.xml
- namespace: `com.rrsjk.light.dao.LightDccCompanyUpdateHistoryDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightAuxiliaryMaterialPlanConfigDetail.xml
- namespace: `com.rrsjk.light.dao.LightAuxiliaryMaterialPlanConfigDetailDao`
- statements: `insert:create`, `update:update`, `update:updateByMaterialConfigId`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:getByMaterialConfigId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/PyStationInfo.xml
- namespace: `com.rrsjk.light.dao.PyStationInfoDao`
- statements: `select:getByStationCode`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightInstantRewardPolicyMonth.xml
- namespace: `com.rrsjk.light.dao.LightInstantRewardPolicyMonthDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightCase.xml
- namespace: `com.rrsjk.light.dao.LightCaseDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `select:getById`, `select:getByOptionId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightElecNoCheck.xml
- namespace: `com.rrsjk.light.dao.LightElecNoCheckDao`
- statements: `insert:create`, `update:update`, `select:findOne`, `select:findList`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/RentTaxAmountRecord.xml
- namespace: `com.rrsjk.light.dao.RentTaxAmountRecordDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `update:updateValidByBatchNo`, `update:updateValidByRentMonth`, `update:updateValidByRentMonthAndCompanyCodes`
- tables: `id`, `rent_tax_amount_record`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightEamFixedPriceConfig.xml
- namespace: `com.rrsjk.light.dao.LightEamFixedPriceConfigDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmGvsSoUse.xml
- namespace: `com.rrsjk.light.dao.CmGvsSoUseDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findBySuccess`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationEpc.xml
- namespace: `com.rrsjk.light.dao.LightStationEpcDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:getByStationId`, `select:getByProjectId`
- tables: `id`, `light_station`, `light_station_epc`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpShareQuotaAuditLog.xml
- namespace: `com.rrsjk.light.dao.LightSpShareQuotaAuditLogDao`
- statements: `insert:create`, `select:findAll`
- tables: `light_sp_share_quota_audit_log`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightShareBill.xml
- namespace: `com.rrsjk.light.dao.LightShareBillDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationPartCompleteApplyImg.xml
- namespace: `com.rrsjk.light.dao.LightStationPartCompleteApplyImgDao`
- statements: `insert:create`, `insert:batchInsert`, `delete:deleteByApplyId`, `select:findBy`, `select:countOf`, `select:getById`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/ChannelYuexiuLogExchange.xml
- namespace: `com.rrsjk.light.dao.ChannelYuexiuLogExchangeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findIncomeInfo`, `select:findIncomeAttachInfo`, `select:findPushInfo`, `select:findPushAttachInfo`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationCodeHuarun.xml
- namespace: `com.rrsjk.light.dao.LightStationCodeHuarunDao`
- statements: `select:list`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpOpsPositiveIac.xml
- namespace: `com.rrsjk.light.dao.LightSpOpsPositiveIacDao`
- statements: `select:findBy`, `select:findDtoBy`, `select:findList`, `select:findListStatus`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:countOfSettle`, `select:findBySettle`
- tables: `id`, `light_sp_ops_settle_iac`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightOpOrder.xml
- namespace: `com.rrsjk.light.dao.LightOpOrderDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findWaitPayOrder`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightHdIncomePriceConfig.xml
- namespace: `com.rrsjk.light.dao.LightHdIncomePriceConfigDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/PyFile.xml
- namespace: `com.rrsjk.light.dao.PyFileDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightEamAssets.xml
- namespace: `com.rrsjk.light.dao.LightEamAssetsDao`
- statements: `update:update`, `update:updateByIdAndStatus`, `insert:create`, `select:findBy`, `select:countOf`, `insert:batchInsert`, `update:updateByIds`, `update:updateByOrdCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightModuleSnLog.xml
- namespace: `com.rrsjk.light.dao.LightModuleSnLogDao`
- statements: `select:findBy`, `select:findList`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/RepairTransferLog.xml
- namespace: `com.rrsjk.light.dao.RepairTransferLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpOpsSettleDcc.xml
- namespace: `com.rrsjk.light.dao.LightSpOpsSettleDccDao`
- statements: `select:findBy`, `select:findData`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByBillCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightShareBillRecordFailLog.xml
- namespace: `com.rrsjk.light.dao.LightShareBillRecordFailLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationPlanChange.xml
- namespace: `com.rrsjk.light.dao.LightStationPlanChangeDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryListBySimple`, `select:queryCountBy`, `select:findByParams`, `select:queryCountByWithLightStation`, `select:queryListByWithLightStation`, `select:findStationCountByDifferNode`
- tables: `id`, `light_station`, `light_station_plan_change`, `light_sub_sp`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightMaterialPackageSkuDataRelation.xml
- namespace: `com.rrsjk.light.dao.LightMaterialPackageSkuDataRelationDao`
- statements: `insert:create`, `insert:batchInsert`, `select:get`, `select:getByPackageNo`, `select:countOf`, `select:findBy`, `update:disableByPackageNo`, `update:disableByPackageNoAndSkuCode`, `delete:deleteByPackageNo`, `update:enableByPackageNo`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightNewMerchantPolicyLog.xml
- namespace: `com.rrsjk.light.dao.LightNewMerchantPolicyLogDao`
- statements: `insert:create`, `select:findBy`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightLend.xml
- namespace: `com.rrsjk.light.dao.LightLendDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getBySourceNo`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/StationChangeOperation.xml
- namespace: `com.rrsjk.light.dao.StationChangeOperationDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findBy`, `select:countOf`
- tables: `id`, `light_station`, `light_sub_sp`, `station_change_operation`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/ReportMWholeCountyGoal.xml
- namespace: `com.rrsjk.light.dao.ReportMWholeCountyGoalDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationPlanChangeAuditLog.xml
- namespace: `com.rrsjk.light.dao.LightStationPlanChangeAuditLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `select:getById`, `select:getByUpdateId`
- tables: `id`, `light_station_plan_change_audit_log`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightNewMerchantPolicyDelayItem.xml
- namespace: `com.rrsjk.light.dao.LightNewMerchantPolicyDelayItemDao`
- statements: `insert:create`, `insert:batchInsert`, `select:findBy`, `delete:deleteByPolicyCode`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationZhongheOwner.xml
- namespace: `com.rrsjk.light.dao.LightStationZhongheOwnerDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByPhone`, `select:getByIdCardNumber`, `select:countOf`, `select:findByJoin`, `select:findByItself`, `select:findNoPath`, `update:updatePath`
- tables: `id`, `light_sub_sp`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmLightProjectCapitalInfo.xml
- namespace: `com.rrsjk.light.dao.CmLightProjectCapitalInfoDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByProjectId`, `update:deleteByProjectId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpZoneStreet.xml
- namespace: `com.rrsjk.light.dao.LightSpZoneStreetDao`
- statements: `insert:created`, `update:update`, `update:deleteByZoneId`, `insert:batchInsert`, `select:findListByZoneId`
- tables: `id`, `light_sp_zone_street`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/ReportMStationGoal.xml
- namespace: `com.rrsjk.light.dao.ReportMStationGoalDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpInspireCategoryConfig.xml
- namespace: `com.rrsjk.light.dao.LightSpInspireCategoryConfigDao`
- statements: `select:findBy`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/TaxAmountCalculateSourceData.xml
- namespace: `com.rrsjk.light.dao.TaxAmountCalculateSourceDataDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:findValidBillRecordNosByRentMonth`, `select:findValidBillRecordNos`, `select:findProcessedUniqueCheckKeys`, `update:updateValidByBatchNo`, `update:updateValidByRentMonth`, `update:updateValidByRentMonthAndCompanyCodes`
- tables: `id`, `tax_amount_calculate_source_data`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStation.xml
- namespace: `com.rrsjk.light.dao.LightStationDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getForUpdate`, `select:findByElecNo`, `select:findByElecNoRightLike`, `select:findByElecNosRightLike`, `select:findByElecNos`, `select:getByStationCode`, `select:getByStationCodes`, `select:findByMemberId`, `select:findByOpMemberId`, `select:countOf`, `select:getMaxId`, `select:getMaxIdCondition`, `select:countForCBSExport`, `select:countOfByAllRefactor`, `select:countOfByAll`, `select:queryLightStationViewCountOf`, `select:findByForCBSExport`, `select:findByForCBSExportNew`, `select:findByForCBSExportPage`, `select:findByRefactor`, `select:findLatestOneByParams`, `select:findByAllOfColumns`, `select:findBy`, `select:queryLightStationView`, `select:queryPyInfos`, `select:findByNoPage`, `select:findOverdueStationsForNotify`, `select:findBySht`, `select:findByOpIdNull`, `select:countReviewMaterialOf`, `select:findReviewMaterialBy`, `select:countFinalFirstOf`, `select:findFinalFirstBy`, `select:getCheckByCode`, `select:findChangeStation`, `select:findStationSum`, `select:findBuildStationSum`, `select:findNoLonLatList`, `select:countReportData`, `select:listReportData`, `select:listReportDataBind`, `select:countReportDataBind`, `update:updateSignStatusByIdCardNumber`, `select:findByMobile`, `select:selectAllStationWithoutPs`, `update:updatePsById`, `select:findAuditOkFinalFirst`, `select:findByStationCode`, `select:findFirstAuditAt`, `select:getByStationCodeAndUserName`, `update:addChuiYangImage`, `select:countOfPlanAudit`, `select:findByForPlanAudit`, `select:findSkillCountOf`, `select:findSkillBy`, `select:findBusinessCountOf`, `select:findBusinessBy`, `select:getAllStationCodeByMemberId`, `select:getSubCenterByCity`, `select:getSubCenterByCityPro`, `select:findEpcStationCountOf`, `select:findEpcStation`, `select:getInstallerList`, `select:getGsyStationBy`, `select:getStationCodeBy`, `select:countGsyStationBy`, `select:getStationsByIds`, `select:getPvStationBAZ`, `select:queryZhongheStation`, `select:queryZhongheStationInfo`, `select:countOfZhongheStationInfo`, `select:findByHds`, `select:countOfHds`, `select:exportByHds`, `select:findNoPath`, `update:updatePath`, `update:changeUnionpayOrSharePayTypeById`
- tables: `boc_leasing_light_station`, `change_station_tmp`, `chd_light_station`, `city`, `cm_contract_manage`, `cm_light_project`, `id`, `light_limit_final_check`, `light_operation_provider`, `light_project_management`, `light_rent`, `light_service_provider`, `light_sp_staff`, `light_staging_records`, `light_station`, `light_station_audit`, `light_station_bank`, `light_station_confirm_img`, `light_station_contract_record`, `light_station_epc`, `light_station_plan_config`, `light_station_white_list`, `light_station_white_list_simple`, `light_station_yuexiu`, `light_sub_sp`, `light_unionpay_user`, `light_zero_carbon_station`, `zero_carbon_station_relate_file`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/GfLightStationConfirmImg.xml
- namespace: `com.rrsjk.light.dao.GfLightStationConfirmImgDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `update:markReject`, `update:clearRejectByAuditType`, `update:clearRejectById`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:findSimpleByParams`, `delete:delete`, `update:deleteByStationCode`, `update:updateStationIdToMinus`, `update:updateConfirmImgToNull`, `update:updateCompleteImgToNull`, `delete:deleteByTypeAndSortNum`, `delete:deleteByType`, `delete:deleteByTypeAndStationCode`, `select:getByImaNameAndType`, `select:getByImaNameAndTypeAndStationCode`, `select:getByImaNameAndStationCode`, `select:getByImgNameAndStationCodes`, `select:getListByImaNameAndType`, `select:getListByImaNameAndTypeAndStationCode`, `select:findByStationCodeAndTypeNoFilter`, `select:getGsyAppStationImg`, `select:findByStationIdAndTypeNoFilter`, `select:getByIds`, `select:getByStationCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/ChannelYuexiuLog.xml
- namespace: `com.rrsjk.light.dao.ChannelYuexiuLogDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findLastOne`, `select:findLastOnePro`, `select:findLastOnePlus`, `select:findIncomeLogs`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmReceiptPay.xml
- namespace: `com.rrsjk.light.dao.CmReceiptPayDao`
- statements: `select:countOf`, `select:findBy`
- tables: `cm_receipt_milestone`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationEpcPlanChangeLog.xml
- namespace: `com.rrsjk.light.dao.LightStationEpcPlanChangeLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightBusinessCustomerProgress.xml
- namespace: `com.rrsjk.light.dao.LightBusinessCustomerProgressDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findProgressByCustomerId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightTransferOrder.xml
- namespace: `com.rrsjk.light.dao.LightTransferOrderDao`
- statements: `select:findBy`, `select:countOf`, `select:findByExcludeInternalType`, `select:findTransferInStoreOptions`, `select:findTransferInTeamOptions`, `select:countOfExcludeInternalType`, `insert:create`, `update:update`, `update:updateByPreStatusAndId`, `insert:batchInsert`, `select:getById`, `select:getByNo`, `select:getByBatchNo`, `select:findStockNumBerMonth`, `select:findStockNumWeek`, `select:getStockOutNumber`, `select:getStockInNumber`, `select:countOfInternalTransferOrder`, `select:findInternalTransferOrder`
- tables: `id`, `light_sku_data`, `light_sp_store`, `light_transfer_order`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/RentSuspendApplicationRecord.xml
- namespace: `com.rrsjk.light.dao.RentSuspendApplicationRecordDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findBy`, `select:countOf`, `insert:batchInsert`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationChangeRecord.xml
- namespace: `com.rrsjk.light.dao.LightStationChangeRecordDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationEnableRewardItem.xml
- namespace: `com.rrsjk.light.dao.LightStationEnableRewardItemDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `update:reserve`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightRentPolicy.xml
- namespace: `com.rrsjk.light.dao.LightRentPolicyDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/StationChangeOperationLog.xml
- namespace: `com.rrsjk.light.dao.StationChangeOperationLogDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findBy`, `select:countOf`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightProjectElectricInvoiceReverseAuditLog.xml
- namespace: `com.rrsjk.light.dao.LightProjectElectricInvoiceReverseAuditLogDao`
- statements: `insert:create`, `select:getById`, `select:getByRecordId`, `select:countOf`, `select:findBy`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStagingRecords.xml
- namespace: `com.rrsjk.light.dao.LightStagingRecordsDao`
- statements: `select:findBy`, `select:findByList`, `select:findByNoPages`, `select:countOf`, `select:countOfList`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByIdForUpdate`, `update:delete`, `select:getByMemberId`, `select:findYanTuData`, `select:findCountOfYanTuData`, `select:findHouseHoldDraftCount`, `select:findHouseHoldDraftList`
- tables: `id`, `light_sp_staff`, `light_staging_records`, `light_station`, `light_sub_sp`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmbLeasingReworkFile.xml
- namespace: `com.rrsjk.light.dao.CmbLeasingReworkFileDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `update:updateStatusByStationCode`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationYuexiuAccountCancel.xml
- namespace: `com.rrsjk.light.dao.LightStationYuexiuAccountCancelDao`
- statements: `select:findBy`, `select:countOf`, `select:countOfForAdd`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightEnablePolicySp.xml
- namespace: `com.rrsjk.light.dao.LightEnablePolicySpDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/AiAssistantSubCenter.xml
- namespace: `com.rrsjk.light.dao.assistant.AiAssistantSubCenterDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/OmStationHistoryRecord.xml
- namespace: `com.rrsjk.light.dao.OmStationHistoryRecordDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:lastOne`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmLightProject.xml
- namespace: `com.rrsjk.light.dao.CmLightProjectDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryListForExportBy`, `select:queryCountBy`, `select:queryPartyListBy`, `select:queryPartyCountBy`, `select:findByParams`, `select:findByCode`, `update:updateProject`, `update:updateVote`, `select:findInIds`, `select:queryListForSummary`, `select:queryCountForSummary`, `select:queryListForReport`, `select:queryCountForReport`, `select:findSignGuaranteeRateReport`, `select:findByInvestor`, `select:queryCountByInvestor`, `update:updateInvestor`, `select:findProjectTotalIncomeReport`, `select:queryProjectTotalIncomeReportCount`, `select:findCountGrouByProjectLeader`, `select:findGrouByProjectLeader`, `select:findListByProjectLeader`, `select:findProjectIncomeAt`, `select:findCountGrouByEngineeringManager`, `select:findGrouByEngineeringManager`, `select:findListByEngineeringManager`
- tables: `cm_construction_plan`, `cm_construction_plan_item`, `cm_contract_manage`, `cm_light_project`, `cm_light_project_income`, `cm_light_project_income_amount`, `cm_light_project_income_confirm`, `cm_light_project_sign_info`, `cm_payment_milestone_audit`, `cm_receipt_milestone`, `cm_simple_project`, `id`, `light_manual_income`, `light_station`, `light_station_epc`, `light_station_plan_config`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationElecContractOcrMapper.xml
- namespace: `com.rrsjk.light.mapper.LightStationElecContractOcrMapper`
- statements: `select:selectByPrimaryKey`, `insert:insert`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `update:updateByPrimaryKey`, `select:selectAllByStationCode`, `insert:batchInsert`, `select:countOf`, `select:findBy`
- tables: `id`, `light_station_elec_contract_ocr`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightLendRejectRecord.xml
- namespace: `com.rrsjk.light.dao.LightLendRejectRecordDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmPaymentMilestone.xml
- namespace: `com.rrsjk.light.dao.CmPaymentMilestoneDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:getOrderNo`, `delete:deleteByProjectId`, `update:updateSettleStatusByProjectId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpOrderLog.xml
- namespace: `com.rrsjk.light.dao.LightSpOrderLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightVisitInfo.xml
- namespace: `com.rrsjk.light.dao.LightVisitInfoDao`
- statements: `insert:create`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpQuotaLog.xml
- namespace: `com.rrsjk.light.dao.LightSpQuotaLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationOwnerHistoryMapper.xml
- namespace: `com.rrsjk.light.dao.LightStationOwnerHistoryDao`
- statements: `select:get`, `select:findBy`, `update:update`, `select:queryCountBy`, `insert:insert`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/YantuRequestLog.xml
- namespace: `com.rrsjk.light.dao.YantuRequestLogDao`
- statements: `insert:create`, `select:selectById`, `select:selectAll`, `update:update`, `delete:deleteById`
- tables: `id`, `yantu_request_log`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/OperationMaintenanceDetailsHistory.xml
- namespace: `com.rrsjk.light.dao.OperationMaintenanceDetailsHistoryDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:lastData`, `select:findGroup`, `update:updateByOrderNo`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightUnionpayRent.xml
- namespace: `com.rrsjk.light.dao.LightUnionpayRentDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByStationId`, `select:getByStationCode`, `update:updateElecNo`
- tables: `id`, `light_station`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightRentRecord.xml
- namespace: `com.rrsjk.light.dao.LightRentRecordDao`
- statements: `insert:create`, `insert:createList`, `update:update`, `select:get`, `select:getByRecordNo`, `select:findByStationId`, `select:countOf`, `select:findBy`, `update:updateByStationId`, `update:updateElecNo`, `select:countOfBillList`, `select:findBillList`, `select:findAccountRecordList`, `select:countOfAccountRecordList`, `select:findStationList`, `select:countOfStationList`, `select:findAccountRecordByOp`, `select:countOfAccountRecordByOp`
- tables: `id`, `light_electric_order`, `light_rent`, `light_rent_record`, `light_share_bill_record`, `light_sp_staff`, `light_station`, `light_station_yuexiu`, `light_sub_sp`, `light_unionpay_bill_record`, `light_unionpay_rent`, `light_unionpay_rent_record`, `light_yuexiu_income_bill`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightCenterPrice.xml
- namespace: `com.rrsjk.light.dao.LightCenterPriceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightTransferOrderSn.xml
- namespace: `com.rrsjk.light.dao.LightTransferOrderSnDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getBySn`, `delete:deleteByTransferId`, `delete:deleteByApplyId`, `update:batchUpdate`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CapitalDataManagement.xml
- namespace: `com.rrsjk.light.dao.CapitalDataManagementDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `update:del`, `insert:batchInsert`, `select:getById`
- tables: `capital_data_management`, `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightYuexiuIncomeBill.xml
- namespace: `com.rrsjk.light.dao.LightYuexiuIncomeBillDao`
- statements: `select:findBy`, `select:countOf`, `select:findDtoBy`, `select:countDtoOf`, `select:findDtoByPro`, `select:countDtoOfPro`, `select:getMinTimes`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:updateByCfId`, `select:findByDetail`, `select:countOfDetail`, `select:findMissingPeriodsData`, `select:findByPartnersContractNumber`
- tables: `id`, `light_station`, `light_station_bank`, `light_station_yuexiu`, `light_unionpay_rent_record`, `light_yue_xiu_income_bill_exception`, `light_yuexiu_income_bill`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightOverdueListDetail.xml
- namespace: `com.rrsjk.light.dao.LightOverdueListDetailDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationRelateFile.xml
- namespace: `com.rrsjk.light.dao.LightStationRelateFileDao`
- statements: `select:findBy`, `select:findList`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `delete:deleteByStationId`, `select:getById`, `select:getByIds`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightInstantRewardPolicyLog.xml
- namespace: `com.rrsjk.light.dao.LightInstantRewardPolicyLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightAwardAppealItem.xml
- namespace: `com.rrsjk.light.dao.LightAwardAppealItemDao`
- statements: `select:selectByPrimaryKey`, `delete:deleteByPrimaryKey`, `select:get`, `insert:batchInsert`, `select:findByPage`, `delete:deleteByStationCodeAndNo`
- tables: `light_award_appeal_item`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpWithdrawalApplicationVoucher.xml
- namespace: `com.rrsjk.light.dao.LightSpWithdrawalApplicationVoucherDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/DbMonitorRecord.xml
- namespace: `com.rrsjk.light.dao.DbMonitorRecordDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteBeforeToday`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmInvoiceApply.xml
- namespace: `com.rrsjk.light.dao.CmInvoiceApplyDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByApplyCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightCostAccount.xml
- namespace: `com.rrsjk.light.dao.LightCostAccountDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:getByStationId`, `select:getByStationCode`, `select:getByStationIdList`, `update:deleteByStationId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmSignGuaranteeRateReportItem.xml
- namespace: `com.rrsjk.light.dao.CmSignGuaranteeRateReportItemDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteByDate`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationEnableReward.xml
- namespace: `com.rrsjk.light.dao.LightStationEnableRewardDao`
- statements: `select:findBy`, `select:findOneBy`, `select:countOf`, `insert:create`, `update:update`, `update:removeCostVoucher`, `insert:batchInsert`, `select:getById`, `select:findByNotConfirm`, `select:findCompleteByNotConfirm`, `select:findEnableByNotConfirm`, `select:findCompleteByNotConfirmAndStationCode`, `select:findCompleteByNotConfirmByStationCode`, `select:findCompleteByNotCostVoucherByStationCode`, `select:findEnableByNotCostVoucherByStationCode`, `select:findEnableByNotConfirmByStationCode`, `select:findPricePolicyByNotConfirm`, `select:findPricePolicyByNotConfirmByStationCode`, `select:getByOrderNo`, `select:findStationCodeList`, `select:findByPageOrder`, `select:findStationEnableRewardByStationCodeList`
- tables: `id`, `light_station`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightOpAuthorityZone.xml
- namespace: `com.rrsjk.light.dao.LightOpAuthorityZoneDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:findByOpId`, `select:findSpByCityIds`, `select:findByStatus`, `insert:batchInsert`, `select:findByOpContractId`, `select:findByRegionIds`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightPurchasePre.xml
- namespace: `com.rrsjk.light.dao.LightPurchasePreDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `update:batchUpdateStatus`, `select:get`, `select:countOf`, `select:findBy`, `select:findByPurchaseOrderId`, `select:getLastByPurchaseOrderId`, `select:getByRelateNo`, `select:findByPreOrderId`, `select:findByIds`, `select:findRelateNoIsNull`
- tables: `id`, `light_sp_share_quota`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightEamYearBudget.xml
- namespace: `com.rrsjk.light.dao.LightEamYearBudgetDao`
- statements: `update:update`, `insert:create`, `insert:batchInsert`, `select:findBy`, `select:countOf`, `delete:deleteByYear`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpStaffSubRelation.xml
- namespace: `com.rrsjk.light.dao.LightSpStaffSubRelationDao`
- statements: `select:findBy`, `insert:create`, `insert:batchInsert`, `delete:deleteByStaffId`
- tables: `light_sp_staff_sub_relation`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightLendOutRecord.xml
- namespace: `com.rrsjk.light.dao.LightLendOutRecordDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getBySourceNo`
- tables: `id`, `light_lend`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpShareQuota.xml
- namespace: `com.rrsjk.light.dao.LightSpShareQuotaDao`
- statements: `insert:create`, `update:update`, `update:batchUpdateStatus`, `select:get`, `select:findList`, `select:findCount`, `select:findEnableBySubSpId`, `select:findBySubSpId`, `select:findBySubSpIdInRelease`, `select:findEnableByHeadSpId`, `select:findByHeadSpId`, `select:findByOrderNo`
- tables: `id`, `light_sp_share_quota`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/ChannelYuexiuProductRegion.xml
- namespace: `com.rrsjk.light.dao.ChannelYuexiuProductRegionDao`
- statements: `insert:create`, `update:update`, `select:queryOne`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationRelateFileTemp.xml
- namespace: `com.rrsjk.light.dao.LightStationRelateFileTempDao`
- statements: `select:findBy`, `select:findList`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `delete:deleteByStationId`, `select:getById`, `select:findByStationId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/PyInvoiceLog.xml
- namespace: `com.rrsjk.light.dao.PyInvoiceLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`, `py_invoice_log`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightEnablePolicyNodeProp.xml
- namespace: `com.rrsjk.light.dao.LightEnablePolicyNodePropDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteByPolicyId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightFapRecord.xml
- namespace: `com.rrsjk.light.dao.LightFapRecordDao`
- statements: `select:findBy`, `select:findByPrams`, `select:countOf`, `insert:create`, `update:update`, `update:updateByOrderNo`, `insert:batchInsert`, `select:getById`, `select:getByFapOrderNo`, `select:getByOrderNo`, `select:getByOrderNoAndBizType`, `select:queryVppFapRecordByOrderNo`, `select:findSentForFapQuery`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightMakeOrderCbs.xml
- namespace: `com.rrsjk.light.dao.LightMakeOrderCbsDao`
- statements: `select:countOf`, `select:findBy`, `select:countAllOf`, `select:findAllBy`, `select:countOfAuxiliary`, `select:findAuxiliaryBy`
- tables: `light_make_order`, `light_station`, `light_sub_sp`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightZhIncomePrice.xml
- namespace: `com.rrsjk.light.dao.LightZhIncomePriceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightShareBillPayFailRecord.xml
- namespace: `com.rrsjk.light.dao.LightShareBillPayFailRecordDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmPreOrderVt.xml
- namespace: `com.rrsjk.light.dao.CmPreOrderVtDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationModuleAngleOcrMapper.xml
- namespace: `com.rrsjk.light.mapper.LightStationModuleAngleOcrMapper`
- statements: `select:selectByPrimaryKey`, `insert:insert`, `insert:insertSelective`, `update:updateByIdSelective`, `update:updateById`, `insert:batchInsert`, `select:selectLatest`
- tables: `id`, `light_station_module_angle_ocr`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationWhiteList.xml
- namespace: `com.rrsjk.light.dao.LightStationWhiteListDao`
- statements: `select:findBy`, `select:findSave`, `select:findByParams`, `select:findByOrderNoNotNull`, `select:findByStationCode`, `select:countOf`, `insert:create`, `update:updateSave`, `insert:saveMaster`, `insert:saveThree`, `update:update`, `update:updateByOrderNo`, `update:updateByStationCode`, `insert:batchInsert`, `select:getById`, `select:getByStationCode`, `select:getByOrderNo`, `select:existByBatchNo`, `update:updateWhiteListOrderStatus`, `update:updateWhiteListOrderStatusAndClearOrderNo`
- tables: `id`, `light_station`, `light_station_white_list`, `save_file`, `save_file_three`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightUnionpayRentRecord.xml
- namespace: `com.rrsjk.light.dao.LightUnionpayRentRecordDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByStationIdAndRentDate`, `select:getByStationId`, `select:getByStationCode`, `select:findByStationCodeAndRentDateNoNotNeedPay`, `select:findByElecNoAndRentDate`, `update:updateCollectAtByOrderId`, `update:updatePayAtByOrderIdAndStationCode`, `select:findByUnionpayWaitPay`, `select:findByShareWaitPay`, `select:findByOffLineWaitPay`, `select:findByOffLineWaitPayNoContract`, `select:findByShareCantWaitPayWithOther`, `select:getByOrderNo`, `update:cancelRentByStationId`, `update:cancelRentByRecordId`, `update:updateElecNo`, `update:batchNullOrderId`, `update:batchNullOrderIdByStationCodes`, `delete:deleteById`, `update:updateStatusAndPayStatus`, `update:batchStatusAndRemarkByIds`
- tables: `id`, `light_project_owner_account`, `light_station_bank`, `light_station_contract_record`, `share_project_payment_account`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightElecContractSkuRelation.xml
- namespace: `com.rrsjk.light.dao.LightElecContractSkuRelationDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByParams`, `update:deleteByContractIdList`, `insert:batchInsert`
- tables: `id`, `light_elec_contract_sku_relation`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpUnionpayRent.xml
- namespace: `com.rrsjk.light.dao.LightSpUnionpayRentDao`
- statements: `select:findBy`, `select:findByStationCode`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findWaitCostByStationCode`, `select:findNoVoucher`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightOpContractConfig.xml
- namespace: `com.rrsjk.light.dao.LightOpContractConfigDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByContractNo`, `select:findByOpContractId`, `select:findByConfigAndContract`
- tables: `id`, `light_elec_contract`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightPurchaseAppeals.xml
- namespace: `com.rrsjk.light.dao.LightPurchaseAppealsDao`
- statements: `select:countOf`, `select:findBy`, `insert:create`, `update:update`, `select:get`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightLendSapQueue.xml
- namespace: `com.rrsjk.light.dao.LightLendSapQueueDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightZhSettleSum.xml
- namespace: `com.rrsjk.light.dao.LightZhSettleSumDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CapitalDataContract.xml
- namespace: `com.rrsjk.light.dao.CapitalDataContractDao`
- statements: `select:findBy`, `select:getByRelationId`, `select:countOf`, `insert:create`, `update:update`, `update:isDel`, `insert:batchInsert`, `select:getById`
- tables: `capital_data_contract`, `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/RentSuspendApplication.xml
- namespace: `com.rrsjk.light.dao.RentSuspendApplicationDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findBy`, `select:countOf`, `insert:batchInsert`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/ChannelYuexiuProduct.xml
- namespace: `com.rrsjk.light.dao.ChannelYuexiuProductDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByProvinceId`, `select:getByProductCode`, `select:countOf`, `select:findBy`, `select:queryOne`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpQuotaDedicatedLog.xml
- namespace: `com.rrsjk.light.dao.LightSpQuotaDedicatedLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationInfoUpdateAuditLog.xml
- namespace: `com.rrsjk.light.dao.LightStationInfoUpdateAuditLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `select:getById`, `select:getByUpdateId`
- tables: `id`, `light_station_info_update_audit_log`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/PvPowerConstantDao.xml
- namespace: `com.rrsjk.light.dao.PvPowerConstantDao`
- statements: `select:selectByStationCode`, `insert:insert`, `update:updateById`, `insert:batchInsert`, `select:findBy`, `select:countOf`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightProjectElectricOrderChange.xml
- namespace: `com.rrsjk.light.dao.LightProjectElectricOrderChangeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/WholeVillageTogether.xml
- namespace: `com.rrsjk.light.dao.WholeVillageTogetherDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:delLogic`
- tables: `id`, `light_sp_staff`, `light_sub_sp`, `whole_village_together_detail`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmLightUse.xml
- namespace: `com.rrsjk.light.dao.CmLightUseDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationEnableRewardVerify.xml
- namespace: `com.rrsjk.light.dao.LightStationEnableRewardVerifyDao`
- statements: `select:getDealData`, `update:update`, `select:getByStationCode`, `insert:create`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightFreezeAuditSerialMapper.xml
- namespace: `com.rrsjk.light.mapper.LightFreezeAuditSerialMapper`
- statements: `select:selectByPrimaryKey`, `insert:insert`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `update:updateByPrimaryKey`, `select:findByPage`, `select:countOf`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpInstallAwardPolicy.xml
- namespace: `com.rrsjk.light.dao.LightSpInstallAwardPolicyDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:findBy`, `select:queryByPolicyCode`, `select:countOf`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmLightProjectSummary.xml
- namespace: `com.rrsjk.light.dao.CmLightProjectSummaryDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightGroovyScript.xml
- namespace: `com.rrsjk.light.dao.LightGroovyScriptDao`
- statements: `select:findBy`, `select:findOne`, `select:countByType`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpAudit.xml
- namespace: `com.rrsjk.light.dao.LightSpAuditDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:getByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpAuclonStoreChangeLog.xml
- namespace: `com.rrsjk.light.dao.LightSpAuclonStoreChangeLogDao`
- statements: `insert:create`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmDataSync.xml
- namespace: `com.rrsjk.light.dao.CmDataSyncDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightElecContractLog.xml
- namespace: `com.rrsjk.light.dao.LightElecContractLogDao`
- statements: `insert:create`, `update:update`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightNewMerchantReward.xml
- namespace: `com.rrsjk.light.dao.LightNewMerchantRewardDao`
- statements: `select:countOf`, `select:findBy`, `select:findByNotConfirmByIds`, `insert:create`, `update:update`, `select:findByNotConfirm`, `select:getById`, `select:getByOrderNo`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightProjectRentConfirmQueue.xml
- namespace: `com.rrsjk.light.dao.LightProjectRentConfirmQueueDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightPreOrderRelatePurchase.xml
- namespace: `com.rrsjk.light.dao.LightPreOrderRelatePurchaseDao`
- statements: `select:countOf`, `select:findBy`
- tables: `light_purchase_pre`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationPlanDesignChangeDetail.xml
- namespace: `com.rrsjk.light.dao.LightStationPlanDesignChangeDetailDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `update:batchUpdateStatusToDisableByChangeId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationPlanChangeDetail.xml
- namespace: `com.rrsjk.light.dao.LightStationPlanChangeDetailDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:findEnableByChangeId`, `update:batchUpdateStatusToDisableByChangeId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightNewMerchantRewardQueue.xml
- namespace: `com.rrsjk.light.dao.LightNewMerchantRewardQueueDao`
- statements: `select:findBy`, `insert:create`, `update:update`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationZhRulesSend.xml
- namespace: `com.rrsjk.light.dao.LightStationZhRulesSendDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationYuexiuYb.xml
- namespace: `com.rrsjk.light.dao.LightStationYuexiuYbDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByParam`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/OffLineStationFlow.xml
- namespace: `com.rrsjk.light.dao.OffLineStationFlowDao`
- statements: `select:countOf`, `select:countOfMerchant`, `select:queryPageOffLine`, `select:queryMerchantPageOffLine`
- tables: `light_sp_staff`, `light_station`, `light_station_audit`, `light_station_plan_config`, `light_sub_sp`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightCoin.xml
- namespace: `com.rrsjk.light.dao.LightCoinDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByStationId`, `select:getByStationCode`, `select:findByPhoneAndStatus`, `select:findByPhone`, `select:findByAllowConsume`, `select:countOf`, `select:findBy`, `update:consume`, `update:returned`, `select:findByAllowReverseCost`, `update:reverseCost`, `select:findByExpireCost`, `select:getByCoinNo`, `select:findByExpireBeforeSms`, `select:incomeDaySum`, `update:updateIncomeDaySum`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightOverdueBlackListAuditLog.xml
- namespace: `com.rrsjk.light.dao.LightOverdueBlackListAuditLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmStock.xml
- namespace: `com.rrsjk.light.dao.CmStockDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationYuexiuExchange.xml
- namespace: `com.rrsjk.light.dao.LightStationYuexiuExchangeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByStationCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightManualIncome.xml
- namespace: `com.rrsjk.light.dao.LightManualIncomeDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationConfirmImg.xml
- namespace: `com.rrsjk.light.dao.LightStationConfirmImgDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `update:markReject`, `update:clearRejectByAuditType`, `update:clearRejectById`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:findSimpleByParams`, `update:delete`, `update:deleteByStationCode`, `update:updateStationIdToMinus`, `update:updateConfirmImgToNull`, `update:updateCompleteImgToNull`, `update:deleteByTypeAndSortNum`, `update:deleteByType`, `update:deleteByTypeAndStationCode`, `select:getByImaNameAndType`, `select:getByImaNameAndTypeAndStationCode`, `select:getByImaNameAndStationCode`, `select:getByImgNameAndStationCodes`, `select:getListByImaNameAndType`, `select:getListByImaNameAndTypeAndStationCode`, `select:findByStationCodeAndTypeNoFilter`, `select:getGsyAppStationImg`, `select:findByStationIdAndTypeNoFilter`, `select:getByIds`, `select:getByStationCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSubSp.xml
- namespace: `com.rrsjk.light.dao.LightSubSpDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByMemberId`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:getByMobile`, `select:getChildren`, `select:findSubMemberIdByMobile`, `select:findSubMemberIdByMemberId`, `select:isOnlySelf`, `select:findByServiceProvider`, `select:queryCountByServiceProvider`, `select:findByName`, `select:getSubSpByAncestorSubMember`, `select:getSubSpsByAncestorSubMembers`, `select:getSubSpsByAncestorSubMembers`
- tables: `id`, `light_service_provider`, `light_sp_staff`, `light_sub_sp`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmReceiptMilestoneCheck.xml
- namespace: `com.rrsjk.light.dao.CmReceiptMilestoneCheckDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/OperationMaintenanceTask.xml
- namespace: `com.rrsjk.light.dao.OperationMaintenanceTaskDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightProjectOwnerAccount.xml
- namespace: `com.rrsjk.light.dao.LightProjectOwnerAccountDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByIdCardAndProjectCompanyCode`, `select:findByAllIdCardAndAllProjectCompanyCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmProjectStatusMove.xml
- namespace: `com.rrsjk.light.dao.CmProjectStatusMoveDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightGreenIncome.xml
- namespace: `com.rrsjk.light.dao.LightGreenIncomeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpInspireLog.xml
- namespace: `com.rrsjk.light.dao.LightSpInspireLogDao`
- statements: `insert:create`, `select:findBy`, `select:countOf`, `insert:batchInsert`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightCalculateIncome.xml
- namespace: `com.rrsjk.light.dao.LightCalculateIncomeDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationPolicyIncomeDetail.xml
- namespace: `com.rrsjk.light.dao.LightStationPolicyIncomeDetailDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findSuccessByTimeAndType`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpPlanConfig.xml
- namespace: `com.rrsjk.light.dao.LightSpPlanConfigDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmProductionValue.xml
- namespace: `com.rrsjk.light.dao.CmProductionValueDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByOrderNo`, `select:findGroupByProjectCode`, `select:countOfGroupByProjectCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightConstructionTeam.xml
- namespace: `com.rrsjk.light.dao.LightConstructionTeamDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:findByMobile`, `select:findByMemberId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightInstantRewardItem.xml
- namespace: `com.rrsjk.light.dao.LightInstantRewardItemDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByRewardId`, `select:countOfToTarget`
- tables: `id`, `light_instant_reward_item`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpOpGroupSumLog.xml
- namespace: `com.rrsjk.light.dao.LightSpOpGroupSumLogDao`
- statements: `insert:create`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSapLog.xml
- namespace: `com.rrsjk.light.dao.LightSapLogDao`
- statements: `insert:create`, `update:update`, `select:get`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/ZhaoYinTradeIncomeSettle.xml
- namespace: `com.rrsjk.light.dao.ZhaoYinTradeIncomeSettleDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:updateByBatchNo`, `delete:deleteByBatchNo`, `select:existsByStationCode`, `select:findActiveStationCodes`, `select:getLatestByStationCode`, `select:getLatestIncomeTime`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightEpcSpQuarterTarget.xml
- namespace: `com.rrsjk.light.dao.LightEpcSpQuarterTargetDao`
- statements: `insert:create`, `update:update`, `insert:batchInsert`, `select:findBySpId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightServiceProviderAuditType.xml
- namespace: `com.rrsjk.light.dao.LightServiceProviderAuditTypeDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:getBySpIdAndType`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightCapitalCompanyInfo.xml
- namespace: `com.rrsjk.light.dao.LightCapitalCompanyInfoDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightCoinRecord.xml
- namespace: `com.rrsjk.light.dao.LightCoinRecordDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByRecordNo`, `select:findByStationId`, `select:findByRecordNoAndRecordType`, `select:countOf`, `select:findBy`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationNanny.xml
- namespace: `com.rrsjk.light.dao.LightStationNannyDao`
- statements: `insert:create`, `update:update`, `update:updateProviderByIds`, `select:findBy`, `select:countOf`, `select:getById`, `select:getByPhone`, `select:getByMemberId`, `select:getByPhoneAndIsImport`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmPayment.xml
- namespace: `com.rrsjk.light.dao.CmPaymentDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSendAppliance.xml
- namespace: `com.rrsjk.light.dao.LightSendApplianceDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightProjectElectricOrder.xml
- namespace: `com.rrsjk.light.dao.LightProjectElectricOrderDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByIds`, `select:getByOrderNo`, `select:getByElecNoAndMonthAt`, `select:getByElecNoAndMonthAtAndCustomerName`, `select:listByElecNoAndMonthRange`, `select:countByElecNoAndMonthRange`, `select:countByElecNoAndCustomerAndMonthRange`, `select:countOf`, `select:checkIdsWaitOrWaitConfirm`, `update:batchDelete`, `select:findBy`, `select:findByYx`, `select:findStationBy`, `select:countOfYx`, `select:countStationBy`, `select:countByBatchNoAndInvoiceNoNoTargetId`, `update:updateVoiceStatusByIds`, `select:findByWithTemplate`, `select:countOfWithTemplate`, `update:batchUpdateStatus`, `select:findJinDieA02Orders`, `select:findJinDieH01Orders`, `select:getByOrderNoIncludeDeleted`
- tables: `id`, `light_capital_company_info`, `light_company_info`, `light_invoice_template`, `light_project_electric_order`, `light_project_electric_order_owner`, `light_station`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightServiceProvider.xml
- namespace: `com.rrsjk.light.dao.LightServiceProviderDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:getByIdForUpdate`, `select:getByMemberId`, `select:getByMobile`, `select:getByName`, `select:queryListBy`, `select:queryCountBy`, `select:queryAuxiliaryQuotaAuditListBy`, `select:queryAuxiliaryQuotaAuditCountBy`, `select:findByParams`, `update:addDeposit`, `update:substractDeposit`, `update:addAuxiliaryDepositBalance`, `update:substractAuxiliaryDepositBalance`, `update:addAuxiliaryDepositAmount`, `update:addAuxiliaryDepositFreezeAmount`, `update:substractAuxiliaryDepositFreezeAmount`, `update:addAuxiliaryDepositSignedAmount`, `update:substractAuxiliaryDepositSignedAmount`, `update:addAuxiliaryDepositWrittenOffAmount`, `update:substractAuxiliaryDepositWrittenOffAmount`, `update:addAuxiliaryDepositPendingWrittenOffAmount`, `update:substractAuxiliaryDepositPendingWrittenOffAmount`, `select:isAuxiliaryDepositOpened`, `select:findLastBySpCode`, `select:findAuthRegionSum`, `select:findCountyCenterSum`, `select:findEffectiveProviders`, `select:getEpcByMemberId`, `select:checkRegisterByMemberId`, `select:epcCheckRegisterByMemberId`, `select:findHouseByNameLike`
- tables: `id`, `light_service_provider`, `light_service_provider_audit_type`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationBackPolicyChange.xml
- namespace: `com.rrsjk.light.dao.LightStationBackPolicyChangeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightOperationDeposit.xml
- namespace: `com.rrsjk.light.dao.LightOperationDepositDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByMemberId`, `select:getByDepositNo`, `select:countOf`, `select:sumPay`, `select:findBy`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/OperationMaintenance.xml
- namespace: `com.rrsjk.light.dao.OperationMaintenanceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByOrderNo`, `select:findHistory`, `select:findByCodeIsNull`, `select:findJob`, `update:updateHistory`, `update:updateHistoryStatus`, `update:updateByProjectCompanyCodeStatus`, `select:findHistoryDetails`, `update:updateHandleStatus`, `update:updateByOrderNo`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/PvpPeakValleyElectricityPriceHistory.xml
- namespace: `com.rrsjk.light.dao.PvpPeakValleyElectricityPriceHistoryDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByMonth`, `update:updateByRelationId`, `select:findByRelationId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightAwardAppeal.xml
- namespace: `com.rrsjk.light.dao.LightAwardAppealDao`
- statements: `select:selectByPrimaryKey`, `delete:deleteByPrimaryKey`, `insert:create`, `update:update`, `update:updateByPrimaryKey`, `select:findByPage`, `select:findByPageCount`, `select:get`, `select:findDealBill`, `select:getValidOrder`
- tables: `id`, `light_award_appeal`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmLightProjectIncomePolicyItem.xml
- namespace: `com.rrsjk.light.dao.CmLightProjectIncomePolicyItemDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:deleteByPolicyId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightAuxiliaryMakeOrderOperatorLog.xml
- namespace: `com.rrsjk.light.dao.LightAuxiliaryMakeOrderOperateLogDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByParams`, `select:countOf`, `select:findByOrderNo`, `select:getSubCenterAudit`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/YantuFactoryArea.xml
- namespace: `com.rrsjk.light.dao.YantuFactoryAreaDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:updateByRelationId`, `select:findByRelationId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/IncomeOrder.xml
- namespace: `com.rrsjk.light.dao.IncomeOrderDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmStore.xml
- namespace: `com.rrsjk.light.dao.CmStoreDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationIncomeReverseLog.xml
- namespace: `com.rrsjk.light.dao.LightStationIncomeReverseLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByRelationId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/PyNetPrice.xml
- namespace: `com.rrsjk.light.dao.PyNetPriceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByStationCode`, `select:getAllOf`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmLightProjectIncomeRecord.xml
- namespace: `com.rrsjk.light.dao.CmLightProjectIncomeRecordDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationOtherMaterialPolicy.xml
- namespace: `com.rrsjk.light.dao.LightStationOtherMaterialPolicyDao`
- statements: `insert:create`, `update:update`, `update:delete`, `select:getById`, `select:getByBatchNo`, `select:getLatestEffectiveByRegion`, `select:getLatestEffectiveByRegionAndTime`, `select:list`, `select:findBy`, `select:countOf`
- tables: `id`, `light_station_other_material_policy`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightProjectElectricOrderOwnerQueue.xml
- namespace: `com.rrsjk.light.dao.LightProjectElectricOrderOwnerQueueDao`
- statements: `insert:batchInsert`, `insert:create`, `select:findBy`, `select:countOf`, `select:findDeal`, `update:update`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/GsyStationInvestorRelation.xml
- namespace: `com.rrsjk.light.dao.GsyStationInvestorRelationDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByMemberId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightEpcSpInfo.xml
- namespace: `com.rrsjk.light.dao.LightEpcSpInfoDao`
- statements: `insert:create`, `update:update`, `select:findBySpId`
- tables: `id`, `light_epc_sp_info`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmLightProjectNodeRecord.xml
- namespace: `com.rrsjk.light.dao.CmLightProjectNodeRecordDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByProjectId`, `select:getLastOneByMap`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/YuexiuElectricityBillCopy.xml
- namespace: `com.rrsjk.light.dao.YuexiuElectricityBillCopyDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByBillId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightProjectOperateLog.xml
- namespace: `com.rrsjk.light.dao.LightProjectOperateLogDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightWorkOrder.xml
- namespace: `com.rrsjk.light.dao.LightWorkOrderDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationYuexiuAccount.xml
- namespace: `com.rrsjk.light.dao.LightStationYuexiuAccountDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByIdCardNumber`, `select:getVirtueByIdCardNumber`, `select:getByPhone`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmGrossMarginChangeAudit.xml
- namespace: `com.rrsjk.light.dao.CmGrossMarginChangeAuditDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSubTransferOrder.xml
- namespace: `com.rrsjk.light.dao.LightSubTransferOrderDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmReceiptMilestone.xml
- namespace: `com.rrsjk.light.dao.CmReceiptMilestoneDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `delete:deleteByProjectId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightUnionpayBillRecord.xml
- namespace: `com.rrsjk.light.dao.LightUnionpayBillRecordDao`
- statements: `select:findBy`, `select:countOf`, `select:findByUnionAndShare`, `select:countOfUnionAndShare`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByOrderNo`, `select:findDtoByPage`, `select:countOfDto`, `select:findByDetail`, `select:countOfDetail`, `select:findDtoByPageInCmb`, `select:countOfDtoInCmb`
- tables: `cmb_leasing_station`, `id`, `light_share_bill_record`, `light_station`, `light_station_plan_config`, `light_unionpay_bill_record`, `light_unionpay_rent`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationPlanConfig.xml
- namespace: `com.rrsjk.light.dao.LightStationPlanConfigDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `update:disabledByPlanDesignId`, `select:getById`, `select:queryListBy`, `select:queryMajorListBy`, `select:queryCountBy`, `select:queryMajorCountBy`, `select:findByParams`, `select:findMajorByParams`, `select:findMajorPlanConfigSimpleInfo`, `select:findGroupBySku`, `select:findMajorGroupByStationIdAndSku`, `select:findAuxiliaryGroupBySku`, `select:sumMoreNumberBySpSku`, `select:sumLittleNumberBySpSku`, `select:sumPlanNumberBySpSkuMake`, `select:sumPlanNumberByEnableMake`, `select:sumPlanNumberByEnableMakeAuxiliary`, `select:findAllByStationIds`, `select:findStationPower`, `select:findBuildStationPower`, `select:findFinishedPowerByStationId`, `select:queryModuleOneByStationId`, `delete:deleteByStationIdAndConfigType`, `select:findDraftSku`, `select:findModulePlanConfigSimpleInfo`, `select:findModulePlanConfigDraftInfo`
- tables: `id`, `light_station`, `light_station_plan_config`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStockTakingVarianceAnalysis.xml
- namespace: `com.rrsjk.light.dao.LightStockTakingVarianceAnalysisDao`
- statements: `insert:create`, `update:update`, `insert:batchInsert`, `select:get`, `select:getByTakingId`, `select:getByDetailId`, `delete:deleteByTakingIdAndSkuCode`, `select:countOf`, `select:findBy`, `select:sumAnalysisNumber`, `select:sumBeUsedNumber`, `select:getAllAnalysisReason`
- tables: `id`, `light_stock_taking_variance_analysis`, `rrsjk_light.light_stock_taking`, `rrsjk_light.light_stock_taking_variance_analysis`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationRepurchase.xml
- namespace: `com.rrsjk.light.dao.LightStationRepurchaseDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:updateInvoiceInfo`, `select:findApplySettleListToPay`, `select:findActiveRepurchaseStationCodes`
- tables: `id`, `light_station_repurchase`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightProjectElectricOrderInvoice.xml
- namespace: `com.rrsjk.light.dao.LightProjectElectricOrderInvoiceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightOpOrderInvoice.xml
- namespace: `com.rrsjk.light.dao.LightOpOrderInvoiceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByOrderId`, `delete:deleteByOrderId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationYuexiu.xml
- namespace: `com.rrsjk.light.dao.LightStationYuexiuDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:countOfPro`, `select:findBy`, `select:findByPro`, `select:getByStationId`, `select:findByWaitFarmerSignStatus`, `select:findByWaitPushProject`, `select:findByWaitPushPrjSign`, `select:cancelLease`, `select:findByWaitProjectStatus`, `select:findByWaitContractTextStatus`, `select:findByWaitContractTextStatusAttach`, `select:findByWaitContractStatusUrgent`, `select:findByWaitContractStatusReset`, `select:findByWaitPaymentStatus`, `select:findByBusinessKey`, `select:findBySignedContractTextStatus`, `select:findByMasterContractTextStatus`, `select:findPageBySignedContractTextStatus`, `select:findCountBySignedContractTextStatus`, `select:queryReUpdateContractStation`, `select:getByOwnerIdCard`
- tables: `id`, `light_station`, `light_station_audit`, `light_station_contract_record`, `light_station_yuexiu`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationEnableRewardCache.xml
- namespace: `com.rrsjk.light.dao.LightStationEnableRewardCacheDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightZhSettle.xml
- namespace: `com.rrsjk.light.dao.LightZhSettleDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `update:updateZhSettleForReverse`, `update:updateZhSettleForReIncome`, `insert:batchInsert`, `update:batchUpdate`, `select:getById`, `select:getByStationCode`, `update:batchUpdateInfoForReverse`, `select:findNeedReverseList`, `delete:deleteByBatchNo`, `select:existsByStationCode`, `select:findActiveStationCodes`, `select:getLatestIncomeTime`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightGridAwardPolicyLog.xml
- namespace: `com.rrsjk.light.dao.LightGridAwardPolicyLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/TaxAmountCalculateSourceDataTemp.xml
- namespace: `com.rrsjk.light.dao.TaxAmountCalculateSourceDataTempDao`
- statements: `delete:truncate`, `insert:insertFromLightShareBillRecord`, `insert:insertFromLightShareBillRecordStrict`, `select:findBy`, `select:countOf`, `select:findDistinctCompanyCodes`, `select:findByCompanyCode`
- tables: `light_share_bill_record`, `rrsjk_light.tax_amount_calculate_source_data_temp`, `tax_amount_calculate_source_data_temp`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationBaiduAILogMapper.xml
- namespace: `com.rrsjk.light.mapper.LightStationBaiduAILogMapper`
- statements: `select:selectByPrimaryKey`, `insert:insert`, `insert:insertSelective`, `update:updateByIdOrImageIdSelective`, `update:updateByPrimaryKey`, `select:findAllByImageIdAndId`
- tables: `id`, `light_station_baiduAI_log`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/ReportMGridGoal.xml
- namespace: `com.rrsjk.light.dao.ReportMGridGoalDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightPolicyIntervention.xml
- namespace: `com.rrsjk.light.dao.LightPolicyInterventionDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStockTakingOperateLog.xml
- namespace: `com.rrsjk.light.dao.LightStockTakingOperateLogDao`
- statements: `insert:create`, `select:get`
- tables: `rrsjk_light.light_stock_taking_operate_log`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/YantuAutomaticallyDesignTemporaryStorage.xml
- namespace: `com.rrsjk.light.dao.YantuAutomaticallyDesignTemporaryStorageDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByHds`, `select:countOfHds`
- tables: `id`, `light_service_provider`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightPlanDetail.xml
- namespace: `com.rrsjk.light.dao.LightPlanDetailDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightOpContractRecord.xml
- namespace: `com.rrsjk.light.dao.LightOpContractRecordDao`
- statements: `select:findBy`, `select:findByParams`, `select:getByContractNo`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByOpId`, `select:findByHds`, `select:countOfHds`
- tables: `id`, `light_elec_contract`, `light_op_contract_config`, `light_op_contract_record`, `light_operation_provider`, `rrsjk_light_operation.light_zero_carbon_operation_provider`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightPreOrder.xml
- namespace: `com.rrsjk.light.dao.LightPreOrderDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByPreOrderNo`, `select:countOf`, `select:findBy`, `select:findWaitMakeBySkuCode`, `update:addDeliverNumber`, `update:addInStoreNumber`, `select:findPreAndPurchaseOrderBy`, `select:countPreAndPurchaseOrderOf`, `select:findByHistoryData`
- tables: `id`, `light_purchase_order`, `light_purchase_pre`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightWvRentRecord.xml
- namespace: `com.rrsjk.light.dao.LightWvRentRecordDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByStationIdAndRentDate`, `select:findByElecNoAndRentDate`, `update:updatePayAtByOrderIdAndStationCode`, `update:updateCollectAtByOrderId`, `update:batchNullOrderId`, `update:updateElecNo`, `update:batchNullOrderIdByStationCodes`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CancelLeaseYxStation.xml
- namespace: `com.rrsjk.light.dao.CancelLeaseYxStationDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationInfoUpdateLog.xml
- namespace: `com.rrsjk.light.dao.LightStationInfoUpdateLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:updatePassByUpdateId`
- tables: `id`, `light_station`, `light_station_info_update_log`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightEnablePolicy.xml
- namespace: `com.rrsjk.light.dao.LightEnablePolicyDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByTimeCoincide`, `select:countToConfirmed`, `select:findToConfirmed`, `select:findByPolicyIds`, `delete:deleteById`
- tables: `id`, `light_enable_policy`, `light_enable_policy_area`, `light_enable_policy_sp`, `light_service_provider`, `light_sp_authority_zone`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightZhSettleQueue.xml
- namespace: `com.rrsjk.light.dao.LightZhSettleQueueDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:updateByStationCode`, `delete:deleteByStationCodeList`, `select:findByStationCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightWorkOrderOperatorLog.xml
- namespace: `com.rrsjk.light.dao.LightWorkOrderOperateLogDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpOrderSn.xml
- namespace: `com.rrsjk.light.dao.LightSpOrderSnDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteByOrderId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightWvRentQueue.xml
- namespace: `com.rrsjk.light.dao.LightWvRentQueueDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByStationId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightOcrXlsMapper.xml
- namespace: `com.rrsjk.light.mapper.LightOcrXlsMapper`
- statements: `select:selectByPrimaryKey`, `insert:insert`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `update:updateByPrimaryKey`, `select:findByPage`, `select:findMasterContract`, `select:findMasterContractOwner`, `update:updateBatchById`
- tables: `id`, `light_elec_contract`, `light_ocr_xls`, `light_station_contract_record`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationImageDownload.xml
- namespace: `com.rrsjk.light.dao.LightStationImageDownloadDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightProjectOwnerAccountQueue.xml
- namespace: `com.rrsjk.light.dao.LightProjectOwnerAccountQueueDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightEnablePolicySpPropLog.xml
- namespace: `com.rrsjk.light.dao.LightEnablePolicySpPropLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightInstantGridRewardPolicy.xml
- namespace: `com.rrsjk.light.dao.LightInstantGridRewardPolicyDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:checkCompleteAt`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightNegativeReducePolicy.xml
- namespace: `com.rrsjk.light.dao.LightNegativeReducePolicyDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByTimeAndStatus`, `select:countByStartTimeAndEndTime`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationNew.xml
- namespace: `com.rrsjk.light.dao.LightStationNewDao`
- statements: `select:getByStationCode`, `update:update`, `update:updateByCode`
- tables: `id`, `light_station`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightProjectRentQueue.xml
- namespace: `com.rrsjk.light.dao.LightProjectRentQueueDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByStationId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmStockChange.xml
- namespace: `com.rrsjk.light.dao.CmStockChangeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/ReportMWholeCounty.xml
- namespace: `com.rrsjk.light.dao.ReportMWholeCountyDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightOverdueListDetailRejectOther.xml
- namespace: `com.rrsjk.light.dao.LightOverdueListDetailRejectOtherDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`, `light_overdue_list_detail`, `light_overdue_list_detail_reject_other`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationCompleteImg.xml
- namespace: `com.rrsjk.light.dao.LightStationCompleteImgDao`
- statements: `insert:create`, `insert:batchInsert`, `select:getByImaNameAndType`, `update:update`, `select:getById`, `select:getByStationId`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `delete:delete`, `delete:deleteByTypeAndStationId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightEnablePolicyItem.xml
- namespace: `com.rrsjk.light.dao.LightEnablePolicyItemDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByPolicyId`, `select:getByUnionKey`, `delete:deleteByPolicyId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationAuditImg.xml
- namespace: `com.rrsjk.light.dao.LightStationAuditImgDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightInstantGridRewardPolicyLog.xml
- namespace: `com.rrsjk.light.dao.LightInstantGridRewardPolicyLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightForward.xml
- namespace: `com.rrsjk.light.dao.LightForwardDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `city`, `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpOpsNegativeIac.xml
- namespace: `com.rrsjk.light.dao.LightSpOpsNegativeIacDao`
- statements: `select:findBy`, `select:findDtoBy`, `select:findList`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:countOfSettle`, `select:findBySettle`
- tables: `id`, `light_sp_ops_settle_iac`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationEnableRewardCacheItem.xml
- namespace: `com.rrsjk.light.dao.LightStationEnableRewardCacheItemDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationSettleSumQueue.xml
- namespace: `com.rrsjk.light.dao.LightStationSettleSumQueueDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/RegionAuditRecord.xml
- namespace: `com.rrsjk.light.dao.RegionAuditRecordDao`
- statements: `select:findBy`, `select:findByIds`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpGridAwardOrder.xml
- namespace: `com.rrsjk.light.dao.LightSpGridAwardOrderDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByIds`, `select:getByBillNo`, `select:getFirstMonthOne`, `select:selectNotAcc`, `select:selectNotAccByOrderId`, `select:findAllBnAgeingOrder`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightProjectRentRecord.xml
- namespace: `com.rrsjk.light.dao.LightProjectRentRecordDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByStationIdAndRentDate`, `update:updateCollectAtByOrderId`, `update:updatePayAtByOrderIdAndStationCode`, `select:findByElecNoAndRentDate`, `update:batchNullOrderId`, `update:updateElecNo`, `update:batchNullOrderIdByStationCodes`
- tables: `id`, `light_station`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightImgsHistory.xml
- namespace: `com.rrsjk.light.dao.LightImgsHistoryDao`
- statements: `select:findBy`, `select:countOf`, `insert:createInfo`, `update:updateInfo`
- tables: `id`, `operation`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationOwnerExchange.xml
- namespace: `com.rrsjk.light.dao.LightStationOwnerExchangeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByWaitPush`, `select:findByPushedAndWaitCheck`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightGreenEnergy.xml
- namespace: `com.rrsjk.light.dao.LightGreenEnergyDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getIncom`, `select:getPay`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightRentQueue.xml
- namespace: `com.rrsjk.light.dao.LightRentQueueDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findBySuccess`, `select:getByStationIdAndAction`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightGridAwardPolicy.xml
- namespace: `com.rrsjk.light.dao.LightGridAwardPolicyDao`
- statements: `insert:create`, `update:update`, `select:findBySignAt`, `select:getById`, `select:findBy`, `select:countOf`, `select:checkB`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightAccount.xml
- namespace: `com.rrsjk.light.dao.LightAccountDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByType`, `select:getByTypes`, `select:findAllPayType`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightProjectFunnelManagement.xml
- namespace: `com.rrsjk.light.dao.LightProjectFunnelManagementDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:getByProjectCode`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `update:updateBindStatus`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStock.xml
- namespace: `com.rrsjk.light.dao.LightStockDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByStoreCodeAndSku`, `select:getByStoreIdAndSku`, `select:findByMemberId`, `select:countOf`, `select:findBy`, `select:countOfJoInStore`, `select:findByJoInStore`, `update:inStock`, `update:outStockRollBack`, `update:outStock`, `select:sumStockBySku`, `update:freezeStock`, `update:unFreezeStock`, `update:freezeSub`, `select:findStockStoreNameList`, `select:stockSummary`, `select:getByMemberIdAndSku`, `select:countOfStockGroupBySkuCode`, `select:findStockGroupBySkuCode`, `select:countOfSapStockForCbs`, `select:findSapStockForCbs`, `select:countOfSapStockForCbsExcludeInternalTransfer`, `select:findSapStockForCbsExcludeInternalTransfer`, `update:useStock`, `update:usedToSold`, `update:useStockRollback`
- tables: `id`, `light_sp_store`, `light_stock`, `light_stock_change`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightProjectSpPartner.xml
- namespace: `com.rrsjk.light.dao.LightProjectSpPartnerDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpStore.xml
- namespace: `com.rrsjk.light.dao.LightSpStoreDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:findMainStoreBySpId`, `select:findBy`, `select:findByOld`, `select:findCountBy`, `select:findCountByOld`, `select:getByStoreCodeAndSpId`, `select:findSecondClassStoreBySubSpId`, `select:findMainStoreBySpIdList`, `select:countOfMainStoreByJoinStoreAddress`, `select:findMainStoreByJoinStoreAddress`, `select:countOfStoreListForCbs`, `select:findStoreListForCbs`, `select:findStoreListForCbsExport`, `select:findBySubSpId`, `select:countOfSecondClassStoreListForCbs`, `select:findSecondClassStoreList`, `select:findMainDefaultBySpId`, `select:findSecondBySubId`
- tables: `id`, `light_sp_authority_zone`, `light_sp_store`, `light_store_address`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/OperationMaintenanceLog.xml
- namespace: `com.rrsjk.light.dao.OperationMaintenanceLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpOrderQueue.xml
- namespace: `com.rrsjk.light.dao.LightSpOrderQueueDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSupplierContracts.xml
- namespace: `com.rrsjk.light.dao.LightSupplierContractsDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/ReportMStation.xml
- namespace: `com.rrsjk.light.dao.ReportMStationDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightGreenIncomeBatch.xml
- namespace: `com.rrsjk.light.dao.LightGreenIncomeBatchDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByOrderNo`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpcOperateLog.xml
- namespace: `com.rrsjk.light.dao.LightSpcOperateLogDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpAuthOperate.xml
- namespace: `com.rrsjk.light.dao.LightSpAuthOperateDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationZhongheLog.xml
- namespace: `com.rrsjk.light.dao.LightStationZhongheLogDao`
- statements: `insert:create`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStockTaking.xml
- namespace: `com.rrsjk.light.dao.LightStockTakingDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:findTaking`, `select:countTaking`
- tables: `id`, `light_stock_taking`, `rrsjk_light.light_stock_taking`, `rrsjk_light.light_stock_taking_detail`, `rrsjk_light.light_stock_taking_variance_analysis`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpOrder.xml
- namespace: `com.rrsjk.light.dao.LightSpOrderDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findWaitPayOrder`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightNegativeReduceLog.xml
- namespace: `com.rrsjk.light.dao.LightNegativeReduceLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightImageVerifyLogMapper.xml
- namespace: `com.rrsjk.light.mapper.LightImageVerifyLogMapper`
- statements: `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `select:queryByUniqueImageKey`, `select:queryByUploadUrl`
- tables: `id`, `light_image_verify_log`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmOwnerStationWhiteList.xml
- namespace: `com.rrsjk.light.dao.CmOwnerStationWhiteListDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmSapQueue.xml
- namespace: `com.rrsjk.light.dao.CmSapQueueDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findBySuccess`, `select:findBySuccessAction`, `select:getByRecordIdAndAction`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpContractRecord.xml
- namespace: `com.rrsjk.light.dao.LightSpContractRecordDao`
- statements: `insert:create`, `update:update`, `select:queryOne`, `select:queryListBySpId`, `select:queryCountBySpId`, `select:queryOneByZoneId`, `select:queryOneByProjectId`, `select:queryOneByQuotaId`, `select:getContractsBySuppliers`
- tables: `id`, `light_elec_contract`, `light_service_provider`, `light_sp_contract_record`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmChange.xml
- namespace: `com.rrsjk.light.dao.CmChangeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationYuexiuSk.xml
- namespace: `com.rrsjk.light.dao.LightStationYuexiuSkDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByBatchNo`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpQuotaDedicated.xml
- namespace: `com.rrsjk.light.dao.LightSpQuotaDedicatedDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationEpcFile.xml
- namespace: `com.rrsjk.light.dao.LightStationEpcFileDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteByStationIdAndStage`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightCompanyInfo.xml
- namespace: `com.rrsjk.light.dao.LightCompanyInfoDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findByName`, `select:getByCompanyCodes`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:getByName`, `select:getByCompanyCode`, `select:getEnableByCompanyCode`, `select:findByBusinessCode`, `select:findByBusinessCodeList`, `update:updateframe`, `update:finance`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationTransferOrderLog.xml
- namespace: `com.rrsjk.light.dao.LightStationTransferOrderLogDao`
- statements: `insert:create`, `insert:batchCreate`, `select:findByTransferOrderId`
- tables: `light_station_transfer_order_log`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/RegionModifyAudit.xml
- namespace: `com.rrsjk.light.dao.RegionModifyAuditDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightTransitLog.xml
- namespace: `com.rrsjk.light.dao.LightTransitLogDao`
- statements: `insert:create`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightCommodity.xml
- namespace: `com.rrsjk.light.dao.LightCommodityDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightCompanyPolicyAuditLog.xml
- namespace: `com.rrsjk.light.dao.LightCompanyPolicyAuditLogDao`
- statements: `insert:create`, `update:update`, `select:findListByPolicyId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightImageVerificationMapper.xml
- namespace: `com.rrsjk.light.mapper.LightImageVerificationMapper`
- statements: `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `select:queryByUniqueImageKey`, `select:queryLastedByUniqueKey`, `select:queryImageDetail`
- tables: `id`, `light_image_verification`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightDccCompany.xml
- namespace: `com.rrsjk.light.dao.LightDccCompanyDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByLicenceNo`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightGridCert.xml
- namespace: `com.rrsjk.light.dao.LightGridCertDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByStationCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationInverterOcrMapper.xml
- namespace: `com.rrsjk.light.mapper.LightStationInverterOcrMapper`
- statements: `select:selectById`, `insert:insert`, `insert:insertSelective`, `update:updateByIdSelective`, `update:updateById`, `update:updateByStationCodeAndTaskId`, `select:queryAllByStationCodeAndImageUrl`, `select:queryLastedWithInverter`
- tables: `id`, `light_station_inverter_ocr`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightGroovyScriptParam.xml
- namespace: `com.rrsjk.light.dao.LightGroovyScriptParamDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `delete:deleteByType`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/SwitchLightOperateLog.xml
- namespace: `com.rrsjk.light.dao.SwitchLightOperateLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightPlan.xml
- namespace: `com.rrsjk.light.dao.LightPlanDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationMasterContractOcrMapper.xml
- namespace: `com.rrsjk.light.mapper.LightStationMasterContractOcrMapper`
- statements: `select:selectByPrimaryKey`, `insert:insert`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `update:updateByPrimaryKey`, `select:countByStationCode`, `insert:batchInsert`, `select:selectOneByStationCode`, `select:findBy`, `select:countOf`
- tables: `id`, `light_station_master_contract_ocr`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/WindSnowData.xml
- namespace: `com.rrsjk.light.dao.WindSnowDataDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByCityCodeAndRegionCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightAwardAppealAuditLog.xml
- namespace: `com.rrsjk.light.dao.LightAwardAppealAuditLogDao`
- statements: `insert:create`, `select:get`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightContractRevocateAndRestoreLog.xml
- namespace: `com.rrsjk.light.dao.LightContractRevocateAndRestoreLogDao`
- statements: `insert:create`, `update:update`, `select:findBy`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightLendOutSn.xml
- namespace: `com.rrsjk.light.dao.LightLendOutSnDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/ElectricCompetePriceInfoMapper.xml
- namespace: `com.rrsjk.light.dao.ElectricCompetePriceInfoDao`
- statements: `select:getById`, `insert:create`, `update:updateById`, `insert:batchInsert`, `select:countOf`, `select:findBy`, `select:getByStationCode`, `update:batchUpdateByNo`
- tables: `electric_compete_price_info`, `id`, `light_station`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationInsurance.xml
- namespace: `com.rrsjk.light.dao.LightStationInsuranceDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:findByStationId`, `select:findByStationCode`, `select:findEnableByStationId`, `select:getExpirationByStationCodeAndType`, `select:getByStationCodeAndType`, `select:findByInsuranceNo`, `select:countOfWaitPush`, `select:findByWaitPushYuexiu`, `update:updateByStationCode`, `select:findToPush`, `select:findToPushCount`, `select:getThisYearInsurance`, `select:findExchangeToPush`, `select:countOfInCmb`, `select:findByInCmb`
- tables: `cmb_leasing_station`, `id`, `insurance_push_data`, `light_station`, `light_station_insurance`, `light_station_yuexiu`, `light_station_yuexiu_exchange`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightUseOrderReverse.xml
- namespace: `com.rrsjk.light.dao.LightUseOrderReverseDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationSettle.xml
- namespace: `com.rrsjk.light.dao.LightStationSettleDao`
- statements: `select:findBy`, `select:getByRelationId`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByRelationId`, `select:countOfRelationId`, `update:updateIsDel`, `select:sumBaseAmount`
- tables: `id`, `light_station_settle`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/DatabaseManagement.xml
- namespace: `com.rrsjk.light.dao.DatabaseManagementDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightManualIncomeInvoice.xml
- namespace: `com.rrsjk.light.dao.LightManualIncomeInvoiceDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:findByParam`, `select:findByIncomeId`, `select:getByRelationNo`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightShareBillRecord.xml
- namespace: `com.rrsjk.light.dao.LightShareBillRecordDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `update:updateAuditAtByBillNo`, `insert:batchInsert`, `select:getById`, `select:findPayedByStationId`, `select:findByDetail`, `select:countOfDetail`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmLightProjectIncome.xml
- namespace: `com.rrsjk.light.dao.CmLightProjectIncomeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/lightStationRegisterDraft.xml
- namespace: `com.rrsjk.light.dao.LightStationRegisterDraftDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `update:delete`, `insert:batchInsert`, `select:getById`, `select:getByMemberId`
- tables: `id`, `light_sp_staff`, `light_station_register_draft`, `light_sub_sp`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationConfirmImgTemp.xml
- namespace: `com.rrsjk.light.dao.LightStationConfirmImgTempDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `delete:delete`, `update:updateStationIdToMinus`, `update:updateConfirmImgToNull`, `update:updateCompleteImgToNull`, `delete:deleteByTypeAndSortNum`, `delete:deleteByType`, `select:getByImaNameAndType`, `select:getListByImaNameAndType`, `select:getGsyAppStationImg`, `delete:batachDeleteByStationId`, `select:findByStationId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightDepositLog.xml
- namespace: `com.rrsjk.light.dao.LightDepositLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationInfoUpdate.xml
- namespace: `com.rrsjk.light.dao.LightStationInfoUpdateDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `select:getById`, `select:getByIdAndUserId`, `select:getDoingUpdate`, `select:getDoingUpdateForStationCode`, `select:getUpdateCount`, `select:getUpdateList`, `update:audit`, `update:update`, `update:updateDelete`, `select:getByIdAndPhone`, `select:getDoingUpdateByPhone`, `select:getUpdateCountByPhone`
- tables: `id`, `light_station`, `light_station_info_update`, `light_sub_sp`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/ReportMOrder.xml
- namespace: `com.rrsjk.light.dao.ReportMOrderDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightConfirmOrder.xml
- namespace: `com.rrsjk.light.dao.LightConfirmOrderDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `delete:delete`, `select:countOfMainProvider`, `select:findMainProviderBy`, `select:findAllBy`, `select:countOfAll`
- tables: `id`, `light_confirm_order`, `light_sp_auclon_store`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpServiceProvinceAuditLog.xml
- namespace: `com.rrsjk.light.dao.LightSpServiceProvinceAuditLogDao`
- statements: `insert:create`, `update:update`, `select:findBySpServiceProvinceId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightUseOrder.xml
- namespace: `com.rrsjk.light.dao.LightUseOrderDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:countOfCbs`, `select:findByForCbs`, `select:getByUseOrderNo`, `select:getByPlanConfigId`, `select:getByPlanConfigIdAndEnable`, `select:findByStationId`, `select:findByCreatedBy`, `select:getLastBySkuCode`, `update:batchDeleteByStationCode`, `select:findCompleteBeforeByStationIdAndUseStatus`, `select:findCompleteBeforeByStationId`, `select:findByPlanConfigIds`, `update:batchUpdateUseStatus`, `select:findStationListByPage`, `select:countStationListByPage`, `select:findListByPageForCbs`, `select:countListByPageForCbs`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightEnablePolicyArea.xml
- namespace: `com.rrsjk.light.dao.LightEnablePolicyAreaDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByPolicyId`, `delete:deleteByPolicyId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightProjectElectricEpcWhiteList.xml
- namespace: `com.rrsjk.light.dao.LightProjectElectricEpcWhiteListDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightEamNetlistQueue.xml
- namespace: `com.rrsjk.light.dao.LightEamNetlistQueueDao`
- statements: `update:update`, `update:updateByIdAndSuccess`, `insert:create`, `select:findBy`, `select:countOf`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightMakeOrder.xml
- namespace: `com.rrsjk.light.dao.LightMakeOrderDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByOrderNo`, `select:findByMemberId`, `select:findAllByMemberId`, `select:getByStationId`, `select:findByBatchNo`, `select:countOf`, `select:findBy`, `select:findByIdList`, `select:findByConfirmOrderIdList`, `update:quitOrder`, `select:findByConfirmId`, `select:findNotStopByConfirmId`, `select:findStopByConfirmId`, `select:getAllDisplayName`, `select:findRoboAdvisorOrderByConfirmId`
- tables: `id`, `light_station`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightCompanyInfoUpdateLogDao.xml
- namespace: `com.rrsjk.light.dao.LightCompanyInfoUpdateLogDao`
- statements: `select:findList`, `insert:insertdata`
- tables: `light_company_info_update_log`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationBankCardChange.xml
- namespace: `com.rrsjk.light.dao.LightStationBankCardChangeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByStationCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpQuotaDedicatedConfig.xml
- namespace: `com.rrsjk.light.dao.LightSpQuotaDedicatedConfigDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmSignAmountTarget.xml
- namespace: `com.rrsjk.light.dao.CmSignAmountTargetDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationPartCompleteApply.xml
- namespace: `com.rrsjk.light.dao.LightStationPartCompleteApplyDao`
- statements: `insert:create`, `update:update`, `select:findBy`, `select:countOf`, `select:getById`
- tables: `id`, `light_sub_sp`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightInstantGridReward.xml
- namespace: `com.rrsjk.light.dao.LightInstantGridRewardDao`
- statements: `select:findBy`, `select:findOneBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findCompleteByNotConfirm`, `select:findByNotConfirm`, `select:findByNotConfirmByStationCode`, `select:findByStationCode`, `update:removeCostVoucher`, `update:delete`
- tables: `id`, `light_instant_grid_reward`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightProjectElectricOrderOwner.xml
- namespace: `com.rrsjk.light.dao.LightProjectElectricOrderOwnerDao`
- statements: `insert:batchInsert`, `select:findBy`, `select:countOf`, `update:update`, `select:findPfBy`, `select:countOfPf`, `select:findByInCmb`, `select:countOfInCmb`, `delete:deleteByElecOrderNo`, `select:findByTotalCapacityIsNull`, `update:batchUpdateTotalCapacity`
- tables: `cmb_leasing_station`, `id`, `light_project_electric_order`, `light_project_electric_order_owner`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightLikes.xml
- namespace: `com.rrsjk.light.dao.LightLikesDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `select:getByParm`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightBillFunnelCache.xml
- namespace: `com.rrsjk.light.dao.LightBillFunnelCacheDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/ErrorLog.xml
- namespace: `com.rrsjk.light.dao.ErrorLogDao`
- statements: `select:findList`, `insert:create`, `update:update`, `select:get`, `select:getByStationCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationHouseCertificateOcrMapper.xml
- namespace: `com.rrsjk.light.mapper.LightStationHouseCertificateOcrMapper`
- statements: `select:selectByPrimaryKey`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `select:selectLatest`, `select:checkIfExist`
- tables: `id`, `light_station_house_certificate_ocr`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightAuxiliaryMaterialPlanConfig.xml
- namespace: `com.rrsjk.light.dao.LightAuxiliaryMaterialPlanConfigDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationYuexiuSettle.xml
- namespace: `com.rrsjk.light.dao.LightStationYuexiuSettleDao`
- statements: `select:findBy`, `select:findByPro`, `select:countOf`, `select:countOfPro`, `insert:create`, `update:update`, `update:updateForReIncome`, `update:updateByBatchNo`, `update:updateByStationCode`, `insert:batchInsert`, `update:batchUpdate`, `select:getById`, `select:getByStationCode`, `select:findSk`, `select:findForExport`, `update:batchUpdateInfoForReverse`, `select:findNeedReverseData`, `select:findNeedIncomeData`, `delete:deleteByBatchNo`, `select:existsByStationCode`, `select:findActiveStationCodes`, `select:getLatestIncomeTime`
- tables: `id`, `rrsjk_trade`.invoice`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightProjectPartner.xml
- namespace: `com.rrsjk.light.dao.LightProjectPartnerDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:getByMemberId`, `select:getByName`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmLightProjectIncomeInvoice.xml
- namespace: `com.rrsjk.light.dao.CmLightProjectIncomeInvoiceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteByIncomeId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightEnablePolicySpProp.xml
- namespace: `com.rrsjk.light.dao.LightEnablePolicySpPropDao`
- statements: `select:findBy`, `select:findAllEnableBySpId`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightHdIncome.xml
- namespace: `com.rrsjk.light.dao.LightHdIncomeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:batchUpdate`, `select:existsByStationCode`, `select:findActiveStationCodes`, `select:getLatestIncomeTime`, `select:findByStationCode`, `select:findLatestByStationCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmConstructionPlan.xml
- namespace: `com.rrsjk.light.dao.CmConstructionPlanDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findReportBy`, `select:countReportOf`
- tables: `cm_construction_plan`, `cm_construction_plan_item`, `cm_light_project`, `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpStaff.xml
- namespace: `com.rrsjk.light.dao.LightSpStaffDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByMemberId`, `select:findByNoPages`, `select:getByAccount`, `select:findBySpIdAndRegionId`, `select:getByMobile`, `select:findParentMemberIdByRole`, `select:findByCbs`, `select:countOfCbs`, `select:findByParentMemberIds`
- tables: `id`, `light_sp_staff_region`, `light_sub_sp`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightMaterialPackage.xml
- namespace: `com.rrsjk.light.dao.LightMaterialPackageDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByPackageNo`, `select:getEnableByPackageNo`, `select:countOf`, `select:findBy`, `update:disable`, `update:enable`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/GsyStationInfoUserExtend.xml
- namespace: `com.rrsjk.light.dao.GsyStationInfoUserExtendDao`
- statements: `select:findLastOne`, `insert:create`
- tables: `station_img`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightOpOrderLog.xml
- namespace: `com.rrsjk.light.dao.LightOpOrderLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmLightProjectVoteImgInfo.xml
- namespace: `com.rrsjk.light.dao.CmLightProjectVoteImgInfoDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByProjectId`, `update:deleteByProjectId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSysUser.xml
- namespace: `com.rrsjk.light.dao.LightSysUserDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByMemberId`, `select:getByMobile`, `select:findExistByMobile`, `select:getSubSpByAncestorSubMember`, `select:getSubSpsByAncestorSubMembers`, `select:getSpUserByChildMemberId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmSettlement.xml
- namespace: `com.rrsjk.light.dao.CmSettlementDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmReportChainGroupIncome.xml
- namespace: `com.rrsjk.light.dao.CmReportChainGroupIncomeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationPlanDesign.xml
- namespace: `com.rrsjk.light.dao.LightStationPlanDesignDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightCoinStation.xml
- namespace: `com.rrsjk.light.dao.LightCoinStationDao`
- statements: `select:countOf`, `select:findBy`
- tables: `light_coin`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightProjectElectricOrderFapRecord.xml
- namespace: `com.rrsjk.light.dao.LightProjectElectricOrderFapRecordDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findNewEnergyHistory`
- tables: `id`, `light_project_electric_order_fap_record`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpWithdrawalApplication.xml
- namespace: `com.rrsjk.light.dao.LightSpWithdrawalApplicationDao`
- statements: `insert:create`, `update:update`, `select:findByCreatedAt`, `select:getById`, `select:findBy`, `select:countOf`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/ReportMGrid.xml
- namespace: `com.rrsjk.light.dao.ReportMGridDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightQuotaChange.xml
- namespace: `com.rrsjk.light.dao.LightQuotaChangeDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:sumUsedQuota`, `select:sumReleaseQuota`, `select:sumAuxiliaryUsedQuota`, `select:sumAuxiliaryReleaseQuota`, `select:sumMajorUsedQuota`, `select:sumMajorReleaseQuota`, `select:sumMajorUsedQuotaForMultiSp`, `select:sumMajorReleaseQuotaForMultiSp`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpAuclonStore.xml
- namespace: `com.rrsjk.light.dao.LightSpAuclonStoreDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `insert:batchInsert`
- tables: `id`, `light_sub_sp`, `light_sub_sp_region`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmReportIncomeItem.xml
- namespace: `com.rrsjk.light.dao.CmReportIncomeItemDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteByDate`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightProjectElectricInvoiceReverseRecord.xml
- namespace: `com.rrsjk.light.dao.LightProjectElectricInvoiceReverseRecordDao`
- statements: `insert:create`, `update:updateNoCheck`, `update:update`, `select:getById`, `select:findByIds`, `select:countOf`, `select:findBy`, `select:getByInvoiceNumber`, `select:getNoFinishedByBatchNoAndInvoiceNo`, `select:getNoNewInvoiceNumberByBatchNoAndInvoiceNo`, `select:getByBatchNoAndInvoiceNo`, `delete:logicDeleteById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpExcitationStatusRecord.xml
- namespace: `com.rrsjk.light.dao.LightSpExcitationStatusRecordDao`
- statements: `select:findBy`, `select:findList`, `select:findByRelateId`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightModulePartCompleteApplyImg.xml
- namespace: `com.rrsjk.light.dao.LightModulePartCompleteApplyImgDao`
- statements: `insert:create`, `insert:batchInsert`, `delete:deleteByApplyId`, `select:findBy`, `select:countOf`, `select:getById`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightInstantGridRewardItem.xml
- namespace: `com.rrsjk.light.dao.LightInstantGridRewardItemDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightPMConfirm.xml
- namespace: `com.rrsjk.light.dao.LightPMConfirmDao`
- statements: `select:queryListBy`, `select:queryCountBy`
- tables: `light_company_info`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightElecContract.xml
- namespace: `com.rrsjk.light.dao.LightElecContractDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:queryListBy`, `select:find`, `select:queryCountBy`, `select:getByContractId`, `select:getByContractNo`, `select:getByRelateIdAndType`, `select:getByContractNoType`, `select:findSignedSpContract`, `select:findByParams`, `update:delete`, `update:deleteByRelateId`, `update:deleteByIdList`, `select:selectStationContractList`, `select:getByContractNoHistory`, `select:findSignedContract`, `select:findSignedContractByCode`, `select:findNeedPushContractList`, `select:findSignedStationContract`
- tables: `id`, `light_elec_contract`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpGridAwardOrderItem.xml
- namespace: `com.rrsjk.light.dao.LightSpGridAwardOrderItemDao`
- statements: `select:findBy`, `select:countOf`, `select:countOfToTarget`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`, `light_sp_grid_award_order_item`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationIncomeReverse.xml
- namespace: `com.rrsjk.light.dao.LightStationIncomeReverseDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightMakeOrderOperatorLog.xml
- namespace: `com.rrsjk.light.dao.LightMakeOrderOperateLogDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByParams`, `select:countOf`, `select:getSubCenterAudit`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/ChuiYangRequestLog.xml
- namespace: `com.rrsjk.light.dao.ChuiYangRequestLogDao`
- statements: `insert:create`
- tables: `chui_yang_request_log`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightEamPay.xml
- namespace: `com.rrsjk.light.dao.LightEamPayDao`
- statements: `insert:create`, `select:findBy`, `select:countOf`, `delete:deleteByOrdCode`, `insert:batchInsert`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmLightProjectVoteFeeInfo.xml
- namespace: `com.rrsjk.light.dao.CmLightProjectVoteFeeInfoDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByProjectId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightDeposit.xml
- namespace: `com.rrsjk.light.dao.LightDepositDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByMemberId`, `select:getByDepositNo`, `select:countOf`, `select:findBy`, `select:getFirstDeposit`, `select:findRepurchaseDepositList`, `select:countOfRepurchaseDepositList`
- tables: `id`, `light_deposit`, `light_service_provider`, `light_sp_order`, `light_station_repurchase`, `rrsjk_light_operation.light_operation_loss_management`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmLightProjectFinishLog.xml
- namespace: `com.rrsjk.light.dao.CmLightProjectFinishLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpMaterialPriceChangeLog.xml
- namespace: `com.rrsjk.light.dao.LightSpMaterialPriceChangeLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `update:batchUpdate`, `select:findById`, `select:findByPriceId`, `select:getLatestLogByPriceId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationOperatorLogExchange.xml
- namespace: `com.rrsjk.light.dao.LightStationOperatorLogExchangeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightPurchaseCost.xml
- namespace: `com.rrsjk.light.dao.LightPurchaseCostDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:getLastBySkuCodeAndCompanyCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightOpOrderQueue.xml
- namespace: `com.rrsjk.light.dao.LightOpOrderQueueDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/WindSnowLoadData.xml
- namespace: `com.rrsjk.light.dao.WindSnowLoadDataDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByProvinceAndCity`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/MaintenanceStationAdd.xml
- namespace: `com.rrsjk.light.dao.MaintenanceStationAddDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightZhPower.xml
- namespace: `com.rrsjk.light.dao.LightZhPowerDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightEnablePolicyLog.xml
- namespace: `com.rrsjk.light.dao.LightEnablePolicyLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByPolicyId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationContractInfo.xml
- namespace: `com.rrsjk.light.dao.LightStationContractInfoDao`
- statements: `insert:create`, `update:update`, `update:updateByRecordIdAndCode`, `select:findListByRecordId`, `select:findById`, `select:findByStationId`
- tables: `id`, `light_station_contract_info`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationPolicyIncome.xml
- namespace: `com.rrsjk.light.dao.LightStationPolicyIncomeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/GsySkuData.xml
- namespace: `com.rrsjk.light.dao.GsySkuDataDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:updateByRelationId`, `select:findByRelationId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationZhMigrateRecord.xml
- namespace: `com.rrsjk.light.dao.LightStationZhMigrateRecordDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByStationIdAndNode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationAreaLimit.xml
- namespace: `com.rrsjk.light.dao.LightStationAreaLimitDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByProvinceId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/YuexiuElectricityBill.xml
- namespace: `com.rrsjk.light.dao.YuexiuElectricityBillDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByBillId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmInvoiceApplyItem.xml
- namespace: `com.rrsjk.light.dao.CmInvoiceApplyItemDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByApplyCode`, `select:findHistoryEnableList`, `delete:deleteByApplyCode`
- tables: `cm_invoice_apply`, `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSubsidy.xml
- namespace: `com.rrsjk.light.dao.LightSubsidyDao`
- statements: `insert:create`, `update:update`, `update:removeCostVoucher`, `select:get`, `select:getByStationId`, `select:getByStationCode`, `select:countOf`, `select:findBy`, `select:accountMonthSum`, `update:updateAccountMonthSum`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSpWithdrawalApplicationLog.xml
- namespace: `com.rrsjk.light.dao.LightSpWithdrawalApplicationLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/CmLightProjectFinishAccounting.xml
- namespace: `com.rrsjk.light.dao.CmLightProjectFinishAccountingDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:deleteByProjectCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightAuxiliaryPreOrder.xml
- namespace: `com.rrsjk.light.dao.LightAuxiliaryPreOrderDao`
- statements: `select:findPageGroupByPreAuxiliaryOrderNo`, `select:findBy`, `select:countOfGroupByPreAuxiliaryOrderNo`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByAuxiliaryPurchaseOrderNoAndSkuCodeAndSupplierCode`
- tables: `id`, `light_purchase_order`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightUnionpayUser.xml
- namespace: `com.rrsjk.light.dao.LightUnionpayUserDao`
- statements: `insert:create`, `update:update`, `select:findBy`, `select:countOf`, `select:getById`, `select:getByIdCardNumber`, `delete:deleteByIdCardNumber`, `delete:deleteByIdCardNumberSpId`, `select:getByIdComCodeSpId`
- tables: `id`, `light_station`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationYuexiuPrice.xml
- namespace: `com.rrsjk.light.dao.LightStationYuexiuPriceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByStationCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightOption.xml
- namespace: `com.rrsjk.light.dao.LightOptionDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `select:getById`, `select:getAll`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/AgentTokenViewMapper.xml
- namespace: `com.rrsjk.light.mapper.AgentTokenViewMapper`
- statements: `select:selectByPrimaryKey`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `select:selectByParam`
- tables: `agent_token_view`, `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightStationAuditReport.xml
- namespace: `com.rrsjk.light.dao.LightStationAuditReportDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/LightSapSoQueue.xml
- namespace: `com.rrsjk.light.dao.LightSapSoQueueDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findBySuccess`, `select:getByOrderIdAndAction`, `select:findByOrderNo`, `select:findByOrderNoList`, `update:batchUpdate`, `select:findReCountByStationCode`, `select:findReCountByOrderNo`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/dispatch/LightAuditDispatchTimeConfigMapper.xml
- namespace: `com.rrsjk.light.dao.dispatch.LightAuditDispatchTimeConfigDao`
- statements: `insert:create`, `update:update`, `delete:deleteById`, `select:getById`, `select:findByConfigDateAndAuditType`, `select:findEnabledByConfigDateAndAuditType`, `select:findByPage`, `select:findByPageCount`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/dispatch/LightAuditDispatchLog.xml
- namespace: `com.rrsjk.light.dao.dispatch.LightAuditDispatchLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findLatestDispatchLogByStationIdAndAuditType`, `select:findLatestWaitDispatchLogByStationIdAndAuditType`, `select:findWaitDispatchLogByStationIdAndAuditType`, `select:countNormalDispatchByAuditorsForCurrentDay`, `select:findWaitAuditByStationCodeList`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/dispatch/LightTechAuditor.xml
- namespace: `com.rrsjk.light.dao.dispatch.LightTechAuditorDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByEmployeeCodeAndAuditType`, `select:findByValidEmployeeCodeAndAuditType`, `select:findByAuditType`, `select:findByAuditTypeAndName`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/dispatch/LightTechAuditorOperationLog.xml
- namespace: `com.rrsjk.light.dao.dispatch.LightTechAuditorOperationLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByAuditorId`, `select:findByEmployeeCodeAndDate`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroCarbonStoreChangeLog.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.LightZeroCarbonStoreChangeLogDao`
- statements: `insert:create`, `select:getByStoreId`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonSpDeposit.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.ZeroCarbonSpDepositDao`
- statements: `insert:create`, `update:update`, `update:updateByOrderNo`, `select:countOf`, `select:findBy`, `select:getByDepositNo`, `select:findByClientId`, `select:getById`, `select:findByDepositNos`, `update:batchUpdate`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonMessage.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.ZeroCarbonMessageDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:findList`, `select:findMerchantNoticeList`
- tables: `id`, `zero_carbon_message`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroCarbonButtonHitCount.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.LightZeroCarbonButtonHitCountDao`
- statements: `update:update`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroCarbonEnergyConnectionInverter.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.LightZeroCarbonEnergyConnectionInverterDao`
- statements: `insert:create`, `select:get`, `select:getBySnCode`, `update:update`
- tables: `id`, `light_zero_carbon_energy_connection_inverter`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroCarbonStation.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.LightZeroCarbonStationDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByStationCode`, `select:countOf`, `select:findBy`, `select:findByPhone`, `select:findByAuditType`, `select:countOfAuditType`, `select:findFinishedStation`, `select:getLightStationByDraftId`, `select:findZeroCarbonStationCount`, `select:findZeroCarbonStationList`, `select:findZeroCarbonStationCountEnable`, `select:findZeroCarbonStationListEnable`
- tables: `id`, `light_zero_carbon_station`, `light_zero_carbon_station_audit`, `light_zero_carbon_station_register_draft`, `rrsjk_light.light_zero_carbon_station`, `zero_carbon_station_relate_file`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroCarbonStationRegisterDraft.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.LightZeroCarbonStationRegisterDraftDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `update:delete`, `insert:batchInsert`, `select:getById`, `select:getByIdYantu`, `select:findZeroCarbonDraftCount`, `select:findZeroCarbonDraftList`, `select:findYanTuData`, `select:findCountOfYanTuData`
- tables: `id`, `light_zero_carbon_station`, `light_zero_carbon_station_register_draft`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroCarbonEnergyLog.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.LightZeroCarbonEnergyLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroCarbonOrderGrabbingCampaignOperateLog.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.LightZeroCarbonOrderGrabbingCampaignOperateLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByCampaignId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonServiceProvider.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.ZeroCarbonServiceProviderDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findOne`, `select:findCount`, `select:findPage`, `update:addDeposit`, `select:findSubsCount`, `select:findSubsPage`, `select:findSubSPCount`, `select:findSubSPPage`, `select:findSubCitySP`, `select:selectRecruitmentList`, `select:selectRecruitmentCount`, `select:findListByIds`, `select:findSubModesPage`, `select:findByMemberId`, `select:updateData`, `select:findListByIdsNotStatus`, `select:findByBusinessModel`
- tables: `id`, `sub_goal`, `zero_carbon_order_policy`, `zero_carbon_order_policy_service_provider`, `zero_carbon_service_provider`, `zero_carbon_sp_business_model`, `zero_carbon_sp_deposit`, `zero_carbon_sub`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonPolicy.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.ZeroCarbonPolicyDao`
- statements: `insert:create`, `update:update`, `select:findList`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroCarbonEStationAuditLogMapper.xml
- namespace: `com.rrsjk.light.mapper.zerocarbon.LightZeroCarbonEStationAuditLogMapper`
- statements: `select:selectByPrimaryKey`, `insert:insert`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `update:updateByPrimaryKey`, `select:findByParams`, `select:selectByStationId`
- tables: `id`, `light_zero_carbon_e_station_audit_log`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroMerchantNotice.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.LightZeroMerchantNoticeDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:selectAll`, `select:findBy`, `select:findByPage`, `select:findByPageCount`, `select:getMerchantPage`, `select:getMerchantPageCount`, `select:count`, `select:findByNoticeScope`
- tables: `id`, `light_zero_merchant_notice`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroCarbonStationPlanConfig.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.LightZeroCarbonStationPlanConfigDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:getConfigListByStationId`, `delete:delete`, `select:getAiXuModuleListByStationId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonContractRecord.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.ZeroCarbonContractRecordDao`
- statements: `insert:create`, `update:update`, `select:findOne`, `select:findList`, `select:findCount`, `select:findListBySpIds`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonOrderPolicyCashDetail.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.ZeroCarbonOrderPolicyCashDetailDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:findList`, `select:findCount`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroMaterialManageSerialMapper.xml
- namespace: `com.rrsjk.light.mapper.zerocarbon.LightZeroMaterialManageSerialMapper`
- statements: `select:selectByPrimaryKey`, `insert:insert`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `update:updateByPrimaryKey`, `select:countOf`, `select:findByPage`, `select:findByStationId`
- tables: `id`, `light_zero_material_manage_serial`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonSpBusinessModel.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.ZeroCarbonSpBusinessModelDao`
- statements: `insert:created`, `update:update`, `select:findBy`, `select:get`, `select:findPage`, `select:findCount`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonOrderPolicyLadder.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.ZeroCarbonOrderPolicyLadderDao`
- statements: `insert:create`, `update:update`, `insert:batchInsert`, `select:findList`, `delete:deleteByPolicyId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroCarbonStationRelateFile.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.LightZeroCarbonStationRelateFileDao`
- statements: `select:findBy`, `select:findList`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `delete:deleteByStationId`, `select:getById`, `select:getByIds`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroCarbonOrderGrabbingCampaignSupportingDocuments.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.LightZeroCarbonOrderGrabbingCampaignSupportingDocumentsDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:deleteByCampaignId`, `select:findByCampaignId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonOrderPolicyServiceProvider.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.ZeroCarbonOrderPolicyServiceProviderDao`
- statements: `insert:create`, `update:update`, `insert:batchInsert`, `select:findList`, `delete:deleteByPolicyId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroCarbonStockChange.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.LightZeroCarbonStockChangeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroMaterialPurchaseOrderMapper.xml
- namespace: `com.rrsjk.light.mapper.zerocarbon.LightZeroMaterialPurchaseOrderMapper`
- statements: `select:selectByPrimaryKey`, `insert:insert`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `update:updateByPrimaryKey`, `select:countOf`, `select:findByPage`, `select:selectForCompleteAudit`, `select:selectByItemOrderId`, `select:findSkuCodeForZeroStation`
- tables: `id`, `light_zero_material_purchase_order`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroCarbonStationSku.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.LightZeroCarbonStationSkuDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:get`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:findBySnListInOtherStation`, `update:disableByStationId`, `update:disableByStationIdExceptSkuTypeList`, `update:disableByStationIdAndSkuTypeList`, `select:getStationSkuByStationId`, `select:getInverterBySn`, `select:getModuleSnByStationId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonStationPolicy.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.ZeroCarbonStationPolicyDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findPage`, `select:findCount`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonOrderPolicyCash.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.ZeroCarbonOrderPolicyCashDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findCount`, `select:findPage`, `select:findList`
- tables: `id`, `zero_carbon_order_policy_cash`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonSpShopImg.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.ZeroCarbonSpShopImgDao`
- statements: `insert:create`, `update:update`, `insert:batchInsert`, `delete:batchDelete`, `select:findListByShopCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroCarbonStationOperateLog.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.LightZeroCarbonStationOperateLogDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findByParams`, `select:countOf`, `select:getOperateLogListByStationId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroCarbonStationAudit.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.LightZeroCarbonStationAuditDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:findByStationIdAndAuditType`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonOrderPolicy.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.ZeroCarbonOrderPolicyDao`
- statements: `insert:create`, `update:update`, `select:findCount`, `select:findPage`, `select:checkExist`, `select:get`, `select:findByExchange`, `select:findByExchangeNew`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroMerchantNoticeOperateLog.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.LightZeroMerchantNoticeOperateLogDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:selectById`, `select:selectAll`, `select:findBy`, `select:count`
- tables: `id`, `light_zero_merchant_notice_operate_log`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonStationPolicyDetail.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.ZeroCarbonStationPolicyDetailDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:findByPolicyId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroCarbonStock.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.LightZeroCarbonStockDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getBySkuCodeAndStoreCode`, `update:inStock`, `update:outStock`, `update:freezeStock`, `update:unFreezeStock`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroCarbonEStationSkuMapper.xml
- namespace: `com.rrsjk.light.mapper.zerocarbon.LightZeroCarbonEStationSkuMapper`
- statements: `select:selectByPrimaryKey`, `insert:insert`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `update:updateByPrimaryKey`, `select:findByParam`, `insert:batchInsert`, `update:deleteById`, `update:batchDeleteByStationIdAndSkuType`, `select:selectByStationId`, `update:deleteByStationId`
- tables: `id`, `light_zero_carbon_e_station_sku`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroCarbonStationConfirmImg.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.LightZeroCarbonStationConfirmImgDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `delete:delete`, `update:updateStationIdToMinus`, `select:getListByImaNameAndTypeAndStationCode`, `select:getConfirmImgListByStationId`, `update:disableByStationIdAndType`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonElecContract.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.ZeroCarbonElecContractDao`
- statements: `insert:create`, `update:update`, `select:findOne`
- tables: `id`, `zero_carbon_elec_contract`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroCarbonStore.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.LightZeroCarbonStoreDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroCarbonComponentLibrary.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.LightZeroCarbonComponentLibraryDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:countOfAge`, `update:freezeAssemblySn`, `update:disableAssemblySn`, `select:findBySnList`, `select:findEStationSku`, `update:occupyAssemblySn`
- tables: `id`, `light_module_sn`, `light_zero_carbon_component_library`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroCarbonEStationConfirmImgMapper.xml
- namespace: `com.rrsjk.light.mapper.zerocarbon.LightZeroCarbonEStationConfirmImgMapper`
- statements: `select:selectByPrimaryKey`, `insert:insert`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `update:updateByPrimaryKey`, `insert:batchInsert`, `update:deleteByStationId`, `select:selectByStationId`
- tables: `id`, `light_zero_carbon_e_station_confirm_img`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonSpLog.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.ZeroCarbonSpLogDao`
- statements: `insert:create`, `update:update`, `select:findList`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroMaterialManageMapper.xml
- namespace: `com.rrsjk.light.mapper.zerocarbon.LightZeroMaterialManageMapper`
- statements: `select:selectByPrimaryKey`, `insert:insert`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `update:updateByPrimaryKey`, `select:countOf`, `select:findByPage`
- tables: `id`, `light_zero_material_manage`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroCarbonSkuRetailUnitCost.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.LightZeroCarbonSkuRetailUnitCostDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findInverterCodeList`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonPointsWallet.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.ZeroCarbonPointsWalletDao`
- statements: `insert:create`, `update:update`, `select:findList`, `select:findCount`, `select:findIn`, `select:findOut`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonSub.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.ZeroCarbonSubDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findOne`, `select:findCount`, `select:findPage`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroCarbonPurchaseOrder.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.LightZeroCarbonPurchaseOrderDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:updateSignImageById`, `select:findWaitingToMake`, `update:relatePurchaseOrder`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroCarbonOrderGrabbingCampaign.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.LightZeroCarbonOrderGrabbingCampaignDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:batchUpdate`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonSpShopAuditLog.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.ZeroCarbonSpShopAuditLogDao`
- statements: `insert:create`, `update:update`, `select:findListByShopCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/SubGoal.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.SubGoalDao`
- statements: `insert:create`, `update:update`, `select:findOne`, `select:findList`, `select:findCount`, `select:findSubGoalSum`, `select:findSubGoalSumCount`, `delete:delete`
- tables: `id`, `sub_goal`, `zero_carbon_sub`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroCarbonInstallationFee.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.LightZeroCarbonInstallationFeeDao`
- statements: `insert:create`, `update:update`, `update:updateToConfirmedStatus`, `update:updateToRejectedStatus`, `select:get`, `select:countOf`, `select:findBy`, `select:countOfForMerchant`, `select:findByForMerchant`
- tables: `id`, `light_zero_carbon_installation_fee`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonSubNewMapper.xml
- namespace: `com.rrsjk.light.mapper.zerocarbon.ZeroCarbonSubNewMapper`
- statements: `select:selectByPrimaryKey`, `insert:insert`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `update:updateByPrimaryKey`, `select:selectSubCenter`
- tables: `id`, `zero_carbon_sub_new`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonSpShop.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.ZeroCarbonSpShopDao`
- statements: `insert:create`, `update:update`, `select:findPage`, `select:findCount`, `select:findOneById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonSpAuthRegion.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.ZeroCarbonSpAuthRegionDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findList`, `select:findByProviderId`, `select:findMasterRegion`, `select:findPage`, `select:findCount`, `select:findListByProviderIds`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroCarbonEStationMapper.xml
- namespace: `com.rrsjk.light.mapper.zerocarbon.LightZeroCarbonEStationMapper`
- statements: `select:selectByPrimaryKey`, `insert:insert`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `update:updateByPrimaryKey`, `select:countOfParams`, `select:findByParams`, `update:rejectAssignment`, `select:selectByStationCode`
- tables: `id`, `light_zero_carbon_e_station`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonElecSealUse.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.ZeroCarbonElecSealUseDao`
- statements: `insert:create`, `update:update`, `select:findOne`, `select:findList`
- tables: `id`, `zero_carbon_elec_seal_use`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/zerocarbon/LightZeroCarbonSkuData.xml
- namespace: `com.rrsjk.light.dao.zerocarbon.LightZeroCarbonSkuDataDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:getBySkuAndCompanyCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/tenderManagment/tenderManagmentAudit.xml
- namespace: `com.rrsjk.light.dao.tenderManagment.TenderManagmentAuditDao`
- statements: `insert:create`, `select:getById`, `select:getByName`, `update:update`, `delete:deleteById`, `select:findBy`, `select:countOf`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/tenderManagment/tenderManagmentAuditLog.xml
- namespace: `com.rrsjk.light.dao.tenderManagment.TenderManagmentAuditLogDao`
- statements: `insert:create`, `select:getById`, `select:findByTmaId`, `update:update`, `delete:deleteById`, `select:findBy`, `select:countOf`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/sharePayment/ShareProjectPaymentAccount.xml
- namespace: `com.rrsjk.light.dao.sharePayment.ShareProjectPaymentAccountDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByProjectCompanyCodes`, `update:batchUpdateStatus`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/investor/InvestorMasterDataAudit.xml
- namespace: `com.rrsjk.light.dao.investor.InvestorMasterDataAuditDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/investor/InvestorMasterData.xml
- namespace: `com.rrsjk.light.dao.investor.InvestorMasterDataDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteById`, `select:countByCooperationStatus`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/gf/GfSecondClassAccountOpenRecord.xml
- namespace: `com.rrsjk.light.dao.gf.GfSecondClassAccountOpenRecordDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `select:getById`, `select:getByAccountId`, `select:getByInputPieceId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/gf/GfStationContractShareRule.xml
- namespace: `com.rrsjk.light.dao.gf.GfStationContractShareRuleDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findBy`, `delete:deleteById`, `insert:batchInsert`, `delete:batchDeleteByContractId`
- tables: `id`, `light_station_contract_share_rule`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/gf/GfLightStation.xml
- namespace: `com.rrsjk.light.dao.gf.GfLightStationDao`
- statements: `select:findBy`, `select:startToFirstInputPiece`, `select:startToPushCompleteInputPiece`, `select:findByJoin`, `select:countOf`, `select:countOfJoin`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByStationCode`, `update:deleteByStationCode`, `select:getByInputPieceId`, `select:findByCbsRefactor`, `select:countOfByCbsRefactor`, `select:findByCbs`, `select:countOfByCbs`
- tables: `gf_business_opportunity`, `id`, `light_station`, `light_station_plan_config`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/gf/GfSecondClassAccount.xml
- namespace: `com.rrsjk.light.dao.gf.GfSecondClassAccountDao`
- statements: `select:findBy`, `select:countOf`, `select:findByExcludingNoNeedStatus`, `select:countOfExcludingNoNeedStatus`, `insert:create`, `update:update`, `select:getById`, `select:getByInputPieceId`, `select:findNoOpenAndNoSignAccount`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/gf/GfApiInteractionLog.xml
- namespace: `com.rrsjk.light.dao.gf.GfApiInteractionLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/gf/GfBusinessOpportunity.xml
- namespace: `com.rrsjk.light.dao.gf.GfBusinessOpportunityDao`
- statements: `select:findBy`, `select:findByJoin`, `select:findDtoBy`, `select:countOf`, `select:countOfJoin`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByInputPieceId`, `select:getByStationNo`, `select:findByCbs`, `select:selectOption`, `select:findToUpdateContract`, `select:findToUpdateConfirmUrl`, `select:getByIdCardNumber`
- tables: `gf_business_opportunity`, `gf_light_station`, `id`, `light_sp_staff`, `light_station_contract_record`, `light_sub_sp`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/gf/GfFileModule.xml
- namespace: `com.rrsjk.light.dao.gf.GfFileModuleDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:deleteByInputPieceId`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/gf/GfCompleteInputPiece.xml
- namespace: `com.rrsjk.light.dao.gf.GfCompleteInputPieceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:deleteByInputPieceId`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByCbs`, `select:countOfCbs`, `select:getByStationCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/gf/GfProductInformation.xml
- namespace: `com.rrsjk.light.dao.gf.GfProductInformationDao`
- statements: `select:findBy`, `select:findByCbs`, `select:countOf`, `insert:create`, `update:update`, `update:updateByCodeId`, `update:updateByAdress`, `select:getById`
- tables: `id`, `light_sp_staff`, `light_sub_sp`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/gf/GfFirstInputPiece.xml
- namespace: `com.rrsjk.light.dao.gf.GfFirstInputPieceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:deleteByInputPieceId`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByCbs`, `select:countOfCbs`
- tables: `gf_business_opportunity`, `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/reverse/LightStationChangPlanInverter.xml
- namespace: `com.rrsjk.light.dao.reverse.LightStationChangePlanInverterDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByStationCode`, `select:findByChangeId`, `update:logicDeleteByChangeId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/reverse/LightStationChangPlanModuleSn.xml
- namespace: `com.rrsjk.light.dao.reverse.LightStationChangePlanModuleSnDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByStationCode`, `select:findByChangeId`, `update:logicDeleteByChangeId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/reverse/LightStationChangPlanToDo.xml
- namespace: `com.rrsjk.light.dao.reverse.LightStationChangePlanToDoDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:countByStationCode`, `select:findByStationCode`, `select:findByPlanChangeId`, `select:findWaitDealToDoList`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/reverse/LightStationChangPlanModuleImg.xml
- namespace: `com.rrsjk.light.dao.reverse.LightStationChangePlanModuleImgDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByStationCode`, `select:findByChangeId`, `update:logicDeleteByChangeId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/report/LightReportComponentPriceMapper.xml
- namespace: `com.rrsjk.light.dao.report.LightReportComponentPriceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `insert:batchInsert`, `update:update`, `update:batchDelete`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/report/LightReportCompetitorPriceMapper.xml
- namespace: `com.rrsjk.light.dao.report.LightReportCompetitorPriceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `insert:batchInsert`, `update:update`, `update:batchDelete`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/report/LightReportPurchasePriceMapper.xml
- namespace: `com.rrsjk.light.dao.report.LightReportPurchasePriceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `insert:batchInsert`, `update:update`, `update:batchDelete`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/report/LightReportComponentSwitchMapper.xml
- namespace: `com.rrsjk.light.dao.report.LightReportComponentSwitchDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `insert:batchInsert`, `update:update`, `update:batchDelete`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/evaluate/LightStationEvaluationWorkOrder.xml
- namespace: `com.rrsjk.light.dao.evaluate.LightStationEvaluationWorkOrderDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/evaluate/LightStationEvaluationRecord.xml
- namespace: `com.rrsjk.light.dao.evaluate.LightStationEvaluationRecordDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findRecentRecords`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/evaluate/LightStationEvaluationTeamFeedBack.xml
- namespace: `com.rrsjk.light.dao.evaluate.LightStationEvaluationTeamFeedBackDao`
- statements: `insert:create`, `select:getById`, `update:update`, `select:findFeedBacksByTime`, `delete:deleteById`, `select:findRecentFeedBacksByMemberId`, `select:findBy`, `select:countOf`
- tables: `id`, `light_sub_sp`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/lightUpload/LightBatchUploadMapper.xml
- namespace: `com.rrsjk.light.dao.lightUpload.LightBatchUploadDao`
- statements: `select:get`, `select:countOf`, `select:findBy`, `insert:create`, `insert:batchInsert`, `update:updateById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/wms/LightStoreAddress.xml
- namespace: `com.rrsjk.light.dao.wms.LightStoreAddressDao`
- statements: `select:findBy`, `select:countOf`, `select:findByForCbs`, `select:countOfCbs`, `insert:create`, `update:update`, `insert:batchInsert`, `update:batchUpdateStatus`, `select:getById`
- tables: `id`, `light_sp_store`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/wms/LightSpecialOutboundApplyDetail.xml
- namespace: `com.rrsjk.light.dao.wms.LightSpecialOutboundApplyDetailDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:findById`, `select:findByApplyId`, `delete:deleteByApplyId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/wms/LightSpecialOutboundSapRecord.xml
- namespace: `com.rrsjk.light.dao.wms.LightSpecialOutboundSapRecordDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `select:findById`, `select:findByUseOrderNo`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/wms/LightSpecialOutboundApplyImg.xml
- namespace: `com.rrsjk.light.dao.wms.LightSpecialOutboundApplyImgDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:findById`, `select:findByApplyId`, `delete:deleteByApplyId`, `delete:deleteCompleteImgByApplyId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/wms/LightSpecialOutboundApply.xml
- namespace: `com.rrsjk.light.dao.wms.LightSpecialOutboundApplyDao`
- statements: `select:findBy`, `select:countOf`, `select:findByJoin`, `select:countOfJoin`, `insert:create`, `update:update`, `insert:batchInsert`, `select:findById`
- tables: `id`, `light_special_outbound_apply`, `light_special_outbound_apply_detail`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/wms/LightSpecialOutboundApplyAuditLog.xml
- namespace: `com.rrsjk.light.dao.wms.LightSpecialOutboundApplyAuditLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:findById`, `select:findByApplyId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/insurance/InsuranceRenewalStationLog.xml
- namespace: `com.rrsjk.light.dao.insurance.InsuranceRenewalStationLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/insurance/InsuranceRenewalAssemble.xml
- namespace: `com.rrsjk.light.dao.insurance.InsuranceRenewalAssembleDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByWaitUpdateRenewalStatus`, `select:findOneWaitPushBatchNo`, `select:findWaitGenerateBatchNo`, `update:updateBatchNoIfAbsent`, `update:updateSplitBatchNo`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/yuexiu/LightYueXiuIncomeBillException.xml
- namespace: `com.rrsjk.light.dao.yuexiu.LightYueXiuIncomeBillExceptionDao`
- statements: `select:findBy`, `select:countOf`, `select:findByJoin`, `select:countOfJoin`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`, `light_station_yuexiu`, `light_yue_xiu_income_bill_exception`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/gh/GhApiAccessLog.xml
- namespace: `com.rrsjk.light.dao.gh.GhApiAccessLogDao`
- statements: `select:findBy`, `insert:create`, `select:getById`, `select:findByMsgId`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/gh/GhBindStation.xml
- namespace: `com.rrsjk.light.dao.gh.GhBindStationDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/gh/GhSecondClassAccount.xml
- namespace: `com.rrsjk.light.dao.gh.GhSecondClassAccountDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `delete:delete`, `select:getByPhoneNumber`, `select:getWaitOpenByPhoneNumber`, `select:getByGhUserCode`, `select:getByPhoneNumberAndProjectCompanyCode`, `select:getByCertNoAndProjectCompanyCode`, `select:findOpenAndAuthorityAccount`, `select:findBalanceMoreThanZero`, `select:selectUniqueKey`, `select:findAccountByQueryJob`, `select:findAccountBalanceByQueryJob`, `select:findAccountBySignHoldingAgreement`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/gh/GhProjectCompanyAccount.xml
- namespace: `com.rrsjk.light.dao.gh.GhProjectCompanyAccountDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByProjectCompanyCode`, `select:getByGhProjectCode`, `select:getByBankCardNumber`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/dh/LightStationFlatRoof.xml
- namespace: `com.rrsjk.light.dao.dh.LightStationFlatRoofDao`
- statements: `select:findBy`, `select:getByStationCode`, `select:countOf`, `delete:deleteByStationCode`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/dh/StationRoofTypeImg.xml
- namespace: `com.rrsjk.light.dao.dh.StationRoofTypeImgDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/dh/DhSecondClassAccount.xml
- namespace: `com.rrsjk.light.dao.dh.DhSecondClassAccountDao`
- statements: `select:findBy`, `select:countOf`, `select:findByExcludingNoNeedStatus`, `select:countOfExcludingNoNeedStatus`, `insert:create`, `update:update`, `select:getById`, `select:getByInputPieceId`, `select:findNoOpenAndNoSignAccount`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/dh/LightStationPitchedRoof.xml
- namespace: `com.rrsjk.light.dao.dh.LightStationPitchedRoofDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteByStationCode`, `select:getByStationCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/dh/DhBusinessOpportunity.xml
- namespace: `com.rrsjk.light.dao.dh.DhBusinessOpportunityDao`
- statements: `select:findBy`, `select:findByJoin`, `select:findDtoBy`, `select:countOf`, `select:countOfJoin`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByInputPieceId`, `select:getByStationNo`, `select:findByCbs`, `select:selectOption`, `select:findToUpdateContract`, `select:findToUpdateConfirmUrl`
- tables: `dh_business_opportunity`, `dh_second_class_account`, `id`, `light_sp_staff`, `light_station_contract_record`, `light_sub_sp`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/dh/DhSecondClassAccountOpenRecord.xml
- namespace: `com.rrsjk.light.dao.dh.DhSecondClassAccountOpenRecordDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `select:getById`, `select:getByAccountId`, `select:getByInputPieceId`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/dh/DhApiInteractionLog.xml
- namespace: `com.rrsjk.light.dao.dh.DhApiInteractionLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/dh/DhStationContractShareRule.xml
- namespace: `com.rrsjk.light.dao.dh.DhStationContractShareRuleDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findBy`, `delete:deleteById`, `insert:batchInsert`, `delete:batchDeleteByContractId`
- tables: `id`, `light_station_contract_share_rule`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/dh/DhLightStation.xml
- namespace: `com.rrsjk.light.dao.dh.DhLightStationDao`
- statements: `select:findBy`, `select:startToFirstInputPiece`, `select:findByJoin`, `select:countOf`, `select:countOfJoin`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByStationCode`, `update:deleteByStationCode`, `select:getByInputPieceId`, `select:findByCbsRefactor`, `select:findByCbs`, `select:countOfByCbsRefactor`, `select:countOfByCbs`
- tables: `dh_business_opportunity`, `id`, `light_station`, `light_station_audit`, `light_station_plan_config`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/dh/LightStationFloorRoof.xml
- namespace: `com.rrsjk.light.dao.dh.LightStationFloorRoofDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteByStationCode`, `select:getByStationCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/dh/DhFirstInputPiece.xml
- namespace: `com.rrsjk.light.dao.dh.DhFirstInputPieceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:deleteByInputPieceId`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByCbs`, `select:countOfCbs`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/dh/DhFileModule.xml
- namespace: `com.rrsjk.light.dao.dh.DhFileModuleDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:deleteByInputPieceId`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/roboAdvisor/LightRoboAdvisorOrder.xml
- namespace: `com.rrsjk.light.dao.roboAdvisor.LightRoboAdvisorOrderDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByOrderNo`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/roboAdvisor/LightRoboAdvisorSku.xml
- namespace: `com.rrsjk.light.dao.roboAdvisor.LightRoboAdvisorSkuDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:disableByOrderId`, `update:updateMakeOrderIdByOrderId`, `select:findByOrderId`, `select:findByMakeOrderId`, `select:findGroupBySku`, `select:findDetailByOrderId`
- tables: `id`, `light_sku_data`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/payment/CnnNuclearProjectInvoice.xml
- namespace: `com.rrsjk.light.dao.cnnPayment.CnnNuclearProjectInvoiceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/payment/CnnNuclearProjectPayment.xml
- namespace: `com.rrsjk.light.dao.cnnPayment.CnnNuclearProjectPaymentDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/cmbleasing/CmbOperatorLog.xml
- namespace: `com.rrsjk.light.dao.cmbleasing.CmbOperatorLogDao`
- statements: `select:findBy`, `select:getOperatorLogByStationCode`, `select:selectLatest`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/cmbleasing/CmbLeasingStation.xml
- namespace: `com.rrsjk.light.dao.cmbleasing.CmbLeasingStationDao`
- statements: `select:findBy`, `select:findBySort`, `select:findBySortFailedReasonNull`, `select:findByJoin`, `select:countOf`, `select:countOfJoin`, `insert:create`, `insert:insertActionLog`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByStationCode`, `select:getCmbRegion`, `select:getPrice`, `select:getPriceV2`
- tables: `cmb_base_region`, `cmb_channel_log`, `cmb_electric_price`, `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/cmbleasing/CmbPushFile.xml
- namespace: `com.rrsjk.light.dao.cmbleasing.CmbPushFileDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByStationCode`, `delete:deleteByStationCode`, `delete:deleteByStationCodeAndFileName`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/electric/LightStationElecTemplateMapping.xml
- namespace: `com.rrsjk.light.dao.electric.LightStationElecTemplateMappingDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:get`, `select:getByIds`, `select:findAll`, `select:findBy`, `select:countOf`, `select:findByStationElecNo`, `select:exportBy`, `select:getByStationElecNoAndTemplateCode`, `select:findByStationElecNos`, `delete:deleteById`, `delete:deleteByStationElecNos`
- tables: `id`, `light_invoice_template`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/hrflc/HrflcProjectReform.xml
- namespace: `com.rrsjk.light.dao.hrflc.HrflcProjectReformDao`
- statements: `select:getById`, `insert:create`, `update:updateById`, `insert:batchInsert`, `select:countOf`, `select:findBy`, `select:findByCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/hrflc/HrflcStationElecPushHistoryMapper.xml
- namespace: `com.rrsjk.light.mapper.HrflcStationElecPushHistoryMapper`
- statements: `select:selectByPrimaryKey`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`
- tables: `hrflc_station_elec_push_history`, `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/hrflc/HrflcPvMaterialCofng.xml
- namespace: `com.rrsjk.light.dao.hrflc.HrflcPvMaterialConfigDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/hrflc/HrflcPvPriceConfig.xml
- namespace: `com.rrsjk.light.dao.hrflc.HrflcPvPriceConfigDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getPrice`, `update:batchDisable`, `select:selectPriceByMultiCondition`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/hrflc/HrflcAuditOwner.xml
- namespace: `com.rrsjk.light.dao.hrflc.HrflcAuditOwnerDao`
- statements: `select:findBy`, `select:findByIdCardNoAndCertificateNumber`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findPendingCreditQuery`, `select:findByIdCardNo`, `select:findAllWaitingAudit`, `select:findByIdCardNoAndSource`, `select:findByIdCardNoAndCertificateCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/hrflc/HrflcRelecodeDetailInfoDao.xml
- namespace: `com.rrsjk.light.dao.hrflc.HrflcRelecodeDetailInfoDao`
- statements: `select:getById`, `select:findBy`, `select:countOf`, `insert:create`, `insert:batchInsert`, `update:update`, `delete:deleteById`
- tables: `hrflc_relecode_detail_info`, `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/hrflc/HrflcStationElecPushRecordMapper.xml
- namespace: `com.rrsjk.light.mapper.HrflcStationElecPushRecordMapper`
- statements: `select:selectById`, `insert:insertSelective`, `update:updateById`
- tables: `hrflc_station_elec_push_record`, `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/hrflc/HrflcPvFileRecord.xml
- namespace: `com.rrsjk.light.dao.hrflc.HrflcPvFileRecordDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/hrflc/HrflcOperationLog.xml
- namespace: `com.rrsjk.light.dao.hrflc.HrflcOperationLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getLatestByStationCode`, `select:findByCondition`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/hrflc/HrflcPvFileRecordHistory.xml
- namespace: `com.rrsjk.light.dao.hrflc.HrflcPvFileRecordHistoryDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/hrflc/HrflcRegionDict.xml
- namespace: `com.rrsjk.light.dao.hrflc.HrflcRegionDictDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/hrflc/LightStationHrflcMapper.xml
- namespace: `com.rrsjk.light.dao.hrflc.LightStationHrflcDao`
- statements: `select:get`, `select:getByStationCode`, `select:getByStationId`, `select:countOf`, `select:findBy`, `select:findByNoPage`, `insert:create`, `update:update`, `delete:delete`, `update:updateByStationId`
- tables: `id`, `light_station_hrflc`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/hrflc/HrflcRelecodeInvoiceInfoDao.xml
- namespace: `com.rrsjk.light.dao.hrflc.HrflcRelecodeInvoiceInfoDao`
- statements: `select:getById`, `select:findBy`, `select:findByPage`, `select:countOfPage`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `delete:deleteById`
- tables: `hrflc_relecode_invoice_info`, `hrflc_sync_pv_info`, `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/hrflc/HrflcSyncPvInfo.xml
- namespace: `com.rrsjk.light.dao.hrflc.HrflcSyncPvInfoDao`
- statements: `select:findBy`, `select:findDataToHandle`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByStationCode`, `select:getIdCardDetail`, `select:selectSyncInfoByStationCodes`, `select:findUnPushHistoryData`, `select:findUnPushElecDataNow`
- tables: `hrflc_station_elec_push_now`, `hrflc_sync_pv_info`, `huarong_id_card_info`, `id`, `light_station`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/hrflc/HrflcSyncPvResultQuery.xml
- namespace: `com.rrsjk.light.dao.hrflc.HrflcSyncPvResultQueryDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `insert:createNew`, `update:update`, `update:updateNew`, `insert:batchInsert`, `select:getById`, `select:findByReqContNumber`, `select:findByReqContNumberNew`
- tables: `hrflc_sync_pv_result_query_new`, `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/hrflc/HrflcChannelLog.xml
- namespace: `com.rrsjk.light.dao.hrflc.HrflcChannelLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/hrflc/HrflcStationElecPushNowMapper.xml
- namespace: `com.rrsjk.light.mapper.HrflcStationElecPushNowMapper`
- statements: `select:selectById`, `insert:insertSelective`, `update:updateById`, `update:updateByCode`, `update:updateDataUnPush`, `select:findByStationCode`, `select:findNeedPushStationCode`, `select:getUnInsertData`
- tables: `hrflc_station_elec_push_now`, `hrflc_sync_pv_info`, `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/warn/LightUnfinishedStationWarn.xml
- namespace: `com.rrsjk.light.dao.warn.LightUnfinishedStationWarnDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:findById`
- tables: `id`, `light_sub_sp`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/policy/LightAnnualScalePolicyStaging.xml
- namespace: `com.rrsjk.light.dao.policy.LightAnnualScalePolicyStagingDao`
- statements: `select:getById`, `select:getByMerchantAndYear`, `select:countOf`, `select:pageQuery`, `select:listByYear`, `insert:insert`, `update:update`, `update:deleteById`
- tables: `id`, `light_annual_scale_policy_staging`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/policy/LightAnnualScalePolicyMonthlyDetail.xml
- namespace: `com.rrsjk.light.dao.policy.LightAnnualScalePolicyMonthlyDetailDao`
- statements: `select:getById`, `select:listByMonthlyId`, `select:listByMerchantYearMonth`, `select:listByYearMonth`, `select:findNoCostVoucherByStationCode`, `select:findByStationCode`, `select:getByMonthlyIds`, `select:sumPriceByMerchantIdAndYear`, `insert:insert`, `insert:batchInsert`, `update:update`, `update:removeCostVoucher`, `update:deleteById`, `update:deleteByMonthlyId`
- tables: `id`, `light_annual_scale_policy_monthly`, `light_annual_scale_policy_monthly_detail`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/policy/LightAnnualScalePolicyStagingDetail.xml
- namespace: `com.rrsjk.light.dao.policy.LightAnnualScalePolicyStagingDetailDao`
- statements: `select:getById`, `select:listByStagingId`, `select:listByStagingIds`, `select:listByMonth`, `select:countOf`, `select:pageQuery`, `insert:insert`, `update:update`, `update:deleteById`
- tables: `id`, `light_annual_scale_policy_staging_detail`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/policy/LightAnnualScalePolicyDetail.xml
- namespace: `com.rrsjk.light.dao.policy.LightAnnualScalePolicyDetailDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:findById`, `select:findByPolicyId`, `select:findByPolicyNo`
- tables: `id`, `light_annual_scale_policy`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/policy/LightAnnualScalePolicyMonthly.xml
- namespace: `com.rrsjk.light.dao.policy.LightAnnualScalePolicyMonthlyDao`
- statements: `select:getById`, `select:getByMerchantYearMonth`, `select:listByMerchantYear`, `select:listByYearAndMonth`, `select:countOf`, `select:pageQuery`, `insert:insert`, `update:update`, `update:deleteById`
- tables: `id`, `light_annual_scale_policy_monthly`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/policy/LightAnnualScalePolicy.xml
- namespace: `com.rrsjk.light.dao.policy.LightAnnualScalePolicyDao`
- statements: `select:getById`, `select:listEnable`, `insert:insert`, `update:update`, `update:deleteById`, `select:findByYear`
- tables: `id`, `light_annual_scale_policy`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/policy/LightMerchantDepositChange.xml
- namespace: `com.rrsjk.light.dao.policy.LightMerchantDepositChangeDao`
- statements: `select:getById`, `select:listByMerchantId`, `select:countOf`, `select:pageQuery`, `select:listAnnualServiceProvider`, `insert:insert`, `update:update`, `update:deleteById`
- tables: `id`, `light_merchant_deposit_change`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/puyin/PuYinSettleQueue.xml
- namespace: `com.rrsjk.light.dao.puyin.PuYinSettleQueueDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByStationCode`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/puyin/PuYinTradePriceConfig.xml
- namespace: `com.rrsjk.light.dao.puyin.PuYinTradePriceConfigDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:findByP_CWithoutRegion`, `update:updateDisableByBatchNo`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/puyin/PuYinTradeIncomSettle.xml
- namespace: `com.rrsjk.light.dao.puyin.PuYinTradeIncomeSettleDao`
- statements: `insert:create`, `update:update`, `update:updateByBatchNo`, `update:updateByStationCode`, `select:get`, `select:countOf`, `select:findBy`, `insert:batchInsert`, `delete:deleteByBatchNo`, `select:getLatestByStationCode`, `select:existsByStationCode`, `select:findActiveStationCodes`, `select:getLatestIncomeTime`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/inventoryAge/SpSkuInventoryAge.xml
- namespace: `com.rrsjk.light.dao.inventoryAge.SpSkuInventoryAgeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByBatchConditions`, `select:findBySkuCodes`, `update:batchUpdate`, `delete:deleteAll`
- tables: `id`, `sp_sku_inventory_age`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/inventoryAge/TotalInventoryAge.xml
- namespace: `com.rrsjk.light.dao.inventoryAge.TotalInventoryAgeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findBySkuCodes`, `update:batchUpdate`, `delete:deleteAll`
- tables: `id`, `total_inventory_age`

## rrsjk-light-service/rrsjk-light-impl/src/main/resources/mybatis/mapper/powerpurchase/PowerPurchaseManagement.xml
- namespace: `com.rrsjk.light.dao.powerpurchase.PowerPurchaseManagementDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-service/rrsjk-light-impl/src/main/java/com/rrsjk/light/dao/LightSpOperateLog.xml
- namespace: `com.rrsjk.light.dao.LightSpOperateLogDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/upp/InvoiceCheckMapper.xml
- namespace: `com.rrsjk.finance.upp.dao.InvoiceCheckDao`
- statements: `select:queryCountBy`, `select:queryListBy`, `select:findOneByParams`, `insert:createList`, `insert:insert`, `update:update`, `select:isExist`, `delete:delete`, `update:updateByBatchNo`, `select:findListByIds`, `select:findOneById`, `select:findListByBatchNo`, `update:updateInvoiceByIds`, `update:updateBatchIdToNullById`, `delete:deleteInvoiceCheckPhy`, `select:findDeletedInvoiceList`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/upp/UppInvoiceRecordMapper.xml
- namespace: `com.rrsjk.finance.upp.dao.UppInvoiceRecordDao`
- statements: `select:findOneByParams`, `insert:insert`, `insert:insertList`, `update:update`, `update:updateByBatchNo`, `select:findListByBatchNo`, `delete:deleteByBatchNo`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/upp/UppRecordMapper.xml
- namespace: `com.rrsjk.finance.upp.dao.UppRecordDao`
- statements: `select:queryCountBy`, `select:queryListBy`, `insert:insert`, `update:update`, `update:updateByBatchNo`, `select:findOneByBatchNo`, `select:findOneByParams`, `select:findNeedPushUpp`, `select:findNeedSyncStatus`, `select:findNeedPullVoucherFromUpp`, `select:findNeedUpdateVoucher`, `delete:deleteByBatchNo`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/upp/UppOrderRecordMapper.xml
- namespace: `com.rrsjk.finance.upp.dao.UppOrderRecordDao`
- statements: `insert:insert`, `insert:insertList`, `update:update`, `update:updateByBatchNo`, `select:findOneByParams`, `select:findListByBatchNo`, `delete:deleteByBatchNo`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/upp/ProfitCenterSetting.xml
- namespace: `com.rrsjk.finance.upp.dao.ProfitCenterSettingDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/purchase/PayAccountQuotaReport.xml
- namespace: `com.rrsjk.finance.purchase.dao.PayAccountQuotaReportDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/purchase/EaiOpenMapper.xml
- namespace: `com.rrsjk.finance.purchase.dao.EaiOpenDao`
- statements: `select:getEainame`, `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `eai_open`, `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/purchase/PurchaseApplySettleMapper.xml
- namespace: `com.rrsjk.finance.purchase.dao.PurchaseApplySettleDao`
- statements: `select:getApplyNo`, `select:getById`, `insert:insert`, `update:update`, `select:selectRecord`, `select:selectAllRecord`, `select:selectToBccRecord`, `select:findCount`, `select:findAllCount`, `update:updateById`, `update:updateInvoice`, `select:findBySupplier`, `update:completeUpdate`, `select:findYbzSettleCount`, `select:getApplyNoList`
- tables: `id`, `purchase_apply_settle`, `purchase_apply_settle_log`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/purchase/PurchaseApplySettleAttachment.xml
- namespace: `com.rrsjk.finance.purchase.dao.PurchaseApplySettleAttachmentDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/purchase/BccRebateRecordMapper.xml
- namespace: `com.rrsjk.finance.purchase.dao.BccRebateRecordDao`
- statements: `insert:create`, `update:update`, `select:countOf`, `select:findBy`, `select:selectBccRecordResult`, `select:findByRowId`, `select:findById`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/purchase/LightSpNameChange.xml
- namespace: `com.rrsjk.finance.purchase.dao.LightSpNameChangeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/purchase/LightAuxiliaryMaterialQuotaExchange.xml
- namespace: `com.rrsjk.finance.purchase.dao.LightAuxiliaryMaterialQuotaExchangeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/purchase/PurchaseApplySettleDeduction.xml
- namespace: `com.rrsjk.finance.purchase.dao.PurchaseApplySettleDeductionDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/purchase/PurchaseApplySettleQuotaAudit.xml
- namespace: `com.rrsjk.finance.purchase.dao.PurchaseApplySettleQuotaAuditDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/purchase/PurchaseApplySettleQuotaLog.xml
- namespace: `com.rrsjk.finance.purchase.dao.PurchaseApplySettleQuotaLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/purchase/PurchaseApplySettleNoPaper.xml
- namespace: `com.rrsjk.finance.purchase.dao.PurchaseApplySettleNoPaperDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByApplyNo`, `select:getByOssKey`, `select:findWaitConfirmBillRecord`, `select:findByWithSub`, `select:countOfWithSub`, `select:findYbzSettleCount`, `select:findByWithSubOperation`, `select:countOfWithSubOperation`
- tables: `id`, `purchase_apply_settle_no_paper`, `rrsjk_light.light_service_provider`, `rrsjk_light_operation.light_operation_provider`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/purchase/PayAccountQuotaConfig.xml
- namespace: `com.rrsjk.finance.purchase.dao.PayAccountQuotaConfigDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByOrderNo`, `select:findPayAccountList`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/purchase/PurchaseApplySettleLog.xml
- namespace: `com.rrsjk.finance.purchase.dao.PurchaseApplySettleLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByApplyNo`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/purchase/PayAccountQuotaConfigLog.xml
- namespace: `com.rrsjk.finance.purchase.dao.PayAccountQuotaConfigLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/purchase/PurchaseApplySettleDepositRefund.xml
- namespace: `com.rrsjk.finance.purchase.dao.PurchaseApplySettleDepositRefundDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByApplyNo`, `select:findListByParam`, `select:findCount`
- tables: `id`, `purchase_apply_settle_deposit_refund`, `rrsjk_light.light_service_provider`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/purchase/PurchaseApplySettleQuota.xml
- namespace: `com.rrsjk.finance.purchase.dao.PurchaseApplySettleQuotaDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/purchase/PayAccountQuotaOccupyRecord.xml
- namespace: `com.rrsjk.finance.purchase.dao.PayAccountQuotaOccupyRecordDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/purchase/DefaultPayTypeConfig.xml
- namespace: `com.rrsjk.finance.purchase.dao.DefaultPayTypeConfigDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findLatestConfig`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/haierRecruit/HaierRecruitXsSummary.xml
- namespace: `com.rrsjk.finance.haierRecruit.dao.HaierRecruitXsSummaryDao`
- statements: `insert:insert`, `insert:insertSelective`, `select:countOf`, `select:selectByMap`, `update:updateBySelective`, `select:selectNoRebate`, `select:getById`
- tables: `haier_recruit_xs_summary`, `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/haierRecruit/HaierRecruitSettleDetail.xml
- namespace: `com.rrsjk.finance.haierRecruit.dao.HaierRecruitSettleDetailDao`
- statements: `insert:create`, `insert:insertSelective`, `select:countOf`, `select:findBy`, `update:updateByMap`, `select:SummaryXSCommisions`, `update:updateXSCommision`, `update:updateXSCommisionResult`
- tables: `haier_recruit_settle_detail`, `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/haierRecruit/HaierRecruitPayDetail.xml
- namespace: `com.rrsjk.finance.haierRecruit.dao.HaierRecruitPayDetailDao`
- statements: `insert:create`, `insert:insertSelective`, `update:updateByMap`, `select:findBy`, `select:countOf`, `select:selectByMap`, `select:selectNeedingInvoice`, `update:updateBySelective`
- tables: `haier_recruit_pay_detail`, `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/zerocarbon/BudgetOccupationRequestSubRecord.xml
- namespace: `com.rrsjk.finance.zerocarbon.dao.BudgetOccupationRequestSubRecordDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:selectAll`, `select:findBy`, `select:count`
- tables: `budget_occupation_sub_flow_record`, `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonInvoiceCheckMapper.xml
- namespace: `com.rrsjk.finance.zerocarbon.dao.ZeroCarbonInvoiceCheckDao`
- statements: `select:queryCountBy`, `select:queryListBy`, `select:findOneByParams`, `insert:createList`, `insert:insert`, `update:update`, `select:isExist`, `delete:delete`, `update:updateByBatchNo`, `select:findListByIds`, `select:findOneById`, `select:findListByBatchNo`, `update:updateInvoiceByIds`, `update:updateBatchIdToNullById`, `delete:deleteInvoiceCheckPhy`, `select:findDeletedInvoiceList`, `select:findInIds`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonInstallBill.xml
- namespace: `com.rrsjk.finance.zerocarbon.dao.ZeroCarbonInstallBillDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `update:updateByApplyNo`, `select:getById`, `select:getByApplyNo`, `select:selectAll`, `select:findBy`, `select:findByWithBillStatus`, `select:queryInstallationFeeForSettle`, `select:count`, `select:findInIds`, `select:findInIdsAndStatus`
- tables: `id`, `zero_carbon_apply_settle`, `zero_carbon_install_bill`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/zerocarbon/YbzBillQueryResult.xml
- namespace: `com.rrsjk.finance.zerocarbon.dao.YbzBillQueryResultDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:selectAll`, `select:findBy`, `select:count`
- tables: `id`, `ybz_bill_query_result`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonDepositRecord.xml
- namespace: `com.rrsjk.finance.zerocarbon.dao.ZeroCarbonDepositRecordDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `update:updateByApplyNo`, `select:getById`, `select:getByDbNo`, `select:getByApplyNo`, `select:selectAll`, `select:findBy`, `select:findByCondition`, `select:count`, `select:findInIdsAndStatus`, `select:queryRecordListForApplySettle`
- tables: `id`, `zero_carbon_deposit_record`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/zerocarbon/BudgetOccupationResponseRecord.xml
- namespace: `com.rrsjk.finance.zerocarbon.dao.BudgetOccupationResponseRecordDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:selectAll`, `select:findBy`, `select:count`
- tables: `budget_occupation_response_record`, `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonApplySettleNoPaper.xml
- namespace: `com.rrsjk.finance.zerocarbon.dao.ZeroCarbonApplySettleNoPaperDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `update:updateByApplyNo`, `select:getById`, `select:getByApplyNo`, `select:selectAll`, `select:findBy`, `select:count`, `select:getByOssKey`
- tables: `id`, `zero_carbon_apply_settle_no_paper`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/zerocarbon/YbzBillMainResponseRecord.xml
- namespace: `com.rrsjk.finance.zerocarbon.dao.YbzBillMainResponseRecordDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:selectAll`, `select:findBy`, `select:count`
- tables: `id`, `ybz_bill_main_response_record`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonApplySettleDepositRefund.xml
- namespace: `com.rrsjk.finance.zerocarbon.dao.ZeroCarbonApplySettleDepositRefundDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `update:updateByApplyNo`, `select:getById`, `select:getByApplyNo`, `select:selectAll`, `select:findBy`, `select:count`
- tables: `id`, `zero_carbon_apply_settle_deposit_refund`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonApplySettleLog.xml
- namespace: `com.rrsjk.finance.zerocarbon.dao.ZeroCarbonApplySettleLogDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:selectAll`, `select:findBy`, `select:findByTypeList`, `select:count`
- tables: `id`, `zero_carbon_apply_settle_log`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonApplySettle.xml
- namespace: `com.rrsjk.finance.zerocarbon.dao.ZeroCarbonApplySettleDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `update:updateByApplyNo`, `select:getById`, `select:getApplyNo`, `select:selectAll`, `select:findBy`, `select:count`, `select:queryBudgetOccupyApplyList`, `select:querySettleListForYbz`, `select:queryYbzStatusList`, `select:queryLightInstallationFeeStatusList`, `select:getOccupyPage`, `select:countOccupy`
- tables: `id`, `purchase_apply_settle`, `zero_carbon_apply_settle`, `zero_carbon_install_bill`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/zerocarbon/BudgetOccupationRequestRecord.xml
- namespace: `com.rrsjk.finance.zerocarbon.dao.BudgetOccupationRequestRecordDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:selectAll`, `select:findBy`, `select:count`
- tables: `budget_occupation_request_record`, `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/zerocarbon/ZeroCarbonCloudReportBillMain.xml
- namespace: `com.rrsjk.finance.zerocarbon.dao.ZeroCarbonCloudReportBillMainDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:selectAll`, `select:findBy`, `select:count`
- tables: `id`, `ybz_bill_main_request_record`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/zerocarbon/YbzBillRequestParamRecord.xml
- namespace: `com.rrsjk.finance.zerocarbon.dao.YbzBillRequestParamRecordDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:selectAll`, `select:findBy`, `select:count`
- tables: `id`, `ybz_bill_request_param_record`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/api/RebatesMapper.xml
- namespace: `com.rrsjk.finance.api.dao.RebatesDao`
- statements: `select:queryDateList`, `select:queryCloudWisdomDateList`, `select:queryByDateList`, `select:queryByCloudWisdomDateList`
- tables: `order_item_fee_self`, `settlement_third_order_item`, `settlement_third_order_item_commission`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/report/ReportIncomeRecordMapper.xml
- namespace: `com.rrsjk.finance.report.dao.ReportIncomeRecordDao`
- statements: `insert:insert`, `select:isExist`, `select:isExistByTaxAmount`, `insert:batchInsert`, `select:getThisMonthIncome`, `select:getThisDayIncome`, `select:countOf`, `select:findBy`, `select:findSumBy`, `select:findOtherIncome`, `select:findOtherIncomeByOrderItemList`
- tables: `report_income_record`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/report/ReportReceiptRecordMapper.xml
- namespace: `com.rrsjk.finance.report.dao.ReportReceiptRecordDao`
- statements: `select:isExist`, `insert:batchInsert`, `select:getThisMonthReceipt`, `select:getThisDayReceipt`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/report/ReportOrderRecordMapper.xml
- namespace: `com.rrsjk.finance.report.dao.ReportOrderRecordDao`
- statements: `insert:insert`, `select:isExist`, `update:update`, `select:getThisMonthOrderNumber`, `select:getThisDayOrderNumber`, `select:getThisMonthOrderAmount`, `select:getThisDayOrderAmount`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/cloudWisdom/CloudWisdomUserWalletMapper.xml
- namespace: `com.rrsjk.finance.cloudWisdom.dao.CloudWisdomUserWalletDao`
- statements: `insert:insert`, `update:update`, `select:getByMemberId`
- tables: `cloud_wisdom_user_wallet`, `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/cloudWisdom/CloudWisdomUserWalletLogMapper.xml
- namespace: `com.rrsjk.finance.cloudWisdom.dao.CloudWisdomUserWalletLogDao`
- statements: `insert:insert`, `update:update`, `update:updateReceiptVoucher`, `select:isExist`, `select:countOf`, `select:findBy`, `select:getByTypeAndSerialNumber`, `select:findNeedCheckLog`
- tables: `cloud_wisdom_user_wallet_log`, `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/cloudWisdom/CloudWisdomWalletRechargeMapper.xml
- namespace: `com.rrsjk.finance.cloudWisdom.dao.CloudWisdomWalletRechargeDao`
- statements: `insert:insert`, `update:update`, `select:countOf`, `select:findBy`, `select:findCustomerCode`
- tables: `cloud_wisdom_wallet_recharge`, `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/lnThirdOrder/LnThirdFeeRecordMapper.xml
- namespace: `com.rrsjk.finance.lnThirdOrder.dao.LnThirdFeeRecordDao`
- statements: `insert:insert`, `select:isExist`, `update:update`, `update:updateByIds`, `select:countOf`, `select:findBy`, `select:findBySettledId`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/lnThirdOrder/LnThirdCommissionPaymentRecordMapper.xml
- namespace: `com.rrsjk.finance.lnThirdOrder.dao.LnThirdCommissionPaymentRecordDao`
- statements: `insert:insert`, `select:isExist`, `update:update`, `select:findNeedSyncSap`, `select:countOf`, `select:findBy`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/lnThirdOrder/LnThirdOrderMapper.xml
- namespace: `com.rrsjk.finance.lnThirdOrder.dao.LnThirdOrderDao`
- statements: `insert:batchCreate`, `insert:create`, `select:countOf`, `select:findBy`, `select:findNeedCheck`, `update:update`
- tables: `id`, `order_date`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/mpcRebate/MpcRebateRecord.xml
- namespace: `com.rrsjk.finance.mpcRebate.dao.MpcRebateRecordDao`
- statements: `insert:insert`, `update:update`, `select:countOf`, `select:findBy`, `select:isExist`, `select:getBySettleDailySumIdAndType`, `select:findById`, `update:updateDailyRebateId`, `select:findNeedSyncSap`, `select:findNeedSyncSapChargeFee`, `select:findByCheckKJT`, `update:updateChecked`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/mpcRebate/KjtChargefeeTradeLog.xml
- namespace: `com.rrsjk.finance.mpcRebate.dao.KjtChargefeeTradeLogDao`
- statements: `insert:insert`, `update:update`, `select:getNeedCheckKJTChargeFee`, `update:updateChecked`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/mpcRebate/MpcRebateRecordDaily.xml
- namespace: `com.rrsjk.finance.mpcRebate.dao.MpcRebateRecordDailyDao`
- statements: `insert:insert`, `update:update`, `select:isExist`, `select:sumSuccessMpcRebateRecord`, `select:sumReExchangeMpcRebateRecord`
- tables: `id`, `mpc_rebate_record`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/mpcRebate/MpcRebateRecordLog.xml
- namespace: `com.rrsjk.finance.mpcRebate.dao.MpcRebateRecordLogDao`
- statements: `insert:insert`, `update:update`, `select:countOf`, `select:findBy`, `select:isExist`, `select:findByDocNo`, `select:findBack`, `select:getMPCRebateRecordLog`, `update:dealRebateLog`, `select:findBackBySys`, `select:getNoSyncBySys`, `select:getSuccessBySys`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/mpcRebate/AreaInfo.xml
- namespace: `com.rrsjk.finance.mpcRebate.dao.AreaInfoDao`
- statements: `select:findByAreaCode`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/customerManagement/MdrCustomerInfoMapper.xml
- namespace: `com.rrsjk.finance.customerManagement.dao.MdrCustomerInfoDao`
- statements: `select:isExist`, `select:isExistByCompanyCode`, `select:findRemainingAmount`, `insert:insert`, `update:update`, `update:updateRemainingAmountJoint`, `update:updateRemainingAmountRrs`, `select:findByMdmCodeIsNotNull`, `select:findCompanyDto`, `select:findFinancialSolutionsAmount`, `select:countOf`, `select:findBy`, `select:findByCompanyAndMdm`
- tables: `credit_customer_info`, `id`, `mdr_customer_contract_info`, `mdr_customer_info`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/customerManagement/MdrCustomerContractInfoMapper.xml
- namespace: `com.rrsjk.finance.customerManagement.dao.MdrCustomerContractInfoDao`
- statements: `insert:insert`, `select:isExist`, `select:countOf`, `select:findBy`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/customerManagement/MdrFinancialSolutionsMapper.xml
- namespace: `com.rrsjk.finance.customerManagement.dao.MdrFinancialSolutionsDao`
- statements: `insert:insert`, `select:isExist`, `update:update`, `select:countOf`, `select:findBy`, `select:findById`, `select:findFinancialSolutionsFinishedAmount`, `select:findFinancialSolutionsDoingAmount`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/customerManagement/MdrCustomerLimitLogMapper.xml
- namespace: `com.rrsjk.finance.customerManagement.dao.MdrCustomerLimitLogDao`
- statements: `insert:insert`, `update:update`, `select:isExist`, `select:isExistUseLog`, `select:isExistInitial`, `select:countOf`, `select:findBy`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/customerManagement/MdrCustomerOrderDetailsMapper.xml
- namespace: `com.rrsjk.finance.customerManagement.dao.MdrCustomerOrderDetailsDao`
- statements: `select:isExist`, `insert:insert`, `update:update`, `update:updateReceiptStatus`, `update:updateExpressReceived`, `select:countOf`, `select:overDueCountOf`, `select:customerOrderCountOf`, `select:customerOverDueCountOf`, `select:findBy`, `select:findOverDueList`, `select:findOrderDetailsList`, `select:findOverDueOrderDetailsList`, `select:findOverdueAmount`, `select:findReceivableAmount`
- tables: `id`, `mdr_customer_order_details`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/customerManagement/MdrFinancialSolutionsDetailsMapper.xml
- namespace: `com.rrsjk.finance.customerManagement.dao.MdrFinancialSolutionsDetailsDao`
- statements: `select:isExist`, `insert:insert`, `update:update`, `select:countOf`, `select:findBy`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/customerManagement/CreditCustomerInfoMapper.xml
- namespace: `com.rrsjk.finance.customerManagement.dao.CreditCustomerInfoDao`
- statements: `select:isExist`, `insert:insert`, `update:update`, `select:countOf`, `select:findBy`, `select:findCompanyDto`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/task/Task.xml
- namespace: `com.rrsjk.finance.task.dao.TaskDao`
- statements: `insert:create`, `select:get`, `select:getByDoneAtAndJobType`, `select:countOf`, `select:findBy`, `select:findByDoneAt`, `select:unfinished`, `select:getIngByType`, `update:fail`, `update:not`, `update:ing`, `update:done`
- tables: `id`, `task`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/error/FinanceErrorLogMapper.xml
- namespace: `com.rrsjk.finance.error.dao.FinanceErrorLogDao`
- statements: `delete:delete`, `select:getByCodeAndOrderItemNo`, `insert:insert`, `select:countOf`, `select:findBy`, `update:update`
- tables: `finance_error_log`, `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/settlement/CustomRebateSelfMonthly.xml
- namespace: `com.rrsjk.finance.settlement.summary.dao.CustomRebateSelfMonthlyDao`
- statements: `insert:insert`, `update:updateByExampleSelective`, `select:sumMonthlyCommission`
- tables: `id`, `order_item_fee_self`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/settlement/SettlementThirdOrderItemCommissionDailySum.xml
- namespace: `com.rrsjk.finance.settlement.summary.dao.SettlementThirdOrderItemCommissionDailySumDao`
- statements: `insert:insert`, `update:update`, `select:countOf`, `select:findBy`, `select:findSumBy`, `select:countDailyOf`, `select:findDailyBy`, `select:isExist`, `select:sumCustomSettlement`, `update:updateCustomRebateId`, `update:updateStatusByCustomRebateId`
- tables: `id`, `settlement_third_order_item_commission`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/settlement/CustomRebateSelf.xml
- namespace: `com.rrsjk.finance.settlement.summary.dao.CustomRebateSelfDao`
- statements: `insert:insert`, `update:update`, `update:updateRebatesMessage`, `select:countOf`, `select:findBy`, `select:findSumBy`, `select:getById`, `select:isExist`, `select:sumCustomCommission`, `select:findNeedRebates`
- tables: `id`, `order_item_fee_self`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/settlement/CashPoolThird.xml
- namespace: `com.rrsjk.finance.settlement.summary.dao.CashPoolThirdDao`
- statements: `insert:insert`, `update:update`, `select:countOf`, `select:findBy`, `select:findSumBy`, `select:isExist`, `select:sumCustomEarning`
- tables: `id`, `order_item_fee_third`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/settlement/CustomRebateThird.xml
- namespace: `com.rrsjk.finance.settlement.summary.dao.CustomRebateThirdDao`
- statements: `insert:insert`, `update:update`, `update:updateRebatesMessage`, `select:countOf`, `select:findBy`, `select:findSumBy`, `select:getById`, `select:isExist`, `select:sumCustomRebate`, `select:findNeedRebates`
- tables: `id`, `settlement_third_order_item_commission_daily_sum`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/settlement/SelfIncomeInvoices.xml
- namespace: `com.rrsjk.finance.settlement.summary.dao.SelfIncomeInvoicesDao`
- statements: `insert:insert`, `update:update`, `select:getById`, `select:isExist`, `select:findInvoicing`, `select:findSyncSap`, `select:countOfSelfIncomeInvoices`, `select:findSelfIncomeInvoices`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/settlement/SellerOrderInvoice.xml
- namespace: `com.rrsjk.finance.settlement.summary.dao.SellerOrderInvoiceDao`
- statements: `insert:insert`, `update:update`, `select:isExist`, `select:sumLnInvoice`, `select:findNeedInvoice`, `select:findInvoicing`, `select:countOfSellerOrderInvoice`, `select:findSellerOrderInvoice`
- tables: `id`, `seller_order_invoice`, `settlement_third_order_item_commission`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/bill/BillAlipay.xml
- namespace: `com.rrsjk.finance.bill.dao.BillAlipayDao`
- statements: `insert:insert`, `select:get`, `select:findByTradeNo`, `select:findByMerchantNo`, `select:findByIwAccountLogId`, `select:find`, `select:countOf`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/bill/BillNetPay.xml
- namespace: `com.rrsjk.finance.bill.dao.BillNetPayDao`
- statements: `insert:create`, `update:update`, `select:selectOne`, `select:selectList`, `select:findPageCount`, `select:findPage`
- tables: `bill_net_pay`, `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/bill/BillCcb.xml
- namespace: `com.rrsjk.finance.bill.dao.BillCcbDao`
- statements: `insert:insert`, `select:getByTradeNo`, `select:countOf`, `select:find`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/bill/BillWechat.xml
- namespace: `com.rrsjk.finance.bill.dao.BillWechatDao`
- statements: `insert:insert`, `select:findByTransactionId`, `select:isExist`, `select:find`, `select:countOf`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/bill/Bill.xml
- namespace: `com.rrsjk.finance.bill.dao.BillDao`
- statements: `insert:insert`, `update:update`, `select:findByTradeNo`, `select:findByTradeNoAndType`, `select:findByPaymentNo`, `select:findByPaymentNoAndType`, `select:getBy`, `update:updateCommision`, `update:updateFee`, `select:countOf`, `select:find`, `select:findByTradeAtAndPayChannel`, `select:getSelfOrderItemVoucher`, `select:getThirdOrderItemVoucher`, `select:getOutBusinessFeeVoucher`
- tables: `bill`, `cash_self_order_item`, `id`, `order_item_fee_third`, `out_business_fee`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/ybz/YbzRecord.xml
- namespace: `com.rrsjk.finance.ybz.dao.YbzRecordDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findCount`, `select:getByApplyNo`
- tables: `id`, `purchase_apply_settle`, `ybz_record`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/ybz/LightRentPaymentRecord.xml
- namespace: `com.rrsjk.finance.ybz.dao.LightRentPaymentRecordDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByRelationNo`, `select:findByRelationNoList`, `delete:deleteByRelationNo`, `select:findNeedReconfirmList`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/ybz/YbzRecordParam.xml
- namespace: `com.rrsjk.finance.ybz.dao.YbzRecordParamDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/sap/SapOrderRecordMapper.xml
- namespace: `com.rrsjk.finance.sap.dao.SapOrderRecordDao`
- statements: `select:getBybstkd`, `insert:insert`, `update:update`
- tables: `id`, `sap_order_record`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/sap/SapHandIncomeMapper.xml
- namespace: `com.rrsjk.finance.sap.dao.SapHandIncomeDao`
- statements: `insert:batchInsert`, `insert:insert`, `select:selectRecord`, `select:countRecord`
- tables: `sap_hand_income`, `sap_relation`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/sap/LightSapLedgerQueue.xml
- namespace: `com.rrsjk.finance.sap.dao.LightSapLedgerQueueDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findBySuccess`, `select:getByStationIdAndAction`, `select:findByStationIdAndAction`, `select:findBySuccessAction`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/sap/KingDieSapRecordMapper.xml
- namespace: `com.rrsjk.finance.sap.dao.KingDieSapRecordDao`
- statements: `select:getByBidAndYWMS`, `select:getValidByRowId`, `select:getValidByBidAndYWMS`, `insert:insert`, `insert:insertItems`, `update:update`, `delete:deleteItems`, `select:getByRowId`
- tables: `id`, `king_die_sap_item_record`, `king_die_sap_record`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/sap/CompanyExtrasDao.xml
- namespace: `com.rrsjk.finance.sap.dao.CompanyExtrasDao`
- statements: `select:findBy`, `select:getCompanyList`, `select:getByCompanyCode`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/sap/DepositRecord.xml
- namespace: `com.rrsjk.finance.sap.dao.DepositRecordDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:updateInvoiceBelnrByPurchaseNos`, `select:getByIds`, `select:findListByApplyNo`, `update:updateStatusAndApplyNoByIds`, `select:findPendingList`
- tables: `deposit_record`, `id`, `sap_purchase_record`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/sap/JointCompanyOrderRefundMapper.xml
- namespace: `com.rrsjk.finance.sap.dao.JointCompanyOrderRefundDao`
- statements: `select:findNeedSyncSap`, `select:isExist`, `insert:insert`, `update:update`
- tables: `id`, `joint_company_order_refund`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/sap/SapRecordMapper.xml
- namespace: `com.rrsjk.finance.sap.dao.SapRecordDao`
- statements: `select:getByRowId`, `select:getValidByRowId`, `select:getByBidAndYWMS`, `select:getValidByBidAndYWMS`, `insert:insert`, `insert:insertItems`, `update:update`, `select:findEPCIncomeByTime`, `select:findEPCIncomeByTimeCx`, `select:findLightPSIncomeByTime`, `select:findLightPSIncomeByTimeCx`, `select:findLightPSIncomeByTimeOther`, `select:findLightPSIncomeByTimeCxOther`, `select:findLightYuexiuIncome`, `select:findLightYuexiuIncomeCx`, `select:findPuYinIncome`, `select:findPuYinIncomeCx`, `select:findZhaoYinIncome`, `select:findZhaoYinIncomeCx`, `select:findLightYuexiuIncomeByStationCodeList`, `select:findLightYuexiuIncomeCxByStationCodeList`, `select:findLightYuexiuCostByStationCodeList`, `select:findLightYuexiuCostCxByStationCodeList`, `select:findLightIncome`, `select:findLightIncomeCx`, `select:findLNIncome`, `select:findLNIncomeCx`, `select:findZHIncome`, `select:findZHIncomeCx`, `select:findOpsIncome`, `select:findOpsIncomeCx`, `select:findZHIncomeByStationCodeList`, `select:findZHIncomeCxByStationCodeList`, `select:findZHCostByStationCodeList`, `select:findZHCostCxByStationCodeList`, `select:findNewEPCIncomeCombined`, `select:findNewEPCIncome`, `select:findNewEPCIncomeCx`, `select:findZHEPCIncomeBids`, `select:findZHEPCCXBids`, `select:findYXEPCIncomeBids`, `select:findYXEPCCXBids`, `select:findPuYinIncomeList`, `select:findManualIncome`, `select:findManualIncomeCx`, `select:getSapRecordsByBid`, `select:findByBidLeftAndBelnr`, `select:findIncomeOfStorageSales`
- tables: `id`, `sap_item_record`, `sap_record`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/sap/LightOpsSap.xml
- namespace: `com.rrsjk.finance.sap.dao.LightOpsSapDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findBySapStatus`, `select:countOf`, `select:findBy`, `select:findByTime`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/sap/LightIncomeRecord.xml
- namespace: `com.rrsjk.finance.sap.dao.LightIncomeRecordDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:getByOrderNo`, `select:findByInvoiceWaitSync`, `select:findNYBIncome`, `select:findNYBByStationList`
- tables: `id`, `light_income_record`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/sap/LightSaleOrder.xml
- namespace: `com.rrsjk.finance.sap.dao.LightSaleOrderDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByOrderNo`, `select:findByStatus`, `select:countOf`, `select:findBy`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/sap/SapReverseQueue.xml
- namespace: `com.rrsjk.finance.sap.dao.SapReverseQueueDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:findBySuccess`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/sap/SapRelation.xml
- namespace: `com.rrsjk.finance.sap.dao.SapRelationDao`
- statements: `select:get`, `select:isExist`, `select:getByOrderItemId`, `select:getByRepairOrderItemId`, `insert:insert`, `update:update`, `select:getSapRelationByPager`, `select:countSapRelation`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/sap/OrderToSapSelfAccountMapper.xml
- namespace: `com.rrsjk.finance.sap.dao.OrderToSapSelfAccountDao`
- statements: `insert:insertSapSelfAccount`, `select:isExist`, `select:findByAccountAt`, `select:findIncomeByParams`, `select:getSelfIncome`, `select:findCount`, `select:getSelfOrderIncome`, `select:getIncomeByOrderItemNo`, `select:findDomesticIncome`, `select:findOtherIncome`, `select:find1TP0Income`
- tables: `sap_self_account`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/sap/SapPurchaseRecordMapper.xml
- namespace: `com.rrsjk.finance.sap.dao.SapPurchaseRecordDao`
- statements: `select:findById`, `select:getPurchaseNo`, `select:getBySettleId`, `select:getByApplyNo`, `select:getByApplyNoList`, `select:getByEbeln`, `select:getByEbelnAndApplyNo`, `insert:insert`, `select:selectRecord`, `select:findCount`, `select:getRecordByIds`, `update:updateByIds`, `update:updateByPurchaseNos`, `update:update`, `update:updateSapPurchaseRecordStatus`, `select:getPurchaseOrderByPay`, `update:updateBySettledId`, `select:sumAmount`, `update:updateById`, `select:findInIds`, `update:updateByRelateSettle`, `select:findPsRecordByMonth`, `select:getPaidOutRecordByPurchaseNos`, `select:claimAmountSumBySupplierNo`, `select:isPaymenting`, `select:findCountByOperation`, `select:sumPriceBySpCodeAndPurchaseTypeAndStatusList`, `select:selectRecordByOperation`, `select:getByPurchaseNos`, `select:findByPurchaseType`, `select:findByStatusAndPurchaseType`
- tables: `OrderProducts`, `id`, `rrsjk_light.light_sp_ops_settle`, `rrsjk_light.light_sp_ops_settle_iac`, `sap_purchase_record`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/sap/SapPurchaseFreeze.xml
- namespace: `com.rrsjk.finance.sap.dao.SapPurchaseFreezeDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:updateByBatchNo`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/sap/OrderSapQueue.xml
- namespace: `com.rrsjk.finance.sap.dao.OrderSapQueueDao`
- statements: `insert:create`, `update:update`, `update:updateByOrderItemId`, `update:updateStatus`, `select:get`, `select:findBySuccess`, `select:getByOrderItemIdAction`, `select:getBySuccess`, `select:getByOrderItemIdAndAction`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/cashSummary/CashThirdOrderItem.xml
- namespace: `com.rrsjk.finance.cashSummary.dao.CashThirdOrderItemDao`
- statements: `insert:insert`, `update:update`, `select:isExist`, `select:sumCustomCash`, `select:countOf`, `select:findBy`, `select:findSumBy`, `select:countDailyOf`, `select:findDailyBy`
- tables: `id`, `order_item_fee_third`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/check/OrderItemUnCash.xml
- namespace: `com.rrsjk.finance.check.dao.OrderItemUnCashDao`
- statements: `insert:insert`, `update:update`, `select:isExist`, `select:getFirstUncheckedRefund`, `update:updatePayUnCashFromBill`, `update:updateVoucherPayFromBill`, `update:updateVoucherRefundFromBill`, `update:updateBalance`, `select:findNeedSyncSap`, `select:countOf`, `select:findBy`, `select:findSumOrderItemUnCash`
- tables: `bill`, `id`, `order_item_un_cash`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/check/OutBusinessFee.xml
- namespace: `com.rrsjk.finance.check.dao.OutBusinessFeeDao`
- statements: `insert:insert`, `update:update`, `select:isExist`, `select:countOf`, `select:findBy`, `select:findSumBy`, `select:findNeedSyncSap`, `update:updateThirdVoucher`, `update:updateSelfVoucher`
- tables: `cash_self_order_item`, `id`, `order_item_fee_third`, `out_business_fee`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/check/ServiceError.xml
- namespace: `com.rrsjk.finance.check.dao.ServiceErrorDao`
- statements: `insert:insert`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/check/OrderItemFeeThird.xml
- namespace: `com.rrsjk.finance.check.dao.OrderItemFeeThirdDao`
- statements: `insert:createList`, `select:isExist`, `select:findListByOrderItemNo`, `update:updateCustomCashId`, `select:findNeedSyncSap`, `update:update`, `select:countOf`, `select:findBy`, `select:findSumBy`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/check/OrderItemFeeSelf.xml
- namespace: `com.rrsjk.finance.check.dao.OrderItemFeeSelfDao`
- statements: `insert:insert`, `insert:insertList`, `update:update`, `select:countOf`, `select:findBy`, `select:findSumBy`, `select:findByFeeNo`, `select:findByOrderItemNo`, `update:updateByOrderItemNo`, `select:findOperatorCommissionList`, `select:getLeftCommisionInfo`, `select:loadMoreThanCommission`, `select:loadCommissionByCustomerAll`, `select:loadCommissionByCustomer`, `update:updateSummedAt`, `update:updateCustomRebateId`, `update:updateMonthlyCustomRebateId`, `select:sumCommissionBy`, `update:updateStatusByCustomRebateId`, `select:getListByCustomCommissionId`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/check/SettlementThirdOrderItem.xml
- namespace: `com.rrsjk.finance.check.dao.SettlementThirdOrderItemDao`
- statements: `insert:create`, `select:findByOrderItemNo`, `update:update`, `update:updateFinished`, `update:updateBalance`
- tables: `id`, `settlement_third_order_item`, `settlement_third_order_item_commission`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/check/CheckAccountError.xml
- namespace: `com.rrsjk.finance.check.dao.CheckAccountErrorDao`
- statements: `insert:insert`, `update:update`, `select:countOf`, `select:findBy`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/check/CashSelfOrderItem.xml
- namespace: `com.rrsjk.finance.check.dao.CashSelfOrderItemDao`
- statements: `insert:insert`, `update:update`, `update:updateByOrderItemNo`, `select:isExist`, `select:findNeedSyncSap`, `select:findSyncToSap`, `select:countOf`, `select:findBy`, `select:findSumSelfOrderItemDetail`
- tables: `id`

## rrsjk-finance-service/rrsjk-finance-impl/src/main/resources/mybatis/mapper/check/SettlementThirdOrderItemCommission.xml
- namespace: `com.rrsjk.finance.check.dao.SettlementThirdOrderItemCommissionDao`
- statements: `select:findListByOrderItemNo`, `select:findListByOrderItemNoFeeAmount`, `insert:createList`, `update:update`, `select:countOf`, `select:countOfByShop`, `select:findBy`, `select:findGoodsByShop`, `select:findNormalCommissionByShop`, `select:findCountyCommissionByShop`, `select:findNormalCommissionByOrderItemNo`, `select:findCountyCommissionByOrderItemNo`, `select:findByCustomerRebateId`, `select:findSumBy`, `update:updateSummedAt`, `update:updateCustomSettlementId`, `select:selectUpdateCustomSettlementIdCount`, `update:updateCustomRebateId`, `select:selectCountUpdateCustomRebateId`, `update:updateLnInvoiceId`, `update:updateBalance`, `update:updateStatusByCustomRebateId`, `update:updateByInvoiceId`, `update:updateReceiptSapVoucher`, `select:findNeedSyncSap`, `select:getNewRrsCommission`, `select:getNewThirdCommission`, `select:findNeedSyncInvoice`, `select:getListByCustomRebateId`, `update:updateSapCustomVoucher`, `update:updateSapCustomVoucherReExchange`, `select:findJointOrderList`, `select:findPlatformIncomeByParams`, `select:sumCustomEarningBy`, `select:findMpcNoByOrderItemNo`
- tables: `id`, `settlement_third_order_item`, `settlement_third_order_item_commission`

## vpp-openapi/vpp-openapi-biz/src/main/resources/mapper/SysPermissionMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.SysPermissionMapper`

## vpp-openapi/vpp-openapi-biz/src/main/resources/mapper/SysAccessKeyMapper.xml
- namespace: `com.nahui.energy.mapper.vpp.SysAccessKeyMapper`

## rrsjk-light-openapi-service/rrsjk-light-openapi-impl/src/main/resources/mybatis/mapper/report/EnergyOverdueInventoryControlDataBase.xml
- namespace: `com.rrsjk.openapi.dao.report.EnergyOverdueInventoryControlDataBaseDao`
- statements: `insert:create`, `insert:batchInsert`, `select:get`, `select:countOf`, `select:findBy`
- tables: `energy_overdue_inventory_control_data_base`

## rrsjk-light-openapi-service/rrsjk-light-openapi-impl/src/main/resources/mybatis/mapper/report/EnergyOverdueInventoryControlSku.xml
- namespace: `com.rrsjk.openapi.dao.report.EnergyOverdueInventoryControlSkuDao`
- statements: `insert:create`, `select:get`, `select:countOf`, `select:findBy`, `insert:batchInsert`

## rrsjk-light-openapi-service/rrsjk-light-openapi-impl/src/main/resources/mybatis/mapper/report/GvsWarehouseAgeAnalysis.xml
- namespace: `com.rrsjk.openapi.dao.report.GvsWarehouseAgeAnalysisDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:getGvsSummary`, `select:getSumGvsGroupBySku`, `select:countGroupByAgeStatus`, `select:findGroupByAgeStatus`, `select:findToSpData`, `select:findSkuInfo`
- tables: `gvs_warehouse_age_analysis`, `id`, `light_sku_data`, `sap_sp_center_relation`

## rrsjk-light-openapi-service/rrsjk-light-openapi-impl/src/main/resources/mybatis/mapper/report/EnergyOverdueInventoryControlCenter.xml
- namespace: `com.rrsjk.openapi.dao.report.EnergyOverdueInventoryControlCenterDao`
- statements: `insert:create`, `select:get`, `select:countOf`, `select:findBy`, `insert:batchInsert`

## rrsjk-light-openapi-service/rrsjk-light-openapi-impl/src/main/resources/mybatis/mapper/report/SapSpCenterRelation.xml
- namespace: `com.rrsjk.openapi.dao.report.SapSpCenterRelationDao`
- statements: `select:findAll`

## rrsjk-light-openapi-service/rrsjk-light-openapi-impl/src/main/resources/mybatis/mapper/report/EnergyLeasedStationAssetManagement.xml
- namespace: `com.rrsjk.openapi.dao.report.EnergyLeasedStationAssetManagementDao`
- statements: `select:findForZhaoYinBy`
- tables: `cmb_leasing_station`

## rrsjk-light-openapi-service/rrsjk-light-openapi-impl/src/main/resources/mybatis/mapper/report/EnergyOverdueInventoryControlSummary.xml
- namespace: `com.rrsjk.openapi.dao.report.EnergyOverdueInventoryControlSummaryDao`
- statements: `insert:create`, `select:get`, `select:countOf`, `select:findBy`, `insert:batchInsert`, `select:getLossSumGroupByCenter`
- tables: `energy_overdue_inventory_control_summary`

## rrsjk-light-openapi-service/rrsjk-light-openapi-impl/src/main/resources/mybatis/mapper/light/LightOwnAssetStatus.xml
- namespace: `com.rrsjk.openapi.dao.light.LightOwnAssetStatusDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `insert:batchInsert`, `select:getLastDataByCbsId`
- tables: `id`, `light_own_asset_status`

## rrsjk-light-openapi-service/rrsjk-light-openapi-impl/src/main/resources/mybatis/mapper/light/LightOwnAsset.xml
- namespace: `com.rrsjk.openapi.dao.light.LightOwnAssetDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `insert:batchInsert`, `select:findByContractNumberList`, `update:updateByCbsId`
- tables: `id`, `light_own_asset`

## rrsjk-light-openapi-service/rrsjk-light-openapi-impl/src/main/resources/mybatis/mapper/light/LightProjectElectricOrder.xml
- namespace: `com.rrsjk.openapi.dao.light.LightProjectElectricOrderDao`
- statements: `select:findStationBy`
- tables: `light_project_electric_order`, `light_project_electric_order_owner`

## rrsjk-light-openapi-service/rrsjk-light-openapi-impl/src/main/resources/mybatis/mapper/light/LightCompanyInfo.xml
- namespace: `com.rrsjk.openapi.dao.light.LightCompanyInfoDao`
- statements: `select:findByParams`

## rrsjk-light-openapi-service/rrsjk-light-openapi-impl/src/main/resources/mybatis/mapper/light/LightShareBillRecord.xml
- namespace: `com.rrsjk.openapi.dao.light.LightShareBillRecordDao`
- statements: `select:findLessorRent`
- tables: `light_share_bill_record`, `light_station`

## rrsjk-light-openapi-service/rrsjk-light-openapi-impl/src/main/resources/mybatis/mapper/local/LightAssetApplicationLog.xml
- namespace: `com.rrsjk.openapi.dao.local.LightAssetApplicationLogDao`
- statements: `insert:create`, `select:get`, `select:countOf`, `select:findBy`, `insert:batchInsert`

## rrsjk-light-openapi-service/rrsjk-light-openapi-impl/src/main/resources/mybatis/mapper/local/LightBocHourElec.xml
- namespace: `com.rrsjk.openapi.dao.local.LightBocHourElecDao`
- statements: `insert:create`, `select:get`, `update:update`, `select:findBy`, `select:findByElec`
- tables: `id`

## rrsjk-light-openapi-service/rrsjk-light-openapi-impl/src/main/resources/mybatis/mapper/ods/OdsLightStationElec.xml
- namespace: `com.rrsjk.openapi.dao.ods.OdsLightStationElecDao`
- statements: `select:findZhaoYinStationCode`, `select:findZhaoYinDayPowerBySation`, `select:findZhaoYinInverterRealTimePower`, `select:findZhaoYinStationStatus`, `select:findZhongYinStation`, `select:findZhongYinInverterDataBySation`, `select:findZhongYinTotalElec`
- tables: `green_energy_boc_leasing_light_station`, `green_energy_cmb_leasing_station`, `green_energy_light_inveter_data`, `green_energy_light_station`, `green_energy_light_station_elec_day_report_new`

## cbs-web/src/main/resources/sql-mapper/shop-write/PubHeaderFooterLogWriteMapper.xml
- namespace: `com.haier.cbs.dao.PubHeaderFooterLogWriteDao`
- statements: `insert:insert`
- tables: `pub_header_footer_log`

## cbs-web/src/main/resources/sql-mapper/shop-write/PubHeaderFooterWriteMapper.xml
- namespace: `com.haier.cbs.dao.PubHeaderFooterWriteDao`
- statements: `insert:create`, `update:update`, `update:publish`
- tables: `id`, `pub_header_footer`

## cbs-web/src/main/resources/sql-mapper/shop-write/HPRecordWriteMapper.xml
- namespace: `com.haier.cbs.dao.HPRecordWriteDao`
- statements: `insert:insertHPRecord`, `update:updateStatus`, `select:findListForHPRecord`
- tables: `hp_record`, `id`

## cbs-web/src/main/resources/sql-mapper/shop-write/HPDispatchWriteMapper.xml
- namespace: `com.haier.cbs.dao.HPDispatchWriteDao`
- statements: `insert:create`, `select:getHttpInterfaceInfo`, `select:getHttpInterfaceCount`, `select:getOrderProductIdsInfo`, `select:getOpIdsFromInvoices`, `select:getExistOrderProductIdsInfo`, `select:getExistInvSapInfo`, `update:updateHpQueues`, `update:updateLes`, `update:updateInvoice`, `update:updateInvoiceSapLog`, `insert:insertLesQueue`, `insert:insertHpQueue`, `insert:insertInvSapQueue`
- tables: `HPQueues`, `InvoiceSAPLogs`, `Invoices`, `LesQueues`, `OrderProducts`, `http_interface_info`, `id`, `invoice_queue`

## cbs-web/src/main/resources/sql-mapper/job-write/SysJobLogMapper.xml
- namespace: `com.haier.cbs.dao.SysJobLogDao`
- statements: `select:find`, `select:getCount`
- tables: `sys_job`, `sys_job_log`

## cbs-web/src/main/resources/sql-mapper/job-write/SysJobMapper.xml
- namespace: `com.haier.cbs.dao.SysJobDao`
- statements: `select:find`, `select:getCount`, `insert:insert`, `update:update`, `update:updateByName`
- tables: `id`, `sys_job`

## cbs-web/src/main/resources/sql-mapper/shop-read/PubHeaderFooterReadMapper.xml
- namespace: `com.haier.cbs.dao.PubHeaderFooterReadDao`
- statements: `select:get`, `select:findAll`
- tables: `pub_header_footer`

## cbs-web/src/main/resources/sql-mapper/shop-read/InvoiceMapper.xml
- namespace: `com.haier.cbs.dao.InvoiceDao`
- statements: `select:getInvoicesByID`, `select:getInvoicesByReceiptNum`, `select:getInvoiceMakeOutList`, `select:getExportInvoiceMakeOutList`, `select:getRowCnts`, `select:getInvoiceApiLogs`, `select:getElectronicInvoiceLogs`, `select:getMemberInvoicesOrderList`, `select:getMemberInvoicesDiffOrderList`, `select:getMemberInvoicesSpecialOrderList`, `select:get`, `select:getInvoicePosProofsList`, `select:getInvoicePosProofsTotalAmount`, `select:getInvoiceSapProofsList`, `select:getInvoiceSapLogList`, `select:getMemberInvoicesById`, `select:getOrderProductsByOrderId`, `select:getInvoiceUsableBycOrderId`, `select:getInvoiceChangeLogs`, `select:getMemberInvoiceByInvoiceTitle`, `select:getInvoicesByCOrderSn`, `select:getVatInvoiceList`, `select:getMemberVatInvoiceList`, `select:getMemberVatInvoiceById`
- tables: `InvoiceApiLogs`, `InvoiceChangeLogs`, `InvoiceElectricLogs`, `InvoiceSAPLogs`, `Invoices`, `MemberInvoices`, `MemberVatInvoice`, `Members`, `Order2ths`, `Order4Invoices`, `OrderProducts`, `Orders`, `PosProofs`, `SapProofs`

## cbs-web/src/main/resources/sql-mapper/shop-read/PubHeaderFooterLogReadMapper.xml
- namespace: `com.haier.cbs.dao.PubHeaderFooterLogReadDao`
- statements: `select:get`, `select:find`
- tables: `pub_header_footer_log`

## rrsjk-pvbusiness-job-service/rrsjk-pvbusiness-job-impl/src/main/resources/mybatis/mapper/report/EnergyOverdueInventoryControlDataBase.xml
- namespace: `com.rrsjk.pvbusinessjob.dao.report.EnergyOverdueInventoryControlDataBaseDao`
- statements: `insert:create`, `insert:batchInsert`, `select:get`, `select:countOf`, `select:findBy`
- tables: `energy_overdue_inventory_control_data_base`

## rrsjk-pvbusiness-job-service/rrsjk-pvbusiness-job-impl/src/main/resources/mybatis/mapper/report/EnergyOverdueInventoryControlSku.xml
- namespace: `com.rrsjk.pvbusinessjob.dao.report.EnergyOverdueInventoryControlSkuDao`
- statements: `insert:create`, `select:get`, `select:countOf`, `select:findBy`, `insert:batchInsert`

## rrsjk-pvbusiness-job-service/rrsjk-pvbusiness-job-impl/src/main/resources/mybatis/mapper/report/GvsWarehouseAgeAnalysis.xml
- namespace: `com.rrsjk.pvbusinessjob.dao.report.GvsWarehouseAgeAnalysisDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:getGvsSummary`, `select:getSumGvsGroupBySku`, `select:countGroupByAgeStatus`, `select:findGroupByAgeStatus`, `select:findToSpData`, `select:findSkuInfo`
- tables: `gvs_warehouse_age_analysis`, `id`, `light_sku_data`, `sap_sp_center_relation`

## rrsjk-pvbusiness-job-service/rrsjk-pvbusiness-job-impl/src/main/resources/mybatis/mapper/report/EnergyOverdueInventoryControlCenter.xml
- namespace: `com.rrsjk.pvbusinessjob.dao.report.EnergyOverdueInventoryControlCenterDao`
- statements: `insert:create`, `select:get`, `select:countOf`, `select:findBy`, `insert:batchInsert`

## rrsjk-pvbusiness-job-service/rrsjk-pvbusiness-job-impl/src/main/resources/mybatis/mapper/report/SapSpCenterRelation.xml
- namespace: `com.rrsjk.pvbusinessjob.dao.report.SapSpCenterRelationDao`
- statements: `select:findAll`

## rrsjk-pvbusiness-job-service/rrsjk-pvbusiness-job-impl/src/main/resources/mybatis/mapper/report/EnergyOverdueInventoryControlSummary.xml
- namespace: `com.rrsjk.pvbusinessjob.dao.report.EnergyOverdueInventoryControlSummaryDao`
- statements: `insert:create`, `select:get`, `select:countOf`, `select:findBy`, `insert:batchInsert`, `select:getLossSumGroupByCenter`
- tables: `energy_overdue_inventory_control_summary`

## rrsjk-pvbusiness-job-service/rrsjk-pvbusiness-job-impl/src/main/resources/mybatis/mapper/light/LightOwnAssetStatus.xml
- namespace: `com.rrsjk.pvbusinessjob.dao.light.LightOwnAssetStatusDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `insert:batchInsert`, `select:getLastDataByCbsId`
- tables: `id`, `light_own_asset_status`

## rrsjk-pvbusiness-job-service/rrsjk-pvbusiness-job-impl/src/main/resources/mybatis/mapper/light/LightOwnAsset.xml
- namespace: `com.rrsjk.pvbusinessjob.dao.light.LightOwnAssetDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `insert:batchInsert`, `select:findByContractNumberList`, `update:updateByCbsId`
- tables: `id`, `light_own_asset`

## rrsjk-pvbusiness-job-service/rrsjk-pvbusiness-job-impl/src/main/resources/mybatis/mapper/light/LightCompanyInfo.xml
- namespace: `com.rrsjk.pvbusinessjob.dao.light.LightCompanyInfoDao`
- statements: `select:findByParams`

## rrsjk-pvbusiness-job-service/rrsjk-pvbusiness-job-impl/src/main/resources/mybatis/mapper/local/LightAssetApplicationLog.xml
- namespace: `com.rrsjk.pvbusinessjob.dao.local.LightAssetApplicationLogDao`
- statements: `insert:create`, `select:get`, `select:countOf`, `select:findBy`, `insert:batchInsert`

## vpp-api-system/vpp-system-biz/src/main/resources/mapper/MenuMapper.xml
- namespace: `com.nahui.energy.mapper.MenuMapper`
- statements: `select:selectMenuTreeByUserId`, `select:findMenuTreeByMenuIdsAndStatusAndMenuTypes`, `select:findMenuTreeByMenuIdsAndStatusAndMenuTypesAndPortalId`
- tables: `menu_tree`, `sys_menu`, `sys_role`, `sys_role_menu`, `sys_user`, `sys_user_role`

## vpp-api-system/vpp-system-biz/src/main/resources/mapper/SysI18nTagLinkMapper.xml
- namespace: `com.nahui.energy.mapper.SysI18nTagLinkMapper`

## vpp-api-system/vpp-system-biz/src/main/resources/mapper/OssMapper.xml
- namespace: `com.nahui.energy.mapper.OssMapper`

## vpp-api-system/vpp-system-biz/src/main/resources/mapper/TestDemoMapper.xml
- namespace: `com.nahui.energy.mapper.TestDemoMapper`

## vpp-api-system/vpp-system-biz/src/main/resources/mapper/SysLanguageMapper.xml
- namespace: `com.nahui.energy.mapper.SysLanguageMapper`

## vpp-api-system/vpp-system-biz/src/main/resources/mapper/UserRoleMapper.xml
- namespace: `com.nahui.energy.mapper.UserRoleMapper`
- statements: `delete:deleteUserRoleByUserId`, `select:countUserRoleByRoleId`, `select:selectByUserId`, `delete:deleteUserRole`, `delete:deeplyDeleteByUserId`
- tables: `sys_role`, `sys_user_role`

## vpp-api-system/vpp-system-biz/src/main/resources/mapper/RoleDeptMapper.xml
- namespace: `com.nahui.energy.mapper.RoleDeptMapper`

## vpp-api-system/vpp-system-biz/src/main/resources/mapper/RoleMapper.xml
- namespace: `com.nahui.energy.mapper.RoleMapper`

## vpp-api-system/vpp-system-biz/src/main/resources/mapper/TenantMapper.xml
- namespace: `com.nahui.energy.mapper.TenantMapper`

## vpp-api-system/vpp-system-biz/src/main/resources/mapper/DictDataMapper.xml
- namespace: `com.nahui.energy.mapper.DictDataMapper`

## vpp-api-system/vpp-system-biz/src/main/resources/mapper/ConfigMapper.xml
- namespace: `com.nahui.energy.mapper.ConfigMapper`
- statements: `select:selectConfigList`
- tables: `sys_config`

## vpp-api-system/vpp-system-biz/src/main/resources/mapper/UserPostMapper.xml
- namespace: `com.nahui.energy.mapper.UserPostMapper`

## vpp-api-system/vpp-system-biz/src/main/resources/mapper/PostMapper.xml
- namespace: `com.nahui.energy.mapper.PostMapper`

## vpp-api-system/vpp-system-biz/src/main/resources/mapper/OutSystemMapper.xml
- namespace: `com.nahui.energy.mapper.OutSystemMapper`

## vpp-api-system/vpp-system-biz/src/main/resources/mapper/OperLogMapper.xml
- namespace: `com.nahui.energy.mapper.OperLogMapper`

## vpp-api-system/vpp-system-biz/src/main/resources/mapper/UserMapper.xml
- namespace: `com.nahui.energy.mapper.UserMapper`

## vpp-api-system/vpp-system-biz/src/main/resources/mapper/NoticeMapper.xml
- namespace: `com.nahui.energy.mapper.NoticeMapper`

## vpp-api-system/vpp-system-biz/src/main/resources/mapper/TestTreeMapper.xml
- namespace: `com.nahui.energy.mapper.TestTreeMapper`

## vpp-api-system/vpp-system-biz/src/main/resources/mapper/DictTypeMapper.xml
- namespace: `com.nahui.energy.mapper.DictTypeMapper`

## vpp-api-system/vpp-system-biz/src/main/resources/mapper/OssConfigMapper.xml
- namespace: `com.nahui.energy.mapper.OssConfigMapper`

## vpp-api-system/vpp-system-biz/src/main/resources/mapper/DeptMapper.xml
- namespace: `com.nahui.energy.mapper.DeptMapper`
- statements: `update:updateDeptChildren`, `select:findAllChildDeptIds`
- tables: `id`, `sys_dept`

## vpp-api-system/vpp-system-biz/src/main/resources/mapper/LogininforMapper.xml
- namespace: `com.nahui.energy.mapper.LogininforMapper`

## vpp-api-system/vpp-system-biz/src/main/resources/mapper/RegionMapper.xml
- namespace: `com.nahui.energy.mapper.RegionMapper`

## vpp-api-system/vpp-system-biz/src/main/resources/mapper/UserTenantMapper.xml
- namespace: `com.nahui.energy.mapper.UserTenantMapper`

## vpp-api-system/vpp-system-biz/src/main/resources/mapper/OutUserMapper.xml
- namespace: `com.nahui.energy.mapper.OutUserMapper`

## vpp-api-system/vpp-system-biz/src/main/resources/mapper/SysPortalMapper.xml
- namespace: `com.nahui.energy.mapper.SysPortalMapper`

## vpp-api-system/vpp-system-biz/src/main/resources/mapper/RoleMenuMapper.xml
- namespace: `com.nahui.energy.mapper.RoleMenuMapper`
- statements: `select:checkMenuExistRole`, `select:selectMenuListByRoleId`, `delete:deleteRoleMenuByRoleId`, `delete:deleteRoleMenu`, `insert:batchRoleMenu`
- tables: `sys_role_menu`

## order-service/order-impl/src/main/resources/order-sql-mapper/SapOrderRecordMapper.xml
- namespace: `com.haier.cbs.order.dao.SapOrderRecordDao`
- statements: `select:getBybstkd`, `insert:insert`, `update:update`
- tables: `id`, `sap_order_record`

## order-service/order-impl/src/main/resources/order-sql-mapper/FreightCostMapper.xml
- namespace: `com.haier.cbs.order.dao.FreightCostDao`
- statements: `insert:saveFreightCost`, `update:updateFreightCost`, `select:selectFreightCost`, `select:countFreightCost`, `update:deleteFreightCost`, `select:selectFreightCostById`, `select:selectFreightCostNopage`
- tables: `freight_cost`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/InvoiceApiLogsMapper.xml
- namespace: `com.haier.cbs.order.dao.InvoiceApiLogsDao`
- statements: `select:get`, `select:getByInvoiceIdAndType`, `insert:insert`, `update:update`, `update:updateByInvoiceIdAndType`
- tables: `InvoiceApiLogs`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/EamAssetOrderMapper.xml
- namespace: `com.haier.cbs.order.dao.EamAssetOrderDao`
- statements: `select:getByOrderProductId`, `select:selectEamAssetOrder`, `select:countEamAssetOrder`, `insert:saveEamAssetOrder`, `update:updateEamAssetOrder`, `select:getSkuByCreateAt`, `select:getByNeedGroup`, `select:countByNeedGroup`, `update:updateByNeedGroup`, `select:getSupplierByCreateAt`, `select:countBySupplierNeedGroup`, `select:getBySupplierNeedGroup`, `update:updateBySupplierNeedGroup`, `select:getByGroupId`, `update:updateStatusByGroupId`, `select:getByStatus`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/InvoiceQueueMapper.xml
- namespace: `com.haier.cbs.order.dao.InvoiceQueueDao`
- statements: `select:get`, `select:getBySuccess`, `select:getByOrderProductId`, `insert:insert`, `update:updateAfterProccess`
- tables: `id`, `invoice_queue`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrdersMapper.xml
- namespace: `com.haier.cbs.order.dao.OrdersDao`
- statements: `select:get`, `select:getByOrderSn`, `select:getByRelationOrderSnAndChannelId`, `select:getByIds`, `insert:insert`, `update:updateForInvoice`, `update:updateForPayment`, `update:updateForTailPayTime`, `update:updateOrderStatus`, `update:updateOrderStatusForAutoCancel`, `update:completeClose`, `select:getStepMsgByOrerSn`, `update:updateForStep`, `select:getNotAutoConfirmOrders`, `select:getNotAutoConfirmOrdersForException`, `update:updateForConfirm`, `update:updateSmConfirmStatus`, `select:getByIdsForConfirm`, `insert:insertKjtProofs`, `insert:insert`, `update:update`, `update:updateRefundStatus`, `select:getWaitConfirmOrderCount`, `select:getWaitConfirmOrder`, `select:getNotSyncBccZeroOrders`, `update:updateOrderSourceOrderSn`, `select:getOrdersToSendSms`, `select:getBucketOrders`, `select:getDistinctAddrList`, `select:getOrdersByAddr`, `select:getZeroOrderNumberByBucket`, `select:getKJTCountByMemberId`, `select:getCodeCountByMemberId`, `select:getDispenserIncome`, `select:findDispenserIncome`, `select:findDispenserRefundAmount`, `select:findDispenserSalary`, `select:findDispenserSalaryRefundAmount`, `select:findDispenserOrderSum`, `select:findRegionByOrderSn`, `select:findOrderAmountByShopId`, `select:getBucketZeroOrderByDesc`, `select:getBucketBuyerClosed`, `select:queryOrderList`, `select:queryGFOrderList`, `select:getGFRrsFee`, `select:getGFRrsCommission`, `select:listAllOrderMemberId`, `update:updateOrders`, `select:getBySourceOrerSn`, `select:getByRelationOrderSnAndOrderType`, `select:listOrderNoByParams`, `select:getListByOrderSns`, `update:finishByIds`, `select:sumOrderAmountByPayTime`, `update:refundClose`, `update:updatePaymentStatus`, `update:updateConfirmTime`, `select:findDispenserTransaction`, `select:listTimeoutNoShippingOrder`, `select:getCompanyConfirmOrders`, `select:getOrdersBycOrderSn`, `update:updateRelationOrderSn`, `update:companyOrderAudit`, `update:confirmOrderReceipt`, `update:confirmIncreaseStock`, `update:updateBakeOrderSource`
- tables: `Jde_SelfAccount`, `KjtProofs`, `OrderProducts`, `OrderRepairs`, `Orders`, `id`, `rrsv3_store`

## order-service/order-impl/src/main/resources/order-sql-mapper/EamAssetInvokeTime.xml
- namespace: `com.haier.cbs.order.dao.EamAssetInvokeTimeDao`
- statements: `select:getByNode`, `update:update`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrderWorkflowRegionMapper.xml
- namespace: `com.haier.cbs.order.dao.OrderWorkflowRegionDao`
- statements: `select:get`, `select:getFdArea`, `select:getTrade`, `select:getSCode`, `select:getOwfRegion`, `insert:insert`, `update:update`
- tables: `id`, `ord_wf_region`

## order-service/order-impl/src/main/resources/order-sql-mapper/AssetPurchaseOrderMapper.xml
- namespace: `com.haier.cbs.order.dao.AssetPurchaseOrderDao`
- statements: `select:getByOrderProductId`, `select:selectPurchaseOrder`, `select:countPurchaseOrder`, `insert:savePurchaseOrder`, `update:updatePurchaseOrder`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrderProductsMapper.xml
- namespace: `com.haier.cbs.order.dao.OrderProductsDao`
- statements: `select:get`, `select:getByIds`, `select:getByCOrderSn`, `select:getByCOrderSnList`, `select:getByPdOrderStatus`, `select:getOrderProductsBySecCode`, `select:getByPdOrderStatusPaging`, `update:updateAfterTransferIn`, `update:updateStatusAfterOut`, `update:updateStatus`, `update:completeClose`, `update:cancelClose`, `update:updateAfterDelivery`, `update:updateAfterTransferFirstOut`, `update:updateAfterTransferSecondOut`, `update:updateRRSById`, `insert:insert`, `update:updateCOrderSn`, `update:updateAfterMatchTail`, `select:getByOrderIds`, `select:getByOrderId`, `insert:insert`, `update:update`, `update:updateForsyncInvoice`, `update:updateCbsSecCode`, `update:updateAfterSyncLes`, `update:updateSyncLes`, `update:updateAfterCreateInvoice`, `update:updateForMakeReceiptType`, `update:updateForFrozenStock`, `select:getByOrderIdsForConfirm`, `select:getUnLockStockOpList`, `select:getLockStockExceptionOpList`, `update:updateMakeReceiptType`, `update:updateAfterPayment`, `select:getListByOrderSn`, `select:getNeedReleaseStockOpList`, `select:getPromoteNeedReleaseStockOpList`, `update:updateForReleaseStock`, `update:updateForReleaseStockCancelOrder`, `select:getNotSyncToVomOrders`, `update:updatePaymentStatusForCod`, `update:updateStatusForRepair`, `update:updateKuaiDiDan`, `select:getExpiredZYKOrderProducts`, `select:getExpiredNormalZeroProducts`, `select:getExpiredRankOrderProducts`, `select:getInterBuyPaidOrderProducts`, `select:getOrderProductsByPayTime`, `select:getById`, `select:getPreSaleStockOpList`, `select:getHiPayNeedReleaseStockOpList`, `select:getTransferPayNeedReleaseStockOpList`, `select:getPresaleNeedReleaseStockOpList`, `select:getStateByExpressSn`, `select:getAllNumbersByMemberId`, `select:getTailPresaleNeedReleaseStockOpList`, `select:getOrderIdsByOrderSnList`, `select:getShippingNumByOrderSnList`, `select:getShippingNumByMemberId`, `select:getOrderNumByOrderSnList`, `select:getOrderNumByMemberId`, `select:getShippingOrderSnByMemberId`, `select:getProductAmountAndSumByCateIds`, `select:getOrderIdByCateIds`, `select:getGFProductAmountAndSumByCateIds`, `select:getGFOrderIdByCateIds`, `select:getCateIdByOrderSn`, `select:getOrderUserSumByCateIds`, `select:getGFOrderUserSumByCateIds`, `select:getGFIncome`, `select:sumAmountByCompleteOrder`, `select:getReportByCompleteOrder`, `select:getOrderMemberId`, `select:getAllOrderMemberId`, `select:queryStatusByCOrderSn`, `select:queryProductAmountAndOrderSumByBrand`, `select:queryGFProductAmountAndOrderSumByBrand`, `select:getOrderUserSum`, `select:queryThirdOrderInfo`
- tables: `CouponCodes`, `Jde_SelfAccount`, `OrderProducts`, `Orders`, `PreSale`, `express_record`, `id`, `packageProducts`, `rrsv3_store`, `shop.CouponReceivedByOrderLogs`, `shop.OrderProducts`, `shop.packageProducts`, `stock_wly_sku`

## order-service/order-impl/src/main/resources/order-sql-mapper/EamAssetProjectMapper.xml
- namespace: `com.haier.cbs.order.dao.EamAssetProjectDao`
- statements: `select:get`, `select:getByOrgAndBudgetyear`, `select:getByPrjcode`, `select:selectEamAssetProject`, `select:countEamAssetProject`, `insert:saveEamAssetProject`, `update:updateEamAssetProject`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrderToJDERecordMapper.xml
- namespace: `com.haier.cbs.order.dao.OrderToJDERecordDao`
- statements: `insert:insertInStockRecord`, `select:getInStockToJDERecord`, `select:queryInStockToJDERecordByJdeOrderNo`, `update:updateInStock`, `select:getUserIdByMemberId`, `insert:insertSaleOrderToJde`, `insert:wareStraightProductsToJdeInsert`, `select:getSaleOrderToJDERecord`, `update:updateSaleOrder`, `select:selectSonProductBySaleSku`, `select:getRepairSnByCOrderSn`, `insert:insertSaleIncomeToJde`, `select:getSaleIncomeToJDERecord`, `select:getSaleIncomeToJDERecordByCOrderSn`, `select:getProductAmountByCorderSn`, `select:getOrderSnBySdoco`, `select:getById`, `select:selectIncomeToJDERecord`, `select:selectIncomeToJDERecordCount`
- tables: `Jde_IncomeRecord`, `Jde_OrderRecord`, `Members`, `OP2JDESharing`, `OrderProducts`, `OrderRepairs`, `VOMProductData`, `id`, `packageProducts`

## order-service/order-impl/src/main/resources/order-sql-mapper/ForecastOrderMapper.xml
- namespace: `com.haier.cbs.order.dao.ForecastOrderDao`
- statements: `select:getForecastDetailByForecastId`, `insert:save`, `insert:saveDetail`, `update:update`, `update:updateDetail`, `select:countForecastOrder`, `select:selectForecastOrder`, `update:deleteForecastOrders`, `select:getForecastDetailByForecastOrder`, `select:selectManageForecast`, `select:getManageForecastById`, `select:countManageForecast`, `update:lockForecastOrder`, `update:lockForecastOrderDetail`, `insert:saveManageForecast`, `select:buildManageForecastDetail`, `insert:saveManageForecastDetail`, `update:updateManageForecast`, `select:getManageDetailByManageInfo`, `update:saveManageDetailNumber`, `update:updateManageForecastDetail`, `update:updateForecastDetail`
- tables: `VOMProductData`, `forecast_order`, `id`, `rrsv3_stock`, `shop.VOMPurchaseOrder`, `shop.forecast_order`, `shop.forecast_order_detail`, `shop.manage_forecast`, `shop.manage_forecast_detail`, `vom_product_price`

## order-service/order-impl/src/main/resources/order-sql-mapper/JdeOffsetTaskMapper.xml
- namespace: `com.haier.cbs.order.dao.JdeOffsetTaskDao`
- statements: `select:selectByPrimaryKey`, `select:selectWaitSynTask`, `update:updateStatusWithBatch`, `update:updateByPrimaryKeySelective`
- tables: `JdeOffsetTask`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/VOMProductPriceMapper.xml
- namespace: `com.haier.cbs.order.dao.VOMProductPriceDao`
- statements: `select:countOf`, `select:findBy`, `select:findUncheckedByProductCode`, `select:findCheckedByProductCode`, `select:findById`, `insert:insert`, `update:update`, `delete:deleteList`, `select:findTaxRate`, `select:findByProductCode`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/JdeQueuesMapper.xml
- namespace: `com.haier.cbs.order.dao.JdeQueuesDao`
- statements: `insert:insert`, `select:getInStockSendQueues`, `select:getSaleOrderSendQueues`, `update:updateAfterSyncJde`, `select:getInStockSendQueuesByParentId`
- tables: `JdeQueues`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/MemberCorpMonthMapper.xml
- namespace: `com.haier.cbs.order.dao.MemberCorpMonthDao`
- statements: `select:get`, `insert:insert`, `select:getLastRecord`, `select:getByYearAndMonth`, `select:select`, `select:count`

## order-service/order-impl/src/main/resources/order-sql-mapper/RrsLnProduct.xml
- namespace: `com.haier.cbs.order.dao.RrsLnProductDao`
- statements: `insert:insert`, `update:update`, `select:get`, `select:getByPager`, `select:count`, `select:getBySku`, `select:getByLnProductCode`, `select:getByProductId`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/BubbleMapper.xml
- namespace: `com.haier.cbs.order.dao.BubbleDao`
- statements: `select:getAfter30MinUnPayOrdersIn10Min`
- tables: `Orders`

## order-service/order-impl/src/main/resources/order-sql-mapper/ZeroOrderProductsMapper.xml
- namespace: `com.haier.cbs.order.dao.ZeroOrderProductsDao`
- statements: `select:count`, `select:getZeroOrderProductByPager`, `select:getZeroOrderProductList`
- tables: `OrderProducts`, `Orders`

## order-service/order-impl/src/main/resources/order-sql-mapper/ThirdFeeRecordMapper.xml
- namespace: `com.haier.cbs.order.dao.ThirdFeeRecordDao`
- statements: `insert:create`, `insert:batchCreate`, `update:update`, `update:updateByIds`, `select:countOf`, `select:findBy`, `select:findListByIds`, `select:findBySettledId`, `update:updateBySettledId`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/ExpressRecordWriteMapper.xml
- namespace: `com.haier.cbs.order.dao.ExpressRecordWriteDao`
- statements: `insert:saveExpressRecord`, `update:updateExpressRecord`, `delete:delExpressRecord`
- tables: `express_record`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/InvoiceChangeLogsMapper.xml
- namespace: `com.haier.cbs.order.dao.InvoiceChangeLogsDao`
- statements: `select:get`, `insert:insert`, `update:update`, `select:getLogsByInvoiceId`
- tables: `InvoiceChangeLogs`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/PremiumsOrderFeedbackMapper.xml
- namespace: `com.haier.cbs.order.dao.PremiumsOrderFeedbackDao`
- statements: `insert:createPremiumsOrderFeedback`, `select:getPremiumsOrderFeedbackByOrderSn`, `select:getPremiumsOrderFeedbackByBudgetCode`
- tables: `PremiumsOrderFeedback`

## order-service/order-impl/src/main/resources/order-sql-mapper/AssetQueueMapper.xml
- namespace: `com.haier.cbs.order.dao.AssetQueueDao`
- statements: `select:get`, `select:getBySuccess`, `select:getByOrderProductId`, `insert:insert`, `update:update`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/InvoicesReadyMapper.xml
- namespace: `com.haier.cbs.order.dao.InvoicesReadyDao`
- statements: `select:get`, `select:getByOrderProductId`, `insert:insert`, `update:update`
- tables: `InvoicesReady`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/ShopOrderMapper.xml
- namespace: `com.haier.cbs.order.dao.ShopOrderDao`
- statements: `select:getShopOrderByModified`, `update:shopOrderProductDeliver`, `update:shopOrderDeliver`
- tables: `OrderProducts`, `Orders`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/RrsHpAmountMapper.xml
- namespace: `com.haier.cbs.order.dao.RrsHpAmountDao`
- statements: `select:get`, `select:getByPointCode`, `insert:insert`, `update:update`, `select:getRrsHpAmountByPager`, `select:countRrsHpAmount`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/CompanyFinanceMapper.xml
- namespace: `com.haier.cbs.order.dao.CompanyFinanceDao`
- statements: `select:getProfitCenterCode`
- tables: `company_extras`

## order-service/order-impl/src/main/resources/order-sql-mapper/EchannelOrderTransQueue.xml
- namespace: `com.haier.cbs.order.dao.EchannelOrderTransQueueDao`
- statements: `insert:create`, `update:update`, `select:getByStatus`, `select:getByEchannelAndObjid`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/SapHandIncomeMapper.xml
- namespace: `com.haier.cbs.order.dao.SapHandIncomeDao`
- statements: `insert:batchInsert`, `insert:insert`, `select:selectRecord`, `select:countRecord`
- tables: `order_relation`, `sap_hand_income`

## order-service/order-impl/src/main/resources/order-sql-mapper/RrsRecRelMapper.xml
- namespace: `com.haier.cbs.order.dao.RrsRecRelDao`
- statements: `select:getByTypeAndId`

## order-service/order-impl/src/main/resources/order-sql-mapper/HpSparePartMapper.xml
- namespace: `com.haier.cbs.order.dao.HpSparePartDao`
- statements: `insert:insert`, `update:update`, `select:getById`, `select:getByApplyNo`, `select:getByCondition`, `select:getHpSparePartByPager`, `select:countHpSparePart`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/SmsLogsWriteMapper.xml
- namespace: `com.haier.cbs.order.dao.SmsLogsWriteDao`
- statements: `insert:insertSmsLogs`
- tables: `SmsLogs`

## order-service/order-impl/src/main/resources/order-sql-mapper/HpHaierFee.xml
- namespace: `com.haier.cbs.order.dao.HpHaierFeeDao`
- statements: `insert:createList`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/ExpressMapper.xml
- namespace: `com.haier.cbs.order.dao.ExpressDao`
- statements: `select:getExpresses`, `select:getVatInvoiceExpresses`
- tables: `Invoices`, `OrderProducts`, `Orders`, `express_register`, `rrsv3_store`

## order-service/order-impl/src/main/resources/order-sql-mapper/V3StoreMapper.xml
- namespace: `com.haier.cbs.order.dao.V3StoreDao`
- statements: `select:getStoreBySecCode`, `select:selectStoreByTpye`, `insert:createStore`, `select:count`, `select:getV3StoreList`, `select:getStoreById`, `update:updateStore`, `select:findTypeBySecCodes`, `select:getStoreBySku`, `select:getFreezeStockByException`
- tables: `OrderProducts`, `id`, `rrsV3_freezeStock`, `rrsv3_stock`, `rrsv3_store`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrderOperateLogsMapper.xml
- namespace: `com.haier.cbs.order.dao.OrderOperateLogsDao`
- statements: `select:get`, `insert:insert`, `insert:batchInsert`, `select:getOrderOperateLogsByOrderId`, `select:getOrderOperateLogsByOrderProductId`, `update:update`, `select:getByOrderProductIdChangeLog`
- tables: `OrderOperateLogs`, `OrderProducts`, `Orders`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/BookProductsMapper.xml
- namespace: `com.haier.cbs.order.dao.BookProductsDao`
- statements: `select:getBookProductsByScodeA`, `select:getBookProductsByScodeB`, `update:setEmailHasSended`
- tables: `BookProducts`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrderWorkFlowOrderExceptionMapper.xml
- namespace: `com.haier.cbs.order.dao.OrderWorkFlowOrderExceptionDao`
- statements: `select:getConfirmExceptionOrderCount`, `select:getConfirmExceptionOrder`, `select:getConfirmWarningOrderCount`, `select:getConfirmWarningOrder`, `select:getConfirmTimeOutOrderCount`, `select:getConfirmTimeOutOrder`, `select:getProductType`, `select:getStorage`, `insert:insert`, `update:update`, `select:getAutoCloseOrderException`, `update:autoCloseOrderException`
- tables: `OrderProducts`, `OrderWorkflows`, `Orders`, `ProductTypes`, `Storages`, `id`, `ord_wf_exception_config`, `ord_wf_order_exception`

## order-service/order-impl/src/main/resources/order-sql-mapper/Order2thsMapper.xml
- namespace: `com.haier.cbs.order.dao.Order2thsDao`
- statements: `select:get`, `update:update`, `update:updateForsynInvoices`
- tables: `Order2ths`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrderRepairsMapper.xml
- namespace: `com.haier.cbs.order.dao.OrderRepairsDao`
- statements: `select:get`, `select:getValidByOrderProductId`, `select:getByOrderProductId`, `update:updateAfterLesInStorage`, `insert:insert`, `update:update`, `update:updateForStatus`, `insert:saveOrderRepairsRecord`, `select:getOrderRepairListByOrderId`, `update:updateForPaymentStatusByOrderId`, `select:getOrderRepairsSupplierPage`, `select:getOrderRepairsSupplierCount`, `select:getOrderRepairsPage`, `select:getOrderRepairsCount`, `insert:saveOrderRepairsList`, `select:getOrderRepairsEntity`, `update:updateForPaymentStatusById`, `select:getOrderRepairsByOrderProductId`, `update:updateByRefundSuccess`, `update:rejectOrderRepair`, `update:agreeOrderRepair`, `update:updateHandleStatus`, `update:reApplyRepair`
- tables: `OrderProducts`, `OrderRepairs`, `Orders`, `Regions`, `WarehouseStraightProducts`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/HpOrder.xml
- namespace: `com.haier.cbs.order.dao.HpOrderDao`
- statements: `select:findByProductNoAndServiceType`, `insert:createList`, `select:select`
- tables: `branch_id`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrderToJDESelfAccountMapper.xml
- namespace: `com.haier.cbs.order.dao.OrderToJDESelfAccountDao`
- statements: `insert:insertJDESelfAccount`, `select:isexist`, `select:getCOrderSnByJde`, `select:getJdeSelfAccountByCOrderSn`, `select:selectSelfAccount`, `select:countSelfAccount`, `select:findSelfAccountList`
- tables: `Jde_SelfAccount`

## order-service/order-impl/src/main/resources/order-sql-mapper/RrsOrderWhiteListMapper.xml
- namespace: `com.haier.cbs.order.dao.RrsOrderWhiteListDao`
- statements: `select:findByCondition`, `select:findByConditionAndType`, `select:getBy`, `select:findBy`

## order-service/order-impl/src/main/resources/order-sql-mapper/CmtCommentOrderProductsMapper.xml
- namespace: `com.haier.cbs.order.dao.CmtCommentOrderProductsDao`
- statements: `insert:insert`
- tables: `DUAL`, `cmt_comment_order_products`

## order-service/order-impl/src/main/resources/order-sql-mapper/CardBinMapper.xml
- namespace: `com.haier.cbs.order.dao.CardBinDao`
- statements: `select:getCardBinByCardBinString`
- tables: `card_bin`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrderProductsPackageMapper.xml
- namespace: `com.haier.cbs.order.dao.OrderProductsPackageDao`
- statements: `select:getByOrderProductId`, `select:get`, `insert:insert`

## order-service/order-impl/src/main/resources/order-sql-mapper/EchannelReshuiTrade.xml
- namespace: `com.haier.cbs.order.dao.EchannelReshuiTradeDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByTid`, `select:findBy`, `select:count`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/ExtendedWarrantyHpDispatchMapper.xml
- namespace: `com.haier.cbs.order.dao.ExtendedWarrantyHpDispatchDao`
- statements: `select:getYBCardInfo`, `select:getInfactProduct`, `update:updateYBCardInfo`
- tables: `OrderProducts`, `OrderYBCards`, `Orders`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/VOMReturnFactoryProductAndOrderMapper.xml
- namespace: `com.haier.cbs.order.dao.VOMReturnFactoryProductAndOrderDao`
- statements: `select:selectReturnFactoryProduct`, `select:countReturnFactoryProduct`, `insert:savePurchaseReturnFactoryOrder`, `update:updatePurReturnFactoryOrder`, `select:selectPurchaseReturnFactoryOrder`, `select:countPurchaseReturnFactoryOrder`, `select:selectReturnFactoryOrderDetailByNo`
- tables: `VOMProductData`, `VOMPurchaseOrder`, `VOMPurchaseReturnFactoryOrder`, `id`, `rrsv3_stock`, `rrsv3_store`, `vom_product_price`

## order-service/order-impl/src/main/resources/order-sql-mapper/SupplierCctExpressMapper.xml
- namespace: `com.haier.cbs.order.dao.SupplierCctExpressDao`
- statements: `select:get`, `select:getEffectBySupplierCode`, `select:getByCodeAndType`, `select:getBySupplierAndCodeAndType`, `insert:insert`, `update:update`, `update:updateStatusBySupplier`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrderStatisticMapper.xml
- namespace: `com.haier.cbs.order.dao.OrderStatisticDao`
- statements: `select:get`, `select:queryFromOrderProducts`
- tables: `OrderProducts`, `OrderStatistic`, `Orders`, `ProductTypes`, `Products`, `StorageProducts`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrderCancelLogsMapper.xml
- namespace: `com.haier.cbs.order.dao.OrderCancelLogsDao`
- statements: `insert:insert`
- tables: `OrderCancelLogs`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrderQueueExtendMapper.xml
- namespace: `com.haier.cbs.order.dao.OrderQueueExtendDao`
- statements: `select:get`, `update:updateSapStatus`, `update:updateInvoiceStatus`, `select:queryOrderQueueExtList`, `select:queryOrderOutList`, `select:queryInvoiceList`, `insert:insert`, `update:cancelOrderExt`, `update:update`
- tables: `OrderQueueExtend`, `dual`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/InvoiceElectric2OutMapper.xml
- namespace: `com.haier.cbs.order.dao.InvoiceElectric2OutDao`
- statements: `select:get`, `select:getSendToHpList`, `select:getSendToSapList`, `insert:insert`, `update:updateAfterSync`
- tables: `id`, `invoice_electric_2_out`

## order-service/order-impl/src/main/resources/order-sql-mapper/HpRegionsMapper.xml
- namespace: `com.haier.cbs.order.dao.HpRegionsDao`
- statements: `select:query`, `select:queryHpRegionsInfo`, `update:updateHpRegionsInfo`, `insert:addRegionsInfo`, `select:queryRegionInfo`, `update:updateRegionsInfoProvince`, `update:updateRegionsInfoCity`, `update:updateRegionsInfoArea`, `insert:addRegions`
- tables: `Regions`, `hp_regions_info`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/orderProductsExtraMapper.xml
- namespace: `com.haier.cbs.order.dao.OrderProductsExtraDao`
- statements: `insert:saveOrderProductsExtra`, `select:selectOrderProductsExtraByCorderId`
- tables: `order_products_extra`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrderWorkFlowNodeConfigMapper.xml
- namespace: `com.haier.cbs.order.dao.OrderWorkFlowNodeConfigDao`
- statements: `select:get`, `insert:insert`, `update:update`
- tables: `id`, `ord_wf_node_config`

## order-service/order-impl/src/main/resources/order-sql-mapper/PurchaseApplySettleMapper.xml
- namespace: `com.haier.cbs.order.dao.PurchaseApplySettleDao`
- statements: `select:getApplyNo`, `select:getById`, `insert:insert`, `update:update`, `select:selectRecord`, `select:countRecord`, `select:findByPayType`, `update:updateById`
- tables: `id`, `purchase_apply_settle`

## order-service/order-impl/src/main/resources/order-sql-mapper/InternalBuyMapper.xml
- namespace: `com.haier.cbs.order.dao.InternalBuyDao`
- statements: `select:findAllCount`, `select:findAllByPaging`, `select:selectById`, `select:selectInternalBuyByNum`, `select:getInternalBuyByCompany`, `insert:insert`, `update:updateFinishStateByNum`, `update:updateAmountUsedByNum`, `update:updateSelectiveById`, `select:searchBySettlementNum`, `delete:deleteById`, `select:getInternalBuyByOrderId`, `select:searchNoLinkByCompany`, `select:getByOrderSn`
- tables: `OrderAndOPExtAttr`, `id`, `internal_buy`

## order-service/order-impl/src/main/resources/order-sql-mapper/VomPoSapQueueMapper.xml
- namespace: `com.haier.cbs.order.dao.VomPoSapQueueDao`
- statements: `insert:insert`, `update:update`, `select:get`, `select:getBySuccess`, `select:getByPoId`, `select:getByPoSn`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/CustomerCodesMapper.xml
- namespace: `com.haier.cbs.order.dao.CustomerCodeDao`
- statements: `select:getCustomerCode`
- tables: `CustomerCodes`

## order-service/order-impl/src/main/resources/order-sql-mapper/RrsHpServicelogMapper.xml
- namespace: `com.haier.cbs.order.dao.RrsHpServiceLogDao`
- statements: `insert:create`, `update:updateWorkStatus`, `select:findByWorkStatus`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/VOMTransferOrderMapper.xml
- namespace: `com.haier.cbs.order.dao.VOMTransferOrderDao`
- statements: `insert:saveTransferOrder`, `update:updateTransferOrder`, `update:updateTransferOrderByorderNo`, `select:selectTransferOrder`, `select:countTransferOrder`, `select:selectTransferOrderDetailByNo`
- tables: `id`, `vom_transfer_order`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrderAndOPExtAttr.xml
- namespace: `com.haier.cbs.order.dao.OrderAndOPExtAttrDao`
- statements: `select:getInternalBuySettlementNo`
- tables: `OrderAndOPExtAttr`

## order-service/order-impl/src/main/resources/order-sql-mapper/RegionCctMapper.xml
- namespace: `com.haier.cbs.order.dao.RegionCctDao`
- statements: `select:getByCode`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrderRepairLogsMapper.xml
- namespace: `com.haier.cbs.order.dao.OrderRepairLogsDao`
- statements: `select:get`, `insert:insert`, `update:update`, `insert:saveOrderRepairLogsList`, `select:getOrderRepairsLogsList`
- tables: `OrderRepairLogs`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/SupplierContractMapper.xml
- namespace: `com.haier.cbs.order.dao.SupplierContractDao`
- statements: `insert:create`, `select:findBySupplierId`, `select:findByContractName`

## order-service/order-impl/src/main/resources/order-sql-mapper/MembersMapper.xml
- namespace: `com.haier.cbs.order.dao.MembersDao`
- statements: `select:get`, `select:getMemberMobile`
- tables: `Members`

## order-service/order-impl/src/main/resources/order-sql-mapper/V3StockLimitMapper.xml
- namespace: `com.haier.cbs.order.dao.V3StockLimitDao`
- statements: `select:getStockLimitBySku`, `select:getNotInStoreNumber`
- tables: `VOMPurchaseOrder`, `rrsv3_stock_limit`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrderWorkFlowExceptionConfigMapper.xml
- namespace: `com.haier.cbs.order.dao.OrderWorkFlowExceptionConfigDao`
- statements: `select:get`, `insert:insert`, `update:update`
- tables: `id`, `ord_wf_exception_config`

## order-service/order-impl/src/main/resources/order-sql-mapper/ReservationShippingMapper.xml
- namespace: `com.haier.cbs.order.dao.ReservationShippingDao`
- statements: `select:get`
- tables: `ReservationShipping`

## order-service/order-impl/src/main/resources/order-sql-mapper/ProductActivitiesMapper.xml
- namespace: `com.haier.cbs.order.dao.ProductActivitiesDao`
- statements: `select:get`
- tables: `ProductActivities`

## order-service/order-impl/src/main/resources/order-sql-mapper/RrsRecCommissionMapper.xml
- namespace: `com.haier.cbs.order.dao.RrsRecCommissionDao`
- statements: `insert:insert`, `update:update`, `select:getByOpId`, `select:get`, `select:selectRrsRecCommission`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrderYBCardsMapper.xml
- namespace: `com.haier.cbs.order.dao.OrderYBCardsDao`
- statements: `insert:insert`, `update:update`, `select:queryByStatus`
- tables: `OrderYBCards`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/RrsShipLogMapper.xml
- namespace: `com.haier.cbs.order.dao.RrsShipLogDao`
- statements: `select:get`, `select:getByGroupno`, `insert:insert`

## order-service/order-impl/src/main/resources/order-sql-mapper/SapQueueMapper.xml
- namespace: `com.haier.cbs.order.dao.SapQueueDao`
- statements: `select:getNeedSynced`, `insert:insert`, `insert:insertRecordId`, `update:update`
- tables: `id`, `sap_queue`

## order-service/order-impl/src/main/resources/order-sql-mapper/SapIncomeInvoiceMapper.xml
- namespace: `com.haier.cbs.order.dao.SapIncomeInvoiceDao`
- statements: `insert:create`, `select:getByBidAndYWLX`

## order-service/order-impl/src/main/resources/order-sql-mapper/SapRecordMapper.xml
- namespace: `com.haier.cbs.order.dao.SapRecordDao`
- statements: `select:getByRowId`, `select:getById`, `select:getByBidAndYWMS`, `insert:insert`, `insert:insertItems`, `update:update`, `update:updateItem`, `select:getForStockReport`
- tables: `id`, `sap_item_record`, `sap_record`

## order-service/order-impl/src/main/resources/order-sql-mapper/BccRebateRecordMapper.xml
- namespace: `com.haier.cbs.order.dao.BccRebateRecordDao`
- statements: `insert:create`, `update:update`, `select:countOf`, `select:findBy`, `select:findByRowId`, `select:findById`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/EamAssetQueueMapper.xml
- namespace: `com.haier.cbs.order.dao.EamAssetQueueDao`
- statements: `select:get`, `select:getBySuccess`, `select:getByOrderProductId`, `insert:insert`, `update:update`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/ExpressCompany.xml
- namespace: `com.haier.cbs.order.dao.ExpressCompanyDao`
- statements: `select:findAll`, `select:getByCode`, `select:getByName`

## order-service/order-impl/src/main/resources/order-sql-mapper/EchannelWeight.xml
- namespace: `com.haier.cbs.order.dao.EchannelWeightDao`
- statements: `select:getBySku`

## order-service/order-impl/src/main/resources/order-sql-mapper/ExpressRecordMapper.xml
- namespace: `com.haier.cbs.order.dao.ExpressRecordDao`
- statements: `select:getExpressRecordByExpressSn`, `select:getLastExpressRecordByExpressSn`, `select:findByParams`
- tables: `express_record`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrderRelationQueueMapper.xml
- namespace: `com.haier.cbs.order.dao.OrderRelationQueueDao`
- statements: `select:get`, `select:getBySuccess`, `select:getBySuccessAndAction`, `select:getByOrderProductIdAndAction`, `select:getByChildOrderProductIdAndAction`, `insert:insert`, `update:update`, `select:getByRepairIdAndAction`, `select:getByRepairChildOrderProductIdAndAction`, `select:getByOrderProductId`, `insert:batchInsertByOrderProductIds`
- tables: `id`, `order_relation_queue`

## order-service/order-impl/src/main/resources/order-sql-mapper/IncomeActualMapper.xml
- namespace: `com.haier.cbs.order.dao.IncomeActualDao`
- statements: `select:summarySubtotal`, `select:summaryTotal`, `insert:createList`, `select:countOfForecastAndActualList`, `select:queryForecastAndActualListBy`, `select:countOf`, `select:findBy`
- tables: `income_actual`, `income_forecast`, `month_amount`

## order-service/order-impl/src/main/resources/order-sql-mapper/Item2OrderSourceMapper.xml
- namespace: `com.haier.cbs.order.dao.Item2OrderSourceDao`
- statements: `select:getByOrderSource`
- tables: `item_2_order_source`

## order-service/order-impl/src/main/resources/order-sql-mapper/V3StoreCityMapper.xml
- namespace: `com.haier.cbs.order.dao.V3StoreCityDao`
- statements: `insert:createStoreCity`, `select:count`, `select:getV3StoreCityList`, `update:updateByIdList`, `delete:deleteById`, `select:getStoreCityBySecCode`, `delete:deleteBySecCode`, `select:getStoreCityByCityId`
- tables: `id`, `rrsv3_store_city`

## order-service/order-impl/src/main/resources/order-sql-mapper/InvoiceElectricSyncLogsMapper.xml
- namespace: `com.haier.cbs.order.dao.InvoiceElectricSyncLogsDao`
- statements: `insert:insert`, `update:update`
- tables: `InvoiceElectricSyncLogs`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/RrsHpAmountDetailMapper.xml
- namespace: `com.haier.cbs.order.dao.RrsHpAmountDetailDao`
- statements: `select:get`, `select:getByHpCode`, `select:getByPointCode`, `select:getByAmountId`, `insert:insert`, `update:update`, `select:getRrsHpAmountDetailByPager`, `select:countRrsHpAmountDetail`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/MemberCorpHpMapper.xml
- namespace: `com.haier.cbs.order.dao.MemberCorpHpDao`
- statements: `select:get`, `insert:insert`, `select:select`, `select:count`, `select:getByHpno`, `select:getHrcodeGroupBy`, `update:updateByHrcodeAndDate`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/TaoBaoGroupsMapper.xml
- namespace: `com.haier.cbs.order.dao.TaoBaoGroupsDao`
- statements: `select:get`
- tables: `TaoBaoGroups`

## order-service/order-impl/src/main/resources/order-sql-mapper/LesQueuesMapper.xml
- namespace: `com.haier.cbs.order.dao.LesQueuesDao`
- statements: `select:get`, `select:getSendQueues`, `update:updateAfterSyncLes`, `select:getCreateInvoiceQueues`, `insert:insert`, `select:getCountByOpId`, `update:updateByOpId`
- tables: `LesQueues`, `OrderProducts`, `Orders`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrderCosmoQueueMapper.xml
- namespace: `com.haier.cbs.order.dao.OrderCosmoQueueDao`
- statements: `select:get`, `select:getBySuccess`, `select:getBySuccessAndAction`, `select:getByOrderProductIdAndAction`, `select:getByOrderProductId`, `insert:insert`, `update:update`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/SupplierPaySettingsMapper.xml
- namespace: `com.haier.cbs.order.dao.SupplierPaySettingsDao`
- statements: `select:getBySku`
- tables: `supplier_pay_settings`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrderShippedQueueMapper.xml
- namespace: `com.haier.cbs.order.dao.OrderShippedQueueDao`
- statements: `select:getListToProcess`, `insert:insert`, `update:delete`, `update:update`
- tables: `id`, `order_shipped_queue`

## order-service/order-impl/src/main/resources/order-sql-mapper/HPQueuesMapper.xml
- namespace: `com.haier.cbs.order.dao.HPQueuesDao`
- statements: `insert:insert`, `update:update`, `select:getCountByOpId`
- tables: `HPQueues`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/MemberCorpSaleMapper.xml
- namespace: `com.haier.cbs.order.dao.MemberCorpSaleDao`
- statements: `update:update`, `select:getById`, `select:getByMemberId`, `select:getHrcodeByMemberId`, `select:getNeedAmount`, `select:getByCondition`, `select:getByPager`, `select:countMemberCorpSale`, `select:sumAmount`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/HpSocialFee.xml
- namespace: `com.haier.cbs.order.dao.HpSocialFeeDao`
- statements: `insert:createList`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/InvoicePostManagerMapper.xml
- namespace: `com.haier.cbs.order.dao.InvoicePostManagerDao`
- statements: `select:getManagerByMap`, `select:getAllManagers`

## order-service/order-impl/src/main/resources/order-sql-mapper/RrsCxwShipMapper.xml
- namespace: `com.haier.cbs.order.dao.RrsCxwShipDao`
- statements: `select:getBySku`

## order-service/order-impl/src/main/resources/order-sql-mapper/InstallationCostMapper.xml
- namespace: `com.haier.cbs.order.dao.InstallationCostDao`
- statements: `select:queryInstallationCost`, `select:countInstallationCost`, `select:countProductData`, `select:selectProduct`, `select:selectProductBySku`, `insert:saveInstallationCost`, `insert:saveMoreInstallationCost`, `update:deleteInstallationCost`, `select:getInstallationCostById`
- tables: `InstallationCost`, `VOMProductData`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrderRelation.xml
- namespace: `com.haier.cbs.order.dao.OrderRelationDao`
- statements: `select:get`, `select:isExist`, `select:getByChildOrderProductSn`, `select:getByOrderProductId`, `select:getByRepairChildOrderProductSn`, `select:getByRepairOrderProductId`, `insert:insert`, `update:update`, `select:getOrderRelationByPager`, `select:countOrderRelation`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/InvoiceSAPLogsMapper.xml
- namespace: `com.haier.cbs.order.dao.InvoiceSAPLogsDao`
- statements: `select:getInvoiceSAPLogsList`, `update:updateInvoiceSAP`, `insert:insert`, `select:getByInvoiceIdAndPushType`
- tables: `InvoiceSAPLogs`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/BudgetMapper.xml
- namespace: `com.haier.cbs.order.dao.BudgetDao`
- statements: `insert:createBudget`, `select:count`, `select:getBudgetList`, `update:updateBudget`, `select:getBudgetById`, `select:getBudgetByCode`, `select:getBudgetCodeByParam`
- tables: `Budget`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/RrsjkOrderMapper.xml
- namespace: `com.haier.cbs.order.dao.RrsjkOrderDao`
- statements: `select:countRrsjkOrder`, `select:getRrsjkOrderByPager`
- tables: `OrderProducts`, `OrderRepairs`, `Orders`

## order-service/order-impl/src/main/resources/order-sql-mapper/MsLinkageMapper.xml
- namespace: `com.haier.cbs.order.dao.MsLinkageDao`
- statements: `select:getMsLinkage`
- tables: `ms_linkage`

## order-service/order-impl/src/main/resources/order-sql-mapper/StockFrozenQueuesMapper.xml
- namespace: `com.haier.cbs.order.dao.StockFrozenQueuesDao`
- statements: `insert:insert`, `update:update`, `update:updateByOpId`, `select:getUnFrozenQueues`
- tables: `id`, `stock_frozen_queues`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrderRepairLESRecordsMapper.xml
- namespace: `com.haier.cbs.order.dao.OrderRepairLESRecordsDao`
- statements: `select:get`, `select:getByRecordSn`, `update:updateAfterLesInStorage`, `update:updateAfterVomAccepted`, `insert:insert`, `update:update`
- tables: `OrderRepairLESRecords`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/ThirdFeeInvoiceSettleMapper.xml
- namespace: `com.haier.cbs.order.dao.ThirdFeeInvoiceSettleDao`
- statements: `insert:create`, `update:update`, `select:findById`, `select:getApplyNo`, `select:countOf`, `select:findBy`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/RrsCctOrderMapper.xml
- namespace: `com.haier.cbs.order.dao.RrsCctOrderDao`
- statements: `select:get`, `select:getOrderByStatus`, `select:getNeedExpressOrder`, `select:getByCbsOrderNo`, `select:getByCctOrderNo`, `select:getBusinessId`, `select:getOrderByBusinessId`, `insert:insert`, `update:update`, `select:getGroupNo`, `select:getOrderByGroupNo`, `select:getByPager`, `select:count`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/InvoicesMapper.xml
- namespace: `com.haier.cbs.order.dao.InvoicesDao`
- statements: `select:get`, `select:getByCorderSn`, `select:getByOrderProductId`, `insert:insertInvoice`, `update:update`, `select:getSyncInvoiceList`, `select:getSyncedInvoiceList`, `select:getInvalidInvoiceList`, `select:getMemberVatInvoiceById`, `select:getMemberInvoicesByTaxPayerNumber`, `select:getInvoicesByTaxPayerNumber`, `update:updateMemberVatInvoice`, `update:updateMemberInvoicesById`, `update:updateInvoicesById`, `select:getSyncVatInvoiceList`, `select:querySyncedVatInvoiceList`, `update:updateInvoicesAmountById`, `select:getInvoiceByorderProductId`, `select:getInvoiceByorderProductIdsState`, `select:getSyncElectricInvoiceList`, `select:getNeedSyncInvoiceNumberList`, `select:getByOrderLineNumber`, `select:getVatInvoiceExpressSign`, `select:getVatInvoiceExpressList`, `select:getInvoicesByReceiptNum`, `select:getElecInvoiceFromTax`, `select:getElecInvoiceInvalidFromTax`, `select:queryByTaxInvoiceCloud`
- tables: `Invoices`, `MemberInvoices`, `MemberVatInvoice`, `express_record`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/InvoicePostMapper.xml
- namespace: `com.haier.cbs.order.dao.InvoicePostDao`
- statements: `insert:insert`, `insert:insertList`, `update:update`, `select:queryCountBy`, `select:getInvoicePostList`, `select:queryByMap`, `select:queryJDERecord`, `select:queryExpress`, `select:emailRemindManager`, `select:getByOrderProductId`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/ServiceIncomeInvoiceQueueMapper.xml
- namespace: `com.haier.cbs.order.dao.ServiceIncomeInvoiceQueueDao`
- statements: `insert:create`, `update:updateInvoiceNumberBy`, `update:updateInvoiceSyncedBy`, `select:isExist`, `select:getInvoiceNumber`, `select:getSyncToSapInvoiceList`
- tables: `Invoices`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/ExpressRegisterMapper.xml
- namespace: `com.haier.cbs.order.dao.ExpressRegisterDao`
- statements: `select:getExpressRegisterByExpressSn`, `select:getExpressRegisterListByResponseCode`
- tables: `express_register`

## order-service/order-impl/src/main/resources/order-sql-mapper/VomAllocateOrderMapper.xml
- namespace: `com.haier.cbs.order.dao.VomAllocateOrderDao`
- statements: `insert:insert`, `update:update`, `select:getById`, `select:getByOrderno`, `select:getByPager`, `select:count`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/ProductPriceChangeLog.xml
- namespace: `com.haier.cbs.order.dao.ProductPriceChangeLogDao`
- statements: `insert:create`

## order-service/order-impl/src/main/resources/order-sql-mapper/ExpressAbortMapper.xml
- namespace: `com.haier.cbs.order.dao.ExpressAbortDao`
- statements: `select:getExpressAbortByExpressSn`, `select:getAllExpressAbort`
- tables: `express_abort`

## order-service/order-impl/src/main/resources/order-sql-mapper/BookLogsMapper.xml
- namespace: `com.haier.cbs.order.dao.BookLogsDao`
- statements: `select:getBookLogs`, `update:setEmailHasSended`
- tables: `BookLogs`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrderQueuesMapper.xml
- namespace: `com.haier.cbs.order.dao.OrderQueuesDao`
- statements: `select:get`, `insert:insert`, `update:update`, `select:getByOrderProductId`, `select:getOrderQueuesList`
- tables: `id`, `order_queues`

## order-service/order-impl/src/main/resources/order-sql-mapper/MemberInvoicesMapper.xml
- namespace: `com.haier.cbs.order.dao.MemberInvoicesDao`
- statements: `select:get`, `insert:insert`, `update:update`, `update:updateForsynInvoices`, `select:getByOrderId`, `select:checkPassedValuedInvoice`
- tables: `MemberInvoices`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/BranchMapper.xml
- namespace: `com.haier.cbs.order.dao.BranchDao`
- statements: `select:get`, `select:getByCode`, `select:getAll`, `select:select`

## order-service/order-impl/src/main/resources/order-sql-mapper/RrsHpQueueMapper.xml
- namespace: `com.haier.cbs.order.dao.RrsHpQueueDao`
- statements: `select:get`, `select:getBySuccess`, `select:getByNotComplete`, `select:getByTypeAndId`, `insert:insert`, `update:update`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/IncomeDifferenceReportMapper.xml
- namespace: `com.haier.cbs.order.dao.IncomeDifferenceReportDao`
- statements: `select:countOf`, `select:findBy`, `insert:createList`, `update:setRate`
- tables: `id`, `target`

## order-service/order-impl/src/main/resources/order-sql-mapper/MemberCorpNetpointAmountMapper.xml
- namespace: `com.haier.cbs.order.dao.MemberCorpNetpointAmountDao`
- statements: `select:get`, `insert:insert`, `update:update`, `select:select`, `select:count`, `select:getByHrcodeAndDate`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/HpWorkMapper.xml
- namespace: `com.haier.cbs.order.dao.HpWorkDao`
- statements: `select:get`, `insert:insert`, `update:update`, `select:selectHpWork`, `select:countHpWork`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/SuppliersMapper.xml
- namespace: `com.haier.cbs.order.dao.SuppliersDao`
- statements: `select:getSuppliersById`, `select:getSuppliersByMasterName`, `select:count`, `select:getSuppliersList`, `update:updateById`, `insert:createSuppliers`, `select:getBySupplierCode`, `select:getSuppliersByEmail`, `select:getByTaxno`, `select:getSuppliersByCctId`, `select:getNeedTaxNo`
- tables: `Suppliers`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/CouponReceivedByOrderLogsMapper.xml
- namespace: `com.haier.cbs.order.dao.CouponReceivedByOrderLogsDao`
- statements: `insert:saveCouponReceivedCouponLogs`, `select:searchCouponBySnAndOrderSn`, `select:searchCouponBySnAndOrderSnCount`
- tables: `CouponLogs`, `CouponReceivedByOrderLogs`

## order-service/order-impl/src/main/resources/order-sql-mapper/Order4InvoicesMapper.xml
- namespace: `com.haier.cbs.order.dao.Order4InvoicesDao`
- statements: `select:get`, `update:update`, `update:updateForsynInvoices`
- tables: `Order4Invoices`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/MemberCorpHpAmountMapper.xml
- namespace: `com.haier.cbs.order.dao.MemberCorpHpAmountDao`
- statements: `select:get`, `insert:insert`, `select:select`, `select:count`, `select:getHrcodeGroupBy`, `select:getByHrcodeAndDate`, `select:getBranchCodeBy`, `select:getHrcodeGroupByBranch`, `select:sumAmount`

## order-service/order-impl/src/main/resources/order-sql-mapper/WaterEcologicalIncomeMapper.xml
- namespace: `com.haier.cbs.order.dao.WaterEcologicalIncomeDao`
- statements: `select:queryListBy`, `select:findEcologicalIncomeCateNameList`, `select:findHardwareIncomeAmountMonth`
- tables: `ecological_income_cate_name2019`, `rrs_income_data_finance`, `rrs_income_data_finance2019`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrderWorkFlowOrderExceptionFixLogMapper.xml
- namespace: `com.haier.cbs.order.dao.OrderWorkFlowOrderExceptionFixLogDao`
- statements: `select:getbyOrderProductId`, `insert:insert`, `update:update`
- tables: `id`, `ord_wf_order_exception_fix_log`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrderRepairLESQueuesMapper.xml
- namespace: `com.haier.cbs.order.dao.OrderRepairLESQueuesDao`
- statements: `select:getByOrderProductId`, `insert:updateVomResult`
- tables: `OrderRepairLESQueues`

## order-service/order-impl/src/main/resources/order-sql-mapper/PurchaseOrderReturnFactoryMapper.xml
- namespace: `com.haier.cbs.order.dao.PurchaseOrderReturnFactoryDao`
- statements: `select:queryCountBy`, `select:queryListBy`, `select:getById`, `insert:insert`, `update:update`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/RegionsMapper.xml
- namespace: `com.haier.cbs.order.dao.RegionsDao`
- statements: `select:get`, `select:getByProvinceName`, `select:getByNameAndParentId`, `select:getByParentId`, `select:getByIds`, `select:getRegionsPage`, `select:getRegionsCount`, `update:update`, `insert:saveRegions`, `select:getRegionsByMap`, `delete:delete`, `select:getByRegionType`, `select:getByCode`, `select:getAllRegionByCode`
- tables: `Regions`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/SimpleOrderMapper.xml
- namespace: `com.haier.cbs.order.dao.SimpleOrderDao`
- statements: `select:countSimpleOrder`, `select:getSimpleOrderByPager`, `select:get`, `select:countSimpleOrderInvoice`, `select:getSimpleOrderInvoiceByPager`, `insert:insertMemberVatInvoice`, `update:updateMemberVatInvoice`, `update:updateSimpleOrderInvoices`, `select:countRelationOrder`, `select:getRelationOrderByPager`, `select:getByTaxPayerNumber`
- tables: `MemberInvoices`, `MemberVatInvoice`, `OrderProducts`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/InternalBuyOrderMapper.xml
- namespace: `com.haier.cbs.order.dao.InternalBuyOrderDao`
- statements: `select:selectById`, `select:selectInternalBuyByNum`, `insert:insert`, `update:update`, `update:linkPurchaseInternalAll`, `select:getOrderProductsCount`, `select:getOrderProductsPage`, `select:getOrderProductsFromInternalBuy`, `update:linkSettleByOrderIds`, `update:updateInternalBuyOrderBycancelOrder`
- tables: `OrderAndOPExtAttr`, `OrderProducts`, `Orders`, `id`, `internal_buy`, `internal_buy_order`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrderWorkFlowOrderNodeMapper.xml
- namespace: `com.haier.cbs.order.dao.OrderWorkFlowOrderNodeDao`
- statements: `select:get`, `insert:insert`, `update:update`
- tables: `id`, `ord_wf_order_node`

## order-service/order-impl/src/main/resources/order-sql-mapper/SupplierStoreMapper.xml
- namespace: `com.haier.cbs.order.dao.SupplierStoreDao`
- statements: `select:get`, `select:getEffectBySupplierCode`, `insert:insert`, `update:update`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/RrsLnQueueMapper.xml
- namespace: `com.haier.cbs.order.dao.RrsLnQueueDao`
- statements: `select:get`, `select:getBySuccess`, `select:getByTypeAndTid`, `insert:insert`, `update:update`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/EchannelApiInvokeTime.xml
- namespace: `com.haier.cbs.order.dao.EchannelApiInvokeTimeDao`
- statements: `select:getByApiChannelAndName`, `update:update`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/CompanyOrderMapper.xml
- namespace: `com.haier.cbs.order.dao.CompanyOrderDao`
- statements: `select:countCompanyOrderProduct`, `select:getCompanyOrderProductByPager`, `select:countCompanyOrder`, `select:getCompanyOrderByPager`, `select:findFinancialSolutionsAmount`
- tables: `OrderProducts`, `Orders`

## order-service/order-impl/src/main/resources/order-sql-mapper/HPBccPayMapper.xml
- namespace: `com.haier.cbs.order.dao.HpBccPayDao`
- statements: `insert:insert`, `update:update`, `update:updateAll`, `select:getByRowIdOrOrderNo`, `select:getNeedPay`, `select:countOf`, `select:findBy`
- tables: `hp_bcc_pay`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/EhaierQueuesMapper.xml
- namespace: `com.haier.cbs.order.dao.EhaierQueuesDao`
- statements: `select:get`, `select:getSendQueues`, `update:updateAfterSyncLes`, `select:getCreateInvoiceQueues`, `insert:insert`, `select:getCountByOpId`, `update:updateByOpId`
- tables: `EhaierQueues`, `OrderProducts`, `Orders`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrderRepairHPRecordsMapper.xml
- namespace: `com.haier.cbs.order.dao.OrderRepairHPRecordsDao`
- statements: `select:get`, `select:getByRepairIdAndCheckType`, `insert:insert`, `update:update`
- tables: `OrderRepairHPRecords`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/SapReverseRecordMapper.xml
- namespace: `com.haier.cbs.order.dao.SapReverseRecordDao`
- statements: `select:getById`, `select:getByPreBelnrAndType`, `insert:insert`, `update:update`, `select:selectRecord`, `select:countRecord`
- tables: `id`, `sap_reverse_record`

## order-service/order-impl/src/main/resources/order-sql-mapper/MemberCorpBranchAmountMapper.xml
- namespace: `com.haier.cbs.order.dao.MemberCorpBranchAmountDao`
- statements: `select:get`, `insert:insert`, `update:update`, `select:select`, `select:count`, `select:getByBranchAndDate`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/SapPurchaseRecordMapper.xml
- namespace: `com.haier.cbs.order.dao.SapPurchaseRecordDao`
- statements: `select:getPurchaseNo`, `select:getBySettleId`, `select:getByebeln`, `insert:insert`, `select:selectRecord`, `select:countRecord`, `select:getRecordByIds`, `update:updateByIds`, `update:update`, `select:getPurchaseOrderByPay`, `select:selectRecordDTOList`, `select:countRecordDTO`, `update:updateBySettledId`
- tables: `OrderProducts`, `VOMProductData`, `id`, `sap_purchase_record`

## order-service/order-impl/src/main/resources/order-sql-mapper/EchannelLnDeliver.xml
- namespace: `com.haier.cbs.order.dao.EchannelLnDeliverDao`
- statements: `insert:create`, `update:update`, `select:countEchannelLnDeliver`, `select:getEchannelLnDeliverByPager`, `select:getByCondition`, `select:get`, `select:getByMsn`, `select:getByOsn`, `select:getBySn`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/GroupOrdersMapper.xml
- namespace: `com.haier.cbs.order.dao.GroupOrdersDao`
- statements: `select:getByDepositOrderId`, `insert:insert`, `update:updateStatus`, `update:updateLesStatus`, `select:getGroupOrdersQueues`
- tables: `GroupOrders`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/RrsServiceLogMapper.xml
- namespace: `com.haier.cbs.order.dao.RrsServiceLogDao`
- statements: `insert:insert`, `update:update`, `select:getById`, `select:getByCodeAndSn`, `select:getByCondition`, `select:getRrsServiceLogByPager`, `select:countRrsServiceLog`, `delete:delete`, `delete:deleteByOptime`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/TransferPayConfirmMapper.xml
- namespace: `com.haier.cbs.order.dao.TransferPayConfirmDao`
- statements: `insert:insert`, `select:getByOrderId`

## order-service/order-impl/src/main/resources/order-sql-mapper/InvoiceLineMapper.xml
- namespace: `com.haier.cbs.order.dao.InvoiceLineDao`
- statements: `select:get`, `select:getByInvoiceId`, `insert:create`, `update:update`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/MemberCorpStockMapper.xml
- namespace: `com.haier.cbs.order.dao.MemberCorpStockDao`
- statements: `insert:insert`, `update:update`, `select:getById`, `select:getByMemberIdSku`, `select:getByMemberId`, `select:getByCondition`, `select:getByPager`, `select:countMemberCorpStock`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/EchannelTmallTradeOrder.xml
- namespace: `com.haier.cbs.order.dao.EchannelTmallTradeOrderDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByOid`, `select:getByTid`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/VOMQueuesMapper.xml
- namespace: `com.haier.cbs.order.dao.VOMQueuesDao`
- statements: `insert:insert`, `select:getPoSendQueues`, `update:updateAfterSyncVom`, `select:getPdSendQueues`, `select:selectVomQueusByOrderIdAndAction`, `update:updateVomQueuesByOrderId`, `select:getDbSendQueues`
- tables: `VOMProductData`, `VOMPurchaseOrder`, `VOMQueues`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/RegionSmallMicroMapper.xml
- namespace: `com.haier.cbs.order.dao.RegionSmallMicroDao`
- statements: `select:getSubCenterList`, `select:getRegionList`
- tables: `county_small_micro_detail`

## order-service/order-impl/src/main/resources/order-sql-mapper/VomAllocateSapQueueMapper.xml
- namespace: `com.haier.cbs.order.dao.VomAllocateSapQueueDao`
- statements: `insert:insert`, `update:update`, `select:getById`, `select:getBySuccess`, `select:getByAllocateSn`, `select:getByAllocateId`, `select:countByAllocateId`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/RrsRecCodeMapper.xml
- namespace: `com.haier.cbs.order.dao.RrsRecCodeDao`
- statements: `select:getByCode`

## order-service/order-impl/src/main/resources/order-sql-mapper/WareStraightProductsMapper.xml
- namespace: `com.haier.cbs.order.dao.WarehouseStraightProductsDao`
- statements: `insert:saveWareStraightProd`, `select:countWareStraightProd`, `select:selectWareStraightProd`, `update:deleteWareStraightProd`, `select:getLatestEffectiveProduct`, `select:getWarehouseStraightProductsBySupplierCode`, `select:getSupplierByStore`, `select:getLatestEffectiveProductBySkuAndSupply`, `select:getStorecodeBySupplierCode`
- tables: `WarehouseStraightProducts`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/MemberCorpSumAmountMapper.xml
- namespace: `com.haier.cbs.order.dao.MemberCorpSumAmountDao`
- statements: `select:get`, `insert:insert`, `update:update`, `select:select`, `select:count`, `select:getByMemberIdAndDate`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/MemberCorpNetpointSumMapper.xml
- namespace: `com.haier.cbs.order.dao.MemberCorpNetpointSumDao`
- statements: `select:get`, `insert:insert`, `update:update`, `select:select`, `select:count`, `select:getByHrcodeIdAndDate`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/Company.xml
- namespace: `com.haier.cbs.order.dao.CompanyDao`
- statements: `insert:insert`, `update:update`, `select:getByCompanyCode`, `select:findByAll`, `select:getCompanyByPager`, `select:countCompany`, `select:getByTypeAndLnShop`, `select:getByCustomerCode`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/IncomeRecordMapper.xml
- namespace: `com.haier.cbs.order.dao.IncomeRecordDao`
- statements: `insert:insert`, `insert:insertDetails`, `select:findAllCount`, `select:findAllByPaging`, `select:selectById`, `select:isExist`, `update:updateSelectiveById`, `update:confirmReceiptUpdate`, `delete:deleteById`, `select:selectByCreatedAt`, `select:listEcologicalIncome`, `select:getAdIncome`, `select:getIncomeByType`, `select:listEveryDayAdIncome`, `select:findSyncToSapByCustomerCode`, `select:findIncomeRecordList`
- tables: `id`, `service_income_record`, `service_income_record_detail`

## order-service/order-impl/src/main/resources/order-sql-mapper/HpDispatchMapper.xml
- namespace: `com.haier.cbs.order.dao.HpDispatchDao`
- statements: `select:getHpQueueInfo`, `select:getOrderProductInfo`, `select:getOrderInfo`, `select:getOrderWorkFlowInfo`, `select:getReservationShippingInfo`, `select:getMemberInvoiceInfo`, `select:getOrderCountList`, `select:getRegions`, `select:getSkuMappings`, `update:updateHPQueue`, `update:updateOrderProductStatus`, `update:updateSyncHpTime`
- tables: `HPQueues`, `MemberInvoices`, `OrderProducts`, `OrderWorkflows`, `Orders`, `Regions`, `ReservationShipping`, `SkuMappings`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/IncomeForecastMapper.xml
- namespace: `com.haier.cbs.order.dao.IncomeForecastDao`
- statements: `insert:createTotal`, `insert:createList`, `select:countOf`, `select:findBy`, `update:setInvalid`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/V3StockMapper.xml
- namespace: `com.haier.cbs.order.dao.V3StockDao`
- statements: `select:getStockBySkuSec`, `insert:insertStock`, `insert:insertStockInway`, `select:count`, `select:getV3StockList`, `select:exportV3StockList`, `update:updateStockById`, `select:getV3StockBySku`, `select:getSecCodeBySku`, `insert:insertRecord`, `select:getDispenserStockList`, `update:freezeWaitOutNumber`, `update:releaseWaitOutNumber`, `update:outStoreOutWayNumber`, `update:outStoreWaitInNumber`, `update:inStoreInWayNumber`, `insert:insertWaitInNumber`
- tables: `id`, `rrsv3_stock`, `rrsv3_stock_record`

## order-service/order-impl/src/main/resources/order-sql-mapper/InvoiceElectricLogsMapper.xml
- namespace: `com.haier.cbs.order.dao.InvoiceElectricLogsDao`
- statements: `select:getByInvoiceIdAndType`, `select:getByInvoiceIdAndTypeList`, `insert:insertLog`, `update:update`, `update:updateByInvoiceIdAndType`
- tables: `InvoiceElectricLogs`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/EchannelTmallTrade.xml
- namespace: `com.haier.cbs.order.dao.EchannelTmallTradeDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByTid`, `select:getByOrderSn`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrderRepairHPQueuesMapper.xml
- namespace: `com.haier.cbs.order.dao.OrderRepairHPQueuesDao`
- statements: `select:get`, `insert:insert`, `update:update`
- tables: `OrderRepairHPQueues`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/OrderWorkflowsMapper.xml
- namespace: `com.haier.cbs.order.dao.OrderWorkflowsDao`
- statements: `select:get`, `select:getByOrderProductId`, `select:getConfirmList`, `select:getHpList`, `select:getNetpointList`, `select:getUserList`, `select:getRepairList`, `select:getHpCancelByOrderProductId`, `select:getOntimeRate`, `select:getOntimeRate`, `select:getRepairListByDate`, `select:getRegions`, `select:getOntimeRateDetailCount`, `select:getOntimeRateDetail`, `select:getShippingTimeByRegionId`, `select:getStorages`, `select:queryById`, `select:getTelephoneInfo`, `select:getTradeInfo`, `select:getCenterInfo`, `select:getShippingTimeInfo`, `update:updateAfterLesShipped`, `update:updateAfterPayment`, `update:updateTime`, `insert:insert`, `update:updateForConformOrder`, `update:updateNetPointArriveTime`, `update:updateUserAcceptTime`, `update:update`, `update:updateAfterSyncOrderToLes`, `update:updateForPubCountTime`, `select:getListByOrderSn`, `update:updateForCancelOrder`, `update:updateSyncVOMTime`
- tables: `NetPoints`, `OrderOperateLogs`, `OrderProducts`, `OrderRepairs`, `OrderWorkflows`, `Orders`, `Regions`, `ReservationShipping`, `Storages`, `id`, `ord_wf_address_list`, `ord_wf_region`

## order-service/order-impl/src/main/resources/order-sql-mapper/EchannelDeliverQueue.xml
- namespace: `com.haier.cbs.order.dao.EchannelDeliverQueueDao`
- statements: `insert:create`, `update:update`, `select:getByStatus`, `select:getByTid`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/VOMReturnLogsMapper.xml
- namespace: `com.haier.cbs.order.dao.VOMReturnLogsDao`
- statements: `select:selectVomReturnLog`, `select:countVomReturnLog`, `insert:saveVomReturnLog`, `update:updateVomReturnLog`, `select:getVomReturnLogByButypeAndOrderno`, `select:getVomReturnLogsByOutcode`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/EamAssetOrderGroupMapper.xml
- namespace: `com.haier.cbs.order.dao.EamAssetOrderGroupDao`
- statements: `select:get`, `select:getByGroupNo`, `select:getByStatus`, `select:selectEamAssetOrderGroup`, `select:countEamAssetOrderGroup`, `insert:saveEamAssetOrderGroup`, `update:updateEamAssetOrderGroup`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/RegionNewOldMapper.xml
- namespace: `com.haier.cbs.order.dao.RegionNewOldDao`
- statements: `select:getByCityIdAndOldRegionName`, `select:getByOldcode`

## order-service/order-impl/src/main/resources/order-sql-mapper/VOMProductAndOrderMapper.xml
- namespace: `com.haier.cbs.order.dao.VOMProductAndOrderDao`
- statements: `insert:saveProduct`, `select:selectProduct`, `select:countProductData`, `update:updateProductDataStatus`, `select:getPdById`, `select:getPdByProductCode`, `insert:savePurchaseOrder`, `update:updatePurOrderNo`, `select:selectPurchaseOrder`, `select:countPurchaseOrder`, `update:updatePurchaseOrder`, `update:updatePurchaseOrderStatus`, `update:updatePurchaseOrderAuditStatus`, `select:getPoById`, `select:countSelfPurchaseOrder`, `select:selectSelfPurchaseOrder`, `select:countRequisition`, `select:selectRequisition`, `select:getPoByOrderNo`, `select:selectStockRecord`, `select:countStockRecord`, `select:selectStockRecordByOrderNo`, `update:deletePurchaseOrder`, `select:getlatestPrice`, `select:selectStore`, `insert:insertPurchaseCost`, `insert:insertPurchaseCostFromProductPrice`, `select:selectPurchaseCost`, `select:getStockByRecordCode`, `insert:saveAwsProduct`, `select:findYBBysku`, `select:selectPurchaseOrderForCreateOrder`, `update:updatePurchaseOrderPlatCheck`, `update:updatePurchaseOrderSecondCheck`, `update:updatePurchaseOrderProductSn`, `select:findPurchaseOrderDetail`
- tables: `PurchaseCost`, `VOMProductData`, `VOMPurchaseOrder`, `id`, `jde_yb_product`, `rrsv3_stock`, `rrsv3_stock_record`, `rrsv3_store`

## order-service/order-impl/src/main/resources/order-sql-mapper/VomProductOuterMapper.xml
- namespace: `com.haier.cbs.order.dao.VomProductOuterDao`
- statements: `select:get`, `select:getBySuccess`, `select:getByOuterSku`, `select:getBySku`, `insert:insert`, `update:update`, `select:countVomProductOuter`, `select:getVomProductOuterByPager`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/ExpressRegisterWriteMapper.xml
- namespace: `com.haier.cbs.order.dao.ExpressRegisterWriteDao`
- statements: `insert:saveExpressRegister`, `update:updateExpressRegister`, `delete:delExpressRegister`
- tables: `express_register`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/RrsCctOrderQueueMapper.xml
- namespace: `com.haier.cbs.order.dao.RrsCctOrderQueueDao`
- statements: `select:get`, `select:getByStatus`, `select:getByOrderProductId`, `insert:insert`, `update:update`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/ExpressAbortWriteMapper.xml
- namespace: `com.haier.cbs.order.dao.ExpressAbortWriteDao`
- statements: `insert:saveExpressAbort`, `update:updateExpressAbort`, `delete:delExpressAbort`
- tables: `express_abort`, `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/ApplyReturnGoodMapper.xml
- namespace: `com.haier.cbs.order.dao.ApplyReturnGoodDao`
- statements: `insert:insert`, `update:update`, `select:get`, `select:getByOrderno`, `select:getByCode`, `select:getByVoucher`, `select:count`, `select:select`
- tables: `id`

## order-service/order-impl/src/main/resources/order-sql-mapper/PackageProductsMapper.xml
- namespace: `com.haier.cbs.order.dao.PackageProductsDao`
- statements: `select:countOf`, `select:findBy`, `select:findById`, `insert:insert`, `select:findBySaleSku`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/CustomizedItem.xml
- namespace: `com.rrsjk.cms.mobile.dao.CustomizedItemDao`
- statements: `insert:insert`, `update:update`, `select:findShowList`, `select:findCount`, `select:find`
- tables: `id`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/LjNewItem.xml
- namespace: `com.rrsjk.cms.mobile.dao.LjNewItemDao`
- statements: `insert:insert`, `update:update`, `select:findList`, `select:findCount`, `select:find`
- tables: `id`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/LjCarousel.xml
- namespace: `com.rrsjk.cms.mobile.dao.LjCarouselDao`
- statements: `insert:insert`, `update:update`, `select:findShowList`, `select:findCount`, `select:find`, `select:getById`
- tables: `id`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/AppSubImage.xml
- namespace: `com.rrsjk.cms.mobile.dao.AppSubImageDao`
- statements: `insert:insert`, `insert:batchInsert`, `update:update`, `select:findShowList`
- tables: `id`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/Bulletin.xml
- namespace: `com.rrsjk.cms.mobile.dao.BulletinDao`
- statements: `insert:insert`, `update:update`, `select:findShowList`, `select:findCount`, `select:find`
- tables: `id`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/WeeklyProductMapper.xml
- namespace: `com.rrsjk.cms.mobile.dao.WeeklyProductDao`
- statements: `select:findWeeklyList`, `delete:deleteByPrimaryKey`, `insert:insert`, `insert:insertWeeklySelective`, `update:updateByPrimaryKeySelective`, `update:updateByPrimaryKey`
- tables: `id`, `weekly_product`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/ArticleItemPackage.xml
- namespace: `com.rrsjk.cms.mobile.dao.ArticleItemPackageDao`
- statements: `insert:insert`, `select:findByArticleId`, `delete:deleteByArticleId`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/GoodlifeClass.xml
- namespace: `com.rrsjk.cms.mobile.dao.GoodlifeClassDao`
- statements: `insert:insert`, `update:update`, `select:findCount`, `select:find`
- tables: `id`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/AppStatistic.xml
- namespace: `com.rrsjk.cms.mobile.dao.AppStatisticDao`
- statements: `insert:insert`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/GroupCustomizedItem.xml
- namespace: `com.rrsjk.cms.mobile.dao.GroupCustomizedItemDao`
- statements: `insert:insert`, `update:update`, `select:findShowList`, `select:getByItemId`, `select:findCount`, `select:find`
- tables: `id`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/VideoMapper.xml
- namespace: `com.rrsjk.cms.mobile.dao.VideoDao`
- statements: `select:selectByPrimaryKey`, `delete:deleteByPrimaryKey`, `insert:insert`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `update:updateByPrimaryKey`, `select:selectBySelective`, `select:selectCountBySelective`
- tables: `id`, `video`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/HomePageHotItem.xml
- namespace: `com.rrsjk.cms.mobile.dao.HomePageHotItemDao`
- statements: `insert:insert`, `update:update`, `select:findList`, `select:findListPage`, `select:findCount`, `select:existenceItem`
- tables: `id`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/Cookbook.xml
- namespace: `com.rrsjk.cms.mobile.dao.CookbookDao`
- statements: `select:selectByPrimaryKey`, `delete:deleteByPrimaryKey`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `update:updateByPrimaryKey`, `select:getCookbookByCategory`, `select:selectPageByPara`, `select:selectCountByPara`
- tables: `cookbook`, `dispenser.water_article`, `id`, `rrsjk_cms.cookbook`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/LjCategory.xml
- namespace: `com.rrsjk.cms.mobile.dao.LjCategoryDao`
- statements: `insert:insert`, `update:update`, `select:findCategoryList`, `select:findCount`, `select:find`, `select:findOtherCategoryList`, `select:getById`
- tables: `id`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/Questionnaire.xml
- namespace: `com.rrsjk.cms.mobile.dao.QuestionnaireDao`
- statements: `insert:insert`, `insert:batchInsert`, `select:getCountByLoginId`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/LjSeckillItem.xml
- namespace: `com.rrsjk.cms.mobile.dao.LjSeckillItemDao`
- statements: `insert:insert`, `update:update`, `select:findList`
- tables: `id`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/Carousel.xml
- namespace: `com.rrsjk.cms.mobile.dao.CarouselDao`
- statements: `insert:insert`, `update:update`, `select:findShowList`, `select:findCount`, `select:find`
- tables: `id`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/HomePageRecommend.xml
- namespace: `com.rrsjk.cms.mobile.dao.HomePageRecommendDao`
- statements: `insert:insert`, `update:update`, `select:findList`
- tables: `id`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/HomePageFloorItem.xml
- namespace: `com.rrsjk.cms.mobile.dao.HomePageFloorItemDao`
- statements: `insert:insert`, `update:update`, `select:findByFloorId`, `select:findCount`, `select:findListPage`, `select:existenceItem`, `update:moveItem`
- tables: `id`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/AppImage.xml
- namespace: `com.rrsjk.cms.mobile.dao.AppImageDao`
- statements: `insert:insert`, `update:update`, `select:findShowList`, `select:findCount`, `select:find`, `select:getLjDiscoverArticleIds`, `select:getLjXcxDiscoverArticleIds`
- tables: `id`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/CookDayMapper.xml
- namespace: `com.rrsjk.cms.mobile.dao.CookDayDao`
- statements: `select:selectByPrimaryKey`, `delete:deleteByPrimaryKey`, `insert:insert`, `insert:insertSelective`, `update:updateByPrimaryKeySelective`, `update:updateByPrimaryKey`, `select:selectBySelective`, `select:selectPageByPara`, `select:selectCountByPara`
- tables: `cook_day`, `dispenser.water_article`, `id`, `rrsjk_cms.cook_day`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/LiveInfoMapper.xml
- namespace: `com.rrsjk.cms.mobile.dao.LiveInfoDao`
- statements: `insert:insert`, `update:updateByPrimaryKeySelective`, `select:getById`, `select:findList`, `select:selectPage`, `select:count`, `select:selectInfoPage`, `select:selectLiveInfo`, `select:selectMinRoomId`, `select:selectMaxRoomId`, `select:selectLiveInfoByCondition`, `select:findLiveInfo`, `select:findCountForCbs`, `select:findForCbs`
- tables: `id`, `live_replay`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/HomePageFloorImage.xml
- namespace: `com.rrsjk.cms.mobile.dao.HomePageFloorImageDao`
- statements: `insert:insert`, `update:update`, `select:findList`, `select:findCount`, `select:find`, `select:findOtherFloorList`, `select:getById`
- tables: `id`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/LjCategoryItem.xml
- namespace: `com.rrsjk.cms.mobile.dao.LjCategoryItemDao`
- statements: `insert:insert`, `update:update`, `select:findByCategoryId`, `select:findCount`, `select:find`, `update:moveItem`
- tables: `id`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/LiveGoodsMapper.xml
- namespace: `com.rrsjk.cms.mobile.dao.LiveGoodsDao`
- statements: `insert:insert`, `insert:batchInsert`, `update:updateByPrimaryKeySelective`, `delete:deleteByRoomId`, `select:findList`
- tables: `id`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/ArticleItem.xml
- namespace: `com.rrsjk.cms.mobile.dao.ArticleItemDao`
- statements: `select:get`, `insert:insert`, `update:update`, `select:findCount`, `select:find`
- tables: `id`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/LiveReplayMapper.xml
- namespace: `com.rrsjk.cms.mobile.dao.LiveRelayDao`
- statements: `insert:insert`, `insert:batchInsert`, `update:updateByPrimaryKeySelective`, `select:getByParams`, `select:findList`, `select:selectPage`, `select:count`, `select:selectLiveRelayPage`
- tables: `id`, `live_replay`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/HomePageCustomZone.xml
- namespace: `com.rrsjk.cms.mobile.dao.HomePageCustomZoneDao`
- statements: `insert:insert`, `update:update`, `select:findListPage`, `select:findList`, `select:findCount`
- tables: `id`

## rrsjk-cms-service/rrsjk-cms-impl/src/main/resources/mybatis/mapper/mobile/LjHotItem.xml
- namespace: `com.rrsjk.cms.mobile.dao.LjHotItemDao`
- statements: `insert:insert`, `update:update`, `select:findList`, `select:findCount`, `select:find`
- tables: `id`

## rrsjk-admin-authz-service/rrsjk-admin-authz-impl/src/main/resources/mybatis/mapper/AuthzRepositoryMapper.xml
- namespace: `com.rrsjk.adminauthz.mapper.AuthzRepositoryMapper`
- statements: `select:findUser`, `select:listAllUsers`, `select:listUsersByClient`, `update:updateUser`, `insert:insertUser`, `select:findPasswordCredential`, `update:updateUserPassword`, `insert:insertUserPassword`, `select:listRoleCodesByUser`, `select:listRoleCodesByUserForClient`, `select:listRolesByCodes`, `select:listAllRoles`, `select:listAllRolesForClient`, `select:countByRoleCode`, `insert:insertRole`, `update:updateRole`, `delete:deleteRole`, `delete:deleteRolePermissions`, `delete:deleteUserRolesByRole`, `delete:deleteUserRoles`, `delete:deleteUserRolesForClient`, `insert:insertUserRole`, `select:listPermissionsByRole`, `select:listAllPermissions`, `select:listAllPermissionsForClient`, `select:listByPermissionKeys`, `select:listByPermissionKeysForClient`, `select:listEffectivePermissionsByUser`, `insert:insertPermission`, `update:updatePermission`, `delete:deletePermission`, `delete:deletePermissionForClient`, `delete:deleteRolePermissionsByPermission`, `delete:deleteRoleClientPermissionsByPermission`, `delete:deleteUserPermissionsByPermission`, `delete:deleteUserClientPermissionsByPermission`, `delete:deleteRoleClientPermissions`, `insert:insertRolePermission`, `delete:deleteUserClientPermissions`, `delete:deleteUserPermissions`, `insert:insertUserPermission`, `select:listRolePermissionKeysByUser`, `select:listDirectPermissionKeysByUser`, `select:listSubCentersByUser`, `select:listAllMenus`, `select:listAllMenusForClient`, `update:updateMenu`, `insert:insertMenu`, `delete:deleteMenu`, `delete:deleteMenuForClient`, `delete:deleteUser`
- tables: `authz_menu`, `authz_permission`, `authz_role`, `authz_role_permission`, `authz_sub_center`, `authz_user`, `authz_user_password`, `authz_user_permission`, `authz_user_role`, `authz_user_sub_center`, `id`

## vpp-api-km/vpp-km-biz/src/main/resources/mapper/km/KnowledgeFileMapper.xml
- namespace: `com.nahui.energy.dao.km.KnowledgeFileMapper`

## vpp-api-km/vpp-km-biz/src/main/resources/mapper/km/KnowledgeUserMapper.xml
- namespace: `com.nahui.energy.dao.km.KnowledgeUserMapper`
- statements: `delete:physicalDeleteBatchIds`
- tables: `knowledge_user`

## vpp-api-km/vpp-km-biz/src/main/resources/mapper/km/KnowledgeFileMappingMapper.xml
- namespace: `com.nahui.energy.dao.km.KnowledgeFileMappingMapper`

## vpp-api-km/vpp-km-biz/src/main/resources/mapper/km/KnowledgeFileLogMapper.xml
- namespace: `com.nahui.energy.dao.km.KnowledgeFileLogMapper`

## vpp-api-km/vpp-km-biz/src/main/resources/mapper/km/KnowledgeDirectoryMapper.xml
- namespace: `com.nahui.energy.dao.km.KnowledgeDirectoryMapper`
- statements: `select:queryByPage`

## rrsjk-pay-service/rrsjk-pay-impl/src/main/resources/mybatis/mapper/payment/Payment.xml
- namespace: `com.rrsjk.pay.payment.dao.PaymentDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByPayNo`, `select:getByThirdTradeNo`, `select:findBySceneNo`, `select:findTransferByPaid`
- tables: `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/order/WoPart.xml
- namespace: `com.pvs.ops.repairs.order.dao.WoPartDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:updateByParams`, `select:findByOrderWoPart`, `select:countOfOrderWoPart`, `select:selectIdByWoId`, `select:selectIdByWoIdIncrement`, `select:getbatchNumByNo`, `select:getBorrowNumByWoId`, `select:getBorrowPartByWoId`
- tables: `cd_dict_data`, `cd_material`, `cd_warehouse`, `id`, `sp_express_company`, `sp_nsco_trace`, `sp_order`, `sp_order_borrow`, `sp_order_borrow_detail`, `sp_order_detail`, `wo_part`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/order/SpTranDetail.xml
- namespace: `com.pvs.ops.repairs.order.dao.SpTranDetailDao`
- statements: `select:findBy`, `select:findInfoList`, `select:countOf`, `insert:create`, `update:update`, `update:batchUpdate`, `insert:batchInsert`, `select:getById`, `select:getByOrderIdMaterialId`, `select:getDetailInfo`, `select:findByOutInfoByTran`, `update:batchUpdateByBatchNumAndTranId`, `update:updateIfWarrantByWoPartId`, `update:batchUpdateWithBatchNumByIds`
- tables: `cd_material`, `id`, `sp_order_detail`, `sp_tran`, `sp_tran_detail`, `sp_tran_sn`, `sp_tran_sn_detail`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/order/SpReserveAllocationOrderDetail.xml
- namespace: `com.pvs.ops.repairs.order.dao.SpReserveAllocationOrderDetailDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getListByOrderCode`
- tables: `id`, `sp_reserve_allocation_order`, `sp_reserve_allocation_order_detail`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/order/SpOldbackLists.xml
- namespace: `com.pvs.ops.repairs.order.dao.SpOldbackListsDao`
- statements: `select:findBy`, `select:findBySelect`, `select:findBySelectListInfo`, `select:countOfSelect`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:queryUnconfirmedOldBack`, `update:updateExpressSingByExpressInfo`, `update:batchUpdateById`
- tables: `cd_material`, `cd_warehouse`, `id`, `sp_express_company`, `sp_oldback_lists`, `sp_oldback_lists_detail`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/order/SpOrderBorrowDetail.xml
- namespace: `com.pvs.ops.repairs.order.dao.SpOrderBorrowDetailDao`
- statements: `select:findBy`, `select:getById`, `insert:create`, `insert:batchInsert`, `update:update`, `select:countOf`, `update:del`
- tables: `id`, `sp_order_borrow_detail`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/order/SpTran.xml
- namespace: `com.pvs.ops.repairs.order.dao.SpTranDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:queryCountBy`, `select:queryListBy`, `select:queryListByTwoStore`, `select:queryListByTwoStoreCount`, `select:queryListByTwoStoreExport`, `select:queryListInfo`
- tables: `cd_material`, `cd_warehouse`, `id`, `sp_purchase`, `sp_reserve_allocation_order`, `sp_tran`, `sp_tran_detail`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/order/SpOrderBorrow.xml
- namespace: `com.pvs.ops.repairs.order.dao.SpOrderBorrowDao`
- statements: `select:findBy`, `select:getListInfo`, `select:countOfListInfo`, `select:getById`, `insert:create`, `update:update`, `update:updateByOrderNo`, `select:countOf`
- tables: `cd_warehouse`, `id`, `sp_order_borrow`, `sp_order_borrow_detail`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/order/SpReserveAllocationOrder.xml
- namespace: `com.pvs.ops.repairs.order.dao.SpReserveAllocationOrderDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `update:updateByOrderCode`, `insert:batchInsert`, `select:getById`
- tables: `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/order/SpOrderBack.xml
- namespace: `com.pvs.ops.repairs.order.dao.SpOrderBackDao`
- statements: `select:findBy`, `select:countOf`, `select:getById`, `insert:create`, `update:update`
- tables: `id`, `sp_order_back`, `sp_order_borrow`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/order/SpOrderBackInvoice.xml
- namespace: `com.pvs.ops.repairs.order.dao.SpOrderBackInvoiceDao`
- statements: `select:findBy`, `select:countOf`, `select:getById`, `insert:create`, `update:update`, `delete:delByOrderId`
- tables: `id`, `sp_order_back_invoice`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/order/SpQualityInspect.xml
- namespace: `com.pvs.ops.repairs.order.dao.SpQualityInspectDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/order/SpOldbackListsDetail.xml
- namespace: `com.pvs.ops.repairs.order.dao.SpOldbackListsDetailDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:del`, `select:findBackListsBy`, `select:supplierFindListsBy`, `select:supplierCountOf`, `update:batchUpdateById`, `update:batchUpdateByBatchNumAndOldbackId`
- tables: `cd_material`, `cd_warehouse`, `id`, `sp_oldback_lists`, `sp_oldback_lists_detail`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/order/SpTranOut.xml
- namespace: `com.pvs.ops.repairs.order.dao.SpTranOutDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findExpressBy`, `select:countOfExpress`
- tables: `cd_material`, `cd_warehouse`, `id`, `sp_express_company`, `sp_order`, `sp_tran`, `sp_tran_detail`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/order/SpTranSnDetailSh.xml
- namespace: `com.pvs.ops.repairs.order.dao.SpTranSnDetailShDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `cd_material`, `cd_warehouse`, `id`, `sp_order`, `sp_tran`, `sp_tran_sn`, `sp_tran_sn_detail_sh`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/order/SpTranSnDetail.xml
- namespace: `com.pvs.ops.repairs.order.dao.SpTranSnDetailDao`
- statements: `select:findBy`, `select:selectList`, `select:countOf`, `insert:create`, `update:update`, `delete:deleteByTranId`, `insert:batchInsert`, `select:getById`, `update:batchDelete`, `select:countOfRelation`, `select:queryNetStoreId`, `select:queryOldPartsDetail`, `update:updateApprove`, `select:selectListByWoPartId`, `select:tranSnDetailByWoPartId`, `update:batchUpdateByBatchNumAndTranId`
- tables: `cd_material`, `id`, `sp_nsco_trace`, `sp_tran_sn`, `sp_tran_sn_detail`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/order/SpTranSn.xml
- namespace: `com.pvs.ops.repairs.order.dao.SpTranSnDao`
- statements: `select:findBy`, `select:queryPage`, `select:queryPageTranSnIn`, `select:queryPageTranSnInListInfo`, `select:countOf`, `select:countOfTranSnOut`, `select:countOfTranSnIn`, `select:queryCountOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getBorrowTranById`, `select:querySpTranSnPage`, `select:getStockAdjustmentListInfo`, `select:countOfNewAndOldParts`, `select:queryNewAndOldPartsPage`, `select:tranSnOutByWoPartId`, `select:tranSnByWoPartIdAndType`, `select:selectCountByPartId`, `select:countOfBorrow`, `select:queryBorrowPage`, `update:batchUpdateById`
- tables: `cd_material`, `cd_warehouse`, `id`, `sp_order`, `sp_order_borrow`, `sp_tran`, `sp_tran_sn`, `sp_tran_sn_detail`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/order/SpNscoTrace.xml
- namespace: `com.pvs.ops.repairs.order.dao.SpNscoTraceDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `update:updateByWoPartId`, `insert:batchInsert`, `select:getById`, `update:updateReceiveDate`, `select:getPendingShipmentInformation`, `update:updateByPartIdAndWoId`, `select:getByWoPartId`, `update:updateByPartId`
- tables: `id`, `sp_nsco_trace`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/order/SpOrderDetail.xml
- namespace: `com.pvs.ops.repairs.order.dao.SpOrderDetailDao`
- statements: `select:findBy`, `select:findList`, `select:countOf`, `insert:create`, `update:update`, `update:del`, `insert:batchInsert`, `select:getById`, `select:orderExecutionPage`, `select:orderExecutionCountOf`, `select:ordeMatchingByOrderId`, `select:orderCenterMatchingByOrderId`, `select:orderDetailByOrderId`, `select:getByParam`, `select:findMaterialByOrderId`
- tables: `cd_dict_data`, `cd_material`, `cd_warehouse`, `id`, `sp_order`, `sp_order_detail`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/order/SpOrder.xml
- namespace: `com.pvs.ops.repairs.order.dao.SpOrderDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:servicePITPage`, `select:getServicePITListInfo`, `select:countServicePIT`, `select:nodeInfo`, `select:getListExcel`, `select:serviceRrsBuyLossPage`, `select:countServiceRrsBuyLoss`
- tables: `cd_branch_info`, `cd_warehouse`, `id`, `sp_order`, `sp_order_detail`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/order/SpIssueJobLog.xml
- namespace: `com.pvs.ops.repairs.order.dao.SpIssueJobLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/order/SpOrderBorrowSn.xml
- namespace: `com.pvs.ops.repairs.order.dao.SpOrderBorrowSnDao`
- statements: `select:findBy`, `select:getById`, `select:selectModelSnByOrderNo`, `insert:create`, `update:update`, `insert:batchInsertModelSn`, `select:selectBorrowModelSn`, `update:batchUpdate`, `delete:deleteSnByOrderno`, `select:findDifferentCodeOldback`
- tables: `id`, `sp_order_borrow`, `sp_order_borrow_sn`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/order/SpQualityInspectDetail.xml
- namespace: `com.pvs.ops.repairs.order.dao.SpQualityInspectDetailDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteByQualityOrderId`
- tables: `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/inverter/SpInverterSnInfo.xml
- namespace: `com.pvs.ops.repairs.inverter.dao.SpInverterSnInfoDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:del`
- tables: `id`, `sp_inverter_service_sn`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/inverter/SpInverterInfo.xml
- namespace: `com.pvs.ops.repairs.inverter.dao.SpInverterInfoDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/report/SpSupplierPartsCost.xml
- namespace: `com.pvs.ops.repairs.report.dao.SpSupplierPartsCostDao`
- statements: `select:findBy`, `select:countOf`, `select:countOfByWoPartId`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:supplierPartsCostJob`, `select:groupedByMonthAndSupplierWithPage`, `select:countGroupedByMonthAndSupplier`, `select:getPageTwoLevel`, `select:countOfTwoLevel`
- tables: `cd_material`, `id`, `sp_supplier_parts_cost`, `sp_tran_sn`, `sp_tran_sn_detail`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/report/HDSMonitoringReport.xml
- namespace: `com.pvs.ops.repairs.report.dao.HDSMonitoringReportDao`
- statements: `select:findBy`, `select:countOf`
- tables: `cd_dict_data`, `cd_material`, `cd_warehouse`, `sp_express_company`, `sp_order`, `sp_order_borrow`, `sp_tran`, `sp_tran_detail`, `sp_tran_sn`, `sp_tran_sn_detail`, `sp_tran_sn_detail_sh`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/report/OrderMaterialReport.xml
- namespace: `com.pvs.ops.repairs.report.dao.OrderMaterialReportDao`
- statements: `select:findBy`, `select:countOf`
- tables: `cd_dict_data`, `cd_material`, `cd_warehouse`, `sp_nsco_trace`, `sp_order`, `sp_order_detail`, `wo_part`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/report/HDSReturnMonitoring.xml
- namespace: `com.pvs.ops.repairs.report.dao.HDSReturnMonitoringDao`
- statements: `select:findBy`, `select:countOf`
- tables: `cd_dict_data`, `cd_material`, `cd_warehouse`, `sp_express_company`, `sp_oldback_lists`, `sp_oldback_lists_detail`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/report/OrderMonitorDelivery.xml
- namespace: `com.pvs.ops.repairs.report.dao.OrderMonitorDeliveryReportDao`
- statements: `select:findBy`, `select:countOf`
- tables: `cd_dict_data`, `cd_material`, `cd_warehouse`, `sp_order`, `sp_order_detail`, `wo_part`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/workflow/WfFormDao.xml
- namespace: `com.pvs.ops.flowable.dao.WfFormDao`
- statements: `select:queryListBy`, `select:queryCountBy`, `insert:insert`, `update:update`, `insert:batchInsert`, `select:getById`, `select:selectFormVoListByDeployId`, `delete:deleteBatchIds`
- tables: `id`, `wf_deploy_form`, `wf_form`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/workflow/ActWorkflowInfo.xml
- namespace: `com.pvs.ops.flowable.dao.ActWorkflowInfoDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByBusinessKey`
- tables: `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/workflow/WfDeployFormDao.xml
- namespace: `com.pvs.ops.flowable.dao.WfDeployFormDao`
- statements: `select:queryListBy`, `select:queryCountBy`, `insert:insert`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteById`
- tables: `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/workflow/WfCopyDao.xml
- namespace: `com.pvs.ops.flowable.dao.WfCopyDao`
- statements: `select:queryListBy`, `select:queryCountBy`, `insert:insert`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/workflow/WfCategoryDao.xml
- namespace: `com.pvs.ops.flowable.dao.WfCategoryDao`
- statements: `select:queryListBy`, `select:queryCountBy`, `insert:insert`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteBatchIds`, `select:checkCategoryCodeUnique`
- tables: `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/finance/SpAdvancePayment.xml
- namespace: `com.pvs.ops.repairs.finance.dao.SpAdvancePaymentDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `update:updateAdvanceStatus`, `insert:batchInsert`, `select:getById`, `select:queryCountBy`, `select:queryListBy`
- tables: `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/finance/SpSettlementData.xml
- namespace: `com.pvs.ops.repairs.finance.dao.SpSettlementDataDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findTranSnDetailByIfWarrant`, `select:findOldbackDetailByIfWarrant`, `select:findtranSnByIfWarrant`, `select:findOldbackDutyDetailByIfWarrant`
- tables: `cd_material`, `cd_warehouse`, `id`, `sp_oldback_lists`, `sp_oldback_lists_detail`, `sp_tran_sn`, `sp_tran_sn_detail`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/finance/SpAdvanceClearEntity.xml
- namespace: `com.pvs.ops.repairs.finance.dao.SpAdvanceClearEntityDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getOnOrderAmnt`
- tables: `id`, `sp_order`, `sp_order_detail`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/finance/SpSapAccount.xml
- namespace: `com.pvs.ops.repairs.finance.dao.SpSapAccountDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/finance/SpAccountsPayableDetail.xml
- namespace: `com.pvs.ops.repairs.finance.dao.SpAccountsPayableDetailDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/finance/ApAccountsDcc.xml
- namespace: `com.pvs.ops.repairs.finance.dao.SpAccountsDccDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByRelationNo`
- tables: `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/finance/SpAccountsPayable.xml
- namespace: `com.pvs.ops.repairs.finance.dao.SpAccountsPayableDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByAccountNo`
- tables: `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/finance/SpAccountsReceivableDetail.xml
- namespace: `com.pvs.ops.repairs.finance.dao.SpAccountsReceivableDetailDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/finance/SpAccountsReceivable.xml
- namespace: `com.pvs.ops.repairs.finance.dao.SpAccountsReceivableDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByAccountNo`
- tables: `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/express/SpExpressRouting.xml
- namespace: `com.pvs.ops.repairs.express.dao.SpExpressRoutingDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteByCom`, `select:findExpressDetailByNuAndCom`
- tables: `cd_dict_data`, `id`, `sp_express_routing`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/express/SpRoutingLog.xml
- namespace: `com.pvs.ops.repairs.express.dao.SpRoutingLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/express/SpExpressCompany.xml
- namespace: `com.pvs.ops.repairs.express.dao.SpExpressCompanyDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByCode`
- tables: `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/base/SpFile.xml
- namespace: `com.pvs.ops.repairs.base.dao.SpFileDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `update:del`, `insert:batchInsert`, `select:getById`
- tables: `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/base/SpInterfaceLog.xml
- namespace: `com.pvs.ops.repairs.capital.dao.SpInterfaceLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/base/CdFile.xml
- namespace: `com.pvs.ops.repairs.base.dao.CdFileDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `delete:deleteByMainDetailId`, `update:del`
- tables: `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/base/SpForegift.xml
- namespace: `com.pvs.ops.repairs.capital.dao.SpForegiftDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:queryCountBy`, `select:queryListBy`, `select:querySourceAndBatch`
- tables: `cd_warehouse`, `id`, `sp_foregift`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/base/SpWarehouseAttach.xml
- namespace: `com.pvs.ops.repairs.capital.dao.SpWarehouseAttachDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findListBy`, `select:countListOf`, `select:findAttach`, `select:orderedAmount`, `select:transitAmount`, `select:inventoryAmount`
- tables: `cd_material`, `cd_warehouse`, `id`, `sp_order`, `sp_storeage`, `sp_tran_sn`, `sp_warehouse_attach`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/base/CdWarehouse.xml
- namespace: `com.pvs.ops.repairs.base.dao.CdWarehosueDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `update:batchUpdate`, `insert:batchInsert`, `select:getById`, `select:queryCountBy`, `select:queryListBy`, `select:queryBatchByIds`, `select:queryBatchByMemberIds`, `select:queryBatchByBranchIds`, `select:findWarehousePosByCodey`
- tables: `cd_pos`, `cd_warehouse`, `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/base/CdWarehouseAddress.xml
- namespace: `com.pvs.ops.repairs.base.dao.CdWarehouseAddressDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `update:updateDefault`, `insert:batchInsert`, `select:getById`
- tables: `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/base/SpPurchase.xml
- namespace: `com.pvs.ops.repairs.capital.dao.SpPurchaseDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:queryCountBy`, `select:queryListBy`
- tables: `cd_branch_info`, `cd_warehouse`, `id`, `sp_purchase`, `sp_purchase_detail`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/base/CdPos.xml
- namespace: `com.pvs.ops.repairs.base.dao.CdPosDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `cd_pos`, `cd_warehouse`, `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/base/CdWarehouseCenter.xml
- namespace: `com.pvs.ops.repairs.base.dao.CdWarehouseCenterDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/base/CdMaterialSubstitute.xml
- namespace: `com.pvs.ops.repairs.base.dao.CdMaterialSubstituteDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:queryCountBy`, `select:queryListBy`, `select:queryCountByParam`, `select:queryListByParam`
- tables: `cd_material`, `cd_material_substitute`, `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/base/CdDictData.xml
- namespace: `com.pvs.ops.repairs.base.dao.CdDictDataDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:updateOrDelete`
- tables: `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/base/SpStoreage.xml
- namespace: `com.pvs.ops.repairs.capital.dao.SpStoreageDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:queryCountBy`, `select:queryListBy`, `select:queryListInfo`, `select:getActiveAmountByMaterialStore`, `select:getStoreageList`, `select:getStoreageTotalList`, `select:getByParam`, `select:getEffectiveInventory`, `delete:delete`, `select:findByPage`, `update:batchUpdate`, `delete:batchDeleteByIds`
- tables: `cd_dict_data`, `cd_material`, `cd_warehouse`, `id`, `sp_storeage`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/base/CdMaterial.xml
- namespace: `com.pvs.ops.repairs.base.dao.CdMaterialDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `update:updateProcRrsSuccessByIds`, `insert:batchInsert`, `select:getById`, `select:queryCountBy`, `select:queryListBy`, `select:queryBatchByIds`, `select:getSubstituteByMaterialId`, `select:getUseDataById`
- tables: `cd_dict_data`, `cd_material`, `cd_material_substitute`, `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/base/SpMaterialNum.xml
- namespace: `com.pvs.ops.repairs.capital.dao.SpMaterialNumDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/base/CdBranchInfo.xml
- namespace: `com.pvs.ops.repairs.base.dao.CdBranchInfoDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `update:batchUpdate`, `insert:batchInsert`, `select:getById`, `select:queryCountBy`, `select:queryListBy`, `select:queryBatchByIds`
- tables: `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/base/SpStoreageLog.xml
- namespace: `com.pvs.ops.repairs.capital.dao.SpStoreageLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/base/CdMaterialWarrant.xml
- namespace: `com.pvs.ops.repairs.base.dao.CdMaterialWarrantDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:queryCountBy`, `select:queryListBy`
- tables: `cd_material`, `cd_material_warrant`, `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/base/CdWarehouseRoute.xml
- namespace: `com.pvs.ops.repairs.base.dao.CdWarehouseRouteDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:queryCountBy`, `select:queryListBy`, `select:getRouteWarehoueBuMemberId`
- tables: `cd_warehouse`, `cd_warehouse_route`, `id`

## repairs/repairs-impl/src/main/resources/mybatis/mapper/base/SpPurchaseDetail.xml
- namespace: `com.pvs.ops.repairs.capital.dao.SpPurchaseDetailDao`
- statements: `select:findBy`, `select:queryInfoList`, `select:countOf`, `insert:create`, `update:update`, `update:del`, `insert:batchInsert`, `select:getById`, `select:findByList`
- tables: `cd_material`, `id`, `sp_purchase_detail`, `sp_tran`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/shop/SapRecord.xml
- namespace: `com.rrsjk.report.dao.shop.SapRecordDao`
- statements: `select:findEcoToiletIncome`, `select:findEcoToiletIncomeCx`, `select:findIncome`, `select:findIncomeCx`, `select:findBidByYwmsAndTime`, `select:findYuexiuRecordBidList`, `select:findZHRecordBidList`, `select:findZHEPCIncomeBids`, `select:findZHEPCCXBids`, `select:findYXEPCIncomeBids`, `select:findYXEPCCXBids`
- tables: `sap_item_record`, `sap_record`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/operation/LightOperationWorkOrderMapper.xml
- namespace: `com.rrsjk.report.dao.operation.LightOperationWorkOrderDao`
- statements: `insert:insert`, `insert:batchInsert`, `update:updateById`, `select:selectById`, `select:selectAll`, `select:selectByCondition`, `select:count`, `select:countInService`, `select:countFinishedOfThisMonth`, `select:countFinished`
- tables: `id`, `light_operation_work_order`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/operation/WorkOrderCount.xml
- namespace: `com.rrsjk.report.dao.operation.WorkOrderCountDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByFetchAt`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/operation/LightWorkOrder.xml
- namespace: `com.rrsjk.report.dao.operation.LightWorkOrderDao`
- statements: `select:findBy`, `select:countOf`, `select:countOfService`, `select:findCount`
- tables: `light_work_order`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/operation/LightOperationElecPrice.xml
- namespace: `com.rrsjk.report.dao.operation.LightOperationElecPriceDao`
- statements: `select:findBy`, `select:findLastMonthPrice`
- tables: `light_operation_elec_price`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/CmConstructionProgressAudit.xml
- namespace: `com.rrsjk.report.dao.light.CmConstructionProgressAuditDao`
- statements: `select:listAuditWithProject`
- tables: `cm_construction_progress_audit`, `cm_light_project`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightPurchaseOrder.xml
- namespace: `com.rrsjk.report.dao.light.LightPurchaseOrderDao`
- statements: `select:findBy`, `select:findOverdueReportDetail`, `select:countOfOverdueReportDetail`
- tables: `light_purchase_order`, `light_sp_store`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/ReportConfigQueryMapper.xml
- namespace: `com.rrsjk.report.dao.light.ReportConfigQueryDao`
- statements: `select:findPurchasePriceBy`, `select:findComponentPriceBy`, `select:findCompetitorPriceBy`, `select:queryProjectManagement`, `select:findComponentSwitchBy`
- tables: `light_project_management`, `light_report_competitor_price`, `light_report_component_price`, `light_report_component_switch`, `light_report_purchase_price`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightElectricOrder.xml
- namespace: `com.rrsjk.report.dao.light.LightElectricOrderDao`
- statements: `select:findCount`, `select:findAmount`, `select:findPaymentTime`, `select:findList`, `select:findPaymentMoney`, `select:findListByBeneficiary`, `select:findListRegionByBeneficiary`, `select:findListByBeneficiaryExcludeYueXiu`
- tables: `light_station`, `yuexiu_electricity_bill`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightInstantReward.xml
- namespace: `com.rrsjk.report.dao.light.LightInstantRewardDao`
- statements: `select:findBy`, `select:countOf`, `select:getById`, `select:findByNotConfirm`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightSubSpRegion.xml
- namespace: `com.rrsjk.report.dao.light.LightSubSpRegionDao`
- statements: `select:findList`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightAuditDispatchLog.xml
- namespace: `com.rrsjk.report.dao.light.LightAuditDispatchLogDao`
- statements: `select:processCloseReportData`, `select:processTimeLinessData`
- tables: `city`, `light_audit_dispatch_log`, `light_station`, `light_station_audit`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightZeroCarbonStation.xml
- namespace: `com.rrsjk.report.dao.light.LightZeroCarbonStationDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:getByStationCode`, `select:countOf`, `select:findBy`, `select:findByPhone`, `select:findByAuditType`, `select:countOfAuditType`, `select:findFinishedStation`, `select:getLightStationByDraftId`, `select:findZeroCarbonStationCount`, `select:findZeroCarbonStationList`, `select:findZeroCarbonStationCountEnable`, `select:findZeroCarbonStationListEnable`, `select:findCountForReport`, `select:findListForReport`
- tables: `id`, `light_zero_carbon_station`, `light_zero_carbon_station_audit`, `light_zero_carbon_station_register_draft`, `rrsjk_light.light_zero_carbon_station`, `zero_carbon_service_provider`, `zero_carbon_station_relate_file`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/City.xml
- namespace: `com.rrsjk.report.dao.light.CityDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findSettledCityList`, `select:findByCodes`, `select:findZHStationSubCenterByTime`, `select:findOneByCityCode`, `select:getAllCenter`, `select:getAllGroupSubCenter`
- tables: `city`, `id`, `light_station`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightStationInverter.xml
- namespace: `com.rrsjk.report.dao.light.LightStationInverterDao`
- statements: `select:findByStationId`, `select:findByStationIds`, `select:findByStationCityIds`, `select:findByInverterSn`, `select:findByStationByCond`, `select:findGridInverter`
- tables: `light_station`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightStationAudit.xml
- namespace: `com.rrsjk.report.dao.light.LightStationAuditDao`
- statements: `select:findOneByStationId`
- tables: `light_station_audit`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightElectTarget.xml
- namespace: `com.rrsjk.report.dao.light.LightElectTargetDao`
- statements: `select:findBy`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightProjectRent.xml
- namespace: `com.rrsjk.report.dao.light.LightProjectRentDao`
- statements: `select:findByStationCode`
- tables: `light_project_rent`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightSkuData.xml
- namespace: `com.rrsjk.report.dao.light.LightSkuDataDao`
- statements: `select:findByParams`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightProjectManagement.xml
- namespace: `com.rrsjk.report.dao.light.LightProjectManagementDao`
- statements: `select:findByProjectCode`, `select:findByProjectCodes`
- tables: `light_project_management`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightComponentLibrary.xml
- namespace: `com.rrsjk.report.dao.light.LightComponentLibraryDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:countOfAge`, `select:findAgeBy`, `update:freezeAssemblySn`, `update:disableAssemblySn`, `select:findAgeByInTransfer`, `select:countOfAgeTransfer`
- tables: `id`, `light_component_library`, `light_module_sn`, `light_purchase_order`, `light_transfer_order`, `light_transfer_order_sn`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightCityElecPrice.xml
- namespace: `com.rrsjk.report.dao.light.LightCityElecPriceDao`
- statements: `select:findElecPrice`, `select:findAll`, `select:find`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightSpOpGroupSum.xml
- namespace: `com.rrsjk.report.dao.light.LightSpOpGroupSumDao`
- statements: `select:findVillageXgj`, `select:findVillageXgjBySpName`
- tables: `light_sp_op_group_sum`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightSpAuthorityZone.xml
- namespace: `com.rrsjk.report.dao.light.LightSpAuthorityZoneDao`
- statements: `select:findRegionNum`, `select:findList`
- tables: `light_sp_authority_zone`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightStationNannyUser.xml
- namespace: `com.rrsjk.report.dao.light.LightStationNannyUserDao`
- statements: `insert:create`, `update:update`, `select:queryBy`
- tables: `id`, `light_station_nanny_user`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightSpGridAwardOrderDetail.xml
- namespace: `com.rrsjk.report.dao.light.LightSpGridAwardOrderDetailDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByOrderId`, `select:getByStationCodeList`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightCompanyPolicy.xml
- namespace: `com.rrsjk.report.dao.light.LightCompanyPolicyDao`
- statements: `select:findPrice`, `select:findYgfPrice`, `select:findByPolicyAndTime`, `select:findDistinctDimensions`
- tables: `light_company_manage_region`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/PuYinTradeIncomeSettle.xml
- namespace: `com.rrsjk.report.dao.light.PuYinTradeIncomeSettleDao`
- statements: `select:findStationCode`, `select:findBy`
- tables: `pu_yin_trade_income_settle`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightInstantRewardPolicy.xml
- namespace: `com.rrsjk.report.dao.light.LightInstantRewardPolicyDao`
- statements: `select:findBy`, `select:findEnableByTime`, `select:checkCompleteAt`, `select:countOf`, `select:getById`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightSpOrderItem.xml
- namespace: `com.rrsjk.report.dao.light.LightSpOrderItemDao`
- statements: `select:findByTime`, `select:findByStationList`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightNewMerchantRewardItem.xml
- namespace: `com.rrsjk.report.dao.light.LightNewMerchantRewardItemDao`
- statements: `select:findBy`, `select:countOf`, `insert:batchInsert`, `update:update`, `update:removeCostVoucher`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/EnergyAuditStatusReport.xml
- namespace: `com.rrsjk.report.dao.light.EnergyAuditStatusReportDao`
- statements: `select:findParty`, `select:findSp`
- tables: `ehaier_system.sys_party`, `light_service_provider`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/ZhongYinTradeIncomeSettle.xml
- namespace: `com.rrsjk.report.dao.light.ZhongYinTradeIncomeSettleDao`
- statements: `select:findBy`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/CmSimpleProject.xml
- namespace: `com.rrsjk.report.dao.light.CmSimpleProjectDao`
- statements: `select:findIncomeCodeList`, `select:findSignGuaranteeRateReport`
- tables: `cm_light_project_income`, `cm_light_project_income_amount`, `cm_simple_project`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightCompanyManageRegion.xml
- namespace: `com.rrsjk.report.dao.light.LightCompanyManageRegionDao`
- statements: `select:findEnabledRegions`, `select:findByDimensions`
- tables: `light_company_manage_region`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightElectricMonthSum.xml
- namespace: `com.rrsjk.report.dao.light.LightElectricMonthSumDao`
- statements: `select:findCountByTime`, `select:findSumByTime`, `select:findList`, `select:findListToElecIncome`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/EnergyAuditValidityReport.xml
- namespace: `com.rrsjk.report.dao.light.EnergyAuditValidityReportDao`
- statements: `select:auditValidity`, `select:countByPeopleNameAndAuditType`
- tables: `light_station_operate_log`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/lightModuleSn.xml
- namespace: `com.rrsjk.report.dao.light.LightModuleSnDao`
- statements: `select:findBy`, `select:findList`, `select:countOf`, `select:getById`
- tables: `light_station`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/HuaRongTradeIncomeSettle.xml
- namespace: `com.rrsjk.report.dao.light.HuaRongTradeIncomeSettleDao`
- statements: `select:findBy`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightRent.xml
- namespace: `com.rrsjk.report.dao.light.LightRentDao`
- statements: `select:findProvince`, `select:findStationCodeByProvince`, `select:findStationIdByProvince`, `select:findCost`, `select:findCostByStationCode`, `select:findOneByStationCode`, `select:findDayCostByStationCode`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightStationEpc.xml
- namespace: `com.rrsjk.report.dao.light.LightStationEpcDao`
- statements: `select:findByStationId`
- tables: `light_station_epc`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightStation.xml
- namespace: `com.rrsjk.report.dao.light.LightStationDao`
- statements: `update:update`, `select:get`, `select:getByStationCode`, `select:getByStationCodes`, `select:findStationSum1`, `select:findStationSum`, `select:findStationSumUpgrade`, `select:findStationRegionSum`, `select:findAllStationRegionSum`, `select:findStationCode`, `select:findStationCodeYearMonth`, `select:findByParams`, `select:findStationByParams`, `select:findAreaSum`, `select:findProvince`, `select:findStationCodeByProvince`, `select:findHouseHoldProvince`, `select:findHouseHoldStation`, `select:findMultiProvince`, `select:findMultiStation`, `select:findIndustryProvince`, `select:findIndustryStation`, `select:findSocialProvince`, `select:findSocialStation`, `select:findWholeProvince`, `select:findWholeStation`, `select:findStationIdByProvince`, `select:findMulti`, `select:findIndustry`, `select:findSocial`, `select:findWhole`, `select:findGridHouseNum`, `select:findGridHouseNumBySubNameList`, `select:findInstallHouseNum`, `select:findInstallHouseNumBySubNameList`, `select:findOrderHouseNum`, `select:findOrderHouseNumBySubNameList`, `select:findGridQuota`, `select:findGridQuotaBySubNameList`, `select:findHouseholdGridQuota`, `select:findPublicBuildingsGridQuota`, `select:findHouseholdGridQuotaBT`, `select:findPublicBuildingsGridQuotaBT`, `select:findHouseholdGridQuotaYX`, `select:findPublicBuildingsGridQuotaYX`, `select:findHouseholdGridQuotaZH`, `select:findPublicBuildingsGridQuotaZH`, `select:findMultiGridQuota`, `select:findIndustryGridQuota`, `select:findSocialGridQuota`, `select:findWholeGridQuota`, `select:findInstallQuota`, `select:findInstallQuotaBySubNameList`, `select:findOrderQuota`, `select:findOrderQuotaBySubNameList`, `select:findEfNetTotal`, `select:findSpTodayInstall`, `select:findSpFirstInstall`, `select:findSpMonthInstall`, `select:findOrderSpId`, `select:findGridByCenter`, `select:findGridByCityId`, `select:findGridQuotaByCityId`, `select:findHouseholdGridQuotaByCityId`, `select:findPublicBuildingsGridQuotaByCityId`, `select:findMultiGridQuotaByCityId`, `select:findIndustryGridQuotaByCityId`, `select:findInstallHouseNumByCityId`, `select:findOrderHouseNumByCityId`, `select:findInstallQuotaByCityId`, `select:findOrderQuotaByCityId`, `select:findEfNetTotalByCityId`, `select:findSpMonthInstallByCityId`, `select:findOrderSpIdByCityId`, `select:findGridBySpId`, `select:findGridQuotaBySpId`, `select:findInstallHouseNumBySpId`, `select:findOrderHouseNumBySpId`, `select:findInstallQuotaBySpId`, `select:findOrderQuotaBySpId`
- tables: `city`, `cmb_leasing_station`, `id`, `light_company_info`, `light_make_order`, `light_purchase_order`, `light_service_provider`, `light_station`, `light_station_audit`, `light_station_operate_log`, `light_station_yuexiu`, `light_station_yuexiu_settle`, `light_zh_settle`, `rrsjk_light_report.energy_summary_target`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightTransferOrder.xml
- namespace: `com.rrsjk.report.dao.light.LightTransferOrderDao`
- statements: `select:findBy`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightRentPolicy.xml
- namespace: `com.rrsjk.report.dao.light.LightRentPolicyDao`
- statements: `select:findByProjectId`
- tables: `light_rent_policy`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/CmLightProject.xml
- namespace: `com.rrsjk.report.dao.light.CmLightProjectDao`
- statements: `select:findByProjectCode`, `select:findIncomeCodeList`, `select:findThirdIncomeCodeList`, `select:findSignGuaranteeRateReport`
- tables: `cm_contract_manage`, `cm_light_project`, `cm_light_project_income`, `cm_light_project_income_amount`, `cm_light_project_income_confirm`, `cm_payment_milestone_audit`, `cm_receipt_milestone`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightUnionpayRent.xml
- namespace: `com.rrsjk.report.dao.light.LightUnionpayRentDao`
- statements: `select:findByStationCode`
- tables: `light_unionpay_rent`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightRentRecord.xml
- namespace: `com.rrsjk.report.dao.light.LightRentRecordDao`
- statements: `select:findListByDueAt`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightYuexiuIncomeBill.xml
- namespace: `com.rrsjk.report.dao.light.LightYuexiuIncomeBillDao`
- statements: `select:findReceivedAmount`, `select:findListByWriteOffFlagAndCfDirection`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightCostAccount.xml
- namespace: `com.rrsjk.report.dao.light.LightCostAccountDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:getByStationId`, `select:getByStationIdList`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightStationEnableReward.xml
- namespace: `com.rrsjk.report.dao.light.LightStationEnableRewardDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByNotConfirm`, `select:getByOrderNo`, `select:findStationEnableRewardByStationCodeList`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightStationWhiteList.xml
- namespace: `com.rrsjk.report.dao.light.LightStationWhiteListDao`
- statements: `select:countOfGrid`, `select:queryCodeList`, `select:capacityRank`, `select:pvStationCountRank`, `select:countOfDashStation`, `select:findDashStation`
- tables: `light_station`, `light_station_white_list`, `light_station_white_list_simple`, `rrsjk_light_report.energy_leased_station_asset_management`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightPurchaseAppeals.xml
- namespace: `com.rrsjk.report.dao.light.LightPurchaseAppealsDao`
- statements: `select:countOf`, `select:findBy`, `insert:create`, `update:update`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/HrflcSyncPvInfo.xml
- namespace: `com.rrsjk.report.dao.light.HrflcSyncPvInfoDao`
- statements: `select:countOfGrid`, `select:queryCodeList`, `select:capacityRank`, `select:pvStationCountRank`, `select:countOfDashStation`, `select:findDashStation`
- tables: `hrflc_sync_pv_info`, `light_station`, `light_station_white_list`, `light_station_white_list_simple`, `rrsjk_light_report.energy_leased_station_asset_management`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightNewMerchantReward.xml
- namespace: `com.rrsjk.report.dao.light.LightNewMerchantRewardDao`
- statements: `select:countOf`, `select:findBy`, `insert:create`, `update:update`, `select:findByNotConfirm`, `select:getById`, `select:getByOrderNo`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightManualIncome.xml
- namespace: `com.rrsjk.report.dao.light.LightManualIncomeDao`
- statements: `select:findBuildIncome`, `select:findMaterialIncome`, `select:findIncomeCodeList`
- tables: `light_manual_income`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightSubSp.xml
- namespace: `com.rrsjk.report.dao.light.LightSubSpDao`
- statements: `select:get`, `select:findOneByMemberId`, `select:findListBySpMemberId`, `select:findListByParentMemberId`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightConstructionTeam.xml
- namespace: `com.rrsjk.report.dao.light.LightConstructionTeamDao`
- statements: `select:findCount`, `select:findCountBySpId`, `select:findCountBySpName`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightInstantRewardItem.xml
- namespace: `com.rrsjk.report.dao.light.LightInstantRewardItemDao`
- statements: `select:findBy`, `select:countOf`, `select:getById`, `select:countOfToTarget`
- tables: `light_instant_reward_item`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightSpOpGroupSumLog.xml
- namespace: `com.rrsjk.report.dao.light.LightSpOpGroupSumLogDao`
- statements: `select:findDayVillageXgj`
- tables: `light_sp_op_group_sum_log`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/ZhaoYinTradeIncomeSettle.xml
- namespace: `com.rrsjk.report.dao.light.ZhaoYinTradeIncomeSettleDao`
- statements: `select:findBy`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightStationNanny.xml
- namespace: `com.rrsjk.report.dao.light.LightStationNannyDao`
- statements: `insert:create`, `update:update`, `select:findCountBySpName`, `select:findCountBySpIdList`
- tables: `id`, `light_station_nanny`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightProjectElectricOrder.xml
- namespace: `com.rrsjk.report.dao.light.LightProjectElectricOrderDao`
- statements: `select:findCountByTime`, `select:findSumByTime`, `select:findHouseHoldSumByTime`, `select:findAmount`, `select:findList`, `select:findListToElecIncome`, `select:findListForOff`, `select:findListOfProvince`, `select:findListOfCompany`, `select:findElecPriceReportRegion`, `select:findElecPriceReportCompany`, `select:findElecPriceStation`, `select:findElecPriceReportProvince`, `select:findNoOrderList`, `select:findListForOffTest`
- tables: `light_project_electric_order`, `light_project_electric_order_owner`, `light_station`, `rrsjk_light.light_project_electric_order`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightServiceProvider.xml
- namespace: `com.rrsjk.report.dao.light.LightServiceProviderDao`
- statements: `select:getById`, `select:findCountyCenterSum`, `select:findAllCountyCenterSum`, `select:findAllSp`, `select:findByCityIdList`, `select:findBySubCenter`, `select:findBySubCenterList`, `select:getByMemberId`, `select:findByIds`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightTechAuditor.xml
- namespace: `com.rrsjk.report.dao.light.LightTechAuditorDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByEmployeeCodeAndAuditType`, `select:findByValidEmployeeCodeAndAuditType`, `select:findByAuditType`, `select:findByAuditTypeAndName`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightUnionpayBillRecord.xml
- namespace: `com.rrsjk.report.dao.light.LightUnionpayBillRecordDao`
- statements: `select:findBy`
- tables: `light_station`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightStationPlanConfig.xml
- namespace: `com.rrsjk.report.dao.light.LightStationPlanConfigDao`
- statements: `select:findStationPower`, `select:findStationPower`, `select:findStationPowerPro`, `select:findQuantity`, `select:findOneByStationId`, `select:findByParams`, `select:findQuotaByStationCodeList`, `select:findStationGroupPower`
- tables: `light_service_provider`, `light_station`, `rrsjk_light_report.energy_summary_target`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightStationYuexiu.xml
- namespace: `com.rrsjk.report.dao.light.LightStationYuexiuDao`
- statements: `select:getListLightStationYuexiu`, `select:yxPartsSpName`, `select:yxPartsSubCenterName`, `select:yxPartsSubCenterNameCity`, `select:yxPutInSpName`, `select:yxPutInSubCenterName`, `select:yxPutInSubCenterNameCity`, `select:yxClassIiCard`, `select:yxClassIiCardCity`, `select:getByStationCodes`
- tables: `light_station_yuexiu`, `light_station_yuexiu_account`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightEnablePolicy.xml
- namespace: `com.rrsjk.report.dao.light.LightEnablePolicyDao`
- statements: `select:findEnabledByRegion`, `select:findItemByPolicyId`, `select:findAllNPolicyWithItems`
- tables: `light_enable_policy`, `light_enable_policy_area`, `light_enable_policy_item`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightCompanyPower.xml
- namespace: `com.rrsjk.report.dao.light.LightCompanyPowerDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightInstantGridRewardPolicy.xml
- namespace: `com.rrsjk.report.dao.light.LightInstantGridRewardPolicyDao`
- statements: `select:findEnabledByProvince`
- tables: `light_instant_grid_reward_policy`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightStationNew.xml
- namespace: `com.rrsjk.report.dao.light.LightStationNewDao`
- statements: `select:getTeamReportCount`, `select:getTeamBusinessOperationReport`, `select:getTeamAreaReportCount`, `select:getTeamAreaBusinessOperationReport`, `select:getTeamOpDetailCount`, `select:getTeamOpOrderData`, `select:getTeamOpSignData`, `select:getTeamOpCompleteData`, `select:getTeamOpGridData`
- tables: `light_sp_staff`, `light_station`, `light_sub_sp`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightEnablePolicyItem.xml
- namespace: `com.rrsjk.report.dao.light.LightEnablePolicyItemDao`
- statements: `select:findItemBy`, `select:findByPolicyAndRegion`
- tables: `light_enable_policy`, `light_enable_policy_area`, `light_enable_policy_item`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightStationSettleSumQueue.xml
- namespace: `com.rrsjk.report.dao.light.LightStationSettleSumQueueDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightSpGridAwardOrder.xml
- namespace: `com.rrsjk.report.dao.light.LightSpGridAwardOrderDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByBillNo`, `select:getFirstMonthOne`, `select:selectNotAcc`, `select:findAllBnAgeingOrder`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightStock.xml
- namespace: `com.rrsjk.report.dao.light.LightStockDao`
- statements: `select:findBy`
- tables: `light_sku_data`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightTechAuditorOperationLog.xml
- namespace: `com.rrsjk.report.dao.light.LightTechAuditorOperationLogDao`
- statements: `select:findByEmployeeCodeAndDate`, `select:findLastBeforeDate`, `select:findByAuditorIdAndDate`, `select:findLastByAuditorIdBeforeDate`
- tables: `light_tech_auditor_operation_log`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightSpStore.xml
- namespace: `com.rrsjk.report.dao.light.LightSpStoreDao`
- statements: `select:findByParams`, `select:findBySubSpId`, `select:findByStoreCodes`, `select:findByIds`, `select:findAllStore`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightCompanyInfo.xml
- namespace: `com.rrsjk.report.dao.light.LightCompanyInfoDao`
- statements: `select:findCompanyCode`, `select:findOffCompanyCode`, `select:findByCode`, `select:findAll`, `select:findForCapital`
- tables: `light_capital_company_info`, `light_company_info`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightStationRentReport.xml
- namespace: `com.rrsjk.report.dao.light.LightStationRentReportDao`
- statements: `select:findStationCodeBySubCenter`, `select:getBeforeAmountBySubCenter`
- tables: `light_station`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightShareBillRecord.xml
- namespace: `com.rrsjk.report.dao.light.LightShareBillRecordDao`
- statements: `select:findPaymentAmount`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/CmLightProjectIncome.xml
- namespace: `com.rrsjk.report.dao.light.CmLightProjectIncomeDao`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightUseOrder.xml
- namespace: `com.rrsjk.report.dao.light.LightUseOrderDao`
- statements: `select:findBy`, `select:findAgeAnalysisGroup`
- tables: `light_sp_store`, `light_use_order`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightEnablePolicyArea.xml
- namespace: `com.rrsjk.report.dao.light.LightEnablePolicyAreaDao`
- statements: `select:findAreaByPolicyId`
- tables: `light_enable_policy_area`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightInstantGridReward.xml
- namespace: `com.rrsjk.report.dao.light.LightInstantGridRewardDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findCompleteByNotConfirm`, `select:findByNotConfirm`, `update:removeCostVoucher`
- tables: `id`, `light_instant_grid_reward`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightStationYuexiuSettle.xml
- namespace: `com.rrsjk.report.dao.light.LightStationYuexiuSettleDao`
- statements: `select:findIncomeByTime`, `select:findSumSalesRevenue`, `select:findSumAmountCollected`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/CmConstructionPlan.xml
- namespace: `com.rrsjk.report.dao.light.CmConstructionPlanDao`
- statements: `select:queryGridStats`, `select:queryCmCityStats`, `select:findCityStatsByProjectCodes`
- tables: `cm_construction_plan`, `cm_construction_plan_item`, `light_station`, `light_station_epc`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightInstantGridRewardItem.xml
- namespace: `com.rrsjk.report.dao.light.LightInstantGridRewardItemDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightDeposit.xml
- namespace: `com.rrsjk.report.dao.light.LightDepositDao`
- statements: `select:findCountBySpName`
- tables: `light_deposit`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/YuexiuElectricityBill.xml
- namespace: `com.rrsjk.report.dao.light.YuexiuElectricityBillDao`
- statements: `select:findBy`, `select:findBillCompanyBy`
- tables: `light_station`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/light/LightStationSettleSum.xml
- namespace: `com.rrsjk.report.dao.light.LightStationSettleSumDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`, `light_station`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/elec/ReportLightStation.xml
- namespace: `com.rrsjk.report.dao.elec.ReportLightStationDao`
- statements: `select:findAreaSum`, `select:countOfDashStation`, `select:countOfDashStationHuarong`, `select:findDashStationHuarong`, `select:findDashStation`, `select:findBocDashStation`, `select:findCnncDashStation`, `select:findYueXiuDashStation`, `select:countOfBocDashStation`, `select:countOfCnncDashStation`, `select:countOfYueXiuDashStation`, `select:getAllOfCapacity`, `select:getBocAllOfCapacity`, `select:getCnncAllOfCapacity`, `select:getYueXiuAllOfCapacity`, `select:getAllOfPuyinCapacity`, `select:getAllOfHuarongCapacity`, `select:findCityStatsByProjectCodes`
- tables: `boc_leasing_light_station`, `cmb_leasing_station`, `cnnc_leasing_light_station`, `energy_leased_station_asset_management`, `hrflc_sync_pv_info`, `light_station`, `light_station_white_list_simple`, `yuexiu_leasing_light_station`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/elec/LightStationElecDayReport.xml
- namespace: `com.rrsjk.report.dao.elec.LightStationElecDayReportDao`
- statements: `select:findElectByStationCodeAndFetchAt`, `select:countOfElect`, `select:sumOfElectByStationCodes`, `select:findActualElectStationList`, `select:findElecByStationCodeAndFetchAt`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/elec/ReportInveterChartDay.xml
- namespace: `com.rrsjk.report.dao.elec.ReportInveterChartDayDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findByParams`, `select:findChart`, `select:getHourZero`, `select:getHourZeroSix`, `select:findDayElec`, `select:countHourElec`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/elec/LightStationElectricDayReportNew.xml
- namespace: `com.rrsjk.report.dao.elec.LightStationElectricDayReportNewDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByGroupByStationCode`, `update:updateByStationCode`, `select:getElectricSum`, `select:getElectricAndIncome`, `select:getElectricAndIncome`, `select:queryDayElectric`, `select:queryBocDayElectric`, `select:queryCnncDayElectric`, `select:queryYueXiuDayElectric`, `select:getElectricAndIncomeByCode`, `select:getBocElectricAndIncomeByCode`, `select:getCnncElectricAndIncomeByCode`, `select:getYueXiuElectricAndIncomeByCode`, `select:queryDayElectricByCode`, `select:queryBocDayElectricByCode`, `select:queryCnncDayElectricByCode`, `select:queryYueXiuDayElectricByCode`, `select:findDaysElectric`, `select:findStationColumnByCmb`, `select:findStationColumnByBoc`, `select:findStationColumnByCnnc`, `select:findStationColumnByYueXiu`, `select:queryTotalElectricByCompanyCode`, `select:getElectricAndIncomeForPuyin`, `select:getElectricAndIncomeForPuyinByCode`, `select:getElectricAndIncomeByCodeInAssert`, `select:queryDayElectricByCodeInAssert`, `select:queryChartMonthElecByMonth`
- tables: `boc_leasing_light_station`, `cmb_leasing_station`, `cnnc_leasing_light_station`, `energy_leased_station_asset_management`, `id`, `light_city_elec_price`, `light_station`, `light_station_elec_day_report_new`, `light_station_white_list`, `light_station_white_list_simple`, `report_station_chart_month`, `yuexiu_leasing_light_station`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/elec/ReportStationChartYear.xml
- namespace: `com.rrsjk.report.dao.elec.ReportStationChartYearDao`
- statements: `select:sumMonthOfYearElec`, `select:sumYearElec`
- tables: `report_station_chart_year`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/elec/LightInveterData.xml
- namespace: `com.rrsjk.report.dao.elec.LightInveterDataDao`
- statements: `select:findByParams`, `select:findStationCodeByParams`, `select:getTotalByParams`, `select:queryElectricSum`, `select:findDayPower`, `select:findMonthPower`, `select:findYearPower`, `select:findBindStation`, `select:getElecMonth`, `select:findGridStation`, `select:findOneByStationCode`, `select:findDayPowerByStationCode`, `select:findStation`, `select:findFirstLinkAt`, `select:findPower`, `select:findByStation`, `select:findList`, `select:findListByBindYear`, `select:findTotalGridStation`, `select:getRealtimePower`, `select:getBocRealtimePower`, `select:getCnncRealtimePower`, `select:getYueXiuRealtimePower`, `select:getHuarongRealtimePower`, `select:findSnByStationCode`, `select:listInveterError`, `select:listInveterErrorNow`, `select:findDashBoardCountData`, `select:findBocDashBoardCountData`, `select:findCnncDashBoardCountData`, `select:findYueXiuDashBoardCountData`, `select:findHuarongDashBoardCountData`, `select:findHuarongDashBoardCountData`, `select:getTotalFacByParams`, `select:getPuyinRealtimePower`, `select:findPuyinDashBoardCountData`, `select:getRealtimePowerInAssert`
- tables: `boc_leasing_light_station`, `cmb_leasing_station`, `cnnc_leasing_light_station`, `enabled_inverters`, `energy_leased_station_asset_management`, `hrflc_sync_pv_info`, `light_inveter_data`, `light_station`, `light_station_elec_day_report_new`, `light_station_inverter`, `light_station_white_list_simple`, `station_capacity`, `yuexiu_leasing_light_station`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/elec/ReportStationChartMonth.xml
- namespace: `com.rrsjk.report.dao.elec.ReportStationChartMonthDao`
- statements: `select:sumDayOfMonthElec`, `select:queryDayElectricForPuyin`, `select:queryDayElectricForPuyinByCode`, `select:queryDayElectricForHuarongByCode`, `select:queryDayElectricForHuarong`, `select:queryDayElecListByYearAndMonth`
- tables: `hrflc_sync_pv_info`, `light_station_white_list_simple`, `report_station_chart_month`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/elec/LightInveter.xml
- namespace: `com.rrsjk.report.dao.elec.LightInveterDao`
- statements: `select:findByFetchAt`, `select:findByFetchAtAndSnList`, `select:findYearByFetchAtAndSnList`, `select:findByTimeAndSnList`, `select:findELECDayNum`, `select:findMonthByFetchAtAndSnList`, `select:findTotalByFetchAtAndSnList`, `select:findNormalInverterByFetchAtAndSnList`, `select:findElectFetchAtAndSnList`, `select:findPowerErrorInverterByFetchAtAndSnList`, `select:findElecWarning`, `select:findByType`, `select:findElecIncome`
- tables: `light_station`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/elec/ReportInveterChartYear.xml
- namespace: `com.rrsjk.report.dao.elec.ReportInveterChartYearDao`
- statements: `select:getById`, `select:findByParams`, `select:getElecByParams`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/elec/ReportStationChartTotal.xml
- namespace: `com.rrsjk.report.dao.elec.ReportStationChartTotalDao`
- statements: `select:sumTotalElec`
- tables: `report_station_chart_total`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/elec/LightStationElec.xml
- namespace: `com.rrsjk.report.dao.elec.LightStationElecDao`
- statements: `select:getById`, `select:queryListBy`, `select:queryDistinctListBy`, `select:queryCountBy`, `select:findByParams`, `select:findElecSum`, `select:findElecSumProvince`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/ads/AdsReportStationChartTotal.xml
- namespace: `com.rrsjk.report.dao.ads.AdsReportStationChartTotalDao`
- statements: `select:findChart`, `select:sumTotalElec`
- tables: `ads.green_energy_report_light_station_chart_total`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/ads/ZeroCarbonDayReport.xml
- namespace: `com.rrsjk.report.dao.ads.ZeroCarbonDayReportDao`
- statements: `select:findBy`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/ads/AdsReportInveterChartTotal.xml
- namespace: `com.rrsjk.report.dao.ads.AdsReportInveterChartTotalDao`
- statements: `select:findChart`
- tables: `ads.green_energy_report_light_inverter_chart_total`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/ads/AdsReportInveterChartYear.xml
- namespace: `com.rrsjk.report.dao.ads.AdsReportInveterChartYearDao`
- statements: `select:findChart`
- tables: `ads.green_energy_report_light_inverter_chart_year`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/ads/EnergyChainGroupIncomeComment.xml
- namespace: `com.rrsjk.report.dao.ads.EnergyChainGroupIncomeCommentDao`
- statements: `select:findBy`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/ads/AdsReportStationChartYear.xml
- namespace: `com.rrsjk.report.dao.ads.AdsReportStationChartYearDao`
- statements: `select:findChart`, `select:sumMonthOfYearElec`, `select:sumYearElec`
- tables: `ads.green_energy_report_light_station_chart_year`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/ads/AdsReportInveterChartDay.xml
- namespace: `com.rrsjk.report.dao.ads.AdsReportInveterChartDayDao`
- statements: `select:findChart`, `select:countHourElec`
- tables: `ads.green_energy_report_light_inverter_chart_day`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/ads/RealTimeStationElecChartMonth.xml
- namespace: `com.rrsjk.report.dao.ads.RealTimeStationElecChartMonthDao`
- statements: `select:queryDayElectricForPuyin`
- tables: `green_energy_report_light_station_chart_month`, `ods.green_energy_light_station_white_list_simple`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/ads/ZeroCarbonDayReportDifference.xml
- namespace: `com.rrsjk.report.dao.ads.ZeroCarbonDayReportDifferenceDao`
- statements: `select:countOf`, `select:findBy`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/ads/EnergyChainGroupIncome.xml
- namespace: `com.rrsjk.report.dao.ads.EnergyChainGroupIncomeDao`
- statements: `update:update`, `select:findBy`, `select:findOne`
- tables: `energy_chain_group_income`, `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/ads/AdsReportStationChartMonth.xml
- namespace: `com.rrsjk.report.dao.ads.AdsReportStationChartMonthDao`
- statements: `select:findChart`, `select:queryDayElectricForPuyinByCode`, `select:sumDayOfMonthElec`
- tables: `ads.green_energy_report_light_station_chart_month`, `ods.green_energy_light_station_white_list_simple`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/ads/AdsReportInveterPacChartDay.xml
- namespace: `com.rrsjk.report.dao.ads.AdsReportInveterPacChartDayDao`
- statements: `select:findChart`
- tables: `ads.green_energy_report_light_inverter_pac_chart_day`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/ads/AdsReportInveterChartMonth.xml
- namespace: `com.rrsjk.report.dao.ads.AdsReportInveterChartMonthDao`
- statements: `select:findChart`, `select:findChartPro`
- tables: `ads.green_energy_report_light_inverter_chart_month`, `dws.green_energy_inverter_current`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/ads/AdsReportStationChartDay.xml
- namespace: `com.rrsjk.report.dao.ads.AdsReportStationChartDayDao`
- statements: `select:findChart`, `select:getMinFetchAt`
- tables: `ads.green_energy_report_light_station_chart_day`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/ads/ElecWarningStation.xml
- namespace: `com.rrsjk.report.dao.ads.ElecWarningStationDao`
- statements: `select:findNoElecStationList`, `select:findNoElecStationCount`, `select:findNoElecStationCount`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyIncomeTarget.xml
- namespace: `com.rrsjk.report.dao.local.EnergyIncomeTargetDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:findTarget`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyLightEstimateStation.xml
- namespace: `com.rrsjk.report.dao.local.EnergyLightEstimateStationDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:findByStationCodeAndDayAt`, `select:findByStationList`, `select:findByCompanyCode`, `select:findByType`, `select:findList`, `select:findCommonSum`, `select:findPublicSum`, `select:findForOff`, `select:findByStationForOff`
- tables: `energy_light_estimate_station`, `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyOverdueInventoryControlDataBase.xml
- namespace: `com.rrsjk.report.dao.local.EnergyOverdueInventoryControlDataBaseDao`
- statements: `insert:create`, `insert:batchInsert`, `select:get`, `select:countOf`, `select:findBy`
- tables: `energy_overdue_inventory_control_data_base`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyTradeIncomeInfo.xml
- namespace: `com.rrsjk.report.dao.local.EnergyTradeIncomeInfoDao`
- statements: `select:findCountBySubName`, `select:findQuotaBySubName`, `select:findCountByCityIdList`, `select:findQuotaByCityIdList`, `select:findCountBySubNameList`, `select:findQuotaBySubNameList`, `select:findQuotaByStationCodes`
- tables: `energy_trade_income_info`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyOverseasIncomeDetail.xml
- namespace: `com.rrsjk.report.dao.local.EnergyOverseasIncomeDetailDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:deleteByDate`, `update:deleteByYearMonth`, `select:orderGroupByProductCategory`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportStationSumElectHourDay.xml
- namespace: `com.rrsjk.report.dao.local.ReportStationSumElectHourDayDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByStationCodeAndDayAt`, `select:sumOfElectHourByStationCodesAndDayAt`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyOverdueInventoryControlSku.xml
- namespace: `com.rrsjk.report.dao.local.EnergyOverdueInventoryControlSkuDao`
- statements: `insert:create`, `select:get`, `select:countOf`, `select:findBy`, `insert:batchInsert`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyOverseasIncomeMonth.xml
- namespace: `com.rrsjk.report.dao.local.EnergyOverseasIncomeMonthDao`
- statements: `insert:create`, `update:update`, `select:findByDate`, `select:findByStartTime`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyElecPriceReportCompany.xml
- namespace: `com.rrsjk.report.dao.local.EnergyElecPriceReportCompanyDao`
- statements: `insert:create`, `update:update`, `select:findList`, `select:findCount`, `select:findOne`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportScreenGrid.xml
- namespace: `com.rrsjk.report.dao.local.ReportScreenGridDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyReport.xml
- namespace: `com.rrsjk.report.dao.local.EnergyReportDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:findByType`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ObsOrderItem.xml
- namespace: `com.rrsjk.report.dao.local.ObsOrderItemDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:orderGroupByProductCategory`
- tables: `id`, `obs_order`, `obs_order_item`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/CenterMapping.xml
- namespace: `com.rrsjk.report.dao.local.CenterMappingDao`
- statements: `select:findSubCenterNamesByPartyCodes`, `select:findAll`, `select:findCenterOptions`
- tables: `center_mapping`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyStatisticIncomeReport.xml
- namespace: `com.rrsjk.report.dao.local.EnergyStatisticIncomeReportDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByCloseDate`, `select:getLastDay`
- tables: `energy_statistic_income_report`, `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/GreenEnergySignAndGridScale.xml
- namespace: `com.rrsjk.report.dao.local.GreenEnergySignAndGridScaleDao`
- statements: `insert:create`, `update:update`, `select:findByDayAt`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/YueXiuLeasingStation.xml
- namespace: `com.rrsjk.report.dao.local.YueXiuLeasingStationDao`
- statements: `select:findBy`, `select:findStationColumnBy`, `select:findJoinStationColumnBy`, `select:findBySort`, `select:countOf`, `insert:create`, `select:getById`, `select:getByStationCode`, `select:getPrice`, `select:capacityRank`, `select:pvStationCountRank`, `select:findElecSum`, `select:queryDayElectric`
- tables: `cmb_electric_price`, `cmb_leasing_station`, `report_station_chart_month`, `rrsjk_light.light_station`, `rrsjk_light.yuexiu_leasing_light_station`, `yuexiu_leasing_light_station`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyZhengzhouSpLeader.xml
- namespace: `com.rrsjk.report.dao.local.EnergyZhengzhouSpLeaderDao`
- statements: `select:findSpId`, `select:findList`, `select:findCityIdByLeaderName`, `select:findCityIdBySubCenter`
- tables: `energy_zhengzhou_sp_leader`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyElecPriceReportProvince.xml
- namespace: `com.rrsjk.report.dao.local.EnergyElecPriceReportProvinceDao`
- statements: `insert:create`, `update:update`, `select:findList`, `select:findCount`, `select:findOne`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/SpSubOperationEvaluateDashboardMapper.xml
- namespace: `com.rrsjk.report.dao.local.SpSubOperationEvaluateDashboardDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findByPage`, `update:updateBatch`, `insert:batchInsert`, `select:joinQueryBuildTable`
- tables: `id`, `sp_sub_build_evaluate_dashboard`, `sp_sub_operation_evaluate_dashboard`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportPolicyForecastMapper.xml
- namespace: `com.rrsjk.report.dao.local.ReportPolicyForecastDao`
- statements: `select:findByPage`, `select:countByPage`, `delete:deleteByForecastMonth`, `insert:batchInsert`
- tables: `rrsjk_light_report.report_policy_forecast`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportZhModeStation.xml
- namespace: `com.rrsjk.report.dao.local.ReportZhModeStationDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportScreenMapPuyin.xml
- namespace: `com.rrsjk.report.dao.local.ReportScreenMapPuyinDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ObsOrder.xml
- namespace: `com.rrsjk.report.dao.local.ObsOrderDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findNoDsoIncome`, `select:findDsoIncome`
- tables: `id`, `obs_order`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportCnncScreenMonthElectric.xml
- namespace: `com.rrsjk.report.dao.local.ReportCnncScreenMonthElectricDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyLightEstimateTest.xml
- namespace: `com.rrsjk.report.dao.local.EnergyLightEstimateTestDao`
- statements: `insert:create`, `update:update`
- tables: `energy_light_estimate_test`, `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/LightTechAuditTimeLinessReport.xml
- namespace: `com.rrsjk.report.dao.local.LightTechAuditTimeLinessReportDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:selectAll`, `select:findBy`, `select:count`, `select:getByAuditTypeAcceptDate`, `select:findPage`, `select:countTotal`
- tables: `id`, `light_tech_audit_time_liness_report`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyCenterProfitConfig.xml
- namespace: `com.rrsjk.report.dao.local.EnergyCenterProfitConfigDao`
- statements: `insert:create`, `update:update`, `select:findBy`, `select:findOneBySubCenter`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergySpDay.xml
- namespace: `com.rrsjk.report.dao.local.EnergySpDayDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:findList`, `select:findCount`, `select:findCenterList`, `select:findProvinceList`, `select:findCityList`, `select:findDistrictList`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyEteIncomeDay.xml
- namespace: `com.rrsjk.report.dao.local.EnergyEteIncomeDayDao`
- statements: `insert:create`, `update:update`, `select:queryOne`, `select:findBy`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportScreenMapHuarong.xml
- namespace: `com.rrsjk.report.dao.local.ReportScreenMapHuarongDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyInvestorData.xml
- namespace: `com.rrsjk.report.dao.local.EnergyInvestorDataDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByInvestor`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportScreenMap.xml
- namespace: `com.rrsjk.report.dao.local.ReportScreenMapDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/VmOrder.xml
- namespace: `com.rrsjk.report.dao.local.VmOrderDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportScreenDashboardCnnc.xml
- namespace: `com.rrsjk.report.dao.local.ReportScreenDashboardCnncDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByFetchAt`, `select:getLatestByFetchAt`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyBuildTarget.xml
- namespace: `com.rrsjk.report.dao.local.EnergyBuildTargetDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:findTarget`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyExchangeRate.xml
- namespace: `com.rrsjk.report.dao.local.EnergyExchangeRateDao`
- statements: `select:find`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyCenterNetworkBuild.xml
- namespace: `com.rrsjk.report.dao.local.EnergyCenterNetworkBuildDao`
- statements: `insert:create`, `update:update`, `select:findList`, `select:findOne`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/SpSubBaseDataDashboardMapper.xml
- namespace: `com.rrsjk.report.dao.local.SpSubBaseDataDashboardDao`
- statements: `insert:create`, `select:get`, `update:update`, `select:countOf`, `select:findByPage`, `insert:everyDayIntoData`
- tables: `id`, `rrsjk_light.light_sp_authority_zone`, `rrsjk_light.light_station`, `rrsjk_light.light_sub_sp_region`, `rrsjk_light`.light_station`, `rrsjk_light`.light_sub_sp`, `sp_sub_base_data_dashboard`, `sub_center_code`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyStationElecReport.xml
- namespace: `com.rrsjk.report.dao.local.EnergyStationElecReportDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportAssetScreenProvinceGrid.xml
- namespace: `com.rrsjk.report.dao.local.ReportAssetScreenProvinceGridDao`
- statements: `select:findBy`, `select:findByMonth`, `select:findAllMonth`, `select:findAllMonthByProvince`, `select:findCurYearByProvince`, `select:findGroupByYear`, `select:findTailMonth`, `select:findCurYearTailMonth`, `select:findByProvince`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportHuarongScreenDashboard.xml
- namespace: `com.rrsjk.report.dao.local.ReportHuarongScreenDashboardDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByFetchAt`, `select:getLatestByFetchAt`, `select:getTotalData`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportPuyinScreenDashboard.xml
- namespace: `com.rrsjk.report.dao.local.ReportPuyinScreenDashboardDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByFetchAt`, `select:getLatestByFetchAt`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyLightSubchain.xml
- namespace: `com.rrsjk.report.dao.local.EnergyLightSubchainDao`
- statements: `insert:create`, `update:update`, `select:findList`, `select:findOne`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyOfflineIncome.xml
- namespace: `com.rrsjk.report.dao.local.EnergyOfflineIncomeDao`
- statements: `insert:create`, `update:update`, `select:findCount`, `select:findPage`, `select:get`, `select:findSum`, `select:findWhole`, `select:findList`, `select:findQualifyingProjectCodes`, `select:queryGridStats`
- tables: `id`, `rrsjk_light.cm_simple_project`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportScreenCmbStationRank.xml
- namespace: `com.rrsjk.report.dao.local.ReportScreenCmbStationRankDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/GvsWarehouseAgeAnalysis.xml
- namespace: `com.rrsjk.report.dao.local.GvsWarehouseAgeAnalysisDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:getGvsSummary`, `select:getSumGvsGroupBySku`, `select:countGroupByAgeStatus`, `select:findGroupByAgeStatus`, `select:findToSpData`, `select:findSkuInfo`
- tables: `gvs_warehouse_age_analysis`, `id`, `light_sku_data`, `sap_sp_center_relation`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyElecIncomeReport.xml
- namespace: `com.rrsjk.report.dao.local.EnergyElecIncomeReportDao`
- statements: `insert:created`, `insert:batchInsert`, `update:updated`, `select:findList`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportScreenOrder.xml
- namespace: `com.rrsjk.report.dao.local.ReportScreenOrderDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportCmbScreenMonthElectric.xml
- namespace: `com.rrsjk.report.dao.local.ReportCmbScreenMonthElectricDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/CmbLeasingStation.xml
- namespace: `com.rrsjk.report.dao.local.CmbLeasingStationDao`
- statements: `select:findBy`, `select:findStationColumnBy`, `select:findJoinStationColumnBy`, `select:findBySort`, `select:countOf`, `insert:create`, `select:getById`, `select:getByStationCode`, `select:getPrice`, `select:capacityRank`, `select:pvStationCountRank`, `select:findElecSum`, `select:queryDayElectric`
- tables: `cmb_electric_price`, `cmb_leasing_station`, `energy_leased_station_asset_management`, `report_station_chart_month`, `rrsjk_light.cmb_leasing_station`, `rrsjk_light.light_station`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportCityPowerSummaryMapper.xml
- namespace: `com.rrsjk.report.dao.local.ReportCityPowerSummaryDao`
- statements: `select:findByPage`, `select:countByPage`, `delete:deleteByDataDate`, `insert:batchInsert`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportMInstall.xml
- namespace: `com.rrsjk.report.dao.local.ReportMInstallDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportScreenGoal.xml
- namespace: `com.rrsjk.report.dao.local.ReportScreenGoalDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/GreenEnergyChainGroup.xml
- namespace: `com.rrsjk.report.dao.local.GreenEnergyChainGroupDao`
- statements: `select:findChainGroup`
- tables: `green_energy_chain_group`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyInventoryTurnoverControlSubCenter.xml
- namespace: `com.rrsjk.report.dao.local.EnergyInventoryTurnoverControlSubCenterDao`
- statements: `insert:create`, `select:get`, `select:countOf`, `select:findBy`, `select:list`, `insert:batchInsert`, `select:getSumSomeDays`
- tables: `energy_inventory_turnover_control_sub_center`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyYuexiuSubCenterData.xml
- namespace: `com.rrsjk.report.dao.local.EnergyYuexiuSubCenterDataDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyBuildDay.xml
- namespace: `com.rrsjk.report.dao.local.EnergyBuildDayDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:findByDayAtAndType`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportCityGeocode.xml
- namespace: `com.rrsjk.report.dao.local.ReportCityGeocodeDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportStationProcessWarning.xml
- namespace: `com.rrsjk.report.dao.local.ReportStationProcessWarningDao`
- statements: `select:findBy`, `select:findByParams`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `delete:batchDelete`, `select:getById`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyStationTarget.xml
- namespace: `com.rrsjk.report.dao.local.EnergyStationTargetDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:findTarget`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyGridIncomeTarget.xml
- namespace: `com.rrsjk.report.dao.local.EnergyGridIncomeTargetDao`
- statements: `select:findOne`
- tables: `energy_grid_income_target`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyInventoryTurnoverControlSku.xml
- namespace: `com.rrsjk.report.dao.local.EnergyInventoryTurnoverControlSkuDao`
- statements: `insert:create`, `select:get`, `select:countOf`, `select:findBy`, `insert:batchInsert`, `select:getSumSomeDays`
- tables: `energy_inventory_turnover_control_sku`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportAssetScreenCmGrid.xml
- namespace: `com.rrsjk.report.dao.local.ReportAssetScreenCmGridDao`
- statements: `select:findBy`, `select:findByParams`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/SpSubBuildEvaluateDashboardMapper.xml
- namespace: `com.rrsjk.report.dao.local.SpSubBuildEvaluateDashboardDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findByPage`, `insert:batchInsert`
- tables: `data_at`, `id`, `sp_sub_build_evaluate_dashboard`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/LightOrderInstallGrid.xml
- namespace: `com.rrsjk.report.dao.local.LightOrderInstallGridDao`
- statements: `insert:create`, `update:update`, `select:findByParams`, `select:getByDataTime`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/GreenEnergySignAndGridScaleTarget.xml
- namespace: `com.rrsjk.report.dao.local.GreenEnergySignAndGridScaleTargetDao`
- statements: `select:findTarget`
- tables: `green_energy_sign_and_grid_scale_target`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyOfflineIncomeLog.xml
- namespace: `com.rrsjk.report.dao.local.EnergyOfflineIncomeLogDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/CnncLeasingStation.xml
- namespace: `com.rrsjk.report.dao.local.CnncLeasingStationDao`
- statements: `select:findBy`, `select:findStationColumnBy`, `select:findJoinStationColumnBy`, `select:findBySort`, `select:countOf`, `insert:create`, `select:getById`, `select:getByStationCode`, `select:getPrice`, `select:capacityRank`, `select:pvStationCountRank`, `select:findElecSum`, `select:queryDayElectric`
- tables: `cmb_electric_price`, `cmb_leasing_station`, `cnnc_leasing_light_station`, `report_station_chart_month`, `rrsjk_light.cnnc_leasing_light_station`, `rrsjk_light.light_station`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyCenterProfitCost.xml
- namespace: `com.rrsjk.report.dao.local.EnergyCenterProfitCostDao`
- statements: `insert:create`, `update:update`, `select:queryListBy`, `select:queryCountBy`, `insert:batchInsert`, `select:findOne`, `select:findYear`
- tables: `energy_center_profit_cost`, `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergySpData.xml
- namespace: `com.rrsjk.report.dao.local.EnergySpDataDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:findList`, `select:findCount`, `delete:delete`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportScreenMapCm.xml
- namespace: `com.rrsjk.report.dao.local.ReportScreenMapCmDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyEteCenterDay.xml
- namespace: `com.rrsjk.report.dao.local.EnergyEteCenterDayDao`
- statements: `insert:create`, `update:update`, `select:queryOne`, `select:findBy`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyCapitalData.xml
- namespace: `com.rrsjk.report.dao.local.EnergyCapitalDataDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:findList`, `select:findCount`
- tables: `energy_capital_data`, `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportScreenStationRank.xml
- namespace: `com.rrsjk.report.dao.local.ReportScreenStationRankDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergySubchainGroupTarget.xml
- namespace: `com.rrsjk.report.dao.local.EnergySubchainGroupTargetDao`
- statements: `insert:insert`, `update:update`, `select:findByChainGroup`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergySubchainGroupTargetReach.xml
- namespace: `com.rrsjk.report.dao.local.EnergySubchainGroupTargetReachDao`
- statements: `insert:create`, `update:update`, `select:findByDayAtAndSubchainGroup`, `select:findListByDayAt`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/GreenEnergyMarketScaleTarget.xml
- namespace: `com.rrsjk.report.dao.local.GreenEnergyMarketScaleTargetDao`
- statements: `select:findTarget`
- tables: `green_energy_market_scale_target`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportStationDevelopWarningDetail.xml
- namespace: `com.rrsjk.report.dao.local.ReportStationDevelopWarningDetailDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyCenterIncomeDay.xml
- namespace: `com.rrsjk.report.dao.local.EnergyCenterIncomeDayDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:getBySubCenterDayAt`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportScreenInstallShaft.xml
- namespace: `com.rrsjk.report.dao.local.ReportScreenInstallShaftDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyElecOrder.xml
- namespace: `com.rrsjk.report.dao.local.EnergyElecOrderDao`
- statements: `insert:create`, `update:update`, `insert:batchInsert`, `select:findPage`, `select:findPageDto`, `select:findCount`
- tables: `energy_elec_order`, `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportScreenMapCmb.xml
- namespace: `com.rrsjk.report.dao.local.ReportScreenMapCmbDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/BocLeasingStation.xml
- namespace: `com.rrsjk.report.dao.local.BocLeasingStationDao`
- statements: `select:findBy`, `select:findStationColumnBy`, `select:findJoinStationColumnBy`, `select:findBySort`, `select:countOf`, `insert:create`, `select:getById`, `select:getByStationCode`, `select:getPrice`, `select:capacityRank`, `select:pvStationCountRank`, `select:findElecSum`, `select:queryDayElectric`
- tables: `boc_leasing_light_station`, `cmb_electric_price`, `cmb_leasing_station`, `energy_leased_station_asset_management`, `report_station_chart_month`, `rrsjk_light.boc_leasing_light_station`, `rrsjk_light.light_station`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportAssetScreenInvestorData.xml
- namespace: `com.rrsjk.report.dao.local.ReportAssetScreenInvestorDataDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyYuexiuSpData.xml
- namespace: `com.rrsjk.report.dao.local.EnergyYuexiuSpDataDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyHouseholdStationIncome.xml
- namespace: `com.rrsjk.report.dao.local.EnergyHouseholdStationIncomeDao`
- statements: `insert:create`, `update:update`, `select:findByStationCode`, `select:findList`, `select:queryCountBy`
- tables: `energy_household_station_income`, `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ZeroCarbonDayReportTarget.xml
- namespace: `com.rrsjk.report.dao.local.ZeroCarbonDayReportTargetDao`
- statements: `insert:create`, `update:update`, `select:findOne`, `select:findCount`, `select:findBy`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyLightEstimateOffStation.xml
- namespace: `com.rrsjk.report.dao.local.EnergyLightEstimateOffStationDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:findListForOff`, `select:findListByStationCode`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/LightElectTargetYearReport.xml
- namespace: `com.rrsjk.report.dao.local.LightElectTargetYearReportDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `select:getByStationCodeAndDayAt`, `select:sumOfElectHourYear`, `select:countOfGenElect`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportHuarongScreenMonthElectric.xml
- namespace: `com.rrsjk.report.dao.local.ReportHuarongScreenMonthElectricDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportStationDevelopWarning.xml
- namespace: `com.rrsjk.report.dao.local.ReportStationDevelopWarningDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByParams`, `select:findByRangeDateAt`, `select:findBySubAndDate`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/LightElectTargetMonthReport.xml
- namespace: `com.rrsjk.report.dao.local.LightElectTargetMonthReportDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `select:sumOfElectHourTargetLastMonth`, `select:sumOfElectHourActualLastMonth`, `select:sumOfElectHourTargetLastYear`, `select:sumOfElectHourActualLastYear`, `select:findLastYearElectTargetList`, `select:countOfLastYear`, `select:getByStationCodeAndDayAt`, `select:sumOfElectHourMonth`, `select:sumOfElectHourMonthByStationCodes`
- tables: `id`, `light_elect_target_month_report`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyStatisticIncomeTarget.xml
- namespace: `com.rrsjk.report.dao.local.EnergyStatisticIncomeTargetDao`
- statements: `select:getYearTarget`, `select:getMonthTarget`
- tables: `energy_statistic_income_target`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportScreenInstall.xml
- namespace: `com.rrsjk.report.dao.local.ReportScreenInstallDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyOverdueInventoryControlCenter.xml
- namespace: `com.rrsjk.report.dao.local.EnergyOverdueInventoryControlCenterDao`
- statements: `insert:create`, `select:get`, `select:countOf`, `select:findBy`, `insert:batchInsert`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyLightEstimateStationTest.xml
- namespace: `com.rrsjk.report.dao.local.EnergyLightEstimateStationTestDao`
- statements: `insert:create`, `insert:batchInsert`
- tables: `energy_light_estimate_station_test`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyLightEstimateNoElecPrice.xml
- namespace: `com.rrsjk.report.dao.local.EnergyLightEstimateNoElecPriceDao`
- statements: `insert:create`, `update:update`, `select:findCount`, `select:findList`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportBtModeDay.xml
- namespace: `com.rrsjk.report.dao.local.ReportBtModeDayDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportScreenDashboardYueXiu.xml
- namespace: `com.rrsjk.report.dao.local.ReportScreenDashboardYueXiuDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByFetchAt`, `select:getLatestByFetchAt`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportScreenDashboardBoc.xml
- namespace: `com.rrsjk.report.dao.local.ReportScreenDashboardBocDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByFetchAt`, `select:getLatestByFetchAt`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergySubchainGroupSameTime.xml
- namespace: `com.rrsjk.report.dao.local.EnergySubchainGroupSameTimeDao`
- statements: `select:findStorageOther`, `select:findLightElec`, `select:findLightOther`
- tables: `energy_subchain_group_same_time`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportCmbScreenEnergy.xml
- namespace: `com.rrsjk.report.dao.local.ReportCmbScreenEnergyDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/LightTechAuditClosedReport.xml
- namespace: `com.rrsjk.report.dao.local.LightTechAuditClosedReportDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:selectAll`, `select:findBy`, `select:findPage`, `select:countTotal`, `select:getByCenterCodeTypeDate`, `select:count`
- tables: `id`, `light_tech_audit_closed_report`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyLightEstimate.xml
- namespace: `com.rrsjk.report.dao.local.EnergyLightEstimateDao`
- statements: `insert:create`, `update:update`, `select:findByCompanyCodeAndDayAt`, `select:findByDayAt`, `select:findEstimateOff`, `select:findByCompanyCode`, `select:findByTypeAndDayAt`, `select:findEstimateOffSum`, `select:queryCountByParams`, `select:findByGroupBY`, `select:findByid`, `select:findForOff`, `select:checkForOff`
- tables: `energy_light_estimate`, `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/LightEstimateCityElecPrice.xml
- namespace: `com.rrsjk.report.dao.local.LightEstimateCityElecPriceDao`
- statements: `select:findElecPrice`, `select:findAll`, `select:find`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyCountyCenterDay.xml
- namespace: `com.rrsjk.report.dao.local.EnergyCountyCenterDayDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:findByDayAtAndSort`, `select:findBySort`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/SapSpCenterRelation.xml
- namespace: `com.rrsjk.report.dao.local.SapSpCenterRelationDao`
- statements: `select:findAll`, `select:findRealAll`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyLeasedStationAssetManagement.xml
- namespace: `com.rrsjk.report.dao.local.EnergyLeasedStationAssetManagementDao`
- statements: `insert:create`, `select:get`, `select:getByStationCode`, `select:countOf`, `select:findBy`, `insert:batchInsert`, `select:findByStationCodeList`, `update:update`, `delete:delete`, `select:findSumPriceByCustomerCode`, `select:findAll`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyInventoryTurnoverControlSp.xml
- namespace: `com.rrsjk.report.dao.local.EnergyInventoryTurnoverControlSpDao`
- statements: `insert:create`, `select:get`, `select:countOf`, `select:findBy`, `insert:batchInsert`, `select:getSumSomeDays`
- tables: `energy_inventory_turnover_control_sp`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyCenterProfitTarget.xml
- namespace: `com.rrsjk.report.dao.local.EnergyCenterProfitTargetDao`
- statements: `select:findMonth`, `select:findYear`, `select:findPuYinIncome`, `select:findPuYinCost`, `select:findByCenterAndMonth`, `select:findYearPuYinIncome`, `select:findYearPuYinCost`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/OeratingLeasePaymentPeceipt.xml
- namespace: `com.rrsjk.report.dao.local.OeratingLeasePaymentPeceiptDao`
- statements: `insert:create`, `select:countOf`, `select:findBy`, `select:getByPaymentReceiptCode`, `delete:deleteByPaymentReceiptCode`, `update:update`, `update:updateByPaymentReceiptCode`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyElecWarningDetail.xml
- namespace: `com.rrsjk.report.dao.local.EnergyElecWarningDetailDao`
- statements: `insert:created`, `insert:batchInsert`, `update:updated`, `select:findOne`, `select:findList`, `delete:batchDeleteByTime`
- tables: `energy_elec_warning_detail`, `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportScreenMapBoc.xml
- namespace: `com.rrsjk.report.dao.local.ReportScreenMapBocDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyCenterProfit.xml
- namespace: `com.rrsjk.report.dao.local.EnergyCenterProfitDao`
- statements: `insert:create`, `update:update`, `select:findByTypeAndDayAt`, `select:findOne`
- tables: `energy_center_profit`, `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyCenterProfitActualLog.xml
- namespace: `com.rrsjk.report.dao.local.EnergyCenterProfitActualLogDao`
- statements: `insert:create`, `update:update`, `select:findOne`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyElecWarningReport.xml
- namespace: `com.rrsjk.report.dao.local.EnergyElecWarningReportDao`
- statements: `insert:created`, `insert:batchInsert`, `update:update`, `select:findList`, `select:findOne`, `delete:batchDeleteByTime`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyLightIncomeRecord.xml
- namespace: `com.rrsjk.report.dao.local.EnergyLightIncomeRecordDao`
- statements: `insert:create`, `update:update`, `select:findByDayAt`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportSpStationDevelopWarning.xml
- namespace: `com.rrsjk.report.dao.local.ReportSpStationDevelopWarningDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findBySpAndDate`, `select:findByRangeDateAt`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportAssetScreenCompanyRevenue.xml
- namespace: `com.rrsjk.report.dao.local.ReportAssetScreenCompanyRevenueDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/GreenEnergyChainGroupIncome.xml
- namespace: `com.rrsjk.report.dao.local.GreenEnergyChainGroupIncomeDao`
- statements: `insert:create`, `insert:batchInsert`, `select:findByDayAt`
- tables: `green_energy_chain_group_income`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyLightSubchainTarget.xml
- namespace: `com.rrsjk.report.dao.local.EnergyLightSubchainTargetDao`
- statements: `insert:create`, `update:update`, `select:findList`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportScreenMapCnnc.xml
- namespace: `com.rrsjk.report.dao.local.ReportScreenMapCnncDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyChainGroupIncomeChange.xml
- namespace: `com.rrsjk.report.dao.local.EnergyChainGroupIncomeChangeDao`
- statements: `insert:create`, `update:update`, `select:findOne`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyStationElecIncome.xml
- namespace: `com.rrsjk.report.dao.local.EnergyStationElecIncomeDao`
- statements: `insert:create`, `update:update`, `select:findOne`, `select:findByTime`, `select:findCount`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportBocScreenMonthElectric.xml
- namespace: `com.rrsjk.report.dao.local.ReportBocScreenMonthElectricDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyEteDay.xml
- namespace: `com.rrsjk.report.dao.local.EnergyEteDayDao`
- statements: `insert:create`, `update:update`, `select:queryOne`, `select:findBy`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyGridIncomeDay.xml
- namespace: `com.rrsjk.report.dao.local.EnergyGridIncomeDayDao`
- statements: `insert:create`, `update:update`, `select:findBy`, `select:findByDayAtAndType`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/GreenEnergyMarketScale.xml
- namespace: `com.rrsjk.report.dao.local.GreenEnergyMarketScaleDao`
- statements: `insert:create`, `update:update`, `select:findByDayAt`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyAppOverdueInventory.xml
- namespace: `com.rrsjk.report.dao.local.EnergyAppOverdueInventoryDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getDay3090`, `select:countOfDay`, `select:getDayOver90`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyElecPriceReportRegion.xml
- namespace: `com.rrsjk.report.dao.local.EnergyElecPriceReportRegionDao`
- statements: `insert:create`, `update:update`, `select:findList`, `select:findCount`, `select:findOne`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportStationDelivery.xml
- namespace: `com.rrsjk.report.dao.local.ReportStationDeliveryDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportScreenDashboard.xml
- namespace: `com.rrsjk.report.dao.local.ReportScreenDashboardDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByFetchAt`, `select:getLatestByFetchAt`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportYueXiuScreenMonthElectric.xml
- namespace: `com.rrsjk.report.dao.local.ReportYueXiuScreenMonthElectricDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportCmGridHistory.xml
- namespace: `com.rrsjk.report.dao.local.ReportCmGridHistoryDao`
- statements: `select:findAll`, `select:querySummary`, `select:getByProjectCode`, `insert:create`, `insert:batchInsert`, `update:update`, `select:findAllProjectCodes`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportPuyinScreenMonthElecMapper.xml
- namespace: `com.rrsjk.report.dao.local.ReportPuyinScreenMonthElecDao`
- statements: `select:getById`, `insert:create`, `update:update`, `select:findByParams`
- tables: `id`, `report_puyin_screen_month_elec`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportMOrder.xml
- namespace: `com.rrsjk.report.dao.local.ReportMOrderDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyChainGroup.xml
- namespace: `com.rrsjk.report.dao.local.EnergyChainGroupDao`
- statements: `select:get`, `select:findOne`, `select:findListByParentId`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportAssetScreenWorkOrder.xml
- namespace: `com.rrsjk.report.dao.local.ReportAssetScreenWorkOrderDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportScreenElecPrice.xml
- namespace: `com.rrsjk.report.dao.local.ReportScreenElecPriceDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`, `select:getByCityId`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportWholeCounty.xml
- namespace: `com.rrsjk.report.dao.local.ReportWholeCountyDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyIncomeDay.xml
- namespace: `com.rrsjk.report.dao.local.EnergyIncomeDayDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:findByDayAtAndType`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyDomesticIncomeReport.xml
- namespace: `com.rrsjk.report.dao.local.EnergyDomesticIncomeReportDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `update:updateIncomeTimeByOrderItemNo`, `select:countByIncomeTime`, `select:getByIncomeTime`, `select:countByOrderCreateTime`, `select:getByOrderCreateTime`, `select:incomeGroupByProductCategory`, `select:orderGroupByProductCategory`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportPolicyForecastFinalMapper.xml
- namespace: `com.rrsjk.report.dao.local.ReportPolicyForecastFinalDao`
- statements: `select:findByPage`, `select:countByPage`, `delete:deleteByForecastMonth`, `insert:batchInsert`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyCapitalDataDetail.xml
- namespace: `com.rrsjk.report.dao.local.EnergyCapitalDataDetailDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:findList`, `select:findCount`
- tables: `energy_capital_data_detail`, `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportScreenMapYueXiu.xml
- namespace: `com.rrsjk.report.dao.local.ReportScreenMapYueXiuDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/LightUseOrderAgeAnalysis.xml
- namespace: `com.rrsjk.report.dao.local.LightUseOrderAgeAnalysisDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `delete:deleteByStatisticalDeadline`, `select:getSumGroupBySku`, `select:findReport`, `select:countReport`
- tables: `gvs_warehouse_age_analysis`, `id`, `light_use_order_age_analysis`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportAssetScreenRent.xml
- namespace: `com.rrsjk.report.dao.local.ReportAssetScreenRentDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyLightEstimateOffStationTest.xml
- namespace: `com.rrsjk.report.dao.local.EnergyLightEstimateOffStationTestDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:findListForOff`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportMGrid.xml
- namespace: `com.rrsjk.report.dao.local.ReportMGridDao`
- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergySummaryDay.xml
- namespace: `com.rrsjk.report.dao.local.EnergySummaryDayDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:findByProvince`, `select:findByDayAtAndSort`, `select:findByDayAt`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyJinanSpLeader.xml
- namespace: `com.rrsjk.report.dao.local.EnergyJinanSpLeaderDao`
- statements: `select:findSpId`, `select:findList`, `select:findRegionIdByLeaderName`
- tables: `energy_jinan_sp_leader`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyCenterNetworkBuildTarget.xml
- namespace: `com.rrsjk.report.dao.local.EnergyCenterNetworkBuildTargetDao`
- statements: `insert:create`, `update:update`, `select:findList`
- tables: `energy_center_network_build_target`, `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergySummaryTarget.xml
- namespace: `com.rrsjk.report.dao.local.EnergySummaryTargetDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:findSubCenter`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyYuexiuReportData.xml
- namespace: `com.rrsjk.report.dao.local.EnergyYuexiuReportDataDao`
- statements: `insert:create`, `update:update`, `select:findBy`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportAssetScreenElectricRevenue.xml
- namespace: `com.rrsjk.report.dao.local.ReportAssetScreenElectricRevenueDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyOverseasIncome.xml
- namespace: `com.rrsjk.report.dao.local.EnergyOverseasIncomeDao`
- statements: `insert:create`, `update:update`, `select:findByInvoiceNumber`, `select:findByStartTime`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyOverdueInventoryControlSummary.xml
- namespace: `com.rrsjk.report.dao.local.EnergyOverdueInventoryControlSummaryDao`
- statements: `insert:create`, `select:get`, `select:countOf`, `select:findBy`, `insert:batchInsert`, `select:getLossSumGroupByCenter`
- tables: `energy_overdue_inventory_control_summary`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/OperationalAssetManagement.xml
- namespace: `com.rrsjk.report.dao.local.OperationalAssetManagementDao`
- statements: `insert:create`, `insert:batchCreate`, `select:countOf`, `select:findBy`, `select:findByStationCodeList`, `select:findByPaymentReceiptCode`, `update:update`, `delete:delete`, `delete:deleteByPaymentReceiptCode`, `select:getByStationCodes`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportScreenEnergy.xml
- namespace: `com.rrsjk.report.dao.local.ReportScreenEnergyDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportScreenMonthElec.xml
- namespace: `com.rrsjk.report.dao.local.ReportScreenMonthElecDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/VmOrderBill.xml
- namespace: `com.rrsjk.report.dao.local.VmOrderBillDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getNewOrderNumList`, `select:findSumByTime`, `select:getOrderIncomeByTime`
- tables: `id`, `vm_order`, `vm_order_bill`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportScreenCounty.xml
- namespace: `com.rrsjk.report.dao.local.ReportScreenCountyDao`
- statements: `insert:create`, `update:update`, `select:getById`, `select:queryListBy`, `select:queryCountBy`, `select:findByParams`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/ReportRegionPowerSummaryMapper.xml
- namespace: `com.rrsjk.report.dao.local.ReportRegionPowerSummaryDao`
- statements: `select:findByPage`, `select:countByPage`, `delete:deleteByDataDate`, `insert:batchInsert`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/EnergyStationDay.xml
- namespace: `com.rrsjk.report.dao.local.EnergyStationDayDao`
- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`, `select:findByDayAtAndType`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/bt/BtProjectCompanyMasterData.xml
- namespace: `com.rrsjk.report.dao.local.bt.BtProjectCompanyMasterDataDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByCompanyCode`, `select:getByCompanyCodes`, `update:voidByCompanyCode`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/bt/BtFundAssetRepaymentRecord.xml
- namespace: `com.rrsjk.report.dao.local.bt.BtFundAssetRepaymentRecordDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `select:getById`, `select:findByRepaymentId`, `select:findByRepaymentIdAndFap`, `select:findRepaymentAmount`, `select:getMaxOrderByRepaymentId`, `select:sumAmountByRepaymentId`, `select:getByRecordNo`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/bt/LightAssetManagementReport.xml
- namespace: `com.rrsjk.report.dao.local.bt.LightAssetManagementReportDao`
- statements: `insert:create`, `update:update`, `insert:batchInsert`, `select:findAll`, `delete:delete`, `select:findByCond`, `select:countOf`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/bt/BtAssetManagement.xml
- namespace: `com.rrsjk.report.dao.local.bt.BtAssetManagementDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getByStationCode`, `select:findAll`, `select:getByStationCodes`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/bt/BtFundAssetRepayment.xml
- namespace: `com.rrsjk.report.dao.local.bt.BtFundAssetRepaymentDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `select:getById`, `select:getByRepaymentNo`, `select:findByBatchKeys`, `select:getMaxRepaymentNoByPrefix`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/bt/BtFundAssetManagementReport.xml
- namespace: `com.rrsjk.report.dao.local.bt.BtFundAssetManagementReportDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `select:getById`, `select:getByStationCode`, `select:getByStationCodes`, `select:findAll`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/bt/LightAssetInProgressReport.xml
- namespace: `com.rrsjk.report.dao.local.bt.LightAssetInProgressReportDao`
- statements: `insert:create`, `update:update`, `insert:batchInsert`, `select:findByCond`, `select:countOf`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/local/bt/BtFundAssetAllocateDetail.xml
- namespace: `com.rrsjk.report.dao.local.bt.BtFundAssetAllocateDetailDao`
- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:findUnlinked`, `select:findUnlinkedGroupBy`, `select:findByGroupKeys`, `update:updateRepaymentNo`, `select:findByStationCodes`
- tables: `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/finance/LightIncomeRecord.xml
- namespace: `com.rrsjk.report.dao.finance.LightIncomeRecordDao`
- statements: `select:findByMode`
- tables: `light_income_record`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/dws/DwsLightStationElec.xml
- namespace: `com.rrsjk.report.dao.dws.DwsLightStationElecDao`
- statements: `select:queryDistinctListBy`, `select:findElecSumProvince`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/dws/DwsLightStationElectricDayReportNew.xml
- namespace: `com.rrsjk.report.dao.dws.DwsLightStationElectricDayReportNewDao`
- statements: `select:findBy`, `select:countOf`, `select:findByGroupByStationCode`, `select:getElectricSum`, `select:getElectricAndIncome`, `select:queryDayElectric`, `select:queryBocDayElectric`, `select:queryCnncDayElectric`, `select:queryYueXiuDayElectric`, `select:getElectricAndIncomeByCode`, `select:getBocElectricAndIncomeByCode`, `select:getCnncElectricAndIncomeByCode`, `select:getYueXiuElectricAndIncomeByCode`, `select:queryDayElectricByCode`, `select:queryBocDayElectricByCode`, `select:queryCnncDayElectricByCode`, `select:queryYueXiuDayElectricByCode`, `select:findDaysElectric`, `select:findStationColumnByCmb`, `select:findStationColumnByBoc`, `select:findStationColumnByCnnc`, `select:findStationColumnByYueXiu`, `select:queryTotalElectricByCompanyCode`, `select:getElectricAndIncomeForPuyin`, `select:getElectricAndIncomeForPuyinByCode`, `select:getElectricAndIncomeByCodeInAssert`, `select:queryDayElectricByCodeInAssert`, `select:queryChartMonthElecByMonth`, `select:getPuyinElectricAndIncome`
- tables: `ads.green_energy_report_light_station_chart_month`, `boc_leasing_light_station`, `cmb_leasing_station`, `cnnc_leasing_light_station`, `dws.green_energy_light_station_daily_current`, `energy_leased_station_asset_management`, `light_city_elec_price`, `light_station`, `light_station_elec_day_report_new`, `light_station_white_list_simple`, `ods.energy_leased_station_asset_management`, `ods.green_energy_cmb_leasing_station`, `ods.green_energy_light_city_elec_price`, `ods.green_energy_light_station_white_list`, `ods.green_energy_light_station_white_list_simple`, `report_station_chart_month`, `yuexiu_leasing_light_station`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/dws/GreenEnergyInverterCurrent.xml
- namespace: `com.rrsjk.report.dao.dws.GreenEnergyInverterCurrentDao`
- statements: `select:getPuyinRealtimePower`, `select:findPuyinDashBoardCountData`, `select:findSnByStationCode`, `select:listInveterError`, `select:listInveterErrorNow`, `select:getTotalFacByParams`, `select:findByParams`, `select:findList`, `select:getTotalByParams`, `select:findListByBindYear`
- tables: `ads.green_energy_report_light_inverter_chart_day`, `base_stations`, `cond1_count`, `dws.green_energy_inverter_current`, `dws.green_energy_light_station_daily_current`, `elec_today_val`, `ods.green_energy_light_station`, `ods.green_energy_light_station_inverter`, `ods.green_energy_light_station_white_list_simple`, `offline_old_count`, `offline_today_count`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/dwt/ZeroCarbonHomeStationDetails.xml
- namespace: `com.rrsjk.report.dao.dwt.ZeroCarbonHomeStationDetailsDao`
- statements: `select:findCount`, `select:findBy`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/dwt/ZeroCarbonEsStationDetails.xml
- namespace: `com.rrsjk.report.dao.dwt.ZeroCarbonEsStationDetailsDao`
- statements: `select:findCount`, `select:findBy`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/ods/ChargingStationTOrderChargingHistory.xml
- namespace: `com.rrsjk.report.dao.ods.ChargingStationTOrderChargingHistoryDao`
- statements: `select:findBy`, `select:countOf`, `select:getById`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/ods/OdsEnergyAuditValidityReport.xml
- namespace: `com.rrsjk.report.dao.ods.OdsEnergyAuditValidityReportDao`
- statements: `select:auditValidity`, `select:countByPeopleNameAndAuditType`
- tables: `green_energy_light_station_operate_log`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/ods/LightStationElectricDayReportNewOds.xml
- namespace: `com.rrsjk.report.dao.ods.LightStationElectricDayReportNewOdsDao`
- statements: `select:findBy`, `select:getElectricAndIncomeHuarong`, `select:getElectricAndIncomeByCodeHuarong`, `select:getBocElectricAndIncomeByCode`, `select:getCnncElectricAndIncomeByCode`, `select:getYueXiuElectricAndIncomeByCode`, `select:findDaysElectric`
- tables: `green_energy_boc_leasing_light_station`, `green_energy_cnnc_leasing_light_station`, `green_energy_energy_leased_station_asset_management`, `green_energy_hrflc_sync_pv_info`, `green_energy_light_city_elec_price`, `green_energy_light_station_elec_day_report_new`, `green_energy_yuexiu_leasing_light_station`, `light_city_elec_price`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/ods/OdsLightProjectElectricOrder.xml
- namespace: `com.rrsjk.report.dao.ods.OdsLightProjectElectricOrderDao`
- statements: `select:findCount`, `select:maxId`, `select:findBy`, `select:findByWithIdPage`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/ods/TPlant.xml
- namespace: `com.rrsjk.report.dao.ods.TPlantDao`
- statements: `select:get`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/ods/ReportConfigQueryOdsMapper.xml
- namespace: `com.rrsjk.report.dao.ods.ReportConfigQueryOdsDao`
- statements: `select:findStationPlanConfigs`, `select:findUseOrderBySkuAndStation`, `select:findStationIdsByRegion`, `select:findModuleCostByRegion`, `select:findInverterCostByRegion`
- tables: `green_energy_light_station`, `green_energy_light_station_plan_config`, `green_energy_light_use_order`, `green_energy_product_price`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/ods/ChargingStationTOrderSettlenfo.xml
- namespace: `com.rrsjk.report.dao.ods.ChargingStationTOrderSettlenfoDao`
- statements: `select:findBy`, `select:countOf`, `select:getById`, `select:findByStationIdAndMonth`
- tables: `charging_station_t_order_charging_history`, `charging_station_t_order_settle_info`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/ods/ReportPowerSummaryOdsMapper.xml
- namespace: `com.rrsjk.report.dao.ods.ReportPowerSummaryOdsDao`
- statements: `select:queryStationPowerData`
- tables: `green_energy_light_station`, `green_energy_light_station_elec_day_report_new`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/ods/SapPurchaseRecordMapper.xml
- namespace: `com.rrsjk.report.dao.ods.SapPurchaseRecordOdsDao`
- statements: `select:getPurchaseNo`, `select:getBySettleId`, `select:getByEbeln`, `insert:insert`, `select:selectRecord`, `select:selectGroupByPurchaseNoLeftLike`, `select:findCount`, `select:getRecordByIds`, `update:updateByIds`, `update:update`, `update:updateSapPurchaseRecordStatus`, `select:getPurchaseOrderByPay`, `update:updateBySettledId`, `select:selectByNoLike`, `select:selectByNoLike`, `select:findSpGridPolicyInfo`
- tables: `OrderProducts`, `green_energy_light_sp_grid_award_order`, `green_energy_sap_purchase_record`, `id`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/ods/OdsLightStationElectricDayReportNew.xml
- namespace: `com.rrsjk.report.dao.ods.OdsLightStationElectricDayReportNewDao`
- statements: `select:queryTotalElectricByCompanyCode`, `select:getElectricAndIncome`, `select:getBocElectricAndIncome`, `select:getCnncElectricAndIncome`, `select:getYueXiuElectricAndIncome`, `select:getPuyinElectricAndIncome`
- tables: `green_energy_boc_leasing_light_station`, `green_energy_cmb_leasing_station`, `green_energy_cnnc_leasing_light_station`, `green_energy_energy_leased_station_asset_management`, `green_energy_light_city_elec_price`, `green_energy_light_station_elec_day_report_new`, `green_energy_light_station_white_list_simple`, `green_energy_yuexiu_leasing_light_station`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/ods/SpSubDataDashboard.xml
- namespace: `com.rrsjk.report.dao.ods.SpSubDataDashboardDao`
- statements: `select:findBuildData`, `select:findInitialOperationData`
- tables: `green_energy_light_sp_authority_zone`, `green_energy_light_sp_inspire`, `green_energy_light_station`, `green_energy_light_station_operate_log`, `green_energy_light_sub_sp`, `green_energy_light_sub_sp_region`

## rrsjk-light-report-service/rrsjk-light-report-impl/src/main/resources/mybatis/mapper/ods/HaierEnergyTSelfReportMetric.xml
- namespace: `com.rrsjk.report.dao.ods.HaierEnergyTSelfReportMetricDao`
- statements: `select:findBy`, `select:countOf`, `select:getById`, `select:getPvGenerationByMonth`, `select:getPvGenerationByMapIdAndMonth`
- tables: `haier_energy_t_self_report_metric`

## item-service/item-impl/src/main/resources/item-sql-mapper/BrandsMapper.xml
- namespace: `com.haier.cbs.item.dao.BrandsDao`
- statements: `select:get`, `insert:insert`, `update:update`
- tables: `Brands`, `id`

## item-service/item-impl/src/main/resources/item-sql-mapper/PaymentsMapper.xml
- namespace: `com.haier.cbs.item.dao.PaymentsDao`
- statements: `select:get`, `select:getByCode`
- tables: `Payments`

## item-service/item-impl/src/main/resources/item-sql-mapper/ProductCatesMapper.xml
- namespace: `com.haier.cbs.item.dao.ProductCatesDao`
- statements: `select:get`, `select:getAllProductCates`, `select:getAllChildren`, `insert:insert`, `update:update`
- tables: `ProductCates`, `id`, `productcates`

## item-service/item-impl/src/main/resources/item-sql-mapper/NetPointsMapper.xml
- namespace: `com.haier.cbs.item.dao.NetPointsDao`
- statements: `select:get`, `select:getByNetPointByCode`
- tables: `NetPoints`

## item-service/item-impl/src/main/resources/item-sql-mapper/ItemBaseMapper.xml
- namespace: `com.haier.cbs.item.dao.ItemBaseDao`
- statements: `select:get`, `select:getBySku`, `update:update`, `update:updateNotNull`, `insert:insert`, `select:getItemListByDepList`, `select:list`, `select:getIncompleteItemBaseList`, `select:countItemBaseByParamWithLike`, `select:queryItemBaseByParamWithLike`, `select:findItemBaseByMaterialId`
- tables: `id`, `item_base`

## item-service/item-impl/src/main/resources/item-sql-mapper/ItemAttributeMapper.xml
- namespace: `com.haier.cbs.item.dao.ItemAttributeDao`
- statements: `select:get`, `select:getByValueAndValueSetId`, `update:update`, `update:updateNotNull`, `insert:insert`, `select:list`, `select:getAllCbsCategory`, `select:countItemAttributeWithLike`, `select:queryItemAttributeWithLike`, `select:queryProductGroupByCbsCategory`, `select:getByValueSetId`, `select:getCbsCategoryByProductGroup`
- tables: `id`, `item_attribute`

## item-service/item-impl/src/main/resources/item-sql-mapper/ProductTypesMapper.xml
- namespace: `com.haier.cbs.item.dao.ProductTypesDao`
- statements: `select:getById`, `insert:insert`, `update:update`
- tables: `ProductTypes`, `id`, `producttypes`

## item-service/item-impl/src/main/resources/item-sql-mapper/ProductsMapper.xml
- namespace: `com.haier.cbs.item.dao.ProductsDao`
- statements: `select:queryLastInsertPriceRuleId`, `select:queryPriceRuleCount`, `insert:insertPriceRulesLogs`, `select:getDetailPriceRuleByProId`, `delete:deleteOldLadderPrice`, `select:getAlProductLadderPrices`, `select:getProductCost`, `insert:addProductLadderPrice`, `select:viewProductLadderPrice`, `update:editProductLadderPrice`, `update:publishProductPrice`, `update:deleteProductPrice`, `update:terminateProductPrice`, `select:get`, `select:getBySku`, `select:getAllProductInfo`, `select:getListBySkus`, `select:getAllSkusListBySale`, `select:getBaseBySku`, `select:getAllProductsBysCode`, `update:updateSaleNumBySku`, `insert:insert`, `update:update`, `update:updateProductsSaleNumById`, `select:getProductIdByRuleId`, `select:getNeedChangeStatusPriceRules`, `update:changePriceRuleStatus`, `select:getTotalSaleNum`, `update:updateVirtualSaleNum`, `update:updateTaoBaoId`
- tables: `PriceRules`, `Products`, `id`, `shop`.`PriceRuleLogs`, `shop`.`PriceRules`, `shop`.`PurchaseCost`

## item-service/item-impl/src/main/resources/item-sql-mapper/LesFiveYardsMapper.xml
- namespace: `com.haier.cbs.item.dao.LesFiveYardsDao`
- statements: `select:selectLesFiveYards`
- tables: `LesFiveYards`
