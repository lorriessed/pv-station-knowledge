     1|# Controller/API 索引
     2|
     3|来源: master 代码静态扫描。
     4|
     5|## ShopController
     6|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/shop/ShopController.java`
     7|- @RequestMapping("/shop")
     8|- @GetMapping("/{shop_id}/get.do")
     9|- @GetMapping("/listShopCarousel.do")
    10|- @GetMapping("/{shop_id}/getDetail.do")
    11|
    12|## ShopProductController
    13|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/shop/ShopProductController.java`
    14|- @RequestMapping("/shop")
    15|- @GetMapping("/{shop_id}/product/get.do")
    16|
    17|## YzzShopController
    18|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/shop/YzzShopController.java`
    19|- @RequestMapping("/yzz")
    20|- @GetMapping("/getByLatLnt.do")
    21|- @GetMapping("/getYzzGuideByShopId.do")
    22|- @GetMapping("/getYzzGuide.do")
    23|- @GetMapping("/getYzzShop.do")
    24|- @GetMapping("/getYzzQrCode.do")
    25|- @GetMapping("/getYzzOptItem.do")
    26|- @GetMapping("/getYzzShopMember.do")
    27|
    28|## PosthouseController
    29|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/shop/PosthouseController.java`
    30|- @RequestMapping("/posthouse")
    31|- @GetMapping("/getByAddress.do")
    32|- @GetMapping("/getDetail.do")
    33|- @PostMapping("/applyPosthouse.do")
    34|- @PostMapping("/updatePosthouse.do")
    35|- @GetMapping("/getPosthouseAdDesc.do")
    36|- @GetMapping("/getPosthouse.do")
    37|
    38|## CartController
    39|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/cart/CartController.java`
    40|- @RequestMapping("/cart")
    41|- @GetMapping("/get.do")
    42|- @PostMapping("/addToCart.do")
    43|- @GetMapping("/validStock.do")
    44|- @PostMapping("/modifyNumber.do")
    45|- @PostMapping("/clearCart.do")
    46|- @GetMapping("/getCartItemNumber.do")
    47|- @PostMapping("/clearCartByChannelType.do")
    48|
    49|## CouponController
    50|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/coupon/CouponController.java`
    51|- @RequestMapping("/coupon")
    52|- @PostMapping("/claimCoupon.do")
    53|- @GetMapping("/show/listCoupon.do")
    54|- @GetMapping("/getEnableCoupon.do")
    55|- /*@GetMapping("/getAvailableClaimCoupon.do")
    56|- @GetMapping("/show/listItemCoupon.do")
    57|- @GetMapping("/getOwnerCoupon.do")
    58|- @GetMapping("/show/listShopCoupon.do")
    59|- @GetMapping("/getOwnerCouponSum.do")
    60|- @GetMapping("/show/checkExist.do")
    61|- @GetMapping("/getYzzOwnerCoupon.do")
    62|
    63|## EnergyIntroduceController
    64|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/energy/EnergyIntroduceController.java`
    65|- @RequestMapping("/energyIntroduce")
    66|- @GetMapping("/getIntroduceVideo.do")
    67|
    68|## FeeStandardController
    69|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/energy/FeeStandardController.java`
    70|- @RequestMapping("/feeStandard")
    71|- @GetMapping("/getStandardPic.do")
    72|
    73|## PhotovoltaicController
    74|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/photovoltaic/PhotovoltaicController.java`
    75|- @RequestMapping("/photovoltaic")
    76|- @PostMapping("saveOrUpdate.do")
    77|- @GetMapping("statusCountByMember.do")
    78|- @GetMapping("/detail.do")
    79|- @GetMapping("listByMember.do")
    80|
    81|## LjcpController
    82|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/ljcp/LjcpController.java`
    83|- @RequestMapping("/ljcp")
    84|- @GetMapping("/homePage.do")
    85|- @GetMapping("/listCategory.do")
    86|
    87|## OrderCreateController
    88|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/order/OrderCreateController.java`
    89|- @RequestMapping("/order")
    90|- @PostMapping("create.do")
    91|
    92|## OrderPosthouseController
    93|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/order/OrderPosthouseController.java`
    94|- @RequestMapping("/order")
    95|- @GetMapping("posthouseOrderItemList.do")
    96|- @PostMapping("/pickFinishAll.do")
    97|- @PostMapping("pickFinishOrderItem.do")
    98|- @PostMapping("batchPickFinishOrderItem.do")
    99|- @GetMapping("/groupConsignee.do")
   100|- @PostMapping("batchSmsZiti.do")
   101|- @PostMapping("/smsZitiAll.do")
   102|- @GetMapping("/countOrderItemGroup.do")
   103|- @PostMapping("batchGroupApplyRefund.do")
   104|
   105|## OrderController
   106|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/order/OrderController.java`
   107|- @RequestMapping("/order")
   108|- @GetMapping("orderList.do")
   109|- @GetMapping("/orderDetail.do")
   110|- @PostMapping("cancelOrder.do")
   111|
   112|## OrderSettleController
   113|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/order/OrderSettleController.java`
   114|- @RequestMapping("/order")
   115|- @GetMapping("getOrderCartBySettle.do")
   116|
   117|## OrderItemController
   118|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/order/OrderItemController.java`
   119|- @RequestMapping("/order")
   120|- @GetMapping("orderItemList.do")
   121|- @GetMapping("orderItemCount.do")
   122|- @GetMapping("/orderItemDetail.do")
   123|- @GetMapping("/findExpressRecord.do")
   124|- @PostMapping("cancelOrderItem.do")
   125|- @PostMapping("finishOrderItem.do")
   126|- @PostMapping("applyRefundOrderItem.do")
   127|- @PostMapping("cancelRefundOrderItem.do")
   128|- @GetMapping("/countOrderCommission.do")
   129|- @PostMapping("delaySignDay.do")
   130|
   131|## ActivityController
   132|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/activity/ActivityController.java`
   133|- @RequestMapping("/activity")
   134|- @GetMapping("/getPrize.do")
   135|- @PostMapping("/claimCoupon.do")
   136|- @GetMapping("getActivityFlag.do")
   137|- @PostMapping("/lottory.do")
   138|- @PostMapping("/addLottoryTimes.do")
   139|- @GetMapping("/getLottoryRecord.do")
   140|- @PostMapping("/saveLottoryRecord.do")
   141|- @GetMapping("/getSignInRecord.do")
   142|- @PostMapping("/signIn.do")
   143|- @GetMapping("/findLottoryRecord.do")
   144|- @GetMapping("/findActivityPicture.do")
   145|- @GetMapping("/getSignTimes.do")
   146|- @GetMapping("/checkSnatch.do")
   147|- @PostMapping("/snatchRedEnvelopes.do")
   148|- @PostMapping("/getPointsForSignIn.do")
   149|
   150|## SolitaireController
   151|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/activity/SolitaireController.java`
   152|- @RequestMapping("/solitaire")
   153|- @GetMapping("/listSolitaire.do")
   154|- @PostMapping("/saveSolitaire.do")
   155|- @PostMapping("/updateSolitaire.do")
   156|- @GetMapping("/solitaireItemTotal.do")
   157|- @GetMapping("/listSolitaireItem.do")
   158|- @GetMapping("/solitaireView.do")
   159|- @GetMapping("/mySolitaireOrderList.do")
   160|- @GetMapping("/listSolitaireOrder.do")
   161|- @PostMapping("/addOrderItem.do")
   162|- @PostMapping("/deleteOrderItem.do")
   163|- @GetMapping("/mySolitaireOrder.do")
   164|- @PostMapping("/receiveItem.do")
   165|
   166|## AppDownloadStatisticController
   167|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/activity/AppDownloadStatisticController.java`
   168|- @RequestMapping("/activity")
   169|- @GetMapping("/app_download_stats.do")
   170|
   171|## QuestionnaireController
   172|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/activity/QuestionnaireController.java`
   173|- @RequestMapping("/dcwj")
   174|- @PostMapping("/save.do")
   175|
   176|## ProjectInvestmentIncomeController
   177|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/businessforecast/ProjectInvestmentIncomeController.java`
   178|- @RequestMapping("/businessForecast/investmentIncome")
   179|- @PostMapping("/calculate")
   180|
   181|## ProjectCostInfoDetailController
   182|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/businessforecast/ProjectCostInfoDetailController.java`
   183|- @RequestMapping("/businessForecast/costInfo")
   184|- @PostMapping("/createOrUpdateInfo")
   185|
   186|## ElectricityGenerationDetailController
   187|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/businessforecast/ElectricityGenerationDetailController.java`
   188|- @RequestMapping("/businessForecast/electricityGeneration")
   189|- @GetMapping("/calculate")
   190|
   191|## ForecastProjectDetailController
   192|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/businessforecast/ForecastProjectDetailController.java`
   193|- @RequestMapping("/businessForecast/projectDetail")
   194|- @GetMapping("/doList")
   195|- @GetMapping("/getDetailByProjectCode")
   196|- @PostMapping("/createOrUpdateProject")
   197|- @GetMapping("/createBusinessPlan")
   198|
   199|## BaseElectricityPriceController
   200|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/businessforecast/base/BaseElectricityPriceController.java`
   201|- @RequestMapping("/businessForecast/price")
   202|- @GetMapping("/businessElectricityPrice")
   203|- @GetMapping("/businessElectricityDiffPeriodPrice")
   204|- @GetMapping("/electricityPriceByCoal")
   205|
   206|## EmissionReduceController
   207|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/businessforecast/base/EmissionReduceController.java`
   208|- @RequestMapping("/businessForecast/emission")
   209|- @GetMapping("/reduce")
   210|
   211|## CookbookController
   212|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/cook/CookbookController.java`
   213|- @RequestMapping("/cook")
   214|- @PostMapping("/getCookbookByCategory.do")
   215|- @PostMapping("/insert.do")
   216|- @PostMapping("/update.do")
   217|- @PostMapping("/getCookDayByCategory.do")
   218|
   219|## TokenController
   220|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/global/TokenController.java`
   221|- @RequestMapping("/global")
   222|- @GetMapping("/token.do")
   223|
   224|## AppApiImageController
   225|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/appImg/AppApiImageController.java`
   226|- @RequestMapping("/appImg/")
   227|- @GetMapping("/findImage")
   228|
   229|## LightStationEvaluationController
   230|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/evaluate/LightStationEvaluationController.java`
   231|- @RequestMapping("/evaluation")
   232|- @GetMapping("/getToBeEvaluatedStation.do")
   233|- @PostMapping("/addEvaluation")
   234|
   235|## ItemSearchController
   236|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/item/ItemSearchController.java`
   237|- @RequestMapping("/item/search/")
   238|- @GetMapping("/homePageSearch.do")
   239|- @GetMapping("/favorateSearch.do")
   240|- @GetMapping("/categorySearch.do")
   241|- @GetMapping("/filterItemSearch.do")
   242|- @GetMapping("/purchaseSearch.do")
   243|- @GetMapping("/customDrinks.do")
   244|- @GetMapping("/listCategoryItem.do")
   245|
   246|## CommentController
   247|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/item/CommentController.java`
   248|- @RequestMapping("/comment")
   249|- @PostMapping("/saveComment.do")
   250|- @PostMapping("/saveAdditionalComment.do")
   251|- @PostMapping("/show/listComment.do")
   252|- @GetMapping("/show/getCommentCount.do")
   253|
   254|## ItemDetailController
   255|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/item/ItemDetailController.java`
   256|- @RequestMapping("/item")
   257|- @GetMapping("/{item_id}/get.do")
   258|- @GetMapping("/{item_id}/getDetail.do")
   259|- @GetMapping("/chunengList.do")
   260|- @GetMapping("/{item_id}/geInstructions.do")
   261|
   262|## YzzItemSearchController
   263|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/item/YzzItemSearchController.java`
   264|- @RequestMapping("/item/search/")
   265|- @GetMapping("/yzzCategorySearch.do")
   266|- @GetMapping("/yzzItemSearch.do")
   267|
   268|## CustomDrinksController
   269|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/item/CustomDrinksController.java`
   270|- @RequestMapping("/item/custom/")
   271|- @GetMapping("/customDrinksList.do")
   272|- @PostMapping("/addCustomDrinks.do")
   273|- @PostMapping("/updateCustomDrinks.do")
   274|- @GetMapping("/editCustomDrinks.do")
   275|- @PostMapping("/cancelCustomDrinks.do")
   276|- @GetMapping("/customDrinksSearch.do")
   277|- @GetMapping("/getByCode.do")
   278|
   279|## ItemDetailPreviewController
   280|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/item/ItemDetailPreviewController.java`
   281|- @RequestMapping("/item/preview")
   282|- @GetMapping("/{item_id}/get.do")
   283|- @GetMapping("/{item_id}/getDetail.do")
   284|
   285|## FrontCategoryController
   286|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/item/FrontCategoryController.java`
   287|- @RequestMapping("/category")
   288|- @GetMapping("/listFrontCategory.do")
   289|- @GetMapping("/listFrontCategoryCarousel.do")
   290|
   291|## ConsultationDetailController
   292|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/energyStorage/ConsultationDetailController.java`
   293|- @RequestMapping("/ConsultationDetail/")
   294|- @PostMapping("add.do")
   295|
   296|## InstallMaintenanceInfoController
   297|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/energyStorage/InstallMaintenanceInfoController.java`
   298|- @RequestMapping("/InstallMaintenanceInfo/")
   299|- @GetMapping("/find.do")
   300|- @GetMapping("/findById.do")
   301|- @PostMapping("add.do")
   302|- @PostMapping("edit.do")
   303|- @GetMapping("/findModel.do")
   304|- @PostMapping("uploadVideo.do")
   305|
   306|## OssController
   307|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/oss/OssController.java`
   308|- @RequestMapping("/oss")
   309|- @RequestMapping("getUploadInfo")
   310|
   311|## CnIncomeCalcInfoController
   312|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/energystorage/CnIncomeCalcInfoController.java`
   313|- @RequestMapping("/energystorage/incomeCalc")
   314|- @PostMapping("/submit.do")
   315|- @PostMapping("/checkNeedCount.do")
   316|- @GetMapping("findTemp.do")
   317|- @GetMapping("findById.do")
   318|- @GetMapping("qualification.do")
   319|- @GetMapping("/regionList.do")
   320|
   321|## CnDataDictController
   322|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/energystorage/CnDataDictController.java`
   323|- @RequestMapping("/energystorage/datadict")
   324|- @GetMapping("getDictsByType.do")
   325|
   326|## LightCoinController
   327|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/LightCoinController.java`
   328|- @RequestMapping("/lightCoin")
   329|- @GetMapping("/coinDetail.do")
   330|- @GetMapping("coinStationList.do")
   331|- @GetMapping("findLightCoinRecord.do")
   332|
   333|## LightVisitController
   334|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/LightVisitController.java`
   335|- @RequestMapping("/lightVisit")
   336|- @PostMapping("/saveVisitInfo.do")
   337|
   338|## LightRoadWorkController
   339|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/LightRoadWorkController.java`
   340|- @RequestMapping("/roadWork/")
   341|- @GetMapping("findProjectList.do")
   342|- @PostMapping("/confirmAccept.do")
   343|- @GetMapping("/getProjectDetail.do")
   344|- @PostMapping("/startWork.do")
   345|- @GetMapping("/getTodoTaskSum.do")
   346|- @PostMapping("/uploadCompleteImg.do")
   347|- @PostMapping("imagePredict")
   348|- @PostMapping("imageQueryOCR")
   349|- @PostMapping("uploadModuleSn")
   350|- @PostMapping("setModuleSnCache")
   351|- @GetMapping("queryModuleSnLog")
   352|- @GetMapping("queryByNameAndStationCode")
   353|- @PostMapping("/changeCompleteImg.do")
   354|- @GetMapping("/findPlanConfigList.do")
   355|- @PostMapping("/submitRoadWorkInfo.do")
   356|- @GetMapping("/getCompleteImg.do")
   357|- @GetMapping("/getWorkOrderDetail.do")
   358|- @GetMapping("/getStatusSum.do")
   359|
   360|## LightStationNannyController
   361|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/LightStationNannyController.java`
   362|- @RequestMapping("/lightStationNanny/")
   363|- @PostMapping("regist")
   364|- @PostMapping("sendSms")
   365|- @GetMapping("getServiceProvider")
   366|- @GetMapping("examine.do")
   367|
   368|## LightGreenEnergyController
   369|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/LightGreenEnergyController.java`
   370|- @RequestMapping("/LightGreenEnergy/")
   371|- @PostMapping("doList.do")
   372|- @PostMapping("total")
   373|
   374|## LightForwardController
   375|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/LightForwardController.java`
   376|- @RequestMapping("/forward/")
   377|- @PostMapping("/forwardStation.do")
   378|- @PostMapping("/calculateIncomr.do")
   379|
   380|## LightUniqueImageController
   381|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/LightUniqueImageController.java`
   382|- @RequestMapping("/light/imageVerify/")
   383|- @PostMapping("save")
   384|- @PostMapping("verify")
   385|
   386|## LightCommodityController
   387|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/LightCommodityController.java`
   388|- @RequestMapping("/lightCommodity/")
   389|- @GetMapping("product")
   390|
   391|## LightStationYuexiuAccountController
   392|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/LightStationYuexiuAccountController.java`
   393|- @RequestMapping("/yuexiu/account/")
   394|- @GetMapping("queryStatus.do")
   395|- @PostMapping("open.do")
   396|
   397|## LightStationInfoUpdateController
   398|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/LightStationInfoUpdateController.java`
   399|- @RequestMapping("/stationInfoUpdate/")
   400|- @GetMapping("/checkBankChangeHistory.do")
   401|- @GetMapping("/getUserStations.do")
   402|- @GetMapping("/getBankChangeList.do")
   403|- @PostMapping("/createBankChange.do")
   404|- @GetMapping("/getStationDetailForUpdate.do")
   405|- @GetMapping("/getDetail.do")
   406|- @PostMapping("/update.do")
   407|- @PostMapping("/delete.do")
   408|- @GetMapping("/searchBankChanges.do")
   409|
   410|## LightBenefitConversionController
   411|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/LightBenefitConversionController.java`
   412|- @RequestMapping("/lightBenefitConversion/")
   413|- @GetMapping("doList.do")
   414|- @GetMapping("getRule")
   415|- @PostMapping("exchange")
   416|- @GetMapping("getMemberRole")
   417|
   418|## LightCaseController
   419|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/LightCaseController.java`
   420|- @RequestMapping("/lightCase/")
   421|- @GetMapping("/findCase.do")
   422|- @GetMapping("/findById.do")
   423|- @GetMapping("/getAll.do")
   424|- @PostMapping("/likes.do")
   425|
   426|## LightStationNannyUserController
   427|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/LightStationNannyUserController.java`
   428|- @RequestMapping("/lightStationNannyUser/")
   429|- @PostMapping("saveOrUpdate")
   430|- @GetMapping("detail")
   431|- @GetMapping("list.do")
   432|- @PostMapping("delete")
   433|
   434|## HhDoctorController
   435|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/HhDoctorController.java`
   436|- @RequestMapping("/hhDoctor/")
   437|- @GetMapping("/qualification.do")
   438|- @GetMapping("/registerAndActivate.do")
   439|- @GetMapping("/isActivate.do")
   440|- @PostMapping("/codeRegisterAndActivate.do")
   441|
   442|## LightStationController
   443|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/LightStationController.java`
   444|- @RequestMapping("/station/")
   445|- @GetMapping("/stationList.do")
   446|- @GetMapping("/getStationDetail.do")
   447|- @GetMapping("/getStationAccount.do")
   448|- @GetMapping("/findElectricOrder.do")
   449|- @GetMapping("/findRentRecord.do")
   450|- @GetMapping("/yxAccountBill.do")
   451|- @GetMapping("/ylAccountBill.do")
   452|- @GetMapping("/ylRentList.do")
   453|- @GetMapping("/getMiniProgramTemplateByModeAndHouseType.do")
   454|
   455|## GhSecondClassAccountController
   456|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/gh/GhSecondClassAccountController.java`
   457|- @RequestMapping("/gh/account")
   458|- @GetMapping("/findAccountInfo")
   459|- @GetMapping("/findCompanyInfo")
   460|- @GetMapping("/getById")
   461|- @GetMapping("/openAccountH5")
   462|
   463|## DhSecondClassAccountController
   464|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/dh/DhSecondClassAccountController.java`
   465|- @RequestMapping("/dh/secondAccount")
   466|- @GetMapping("/doList")
   467|- @GetMapping("/getById")
   468|- @GetMapping("/openAccount")
   469|- @GetMapping("/queryOpenAccount")
   470|
   471|## HhOrderController
   472|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/hhmedic/HhOrderController.java`
   473|- @RequestMapping("/hhmedic")
   474|- @PostMapping("updateInfo.do")
   475|- @GetMapping("getStatus.do")
   476|- @GetMapping("getInfo.do")
   477|- @PostMapping("activeCard.do")
   478|- @GetMapping("getOrRegister.do")
   479|- @GetMapping("getActivateCode.do")
   480|- @PostMapping("addFamilyMember.do")
   481|- @PostMapping("updateFamilyMember.do")
   482|- @GetMapping("getFamily.do")
   483|
   484|## CardController
   485|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/rank/CardController.java`
   486|- @RequestMapping("/rank/card")
   487|- @GetMapping("getList.do")
   488|- @PostMapping("active.do")
   489|- @PostMapping("donate.do")
   490|- @PostMapping("activeEntityCard.do")
   491|- @GetMapping("/getCardChannel.do")
   492|
   493|## BenefitConsumerController
   494|- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/rank/BenefitConsumerController.java`
   495|- @RequestMapping("/rank/benefitConsumer")
   496|- @PostMapping("consumer.do")
   497|- @PostMapping("batchConsumer.do")
   498|- @PostMapping("receiveGoods.do")
   499|
   500|## BenefitPackageController
   501|

### 合同相关 Controller
- `LightStationContractInfoController` (rrsjk-merchant-web) - 合同信息查询
  - `findNewOne.do` - 查询最新合同记录
- `LightOpContractRecordController` (rrsjk-hds-web) - 运维合同记录
- `SocializationContractInfoController` (rrsjk-hds-web) - 社会化合同信息
