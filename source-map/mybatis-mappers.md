     1|# MyBatis Mapper 索引
     2|
     3|来源: master XML 静态扫描。
     4|
     5|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/SaleArea.xml
     6|- namespace: `com.rrsjk.item.dao.SaleAreaDao`
     7|- statements: `insert:create`, `update:update`, `select:get`, `select:findByShopId`, `select:findByShopIdAndName`, `select:findByShopIdAndDefault`, `select:countOf`, `select:findBy`, `select:findByProvince`
     8|- tables: `id`
     9|
    10|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/CustomDrinks.xml
    11|- namespace: `com.rrsjk.item.dao.CustomDrinksDao`
    12|- statements: `insert:create`, `update:update`, `select:getById`, `select:findCount`, `select:find`
    13|- tables: `id`
    14|
    15|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/SaleChannel.xml
    16|- namespace: `com.rrsjk.item.dao.SaleChannelDao`
    17|- statements: `select:get`, `select:findBy`
    18|
    19|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ItemAuditApply.xml
    20|- namespace: `com.rrsjk.item.dao.ItemAuditApplyDao`
    21|- statements: `insert:create`, `update:update`, `select:get`, `select:getLastByItemId`
    22|- tables: `id`
    23|
    24|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/SettleType.xml
    25|- namespace: `com.rrsjk.item.dao.SettleTypeDao`
    26|- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`
    27|- tables: `id`
    28|
    29|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/productBreakevenPriceChangeNoticeObs.xml
    30|- namespace: `com.rrsjk.item.dao.ProductBreakevenPriceChangeNoticeObsDao`
    31|- statements: `select:findBy`, `select:countOf`, `insert:create`, `update:update`, `insert:batchInsert`, `select:getById`, `select:getNoticeFail`
    32|- tables: `id`, `product_breakeven_price`, `product_breakeven_price_change_notice_obs`
    33|
    34|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ItemAuditRecord.xml
    35|- namespace: `com.rrsjk.item.dao.ItemAuditRecordDao`
    36|- statements: `insert:create`, `update:update`, `select:get`
    37|- tables: `id`
    38|
    39|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/Collect.xml
    40|- namespace: `com.rrsjk.item.dao.CollectDao`
    41|- statements: `insert:insert`, `select:findByMemberIdAndItemId`
    42|
    43|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/Spu.xml
    44|- namespace: `com.rrsjk.item.dao.SpuDao`
    45|- statements: `insert:create`, `update:update`, `select:get`, `select:findByCategoryId`, `select:findByParams`, `select:findCount`, `select:find`
    46|- tables: `id`
    47|
    48|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ItemSearchRecord.xml
    49|- namespace: `com.rrsjk.item.dao.ItemSearchRecordDao`
    50|- statements: `insert:create`, `select:findByMemberId`, `select:getByMemberIdAndContent`
    51|
    52|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/SkuMeal.xml
    53|- namespace: `com.rrsjk.item.dao.SkuMealDao`
    54|- statements: `insert:create`, `update:update`, `select:get`, `select:findByItemId`, `select:findBySkuId`, `select:countOf`, `select:findBy`
    55|- tables: `id`
    56|
    57|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ItemImage.xml
    58|- namespace: `com.rrsjk.item.dao.ItemImageDao`
    59|- statements: `insert:create`, `update:update`, `select:get`, `select:findByItemId`, `select:findByItemIdAndImageType`, `update:disableBannerByItemId`
    60|- tables: `id`
    61|
    62|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/FrontCategory.xml
    63|- namespace: `com.rrsjk.item.dao.FrontCategoryDao`
    64|- statements: `insert:create`, `update:update`, `select:get`, `select:findCount`, `select:find`
    65|- tables: `id`
    66|
    67|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/SkuLimited.xml
    68|- namespace: `com.rrsjk.item.dao.SkuLimitedDao`
    69|- statements: `insert:create`, `update:update`, `select:get`, `select:getBySkuId`, `select:countOf`, `select:findBy`
    70|- tables: `id`
    71|
    72|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ZeroCarbonItemSetMealStockChangeLogMapper.xml
    73|- namespace: `com.rrsjk.item.dao.ZeroCarbonItemSetMealStockChangeLogDao`
    74|- statements: `insert:created`, `insert:batchInsert`, `update:updated`, `delete:deleteById`, `select:selectById`, `select:findList`, `select:selectByCondition`, `select:count`, `select:findCount`, `select:findPage`, `select:getAllBySetMealCode`, `select:countByOrderNoAndType`, `select:findByOrderNoAndType`
    75|- tables: `id`, `zero_carbon_item_set_meal_stock_change_log`
    76|
    77|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/YzzOptItem.xml
    78|- namespace: `com.rrsjk.item.dao.YzzOptItemDao`
    79|- statements: `insert:insert`, `update:update`, `select:find`
    80|- tables: `id`
    81|
    82|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/CustomDrinksDetail.xml
    83|- namespace: `com.rrsjk.item.dao.CustomDrinksDetailDao`
    84|- statements: `insert:create`, `update:update`, `select:findByCustomId`, `delete:deleteByPrimaryKey`
    85|- tables: `id`
    86|
    87|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ItemSaleChannel.xml
    88|- namespace: `com.rrsjk.item.dao.ItemSaleChannelDao`
    89|- statements: `insert:create`, `update:update`, `select:get`, `select:findByItemId`, `delete:deleteByItemId`, `select:findBySaleChannel`
    90|- tables: `id`
    91|
    92|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ProductPrice.xml
    93|- namespace: `com.rrsjk.item.dao.ProductPriceDao`
    94|- statements: `insert:create`, `update:update`, `select:get`, `select:findCount`, `select:find`, `select:findSkuTaxRate`, `select:selectProductPriceByMultiCondition`
    95|- tables: `id`
    96|
    97|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/CbsItemSku.xml
    98|- namespace: `com.rrsjk.item.dao.CbsItemSkuDao`
    99|- statements: `select:countOf`, `select:findBy`
   100|- tables: `item`
   101|
   102|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ShopSpuPlateformRate.xml
   103|- namespace: `com.rrsjk.item.dao.ShopSpuPlateformRateDao`
   104|- statements: `insert:create`, `update:update`, `select:get`, `select:findCount`, `select:find`, `select:getByShopIdAndSpuId`
   105|- tables: `id`
   106|
   107|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ProductBreakevenPrice.xml
   108|- namespace: `com.rrsjk.item.dao.ProductBreakevenPriceDao`
   109|- statements: `insert:create`, `update:update`, `select:get`, `select:findCount`, `select:find`, `select:getBySkuCode`, `select:getBySkuCodeAndCompanyCode`
   110|- tables: `id`
   111|
   112|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/CustomDrinksVoice.xml
   113|- namespace: `com.rrsjk.item.dao.CustomDrinksVoiceDao`
   114|- statements: `insert:create`, `update:update`, `select:getById`, `select:getByCode`, `select:findCount`, `select:find`
   115|- tables: `id`
   116|
   117|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/Category.xml
   118|- namespace: `com.rrsjk.item.dao.CategoryDao`
   119|- statements: `insert:create`, `update:update`, `select:get`, `select:findChildren`, `select:findCount`, `select:findMaxSort`, `select:findByName`
   120|- tables: `category`, `id`
   121|
   122|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/SkuRelate.xml
   123|- namespace: `com.rrsjk.item.dao.SkuRelateDao`
   124|- statements: `insert:create`, `update:update`, `select:get`, `select:getEnableBySkuId`, `select:countOf`, `select:findBy`
   125|- tables: `id`
   126|
   127|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ZeroCarbonItemSetMealStockMapper.xml
   128|- namespace: `com.rrsjk.item.dao.ZeroCarbonItemSetMealStockDao`
   129|- statements: `insert:created`, `insert:batchInsert`, `update:updated`, `delete:deleteById`, `select:selectById`, `select:findList`, `select:selectByCondition`, `select:count`, `select:findCount`, `select:findPage`, `select:getAvailableStockByCode`, `select:selectByPlanStockCode`, `update:updateStockById`, `update:recoverStock`
   130|- tables: `id`, `zero_carbon_item_set_meal_stock`
   131|
   132|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ShopTypeSaleChannel.xml
   133|- namespace: `com.rrsjk.item.dao.ShopTypeSaleChannelDao`
   134|- statements: `insert:create`, `update:update`, `select:get`, `select:findByShopType`
   135|- tables: `id`
   136|
   137|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/CategoryAttributeValue.xml
   138|- namespace: `com.rrsjk.item.dao.CategoryAttributeValueDao`
   139|- statements: `insert:create`, `update:update`, `select:get`, `select:find`, `select:findByAttributeId`, `update:delCateAttrValByCateId`
   140|- tables: `id`
   141|
   142|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/Item.xml
   143|- namespace: `com.rrsjk.item.dao.ItemDao`
   144|- statements: `insert:create`, `update:update`, `select:get`, `select:batchGet`, `select:countOf`, `select:findBy`, `select:findBySpuId`, `select:findBySaleAreaId`, `update:addSale`, `select:findByItemIdList`, `select:findCountByItemIdList`, `select:findByParam`, `select:findItemBrandName`, `select:findItemBrandNameForOther`, `select:findShopForQuota`
   145|- tables: `category`, `id`, `item`
   146|
   147|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/FrontCategoryTopItem.xml
   148|- namespace: `com.rrsjk.item.dao.FrontCategoryTopItemDao`
   149|- statements: `insert:create`, `update:update`, `select:getByItemId`, `select:get`, `delete:del`, `select:findCount`, `select:find`
   150|- tables: `front_category_top_item`, `id`
   151|
   152|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/Brand.xml
   153|- namespace: `com.rrsjk.item.dao.BrandDao`
   154|- statements: `insert:create`, `update:update`, `select:get`, `select:findByParam`, `select:findCount`, `select:find`
   155|- tables: `id`
   156|
   157|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/CategoryMapping.xml
   158|- namespace: `com.rrsjk.item.dao.CategoryMappingDao`
   159|- statements: `insert:create`, `update:update`, `select:findCount`, `select:find`, `select:findByParams`, `delete:delete`
   160|- tables: `front_category`, `id`
   161|
   162|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/CategoryAttribute.xml
   163|- namespace: `com.rrsjk.item.dao.CategoryAttributeDao`
   164|- statements: `insert:create`, `update:update`, `select:get`, `select:find`, `select:findCount`, `update:delCateAttrByCateId`
   165|- tables: `id`
   166|
   167|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/YzzCategoryItem.xml
   168|- namespace: `com.rrsjk.item.dao.YzzCategoryItemDao`
   169|- statements: `insert:insert`, `update:update`, `select:findByCategoryId`, `select:findCount`, `select:find`, `select:getByItemId`, `select:getById`
   170|- tables: `id`
   171|
   172|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ProductPriceChangeLog.xml
   173|- namespace: `com.rrsjk.item.dao.ProductPriceChangeLogDao`
   174|- statements: `insert:create`
   175|
   176|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/Comment.xml
   177|- namespace: `com.rrsjk.item.dao.CommentDao`
   178|- statements: `insert:create`, `update:update`, `select:get`, `select:countOf`, `select:findBy`
   179|- tables: `id`
   180|
   181|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/FrontCategoryCarousel.xml
   182|- namespace: `com.rrsjk.item.dao.FrontCategoryCarouselDao`
   183|- statements: `insert:create`, `update:update`, `select:findShowList`, `select:findCount`, `select:find`, `delete:delete`
   184|- tables: `id`
   185|
   186|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/SpuAttributeValue.xml
   187|- namespace: `com.rrsjk.item.dao.SpuAttributeValueDao`
   188|- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:get`, `select:find`, `delete:delete`, `select:findBySpuIdAndType`, `update:updateStatusBySpuId`
   189|- tables: `id`
   190|
   191|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ItemExtras.xml
   192|- namespace: `com.rrsjk.item.dao.ItemExtrasDao`
   193|- statements: `insert:create`, `update:update`, `select:get`, `select:getByItemId`
   194|- tables: `id`
   195|
   196|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ProductData.xml
   197|- namespace: `com.rrsjk.item.dao.ProductDataDao`
   198|- statements: `insert:create`, `update:update`, `select:get`, `select:getBySkuCode`, `select:getBySkuCodeAndCompanyCode`, `select:findCount`, `select:find`, `select:findByParams`, `select:findBySkus`
   199|- tables: `id`
   200|
   201|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ItemSku.xml
   202|- namespace: `com.rrsjk.item.dao.ItemSkuDao`
   203|- statements: `select:countOf`, `select:findBy`, `select:sumPriceByMealSkuId`, `select:findByMealSkuId`
   204|- tables: `item`, `sku`
   205|
   206|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ProductPurchaseCost.xml
   207|- namespace: `com.rrsjk.item.dao.ProductPurchaseCostDao`
   208|- statements: `insert:create`, `update:update`, `select:get`, `select:findCount`, `select:find`, `select:getLastEffective`, `select:getLastEffectiveByCompanyCode`, `insert:batchInsert`
   209|- tables: `id`
   210|
   211|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/SpuImage.xml
   212|- namespace: `com.rrsjk.item.dao.SpuImageDao`
   213|- statements: `insert:create`, `update:update`, `select:get`
   214|- tables: `id`
   215|
   216|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ZeroCarbonItemSetMeal.xml
   217|- namespace: `com.rrsjk.item.dao.ZeroCarbonItemSetMealDao`
   218|- statements: `insert:created`, `update:updated`, `select:get`, `select:findCount`, `select:findPage`, `update:updateToDelete`, `select:findAllByShop`
   219|- tables: `id`
   220|
   221|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ItemOperateLog.xml
   222|- namespace: `com.rrsjk.item.dao.ItemOperateLogDao`
   223|- statements: `insert:create`, `update:update`, `select:get`
   224|- tables: `id`
   225|
   226|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ZeroCarbonItemSetMealContent.xml
   227|- namespace: `com.rrsjk.item.dao.ZeroCarbonItemSetMealContentDao`
   228|- statements: `insert:created`, `insert:batchInsert`, `update:update`, `select:findList`
   229|- tables: `id`
   230|
   231|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/YzzCategory.xml
   232|- namespace: `com.rrsjk.item.dao.YzzCategoryDao`
   233|- statements: `insert:insert`, `update:update`, `select:findCategoryList`, `select:findCount`, `select:find`, `select:findOtherCategoryList`, `select:getById`
   234|- tables: `id`
   235|
   236|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ItemChuneng.xml
   237|- namespace: `com.rrsjk.item.dao.ItemChunengDao`
   238|- statements: `select:findBySort`
   239|
   240|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/Sku.xml
   241|- namespace: `com.rrsjk.item.dao.SkuDao`
   242|- statements: `insert:create`, `update:update`, `select:get`, `select:findByItemId`, `select:findBySkuCode`, `select:findByItemIdAndStatus`, `select:findByItemIdAndAuditStatus`, `select:countOf`, `select:findBy`
   243|- tables: `id`
   244|
   245|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/ItemPage.xml
   246|- namespace: `com.rrsjk.item.dao.ItemPageDao`
   247|- statements: `select:countOf`, `select:findBy`
   248|- tables: `item`
   249|
   250|## rrsjk-item-service/rrsjk-item-impl/src/main/resources/mybatis/mapper/CommentImage.xml
   251|- namespace: `com.rrsjk.item.dao.CommentImageDao`
   252|- statements: `insert:create`, `insert:batchInsert`, `select:findByCommentId`
   253|
   254|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/shop/VOMProductPriceMapper.xml
   255|- namespace: `com.rrsjk.migration.shop.dao.VOMProductPriceDao`
   256|- statements: `select:findInfo`, `select:batchGet`
   257|- tables: `vom_product_price`
   258|
   259|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/shop/WarehouseStraightProductsMapper.xml
   260|- namespace: `com.rrsjk.migration.shop.dao.WarehouseStraightProductsDao`
   261|- statements: `select:findAddInfo`, `select:findDelInfo`, `select:batchGet`
   262|- tables: `WarehouseStraightProducts`
   263|
   264|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/shop/ShopSupplier.xml
   265|- namespace: `com.rrsjk.migration.shop.dao.ShopSupplierDao`
   266|- statements: `select:batchGet`, `select:findInfo`
   267|
   268|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/shop/ShopMemberAddressMapper.xml
   269|- namespace: `com.rrsjk.migration.shop.dao.ShopMemberAddressDao`
   270|- statements: `insert:insert`, `insert:batchInsert`, `select:findByMemberId`
   271|
   272|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/shop/MemberLoginInfoMapper.xml
   273|- namespace: `com.rrsjk.migration.shop.dao.ShopMemberLoginInfoDao`
   274|- statements: `insert:insertLoginInfo`, `select:getMemberLoginInfo`, `select:getLoginInfoByLoginName`, `select:getLoginInfoByLoginNameAndMemberId`
   275|- tables: `LoginInfo`
   276|
   277|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/shop/VOMProductDataMapper.xml
   278|- namespace: `com.rrsjk.migration.shop.dao.VOMProductDataDao`
   279|- statements: `select:findInfo`
   280|- tables: `VOMProductData`
   281|
   282|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/shop/BreakevenPriceMapper.xml
   283|- namespace: `com.rrsjk.migration.shop.dao.BreakevenPricesDao`
   284|- statements: `select:findInfo`
   285|- tables: `BreakevenPrices`
   286|
   287|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/shop/ShopMembersMapper.xml
   288|- namespace: `com.rrsjk.migration.shop.dao.ShopMembersDao`
   289|- statements: `insert:addMember`, `select:getMemberById`
   290|- tables: `Members`
   291|
   292|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/merchant/MerchantResource.xml
   293|- namespace: `com.rrsjk.migration.merchant.dao.MerchantResourceDao`
   294|- statements: `insert:create`, `insert:batchInsert`
   295|
   296|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/merchant/Supplier.xml
   297|- namespace: `com.rrsjk.migration.merchant.dao.SupplierDao`
   298|- statements: `insert:create`, `update:update`, `select:get`, `select:getByMerchantId`, `select:getBySupplierCode`
   299|- tables: `id`
   300|
   301|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/merchant/Merchant.xml
   302|- namespace: `com.rrsjk.migration.merchant.dao.MerchantDao`
   303|- statements: `insert:create`, `update:update`, `select:get`, `select:getByMemberId`, `select:getByTaxCode`, `select:getBySupplierCode`
   304|- tables: `id`
   305|
   306|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/merchant/ProfessionalCustomer.xml
   307|- namespace: `com.rrsjk.migration.merchant.dao.ProfessionalCustomerDao`
   308|- statements: `insert:create`, `update:update`, `select:get`, `select:getByMerchantId`
   309|- tables: `id`
   310|
   311|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/merchant/ShopExtras.xml
   312|- namespace: `com.rrsjk.migration.merchant.dao.ShopExtrasDao`
   313|- statements: `insert:create`, `update:update`, `select:get`, `select:getByShopId`
   314|- tables: `id`
   315|
   316|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/merchant/MerchantExtras.xml
   317|- namespace: `com.rrsjk.migration.merchant.dao.MerchantExtrasDao`
   318|- statements: `insert:create`, `update:update`, `select:get`, `select:getByMerchantId`
   319|- tables: `id`
   320|
   321|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/merchant/CorporateClient.xml
   322|- namespace: `com.rrsjk.migration.merchant.dao.CorporateClientDao`
   323|- statements: `insert:create`, `update:update`, `select:get`, `select:getByMerchantId`
   324|- tables: `id`
   325|
   326|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/merchant/Shop.xml
   327|- namespace: `com.rrsjk.migration.merchant.dao.ShopDao`
   328|- statements: `insert:create`, `update:update`, `select:get`, `select:getByLnShopId`, `select:findAll`
   329|- tables: `id`
   330|
   331|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/rrs/RrsShopExtra.xml
   332|- namespace: `com.rrsjk.migration.rrs.dao.RrsShopExtraDao`
   333|- statements: `select:findByShopId`
   334|
   335|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/rrs/RrsShop.xml
   336|- namespace: `com.rrsjk.migration.rrs.dao.RrsShopDao`
   337|- statements: `select:batchGet`, `select:getById`
   338|
   339|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/portal/BusinessFee.xml
   340|- namespace: `com.rrsjk.migration.portal.dao.BusinessFeeDao`
   341|- statements: `select:getByApplyId`
   342|
   343|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/portal/BusinessContract.xml
   344|- namespace: `com.rrsjk.migration.portal.dao.BusinessContractDao`
   345|- statements: `select:getByApplyId`
   346|
   347|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/portal/BusinessApply.xml
   348|- namespace: `com.rrsjk.migration.portal.dao.BusinessApplyDao`
   349|- statements: `insert:insert`, `update:update`, `update:updateForce`, `select:getById`, `select:findProfessional`
   350|- tables: `id`
   351|
   352|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/system/SystemSysUser.xml
   353|- namespace: `com.rrsjk.migration.system.dao.SystemSysUserDao`
   354|- statements: `select:getPasswordByLoginId`, `select:listInfo`
   355|- tables: `sys_user`
   356|
   357|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/SaleChannel.xml
   358|- namespace: `com.rrsjk.migration.item.dao.SaleChannelDao`
   359|- statements: `select:get`, `select:findBy`
   360|
   361|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/Spu.xml
   362|- namespace: `com.rrsjk.migration.item.dao.SpuDao`
   363|- statements: `insert:create`, `update:update`, `select:getById`, `select:getMaxSpuId`
   364|- tables: `id`
   365|
   366|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/ItemImage.xml
   367|- namespace: `com.rrsjk.migration.item.dao.ItemImageDao`
   368|- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:get`, `select:findByItemId`
   369|- tables: `id`
   370|
   371|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/ItemSaleChannel.xml
   372|- namespace: `com.rrsjk.migration.item.dao.ItemSaleChannelDao`
   373|- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:get`, `select:findByItemId`, `delete:deleteByItemId`
   374|- tables: `id`
   375|
   376|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/ProductPrice.xml
   377|- namespace: `com.rrsjk.migration.item.dao.ProductPriceDao`
   378|- statements: `insert:create`, `update:update`, `select:getBySkuAndPurchaseType`, `select:getCheckedBySkuAndPurchaseType`
   379|- tables: `id`
   380|
   381|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/ShopSpuPlateformRate.xml
   382|- namespace: `com.rrsjk.migration.item.dao.ShopSpuPlateformRateDao`
   383|- statements: `insert:create`, `update:update`, `select:get`, `select:getByShopIdAndSpuId`
   384|- tables: `id`
   385|
   386|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/ProductBreakevenPrice.xml
   387|- namespace: `com.rrsjk.migration.item.dao.ProductBreakevenPriceDao`
   388|- statements: `insert:create`, `update:update`, `select:getBySkuCode`
   389|- tables: `id`
   390|
   391|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/CategoryAttributeValue.xml
   392|- namespace: `com.rrsjk.migration.item.dao.CategoryAttributeValueDao`
   393|- statements: `insert:create`, `update:update`, `select:get`, `select:find`, `select:findByAttributeId`, `update:delCateAttrValByCateId`
   394|- tables: `id`
   395|
   396|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/Item.xml
   397|- namespace: `com.rrsjk.migration.item.dao.ItemDao`
   398|- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:get`, `select:batchGet`, `select:getMaxProductId`
   399|- tables: `id`
   400|
   401|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/Brand.xml
   402|- namespace: `com.rrsjk.migration.item.dao.BrandDao`
   403|- statements: `select:getByBrandName`, `select:findAllBrand`
   404|
   405|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/CategoryAttribute.xml
   406|- namespace: `com.rrsjk.migration.item.dao.CategoryAttributeDao`
   407|- statements: `select:get`, `select:findByCategoryId`
   408|
   409|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/Comment.xml
   410|- namespace: `com.rrsjk.migration.item.dao.CommentDao`
   411|- statements: `insert:create`, `update:update`, `select:get`, `select:getByParams`
   412|- tables: `id`
   413|
   414|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/SpuAttributeValue.xml
   415|- namespace: `com.rrsjk.migration.item.dao.SpuAttributeValueDao`
   416|- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:get`, `select:findBy`
   417|- tables: `id`
   418|
   419|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/ItemExtras.xml
   420|- namespace: `com.rrsjk.migration.item.dao.ItemExtrasDao`
   421|- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:get`, `select:getByItemId`
   422|- tables: `id`
   423|
   424|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/ProductData.xml
   425|- namespace: `com.rrsjk.migration.item.dao.ProductDataDao`
   426|- statements: `insert:create`, `update:update`, `select:getBySkuCode`
   427|- tables: `id`
   428|
   429|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/ProductPurchaseCost.xml
   430|- namespace: `com.rrsjk.migration.item.dao.ProductPurchaseCostDao`
   431|- statements: `insert:create`, `update:update`, `select:getBySkuCodeAndEffectTime`
   432|- tables: `id`
   433|
   434|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/Sku.xml
   435|- namespace: `com.rrsjk.migration.item.dao.SkuDao`
   436|- statements: `insert:create`, `insert:batchInsert`, `update:update`, `select:get`, `select:getByItemId`
   437|- tables: `id`
   438|
   439|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/item/CommentImage.xml
   440|- namespace: `com.rrsjk.migration.item.dao.CommentImageDao`
   441|- statements: `insert:create`, `insert:batchInsert`, `select:findByCommentId`, `delete:delete`
   442|
   443|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/ln/ProductOrderAppraiseImgs.xml
   444|- namespace: `com.rrsjk.migration.ln.dao.ProductOrderAppraiseImgsDao`
   445|- statements: `select:findBy`
   446|
   447|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/ln/ProductImgs.xml
   448|- namespace: `com.rrsjk.migration.ln.dao.ProductImgsDao`
   449|- statements: `select:findBy`, `select:getById`
   450|
   451|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/ln/LnProduct.xml
   452|- namespace: `com.rrsjk.migration.ln.dao.LnProductDao`
   453|- statements: `select:findBy`, `select:getBrandId`
   454|
   455|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/ln/ReceiveAddress.xml
   456|- namespace: `com.rrsjk.migration.ln.dao.ReceiveAddressDao`
   457|- statements: `select:findBy`
   458|
   459|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/ln/SalesOrganization.xml
   460|- namespace: `com.rrsjk.migration.ln.dao.SalesOrganizationDao`
   461|- statements: `select:batchGet`, `select:getBySoId`
   462|
   463|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/ln/ProductCategory.xml
   464|- namespace: `com.rrsjk.migration.ln.dao.ProductCategoryDao`
   465|- statements: `select:findBy`, `select:getByPcId`
   466|
   467|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/ln/SysUser.xml
   468|- namespace: `com.rrsjk.migration.ln.dao.SysUserDao`
   469|- statements: `select:getBySalesOrganizationId`
   470|
   471|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/ln/Mdm.xml
   472|- namespace: `com.rrsjk.migration.ln.dao.MdmDao`
   473|- statements: `select:listMdm`
   474|
   475|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/ln/ProductStock.xml
   476|- namespace: `com.rrsjk.migration.ln.dao.ProductStockDao`
   477|- statements: `select:findBy`, `select:getById`
   478|
   479|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/ln/ProductBrand.xml
   480|- namespace: `com.rrsjk.migration.ln.dao.ProductBrandDao`
   481|- statements: `select:findBy`, `select:getById`
   482|
   483|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/ln/ProductCategoryCommission.xml
   484|- namespace: `com.rrsjk.migration.ln.dao.ProductCategoryCommissionDao`
   485|- statements: `select:findBy`, `select:getByPccId`
   486|
   487|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/ln/ProductUnit.xml
   488|- namespace: `com.rrsjk.migration.ln.dao.ProductUnitDao`
   489|- statements: `select:findBy`, `select:getById`
   490|
   491|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/ln/ProductOrderAppraise.xml
   492|- namespace: `com.rrsjk.migration.ln.dao.ProductOrderAppraiseDao`
   493|- statements: `select:batchGet`, `select:getOrderNoByOrderId`
   494|- tables: `product_order`
   495|
   496|## rrsjk-migration-mix/rrsjk-migration-mix-impl/src/main/resources/mybatis/mapper/member/LoginInfo.xml
   497|- namespace: `com.rrsjk.migration.member.dao.LoginInfoDao`
   498|- statements: `insert:create`, `select:getByLoginId`, `select:getMemberLoginInfos`, `update:changePassword`
   499|- tables: `id`
   500|
   501|

### 合同相关 Mapper
- `LightStationContractRecord.xml` - 合同记录查询/更新 (rrsjk-light-service)
- `LightStationContractRecordLog.xml` - 合同操作日志 (rrsjk-light-service)
- `LightStationContractInfo.xml` - 合同信息详情 (rrsjk-light-service)
- `LightElecContract.xml` - 电费合同 (rrsjk-light-service)
- `LightElecSealUse.xml` - 用印记录 (rrsjk-light-service)
