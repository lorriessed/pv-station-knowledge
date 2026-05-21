# Controller/API 索引

来源: master 代码静态扫描。

## ScanOrderController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/watercontrol/ScanOrderController.java`
- @RequestMapping("/watercontrol")
- @GetMapping("/machineDetail.do")
- @PostMapping("scanOrder.do")

## ShopController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/shop/ShopController.java`
- @RequestMapping("/shop")
- @GetMapping("/{shop_id}/get.do")
- @GetMapping("/listShopCarousel.do")
- @GetMapping("/{shop_id}/getDetail.do")

## ShopProductController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/shop/ShopProductController.java`
- @RequestMapping("/shop")
- @GetMapping("/{shop_id}/product/get.do")

## YzzShopController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/shop/YzzShopController.java`
- @RequestMapping("/yzz")
- @GetMapping("/getByLatLnt.do")
- @GetMapping("/getYzzGuideByShopId.do")
- @GetMapping("/getYzzGuide.do")
- @GetMapping("/getYzzShop.do")
- @GetMapping("/getYzzQrCode.do")
- @GetMapping("/getYzzOptItem.do")
- @GetMapping("/getYzzShopMember.do")

## PosthouseController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/shop/PosthouseController.java`
- @RequestMapping("/posthouse")
- @GetMapping("/getByAddress.do")
- @GetMapping("/getDetail.do")
- @PostMapping("/applyPosthouse.do")
- @PostMapping("/updatePosthouse.do")
- @GetMapping("/getPosthouseAdDesc.do")
- @GetMapping("/getPosthouse.do")

## CartController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/cart/CartController.java`
- @RequestMapping("/cart")
- @GetMapping("/get.do")
- @PostMapping("/addToCart.do")
- @GetMapping("/validStock.do")
- @PostMapping("/modifyNumber.do")
- @PostMapping("/clearCart.do")
- @GetMapping("/getCartItemNumber.do")
- @PostMapping("/clearCartByChannelType.do")

## CouponController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/coupon/CouponController.java`
- @RequestMapping("/coupon")
- @PostMapping("/claimCoupon.do")
- @GetMapping("/show/listCoupon.do")
- @GetMapping("/getEnableCoupon.do")
- /*@GetMapping("/getAvailableClaimCoupon.do")
- @GetMapping("/show/listItemCoupon.do")
- @GetMapping("/getOwnerCoupon.do")
- @GetMapping("/show/listShopCoupon.do")
- @GetMapping("/getOwnerCouponSum.do")
- @GetMapping("/show/checkExist.do")
- @GetMapping("/getYzzOwnerCoupon.do")

## EnergyIntroduceController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/energy/EnergyIntroduceController.java`
- @RequestMapping("/energyIntroduce")
- @GetMapping("/getIntroduceVideo.do")

## FeeStandardController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/energy/FeeStandardController.java`
- @RequestMapping("/feeStandard")
- @GetMapping("/getStandardPic.do")

## PhotovoltaicController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/photovoltaic/PhotovoltaicController.java`
- @RequestMapping("/photovoltaic")
- @PostMapping("saveOrUpdate.do")
- @GetMapping("statusCountByMember.do")
- @GetMapping("/detail.do")
- @GetMapping("listByMember.do")

## LjcpController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/ljcp/LjcpController.java`
- @RequestMapping("/ljcp")
- @GetMapping("/homePage.do")
- @GetMapping("/listCategory.do")

## OrderCreateController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/order/OrderCreateController.java`
- @RequestMapping("/order")
- @PostMapping("create.do")

## OrderPosthouseController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/order/OrderPosthouseController.java`
- @RequestMapping("/order")
- @GetMapping("posthouseOrderItemList.do")
- @PostMapping("/pickFinishAll.do")
- @PostMapping("pickFinishOrderItem.do")
- @PostMapping("batchPickFinishOrderItem.do")
- @GetMapping("/groupConsignee.do")
- @PostMapping("batchSmsZiti.do")
- @PostMapping("/smsZitiAll.do")
- @GetMapping("/countOrderItemGroup.do")
- @PostMapping("batchGroupApplyRefund.do")

## OrderController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/order/OrderController.java`
- @RequestMapping("/order")
- @GetMapping("orderList.do")
- @GetMapping("/orderDetail.do")
- @PostMapping("cancelOrder.do")

## OrderSettleController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/order/OrderSettleController.java`
- @RequestMapping("/order")
- @GetMapping("getOrderCartBySettle.do")

## OrderItemController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/order/OrderItemController.java`
- @RequestMapping("/order")
- @GetMapping("orderItemList.do")
- @GetMapping("orderItemCount.do")
- @GetMapping("/orderItemDetail.do")
- @GetMapping("/findExpressRecord.do")
- @PostMapping("cancelOrderItem.do")
- @PostMapping("finishOrderItem.do")
- @PostMapping("applyRefundOrderItem.do")
- @PostMapping("cancelRefundOrderItem.do")
- @GetMapping("/countOrderCommission.do")
- @PostMapping("delaySignDay.do")

## ActivityController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/activity/ActivityController.java`
- @RequestMapping("/activity")
- @GetMapping("/getPrize.do")
- @PostMapping("/claimCoupon.do")
- @GetMapping("getActivityFlag.do")
- @PostMapping("/lottory.do")
- @PostMapping("/addLottoryTimes.do")
- @GetMapping("/getLottoryRecord.do")
- @PostMapping("/saveLottoryRecord.do")
- @GetMapping("/getSignInRecord.do")
- @PostMapping("/signIn.do")
- @GetMapping("/findLottoryRecord.do")
- @GetMapping("/findActivityPicture.do")
- @GetMapping("/getSignTimes.do")
- @GetMapping("/checkSnatch.do")
- @PostMapping("/snatchRedEnvelopes.do")
- @PostMapping("/getPointsForSignIn.do")

## SolitaireController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/activity/SolitaireController.java`
- @RequestMapping("/solitaire")
- @GetMapping("/listSolitaire.do")
- @PostMapping("/saveSolitaire.do")
- @PostMapping("/updateSolitaire.do")
- @GetMapping("/solitaireItemTotal.do")
- @GetMapping("/listSolitaireItem.do")
- @GetMapping("/solitaireView.do")
- @GetMapping("/mySolitaireOrderList.do")
- @GetMapping("/listSolitaireOrder.do")
- @PostMapping("/addOrderItem.do")
- @PostMapping("/deleteOrderItem.do")
- @GetMapping("/mySolitaireOrder.do")
- @PostMapping("/receiveItem.do")

## AppDownloadStatisticController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/activity/AppDownloadStatisticController.java`
- @RequestMapping("/activity")
- @GetMapping("/app_download_stats.do")

## QuestionnaireController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/activity/QuestionnaireController.java`
- @RequestMapping("/dcwj")
- @PostMapping("/save.do")

## ProjectInvestmentIncomeController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/businessforecast/ProjectInvestmentIncomeController.java`
- @RequestMapping("/businessForecast/investmentIncome")
- @PostMapping("/calculate")

## ProjectCostInfoDetailController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/businessforecast/ProjectCostInfoDetailController.java`
- @RequestMapping("/businessForecast/costInfo")
- @PostMapping("/createOrUpdateInfo")

## ElectricityGenerationDetailController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/businessforecast/ElectricityGenerationDetailController.java`
- @RequestMapping("/businessForecast/electricityGeneration")
- @GetMapping("/calculate")

## ForecastProjectDetailController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/businessforecast/ForecastProjectDetailController.java`
- @RequestMapping("/businessForecast/projectDetail")
- @GetMapping("/doList")
- @GetMapping("/getDetailByProjectCode")
- @PostMapping("/createOrUpdateProject")
- @GetMapping("/createBusinessPlan")

## BaseElectricityPriceController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/businessforecast/base/BaseElectricityPriceController.java`
- @RequestMapping("/businessForecast/price")
- @GetMapping("/businessElectricityPrice")
- @GetMapping("/businessElectricityDiffPeriodPrice")
- @GetMapping("/electricityPriceByCoal")

## EmissionReduceController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/businessforecast/base/EmissionReduceController.java`
- @RequestMapping("/businessForecast/emission")
- @GetMapping("/reduce")

## CookbookController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/cook/CookbookController.java`
- @RequestMapping("/cook")
- @PostMapping("/getCookbookByCategory.do")
- @PostMapping("/insert.do")
- @PostMapping("/update.do")
- @PostMapping("/getCookDayByCategory.do")

## TokenController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/global/TokenController.java`
- @RequestMapping("/global")
- @GetMapping("/token.do")

## AppApiImageController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/appImg/AppApiImageController.java`
- @RequestMapping("/appImg/")
- @GetMapping("/findImage")

## LightStationEvaluationController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/evaluate/LightStationEvaluationController.java`
- @RequestMapping("/evaluation")
- @GetMapping("/getToBeEvaluatedStation.do")
- @PostMapping("/addEvaluation")

## ItemSearchController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/item/ItemSearchController.java`
- @RequestMapping("/item/search/")
- @GetMapping("/homePageSearch.do")
- @GetMapping("/favorateSearch.do")
- @GetMapping("/categorySearch.do")
- @GetMapping("/filterItemSearch.do")
- @GetMapping("/purchaseSearch.do")
- @GetMapping("/customDrinks.do")
- @GetMapping("/listCategoryItem.do")

## CommentController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/item/CommentController.java`
- @RequestMapping("/comment")
- @PostMapping("/saveComment.do")
- @PostMapping("/saveAdditionalComment.do")
- @PostMapping("/show/listComment.do")
- @GetMapping("/show/getCommentCount.do")

## ItemDetailController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/item/ItemDetailController.java`
- @RequestMapping("/item")
- @GetMapping("/{item_id}/get.do")
- @GetMapping("/{item_id}/getDetail.do")
- @GetMapping("/chunengList.do")
- @GetMapping("/{item_id}/geInstructions.do")

## YzzItemSearchController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/item/YzzItemSearchController.java`
- @RequestMapping("/item/search/")
- @GetMapping("/yzzCategorySearch.do")
- @GetMapping("/yzzItemSearch.do")

## CustomDrinksController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/item/CustomDrinksController.java`
- @RequestMapping("/item/custom/")
- @GetMapping("/customDrinksList.do")
- @PostMapping("/addCustomDrinks.do")
- @PostMapping("/updateCustomDrinks.do")
- @GetMapping("/editCustomDrinks.do")
- @PostMapping("/cancelCustomDrinks.do")
- @GetMapping("/customDrinksSearch.do")
- @GetMapping("/getByCode.do")

## ItemDetailPreviewController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/item/ItemDetailPreviewController.java`
- @RequestMapping("/item/preview")
- @GetMapping("/{item_id}/get.do")
- @GetMapping("/{item_id}/getDetail.do")

## FrontCategoryController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/item/FrontCategoryController.java`
- @RequestMapping("/category")
- @GetMapping("/listFrontCategory.do")
- @GetMapping("/listFrontCategoryCarousel.do")

## ConsultationDetailController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/energyStorage/ConsultationDetailController.java`
- @RequestMapping("/ConsultationDetail/")
- @PostMapping("add.do")

## InstallMaintenanceInfoController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/energyStorage/InstallMaintenanceInfoController.java`
- @RequestMapping("/InstallMaintenanceInfo/")
- @GetMapping("/find.do")
- @GetMapping("/findById.do")
- @PostMapping("add.do")
- @PostMapping("edit.do")
- @GetMapping("/findModel.do")
- @PostMapping("uploadVideo.do")

## OssController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/oss/OssController.java`
- @RequestMapping("/oss")
- @RequestMapping("getUploadInfo")

## CnIncomeCalcInfoController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/energystorage/CnIncomeCalcInfoController.java`
- @RequestMapping("/energystorage/incomeCalc")
- @PostMapping("/submit.do")
- @PostMapping("/checkNeedCount.do")
- @GetMapping("findTemp.do")
- @GetMapping("findById.do")
- @GetMapping("qualification.do")
- @GetMapping("/regionList.do")

## CnDataDictController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/energystorage/CnDataDictController.java`
- @RequestMapping("/energystorage/datadict")
- @GetMapping("getDictsByType.do")

## LightCoinController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/LightCoinController.java`
- @RequestMapping("/lightCoin")
- @GetMapping("/coinDetail.do")
- @GetMapping("coinStationList.do")
- @GetMapping("findLightCoinRecord.do")

## LightVisitController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/LightVisitController.java`
- @RequestMapping("/lightVisit")
- @PostMapping("/saveVisitInfo.do")

## LightRoadWorkController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/LightRoadWorkController.java`
- @RequestMapping("/roadWork/")
- @GetMapping("findProjectList.do")
- @PostMapping("/confirmAccept.do")
- @GetMapping("/getProjectDetail.do")
- @PostMapping("/startWork.do")
- @GetMapping("/getTodoTaskSum.do")
- @PostMapping("/uploadCompleteImg.do")
- @PostMapping("imagePredict")
- @PostMapping("imageQueryOCR")
- @PostMapping("uploadModuleSn")
- @PostMapping("setModuleSnCache")
- @GetMapping("queryModuleSnLog")
- @GetMapping("queryByNameAndStationCode")
- @PostMapping("/changeCompleteImg.do")
- @GetMapping("/findPlanConfigList.do")
- @PostMapping("/submitRoadWorkInfo.do")
- @GetMapping("/getCompleteImg.do")
- @GetMapping("/getWorkOrderDetail.do")
- @GetMapping("/getStatusSum.do")

## LightStationNannyController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/LightStationNannyController.java`
- @RequestMapping("/lightStationNanny/")
- @PostMapping("regist")
- @PostMapping("sendSms")
- @GetMapping("getServiceProvider")
- @GetMapping("examine.do")

## LightGreenEnergyController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/LightGreenEnergyController.java`
- @RequestMapping("/LightGreenEnergy/")
- @PostMapping("doList.do")
- @PostMapping("total")

## LightForwardController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/LightForwardController.java`
- @RequestMapping("/forward/")
- @PostMapping("/forwardStation.do")
- @PostMapping("/calculateIncomr.do")

## IcbcSecondClassAccountController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/IcbcSecondClassAccountController.java`
- //@RequestMapping("/icbc/account")
- //    @GetMapping("/findAccountInfo")
- //    @GetMapping("/findCompanyInfo")
- //    @PostMapping("updateAccountInfo")
- //    @PostMapping("/realTimeImgUpload")
- //    @PostMapping("/openAccount")
- //    @PostMapping("/smsCodeVerifyForOpen")
- //    @PostMapping("/sendSmsCode")
- //    @GetMapping("/queryAccountStatus")
- //    @GetMapping("/obtainEntrustedAgreementCode")
- //    @GetMapping("/signEntrustedAgreement")
- //    @PostMapping("/accountOpen/notify")
- //    @PostMapping("/withdraw/notify")
- //    @PostMapping("/recharge")

## LightUniqueImageController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/LightUniqueImageController.java`
- @RequestMapping("/light/imageVerify/")
- @PostMapping("save")
- @PostMapping("verify")

## LightCommodityController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/LightCommodityController.java`
- @RequestMapping("/lightCommodity/")
- @GetMapping("product")

## LightStationYuexiuAccountController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/LightStationYuexiuAccountController.java`
- @RequestMapping("/yuexiu/account/")
- @GetMapping("queryStatus.do")
- @PostMapping("open.do")

## LightStationInfoUpdateController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/LightStationInfoUpdateController.java`
- @RequestMapping("/stationInfoUpdate/")
- @GetMapping("/checkBankChangeHistory.do")
- @GetMapping("/getUserStations.do")
- @GetMapping("/getBankChangeList.do")
- @PostMapping("/createBankChange.do")
- @GetMapping("/getStationDetailForUpdate.do")
- @GetMapping("/getDetail.do")
- @PostMapping("/update.do")
- @PostMapping("/delete.do")
- @GetMapping("/searchBankChanges.do")

## LightBenefitConversionController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/LightBenefitConversionController.java`
- @RequestMapping("/lightBenefitConversion/")
- @GetMapping("doList.do")
- @GetMapping("getRule")
- @PostMapping("exchange")
- @GetMapping("getMemberRole")

## LightCaseController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/LightCaseController.java`
- @RequestMapping("/lightCase/")
- @GetMapping("/findCase.do")
- @GetMapping("/findById.do")
- @GetMapping("/getAll.do")
- @PostMapping("/likes.do")

## LightStationNannyUserController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/LightStationNannyUserController.java`
- @RequestMapping("/lightStationNannyUser/")
- @PostMapping("saveOrUpdate")
- @GetMapping("detail")
- @GetMapping("list.do")
- @PostMapping("delete")

## HhDoctorController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/HhDoctorController.java`
- @RequestMapping("/hhDoctor/")
- @GetMapping("/qualification.do")
- @GetMapping("/registerAndActivate.do")
- @GetMapping("/isActivate.do")
- @PostMapping("/codeRegisterAndActivate.do")

## LightStationController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/light/LightStationController.java`
- @RequestMapping("/station/")
- @GetMapping("/stationList.do")
- @GetMapping("/getStationDetail.do")
- @GetMapping("/getStationAccount.do")
- @GetMapping("/findElectricOrder.do")
- @GetMapping("/findRentRecord.do")
- @GetMapping("/yxAccountBill.do")
- @GetMapping("/ylAccountBill.do")
- @GetMapping("/ylRentList.do")
- @GetMapping("/getMiniProgramTemplateByModeAndHouseType.do")

## GhSecondClassAccountController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/gh/GhSecondClassAccountController.java`
- @RequestMapping("/gh/account")
- @GetMapping("/findAccountInfo")
- @GetMapping("/findCompanyInfo")
- @GetMapping("/getById")
- @GetMapping("/openAccountH5")

## DhSecondClassAccountController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/dh/DhSecondClassAccountController.java`
- @RequestMapping("/dh/secondAccount")
- @GetMapping("/doList")
- @GetMapping("/getById")
- @GetMapping("/openAccount")
- @GetMapping("/queryOpenAccount")

## HhOrderController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/hhmedic/HhOrderController.java`
- @RequestMapping("/hhmedic")
- @PostMapping("updateInfo.do")
- @GetMapping("getStatus.do")
- @GetMapping("getInfo.do")
- @PostMapping("activeCard.do")
- @GetMapping("getOrRegister.do")
- @GetMapping("getActivateCode.do")
- @PostMapping("addFamilyMember.do")
- @PostMapping("updateFamilyMember.do")
- @GetMapping("getFamily.do")

## GsyAppMemberController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/gsyapp/GsyAppMemberController.java`
- @RequestMapping("/gsyapp/member/")
- @PostMapping("sendRegisterSms.do")
- @PostMapping("register.do")
- @GetMapping("/sendUpdatePasswordSms.do")
- @PostMapping("/updatePassword.do")
- @GetMapping("getRole.do")
- @GetMapping("logOff.do")

## CardController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/rank/CardController.java`
- @RequestMapping("/rank/card")
- @GetMapping("getList.do")
- @PostMapping("active.do")
- @PostMapping("donate.do")
- @PostMapping("activeEntityCard.do")
- @GetMapping("/getCardChannel.do")

## BenefitConsumerController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/rank/BenefitConsumerController.java`
- @RequestMapping("/rank/benefitConsumer")
- @PostMapping("consumer.do")
- @PostMapping("batchConsumer.do")
- @PostMapping("receiveGoods.do")

## BenefitPackageController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/rank/BenefitPackageController.java`
- @RequestMapping("/rank/benefitPackage")
- @GetMapping("getAll.do")

## MemberBenefitController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/rank/MemberBenefitController.java`
- @RequestMapping("/rank/memberBenefit")
- @GetMapping("getByCard.do")
- @GetMapping("getSumCount.do")
- @GetMapping("getCardBenefitList.do")
- @GetMapping("getSumDetail.do")

## LightModuleInfoController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/lightoperation/LightModuleInfoController.java`
- @RequestMapping("/module/info")
- @GetMapping("list.do")

## LightDataController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/lightoperation/LightDataController.java`
- @RequestMapping("/light/data")
- @GetMapping("/elec/list.do")
- @GetMapping("/elec/detail.do")
- @GetMapping("/elec/dayChart.do")
- @GetMapping("/elec/monthChart.do")
- @GetMapping("/elec/yearChart.do")
- @GetMapping("/elec/totalChart.do")
- @GetMapping("/inveter/detail.do")
- @GetMapping("/inveter/query.do")
- @GetMapping("/inveter/historyChart.do")
- @PostMapping("addRole.do")
- @PostMapping("checkOverdue.do")
- @PostMapping("checkOpServiceStatus.do")

## LightRepairOrderController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/lightoperation/LightRepairOrderController.java`
- @RequestMapping("/repair/order")
- @GetMapping("list.do")
- @GetMapping("stationInfo.do")
- @PostMapping("create.do")

## DatabaseManagementOpController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/lightoperation/DatabaseManagementOpController.java`
- @RequestMapping("/light/databaseManagementOp/")
- @GetMapping("list.do")
- @PostMapping("addNum")

## LightWorkOrderController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/lightoperation/LightWorkOrderController.java`
- @RequestMapping("/work/order")
- @PostMapping("bind.do")
- @GetMapping("detail.do")
- @GetMapping("list.do")
- @PostMapping("toDoor.do")
- @PostMapping("complete.do")
- @PostMapping("receipt.do")
- @GetMapping("getModule.do")
- @PostMapping("receiveModule.do")
- @PostMapping("addProcess.do")

## LightFaultDictionaryController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/lightoperation/LightFaultDictionaryController.java`
- @RequestMapping("/lightFaultDictionary/")
- @GetMapping("/findFirst.do")
- @GetMapping("/findSecond.do")
- @GetMapping("/findThird.do")

## OCRController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/base/OCRController.java`
- @RequestMapping("ocr")
- @GetMapping("idCard")

## MemberEnergyController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/member/MemberEnergyController.java`
- @RequestMapping("/member/energy")
- @GetMapping(value = "/get.do")
- @PostMapping(value="/sign.do",produces = "application/json",consumes = "application/json")
- @PostMapping(value="/share.do")
- @PostMapping(value="/sport.do")
- @PostMapping(value="/weight.do")
- @PostMapping(value="/energy.do")
- @GetMapping(value="/sort.do")
- @PostMapping(value="/check.do")

## MemberFitnessController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/member/MemberFitnessController.java`
- @RequestMapping("/member/fitness")
- @PostMapping("/checkFitness.do")
- @PostMapping("/signFitness.do")
- @PostMapping("/signFitnessSign.do")
- @PostMapping("/getFitnessSign.do")

## MemberVatInvoiceQualificationController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/member/MemberVatInvoiceQualificationController.java`
- @RequestMapping("/member/vatInvoiceQualification")
- @GetMapping("/get.do")
- @PostMapping("/save.do")
- @PostMapping("/delete.do")

## MemberController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/member/MemberController.java`
- @RequestMapping("/member")
- @GetMapping("getLoginMember.do")
- @PostMapping("registerCustomer.do")

## MemberAddressController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/member/MemberAddressController.java`
- @RequestMapping("/member/address")
- @GetMapping("/get.do")
- @GetMapping("/mark_as_default.do")
- @GetMapping("/list.do")
- @PostMapping("/saveAddress.do")
- @GetMapping("/regionList.do")
- @PostMapping("/removeAddress.do")
- @GetMapping("/addressRegionList.do")

## FindPasswordController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/member/FindPasswordController.java`
- @RequestMapping("/member/find_password")
- @PostMapping("/change.do")
- @GetMapping("/send_sms.do")

## MemberTestMealController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/member/MemberTestMealController.java`
- @RequestMapping("/member/test")
- @GetMapping("/check.do")

## ExpertCustomerController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/expert/ExpertCustomerController.java`
- @RequestMapping("/expert")
- @GetMapping("/listExpertShop.do")
- @GetMapping("/getExpertCustomer.do")

## DispenserSubsidyController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/dispenser/DispenserSubsidyController.java`
- @RequestMapping("/dispenser")
- @GetMapping("/listSubsidy.do")
- @PostMapping("/abtainSubsidy.do")

## WoPartController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/repairs/WoPartController.java`
- @RequestMapping("/repairs/woPart")
- @PostMapping("/getPage")
- @PostMapping("/getInfo")
- @PostMapping("/applyPartCheck")
- @PostMapping("/applyPart")
- @PostMapping("/sparePartsRegistrationCheck")
- @PostMapping("/sparePartsRegistration")
- @PostMapping("/orderWoPartPage")
- @PostMapping("/orderWoPartPageAndFile")
- @PostMapping("/saveOrderWoPartFile")

## CdWarehouseAddressController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/repairs/CdWarehouseAddressController.java`
- @RequestMapping("/repairs/cdWarehouseAddress")
- @GetMapping("/getCdWarehouseAndAddressByMemberID")
- @PostMapping("/getAllList")
- @PostMapping("/updateDefault")
- @GetMapping("/getInfoById")
- @PostMapping("/save")
- @PostMapping("/update")
- @PostMapping("/delete")

## CdDictDateController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/repairs/CdDictDateController.java`
- @RequestMapping("/repairs/cdDictData")
- @PostMapping("/getList")
- @GetMapping("/getInfoById")

## CdMaterialController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/repairs/CdMaterialController.java`
- @RequestMapping("/repairs/cdMaterial")
- @PostMapping("/getPage")
- @PostMapping("/getList")

## LiveController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/live/LiveController.java`
- @RequestMapping("/live")
- @PostMapping("/getLiveList.do")
- @PostMapping("/getLiveReplay.do")
- @PostMapping("/getRelayList.do")
- @GetMapping("/getYzzLiveList.do")
- @GetMapping("/getYzzLiveReplay.do")
- @GetMapping("/getYzzRelayList.do")
- @PostMapping("/sendSubMessage.do")

## HotNewsController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/index/HotNewsController.java`
- @RequestMapping("/hotNews")
- @GetMapping("/getHotNewsList.do")

## HomePageController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/index/HomePageController.java`
- @RequestMapping("/homePage")
- @GetMapping("/listRecommend.do")
- @GetMapping("/listCustomZone.do")
- @GetMapping("/listFloorItem.do")
- @GetMapping("/listHotItem.do")
- @GetMapping("/listGroupItem.do")

## CooperationInfoController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/index/CooperationInfoController.java`
- @RequestMapping("/cooperationInfo")
- @PostMapping("/add.do")
- @GetMapping("/getIntroducePic.do")

## EnergyCaseController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/index/EnergyCaseController.java`
- @RequestMapping("/energyCase")
- @GetMapping("/getEnergyCaseList.do")

## CarouselController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/carousel/CarouselController.java`
- @RequestMapping("/carousel")
- @GetMapping("/listCarousel.do")

## AppImageController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/carousel/AppImageController.java`
- @RequestMapping("/appimage")
- @GetMapping("/listItem.do")

## WechatShareController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/wechat/WechatShareController.java`
- @RequestMapping("/wechat")
- @PostMapping("share.do")

## MiniProgramT1Controller
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/wechat/MiniProgramT1Controller.java`
- @RequestMapping("minijumpurl")
- @PostMapping("generate_urllink")

## ParkController
- 文件: `rrsjk-mobile-web/src/main/java/com/rrsjk/mobile/controller/park/ParkController.java`
- @RequestMapping("/park")
- @GetMapping("/findByParent.do")
- @PostMapping("appraiseUp.do")
- @GetMapping("getAppraiseConfig.do")

## GlobalExceptionHandler
- 文件: `vpp-api-meta/vpp-biz/src/main/java/com/nahui/energy/handler/GlobalExceptionHandler.java`
- 未扫描到显式 Mapping 注解

## ShipmentLogController
- 文件: `vpp-api-meta/vpp-biz/src/main/java/com/nahui/energy/controller/ShipmentLogController.java`
- @RequestMapping("/shipment")
- @GetMapping("/page")
- @PostMapping("/importData")
- @DeleteMapping("/{id}")
- @PostMapping("/add")

## ProductLogController
- 文件: `vpp-api-meta/vpp-biz/src/main/java/com/nahui/energy/controller/ProductLogController.java`
- @RequestMapping("/product/log/")

## ProductController
- 文件: `vpp-api-meta/vpp-biz/src/main/java/com/nahui/energy/controller/ProductController.java`
- @RequestMapping("/product")
- @GetMapping("/page")
- @GetMapping("/{id}")
- @PostMapping
- @PutMapping
- @PutMapping("/changeStatus")

## WechatNotifyController
- 文件: `rrsjk-pay-web/src/main/java/com/rrsjk/pay/controller/notify/WechatNotifyController.java`
- @RequestMapping("/notify/wechat")
- @PostMapping("payNotify.do")
- @GetMapping("/authorize.do")
- @GetMapping("/accessToken.do")
- @GetMapping("/accessTokenDev.do")

## AlipayNotifyController
- 文件: `rrsjk-pay-web/src/main/java/com/rrsjk/pay/controller/notify/AlipayNotifyController.java`
- @RequestMapping("/notify/alipay")
- @PostMapping("payNotify.do")

## CcbNotifyController
- 文件: `rrsjk-pay-web/src/main/java/com/rrsjk/pay/controller/notify/CcbNotifyController.java`
- @RequestMapping("/notify/ccb")
- @PostMapping("payNotify.do")

## BaiduNotifyController
- 文件: `rrsjk-pay-web/src/main/java/com/rrsjk/pay/controller/notify/BaiduNotifyController.java`
- @RequestMapping("/notify/baidu")
- @PostMapping("payNotify.do")
- @PostMapping("refundAuditNotify.do")
- @PostMapping("refundNotify.do")

## PayDispenserNotifyController
- 文件: `rrsjk-pay-web/src/main/java/com/rrsjk/pay/controller/notify/PayDispenserNotifyController.java`
- @RequestMapping("/notify")
- @PostMapping("/alipay/payNotifyDispenser.do")
- @PostMapping("/ccb/payNotifyDispenser.do")
- @PostMapping("/wechat/payNotifyDispenser.do")

## PaymentController
- 文件: `rrsjk-pay-web/src/main/java/com/rrsjk/pay/controller/pay/PaymentController.java`
- @RequestMapping("/pay")
- @PostMapping("createPayment.do")
- @GetMapping("/getPayResult.do")
- @GetMapping("/getMicroPayTradeState.do")
- @GetMapping("/getMicroPayTradeStateByScene.do")

## PayController
- 文件: `rrsjk-pay-web/src/main/java/com/rrsjk/pay/controller/pay/PayController.java`
- @RequestMapping("/pay")
- @PostMapping("pay.do")

## PayWaterControlController
- 文件: `rrsjk-pay-web/src/main/java/com/rrsjk/pay/controller/pay/PayWaterControlController.java`
- @RequestMapping("/payWaterControl")
- @PostMapping("createPayment.do")
- @PostMapping("pay.do")
- @GetMapping("/getPayResult.do")

## PayDispenserController
- 文件: `rrsjk-pay-web/src/main/java/com/rrsjk/pay/controller/pay/PayDispenserController.java`
- @RequestMapping("/payDispenser")
- @PostMapping("pay.do")
- @GetMapping("/getPayResult.do")

## HuarongDashboardController
- 文件: `rrsjk-report-web/src/main/java/com/rrsjk/report/controller/light/HuarongDashboardController.java`
- @RequestMapping("/light/screen/huarong/")
- @GetMapping("todayData.do")
- @GetMapping("locationAnalyse.do")
- @GetMapping("capacityRank.do")
- @GetMapping("electricMonthGraphic.do")
- @GetMapping("pvStationCountRank.do")
- @GetMapping("findDashStation.do")
- @GetMapping("findDashStationDetail.do")
- @GetMapping(value = { "/listRegion.do" })

## PuyinDashboardController
- 文件: `rrsjk-report-web/src/main/java/com/rrsjk/report/controller/light/PuyinDashboardController.java`
- @RequestMapping("/light/screen/white/")
- @GetMapping("todayData.do")
- @GetMapping("locationAnalyse.do")
- @GetMapping("capacityRank.do")
- @GetMapping("electricMonthGraphic.do")
- @GetMapping("pvStationCountRank.do")
- @GetMapping("findDashStation.do")
- @GetMapping("findDashStationDetail.do")
- @GetMapping(value = { "/listRegion.do" })

## ReportScreenController
- 文件: `rrsjk-report-web/src/main/java/com/rrsjk/report/controller/light/ReportScreenController.java`
- @RequestMapping("/light/screen/")
- @GetMapping("getCoverageArea.do")
- @GetMapping("getOrder.do")
- @GetMapping("getInstallShaft.do")
- @GetMapping("getInstallt.do")
- @GetMapping("getStationRank.do")
- @GetMapping("getGrid.do")
- @GetMapping("getMap.do")
- @GetMapping("getEnergy.do")
- @GetMapping("getMonthElectricity.do")
- @GetMapping("getWorkPercent.do")
- @GetMapping("getWorkTotal.do")
- @PostMapping("/getWorkOrderStatistics")
- @GetMapping("getWorkOrderCount.do")

## CnncDashboardController
- 文件: `rrsjk-report-web/src/main/java/com/rrsjk/report/controller/light/CnncDashboardController.java`
- @RequestMapping("/light/screen/cnnc/")
- @GetMapping("todayData.do")
- @GetMapping("electricMonthGraphic.do")
- @GetMapping("locationAnalyse.do")
- @GetMapping("capacityRank.do")
- @GetMapping("pvStationCountRank.do")
- @GetMapping(value = { "/listRegion.do" })
- @GetMapping("findDashStation.do")
- @GetMapping("findDashStationDetail.do")

## CmbDashboardController
- 文件: `rrsjk-report-web/src/main/java/com/rrsjk/report/controller/light/CmbDashboardController.java`
- @RequestMapping("/light/screen/cmb/")
- @GetMapping("todayData.do")
- @GetMapping("locationAnalyse.do")
- @GetMapping("capacityRank.do")
- @GetMapping("electricMonthGraphic.do")
- @GetMapping("pvStationCountRank.do")
- @GetMapping("findDashStation.do")
- @GetMapping("findDashStationDetail.do")
- @GetMapping(value = { "/listRegion.do" })

## YueXiuDashboardController
- 文件: `rrsjk-report-web/src/main/java/com/rrsjk/report/controller/light/YueXiuDashboardController.java`
- @RequestMapping("/light/screen/yuexiu/")
- @GetMapping("todayData.do")
- @GetMapping("electricMonthGraphic.do")
- @GetMapping("locationAnalyse.do")
- @GetMapping("capacityRank.do")
- @GetMapping("pvStationCountRank.do")
- @GetMapping(value = { "/listRegion.do" })
- @GetMapping("findDashStation.do")
- @GetMapping("findDashStationDetail.do")

## BocDashboardController
- 文件: `rrsjk-report-web/src/main/java/com/rrsjk/report/controller/light/BocDashboardController.java`
- @RequestMapping("/light/screen/boc/")
- @GetMapping("todayData.do")
- @GetMapping("electricMonthGraphic.do")
- @GetMapping("locationAnalyse.do")
- @GetMapping("capacityRank.do")
- @GetMapping("pvStationCountRank.do")
- @GetMapping(value = { "/listRegion.do" })
- @GetMapping("findDashStation.do")
- @GetMapping("findDashStationDetail.do")

## ReportAssetScreenController
- 文件: `rrsjk-report-web/src/main/java/com/rrsjk/report/controller/light/ReportAssetScreenController.java`
- @RequestMapping("/light/screen/asset/")
- @GetMapping("getCoverageArea.do")
- @GetMapping("getGrid.do")
- @GetMapping("getCmGrid.do")
- @GetMapping("getStationRank.do")
- @GetMapping("getRentRank.do")
- @GetMapping("getElectricRevenueRank.do")
- @GetMapping("getInvestorData.do")
- @GetMapping("getEnergy.do")
- @GetMapping("getCompanyRevenueRank.do")
- @GetMapping("getMonthElectricity.do")
- @GetMapping("getYearElectricity.do")
- @GetMapping("getWorkOrderCount.do")
- @GetMapping("getWorkOrderSum.do")
- @GetMapping("getMap.do")
- @GetMapping("findDashStation.do")
- @GetMapping("findDashStationDetail.do")
- @GetMapping(value = { "/listRegion.do" })
- @GetMapping("getProvinceGrid.do")
- @GetMapping("getMonthGrid.do")
- @GetMapping("getMonthDayElec.do")
- @GetMapping("getCmMap.do")
- @GetMapping("getGridNew.do")

## GlobalExceptionHandler
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/config/GlobalExceptionHandler.java`
- 未扫描到显式 Mapping 注解

## OssApkFileController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/OssApkFileController.java`
- @RequestMapping("/oss/apkFile/")
- @PostMapping("uploadLvFile.do")
- @PostMapping("uploadLvV4File.do")
- @PostMapping("uploadNgbFile.do")
- @PostMapping("uploadOpsFile.do")

## OssImageController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/OssImageController.java`
- @RequestMapping("/oss/image/")
- @PostMapping("upload.do")

## OssFileController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/OssFileController.java`
- @RequestMapping("/oss/file/")
- @PostMapping("upload.do")

## EnergyStatisticIncomeController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/energy/EnergyStatisticIncomeController.java`
- @RequestMapping("/energy")
- @GetMapping("getScopeDataByDate")
- @GetMapping("getDetail")
- @GetMapping("exportDetail")

## SpdbFeeController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/threepartenr/SpdbFeeController.java`
- @RequestMapping("third/spdb/fee")
- @PostMapping("electricCharge")

## OuterExposeController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/threepartenr/OuterExposeController.java`
- @RequestMapping("/nahui/station/api/")
- @GetMapping("queryStation")
- @GetMapping("inverterQueryByPage")
- @GetMapping("realtimeInverterQueryByPage")
- @GetMapping("workOrderQueryByPage")
- @GetMapping("queryInvertersp")

## SpdbOuterController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/threepartenr/SpdbOuterController.java`
- @RequestMapping("spdb/electricity")
- @PostMapping("powerQuery")

## LightInverterController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/inverter/LightInverterController.java`
- @RequestMapping("inverter")

## HdsStationElecReportController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/HdsStationElecReportController.java`
- @RequestMapping("/report/hds/elec")
- @PostMapping("/total/page")
- @PostMapping("/year/page")
- @PostMapping("/month/page")
- @GetMapping("/total/export")
- @GetMapping("/year/export")
- @GetMapping("/month/export")

## ReportCmIncomeController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/ReportCmIncomeController.java`
- @RequestMapping("report/cmIncome")
- @GetMapping("/findCmChainGroupIncomeReport")
- @GetMapping("/findCmProjectTotalIncomeReport")
- @GetMapping("/findCmIncomeItemReport")
- @GetMapping("/exportCmChainGroupIncomeReport")
- @GetMapping("/exportCmProjectTotalIncomeReport")
- @GetMapping("/exportCmIncomeItemReport")
- @GetMapping("/updateReport")

## EnergySpDayController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/EnergySpDayController.java`
- @RequestMapping("/report/spDay")
- @GetMapping("/findList")
- @GetMapping("/export")
- @GetMapping("/centerList")
- @GetMapping("/provinceList")
- @GetMapping("/cityList")
- @GetMapping("/districtList")

## EnergyStationElecIncomeController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/EnergyStationElecIncomeController.java`
- @RequestMapping("/report/stationElecIncome")
- @PostMapping("/findList")
- @GetMapping("/doExcel")

## ReportBtModeDayController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/ReportBtModeDayController.java`
- @RequestMapping("report/btModeDay")
- @GetMapping("/findByDateAt")
- @GetMapping("/export")

## EnergyCenterProfitController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/EnergyCenterProfitController.java`
- @RequestMapping("/report/centerProfit")
- @GetMapping("/findList")

## EnergyIncomeDayController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/EnergyIncomeDayController.java`
- @RequestMapping("/report/incomeDay")
- @GetMapping("/findByDayAt")

## EnergyYuexiuSubCenterDataController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/EnergyYuexiuSubCenterDataController.java`
- @RequestMapping("/report/yuexiuSubCenterDay")
- @GetMapping("/findByDayAt")
- @GetMapping("/export")

## EnergyJobController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/EnergyJobController.java`
- @RequestMapping("/report/update")
- @GetMapping("/income")
- @GetMapping("/station")
- @GetMapping("/build")
- @GetMapping("/summary")
- @GetMapping("/center")
- @GetMapping("/subchain")
- @GetMapping("/incomeRecord")
- @GetMapping("/subchainRecord")
- @GetMapping("/estimate")
- @GetMapping("/estimateToSap")
- @GetMapping("/estimateRecord")
- @GetMapping("/estimateToSapAgainByCompanyCode")
- @GetMapping("/estimateToSapAgain")
- @GetMapping("/householdStation")
- @GetMapping("/yuexiuReport")
- @GetMapping("/estimateOff")
- @GetMapping("/estimateOffToSap")
- @GetMapping("/eteCenter")
- @GetMapping("/houseHoldIncome")
- @GetMapping("/eteCenterAll")
- @GetMapping("/updateAllWarning")
- @GetMapping("/eteIncome")
- @GetMapping("/eteIncomeAll")
- @GetMapping("/estimateStation")
- @GetMapping("/centerProfitForecast")
- @GetMapping("/centerProfitActual")
- @GetMapping("/stationElecIncome")
- @GetMapping("/stationWarning")
- @GetMapping("/lightSubchain")
- @GetMapping("/lightSubchainAll")
- @GetMapping("/delivery")
- @GetMapping("/centerNetworkBuild")
- @GetMapping("/ZhMode")
- @GetMapping("/btMode")
- @GetMapping("/spDay")
- @GetMapping("/sumElectHourDay")
- @GetMapping("/electTargetMonth")
- @GetMapping("/electTargetYear")
- @GetMapping("/estimateStationSum")
- @GetMapping("/elecPriceReport")
- @GetMapping("/elecOrder")
- @GetMapping("/estimateOffStation")
- @GetMapping("/estimateOffStationSum")

## EnergySummaryDayController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/EnergySummaryDayController.java`
- @RequestMapping("/report/summaryDay")
- @GetMapping("/findByDayAt")
- @GetMapping("/export")

## ReportStationEchartsController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/ReportStationEchartsController.java`
- @RequestMapping("report/echarts")
- @GetMapping("echartsNew")
- @GetMapping("echarts")
- @GetMapping("m2")
- @GetMapping("m3")
- @GetMapping("m4")
- @GetMapping("m5")
- @GetMapping("m6")
- @GetMapping("m7")

## GreenEnergyDayReportController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/GreenEnergyDayReportController.java`
- @RequestMapping("/greenEnergyDayReport")
- @GetMapping("/chainGroupIncome/findList")
- @GetMapping("/signAndGridScale/findList")
- @GetMapping("/MarketScale/findList")

## EnergyCountyCenterDayController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/EnergyCountyCenterDayController.java`
- @RequestMapping("/report/countyCenterDay")
- @GetMapping("/findByDayAt")
- @GetMapping("/export")

## ReportCmSignGuaranteeRateController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/ReportCmSignGuaranteeRateController.java`
- @RequestMapping("report/cmSignGuaranteeRate")
- @GetMapping("/findByDateAt")
- @GetMapping("/export")
- @GetMapping("/updateReport")

## EnergyCenterProfitCostController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/EnergyCenterProfitCostController.java`
- @RequestMapping("/report/centerProfitCost")
- @GetMapping("/queryPage")
- @PostMapping("importCenterProfitCost.do")
- @GetMapping("downloadTemplate.do")

## EnergyAuditStatusReportController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/EnergyAuditStatusReportController.java`
- @RequestMapping("/report/auditStatus")
- @GetMapping("/find")
- @GetMapping("/findParty")
- @GetMapping("/findSp")
- @GetMapping("/export")

## ReportSpStationDevelopWarningController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/ReportSpStationDevelopWarningController.java`
- @RequestMapping("report/spStationDevelopWarning")
- @GetMapping("/list")
- @GetMapping("/export")
- @GetMapping("/echarts")

## EnergySubchainGroupTargetReachController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/EnergySubchainGroupTargetReachController.java`
- @RequestMapping("/report/subchainGroup")
- @GetMapping("/findByDayAt")
- @GetMapping("/export")

## ReportStationProcessWarningController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/ReportStationProcessWarningController.java`
- @RequestMapping("report/stationProcessWarning")
- @GetMapping("exejobMethod")
- @GetMapping("queryReportBody")
- @GetMapping("exportData")

## EnergyCenterProfitConfigController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/EnergyCenterProfitConfigController.java`
- @RequestMapping("/report/centerProfitConfig")
- @PostMapping("/updatePersonNum")
- @GetMapping("/findList")

## EnergyYuexiuSpDataController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/EnergyYuexiuSpDataController.java`
- @RequestMapping("/report/yuexiuSpDay")
- @GetMapping("/findByDayAt")
- @GetMapping("/export")

## EnergyHouseholdStationIncomeController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/EnergyHouseholdStationIncomeController.java`
- @RequestMapping("/report/householdStation")
- @GetMapping("/findList")
- @GetMapping("/export")

## zeroCarbonDayReportController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/zeroCarbonDayReportController.java`
- @RequestMapping("/zeroCarbonReport/dayReport")
- @GetMapping("/findDayReport")
- @GetMapping("dayReportExport")
- @GetMapping("/findDayReportDifference")
- @GetMapping("dayReportDifferenceExport")
- @GetMapping("/findDayReportDetails")
- @GetMapping("/findSub")

## LightStationAuditReportController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/LightStationAuditReportController.java`
- @RequestMapping("/report/stationAudit")
- @GetMapping("/find")
- @GetMapping("/export")
- //    @PostMapping("/generate")
- //    @PostMapping("/refresh")
- //    @PostMapping("/batchRefresh")

## EnergyChainGroupIncomeController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/EnergyChainGroupIncomeController.java`
- @RequestMapping("/report/chainGroupIncome")
- @GetMapping("/findByDayAt")
- @PostMapping("/changeReport")
- @GetMapping("/export")

## EnergyElecWarningReportController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/EnergyElecWarningReportController.java`
- @RequestMapping("/report/elecWarning")
- @GetMapping("/queryListByDayAt")
- @GetMapping("/queryDetail")
- @GetMapping("companyInfoList")

## EnergyLightSubchainController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/EnergyLightSubchainController.java`
- @RequestMapping("/report/lightSubchain")
- @GetMapping("/findByDayAt")

## EnergyCenterNetworkBuildController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/EnergyCenterNetworkBuildController.java`
- @RequestMapping("/report/centerNetwork")
- @GetMapping("/findByDayAt")

## EnergyBuildDayController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/EnergyBuildDayController.java`
- @RequestMapping("/report/buildDay")
- @GetMapping("/findByDayAt")

## EnergyAuditValidityReportController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/EnergyAuditValidityReportController.java`
- @RequestMapping("/report/auditValidity")
- @GetMapping("/find")
- @GetMapping("/export")

## ReportZhModelStationController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/ReportZhModelStationController.java`
- @RequestMapping("report/reportZhModeStation")
- @GetMapping("/findByDateAt")
- @GetMapping("/export")

## EnergyYuexiuReportDataController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/EnergyYuexiuReportDataController.java`
- @RequestMapping("/report/yuexiuDay")
- @GetMapping("/findByDayAt")
- @GetMapping("/export")

## ReportDeliveryStationController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/ReportDeliveryStationController.java`
- @RequestMapping("report/delivery-station")
- @GetMapping("/list")
- @GetMapping("/lastYearElectTargetList")
- @GetMapping("/lastMonthElectTargetList")
- @GetMapping("/electTargetSumList")
- @GetMapping("/lastMonthElectTarget/export")
- @GetMapping("/lastYearElectTarget/export")
- @GetMapping("/electTargetSum/export")

## FinanceController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/FinanceController.java`
- @RequestMapping("/bxFinance/test")
- @GetMapping("/income")

## EnergyStationDayController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/EnergyStationDayController.java`
- @RequestMapping("/report/stationDay")
- @GetMapping("/findByDayAt")

## EnergyElecIncomeReportController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/EnergyElecIncomeReportController.java`
- @RequestMapping("/report/elecIncome")
- @GetMapping("/queryListByDayAt")

## ReportStationDevelopWarningController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/report/ReportStationDevelopWarningController.java`
- @RequestMapping("report/stationDevelopWarning")
- @GetMapping("queryReportBody")
- @GetMapping("/export")

## SysEvaluateController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/system/SysEvaluateController.java`
- @RequestMapping("/sysEvaluate/")
- @GetMapping("get.do")
- @PostMapping("/add.do")
- @GetMapping("list.do")

## MenuController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/system/MenuController.java`
- @RequestMapping("/system/menu/")
- @GetMapping("/permissions.do")
- @GetMapping("/menus.do")

## WfTaskController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/workflow/WfTaskController.java`
- @RequestMapping("/workflow/task")
- @PostMapping(value = "/stopProcess")
- @PostMapping(value = "/revokeProcess")
- @GetMapping(value = "/processVariables/{taskId}")
- @PostMapping(value = "/complete")
- @PostMapping(value = "/reject")
- @PostMapping(value = "/return")
- @PostMapping(value = "/returnList")
- @DeleteMapping(value = "/delete")
- @PostMapping(value = "/claim")
- @PostMapping(value = "/unClaim")
- @PostMapping(value = "/delegate")
- @PostMapping(value = "/transfer")
- @RequestMapping("/diagram/{processId}")

## WfProcessController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/workflow/WfProcessController.java`
- @RequestMapping("/workflow/process")
- @GetMapping(value = "/list")
- @GetMapping(value = "/ownList")
- @GetMapping(value = "/todoList")
- @GetMapping(value = "/claimList")
- @GetMapping(value = "/finishedList")
- @GetMapping(value = "/copyList")
- @PostMapping("/startExport")
- @PostMapping("/ownExport")
- @PostMapping("/todoExport")
- @PostMapping("/claimExport")
- @PostMapping("/finishedExport")
- @PostMapping("/copyExport")
- @GetMapping("/getProcessForm")
- @PostMapping("/start/{processDefId}")
- @DeleteMapping("/instance/{instanceIds}")
- @GetMapping("/bpmnXml/{processDefId}")
- @GetMapping("/detail")
- @GetMapping("doExport.do")
- @GetMapping("doExportOfMine.do")
- @GetMapping("doExportTaskTODo.do")
- @GetMapping("doExportFinish.do")

## WfModelController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/workflow/WfModelController.java`
- @RequestMapping("/workflow/model")
- @GetMapping("/list")
- @GetMapping("/historyList")
- @GetMapping(value = "/{modelId}")
- @GetMapping(value = "/bpmnXml/{modelId}")
- @PostMapping
- @PutMapping
- @PostMapping("/save")
- @PostMapping("/latest")
- @DeleteMapping("/{modelIds}")
- @PostMapping("/deploy")
- @GetMapping("doExport.do")

## WfCategoryController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/workflow/WfCategoryController.java`
- @RequestMapping("/workflow/category")
- @GetMapping("/list")
- @GetMapping("/listAll")
- @GetMapping("/{categoryId}")
- @PostMapping()
- @PutMapping()
- @DeleteMapping("/{categoryIds}")
- @GetMapping("doExport.do")

## WfInstanceController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/workflow/WfInstanceController.java`
- @RequestMapping("/workflow/instance")
- @PostMapping(value = "/updateState")
- @PostMapping(value = "/stopProcessInstance")
- @DeleteMapping(value = "/delete")
- @GetMapping("/detail")

## WfFormController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/workflow/WfFormController.java`
- @RequestMapping("/workflow/form")
- @GetMapping("/list")
- @GetMapping(value = "/{formId}")
- @PostMapping
- @PutMapping
- @DeleteMapping("/{formIds}")
- @PostMapping("/addDeployForm")
- @GetMapping("/getRoleList")
- @GetMapping("/getUserList")

## WfDeployController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/workflow/WfDeployController.java`
- @RequestMapping("/workflow/deploy")
- @GetMapping("/list")
- @GetMapping("/publishList")
- @PutMapping(value = "/changeState")
- @GetMapping("/bpmnXml/{definitionId}")
- @DeleteMapping("/{deployIds}")
- @GetMapping("/form/{deployId}")
- @GetMapping("doExport.do")

## ScheduledTasksController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/task/ScheduledTasksController.java`
- @RequestMapping("/scheduledTasks")
- @GetMapping("historySettle")
- @GetMapping("historySettleByIac")
- @GetMapping("/operationMaintenance/createData")
- @GetMapping("/lightElectricUnusual/createData")
- @GetMapping("/lightElectricUnusual/closed")
- @GetMapping("/lightElectricUnusual/updateDays")

## EvaluateController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/evaluate/EvaluateController.java`
- @RequestMapping("/evaluate/")
- @GetMapping("get.do")
- @PostMapping("/add.do")
- @GetMapping("list.do")

## BocLightStationController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/boc/BocLightStationController.java`
- @RequestMapping("/bocLightStation")
- @RequestMapping("queryPage")
- @GetMapping("getStationDetail")
- @GetMapping("showRecord.do")

## ZeroCarbonSubNewController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/light/ZeroCarbonSubNewController.java`
- @RequestMapping("/light/zeroCarbonSubNew")
- @GetMapping("getSubInfo.do")

## NoOpStationController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/light/NoOpStationController.java`
- @RequestMapping("/noOpStation")
- @GetMapping("list.do")
- @GetMapping("getByStationCode.do")
- @PostMapping("addData.do")
- @PostMapping("audiOk.do")
- @PostMapping("audiReject.do")
- @GetMapping("del.do")
- @GetMapping("export.do")
- @GetMapping("getCompanyInfo.do")

## OperationMaintenanceTaskController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/light/OperationMaintenanceTaskController.java`
- @RequestMapping("/light/operationMaintenanceTask")
- @GetMapping("/findParams.do")

## SellLightStationController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/light/SellLightStationController.java`
- @RequestMapping("/sell/lightStation")
- @GetMapping("postStation")
- @GetMapping("pushExchangeUserInfo")
- @GetMapping("syncBpStatusFromYuexiuExchange")
- @GetMapping("pushProjectInfo")
- @GetMapping("syncProjectStatus")
- @GetMapping("saveInveterHistory")
- @GetMapping("url")
- @GetMapping("batchUrlUpload")
- @GetMapping("save")
- @GetMapping("saveHistoryDataSiNeng")
- @PostMapping("downLoadImage")

## LightOpOrderCenterController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/light/LightOpOrderCenterController.java`
- @RequestMapping("/lightOpOrderCenter")
- @GetMapping("doList.do")
- @PostMapping(value = {"audit.do"})
- @PostMapping(value = {"detail.do"})
- @GetMapping("doExport.do")

## OperationMaintenanceLogController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/light/OperationMaintenanceLogController.java`
- @RequestMapping("/light/operationMaintenanceLog")
- @GetMapping("/findParams.do")
- @PostMapping("/addRemarks.do")

## OperationMaintenanceStationController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/light/OperationMaintenanceStationController.java`
- @RequestMapping("/operationMaintenanceStation")
- @GetMapping("list.do")
- @GetMapping("export.do")

## LightStationChangeOperationController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/light/LightStationChangeOperationController.java`
- @RequestMapping("/lightStationChangeOperation")
- @GetMapping("findByPage")
- @GetMapping("/downTemplate")
- @PostMapping("importData.do")
- @PostMapping("addData.do")
- @PostMapping("audiOk")
- @PostMapping("audiReject")
- @PostMapping("del.do")
- @PostMapping("getAuth.do")
- @PostMapping("getOperation.do")
- @GetMapping("doExport.do")
- @PostMapping("details.do")
- @GetMapping("doExportDetails.do")
- @PostMapping("saveErrorData")
- @PostMapping("addNewOldRegionId")

## LightRentController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/light/LightRentController.java`
- @RequestMapping("/lightRent")
- @GetMapping("/accountRecordByOp.do")
- @GetMapping("/accountDetailOp.do")
- @GetMapping("doExport.do")
- @GetMapping("doExportList.do")

## LightProjectELecOrderOwnerController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/light/LightProjectELecOrderOwnerController.java`
- @RequestMapping("lightProjectELecOrderOwner")
- @GetMapping("queryList")
- @GetMapping("export")

## CreateOperationMaintenanceStationController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/light/CreateOperationMaintenanceStationController.java`
- @RequestMapping("createOperationMaintenanceStation")
- @PostMapping("importData.do")
- @PostMapping("importDataByHuaRong.do")
- @PostMapping("simpleImportData.do")
- @GetMapping("removeOpAuth.do")
- @GetMapping("createSupplementContract.do")
- @GetMapping("/downTemplateByChongXiao")
- @PostMapping("importDataTwo.do")
- @PostMapping("addRegion.do")
- @PostMapping("importDataThree.do")
- @PostMapping("importSettle.do")
- @PostMapping("importDataFour.do")
- @PostMapping("importDataFive.do")
- @PostMapping("importFixSettle.do")
- @PostMapping("importFixMOSettle.do")
- @PostMapping("importErrorOperationMaintenance.do")

## LightUnionpayBillRecordCmbController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/light/LightUnionpayBillRecordCmbController.java`
- @RequestMapping("/lightUnionpayBillRecordCmb")
- @RequestMapping(value = "doList.do", method = RequestMethod.POST)
- @RequestMapping(value = "doDetailList.do", method = RequestMethod.POST)
- @RequestMapping(value = "repay.do", method = RequestMethod.POST)
- @RequestMapping(value = "repayDetailInfo.do", method = RequestMethod.POST)
- @RequestMapping(value = "batchRepay.do", method = RequestMethod.POST)
- @GetMapping("doExport.do")
- @RequestMapping(value = "detailDoExport.do", method = RequestMethod.GET)

## LightStationRentDeductController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/light/LightStationRentDeductController.java`
- @RequestMapping("/lightStationRentDeduct")
- @RequestMapping(value = "/templatePath", method = {RequestMethod.GET})
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping("importData.do")
- @RequestMapping("doConfirm.do")
- @RequestMapping("doCount.do")
- @RequestMapping("doDel.do")

## OperationMaintenanceController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/light/OperationMaintenanceController.java`
- @RequestMapping("/light/operationMaintenance")
- @GetMapping("/findParams.do")
- @PostMapping("/confirmSettle")
- @PostMapping("/confirmSettleHistory")
- @PostMapping("confirmIncome")
- @PostMapping("confirmIncomeHistory")
- @PostMapping("confirmSk")
- @PostMapping("mergeInvoice")
- @PostMapping("invoiceByOne")
- @GetMapping("doExport.do")
- @GetMapping("stationDetails")
- @GetMapping("doExportStation.do")
- @GetMapping("/downTemplate")
- @GetMapping("/downTemplateA51")
- @PostMapping("importData.do")
- @PostMapping("importDataA51.do")
- @GetMapping("/downTemplateAll")
- @PostMapping("importDataAll.do")
- @PostMapping("importDell.do")
- @GetMapping("/downTemplateDel")
- @PostMapping("importBf.do")
- @PostMapping("addProtectionData.do")
- @PostMapping("confirmIncomeBf.do")
- @PostMapping("importCover.do")
- @GetMapping("/downCover")
- @PostMapping("addCoverData.do")
- @PostMapping("checkImportDataAll.do")
- @PostMapping("mergeSk.do")

## OperationSettlementDataController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/light/OperationSettlementDataController.java`
- @RequestMapping("/operationSettlementData/")
- @GetMapping("/find.do")
- @GetMapping("doExport.do")
- @PostMapping("audiOk")
- @PostMapping("audiReject")
- @PostMapping("del.do")
- @PostMapping("addData.do")
- @GetMapping("getOperationProvider")
- @GetMapping("getPower")
- @GetMapping("getProject")
- @PostMapping("/renewalAudiOk.do")
- @PostMapping("/renewalAudiReject.do")
- @PostMapping("/renewalCreate.do")
- @PostMapping("/stopCreate.do")
- @PostMapping("/stopUpload.do")
- @PostMapping("/stopAudiOk.do")
- @PostMapping("/stopAudiReject.do")

## OmStationHistoryRecordController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/light/OmStationHistoryRecordController.java`
- @RequestMapping("omStationHistoryRecord")
- @GetMapping("/findParams.do")
- @GetMapping("/findLastOne.do")
- @GetMapping("export.do")

## OperationInstallController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/light/OperationInstallController.java`
- @RequestMapping("/light/operationInstall")
- @GetMapping("/findParams.do")
- @PostMapping("/confirmSettle")
- @PostMapping("confirmIncome")
- @PostMapping("confirmSk")
- @PostMapping("mergeInvoice")
- @PostMapping("invoiceByOne")
- @GetMapping("doExport.do")
- @GetMapping("stationDetails")
- @GetMapping("doExportStation.do")
- @GetMapping("/downTemplate")
- @GetMapping("/downTemplateList")
- @PostMapping("importData.do")
- @PostMapping("importDataList.do")

## LightUnionpayBillRecordController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/light/LightUnionpayBillRecordController.java`
- @RequestMapping("/lightUnionpayBillRecord")
- @RequestMapping(value = "doList.do", method = RequestMethod.POST)
- @RequestMapping(value = "doDetailList.do", method = RequestMethod.POST)
- @RequestMapping(value = "repay.do", method = RequestMethod.POST)
- @RequestMapping(value = "repayDetailInfo.do", method = RequestMethod.POST)
- @RequestMapping(value = "batchRepay.do", method = RequestMethod.POST)
- @GetMapping("doExport.do")
- @RequestMapping(value = "detailDoExport.do", method = RequestMethod.GET)

## LightUnionpayBillController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/light/LightUnionpayBillController.java`
- @RequestMapping("/lightUnionpayBill")
- @RequestMapping(value = "doList.do", method = RequestMethod.POST)
- @GetMapping("queryBalance.do")
- @PostMapping("payBill.do")
- @PostMapping("confirm.do")
- @RequestMapping(value = "doExport.do", method = RequestMethod.GET)

## LightStagingRecordsController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/light/LightStagingRecordsController.java`
- @RequestMapping("/yantuData")
- @GetMapping("/findPage.do")
- @GetMapping("doExport.do")

## LightStationController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/light/LightStationController.java`
- @RequestMapping("/light/station")
- @GetMapping("getCurrentUser")
- @GetMapping("/getByStationCode.do")
- @GetMapping("/getWaitCompanySignZhStation.do")
- @GetMapping("/signZhMaster.do")
- @GetMapping("/getContractUrl.do")
- @GetMapping("queryLightStationCommon")
- @GetMapping("queryLightStationForCnnAuditList")
- @GetMapping("exportLightStationForCnnAuditList")
- @GetMapping("queryLightStationView")
- @GetMapping("exportLightStationDataCommon_deprecated")
- @GetMapping("exportLightStationDataCommon")
- @GetMapping("exportLightStationDataGXCommon")
- @GetMapping("getStationDetail")
- @GetMapping("/showAcceptanceReport.do")
- @PostMapping("acceptanceAuditOk.do")
- @GetMapping("showRecord.do")
- @PostMapping("acceptanceAuditFail.do")
- //    @GetMapping("exportLightStationTodayE.do")
- @GetMapping("exportLightStationTodayE.do")
- @GetMapping("exportCqGdtLightStationTodayE.do")
- @GetMapping("exportElecZH.do")
- @GetMapping("exportElecCmb.do")
- @GetMapping("exportElecZHBaclUp.do")
- @GetMapping("/findZhCompanyList.do")
- @GetMapping("/findZhPower.do")
- @GetMapping("/exportZhPower.do")
- @GetMapping("exportElecChd.do")
- @GetMapping("exportElecBoc.do")

## LightVersionInformationController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/light/LightVersionInformationController.java`
- @RequestMapping("/light/lightVersionInformation/")
- @GetMapping("list.do")
- @PostMapping("add.do")
- @PostMapping("revoke.do")
- @GetMapping("doExport.do")

## LightOpAuthorityZoneController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/light/LightOpAuthorityZoneController.java`
- @RequestMapping("/lightOpAuthorityZone/")
- @GetMapping("/find.do")
- @PostMapping("audiOk")
- @PostMapping("audiReject")
- @GetMapping("getData")
- @GetMapping("checkAuthListAll")
- @GetMapping("doExport.do")

## LightOpOrderFinanceController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/light/LightOpOrderFinanceController.java`
- @RequestMapping("/lightOpOrderFinance")
- @GetMapping("doList.do")
- @PostMapping(value = {"detail.do"})
- @PostMapping(value = {"audit.do"})
- @PostMapping(value = {"confirm.do"})
- @GetMapping("doExport.do")

## InverterController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/light/InverterController.java`
- @RequestMapping("inverter")
- @GetMapping("queryInverterList")
- @GetMapping("queryZHInverterList")
- @GetMapping("queryCqGdtInverterList")
- @GetMapping("queryInverterListByProvince")
- @GetMapping("exportElecSiChuan.do")
- @GetMapping("queryInverterListByCmb")
- @GetMapping("queryChdInverterList")
- @GetMapping("queryBocInverterList")

## LightCompanyInfoController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/company/LightCompanyInfoController.java`
- @RequestMapping(value = "/light/company")
- @GetMapping("queryCompanyList")
- @GetMapping("queryRelateCompanyInfo")

## LightStationEpcController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/epc/LightStationEpcController.java`
- @RequestMapping("lightStation/epc")
- @GetMapping("queryPageTable")
- @PostMapping("approval")
- @PostMapping("approvalFinal")

## CmLightMilestoneCheckController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/epc/CmLightMilestoneCheckController.java`
- @RequestMapping("/light/cmCheck/")
- @PostMapping("/checkAndAcceptPayment.do")
- @PostMapping("/checkAndAcceptPaymentUpFile.do")
- @GetMapping("/showPaymentCheckDetail.do")
- @GetMapping("/showPaymentFileDetail.do")
- @GetMapping("/showPaymentInvoiceDetail.do")
- @PostMapping("/applyPayment.do")
- @GetMapping("/showReceiptCheckDetail.do")
- @PostMapping("/checkAndAcceptReceipt.do")
- @PostMapping("/uploadVoucher.do")

## CmLightProjectController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/epc/CmLightProjectController.java`
- @RequestMapping("/light/cmProject/")
- @GetMapping("/findProjectList.do")
- @GetMapping("/doExportProject.do")
- @GetMapping("/doExport")
- @GetMapping("/getDraftProject.do")
- @GetMapping("/getProject.do")
- @GetMapping("/findFunnelList.do")
- @PostMapping("/temporaryProject.do")
- @PostMapping("/saveProject.do")
- @GetMapping("/findReceiptList.do")
- @PostMapping("/temporaryReceipt.do")
- @PostMapping("/saveReceipt.do")
- @GetMapping("/findPaymentList.do")
- @GetMapping("/findPaymentByPIdAndPartyType.do")
- @PostMapping("/temporaryPayment.do")
- @PostMapping("/savePayment.do")
- @PostMapping("/verifyProject.do")
- @PostMapping("/auditProject.do")
- @PostMapping("rejectCheckIn.do")

## CmLightContractController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/epc/CmLightContractController.java`
- @RequestMapping("/light/cmContract/")
- @GetMapping("/getContract.do")
- @PostMapping("/saveContract.do")
- @GetMapping("/findInstaller.do")
- @GetMapping("/findSupplier.do")
- @GetMapping("/findByProjectId.do")

## CHDEpcLightStationController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/dhpepc/CHDEpcLightStationController.java`
- @RequestMapping("/CHDEpcLightStation")
- @RequestMapping("queryPage")
- @GetMapping("getStationDetail")
- @GetMapping("showRecord.do")

## LightSpOpsNegativeExcitationController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/spops/LightSpOpsNegativeExcitationController.java`
- @RequestMapping("/spLedger/nagative")
- @GetMapping("findByPage")
- @GetMapping("/doExport")
- @PostMapping("audit")
- @PostMapping("batchAudit")
- @GetMapping("/downTemplate")
- @PostMapping("importData.do")
- @PostMapping("change")
- @PostMapping("batchDel.do")
- @PostMapping("del.do")
- @PostMapping("importDataForXiaoXiang.do")

## LightSpOpsSettleController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/spops/LightSpOpsSettleController.java`
- @RequestMapping("lightSpOpsSettle")
- @GetMapping("findByPage")
- @GetMapping("/doExport")
- @PostMapping("confirmSpLedger")
- @PostMapping("billPdf")
- @PostMapping("checkConfirm")
- @GetMapping("showDetails")
- @GetMapping("/doExportDetails")
- @GetMapping("/createPdfUrl")

## LightSpOpsPositiveIacController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/spops/LightSpOpsPositiveIacController.java`
- @RequestMapping("/iac/positive")
- @GetMapping("findByPage")
- @GetMapping("/doExport")
- @PostMapping("audit")
- @PostMapping("batchAudit")
- @PostMapping("update")
- @GetMapping("/downTemplate")
- @PostMapping("importData.do")
- @PostMapping("change")
- @PostMapping("importDataForXiaoXiang.do")

## LightSpOpsNegativeIacController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/spops/LightSpOpsNegativeIacController.java`
- @RequestMapping("/iac/nagative")
- @GetMapping("findByPage")
- @GetMapping("/doExport")
- @PostMapping("audit")
- @PostMapping("batchAudit")
- @GetMapping("/downTemplate")
- @PostMapping("importData.do")
- @PostMapping("change")
- @PostMapping("importDataForXiaoXiang.do")

## LightSpOpsPositiveExcitationController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/spops/LightSpOpsPositiveExcitationController.java`
- @RequestMapping("/spLedger/positive")
- @GetMapping("findByPage")
- @GetMapping("/doExport")
- @PostMapping("audit")
- @PostMapping("auditByPreliminary")
- @PostMapping("batchAudit")
- @PostMapping("batchAuditByPreliminary")
- @PostMapping("update")
- @GetMapping("/downTemplate")
- @PostMapping("importData.do")
- @PostMapping("change")
- @PostMapping("importDataForXiaoXiang.do")

## LightSpOpsSettleIacController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/spops/LightSpOpsSettleIacController.java`
- @RequestMapping("lightSpOpsSettleIac")
- @GetMapping("findByPage")
- @GetMapping("/doExport")
- @PostMapping("confirmSpLedger")
- @PostMapping("billPdf")
- @PostMapping("checkConfirm")
- @PostMapping("getStation")
- @GetMapping("doExportDetails.do")

## CmbLeasingStationController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/cmbleasing/CmbLeasingStationController.java`
- @RequestMapping("/cmbLeasingStation")
- @GetMapping("queryPage")

## PublicLiabilityInsuranceController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/PublicLiabilityInsuranceController.java`
- @RequestMapping("/publicLiabilityInsurance")
- @GetMapping("findByPage")
- @PostMapping("auditOk.do")
- @PostMapping("auditReject.do")
- @GetMapping("doExport.do")

## LightFaultFreeConfigController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/LightFaultFreeConfigController.java`
- @RequestMapping("/free/config/")
- @GetMapping("find.do")
- @PostMapping("/edit.do")

## LightOperationDepositController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/LightOperationDepositController.java`
- @RequestMapping("/light/deposit/")
- @GetMapping("find.do")
- @PostMapping("addDeposit.do")

## LightZeroCarbonOperationProviderController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/LightZeroCarbonOperationProviderController.java`
- @RequestMapping("/lightZeroCarbonOperationProvider/")
- @GetMapping("/find.do")
- @PostMapping("/auditOk.do")
- @PostMapping("/auditReject.do")
- @PostMapping("/checkAuth.do")
- @PostMapping("/stopAudiOk.do")
- @PostMapping("/stopAudiReject.do")
- @PostMapping("/stopCreate.do")
- @PostMapping("/stopUpload.do")
- @GetMapping("export.do")
- @PostMapping("findZeroStation")

## HdsLightStationController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/HdsLightStationController.java`
- @RequestMapping("/hdsLightStation/")
- @GetMapping("list.do")
- @GetMapping("export.do")

## SpecialFlagObjectController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/SpecialFlagObjectController.java`
- @RequestMapping("/specialFlagObject")
- @GetMapping("findList")
- @GetMapping("findListAll")

## LightModuleInfoController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/LightModuleInfoController.java`
- @RequestMapping("/module/info")
- @GetMapping("list.do")
- @GetMapping("get.do")
- @PostMapping("add.do")
- @PostMapping("update.do")
- @PostMapping("importData.do")
- @GetMapping("/downTemplate.do")
- @GetMapping("doExport.do")

## SocializationStationController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/SocializationStationController.java`
- @RequestMapping("/socializationStation")
- @GetMapping("/find.do")
- @GetMapping("/downTemplate")
- @PostMapping("importData.do")
- @GetMapping("export.do")
- @PostMapping("uploadZips.do")
- @PostMapping("saveImages.do")
- @GetMapping("findDetail.do")
- @PostMapping("batchDel")

## LightRepairOrderController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/LightRepairOrderController.java`
- @RequestMapping("/repair/order")
- @GetMapping("list.do")
- @PostMapping("transfer.do")
- @PostMapping("close.do")
- @GetMapping("doExport.do")

## HdsGsyLightStationController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/HdsGsyLightStationController.java`
- @RequestMapping("/hdsGsyLightStation/")
- @GetMapping("list.do")
- @GetMapping("export.do")

## LightOperationProviderExpandController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/LightOperationProviderExpandController.java`
- @RequestMapping("/lightOperationProviderExpand/")
- @GetMapping("/find.do")
- @PostMapping("/auditOk.do")
- @PostMapping("/auditReject.do")
- @PostMapping("/add.do")
- @GetMapping("/findLog.do")
- @GetMapping("/getById.do")
- @PostMapping("/modify.do")
- @GetMapping("doExport.do")

## AllRisksInsuranceController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/AllRisksInsuranceController.java`
- @RequestMapping("/allRisksInsurance")
- @GetMapping("findByPage")
- @PostMapping("auditOk.do")
- @PostMapping("auditReject.do")
- @GetMapping("doExport.do")

## LightElectricUnusualController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/LightElectricUnusualController.java`
- @RequestMapping("/lightElectricUnusual/")
- @GetMapping("list.do")
- @GetMapping("doExport.do")

## LightStationPolicyNoController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/LightStationPolicyNoController.java`
- @RequestMapping("/lightStationPolicyNo")
- @GetMapping("findByPage")
- @GetMapping("findByPageInCmb")
- @PostMapping("importData.do")
- @GetMapping("/downTemplate.do")
- @PostMapping("/delete.do")
- @GetMapping("doExport.do")
- @GetMapping("doExportInCmb.do")

## LightOperationCertificationController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/LightOperationCertificationController.java`
- @RequestMapping("/lightOperationCertification/")
- @PostMapping("/list.do")
- @PostMapping("/audiOkCertification")
- @PostMapping("/audiRejectCertification")
- @GetMapping("doExport.do")

## LightSettleBillsController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/LightSettleBillsController.java`
- @RequestMapping("/settle/bille")
- @GetMapping("list.do")
- @GetMapping("doExport.do")

## LightStationInsuranceController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/LightStationInsuranceController.java`
- @RequestMapping("/lightStationInsurance")
- @GetMapping("doList.do")
- @GetMapping("doExport.do")

## OperationMaintenanceConfigController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/OperationMaintenanceConfigController.java`
- @RequestMapping("/operationMaintenanceConfig")
- @GetMapping("findByPage")
- @PostMapping("/audiOk.do")
- @PostMapping("/audiReject.do")
- @PostMapping("/addData.do")
- @PostMapping("/findCompany")
- @GetMapping("doExport.do")

## LightNefficientStationController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/LightNefficientStationController.java`
- @RequestMapping("/lightNefficientStation")
- @GetMapping("list.do")
- @GetMapping("doExport.do")
- @PostMapping("transferOrder")
- @PostMapping("closeOrder")

## LightNefficientController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/LightNefficientController.java`
- @RequestMapping("/lightNefficient")
- @GetMapping("list.do")
- @GetMapping("doExport.do")
- @PostMapping("importData.do")
- @PostMapping("checkData")
- @GetMapping("/downTemplate.do")

## LightOpStaffController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/LightOpStaffController.java`
- @RequestMapping("/light/staff/")
- @GetMapping("hdsfind.do")
- @GetMapping("get.do")
- @PostMapping("/examine.do")
- @PostMapping("/twoExamine.do")
- @GetMapping("export.do")

## LightFaultCodeRuleController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/LightFaultCodeRuleController.java`
- @RequestMapping("/fault/rule")
- @GetMapping("list.do")
- @PostMapping("add.do")
- @PostMapping("update.do")
- @PostMapping("delete.do")
- @GetMapping("doExport.do")
- @PostMapping("importData.do")
- @GetMapping("/downTemplate.do")

## HdsMemberRoleController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/HdsMemberRoleController.java`
- @RequestMapping("/hdsMemberRole/")
- @GetMapping("/find.do")
- @PostMapping("/addData.do")
- @GetMapping("/freeze.do")
- @GetMapping("/enable.do")
- @GetMapping("doExport.do")

## LightWorkOrderTypeController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/LightWorkOrderTypeController.java`
- @RequestMapping("/lightWorkOrderType/")
- @GetMapping("/find.do")
- @PostMapping("/add.do")
- @PostMapping("/edit.do")
- @PostMapping("/delete.do")
- @GetMapping("doExport.do")

## LightWorkOrderController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/LightWorkOrderController.java`
- @RequestMapping("/work/order")
- @GetMapping("list.do")
- @GetMapping("detail.do")
- @GetMapping("doExport.do")
- @PostMapping("setTime.do")
- @GetMapping("getTime.do")
- @PostMapping("addProcess.do")
- @PostMapping("audiOk.do")
- @PostMapping("audiReject.do")

## BusinessCooperationIntentionController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/BusinessCooperationIntentionController.java`
- @RequestMapping("/light/operation/businessCooperationIntention")
- @PostMapping("/insert")
- @GetMapping("/findStation")
- @GetMapping("/getDetail")
- @GetMapping("/findWeather")
- @GetMapping("/findInverterData")
- @GetMapping("/findScreenData")
- @GetMapping("/findMonthElecData")
- @GetMapping("/findMapData")

## LightCsOrderController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/LightCsOrderController.java`
- @RequestMapping("/cs/order")
- @GetMapping("list.do")
- @GetMapping("checkCloseTime")
- @GetMapping("detail.do")
- @PostMapping("add.do")
- @PostMapping("transfer.do")
- @PostMapping("close.do")
- @GetMapping("doExport.do")
- @GetMapping("/getByStationCode.do")

## LightWorkOrderZhServiceController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/LightWorkOrderZhServiceController.java`
- @RequestMapping("/lightWorkOrderZhService")
- @GetMapping("findByPage")
- @GetMapping("doExport.do")

## LightOpContractRecordController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/LightOpContractRecordController.java`
- @RequestMapping("/lightOpContractRecord/")
- @GetMapping("/find.do")
- @GetMapping("doExport.do")

## LightFaultLevelController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/LightFaultLevelController.java`
- @RequestMapping("/light/fault/")
- @GetMapping("find.do")
- @GetMapping("get.do")
- @GetMapping("leveltype.do")
- @PostMapping("/add.do")
- @PostMapping("/edit.do")
- @PostMapping("/delete.do")
- @GetMapping("doExport.do")

## LightCloseReasonController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/LightCloseReasonController.java`
- @RequestMapping("/close/reason")
- @GetMapping("list.do")
- @GetMapping("listAll.do")
- @PostMapping("delete.do")
- @PostMapping("addOrUpdate.do")
- @GetMapping("doExport.do")

## LightRepairOrderReasonController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/LightRepairOrderReasonController.java`
- @RequestMapping("/repair/order")
- @GetMapping("find.do")
- @GetMapping("get.do")
- @PostMapping("add.do")
- @PostMapping("update.do")
- @PostMapping("delete.do")

## CapitalDataManagementController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/CapitalDataManagementController.java`
- @RequestMapping("/capitalDataManagement")
- @GetMapping("findByPage")
- @PostMapping("changeData")
- @GetMapping("doExport.do")

## LightTrippingOperationController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/LightTrippingOperationController.java`
- @RequestMapping("/lightTrippingOperation")
- @GetMapping("list.do")
- @GetMapping("doExport.do")
- @PostMapping("transferOrder")
- @PostMapping("closeOrder")

## LightFaultDictionaryController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/LightFaultDictionaryController.java`
- @RequestMapping("/lightFaultDictionary/")
- @GetMapping("/get.do")
- @GetMapping("/find.do")
- @GetMapping("/first.do")
- @GetMapping("/second.do")
- @GetMapping("/third.do")
- @PostMapping("/add.do")
- @PostMapping("/edit.do")
- @PostMapping("/delete.do")
- @GetMapping("/findFirst.do")
- @GetMapping("/findSecond.do")
- @GetMapping("/findThird.do")
- @PostMapping("/sort.do")
- @GetMapping("doExport.do")

## LightStationInverterChangeController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/LightStationInverterChangeController.java`
- @RequestMapping("/lightStationInverterChange")
- @GetMapping("list.do")
- @PostMapping("auditOk")
- @PostMapping("reject")
- @GetMapping("doExport.do")
- @PostMapping("getLog")

## LightOperationCapitalController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/LightOperationCapitalController.java`
- @RequestMapping("/lightOperationCapital")
- @GetMapping("/findParams.do")
- @PostMapping("/create.do")
- @GetMapping("/detail.do")
- @GetMapping("/findByPoily.do")
- @GetMapping("/findByPartner.do")
- @GetMapping("/findByContract.do")
- @GetMapping("/findByLog.do")
- @PostMapping("/auditPass.do")
- @PostMapping("/auditReject.do")
- @PostMapping("/addContract.do")
- @GetMapping("export.do")

## SocializationContractInfoController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/SocializationContractInfoController.java`
- @RequestMapping("/socializationContractInfo")
- @GetMapping("findByPage")
- @PostMapping("add.do")
- @PostMapping("submitTerminate.do")
- @PostMapping("auditTerminate.do")
- @PostMapping("auditTerminateReject.do")
- @PostMapping("uploadTerminateAgreement.do")
- @GetMapping("export.do")

## OperationAlarmRateController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/OperationAlarmRateController.java`
- @RequestMapping("/operationAlarmRate/")
- @GetMapping("/find.do")
- @GetMapping("doExport.do")

## LightOperationProviderController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/LightOperationProviderController.java`
- @RequestMapping("/lightOperationProvider/")
- @GetMapping("/find.do")
- @GetMapping("/get.do")
- @PostMapping("/auditOk.do")
- @PostMapping("/auditReject.do")
- @PostMapping("/expansion.do")
- @PostMapping("/checkAuth.do")
- @PostMapping("/getAuth.do")
- @PostMapping("/checkAuthContractStatus.do")
- @PostMapping("/renewalAudiOk.do")
- @PostMapping("/stopAudiOk.do")
- @PostMapping("/renewalAudiReject.do")
- @PostMapping("/stopAudiReject.do")
- @PostMapping("/renewalCreate.do")
- @PostMapping("/stopCreate.do")
- @PostMapping("/stopUpload.do")
- @PostMapping("/checkAuthEnable.do")
- @GetMapping("export.do")
- @PostMapping("/remind.do")

## LightOperationRegionBlockController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/bidding/LightOperationRegionBlockController.java`
- @RequestMapping("/light/operation/region-block")
- @GetMapping("page")
- @GetMapping("get")
- @PostMapping("add")
- @PostMapping("edit")
- @PostMapping("delete")
- @GetMapping("areas")
- @PostMapping("check-area-conflict")
- @PostMapping("count-stations")
- @PostMapping("import")
- @GetMapping("template")
- @GetMapping("export-template")
- @GetMapping("export")
- @GetMapping("region-tree")
- @PostMapping("release")
- @GetMapping("release/page")
- @GetMapping("release/get")
- @GetMapping("release/history")

## LightOperationRatingController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/bidding/LightOperationRatingController.java`
- @RequestMapping("/light/operation/bidding/rating")
- @GetMapping("table/page")
- @GetMapping("table/get/{id}")
- @PostMapping("table/add")
- @PostMapping("table/edit")
- @DeleteMapping("table/delete/{id}")
- @PostMapping("table/validate-weights")
- @PostMapping("table/update-status")
- @PostMapping("table/copy")
- @GetMapping("item/page")
- @GetMapping("item/list-by-table/{tableId}")
- @GetMapping("item/config-by-table/{tableId}")
- @GetMapping("item/get/{id}")
- @GetMapping("item/config/{id}")
- @PostMapping("item/add")
- @PostMapping("item/add-with-config")
- @PostMapping("item/edit")
- @PostMapping("item/edit-with-config")
- @DeleteMapping("item/delete/{id}")
- @PostMapping("item/batch-update-sort")
- @PostMapping("calculate/final-score")
- @PostMapping("calculate/preview-score")

## LightOperationBiddingRegistrationController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/bidding/LightOperationBiddingRegistrationController.java`
- @RequestMapping("/light/operation/bidding/registration")
- @GetMapping("pendingAuditPage")
- @GetMapping("auditedPage")
- @GetMapping("approved/list")
- @GetMapping("approved/details")
- @GetMapping("get")
- @PostMapping("audit")
- @PostMapping("lock/{id}")
- @PostMapping("unlock/{id}")
- @GetMapping("yearly-closed-rate")
- @GetMapping("export/registrations")

## LightOperationBiddingRatingController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/bidding/LightOperationBiddingRatingController.java`
- @RequestMapping("/light/operation/bidding/project/rating")
- @GetMapping("/pending")
- @GetMapping("/completed")
- @PostMapping("/table/bind")
- @GetMapping("/table/{projectId}")
- @GetMapping("/record/my")
- @GetMapping("/record/page")
- @GetMapping("/record/{id}")
- @PostMapping("/record/save-draft")
- @PostMapping("/record/submit")
- @GetMapping("/summary/page")
- @GetMapping("/summary/registration/{registrationId}")
- @GetMapping("/summary/ranking/{projectId}")
- @GetMapping("/record/project/{projectId}")

## LightOperationBiddingProjectController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/bidding/LightOperationBiddingProjectController.java`
- @RequestMapping("/light/operation/bidding/project")
- @GetMapping("myPage")
- @GetMapping("managementPage")
- @GetMapping("page")
- @GetMapping("get")
- @PostMapping("saveOrUpdate")
- @PostMapping("submit")
- @PostMapping("publish")
- @PostMapping("abandon")
- @PostMapping("delete")
- @GetMapping("/selectEvaluator")
- @PostMapping("/delay")
- @GetMapping("/announcement/page")
- @GetMapping("/announcement/get")
- @GetMapping("/preview-announcement/{projectId}")
- @PostMapping("/confirm")
- @GetMapping("/region-blocks")
- @GetMapping("export/myProjects")
- @GetMapping("export")

## LightOperationSolutionController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationSolutionController.java`
- @RequestMapping("/light/operation/solution")
- @GetMapping("page")
- @GetMapping("get")
- @PostMapping("add")
- @PostMapping("edit")
- @PostMapping("delete")
- @GetMapping("list")

## LightOperationStationTagDefinitionController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationStationTagDefinitionController.java`
- @RequestMapping("/light/operation/stationTag/definitions")
- @GetMapping("page")
- @GetMapping("list")
- @GetMapping("available")
- @GetMapping("{id}")
- @PostMapping
- @PostMapping("edit")
- @PostMapping("updateStatus")
- @GetMapping("check-name")
- @GetMapping("{id}/records")
- @PostMapping("bind")
- @PostMapping("delete")
- @GetMapping("export")

## LightOperationWorkOrderZhaoYinController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationWorkOrderZhaoYinController.java`
- @RequestMapping("/light/operation/workOrder/zhaoYin")
- @GetMapping("loginUser/isSubCenterUser")
- @GetMapping("page")
- @GetMapping("/handled/page")
- @GetMapping("getByOrderCode/{orderCode}")
- @GetMapping("list")
- @GetMapping("to-dispatch")
- @PostMapping("{orderCode}/dispatch")
- @GetMapping("to-audit")
- @GetMapping("count")
- @PostMapping("{orderCode}/audit-pass")
- @PostMapping("batch-audit-pass")
- @PostMapping("batch-dispatch")
- @PostMapping("audit-reject")
- @PostMapping("submit")
- @PostMapping("/handle")
- @GetMapping("my-submitted")
- @PostMapping("/close")
- @GetMapping("efficiency-op")
- @GetMapping("efficiency-total")
- @GetMapping("/appeal/list")
- @PostMapping("/appeal/audit")
- @GetMapping("/appeal/pending")
- @GetMapping("/appeal/audited")
- @GetMapping("/export")
- @GetMapping("/efficiency/export")
- @PostMapping("/process-record/add")

## LightOperationWorkOrderController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationWorkOrderController.java`
- @RequestMapping("/light/operation/workOrder")
- @GetMapping("loginUser/isSubCenterUser")
- @GetMapping("page")
- @GetMapping("/handled/page")
- @GetMapping("getByOrderCode/{orderCode}")
- @GetMapping("list")
- @GetMapping("to-dispatch")
- @PostMapping("{orderCode}/dispatch")
- @GetMapping("to-audit")
- @GetMapping("count")
- @PostMapping("{orderCode}/audit-pass")
- @PostMapping("batch-audit-pass")
- @PostMapping("batch-dispatch")
- @PostMapping("audit-reject")
- @PostMapping("submit")
- @PostMapping("/handle")
- @GetMapping("my-submitted")
- @PostMapping("/close")
- @GetMapping("efficiency-op")
- @GetMapping("efficiency-total")
- @GetMapping("/appeal/list")
- @PostMapping("/appeal/audit")
- @GetMapping("/appeal/pending")
- @GetMapping("/appeal/audited")
- @GetMapping("/export")
- @GetMapping("/efficiency/export")
- @PostMapping("/process-record/add")
- @PostMapping("/import")
- @GetMapping("/downloadTemplate")
- @GetMapping("/appeal/getRoleList")

## LightOperationStationInsuranceController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationStationInsuranceController.java`
- @RequestMapping("/light/operation/station-insurance")
- @GetMapping("/page")
- @GetMapping("/list")
- @PostMapping("/create")
- @PostMapping("/edit")
- @PostMapping("/delete")
- @GetMapping("/export")
- @PostMapping("/import")
- @GetMapping("/downloadTemplate")

## LightOperationExamController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationExamController.java`
- @RequestMapping("/light/operation/exam")
- @GetMapping("page")
- @GetMapping("get")
- @PostMapping("add")
- @PostMapping("edit")
- @PostMapping("publish")
- @PostMapping("end")
- @PostMapping("delete")
- @PostMapping("user-page")
- @GetMapping("get-exam-paper")
- @GetMapping("statistics")
- @GetMapping("statistics/person-details")

## LightOperationChatController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationChatController.java`
- @RequestMapping("/light/operation/ai/chat")
- @PostMapping("/message")
- @PostMapping(value = "/stream", produces = MediaType.TEXT_EVENT_STREAM_VALUE)
- @GetMapping("/history")
- @PostMapping("/history/clear")
- @GetMapping("/history/page")
- @GetMapping("/question-templates")
- @PostMapping(value = "/regenerate", produces = MediaType.TEXT_EVENT_STREAM_VALUE)

## LightOperationUserController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationUserController.java`
- @RequestMapping("/light/operation/app/user")
- @GetMapping("/info")
- @PostMapping("/changePassword")

## LightOperationExternalDiagnosisTaskController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationExternalDiagnosisTaskController.java`
- @RequestMapping("/light/operation/external-diagnosis-task")
- @PostMapping("/create")
- @GetMapping("/page")
- @PostMapping("/update")
- @GetMapping("/{id}")
- @PostMapping("/import-stations")
- @PostMapping("/import-inverters")
- @PostMapping("/oss/upload-signature")
- @PostMapping("/oss/upload-complete")
- @GetMapping("/template/station")
- @GetMapping("/template/inverter")
- @GetMapping("/template/inverter-record")
- @PostMapping("/start-analysis")
- @GetMapping("/analysis-result")
- @GetMapping("/station/page")
- @GetMapping("/station/diagnosis/page")

## LightOperationExamAnswerController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationExamAnswerController.java`
- @RequestMapping("/light/operation/exam/answer")
- @GetMapping("getOrCreate")
- @GetMapping("getDetail")
- @GetMapping("getByExamAndUser")
- @PostMapping("updateProgress")
- @PostMapping("submit")
- @GetMapping("listByExam")

## LightOperationInspectionConfigController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationInspectionConfigController.java`
- @RequestMapping("/light/operation/inspection-config")
- @GetMapping("page")
- @GetMapping("get")
- @PostMapping("add")
- @PostMapping("edit")
- @PostMapping("delete")
- @GetMapping("list")
- @PostMapping("updateStatus")

## LightOperationQuestionController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationQuestionController.java`
- @RequestMapping("/light/operation/question")
- @GetMapping("page")
- @GetMapping("get")
- @PostMapping("add")
- @PostMapping("edit")
- @GetMapping("listByBank")
- @PostMapping("delete")

## LightOperationMessageController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationMessageController.java`
- @RequestMapping("/light/operation/message")
- @GetMapping("/page")
- @GetMapping("/detail")
- @PostMapping("/create")
- @PostMapping("/create-and-send")
- @PostMapping("/send")
- @PostMapping("/mark-read")
- @PostMapping("/batch-mark-read")
- @GetMapping("/unread-count")
- @GetMapping("/all/page")
- @GetMapping("/my-messages")
- @PostMapping("/update")
- @PostMapping("/update-and-send")

## LightOperationStationGuaranteeTargetController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationStationGuaranteeTargetController.java`
- @RequestMapping("/light/operation/guarantee-target")
- @GetMapping("/page")
- @GetMapping("/detail")
- @PostMapping("/create")
- @PostMapping("/update")
- @PostMapping("/import")
- @GetMapping("/downloadTemplate")
- @DeleteMapping("/{id}")
- @DeleteMapping("/station/{stationCode}")

## LightOperationQuestionBankController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationQuestionBankController.java`
- @RequestMapping("/light/operation/question/bank")
- @GetMapping("page")
- @GetMapping("get")
- @PostMapping("add")
- @PostMapping("edit")
- @PostMapping("delete")
- @GetMapping("listByCategory")
- @GetMapping("list")

## LightOperationStationElecBillController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationStationElecBillController.java`
- @RequestMapping("/light/operation/station-elec-bill")
- @GetMapping("/page")
- @GetMapping("/bill-only/page")
- @GetMapping("/detail")
- @PostMapping("/update")
- @GetMapping("/summary")
- @GetMapping("/export/count")
- @GetMapping("/export")
- @GetMapping("/export/async")
- @GetMapping("/export/list")
- @PostMapping("/export/cancel")
- @GetMapping("/project-company/search")
- @GetMapping("/substation/search")
- @PostMapping("/import")
- @GetMapping("/import/template")
- @GetMapping("/subCenterPage")
- @GetMapping("exportSunCenter.do")
- @GetMapping("/projectCompanyPage")
- @GetMapping("exportProjectCompany.do")
- @GetMapping("/specialFlagPage")
- @GetMapping("exportSpecialFlag.do")
- @GetMapping("/projectCompanySubstationPage")
- @GetMapping("exportProjectCompanySubstation")
- @GetMapping("/findStreet")
- @PostMapping("/migration/import")
- @GetMapping("/migration/template")

## LightOperationStationAnnualGuaranteeController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationStationAnnualGuaranteeController.java`
- @RequestMapping("/light/operation/annual-guarantee")
- @GetMapping("/page")
- @GetMapping("/stat")
- @GetMapping("/page/export")
- @GetMapping("/history")
- @GetMapping("/history/export")
- @GetMapping("/third-party/page")
- @GetMapping("/third-party/stat")
- @GetMapping("/third-party/page/export")
- @GetMapping("/third-party/history")
- @GetMapping("/third-party/history/export")

## LightOperationStationController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationStationController.java`
- @RequestMapping("/light/operation/station")
- @GetMapping("page")
- @GetMapping("get")
- @GetMapping("getByStationCode")
- @GetMapping("list")
- @GetMapping("/special-flag/data")
- @PostMapping("location/update")
- @PostMapping("info/update")
- @GetMapping("inverter/mppt-data")
- @GetMapping("inverter/list")
- @GetMapping("inverter/data")
- @GetMapping("inverter/elec-data")
- @PostMapping("inverter/mppt/update")
- @GetMapping("inverter/weather-radiation-data")
- @GetMapping("station/rent/months")
- @GetMapping("station/rent/by-station-code")
- @GetMapping("/export")

## LightOperationWorkOrderConfigController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationWorkOrderConfigController.java`
- @RequestMapping("/light/operation/work-order-config")
- @GetMapping("page")
- @GetMapping("get")
- @PostMapping("add")
- @PostMapping("edit")
- @PostMapping("delete")
- @GetMapping("list")
- @PostMapping("updateStatus")

## LightOperationDashboardController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationDashboardController.java`
- @RequestMapping("/light/operation/dashboard")
- @PostMapping("/queryYearElecByRegion")
- @PostMapping("/queryMonthlyElecByYear")
- @PostMapping("/queryDailyElecByMonth")
- @PostMapping("/getRegionCoverageStatistics")
- @PostMapping("/getConnectedStationStatistics")
- @PostMapping("/getElectricityStatistics")
- @PostMapping("/getTopCitiesByStationCount")
- @PostMapping("/getStationStateStatistics")
- @PostMapping("/getTopEfficiencyStations")
- @PostMapping("/getWorkOrderStatistics")
- @GetMapping("/getStationDetail/{stationCode}")
- @GetMapping("/searchStationsByKeyword/{keyword}")
- @PostMapping("/getStationCountByRegion")
- @PostMapping("/getTodayInverterPowerTrendData")

## LightOperationFaultSolutionController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationFaultSolutionController.java`
- @RequestMapping("/light/operation/fault-solution")
- @GetMapping("page")
- @GetMapping("get")
- @PostMapping("add")
- @PostMapping("edit")
- @PostMapping("delete")
- @GetMapping("list")
- @GetMapping("by-fault")
- @GetMapping("check-items")

## LightOperationSolutionCategoryController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationSolutionCategoryController.java`
- @RequestMapping("/light/operation/solution-category")
- @PostMapping("/create")
- @PostMapping("/update/{id}")
- @GetMapping("/detail/{id}")
- @GetMapping("/list")
- @GetMapping("/children/{parentId}")
- @GetMapping("/tree")
- @GetMapping("/path/{path}")
- @PostMapping("/delete/{id}")

## LightOperationInspectionPlanController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationInspectionPlanController.java`
- @RequestMapping("/light/operation/inspection/plan")
- @GetMapping("page")
- @GetMapping("get")
- @PostMapping("create")
- @PostMapping("update")
- @GetMapping("list")
- @PostMapping("delete")

## LightOperationZeroCarbonEStationController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationZeroCarbonEStationController.java`
- @RequestMapping("/light/operation/zero-carbon/station/e")
- @GetMapping("page")
- @GetMapping("getByStationCode")
- @GetMapping("sku/list")
- @GetMapping("weather-radiation-data")
- @GetMapping("weather")

## LightOperationDictController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationDictController.java`
- @RequestMapping("/light/operation/dict")
- @GetMapping("/items/{dictCode}")
- @PostMapping("/items/batch")
- @GetMapping("/page")
- @GetMapping("/list")
- @GetMapping("/{id}")
- @GetMapping("/code/{dictCode}")
- @PostMapping
- @PostMapping("/update")
- @PostMapping("/delete/{id}")
- @GetMapping("/items/page")
- @GetMapping("/items/list")
- @GetMapping("/items/{id}")
- @GetMapping("/items/dict/{dictId}")
- @PostMapping("/items")
- @PostMapping("/items/update")
- @PostMapping("/items/delete/{id}")
- @GetMapping("/items/map/{dictCode}")
- @GetMapping("/items/maps")

## LightOperationElecPriceController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationElecPriceController.java`
- @RequestMapping("/light/operation/elec-price")
- @GetMapping("/detail")
- @PostMapping("/create")
- @PostMapping("/update")
- @GetMapping("/by-year")
- @PostMapping("/import")
- @GetMapping("/downloadTemplate")
- @GetMapping("/export")

## LightOperationInspectionWorkOrderController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationInspectionWorkOrderController.java`
- @RequestMapping("/light/operation/inspection/work-order")
- @GetMapping("page")
- @GetMapping("get")
- @GetMapping("list")
- @GetMapping("statistics")
- @GetMapping("statistics/plan")
- @GetMapping("statistics/total")
- @GetMapping("count")
- @GetMapping("/export")

## LightOperationEnergyStorageStationController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationEnergyStorageStationController.java`
- @RequestMapping("/light/operation/energy-storage/station")
- @GetMapping("page")
- @GetMapping("summary")
- @GetMapping("details")
- @GetMapping("data-stat")
- @GetMapping("core-metric")
- @GetMapping("pcs/list")
- @GetMapping("device-cluster")
- @GetMapping("curve")
- @GetMapping("alarm/page")
- @GetMapping("battery/analysis")
- @GetMapping("weather")

## LightOperationPracticeController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationPracticeController.java`
- @RequestMapping("/light/operation/exam/practice")
- @PostMapping("/generate")
- @GetMapping("/list")
- @GetMapping("/detail")
- @PostMapping("/updateProgress")
- @PostMapping("/complete")
- @PostMapping("/delete")
- @GetMapping("/info")

## LightOperationFaultController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationFaultController.java`
- @RequestMapping("/light/operation/fault")
- @GetMapping("page")
- @GetMapping("get")
- @PostMapping("add")
- @PostMapping("edit")
- @PostMapping("delete")
- @GetMapping("list")
- @PostMapping("updateStatus")
- @PostMapping("updateSecondStatus")
- @GetMapping("rootFaults")
- @GetMapping("children")

## LightOperationReportConfigController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationReportConfigController.java`
- @RequestMapping("/light/operation/report-config")
- @GetMapping("/page")
- @GetMapping("/detail")
- @PostMapping("/create")
- @PostMapping("/update")
- @PostMapping("/delete")
- @PostMapping("/update-status")
- @GetMapping("/data-fields/list-by-type")

## LightOperationQuestionCategoryController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationQuestionCategoryController.java`
- @RequestMapping("/light/operation/question/category")
- @GetMapping("page")
- @GetMapping("get")
- @PostMapping("add")
- @PostMapping("edit")
- @PostMapping("delete")
- @GetMapping("list")

## LightOperationReportCenterController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationReportCenterController.java`
- @RequestMapping("/light/operation/report-center")
- @GetMapping("/my-config-list")
- @PostMapping("/get-by-config")
- @PostMapping("/export")

## LightOperationZeroCarbonStationController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/lightoperation/v2/LightOperationZeroCarbonStationController.java`
- @RequestMapping("/light/operation/zero-carbon/station")
- @GetMapping("page")
- @GetMapping("generation/page")
- @GetMapping("summary")
- @GetMapping("details")
- @GetMapping("sku/list")
- @GetMapping("device/fault/list")
- @GetMapping("device/fault/stat")
- @GetMapping("device/fault/stat/monthly-last12")
- @GetMapping("inverter/realtime")
- @GetMapping("inverter/curve")
- @GetMapping("weather-radiation-data")
- @GetMapping("weather")

## MemberAddressController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/member/MemberAddressController.java`
- @RequestMapping("/member/address")
- @GetMapping("/get.do")
- @GetMapping("/mark_as_default.do")
- @GetMapping("/list.do")
- @PostMapping("/saveAddress.do")
- @GetMapping("/regionList.do")

## YantuAutomaticallyDesignTemporaryStorageController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/yantu/YantuAutomaticallyDesignTemporaryStorageController.java`
- @RequestMapping("/yantuAutomaticallyDesignTemporaryStorage/")
- @GetMapping("/find.do")

## DictTypeController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/yantu/DictTypeController.java`
- @RequestMapping("/yantuDict")
- @GetMapping("/selectDictValueByCode.do")

## OperationHistorySettleController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/historysettle/OperationHistorySettleController.java`
- @RequestMapping("/operationHistorySettle")
- @PostMapping("import.do")

## SpOldbackListsController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/repairs/SpOldbackListsController.java`
- @RequestMapping("/repairs/spOldbackLists")
- @PostMapping("/getPage")
- @GetMapping("/getInfoById")
- @GetMapping("/dzjOrderExport")

## SpOrderController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/repairs/SpOrderController.java`
- @RequestMapping("/repairs/spOrder")
- @PostMapping("/serviceCancelOrder")
- @PostMapping("/getServicePITPage")
- @PostMapping("/addServicePIT")
- @PostMapping("/updateServicePIT")
- @PostMapping("/delServicePIT")
- @PostMapping("/getInfoServicePIT")
- @PostMapping("/submitServicePIT")
- @PostMapping("/approvalServicePIT")
- @GetMapping("/getServicePITPage/export")
- @PostMapping("/getRrsBuyLossPage")
- @PostMapping("/addRrsBuyLoss")
- @PostMapping("/updateRrsBuyLoss")
- @PostMapping("/submitRrsBuyLoss")
- @GetMapping("/getRrsBuyLossPage/export")
- @PostMapping("/getInfoById")

## CdMaterialSubstituteController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/repairs/CdMaterialSubstituteController.java`
- @RequestMapping("/repairs/cdMaterialSubstitute")
- @PostMapping("/getPage")
- @PostMapping("/delete")
- @PostMapping("/add")
- @PostMapping("/update")
- @PostMapping("/export")

## SpOrderBackController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/repairs/SpOrderBackController.java`
- @RequestMapping("/repairs/spOrderBack")
- @PostMapping("/getPage")
- @GetMapping("/getPage/export")
- @GetMapping("/getInfoById")
- @PostMapping("/submitOrder")
- @PostMapping("/submitOrderPay")

## SpAccountsPayableController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/repairs/SpAccountsPayableController.java`
- @RequestMapping("/repairs/spAccountsPayable")
- @GetMapping("findByPage")
- @GetMapping("getPdfUrl.do")
- @GetMapping("findDetail.do")
- @GetMapping("confirmSettle.do")

## SpOldbackListsDetailController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/repairs/SpOldbackListsDetailController.java`
- @RequestMapping("/repairs/spOldbackListsDetail")
- @PostMapping("/getSupplierPage")
- @PostMapping("/getDutyAuditPage")
- @PostMapping("/judgeResponsibilityInfo")
- @PostMapping("/dutyAuditSubmit")
- @GetMapping("/export")

## WoPartController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/repairs/WoPartController.java`
- @RequestMapping("/repairs/woPart")
- @PostMapping("/orderWoPartPage")
- @PostMapping("/orderWoPartPageAndFile")

## SpSettlementDataController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/repairs/SpSettlementDataController.java`
- @RequestMapping("/repairs/spSettlementData")
- @PostMapping("/getPage")

## CdWarehouseAddressController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/repairs/CdWarehouseAddressController.java`
- @RequestMapping("/repairs/cdWarehouseAddress")
- @PostMapping("/getAllList")
- @PostMapping("/getList")
- @GetMapping("/getInfoById")
- @PostMapping("/save")
- @PostMapping("/update")
- @PostMapping("/delete")
- @PostMapping("/updateDefault")
- @GetMapping("/getCdWarehouseAndAddressByMemberID")

## SpOrderBorrowController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/repairs/SpOrderBorrowController.java`
- @RequestMapping("/repairs/spOrderBorrow")
- @PostMapping("/getPage")
- @GetMapping("/getInfoById")
- @PostMapping("/findProviderList")
- @PostMapping("/zxjlApproval")
- @PostMapping("/zbApproval")
- @GetMapping("/orderBorrow/export")

## SpAdvanceClearController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/repairs/SpAdvanceClearController.java`
- @RequestMapping("/repairs/spAdvanceClear")
- @PostMapping("/getPage")
- @GetMapping("/getInfoById")
- @GetMapping("/getInfoByOrderNo")
- @PostMapping("/save")
- @PostMapping("/update")
- @GetMapping("/submitOrder")
- @GetMapping("/delete")
- @PostMapping("/centerApproval")
- @PostMapping("/businessDepartmentApproval")
- @PostMapping("/financeApproval")
- @GetMapping("/export")

## CdBranchInfoController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/repairs/CdBranchInfoController.java`
- @RequestMapping("/repairs/cdBranchInfo")
- @PostMapping("/getPage")
- @PostMapping("/delete")
- @PostMapping("/add")
- @PostMapping("/update")

## SpAccountsReceivableController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/repairs/SpAccountsReceivableController.java`
- @RequestMapping("/repairs/spAccountsReceivable")
- @GetMapping("findByPage")
- @GetMapping("getPdfUrl.do")
- @GetMapping("findDetail.do")
- @GetMapping("confirmSettle.do")

## RepairsAndRrsController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/repairs/RepairsAndRrsController.java`
- @RequestMapping("/repairs/repairsAndRrs")
- @PostMapping(value = "/receiveRrsOrderInfo",
- @PostMapping("/repairsToRrsTest")

## CdDictDateController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/repairs/CdDictDateController.java`
- @RequestMapping("/repairs/cdDictData")
- @PostMapping("/getPage")
- @PostMapping("/getList")
- @GetMapping("/getInfoById")
- @PostMapping("/save")
- @PostMapping("/update")
- @PostMapping("/delete")
- @GetMapping("doExport.do")

## SpStoreageController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/repairs/SpStoreageController.java`
- @RequestMapping("/repairs/spStoreage")
- @PostMapping("/getPage")
- @PostMapping("/getInfoById")
- @PostMapping("/export")
- @PostMapping("/getStoreage")
- @PostMapping("/getStoreageTotal")

## CdWarehouseController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/repairs/CdWarehouseController.java`
- @RequestMapping("/repairs/cdWarehouse")
- @PostMapping("/getPage")
- @PostMapping("/delete")
- @PostMapping("/add")
- @PostMapping("/update")
- @PostMapping("/export")
- @PostMapping("/list")
- @GetMapping("/getCdWarehouseByMemberID")
- @GetMapping("/serviceProviderSyncJob")
- @GetMapping("/serviceSupplierSyncJob")

## CdPosController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/repairs/CdPosController.java`
- @RequestMapping("/repairs/cdPos")
- @PostMapping("/getPage")
- @PostMapping("/getList")
- @PostMapping("/delete")
- @PostMapping("/add")
- @PostMapping("/update")
- @PostMapping("/export")

## SpQualityInspectController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/repairs/SpQualityInspectController.java`
- @RequestMapping("/repairs/spQualityInspect")
- @PostMapping("/getPage")
- @PostMapping("/getList")
- @PostMapping("/delete")
- @PostMapping("/add")
- @PostMapping("/update")
- @PostMapping("/submit")
- @PostMapping("/export")
- @GetMapping("/getInfoById")

## CdMaterialController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/repairs/CdMaterialController.java`
- @RequestMapping("/repairs/cdMaterial")
- @PostMapping("/getPage")
- @PostMapping("/getList")
- @PostMapping("/synchronousRrsMaterialJob")
- @PostMapping("/delete")
- @PostMapping("/add")
- @PostMapping("/update")
- @PostMapping("/export")
- @GetMapping("/downTemplate")
- @RequestMapping(value = "/importData", method = RequestMethod.POST)

## SpInverterInfoController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/repairs/SpInverterInfoController.java`
- @RequestMapping("/repairs/spInverterInfo")
- @PostMapping("/getPage")
- @GetMapping("/getInfoById")
- @GetMapping("/getInfoByOrderNo")
- @PostMapping("/save")
- @PostMapping("/update")
- @GetMapping("/submitOrder")
- @GetMapping("/delete")
- @GetMapping("/withdrawn")
- @PostMapping("/supplierApproval")
- @PostMapping("/operationAndMaintenanceVendorsPost")
- @PostMapping("/supplierSign")
- @PostMapping("/supplierDelivery")
- @PostMapping("/operationAndMaintenanceVendorsSign")
- @GetMapping("/export")

## SpTranController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/repairs/SpTranController.java`
- @RequestMapping("/repairs/spTran")
- @PostMapping("/getPage")
- @PostMapping("/getPageTwoStore")
- @GetMapping("/getPage/export")
- @GetMapping("/getPage/exportCenter")
- @PostMapping("/update")
- @PostMapping("/customsDocumentsWarehouse")
- @PostMapping("/getInfo")
- @GetMapping("/out/outInfoBytranId")
- @PostMapping("/updateInfo")
- @PostMapping("/updateFile")
- @PostMapping("/updateDetail")
- @PostMapping("/out/getPage")
- @GetMapping("/out/export")
- @GetMapping("/out/cancelOutbound")
- @PostMapping("/getPageExpressOut")

## SpSupplierPartsCostController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/repairs/SpSupplierPartsCostController.java`
- @RequestMapping("/repairs/spSupplierPartsCost")
- @PostMapping("/getPageOneLevel")
- @GetMapping("/getPageOneLevel/export")
- @PostMapping("/getPageTwoLevel")
- @GetMapping("/getPageTwoLevel/export")

## CdMaterialWarrantController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/repairs/CdMaterialWarrantController.java`
- @RequestMapping("/repairs/cdMaterialWarrant")
- @PostMapping("/getPage")
- @PostMapping("/delete")
- @PostMapping("/add")
- @PostMapping("/update")
- @PostMapping("/export")

## SpReportController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/repairs/SpReportController.java`
- @RequestMapping("/repairs/spReport")
- @PostMapping("/orderMaterialReport/Page")
- @PostMapping("/orderMonitorDelivery/Page")
- @PostMapping("/hDSMonitoringReportPage")
- @PostMapping("/hDSReturnMonitoringPage")
- @GetMapping("/orderMaterialReport/export")
- @GetMapping("/orderMonitorDelivery/export")
- @GetMapping("/doExportHDSMonitoringReport")
- @GetMapping("/doExportHDSReturnMonitoring")
- @PostMapping("/billFlowQueryReport/Page")
- @GetMapping("/doExportBillFlowQuery")

## SpReserveAllocationOrderController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/repairs/SpReserveAllocationOrderController.java`
- @RequestMapping("/repairs/spReserveAllocationOrder")
- @PostMapping("/getPage")
- @PostMapping("/getList")
- @PostMapping("/delete")
- @PostMapping("/add")
- @PostMapping("/update")
- @PostMapping("/export")
- @PostMapping("/detail/export")

## CdWarehouseRouteController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/repairs/CdWarehouseRouteController.java`
- @RequestMapping("/repairs/cdWarehouseRoute")
- @PostMapping("/getPage")
- @PostMapping("/delete")
- @PostMapping("/add")
- @PostMapping("/update")
- @PostMapping("/queryRoute")
- @PostMapping("/export")

## SpExpressRoutingController
- 文件: `rrsjk-hds-web/src/main/java/com/rrsjk/hds/controller/repairs/SpExpressRoutingController.java`
- @RequestMapping("/repairs/spExpressRouting")
- @PostMapping("/getPage")
- @PostMapping("/list")

## AsyncImportExportTaskController
- 文件: `rrsjk-async-import-export/src/main/java/com/rrsjk/async/controller/AsyncImportExportTaskController.java`
- @RequestMapping("/task")
- @PostMapping("/export")
- @GetMapping(value = "/{taskId}")

## PvStationPayPlanController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/PvStationPayPlanController.java`
- @RequestMapping("/PvStationPayPlan")
- @PostMapping("/add")
- @PostMapping("/changeByPlanNo")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @GetMapping("/export")

## PvStationInfoController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/PvStationInfoController.java`
- @RequestMapping("/PvStationInfo")
- @PostMapping("/add")
- @PostMapping("/changeByPvStationCode")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @GetMapping("/export")

## SelftInsertDataController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/SelftInsertDataController.java`
- @RequestMapping("/SelfInsertData")
- @PostMapping("/addPvStation")
- @PostMapping("/addPvPayPlan")
- @PostMapping("/addPvPurchaseOrder")
- @PostMapping("/addSaleOrder")
- @PostMapping("/saleOrderGetCode")
- @PostMapping("/addPvInvoice")
- @PostMapping("/confirmPayPlan")
- @PostMapping("/confirmSaleOrder")
- @PostMapping("/confirmPurchaseOrder")
- @PostMapping("/opPurchaseCreateJob")
- @PostMapping("/opPurchaseSignJob")
- @PostMapping("/opSaleCreateJob")
- @PostMapping("/opSaleDeliveryJob")
- @PostMapping("/opSaleBillingJob")
- @PostMapping("/opPlanInitialJob")
- @PostMapping("/opPlanFinalJob")
- @PostMapping("/opInvoiceInitialJob")
- @PostMapping("/opInvoiceFinalJob")

## PvStationInvoiceController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/PvStationInvoiceController.java`
- @RequestMapping("/PvStationInvoice")
- @PostMapping("/add")
- @PostMapping("/changeByPvStationCode")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @GetMapping("/export")

## PvSalesOrderController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/PvSalesOrderController.java`
- @RequestMapping("/PvSaleOrder")
- @PostMapping("/add")
- @PostMapping("/changeBySaleOrderNo")
- @GetMapping("/queryById")
- @GetMapping("/queryByPage")
- @GetMapping("/export")

## PvServiceProviderController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/PvServiceProviderController.java`
- @RequestMapping("/PvServiceProvider")
- @PostMapping("/add")
- @PostMapping("/changeBySpId")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @GetMapping("/export")
- @PostMapping("/getSpMdmInfo")
- @PostMapping("/getSpMdmBankInfo")

## PvPickingOrderController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/PvPickingOrderController.java`
- @RequestMapping("/PvPickingOrder")
- @PostMapping("/add")
- @PostMapping("/changeByPickingNo")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @GetMapping("/export")

## PvStationMaterialController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/PvStationMaterialController.java`
- @RequestMapping("/PvStationMaterial")
- @PostMapping("/add")
- @PostMapping("/changeMaterialByPvStationCode")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")

## PvSystemInteractionLogController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/PvSystemInteractionLogController.java`
- @RequestMapping("/pvLog")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")

## PvStationInfoHistoryController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/PvStationInfoHistoryController.java`
- @RequestMapping("/PvStationInfoHistory")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")

## ServiceProviderDepositController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/ServiceProviderDepositController.java`
- @RequestMapping("/ServiceProviderDeposit")
- @PostMapping("/add")
- @PostMapping("/changeByDepositNo")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @GetMapping("/export")

## PvPurchaseOrderController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/PvPurchaseOrderController.java`
- @RequestMapping("/PurchaseOrder")
- @PostMapping("/add")
- @PostMapping("/changeByPurchaseNo")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @GetMapping("/export")

## SapFinanceReceiptRecordingController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/sap/SapFinanceReceiptRecordingController.java`
- @RequestMapping("/SapFinanceReceiptRecording")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @GetMapping("/queryOffSetByPage")
- @GetMapping("/queryByRowId")
- @PostMapping("/doPayOffSet")

## SapQueueController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/sap/SapQueueController.java`
- @RequestMapping("/SapQueue")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")

## SapChannelLogController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/sap/SapChannelLogController.java`
- @RequestMapping("/SapChannelLog")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")

## SapSaleOrderRecordController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/sap/SapSaleOrderRecordController.java`
- @RequestMapping("/SapSaleOrderRecord")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @GetMapping("/export")

## MkYbzLogController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/mk/MkYbzLogController.java`
- @RequestMapping("/MkYbzLog")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")

## MkYbzQueryStatusLogController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/mk/MkYbzQueryStatusLogController.java`
- @RequestMapping("/MkYbzQueryStatusLog")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")

## MkHbcOccupyRecordController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/mk/MkHbcOccupyRecordController.java`
- @RequestMapping("/MkHbcOccupyRecord")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")

## MkHbcLogController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/mk/MkHbcLogController.java`
- @RequestMapping("/MkHbcLog")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")

## MkPvConfirmationController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/mk/MkPvConfirmationController.java`
- @RequestMapping("/MkPvConfirmation")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @GetMapping("/export")

## MkYbzSettlementRecordController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/mk/MkYbzSettlementRecordController.java`
- @RequestMapping("/MkYbzSettlementRecord")
- @PostMapping("/add")
- @PostMapping("/update")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @PostMapping("/remove")

## MkHbcUsedBudgetRecordController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/mk/MkHbcUsedBudgetRecordController.java`
- @RequestMapping("/MkHbcUsedBudgetRecord")
- @PostMapping("/add")
- @PostMapping("/update")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @PostMapping("/remove")

## MkPvSettlementController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/mk/MkPvSettlementController.java`
- @RequestMapping("/MkPvSettlement")
- @PostMapping("/add")
- @PostMapping("/firstAudit")
- //    @PostMapping("/update")
- @PostMapping("/submitAudit")
- @PostMapping("/secondAudit")
- @GetMapping("/queryById")
- @GetMapping("/queryByPage")
- @PostMapping("/remove")
- @GetMapping("/downloadDoc")

## MkPvSettlementAuditLogController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/mk/MkPvSettlementAuditLogController.java`
- @RequestMapping("/MkPvSettlementAuditLog")
- @PostMapping("/add")
- @PostMapping("/update")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @PostMapping("/remove")

## MkInvoiceController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/mk/MkInvoiceController.java`
- @RequestMapping("/MkInvoice")
- @PostMapping("/add")
- @PostMapping("/changeByInvoiceNo")
- @PostMapping("/auditInvoice")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @PostMapping("/remove")

## MkYbzSettlementCallBackLogController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/mk/MkYbzSettlementCallBackLogController.java`
- @RequestMapping("/MkYbzSettlementCallBackLog")
- @PostMapping("/add")
- @PostMapping("/update")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @PostMapping("/remove")

## MkSettlementRelateInvoiceController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/mk/MkSettlementRelateInvoiceController.java`
- @RequestMapping("/MkSettlementRelateInvoice")
- @PostMapping("/add")
- @PostMapping("/update")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @PostMapping("/remove")

## MkSettlementRelateConfirmationController
- 文件: `vpp-pv-oversea/vpp-pv-oversea-biz/src/main/java/com/nahui/energy/controller/mk/MkSettlementRelateConfirmationController.java`
- @RequestMapping("/MkSettlementRelateConfirmation")
- @PostMapping("/add")
- @PostMapping("/update")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @PostMapping("/remove")
- @GetMapping("/export")

## OverseaYbzSettlementCallbackController
- 文件: `vpp-pv-oversea/vpp-pv-ex-api/src/main/java/com/nahui/energy/controller/OverseaYbzSettlementCallbackController.java`
- @RequestMapping("/OverseaYbzSettlementCallback")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @PostMapping("/callback")

## SwaggerController
- 文件: `vpp-api-gateway/vpp-gateway-biz/src/main/java/com/nahui/energy/controller/SwaggerController.java`
- @RequestMapping("/swagger-resources")
- @RequestMapping(value = "/configuration/security")
- @RequestMapping(value = "/configuration/ui")
- @RequestMapping

## ImportTaskController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/ImportTaskController.java`
- @RequestMapping("/ImportTask")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")

## TestController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/TestController.java`
- @GetMapping("/test")

## CustomerController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/customer/CustomerController.java`
- @RequestMapping("customer")
- @GetMapping("queryPage")
- @PostMapping("saveOrUpdate")
- @DeleteMapping("remove/{id}")
- @GetMapping("queryById/{id}")
- @GetMapping("queryByType/{type}")
- @GetMapping("queryForNewCust")
- @GetMapping("/export")

## IntendCustomerController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/customer/IntendCustomerController.java`
- @RequestMapping("intendCustomer")
- @GetMapping("queryPage")
- @GetMapping("queryAuditLogPage")
- @PostMapping("add")
- @PostMapping("findItemById")
- @PostMapping("commitToAudit")
- @PostMapping("addAndCommitToAudit")
- @PostMapping("auditOk")
- @PostMapping("auditReject")
- @PostMapping("change")
- @PostMapping("updateOrderNoById")
- @GetMapping("queryIntendNoByCustomerNo")
- @GetMapping("export")
- @GetMapping("showSubmitButton")
- @GetMapping("showApproveButton")
- @GetMapping("showApproveButtonByApproveCode")
- @GetMapping("subordinateRejectNode")
- @PostMapping("withdraw")

## CustomerInvoiceController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/customer/CustomerInvoiceController.java`
- @RequestMapping("/customerInvoice")
- @PostMapping("queryInvoicePage")
- @PostMapping("findMdmCustomer")

## GecStockChangeRecordController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/stock/GecStockChangeRecordController.java`
- @RequestMapping("/gecStockChangeRecord")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryPage")
- @GetMapping("/export")
- @GetMapping("/queryById")

## GecStockController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/stock/GecStockController.java`
- @RequestMapping("/stock")
- @PostMapping("/getImportTemplate")
- @PostMapping(value = "/importStock", consumes = MediaType.MULTIPART_FORM_DATA_VALUE)
- @PostMapping(value = "/importStockNew", consumes = MediaType.MULTIPART_FORM_DATA_VALUE)
- @DeleteMapping("remove/{ids}")
- @GetMapping("/list")
- @GetMapping("/autoMatchGecStock")
- @GetMapping("/export")
- @GetMapping("/listGroupByProject")
- @GetMapping("/exportGroupByProject")
- @GetMapping("/listGroupByProjectCompany")
- @GetMapping("/exportGroupByProjectCompany")
- @GetMapping("/listGroupBySubCenter")
- @GetMapping("/exportGroupBySubCenter")
- @GetMapping("queryAvailableStockList")
- @GetMapping("exportAvailableStockList")
- @PostMapping("/occupyStock")
- @GetMapping("/releaseStock")
- @GetMapping("/outStock")

## GecPurchaseOrderItemReceiptVoucherController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/purchase/GecPurchaseOrderItemReceiptVoucherController.java`
- @RequestMapping("/GecPurchaseOrderItemReceiptVoucher")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @GetMapping("/queryByPurchaseOrderNo")

## GecPurchaseContractController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/purchase/GecPurchaseContractController.java`
- @RequestMapping("/purchase/contract")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @GetMapping("queryByPurchaseOrderId")
- @PostMapping("/temporarySaveContract")
- @PostMapping("/checkAndAdd")

## GecPurchaseAuditLogController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/purchase/GecPurchaseAuditLogController.java`
- @RequestMapping("/GecPurchaseAuditLog")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @GetMapping("/queryByTypeAndPurchaseOrderNo")

## GecPurchaseOrderController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/purchase/GecPurchaseOrderController.java`
- @RequestMapping("/purchase")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @GetMapping("/queryAllInfoById")
- @GetMapping("/export")
- @GetMapping("/invalid")
- @PostMapping("/purchaseAudit")
- @PostMapping("/contractAudit")
- @PostMapping("/temporarySaveInvoice")
- @PostMapping("/saveInvoice")
- @PostMapping("/applySettleAudit")
- @PostMapping("/submitReceiptVoucher")
- @PostMapping("/tempSubmitReceiptVoucher")
- @PostMapping("/auditReceiptVoucher")
- @GetMapping("/templateModuleUrl")

## GecPurchaseOrderItemController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/purchase/GecPurchaseOrderItemController.java`
- @RequestMapping("/purchase/item")

## GecPurchaseApplySettleController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/purchase/GecPurchaseApplySettleController.java`
- @RequestMapping("/purchaseApplySettle")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @GetMapping("queryByPurchaseOrderId")
- @PostMapping("/temporarySave")
- @PostMapping("/add")

## OrderVoucherLogController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/order/OrderVoucherLogController.java`
- @RequestMapping("order/voucherLog")
- @GetMapping("queryList")

## OrderManagementInfoController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/order/OrderManagementInfoController.java`
- @RequestMapping("order")
- @GetMapping("queryOrderPage")
- @GetMapping("/export")
- @PostMapping("cacheContract")
- @GetMapping("getContractCache")
- @PostMapping("cacheInvoice")
- @GetMapping("getInvoiceCache")
- @PostMapping("cacheGecSelection")
- @GetMapping("getGecSelectionCache")
- @PostMapping("cacheVoucher")
- @GetMapping("getVoucherCache")
- @PostMapping("setCacheOrderInfo")
- @GetMapping("getOrderFromCache")
- @PostMapping("createOrder")
- @PostMapping("updateCustomerInovice")
- @PostMapping("uploadContract")
- @PostMapping("contractAudit")
- @PostMapping("choseGec")
- @GetMapping("queryOrderItemStockInfo")
- @PostMapping("uploadVoucher")
- @PostMapping("voucherAudit")
- @DeleteMapping("cancelOrder")
- @GetMapping("findItemsByOrderNo")
- @GetMapping("showSubmitButton")
- @GetMapping("showApproveButton")
- @GetMapping("showApproveButtonByApproveCode")
- @GetMapping("subordinateRejectNode")
- @PostMapping("contractWithdraw")
- @PostMapping("voucherWithdraw")

## OrderContractLogController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/order/OrderContractLogController.java`
- @RequestMapping("order/contractLog")
- @GetMapping("queryList")

## OrderManagementItemGecController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/order/OrderManagementItemGecController.java`
- @RequestMapping("/OrderManagementItemGec")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")

## ProjectController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/project/ProjectController.java`
- @RequestMapping("/Project")
- @PostMapping("/add")
- @DeleteMapping("/remove/{id}")
- @GetMapping("/queryByPage")
- @GetMapping("/queryProjectCompanyCodeAndName")
- @GetMapping("/queryById")
- @PostMapping(value = "/importData", consumes = MediaType.MULTIPART_FORM_DATA_VALUE)
- @PostMapping(value = "/importDataNew", consumes = MediaType.MULTIPART_FORM_DATA_VALUE)
- @GetMapping("/export")

## SalesEntityCompanyController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/project/SalesEntityCompanyController.java`
- @RequestMapping("/SalesEntityCompany")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryMdmInfo")
- @GetMapping("/queryByName")
- @GetMapping("/queryById")

## ProjectCompanyTradeTypeController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/project/ProjectCompanyTradeTypeController.java`
- @RequestMapping("/ProjectCompanyTradeType")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryByProjectCompanyCode")
- @GetMapping("/queryById")

## SubProjectController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/project/SubProjectController.java`
- @RequestMapping("/subProject")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @PostMapping(value = "/importData", consumes = MediaType.MULTIPART_FORM_DATA_VALUE)
- @PostMapping(value = "/importDataNew", consumes = MediaType.MULTIPART_FORM_DATA_VALUE)
- @GetMapping("/export")

## SapController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/sap/SapController.java`
- @RequestMapping("/sap")
- @PostMapping("/reserve")
- @PostMapping("/reSap")
- @PostMapping("/reSapByOrderNo")

## SapItemRecordController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/sap/SapItemRecordController.java`
- @RequestMapping("/sapItemRecord")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")

## LightStationGreenCertificateProgressController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/progressgreen/LightStationGreenCertificateProgressController.java`
- @RequestMapping("/progressGreen")
- @GetMapping("/queryByPage")
- @PostMapping(value = "/importDataJianDangNew", consumes = MediaType.MULTIPART_FORM_DATA_VALUE)
- @PostMapping(value = "/importDataGreenFileNew", consumes = MediaType.MULTIPART_FORM_DATA_VALUE)
- @GetMapping("/export")

## InvoiceAttachmentController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/invoice/InvoiceAttachmentController.java`
- @RequestMapping("/InvoiceAttachment")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")

## InvoiceController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/invoice/InvoiceController.java`
- @RequestMapping("/invoice")
- @PostMapping("queryInvoicePage")
- @PostMapping("sendInvoiceJob")
- @PostMapping("queryInvoiceResultJob")

## GecInvoiceCheckController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/invoice/GecInvoiceCheckController.java`
- @RequestMapping("/invoiceCheck")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @GetMapping("/queryByPurchaseOrderNo")
- @GetMapping("/acquireInvoiceInfoFromCbs")
- @PostMapping("/addInvoiceCheckToCbs")

## InvoiceItemController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/invoice/InvoiceItemController.java`
- @RequestMapping("/InvoiceItem")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")

## PaybackManageController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/fund/PaybackManageController.java`
- @RequestMapping("fund")
- @GetMapping("queryPaybackPage")
- @PostMapping("uploadPayVoucher")
- @PostMapping("payVoucherAudit")
- @PostMapping("paybackManagementAuditStatusForUploadTradeType")
- @PostMapping("setPayVoucherCache")
- @PostMapping("getPayVoucherCache")
- @PostMapping("manualCreateInvoice")
- @PostMapping("invoiceOffLine")
- @GetMapping("export")

## PaybackConfirmAuditLogController
- 文件: `vpp-api-gect/vpp-gect-biz/src/main/java/com/nahui/energy/controller/fund/PaybackConfirmAuditLogController.java`
- @RequestMapping("fund/confirmLog")
- @GetMapping("queryList")

## GlobalExceptionHandler
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/util/GlobalExceptionHandler.java`
- 未扫描到显式 Mapping 注解

## SpSettlementDataController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/SpSettlementDataController.java`
- @RequestMapping("/repairs/spSettlementData")
- @PostMapping("/getPage")

## LightUseOrderController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/LightUseOrderController.java`
- @RequestMapping("/lightUseOrder")
- @GetMapping("completeBeforeDoList.do")
- @GetMapping("completeBeforeExport.do")
- @PostMapping("manualOutStock.do")

## ChatMessageController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/ChatMessageController.java`
- @RequestMapping("/api/chat")
- @PostMapping("/messages")
- @GetMapping("/test")

## LightUseQueueController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/LightUseQueueController.java`
- @RequestMapping("/lightUseQueue")
- @GetMapping("doList.do")
- @GetMapping("doExport.do")

## MemberRegistController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/MemberRegistController.java`
- @RequestMapping("/member/reg/")
- @PostMapping("check_and_send_sms.do")
- @PostMapping("check_sms_code.do")
- @PostMapping("do_regist.do")
- @PostMapping("send_sms.do")
- @PostMapping("sendRegisterSms.do")
- @PostMapping("register.do")
- @GetMapping("/sendUpdatePasswordSms.do")
- @PostMapping("/updatePassword.do")
- @GetMapping("getRole.do")

## CorporateClientController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/shop/CorporateClientController.java`
- @RequestMapping("/corporate")
- @GetMapping("/get.do")
- @PostMapping("/regist.do")
- @PostMapping("/update.do")
- @GetMapping("/getInfo.do")

## CorporateClientDepositController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/shop/CorporateClientDepositController.java`
- @RequestMapping("/corporate/deposit")
- @GetMapping("find.do")
- @PostMapping("addDeposit.do")
- @PostMapping("modifyDeposit.do")
- @GetMapping("getDeposit.do")
- @GetMapping("getNeedPayDeposit.do")

## ShopController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/shop/ShopController.java`
- @RequestMapping("/shop")
- @GetMapping("/checkShop.do")
- @GetMapping("/getShop.do")
- @GetMapping("/getRealShop.do")

## MerchantController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/shop/MerchantController.java`
- @RequestMapping("/mch")
- @GetMapping("/getAgreementMark.do")
- @GetMapping("/updateAgreementMark.do")
- @GetMapping("/getByTaxNo.do")
- @GetMapping("/fruzzFindByMerchantName.do")
- @GetMapping("supplier.do")
- @RequestMapping(value = { "/merAppliSupplier.do" }, method = { RequestMethod.POST })

## PosthouseController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/shop/PosthouseController.java`
- @RequestMapping("/posthouse")
- @GetMapping("posthouseList.do")
- @GetMapping("/getPosthouse.do")
- @PostMapping("/addPosthouse.do")
- @PostMapping("/updatePosthouse.do")
- @PostMapping("/importPosthouse.do")
- @GetMapping("/posthouseErrExcel.do")
- @GetMapping("/downloadTemplate.do")
- @PostMapping("/updateLonAndLat.do")
- @PostMapping("/updateImageUrl.do")

## DriverDeliveryController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/shop/DriverDeliveryController.java`
- @RequestMapping("/driverDelivery")
- @GetMapping("driverDeliveryList.do")
- @PostMapping("/addDriverDelivery.do")
- @PostMapping("/updateDriverDelivery.do")
- @PostMapping("/addDriverDeliveryRegion.do")
- @PostMapping("/delDriverDeliveryRegion.do")
- @PostMapping("/addLinePosthouse.do")
- @PostMapping("/delLinePosthouse.do")

## ShopCustomerController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/shop/ShopCustomerController.java`
- @RequestMapping("/shopCustomer")
- @PostMapping("/selectCustomer.do")
- @PostMapping("/createCustomer.do")
- @GetMapping("/listShopCustomer.do")

## ExpertCustomerController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/shop/ExpertCustomerController.java`
- @RequestMapping("/expert")
- @GetMapping("expertList.do")
- @PostMapping("/addExpertCustomer.do")
- @PostMapping("/addExpertCustomerContacts.do")
- @PostMapping("/enabledExpertCustomer.do")
- @PostMapping("/disabledExpertCustomer.do")
- @PostMapping("/deletedExpertCustomer.do")
- @GetMapping("/getCustomerInfo.do")
- @PostMapping("/saveCustomerAddress.do")
- @GetMapping("/getCustomerDetail.do")
- @GetMapping("/getCustomerSum.do")
- @PostMapping("/setCustomerCredit.do")
- @PostMapping("/saveContract.do")
- @GetMapping("/findContractInfo.do")
- @PostMapping("/deletedContractImage.do")

## CartController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/cart/CartController.java`
- @RequestMapping("/cart")
- @GetMapping("/get.do")
- @PostMapping("/addToCart.do")
- @PostMapping("/batchAddToCart.do")
- @GetMapping("/validStock.do")
- @PostMapping("/modifyNumber.do")
- @PostMapping("/clearCart.do")
- @GetMapping("/getCartItemNumber.do")

## CouponController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/coupon/CouponController.java`
- @RequestMapping("/coupon")
- @GetMapping("/find.do")
- @PostMapping("/saveCoupon.do")
- @GetMapping("/listItem.do")
- @PostMapping("/delete.do")
- @GetMapping("/showCoupon.do")
- @GetMapping("/showItem.do")

## LnWalletController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/order/LnWalletController.java`
- @RequestMapping("/order/lnWallet/")
- @GetMapping("/getOrderLnWallet.do")
- @PostMapping("sendSmsCode.do")

## OrderCreateController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/order/OrderCreateController.java`
- @RequestMapping("/order")
- @PostMapping("create.do")

## OrderSumCountController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/order/OrderSumCountController.java`
- @RequestMapping("/order/orderItem/")
- @GetMapping("/paidOrderSumCount.do")
- @GetMapping("paidOrderSumCountWeekGroup.do")

## LightPurchaseSalesPurchaseOrderController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/order/LightPurchaseSalesPurchaseOrderController.java`
- @RequestMapping("/lightPurchaseSalesPurchaseOrder")
- @GetMapping("findPage.do")
- @GetMapping("find1QJ0Page.do")
- @GetMapping("find1QJ0PageForThirdPartStore.do")
- @PostMapping("deliver.do")
- @PostMapping("doExport.do")
- @PostMapping("do1QJ0Export.do")
- @PostMapping("do1QJ0ExportForThirdPartStore.do")
- @PostMapping("deliverToSap.do")

## NetPayOrderCheckController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/order/NetPayOrderCheckController.java`
- @RequestMapping("/netPayOrderCheck")
- @PostMapping("check.do")
- @PostMapping("checkAll.do")
- @PostMapping("retryToSap.do")

## DsPredictionOrderController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/order/DsPredictionOrderController.java`
- @RequestMapping("/ds/prediction/")
- @GetMapping("predictionOrderList.do")
- @GetMapping("predictionOrderListExcel.do")

## DsStockOrderController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/order/DsStockOrderController.java`
- @RequestMapping("/ds/stock/")
- @GetMapping("stockOrderList.do")
- @GetMapping("stockOrderListExcel.do")
- @PostMapping("/editStatus.do")
- @GetMapping("statusCount.do")
- @PostMapping("deliver.do")
- @PostMapping("importDeliver.do")
- @GetMapping("deliverTemplate.do")
- @GetMapping("findExpressRecord.do")

## PcsOrderDeliveryToLightQueueController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/order/PcsOrderDeliveryToLightQueueController.java`
- @RequestMapping("/pcsOrderDeliveryQueue")
- @PostMapping("create.do")
- @PostMapping("ensCreate.do")

## OrderJointVentureController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/order/OrderJointVentureController.java`
- @RequestMapping("/order/orderItem/")
- @GetMapping("getOrderInvoice.do")
- @GetMapping("orderItemJointVentureList.do")
- @PostMapping("uploadAccountVoucher.do")
- @PostMapping("uploadInvoiceVoucher.do")
- @PostMapping("confirmSignQuantity.do")

## OrderRepairController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/order/OrderRepairController.java`
- @RequestMapping("/order/orderRepair")
- @PostMapping("auditRefundOrderItem.do")

## GroupSubtotalExcelController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/order/GroupSubtotalExcelController.java`
- @RequestMapping("/order/group/")
- @GetMapping("exportBySkuSubtotal.do")
- @GetMapping("exportByLineSubtotal.do")
- @GetMapping("exportByDeliverSubtotal.do")
- @GetMapping("exportByPickSubtotal.do")

## OrderSettleController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/order/OrderSettleController.java`
- @RequestMapping("/order/cart")
- @GetMapping("getOrderCartBySettle.do")

## LightPurchaseSalesController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/order/LightPurchaseSalesController.java`
- @RequestMapping("/lightPurchaseSalesOrder")
- @PostMapping("create.do")
- @GetMapping("userFindPage.do")
- @GetMapping("userFind1Qj0Page.do")
- @GetMapping("shopFindPage.do")
- @GetMapping("shopFind1QJ0Page.do")
- @GetMapping("findDetail.do")
- @PostMapping("uploadPayVoucher.do")
- @PostMapping("confirmReceipt.do")
- @PostMapping("uploadReceipt.do")
- @GetMapping("toPay.do")
- @PostMapping("notifyNetPay.do")
- @PostMapping("payResultQuery.do")
- @PostMapping("applyRefund.do")
- @PostMapping("reZeroIncomeToSap.do")
- @PostMapping("updateAddress.do")
- @GetMapping("cancelOrder.do")
- @PostMapping("refund")
- @PostMapping("payToSap.do")

## OrderNetPayNotifyController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/order/OrderNetPayNotifyController.java`
- @RequestMapping("/order/netPayNotify/")
- @PostMapping("notifyNetPay.do")

## OrderBuyerController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/order/OrderBuyerController.java`
- @RequestMapping("/order/buyer/")
- @GetMapping("orderItemList.do")
- @GetMapping("doExport.do")
- @GetMapping("/orderItemDetail.do")
- @GetMapping("/findExpressRecord.do")
- @PostMapping("cancelOrderItem.do")
- @PostMapping("finishOrderItem.do")
- @PostMapping("applyRefundOrderItem.do")
- @PostMapping("cancelRefundOrderItem.do")
- @PostMapping("uploadTransferVoucher.do")
- @PostMapping("orderUploadTransferVoucher.do")
- @GetMapping("toPay.do")
- @PostMapping("payResultQuery.do")
- @PostMapping("downAccountStatement.do")
- @PostMapping("downAccountStatementByStart.do")
- @PostMapping("netPayToBillAll.do")
- @PostMapping("netPayToBill.do")
- @PostMapping("invoice")
- @PostMapping("createSapPurchaseOrder")
- @PostMapping("refund")
- @PostMapping("refundOrderItem")
- @PostMapping("createOrderItemFeeByPaid.do")
- @PostMapping("createOrderItemFeeByRefund.do")
- @PostMapping("updateStatus")
- @GetMapping("getAuxiliaryMaterialCreditLimitBalance.do")
- @GetMapping("auxiliaryMaterialCreditLimitPay.do")
- @GetMapping("auxiliaryMaterialCreditLimitOrderItemList.do")
- @GetMapping("getAuxiliaryMaterialCreditLimit.do")
- @GetMapping("auxiliaryMaterialCreditLimitOrderItemListExport.do")

## OrderItemController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/order/OrderItemController.java`
- @RequestMapping("/order/orderItem/")
- @GetMapping("orderItemList.do")
- @GetMapping("orderItemDetail.do")
- @GetMapping("findExpressRecord.do")
- @PostMapping("deliverOrderItem.do")
- @GetMapping("downloadTemplate.do")
- @PostMapping("importDeliverOrderItem.do")
- @GetMapping("listAllExpress.do")
- @PostMapping("/addShopRemark.do")
- @GetMapping("orderItemCount.do")
- @PostMapping("adjustPayAmount.do")
- @PostMapping("offlineConfirmPaid.do")
- @PostMapping("cctCarDeliverOrderItem.do")
- @PostMapping("deliverToSap.do")

## GroupSubtotalController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/order/GroupSubtotalController.java`
- @RequestMapping("/order/group/")
- @GetMapping("findBySkuSubtotal.do")
- @GetMapping("findByLineSubtotal.do")
- @GetMapping("findByDeliverSubtotal.do")
- @GetMapping("findByPickSubtotal.do")

## OrderItemExcelController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/order/OrderItemExcelController.java`
- @RequestMapping("/order/orderItem/")
- @GetMapping("orderItemListExcel.do")

## messageController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/message/messageController.java`
- @RequestMapping("/message/")
- @GetMapping("/getMessages")
- @GetMapping("/getMessageInfo")
- @GetMapping("/countUnreadMessages")
- @PostMapping("/markMessageAsRead")
- @GetMapping("/searchHistory")
- @PostMapping("/markAsAgree")
- @GetMapping("/deleteSearchHistory")
- @GetMapping("/deleteSearchHistoryByType")
- @GetMapping("/getUrgentMessagePopup")
- @GetMapping("/checkDocIsDelete")
- @GetMapping("/getMessagePopup")

## ZeroCarbonOrderPolicyCashController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/ZeroCarbonOrderPolicyCashController.java`
- @RequestMapping("/light/zeroCarbonOrderPolicyCash")
- @GetMapping("/findPage.do")
- @GetMapping("/findDetail.do")
- @GetMapping("/updateCash.do")

## ZeroCarbonSubNewController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/ZeroCarbonSubNewController.java`
- @RequestMapping("/light/zeroCarbonSubNew")
- @GetMapping("getSubInfo.do")

## ZeroCarbonItemSetMealStockController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/ZeroCarbonItemSetMealStockController.java`
- @RequestMapping("/light/zeroCarbonItemSetMealStock")
- @PostMapping("/create")
- @GetMapping("/getAvailableStockByCode")
- @GetMapping("/findPage")
- @GetMapping("/queryStockChangeLog")
- @GetMapping("/getAllBySetMealCode")

## LightZeroCarbonStockController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/LightZeroCarbonStockController.java`
- @RequestMapping("/light/zeroCarbon/stock/")
- @GetMapping("/getStock.do")
- @GetMapping("/export.do")

## ZeroCarbonDepositRecordController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/ZeroCarbonDepositRecordController.java`
- @RequestMapping(value = "/light/zeroCarbon/depositRecord/", produces = {"application/json;"})
- @GetMapping("/list.do")
- @GetMapping("/recordList.do")
- @GetMapping("/queryRecordListForApplySettle.do")
- @PostMapping("/add.do")
- @PostMapping("/update.do")
- @PostMapping("/delete.do")
- @GetMapping("/detail.do")

## ZeroCarbonPointsWalletController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/ZeroCarbonPointsWalletController.java`
- @RequestMapping("/light/zeroCarbonPointsWallet")
- @GetMapping("/findPage.do")
- @GetMapping("/findPointsBalance.do")

## ZeroCarbonServiceProviderController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/ZeroCarbonServiceProviderController.java`
- @RequestMapping("/light/zeroCarbonSp")
- @PostMapping("/register.do")
- @GetMapping("/get.do")
- @GetMapping("/findAuthRegionList.do")

## ZeroCarbonInstallationSettleNoPaperController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/ZeroCarbonInstallationSettleNoPaperController.java`
- @RequestMapping(value = "/light/zeroCarbon/settleNoPaPer/", produces = {"application/json;"})
- @GetMapping("/list.do")
- @PostMapping("/add.do")
- @PostMapping("/update.do")
- @PostMapping("/delete.do")
- @GetMapping("/detail.do")
- @PostMapping("/relateInvoice.do")
- @GetMapping("/getConfirmBeforeBillUrl.do")
- @GetMapping("/getConfirmUrl.do")
- @PostMapping("/ybzCreateCallback")
- @GetMapping("export.do")

## ZeroCarbonGridConnectionController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/ZeroCarbonGridConnectionController.java`
- @RequestMapping("/light/zeroCarbon/station/grid/")
- @PostMapping("/submit.do")
- @PostMapping("/saveCache.do")
- @PostMapping("/edit.do")
- @GetMapping("/getCache.do")
- @PostMapping("/withdraw.do")

## ZeroCarbonConnectEnergySystemController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/ZeroCarbonConnectEnergySystemController.java`
- @RequestMapping(value = "/light/zeroCarbon/energy/", produces = {"application/json;"})
- @PostMapping("/connect.do")
- @PostMapping("/completionInfo/upload.do")

## ZeroCarbonMessageController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/ZeroCarbonMessageController.java`
- @RequestMapping("/light/zeroCarbonMessage")
- @GetMapping("/findList.do")
- @GetMapping("/readMessage.do")

## LightZeroMaterialManageController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/LightZeroMaterialManageController.java`
- @RequestMapping(value ="/light/zeroCarbon/materialManage", produces = {"application/json;"})
- @GetMapping("manageList.do")
- @GetMapping("/export.do")

## LightZeroCarbonStationController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/LightZeroCarbonStationController.java`
- @RequestMapping("/light/zeroCarbon/station/")
- @PostMapping("/registerStation.do")
- @PostMapping("/resubmitStation.do")
- @GetMapping("/stationList.do")
- @GetMapping("getImgTemplate")
- @GetMapping("/getStationById.do")
- @PostMapping("/registerCache.do")
- @GetMapping("/findSku.do")
- @PostMapping("/uploadEntrancePhoto.do")
- @GetMapping("/export.do")
- @GetMapping("/stationStatusSum.do")
- @PostMapping("/withdraw.do")

## LightZeroMaterialSerialController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/LightZeroMaterialSerialController.java`
- @RequestMapping(value ="/light/zeroCarbon/materialSerial", produces = {"application/json;"})
- @GetMapping("serialList.do")
- @GetMapping("export.do")

## ZeroCarbonSpAuthRegionController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/ZeroCarbonSpAuthRegionController.java`
- @RequestMapping("/light/zeroCarbonSpAuthRegion")
- @GetMapping("/findAuthRegionPage.do")
- @PostMapping("/applyAuthorityRegion.do")
- @PostMapping("/editAuthorityRegion.do")
- @GetMapping("/previewRegionContract.do")
- @PostMapping("/signRegionContract.do")

## ZeroCarbonCompleteConfirmController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/ZeroCarbonCompleteConfirmController.java`
- @RequestMapping("/light/zeroCarbon/station/complete/")
- @PostMapping("/confirm.do")
- @PostMapping("/confirmCache.do")
- @PostMapping("/editConfirm.do")
- @GetMapping("/getConfirmCache.do")
- @PostMapping("/withdraw.do")

## ZeroCarbonPolicyController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/ZeroCarbonPolicyController.java`
- @RequestMapping("/light/zeroCarbonPolicy")
- @GetMapping("/findList.do")

## LightZeroCarbonPurchaseOrderController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/LightZeroCarbonPurchaseOrderController.java`
- @RequestMapping("/light/zeroCarbon/purchase/")
- @GetMapping("/out/getOrder.do")
- @GetMapping("/out/export.do")
- @GetMapping("/in/getOrder.do")
- @GetMapping("/in/export.do")
- @PostMapping("/plan/deliver")
- @PostMapping("/thirdParty/inStore.do")
- @PostMapping("/thirdParty/inStoreBatch.do")
- @PostMapping("/updateSign.do")
- @GetMapping("/getDetail.do")

## ZeroCarbonContractController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/ZeroCarbonContractController.java`
- @RequestMapping("/light/zeroCarbonContract")
- @GetMapping("/previewContract.do")
- @PostMapping("/signContract.do")
- @GetMapping("/findWaitSignList.do")
- @GetMapping("/findPage.do")
- @GetMapping("/findSignedUrl.do")

## LightZeroCarbonOrderGrabbingCampaignController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/LightZeroCarbonOrderGrabbingCampaignController.java`
- @RequestMapping("/light/zeroCarbon/campaign/")
- @GetMapping("/list.do")
- @GetMapping("/export.do")
- @PostMapping("/create.do")
- @PostMapping("/edit.do")
- @PostMapping("/submitSupportingDocuments.do")
- @GetMapping("/getById.do")

## ZeroCarbonMerchantNoticeController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/ZeroCarbonMerchantNoticeController.java`
- @RequestMapping("/zeroCarbon/merchantNotice")
- @RequestMapping("queryMerchantNoticeList")
- @RequestMapping("queryMerchantNoticeDetail")

## ZeroCarbonStationPolicyController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/ZeroCarbonStationPolicyController.java`
- @RequestMapping("/light/zeroCarbonStationPolicy")
- @GetMapping("/findPage.do")
- @GetMapping("detail.do")
- @GetMapping("/export.do")

## LightZeroCarbonEStationController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/LightZeroCarbonEStationController.java`
- @RequestMapping("/light/zeroCarbon/eStation/")
- @PostMapping("/registerStation.do")
- @PostMapping("/resubmitStation.do")
- @GetMapping("/stationList.do")
- @GetMapping("/getStationById.do")
- @GetMapping("/findSku.do")
- @PostMapping("/findSkuByStationId.do")
- @GetMapping("/export.do")
- @PostMapping("/cancelStation.do")
- @PostMapping("/cacheEStation.do")
- @PostMapping("/getEStationCache.do")
- @PostMapping("/requestAssignment.do")
- @PostMapping("/processingTheAssignment.do")

## LightZeroMaterialPurchaseController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/LightZeroMaterialPurchaseController.java`
- @RequestMapping(value ="/light/zeroCarbon/materialPurchase/", produces = {"application/json;"})
- @GetMapping("purchaseList.do")
- @GetMapping("export.do")

## ZeroCarbonSpBusinessModelController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/ZeroCarbonSpBusinessModelController.java`
- @RequestMapping("/light/zeroCarbonSpBusinessModel")
- @GetMapping("/findPage.do")
- @PostMapping("/apply.do")
- @PostMapping("/updateHistoricalData.do")

## LightZeroCarbonStationRegisterDraftController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/LightZeroCarbonStationRegisterDraftController.java`
- @RequestMapping("/light/zerocarbon/draft")
- @GetMapping("/getList.do")
- @GetMapping("/getDetail.do")
- @PostMapping("/delete.do")

## ZeroCarbonInstallationFeeController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/ZeroCarbonInstallationFeeController.java`
- @RequestMapping(value = "/light/zeroCarbon/fee/", produces = {"application/json;"})
- @GetMapping("/list.do")
- @GetMapping("/export.do")
- @GetMapping("/queryInstallationFeeForSettle.do")

## ZeroCarbonInstallationSettleController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/ZeroCarbonInstallationSettleController.java`
- @RequestMapping(value = "/light/zeroCarbon/settle/", produces = {"application/json;"})
- @GetMapping("/list.do")
- @GetMapping("/addPrepareInfo.do")

## LightZeroCarbonRetailPriceCalculationController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/LightZeroCarbonRetailPriceCalculationController.java`
- @RequestMapping("/light/zeroCarbon/calculation/")
- @GetMapping("/getInverterCode.do")
- @PostMapping("/calculate.do")
- @PostMapping("/downloadFile.do")
- @GetMapping("/downloadFileGet.do")

## ZeroCarbonOrderPolicyController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/ZeroCarbonOrderPolicyController.java`
- @RequestMapping("/light/zeroCarbonOrderPolicy")
- @GetMapping("/findPage.do")

## ZeroCarbonInvoiceCheckController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/ZeroCarbonInvoiceCheckController.java`
- @RequestMapping("/ZeroCarbonInvoiceCheck/")
- @GetMapping("/list.do")
- @GetMapping("/queryInvoiceForSettle.do")
- @PostMapping("/getInvoiceInfo.do")
- @PostMapping("/addInvoices.do")
- @PostMapping("/updateInvoices.do")
- @PostMapping("/deleteInvoice.do")
- @PostMapping("/manualAddInvoiceCheck.do")
- @PostMapping("/manualAddInvoice.do")

## ZeroCarbonSpShopController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/ZeroCarbonSpShopController.java`
- @RequestMapping("/light/zeroCarbonSpShop")
- @GetMapping("/findPage.do")
- @GetMapping("/findDetail.do")
- @PostMapping("/apply.do")
- @PostMapping("/acceptance.do")

## LightZeroCarbonStoreController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/LightZeroCarbonStoreController.java`
- @RequestMapping("/light/zeroCarbon/store/")
- @GetMapping("/getStore.do")

## ZeroCarbonItemSetMealController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/zerocarbon/ZeroCarbonItemSetMealController.java`
- @RequestMapping("/light/zeroCarbonItemSetMeal")
- @GetMapping("/findPageToShop.do")
- @GetMapping("/exportToShopExcel.do")
- @GetMapping("/findAllByShop")
- @GetMapping("/findPageToUser.do")
- @GetMapping("/findDetail.do")
- @PostMapping("/create.do")
- @GetMapping("/updateSelfStatus.do")
- @GetMapping("/updateToDelete")

## RegionController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/region/RegionController.java`
- @RequestMapping("/region")
- @GetMapping("/getRegionList.do")

## GfBusinessOpportunityController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/gf/GfBusinessOpportunityController.java`
- @RequestMapping("gfBusinessOpportunity")
- @GetMapping("queryTableList")
- @GetMapping("selectOption")
- @PostMapping("add")
- @PostMapping("edit")
- @PostMapping("updateDiscardStatus")
- @GetMapping("getDetailById")
- @GetMapping("delete")
- @GetMapping("getByInputPieceId")

## GfLightStationController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/gf/GfLightStationController.java`
- @RequestMapping("gfLightStation")
- @GetMapping("getByStationCode")

## LightStationInsuranceController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/yuexiuinsurance/LightStationInsuranceController.java`
- @RequestMapping("/lightStationInsurance")
- @GetMapping("/pushByHand")

## LightSpOpsSettleExcitationController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/spledger/LightSpOpsSettleExcitationController.java`
- @RequestMapping("sp/ledger")
- @GetMapping("findByPage")
- @GetMapping("/doExport")
- //    @GetMapping("exejob")
- //    @GetMapping("hisExeJob")
- @GetMapping("/signEleContract")
- @GetMapping("/getContractPdf")
- @GetMapping("showDetails")
- @GetMapping("/doExportDetails")
- @PostMapping("checkConfirm")

## LightSpOpsSettleIacController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/spledger/LightSpOpsSettleIacController.java`
- @RequestMapping("sp/iac")
- @GetMapping("findByPage")
- @GetMapping("/doExport")
- @GetMapping("exejob")
- @GetMapping("/signEleContract")
- @GetMapping("/getContractPdf")
- @PostMapping("checkConfirm")

## EnergyOverseasIncomeController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/report/EnergyOverseasIncomeController.java`
- @RequestMapping("/report/overseasIncome/")
- @PostMapping("/createOverseaIncome.do")
- @PostMapping("/create1PG0OverseaIncome.do")
- @PostMapping("/create1Q80OverseaIncomeMonth.do")
- @PostMapping("/create1PG0OverseaIncomeMonth.do")
- @PostMapping("create1Q80OverseaIncomeDetail.do")

## StationDevelopWarningController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/report/StationDevelopWarningController.java`
- @RequestMapping("/report/developWarning/")
- @GetMapping("/exceedThrNotCompleteList.do")
- @GetMapping("/exceedThrGenElectList.do")
- @GetMapping("/exceedSixGenElectList.do")
- @GetMapping("doExport.do")

## EnergyEteCenterDayController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/report/EnergyEteCenterDayController.java`
- @RequestMapping("/report/eteCenterDay/")
- @GetMapping("/queryList")

## EnergyEteIncomeDayController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/report/EnergyEteIncomeDayController.java`
- @RequestMapping("/report/eteIncomeDay/")
- @GetMapping("/queryList")

## RegionBusinessReportController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/report/RegionBusinessReportController.java`
- @RequestMapping("/report")
- @GetMapping("/regionOperationReport/query")
- @GetMapping("/regionOperationReport/export")
- @GetMapping("/regionOperationTeamReport/query")
- @GetMapping("/regionOperationTeamReport/export")
- @GetMapping("/regionOperationReport/queryOrderDetail")
- @GetMapping("/regionOperationReport/exportOrderDetail")
- @GetMapping("/regionOperationReport/querySignDetail")
- @GetMapping("/regionOperationReport/exportSignDetail")
- @GetMapping("/regionOperationReport/queryCompleteDetail")
- @GetMapping("/regionOperationReport/exportCompleteDetail")
- @GetMapping("/regionOperationReport/queryGridDetail")
- @GetMapping("/regionOperationReport/exportGridDetail")

## EnergyEteDayController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/report/EnergyEteDayController.java`
- @RequestMapping("/report/eteDay/")
- @GetMapping("/queryList")

## TeamBusinessReportController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/report/TeamBusinessReportController.java`
- @RequestMapping("/report")
- //    @GetMapping("/lightSp/query")
- @GetMapping("/teamBusinessOperationReport/query")
- @GetMapping("/teamBusinessOperationReport/export")
- @GetMapping("/teamBusinessOperationAreaReport/query")
- @GetMapping("/teamBusinessOperationAreaReport/export")
- @GetMapping("/teamBusinessOperationAreaReport/queryOrderDetail")
- @GetMapping("/teamBusinessOperationAreaReport/exportOrderDetail")
- @GetMapping("/teamBusinessOperationAreaReport/querySignDetail")
- @GetMapping("/teamBusinessOperationAreaReport/exportSignDetail")
- @GetMapping("/teamBusinessOperationAreaReport/queryCompleteDetail")
- @GetMapping("/teamBusinessOperationAreaReport/exportCompleteDetail")
- @GetMapping("/teamBusinessOperationAreaReport/queryGridDetail")
- @GetMapping("/teamBusinessOperationAreaReport/exportGridDetail")

## AppPolicyReportController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/report/app/AppPolicyReportController.java`
- @RequestMapping("/report/app_policy/")
- @GetMapping("/policy_report/queryPurchaseInfo")
- @GetMapping("/policy_report/queryInstantPolicy")
- @GetMapping("/policy_report/queryOtherPolicy")

## AppReportController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/report/app/AppReportController.java`
- @RequestMapping("/report/app/")
- @GetMapping("/lightSp/query")
- @GetMapping("/businessDataReport/query")
- @GetMapping("/stationManageReport/query")
- @GetMapping("/stationManageReport/queryDetail")
- @GetMapping("/checkRectifiedReport/query")
- @GetMapping("/warningStationReport/query")
- @GetMapping("/warningStationReport/queryDetail")
- @GetMapping("/inventory/summary")
- @GetMapping("/inventory/detail")
- @GetMapping("/overdueOrder/summary")
- @GetMapping("/overdueOrder/detail")

## MerchantUserInfoController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/ai/MerchantUserInfoController.java`
- @RequestMapping("/merchantUserInfo")
- @PostMapping("/getMemberId")
- @PostMapping("/getUserInfo")

## UserProblemManagementController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/ai/UserProblemManagementController.java`
- @RequestMapping("/api/assistant/userProblemManagement")
- @GetMapping("/page")
- @GetMapping("/{id}")
- @PostMapping
- @PutMapping("/{id}")
- @PutMapping("/{id}/solved")
- @GetMapping("/user/{userAccount}")
- @GetMapping("/subCenter/{subCenterCode}")
- @GetMapping("/solved/{isSolved}")
- @PostMapping("/batch")

## BankController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/bank/BankController.java`
- @RequestMapping("/bank/")
- @GetMapping("/findMainBankInfo.do")
- @GetMapping("/findProvinceBank.do")
- @GetMapping("/findCityBank.do")
- @GetMapping("/findRegionBank.do")
- @GetMapping("/findHouseBank.do")
- @GetMapping("/getByCityIdAndHeadBankName.do")
- @GetMapping("/getAllHeadBank.do")
- @GetMapping("/findHrflcMainBankInfo.do")

## ObsOrderController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/obs/ObsOrderController.java`
- @RequestMapping("/obs/order")
- @PostMapping("order")
- @PostMapping("status")

## RollPlanController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/obs/RollPlanController.java`
- @RequestMapping("/obs/rollPlan/")
- @GetMapping("getList")

## ProductController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/obs/ProductController.java`
- @RequestMapping("/obs/product/")
- @GetMapping("breakevenPrice")

## WfTaskController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/workflow/WfTaskController.java`
- @RequestMapping("/workflow/task")
- @PostMapping(value = "/stopProcess")
- @PostMapping(value = "/revokeProcess")
- @GetMapping(value = "/processVariables/{taskId}")
- @PostMapping(value = "/complete")
- @PostMapping(value = "/reject")
- @PostMapping(value = "/rejectWarehouse")
- @PostMapping(value = "/return")
- @PostMapping(value = "/returnList")
- @DeleteMapping(value = "/delete")
- @PostMapping(value = "/claim")
- @PostMapping(value = "/unClaim")
- @PostMapping(value = "/delegate")
- @PostMapping(value = "/transfer")
- @RequestMapping("/diagram/{processId}")

## LightEvaluateFeedbackController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightEvaluate/LightEvaluateFeedbackController.java`
- @RequestMapping("/feedback/")
- @GetMapping("/getFeedbackPage")
- @GetMapping("/getFeedbackDetail")
- @GetMapping("/exportFeedback")
- @PostMapping("/addFeedback")
- @PostMapping("/continueFeedback")
- @GetMapping("/getFeedbackCount")
- @PostMapping("/confirmationFeedback")
- @PostMapping("/changeFeedback")
- @PostMapping("/cancelFeedback")
- @PostMapping("/deleteFeedback")
- @PostMapping("/dealFeedback")

## LightEvaluateController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightEvaluate/LightEvaluateController.java`
- @RequestMapping("/merchant/lightEvaluate/")
- @GetMapping("/getEvaluationRecordPage")
- @GetMapping("/exportEvaluationRecord")
- @GetMapping("/getWorkOrderPage")
- @GetMapping("/exportWorkOrder")
- @PostMapping("/updateWorkOrder")

## MerchantEvaluateController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/evaluate/MerchantEvaluateController.java`
- @RequestMapping("/merchant/evaluate/")
- @GetMapping("get.do")
- @PostMapping("/add.do")
- @GetMapping("list.do")

## SaleAreaController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/item/SaleAreaController.java`
- @RequestMapping("/item/saleArea/")
- @GetMapping("findByShop.do")
- @GetMapping("/get.do")
- @PostMapping("save.do")
- @PostMapping("/defaultSaleArea.do")
- @GetMapping("/findAreaTreeById.do")

## CategoryController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/item/CategoryController.java`
- @RequestMapping("/item/category/")
- @GetMapping("children.do")

## ItemController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/item/ItemController.java`
- @RequestMapping("/item/item/")
- @GetMapping("find.do")
- @GetMapping("/getShopItem.do")
- @PostMapping("/addShopRemark.do")
- @GetMapping("/shopItemSearch.do")

## ReleaseItemController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/item/ReleaseItemController.java`
- @RequestMapping("/item/item/")
- @GetMapping("release_init.do")
- @GetMapping("getBreakevenPrice.do")
- @PostMapping("releaseSkuValidate.do")
- @PostMapping("releaseItem.do")
- @PostMapping("copyItem.do")

## SkuController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/item/SkuController.java`
- @RequestMapping("/item/sku/")
- @GetMapping("find.do")
- @PostMapping("skuOnOffShelf.do")
- @GetMapping("/getSkuById.do")
- @PostMapping("inputBarCode.do")

## SpuController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/item/SpuController.java`
- @RequestMapping("/item/spu/")
- @GetMapping("find_by_category.do")

## SkuMealController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/item/SkuMealController.java`
- @RequestMapping("/item/skuMeal/")
- @GetMapping("find.do")
- @GetMapping("/findSkuMealBySkuId.do")
- @PostMapping("saveSkuMeal.do")

## ItemPosterController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/item/ItemPosterController.java`
- @RequestMapping("/item/item/")
- @PostMapping("posterImage.do")
- @PostMapping("getScanCode.do")

## PurchaseController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/item/PurchaseController.java`
- @RequestMapping("/item/purchase/")
- @GetMapping("findCountyPurchaseItem.do")
- @GetMapping("findProfessionalPurchaseItem.do")
- @GetMapping("findEnterprisePurchaseItem.do")
- @GetMapping("findEnterprisePurchaseItemDetail.do")
- @GetMapping("findInternalPurchaseItemDetail.do")
- @GetMapping("findInternalPurchaseItem.do")
- @GetMapping("findExpertPurchaseItem.do")
- @GetMapping("findYzzPurchaseItem.do")
- @GetMapping("listXiaoweiCategory.do")
- @GetMapping("listItemCategory.do")
- @GetMapping("listItemBrandName.do")
- @GetMapping("findLightPurchaseSalesItem.do")
- @GetMapping("find1TP0Item.do")
- @GetMapping("find1QJ0Item.do")
- @GetMapping("find1QJ0ItemDetail.do")
- @GetMapping("findZeroCarbonEStationItem.do")
- @GetMapping("findZeroCarbonItem.do")
- @GetMapping("findAuxiliaryMaterialItem.do")
- @GetMapping("findAuxiliaryMaterialItemDetail.do")

## OperationUserInformationController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/out/OperationUserInformationController.java`
- @RequestMapping("/light/out/user/")
- @PostMapping("/getName.do")
- @PostMapping("/getAccountInfo.do")

## OssImageController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/oss/OssImageController.java`
- @RequestMapping("/oss/image/")
- @PostMapping("upload.do")
- @RequestMapping(value="uploadPdf.do", method = RequestMethod.POST)
- @RequestMapping(value = "uploadFile.do", method = RequestMethod.POST)

## OssVideoController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/oss/OssVideoController.java`
- @RequestMapping("/oss/video/")
- @PostMapping("upload.do")
- @GetMapping("/getVideoUrl.do")

## OssMultipartUploadController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/oss/OssMultipartUploadController.java`
- @RequestMapping("/oss/multipart/")
- @PostMapping("initiate.do")
- @PostMapping("uploadPart.do")
- @PostMapping("complete.do")
- @GetMapping("progress.do")
- @GetMapping("listParts.do")
- @PostMapping("abort.do")

## OssFileController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/oss/OssFileController.java`
- @RequestMapping("/oss/file/")
- @PostMapping("upload.do")

## NetPayCertificateTestController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/netPay/NetPayCertificateTestController.java`
- @RequestMapping("/netPay/certificateTest")
- @RequestMapping("/test.do")

## MerchantTradeController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/echannel/MerchantTradeController.java`
- @RequestMapping("/echannel/")
- @GetMapping("tradeOrderList.do")
- @GetMapping("getCctExpressPrice.do")
- @PostMapping("deliverTradeOrder.do")

## LightMakeOrderController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightMakeOrderController.java`
- @RequestMapping("/light/makeOrder/")
- @GetMapping("/getStore.do")
- @GetMapping("/findStore.do")
- @PostMapping("create.do")
- @PostMapping("/vip/create.do")
- @PostMapping("/vip/getStations.do")
- @PostMapping("/post1.do")
- @PostMapping("/sku.do")
- @GetMapping("/get.do")
- @GetMapping("/findOrderArea")
- @GetMapping("/export.do")
- @PostMapping("/getStoresByOrders.do")
- @PostMapping("/findAllDisplayName.do")

## LightOverdueListDetailRejectOtherController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightOverdueListDetailRejectOtherController.java`
- @RequestMapping("/lightOverdueListDetailRejectOther")
- @GetMapping("doList.do")

## LightInstantRewardPolicyControllerForMerchant
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightInstantRewardPolicyControllerForMerchant.java`
- @RequestMapping("/LightInstantRewardPolicy")
- @GetMapping("/list")
- @GetMapping("/queryLightInstantRewardPolicyDetail")

## LightStopStationController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightStopStationController.java`
- @RequestMapping("/light/stopStation/")
- @GetMapping("/stopStationList.do")
- @PostMapping("/applyStop.do")
- @PostMapping("/revocationApply.do")
- @GetMapping("/checkStationStop.do")
- @PostMapping("/auditBySp.do")

## LightModulePartCompleteApplyController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightModulePartCompleteApplyController.java`
- @RequestMapping("/light/module/complete/apply")
- @GetMapping("list.do")
- @GetMapping("detail.do")
- @GetMapping("preApply.do")
- @PostMapping("add.do")
- @PostMapping("edit.do")
- @PostMapping("delete.do")

## LightSupplierOrderController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightSupplierOrderController.java`
- @RequestMapping("/light/purchaseOrder/")
- @GetMapping("list.do")
- @GetMapping("export.do")
- @PostMapping("deliver.do")
- @PostMapping("importDeliver.do")
- @GetMapping("deliverTemplate.do")
- @GetMapping("findExpressRecord.do")
- @GetMapping("preOrderList.do")
- @GetMapping("preOrderExport.do")
- @GetMapping("preOrderRelateList.do")
- @GetMapping("preOrderRelateExport.do")

## LightSpGridAwardOrderController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightSpGridAwardOrderController.java`
- @RequestMapping("/light/lightSpGridAwardOrder/")
- @GetMapping("list.do")
- @GetMapping("export.do")

## PowerPurchaseManagementController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/PowerPurchaseManagementController.java`
- @RequestMapping("/light/powerPurchase")
- @GetMapping("/list")
- @GetMapping("/all")

## LightSubStockController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightSubStockController.java`
- @RequestMapping("/light/sub/stock/")
- @GetMapping("findStock.do")
- @GetMapping("/export.do")

## LightOperationDepositController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightOperationDepositController.java`
- @RequestMapping("/light/lightOperationDeposit/")
- @GetMapping("list.do")
- @GetMapping("sumPay")
- @GetMapping("checkToPay")
- @PostMapping("addDeposit.do")
- @PostMapping("toPay.do")
- @PostMapping("modifyDeposit.do")

## LightOverdueListController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightOverdueListController.java`
- @RequestMapping("/lightOverdueList")
- @GetMapping("doList.do")
- @RequestMapping("doExport.do")

## WholeVillageTogetherController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/WholeVillageTogetherController.java`
- @RequestMapping("wholeVillageTogether")
- @GetMapping("tableList")
- @GetMapping("selectOption")
- @GetMapping("getDetail")
- @PostMapping("edit")
- @PostMapping("add")
- @GetMapping("exit")

## OffLineStationFlowController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/OffLineStationFlowController.java`
- @RequestMapping("OffLineStationFlow")
- @GetMapping("/queryMerchantPageOffLine.do")
- @PostMapping("commitOffLineInfo")
- @PostMapping("editOffLineInfo")

## SpecialFlagObjectController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/SpecialFlagObjectController.java`
- @RequestMapping("/specialFlagObject")
- @GetMapping("findList")
- @GetMapping("findListAll")

## LightProjectFunnelManagementController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightProjectFunnelManagementController.java`
- @RequestMapping("/light/funnel/")
- @PostMapping("addProject.do")
- @RequestMapping(value = { "/getBranchCenter.do" }, method = {RequestMethod.GET})
- @GetMapping("find.do")
- @GetMapping("getDetail.do")
- @PostMapping("updateProject.do")

## LightOverduePolicyController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightOverduePolicyController.java`
- @RequestMapping("/lightOverduePolicy")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightSpPlanConfigController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightSpPlanConfigController.java`
- @RequestMapping("/light/sp/planConfig")
- @GetMapping("/findBy")
- @GetMapping("/findAvailableTypeEnum")
- @GetMapping("/checkSpDoFourItem")

## LightStationNannyController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightStationNannyController.java`
- @RequestMapping("/light/station/nanny/")
- @GetMapping("list.do")
- @GetMapping("export.do")

## LightSpSubBaseDataController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightSpSubBaseDataController.java`
- @RequestMapping("/light/lightSubBaseData/")
- @GetMapping("getSubList.do")
- @GetMapping("list.do")
- @GetMapping("export.do")

## LightOrderUserController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightOrderUserController.java`
- @RequestMapping("/light/orderUser/")
- @GetMapping("/findOrderUserByPage.do")
- @PostMapping("/addOrderUser.do")
- @PostMapping("/freezeOrderUser.do")
- @PostMapping("/unFreezeOrderUser.do")
- @PostMapping("/removeOrderUser.do")
- @GetMapping("/orderUserList.do")

## LightPlanChangeController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightPlanChangeController.java`
- @RequestMapping("/light/planChange/")
- @GetMapping("/changeList.do")
- @GetMapping("/addChange.do")
- @PostMapping("/savePlanChange.do")
- @PostMapping("/updatePlanChange.do")
- @GetMapping("/showChangeDetail.do")
- @PostMapping("/removePlanChange.do")
- @PostMapping("/uploadCompleteInfo.do")
- @PostMapping("/editUploadCompleteInfo.do")

## LightConfirmOrderController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightConfirmOrderController.java`
- @RequestMapping("/light/order/confirm/")
- @GetMapping("/getConfirmOrder.do")
- @GetMapping("/exportConfirmOrder.do")
- @GetMapping("/getConfirmOrderRegion.do")
- @GetMapping("/getConfirmOrderArea.do")
- @GetMapping("/getDetails.do")
- @GetMapping("/getSkus.do")
- @PostMapping("/confirm.do")
- @PostMapping("/quitOrder.do")
- @PostMapping("/create.do")
- @PostMapping("/verify.do")

## CmPreOrderController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/CmPreOrderController.java`
- @RequestMapping("/light/cmPreOrder/")
- @GetMapping("list.do")
- @PostMapping("deliver.do")
- @GetMapping("export.do")
- @GetMapping("/applyList.do")
- @GetMapping("applyListExport.do")
- @PostMapping("/confirmSign.do")
- @GetMapping("/applyPreInfo.do")
- @PostMapping("/apply.do")
- @PostMapping("/update.do")
- @GetMapping("/applyDetail.do")
- @PostMapping("/cancel.do")

## LightElectricUnusualController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightElectricUnusualController.java`
- @RequestMapping("/lightElectricUnusual/")
- @GetMapping("list.do")
- @GetMapping("doExport.do")

## LightSpShareQuotaController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightSpShareQuotaController.java`
- @RequestMapping("/light/spShareQuota/")
- @GetMapping("list.do")
- @GetMapping("subsidiarySpList.do")
- @GetMapping("companyInfo.do")
- @PostMapping("apply.do")
- @GetMapping("detail.do")
- @GetMapping("update.do")
- @GetMapping("stop.do")
- @GetMapping("reApply.do")
- @GetMapping("/previewQuotaContract.do")
- @PostMapping("/signQuotaContract.do")
- @GetMapping("/findContract.do")

## LightStationYuexiuAccountCancelController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightStationYuexiuAccountCancelController.java`
- @RequestMapping("/yuexiu/account/cancel/")
- @PostMapping("add.do")
- @GetMapping("list.do")

## LightSubTransferOrderController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightSubTransferOrderController.java`
- @RequestMapping("/light/sub/transfer/")
- @GetMapping("/get.do")
- @PostMapping("/add.do")
- @GetMapping("/getSku.do")

## LightSpWithdrawalApplicationController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightSpWithdrawalApplicationController.java`
- @RequestMapping("/lightSpWithdrawalApplication")
- @GetMapping("doList.do")
- @PostMapping("add.do")
- @PostMapping("detail.do")
- @PostMapping("edit.do")
- @PostMapping("spConfirm.do")
- @PostMapping("spTransferVoucher.do")
- @PostMapping("checkSpInfo.do")
- @GetMapping("doExport.do")

## LightSpOrderController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightSpOrderController.java`
- @RequestMapping("/sp/order/")
- @GetMapping("list.do")
- @GetMapping("findLastInvoiceInfo.do")
- @GetMapping("detail.do")
- @GetMapping("stationInfo.do")
- @PostMapping("apply.do")
- @PostMapping("edit.do")
- @PostMapping("cancel.do")
- @PostMapping("pay.do")
- @GetMapping("/getRepoUrl.do")
- @GetMapping("/getRepoSignLink.do")
- @GetMapping("/uploadInvoice.do")
- @PostMapping("addMaterialPurchase.do")

## LightPurchaseApplySettleController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightPurchaseApplySettleController.java`
- @RequestMapping("/light/lightPurchaseApplySettle/")
- @GetMapping("list.do")
- @GetMapping("export.do")
- @GetMapping("/detail.do")

## LightStationPlanConfigController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightStationPlanConfigController.java`
- @RequestMapping("/light/planConfig/")
- @GetMapping("/findSummaryInfo")
- @GetMapping("/exportSummaryPlanConfig.do")

## LightWvRentRecordController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightWvRentRecordController.java`
- @RequestMapping("/light/wv/rent/")
- @GetMapping("/list.do")

## LightStockController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightStockController.java`
- @RequestMapping("/light/stock/")
- @GetMapping("findStock.do")
- @GetMapping("findStockGroupBySkuCode.do")
- @GetMapping("exportStockGroupBySkuCode.do")
- @GetMapping("stock/export.do")
- @GetMapping("thirdParty/findStockStoreNameList.do")
- @GetMapping("thirdParty/findStock.do")
- @GetMapping("thirdParty/stock/export.do")
- @GetMapping("findStoreOut.do")
- @GetMapping("export.do")
- @GetMapping("/findBySkuCodeAndStoreCode.do")

## LightNewMerchantRewardDetailController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightNewMerchantRewardDetailController.java`
- @RequestMapping("/light/newMerchantRewardDetail/")
- @GetMapping("list.do")
- @GetMapping("export.do")

## ChannelYuexiuProjectController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/ChannelYuexiuProjectController.java`
- @RequestMapping("/light/channelYuexiuProject/")
- @GetMapping("/getString.do")

## LightNewMerchantRewardController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightNewMerchantRewardController.java`
- @RequestMapping("/light/newMerchantReward/")
- @GetMapping("/list.do")
- @GetMapping("/detail.do")
- @GetMapping("export.do")

## LightStationSignController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightStationSignController.java`
- @RequestMapping("/light/signNotify/")
- @PostMapping("/saveHxqNotifyUrl.do")
- @PostMapping("/saveInstallNotifyUrl.do")
- @PostMapping("/saveFinanceNotifyUrl.do")
- @PostMapping("/saveStopNotifyUrl.do")

## LightStationSettleSumController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightStationSettleSumController.java`
- @RequestMapping("/light/settle/sum")
- @GetMapping("/list.do")
- @GetMapping("export.do")
- @GetMapping("spCount.do")

## LightSpController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightSpController.java`
- @RequestMapping("/light/sp/")
- @PostMapping("/registSp.do")
- @GetMapping("/getSpInfo.do")
- @PostMapping("/updateSp.do")
- @GetMapping("/previewContract.do")
- @GetMapping("/showContract.do")
- @PostMapping("/signContract.do")
- @PostMapping("/getSignedContract.do")
- @PostMapping("/registStation.do")
- @PostMapping("/registerStationCache.do")
- @PostMapping("/updateStation.do")
- //    @GetMapping("/findOrderRegion")
- @GetMapping("/findOrderRegion")
- @GetMapping("/auclon/findOrderRegion")
- @GetMapping("/stationList.do")
- @GetMapping("/secondBusinessNameList.do")
- @GetMapping("stationListExport.do")
- @GetMapping("/stationListByLnApp.do")
- @GetMapping("/stationStatusSum.do")
- @GetMapping("/getStationById.do")
- @GetMapping("/getYxStationById.do")
- @GetMapping("/findPlanByStationId.do")
- @GetMapping("/findOriPlanByStationId.do")
- @PostMapping("/removeStation.do")
- @GetMapping("/findType.do")
- @GetMapping("/findByType.do")
- @GetMapping("/findByStationAndType.do")
- @GetMapping("/findProcessRecord.do")
- @GetMapping("/findByStationCodeProcessRecord.do")
- @GetMapping("findAllStatusByStationId")
- @GetMapping("/getPlanBOM.do")
- @GetMapping("/getStationConfirm.do")
- @PostMapping("/confirmStation.do")
- @PostMapping("/queryContractRecord.do")
- @GetMapping("/previewNewContract.do")
- @GetMapping("/showNewContract.do")
- @PostMapping("/signNewContract.do")
- @PostMapping("/signStopContract.do")
- @PostMapping("/isSignedAgreement")
- @GetMapping("/findPolicy")
- @GetMapping("/queryPolicyDetail")
- @GetMapping("/findInstallAdvancePolicy")
- @GetMapping("/queryInstallAdvancePolicyDetail")
- @GetMapping("/findGridPolicy")
- @PostMapping("/registEPCSp.do")
- @PostMapping("/updateEpcSp.do")
- @GetMapping("/checkSpRegister")
- @GetMapping("/checkEpcSpRegister")
- @GetMapping("/findStreet")
- @GetMapping("/stationListYt.do")
- @GetMapping("/waitAuditStationList.do")
- @GetMapping("toBeSurveyedListExport.do")

## LightModuleSnController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightModuleSnController.java`
- @RequestMapping("/light/moduleSn")
- @GetMapping("getHistory")
- @GetMapping("export")

## LightRentController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightRentController.java`
- @RequestMapping("/light/lightRent/")
- @GetMapping("list.do")
- @GetMapping("export.do")
- @GetMapping("/stationList.do")
- @GetMapping("/billList.do")
- @GetMapping("/accountRecordList.do")
- @GetMapping("/accountRecordByOp.do")
- @GetMapping("/accountDetailOp.do")

## LightSpStoreController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightSpStoreController.java`
- @RequestMapping("/light/spStore/")
- @GetMapping("/getStore.do")
- @GetMapping("/doListForAddress.do")
- @GetMapping("doExport.do")
- @GetMapping("/getStoreListBySpId.do")
- @GetMapping("/getAllStoreListBySpId.do")
- @PostMapping("/addAddress.do")
- @GetMapping("/enable.do")
- @GetMapping("/disable.do")
- @PostMapping("/edit.do")
- @GetMapping("/findAddressByStoreId.do")
- @PostMapping("/addSecondClassStore.do")
- @GetMapping("/findSpStoreByLoginAccount.do")

## LightEpcPlanChangeController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightEpcPlanChangeController.java`
- @RequestMapping("/light/epcStation/planChange/")
- @GetMapping("/findList.do")
- @GetMapping("/preInfo.do")
- @PostMapping("/add.do")
- @PostMapping("/update.do")
- @GetMapping("/detail.do")
- @PostMapping("/remove.do")

## LightUniqueImageController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightUniqueImageController.java`
- @RequestMapping("/light/imageVerify/")
- @PostMapping("save")
- @PostMapping("verify")
- @PostMapping("getDetail")

## LightInstantGridRewardPolicyControllerForMerchant
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightInstantGridRewardPolicyControllerForMerchant.java`
- @RequestMapping("/LightInstantGridRewardPolicy")
- @GetMapping("list.do")
- @GetMapping("queryLightInstantGridRewardPolicyDetail")

## LightSpStaffController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightSpStaffController.java`
- @RequestMapping("/light/sp/staff/")
- @GetMapping("list.do")
- @PostMapping("add.do")
- @PostMapping("delete.do")
- @GetMapping("regionList.do")
- @PostMapping("editRegion.do")
- @GetMapping("roles.do")
- @GetMapping("find.do")
- @GetMapping("findByRegion.do")
- @GetMapping("detail.do")
- @PostMapping("relation/update.do")

## LightSpGridAwardOrderDetailController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightSpGridAwardOrderDetailController.java`
- @RequestMapping("/light/lightSpGridAwardOrderDetail/")
- @GetMapping("list.do")
- @GetMapping("export.do")

## LightAwardAppealController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightAwardAppealController.java`
- @RequestMapping("/light/awardAppeal/")
- @PostMapping("appeal.do")
- @GetMapping("/list.do")
- @GetMapping("/detail.do")
- @PostMapping("edit.do")
- @GetMapping("delete.do")
- @GetMapping("check.do")
- @PostMapping("/checkItems.do")

## CmConstructionProgressController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/CmConstructionProgressController.java`
- @RequestMapping("/light/cmConstructionProgress/")
- @GetMapping("list.do")
- @GetMapping("statusCount.do")
- @GetMapping("detail.do")
- @GetMapping("nodeDetail.do")
- @GetMapping("nodeAttachmentTemplate.do")
- @PostMapping("/submitNodeProgress.do")
- @GetMapping("/finish/list.do")
- @GetMapping("/finish/statusCount.do")

## LightSkuDataController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightSkuDataController.java`
- @RequestMapping("/light/lightSkuData")
- @GetMapping("/getInverterBrandList.do")

## LightSpSubBuildDataController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightSpSubBuildDataController.java`
- @RequestMapping("/light/lightSubBuildData/")
- @GetMapping("list.do")
- @GetMapping("export.do")

## LightProjectManagementController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightProjectManagementController.java`
- @RequestMapping("/light/project/")
- @GetMapping("/confirmProjectList.do")
- @GetMapping("/checkBeforeSign.do")
- @GetMapping("/findProject.do")
- @PostMapping("/confirmContract.do")
- @GetMapping("/previewProjectContract.do")
- @PostMapping("/signProjectContract.do")

## LightProfitController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightProfitController.java`
- @RequestMapping("/light/profit/")
- @GetMapping("/getLightProfit.do")
- @GetMapping("/getLightStation.do")

## LightStockChangeController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightStockChangeController.java`
- @RequestMapping("/light/stockChange/")
- @GetMapping("list.do")

## LightConstructionTeamController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightConstructionTeamController.java`
- @RequestMapping("/light/constructionTeam/")
- @GetMapping("/findTeamByPage.do")
- @PostMapping("/addConstructionTeam.do")
- @PostMapping("/freezeConstructionTeam.do")
- @PostMapping("/unFreezeConstructionTeam.do")
- @PostMapping("/removeConstructionTeam.do")
- @GetMapping("/teamList.do")

## GridStationController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/GridStationController.java`
- @RequestMapping("/light/gridStation/")
- @GetMapping("/getAcceptanceInfo.do")

## PurchaseApplySettleDepositRefundController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/PurchaseApplySettleDepositRefundController.java`
- @RequestMapping("/purchaseApplySettleDepositRefund/")
- @GetMapping("/list.do")
- @GetMapping("/addPrepareInfo.do")
- @GetMapping("/queryDepositRecord.do")
- @PostMapping("/add.do")
- @PostMapping("/update.do")
- @PostMapping("/updateBill.do")
- @PostMapping("/delete.do")
- @GetMapping("/detail.do")

## IndustryCommerceController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/IndustryCommerceController.java`
- @RequestMapping("/light/epc/")
- @PostMapping("/regist.do")
- @PostMapping("/update.do")

## LightComponentLibraryController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightComponentLibraryController.java`
- @RequestMapping("/light/componentLibrary/")
- @GetMapping("find.do")
- @GetMapping("findOverview.do")
- @GetMapping("export.do")

## LightCoinStationController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightCoinStationController.java`
- @RequestMapping("/light/coinStation/")
- @GetMapping("find.do")
- @GetMapping("export.do")
- @GetMapping("/detail.do")

## LightInstantRewardControllerForMerchant
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightInstantRewardControllerForMerchant.java`
- @RequestMapping("/LightInstantReward")
- @GetMapping("/list")
- @GetMapping("/queryLightInstantRewardDetail")
- @PostMapping("/export")

## LightSpHomePageController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightSpHomePageController.java`
- @RequestMapping("/sp/homepage/")
- @GetMapping("count1")
- @GetMapping("count2")
- @GetMapping("count3")
- @GetMapping("queryLimit")
- @GetMapping("warningList")
- @GetMapping("logList")

## LightSubSpController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightSubSpController.java`
- @RequestMapping("/light/spAccount/")
- @PostMapping("/addAccount.do")
- @PostMapping("/editAccount.do")
- @GetMapping("/spAccountList.do")
- @GetMapping("/getAccountDetail.do")
- @PostMapping("/freezeAccount.do")
- @PostMapping("/unFreezeAccount.do")
- @GetMapping("/checkSubRole.do")
- @GetMapping("regionList.do")
- @PostMapping("editRegion.do")
- @GetMapping("getSubSp.do")
- @GetMapping("findSubSpNoSecondClassStore.do")

## LightEnablePolicyController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightEnablePolicyController.java`
- @RequestMapping("/light/policy/")
- @GetMapping("spCount.do")
- @PostMapping("confirm.do")
- @GetMapping("list.do")
- @GetMapping("merchantPolicyDetailQuery.do")
- @GetMapping("detail.do")

## GvsWarehouseAgeAnalysisController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/GvsWarehouseAgeAnalysisController.java`
- @RequestMapping("/light/gvs/stockAge")
- @GetMapping("/doList.do")
- @GetMapping("doExport.do")
- @GetMapping("findSkuInfo")
- @PostMapping("createPurchaseAppeals")
- @PostMapping("modifyPurchaseAppeals")
- @GetMapping("/findAuditList.do")
- @GetMapping("/exportAuditList.do")
- @GetMapping("/getGvsAgeNum")
- @GetMapping("/getStationSku")
- @GetMapping("downloadEmpty.do")
- @GetMapping("/getMakeOrderSku")

## LightStationRepurchaseController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightStationRepurchaseController.java`
- @RequestMapping("/stationRepurchase/")
- @GetMapping("/list.do")
- @GetMapping("/detail.do")
- @GetMapping("/addPrepareInfo.do")
- @PostMapping("/add.do")
- @PostMapping("/update.do")
- @PostMapping("/cancel.do")
- @PostMapping("/pay.do")
- @GetMapping("/buy/getUrl.do")
- @GetMapping("/buy/getSignLink.do")
- @GetMapping("/acceptance/getUrl.do")
- @GetMapping("/acceptance/getSignLink.do")

## LightSpAuthorityZoneController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightSpAuthorityZoneController.java`
- @RequestMapping("/light/sp/")
- @GetMapping("/listSpAuthorityZone.do")
- @GetMapping("/exportSpAuthorityZone.do")
- @GetMapping("/listProjectCompany.do")
- @GetMapping("/getMasterProvince.do")
- @PostMapping("/applyAuthorityRegion.do")
- @GetMapping("/getAuthorityRegionDetail.do")
- @PostMapping("/editAuthorityRegion.do")
- @GetMapping("/previewRegionContract.do")
- @PostMapping("/signRegionContract.do")
- @GetMapping("/findSpRegion.do")
- @GetMapping("/findSpRegionForApp.do")

## DccNotifyController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/DccNotifyController.java`
- @RequestMapping("/light/dccCallback/")
- @PostMapping("/companyCheckNotify.do")
- @PostMapping("/signedNotify.do")
- @PostMapping("/signedNotifyUrlToOp.do")
- @PostMapping("/signedNotifyUrlToOpIac.do")
- @PostMapping("/confrimCallBack.do")
- @PostMapping("/zeroCarbonReceiptOrde.do")
- @PostMapping("/repairsPayCallBack.do")
- @PostMapping("/repairsReceiveCallBack.do")
- @PostMapping("/zeroCarbonConfrimCallBack.do")

## AppSearchHistory
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/AppSearchHistory.java`
- @RequestMapping("search/history")
- @GetMapping("querySearchHistory")
- @GetMapping("deleteSearchHistory")

## LightStationChangePlanToDoController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightStationChangePlanToDoController.java`
- @RequestMapping("/planChange/todo")
- @GetMapping("/findByChangeId")

## LightTransferSpApplyController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightTransferSpApplyController.java`
- @RequestMapping("/lightTransferSpApply/")
- @GetMapping("/list.do")
- @GetMapping("/detail.do")
- @GetMapping("/addPreInfo.do")
- @GetMapping("/skuInfo.do")
- @PostMapping("/add.do")
- @PostMapping("/update.do")
- @PostMapping("/cancel.do")
- @PostMapping("outTransfer.do")
- @GetMapping("export.do")

## LightStationSpController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightStationSpController.java`
- @RequestMapping("/light/spStation/")
- @PostMapping("/auditBySpPlan.do")
- @PostMapping("/auditOKBySp.do")
- @PostMapping("/auditFailBySp.do")

## LightSpServiceProvinceController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightSpServiceProvinceController.java`
- @RequestMapping("/light/spServiceProvince/")
- @GetMapping("list.do")
- @PostMapping("apply.do")
- @PostMapping("update.do")
- @GetMapping("findApprovedList.do")

## DatabaseManagementController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/DatabaseManagementController.java`
- @RequestMapping("/light/databaseManagement/")
- @GetMapping("list.do")
- @PostMapping ("addNum")
- @GetMapping("downloadFile.do")

## LightSpAuclonStoreController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightSpAuclonStoreController.java`
- @RequestMapping("/light/store/auclon/")
- @GetMapping("/getStore.do")
- @PostMapping("/import.do")
- @PostMapping("/add.do")
- @PostMapping("/enabled.do")
- @PostMapping("/disabled.do")
- @GetMapping("/findByCity.do")
- @GetMapping("/findByName.do")
- @GetMapping("/findOutStore.do")
- @GetMapping("/findInStore.do")
- @PostMapping("/update.do")

## LightStationYuexiuAccountController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightStationYuexiuAccountController.java`
- @RequestMapping("/yuexiu/account/")
- @GetMapping("list.do")

## LightNegativeReducePolicyController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightNegativeReducePolicyController.java`
- @RequestMapping("/lightNegativeReducePolicy")
- @RequestMapping("doList.do")
- @RequestMapping("queryLightNegativeReducePolicyDetail")

## LightStationInfoUpdateController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightStationInfoUpdateController.java`
- @RequestMapping("/stationInfo/update/")
- @PostMapping("/createUpdate.do")
- @GetMapping("/getList.do")
- @GetMapping("/getDetail.do")
- @PostMapping("/update.do")
- @PostMapping("/delete.do")
- @GetMapping("/getStationDetail.do")
- @GetMapping("downloadEmpty.do")

## LightNewMerchantPolicyController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightNewMerchantPolicyController.java`
- @RequestMapping("/light/newMerchantPolicy/")
- @GetMapping("/list.do")
- @GetMapping("/queryNewMerchantPolicyDetail")
- @GetMapping("/detail.do")

## LightStationPartCompleteApplyController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightStationPartCompleteApplyController.java`
- @RequestMapping("/light/part/complete/apply")
- @GetMapping("list.do")
- @GetMapping("detail.do")
- @GetMapping("preApply.do")
- @PostMapping("add.do")
- @PostMapping("edit.do")
- @PostMapping("delete.do")

## LightStationEnableRewardController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightStationEnableRewardController.java`
- @RequestMapping("/light/lightStationEnableReward/")
- @GetMapping("list.do")
- @GetMapping("detail.do")
- @GetMapping("export.do")

## LightEnablePolicySpPropController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightEnablePolicySpPropController.java`
- @RequestMapping("/lightEnablePolicySpProp")
- @RequestMapping("list")
- @RequestMapping("findBySpIdAndTime")

## LightDccCompanyController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightDccCompanyController.java`
- @RequestMapping("/light/dcc/company")
- @GetMapping("/detail.do")
- @PostMapping("/fddRegist.do")
- @PostMapping("/fddCheckIsRegist.do")
- @PostMapping("/fddAuth.do")
- @PostMapping("/sign.do")
- @GetMapping("/previewSpContract.do")
- @GetMapping("/previewSpEpcContract.do")
- @GetMapping("/previewOpContract.do")
- @GetMapping("/previewContract.do")
- @PostMapping("/signContract.do")
- @PostMapping("/serviceSignMaster.do")
- @PostMapping("/serviceSignEpcMaster.do")
- @PostMapping("/opSignMaster.do")
- @PostMapping("/opAuthority.do")
- @PostMapping("/opZeroSignContract.do")
- @PostMapping("/getLastSingedUrl.do")
- @PostMapping("/modifyFddCompanyInfo.do")
- @PostMapping("/modifyFddCompanyInfoList.do")
- @GetMapping("/modifyFddCompanyDetail.do")

## LightOpContractRecordController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightOpContractRecordController.java`
- @RequestMapping("/light/lightOpContractRecord/")
- @GetMapping("list.do")
- @GetMapping("/showNewContract.do")

## DispatchWorkOrderController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/DispatchWorkOrderController.java`
- @RequestMapping("/light/workOrder/")
- @GetMapping("/workOrderList.do")
- @GetMapping("/exportWorkOrderList.do")
- @GetMapping("/getWorkOrderInfo.do")
- @GetMapping("/getAuditWorkOrderDetail.do")
- @PostMapping("/auditOk.do")
- @PostMapping("/auditOkTechRectify.do")
- @PostMapping("/auditReject.do")

## LightOverdueListDetailController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightOverdueListDetailController.java`
- @RequestMapping("/lightOverdueListDetail")
- @GetMapping("doList.do")
- @RequestMapping("findPolicyByListId.do")
- @RequestMapping("doExport.do")

## LightLogOffController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightLogOffController.java`
- @RequestMapping("/light/lightLogOff/")
- @GetMapping("getMemberId")
- @GetMapping("creatData")
- @PostMapping("/checkCode")

## LightLendController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightLendController.java`
- @RequestMapping("/lightLend/")
- @RequestMapping(value = "lightLendAudit.do", method = {RequestMethod.POST})
- @RequestMapping(value = "lightLendDelivery/snCodeTemplate.do", method = {RequestMethod.POST})
- @RequestMapping(value = "lightLendDelivery/snCode.do", method = {RequestMethod.POST})
- @RequestMapping(value = {"sn/downTemplate.do"}, method = {RequestMethod.GET})
- @GetMapping("/findList.do")
- @GetMapping("/findOutRecordList.do")

## LightStationPlanDesignController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightStationPlanDesignController.java`
- @RequestMapping("/light/planDesign/")
- @GetMapping("getAllPlanDesignByConfigType")

## PurchaseApplySettleNoPaperController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/PurchaseApplySettleNoPaperController.java`
- @RequestMapping("/purchaseApplySettleNoPaper/")
- @GetMapping("/list.do")
- @GetMapping("/addPrepareInfo.do")
- @GetMapping("/queryPurchaseForSettle.do")
- @PostMapping("/add.do")
- @PostMapping("/update.do")
- @PostMapping("/delete.do")
- @GetMapping("/detail.do")
- @PostMapping("/relateInvoice.do")
- @GetMapping("/getConfirmBeforeBillUrl.do")
- @GetMapping("/getConfirmUrl.do")

## LightAuxiliaryMakeOrderController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightAuxiliaryMakeOrderController.java`
- @RequestMapping("/light/auxiliaryMakeOrder/")
- @PostMapping("/batchCreate")
- @GetMapping("/listForMerchant")
- @GetMapping("/findOrderRegion")
- @GetMapping("/orderDetail")
- @GetMapping("export.do")
- @GetMapping("/get.do")
- @GetMapping("/findOrderArea")
- @GetMapping("/order/export.do")

## CmLightProjectController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/CmLightProjectController.java`
- @RequestMapping("/light/cmProject/")
- @GetMapping("/cmProjectList.do")
- @GetMapping("/getContract.do")
- @GetMapping("/findPaymentList.do")
- @PostMapping("/uploadFile.do")
- @PostMapping("/uploadInvoice.do")

## LightProjectPartnerController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightProjectPartnerController.java`
- @RequestMapping("/light/partner/")
- @PostMapping("/registPartner.do")
- @PostMapping("/updatePartner.do")
- @GetMapping("/getPartnerInfo.do")
- @PostMapping("/partnerRegist.do")
- @PostMapping("/partnerRegistSendSms.do")
- @PostMapping("/partnerAuth.do")

## LightRoboAdvisorOrderController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightRoboAdvisorOrderController.java`
- @RequestMapping("/light/roboAdvisor/")
- @GetMapping("/list.do")
- @GetMapping("/order/get.do")
- @GetMapping("/makeOrder/get.do")
- @GetMapping("/quota/get.do")
- @PostMapping("/create.do")
- @PostMapping("/edit.do")
- @PostMapping("/withdraw.do")
- @PostMapping("/delete.do")
- @GetMapping("/skuInfo.do")

## LightElectricOrderController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightElectricOrderController.java`
- @RequestMapping("/outer")
- @PostMapping("/electric-order/list")
- @PostMapping("/electricity/powerQuery")
- @PostMapping("/fap/callback")
- @PostMapping("/cm/signLedger")

## LightStationContractInfoController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightStationContractInfoController.java`
- @RequestMapping("/lightStationContractInfo/")
- @GetMapping("findNewOne.do")

## LightStationRegisterDraftController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightStationRegisterDraftController.java`
- @RequestMapping("/light/draft")
- @GetMapping("/getList.do")
- @GetMapping("/getDetail.do")
- @PostMapping("/delete.do")
- @PostMapping("statinInfos.do")

## LightStationNannyUserController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightStationNannyUserController.java`
- @RequestMapping("/light/station/nanny/user/")
- @GetMapping("list.do")
- @GetMapping("export.do")

## LightGlobalStationController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightGlobalStationController.java`
- @RequestMapping("/light/globalStation/")
- @GetMapping("/stationList.do")
- @GetMapping("/exportGlobalStationList.do")

## PushStationController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/PushStationController.java`
- @RequestMapping("/light/confirmStation/")
- @PostMapping("cancelStation")
- @PostMapping("cacheStation")

## LightCompleteStageController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightCompleteStageController.java`
- @RequestMapping("/light/completeStage/")
- @PostMapping("imagePredict")
- @PostMapping("imageQueryOCR")
- //    @PostMapping("gridCertOCR")
- //    @PostMapping("gridCertQueryOCR")
- @PostMapping("cacheForApp")
- @GetMapping("getCacheForApp")

## LightOperateController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightOperateController.java`
- @RequestMapping("/light/operate/")
- @GetMapping("findPlanBySourceHq.do")
- @PostMapping("complete.do")

## CmConstructionPlanController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/CmConstructionPlanController.java`
- @RequestMapping("/light/cmConstructionPlan/")
- @GetMapping("list.do")
- @GetMapping("statusCount.do")
- @GetMapping("stageList.do")
- @GetMapping("nodeList.do")
- @PostMapping("/create.do")
- @PostMapping("/cache.do")
- @PostMapping("/getCache.do")
- @PostMapping("/update.do")
- @GetMapping("detail.do")

## DepositRecordController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/DepositRecordController.java`
- @RequestMapping("/depositRecord/")
- @GetMapping("/list.do")
- @GetMapping("export.do")

## LightAuxiliaryMaterialDepositAddController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightAuxiliaryMaterialDepositAddController.java`
- @RequestMapping("/light/auxiliaryDepositAdd/")
- @GetMapping("findPage.do")
- @GetMapping("getDeposit.do")
- @PostMapping("applyQuotaAudit.do")
- @PostMapping("addDeposit.do")
- @PostMapping("modifyDeposit.do")

## LightOpContractController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightOpContractController.java`
- @RequestMapping("/light/op/contract")
- @GetMapping("list.do")
- @GetMapping("/detail.do")
- @GetMapping("/checkContractStatus")
- @GetMapping("/newContractSign")
- @GetMapping("/newContractSignDetail")
- @GetMapping("/renewalContractFlag")
- @GetMapping("/newZeroContractSign")

## LightUnionpayUserController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightUnionpayUserController.java`
- @RequestMapping("/light/unionpay/user/")
- @GetMapping("/list.do")
- @GetMapping("export.do")
- @PostMapping("pushYinLian.do")
- @PostMapping("queryUserSign.do")

## InvoiceCheckController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/InvoiceCheckController.java`
- @RequestMapping("/invoiceCheck/")
- @GetMapping("/list.do")
- @GetMapping("/queryInvoiceForSettle.do")
- @PostMapping("/getInvoiceInfo.do")
- @PostMapping("/addInvoices.do")
- @PostMapping("/updateInvoices.do")
- @PostMapping("/deleteInvoice.do")
- @PostMapping("/manualAddInvoiceCheck.do")
- @PostMapping("/manualAddInvoice.do")

## LightStationController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightStationController.java`
- @RequestMapping("/light/station/")
- @PostMapping("/registHoseholdStation.do")
- @PostMapping("/registerHoseholdStationCache.do")
- @PostMapping("/updateHoseholdStation.do")
- @PostMapping("/registWholeVillageStation.do")
- @PostMapping("/registerWholeVillageStationCache.do")
- @PostMapping("/updateWholeVillageStation.do")
- @PostMapping("/registCorpStation.do")
- @PostMapping("/registerCorpStationCache.do")
- @PostMapping("/updateCorpStation.do")
- @PostMapping("/registGovStation.do")
- @PostMapping("/registerGovStationCache.do")
- @PostMapping("/updateGovStation.do")
- @PostMapping("confirmAndSubmitStationInfo")
- @PostMapping("confirmAndSubmitStationInfoZh")
- @PostMapping("confirmAndSubmitStationInfoChd")
- @PostMapping("confirmAndSubmitStationInfoDh")
- @PostMapping("confirmAndSubmitStationInfoGf")
- @PostMapping("confirmAndSubmitStationInfoBT")
- @PostMapping("confirmAndSubmitStationInfoHH")
- @PostMapping("confirmAndSubmitStationInfoGov")
- @PostMapping("confirmAndSubmitStationInfoCorp")
- @PostMapping("confirmAndSubmitStationInfoHrflcEpc")
- @PostMapping("preRegisterStation")
- @PostMapping("/registYuexiuStation.do")
- @PostMapping("/registerYueXiuStationForPub.do")
- @PostMapping("/confirmAndSubmitYueXiuStationInfoPublic.do")
- @PostMapping("/updateYueXiuStationInfoPublic.do")
- @PostMapping("/registerYuexiuStationCache.do")
- @PostMapping("/registerDhStationCache.do")
- @PostMapping("/registerGfStationCache.do")
- //    @GetMapping("/findTemporaryStorage")
- @PostMapping("/deleteTemporaryStorage")
- @PostMapping("/temporaryStorage")
- @PostMapping("/temporaryStorageDh")
- @PostMapping("/temporaryStorageGf")
- @GetMapping("/findTemporaryStorage")
- @GetMapping("/getDhTemporaryDetail")
- @GetMapping("/getGfTemporaryDetail")
- @PostMapping("/registCnnChnStation.do")
- @PostMapping("/registerDhStation.do")
- @PostMapping("/registerGfStation.do")
- @PostMapping("/registChdEpcStation.do")
- @PostMapping("/registerCnnChnStationCache.do")
- @PostMapping("/registerChdStationCache.do")
- @PostMapping("/updateCnChnStation.do")
- @PostMapping("/updateDhStation.do")
- @PostMapping("/updateGfStation.do")
- @PostMapping("/updateChdStation.do")
- @PostMapping("/updateYuexiuStation.do")
- @GetMapping("/getCompleteConfirmInfo.do")
- @PostMapping("/completeConfirm.do")
- @PostMapping("/completeConfirmCache.do")
- @PostMapping("/editCompleteConfirm.do")
- @PostMapping("/editCompleteConfirmImg.do")
- @GetMapping("/getAcceptanceInfo.do")
- @PostMapping("/acceptanceApply.do")
- @PostMapping("/acceptanceApplyCache.do")
- @PostMapping("/editAcceptanceApply.do")
- @PostMapping("/editConfirmImg.do")

## LightInveterController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightInveterController.java`
- @RequestMapping("/light/inveter/")
- @GetMapping("m1")
- @GetMapping("m2")
- @GetMapping("/lightInveterList.do")
- @GetMapping("/exportInveter.do")
- @GetMapping("/inveterDetail.do")
- @GetMapping("/dayChart.do")
- @GetMapping("/monthChart.do")
- @GetMapping("/yearChart.do")
- @GetMapping("/totalChart.do")
- @GetMapping("/dayChartPac.do")

## LightVersionInformationController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightVersionInformationController.java`
- @RequestMapping("/light/lightVersionInformation/")
- @GetMapping("list.do")

## LightOpAuthorityZoneController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightOpAuthorityZoneController.java`
- @RequestMapping("/light/lightOpAuthorityZone/")
- @GetMapping("list.do")
- @PostMapping("add.do")
- @PostMapping("update.do")
- @PostMapping("delete.do")

## LightUnionpayNotifyController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightUnionpayNotifyController.java`
- @RequestMapping("/unionpay/notify/")
- @PostMapping("user/sign")
- @PostMapping("pay")

## LightDepositController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightDepositController.java`
- @RequestMapping("/light/deposit/")
- @GetMapping("/getDeposit.do")
- @GetMapping("find.do")
- @PostMapping("addDeposit.do")
- @PostMapping("modifyDeposit.do")
- @GetMapping("queryLimit.do")

## LightTransferOrderController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightTransferOrderController.java`
- @RequestMapping("/light/transfer/")
- @GetMapping("/out/list.do")
- @GetMapping("/in/list.do")
- @PostMapping("outTransfer.do")
- @PostMapping("internalTransfer.do")
- @PostMapping("signTransfer.do")
- @PostMapping("updateSignImage.do")
- @PostMapping("/previewContract.do")
- @PostMapping("/signContract.do")
- @GetMapping("/internalTransferList.do")
- @GetMapping("/internalTransferListExport.do")
- @GetMapping("getById.do")

## LightStationOwnerController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightStationOwnerController.java`
- @RequestMapping("/light/owner/")
- @GetMapping("find.do")
- @PostMapping("add.do")
- @PostMapping("addBusinessBody.do")
- @PostMapping("edit.do")
- @PostMapping("delete.do")
- @GetMapping("/getYuexiuAccount.do")
- @GetMapping("export.do")
- @GetMapping("/stationOwnerDetail.do")
- @PostMapping("contractTextStatus.do")
- @GetMapping("/contractSignUrl.do")
- @GetMapping("/findContract.do")
- @GetMapping("/getDetails")
- @PostMapping("cresateOrUpdateIdCardOCR")
- @GetMapping("oCRTrigger")
- @GetMapping("getOCRRecordByIdCard")
- @GetMapping("getOCRRecordByBankNo")

## StationChangeOperationController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/StationChangeOperationController.java`
- @RequestMapping("/stationChangeOperation")
- @GetMapping("doList.do")
- @PostMapping("add.do")
- @PostMapping("detail.do")
- @PostMapping("edit.do")
- @PostMapping("revoke.do")
- @PostMapping("deleteApply.do")
- @GetMapping("getInverterSnListByStation.do")
- @GetMapping("getInverterDetailBySn.do")
- @GetMapping("/queryStationBase.do")
- @GetMapping("/getStationPlanConfigByStationCode.do")

## LightEpcStationController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightEpcStationController.java`
- @RequestMapping("/light/epcStation/")
- @PostMapping("/registEpcStation.do")
- @PostMapping("/registEpcStationCache.do")
- @GetMapping("/findList.do")
- @PostMapping("/completeConfirmCache.do")
- @PostMapping("/completeConfirm.do")
- @PostMapping("/submitGridDataCache.do")
- @PostMapping("/submitGridData.do")
- @PostMapping("/createOrder.do")
- @PostMapping("/deleteStation.do")
- @GetMapping("/findDefaultBrandList.do")

## LightSpSubOperationDataController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightSpSubOperationDataController.java`
- @RequestMapping("/light/lightSubOperationData/")
- @GetMapping("list.do")
- @GetMapping("export.do")

## LightPurchaseOrderController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightPurchaseOrderController.java`
- @RequestMapping("/light/purchase/")
- @GetMapping("inboundManagementReminders.do")
- @GetMapping("find.do")
- @GetMapping("getById.do")
- @GetMapping("export.do")
- @GetMapping("thirdParty/find.do")
- @GetMapping("thirdParty/export.do")
- @GetMapping("thirdParty/out/find.do")
- @PostMapping("inStore.do")
- @PostMapping("inStoreBatch.do")
- @PostMapping("thirdParty/inStore.do")
- @PostMapping("thirdParty/inStoreBatch.do")
- @PostMapping("updateSign.do")
- @GetMapping("/findAuxiliaryPurchaseOrderPage")
- @GetMapping("/findAuxiliaryPurchaseOrderDetail")
- @PostMapping("/auxiliaryPurchaseOrderDeliver")
- @PostMapping("/auxiliaryPurchaseOrderDirectDeliver")
- @PostMapping("thirdParty/deliver.do")
- @PostMapping("/exportPurchaseOrder.do")
- @PostMapping("/previewContract.do")
- @PostMapping("/signContract.do")
- @PostMapping("/saveReciveOrder.do")

## LightStationAppController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightStationAppController.java`
- @RequestMapping("/app/lightStation")
- @PostMapping("preRegisterStation")
- @PostMapping("/owner/add.do")
- @PostMapping("/dispatch.do")
- @GetMapping("/owner/find.do")
- @GetMapping("/owner/export.do")
- @PostMapping("/dispatch/change.do")
- @PostMapping("/temporaryStorage")
- @PostMapping("/deleteTemporaryStorage")
- @PostMapping("/owner/delete.do")
- @GetMapping("/owner/detail.do")
- @GetMapping("/image")

## LightInstantGridRewardControllerForMerchant
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightInstantGridRewardControllerForMerchant.java`
- @RequestMapping("/LightInstantGridReward")
- @GetMapping("list.do")
- @GetMapping("queryLightInstantGridRewardDetail")
- @GetMapping("export.do")

## CmChangeController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/CmChangeController.java`
- @RequestMapping("/light/cmChange/")
- @GetMapping("list.do")
- @GetMapping("statusCount.do")
- @GetMapping("preInfo1.do")
- @GetMapping("preInfo2.do")
- @GetMapping("detail.do")
- @PostMapping("/create.do")
- @PostMapping("/update.do")
- @PostMapping("/cache.do")
- @PostMapping("/getCache.do")

## LightSpQuotaController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightSpQuotaController.java`
- @RequestMapping("/light/Quota/")
- @GetMapping("list.do")
- @GetMapping("total.do")
- @GetMapping("queryQuotaDetail")

## LightSapPurchaseRecordController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/light/LightSapPurchaseRecordController.java`
- @RequestMapping("/light/lightSapPurchaseRecord/")
- @GetMapping("list.do")
- @GetMapping("export.do")

## LightSpecialOutboundApplyController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/wms/LightSpecialOutboundApplyController.java`
- @RequestMapping("/outboundApply/")
- @GetMapping("list")
- @PostMapping("addApply.do")
- @PostMapping("editApply.do")
- @GetMapping("/detail.do")
- @PostMapping("uploadCompleteInfo.do")
- @PostMapping("editCompleteInfo.do")

## ImageRecognizeController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/baidu/ImageRecognizeController.java`
- @RequestMapping("/light/imageRecognize")
- @PostMapping("/imageNum.do")

## HroisController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/hrois/HroisController.java`
- @RequestMapping("/hrois")
- @PostMapping("order.do")
- @PostMapping("status.do")
- @PostMapping("orderModify.do")

## TransitStoreController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/transit/TransitStoreController.java`
- @RequestMapping(value = "/light/transit/", produces = {"application/xml;"})
- @PostMapping("/post.do")
- @PostMapping("/zeroCarbon/post.do")
- @PostMapping("/sku.do")
- @PostMapping("/zeroCarbon/sku.do")
- @PostMapping("/post1.do")

## GhAccountOpenCallBackController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/gh/GhAccountOpenCallBackController.java`
- //@RequestMapping("/gh/account")
- //    @RequestMapping(value = "/openCallback")
- //    @RequestMapping(value = "/withdrawCallback")

## GhSecondClassAccountController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/gh/GhSecondClassAccountController.java`
- //@RequestMapping("/gh/account/")
- //    @GetMapping("list")
- //    @GetMapping("doExport.do")
- //    @PostMapping("unbinding")

## GtmsNotifyController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/gtms/GtmsNotifyController.java`
- @RequestMapping("/gtms")
- @PostMapping("notify.do")

## ChuiYangController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/chuiyang/ChuiYangController.java`
- @RequestMapping("/chuiyang/")
- @GetMapping("getStationBaseInfo.do")
- @PostMapping("addImageData.do")
- @PostMapping("addInvestigateData.do")

## YzzOptItemController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/yzz/YzzOptItemController.java`
- @RequestMapping("/yzzoptitem")
- @GetMapping("/getYzzOptItem.do")
- @GetMapping("/getItemByItemId.do")
- @PostMapping("/addYzzOptItem.do")
- @PostMapping("/delYzzOptItem.do")

## YzzGuideController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/yzz/YzzGuideController.java`
- @RequestMapping("/yzzguide")
- @GetMapping("/listYzzGuide.do")
- @PostMapping("/addYzzGuide.do")
- @PostMapping("/enabled.do")
- @PostMapping("/disabled.do")

## YzzUserWalletController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/yzz/YzzUserWalletController.java`
- @RequestMapping("/yzzUserWallet")
- @GetMapping("/getCompanyName.do")
- @PostMapping("/rechargeUserWallet.do")
- @GetMapping("/getWalletAmount.do")
- @GetMapping("/findWalletLogList.do")

## YzzCategoryItemController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/yzz/YzzCategoryItemController.java`
- @RequestMapping("/yzzcategoryitem")
- @GetMapping("/listYzzCategoryItem.do")
- @PostMapping("/addYzzCategoryItem.do")
- @PostMapping("/enabled.do")
- @PostMapping("/disabled.do")
- @GetMapping("/getById.do")
- @PostMapping("/editYzzCategoryItem.do")

## YzzCategoryController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/yzz/YzzCategoryController.java`
- @RequestMapping("/yzzcategory")
- @GetMapping("/listYzzCategory.do")
- @PostMapping("/addYzzCategory.do")
- @PostMapping("/enabled.do")
- @PostMapping("/disabled.do")
- @GetMapping("/getById.do")
- @PostMapping("/editYzzCategory.do")

## YzzShopController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/yzz/YzzShopController.java`
- @RequestMapping("/yzzshop")
- @GetMapping("/getYzzShop.do")
- @PostMapping("/setYzzShop.do")

## DhBusinessOpportunityController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/dh/DhBusinessOpportunityController.java`
- @RequestMapping("dhBusinessOpportunity")
- @GetMapping("queryTableList")
- @GetMapping("selectOption")
- @PostMapping("add")
- @PostMapping("edit")
- @GetMapping("getDetailById")
- @GetMapping("delete")
- @GetMapping("getByInputPieceId")

## DhLightStationController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/dh/DhLightStationController.java`
- @RequestMapping("dhLightStation")
- @GetMapping("getByStationCode")

## SapPurchaseController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/settle/SapPurchaseController.java`
- @RequestMapping("/settle/sapPurchase/")
- @GetMapping("sapPurchaseList.do")
- @GetMapping("sapPurchaseListExcel.do")

## PurchaseApplySettleController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/settle/PurchaseApplySettleController.java`
- @RequestMapping("/settle/purchaseApplySettle/")
- @GetMapping("purchaseApplySettle.do")
- @GetMapping("purchaseApplySettleDetailView.do")

## ShopSettlementController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/settle/ShopSettlementController.java`
- @RequestMapping("/settle/shopSettlement/")
- @GetMapping("shopBindInfo.do")
- @GetMapping("shopCheckBillList.do")
- @GetMapping("shopCheckBillListExcel.do")
- @GetMapping("shopSettlementBillList.do")
- @GetMapping("shopSettlementBillListExcel.do")

## BarCodeApplyController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/bar/BarCodeApplyController.java`
- @RequestMapping("/barCode/apply")
- @GetMapping("list.do")
- @GetMapping("doExport.do")

## BarCodeDetailController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/bar/BarCodeDetailController.java`
- @RequestMapping("/barCode/detail")
- @GetMapping("list.do")
- @GetMapping("doExport.do")

## GsyStationInfoController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/gsyapp/GsyStationInfoController.java`
- @RequestMapping("/gsyapp/station/")
- @GetMapping("getStationList.do")
- @GetMapping("getStationInfo.do")
- @PostMapping("updateStationImg.do")
- @GetMapping("getDeviceInfo.do")

## GsyStationPowerController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/gsyapp/GsyStationPowerController.java`
- @RequestMapping("/gsyapp/power/")
- @GetMapping("getStationPowerInfo.do")
- @GetMapping("getPowerCount.do")
- @GetMapping("getElecCount.do")
- @GetMapping("getAllStationElecCount.do")

## GsyAppMemberController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/gsyapp/GsyAppMemberController.java`
- @RequestMapping("/gsyapp/member/")
- @PostMapping("sendRegisterSms.do")
- @PostMapping("register.do")
- @GetMapping("/sendUpdatePasswordSms.do")
- @PostMapping("/updatePassword.do")
- @GetMapping("getRole.do")

## HroisOrderSupplierController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/haiwai/HroisOrderSupplierController.java`
- @RequestMapping("/haiwai/order/")
- @GetMapping("statusCount.do")
- @GetMapping("list.do")
- @GetMapping("export.do")
- @PostMapping("make.do")
- @PostMapping("deliver.do")
- @PostMapping("importDeliver.do")
- @GetMapping("deliverTemplate.do")

## HroisOrderBoxController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/haiwai/HroisOrderBoxController.java`
- @RequestMapping("/haiwai/order/")
- @GetMapping("query.do")
- @PostMapping("saveBox.do")
- @PostMapping("saveQualityInspectionReport.do")
- @PostMapping("saveLogisticsHandoverSheet.do")

## Kuaidi100Controller
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/kuaidi/Kuaidi100Controller.java`
- @RequestMapping("/kuaidi100")
- @PostMapping("/callback")

## ChargeSaleCustomerController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/finance/ChargeSaleCustomerController.java`
- @RequestMapping("/chargeSaleCustomer/")
- @GetMapping("queryChargeSaleCustomerInfo.do")

## FinancialSolutionsController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/finance/FinancialSolutionsController.java`
- @RequestMapping("/financialSolutions/")
- @GetMapping("queryFinancialSolutions.do")
- @GetMapping("queryFinancialSolutionsDetails.do")

## WorkbenchFinancialController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/finance/WorkbenchFinancialController.java`
- @RequestMapping("/workbenchFinancial/")
- @GetMapping("queryWorkbenchFinanceInfo.do")

## CustomerAnalyzeController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/finance/CustomerAnalyzeController.java`
- @RequestMapping("/customerAnalyze/")
- @GetMapping("queryCustomerAnalyzeInfo.do")
- @GetMapping("queryReceivableCustomerInfo.do")

## InvoiceFinanceController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/finance/InvoiceFinanceController.java`
- @RequestMapping("/finance/invoice/")
- @GetMapping("invoiceFinanceList.do")
- @GetMapping("sumInvoiceAmount.do")
- @PostMapping("invoiceOperation.do")
- @GetMapping("/getCustomerInfo.do")

## IncomeInventoryController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/finance/IncomeInventoryController.java`
- @RequestMapping("/finance/incomeInventory/")
- @GetMapping("incomeInventoryList.do")
- @GetMapping("sumIncomeAmount.do")
- @GetMapping("/orderItemDetail.do")
- @GetMapping("/getCustomerInfo.do")

## HrflcAuditOwnerController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/hrflc/HrflcAuditOwnerController.java`
- @RequestMapping("/hrflc/owner/")
- @GetMapping("find.do")
- @PostMapping("add.do")
- @PostMapping("edit.do")
- @GetMapping("getDetails.do")
- @GetMapping("getDetailsRe.do")
- @GetMapping("/getHrflcEpcPersonalProjectCompanyInfo.do")

## LightUnfinishedStationWarnController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/warn/LightUnfinishedStationWarnController.java`
- @RequestMapping("/station/warn")
- @GetMapping("/doList")
- @GetMapping("doExport.do")

## LightStationBankCardChangeController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperationbank/LightStationBankCardChangeController.java`
- @RequestMapping("/lightOperationBank/")
- @GetMapping("list.do")
- @PostMapping("addOrUpdate.do")
- @PostMapping("getBankInfo.do")
- @PostMapping("cancel.do")

## PublicLiabilityInsuranceController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/PublicLiabilityInsuranceController.java`
- @RequestMapping("/publicLiabilityInsurance")
- @GetMapping("findByPage")
- @PostMapping("add")
- @PostMapping("update")
- @PostMapping("delete")
- @GetMapping("doExport.do")

## InvoiceCheckOperationController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/InvoiceCheckOperationController.java`
- @RequestMapping("/operation/invoiceCheck/")
- @GetMapping("/list.do")
- @GetMapping("/queryInvoiceForSettle.do")
- @PostMapping("/getInvoiceInfo.do")
- @PostMapping("/addInvoices.do")
- @PostMapping("/updateInvoices.do")
- @PostMapping("/deleteInvoice.do")
- @PostMapping("/manualAddInvoiceCheck.do")
- @PostMapping("/manualAddInvoice.do")

## LightSpOpsNegativeExcitationController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/LightSpOpsNegativeExcitationController.java`
- @RequestMapping("/lightSpOpsNegativeExcitation")
- @GetMapping("findByPage")
- @GetMapping("/doExport")

## SocializationStationController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/SocializationStationController.java`
- @RequestMapping("/socializationStation")
- @GetMapping("/find.do")
- @GetMapping("findDetail.do")

## LightSapPurchaseRecordOperationController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/LightSapPurchaseRecordOperationController.java`
- @RequestMapping("/operation/lightSapPurchaseRecord/")
- @GetMapping("list.do")

## AllRisksInsuranceController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/AllRisksInsuranceController.java`
- @RequestMapping("/allRisksInsurance")
- @GetMapping("findByPage")
- @GetMapping("findSkuOrSn")
- @PostMapping("add")
- @PostMapping("update")
- @PostMapping("delete")
- @GetMapping("doExport.do")

## LightStationPolicyNoController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/LightStationPolicyNoController.java`
- @RequestMapping("/lightStationPolicyNo")
- @GetMapping("findByPage")
- @GetMapping("findByStationCode")

## LightOperationCertificationController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/LightOperationCertificationController.java`
- @RequestMapping("/lightOperationCertification/")
- @PostMapping("/findData")
- @PostMapping("/addData")
- @PostMapping("/uploadData")

## LightSettleBillsController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/LightSettleBillsController.java`
- @RequestMapping("/settle/bille")
- @GetMapping("list.do")
- @GetMapping("doExport.do")

## LightSpOpsPositiveIacController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/LightSpOpsPositiveIacController.java`
- @RequestMapping("/iac/positive")
- @GetMapping("findByPage")
- @GetMapping("/doExport")

## DatabaseManagementOpController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/DatabaseManagementOpController.java`
- @RequestMapping("/light/databaseManagementOp/")
- @GetMapping("list.do")

## LightSpOpsNegativeIacController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/LightSpOpsNegativeIacController.java`
- @RequestMapping("/iac/nagative")
- @GetMapping("findByPage")
- @GetMapping("/doExport")

## LightOpStaffController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/LightOpStaffController.java`
- @RequestMapping("/light/staff/")
- @GetMapping("find.do")
- @GetMapping("get.do")
- @PostMapping("/add.do")
- @PostMapping("/editEmployeeStatus.do")
- @PostMapping("/uploadData.do")
- @GetMapping("getList.do")
- @GetMapping("checkOverdue.do")
- @GetMapping("getAuth.do")
- @GetMapping("newStationOp")
- @GetMapping("addNewWarrantyRole")
- @GetMapping("completeOperationCertification")
- @GetMapping("completeOperationStaff")

## LightSpOpsPositiveController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/LightSpOpsPositiveController.java`
- @RequestMapping("/lightSpOpsPositive/")
- @GetMapping("findByPage")
- @GetMapping("/doExport")

## LightWorkOrderController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/LightWorkOrderController.java`
- @RequestMapping("/work/order/")
- @GetMapping("list.do")
- @GetMapping("detail.do")
- @PostMapping("complete.do")
- @PostMapping("dispatcher.do")
- @GetMapping("doExport.do")
- @PostMapping("addProcess.do")
- @PostMapping("createAppeal.do")

## PurchaseApplySettleNoPaperOperationController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/PurchaseApplySettleNoPaperOperationController.java`
- @RequestMapping("/operation/purchaseApplySettleNoPaper/")
- @GetMapping("/list.do")
- @GetMapping("/addPrepareInfo.do")
- @GetMapping("/queryPurchaseForSettle.do")
- @PostMapping("/add.do")
- @PostMapping("/update.do")
- @PostMapping("/delete.do")
- @GetMapping("/detail.do")
- @PostMapping("/relateInvoice.do")
- @GetMapping("/getConfirmBeforeBillUrl.do")
- @GetMapping("/getConfirmUrl.do")
- @PostMapping("export.do")

## LightFaultDictionaryController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/LightFaultDictionaryController.java`
- @RequestMapping("/lightFaultDictionary/")
- @GetMapping("/findFirst.do")
- @GetMapping("/findSecond.do")
- @GetMapping("/findThird.do")

## LightSpOpsPositiveExcitationController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/LightSpOpsPositiveExcitationController.java`
- @RequestMapping("/positive")
- @GetMapping("findByPage")
- @GetMapping("/doExport")
- @PostMapping("update")
- @PostMapping("change")
- @GetMapping("/downTemplate")
- @PostMapping("importData.do")
- @PostMapping("del")
- @PostMapping("importDataForXiaoXiang.do")

## LightStationInverterChangeController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/LightStationInverterChangeController.java`
- @RequestMapping("/lightStationInverterChange")
- @GetMapping("list.do")
- @PostMapping("createData")
- @PostMapping("stop")
- @PostMapping("findByStationCode")

## LightOpStationController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/LightOpStationController.java`
- @RequestMapping("/lightOpStation")
- @GetMapping("list.do")

## LightOpInveterController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/LightOpInveterController.java`
- @RequestMapping("/lightOperationProvider/")
- @GetMapping("/lightInveterList.do")
- @GetMapping("/inveterDetail.do")
- @GetMapping("/historyWeather.do")
- @GetMapping("/weatherByCoordinates.do")
- @GetMapping("/exportInveter.do")

## OcrApiController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/OcrApiController.java`
- @RequestMapping("/ocrApi")
- @PostMapping("/inverterSn/ocr")
- @PostMapping("/bankImg/ocr")

## LightOperationBiddingRegistrationController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/bidding/LightOperationBiddingRegistrationController.java`
- @RequestMapping("/light/operation/bidding/registration")
- @GetMapping("/business-opportunities")
- @GetMapping("/my-business-opportunities")
- @GetMapping("/my-business")
- @GetMapping("/all-business-opportunities")
- @GetMapping("/project/info")
- @GetMapping("/project/region-blocks")
- @PostMapping("/saveDraft")
- @PostMapping("/submit")
- @PostMapping("/update")
- @GetMapping("/get/{id}")
- @DeleteMapping("/delete/{id}")
- @PostMapping("/response/submit")
- @GetMapping("/dashboard/statistics")
- @GetMapping("/company/info")
- @GetMapping("/project/rating/table/{projectId}")
- @GetMapping("/rating/item/config-by-table/{tableId}")
- // @PostMapping("/company/saveOrUpdate")
- // @DeleteMapping("/company/delete/{id}")
- @GetMapping("/announcement/page")
- @GetMapping("/announcement/get")
- @GetMapping("/isOpMember")
- @GetMapping("/yearly-closed-rate")

## LightOperationCdWarehouseAddressController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/v2/LightOperationCdWarehouseAddressController.java`
- @RequestMapping("/light/operation/repairs/cdWarehouseAddress")
- @PostMapping("/getAllList")
- @PostMapping("/getList")
- @GetMapping("/getInfoById")
- @PostMapping("/save")
- @PostMapping("/update")
- @PostMapping("/delete")
- @PostMapping("/updateDefault")
- @GetMapping("/getCdWarehouseAndAddressByMemberID")

## LightOperationSolutionController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/v2/LightOperationSolutionController.java`
- @RequestMapping("/light/operation/solution")
- @GetMapping("/category/list")
- @GetMapping("page")
- @GetMapping("get")
- @GetMapping("list")

## LightOperationWorkOrderController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/v2/LightOperationWorkOrderController.java`
- @RequestMapping("/light/operation/workOrder")
- @GetMapping("page")
- @GetMapping("/config/list")
- @GetMapping("/handled/page")
- @GetMapping("getByOrderCode/{orderCode}")
- @PostMapping("submit")
- @PostMapping("/handle")
- @GetMapping("my-submitted")
- @GetMapping("/staffList")
- @PostMapping("/assign")
- @PostMapping("/close")
- @PostMapping("/appeal/submit")
- @GetMapping("/appeal/list")
- @GetMapping("/appeal/my-submitted")
- @GetMapping("/appeal/op")
- @GetMapping("/export")
- @PostMapping("/process-record/add")
- @GetMapping("/appeal/check")

## LightOperationChatController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/v2/LightOperationChatController.java`
- @RequestMapping("/light/operation/ai/chat")
- @PostMapping("/message")
- @PostMapping(value = "/stream", produces = MediaType.TEXT_EVENT_STREAM_VALUE)
- @GetMapping("/history")
- @PostMapping("/history/clear")
- @GetMapping("/history/page")
- @GetMapping("/question-templates")
- @PostMapping(value = "/regenerate", produces = MediaType.TEXT_EVENT_STREAM_VALUE)

## LightOperationUserController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/v2/LightOperationUserController.java`
- @RequestMapping("/light/operation/app/user")
- @PostMapping("/reg/send_register_sms")
- @PostMapping("/reg/register")
- @GetMapping("/info")

## LightOperationExamAnswerController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/v2/LightOperationExamAnswerController.java`
- @RequestMapping("/light/operation/exam/answer")
- @PostMapping("user-page")
- @GetMapping("get-exam-paper")
- @GetMapping("getOrCreate")
- @GetMapping("getDetail")
- @GetMapping("getByExamAndUser")
- @PostMapping("updateProgress")
- @PostMapping("submit")
- @GetMapping("listByExam")

## LightOperationMessageController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/v2/LightOperationMessageController.java`
- @RequestMapping("/light/operation/message")
- @GetMapping("/page")
- @GetMapping("/detail")
- @PostMapping("/mark-read")
- @PostMapping("/batch-mark-read")
- @GetMapping("/unread-count")

## LightOperationStationController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/v2/LightOperationStationController.java`
- @RequestMapping("/light/operation/station")
- @GetMapping("page")
- @GetMapping("getByStationCode")
- @PostMapping("location/update")
- @PostMapping("info/update")
- @GetMapping("inverter/list")
- @GetMapping("inverter/data")
- @GetMapping("inverter/mppt-data")
- @GetMapping("inverter/elec-data")
- @PostMapping("inverter/mppt/update")
- @GetMapping("inverter/weather-radiation-data")
- @GetMapping("station/rent/months")
- @GetMapping("station/rent/by-station-code")
- @GetMapping("/export")

## LightOperationWorkOrderAppController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/v2/LightOperationWorkOrderAppController.java`
- @RequestMapping("/light/operation/app/workOrder")
- @GetMapping("page")
- @GetMapping("/handled/page")
- @GetMapping("getByOrderCode/{orderCode}")
- @PostMapping("submit")
- @PostMapping("/handle")
- @GetMapping("my-submitted")
- @GetMapping("/staffList")
- @GetMapping("/to-handle")
- @GetMapping("/provider/count")
- @GetMapping("/staff/count")

## LightOperationStationRentController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/v2/LightOperationStationRentController.java`
- @RequestMapping("/light/operation/out/station/rent")
- @GetMapping("list-stations")
- @GetMapping("rent-months")
- @GetMapping("find-by-station")
- @GetMapping("rootFaults")
- @PostMapping("submit/work-order")
- @GetMapping("my/work-order")
- @RequestMapping(value = "uploadFile.do", method = RequestMethod.POST)

## LightOperationDictController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/v2/LightOperationDictController.java`
- @RequestMapping("/light/operation/dict")
- @GetMapping("/items/{dictCode}")
- @PostMapping("/items/batch")

## LightOperationWoPartController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/v2/LightOperationWoPartController.java`
- @RequestMapping("/light/operation/wo-part")
- @PostMapping("/save-order-wo-part-file")
- @PostMapping("/apply-part-check")
- @PostMapping("/apply-part")

## LightOperationInspectionWorkOrderController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/v2/LightOperationInspectionWorkOrderController.java`
- @RequestMapping("/light/operation/inspection/work-order")
- @GetMapping("page")
- @GetMapping("get")
- @GetMapping("list")
- @GetMapping("to-handle")
- @GetMapping("my-handled")
- @PostMapping("handle")
- @PostMapping("assign")
- @PostMapping("batch-assign")
- @GetMapping("statistics")
- @GetMapping("statistics/staff")
- @GetMapping("statistics/plan")
- @GetMapping("statistics/total")
- @GetMapping("plan/list")
- @GetMapping("/export")

## LightOperationPracticeController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/v2/LightOperationPracticeController.java`
- @RequestMapping("/light/operation/exam/practice")
- @GetMapping("/question/bank/list")
- @PostMapping("/generate")
- @GetMapping("/list")
- @GetMapping("/detail")
- @PostMapping("/updateProgress")
- @PostMapping("/complete")
- @PostMapping("/delete")
- @GetMapping("/info")

## LightOperationFaultController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/v2/LightOperationFaultController.java`
- @RequestMapping("/light/operation/fault")
- @GetMapping("rootFaults")
- @GetMapping("children")
- @GetMapping("solutions")
- @GetMapping("solution-check-items")

## LightOperationReportCenterController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/v2/LightOperationReportCenterController.java`
- @RequestMapping("/light/operation/report-center")
- @GetMapping("/my-config-list")
- @PostMapping("/get-by-config")
- @GetMapping("/config/details")

## LightOperationInspectionWorkOrderAppController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/v2/LightOperationInspectionWorkOrderAppController.java`
- @RequestMapping("/light/operation/app/inspection/work-order")
- @GetMapping("provider/count")
- @GetMapping("staff/count")

## LightOperationProviderController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/lightoperation/v2/LightOperationProviderController.java`
- @RequestMapping("/lightOperationProvider/")
- @PostMapping("/apply.do")
- @PostMapping("/registSp.do")
- @PostMapping("/findId.do")
- @PostMapping("/contractStatus")
- @PostMapping("/isRegister")
- @PostMapping("/hasWonBiddingByMemberId.do")
- @PostMapping("/getApplyProviderRequest.do")
- @PostMapping("/updateStatus.do")

## LightAnnualScalePolicyController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/policy/LightAnnualScalePolicyController.java`
- @RequestMapping("/annualScalePolicy")
- @GetMapping("getCurrentPolicy.do")
- @GetMapping("getMySettleInfo.do")
- @GetMapping("/findByExecuteYear.do")

## MemberVatInvoiceQualificationController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/member/MemberVatInvoiceQualificationController.java`
- @RequestMapping("/member/vatInvoiceQualification")
- @GetMapping("/get.do")
- @PostMapping("/save.do")
- @PostMapping("/delete.do")
- @GetMapping("findByMember.do")
- @PostMapping("findMdmCustomer.do")

## MemberController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/member/MemberController.java`
- @RequestMapping("/member/")
- @PostMapping("/changePassword.do")
- @GetMapping("/getMember.do")

## MemberAddressController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/member/MemberAddressController.java`
- @RequestMapping("/member/address")
- @GetMapping("/get.do")
- @GetMapping("/mark_as_default.do")
- @GetMapping("/list.do")
- @PostMapping("/saveAddress.do")
- @GetMapping("/regionList.do")
- @GetMapping("/findAllProvince.do")

## FindPasswordController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/member/FindPasswordController.java`
- @RequestMapping("/member/find_password")
- @PostMapping("/change.do")
- @GetMapping("/send_sms.do")

## MemberOperatorController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/member/MemberOperatorController.java`
- @RequestMapping("/member/operator")
- @GetMapping("operatorShopRelationList.do")

## YantuAutomaticallyDesignTemporaryStorageController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/yantu/YantuAutomaticallyDesignTemporaryStorageController.java`
- @RequestMapping("/yantuAutomaticallyDesignTemporaryStorage")
- @GetMapping("findByPage")
- @PostMapping("saveData")
- @PostMapping("bindProject")
- @PostMapping("delete")
- @PostMapping("detail")
- @GetMapping("detailForYantu")
- @PostMapping("getElectricityDetail")
- @PostMapping("updateElectricityPrice")

## DictTypeController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/yantu/DictTypeController.java`
- @RequestMapping("/yantuDict")
- @GetMapping("/selectDictValueByCode.do")

## YanTuController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/yantu/YanTuController.java`
- @RequestMapping("/yantu")
- @PostMapping("statinInfo.do")
- @PostMapping("statinInfos.do")
- @PostMapping("status.do")
- @GetMapping("/stationList.do")
- @GetMapping("/houseHoldStationList")
- @GetMapping("/zeroCarbonStationList")
- @GetMapping("/houseHoldAerialImageList")
- @GetMapping("/zeroCarbonAerialImageList")
- @PostMapping("/cadFileToOss.do")
- @GetMapping("/getInverterList.do")

## SpOldbackListsController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/repairs/SpOldbackListsController.java`
- @RequestMapping("/repairs/spOldbackLists")
- @PostMapping("/getPage")
- @PostMapping("/getQsPage")
- @GetMapping("/getInfoById")
- @GetMapping("/confirmReturn")
- @PostMapping("/update")
- @PostMapping("/updateTransport")
- @PostMapping("/coreReceipt")
- @PostMapping("/rejectOldback")
- @GetMapping("/export")
- @GetMapping("/coreReceiptExport")
- @GetMapping("/dzjOrderExport")
- @PostMapping("/addDzj")
- @PostMapping("/delDzj")
- @PostMapping("/submitDzj")

## SpOrderController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/repairs/SpOrderController.java`
- @RequestMapping("/repairs/spOrder")
- @PostMapping("/getPage")
- @GetMapping("/export")
- @GetMapping("/getUpdateInfoById")
- @GetMapping("/getInfoById")
- @PostMapping("/save")
- @GetMapping("/downTemplate")
- @RequestMapping(value = "/importData", method = RequestMethod.POST)
- @PostMapping("/update")
- @PostMapping("/delete")
- @PostMapping("/submitOrder")
- @PostMapping("/serviceCancelOrder")
- @PostMapping("/orderExecutionPage")
- @GetMapping("/orderExecution/export")
- @PostMapping("/singleCancel")
- @GetMapping("/ordeMatching")
- @PostMapping("/ordeMatchingJob")
- @PostMapping("/getServicePITPage")
- @GetMapping("/getServicePITPage/export")
- @PostMapping("/addServicePIT")
- @PostMapping("/updateServicePIT")
- @PostMapping("/delServicePIT")
- @PostMapping("/getInfoServicePIT")
- @PostMapping("/submitServicePIT")
- @PostMapping("/approvalServicePIT")

## SpAdvancePaymentController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/repairs/SpAdvancePaymentController.java`
- @RequestMapping("/repairs/spAdvancePayment")
- @PostMapping("/getPage")
- @PostMapping("/addSpAdvancePayment")
- @PostMapping("/updateSpAdvancePayment")
- @PostMapping("/delSpAdvancePayment")
- @PostMapping("/submitSpAdvancePayment")
- @PostMapping("/receivePayStatus")
- @PostMapping("/export")

## SpOrderBackController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/repairs/SpOrderBackController.java`
- @RequestMapping("/repairs/spOrderBack")
- @PostMapping("/getPage")
- @GetMapping("/getPage/export")
- @GetMapping("/getInfoById")
- @PostMapping("/update")
- @PostMapping("/submitOrder")
- @PostMapping("/submitOrderPay")
- @PostMapping("/cbsApprovalOrder")
- @PostMapping("/ywSave")
- @PostMapping("/ywUpdate")

## SpAccountsPayableController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/repairs/SpAccountsPayableController.java`
- @RequestMapping("/repairs/spAccountsPayable")
- @GetMapping("findByPage")
- @GetMapping("getSignUrl.do")
- @GetMapping("getPdfUrl.do")
- @GetMapping("findDetail.do")

## SpExpressCompanyController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/repairs/SpExpressCompanyController.java`
- @RequestMapping("/repairs/spExpressCompany")
- @PostMapping("/getPage")
- @PostMapping("/list")

## SpOldbackListsDetailController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/repairs/SpOldbackListsDetailController.java`
- @RequestMapping("/repairs/spOldbackListsDetail")
- @PostMapping("/getProviderPage")
- @PostMapping("/getSupplierPage")
- @GetMapping("/getSupplierPage/export")
- @PostMapping("/providerAppeal")
- @PostMapping("/judgeResponsibilitySubmit")
- @PostMapping("/providerAdmittingResponsibility")
- @PostMapping("/judgeResponsibilityInfo")

## WoPartController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/repairs/WoPartController.java`
- @RequestMapping("/repairs/woPart")
- @PostMapping("/getPage")
- @PostMapping("/getInfo")
- @PostMapping("/applyPartCheck")
- @PostMapping("/applyPart")
- @PostMapping("/sparePartsRegistrationCheck")
- @PostMapping("/sparePartsRegistration")
- @PostMapping("/sparePartsRegistrationSubmit")
- @PostMapping("/orderWoPartPage")
- @PostMapping("/orderWoPartPageAndFile")
- @PostMapping("/saveOrderWoPartFile")
- @GetMapping("/getLightWorkOrderBySn")
- @PostMapping("/getbatchNumByNo")

## SpPurchaseController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/repairs/SpPurchaseController.java`
- @RequestMapping("/repairs/spPurchase")
- @PostMapping("/getPage")
- @PostMapping("/addSpPurchase")
- @PostMapping("/submit")
- @PostMapping("/updateSpPurchase")
- @PostMapping("/getInfo")
- @PostMapping("/delete")
- @GetMapping("/export")

## CdWarehouseAddressController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/repairs/CdWarehouseAddressController.java`
- @RequestMapping("/repairs/cdWarehouseAddress")
- @PostMapping("/getAllList")
- @PostMapping("/getList")
- @GetMapping("/getInfoById")
- @PostMapping("/save")
- @PostMapping("/update")
- @PostMapping("/delete")
- @PostMapping("/updateDefault")
- @GetMapping("/getCdWarehouseAndAddressByMemberID")

## SpOrderBorrowController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/repairs/SpOrderBorrowController.java`
- @RequestMapping("/repairs/spOrderBorrow")
- @PostMapping("/getPage")
- @PostMapping("/getPageSupplier")
- @GetMapping("/getInfoById")
- @PostMapping("/save")
- @PostMapping("/update")
- @PostMapping("/delete")
- @PostMapping("/submitOrder")
- @PostMapping("/findProviderList")
- @PostMapping("/ywsApproval")
- @PostMapping("/gysApproval")
- @GetMapping("/orderBorrow/export")
- @GetMapping("/orderBorrow/supplierExport")
- @PostMapping("/findLinghtModelSn")
- @PostMapping("/cancel")

## SpAdvanceClearController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/repairs/SpAdvanceClearController.java`
- @RequestMapping("/repairs/spAdvanceClear")
- @PostMapping("/getPage")
- @GetMapping("/getInfoById")
- @GetMapping("/getInfoByOrderNo")
- @PostMapping("/save")
- @PostMapping("/update")
- @GetMapping("/submitOrder")
- @GetMapping("/delete")
- @PostMapping("/centerApproval")
- @PostMapping("/businessDepartmentApproval")
- @PostMapping("/financeApproval")
- @GetMapping("/export")

## SpAccountsReceivableController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/repairs/SpAccountsReceivableController.java`
- @RequestMapping("/repairs/spAccountsReceivable")
- @GetMapping("findByPage")
- @GetMapping("getSignUrl.do")
- @GetMapping("getPdfUrl.do")
- @GetMapping("findDetail.do")

## StockAdjustmentController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/repairs/StockAdjustmentController.java`
- @RequestMapping("/repairs/stockAdjustment")
- @PostMapping("/getPage")
- @GetMapping("/getPage/export")
- @PostMapping("/addStockAdjustment")
- @PostMapping("/delStockAdjustment")
- @PostMapping("/submitStockAdjustment")
- @PostMapping("/updateStockAdjustment")
- @PostMapping("/getInfo")

## SpForegiftController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/repairs/SpForegiftController.java`
- @RequestMapping("/repairs/spForegift")
- @PostMapping("/getPage")
- @GetMapping("/export")

## SpTranSnDetailController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/repairs/SpTranSnDetailController.java`
- @RequestMapping("/repairs/spTranSnDetail")
- @PostMapping("/getPage")

## SpTranSnDetailShController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/repairs/SpTranSnDetailShController.java`
- @RequestMapping("/repairs/spTranSnDetailSh")
- @PostMapping("/getPage")
- @PostMapping("/export")
- @PostMapping("/approve")
- @PostMapping("/update")
- @PostMapping("/revokeAppeal")

## SpTranSnController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/repairs/SpTranSnController.java`
- @RequestMapping("/repairs/spTranSn")
- @PostMapping("/getPage")
- @PostMapping("/queryPageTranSnIn")
- @GetMapping("/queryPageTranSnIn/export")
- @PostMapping("/getNewAndOldPartsPage")
- @PostMapping("/update")
- @PostMapping("/getInfo")
- @PostMapping("/closeTranSnIn")
- @PostMapping("/closeTranSnOut")
- @PostMapping("/newAndOldPartsClose")
- @GetMapping("/newAndOldPartsCreate")
- @PostMapping("/updateButchNum")
- @PostMapping("/borrowOrderInTranSn")

## CdDictDateController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/repairs/CdDictDateController.java`
- @RequestMapping("/repairs/cdDictData")
- @PostMapping("/getPage")
- @PostMapping("/getList")
- @GetMapping("/getInfoById")
- @PostMapping("/save")
- @PostMapping("/update")
- @PostMapping("/delete")

## SpStoreageController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/repairs/SpStoreageController.java`
- @RequestMapping("/repairs/spStoreage")
- @PostMapping("/getPage")
- @PostMapping("/getInfoById")
- @GetMapping("/export")
- @PostMapping("/getStoreage")
- @PostMapping("/getStoreageTotal")

## CdWarehouseController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/repairs/CdWarehouseController.java`
- @RequestMapping("/repairs/cdWarehouse")
- @PostMapping("/list")
- @GetMapping("/getCdWarehouseByMemberID")
- @PostMapping("/getPage")
- @PostMapping("/serviceSupplierSyncJob")

## CdMaterialController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/repairs/CdMaterialController.java`
- @RequestMapping("/repairs/cdMaterial")
- @PostMapping("/getPage")
- @PostMapping("/getList")

## SpInverterInfoController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/repairs/SpInverterInfoController.java`
- @RequestMapping("/repairs/spInverterInfo")
- @PostMapping("/getPage")
- @PostMapping("/getSupplierPage")
- @GetMapping("/getPage/export")
- @GetMapping("/getSupplierPage/export")
- @GetMapping("/getInfoById")
- @GetMapping("/getInfoByOrderNo")
- @PostMapping("/save")
- @PostMapping("/update")
- @GetMapping("/submitOrder")
- @GetMapping("/delete")
- @GetMapping("/withdrawn")
- @PostMapping("/supplierApproval")
- @PostMapping("/operationAndMaintenanceVendorsPost")
- @PostMapping("/supplierSign")
- @PostMapping("/supplierDelivery")
- @PostMapping("/operationAndMaintenanceVendorsSign")
- @GetMapping("/export")

## SpTranController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/repairs/SpTranController.java`
- @RequestMapping("/repairs/spTran")
- @PostMapping("/getPage")
- @GetMapping("/getPage/export")
- @PostMapping("/update")
- @PostMapping("/customsDocumentsWarehouse")
- @PostMapping("/getInfo")
- @PostMapping("/out/getPage")
- @GetMapping("/out/export")
- @GetMapping("/out/outInfoBytranId")
- @GetMapping("/out/outbound")
- @PostMapping("/updateInfo")
- @PostMapping("/updateDetail")
- @GetMapping("/out/cancelOutbound")
- @PostMapping("/getPageExpressOut")
- @PostMapping("/out/updateSN")

## SpSupplierPartsCostController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/repairs/SpSupplierPartsCostController.java`
- @RequestMapping("/repairs/spSupplierPartsCost")
- @PostMapping("/getPageOneLevel")
- @GetMapping("/getPageOneLevel/export")
- @PostMapping("/getPageTwoLevel")
- @GetMapping("/getPageTwoLevel/export")

## SpWarehouseAttachController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/repairs/SpWarehouseAttachController.java`
- @RequestMapping("/repairs/spWarehouseAttach")
- @PostMapping("/page")
- @GetMapping("/getInfoById")
- @PutMapping("/save")
- @PostMapping("/update")
- @GetMapping("/delete")
- @GetMapping("/export")
- @GetMapping("/downTemplate")
- @RequestMapping(value = "/importData", method = RequestMethod.POST)
- @GetMapping("/SynchronizeJob")

## CdWarehouseRouteController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/repairs/CdWarehouseRouteController.java`
- @RequestMapping("/repairs/cdWarehouseRoute")
- @PostMapping("/queryRoute")

## SpExpressRoutingController
- 文件: `rrsjk-merchant-web/src/main/java/com/rrsjk/merchant/controller/repairs/SpExpressRoutingController.java`
- @RequestMapping("/repairs/spExpressRouting")
- @PostMapping("/getPage")
- @PostMapping("/list")
- @GetMapping("/QueryTrack")
- @PostMapping("/expressCallback")

## SmsController
- 文件: `rrsjk-oauth2-web/src/main/java/com/rrsjk/oauth2/security/auth/sms/SmsController.java`
- @RequestMapping("/sms")
- @GetMapping("/sms_code_login.do")
- @RequestMapping("/send_vertify_code_ln.do")

## SmartController
- 文件: `rrsjk-oauth2-web/src/main/java/com/rrsjk/oauth2/security/auth/baidu/smart/SmartController.java`
- @RequestMapping("/baidu/smart")
- @PostMapping("/login.do")

## MiniController
- 文件: `rrsjk-oauth2-web/src/main/java/com/rrsjk/oauth2/security/auth/wechat/mini/MiniController.java`
- @RequestMapping("/wechat/mini/")
- @PostMapping("/login.do")

## AuthController
- 文件: `rrsjk-oauth2-web/src/main/java/com/rrsjk/oauth2/controller/AuthController.java`
- @RequestMapping("/oauth")
- @PostMapping("/login")
- @PostMapping("/sms_login")                                                                    //改成相应参数
- @PostMapping("/loginOut")
- @GetMapping("/convertToken")
- @GetMapping("/hds_idmlogin")
- @PostMapping("/assertLease/login")

## KaptchaController
- 文件: `rrsjk-oauth2-web/src/main/java/com/rrsjk/oauth2/controller/KaptchaController.java`
- @RequestMapping("/captcha.do")

## UserController
- 文件: `rrsjk-oauth2-web/src/main/java/com/rrsjk/oauth2/controller/UserController.java`
- @GetMapping("/principal.do")

## OpsAuthController
- 文件: `rrsjk-oauth2-web/src/main/java/com/rrsjk/oauth2/controller/OpsAuthController.java`
- @RequestMapping("/oauth/ops")
- @PostMapping("/login")
- @GetMapping("/convertToken")

## MybatisPlusGenerator
- 文件: `vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/java/com/nahui/energy/utils/MybatisPlusGenerator.java`
- 未扫描到显式 Mapping 注解

## JasyptController
- 文件: `vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/java/com/nahui/energy/controller/JasyptController.java`
- @RequestMapping("/jasypt")
- @GetMapping("/encrypt")
- @GetMapping("/decrypt")

## LanController
- 文件: `vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/java/com/nahui/energy/controller/i18n/LanController.java`
- @RequestMapping("/lan/")
- @GetMapping
- @GetMapping("{id}")
- @PostMapping
- @PutMapping
- @DeleteMapping

## DrcloudController
- 文件: `vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/java/com/nahui/energy/controller/vpp/DrcloudController.java`
- @RequestMapping("/drcloud")
- @PostMapping("/data/push")

## NgbController
- 文件: `vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/java/com/nahui/energy/controller/vpp/NgbController.java`
- @RequestMapping("/ngb/appShow")
- @GetMapping("/queryNgbStationBase")
- @GetMapping("/robot/{stationId}")
- @GetMapping("/socialContribution/{stationId}")
- @GetMapping("/operation/photovoltaic/{stationId}")
- @GetMapping("/operation/energyStorage/{stationId}")
- @GetMapping("/operation/chargingstation/{stationId}")
- @GetMapping("/generation/power")
- @GetMapping("/generation/energy")
- @GetMapping("/generation/load")
- @GetMapping("/income/day")
- @GetMapping("/income/month")
- @GetMapping("/income/year")
- @GetMapping("/income/all")

## ManualTaskScheduleController
- 文件: `vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/java/com/nahui/energy/controller/vpp/ManualTaskScheduleController.java`
- @RequestMapping("/ngb/task")
- @GetMapping("/stationBaseJobHandler")
- @GetMapping("/stationRobotJobHandler")
- @GetMapping("/socialContributionJobHandler")
- @GetMapping("/operationPhotovoltaicJobHandler")
- @GetMapping("/operationEnergyStorageJobHandler")
- @GetMapping("/operationChargingStationJobHandler")
- @GetMapping("/generationPowerJobHandlerJobHandler")
- @GetMapping("/generationEnergyJobHandlerJobHandler")
- @GetMapping("/generationLoadJobHandler")
- @GetMapping("/incomeDayJobHandler")
- @GetMapping("/incomeMonthJobHandler")
- @GetMapping("/incomeYearJobHandler")

## NgbStationUserController
- 文件: `vpp-api-elecbusiness/vpp-elecbusiness-biz/src/main/java/com/nahui/energy/controller/vpp/NgbStationUserController.java`
- @RequestMapping("/energy/ngbStationUser")
- @GetMapping("/queryNgbStationUser")
- @PostMapping("/addNgbStationUser")
- @PutMapping("/updateNgbStationUser")
- @DeleteMapping("/deleteNgbStationUser")

## MdmController
- 文件: `vpp-api-gpower/vpp-gpower-biz/src/main/java/com/nahui/energy/controller/MdmController.java`
- @RequestMapping("/mdm")
- @GetMapping("/customer")
- @GetMapping("/supplier")
- @GetMapping("/query-by-tax-code")
- @GetMapping("/companies")
- @GetMapping("/customers-real")

## PowerGridContractController
- 文件: `vpp-api-gpower/vpp-gpower-biz/src/main/java/com/nahui/energy/controller/PowerGridContractController.java`
- @RequestMapping("/PowerGridContract")
- @PostMapping("/add")
- @DeleteMapping("/remove/{id}")
- //    @DeleteMapping("/removeBatch")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")

## PowerGridCompanyController
- 文件: `vpp-api-gpower/vpp-gpower-biz/src/main/java/com/nahui/energy/controller/PowerGridCompanyController.java`
- @RequestMapping("/PowerGridCompany")
- @PostMapping("/add")
- @DeleteMapping("/remove/{id}")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @GetMapping("/export")
- @PostMapping("/enable/{id}")
- @PostMapping("/disable/{id}")

## TestController
- 文件: `vpp-api-gpower/vpp-gpower-biz/src/main/java/com/nahui/energy/controller/TestController.java`
- @GetMapping("/test")

## GreenElectricityRevenueController
- 文件: `vpp-api-gpower/vpp-gpower-biz/src/main/java/com/nahui/energy/controller/GreenElectricityRevenueController.java`
- @RequestMapping("/greenElectricityRevenue")
- @GetMapping("/queryByPage")
- @GetMapping("/export")
- @PostMapping("/add")
- @GetMapping("/getImportTemplate")
- @PostMapping(value = "/importDataNew", consumes = MediaType.MULTIPART_FORM_DATA_VALUE)
- @PostMapping("/uploadSettlementDoc")
- @PostMapping("/financeAudit")
- @PostMapping("/confirmPayment")
- @GetMapping("/getDefaultPaymentAccount")
- @DeleteMapping("/remove/{id}")
- @PostMapping("/reserve")

## InvoiceController
- 文件: `vpp-template/vpp-template-biz/src/main/java/com/nahui/energy/controller/InvoiceController.java`
- @RequestMapping("/Invoice")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")

## WechatShareController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WechatShareController.java`
- @RequestMapping("/share/")
- @PostMapping(value = "/wechat.do")

## AreaZoneController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/area/AreaZoneController.java`
- @RequestMapping("/ares/zone")
- @GetMapping("/get.do")

## MemberAddressController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/member/MemberAddressController.java`
- @RequestMapping("/member/address")
- @GetMapping("/get.do")
- @GetMapping("/mark_as_default.do")
- @GetMapping("/list.do")

## MemberLoginController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/member/MemberLoginController.java`
- 未扫描到显式 Mapping 注解

## WaterDispenserOperatorMultiController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/multi/WaterDispenserOperatorMultiController.java`
- @RequestMapping("/2/water/h5/multi")
- @GetMapping("/getWaterDispenser.do")
- @GetMapping("/getWaterCard.do")
- @GetMapping("/getDispensersForCreateCard.do")
- @GetMapping("/getWaterActivityListNew.do")
- @GetMapping("/getTypeByCardNo.do")
- @PostMapping("requestNewCard.do")
- @PostMapping("cardRechare.do")
- @GetMapping("/queryMember.do")
- @GetMapping("/myWaterCard.do")
- @GetMapping("/queryMemberCards.do")
- @GetMapping("/getCardRechargeRecord.do")
- @GetMapping("/fetchWaterList.do")
- @GetMapping("/generateCardNo.do")

## WaterDispenserMultiController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/multi/WaterDispenserMultiController.java`
- @RequestMapping("/2/water/h5/multiDispenser")
- @GetMapping("/getInAndOutTds.do")
- @GetMapping("/getDispenserAndConfig.do")
- @PostMapping("waterFetchByApp.do")
- @GetMapping("/findDispenserList.do")
- @GetMapping("/getDispenserParams.do")
- @PostMapping("/setDispenserParams.do")

## WaterDispenserWineOrderController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/multi/WaterDispenserWineOrderController.java`
- @RequestMapping("/2/water/h5/wineDispenser")
- @GetMapping("/getAppVersion.do")
- @PostMapping("createOrder.do")
- @PostMapping("pay.do")
- @GetMapping("/getPayResult.do")
- @GetMapping("/findAdList.do")
- @GetMapping("/findWineChannelPriceList.do")
- @GetMapping("/findPriceSpecificationList.do")
- @PostMapping("/uploadWineRecord.do")
- @PostMapping("/uploadStatus.do")
- @GetMapping("/getWineCompensate.do")
- @PostMapping("/wineCompensateStatus.do")
- @GetMapping("/getTestStatus.do")
- @PostMapping("/uploadEnomaticPulse.do")

## WaterDispenserPointsController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/multi/WaterDispenserPointsController.java`
- @RequestMapping("/2/water/h5/ponts")
- @GetMapping("/getOperatorPoints")
- @GetMapping("/getPointChangeOperatorList")
- @GetMapping("/productsList")
- @GetMapping("/getHottestProductsList")
- @GetMapping("/getProductOrderList")
- @GetMapping("/getProductOrder")
- @GetMapping("/getProductInfo")
- @GetMapping("/commitOrder")
- @GetMapping("/updateAddress")
- @GetMapping("/getRegions")
- //    @PostMapping("waterFetchByApp.do")

## EnomaticController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/multi/EnomaticController.java`
- @RequestMapping("/2/water/h5/enomatic")
- @GetMapping("/findEnomatic.do")
- @GetMapping("/findFetchRecord.do")
- @GetMapping("/enomaticSign.do")
- @GetMapping("/getEnomaticDetail.do")
- @GetMapping("/getRegion.do")
- @GetMapping("/findEnomaticChannel.do")
- @GetMapping("/findEnomaticAgentName.do")
- @PostMapping("/operatorJoinApply.do")
- @GetMapping("/findExistOperator.do")
- @GetMapping("/findExistOperatorIdCardInfo.do")
- @GetMapping("/readIdCardImgInfo.do")
- @PostMapping("/enomaticChannelReset.do")
- @GetMapping("/isRealName.do")
- @GetMapping("/findRealNameInfo.do")
- @PostMapping("/saveRealNameInfo.do")
- @GetMapping("/findBindCardInfo.do")
- @PostMapping("/saveBindCardInfo.do")
- @GetMapping("/viewEnomaticOperatorContract.do")

## WaterCardCcbController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/multi/WaterCardCcbController.java`
- @RequestMapping("/2/water/h5/multiDispenser")
- @GetMapping("/ccb/getRechargeActivity.do")
- @PostMapping("/ccb/acceptCardRecharge.do")

## WaterShopkeeperAppointmentMaskController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterShopkeeperAppointmentMaskController.java`
- @RequestMapping("/1/water/app/waterShopkeeperAppointmentMask")
- @RequestMapping(value = "/check", method = RequestMethod.GET,produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/appointment", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getCount", method = RequestMethod.GET,produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getDrawCount", method = RequestMethod.GET,produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/draw", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterStationKnowledgeController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterStationKnowledgeController.java`
- @RequestMapping("/1/water/knowledgeapp/waterStationKnowledge")
- @RequestMapping(value = "/getKnowledgeList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getArticle", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterDispenserController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterDispenserController.java`
- @RequestMapping("/1/water/app/waterDispenser")
- @RequestMapping(value = "/queryDispenser", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/dispenserInfo", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/newDispenser", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/updateAlias", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getByDispenserNo", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getWaterFileterUseRecord", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/findDispenserByLongitudeAndLatitude", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/findTownDispenserByLongitudeAndLatitude", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/queryDispenserByMemberId", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/changeDispenserIPToProduction.do", method = RequestMethod.POST,produces = MediaType.APPLICATION_JSON_VALUE)

## WaterPointProductController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterPointProductController.java`
- @RequestMapping(value = "/1/water/app/waterPointProducts")
- @RequestMapping(value = "/productsList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/hottestProductsList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)

## SewageProjectController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/SewageProjectController.java`
- @RequestMapping("/1/water/app/sewage")
- @RequestMapping(value = "/checkJoinResource", method = RequestMethod.GET,produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/create", method = RequestMethod.POST,produces = MediaType.APPLICATION_JSON_VALUE)

## PointsExchangeProductController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/PointsExchangeProductController.java`
- @RequestMapping(value = "/1/water/app/pointsExchangeProduct")
- @RequestMapping(value = "/getProductList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getAddress", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/editAddress", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/exchangeProduct", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterEarnPointsController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterEarnPointsController.java`
- @RequestMapping(value = "/1/water/app/waterEarnPoints")
- @RequestMapping(value = "/getEarnPointsList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getDetail", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getUnCompleteNum", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterPointsOperatorController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterPointsOperatorController.java`
- @RequestMapping(value = "/1/water/app/waterPointsOperator")
- @RequestMapping(value = "/getOperatorPoints", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getPointChangeOperatorList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/walletRechargeByPoints", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/earnPointsForSignIn", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/earnPointsForOperator", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/earnPointsRules", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getOperatorStarLevel", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterFilterController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterFilterController.java`
- @RequestMapping("/1/water/app/waterFilter")
- @RequestMapping(value = "/getWaterFileterRecord", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/applyChangeFilter", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/applyChangeFilterPackage", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/applyChangeFilterPackageNew", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getApplyList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/applyInfo", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getHistoryList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getExpressRecordByExpressSn", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/confirmChangeFilter", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getWaterFileterStatus", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterFetchRecordController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterFetchRecordController.java`
- @RequestMapping("/1/water/app/waterFetchRecord")
- @RequestMapping(value = "/fetchWaterList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/fetchWaterSum", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/dispenserFetchWaterSum", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterOperatorWalletRecordController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterOperatorWalletRecordController.java`
- @RequestMapping("/1/water/app/waterOperatorWalletRecord")
- @RequestMapping(value = "/walletRecordList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterAdvertiseDetailController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterAdvertiseDetailController.java`
- @RequestMapping("/1/water/app/waterAdvertiseDetail")
- @RequestMapping(value = "/receiveAdv", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/receiptAdv", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterBacklogController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterBacklogController.java`
- @RequestMapping("/1/water/app/waterBacklog")
- @RequestMapping(value = "/getWaterBacklogList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterReportOperatorInfoController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterReportOperatorInfoController.java`
- @RequestMapping("/1/water/app/waterReportOperatorInfo")
- @RequestMapping(value = "/getHomeRanking", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getRanking", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getMessageAndBackLogNum", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getReportOperatorInfo", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterPointsController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterPointsController.java`
- @RequestMapping("/1/water/app/waterPoints")
- @RequestMapping(value = "/getPoint", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getPointDetailList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/waterPointsEarn", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/waterPointsEarnNew", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)

## PrizeController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/PrizeController.java`
- @RequestMapping(value = "/1/water/app/prize")
- @RequestMapping(value = "/getPrize", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getPrizeRecordList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getPrizeList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterStationIncomeController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterStationIncomeController.java`
- @RequestMapping("/1/water/app/income")
- @RequestMapping(value = "/getBilling", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/inComeWithdaw", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/incomeDetailList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/findSumMonthlyRebates", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/findMonthlyRebatesList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/findSumDailyRebates", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/findDailyRebates", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/findRebates", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/queryIncomeForApp", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/queryIncomeDetailForApp", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/queryRebatedDetailForApp", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/cashLnCommission", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterLearningController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterLearningController.java`
- @RequestMapping("/learning")
- @RequestMapping(value = "/uploadScore", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/sendLearningCourse", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/uploadLearningRecord", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/uploadExamResults", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterShopkeeperController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterShopkeeperController.java`
- @RequestMapping(value = "/1/water/app/waterShopkeeper")
- @RequestMapping(value = "/join", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/checkShopkeeper", method = RequestMethod.GET,produces = MediaType.APPLICATION_JSON_VALUE)

## WaterSharePointsController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterSharePointsController.java`
- @RequestMapping("/1/water/app/waterSharePoints")
- @RequestMapping(value = "/getShareWallet", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getShareList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterFetchByAppController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterFetchByAppController.java`
- @RequestMapping("/1/water/app/WaterFetchByApp")
- @RequestMapping(value = "/getFetchVolume", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/waterFetchByApp", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)

## PowerStationRelationController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/PowerStationRelationController.java`
- @RequestMapping(value = "/1/water/app/powerStationRelation")
- @RequestMapping(value = "/getByMemberId", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/savePowerStationRelation", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getPowerStationDetail", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/deletePowerStationRelation", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getEtotal", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)

## CxwShopsDataController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/CxwShopsDataController.java`
- @RequestMapping("/cxw")
- @RequestMapping(value = "/postShopData", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/postExpressOrder", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/postExpressOrderInBody", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/postCleanOrder", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterDispenserOperatorController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterDispenserOperatorController.java`
- @RequestMapping("/1/water/app/waterDispenserOperator")
- @RequestMapping(value = "/requestJoin", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/editPassWord", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/agentLeadTestRechare", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/agentLeadTestRechareV2", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/agentLeadRequestJoin", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getOperatorOrderNum", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getOperatorInfo", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/eOperatorJoin", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getLearnScoreByMemberId", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getLearnSubjectName", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getExamCode", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/realNameApply", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/checkOperatorCanCreateCard", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getDispensersForCreateCard", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getCCBUrl", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getOperatorLnPayFlag", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getShowCleanFlag", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/commitIdentificationAndFaceImg", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterReportUserMultiplierController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterReportUserMultiplierController.java`
- @RequestMapping(value = "/1/water/app/waterReportUserMultiplier")
- @RequestMapping(value = "/getUserMultiplier", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/updateHouseholdNumber", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterMemberInfoController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterMemberInfoController.java`
- @RequestMapping("/1/water/app/waterMemberInfo")
- @RequestMapping(value = "/userUploadFiles", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/saveFamilyNum", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getMemberLevel", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getMemberRank", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/saveWaterMemberIdentityCardImg", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/createLnPayMember", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)

## ConsumerFinanceOperatorDataController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/ConsumerFinanceOperatorDataController.java`
- @RequestMapping("/xfjr")
- @RequestMapping(value = "/getInfoForConsumerFinance", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)

## LeNongLiveController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/LeNongLiveController.java`
- @RequestMapping("/1/water/app/leNongLive")
- @RequestMapping(value = "/getLiveUrl", method = RequestMethod.GET,produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/loginByLive", method = RequestMethod.GET,produces = MediaType.APPLICATION_JSON_VALUE)

## WaterStationNewIncomeController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterStationNewIncomeController.java`
- @RequestMapping("/1/water/app/newIncome")
- @RequestMapping(value = "/newQueryIncomeDetailForApp", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/newQueryIncomeDetailForCloudWisdom", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/newCashLnCommission", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterOperatorExpressInfoController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterOperatorExpressInfoController.java`
- @RequestMapping("/1/water/app/waterOperatorExpressInfo")
- @RequestMapping(value = "/getExpressInfo", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_UTF8_VALUE)
- @RequestMapping(value = "/createExpress", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/delToken", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/createExpressByAuthCode", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterCardController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterCardController.java`
- @RequestMapping("/1/water/app/waterCard")
- @RequestMapping(value = "/requestNewCard", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/queryMemberCards", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/queryMember", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/invalidWaterCard", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/cardRechare", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/memberTypeCount", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getCardByMemberId", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getCardListAndCheckCode", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/applyReplaceCard", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/applyReplaceCardForFree", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/createByOperatorWallet", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/paymentPrepareByOperatorWallet", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getCardRechargeRecord", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/editMobileOrAlias", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getTypeByCardNo", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)

## BinkBankCardController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/BinkBankCardController.java`
- @RequestMapping(value = "/1/water/app/binkBankCard")
- @RequestMapping(value = "/showBindInfo", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getBankInfos", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getAreaOptions", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getCityList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getRegionList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getAreaBanks", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/saveBind", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/cancelBind", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/checkBankCard", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/checkBindInfo", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/cancelBindByLeJia", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/saveBindBankCardAndRealName", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)

## PowerStationDataController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/PowerStationDataController.java`
- @RequestMapping(value = "/1/water/powerStationData")
- @RequestMapping(value = "/sendUserAllData", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterQuestionController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterQuestionController.java`
- @RequestMapping(value = "/1/water/app/waterQuestion")
- @RequestMapping(value = "/getQuestionList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/commitExam", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)

## WithOutTokenController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WithOutTokenController.java`
- @RequestMapping("/1/water/withOutToken")
- @RequestMapping(value = "/getWaterAppConfig", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getTodayVolume", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getArticleById", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getArticleList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getLikeNumRule", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/operatorHomePage", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/queryNewestListBy", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/queryHottestListBy", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/queryLocationListBy", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/queryAroundTdsInfoForApp", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/queryAreaInfo", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/queryTdsInfoForApp", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/idCodeImage", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/sendSms", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getReplyList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getArticleMessages", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getArticleReply", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getAdvertImg", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/searchArticleList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/querySendPackageByRegionCode", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/screen/getPlay", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/screen/checkInfo", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/screen/playCount", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getCCBAppKey", produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getCCBAppKeyIos", produces = MediaType.APPLICATION_JSON_VALUE)

## WaterAppMessageController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterAppMessageController.java`
- @RequestMapping("/1/water/app/waterAppMessage")
- @RequestMapping(value = "/getMessageList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/setReaded", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/updateStatus", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterCommentController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterCommentController.java`
- @RequestMapping("/1/water/app/waterComment")
- @RequestMapping(value = "/getDispenserComment", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/uploadComment", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/checkComment", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/filterComment", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getFilterComment", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterDispenserRepairController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterDispenserRepairController.java`
- @RequestMapping("/1/water/app/waterDispenserRepair")
- @RequestMapping(value = "/dispenserApplyRepair", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/applyRepair", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getRepairById", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getRepairByDispenserId", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/saveRepairComment", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/repairRemind", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getFaultDictionary", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getApplyRepairByDispenserId", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterPostMessagesController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterPostMessagesController.java`
- @RequestMapping(value = "/1/water/app/waterPostMessages")
- @RequestMapping(value = "/queryMyPublistListBy", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/queryMyReplyListBy", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/createPostMessages", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/createMessagesReply", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getReplyByMessageId", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getMessagesMemberByMessageId", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/createMessagesMember", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterStationAppLoginController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterStationAppLoginController.java`
- @RequestMapping("/1/water/appLogin")
- @RequestMapping(value = "/sendSmsValidateCodeNew", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/sendSmsFastLoginUserCenter", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/fastLoginUserCenter", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getAgreement", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/retrievePassWord", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getRegion", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getRotatePic", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/checkApkVersion", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/uploadFiles", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/confirmWaterDispenser", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = {"/getcontract", "/getcontract.pdf"}, method = RequestMethod.GET)
- @RequestMapping(value = "/getWaterActivityBannerList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/checkMemberByThirdForOperator", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/operatorLoginVersionTwo", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/registerAndDoLogin", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getLoginInfoByToken", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/bindMobile", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getPlacehoder", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterDispenserAgentController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterDispenserAgentController.java`
- @RequestMapping("/1/water/app/waterDispenserAgent")
- @RequestMapping(value = "/checkAgentById", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterOperatorLikeNumController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterOperatorLikeNumController.java`
- @RequestMapping("/1/water/app/waterOperatorLikeNum")
- @RequestMapping(value = "/getOperatorLikeNum", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/likeOperator", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getRank", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)

## InsuranceProductController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/InsuranceProductController.java`
- @RequestMapping(value = "/1/water/app/insuranceProduct")
- @RequestMapping(value = "/findAllProduct", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterDispenserRuntimeStatusController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterDispenserRuntimeStatusController.java`
- @RequestMapping("/1/water/app/waterDispenserRuntimeStatus")
- @RequestMapping(value = "/getInAndOutTds", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)

## UserCenterController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/UserCenterController.java`
- @RequestMapping("/1/water/app/userCenter")
- @RequestMapping(value = "/checkMobile", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/captcha", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/send", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/signup", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/oauthToken", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/changePassword", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getbackSms", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterStationCheckToken
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterStationCheckToken.java`
- @RequestMapping("/1/water/app/checkToken")
- @RequestMapping(value = "/checkToken", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterDispenserRepairHccController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterDispenserRepairHccController.java`
- @RequestMapping("/1/water/app/waterDispenserRepair/hcc")
- @RequestMapping(value = "/checkWarranty", method = RequestMethod.GET,produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/record", method = RequestMethod.POST,produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/addSpareParts", method = RequestMethod.POST,produces = MediaType.APPLICATION_JSON_VALUE)

## WaterArticleController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterArticleController.java`
- @RequestMapping("/1/water/app/waterArticle")
- @RequestMapping(value = "/getSubTypeList", method = RequestMethod.GET,produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/findArticle", method = RequestMethod.GET,produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/detail", method = RequestMethod.GET,produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/messagePage", method = RequestMethod.GET,produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/likeOrCancelArticle", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/publicArticleMessages", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/publicArticleReply", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/publicMessageMember", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/deleteArticleMessags", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/deleteArticleReply", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/yzz/discover", method = RequestMethod.GET,produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/discover", method = RequestMethod.GET,produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getAllVideos", method = RequestMethod.GET,produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getByType", method = RequestMethod.GET,produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/recommend", method = RequestMethod.GET,produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/messageReplyPage", method = RequestMethod.GET,produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getReadAndMessageNum", method = RequestMethod.GET,produces = MediaType.APPLICATION_JSON_VALUE)

## WaterAppCommentController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterAppCommentController.java`
- @RequestMapping("/1/water/app/waterAppComment")
- @RequestMapping(value = "/saveAppComment", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterCommunityController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterCommunityController.java`
- @RequestMapping(value = "/1/water/app/waterCommunity")
- @RequestMapping(value = "/home", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/fansRank", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/messageList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/messageInfo", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/commentList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/myStars", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/recommend", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/myCenter", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/editMemberInfo", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/myFans", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/myMessages", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/mySecret", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/postMessage", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/deleteMessage", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/postComment", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/deleteComment", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/queryLocationList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/attentionRelation", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/likeRelation", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/hideRelation", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/replyList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/postReply", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/deleteReply", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/postComplaint", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)

## AppImageController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/AppImageController.java`
- @RequestMapping("/1/water/app/carousel")
- @RequestMapping(value = "/findImage", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/findSubImage", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/findCustomizedItem", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/findBulletin", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/findGoodlifeClass", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/findArticleList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/findArticleItem", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/findArticleItemTypeList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)

## WaterStationContractController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterStationContractController.java`
- @RequestMapping("/1/water/app/contract")
- @RequestMapping(value = "/checkContract", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/reContract", method = RequestMethod.POST, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getcontract", method = RequestMethod.GET)
- @RequestMapping(value = "/getContractTemplet.pdf", method = RequestMethod.GET)
- @RequestMapping(value = "/getContractTempletUrl", method = RequestMethod.GET)

## WaterActivityController
- 文件: `rrsjk-appapi-web/src/main/java/com/rrsjk/appapi/controller/WaterStationApp/WaterActivityController.java`
- @RequestMapping("/1/water/app/waterActivity")
- @RequestMapping(value = "/getWaterActivityList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getWaterActivityListNew", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/getReplaceCardList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)

## ControllerConfig
- 文件: `rrsjk-app-web/src/main/java/com/rrsjk/app/config/ControllerConfig.java`
- 未扫描到显式 Mapping 注解

## IndexController
- 文件: `rrsjk-app-web/src/main/java/com/rrsjk/app/controller/IndexController.java`
- @RequestMapping("/")
- @RequestMapping(method=RequestMethod.GET,value= {"index.html",""})
- @RequestMapping(method=RequestMethod.GET,value= {"toJoin.html",""})
- @RequestMapping(method=RequestMethod.GET,value= {"dispenserJoinIntroduce.html",""})
- @RequestMapping(method=RequestMethod.GET,value= {"dispenserJoinBaseInfo.html",""})
- @RequestMapping(value = "/dispenserJoin/getAgentName",method = RequestMethod.POST)
- @RequestMapping(value = "/dispenserJoin/commitDispenserJoinBaseInfo",method = RequestMethod.POST)
- @RequestMapping(method=RequestMethod.GET,value= {"villageInfo.html",""})
- @RequestMapping(method=RequestMethod.GET,value= {"skipVillageInfo.html",""})
- @RequestMapping(value = "/dispenserJoin/commitVillageInfo",method = RequestMethod.POST)
- @RequestMapping(method=RequestMethod.GET,value= {"auditing.html",""})
- @RequestMapping(method=RequestMethod.GET,value= {"rejected.html",""})
- @RequestMapping(method=RequestMethod.GET,value= {"training.html",""})
- @RequestMapping(method=RequestMethod.GET,value= {"exam.html",""})
- @RequestMapping(value = "/dispenserJoin/commitExam",method = RequestMethod.POST)
- @RequestMapping(method=RequestMethod.GET,value= {"drawCard.html",""})
- @RequestMapping(value = "/dispenserJoin/drawCardCommit",method = RequestMethod.POST)
- @RequestMapping(method=RequestMethod.GET,value={"chemicalFertilizer.html",""})
- @RequestMapping(method=RequestMethod.GET,value={"testEarth.html",""})
- @RequestMapping(method=RequestMethod.GET,value={"testEarthInfo.html",""})
- @RequestMapping(method=RequestMethod.GET,value={"chemFertilizerInfo.html",""})
- @RequestMapping(method=RequestMethod.POST,value={"checkTestEarthStatus.html",""},produces = {"text/html;charset=utf-8"})
- @RequestMapping(method=RequestMethod.POST,value={"checkChemicalFertilizerStatus.html",""},produces = {"text/html;charset=utf-8"})
- @RequestMapping(method=RequestMethod.POST,value={"submitTestEarth.html",""},produces = {"text/html;charset=utf-8"})
- @RequestMapping(method=RequestMethod.POST,value={"submitChemicalFertilizer.html",""},produces = {"text/html;charset=utf-8"})
- @RequestMapping(method=RequestMethod.GET,value={"photovoltaicPower.html",""})
- @RequestMapping(method=RequestMethod.GET,value={"applyStore.html",""})
- //	@RequestMapping(method=RequestMethod.GET,value = {"addressArea.html",""})

## HaierRecuitController
- 文件: `rrsjk-app-web/src/main/java/com/rrsjk/app/controller/HaierRecuitController.java`
- @RequestMapping("/haierRecuit")
- @RequestMapping(method=RequestMethod.GET,value= {"homePage.html",""})
- @RequestMapping(method=RequestMethod.GET,value= {"add.html",""})
- @RequestMapping(method=RequestMethod.GET,value= {"result.html",""})
- @RequestMapping(value = "/commitApplyInfo",method = RequestMethod.POST)

## H5FetchWaterWxPayController
- 文件: `rrsjk-app-web/src/main/java/com/rrsjk/app/controller/H5FetchWaterWxPayController.java`
- @RequestMapping(value = "/h5/wxpay")
- @RequestMapping(value = "/toH5FetchWaterWxpay", method = RequestMethod.POST)
- @RequestMapping(value = "/toH5CardRechargeWxpay", method = RequestMethod.POST)

## FetchWaterController
- 文件: `rrsjk-app-web/src/main/java/com/rrsjk/app/controller/FetchWaterController.java`
- @RequestMapping(value = "/h5/fetchWater")
- @RequestMapping(value = { "/index.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = "/getDispenser",method = RequestMethod.POST)
- @RequestMapping(value = { "/toFetch.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/toCardRecharge.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = "/getCard",method = RequestMethod.POST)

## ShopkeeperJoinController
- 文件: `rrsjk-app-web/src/main/java/com/rrsjk/app/controller/ShopkeeperJoinController.java`
- @RequestMapping("/")
- @RequestMapping(method=RequestMethod.GET,value= {"shopkeeperJoinIntroduce.html",""})
- @RequestMapping(method=RequestMethod.GET,value= {"shopkeeperJoinBaseInfo.html",""})
- @RequestMapping(method=RequestMethod.GET,value= {"shopkeeperJoinToBuyGift.html",""})
- @RequestMapping(value = "/shopkeeperJoinToPaymentNow.html", method = RequestMethod.GET)
- @RequestMapping(value = "/shopkeeperJoinPaySuccess.html", method = RequestMethod.GET)
- @RequestMapping(value = "/dispenserJoin/commitShopkeeperJoinBaseInfo",method = RequestMethod.POST)

## CommonController
- 文件: `rrsjk-app-web/src/main/java/com/rrsjk/app/controller/CommonController.java`
- @RequestMapping("/")
- @RequestMapping("/mobile/common/404.html")
- @RequestMapping(value = "/region/getByParentId",method = RequestMethod.GET)

## WaterArticleController
- 文件: `rrsjk-app-web/src/main/java/com/rrsjk/app/controller/WaterArticleController.java`
- @RequestMapping(value = "/article")
- @RequestMapping(value = { "/article.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = "/updateArticleInfo")
- @RequestMapping(value = "/createArticleMessages")
- @RequestMapping(value = "/createArticleReply")
- @RequestMapping(value = { "/articleMessage.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/messageReply.html" }, method = { RequestMethod.GET })
- @RequestMapping("/messageListByAjax")
- @RequestMapping(value = "/getMemberInfo",method = RequestMethod.GET)
- @RequestMapping(value = "/getArticleMember",method = RequestMethod.GET)
- @RequestMapping(value = "/createArticleMember",method = RequestMethod.POST)
- @RequestMapping(value = "/getArticleMessagesMember",method = RequestMethod.GET)
- @RequestMapping(value = "/createArticleMessagesMember",method = RequestMethod.POST)
- @RequestMapping(value = "/getWechatShareSignature", method = { RequestMethod.POST })

## PointController
- 文件: `rrsjk-app-web/src/main/java/com/rrsjk/app/controller/PointController.java`
- @RequestMapping("/point")
- @RequestMapping(method=RequestMethod.GET,value= {"pointRulesUser.html",""})
- @RequestMapping(method=RequestMethod.GET,value= {"pointRulesOperator.html",""})

## GlobalExceptionConfig
- 文件: `vpp-api-ems/vpp-biz/src/main/java/com/nahui/energy/config/GlobalExceptionConfig.java`
- 未扫描到显式 Mapping 注解

## PingController
- 文件: `vpp-api-ems/vpp-biz/src/main/java/com/nahui/energy/controller/ping/PingController.java`
- @GetMapping("/ping")
- @GetMapping("/test")

## AgentController
- 文件: `vpp-api-ems/vpp-biz/src/main/java/com/nahui/energy/controller/agent/AgentController.java`
- @RequestMapping("/admin/agent")
- @GetMapping("/list/page")

## EchoController
- 文件: `vpp-api-ems/vpp-biz/src/main/java/com/nahui/energy/controller/echo/EchoController.java`
- @RequestMapping("/echo")
- @GetMapping("{url}")

## AuthController
- 文件: `vpp-api-ems/vpp-biz/src/main/java/com/nahui/energy/controller/auth/AuthController.java`
- @RequestMapping("auth")
- @PostMapping("/agent/verify/login")

## UserController
- 文件: `vpp-api-ems/vpp-biz/src/main/java/com/nahui/energy/controller/user/UserController.java`
- @RequestMapping("/admin/user")
- @GetMapping("/list/page")
- @GetMapping("/list/email")

## GlobalExceptionHandler
- 文件: `vpp-api-common/vpp-api-base/src/main/java/com/nahui/energy/config/GlobalExceptionHandler.java`
- 未扫描到显式 Mapping 注解

## SysAccessKeyController
- 文件: `vpp-openapi/vpp-openapi-biz/src/main/java/com/nahui/energy/controller/open/SysAccessKeyController.java`
- @RequestMapping("/SysAccessKey")
- @PostMapping("/apply")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/querySelfAk")
- @GetMapping("/queryById")

## SysPermissionController
- 文件: `vpp-openapi/vpp-openapi-biz/src/main/java/com/nahui/energy/controller/open/SysPermissionController.java`
- @RequestMapping("/SysPermission")
- @PostMapping("/apply")
- @PostMapping("/remove")
- @GetMapping("/queryByAkId")
- @GetMapping("/queryById")
- @GetMapping("/allUrlInfo")

## DrcloudController
- 文件: `vpp-openapi/vpp-openapi-biz/src/main/java/com/nahui/energy/controller/business/DrcloudController.java`
- @GetMapping("/auth/token")
- @PostMapping("/data/push")

## DashboardController
- 文件: `vpp-thai-dashboard/vpp-thai-dashboard-biz/src/main/java/com/nahui/energy/controller/DashboardController.java`
- @GetMapping("/dashboard")
- @RequestMapping(value = "/dashboard", method = RequestMethod.OPTIONS)

## StationDataController
- 文件: `vpp-thai-dashboard/vpp-thai-dashboard-biz/src/main/java/com/nahui/energy/controller/StationDataController.java`
- @RequestMapping("/api/station-data")
- @PostMapping("/collect-realtime")

## HomeController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/HomeController.java`
- @RequestMapping(value = {"/index2.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/index.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = "/sys/messages/latest", method = RequestMethod.GET)
- @RequestMapping(value = "/sys/messages/read", method = RequestMethod.GET)
- @RequestMapping(value = {"/login", "/login.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/forget_password.html"}, method = {RequestMethod.GET})
- @PostMapping(value = {"/forget_password_send_sms.do"})
- @PostMapping(value = {"/forget_password.do"})
- @PostMapping("/sys/login.do")
- @RequestMapping(value = {"/sys/logout.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/sys/changePwd"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/sys/accesslog/find"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/dashbord.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/sys/login1169"}, method = {RequestMethod.GET})
- @GetMapping("/sys/loginIdm.do")
- @GetMapping("/sys/loginIdm.do1")

## Alipays
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/alipay/Alipays.java`
- @RequestMapping(value = "/notify", produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/refund/notify", produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/refundOrder/notify", produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/refund/record", produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/wxPayNotify", produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/kjtPayNotify",produces = MediaType.APPLICATION_JSON_VALUE)

## FilterExchangeKeyController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/filter/FilterExchangeKeyController.java`
- @RequestMapping(value = "filterExchangeKey.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/filterExchangeKeyList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportFilterExchangeKey", method = { RequestMethod.GET })
- @RequestMapping(value = "/delivery", method = { RequestMethod.POST })
- @RequestMapping(value = "/deleteBitch", method = { RequestMethod.POST })
- @RequestMapping(value = {"/downloadKeyTemplate.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = "/importFilterExchangeKey")

## FilterExchangeMachineCodeController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/filter/FilterExchangeMachineCodeController.java`
- @RequestMapping(value = "filterExchangeMachineCode.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/filterExchangeMachineCodeList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportFilterExchangeMachineCode", method = { RequestMethod.GET })
- @RequestMapping(value = "/deleteBitchMachineCode", method = { RequestMethod.POST })
- @RequestMapping(value = {"/downloadMachineCodeTemplate.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = "/importFilterExchangeMachineCode")

## UploadStockInOutsController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/stock/UploadStockInOutsController.java`
- @RequestMapping(value = { "/doUploadInOuts" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/uploadInOuts.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/downloadInOutTemplate" })

## Kuaidi100Controller
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/callback/Kuaidi100Controller.java`
- //@RequestMapping("/callback/")
- @RequestMapping(value = { "/kuaidi100.do" }, method = { RequestMethod.POST })

## SelfOrderIncomeRecordController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/income/SelfOrderIncomeRecordController.java`
- @RequestMapping(value = {"/selfOrderIncome.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/querySelfOrderIncome.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/exportSelfOrderIncome.html"}, method = {RequestMethod.GET})

## SapFinanceAndOrderController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/income/SapFinanceAndOrderController.java`
- @RequestMapping(value = {"/sapReverse.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/querySapReverse.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/gotoSapReverseAddView.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/addSapReverse.html"})

## BreakevenPriceController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/income/BreakevenPriceController.java`
- @RequestMapping(value = {"/breakevens.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryBreakevenRecord.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/gotoBreakevenAddView.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/addBreakevenRecord.html"})
- @RequestMapping(value = {"/gotoBreakevenEditView.html"}, method = {RequestMethod.GET})

## IncomeActualController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/income/IncomeActualController.java`
- @RequestMapping(value = {"/incomeActual.html"},method = {RequestMethod.GET})
- @RequestMapping(value = {"/createIncomeActualList.html"},method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryIncomeForecastAndActual.html"},method = {RequestMethod.GET})
- @RequestMapping(value = {"/incomeDifferenceReport.html"},method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryIncomeDifferenceReport.html"},method = {RequestMethod.GET})

## IncomeForecastController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/income/IncomeForecastController.java`
- @RequestMapping(value = {"/incomeForecast.html"},method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryIncomeForecast.html"},method = {RequestMethod.GET})
- @RequestMapping(value = {"/exportIncomeForecast.html"},method = {RequestMethod.GET})
- @RequestMapping(value = {"/gotoIncomeForeCastImportView.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importIncomeForecast.html"})

## IncomeRecordController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/income/IncomeRecordController.java`
- @RequestMapping(value = {"/incomeRecord.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/incomeRecordCheck.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryIncomeRecord.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/exportIncomeRecord.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/gotoIncomeAddView.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/addIncomeRecord.html"})
- @RequestMapping(value = {"/gotoIncomeEditView.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/editIncomeRecord.html"})
- @RequestMapping(value = {"/confirmReceiptUpdate.do"})
- @RequestMapping(value = {"/deleteIncomeRecord.html"})
- @RequestMapping(value = {"/confirmIncomeById.html"})
- @RequestMapping(value = {"/syncSelfOrderIncomeRecord.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/querySyncSelfOrderIncomeRecord.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/exportSyncSelfOrderIncomeRecord.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/downloadIncomeRecordTemplate.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = "sapHandIncome.html", method = {RequestMethod.GET, RequestMethod.POST})
- @RequestMapping(value = "/sapHandIncomeList", method = {RequestMethod.GET})
- @RequestMapping(value = "/gotoSapHandIncomeImportView", method = RequestMethod.GET)
- @RequestMapping(value = {"/importSapHandIncome.html"})
- @RequestMapping(value = {"/getSubCenterList.html"})
- @RequestMapping(value = {"/getRegionList.html"})

## ExtendedWarrantyController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/warranty/ExtendedWarrantyController.java`
- @RequestMapping(value = "/extendedWarranty")
- @RequestMapping(value = "list.html", method = {RequestMethod.GET})
- @RequestMapping(value = "list", method = {RequestMethod.GET})
- @RequestMapping(value = "/batchAudit", method = { RequestMethod.POST })
- @RequestMapping(value = "detail.html", method = {RequestMethod.GET})
- @RequestMapping(value = "audit.html", method = {RequestMethod.GET})
- @RequestMapping(value = "/audit", method = { RequestMethod.POST })
- @RequestMapping(value = "/export", method = {RequestMethod.GET})

## PurchaseReturnFactoryController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/purchase/PurchaseReturnFactoryController.java`
- @RequestMapping(value = {"/purchaseReturnFactory.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/purchaseReturnFactoryOrderAdd.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryProductForReturnFactoryOrder.html"})
- @RequestMapping(value = {"/addPurchaseReturnFactoryOrder.html"})
- @RequestMapping(value = {"/queryPurchaseReturnFactoryOrderList.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/showReturnFactoryOrderDetailByNo.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/exportPurchaseReturnFactoryOrder.html"}, method = {RequestMethod.GET})

## MemberCorpMonthController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/purchase/MemberCorpMonthController.java`
- @RequestMapping(value = {"/memberCorpMonthManager.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/exportMemberCorpMonth.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/selectOrderProductReportById.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/exportOrderProductReportById.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryMemberCorpMonthList.html"}, method = {RequestMethod.GET})

## KjtAccountController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/purchase/KjtAccountController.java`
- @RequestMapping(value = {"/kjt/checkAccount","klw.html"},method = {RequestMethod.GET})

## SapPurchaseController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/purchase/SapPurchaseController.java`
- @RequestMapping(value = {"/sapPurchaseRecord.html"},method = {RequestMethod.GET})
- //    @RequestMapping(value = {"/querySapPurchaseRecord.html"},method = {RequestMethod.GET})
- @RequestMapping(value = {"/querySapPurchaseRecord.html"},method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryPurchaseForSettle"},method = {RequestMethod.POST})
- @RequestMapping(value = {"/exportSapPurchaseRecord.html"},method = {RequestMethod.GET})

## PurchaseApplySettleController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/purchase/PurchaseApplySettleController.java`
- @RequestMapping(value = {"/purchaseApplySettle.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryPurchaseApplySettle.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/exportPurchaseApplySettle.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/gotoPurchaseApplySettleAddView.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/addPurchaseApplySettle.html"})
- @RequestMapping(value = {"/editPurchaseApplySettle.html"})
- @RequestMapping(value = {"/deletePurchaseApplySettle.html"})
- @RequestMapping(value = {"/gotoPurchaseApplySettleEditView.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/gotoPurchaseApplySettleDetailView.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryMdmSupplier.html"})
- @RequestMapping(value = {"/queryMdmCustom.html"})
- @RequestMapping(value = {"/purchaseApplyCheck.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryPurchaseApplyCheck.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/exportPurchaseApplyCheck.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/checkPurchaseApply.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/purchaseApplyConfirm.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryPurchaseApplyConfirm.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/exportPurchaseApplyConfirm.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/confirmPurchaseApply.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryPurchaseApply.html"})
- @RequestMapping(value = {"/queryInvoiceForSettle.html"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"confirmTicketed.do"}, method = {RequestMethod.POST})

## PurchaseManagerController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/purchase/PurchaseManagerController.java`
- @RequestMapping(value = {"/purchaseManager.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/gotoAddView.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryProductForOrder.html"})
- @RequestMapping(value = {"/addPurchaseOrder"})
- @RequestMapping(value = {"/gotoImportView.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/downloadPurchaseOrderTemplate.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importPurchaseOrders.html"})
- @RequestMapping(value = {"/downloadPurchaseOrderError.html"},method = {RequestMethod.GET})
- @RequestMapping(value = {"/exportPurchaseOrder.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryPurchaseOrderList.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/checkOrderDetailByNo.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/exportOrderDetailByNo.html"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/purchaseOrderDetail.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryPurchaseDetailList.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/exportPurchaseDetail.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/purchaseConfirm.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryPurchaseConfirm.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/confirmPurchaseById.html"})
- @RequestMapping(value = {"/deletePurchaseOrder.html"})
- @RequestMapping(value = {"/auditPurchaseOrder.html"})
- @RequestMapping(value = {"/latestPrice.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/productMainData.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryMainData.html"})
- @RequestMapping(value = { "/editSaleChannel.html" })
- @RequestMapping(value = { "/editSupplier.html" })
- @RequestMapping(value = {"/importMainData.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/addManualMainData.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/addProductData.html"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downloadMainDataTemplate.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importProductMainData.html"})
- @RequestMapping(value = {"/warehouseStraightProducts.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryWarehouseStraightProductsList.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/gotoWarehouseStraightProductsAddView.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/addWarehouseStraightProducts"}, method=RequestMethod.POST)
- @RequestMapping(value = {"/exportWarehouseStraightProducts.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/deleteWarehouseStraightProducts.html"})
- @RequestMapping(value = {"/allocationConfirm.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryAllocationConfirm.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/confirmAllocationById.html"})
- @RequestMapping(value = {"/handSyncSelectSelfAccount.html"})
- @RequestMapping(value = {"/queryMainDataPriceDetail.html"})

## AssetPurchaseController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/purchase/AssetPurchaseController.java`
- @RequestMapping(value = {"/assetPurchaseManager.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/exportAssetPurchaseOrder.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryAssetPurchaseOrderList.html"}, method = {RequestMethod.GET})

## PurchaseReturnFactoryManagementController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/purchase/PurchaseReturnFactoryManagementController.java`
- @RequestMapping(value = "purchaseOrderReturnFactoryList.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/purchaseOrderReturnFactoryList", method = { RequestMethod.GET })
- @RequestMapping(value = "/addPurchaseOrderReturnFactory", method = { RequestMethod.POST })
- @RequestMapping(value = "/editOrderReturn", method = RequestMethod.GET)
- @RequestMapping(value = "/editPurchaseOrderReturnFactory", method = { RequestMethod.POST })
- @RequestMapping(value = "/checkPurchaseOrderReturnFactory", method = { RequestMethod.POST })

## ProductPriceController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/purchase/ProductPriceController.java`
- @RequestMapping(value = {"/productPrice.html"},method = {RequestMethod.GET})
- @RequestMapping(value = { "/checkPurchaseAuthority.html" })
- @RequestMapping(value = { "/checkFinanceAuthority.html" })
- @RequestMapping(value = {"/queryProductPrice.html"},method = {RequestMethod.GET})
- @RequestMapping(value = {"/getProductPrice.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/getProductPriceNew"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/exportProductPrice.html"},method = {RequestMethod.GET})
- @RequestMapping(value = {"/gotoPriceImportView.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/downloadProductPriceTemplate.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importProductPrice.html"})
- @RequestMapping(value = {"/downloadProductPriceError.html"},method = {RequestMethod.GET})
- @RequestMapping(value = { "/checkPriceById.html" })
- @RequestMapping(value = { "/deleteProductPrice.html" })

## PurchasePlatCheckController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/purchase/PurchasePlatCheckController.java`
- @RequestMapping(value = "puchasePlatCheck.html", method = {RequestMethod.GET, RequestMethod.POST})
- @RequestMapping(value = "/puchasePlatCheckList", method = {RequestMethod.GET})
- @RequestMapping(value = "/platCheckAgree", method = {RequestMethod.POST})
- @RequestMapping(value = "/platCheckReject", method = {RequestMethod.POST})
- @RequestMapping(value = "/platCheckSecondAgree", method = {RequestMethod.POST})
- @RequestMapping(value = "/platCheckSecondReject", method = {RequestMethod.POST})

## TransferManagerController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/purchase/TransferManagerController.java`
- //    @RequestMapping(value = {"/testtransferManager.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/transferManager.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/transferStockAdd.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryProductForTransfer.html"})
- @RequestMapping(value = {"/addTransferOrder.html"})
- @RequestMapping(value = {"/queryTransferOrderList.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/showTransferOrderDetailByNo.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/exportTransferOrder.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/cancelTransferOrder.html"})

## ThirdFeeInvoiceSettleController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/purchase/ThirdFeeInvoiceSettleController.java`
- @RequestMapping(value = {"/thirdFeeRecord.html"},method = {RequestMethod.GET})
- @RequestMapping(value = {"/thirdFeeInvoiceSettle.html"},method = {RequestMethod.GET})
- @RequestMapping(value = {"/thirdFeeInvoiceCheck.html"},method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryThirdFeeRecord.html"},method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryThirdFeeRecord"},method = {RequestMethod.POST})
- @RequestMapping(value = {"/queryInvoiceForFee.html"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/queryThirdFeeInvoiceSettle.html"},method = {RequestMethod.GET})
- @RequestMapping(value = {"/exportThirdFeeInvoiceSettle.html"},method = {RequestMethod.GET})
- @RequestMapping(value = {"/exportThirdFeeRecord.html"},method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryThirdFeeInvoiceCheck.html"},method = {RequestMethod.GET})
- @RequestMapping(value = {"/exportThirdFeeInvoiceCheck.html"},method = {RequestMethod.GET})
- @RequestMapping(value = {"/checkThirdFeeInvoiceSettle"},method = {RequestMethod.POST})
- @RequestMapping(value = { "/gotoThirdFeeInvoiceSettleAddView.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/gotoThirdFeeInvoiceSettleEditView.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/gotoThirdFeeInvoiceSettleDetailView.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/addThirdFeeInvoiceSettle.html" })
- @RequestMapping(value = { "/editThirdFeeInvoiceSettle.html" })

## PurchaseInternalController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/purchase/PurchaseInternalController.java`
- @RequestMapping(value = { "/purchaseInternal.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/purchaseInternalCheck.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/queryPurchaseInternalList.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/gotoInternalAddView.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/addPurchaseInternal.html" })
- @RequestMapping(value = { "/gotoInternalEditView.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/editPurchaseInternal.html" })
- @RequestMapping(value = { "/deletePurchaseInternal.html" })
- @RequestMapping(value = { "/checkPurchaseInternal.html" })
- @RequestMapping(value = { "/confirmCheckById.html" })
- @RequestMapping(value = { "/generateSettlementNum.html" })
- @RequestMapping(value = { "/gotoInternalLinkView.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/linkPurchaseInternal.html" })
- @RequestMapping(value = "/creditInternalOrderManager.html", method = { RequestMethod.GET })
- @RequestMapping(value = {"/queryCreditInternalOrderList.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/exportCreditInternalOrder.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = { "/gotoInternalPrintView.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/gotoImportInternalView.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/importInternalBuyOrder.html" }, method = { RequestMethod.POST })
- @RequestMapping(value = {"/downloadInternalOrderError.html"},method = {RequestMethod.GET})
- @RequestMapping(value = {"/downloadPurchaseInternalTemplate.html"}, method = {RequestMethod.GET})

## InstallationCostManagerController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/purchase/InstallationCostManagerController.java`
- @RequestMapping(value = { "/installationCostManager.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/installationCostList.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/gotoAddInstallationCost.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/queryProductForInstallationCost.html" })
- @RequestMapping(value = { "/addInstallationCost.html" })
- @RequestMapping(value = { "/exportInstallationCost.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/deleteInstallationCost.html" })

## BccRebateController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/purchase/BccRebateController.java`
- @RequestMapping(value = {"/bccRebate.html"},method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryBccRebate.html"},method = {RequestMethod.GET})
- @RequestMapping(value = {"/exportBccRebate.html"},method = {RequestMethod.GET})

## OrderRelationController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/OrderRelationController.java`
- @RequestMapping(value = "orderRelation.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/orderRelationList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportOrderRelationList", method = { RequestMethod.GET })
- @RequestMapping(value = "/createOrderRelationQueue", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE+";charset=utf-8")

## EamOrderController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/EamOrderController.java`
- @RequestMapping(value = "eamProject.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/eamProjectList", method = { RequestMethod.GET })
- @RequestMapping(value = "/createEamAssetProject", method = { RequestMethod.POST })
- @RequestMapping(value = "eamGroup.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/eamGroupList", method = { RequestMethod.GET })
- @RequestMapping(value = "eamAsset.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/eamAssetList", method = { RequestMethod.GET })
- @RequestMapping(value = "/eamAssetExport", method = { RequestMethod.GET })

## EchannelLnDeliverShipController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/EchannelLnDeliverShipController.java`
- @RequestMapping(value = {"/lnDeliverShipImport.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/doLnDeliverShipImport"})
- @RequestMapping(value = {"/lnDeliverShipTemplate.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/lnDeliverShipFail.html"}, method = {RequestMethod.GET})

## MemberCorpBlpController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/MemberCorpBlpController.java`
- @RequestMapping(value = "corpblp.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/corpblpList", method = { RequestMethod.GET })
- @RequestMapping(value = "corpblpCheck.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "corpblpReCheck.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "memberCorpBlpDetail.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "downAuthInfoFile", method={RequestMethod.POST})
- @RequestMapping(value = "memberCorpBlpDoCheck", method={RequestMethod.GET})
- @RequestMapping(value = "memberCorpBlpDoReview", method={RequestMethod.GET})

## MemberCorpNetpointController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/MemberCorpNetpointController.java`
- @RequestMapping(value = "corpNetpointAmount.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "corpNetpointAmountCondition.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "corpNetpointAmountOther.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/corpNetpointAmountList", method = { RequestMethod.GET })
- @RequestMapping(value = "/expCorpNetpointAmountList", method = { RequestMethod.GET })

## SimpleOrderInvoiceController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/SimpleOrderInvoiceController.java`
- @RequestMapping(value = "simpleOrderInvoice.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/simpleOrderInvoiceList", method = { RequestMethod.GET })
- @RequestMapping(value = "/elecInvoiceToVat", method = { RequestMethod.POST })
- @RequestMapping(value = "/updateElecInvoice", method = { RequestMethod.POST })

## JinkongPayController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/JinkongPayController.java`
- @RequestMapping(value = {"/jinkongPayList.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryJinkongPayList.html"})
- @RequestMapping(value = {"/exportJinkongPayList.html"}, method = {RequestMethod.GET})

## RrsjkSelfOrderController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/RrsjkSelfOrderController.java`
- @RequestMapping(value = "rrsjkSelfOrder.html", method = {RequestMethod.GET, RequestMethod.POST})
- @RequestMapping(value = "/rrsjkSelfOrderList", method = {RequestMethod.GET})
- @RequestMapping(value = "/rrsjkSelfDeliver", method = {RequestMethod.POST})

## RrsjkOrderController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/RrsjkOrderController.java`
- @RequestMapping(value = "rrsjkOrder.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "rrsjkSelfStoreOrder.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/rrsjkSelfStoreOrderList", method = { RequestMethod.GET })
- @RequestMapping(value = "/rrsjkOrderList", method = { RequestMethod.GET })
- @RequestMapping(value = "/rrsjkDeliver", method = { RequestMethod.POST })
- @RequestMapping(value = {"/rrsjkShipImport.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/doRrsjkShipImport"})
- @RequestMapping(value = "/rrsjkOrderExport", method = { RequestMethod.GET })
- @RequestMapping(value = {"/rrsjkShipTemplate.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/rrsjkShipError.html"},method = {RequestMethod.GET})
- @RequestMapping(value = "/rrsjkCctDeliver", method = { RequestMethod.POST })

## CompanyOrderController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/CompanyOrderController.java`
- @RequestMapping(value = "companyOrder.html", method = {RequestMethod.GET, RequestMethod.POST})
- @RequestMapping(value = "/companyOrderList", method = {RequestMethod.GET})
- @RequestMapping(value = "/getCompanyProductBySku", method = {RequestMethod.GET})
- @RequestMapping(value = "companyOrderAdd.html", method = {RequestMethod.GET, RequestMethod.POST})
- @RequestMapping(value = "doCompanyOrderAdd", method = {RequestMethod.POST})
- @RequestMapping(value = "/uploadOrderVoucher", method = RequestMethod.POST)
- @RequestMapping(value = "companyOrderDetail.html", method = {RequestMethod.GET, RequestMethod.POST})
- @RequestMapping(value = "companyOrderAuditLianQun.html", method = {RequestMethod.GET, RequestMethod.POST})
- @RequestMapping(value = "companyOrderAuditFinance.html", method = {RequestMethod.GET, RequestMethod.POST})
- @RequestMapping(value = "doCompanyOrderAuditLianQun", method = {RequestMethod.POST})
- @RequestMapping(value = "doCompanyOrderEnableAudit", method = {RequestMethod.POST})
- @RequestMapping(value = "doCompanyOrderAuditFinance", method = {RequestMethod.POST})
- @RequestMapping(value = {"findByCustomerForOldCbs.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = "/doCompanyOrderIncreaseStock", method = {RequestMethod.POST})

## VomAllocateController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/VomAllocateController.java`
- @RequestMapping(value = "vomAllocateAdd.html", method = {RequestMethod.GET, RequestMethod.POST})
- @RequestMapping(value = "vomAllocateDoAdd", method = {RequestMethod.POST})
- @RequestMapping(value = "/getAllocateStore", method = RequestMethod.GET)
- @RequestMapping(value = "vomAllocate.html", method = {RequestMethod.GET, RequestMethod.POST})
- @RequestMapping(value = "/vomAllocateList", method = {RequestMethod.GET})
- @RequestMapping(value = {"/vomAllocateImport.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/doVomAllocateImport"})
- @RequestMapping(value = "/vomAllocateExport", method = {RequestMethod.GET})
- @RequestMapping(value = {"/vomAllocateTemplate.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/vomAllocateError.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = "/canceVomAllocate", method = {RequestMethod.POST})

## RrsLnProductController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/RrsLnProductController.java`
- @RequestMapping(value = "lnProduct.html", method = {RequestMethod.GET, RequestMethod.POST})
- @RequestMapping(value = "/lnProductList", method = {RequestMethod.GET})
- @RequestMapping(value = "lnProductAdd.html", method = {RequestMethod.GET, RequestMethod.POST})
- @RequestMapping(value = "lnProductDoAdd", method = {RequestMethod.POST})

## MemberCorpStockController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/MemberCorpStockController.java`
- @RequestMapping(value = "corpStock.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/corpStockList", method = { RequestMethod.GET })
- @RequestMapping(value = "/expCorpStockList", method = { RequestMethod.GET })

## ReshuiOrderController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/ReshuiOrderController.java`
- @RequestMapping(value = "reshuiOrder.html", method = {RequestMethod.GET, RequestMethod.POST})
- @RequestMapping(value = "/reshuiOrderList", method = {RequestMethod.GET})
- @RequestMapping(value = "/reshuiOrderExport", method = {RequestMethod.GET})
- @RequestMapping(value = "/reshuiOrderDeliver", method = {RequestMethod.POST})
- @RequestMapping(value = "/reshuiOrderAudit", method = {RequestMethod.POST})
- @RequestMapping(value = "/reshuiOrderDelete", method = {RequestMethod.POST})
- @RequestMapping(value = "/reshuiOrderCancel", method = {RequestMethod.POST})
- @RequestMapping(value = "/reshuiOrderCancelAudit", method = {RequestMethod.POST})
- @RequestMapping(value = "reshuiExpressRecord.html", method = {RequestMethod.GET, RequestMethod.POST})

## RrsjkOrderCxwController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/RrsjkOrderCxwController.java`
- @RequestMapping(value = "/rrsjkDeliverCxw", method = { RequestMethod.POST })
- @RequestMapping(value = {"/rrsjkDeliverCxwImport.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/doRrsjkShipCxwImport"})
- @RequestMapping(value = {"/rrsjkShipCxwTemplate.html"}, method = {RequestMethod.GET})

## HPDispatchInterfaceController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/HPDispatchInterfaceController.java`
- @RequestMapping(value = { "/hpFromCbs" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/getHttpInterfaceInfo.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/updateHpQueueLoad.html" })
- @RequestMapping(value = { "/updateHpQueue.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/updateLes.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/updateInvoice.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/updateInvoiceSapLog.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/insertLesQueue.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/insertHpQueue.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/insertInvSapQueue.html" }, method = { RequestMethod.GET })

## SupplierExpressController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/SupplierExpressController.java`
- @RequestMapping(value = "supplierExpress.html", method = {RequestMethod.GET, RequestMethod.POST})
- @RequestMapping(value = "createSupplierStore.html", method = {RequestMethod.GET})
- @RequestMapping(value = "/getSupplerStoreRegion", method = RequestMethod.GET)
- @RequestMapping(value = "doSupplierStoreAdd", method = {RequestMethod.POST})
- @RequestMapping(value = "deleteSupplierStore", method = {RequestMethod.POST})
- @RequestMapping(value = "applySupplierCctExpress", method = {RequestMethod.POST})
- @RequestMapping(value = "rrsCctOrder.html", method = {RequestMethod.GET, RequestMethod.POST})
- @RequestMapping(value = "/rrsCctOrderList", method = {RequestMethod.GET})
- @RequestMapping(value = "rrsCctExpressRecord.html", method = {RequestMethod.GET, RequestMethod.POST})

## RrsServiceLogController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/RrsServiceLogController.java`
- @RequestMapping(value = "rrsServiceLog.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/rrsServiceLogList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportRrsServiceLogList", method = { RequestMethod.GET })

## ReshuiSendImportController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/ReshuiSendImportController.java`
- @RequestMapping(value = {"/reshuiSendImport.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/doReshuiSendImport"})
- @RequestMapping(value = {"/reshuiSendTemplate.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/reshuiSendError.html"}, method = {RequestMethod.GET})

## RrsHpAmountController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/RrsHpAmountController.java`
- @RequestMapping(value = "rrsHpAmount.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "rrsHpAmountDetailByAmountId.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/rrsHpAmountList", method = { RequestMethod.GET })
- @RequestMapping(value = "rrsHpAmountDetail.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/rrsHpAmountDetailList", method = { RequestMethod.GET })

## CosmoController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/CosmoController.java`
- @RequestMapping(value = "cosmoPd.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "cosmoPdAdd", method = { RequestMethod.GET })
- @RequestMapping(value = "/cosmoPdList", method = { RequestMethod.GET })
- @RequestMapping(value = "/createCosmoSku", method = { RequestMethod.POST })
- @RequestMapping(value = "getProductDataBySku" ,method = RequestMethod.GET)

## MemberCorpHpAmountController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/MemberCorpHpAmountController.java`
- @RequestMapping(value = "/branch", method = RequestMethod.GET)
- @RequestMapping(value = "corpHpAmount.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/corpHpAmountList", method = { RequestMethod.GET })
- @RequestMapping(value = "/expCorpHpAmountList", method = { RequestMethod.GET })

## SimpleOrderController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/SimpleOrderController.java`
- @RequestMapping(value = "simpleOrder.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/simpleOrderList", method = { RequestMethod.GET })
- @RequestMapping(value = "/handleVomStatusNotify", method = { RequestMethod.POST })
- @RequestMapping(value = "/cancelVomOrder", method = { RequestMethod.POST })
- @RequestMapping(value = "/changeMinusDay.do", method = {RequestMethod.POST})

## MemberCorpSaleController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/MemberCorpSaleController.java`
- @RequestMapping(value = "corpSale.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "corpSaleCondition.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/corpSaleList", method = { RequestMethod.GET })
- @RequestMapping(value = "/expCorpSaleList", method = { RequestMethod.GET })

## FreightCostController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/FreightCostController.java`
- @RequestMapping(value = {"/freightCostInit.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryFreightCostList.html"})
- @RequestMapping(value = {"/gotoAddFreightCostView.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/addFreightCost.html"})
- @RequestMapping(value = {"/gotoUpdateFreightCostView.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/updateFreightCost.html"})
- @RequestMapping(value = {"/exportFreightCost.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/deleteFreightCost.html"})
- @RequestMapping(value = {"/gotoImportFreightCostView.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/downloadFreightCostTemplate.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importFreightCost.html"})

## CompanyController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/CompanyController.java`
- @RequestMapping(value = "company.html", method = {RequestMethod.GET, RequestMethod.POST})
- @RequestMapping(value = "/companyList", method = {RequestMethod.GET})
- @RequestMapping(value = "companyAdd.html", method = {RequestMethod.GET, RequestMethod.POST})
- @RequestMapping(value = "companyDoAdd", method = {RequestMethod.POST})

## MemberCorpBranchController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/MemberCorpBranchController.java`
- @RequestMapping(value = "corpBranchAmount.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/corpBranchAmountList", method = { RequestMethod.GET })
- @RequestMapping(value = "/expCorpBranchAmountList", method = { RequestMethod.GET })

## ReshuiOrderImportController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/ReshuiOrderImportController.java`
- @RequestMapping(value = {"/reshuiOrderImport.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/doReshuiOrderImport"})
- @RequestMapping(value = {"/reshuiOrderTemplate.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/reshuiOrderError.html"}, method = {RequestMethod.GET})

## MemberCorpSumAmountController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/MemberCorpSumAmountController.java`
- @RequestMapping(value = "corpSumAmount.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/corpSumAmountList", method = { RequestMethod.GET })
- @RequestMapping(value = "/expCorpSumAmountList", method = { RequestMethod.GET })

## EchannelLnDeliverController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/EchannelLnDeliverController.java`
- @RequestMapping(value = "echannelLnDeliver.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/echannelLnDeliverList", method = { RequestMethod.GET })
- @RequestMapping(value = "/echannelLnDeliverToSend", method = { RequestMethod.POST })
- @RequestMapping(value = "/echannelLnDeliverToSendBatch", method = { RequestMethod.POST })
- @RequestMapping(value = "/exportEchannelLnDeliverList", method = { RequestMethod.GET })
- @RequestMapping(value = "/echannelLnDeliverToSend", method = { RequestMethod.POST })
- @RequestMapping(value = "/echannelLnDeliverToSendBatch", method = { RequestMethod.POST })
- @RequestMapping(value = "/viewLnExpress", method = { RequestMethod.GET })
- @RequestMapping(value = "editLnDeliverAddress.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/getLnDeliverRegions.html", method = RequestMethod.GET)
- @RequestMapping(value = "doEditLnDeliver", method={RequestMethod.POST})

## RrsjkOrderCctController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/RrsjkOrderCctController.java`
- @RequestMapping(value = {"/rrsjkDeliverCctImport.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/doRrsjkShipCctImport"})
- @RequestMapping(value = {"/rrsjkShipCctTemplate.html"}, method = {RequestMethod.GET})

## CompanyOrderProductController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/CompanyOrderProductController.java`
- @RequestMapping(value = "companyOrderProduct.html", method = {RequestMethod.GET, RequestMethod.POST})
- @RequestMapping(value = "/companyOrderProductList", method = {RequestMethod.GET})
- @RequestMapping(value = "companyOrderProductDetail.html", method = {RequestMethod.GET, RequestMethod.POST})
- @RequestMapping(value = "companyOrderProductSign.html", method = {RequestMethod.GET, RequestMethod.POST})
- @RequestMapping(value = "doCompanyOrderProductSign", method = {RequestMethod.POST})
- @RequestMapping(value = "companyPurchaseOrderInStore.html", method = {RequestMethod.GET, RequestMethod.POST})
- @RequestMapping(value = "doCompanyPurchaseOrderInStore", method = {RequestMethod.POST})
- @RequestMapping(value = "/companyOrderProductExport", method = {RequestMethod.GET})

## RrsjkOrderSignController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/RrsjkOrderSignController.java`
- @RequestMapping(value = {"/rrsjkSignImport.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/doRrsjkSignImport"})
- @RequestMapping(value = {"/rrsjkSignTemplate.html"}, method = {RequestMethod.GET})

## HpWorkController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/HpWorkController.java`
- @RequestMapping(value = {"/hpWork.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/hpWorkList.html"})
- @RequestMapping(value = {"/importHpWork.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/downloadHpWorkTemplate.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importHpWorkData.html"})

## HpSparePartController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/HpSparePartController.java`
- @RequestMapping(value = "hpSparePart.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/hpSparePartList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportHpSparePartList", method = { RequestMethod.GET })

## MemberCorpNetpointSumController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/order/MemberCorpNetpointSumController.java`
- @RequestMapping(value = "corpNetpointSum.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "corpNetpointSumCondition.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/corpNetpointSumList", method = { RequestMethod.GET })
- @RequestMapping(value = "/expCorpNetpointSumList", method = { RequestMethod.GET })

## HealthReportController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/health/HealthReportController.java`
- @RequestMapping(value ="/healthDataManageStore.html")
- //    @RequestMapping("/waterDispenserList")
- //    @RequestMapping("/getCardSum")
- //    @RequestMapping("/waterDispenserMapList")
- //    @RequestMapping(value ="/dispenserReportChart.html")
- //    @RequestMapping(value ="/dispenserCount.html")
- //    @RequestMapping(value = "/dispenserInfoReport.html", method = {RequestMethod.GET})
- //    @RequestMapping(value = "/waterDispenserInfo", method = RequestMethod.POST)
- //    @RequestMapping(value = "/waterSampleInfo.html", method = RequestMethod.GET)
- //    @RequestMapping(value = "/waterSubCenterInfoMap.html")
- //    @RequestMapping(value = "/waterSubCenterInfo.html")
- //    @RequestMapping(value = "/getWaterSubCenterInfoByDataType")
- //    @RequestMapping(value = "/subCenterList", method = RequestMethod.GET)
- //    @RequestMapping(value = "/sampleCountyList", method = RequestMethod.GET)
- //	@RequestMapping(value = "/dispenserTimeInterval.html")
- //	@RequestMapping(value = "/dispenserTimeIntervalMap.html")
- //	@RequestMapping(value = "/subCenterTimeInterval.html")
- //	@RequestMapping(value = "/subCenterTimeIntervalMap.html")
- //    @RequestMapping(value = "/cardDetail.html", method = RequestMethod.GET)

## SysSubCenterController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/subCenter/SysSubCenterController.java`
- @RequestMapping("/sysSubCenter")
- @RequestMapping(value = "subCenter.html", method = { RequestMethod.GET })
- @RequestMapping(value = "subCenterUser.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/subCenterList", method = { RequestMethod.GET })
- @RequestMapping(value = "/subCenterUserList", method = { RequestMethod.GET })
- @RequestMapping(value = "/addSubCenterUser", method = { RequestMethod.POST })
- @RequestMapping(value = "/removeSubCenterUser", method = { RequestMethod.POST })
- @RequestMapping(value = "/getSubCenterById", method = { RequestMethod.GET })

## GovernmentAppUserController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/governmentApp/GovernmentAppUserController.java`
- @RequestMapping(value = "userList.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/governmentAppUserlist", method = { RequestMethod.GET })
- @RequestMapping(value = "/createAppUser", method = { RequestMethod.POST })
- @RequestMapping(value = "/updateUserStatus", method = { RequestMethod.POST })
- @RequestMapping(value = "/getOperatorByRegions", method = { RequestMethod.GET })

## SysPartyController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/sysParty/SysPartyController.java`
- @RequestMapping(value = "party.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/partyList", method = { RequestMethod.GET })
- @RequestMapping(value = "/addParty", method = { RequestMethod.POST })
- @RequestMapping(value = "/editParty", method = { RequestMethod.POST })
- @RequestMapping(value = "/deleteOrUse", method = { RequestMethod.POST })

## SysPartyUserController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/sysParty/SysPartyUserController.java`
- @RequestMapping(value = "partyUser.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/partyUserList", method = { RequestMethod.GET })
- @RequestMapping(value = "/addPartyUser", method = { RequestMethod.POST })
- @RequestMapping(value = "/editPartyUser", method = { RequestMethod.POST })
- @RequestMapping(value = "/getPartyUserById", method = { RequestMethod.GET })
- @RequestMapping(value = "/getBranchRegion", method = { RequestMethod.GET })

## PermissionController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/system/PermissionController.java`
- @RequestMapping("/sys/permission")
- @RequestMapping(value = { "/list.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/find-owner" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/find-resource-tree" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/assign" }, method = { RequestMethod.POST })

## ActionController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/system/ActionController.java`
- @RequestMapping("/sys/action")
- @RequestMapping(value = { "/list.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/find" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/get/{actionId}" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/update" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/create" }, method = { RequestMethod.POST })

## RoleController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/system/RoleController.java`
- @RequestMapping("/sys/role")
- @RequestMapping(value = { "/list.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/find" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/get/{roleId}" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/update" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/create" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/user/assigned" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/user/unassigned" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/user/assign" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/user/unassign" }, method = { RequestMethod.POST })

## MenuController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/system/MenuController.java`
- @RequestMapping("/sys/menu")
- @RequestMapping(value = { "/list.html" }, method = { RequestMethod.GET })
- @GetMapping("menus.do")
- @RequestMapping(value = { "/find/my" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/find/menutree" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/update" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/create" }, method = { RequestMethod.POST })

## UserController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/system/UserController.java`
- @RequestMapping("/sys/user")
- @RequestMapping(value = { "/list.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/accessLog_list.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/find" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/get/{userId}" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/update" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/create" }, method = { RequestMethod.POST })

## HtmlCatchServiceController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/eis/HtmlCatchServiceController.java`
- @RequestMapping(value = { "/catchPersonManageHtml" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/catchTradeManageHtml" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/catchCenterManageHtml" }, method = { RequestMethod.GET })

## VomReverseController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/vom/VomReverseController.java`
- @RequestMapping(value = { "vomReverseList.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "findVomReverseList.html" }, method = { RequestMethod.POST })
- @RequestMapping(value = "/updateStorageStatus", method = { RequestMethod.POST })
- @RequestMapping(value = "/updateReceiptStatus", method = { RequestMethod.POST })

## VOMInformationReceiverController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/vom/VOMInformationReceiverController.java`
- @RequestMapping(value = { "/receive" }, method = { RequestMethod.POST })

## VomReturnLogController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/vom/VomReturnLogController.java`
- @RequestMapping(value = { "vomReturnLog.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "findVomReturnLog.html" }, method = { RequestMethod.POST })

## SaleOrderToJDEController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/vom/SaleOrderToJDEController.java`
- @RequestMapping(value = {"/sendSaleOrder"}, method = {RequestMethod.POST})

## JobController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/job/JobController.java`
- @RequestMapping(value = { "/loadJobPage.html" })
- @RequestMapping(value = { "/onViewCronPlan" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/getJobList.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/getJob" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/reStartJob" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/nowStartJob" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/saveJob.html" }, method = { RequestMethod.POST })

## JobLogController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/job/JobLogController.java`
- @RequestMapping(value = { "/loadJobLogPage.html" })
- //    @RequestMapping(value = { "/onViewCronPlan" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/getJobLogList.html" }, method = { RequestMethod.GET })
- //    @RequestMapping(value = { "/getJob" }, method = { RequestMethod.GET })
- //    @RequestMapping(value = { "/reStartJob" }, method = { RequestMethod.GET })
- //    @RequestMapping(value = { "/nowStartJob" }, method = { RequestMethod.GET })
- //    @RequestMapping(value = { "/saveJob.html" }, method = { RequestMethod.POST })

## PubHeaderFooterController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/pub/PubHeaderFooterController.java`
- @RequestMapping(value = { "/getHeaderFooterList.html" })
- @RequestMapping(value = { "/previewHeaderFooter.html" })
- @RequestMapping(value = { "/publishHeaderFooter.html" })
- @RequestMapping(value = { "/addHeaderFooter.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/addHeaderFooterPost.html" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/updateHeaderFooter.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/updateHeaderFooterPost.html" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/queryHeaderFooterLogList.html" })
- @RequestMapping(value = { "/queryHeaderFooterLog.html" })

## HPBccPayController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/hp/HPBccPayController.java`
- @RequestMapping(value = {"/hpBccPay.html"},method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryHpBccPay.html"},method = {RequestMethod.GET})
- @RequestMapping(value = {"/exportHpBccPay.html"},method = {RequestMethod.GET})

## CardBatchRecordController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/rank/CardBatchRecordController.java`
- @RequestMapping(value = "cardBatchRecord.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/cardBatchRecordList", method = { RequestMethod.GET })
- @RequestMapping(value="/cardBatchRecordSave",method = { RequestMethod.POST })
- @RequestMapping(value = "/exportCardStock", method = { RequestMethod.GET })

## SkuServiceController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/rank/SkuServiceController.java`
- @RequestMapping(value = "skuService.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/skuServiceList", method = { RequestMethod.GET })
- @RequestMapping(value="/skuServiceSaveOrUpdate",method = { RequestMethod.POST })

## BenefitPackageController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/rank/BenefitPackageController.java`
- @RequestMapping(value = "benefitPackageDetail.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/benefitPackageList",method = { RequestMethod.GET })
- @RequestMapping(value="/benefitPackageDetailAdd",method = { RequestMethod.POST })
- @RequestMapping(value="/benefitPackageDetailById",method = { RequestMethod.POST })
- @RequestMapping(value="/benefitPackageDetailUpdate",method = { RequestMethod.POST })
- @RequestMapping(value = "/benefitDetailDelete",method = { RequestMethod.POST })
- @RequestMapping(value = "/operatePackage", method = { RequestMethod.POST })
- @RequestMapping(value = "/saveRankVirtualProducts", method = { RequestMethod.POST })

## CardOrderController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/rank/CardOrderController.java`
- @RequestMapping(value = "cardOrder.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/cardOrderList", method = { RequestMethod.GET })
- @RequestMapping(value="/deliverGoodsCardSave",method = { RequestMethod.POST })
- @RequestMapping(value = "/exportCardOrder", method = { RequestMethod.GET })
- @RequestMapping(value = {"/checkInfoCardOrder"},method = RequestMethod.POST)

## CardStockController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/rank/CardStockController.java`
- @RequestMapping(value = "cardStock.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/cardStockList", method = { RequestMethod.GET })

## BenefitOrderReportInfoController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/rank/BenefitOrderReportInfoController.java`
- @RequestMapping("/benefitReport")
- @RequestMapping(value = "list.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/list.do",method = { RequestMethod.GET,RequestMethod.POST })
- @RequestMapping(value = "/export.do", method = {RequestMethod.GET,RequestMethod.POST})

## BenefitController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/rank/BenefitController.java`
- @RequestMapping(value = "benefit.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/benefitList",method = { RequestMethod.GET })
- @RequestMapping(value="/benefitSaveOrUpdate",method = { RequestMethod.POST })
- @RequestMapping(value = "/getBreakevenPrice",method = { RequestMethod.POST })
- @RequestMapping(value = "/benefitDelete",method = { RequestMethod.POST })
- @RequestMapping(value = "/operatess", method = { RequestMethod.POST })

## MemberBenefitController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/rank/MemberBenefitController.java`
- @RequestMapping(value = "memberBenefit.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/memberBenefitList", method = { RequestMethod.GET })
- @RequestMapping(value = "/memberBenefitUseDataList", method = { RequestMethod.GET })

## BatchSyncInvoiceController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/invoice/BatchSyncInvoiceController.java`
- //    @RequestMapping(value = { "/batchLoad.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/batchNewPage.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/doBatchUpdateTaxInfo.html" }, method = { RequestMethod.GET })

## InvoiceController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/invoice/InvoiceController.java`
- @RequestMapping(value = { "invoiceMakeOutList.html" }, method = { RequestMethod.GET })
- @RequestMapping(value={ "invoiceMakeList.html"},method = { RequestMethod.GET})
- @RequestMapping(value = { "szInvoiceList.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "findInvoiceMakeOutList.html" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/exportInvoiceMakeOutList.html" })
- @RequestMapping(value = { "/getTaxInvoicesInfo.html" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/getElectricInvoiceInfo.html" }, method = { RequestMethod.POST })
- @RequestMapping(value = {"/makeInvoice.html"}, method = { RequestMethod.POST })
- @RequestMapping(value = { "invoiceSapProof.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "makeInvoiceApiLogs.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "findMakeInvoiceApiLogs.html" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "electronIcnvoiceLog.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "findelectronIcnvoiceLogs.html" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "memberInvoiceList.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "findMemberInvoiceList.html" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "exportAllMemberInvoiceList.html" })
- @RequestMapping(value = { "invoicePosProofs.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "findPosProofs.html" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/exportInvoicePosProofsList.html" })
- @RequestMapping(value = { "invoiceSapProofs.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "findSapProofs.html" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/exportInvoiceSapProofsList.html" })
- @RequestMapping(value = { "invoiceSapLogList.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "findInvoiceSapLogList.html" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "modifyMemberInvoices.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "getMemberInvoiceByInvoiceTitle.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "saveMemberInvoices.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "unlockMemberInvoices.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/reSendInvoices.html" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/cancelInvoices.html" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/invalidInvoice.html" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/syncStatusInvoices.html" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/getCustomerCodePage.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/getCustomerCode.html" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "vatInvoiceList.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "findVatInvoiceList.html" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "expressInputInfo.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "saveExpressInput.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/exportVatInvoiceList.html" })
- @RequestMapping(value = { "memberVatInvoiceList.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "findMemberVatInvoiceList.html" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "checkVatInvoiceLicence.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "modifyMemberVatInvoice.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "auditMemberVatInvoice.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/exportMemberVatInvoiceList.html" })

## InvoicePostController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/invoice/InvoicePostController.java`
- @RequestMapping(value = { "invoicePost.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "invoicePostList.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "invoicePostDispense.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "invoicePostDispenseList.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/invoicePostDispenseSubmit.html" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/invoicePostReceipt.html" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "saveInvoicePostExpress.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/findAllManagers.html" }, method = { RequestMethod.POST })

## OrderApiController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/httpapi/OrderApiController.java`
- @RequestMapping("/order")
- @RequestMapping(value = { "/on-cancel" }, method = { RequestMethod.GET })

## OrderCancelController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/cancel/OrderCancelController.java`
- @RequestMapping(value = {"/cancelOrder"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/cancelWholeOrder"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/pushRepairOrder"}, method = {RequestMethod.GET})

## ForecastOrderController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/forecast/ForecastOrderController.java`
- @RequestMapping(value = { "/yycForecast.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/yforecast.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/oforecast.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/manageforecast.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/viewforecast.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/oycForecast.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/export.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/template.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/queryForecastData.html" })
- @RequestMapping(value = { "/queryManageForecastData.html" })
- @RequestMapping(value = { "/manageDetail.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/detail.html" })
- @RequestMapping(value = { "/deleteForecast" })
- @RequestMapping(value = { "/saveManage" })
- @RequestMapping(value = { "/submitManage" })
- @RequestMapping(value = { "/forecastJob.html" })
- @RequestMapping(value = { "/colseJob.html" })
- @RequestMapping(value = { "/importForecastOrders.html" })

## EnomaticProductController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/enomatic/EnomaticProductController.java`
- @RequestMapping(value = "enomaticProduct.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/enomaticProductList", method = { RequestMethod.GET })
- @RequestMapping(value = "/saveEnomaticProduct", method = { RequestMethod.POST })

## EnomaticOperatorController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/enomatic/EnomaticOperatorController.java`
- @RequestMapping(value = "enomaticOperator.html", method = { RequestMethod.GET})
- @RequestMapping(value = "branchEnomaticOperator.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/enomaticOperatorList", method = { RequestMethod.GET })
- @RequestMapping(value = "/viewEnomaticOperatorContract", method = { RequestMethod.GET })
- @RequestMapping(value = "/reSignOperatorContract", method = { RequestMethod.POST })
- @RequestMapping(value = "enomaticOpRealName.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/auditEnomaticOpRealName", method = { RequestMethod.POST })

## EnomaticFetchRecordController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/enomatic/EnomaticFetchRecordController.java`
- @RequestMapping(value = "enomaticFetchRecord.html", method = { RequestMethod.GET})
- @RequestMapping(value = "branchEnomaticFetchRecord.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/enomaticFetchRecordList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportEnomaticRecord", method = { RequestMethod.GET })

## WineProductController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/enomatic/WineProductController.java`
- @RequestMapping(value = "wineProduct.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/wineProductList", method = { RequestMethod.GET })
- @RequestMapping(value = "/saveWineProduct", method = { RequestMethod.POST })
- @RequestMapping(value = "/getProductInfo", method = RequestMethod.GET)
- @RequestMapping(value = "/getNZYProductId", method = RequestMethod.GET)
- @RequestMapping(value = "/uploadWineImage", method = RequestMethod.POST)

## EnomaticAgentController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/enomatic/EnomaticAgentController.java`
- @RequestMapping(value = "enomaticAgent.html", method = { RequestMethod.GET})
- @RequestMapping(value = "branchEnomaticAgent.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/enomaticAgentList", method = { RequestMethod.GET })
- @RequestMapping(value = "/enomaticAuditPass", method = { RequestMethod.POST })
- @RequestMapping(value = "/enomaticAuditReject", method = { RequestMethod.POST })
- @RequestMapping(value = "/downloadEnomaticTwoDimensionCode", method = { RequestMethod.GET })
- @RequestMapping(value = "/viewEnomaticAgentContract", method = { RequestMethod.GET })
- @RequestMapping(value = "/judgeEnomaticAgentContract", method = { RequestMethod.GET })

## EnomaticController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/enomatic/EnomaticController.java`
- @RequestMapping(value = "enomatic.html", method = { RequestMethod.GET})
- @RequestMapping(value = "branchEnomatic.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/enomaticList", method = { RequestMethod.GET })
- @RequestMapping(value = "/changeEnomaticMotherboardCode", method = { RequestMethod.POST })
- @RequestMapping(value = "/findChannelWineList", method = { RequestMethod.GET })
- @RequestMapping(value = "/enableEnomatic", method = { RequestMethod.POST })
- @RequestMapping(value = "/disabledEnomatic", method = { RequestMethod.POST })
- @RequestMapping(value = "/editPulseCount", method = { RequestMethod.POST })
- @RequestMapping(value = "/exportEnomatic", method = { RequestMethod.GET })

## WaterReportTimeIntervalController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportTimeIntervalController.java`
- @RequestMapping(value = "/subCenterList", method = RequestMethod.GET)
- @RequestMapping(value = "/sampleCountyList", method = RequestMethod.GET)
- @RequestMapping(value = "/dispenserTimeInterval.html")
- @RequestMapping(value = "/dispenserTimeIntervalMap.html")
- @RequestMapping(value = "/subCenterTimeInterval.html")
- @RequestMapping(value = "/subCenterTimeIntervalMap.html")
- @RequestMapping(value = "/waterFetchInfo.html", method = RequestMethod.GET)
- @RequestMapping(value = "/waterFetchTrendChartMap.html", method = RequestMethod.GET)

## JointVentureOrderController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/JointVentureOrderController.java`
- @RequestMapping(value = "/jointVentureOrder/auditList.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/jointVentureOrder/findAuditList.do", method = { RequestMethod.GET,RequestMethod.POST })
- @PostMapping(value = "/jointVentureOrder/audit.do")

## WaterDispenserCheckInventoryAnalysisController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterDispenserCheckInventoryAnalysisController.java`
- @RequestMapping(value = "/checkInventoryAnalysis.html", method = { RequestMethod.GET })
- @RequestMapping(value="/checkInventoryAnalysisList",method={ RequestMethod.GET })
- @RequestMapping(value = "/exportCheckInventoryAnalysis", method = { RequestMethod.GET })

## ProductShareRebateController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/ProductShareRebateController.java`
- @RequestMapping(value = "productShareRebate.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/productShareRebateList", method = { RequestMethod.GET })
- @RequestMapping(value = "/signOnMicroList", method = { RequestMethod.GET })
- @RequestMapping(value = "/signOnYearList", method = { RequestMethod.GET })
- @RequestMapping(value = "/getPartyList", method = { RequestMethod.GET })
- @RequestMapping(value = "/saveOrUpRebateInfo", method = { RequestMethod.POST })
- @RequestMapping(value = "/uploadRebatePdf", method = RequestMethod.POST)
- @RequestMapping(value = "/viewRebateContract", method = { RequestMethod.GET })
- @RequestMapping(value = "/viewRebateInfo", method = { RequestMethod.GET })
- @RequestMapping(value = "/auditRebateInfo", method = { RequestMethod.POST })
- @RequestMapping(value = "/exportRebate", method = { RequestMethod.GET })

## WaterReportOperationsController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportOperationsController.java`
- @RequestMapping(value = "/dispenserOperations.html")
- @RequestMapping(value = "/dispenserOperationsMap.html")
- @RequestMapping(value = "/dispenserSubCenter.html", method = RequestMethod.GET)
- @RequestMapping(value = "/noInstallDispenserDetail.html")

## WaterReportMapChartController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportMapChartController.java`
- @RequestMapping(value = "/dispenserMapMonitoringChart.html", method = RequestMethod.GET)
- @RequestMapping(value = "/sjrMapChart.html", method = RequestMethod.GET)
- @RequestMapping(value = "/rrsjkIndex.html", method = RequestMethod.GET)
- @RequestMapping(value="/showBranchInfo", method=RequestMethod.GET)
- @RequestMapping(value ="/dispenserMap.html")
- @RequestMapping("/waterBranchDispenserList")
- @RequestMapping("/getBranchDispenserDetail")
- @RequestMapping(value ="/showDispenserMap.html")
- @RequestMapping("/showWaterDispenserList")
- @RequestMapping(value="/showOperatorStarInfo", method=RequestMethod.GET)
- @RequestMapping(value="/showHomePage", method=RequestMethod.GET)
- @RequestMapping(value="/showDegreeCountyDaily", method=RequestMethod.GET)
- @RequestMapping(value="/showDegreeCountyDailyChart", method=RequestMethod.GET)
- @RequestMapping(value="/showCountyInfo", method=RequestMethod.GET)
- @RequestMapping(value="/showOperatorInfo", method=RequestMethod.GET)
- @RequestMapping(value ="/jkshowIndex.html")
- @RequestMapping(value="/showTransaction", method=RequestMethod.GET)
- @RequestMapping(value="/showTransactionRank", method=RequestMethod.GET)
- @RequestMapping(value ="/dispenserIndexScreen.html")

## WaterReportOperatingSituationController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportOperatingSituationController.java`
- @RequestMapping(value = "/dispenserOperatingChartMap.html", method = RequestMethod.GET)

## SocialRechargeController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/SocialRechargeController.java`
- @RequestMapping(value = "socialRecharge.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/socialRechargeList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportSocialRecharge", method = { RequestMethod.GET })

## WaterConvenienceServiceController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterConvenienceServiceController.java`
- @RequestMapping(value = "convenience.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/convenienceList", method = { RequestMethod.GET })
- @RequestMapping(value = "/updatePackage", method = { RequestMethod.POST })
- @RequestMapping(value = "/updatePerson", method = { RequestMethod.POST })
- @RequestMapping(value = {"/conveniencePackageAdd.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/addConveniencePackage"},method = RequestMethod.POST)
- @RequestMapping(value = {"/prewConveniencePackage"},method = RequestMethod.POST)
- @RequestMapping(value = "prewConveniencePackageDetail.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/uploadConverniceImage", method = RequestMethod.POST)
- @RequestMapping(value = {"/showDetail.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = "convenienceDetail.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/convenienceDetailList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportConvenienceDetail", method = { RequestMethod.GET })
- @RequestMapping(value = {"/conveniencePackageUpdate.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/updateConveniencePackage"},method = RequestMethod.POST)

## WaterDispenerAgentController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterDispenerAgentController.java`
- @RequestMapping(value = "waterAgent.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/agentList", method = { RequestMethod.GET })
- @RequestMapping(value = "/updateRate", method = { RequestMethod.POST })
- @RequestMapping(value = "/auditPass", method = { RequestMethod.POST })
- @RequestMapping(value = "/auditReject", method = { RequestMethod.POST })
- @RequestMapping(value = "/newAgent", method = { RequestMethod.POST })
- @RequestMapping(value = "/getBankInfos", method = { RequestMethod.GET })
- @RequestMapping(value = "/getAreaOptions", method = { RequestMethod.GET })
- @RequestMapping(value = "/getAreaBanks", method = { RequestMethod.GET })
- @RequestMapping(value = "/viewAgentContract", method = { RequestMethod.GET })
- @RequestMapping(value = "/viewAgentSupplementContract", method = { RequestMethod.GET })
- @RequestMapping(value = "/judgeAgentContract", method = { RequestMethod.GET })
- @RequestMapping(value = "/downloadTwoDimensionCode", method = { RequestMethod.GET })
- @RequestMapping(value = "/updateAllowOrder", method = { RequestMethod.POST })
- @RequestMapping(value = "waterAgentTrade.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/agentTradeDtoList", method = { RequestMethod.GET })
- @RequestMapping(value = "/reSignContract", method = { RequestMethod.POST })
- @RequestMapping(value = "/getAgentSupplementContract", method = { RequestMethod.GET })
- @RequestMapping(value = "agentSupplement.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/agentSupplementList", method = { RequestMethod.GET })
- @RequestMapping(value = "/signSupplement", method = { RequestMethod.POST })

## WaterDispenserHccSparePartsController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterDispenserHccSparePartsController.java`
- @RequestMapping("/hcc/spareParts")
- @RequestMapping(value = "/spareParts.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/sparePartsList", method = { RequestMethod.GET })
- @RequestMapping(value = "/delivery", method = { RequestMethod.POST })
- @RequestMapping(value = "/sign", method = { RequestMethod.POST })
- @RequestMapping(value = "/exportSpareParts", method = { RequestMethod.GET })

## WaterDispenserAuthorityController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterDispenserAuthorityController.java`
- @RequestMapping(value = "dispenserAuthority.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/getDispenserAuthorityUser", method = { RequestMethod.GET})
- @RequestMapping(value = "branchRechargeRecord.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/exportDispenserForAuthority", method = { RequestMethod.GET })

## WaterDispenserRepairHccRecordController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterDispenserRepairHccRecordController.java`
- @RequestMapping("/repair/hcc/record")
- @GetMapping("list.html")
- @GetMapping("getByHccNo.do")
- @GetMapping("page.do")

## WaterReportNetThreeDailyController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportNetThreeDailyController.java`
- @RequestMapping(value="/netThreeDaily.html", method = RequestMethod.GET)
- @RequestMapping(value = {"/exportNetThreeDaily.html"}, method = {RequestMethod.GET})

## WaterOperatorWarningController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterOperatorWarningController.java`
- @RequestMapping(value="openSmsWarning.html", method={RequestMethod.GET})
- @RequestMapping(value="operationSmsWarning.html", method={RequestMethod.GET})
- @RequestMapping(value="openSmsWarningList", method={RequestMethod.GET})
- @RequestMapping(value="operationSmsWarningList", method={RequestMethod.GET})
- @RequestMapping(value = "/exportopenSmsWarning", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportoperationSmsWarning", method = { RequestMethod.GET })

## WaterReportEcologicalIncomeController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportEcologicalIncomeController.java`
- @RequestMapping(value="/cateEcologicalIncome.html", method = RequestMethod.GET)
- @RequestMapping(value = {"/exportCateEcologicalIncome.html"}, method = {RequestMethod.GET})
- @RequestMapping(value="/branchEcologicalIncome.html", method = RequestMethod.GET)
- @RequestMapping(value = {"/exportBranchEcologicalIncome.html"}, method = {RequestMethod.GET})
- @RequestMapping(value="/branchCateEcologicalIncome.html", method = RequestMethod.GET)
- @RequestMapping(value = {"/exportBranchCateEcologicalIncome.html"}, method = {RequestMethod.GET})

## WaterStepController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterStepController.java`
- @RequestMapping(value = "step.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/stepList", method = { RequestMethod.GET })
- @RequestMapping(value = "stepAdd.html", method = { RequestMethod.GET })
- @RequestMapping(value = "addStep", method = { RequestMethod.POST })
- @RequestMapping(value = "stepDispatch.html", method = { RequestMethod.GET })
- @RequestMapping(value = "dispatchStep", method = { RequestMethod.POST })
- @RequestMapping(value = "stepServerConfirm.html", method = { RequestMethod.GET })
- @RequestMapping(value = "serverConfirmStep", method = { RequestMethod.POST })
- @RequestMapping(value = "stepDetail.html", method = { RequestMethod.GET })
- @RequestMapping(value = "dispatchStepList", method = { RequestMethod.POST })
- @RequestMapping(value = "/exportDispenserStep", method = { RequestMethod.GET })
- @RequestMapping(value = "getDispenserInfo", method = { RequestMethod.GET })
- @RequestMapping(value = "/uploadStepFile", method = RequestMethod.POST)

## WaterReportCommissionController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportCommissionController.java`
- @RequestMapping(value = "/waterReportOperatorCommission.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/waterReportOperatorCommissionList", method = { RequestMethod.GET })
- //    @RequestMapping(value = "/exportWaterReportCommission", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportWaterReportCommission", method = { RequestMethod.GET })

## WaterDispenserController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterDispenserController.java`
- @RequestMapping(value = "dispenser.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/dispenserList", method = { RequestMethod.GET })
- @RequestMapping(value = "/dispenserOperate", method = { RequestMethod.POST })
- @RequestMapping(value = "/dispenserAudit", method = { RequestMethod.POST })
- @RequestMapping(value = "/dispenserWaitReceive", method = { RequestMethod.POST })
- @RequestMapping(value = "/uploadFiles", method = RequestMethod.POST)
- @RequestMapping(value = "/contractslist", method = RequestMethod.GET)
- @RequestMapping(value = "/uploadDisFiles", method = RequestMethod.POST)
- @RequestMapping(value = "/getDispenserImg", method = RequestMethod.GET)
- @RequestMapping(value = "/delImage/{imageId}", method = RequestMethod.POST)
- @RequestMapping(value = "/contracts", method = { RequestMethod.GET })
- @RequestMapping(value = "/editDispenser", method = RequestMethod.GET)
- @RequestMapping(value = "/getDispenserByDispenserNo", method = RequestMethod.GET)
- @RequestMapping(value = "/updateDispenser", method = { RequestMethod.POST })
- @RequestMapping("commentScoreList")
- @RequestMapping(value = "/showOrderInfo", method = RequestMethod.GET)
- @RequestMapping(value = "/createOrder", method = { RequestMethod.POST })
- @RequestMapping(value = "/changePrice", method = { RequestMethod.POST })
- @RequestMapping(value = "/changeIP", method = { RequestMethod.POST })
- @RequestMapping(value = "/changeDispenserMotherboardCode", method = { RequestMethod.POST })
- @RequestMapping(value = "/updateOzoneWorkTime", method = { RequestMethod.POST })
- @RequestMapping(value = "/testJpush", method = RequestMethod.GET)
- @RequestMapping(value = "/exportDispenser", method = { RequestMethod.GET })
- @RequestMapping(value = "/changeSecondPerLitre", method = { RequestMethod.POST })
- @RequestMapping(value = "/viewContract", method = { RequestMethod.GET })
- @RequestMapping(value = "/judgeContract", method = { RequestMethod.GET })
- @RequestMapping(value = "/getDispenserProduct", method = RequestMethod.GET)
- @RequestMapping(value = "/moveDispenserToNewOperator", method = { RequestMethod.POST })
- @RequestMapping(value = "/changeNewFreeModelRate", method = { RequestMethod.POST })
- @RequestMapping(value = "/changePriceMul", method = { RequestMethod.POST })
- @RequestMapping(value = "/enableMul", method = { RequestMethod.POST })
- @RequestMapping(value = "/disabledMul", method = { RequestMethod.POST })
- @RequestMapping(value = "/enableOfflineCustomer", method = { RequestMethod.POST })
- @RequestMapping(value = "/disableOfflineCustomer", method = { RequestMethod.POST })
- @RequestMapping(value = "/editOfflineCustomerTimes", method = { RequestMethod.POST })
- @RequestMapping(value = "/startup", method = { RequestMethod.POST })
- @RequestMapping(value = "/shutdown", method = { RequestMethod.POST })
- @RequestMapping(value = "/changeLockBalance", method = { RequestMethod.POST })
- @RequestMapping(value = "/changeMux", method = { RequestMethod.POST })

## WaterReportRebateController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportRebateController.java`
- @RequestMapping(value="/waterRebate.html")
- @RequestMapping(value="/waterRebate_county.html")
- @RequestMapping(value="/waterRebate_operator.html")
- @RequestMapping(value="/waterRebate_operator_list.html")

## YntWaterDispenserOperatorController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/YntWaterDispenserOperatorController.java`
- @RequestMapping(value = "yntOperator.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/yntOperatorList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportYntOperator", method = { RequestMethod.GET })

## WaterOperatorStakeController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterOperatorStakeController.java`
- @RequestMapping(value = "waterOperatorStake.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/waterOperatorStakeList", method = { RequestMethod.GET })
- @RequestMapping(value = "waterOperatorStakeAdd.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/newWaterOperatorStake", method = { RequestMethod.POST })
- @RequestMapping(value = "/moveStakeToNewOperator", method = { RequestMethod.POST })

## WaterDispenserImportInfoController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterDispenserImportInfoController.java`
- @RequestMapping(value = "/dispenserImportInfo.html")
- @RequestMapping(value = "/updateDispenserImportInfo", method = { RequestMethod.POST })

## WaterMemberProductsController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterMemberProductsController.java`
- @RequestMapping(value = "waterMemberProducts.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/waterMemberProductsList", method = { RequestMethod.GET })
- @RequestMapping(value = "/updateWaterMemberProducts", method = { RequestMethod.POST })
- @RequestMapping(value = "/newWaterMemberProducts", method = { RequestMethod.POST })

## WaterReportFreeOrderController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportFreeOrderController.java`
- @RequestMapping(value="/freeOrderReport.html", method = RequestMethod.GET)
- @RequestMapping(value = {"/exportFreeOrderReport.html"}, method = {RequestMethod.GET})

## WaterSubCenterAdIncomeImportController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterSubCenterAdIncomeImportController.java`
- @RequestMapping(value = "subCenterAdIncome.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/subCenterAdIncomeList", method = { RequestMethod.GET })
- @RequestMapping(value = "/importSubCenterAdIncome")

## SocialOperatorController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/SocialOperatorController.java`
- @RequestMapping(value = "socialOperator.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/socialOperatorList", method = { RequestMethod.GET })
- @RequestMapping(value = "/auditSocialOperator", method = { RequestMethod.POST })
- @RequestMapping(value = "/editSocialOperator", method = RequestMethod.GET)
- @RequestMapping(value = "/updateSocialOperator", method = { RequestMethod.POST })
- @RequestMapping(value = "/exportSocailOperator", method = { RequestMethod.GET })

## WaterReportLnBranchDailyController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportLnBranchDailyController.java`
- @RequestMapping(value="/lnBranchDaily.html", method = RequestMethod.GET)
- @RequestMapping(value = {"/exportLnBranchDaily.html"}, method = {RequestMethod.GET})

## SewageProjectController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/SewageProjectController.java`
- @GetMapping("/sewageProject.html")
- @RequestMapping("/sewageProjectList.do")
- @RequestMapping(value = "/exportSewageProjectList.do", method = { RequestMethod.GET })

## WaterReportLqScreenController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportLqScreenController.java`
- @RequestMapping(value = "/lqScreenChart.html", method = RequestMethod.GET)
- @RequestMapping(value="/lqKpiList", method = RequestMethod.GET)

## PointsExchangeProductController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/PointsExchangeProductController.java`
- @RequestMapping(value = "/exchangeProduct.html", method = { RequestMethod.GET })
- @RequestMapping(value="/exchangeProductList",method={ RequestMethod.GET })
- @RequestMapping(value = "/invalidExchangeProduct", method = { RequestMethod.POST })
- @RequestMapping(value = "/exchangeProductadd.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/getBySku", method = { RequestMethod.POST })
- @RequestMapping(value = "/newExchangeProduct", method = { RequestMethod.POST })

## WaterDispenserInstallController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterDispenserInstallController.java`
- @RequestMapping("/dispenser/install")
- @RequestMapping(value = "list.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/list", method = { RequestMethod.GET })
- @RequestMapping(value = "/list/export", method = { RequestMethod.GET })
- @RequestMapping(value = {"/importDispenserInstallsView.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importDispenserInstalls.html"})
- @RequestMapping(value = {"/downloadDispenserInstallsTemplate.html"}, method = {RequestMethod.GET})

## WaterEarnPointsController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterEarnPointsController.java`
- @RequestMapping(value = "waterEarnPoints.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/earnPointsList", method = { RequestMethod.GET })
- @RequestMapping(value = "/invalidEarnPoints", method = { RequestMethod.POST })
- @RequestMapping(value = "addEarnPoints.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/newEarnPoints", method = { RequestMethod.POST })

## WaterReportOperationStandardController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportOperationStandardController.java`
- @RequestMapping(value = "operationStandard.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/operationStandardList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportOperationStandard", method = { RequestMethod.GET })

## WaterReportOperatorDailyBranchController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportOperatorDailyBranchController.java`
- @RequestMapping(value="/operatorDailyBranch.html", method = RequestMethod.GET)
- @RequestMapping(value = {"/exportOperatorDailyBranch.html"}, method = {RequestMethod.GET})

## FetchRecordController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/FetchRecordController.java`
- @RequestMapping(value = "fetchRecord.html", method = { RequestMethod.POST })
- @RequestMapping(value = "fetchTransactionRecord.html", method = { RequestMethod.POST })
- @RequestMapping(value = "/fetchRecordList", method = { RequestMethod.GET })

## WaterReportUserMapMonitoringController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportUserMapMonitoringController.java`
- @RequestMapping(value = "/dispenserUserMapMonitoringChart.html", method = RequestMethod.GET)
- @RequestMapping(value="/showUserBranchInfo", method=RequestMethod.GET)

## WaterEcologicalIncomeImportController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterEcologicalIncomeImportController.java`
- @RequestMapping(value = "ecologicalIncome.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/ecologicalIncomeList", method = { RequestMethod.GET })
- @RequestMapping(value = "/importMonitoringEcologicalIncome")
- @RequestMapping(value ="/reFetchData.html")

## FilterChangeController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/FilterChangeController.java`
- @RequestMapping(value = "filterChange.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/filterChangeList", method = { RequestMethod.GET })
- @RequestMapping(value = "/filterApplyAuditPassed", method = { RequestMethod.POST })
- @RequestMapping(value = "/filterApplyAuditReject", method = { RequestMethod.POST })
- @RequestMapping(value = "/filterOrderReject", method = { RequestMethod.POST })
- @RequestMapping(value = "/createFilterOrder", method = { RequestMethod.POST })
- @RequestMapping(value = "/viewFilterApply", method = RequestMethod.GET)
- @RequestMapping(value = "/dispenserBrand", method = RequestMethod.GET)
- @RequestMapping(value = "/exportFilterApply", method = { RequestMethod.GET })
- @RequestMapping(value = "/bf_filterChange.html", method = { RequestMethod.GET})

## WaterWalletController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterWalletController.java`
- @RequestMapping(value = "waterWallet.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/waterWalletList", method = { RequestMethod.GET })
- @RequestMapping(value = "waterWalletAdd.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/newWaterWallet", method = { RequestMethod.POST })
- @RequestMapping(value = "waterWalletRecord.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/waterWalletRecordList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportAccount", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportTransferRecord", method = { RequestMethod.GET })

## WaterSubCenterEcologicalIncomeImportController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterSubCenterEcologicalIncomeImportController.java`
- @RequestMapping(value = "subCenterEcologicalIncome.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/subCenterEcologicalIncomeList", method = { RequestMethod.GET })
- @RequestMapping(value = "/importSubCenterEcologicalIncome")

## WaterDispenserChatController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterDispenserChatController.java`
- @RequestMapping(value ="/dispenserChart.html")

## WaterMessageController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterMessageController.java`
- @RequestMapping(value = "waterMessage.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/messageList", method = { RequestMethod.GET })
- @RequestMapping(value = "addMessage.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/newMessage", method = { RequestMethod.POST })

## WaterReportSmallController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportSmallController.java`
- @RequestMapping(value = "/regionSmallList.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/queryList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportSmall.html", method = {RequestMethod.GET})

## StockReportController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/StockReportController.java`
- @RequestMapping(value = "stockReport.html")
- @RequestMapping(value = "/stockReportList")
- @RequestMapping(value = "/exportStockReport", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportPurchaseDetail", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportSaleDetail", method = { RequestMethod.GET })

## WaterAdIncomeImportController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterAdIncomeImportController.java`
- @RequestMapping(value = "adIncome.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/adIncomeList", method = { RequestMethod.GET })
- @RequestMapping(value = "/importMonitoringAdIncome")

## WaterLearningStarLevelController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterLearningStarLevelController.java`
- @RequestMapping(value = "waterLearningStarLevel.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/waterLearningStarLevelList", method = { RequestMethod.GET })
- @RequestMapping(value = "/auditWaterLearningStarLevel", method = { RequestMethod.POST })

## WaterFilterUseRecordController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterFilterUseRecordController.java`
- @RequestMapping(value = "filterRecord.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/filterRecordList", method = { RequestMethod.GET })

## WaterReportNetBranchController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportNetBranchController.java`
- @RequestMapping(value = "waterReportNetBranchGoal.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/netBranchGoalList", method = { RequestMethod.GET })
- @RequestMapping(value = "/importNetBranchGoal")

## WaterDispenserInputOutputController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterDispenserInputOutputController.java`
- @RequestMapping(value="/branchDispenserAnalysis.html", method = RequestMethod.GET)
- @RequestMapping(value = "/branchDispenserAnalysisList", method = { RequestMethod.GET })
- @RequestMapping(value = {"/exportBranchAnalysis"}, method = {RequestMethod.GET})
- @RequestMapping(value="/dispenserAnalysis.html", method = RequestMethod.GET)
- @RequestMapping(value = "/dispenserAnalysisList", method = { RequestMethod.GET })
- @RequestMapping(value = {"/exportAnalysis"}, method = {RequestMethod.GET})

## YtWaterArticleController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/YtWaterArticleController.java`
- @RequestMapping(value = "ytWaterArticle.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/ytArticleList", method = { RequestMethod.GET })
- @RequestMapping(value = "addYtArticle.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/saveYtArticle", method = { RequestMethod.POST })
- @RequestMapping(value = "editYtArticle.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/updateYtArticle", method = { RequestMethod.POST })
- @RequestMapping(value = "/deleteYtArticle", method = { RequestMethod.POST })
- @RequestMapping(value = {"/prewYtArticle"},method = RequestMethod.POST)
- @RequestMapping(value = "prewYtArticleDetail.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/uploadYtWaterArticleImage", method = RequestMethod.POST)

## LnKpiImportController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/LnKpiImportController.java`
- @RequestMapping(value = "lnKpiImport.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/lnKpiImportList", method = { RequestMethod.GET })
- @RequestMapping(value = "/importLnKpiImport")

## WaterReportDataAnalysisController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportDataAnalysisController.java`
- @RequestMapping(value = "/branchDataAnalysis.html", method = RequestMethod.GET)
- @RequestMapping(value = { "/exportBranchDataAnalysis.html" }, method = { RequestMethod.GET })

## WaterReportOperationIncomeController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportOperationIncomeController.java`
- @RequestMapping(value = "/dispenserOperationIncome.html")

## WaterWalletBuyAuditController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterWalletBuyAuditController.java`
- @RequestMapping(value = "waterWalletBuyAudit.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/waterWalletBuyAuditList", method = { RequestMethod.GET })
- @RequestMapping(value = "/auditWaterWalletBuy", method = { RequestMethod.POST })

## YtWaterCommentController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/YtWaterCommentController.java`
- @RequestMapping(value = "ytWaterComment.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/ytWaterCommentList", method = { RequestMethod.GET })

## CheckInventoryController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/CheckInventoryController.java`
- @RequestMapping(value = "/checkInventory.html", method = { RequestMethod.GET })
- @RequestMapping(value="/checkInventoryList",method={ RequestMethod.GET })
- @RequestMapping(value = "/exportCheckInventory", method = { RequestMethod.GET })

## WaterDispenserOperatorCertificateController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterDispenserOperatorCertificateController.java`
- @RequestMapping(value = "operatorCertificate.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/operatorCertificateList", method = { RequestMethod.GET })
- @RequestMapping(value = "/auditOperatorCertificate", method = { RequestMethod.POST })

## WaterReportTransactionController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportTransactionController.java`
- @RequestMapping(value="/transactionReport.html", method = RequestMethod.GET)
- @RequestMapping(value = {"/exportTransactionReport.html"}, method = {RequestMethod.GET})
- @RequestMapping(value="/transactionCateReport.html", method = RequestMethod.GET)
- @RequestMapping(value = {"/exportTransactionCateReport.html"}, method = {RequestMethod.GET})

## WaterReportCountyGoalController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportCountyGoalController.java`
- @RequestMapping(value = "regionCountyGoal.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/regionCountyList", method = { RequestMethod.GET })
- @RequestMapping(value = "/importRegionCountyGoal")

## WaterOperatorCheckController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterOperatorCheckController.java`
- @RequestMapping(value ="/operatorCheck")
- @RequestMapping(value = "index.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/list.do", method = { RequestMethod.GET })
- @RequestMapping(value ="/labels.do")
- @RequestMapping(value ="/save.do")
- @RequestMapping(value ="/detail.do")
- @RequestMapping(value = "/exportOperatorCheck.do", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportCheckDetail.do", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportCheckTemplate.do", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportCheckLabels.do", method = { RequestMethod.GET })
- @RequestMapping(value = "/importCheckInfo.do", method = { RequestMethod.POST })

## WaterCheckInventoryNetworkWarnController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterCheckInventoryNetworkWarnController.java`
- @RequestMapping(value="networkCheck")
- @RequestMapping(value = "checkIndex.html", method = RequestMethod.GET)
- @RequestMapping(value = "/checkList", method = { RequestMethod.GET })
- @RequestMapping(value = "analysisIndex.html", method = RequestMethod.GET)
- @RequestMapping(value = "/analysisList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportCheck", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportCheckAnalysis", method = { RequestMethod.GET })
- @RequestMapping(value = "/beginCheck", method = { RequestMethod.POST })
- @RequestMapping(value = "/endCheck", method = { RequestMethod.POST })
- @RequestMapping(value = "/getCheckSubCenter", method = RequestMethod.GET)
- @RequestMapping(value = "/getCheckBeginTime", method = RequestMethod.GET)
- @RequestMapping(value = "oldCheckIndex.html", method = RequestMethod.GET)
- @RequestMapping(value = "/oldCheckList", method = { RequestMethod.GET })
- @RequestMapping(value = "oldAnalysisIndex.html", method = RequestMethod.GET)
- @RequestMapping(value = "/oldAnalysisList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportOldCheck", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportOldCheckAnalysis", method = { RequestMethod.GET })
- @RequestMapping(value = "dayCheckIndex.html", method = RequestMethod.GET)
- @RequestMapping(value = "/dayCheckList", method = { RequestMethod.GET })
- @RequestMapping(value = "dayAnalysisIndex.html", method = RequestMethod.GET)
- @RequestMapping(value = "/dayAnalysisList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportDayCheck", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportDayCheckAnalysis", method = { RequestMethod.GET })
- @RequestMapping(value = "/offLineCheck", method = { RequestMethod.POST })

## FetchRecordEcologicalController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/FetchRecordEcologicalController.java`
- @RequestMapping(value = "fetchRecordEcological.html", method = { RequestMethod.POST })
- @RequestMapping(value = "/fetchRecordEcologicalList", method = { RequestMethod.GET })

## OperatorRealNameController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/OperatorRealNameController.java`
- @RequestMapping(value = "operatorRealName.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/auditOperatorRealName", method = { RequestMethod.POST })

## WaterReportCountyEcologicalController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportCountyEcologicalController.java`
- @RequestMapping(value="/countyEcological.html", method = RequestMethod.GET)
- @RequestMapping(value = {"/exportCountyEcological.html"}, method = {RequestMethod.GET})

## WaterReportLnEarningsController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportLnEarningsController.java`
- @RequestMapping(value = "earning.html", method = { RequestMethod.GET})
- @RequestMapping(value = {"/exportLnEarning.html"}, method = {RequestMethod.GET})

## WaterManagerController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterManagerController.java`
- @RequestMapping(value = "/manager.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/managerList", method = { RequestMethod.GET })
- @RequestMapping(value = "managerAdd.html", method = { RequestMethod.GET })
- @RequestMapping(value = "addManager", method = { RequestMethod.POST })
- @RequestMapping(value = "batchStop", method = { RequestMethod.POST })
- @RequestMapping(value = "/exportDispenserManager", method = { RequestMethod.GET })
- @RequestMapping(value = {"/queryManagerData.html"})

## HpOrderInfoController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/HpOrderInfoController.java`
- @RequestMapping(value = "/hpRepair.html", method = { RequestMethod.GET })
- @RequestMapping(value="/hpRepairList",method={ RequestMethod.GET })
- @RequestMapping(value = "/exportHpRepairInfo", method = { RequestMethod.GET })
- @RequestMapping(value = "/repealAppeal", method = { RequestMethod.POST })
- @RequestMapping(value = "/appeal", method = { RequestMethod.POST })
- @RequestMapping(value = "/appealDeal", method = { RequestMethod.POST })

## WaterDispenserNoInstallController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterDispenserNoInstallController.java`
- @RequestMapping(value = "/dispenserNoInstall.html", method = { RequestMethod.GET })
- @RequestMapping(value="/dispenserNoInstallList",method={ RequestMethod.GET })
- @RequestMapping(value = "/exportdispenserNoInstall", method = { RequestMethod.GET })

## SocialCardController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/SocialCardController.java`
- @RequestMapping(value = "socialCard.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/socialCardList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportSocialCard", method = { RequestMethod.GET })

## WaterReportNewSalaryController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportNewSalaryController.java`
- @RequestMapping(value="/newSalary.html", method = RequestMethod.GET)
- @RequestMapping(value = {"/exportNewSalary.html"}, method = {RequestMethod.GET})
- @RequestMapping(value ="/reCountNewSalary.html")
- @RequestMapping(value ="/reCountNewSalaryIncome.html")

## WaterDispenserOperatorController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterDispenserOperatorController.java`
- @RequestMapping(value = "operator.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/list", method = { RequestMethod.GET })
- @RequestMapping(value = "/operate", method = { RequestMethod.POST })
- @RequestMapping(value = "/operateIfLeader", method = { RequestMethod.POST })
- @RequestMapping(value = "/audit", method = { RequestMethod.POST })
- @RequestMapping(value = "/auditEOperator", method = { RequestMethod.POST })
- @RequestMapping(value = "/regions", method = RequestMethod.GET)
- @RequestMapping(value = "/citys", method = RequestMethod.GET)
- @RequestMapping(value = "/checkAudit", method = { RequestMethod.GET })
- @RequestMapping(value = "/editoperator", method = RequestMethod.GET)
- @RequestMapping(value = "/updateOperator", method = { RequestMethod.POST })
- @RequestMapping(value = "/changeSource", method = { RequestMethod.POST })
- @RequestMapping(value = "/createTestCard", method = { RequestMethod.POST })
- @RequestMapping(value = "/exportOperator", method = { RequestMethod.GET })
- @RequestMapping(value = "operatorWallet.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/walletList", method = { RequestMethod.GET })
- @RequestMapping(value = "operatorWalletAdd.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/operatorRankList", method = { RequestMethod.GET })
- @RequestMapping(value = "/newWallet", method = { RequestMethod.POST })
- @RequestMapping(value = "walletRecord.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/walletRecordList", method = { RequestMethod.GET })
- @RequestMapping(value = "/replaceOperator", method = { RequestMethod.POST })
- @RequestMapping(value = "/viewMicroShopContract.pdf", method = { RequestMethod.GET })
- @RequestMapping(value = "operatorEastSea.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/eastSeaList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportEastSeaOperator", method = { RequestMethod.GET })
- @RequestMapping(value = "agentOperator.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/operatorListByAgentId", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportAgentOperator", method = { RequestMethod.GET })
- @RequestMapping(value = "/waterDispenserChangeLogList", method = { RequestMethod.GET })
- @RequestMapping(value = "operatorManageLeader.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/operatorManageLeaderList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportManageLeaderOperator", method = { RequestMethod.GET })
- @RequestMapping(value = "/activityAddOperatorList", method = { RequestMethod.GET })

## WaterDispenserReissueController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterDispenserReissueController.java`
- @RequestMapping(value = "dispenserReissue.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/dispenserReissueList", method = { RequestMethod.GET })
- @RequestMapping(value = "dispenserReissueAdd.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "addDispenserReissue", method = { RequestMethod.POST })
- @RequestMapping(value = "/dispenserReissueAudit", method = { RequestMethod.POST })
- @RequestMapping(value = "/getDispenserReissueById", method = RequestMethod.GET)
- @RequestMapping(value = "dispenserReissueEdit.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/updateDispenserReissue", method = { RequestMethod.POST })
- @RequestMapping(value = "/uploadDispenserReissueFile", method = RequestMethod.POST)
- @RequestMapping(value = "/createDispenserReissueOrder", method = { RequestMethod.POST })

## WaterWalletRechargeAuditController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterWalletRechargeAuditController.java`
- @RequestMapping(value = "waterWalletRechargeAudit.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/waterWalletRechargeAuditList", method = { RequestMethod.GET })
- @RequestMapping(value = "/auditWaterWalletRecharge", method = { RequestMethod.POST })

## WarningController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WarningController.java`
- @RequestMapping(value="netOffWarning.html", method={RequestMethod.GET})
- @RequestMapping(value="tdsWarning.html", method={RequestMethod.GET})
- @RequestMapping(value="filterExpireWarning.html", method={RequestMethod.GET})
- @RequestMapping(value="distanceWarning.html", method={RequestMethod.GET})
- @RequestMapping(value="dispenserFault.html", method={RequestMethod.GET})
- @RequestMapping(value="netOffList", method={RequestMethod.GET})
- @RequestMapping(value = "/getRecordByDispenserNo", method = RequestMethod.GET)
- @RequestMapping(value = "/saveVisitRecord", method = { RequestMethod.POST })
- @RequestMapping(value="tdsList", method={RequestMethod.GET})
- @RequestMapping(value="filterExpireList", method={RequestMethod.GET})
- @RequestMapping(value="distanceList", method={RequestMethod.GET})
- @RequestMapping(value="dispenserFaultList.do", method={RequestMethod.GET})
- @RequestMapping(value = "/exportNetOffWarning", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportTdsWarning", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportFilterExpireWarning", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportDistanceWarning", method = { RequestMethod.GET })
- @RequestMapping(value = "/branchList", method = RequestMethod.GET)
- @RequestMapping(value="netOffWarningPreview.html", method={RequestMethod.GET})
- @RequestMapping(value="netOffWarningPreviewList", method={RequestMethod.GET})
- @RequestMapping(value = "/exportNetOffWarningPreview", method = { RequestMethod.GET })

## WaterReportAppAnalyseController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportAppAnalyseController.java`
- @RequestMapping(value = "/dispenserAppAnalyse.html")

## WaterRechargeSubsidyController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterRechargeSubsidyController.java`
- @RequestMapping(value="rechargeSubsidy")
- @RequestMapping(value = "index.html", method = RequestMethod.GET)
- @RequestMapping(value = "/list", method = { RequestMethod.GET })
- @RequestMapping(value = "operatorIndex.html", method = RequestMethod.GET)
- @RequestMapping(value = "/operatorList", method = { RequestMethod.GET })
- @RequestMapping(value = "agentIndex.html", method = RequestMethod.GET)
- @RequestMapping(value = "/agentList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportSubsidy", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportOperatorSubsidy", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportAgentSubsidy", method = { RequestMethod.GET })

## WaterCardMultiRechargeController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterCardMultiRechargeController.java`
- @RequestMapping(value = "rechargeEcological.html", method = { RequestMethod.GET })
- @RequestMapping(value = "rechargeTransactionEcological.html", method = { RequestMethod.POST })
- @RequestMapping(value = "/rechargeEcologicalList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportEcologicalRecharge", method = { RequestMethod.GET })

## WaterReportMobileMonitoringGoalController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportMobileMonitoringGoalController.java`
- @RequestMapping(value = "mobileMonitoringGoal.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/mobileMonitoringGoalList", method = { RequestMethod.GET })
- @RequestMapping(value = "/importMobileMonitoringGoal")

## WaterReportCountyDailyController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportCountyDailyController.java`
- @RequestMapping(value="/dispenserManagerDaily.html", method = RequestMethod.GET)
- @RequestMapping(value="/dispenserManagerDailyNew.html", method = RequestMethod.GET)
- @RequestMapping(value="/dispenserManagerDailyList", method={RequestMethod.GET})
- @RequestMapping(value = {"/exportDispenserManagerDaily.html"}, method = {RequestMethod.GET})

## WaterReportECountyCenterController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportECountyCenterController.java`
- @RequestMapping(value="/waterReportECountyCenter.html", method={RequestMethod.GET})
- @RequestMapping(value="/waterReportECountyCenterList", method={RequestMethod.GET})
- @RequestMapping(value = {"/exportECountyCenter"}, method = {RequestMethod.GET})

## WaterDispenserWarrantyController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterDispenserWarrantyController.java`
- @RequestMapping("/warranty")
- @GetMapping("list.html")
- @GetMapping("page.do")
- @PostMapping("update.do")
- @GetMapping("authority/list.html")
- @GetMapping("authority/page.do")

## WaterOperatorAdvertOrderController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterOperatorAdvertOrderController.java`
- @RequestMapping(value ="/waterOperatorAdvertOrder")
- @RequestMapping(value = "index.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/list.do", method = { RequestMethod.GET })
- @RequestMapping(value ="/audit.do")
- @RequestMapping(value = "/export.do", method = { RequestMethod.GET })
- @RequestMapping(value = "/downloadImage.do", method = { RequestMethod.GET })
- @RequestMapping(value = "/downloadImportTemplate.do", method = { RequestMethod.GET })
- @RequestMapping(value = "/importOrder.do", method = { RequestMethod.POST })

## WaterAdvertiseManagerController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterAdvertiseManagerController.java`
- @RequestMapping(value = "advertise.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/advertiseList", method = { RequestMethod.GET })
- @RequestMapping(value = "/updateAdvertiseStatus", method = { RequestMethod.POST })
- @RequestMapping(value = {"/advertiseAdd.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/addAdvertise"},method = RequestMethod.POST)
- @RequestMapping(value = {"/prewAdvertise"},method = RequestMethod.POST)
- @RequestMapping(value = "prewAdvertiseDetail.html", method = { RequestMethod.GET })
- @RequestMapping(value = {"/showAdvertiseDetail.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/advertiseUpdate.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/updateAdvertise"},method = RequestMethod.POST)
- @RequestMapping(value = "advertiseDetail.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/advertiseDetailList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportAdvertiseDetail", method = { RequestMethod.GET })
- @RequestMapping(value = "/updateAdvertiseDetail", method = { RequestMethod.POST })
- @RequestMapping(value = "/batchUpdateAdvertiseDetail", method = { RequestMethod.POST })
- @RequestMapping(value = "AddAdvertiseDetail.html", method = { RequestMethod.GET })

## YtWaterAreaController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/YtWaterAreaController.java`
- @RequestMapping(value ="/ytWaterArea.html")
- @RequestMapping(value="/saveYtWaterArea",method=RequestMethod.POST)
- @RequestMapping(value="/updateYtWaterArea",method=RequestMethod.POST)
- @RequestMapping(value = "/updateYtAreaIntro",method = RequestMethod.POST)
- //	@RequestMapping(value = "/deleteYtAreaIntro", method = { RequestMethod.POST })
- @RequestMapping(value = "/getWaterArea", method = RequestMethod.GET)
- @RequestMapping(value ="/ytWaterMenu.html")
- @RequestMapping(value="/saveYtWaterMenu",method=RequestMethod.POST)
- @RequestMapping(value = "/getWaterMenu", method = RequestMethod.GET)

## CleanServerOrderManagementController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/CleanServerOrderManagementController.java`
- @RequestMapping(value = "cleanServerOrderManagement.html", method = { RequestMethod.GET })
- @RequestMapping(value="/cleanServerOrderList", method = { RequestMethod.GET})
- @RequestMapping(value = "/queryRegions", method = RequestMethod.GET)
- @RequestMapping(value = "/exportCleanOrder", method = { RequestMethod.GET })

## WaterReportAreaCenterStandardsController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportAreaCenterStandardsController.java`
- @RequestMapping(value="/areaCenterStandard.html", method = RequestMethod.GET)
- @RequestMapping(value = {"/exportAreaCenterStandard.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = "areaTarget.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/areaTargetList", method = { RequestMethod.GET })
- @RequestMapping(value = "/importAreaTarget")

## RiceFieldRecognizeManageController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/RiceFieldRecognizeManageController.java`
- @RequestMapping(value = "riceFieldRecognizeInfoList.html", method = { RequestMethod.GET })
- @RequestMapping(value = "riceFieldRecognizeBrand.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/recognizeList", method = { RequestMethod.GET })
- @RequestMapping(value = "showFilterData.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/showFilterData", method = { RequestMethod.GET })
- @RequestMapping(value = "addRiceFieldRecognize.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/uploadRecognizeImage", method = RequestMethod.POST)
- @RequestMapping(value = "/findRegions", method = RequestMethod.GET)
- @RequestMapping(value = {"/addRecognizeInfo"},method = RequestMethod.POST)
- @RequestMapping(value = {"/findOneRecognize"},method = RequestMethod.POST)
- @RequestMapping(value = "updateRiceFieldRecognize.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/updateRecognize", method = { RequestMethod.POST })
- @RequestMapping(value = "/importRecognizeInfo")
- @RequestMapping(value = "/exportRecognize", method = { RequestMethod.GET })

## WaterReportThreeDegreeDailyBranchController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportThreeDegreeDailyBranchController.java`
- @RequestMapping(value="/threeDegreeDailyBranch.html", method = RequestMethod.GET)
- @RequestMapping(value = {"/exportThreeDegreeDailyBranch.html"}, method = {RequestMethod.GET})

## WaterDispenserTestController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterDispenserTestController.java`
- @RequestMapping(value = "testDispenser.html", method = { RequestMethod.GET })
- @RequestMapping(value = "step02.html", method = { RequestMethod.GET})
- @RequestMapping(value = "step03.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/checkCardAndRecharge", method = { RequestMethod.POST })
- @RequestMapping(value = "/appFetchWater", method = { RequestMethod.POST })
- @RequestMapping(value = "/changeIPAndFinish", method = { RequestMethod.POST })
- @RequestMapping(value = "/updateWaterDispenserTest", method = { RequestMethod.POST })

## WaterReportDirectorController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportDirectorController.java`
- @RequestMapping(value="/directorReport.html", method = RequestMethod.GET)
- @RequestMapping(value = {"/exportDirectorReport.html"}, method = {RequestMethod.GET})

## WaterReportContactLightspotDailyController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportContactLightspotDailyController.java`
- @RequestMapping(value="/contactLightspotDaily.html", method = RequestMethod.GET)
- @RequestMapping(value = {"/exportContactLightspotDaily.html"}, method = {RequestMethod.GET})

## RiceFieldDynamicManageController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/RiceFieldDynamicManageController.java`
- @RequestMapping(value = "riceFieldDynamicList.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/dynamicList", method = { RequestMethod.GET })
- @RequestMapping(value = "addRiceFieldDynamic.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/uploadDynamicImage", method = RequestMethod.POST)
- @RequestMapping(value = {"/addDynamic"},method = RequestMethod.POST)
- @RequestMapping(value = "updateRiceFieldDynamic.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/updateDynamic", method = { RequestMethod.POST })
- @RequestMapping(value = "/deleteDynamic", method = { RequestMethod.POST })
- @RequestMapping(value = "riceFieldCommentList.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/commentList", method = { RequestMethod.GET })
- @RequestMapping(value = "/findOneCommertById", method = { RequestMethod.GET })
- @RequestMapping(value = "/addCommert", method = { RequestMethod.POST })
- @RequestMapping(value = "/hideComment", method = { RequestMethod.POST })

## SocialDispenserController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/SocialDispenserController.java`
- @RequestMapping(value = "socialDispenser.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/socialDispenserList", method = { RequestMethod.GET })
- @RequestMapping(value = "/getSocialDispenserImg", method = RequestMethod.GET)
- @RequestMapping(value = "/editSocialDispenser", method = RequestMethod.GET)
- @RequestMapping(value = "/updateSocialDispenser", method = { RequestMethod.POST })
- @RequestMapping(value = "/changeSocialDispenserMotherboardCode", method = { RequestMethod.POST })
- @RequestMapping(value = "/exportSocialDispenser", method = { RequestMethod.GET })
- @RequestMapping(value = "/socialDispenserOperate", method = { RequestMethod.POST })
- @RequestMapping(value = "/socialOperatorCheck", method = RequestMethod.POST)
- @RequestMapping(value = "/socialDispenserAdresAudit", method = {RequestMethod.POST})
- @RequestMapping(value = "/socialDispenserAudit", method = { RequestMethod.POST })
- @RequestMapping(value = "/createSocialOrder", method = { RequestMethod.POST })

## WaterReportFilterWarningController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportFilterWarningController.java`
- @RequestMapping(value = "waterReportFilterWarning.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/waterReportFilterWarningList", method = { RequestMethod.GET })

## WaterReportBranchEcologicalController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportBranchEcologicalController.java`
- @RequestMapping(value="/branchEcological.html", method = RequestMethod.GET)
- @RequestMapping(value = {"/exportBranchEcological.html"}, method = {RequestMethod.GET})

## WaterReportSampleCountyOperationsController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportSampleCountyOperationsController.java`
- @RequestMapping(value = "/waterSampleCountyOperations.html", method = RequestMethod.GET)
- @RequestMapping(value = "/waterSampleCountyOperationsMap.html", method = RequestMethod.GET)
- @RequestMapping(value = "/dispenserSampleCounty.html", method = RequestMethod.GET)

## YtHomePageController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/YtHomePageController.java`
- @RequestMapping(value ="/ytHomePage.html")
- @RequestMapping(value = "/saveOrUpdateYtAd", method = RequestMethod.POST)
- @RequestMapping(value = "/saveOrUpdateYtNotice", method = RequestMethod.POST)
- @RequestMapping(value="/editYtAd", method=RequestMethod.GET)
- @RequestMapping(value="/editYtNotice", method=RequestMethod.GET)
- @RequestMapping(value="/publishYtHomePage", method=RequestMethod.GET)

## WaterMicroShopHomePageController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterMicroShopHomePageController.java`
- @RequestMapping(value ="/microShopHomePage.html")
- @RequestMapping(value = "/saveOrUpdateMicroShopBanner", method = RequestMethod.POST)
- @RequestMapping(value = "/saveOrUpdateShopTopLine", method = RequestMethod.POST)
- @RequestMapping(value = "/saveOrUpdateShopDailySpecial", method = RequestMethod.POST)
- @RequestMapping(value = "/saveOrUpdateShopRecommend", method = RequestMethod.POST)
- @RequestMapping(value = "/saveOrUpdateProductBanner", method = RequestMethod.POST)
- @RequestMapping(value="/editMicroShopBanner", method=RequestMethod.GET)
- @RequestMapping(value="/editShopTopLine", method=RequestMethod.GET)
- @RequestMapping(value="/editShopDailySpecial", method=RequestMethod.GET)
- @RequestMapping(value="/editProductBanner", method=RequestMethod.GET)
- @RequestMapping(value="/editShopRecommend", method=RequestMethod.GET)
- @RequestMapping(value="/publishShopHomePage", method=RequestMethod.GET)

## ProcessDispenserIssueController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/ProcessDispenserIssueController.java`
- @RequestMapping(value = "processDisIssue.html")
- @RequestMapping(value = "/processList")
- @RequestMapping(value = "/taskList")
- @RequestMapping(value = "/startEvent", method = { RequestMethod.POST })
- @RequestMapping(value = "/auditTask", method = { RequestMethod.POST })
- @RequestMapping(value = "/batchAuditTask", method = { RequestMethod.POST })
- @RequestMapping(value = "/solveTask", method = { RequestMethod.POST })
- @RequestMapping(value = "/stopProcess", method = { RequestMethod.POST })
- @RequestMapping(value = "/uploadAttachment", method = RequestMethod.POST)
- @RequestMapping(value = "showProcessDiagram")
- @RequestMapping(value = "/downloadAttachment", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportProcessIssue")
- @RequestMapping(value = "/showNodeInfo", method = { RequestMethod.GET })

## WaterDispenserBucketController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterDispenserBucketController.java`
- @RequestMapping(value = "dispenserBucket.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/dispenserBucketList", method = { RequestMethod.GET })
- @RequestMapping(value = "/showOrderInfoBucket", method = RequestMethod.GET)
- @RequestMapping(value = "/createOrderBucket", method = { RequestMethod.POST })
- @RequestMapping(value = "/exportDispenserBucket", method = { RequestMethod.GET })
- @RequestMapping(value = "dispenserBucketMake.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = {"/importDispenserOrdersView.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importDispenserOrders.html"})

## WaterReportThreeDegreeDailyBranchGoalController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportThreeDegreeDailyBranchGoalController.java`
- @RequestMapping(value = "waterReportThreeDegreeDailyBranchGoal.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/threeDegreeDailyBranchGoalList", method = { RequestMethod.GET })
- @RequestMapping(value = "/importThreeDegreeDailyBranchGoal")

## WaterRechargeController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterRechargeController.java`
- @RequestMapping(value = "recharge.html", method = { RequestMethod.GET })
- @RequestMapping(value = "rechargeTransaction.html", method = { RequestMethod.POST })
- @RequestMapping(value = "/rechargeList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportRecharge", method = { RequestMethod.GET })
- @RequestMapping(value = "rechargeManager.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/rechargeManagerList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportRechargeManager", method = { RequestMethod.GET })

## WaterDispenserScreenController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterDispenserScreenController.java`
- @RequestMapping("/waterDispenserScreen.html")
- @RequestMapping("/waterDispenserScreenList")
- @RequestMapping("/waterDispenserScreen/queryDispenser")
- @RequestMapping("/waterDispenserScreen/saveOrUpdate")
- @RequestMapping("/waterDispenserScreen/delete")

## WaterReportAppDownloadController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportAppDownloadController.java`
- @RequestMapping(value = "/dispenserMapAppDownload.html", method = RequestMethod.GET)

## WaterReportOperationStandardLevelController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportOperationStandardLevelController.java`
- @RequestMapping(value = "operationStandardLevel.html")

## WaterOperatorHomePageController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterOperatorHomePageController.java`
- @RequestMapping(value ="/operatorHomePage.html")
- @RequestMapping(value = "/saveOrUpdateOperatorAd", method = RequestMethod.POST)
- @RequestMapping(value = "/saveOrUpdateOperatorTl", method = RequestMethod.POST)
- @RequestMapping(value = "/saveOrUpdatePanicBuying", method = RequestMethod.POST)
- @RequestMapping(value = "/saveOrUpdateOperatorRecommend", method = RequestMethod.POST)
- @RequestMapping(value="/editOperatorAd", method=RequestMethod.GET)
- @RequestMapping(value="/editOperatorTl", method=RequestMethod.GET)
- @RequestMapping(value="/editOperatorPb", method=RequestMethod.GET)
- @RequestMapping(value="/editOperatorRecommend", method=RequestMethod.GET)
- @RequestMapping(value="/publishOperatorHomePage", method=RequestMethod.GET)
- @RequestMapping(value="/getRegionTree", method=RequestMethod.GET)
- @RequestMapping(value="/getRegionProduct", method=RequestMethod.GET)
- @RequestMapping(value="/saveOrUpdateRegionProduct", method=RequestMethod.POST)
- @RequestMapping(value="/getRegionSendPackage", method=RequestMethod.GET)
- @RequestMapping(value="/saveOrUpdateRegionPackage", method=RequestMethod.POST)

## SocialFetchRecordController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/SocialFetchRecordController.java`
- @RequestMapping(value = "socialFetchRecord.html", method = { RequestMethod.POST })
- @RequestMapping(value = "/socialFetchRecordList", method = { RequestMethod.GET })

## WaterReportOrderDetailController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportOrderDetailController.java`
- @RequestMapping(value = "orderDetail.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/orderDetailList", method = { RequestMethod.GET })
- @RequestMapping(value = "totalShow", method = { RequestMethod.GET})
- @RequestMapping(value = {"/exportOrderDetail"}, method = {RequestMethod.GET})

## WaterReportDirectorGoalController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportDirectorGoalController.java`
- @RequestMapping(value = "directorGoal.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/directorList", method = { RequestMethod.GET })
- @RequestMapping(value = "/importDirectorGoal")

## WaterReportController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportController.java`
- @RequestMapping(value ="/experiencestore.html")
- @RequestMapping("/waterDispenserList")
- @RequestMapping("/getCardSum")
- @RequestMapping("/getDispenserDetail")
- @RequestMapping("/waterDispenserMapList")
- @RequestMapping(value ="/dispenserReportChart.html")
- @RequestMapping(value ="/dispenserCount.html")
- @RequestMapping(value = "/dispenserInfoReport.html", method = {RequestMethod.GET})
- @RequestMapping(value = "/waterDispenserInfo", method = RequestMethod.POST)
- @RequestMapping(value = "/waterSampleInfo.html", method = RequestMethod.GET)
- @RequestMapping(value = "/waterSubCenterInfoMap.html")
- @RequestMapping(value = "/waterSubCenterInfo.html")
- @RequestMapping(value = "/getWaterSubCenterInfoByDataType")
- @RequestMapping(value = "/cardDetail.html", method = RequestMethod.GET)

## WaterReportFetchUnitPriceController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportFetchUnitPriceController.java`
- @RequestMapping(value = "fetchUnitPrice.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/getPrice", method = { RequestMethod.GET })
- @RequestMapping(value = "/editPrice", method = { RequestMethod.POST })

## WaterReportNetLiveController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportNetLiveController.java`
- @RequestMapping(value = "/netLiveScreen.html", method = RequestMethod.GET)
- @RequestMapping(value="/netLiveScreen.do", method = RequestMethod.GET)
- @RequestMapping(value="/lottory", method = RequestMethod.GET)
- @RequestMapping(value="/getMobile", method = RequestMethod.GET)
- @RequestMapping(value = "netLive.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/netLiveList", method = { RequestMethod.GET })
- @RequestMapping(value = "/updateNetLive", method = { RequestMethod.POST })

## WaterCardController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterCardController.java`
- @RequestMapping(value = "waterCard.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/cardList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportCard", method = { RequestMethod.GET })
- @RequestMapping(value = "yearCard.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/yearCardList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportYearCard", method = { RequestMethod.GET })
- @RequestMapping(value = "/smsLogsList", method = { RequestMethod.GET })
- @RequestMapping(value = "/getWaterCardById", method = RequestMethod.GET)
- @RequestMapping(value = "/updateWaterCard", method = { RequestMethod.POST })
- @RequestMapping(value = "/waterCardChangeLogList", method = { RequestMethod.GET })
- @RequestMapping(value = "/reissueNewWaterCard", method = { RequestMethod.POST })
- @RequestMapping(value = "waterCardManager.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/cardManagerList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportCardManager", method = { RequestMethod.GET })

## WaterReportOperatorDailyCountyController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportOperatorDailyCountyController.java`
- @RequestMapping(value="/operatorDailyCounty.html", method = RequestMethod.GET)
- @RequestMapping(value = {"/exportOperatorDailyCounty.html"}, method = {RequestMethod.GET})

## WaterNewSubCenterLossCostImportController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterNewSubCenterLossCostImportController.java`
- @RequestMapping(value = "newSubCenterLossCost.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/newSubCenterLossCostList", method = { RequestMethod.GET })
- @RequestMapping(value = "/importNewSubCenterLossCost")

## WaterReportPointsOperatorController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportPointsOperatorController.java`
- @RequestMapping(value="reportPoint")
- @RequestMapping(value = "index.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/list", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportList", method = { RequestMethod.GET })
- @RequestMapping(value = "indexHistory.html", method = { RequestMethod.GET})

## WaterReportContactThreeCleanController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportContactThreeCleanController.java`
- @RequestMapping(value = "/waterReportContactThreeClean.html", method = RequestMethod.GET)
- @RequestMapping(value = {"/exportContactThreeClean.html"}, method = {RequestMethod.GET})

## WaterSampleCountyAdIncomeImportController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterSampleCountyAdIncomeImportController.java`
- @RequestMapping(value = "sampleCountyAdIncome.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/sampleCountyAdIncomeList", method = { RequestMethod.GET })
- @RequestMapping(value = "/importSampleCountyAdIncome")

## WaterSgOrderController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterSgOrderController.java`
- @RequestMapping(value = "sgOrder.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/sgOrderList", method = { RequestMethod.GET })
- @RequestMapping(value = "/importSgOrder")

## WaterVatInvoiceController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterVatInvoiceController.java`
- @RequestMapping(value = { "waterVatInvoiceList.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "findWaterVatInvoiceList.html" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "checkWaterVatInvoiceLicence.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "auditWaterVatInvoice.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = {"auditVatInvoice"}, method = { RequestMethod.GET })
- @RequestMapping(value = { "/exportWaterVatInvoiceList.html" })
- @RequestMapping(value = { "waterVatInvoiceExpressList.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "findVatInvoiceExpressList.html" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "saveVatInvoiceExpressInput.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/exportVatInvoiceExpressList.html" })

## LnAppRegisterReportController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/LnAppRegisterReportController.java`
- @RequestMapping(value = "lnAppRegisterReport.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/lnAppRegisterReportList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportLnAppRegisterReport", method = { RequestMethod.GET })

## UploadPhotoController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/UploadPhotoController.java`
- @RequestMapping("/ueditor")
- @RequestMapping
- @RequestMapping(value = "/upload", method = RequestMethod.GET)
- @RequestMapping(value = "/upload", method = RequestMethod.POST)

## WaterOperatorAdvertController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterOperatorAdvertController.java`
- @RequestMapping(value ="/waterOperatorAdvert")
- @RequestMapping(value = "index.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/list.do", method = { RequestMethod.GET })
- @RequestMapping(value = "/shopList.do", method = { RequestMethod.GET })
- @RequestMapping(value ="/addOrUpdate.do")
- @RequestMapping(value ="/getDetail.do")
- @RequestMapping(value ="/delete.do")

## WaterDispenserHomePageController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterDispenserHomePageController.java`
- @RequestMapping(value ="/dispenserHomePage.html")
- @RequestMapping(value = "/saveOrUpdateAdvertisement", method = RequestMethod.POST)
- @RequestMapping(value = "/saveOrUpdateTopLine", method = RequestMethod.POST)
- @RequestMapping(value = "/saveOrUpdateDailySpecial", method = RequestMethod.POST)
- @RequestMapping(value = "/saveOrUpdateRecommend", method = RequestMethod.POST)
- @RequestMapping(value = "/uploadAppImage", method = RequestMethod.POST)
- @RequestMapping(value="/editAd", method=RequestMethod.GET)
- @RequestMapping(value="/editTl", method=RequestMethod.GET)
- @RequestMapping(value="/editDs", method=RequestMethod.GET)
- @RequestMapping(value="/editRecommend", method=RequestMethod.GET)
- @RequestMapping(value="/publishHomePage", method=RequestMethod.GET)

## WaterReportBranchDailyGoalImportController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportBranchDailyGoalImportController.java`
- @RequestMapping(value = "branchDailyGoal.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/branchDailyGoalList", method = { RequestMethod.GET })
- @RequestMapping(value = "/importBranchDailyGoal")

## WaterReportSmallDetailController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportSmallDetailController.java`
- @RequestMapping(value = "/smallDetail.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/queryDetailList", method = { RequestMethod.GET })
- @RequestMapping(value = "/selectCenter", method = { RequestMethod.GET })
- @RequestMapping(value = "/selectProvince", method = { RequestMethod.GET })
- @RequestMapping(value = "/addSmallDetail", method = { RequestMethod.POST })
- @RequestMapping(value = "/delete", method = { RequestMethod.POST })

## WaterCommunityCommentComplainController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterCommunityCommentComplainController.java`
- @RequestMapping(value = "waterCommunityCommentComplain.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/communityCommentComplainList", method = { RequestMethod.GET })
- @RequestMapping(value = "/auditWaterCommunityCommentComplain", method = { RequestMethod.POST })

## WaterDispenserAdvertPlayController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterDispenserAdvertPlayController.java`
- @RequestMapping("/waterDispenserAdvertPlay.html")
- @RequestMapping("/waterDispenserAdvertPlayList")
- @RequestMapping("/waterDispenserAdvertPlayAdd")
- @RequestMapping("/waterDispenserAdvertPlayUpdate")
- @RequestMapping("/waterDispenserAdvertPlayDetail")
- @RequestMapping("/waterDispenserAdvertPlayDelete")

## WaterCommentController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterCommentController.java`
- @RequestMapping(value = "waterComment.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/waterCommentList", method = { RequestMethod.GET })
- @RequestMapping(value = "/commentOperate", method = { RequestMethod.POST })
- @RequestMapping(value = "/exportComment", method = { RequestMethod.GET })

## WaterReportFilterWarningDetailController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportFilterWarningDetailController.java`
- @RequestMapping(value = "waterReportFilterWarningDetail.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/waterReportFilterWarningDetailList", method = { RequestMethod.GET })

## WaterDispenserRepairController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterDispenserRepairController.java`
- @RequestMapping("/dispenser/repair")
- @RequestMapping(value = "list.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/list", method = { RequestMethod.GET })
- @RequestMapping(value = "/detail", method = RequestMethod.GET)
- @RequestMapping(value = "/list/export", method = { RequestMethod.GET })
- @RequestMapping(value = {"/importDispenserRepairsView.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importDispenserRepairs.html"})
- @RequestMapping(value = {"/downloadDispenserRepairsTemplate.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = "/parts/list", method = { RequestMethod.GET })

## WaterReportWarningController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportWarningController.java`
- @RequestMapping(value = "/waterReportWarning.html", method = RequestMethod.GET)

## WaterDispenserAgentRequestController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterDispenserAgentRequestController.java`
- @RequestMapping(value = "waterAgentRequest.html", method = { RequestMethod.GET})
- @RequestMapping(value = "waterAgentRequestWaitFee.html", method = { RequestMethod.GET})
- @RequestMapping(value = "waterAgentRequestPassed.html", method = { RequestMethod.GET})
- @RequestMapping(value = "waterAgentRequestOperations.html", method = { RequestMethod.GET})
- @RequestMapping(value = "waterAgentRequestWaitConfirm.html", method = { RequestMethod.GET})
- @RequestMapping(value = "waitReceive.html", method = { RequestMethod.GET })
- @RequestMapping(value = "operationsFull.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/agentOperatorList", method = { RequestMethod.GET })
- @RequestMapping(value = "/operateConfirmList", method = { RequestMethod.GET })
- @RequestMapping(value = "/agentRequestList", method = { RequestMethod.GET })
- @RequestMapping(value =  "/importDispenser" )
- @RequestMapping(value = "/deleteImpDispenser", method = { RequestMethod.POST })
- @RequestMapping(value = "/batchGenerateDepositNo", method = { RequestMethod.POST })
- @RequestMapping(value = "/batchGenerateOperator", method = { RequestMethod.POST })
- @RequestMapping(value = "/generateOperatorAndCreateOrders", method = { RequestMethod.POST })
- @RequestMapping(value = "/editRequest", method = RequestMethod.GET)
- @RequestMapping(value = "/updateRequest", method = { RequestMethod.POST })
- @RequestMapping(value = "/updatePrice", method = { RequestMethod.POST })
- @RequestMapping(value = "/auditAgentRequest", method = { RequestMethod.POST })

## WarningDetailController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WarningDetailController.java`
- @RequestMapping(value="warningDetail.html", method={RequestMethod.GET})
- @RequestMapping(value="warningDetailList", method={RequestMethod.GET})
- @RequestMapping(value = "/exportWarningDetail", method = { RequestMethod.GET })

## WaterPostMessagesController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterPostMessagesController.java`
- @RequestMapping(value = "waterPostMessages.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/postMessagesList", method = { RequestMethod.GET })
- @RequestMapping(value = "/addPostMessages", method = { RequestMethod.POST })
- @RequestMapping(value = "/updatePostMessages", method = { RequestMethod.POST })
- @RequestMapping(value = "/updateMessagesReply", method = { RequestMethod.POST })
- @RequestMapping(value = "/updateMessagesRemak", method = { RequestMethod.POST })
- @RequestMapping(value = "showApplyDetail.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/messagesReplyList", method = { RequestMethod.GET })
- @RequestMapping(value = "/uploadMessageImage", method = RequestMethod.POST)
- @RequestMapping(value = "/stickMessages", method = { RequestMethod.POST })

## BusinessApplyController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/BusinessApplyController.java`
- @RequestMapping(value = "businessApply.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/businessApplyList", method = { RequestMethod.GET })
- @RequestMapping(value = "/auditBusinessApply", method = { RequestMethod.POST })
- @RequestMapping(value = "/uploadZip", method = RequestMethod.POST)

## LnKpiSourceController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/LnKpiSourceController.java`
- @RequestMapping(value = "lnKpiSource.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/lnKpiSourceList", method = { RequestMethod.GET })
- @RequestMapping(value = {"/exportLnKpiSource.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = "/importLnKpiSource")

## WaterReportDispenserFlowController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportDispenserFlowController.java`
- @RequestMapping(value = "/dispenserFlow.html")
- @RequestMapping(value = {"/exportFlow.html"}, method = {RequestMethod.GET})

## WaterReportOperatorNetTransactionController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportOperatorNetTransactionController.java`
- @RequestMapping(value = "/waterReportOperatorNetTransaction.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/waterReportOperatorNetTransactionList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportOperatorNetTrans", method = { RequestMethod.GET })

## WaterSubCenterLossCostImportController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterSubCenterLossCostImportController.java`
- @RequestMapping(value = "subCenterLossCost.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/subCenterLossCostList", method = { RequestMethod.GET })
- @RequestMapping(value = "/importSubCenterLossCost")

## WaterReportOperatorNetController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportOperatorNetController.java`
- @RequestMapping(value="/branchNetSum.html", method = RequestMethod.GET)
- @RequestMapping(value = {"/exportBranchNetSum.html"}, method = {RequestMethod.GET})

## HaierRecruitProcessController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/HaierRecruitProcessController.java`
- @RequestMapping(value = "haierRecruitProcess.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/haierRecruitProcessList", method = { RequestMethod.GET })
- @RequestMapping(value = "/batchOperation", method = { RequestMethod.POST })
- @RequestMapping(value = "/commissionBack", method = { RequestMethod.POST })
- @RequestMapping(value = "/exportHaierRecruitProcess", method = { RequestMethod.GET })

## WaterReportInstallOperationController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportInstallOperationController.java`
- @RequestMapping(value = "/dispenserInstallOperation.html")

## WaterReportSalaryAreaController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportSalaryAreaController.java`
- @RequestMapping(value = "/waterSalaryAreaInfo.html", method = RequestMethod.GET)
- @RequestMapping(value = {"/exportSalaryArea.html"}, method = {RequestMethod.GET})

## WaterPointProductsController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterPointProductsController.java`
- @RequestMapping(value = "pointProduct.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/pointProductList", method = { RequestMethod.GET })
- @RequestMapping(value = "addPointProduct.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/newPointProduct", method = { RequestMethod.POST })
- @RequestMapping(value = "updatePointProduct.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/updatePointProduct", method = { RequestMethod.POST })
- @RequestMapping(value = "/updatePointProductStatus", method = { RequestMethod.POST })
- @RequestMapping(value = "/uploadPointProductImage", method = RequestMethod.POST)
- @RequestMapping(value = "pointProductOrder.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/pointProductOrderList", method = { RequestMethod.GET })
- @RequestMapping(value = "/updateOrderShipStatus", method = { RequestMethod.POST })
- @RequestMapping(value = "pointListPage.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/pointList", method = { RequestMethod.GET })
- @RequestMapping(value = "pointItemListPage.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/pointItemList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportOperatorPointList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportProductOrderList", method = { RequestMethod.GET })

## HaierRecruitApplyController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/HaierRecruitApplyController.java`
- @RequestMapping(value = "haierRecruitApply.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/haierRecruitApplyList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportHaierRecruitApply", method = { RequestMethod.GET })
- @RequestMapping(value = "/importApplyList")
- @RequestMapping(value = "/deleteRecords", method = { RequestMethod.POST })

## WaterReportNetContactMapMonitoringController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportNetContactMapMonitoringController.java`
- @RequestMapping(value = "/dispenserNetContactMonitoringChart.html", method = RequestMethod.GET)
- @RequestMapping(value="/showNetContactBranchInfo", method=RequestMethod.GET)

## WaterCommonController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterCommonController.java`
- @RequestMapping("/common")
- @RequestMapping(value = "/uploadImage", method = RequestMethod.POST)

## WaterDispenserAdvertCheckinfoController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterDispenserAdvertCheckinfoController.java`
- @RequestMapping("/waterDispenserAdvertCheckinfo.html")
- @RequestMapping("/waterDispenserAdvertCheckinfoList")

## FlowableUserConfigController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/FlowableUserConfigController.java`
- @RequestMapping(value = "flowableUserConfig.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/flowableUserConfigList", method = { RequestMethod.GET })
- @RequestMapping(value = "/saveFlowableUserConfig", method = { RequestMethod.POST })
- @RequestMapping(value = "/updateFlowableUserConfig", method = { RequestMethod.POST })
- @RequestMapping(value = "/removeFlowableUserConfig", method = { RequestMethod.POST })

## WaterReportThreeDegreeDailyCountyController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportThreeDegreeDailyCountyController.java`
- @RequestMapping(value="/threeDegreeDailyCounty.html", method = RequestMethod.GET)
- @RequestMapping(value = {"/exportThreeDegreeDailyCounty.html"}, method = {RequestMethod.GET})

## ServiceStationController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/ServiceStationController.java`
- @RequestMapping(value = "serviceStationHeadquarters.html", method = { RequestMethod.GET })
- @RequestMapping(value = "serviceStationSubcenter.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/serviceStationList", method = { RequestMethod.GET })
- @RequestMapping(value = "/auditServiceStation", method = { RequestMethod.POST })

## WaterActivityTimesImportController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterActivityTimesImportController.java`
- @RequestMapping(value = "activityTimes.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/activityTimesList", method = { RequestMethod.GET })
- @RequestMapping(value = "/importActivityTimes")
- @RequestMapping(value = "/exportActivityTimes", method = { RequestMethod.GET })

## WaterReportDirectorGoalNewController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportDirectorGoalNewController.java`
- @RequestMapping(value = "directorGoalNew.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/directorNewList", method = { RequestMethod.GET })
- @RequestMapping(value = "/importDirectorGoalNew")

## WaterDispenserAdvertController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterDispenserAdvertController.java`
- @RequestMapping("/waterDispenserAdvert.html")
- @RequestMapping("/waterDispenserAdvertList")
- @RequestMapping("/waterDispenserAdvertSaveOrUpdate")
- @RequestMapping("/waterDispenserAdvertDelete")

## WaterReportSalaryController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportSalaryController.java`
- @RequestMapping(value = "/waterSalaryInfo.html", method = RequestMethod.GET)
- @RequestMapping(value = "/waterSalaryFetchInfo.html", method = RequestMethod.GET)
- @RequestMapping(value = {"/exportSalary.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = "/subCenterSalary.html", method = RequestMethod.GET)
- @RequestMapping(value = "/subCenterSalaryInfo", method = RequestMethod.GET)
- @RequestMapping(value = "/getSubCenterList", method = RequestMethod.GET)

## WaterReportSubCenterGoalController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportSubCenterGoalController.java`
- @RequestMapping(value = "subCenterCountyGoal.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/subCenterCountyList", method = { RequestMethod.GET })
- @RequestMapping(value = "/importSubCenterCountyGoal")

## BackCategoryChangeController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/BackCategoryChangeController.java`
- @RequestMapping(value = "backCategory.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/categoryAdd", method = RequestMethod.GET)
- @RequestMapping(value = "/categoryDel", method = RequestMethod.GET)
- @RequestMapping(value = "/categoryUpdate", method = RequestMethod.GET)
- @RequestMapping(value = "/category/{key}", method = RequestMethod.GET)

## WaterReportSampleSalaryController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportSampleSalaryController.java`
- @RequestMapping(value = "/waterSampleSalaryInfo.html", method = RequestMethod.GET)
- @RequestMapping(value = "/waterSampleSalaryFetchInfo.html", method = RequestMethod.GET)
- @RequestMapping(value = {"/exportSampleSalary.html"}, method = {RequestMethod.GET})

## WaterReportFreeOrderGoalController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportFreeOrderGoalController.java`
- @RequestMapping(value = "freeOrderGoal.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/freeOrderGoalList", method = { RequestMethod.GET })
- @RequestMapping(value = "/importFreeOrderGoal")

## WaterReportThreeDegreeDailyCountyGoalController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportThreeDegreeDailyCountyGoalController.java`
- @RequestMapping(value = "waterReportThreeDegreeDailyCountyGoal.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/threeDegreeDailyCountyGoalList", method = { RequestMethod.GET })
- @RequestMapping(value = "/importThreeDegreeDailyCountyGoal")

## WaterReportOperationCenterController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportOperationCenterController.java`
- @RequestMapping(value="/operationCenter.html", method = RequestMethod.GET)
- @RequestMapping(value = {"/exportOerationCenter.html"}, method = {RequestMethod.GET})

## WaterOfflineTrainingActivityController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterOfflineTrainingActivityController.java`
- @RequestMapping(value = "waterOfflineTrainingActivity.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/waterOfflineTrainingActivityList", method = { RequestMethod.GET })
- @RequestMapping(value = "addWaterOfflineTrainingActivity.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/newWaterOfflineTrainingActivity", method = { RequestMethod.POST })
- @RequestMapping(value = "/updateWaterOfflineTrainingActivity", method = { RequestMethod.POST })
- @RequestMapping(value = "/downloadOfflineTrainingTwoDimensionCode", method = { RequestMethod.GET })
- @RequestMapping(value = "/waterOfflineTrainingOperatorList", method = { RequestMethod.GET })
- @RequestMapping(value = "/uploadOfflineTrainingMaterial", method = { RequestMethod.POST })

## WaterSampleCountyLossCostImportController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterSampleCountyLossCostImportController.java`
- @RequestMapping(value = "sampleCountyLossCost.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/sampleCountyLossCostList", method = { RequestMethod.GET })
- @RequestMapping(value = "/importSampleCountyLossCost")

## WaterReportSmallMicroController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportSmallMicroController.java`
- @RequestMapping(value="/smallMicro.html", method = RequestMethod.GET)
- @RequestMapping(value ="/smallMicroDayChart.html")
- @RequestMapping(value ="/smallMicroMonthChart.html")

## WaterReportAgentInfoController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportAgentInfoController.java`
- @RequestMapping(value = "waterReportAgent.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/waterReportAgentList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportReportAgent", method = { RequestMethod.GET })

## FlowableConfigController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/FlowableConfigController.java`
- @RequestMapping(value = "flowableConfig.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "/flowableConfigList", method = { RequestMethod.GET })
- @RequestMapping(value = "/saveFlowableConfig", method = { RequestMethod.POST })
- @RequestMapping(value = "/getFlowableQuesType", method = RequestMethod.GET)

## WaterDispenserRepairHccController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterDispenserRepairHccController.java`
- @RequestMapping("/repair/hcc")
- @GetMapping("list.html")
- @GetMapping("page.do")
- @GetMapping(value = "/export.do")

## WaterArticleController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterArticleController.java`
- @RequestMapping(value = "waterArticle.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/articleList", method = { RequestMethod.GET })
- @RequestMapping(value = "addArticle.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/newArticle", method = { RequestMethod.POST })
- @RequestMapping(value = "/saveArticle", method = { RequestMethod.POST })
- @RequestMapping(value = "updateArticle.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/updateArticle", method = { RequestMethod.POST })
- @RequestMapping(value = "/deleteArticle", method = { RequestMethod.POST })
- @RequestMapping(value = {"/prewArticle"},method = RequestMethod.POST)
- @RequestMapping(value = "prewArticleDetail.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/uploadArticleImage", method = RequestMethod.POST)
- @RequestMapping(value = "/uploadArticleHeadImage", method = RequestMethod.POST)
- @RequestMapping(value = "/uploadArticleHorizontalImage", method = RequestMethod.POST)

## WaterSampleCountyEcologicalIncomeImportController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterSampleCountyEcologicalIncomeImportController.java`
- @RequestMapping(value = "sampleCountyEcologicalIncome.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/sampleCountyEcologicalIncomeList", method = { RequestMethod.GET })
- @RequestMapping(value = "/importSampleCountyEcologicalIncome")

## LnEhrKpiController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/LnEhrKpiController.java`
- @RequestMapping(value="/lnEhrKpi.html", method = RequestMethod.GET)
- @RequestMapping(value="/lnEhrKpiRate.html", method = RequestMethod.GET)
- @RequestMapping(value="/lnEhrKpiList", method = RequestMethod.GET)
- @RequestMapping(value = "/exportKpiInfo", method = { RequestMethod.GET })
- @RequestMapping(value = "/importUpdateKpi")

## WaterReportOperatorUserTransactionController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportOperatorUserTransactionController.java`
- @RequestMapping(value="/waterReportOperatorUserTransaction.html", method={RequestMethod.GET})
- @RequestMapping(value="/waterReportOperatorUserTransactionList", method={RequestMethod.GET})
- @RequestMapping(value = {"/exportOperatorUserTrans"}, method = {RequestMethod.GET})

## WaterCommunityManageController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterCommunityManageController.java`
- @RequestMapping(value = "waterCommunityManage.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/communityManageList", method = { RequestMethod.GET })
- @RequestMapping(value = "/updateCommunityManage", method = { RequestMethod.POST })
- @RequestMapping(value = "showCommunityCommentDetail.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/communityManageCommentList", method = { RequestMethod.GET })
- @RequestMapping(value = "showCommunityReplyDetail.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/communityManageReplyList", method = { RequestMethod.GET })
- @RequestMapping(value = "/updateCommunityManageComment", method = { RequestMethod.POST })
- @RequestMapping(value = "/updateCommunityManageReply", method = { RequestMethod.POST })
- @RequestMapping(value = "/batchHide", method = { RequestMethod.POST })
- @RequestMapping(value = "/getWaterCommunityMessagesById", method = RequestMethod.GET)
- @RequestMapping(value = "/stickCommunityMessages", method = { RequestMethod.POST })
- @RequestMapping(value = "/cancelStickCommunityMessages", method = { RequestMethod.POST })
- @RequestMapping(value = "/jpCommunityMessages", method = { RequestMethod.POST })
- @RequestMapping(value = "/cancelJpCommunityMessages", method = { RequestMethod.POST })

## SocialAgentController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/SocialAgentController.java`
- @RequestMapping(value = "socialAgent.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/socialAgentList", method = { RequestMethod.GET })
- @RequestMapping(value = "/auditSocialAgentPass", method = { RequestMethod.POST })
- @RequestMapping(value = "/auditSocialAgentReject", method = { RequestMethod.POST })
- @RequestMapping(value = "/viewSocialAgentContract", method = { RequestMethod.GET })
- @RequestMapping(value = "/judgeSocialAgentContract", method = { RequestMethod.GET })

## WaterReportCommissionStatisController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportCommissionStatisController.java`
- @RequestMapping(value="/waterReportCommissionStatistics.html", method = RequestMethod.GET)
- @RequestMapping(value = {"/exportReportCommissionStatistics"}, method = {RequestMethod.GET})

## WaterReportLnBranchDailyGoalController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportLnBranchDailyGoalController.java`
- @RequestMapping(value = "waterReportLnBranchDailyGoal.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/lnBranchDailyGoalList", method = { RequestMethod.GET })
- @RequestMapping(value = "/importLnBranchDailyGoal")

## WaterReportCountyCenterOperationsController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportCountyCenterOperationsController.java`
- @RequestMapping(value="/waterReportCountyCenterOperations.html", method={RequestMethod.GET})
- @RequestMapping(value="/waterReportCountyCenterOperationsList", method={RequestMethod.GET})
- @RequestMapping(value = {"/exportCountyCenterOperations"}, method = {RequestMethod.GET})

## WaterReportDispenserVendorReceiptController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportDispenserVendorReceiptController.java`
- @RequestMapping(value = "dispenserVendorReceipt.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/dispenserVendorReceiptList", method = { RequestMethod.GET })

## YtWaterCommentReplyController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/YtWaterCommentReplyController.java`
- @RequestMapping(value = "ytWaterReplyComment.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/ytWaterCommentReplyList", method = { RequestMethod.GET })
- @RequestMapping(value = "/addReplyContent", method = { RequestMethod.POST })

## CxwCleanOrderManagementController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/CxwCleanOrderManagementController.java`
- @RequestMapping(value = "cxwCxwCleanOrderManagement.html", method = { RequestMethod.GET })
- @RequestMapping(value="/cxwCleanOrderList", method = { RequestMethod.GET})
- @RequestMapping(value = "/exportCxwCleanOrder", method = { RequestMethod.GET })

## WaterConfigController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterConfigController.java`
- @RequestMapping("/config")
- @RequestMapping(value = "/waterConfigList.html", method = { RequestMethod.GET })
- @RequestMapping(value="/getWaterConfigList.do",method = {RequestMethod.POST})
- @RequestMapping(value = "/uploadImage.do", method = RequestMethod.POST)
- @RequestMapping(value="/save.do",method = {RequestMethod.POST})
- @RequestMapping(value="/status.do",method = {RequestMethod.POST})
- @RequestMapping(value="/update.do",method = {RequestMethod.POST})

## WaterVillageInteractionActivityController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterVillageInteractionActivityController.java`
- @RequestMapping(value = "waterVillageInteractionActivity.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/waterVillageInteractionActivityList", method = { RequestMethod.GET })
- @RequestMapping(value = "addWaterVillageInteractionActivity.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/newWaterVillageInteractionActivity", method = { RequestMethod.POST })
- @RequestMapping(value = "/updateWaterVillageInteractionActivity", method = { RequestMethod.POST })
- @RequestMapping(value = "/waterVillageInteractionOperatorList", method = { RequestMethod.GET })

## ServiceAutoAgentOperatorRecordController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/ServiceAutoAgentOperatorRecordController.java`
- @RequestMapping(value = "serviceAutoAgentOperatorRecord.html", method = { RequestMethod.GET, RequestMethod.POST })
- @RequestMapping(value = "serviceAutoAgentOperatorRecordList.do", method = { RequestMethod.GET})
- @RequestMapping(value="/serviceAutoAgentOperatorRecordCreate.do",method = { RequestMethod.POST })
- @RequestMapping(value="/serviceAutoAgentOperatorRecordBack.do",method = { RequestMethod.POST })

## WaterReportAgentOperationsController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportAgentOperationsController.java`
- @RequestMapping(value = "waterReportAgentOperations.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/waterReportAgentOperationsList", method = { RequestMethod.GET })
- @RequestMapping(value = "/exportReportAgentOperations", method = { RequestMethod.GET })

## WaterActivityController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterActivityController.java`
- @RequestMapping(value = "waterActivity.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/activityList", method = { RequestMethod.GET })
- @RequestMapping(value = "/invalid", method = { RequestMethod.POST })
- @RequestMapping(value = "addActivity.html", method = { RequestMethod.GET})
- @RequestMapping(value = "/uploadImage", method = RequestMethod.POST)
- @RequestMapping(value = "/newActivity", method = { RequestMethod.POST })
- @RequestMapping(value = "/viewActivity", method = { RequestMethod.GET })
- @RequestMapping("/toLnPayFlag.html")
- @RequestMapping(value = "/queryCountLnPayFlag", method = { RequestMethod.POST })
- @RequestMapping(value = "/addLnPayFlag", method = { RequestMethod.POST })
- @RequestMapping(value = "/checkMemberIdByMobile", method = { RequestMethod.POST })

## WaterDispenserManagerWalletController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterDispenserManagerWalletController.java`
- @RequestMapping(value = "waterDispenserManagerWallet.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/waterDispenserManagerWalletRecord", method = { RequestMethod.GET })
- @RequestMapping(value = "waterDispenserManagerWalletTransfer.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/sendCheckCode", method = { RequestMethod.POST })
- @RequestMapping(value = "/confirmTransfer", method = { RequestMethod.POST })

## WaterReportBranchDailyController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/dispenser/WaterReportBranchDailyController.java`
- @RequestMapping(value="/branchDaily.html", method = RequestMethod.GET)
- @RequestMapping(value = {"/exportBranchDaily.html"}, method = {RequestMethod.GET})

## ExportAgentController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/water/ExportAgentController.java`
- @RequestMapping(value = "/exportAgent")
- @RequestMapping(value = "pdf", method = { RequestMethod.GET,RequestMethod.POST })

## walletDisplayController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/water/walletDisplayController.java`
- @RequestMapping(value = "/wallet")
- @RequestMapping(value = { "walletList.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/checkStatus.do" }, method = { RequestMethod.GET })
- @RequestMapping(value="/walletDisplayList.do",method={ RequestMethod.POST })
- @RequestMapping(value = { "/updateStatus.do" }, method = { RequestMethod.GET })
- @RequestMapping(value="/add.do",method={ RequestMethod.GET })

## ExportController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/water/ExportController.java`
- @RequestMapping(value = "/export")
- @RequestMapping(value = "pdf", method = { RequestMethod.GET,RequestMethod.POST })

## WaterProductController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/water/WaterProductController.java`
- //    @RequestMapping(value = { "tagProductList.html" }, method = { RequestMethod.GET })
- //    @RequestMapping(value = { "findTagProductList.html" }, method = { RequestMethod.POST })
- //    @RequestMapping(value = { "getTagProduct.html" }, method = { RequestMethod.GET })
- //    @RequestMapping(value = { "saveTagProduct.html" }, method = { RequestMethod.GET })

## ActivityController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/app/ActivityController.java`
- @RequestMapping(value = "/chemicalFertilizer.html", method = {RequestMethod.GET})
- @RequestMapping(value = "/showActivityList.html", method = {RequestMethod.POST})
- @RequestMapping(value = "/getRegions", method = RequestMethod.GET)
- @RequestMapping(value = "/getCities", method = RequestMethod.GET)

## ToiletController
- 文件: `cbs-web/src/main/java/com/haier/cbs/web/controller/app/ToiletController.java`
- @RequestMapping(value = "/showToiletList.html", method = {RequestMethod.POST})
- @RequestMapping(value = "/toiletRepair.html", method = {RequestMethod.GET})
- @RequestMapping(value = "/submitTextarea.html", method = {RequestMethod.POST})
- @RequestMapping(value = "/setStatus.html", method = {RequestMethod.POST})
- @RequestMapping(value = "/getImageUrl.html", method = {RequestMethod.POST})

## GlobalExceptionHandler
- 文件: `vpp-api-auth/vpp-biz/src/main/java/com/nahui/energy/handler/GlobalExceptionHandler.java`
- 未扫描到显式 Mapping 注解

## LoginController
- 文件: `vpp-api-auth/vpp-biz/src/main/java/com/nahui/energy/controller/LoginController.java`
- @RequestMapping("/login")
- @PostMapping("/login")

## TokenController
- 文件: `vpp-api-auth/vpp-biz/src/main/java/com/nahui/energy/controller/TokenController.java`
- @RequestMapping("/token")
- @PostMapping("/getVppToken")
- @PostMapping("/token-login")
- @DeleteMapping("logout")
- @PostMapping("refresh")
- @PostMapping("getLoginUser")
- @PostMapping("register")

## ZhongYinLeaseController
- 文件: `rrsjk-openapi-web/src/main/java/com/rrsjk/openapi/controller/zhongyin/ZhongYinLeaseController.java`
- @RequestMapping("/zhongyin")
- @PostMapping("/powerStationList")
- @PostMapping("/queryDailyGenerationSummary")

## ZhaoYinLeaseController
- 文件: `rrsjk-openapi-web/src/main/java/com/rrsjk/openapi/controller/zhaoyin/ZhaoYinLeaseController.java`
- @RequestMapping("/zhaoyin")
- @PostMapping("/api/v1/plant/daily-power")
- //    @PostMapping("/api/v1/inverter/real-time-power")
- @PostMapping("/api/v1/plant/status")
- @PostMapping("/api/v1/electricity/bill")

## SystemApplication
- 文件: `vpp-api-system/vpp-system-starter/src/main/java/com/nahui/energy/SystemApplication.java`
- 未扫描到显式 Mapping 注解

## I18nGlobalExceptionHandler
- 文件: `vpp-api-system/vpp-system-i18n/vpp-system-i18n-api/src/main/java/com/nahui/energy/config/I18nGlobalExceptionHandler.java`
- 未扫描到显式 Mapping 注解

## MybatisPlusGenerator
- 文件: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/utils/MybatisPlusGenerator.java`
- 未扫描到显式 Mapping 注解

## SystemExceptionHandler
- 文件: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/config/SystemExceptionHandler.java`
- 未扫描到显式 Mapping 注解

## EmailController
- 文件: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/EmailController.java`
- @PostMapping("/sendEmailCode")

## JasyptController
- 文件: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/JasyptController.java`
- @RequestMapping("/jasypt")
- @GetMapping("/encrypt")
- @GetMapping("/decrypt")

## TokenController
- 文件: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/TokenController.java`
- @RequestMapping("/token")
- @PostMapping("/getVppToken")
- @PostMapping("/token-login")
- @PostMapping("/token-nonce-login")
- @PostMapping("/token-nonce-init")
- @PostMapping("/SSO-login")
- @PostMapping("/boundUser")
- @GetMapping("/getIdmTokenAndUserInfo")
- @GetMapping("/getIdmToken")
- @PostMapping("getTokenByIdmToken")
- @DeleteMapping("logout")
- @PostMapping("refresh")
- @PostMapping("getLoginUser")
- @PostMapping("findUserByUserTenantId")

## OssController
- 文件: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/oss/OssController.java`
- @RequestMapping("/oss/")
- @PostMapping("/signature")
- @PostMapping("upload")
- @PostMapping("uploadByUrl")

## SysI18nResourceController
- 文件: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/i18n/SysI18nResourceController.java`
- @RequestMapping("/i18n")
- @PostMapping("/add")
- @PostMapping("/change")
- @PostMapping("/removeByKey")
- @GetMapping("/queryByPage")
- @PostMapping("/refresh")
- @GetMapping("/queryTagsByResourceKey")
- @GetMapping("/queryTagsByResourceKeys")
- @GetMapping("/queryTags")
- @GetMapping("/queryById")
- @GetMapping("/getAllResourceByLanguageCodeAndTag")
- @GetMapping("/getAllResource")
- @GetMapping("/getAllResourceToFrontEnd")
- @GetMapping("/getAllResourceByLanguageCodeToFrontEnd")
- @GetMapping("/getAllResourceByLanguageCode")
- @GetMapping("/getResource")
- @GetMapping("/getResources")
- @GetMapping("/getAllLanguage")
- @GetMapping("/exportI18n")
- @PostMapping(value = "/importI18n", consumes = MediaType.MULTIPART_FORM_DATA_VALUE)
- @PostMapping("/testI18nResourceVoResult")

## SysI18nTagLinkController
- 文件: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/i18n/SysI18nTagLinkController.java`
- @RequestMapping("/SysI18nTagLink")
- @PostMapping("/i18nResourceLinkTag")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")

## SysLanguageController
- 文件: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/i18n/SysLanguageController.java`
- @RequestMapping("/SysLanguage")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")

## SSOController
- 文件: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/sso/v1/SSOController.java`
- @RequestMapping("/SSO/v1")
- @PostMapping("/verify")
- @PostMapping("/findTokenUser")

## SysMenuController
- 文件: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/sys/SysMenuController.java`
- @RequestMapping("/menu")
- @GetMapping("/list")
- @GetMapping("/trees")
- @GetMapping("/treeSelect")
- @GetMapping(value = "/{menuId}")
- @PostMapping
- @PutMapping
- @DeleteMapping("/{menuId}")
- @GetMapping("getRouters")
- @GetMapping("getNoPortalRouters")
- @GetMapping("getPortalRouters")
- @GetMapping("/getPermsByUserId")
- @GetMapping("/findButton/{menuId}")
- @PostMapping("/saveButton")

## SysPortalController
- 文件: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/sys/SysPortalController.java`
- @RequestMapping("/SysPortal")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryAllPortal")
- @GetMapping("/queryById")
- @GetMapping("/queryUserPortalRouter")
- @GetMapping("/queryByMenuPath")

## SysDeptController
- 文件: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/sys/SysDeptController.java`
- @RequestMapping("/dept")
- @GetMapping("/list")
- @GetMapping(value = "/{deptId}")
- @GetMapping(value = "/deptName/{deptName}")
- @PostMapping
- @DeleteMapping("/{deptId}")
- @GetMapping("/treeSelect")
- @GetMapping("/loginTreeSelect")
- @GetMapping("/selectList")
- @GetMapping("/getCountryList")
- @GetMapping("/list/exclude/{deptId}")
- @PutMapping
- @GetMapping("/optionselect")

## SysPostController
- 文件: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/sys/SysPostController.java`
- @RequestMapping("/post")
- @GetMapping("/list")
- @PostMapping("/export")
- @GetMapping(value = "/{postId}")
- @PostMapping
- @PutMapping
- @DeleteMapping("/{postIds}")
- @GetMapping("/optionselect")

## SysRoleController
- 文件: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/sys/SysRoleController.java`
- @RequestMapping("/role")
- @GetMapping("/list")
- @GetMapping("/loginUserRole")
- @PostMapping("/export")
- @PutMapping
- @PutMapping("/changeStatus")
- @DeleteMapping("/{roleIds}")
- @GetMapping("/optionselectByRoleId")
- @GetMapping("/authUser/allocatedList")
- @GetMapping("/authUser/unallocatedList")
- @PutMapping("/authUser/cancel")
- @PutMapping("/authUser/cancelAll")
- @PutMapping("/authUser/selectAll")
- @GetMapping(value = "/deptTree/{roleId}")
- @GetMapping(value = "/{roleId}")
- @PostMapping
- @PutMapping("/dataScope")
- @GetMapping("/optionselect")
- @GetMapping("/findByRoleKey")

## SysOutSystemController
- 文件: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/sys/SysOutSystemController.java`
- @RequestMapping("/outSystem")
- @PostMapping("/apply")
- @PostMapping("/audit")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")

## SysConfigController
- 文件: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/sys/SysConfigController.java`
- @RequestMapping("/config")
- @GetMapping("/doList")
- @GetMapping("/list")
- @PostMapping("/export")
- @GetMapping(value = "/{configId}")
- @GetMapping(value = "/configKey/{configKey}")
- @PostMapping
- @PutMapping
- @DeleteMapping("/{configIds}")
- @DeleteMapping("/refreshCache")

## SysUserController
- 文件: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/sys/SysUserController.java`
- @RequestMapping("/user")
- @GetMapping("selectByUserName/{username}")
- @GetMapping("getUserInfo")
- @GetMapping("/list")
- @PostMapping("/export")
- @PostMapping(value = "/importData", consumes = MediaType.MULTIPART_FORM_DATA_VALUE)
- @PostMapping("/importTemplate")
- @PostMapping("changePassword")
- @GetMapping("/getInfo")
- @GetMapping(value = {"/", "/{userId}"})
- @PostMapping
- @PutMapping
- @DeleteMapping("/{userIds}")
- @GetMapping("/optionselect")
- @PutMapping("/resetPwd")
- @PutMapping("/changeStatus")
- @GetMapping("/authRole/{userId}")
- @PutMapping("/authRole")
- @GetMapping("/deptTree")
- @GetMapping("/list/dept/{deptId}")
- @PostMapping("register")
- @PostMapping("refreshToken")
- @PostMapping("switchTenant")

## SysRegionController
- 文件: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/sys/SysRegionController.java`
- @RequestMapping("/region")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById/{id}")
- @GetMapping("/queryByParentIdAndName")
- @GetMapping("/queryProvince")
- @GetMapping("/queryByParentId/{parentId}")

## SysTenantController
- 文件: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/sys/SysTenantController.java`
- @RequestMapping("/Tenant")
- @PostMapping("/add")
- @PostMapping("/change")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @GetMapping("/queryLoginTenant")
- @GetMapping("/queryNowTenant")
- @GetMapping("/queryAllTenantInfo")

## SysDictTypeController
- 文件: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/sys/SysDictTypeController.java`
- @RequestMapping("dict")
- @GetMapping
- @GetMapping("{dictType}")
- @GetMapping("listData")
- @GetMapping("i18n/{dictType}/all")
- @GetMapping("i18n/{dictType}")
- @PostMapping
- @PutMapping
- @DeleteMapping
- @DeleteMapping("deleteDictCache")

## SysDictDataController
- 文件: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/sys/SysDictDataController.java`
- @RequestMapping("/dict/Data")
- @GetMapping("{id}")
- @PostMapping
- @PutMapping
- @DeleteMapping

## GlobalExceptionHandler
- 文件: `vpp-api-template/vpp-biz/src/main/java/com/nahui/energy/handler/GlobalExceptionHandler.java`
- 未扫描到显式 Mapping 注解

## TestController
- 文件: `vpp-api-template/vpp-biz/src/main/java/com/nahui/energy/controller/TestController.java`
- @GetMapping("/test")

## TestController
- 文件: `vpp-api-km/vpp-km-biz/src/main/java/com/nahui/energy/controller/TestController.java`
- @GetMapping("/test")

## KnowledgeDirectoryController
- 文件: `vpp-api-km/vpp-km-biz/src/main/java/com/nahui/energy/controller/km/KnowledgeDirectoryController.java`
- @RequestMapping("/knowledgeDirectory")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @GetMapping("/queryPathById")
- @GetMapping("/querySubDirectoryAndFileById")
- @GetMapping("/trees")
- @GetMapping("/treeSelect")

## KnowledgeFileController
- 文件: `vpp-api-km/vpp-km-biz/src/main/java/com/nahui/energy/controller/km/KnowledgeFileController.java`
- @RequestMapping("/knowledgeFile")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @PostMapping("/edit")

## KnowledgeFileLogController
- 文件: `vpp-api-km/vpp-km-biz/src/main/java/com/nahui/energy/controller/km/KnowledgeFileLogController.java`
- @RequestMapping("/knowledgeFileLog")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")

## KnowledgeUserController
- 文件: `vpp-api-km/vpp-km-biz/src/main/java/com/nahui/energy/controller/km/KnowledgeUserController.java`
- @RequestMapping("/KnowledgeUser")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")
- @GetMapping("/queryCheckedByUserId")
- @PostMapping("/updateByUserId")

## KnowledgeFileMappingController
- 文件: `vpp-api-km/vpp-km-biz/src/main/java/com/nahui/energy/controller/km/KnowledgeFileMappingController.java`
- @RequestMapping("/knowledgeFileMapping")
- @PostMapping("/add")
- @PostMapping("/remove")
- @GetMapping("/queryByPage")
- @GetMapping("/queryById")

## GlobalExceptionResolver
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/security/shiro/GlobalExceptionResolver.java`
- 未扫描到显式 Mapping 注解

## GlobalExceptionHandler
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/util/GlobalExceptionHandler.java`
- 未扫描到显式 Mapping 注解

## IndexController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/IndexController.java`
- @RequestMapping("/")
- @RequestMapping(value = "index.html", method = { RequestMethod.GET })
- @RequestMapping(value="exception.html",method= {RequestMethod.GET})
- @RequestMapping(value = "head.html", method = { RequestMethod.GET })
- @RequestMapping(value = "menu.html", method = { RequestMethod.GET })
- @RequestMapping(value = "welcome.html", method = { RequestMethod.GET })

## LightAnnualScalePolicyController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/LightAnnualScalePolicyController.java`
- @RequestMapping("/annualScalePolicy")
- @RequestMapping("list.html")
- @RequestMapping("form.html")
- @RequestMapping("showDetail.html")
- @RequestMapping("datagrid.json")
- @RequestMapping("listEnable.json")
- @RequestMapping("getById.json")
- @RequestMapping("create.json")
- @RequestMapping("update.json")
- @RequestMapping("delete.json")
- @RequestMapping("changeStatus.json")
- @RequestMapping("stagingList.html")
- @RequestMapping("stagingDatagrid.json")
- @RequestMapping("monthlyList.html")
- @RequestMapping("monthlyDatagrid.json")
- @RequestMapping("monthlyDetail.html")
- @RequestMapping("monthlyDetail.json")
- @RequestMapping("autoCalculate.json")
- @RequestMapping("autoCalculateByMonth.json")
- @RequestMapping("realSettleList.html")
- @RequestMapping("confirmRealSettle.json")
- @RequestMapping("cancelMonthlyEstimate.json")
- @RequestMapping("reportList.html")
- @RequestMapping("reportDatagrid.json")
- @RequestMapping("monthlyExport.do")

## OssImageController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/OssImageController.java`
- @RequestMapping("/oss/image/")
- @RequestMapping(value = "upload.do", method = RequestMethod.POST)
- @RequestMapping(value = "uploadFile.do", method = RequestMethod.POST)
- @RequestMapping(value = "uploadVideo.do", method = RequestMethod.POST)
- @RequestMapping(value = "uploadPdf.do", method = RequestMethod.POST)

## EnergyElecOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/EnergyElecOrderController.java`
- @RequestMapping("/energyElecOrder/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping("doExport.do")

## LightShareBillRecordFailLogController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/LightShareBillRecordFailLogController.java`
- @RequestMapping("/lightShareBillRecordFailLog")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})

## LimitationExportController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/LimitationExportController.java`
- //@RequestMapping("limitationExport")
- //    @GetMapping("index")

## ServiceConfigController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/ServiceConfigController.java`
- @RequestMapping("/config")
- @RequestMapping(value = "/env", method = {RequestMethod.GET})

## SwitchModeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/SwitchModeController.java`
- @RequestMapping("switchMode")
- @GetMapping("list.html")
- @RequestMapping("queryPage.do")
- @GetMapping("confirm")
- @GetMapping("confirmMarketing")
- @GetMapping("confirmAsset")
- @RequestMapping("doExport.do")
- @PostMapping("importData.do")
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping("detailById.html")
- @PostMapping("delete.do")
- @RequestMapping("confirmAudit.html")
- @GetMapping("confirmOk")
- @GetMapping("confirmReject")
- @RequestMapping("marketingAudit.html")
- @GetMapping("marketingDirectorOk")
- @GetMapping("marketingDirectorReject")
- @RequestMapping("assetAudit.html")
- @GetMapping("assetOk")
- @GetMapping("assetReject")
- @RequestMapping("update.html")
- @PostMapping(value = "update.do", consumes = "application/json")

## PurchaseAppealsAuditController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/PurchaseAppealsAuditController.java`
- @RequestMapping("/purchaseAppealsAudit")
- @RequestMapping("list.html")
- @RequestMapping(value = "doList.do", method = RequestMethod.POST)
- @RequestMapping("doExport.do")
- @RequestMapping("batchAudit.do")
- @RequestMapping("auditSingle.do")

## LightMerchantDepositChangeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/LightMerchantDepositChangeController.java`
- @RequestMapping("/merchantDepositChange")
- @RequestMapping("list.html")
- @RequestMapping("datagrid.json")

## CouponController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/coupon/CouponController.java`
- @RequestMapping("/coupon/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @GetMapping("showItem.do")
- @RequestMapping(value = { "audit.do" }, method = { RequestMethod.POST })

## CnChargeBaseController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/energy/CnChargeBaseController.java`
- @RequestMapping("cnChargeBase")
- @RequestMapping("list.html")
- @RequestMapping(value = { "/configDetail.html" }, method = {RequestMethod.GET})
- @RequestMapping("doList.do")
- @RequestMapping("doDetailList.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})

## CnPeriodDivisionController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/energy/CnPeriodDivisionController.java`
- @RequestMapping("cnPeriodDivision")
- @RequestMapping("list.html")
- @RequestMapping(value = { "/configDetail.html" }, method = {RequestMethod.GET})
- @RequestMapping("doList.do")
- @RequestMapping("doDetailList.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})

## CnTouElecPriceController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/energy/CnTouElecPriceController.java`
- @RequestMapping("cnTouElecPrice")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})

## CooperationInfoController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/energy/CooperationInfoController.java`
- @RequestMapping("/cooperationInfo/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## EnergyCaseController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/energy/EnergyCaseController.java`
- @RequestMapping("/energyCase/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("add.do")
- @RequestMapping("update.do")
- //    @RequestMapping(value = { "/option.do" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/listRegion.do" })

## EnergyStorageProjectController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/energy/EnergyStorageProjectController.java`
- @RequestMapping("/energyStorageProject")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("add.html")
- @RequestMapping(value = { "save.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/projectEdit.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/projectDetail.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/orderNo.do" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "projectEdit.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/capitalCollectionUp.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/capitalCollectionEdit.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "capitalCollectionUp.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/design.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/designEdit.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "design.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/projectAudit.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "approval.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/review.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/reviewEdit.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "review.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/agreement.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/agreementEdit.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "agreement.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/order.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/orderEdit.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "order.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/acceptance.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "acceptance.do" }, method = { RequestMethod.POST })
- @RequestMapping("doExport.do")
- @RequestMapping(value = { "/listProvince.do" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/listRegion.do" }, method = {RequestMethod.GET})

## FrontCategoryCarouselController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/category/FrontCategoryCarouselController.java`
- @RequestMapping("/categoryCarousel/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"addFrontCategoryCarousel.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"delete.do"}, method = {RequestMethod.POST})

## FrontCategoryTopController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/category/FrontCategoryTopController.java`
- @RequestMapping("/categoryTop/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"delete.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"save.do"},method = {RequestMethod.POST})

## CategoryMappingController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/category/CategoryMappingController.java`
- @RequestMapping("/categoryMapping/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"addCategoryMapping.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = { "/getBackCategory.do" }, method = {RequestMethod.GET})
- @RequestMapping(value = {"delete.do"}, method = {RequestMethod.POST})

## FrontCategoryController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/category/FrontCategoryController.java`
- @RequestMapping("/category/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"addFrontCategory.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"editFrontCategory.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"disable.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"enable.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"delete.do"}, method = {RequestMethod.POST})

## ParkAppraiseController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/merchant/ParkAppraiseController.java`
- @RequestMapping("/parkAppraise")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## ParkAppraiseUpController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/merchant/ParkAppraiseUpController.java`
- @RequestMapping("/parkAppraiseUp")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## CorporateClientController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/merchant/CorporateClientController.java`
- @RequestMapping("/corporate")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = { "auditOk.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "auditFail.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "accreditCompany.do" }, method = { RequestMethod.GET })
- @RequestMapping("zeroCarbonList.html")
- @RequestMapping("zeroCarbonList.do")
- @RequestMapping("/zeroCarbonExport.do")
- @RequestMapping("zeroCarbonAuditView.html")
- @RequestMapping("zeroCarbonDetailView.html")
- @RequestMapping(value = { "zeroCarbonAuditOk.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "zeroCarbonAuditFail.do" }, method = { RequestMethod.POST })
- @PostMapping("queryContractRecord.do")
- @RequestMapping(value = {"/showContract.do"}, method = {RequestMethod.GET})
- @RequestMapping("zeroCarbonSpAuthRegion.html")
- @RequestMapping("zeroCarbonSpAuthRegionList.do")
- @RequestMapping(value = {"auditRegionFirstOk.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"auditRegionFirstFail.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"auditRegionFinalOk.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"auditRegionFinalFail.do"}, method = {RequestMethod.POST})
- @RequestMapping("salesRevenueList.html")
- @PostMapping("listSalesRevenue.do")
- @RequestMapping("/exportListSalesRevenue.do")
- @RequestMapping("listBusinessRecruitment.html")
- @PostMapping("listBusinessRecruitment.do")
- @RequestMapping("/exportRecruitment.do")
- @RequestMapping("listTouchpoint.html")
- @PostMapping("listTouchpoint.do")
- @RequestMapping("/exportTouchpoint.do")
- @RequestMapping("getMdmInfo")
- @PostMapping("freezeSp.do")
- @PostMapping("unFreezeSp.do")

## CorporateClientDepositController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/merchant/CorporateClientDepositController.java`
- @RequestMapping("/corporate/deposit")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = "/confirmPay.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/batchConfirmPay.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/confirmSap.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/fapRecordCreate.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/cancelFap.do", method = {RequestMethod.POST})

## ShopController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/merchant/ShopController.java`
- @RequestMapping("/shop/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = { "enabled.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "disabled.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "enabledYzz.do" }, method = { RequestMethod.POST })

## MerchantController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/merchant/MerchantController.java`
- @RequestMapping("/merchant/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")

## ParkAppraiseTwoController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/merchant/ParkAppraiseTwoController.java`
- @RequestMapping("/parkAppraiseTwo")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightElectricUnusualController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/operation/LightElectricUnusualController.java`
- @RequestMapping("/lightElectricUnusual/")
- @RequestMapping(value = "list.html")
- @PostMapping("doList.do")
- @GetMapping("doExport.do")

## OperationFaultDetailReportController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/operation/OperationFaultDetailReportController.java`
- @RequestMapping("/operation/operationFaultDetailReport")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("/doExport.do")

## LightOperationLossManagementController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/operation/LightOperationLossManagementController.java`
- @RequestMapping("/operation/lightOperationLossManagement")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("/doExport.do")
- @RequestMapping("/getMemberId")
- @RequestMapping("/add.do")
- @RequestMapping("/update.do")
- @RequestMapping("/firstAudit.do")
- @RequestMapping("/firstAuditReject.do")
- @RequestMapping("/secondAudit.do")
- @RequestMapping("/secondAuditReject.do")
- @RequestMapping("/thirdAudit.do")
- @RequestMapping("/thirdAuditReject.do")
- @RequestMapping("/writeOffApply.do")
- @RequestMapping("/writeOffFirstAudit.do")
- @RequestMapping("/writeOffFirstAuditReject.do")
- @RequestMapping("/writeOffSecondAudit.do")
- @RequestMapping("/writeOffSecondAuditReject.do")
- @RequestMapping("/writeOffThirdAudit.do")
- @RequestMapping("/writeOffThirdAuditReject.do")
- @RequestMapping("/delete.do")
- @RequestMapping("/writeOffUpdate.do")

## PhotovoltaicController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/photovoltaic/PhotovoltaicController.java`
- @RequestMapping("/photovoltaic")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = "doAudit.do", method = {RequestMethod.POST})

## PhotovoltaicExcelController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/photovoltaic/PhotovoltaicExcelController.java`
- @RequestMapping("/photovoltaic")
- @RequestMapping("doExport.do")

## LjNewItemController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/ljcp/LjNewItemController.java`
- @RequestMapping("/ljcpNewItem/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"addNewItem.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"disable.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"enable.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"refreshNewItem.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"changeSort.do"}, method = {RequestMethod.POST})

## LjHotItemController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/ljcp/LjHotItemController.java`
- @RequestMapping("/ljcpHotItem/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"addHotItem.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"disable.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"enable.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"refreshHotItem.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"changeSort.do"}, method = {RequestMethod.POST})

## LjCategoryController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/ljcp/LjCategoryController.java`
- @RequestMapping("/ljcpCategory/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"addCategory.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"disable.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"enable.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"refreshCategory.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"move.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"listCategoryInfo.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"getInfo.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"changeSort.do"}, method = {RequestMethod.POST})

## LjCarouselController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/ljcp/LjCarouselController.java`
- @RequestMapping("/ljcpCarousel/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"addCarousel.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"disable.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"enable.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"delete.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"refreshCarousel.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"getInfo.do"}, method = {RequestMethod.GET})

## LjCategoryItemController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/ljcp/LjCategoryItemController.java`
- @RequestMapping("/ljcpCategoryItem/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"addCategoryItem.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"disable.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"enable.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"changeSort.do"}, method = {RequestMethod.POST})

## InternalPurchaseController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/purchase/InternalPurchaseController.java`
- @RequestMapping("/internalPurchase/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = { "addInternalPurchase.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "editInternalPurchase.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "delete.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "link.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "audit.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "gotoInternalPrintView.html" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "generateSettlementNum.do" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "checkSettlementNum.do" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "queryMdmCustom.do" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "get.do" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "checkCreditInternalPurchase.do" }, method = { RequestMethod.GET })
- @RequestMapping("exportInternalPurchase.do")
- @RequestMapping(value = { "getSettlementInfo.do" }, method = { RequestMethod.GET })

## InternalPurchaseOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/purchase/InternalPurchaseOrderController.java`
- @RequestMapping("/internalPurchaseOrder/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = "/codConfirmOrder.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/codConfirmPaid.do", method = {RequestMethod.POST})
- @RequestMapping("exportInternalPurchaseOrder.do")

## UserProblemManagementController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/assistant/UserProblemManagementController.java`
- @RequestMapping("/userProblemManagement")
- @RequestMapping("list.html")
- @RequestMapping(value = "doList.do", method = RequestMethod.POST)
- @RequestMapping("doExport.do")

## InnerOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/order/InnerOrderController.java`
- @RequestMapping("/innerOrder/")
- @RequestMapping(value = {"innerOrder.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"queryInnerOrder.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/downloadInnerOrderTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importInnerOrder.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downloadInnerOrderError.do"}, method = {RequestMethod.GET})

## LightPurchaseSalesPurchaseOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/order/LightPurchaseSalesPurchaseOrderController.java`
- @RequestMapping("/lightPurchaseSalesPurchaseOrder")
- @RequestMapping("lightPsPurchaseOrderList.html")
- @RequestMapping("lightPsPurchaseOrderList.do")
- @RequestMapping(value = {"confirmOrder.do"}, method = {RequestMethod.POST})
- @RequestMapping("zeroCarbonPurchaseOrderList.html")
- @RequestMapping("zeroCarbonPurchaseOrderList.do")
- @RequestMapping("doExport.do")
- @RequestMapping(value = {"zeroCarbonOrderConfirmOrder.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = "confirmOrderView.html", method = {RequestMethod.GET})
- @RequestMapping(value = "/getSpStoreDetail.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/getRelationDetail.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/makeConfirm.do", method = {RequestMethod.POST})
- @RequestMapping(value = "viewOrderDetail.html", method = {RequestMethod.GET})
- @RequestMapping("zeroCarbonProcurementAndSalesPurchaseOrderList.html")
- @RequestMapping("zeroCarbonProcurementAndSalesPurchaseOrderList.do")
- @RequestMapping("doTransitExport.do")
- @RequestMapping(value = "procurementAndSalesConfirmOrderView.html", method = {RequestMethod.GET})
- @RequestMapping(value = "/makeTransitConfirm.do", method = {RequestMethod.POST})
- @RequestMapping(value = "viewProcurementAndSalesOrderDetail.html", method = {RequestMethod.GET})

## DsPredictionOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/order/DsPredictionOrderController.java`
- @RequestMapping("/dsPredictionOrder")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("getSku.do")
- @RequestMapping("add.html")
- @RequestMapping(value = { "save.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/scbaudit.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "scbapproval.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/gylaudit.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "gylapproval.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/edit.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "edit.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/detail.html" }, method = {RequestMethod.GET})
- @RequestMapping("doExport.do")

## DsStockOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/order/DsStockOrderController.java`
- @RequestMapping("/dsStockOrder")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("getDsPredictionOrder.do")
- @RequestMapping("getDsWarehouse.do")
- @RequestMapping("add.html")
- @RequestMapping(value = { "save.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/confirm.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "confirm.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/detail.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/qsDetail.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/takeOver.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "takeOver.do" }, method = { RequestMethod.POST })
- @RequestMapping("doExport.do")

## DsInventoryManageController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/order/DsInventoryManageController.java`
- @RequestMapping("/dsInventoryManage")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## DsWarehouseController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/order/DsWarehouseController.java`
- @RequestMapping("/dsWarehouse")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("add.html")
- @RequestMapping(value = { "save.do" }, method = { RequestMethod.POST })
- @RequestMapping("doExport.do")
- @RequestMapping(value = { "/listProvince.do" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/listRegion.do" }, method = {RequestMethod.GET})

## OrderJointVentureController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/order/OrderJointVentureController.java`
- @RequestMapping("/order")
- @RequestMapping("orderJointVentureList.html")
- @RequestMapping("doOrderJointVentureList.do")
- @RequestMapping("bizCheckOrderDetail.html")
- @RequestMapping(value = "/doOrderJointVentureBizCheck.do", method = {RequestMethod.POST})
- @RequestMapping("finCheckOrderDetail.html")
- @RequestMapping(value = "/doOrderJointVentureFinCheck.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/doOrderJointVentureBizDeliverCheck.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/doOrderJointVentureBizInvoiceCheck.do", method = {RequestMethod.POST})

## OrderListController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/order/OrderListController.java`
- @RequestMapping("/order")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = {"/exportOrderItemCbs.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = "/changeMinusDay.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/changePlusDay.do", method = {RequestMethod.POST})

## ExpertOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/order/ExpertOrderController.java`
- @RequestMapping("/expertOrder/")
- @RequestMapping(value = {"expertOrder.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"queryExpertOrder.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/downloadExpertOrderTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importExpertOrder.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downloadExpertOrderError.do"}, method = {RequestMethod.GET})

## BarCodeApplyController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/order/BarCodeApplyController.java`
- @RequestMapping("/barCodeApply")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("add.html")
- @RequestMapping(value = { "save.do" }, method = { RequestMethod.POST })
- @RequestMapping("getSku.do")
- @RequestMapping("getSkuList.do")
- @RequestMapping("cancel.do")
- @RequestMapping("doExport.do")
- @RequestMapping("/getUserName.do")

## BudgetController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/order/BudgetController.java`
- @RequestMapping("/budget")
- @RequestMapping("budgetDetail.html")
- @RequestMapping("budgetList.html")
- @RequestMapping("doBudgetList.do")
- @RequestMapping("budgetAdd.html")
- @RequestMapping(value = "doBudgetAdd.do", method = {RequestMethod.POST})
- @RequestMapping("budgetModify.html")
- @RequestMapping(value = "doBudgetModify.do", method = {RequestMethod.POST})
- @RequestMapping("budgetFirstCheck.html")
- @RequestMapping(value = "doBudgetFirstCheck.do", method = {RequestMethod.POST})
- @RequestMapping("budgetFinanceCheck.html")
- @RequestMapping(value = "doBudgetFinanceCheck.do", method = {RequestMethod.POST})

## OrderDetailController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/order/OrderDetailController.java`
- @RequestMapping("/order")
- @RequestMapping("orderDetail.html")

## OrderZeroController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/order/OrderZeroController.java`
- @RequestMapping("/order")
- @RequestMapping("zeroList.html")
- @RequestMapping("doZeroList.do")

## CnOrderListController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/order/CnOrderListController.java`
- @RequestMapping("/cnOrder")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("orderDetail.html")
- @RequestMapping(value = {"/downBatchTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importBatch.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downloadCnOrderError.do"},method = {RequestMethod.GET})

## BarCodeDetailController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/order/BarCodeDetailController.java`
- @RequestMapping("/barCodeDetail")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping("cancel.do")

## OrderTransferListController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/order/OrderTransferListController.java`
- @RequestMapping("/order")
- @RequestMapping("transferList.html")
- @RequestMapping("doTransferList.do")
- @RequestMapping(value = "/transferEnableAudit.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/transferAudit.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/transferCodPaid.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/confirmCustomerCode.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/confirmIncreaseStock.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/batchConfirmCustomerCode.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/batchTransferAudit.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/fapRecordCreate.do", method = {RequestMethod.POST})

## LightPurchaseSalesOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/order/LightPurchaseSalesOrderController.java`
- @RequestMapping("/lightPurchaseSalesOrder")
- @RequestMapping("lightPsOrderList.html")
- @RequestMapping("lightPsOrderList.do")
- @RequestMapping("lightPsOrderDetail.do")
- @RequestMapping("zeroCarbonOrderList.html")
- @RequestMapping("zeroCarbonOrderList.do")
- @RequestMapping("doExport.do")
- @RequestMapping("zeroCarbonOrderDetail.do")
- @RequestMapping(value = "lightPsItemOrderList.do", method = {RequestMethod.GET})
- @RequestMapping(value = "zeroCarbonItemOrderList.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/confirmPay.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/zeroCarbonOrderConfirmPay.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/zeroCarbonOrderBatchConfirmPay.do", method = {RequestMethod.POST})
- @PostMapping("/updateAddress.do")
- @RequestMapping("selectAddressLog.do")
- @RequestMapping(value = "/confirmReceiptUrl.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/fapRecordCreate.do", method = {RequestMethod.POST})

## DispatchReportController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/dispatch/DispatchReportController.java`
- @RequestMapping("/dispatch")
- @RequestMapping("/closedList.html")
- @RequestMapping("/timeLinessList.html")
- @RequestMapping("/closedListQuery.do")
- @RequestMapping("/TimeLinessQuery.do")
- @RequestMapping("/doExport.do")
- @RequestMapping("/doTimeLinessExport.do")

## LightTechAuditorController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/dispatch/LightTechAuditorController.java`
- @RequestMapping("/tech/auditor/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("add.do")
- @RequestMapping("editStatus.do")
- @GetMapping("getLogList.do")
- @RequestMapping("doExport.do")
- @GetMapping("findValidAuditor.do")

## LightAuditDispatchTimeConfigController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/dispatch/LightAuditDispatchTimeConfigController.java`
- @RequestMapping("/dispatch/time/config/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @PostMapping("addConfig.do")
- @PostMapping("updateConfig.do")
- @PostMapping("deleteConfig.do")
- @PostMapping("toggleStatus.do")
- @PostMapping("terminateConfig.do")
- @RequestMapping("doExport.do")

## LightAuditDispatchLogController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/dispatch/LightAuditDispatchLogController.java`
- @RequestMapping("/tech/dispatch/")
- @RequestMapping(value = {"reDispatch.do"},  method = {RequestMethod.POST})

## MessageManagementController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/message/MessageManagementController.java`
- @RequestMapping("/messageManagement/")
- @RequestMapping("list.html")
- @PostMapping("doList.do")
- //    @RequestMapping("add.html")
- @RequestMapping("doAdd.do")
- @RequestMapping(value = { "/messageManagementDetail.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/messageManagementAudit.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "messageManagementAudi.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/delete.do" }, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = "export.do",method = {RequestMethod.GET})

## MessageManagementCreateController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/message/MessageManagementCreateController.java`
- @RequestMapping("/messageManagementCreate/")
- @RequestMapping("list.html")
- @PostMapping("doList.do")
- @RequestMapping("add.html")
- @RequestMapping("doAdd.do")
- @RequestMapping(value = { "/messageManagementDetail.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/delete.do" }, method = {RequestMethod.POST})

## OrderSettleDetailController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/haierRecruit/OrderSettleDetailController.java`
- @RequestMapping("/settleDetails/")
- @RequestMapping("settlelist.html")
- @RequestMapping("settlelist.do")
- @RequestMapping("xsCommissionlist.do")
- @RequestMapping(value = { "confirmCommision.do" }, method = { RequestMethod.POST })

## OrderPayDetailController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/haierRecruit/OrderPayDetailController.java`
- @RequestMapping("/payDetails/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = { "linkInternalPurchase.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "confirmPay.do" }, method = { RequestMethod.POST })

## ZeroCarbonOrderPolicyCashController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/zerocarbon/ZeroCarbonOrderPolicyCashController.java`
- @RequestMapping("/zeroCarbonOrderPolicyCash")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @GetMapping("audit.do")
- @PostMapping("detail.do")

## LightZeroCarbonDepositRefundController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/zerocarbon/LightZeroCarbonDepositRefundController.java`
- @RequestMapping("/zeroCarbon/depositRefund/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")

## LightZeroCarbonStockController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/zerocarbon/LightZeroCarbonStockController.java`
- @RequestMapping("/zeroCarbon/lightZeroCarbonStock")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doTransitExport.do")
- @RequestMapping("transitList.html")
- @RequestMapping("lightZeroCarbonStockChangeList.do")
- @RequestMapping("lightZeroCarbonStockChangeExport.do")

## SubGoalController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/zerocarbon/SubGoalController.java`
- @RequestMapping("/zerocarbon/subGoal/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = {"add.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"add.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"edit.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"edit.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"delete.do"}, method = {RequestMethod.POST})

## LightZeroMaterialManageController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/zerocarbon/LightZeroMaterialManageController.java`
- @RequestMapping("/zeroCarbon/materialManage")
- @RequestMapping("list.html")
- @PostMapping("manageList.do")
- @RequestMapping("doExport.do")

## LightZeroCarbonStationController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/zerocarbon/LightZeroCarbonStationController.java`
- @RequestMapping("/zeroCarbon/lightStation")
- @RequestMapping("stationList.html")
- @RequestMapping("stationList.do")
- @RequestMapping("stationAuditInfo.html")
- @RequestMapping("stationDetail.html")
- @PostMapping("audit.do")
- @RequestMapping("stationExport.do")
- @RequestMapping(value = "/getChangeInstaller.do", method = {RequestMethod.GET})
- @RequestMapping(value = { "dispatch.do" }, method = { RequestMethod.POST })
- @RequestMapping("stationCompleteList.html")
- @RequestMapping("stationCompleteList.do")
- @RequestMapping("stationCompleteAuditInfo.html")
- @RequestMapping("stationCompleteDetail.html")
- @PostMapping("completeAudit.do")
- @RequestMapping("stationCompleteExport.do")
- @RequestMapping("stationGridList.html")
- @RequestMapping("stationGridList.do")
- @RequestMapping("stationGridAuditInfo.html")
- @RequestMapping("stationGridDetail.html")
- @PostMapping("gridAudit.do")
- @RequestMapping("stationGridExport.do")

## LightZeroMaterialSerialController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/zerocarbon/LightZeroMaterialSerialController.java`
- @RequestMapping("/zeroCarbon/materialSerial")
- @RequestMapping("list.html")
- @PostMapping("serialList.do")
- @RequestMapping("doExport.do")

## LightZeroCarbonInstallationFeeSettleController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/zerocarbon/LightZeroCarbonInstallationFeeSettleController.java`
- @RequestMapping("/zeroCarbon/settle/")
- @RequestMapping(value = {"occupyList.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"doOccupyList.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"doList.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"detail.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"audit.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"auditOk.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"auditFail.do"}, method = {RequestMethod.POST})
- @RequestMapping("doExport.do")
- @RequestMapping("doExportOccupy.do")

## LightZeroCarbonComponentLibraryController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/zerocarbon/LightZeroCarbonComponentLibraryController.java`
- @RequestMapping("/zeroCarbon/lightComponentLibrary")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping("doExport.do")

## LightZeroCarbonPurchaseOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/zerocarbon/LightZeroCarbonPurchaseOrderController.java`
- @RequestMapping("/zeroCarbon/lightZeroCarbonPurchaseOrder")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("transitList.html")
- @RequestMapping("doTransitList.do")
- @RequestMapping("audit.do")
- @RequestMapping("doExport.do")
- @RequestMapping("doTransitExport.do")
- @RequestMapping(value = {"cancel.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = "makeDirectStockView.html", method = {RequestMethod.GET})
- @RequestMapping(value = "makeTransitDirectStockView.html", method = {RequestMethod.GET})
- @RequestMapping(value = "/getZeroCarbonStoreDetail.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/getZeroCarbonSkuData.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/getZeroCarbonSkuDataMoreInfo.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/getAmount.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/pushDirectStock.do", method = {RequestMethod.POST})

## LightZeroCarbonOrderGrabbingCampaignController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/zerocarbon/LightZeroCarbonOrderGrabbingCampaignController.java`
- @RequestMapping("/zeroCarbon/campaign")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping("auditInfo.html")
- @RequestMapping("detail.html")
- @PostMapping("audit.do")
- @PostMapping("finalAudit.do")
- @RequestMapping("export.do")

## ZeroCarbonMerchantNoticeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/zerocarbon/ZeroCarbonMerchantNoticeController.java`
- @RequestMapping("/zeroCarbon/merchantNotice")
- @RequestMapping("list.html")
- @RequestMapping("add.html")
- @RequestMapping("audit.html")
- @RequestMapping("edit.html")
- @RequestMapping("detail.html")
- @RequestMapping("queryMerchantNoticeList")
- @RequestMapping("addMerchantNotice")
- @RequestMapping("auditMerchantNotice")
- @RequestMapping("editMerchantNotice")
- @RequestMapping("queryMerchantNoticeDetail")

## ZeroCarbonStationPolicyController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/zerocarbon/ZeroCarbonStationPolicyController.java`
- @RequestMapping("/zeroCarbonStationPolicy")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @GetMapping("audit.do")
- @PostMapping("detail.do")

## LightZeroCarbonEStationController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/zerocarbon/LightZeroCarbonEStationController.java`
- @RequestMapping("/zeroCarbon/EStation")
- @RequestMapping("stationList.html")
- @RequestMapping("stationList.do")
- @RequestMapping("stationDetail.html")
- @RequestMapping("stationAudit.html")
- @PostMapping("auditStation.do")
- @RequestMapping("stationExport.do")
- @RequestMapping(value = "/getChangeInstaller.do", method = {RequestMethod.GET})
- @RequestMapping(value = { "assign.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "rejectAssignment.do" }, method = { RequestMethod.POST })

## LightZeroCarbonDepositRefundAuditController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/zerocarbon/LightZeroCarbonDepositRefundAuditController.java`
- @RequestMapping("/zeroCarbon/depositRefundAudit/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping("detail.html")
- @RequestMapping("audit.html")
- @RequestMapping("audit.do")
- @RequestMapping("/doExport.do")

## LightZeroMaterialPurchaseController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/zerocarbon/LightZeroMaterialPurchaseController.java`
- @RequestMapping("/zeroCarbon/materialPurchase/")
- @RequestMapping("list.html")
- @PostMapping("purchaseList.do")
- @RequestMapping("doExport.do")

## ZeroCarbonSpBusinessModelController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/zerocarbon/ZeroCarbonSpBusinessModelController.java`
- @RequestMapping("/zeroCarbonSpBusinessModel")
- @PostMapping("list.do")
- @PostMapping("audit.do")

## LightZeroCarbonSkuDataController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/zerocarbon/LightZeroCarbonSkuDataController.java`
- @RequestMapping("/zeroCarbon/lightSku")
- @RequestMapping("skuList.html")
- @RequestMapping("skuList.do")
- @RequestMapping(value = { "addSkuData.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = {"editSkuData.do"}, method = { RequestMethod.POST })
- @RequestMapping(value = { "enableSkuData.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "disableSkuData.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = "doExport.do")
- @RequestMapping(value = "/pushDataToRrs.do", method = {RequestMethod.POST})

## LightZeroCarbonInstallationFeeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/zerocarbon/LightZeroCarbonInstallationFeeController.java`
- @RequestMapping("/zeroCarbon/installationFee/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping("export.do")
- @RequestMapping("batchConfirm.do")
- @RequestMapping("batchReject.do")

## ZeroCarbonGvsWarehouseAgeAnalysisController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/zerocarbon/ZeroCarbonGvsWarehouseAgeAnalysisController.java`
- @RequestMapping("/zeroCarbon/ageAnalysis")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("export.do")
- @RequestMapping("pullData.do")

## ZeroCarbonOrderPolicyController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/zerocarbon/ZeroCarbonOrderPolicyController.java`
- @RequestMapping("/zeroCarbonOrderPolicy")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping("create.html")
- @PostMapping("create.do")
- @RequestMapping("detail.html")
- @RequestMapping("audit.html")
- @PostMapping("audit.do")
- @RequestMapping("update.html")
- @PostMapping("update.do")

## ZeroCarbonSpShopController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/zerocarbon/ZeroCarbonSpShopController.java`
- @RequestMapping("/zeroCarbonShop")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping("zeroCarbonShopAudit.html")
- @RequestMapping("zeroCarbonShopAcceptance.html")
- @RequestMapping("zeroCarbonShopDetail.html")
- @PostMapping("audit.do")

## LightZeroCarbonStoreController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/zerocarbon/LightZeroCarbonStoreController.java`
- @RequestMapping("/zeroCarbon/store")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping(value = { "enableThirdPartyStore.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "enableStore.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "disableStore.do" }, method = { RequestMethod.POST })
- @PostMapping("update.do")
- @PostMapping("add.do")
- @RequestMapping(value = "/get.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/getStoreChangeLog.do", method = {RequestMethod.GET})

## LightZeroCarbonInverterController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/zerocarbon/LightZeroCarbonInverterController.java`
- @RequestMapping("/zeroCarbon/lightInverter")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping("detail.html")
- @GetMapping(value = "dayChart.do")
- @GetMapping(value = "historyWeather.do")
- @GetMapping(value = "dayChartPro.do")
- @GetMapping(value = "dayChartProNew.do")
- @GetMapping(value = "monthChart.do")
- @GetMapping(value = "monthChartPro.do")
- @GetMapping(value = "monthChartProNew.do")
- @GetMapping(value = "yearChart.do")
- @GetMapping(value = "yearChartPro.do")
- @GetMapping(value = "yearChartProNew.do")
- @GetMapping(value = "totalChart.do")
- @GetMapping(value = "totalChartPro.do")
- @GetMapping(value = "totalChartProNew.do")
- @RequestMapping(value = {"unBind.do"}, method = {RequestMethod.POST})

## ActivityPictureController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/activity/ActivityPictureController.java`
- @RequestMapping("/activityPicture")
- @RequestMapping("list.html")
- @RequestMapping(value = "/getList.do")
- @RequestMapping(value="/save.do")
- @RequestMapping(value="/update.do")

## SkuLimitedController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/activity/SkuLimitedController.java`
- @RequestMapping("/activity")
- @RequestMapping("skuLimited.html")
- @RequestMapping("skuLimitedList.do")
- @RequestMapping(value = "skuLimitedAdd.do", method = {RequestMethod.POST})

## ShareProjectPaymentAccountController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/sharePayment/ShareProjectPaymentAccountController.java`
- @RequestMapping("/shareProjectPaymentAccount")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("add.html")
- @RequestMapping("edit.html")
- @RequestMapping(value = "save.do", method = RequestMethod.POST)
- @RequestMapping(value = "update.do", method = RequestMethod.POST)
- @RequestMapping(value = "downloadTemplate.do", method = RequestMethod.GET)
- @RequestMapping(value = "importData.do", method = RequestMethod.POST)
- @RequestMapping(value = "exportData.do", method = RequestMethod.GET)
- @RequestMapping("paymentTypeConfig.html")
- @RequestMapping("doPaymentTypeList.do")
- @RequestMapping(value = "updatePaymentType.do", method = RequestMethod.POST)
- @RequestMapping(value = "clearPaymentType.do", method = RequestMethod.POST)
- @RequestMapping("doPaymentTypeLogList.do")
- @RequestMapping(value = "downloadPaymentTypeTemplate.do", method = RequestMethod.GET)
- @RequestMapping(value = "importPaymentType.do", method = RequestMethod.POST)

## BtFundReportController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/bt/BtFundReportController.java`
- @RequestMapping("/btFundReport/")
- @RequestMapping(value = "list.html", method = RequestMethod.GET)
- @RequestMapping(value = "list.do", method = RequestMethod.POST)
- @RequestMapping(value = "allocateDetailList.do", method = RequestMethod.POST)
- @RequestMapping(value = "repaymentRecordList.do", method = RequestMethod.POST)
- @RequestMapping(value = "uploadVoucher.do", method = RequestMethod.POST)
- @RequestMapping("doExport.do")
- @RequestMapping(value = "downloadTemplate.do", method = RequestMethod.GET)
- @RequestMapping(value = "importData.do", method = RequestMethod.POST)
- @RequestMapping(value = "syncFapStatus.do", method = RequestMethod.POST)
- @RequestMapping("getEnums.do")

## BtProjectTransactionController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/bt/BtProjectTransactionController.java`
- @RequestMapping("/btProjectTransaction/")
- @RequestMapping(value = "list.html", method = RequestMethod.GET)
- @RequestMapping(value = "list.do", method = RequestMethod.POST)
- @RequestMapping("doExport.do")
- @RequestMapping(value = "downloadTemplate.do", method = RequestMethod.GET)
- @RequestMapping(value = "importData.do", method = RequestMethod.POST)
- @RequestMapping(value = "downloadImportFailures.do", method = RequestMethod.GET)
- @RequestMapping("getEnums.do")

## BtFundAssetAllocateDetailController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/bt/BtFundAssetAllocateDetailController.java`
- @RequestMapping("/btFundAssetAllocateDetail/")
- @RequestMapping(value = "list.html", method = RequestMethod.GET)
- @RequestMapping(value = "list.do", method = RequestMethod.POST)
- @RequestMapping("doExport.do")
- @RequestMapping(value = "downloadTemplate.do", method = RequestMethod.GET)
- @RequestMapping(value = "importData.do", method = RequestMethod.POST)
- @RequestMapping(value = "downloadImportFailures.do", method = RequestMethod.GET)

## BtAssetManagementController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/bt/BtAssetManagementController.java`
- @RequestMapping("/btAssetManagement/")
- @RequestMapping(value = "list.html", method = RequestMethod.GET)
- @RequestMapping(value = "list.do", method = RequestMethod.POST)
- @RequestMapping("doExport.do")
- @RequestMapping(value = "downloadTemplate.do", method = RequestMethod.GET)
- @RequestMapping(value = "importData.do", method = RequestMethod.POST)
- @RequestMapping(value = "downloadImportFailures.do", method = RequestMethod.GET)
- @RequestMapping("getEnums.do")

## LightAssetInProgressReportController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/bt/LightAssetInProgressReportController.java`
- @RequestMapping("/lightAssetInProgressReport/")
- @RequestMapping(value = "list.html", method = RequestMethod.GET)
- @RequestMapping(value = "list.do", method = RequestMethod.POST)
- @RequestMapping("doExport.do")

## BtFundAssetManagementReportController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/bt/BtFundAssetManagementReportController.java`
- @RequestMapping("/btFundAssetManagementReport/")
- @RequestMapping(value = "list.html", method = RequestMethod.GET)
- @RequestMapping(value = "list.do", method = RequestMethod.POST)
- @RequestMapping("doExport.do")
- @RequestMapping("getEnums.do")

## LightAssetManagementReportController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/bt/LightAssetManagementReportController.java`
- @RequestMapping("/lightAssetManagementReport/")
- @RequestMapping(value = "list.html", method = RequestMethod.GET)
- @RequestMapping(value = "list.do", method = RequestMethod.POST)
- @RequestMapping("doExport.do")
- @RequestMapping("getEnums.do")

## ElectricityPriceSummaryDiffPeriodController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/businessforecast/ElectricityPriceSummaryDiffPeriodController.java`
- @RequestMapping("/electricityPriceSummaryDiffPeriod")
- @RequestMapping("list.html")
- @RequestMapping(value = {"/configDetail.html"}, method = {RequestMethod.GET})
- @RequestMapping("doList.do")
- @RequestMapping("doDetailList.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})

## TouElectricityPriceController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/businessforecast/TouElectricityPriceController.java`
- @RequestMapping("/touElectricityPrice")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})

## ElectricityPriceOfCoalController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/businessforecast/ElectricityPriceOfCoalController.java`
- @RequestMapping("/electricityPriceOfCoal")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("update.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})

## ForecastProjectDetailController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/businessforecast/ForecastProjectDetailController.java`
- @RequestMapping("/forecastProjectDetail")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @PostMapping("delete")
- @RequestMapping("doExport.do")

## CookController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/cook/CookController.java`
- @RequestMapping("/cook")
- @RequestMapping("/list.html")
- @RequestMapping("/getCookbookList.do")
- @RequestMapping("/getCookDayList.do")
- @RequestMapping(value = { "delCookbook.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "delCookDay.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = {"/downloadExpertBookError.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downloadExpertDayError.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/importExpertDay.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/importExpertBook.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downloadDayExpertModel.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downloadBookExpertModel.do"}, method = {RequestMethod.POST})

## InvestorMasterDataAuditController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/investor/InvestorMasterDataAuditController.java`
- @RequestMapping("/investorAudit/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("detail.html")
- @RequestMapping("audit.html")
- @RequestMapping("audit.do")
- @RequestMapping("/doExport.do")

## InvestorMasterDataController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/investor/InvestorMasterDataController.java`
- @RequestMapping("/investor/")
- @RequestMapping(value = {"investorMasterData.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"add.html"}, method = {RequestMethod.GET})
- @RequestMapping("investorMasterData.do")
- @RequestMapping("addInvestor.do")
- @RequestMapping("update.html")
- @RequestMapping("updateInvestor.do")
- @RequestMapping("updateCooperation.html")
- @RequestMapping("updateCooperation.do")
- @PostMapping("delete.do")
- //    @RequestMapping("deleteInvestor.do")
- @RequestMapping("updateRating.do")
- @RequestMapping("updateCooperationStatus.do")
- @RequestMapping("getInvestorById.do")
- @RequestMapping("getInvestorByName.do")
- @RequestMapping("exportInvestor.do")
- @RequestMapping(value = "getProvinceList.do", method = RequestMethod.POST)
- @RequestMapping(value = "getStatistics.do", method = RequestMethod.POST)

## GfFirstInputPieceController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/gf/GfFirstInputPieceController.java`
- @RequestMapping("/gf/gfFirstInputPiece")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = { "/gfFirstInputPiece.html" }, method = {RequestMethod.GET})

## GfBusinessOpportunityController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/gf/GfBusinessOpportunityController.java`
- @RequestMapping("/gf/gfBusinessOpportunity")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("resend.do")
- @RequestMapping("doExport.do")
- @RequestMapping(value = { "/gfBusinessOpportunityDetail.html" }, method = {RequestMethod.GET})

## GfProductInformationController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/gf/GfProductInformationController.java`
- @RequestMapping("/gf/gfProductInformation")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = "/enableData.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/disableData.do", method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})

## GfLightStationController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/gf/GfLightStationController.java`
- @RequestMapping("/gf/gfLightStation")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping("detail.html")
- @RequestMapping(value = "showRecord.do", method = {RequestMethod.GET})
- @RequestMapping(value = "getPlanBom.do", method = {RequestMethod.GET})
- @GetMapping("queryModuleSn.do")
- @GetMapping("getDesignByDetail")
- @RequestMapping(value = "listPlanConfig.do", method = {RequestMethod.GET})

## GfMergeGridInputPieceController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/gf/GfMergeGridInputPieceController.java`
- @RequestMapping("/gf/gfMergeGridInputPiece")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = { "/gfMergeGridInputPiece.html" }, method = {RequestMethod.GET})

## GfCompleteInputPieceController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/gf/GfCompleteInputPieceController.java`
- @RequestMapping("/gf/gfCompleteInputPiece")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = { "/gfCompleteInputPiece.html" }, method = {RequestMethod.GET})

## SubCenterInfoController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/system/SubCenterInfoController.java`
- @RequestMapping("/subCenter")
- @RequestMapping(value = "/list", method = RequestMethod.GET)

## BankAreaController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/system/BankAreaController.java`
- @RequestMapping("/bankArea/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = {"add.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"add.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"edit.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"edit.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"delete.do"}, method = {RequestMethod.POST})

## CnnNuclearProjectPaymentController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/cnnPayment/CnnNuclearProjectPaymentController.java`
- @RequestMapping("/cnnPayment/")
- @RequestMapping(value = {"cnnNuclearProjectPaymentList.html"}, method = {RequestMethod.GET})
- @RequestMapping("cnnNuclearProjectPaymentList.do")
- @RequestMapping(value = {"/cnnNuclearProjectPaymentDelete.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = "exportCnnNuclearProjectPayment.do", method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})

## CnnNuclearProjectInvoiceController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/cnnPayment/CnnNuclearProjectInvoiceController.java`
- @RequestMapping("/cnnInvoice/")
- @RequestMapping(value = {"cnnNuclearProjectInvoiceList.html"}, method = {RequestMethod.GET})
- @RequestMapping("cnnNuclearProjectInvoiceList.do")
- @RequestMapping("cnnNuclearProjectInvoiceDelete.do")
- @RequestMapping(value = "exportCnnNuclearProjectInvoice.do", method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})

## TenderManagementController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/tenderManagement/TenderManagementController.java`
- @RequestMapping("/tenderManagement")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = { "add.do" }, method = { RequestMethod.POST })
- //    @RequestMapping(value = "/del", method = {RequestMethod.POST})
- //    @RequestMapping(value = "/upate", method = {RequestMethod.POST})

## ConsultationDetailController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/energyStorage/ConsultationDetailController.java`
- @RequestMapping("/ConsultationDetail")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = { "/receive.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "receive.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/handle.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "handle.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/detail.html" }, method = {RequestMethod.GET})
- @RequestMapping("doExport.do")

## InstallMaintenanceInfoController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/energyStorage/InstallMaintenanceInfoController.java`
- @RequestMapping("/InstallMaintenanceInfo")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = { "/receive.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "receive.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/handle.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "handle.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/detail.html" }, method = {RequestMethod.GET})
- @RequestMapping("doExport.do")

## EchannelSkuController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/echannel/EchannelSkuController.java`
- @RequestMapping("/echannel")
- @RequestMapping("echannelSkuList.html")
- @RequestMapping("doEchannelSkuList.do")
- @RequestMapping(value = "doEchannelSkuAdd.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/getBySkuId.do", method = {RequestMethod.GET})

## LightMakeOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightMakeOrderController.java`
- @RequestMapping("/lightMakeOrder")
- @RequestMapping("list.html")
- //    @RequestMapping("subCenterList.html")
- @RequestMapping("doList.do")
- @RequestMapping("doSubCenterList.do")
- @GetMapping(value = "makeStockView.html")
- @RequestMapping(value = "makeDirectStockView.html", method = {RequestMethod.GET})
- @PostMapping(value = "/makeStockValidate.do")
- @RequestMapping(value = "/makeStock.do", method = {RequestMethod.POST})
- @RequestMapping("doExport.do")
- @RequestMapping(value = "/getDepositBySp.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/getSp.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/getSpById.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/getAuclonStore.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/getAuclonStoreDetail.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/getSkuData.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/pushDirectStock.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/getSpStoreDetail.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/getBySpIdAndRegionId.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/getStoreAddressListByStoreId.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/getStoreAddressByAddressId.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/getMainStoreListBySpId.do", method = {RequestMethod.GET})

## LightStationDevelopWarningController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationDevelopWarningController.java`
- @RequestMapping("/lightStationDevelopWarning")
- @RequestMapping("/list.do")
- @RequestMapping("doExport.do")
- @RequestMapping("list.html")

## LightOverdueListDetailRejectOtherController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightOverdueListDetailRejectOtherController.java`
- @RequestMapping("/lightOverdueListDetailRejectOther")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @RequestMapping("doExport.do")

## LightInstantRewardPolicyController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightInstantRewardPolicyController.java`
- @RequestMapping("/lightInstantRewardPolicy")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @PostMapping("audit.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping("doExport.do")
- @PostMapping("delete.do")

## LightGroovyScriptParamController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightGroovyScriptParamController.java`
- @RequestMapping("/lightGroovyScriptParam")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("change.do")
- @PostMapping("add.do")

## LightStationEpcPlanChangeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationEpcPlanChangeController.java`
- @RequestMapping("/lightEpcPlanChange/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("detail.html")
- @RequestMapping("audit.html")
- @RequestMapping(value = { "auditOk.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "auditFail.do" }, method = { RequestMethod.POST })

## LightStopStationController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStopStationController.java`
- @RequestMapping("/lightStopStation")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doListTodo.do")
- @RequestMapping(value = { "auditOk.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "auditFail.do" }, method = { RequestMethod.POST })
- @RequestMapping("doExport.do")
- @RequestMapping(value = { "tmpBatchSignStop.do" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "tmpBatchSignMaster.do" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "tmpMyzStop.do" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "tmpSingleSignStop.do" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "tmpSingleSignMaster.do" }, method = { RequestMethod.GET })

## LightInstantGridRewardPolicyController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightInstantGridRewardPolicyController.java`
- @RequestMapping("/lightInstantGridRewardPolicy")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @PostMapping("audit.do")
- @PostMapping("delete.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping("doExport.do")

## LightModulePartCompleteApplyController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightModulePartCompleteApplyController.java`
- @RequestMapping("/lightModulePartCompleteApply/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @GetMapping("detail.do")
- @PostMapping("audit.do")

## LightRentPaymentRecordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightRentPaymentRecordController.java`
- @RequestMapping("/lightRentPaymentRecord")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("/doExport.do")

## LightSpGridAwardOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSpGridAwardOrderController.java`
- @RequestMapping("lightSpGridAwardOrder")
- @RequestMapping("list.html")
- @RequestMapping("policyList.html")
- @RequestMapping("doList.do")
- @RequestMapping("detail.html")
- @RequestMapping("detail.do")
- @GetMapping("doModelDetailList.do")
- @RequestMapping("doExport.do")

## LightCoinController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightCoinController.java`
- @RequestMapping("/lightCoin")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = {"/downBatchTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importBatch.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/checkAccount.do"}, method = {RequestMethod.POST})
- @RequestMapping("doExport.do")

## LightBillFunnelCacheController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightBillFunnelCacheController.java`
- @RequestMapping("/lightBillFunnelCache")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @RequestMapping("deal.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @RequestMapping("doExport.do")

## LightInveterHuarunController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightInveterHuarunController.java`
- @RequestMapping("/lightInveterHuarun")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightCostAccountController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightCostAccountController.java`
- @RequestMapping("/lightCostAccount")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightInstantGridRewardPolicyLogController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightInstantGridRewardPolicyLogController.java`
- @RequestMapping("/lightInstantGridRewardPolicyLog")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping("doExport.do")

## LightMasterHtRecordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightMasterHtRecordController.java`
- @RequestMapping("/lightMasterHtRecord")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping("doExport.do")

## LightUnionpayRentController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightUnionpayRentController.java`
- @RequestMapping("/lightUnionpayRent")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping(value = "detail.html", method = {RequestMethod.GET})

## LightCompanyPriceController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightCompanyPriceController.java`
- @RequestMapping("/lightCompanyPrice")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @GetMapping("/downTemplate.do")
- @PostMapping("importData.do")
- @PostMapping("delete.do")
- @PostMapping("audit.do")
- @PostMapping("auditAll.do")

## PowerPurchaseManagementController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/PowerPurchaseManagementController.java`
- @RequestMapping("/powerPurchaseManagement")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doAdd.do")
- @RequestMapping("doEdit.do")
- @RequestMapping("doDelete.do")
- @RequestMapping("/doExport.do")
- @RequestMapping("/downloadTemplate.do")
- @RequestMapping("/doBatchImport.do")
- @RequestMapping("checkName.do")

## LightStationPlanChangeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationPlanChangeController.java`
- @RequestMapping("/lightPlanChange/")
- @RequestMapping("list.html")
- @RequestMapping("planChangeList.do")
- @RequestMapping(value = { "auditOk.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "auditFail.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = {"assetAuditOk.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"assetAuditReject.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"acceptanceAuditOk.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"acceptanceAuditReject.do"}, method = {RequestMethod.POST})
- @RequestMapping("auditPlanChange.html")
- @RequestMapping("assetAuditPlanChange.html")
- @RequestMapping("acceptanceAuditPlanChange.html")
- @RequestMapping("showPlanChange.html")
- @RequestMapping("doExport.do")
- @RequestMapping(value = {"getLastRejectReason.do"}, method = {RequestMethod.GET})

## HuaRongIncomeQualityGuaranteeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/HuaRongIncomeQualityGuaranteeController.java`
- @RequestMapping("/huaRongIncomeQualityGuarantee")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @GetMapping("/downTemplate.do")
- @PostMapping("importData.do")
- @RequestMapping("doExport.do")
- @GetMapping("countBatch.do")
- @PostMapping("confirm.do")
- @GetMapping("delete.do")
- @GetMapping("/reverse/downTemplate.do")
- @PostMapping("/reverse/importData.do")

## LightSubsidyController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSubsidyController.java`
- @RequestMapping("/lightSubsidy")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping("monthList.html")
- @RequestMapping("doMonthList.do")
- @RequestMapping("doMonthExport.do")

## LightStationZhongheWhiteListController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationZhongheWhiteListController.java`
- @RequestMapping("/lightStationZhongheWhiteList")
- @RequestMapping("list.html")
- @RequestMapping("/doList.do")
- @RequestMapping("/doExport.do")

## LightSubStockController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSubStockController.java`
- @RequestMapping("/lightSubStock")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## CmPreOrderVtController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmPreOrderVtController.java`
- @RequestMapping("/cmPreOrderVt")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = "/calcOrderPrice.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/confirm.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/inStore.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/reverse.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/cancel.do", method = {RequestMethod.GET})

## LightSpInstallAwardPolicyController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSpInstallAwardPolicyController.java`
- @RequestMapping("lightSpInstallAwardPolicy")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @PostMapping("leaderAudit.do")
- @PostMapping("wxAudit.do")
- @PostMapping("financeAudit.do")
- @PostMapping("enable.do")
- @PostMapping("disable.do")

## LightOperationDepositController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightOperationDepositController.java`
- @RequestMapping("/lightOperationDeposit")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = "/transferConfirmPaid.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/confirmSap.do", method = {RequestMethod.POST})

## LightOverdueListController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightOverdueListController.java`
- @RequestMapping("/lightOverdueList")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @RequestMapping("doExport.do")

## WholeVillageTogetherController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/WholeVillageTogetherController.java`
- @RequestMapping("wholeVillageTogether")
- @RequestMapping("list.html")
- @RequestMapping("detail.html")
- @RequestMapping("doExport.do")
- @RequestMapping("doList.do")

## LightStationRefactorController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationRefactorController.java`
- @RequestMapping("/lightStationRefactor")
- @RequestMapping("list.html")
- @RequestMapping(value = "findBy.do", method = RequestMethod.GET)
- @RequestMapping("doExport.do")

## LightOwnAssetController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightOwnAssetController.java`
- @RequestMapping("/asset")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("export.do")
- @RequestMapping(value = "/importData.do", method = RequestMethod.POST)
- @RequestMapping(value = "/getNodeInfo.do", method = {RequestMethod.POST})
- @RequestMapping(value = "pullData.do", method = {RequestMethod.GET})

## LightCompanyPolicyController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightCompanyPolicyController.java`
- @RequestMapping("/lightCompanyPolicy/")
- @RequestMapping("companyPolicyList.html")
- @RequestMapping("fourItemCompanyPolicyList.html")
- @RequestMapping("companyPolicyList.do")
- @RequestMapping(value = { "leaderAuditOk.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "xiaoweiAuditOk.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "leaderAuditFail.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "xiaoweiAuditFail.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "showLog.do" }, method = { RequestMethod.GET })
- @RequestMapping("/export.do")
- @RequestMapping(value = { "batchAudit.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = {"/update.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/importDataForFourItem.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/enable.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/delete.do"}, method = {RequestMethod.POST})

## LightStationForwordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationForwordController.java`
- @RequestMapping("/lightForword")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightCompanyInfoController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightCompanyInfoController.java`
- @RequestMapping(value = "/light/company")
- @RequestMapping("list.html")
- @GetMapping("queryCompanyList")
- @GetMapping("queryRelateCompanyInfo")
- @PostMapping("updateUserRelatedCompanyCode")
- @RequestMapping("add.html")
- @RequestMapping("detaildate.html")
- @RequestMapping("doList.do")
- @GetMapping("/findMainBankInfo.do")
- @GetMapping("/findProvinceBank.do")
- @GetMapping("/findCityBank.do")
- @GetMapping("/findRegionBank.do")
- @GetMapping("/findHouseBank.do")
- @PostMapping("add.do")
- @RequestMapping(value = {"listProvince.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"listRegion.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = "/confirm.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/updateData", method = {RequestMethod.POST})
- @RequestMapping("finance.html")
- @PostMapping("finance.do")
- @RequestMapping("updateframe.html")
- @PostMapping("updateframe.do")
- @RequestMapping(value = "/initTXRegion.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/initTXTownship.do", method = {RequestMethod.POST})
- @PostMapping("update.do")
- @RequestMapping("doExport.do")
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})

## ZhongYinTradeIncomeSettleController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/ZhongYinTradeIncomeSettleController.java`
- @RequestMapping("/zhongYinTradeIncomeSettle")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @GetMapping("/downTemplate.do")
- @PostMapping("importData.do")
- @RequestMapping("doExport.do")
- @GetMapping("countBatch.do")
- @PostMapping("confirm.do")
- @GetMapping("delete.do")
- @GetMapping("/reverse/downTemplate.do")
- @PostMapping("/reverse/importData.do")

## CmDepositAccountController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmDepositAccountController.java`
- @RequestMapping("/cmDepositAccount/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("/doExport.do")

## LightGvsWarehouseAgeAnalysisController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightGvsWarehouseAgeAnalysisController.java`
- @RequestMapping("/ageAnalysis")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("export.do")
- @RequestMapping("pullData.do")

## LightAuxiliaryPreOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightAuxiliaryPreOrderController.java`
- @RequestMapping("lightAuxiliaryPreOrder")
- @RequestMapping("list.html")
- @RequestMapping("purchaseOrderListForAuxiliary.html")
- @RequestMapping("purchaseOrderDoList.do")
- @RequestMapping("auxiliaryPreOrderDetail.html")
- @PostMapping("doList.do")
- @RequestMapping("doExport.do")

## LightContractInfoController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightContractInfoController.java`
- @RequestMapping("/lightContractInfo")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @PostMapping("addContract.do")

## LightProjectFunnelManagementController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightProjectFunnelManagementController.java`
- @RequestMapping("/lightPfm/")
- @RequestMapping("pfmList.html")
- @RequestMapping("pfmList.do")
- @RequestMapping(value = { "/getBranchCenter.do" }, method = {RequestMethod.GET})
- @RequestMapping("pfmAdd.html")
- @PostMapping("addProject.do")
- @GetMapping("/pfmUpdate.html")
- @GetMapping("/pfmDetail.html")
- @PostMapping("updateProject.do")
- @RequestMapping("doExport.do")

## LightOverduePolicyController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightOverduePolicyController.java`
- @RequestMapping("/lightOverduePolicy")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @RequestMapping("doExport.do")

## OeratingLeasePaymentPeceiptController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/OeratingLeasePaymentPeceiptController.java`
- @RequestMapping("/oeratingLeasePaymentPeceipt")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @PostMapping("queryAssetManagement.do")
- @PostMapping("uploadBill.do")
- @PostMapping("uploadAudit.do")
- @PostMapping("uploadReject.do")

## LightSpPlanConfigController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSpPlanConfigController.java`
- @RequestMapping("/light/sp/planConfig")
- @RequestMapping("list.html")
- @RequestMapping("/doList.do")
- @RequestMapping("/findAll.do")
- @PostMapping("/add.do")
- @RequestMapping(value = { "disableSpPlanConfig.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "enableSpPlanConfig.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "editPlanConfig.do" }, method = { RequestMethod.POST })

## CmLightProjectIncomeConfirmController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmLightProjectIncomeConfirmController.java`
- @RequestMapping("/cmLightProjectIncomeConfirm")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("detail.html")
- @RequestMapping("confirm.html")
- @RequestMapping("confirm.do")
- @RequestMapping("/doExport.do")

## EnergyCapitalDataController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/EnergyCapitalDataController.java`
- @RequestMapping(value = "/energyCapitalData")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("detailList.html")
- @RequestMapping("doDetailList.do")
- @RequestMapping("doExport.do")
- @RequestMapping("doDetailExport.do")

## LightStationNannyEpcController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationNannyEpcController.java`
- @RequestMapping("/lightStationNannyEpc")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @PostMapping("bind.do")
- @RequestMapping("doExport.do")
- @RequestMapping(value = "/examine.do", method = {RequestMethod.POST})

## EpcFadeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/EpcFadeController.java`
- @RequestMapping("ecpData")
- @RequestMapping("list.html")
- @RequestMapping("queryPage")

## CmLightProjectReceiptController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmLightProjectReceiptController.java`
- @RequestMapping("/cmLightProjectReceipt/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("add.html")
- @RequestMapping("add.do")
- @RequestMapping("update.html")
- @RequestMapping("update.do")
- @PostMapping("delete.do")
- @PostMapping("cancel.do")
- @RequestMapping("audit.do")
- @RequestMapping("confirmReceipt.do")
- @GetMapping("getProjectByCode.do")
- @GetMapping("getSepcProjectByCode.do")

## LightHdIncomeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightHdIncomeController.java`
- @RequestMapping("/lightHdIncome")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping("doExport.do")
- @RequestMapping("countByBatchNo.do")
- @RequestMapping(value = {"confirm.do"}, method = {RequestMethod.POST})
- @GetMapping("/reverse/downTemplate.do")
- @PostMapping("/reverse/importData.do")

## LightSpOrderItemController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSpOrderItemController.java`
- @RequestMapping("/lightSpOrderItem")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightOrderUserController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightOrderUserController.java`
- @RequestMapping("/lightOrderUser/")
- @RequestMapping("lightOrderUser.html")
- @RequestMapping("lightOrderUser.do")
- @RequestMapping("doExport.do")

## LightCapitalElectricMonthSumController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightCapitalElectricMonthSumController.java`
- @RequestMapping("/capital/electricMonthSum")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping(value = "/confirm.do", method = {RequestMethod.POST})

## IncomeOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/IncomeOrderController.java`
- @RequestMapping("/incomeOrder/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @PostMapping("delete")
- @PostMapping("add")
- @PostMapping("confirm")

## HuaRongTradeIncomeSettleController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/HuaRongTradeIncomeSettleController.java`
- @RequestMapping("/huaRongTradeIncomeSettle")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @GetMapping("/downTemplate.do")
- @PostMapping("importData.do")
- @RequestMapping("doExport.do")
- @GetMapping("countBatch.do")
- @PostMapping("confirm.do")
- @GetMapping("delete.do")
- @GetMapping("/reverse/downTemplate.do")
- @PostMapping("/reverse/importData.do")

## LightEnableRewardSettleProofController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightEnableRewardSettleProofController.java`
- @RequestMapping("/lightEnableRewardSettleProof")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downloadSettleProofTemplate.do"}, method = {RequestMethod.GET})

## LightUseOrderAgeAnalysisController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightUseOrderAgeAnalysisController.java`
- @RequestMapping("/useOrderAgeAnalysis")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("export.do")

## LightElectricOrderHuarunController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightElectricOrderHuarunController.java`
- @RequestMapping("/lightElectricOrderHuarun")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## EnergyCenterIncomeDayController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/EnergyCenterIncomeDayController.java`
- @RequestMapping("/energyCenterIncomeDay")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightStationOwnerExchangeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationOwnerExchangeController.java`
- @RequestMapping("/lightStationOwnerExchange")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})

## LightCoinDaySumController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightCoinDaySumController.java`
- @RequestMapping("/lightCoinDaySum")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightInventoryAgeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightInventoryAgeController.java`
- @RequestMapping("/lightInventoryAge")
- @RequestMapping("spList.html")
- @RequestMapping("totalList.html")
- @RequestMapping("doSpList.do")
- @RequestMapping("doTotalList.do")
- @RequestMapping("doSpExport.do")
- @RequestMapping("doTotalExport.do")
- @RequestMapping("doTriggerTask.do")
- @RequestMapping("doTriggerTotalTask.do")
- @RequestMapping("inventoryAgeDetailList.html")
- @RequestMapping("doInventoryAgeDetailList.do")
- @RequestMapping("doInventoryAgeDetailExport.do")

## CmReceiptPayController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmReceiptPayController.java`
- @RequestMapping("/cmReceiptPay")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = "/confirmPaid.do", method = {RequestMethod.POST})
- @RequestMapping(value = "cmReceiptIncomeView.html", method = {RequestMethod.GET})
- @RequestMapping(value = "/confirmIncome.do", method = {RequestMethod.POST})

## EnergyInventoryTurnoverControlController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/EnergyInventoryTurnoverControlController.java`
- @RequestMapping("/inventoryTurnover")
- @RequestMapping("skuList.html")
- @RequestMapping("spList.html")
- @RequestMapping("subCenterList.html")
- @RequestMapping("doSkuList.do")
- @RequestMapping("doSpList.do")
- @RequestMapping("doSubCenterList.do")
- @RequestMapping("exportSku.do")
- @RequestMapping("exportSp.do")
- @RequestMapping("exportSubCenter.do")

## LightUseOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightUseOrderController.java`
- @RequestMapping("/lightUseOrder")
- @RequestMapping("list.html")
- @RequestMapping("completeBeforeList.html")
- @RequestMapping("doCompleteBeforeList.do")
- @RequestMapping("doCompleteBeforeExport.do")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightWvRentController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightWvRentController.java`
- @RequestMapping("/lightWvRent")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = "detail.html", method = {RequestMethod.GET})
- @RequestMapping("doExport.do")

## LightConfirmOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightConfirmOrderController.java`
- @RequestMapping("/lightConfirmOrder")
- @RequestMapping("list.html")
- @RequestMapping("auxiliaryList.html")
- @RequestMapping("doList.do")
- @RequestMapping("doAuxiliaryList.do")
- @RequestMapping("doExport.do")
- @RequestMapping("doAuxiliaryExport.do")
- @RequestMapping(value = "confirmOrderView.html", method = {RequestMethod.GET})
- @RequestMapping(value = "confirmOrderDetail.html", method = {RequestMethod.GET})
- @RequestMapping(value = "/makeConfirm.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/quitConfirm.do", method = {RequestMethod.POST})
- @RequestMapping(value = "confirmOrderDetailPre.html", method = {RequestMethod.GET})
- @PostMapping("subCenterAudit.do")
- @RequestMapping("lightAuxiliaryBranchAuditView.html")
- @RequestMapping("hrMakeOrderAuxiliaryAudit.html")
- @GetMapping("hrMakeOrderDetail.html")
- @RequestMapping("lightAuxiliaryMakeOrderDetail.html")
- @PostMapping("auditOk")

## LightProjectRentController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightProjectRentController.java`
- @RequestMapping("/lightProjectRent")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = "detail.html", method = {RequestMethod.GET})
- @RequestMapping("doExport.do")

## LightStationIncomeReverseController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationIncomeReverseController.java`
- @RequestMapping("/lightStationIncomeReverse/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("detail.html")
- @RequestMapping("audit.html")
- @RequestMapping("audit.do")
- @RequestMapping(value = {"/sumByBatchNo.do"}, method = {RequestMethod.POST})
- @GetMapping("/downTemplate.do")
- @PostMapping("importData.do")
- @RequestMapping("/doExport.do")

## FileViewController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/FileViewController.java`
- @RequestMapping("/fileView")
- @RequestMapping("view.html")

## CmPreOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmPreOrderController.java`
- @RequestMapping("/cmPreOrder")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("/doExport.do")
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = "/confirm.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/push", method = {RequestMethod.POST})
- @RequestMapping("listV2.html")
- @RequestMapping("doListV2.do")
- @RequestMapping(value = "/calcOrderPrice.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/confirmV2.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/reject.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/cancel.do", method = {RequestMethod.POST})
- @RequestMapping(value = {"/importDataTest.do"}, method = {RequestMethod.POST})
- @RequestMapping("/doExportV2.do")

## OffLingFlowController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/OffLingFlowController.java`
- @RequestMapping("/OffLingFlow")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping("audit.html")
- @RequestMapping(value = { "/planConfig.do" }, method = {RequestMethod.GET})
- @PostMapping(value = { "passAudit.do" })
- @PostMapping(value = { "rejectAudit.do" })

## EnergySummaryDayController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/EnergySummaryDayController.java`
- @RequestMapping("/energySummaryDay")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightUnionpayMchController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightUnionpayMchController.java`
- @RequestMapping("/lightUnionpayMch/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = "add.html", method = RequestMethod.GET)
- @RequestMapping(value = "edit.html", method = RequestMethod.GET)
- @RequestMapping(value = "detail.html", method = RequestMethod.GET)
- @RequestMapping(value = "add.do", method = RequestMethod.POST)
- @RequestMapping(value = "edit.do", method = RequestMethod.POST)
- @RequestMapping(value = "delete.do", method = RequestMethod.POST)

## YuexiuInteractiveLogController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/YuexiuInteractiveLogController.java`
- @RequestMapping("/yuexiuInteractiveLog")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping("lightStationYuexiuInteractiveLog.html")

## LightAuxiliaryMaterialDepositController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightAuxiliaryMaterialDepositController.java`
- @RequestMapping("/lightAuxiliaryMaterialDeposit")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @RequestMapping("auditList.html")
- @RequestMapping("doAuditList.do")
- @RequestMapping("doAuditExport.do")
- @PostMapping("approveAudit.do")
- @RequestMapping("quotaManagement.html")
- @RequestMapping("doQuotaList.do")
- @RequestMapping("doQuotaExport.do")
- @PostMapping("rejectAudit.do")
- @RequestMapping("flowList.html")
- @RequestMapping("doFlowList.do")
- @RequestMapping("doFlowExport.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @RequestMapping(value = "/freeze.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/release.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/canFreeze.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/confirmPay.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/reject.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/confirmSap.do", method = {RequestMethod.POST})
- @RequestMapping("doExport.do")

## LightSpShareQuotaController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSpShareQuotaController.java`
- @RequestMapping("/lightSpShareQuota")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = { "stop.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/detail.html" }, method = {RequestMethod.GET})
- //    @RequestMapping(value = { "/centerAudit.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/headAudit.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/businessAudit.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/supplyAudit.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/chainAudit.html" }, method = {RequestMethod.GET})
- //    @RequestMapping(value = { "auditCenter.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "auditHead.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "auditBusiness.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "auditSupply.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "auditChain.do" }, method = { RequestMethod.POST })
- @RequestMapping("checkSpShareQuota.do")

## LightStationYuexiuAccountCancelController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationYuexiuAccountCancelController.java`
- @RequestMapping("/lightStationYuexiuAccountCancel/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("add.html")
- @PostMapping("add.do")
- @PostMapping("cancelAudit.do")
- @GetMapping("getCardNumberByPhone.do")
- @PostMapping("audit.do")

## LightSpWithdrawalApplicationController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSpWithdrawalApplicationController.java`
- @RequestMapping("/lightSpWithdrawalApplication")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("add.html")
- @RequestMapping("audit.html")
- @RequestMapping("detail.html")
- @GetMapping("exportDetailPdf.do")
- @GetMapping("detail.do")
- @PostMapping("add.do")
- @PostMapping("edit.do")
- @PostMapping("audit.do")
- @PostMapping("clearSum.do")
- //    @RequestMapping("doExport.do")
- //    @RequestMapping("doExport.do")
- @RequestMapping("doExport.do")
- @GetMapping("terminate.do")
- @GetMapping("doExportDetails.do")

## LightSaleOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSaleOrderController.java`
- @RequestMapping("/lightSaleOrder")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})

## LightStationPolicyIncomeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationPolicyIncomeController.java`
- @RequestMapping("/lightStationPolicyIncome")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping("doExport.do")

## EnergyOverdueInventoryControlController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/EnergyOverdueInventoryControlController.java`
- @RequestMapping("/overdueInventory")
- @RequestMapping("summaryList.html")
- @RequestMapping("subCenterList.html")
- @RequestMapping("skuList.html")
- @RequestMapping("baseList.html")
- @RequestMapping("doSkuList.do")
- @RequestMapping("doSummaryList.do")
- @RequestMapping("doSubCenterList.do")
- @RequestMapping("doBaseList.do")
- @RequestMapping("exportSku.do")
- @RequestMapping("exportSummary.do")
- @RequestMapping("exportSubCenter.do")
- @RequestMapping("exportBase.do")

## LightIncomeRecordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightIncomeRecordController.java`
- @RequestMapping("/lightIncomeRecord")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## lightCapitalRentPaymentlRecordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/lightCapitalRentPaymentlRecordController.java`
- @RequestMapping("/lightCapitalRentPaymentRecord")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping("doExport.do")

## LightSparePartsDepositController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSparePartsDepositController.java`
- @RequestMapping("/lightSparePartsDeposit")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = "/transferConfirmPaid.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/cancelSap.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/fapRecordCreate.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/confirmSap.do", method = {RequestMethod.POST})

## LightZhIncomePriceController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightZhIncomePriceController.java`
- @RequestMapping("/lightZhIncomePrice")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")

## LightWvRentRecordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightWvRentRecordController.java`
- @RequestMapping("/lightWvRentRecord")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @PostMapping("confirm.do")
- @RequestMapping("doExport.do")

## ZhaoYinTradeIncomeSettleController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/ZhaoYinTradeIncomeSettleController.java`
- @RequestMapping("/zhaoYinTradeIncomeSettle")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @GetMapping("/downTemplate.do")
- @PostMapping("importData.do")
- @RequestMapping("doExport.do")
- @GetMapping("countBatch.do")
- @PostMapping("confirm.do")
- @GetMapping("delete.do")
- @GetMapping("/reverse/downTemplate.do")
- @PostMapping("/reverse/importData.do")

## LightSubBuildDataController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSubBuildDataController.java`
- @RequestMapping("/lightSubBuildData")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightStockController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStockController.java`
- @RequestMapping("/lightStock")
- @RequestMapping("list.html")
- @RequestMapping("thirdPartyList.html")
- @RequestMapping("transitList.html")
- @RequestMapping("doList.do")
- @RequestMapping("doThirdPartyList.do")
- @RequestMapping("doTransitList.do")
- @RequestMapping("doExport.do")
- @RequestMapping("doThirdPartyExport.do")
- @RequestMapping("doTransitExport.do")
- @RequestMapping("listForSap.html")
- @RequestMapping("doSapList.do")
- @RequestMapping("doSapListExport.do")

## LightNewMerchantRewardDetailController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightNewMerchantRewardDetailController.java`
- @RequestMapping("/lightNewMerchantRewardDetail/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("detail.html")
- @RequestMapping("doExport.do")

## LightEnableRewardSettleProofDetailController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightEnableRewardSettleProofDetailController.java`
- @RequestMapping("/lightEnableRewardSettleProofDetail")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @GetMapping("detail.do")
- @RequestMapping("doExport.do")

## LightAccountController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightAccountController.java`
- @RequestMapping("/lightAccount")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})

## LightInstantRewardPolicyMonthController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightInstantRewardPolicyMonthController.java`
- @RequestMapping("/lightInstantRewardPolicyMonth")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping("doExport.do")

## CmLightProjectFinishController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmLightProjectFinishController.java`
- @RequestMapping("/cmLightProjectFinish")
- @RequestMapping("list.html")
- @RequestMapping("/doList.do")
- @RequestMapping("add.html")
- @RequestMapping("/queryProjectData.do")
- @RequestMapping("next.html")
- @RequestMapping("add.do")
- @RequestMapping("update.html")
- @RequestMapping("update.do")
- @RequestMapping("detail.html")
- @RequestMapping("audit.html")
- @RequestMapping("audit.do")
- @RequestMapping("delete.do")
- @RequestMapping("/doExport.do")

## LightNewMerchantRewardController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightNewMerchantRewardController.java`
- @RequestMapping("/lightNewMerchantReward/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("detail.html")

## LightShareBillController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightShareBillController.java`
- @RequestMapping("/lightShareBill")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @PostMapping("batchFinanceAudit.do")
- @PostMapping("batchChainleadAudit.do")
- @RequestMapping("doExport.do")

## LightInstantGridRewardItemController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightInstantGridRewardItemController.java`
- @RequestMapping("/lightInstantGridRewardItem")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping("doExport.do")

## LightStationSettleSumController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationSettleSumController.java`
- @RequestMapping("/lightStationSettleSum")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightSpController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSpController.java`
- @RequestMapping("/lightSp/")
- @RequestMapping("spList.html")
- @RequestMapping("spList.do")
- @RequestMapping("branchSpList.html")
- @RequestMapping("branchSpList.do")
- @RequestMapping(value = {"/listYearMonth.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"auditOk.do"}, method = {RequestMethod.POST})
- @PostMapping("updateModeForProvider.do")
- @RequestMapping(value = {"auditFail.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"secondAuditOk.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"secondAuditFail.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"finalAuditOk.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"finalAuditFail.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/showContract.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"pushSpContract.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"pushSpLnContract.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"tmpSignSpContract.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/findSpRegion.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"changeOpSum.do"}, method = {RequestMethod.POST})
- @RequestMapping("spAuthRegion.html")
- @RequestMapping("spRegionList.do")
- @RequestMapping("spRegionExport.do")
- @RequestMapping(value = {"/showRegionContract.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"auditRegionOk.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"auditRegionFail.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"createGridAwardAgreement.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"queryGridAwardAgreement.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"createNewMaster.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"queryNewMaster.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"queryLimit.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"freezeDocumentEntry.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"unfreezeDocumentEntry.do"}, method = {RequestMethod.POST})
- @RequestMapping("doExport.do")
- @GetMapping("/getSpList.do")
- @RequestMapping(value = {"auditValid.do"}, method = {RequestMethod.POST})
- @RequestMapping("epcSpList.html")
- @RequestMapping("epcSpList.do")
- @RequestMapping("doEpcExport.do")
- @RequestMapping(value = {"epcSpAuditOk.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"epcSpAuditFail.do"}, method = {RequestMethod.POST})
- @RequestMapping("epcSpAudit.html")
- @RequestMapping(value = {"quarterList.do"}, method = {RequestMethod.GET})
- @PostMapping("queryContractRecord.do")
- @PostMapping("refundDeposit.do")
- @GetMapping("/streetList.do")
- @PostMapping("/updateStreet.do")
- @RequestMapping(value = "/monthScale.do", method = {RequestMethod.POST})
- @PostMapping(value = "/querySp.do")

## LightModuleSnController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightModuleSnController.java`
- @RequestMapping("/lightModuleSn")
- @RequestMapping("list.html")
- @GetMapping("queryPage")
- @RequestMapping("doList.do")
- @RequestMapping(value = "/delete", method = {RequestMethod.POST})

## LightRentController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightRentController.java`
- @RequestMapping("/lightRent")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping(value = "detail.html", method = {RequestMethod.GET})
- @RequestMapping(value = "/stationUserImport.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/stationRepayPlanImport.do", method = {RequestMethod.POST})

## LightStationElecController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationElecController.java`
- @RequestMapping("/lightStationElec")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- //    @RequestMapping("doExportOld.do")
- @RequestMapping("doExport.do")
- //    @RequestMapping("doExportMonth.do")
- @RequestMapping("doExportMonth.do")
- @RequestMapping(value = "getStateSum.do", method = {RequestMethod.GET})
- @RequestMapping(value = "getStatusSum.do", method = {RequestMethod.GET})
- @RequestMapping("detail.html")
- @RequestMapping(value = "dayChart.do", method = {RequestMethod.GET})
- @RequestMapping(value = "monthChart.do", method = {RequestMethod.GET})
- @RequestMapping(value = "yearChart.do", method = {RequestMethod.GET})
- @RequestMapping(value = "totalChart.do", method = {RequestMethod.GET})
- @RequestMapping(value = "updateFirstThreePowerAt.do", method = {RequestMethod.GET})

## LightSpOrderCenterController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSpOrderCenterController.java`
- @RequestMapping("/lightSpOrderCenter")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("forceAdd.html")
- @RequestMapping(value = {"/projectAudit.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"audit.do"}, method = {RequestMethod.POST})
- @RequestMapping("orderCenterDetail.html")
- @RequestMapping("doExport.do")
- @GetMapping("branchSpList.do")
- @GetMapping("findSpById.do")
- @RequestMapping(value = {"findType.do"}, method = {RequestMethod.GET})
- @GetMapping("/findByType.do")
- @PostMapping("forceAdd.do")
- @RequestMapping(value = {"forceCancel.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"confirmPayType.do"}, method = {RequestMethod.POST})

## LightSpStoreController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSpStoreController.java`
- @RequestMapping("/lightSpStore")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping(value = { "enableStore.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "enableThirdPartyStore.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "disableStore.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "disableAddress.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "enableAddress.do" }, method = { RequestMethod.POST })
- @PostMapping("add.do")
- @RequestMapping(value = {"/update.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = { "showLog.do" }, method = { RequestMethod.GET })
- @PostMapping("updateThird.do")
- @RequestMapping(value = "/get.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/getBySpIdAndRegionId.do", method = {RequestMethod.GET})
- @RequestMapping("secondClassStoreList.html")
- @RequestMapping("secondClassStoreList.do")
- @RequestMapping("doSecondClassStoreExport.do")
- @RequestMapping(value = { "findAllStoreBySpId.do" }, method = { RequestMethod.GET })

## LightSpUnionpayRentController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSpUnionpayRentController.java`
- @RequestMapping("/lightSpUnionpayRent")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("change.do")
- @PostMapping("uploadImg.do")
- @RequestMapping(value = {"/importVisit.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping("doExport.do")
- @RequestMapping("doExportWaitVisit.do")

## LightProjectElectricOrderYxController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightProjectElectricOrderYxController.java`
- @RequestMapping("/lightProjectElectricOrder/yx")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping(value = "/confirmAll.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/confirmPaidAll.do", method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = "/deleteAll.do", method = {RequestMethod.POST})

## LightSpStaffController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSpStaffController.java`
- @RequestMapping("/lightSpStaff")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("/doExport.do")

## EnergyLightEstimateController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/EnergyLightEstimateController.java`
- @RequestMapping(value = "/EnergyLightEstimate")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("detail.html")

## LightShareBillAuditLogController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightShareBillAuditLogController.java`
- @RequestMapping("/lightShareBillAuditLog")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("change.do")
- @PostMapping("add.do")

## LightCapitalStationManageController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightCapitalStationManageController.java`
- @RequestMapping("/capital")
- @RequestMapping("/station/list.html")
- @RequestMapping("/station/doList.do")
- @RequestMapping("/inveter/list.html")
- @RequestMapping("/inveter/doList.do")
- @RequestMapping("/rent/list.html")
- @RequestMapping("/rent/doList.do")
- @RequestMapping(value = "/rent/detail.html", method = {RequestMethod.GET})
- @RequestMapping("/unionpayRent/list.html")
- @RequestMapping("/unionpayRent/doList.do")
- @RequestMapping(value = "/unionpayRent/detail.html", method = {RequestMethod.GET})
- @RequestMapping("doExport.do")
- @RequestMapping("/inveter/doExport.do")

## LightStationBackPolicyChangeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationBackPolicyChangeController.java`
- @RequestMapping("/lightStationBackPolicyChange")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping("doExport.do")

## LightSupplierContractsController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSupplierContractsController.java`
- @RequestMapping("/lightSupplierContracts")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping("doExport.do")

## LightSpGridAwardOrderDetailController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSpGridAwardOrderDetailController.java`
- @RequestMapping("lightSpGridAwardOrderDetail")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightAwardAppealController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightAwardAppealController.java`
- @RequestMapping("/lightAwardAppeal/")
- @RequestMapping("lightAwardAppealList.html")
- @RequestMapping("doList.do")
- @RequestMapping("subCenterAudit.html")
- @RequestMapping("marketLeaderAudit.html")
- @RequestMapping("technicalAudit.html")
- @RequestMapping("xiaoweiAudit.html")
- @RequestMapping(value = {"subCenterAudit.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"marketLeaderAudit.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"technicalAudit.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"xiaoweiAudit.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"showLog.do"}, method = {RequestMethod.GET})
- @RequestMapping("detail.html")

## CmConstructionProgressController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmConstructionProgressController.java`
- @RequestMapping("/cmConstructionProgress")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("detail.html")
- @RequestMapping("audit.html")
- @RequestMapping("audit.do")
- @RequestMapping("/doExport.do")

## LightSpInspireController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSpInspireController.java`
- @RequestMapping("/lightSpInspire/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @GetMapping("getSpCode.do")
- @PostMapping("add.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/del.do"}, method = {RequestMethod.POST})
- @PostMapping("batchAudit.do")
- @RequestMapping(value = "/export.do", method = RequestMethod.GET)
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @PostMapping("auditOne.do")
- @PostMapping("auditTwo.do")
- @PostMapping("auditThree.do")
- @PostMapping("update.do")
- @PostMapping("getDetail.do")

## LightRentRecordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightRentRecordController.java`
- @RequestMapping("/lightRentRecord")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightProjectElectricInvoiceReverseRecordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightProjectElectricInvoiceReverseRecordController.java`
- @RequestMapping("/electric/invoice/reverse/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("detail.html")
- @RequestMapping("add.html")
- @RequestMapping("add.do")
- @RequestMapping("edit.html")
- @RequestMapping("edit.do")
- @RequestMapping("audit.html")
- @RequestMapping("auditPass.do")
- @RequestMapping("auditReject.do")
- @RequestMapping("getById.do")
- @RequestMapping(value = {"delete.do"}, method = {RequestMethod.POST})
- @RequestMapping("update.do")
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping("doExport.do")
- @RequestMapping("getOriginInvoiceInfoByInvoiceNumber.do")
- @RequestMapping("getOriginInvoiceInfoByBatchNoAndInvoiceNo.do")
- @RequestMapping("getTemplateByCode.do")
- @RequestMapping("findFinanceAuditSummaryByInvoiceNumbers.do")
- @RequestMapping("batchFinanceAudit.do")

## LightFreezeSettleController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightFreezeSettleController.java`
- @RequestMapping("/lightFreeze/")
- @RequestMapping("list.html")
- @PostMapping("freezeSettleList.do")
- @PostMapping("addFreezeSettle.do")
- @PostMapping("auditFreezeSettle.do")
- @RequestMapping("detail.html")
- @RequestMapping("getSerialLsit.do")
- @RequestMapping("doExport.do")
- @PostMapping("deleteFreezeSettle.do")

## LightSkuDataController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSkuDataController.java`
- @RequestMapping("/lightSku")
- @RequestMapping("skuList.html")
- @RequestMapping("skuList.do")
- @RequestMapping(value = { "addSkuData.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = {"editSkuData.do"}, method = { RequestMethod.POST })
- @RequestMapping(value = { "enableSkuData.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "disableSkuData.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = "doExport.do")
- @RequestMapping(value = "/importData.do", method = RequestMethod.POST)
- @RequestMapping(value = "/getSkuData.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/getAllSkuData.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/pushDataToRrs.do", method = {RequestMethod.POST})
- @RequestMapping(value = {"updatePaymentTerms.do"}, method = { RequestMethod.POST })

## LightCalculateIncomeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightCalculateIncomeController.java`
- @RequestMapping("/lightCalculate")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightProjectElectricEpcWhiteListController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightProjectElectricEpcWhiteListController.java`
- @RequestMapping("/lightProjectElectricEpcWhiteList")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping("doExport.do")

## LightSpQuotaDedicatedController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSpQuotaDedicatedController.java`
- @RequestMapping("/lightSpQuotaDedicated")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("add.html")
- @PostMapping("add.do")
- @RequestMapping("detail.html")
- @RequestMapping(value = {"/configsPT.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/configsZJ.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/logList.do"}, method = {RequestMethod.GET})
- @RequestMapping("steepAudit.html")
- @PostMapping("steepAudit.do")
- @RequestMapping("xwAudit.html")
- @PostMapping("xwAudit.do")

## CmSimplePreOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmSimplePreOrderController.java`
- @RequestMapping("/cmSimplePreOrder/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("apply.html")
- @GetMapping("getProjectByCode.do")
- @RequestMapping(value = "/findSkuList.do")
- @RequestMapping(value = "/createOrder.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/signOrder.do", method = {RequestMethod.POST})
- @RequestMapping("/doExport.do")

## LightProjectManagementController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightProjectManagementController.java`
- @RequestMapping("/lightPm/")
- @RequestMapping("pmList.html")
- @RequestMapping(value = { "/projectCompany.do" }, method = {RequestMethod.GET})
- @RequestMapping("pmList.do")
- @RequestMapping("pmAdd.html")
- @GetMapping("/getProjectCompany.do")
- @GetMapping("/getProjectCompanyByRegionId.do")
- @RequestMapping(value = { "/listPhaseYear.do" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "addProject.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "updateProject.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/projectDetail.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = {"/logs.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = { "/projectAuditZx.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/projectAuditSc.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/projectAuditXw.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/projectAuditCw.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "auditProjectZx.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "auditProjectSc.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "auditProjectXw.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "auditProjectCw.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/getProjectDetail.do" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/projectEdit.html" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "removePm.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "confirmProjectFinished.do" }, method = { RequestMethod.POST })
- @RequestMapping("doExport.do")

## LightProfitController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightProfitController.java`
- @RequestMapping("/lightProfit")
- @GetMapping("/createProfit")
- @GetMapping("/createProfitAll")

## LightStockChangeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStockChangeController.java`
- @RequestMapping("/lightStockChange")
- @RequestMapping("list.html")
- @RequestMapping("thirdPartyList.html")
- @RequestMapping("transitList.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping("sapChangeList.html")
- @RequestMapping("doSapList.do")
- @RequestMapping("doSapExportList.do")

## CmbLeasingReworkFileController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmbLeasingReworkFileController.java`
- @RequestMapping("/cmbLeasingReworkFile")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping("doExport.do")

## LightGreenIncomeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightGreenIncomeController.java`
- @RequestMapping("/lightGreenIncome")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @PostMapping("confirm.do")
- @PostMapping("cancel.do")
- @RequestMapping("doExport.do")
- @GetMapping("calcIncomesTotal.do")
- @PostMapping("batchConfirm.do")
- @RequestMapping("/batch/list.html")
- @RequestMapping("/batch/doList.do")
- @RequestMapping("checkBatchConfirmByMajorMaterial.do")
- @RequestMapping("batchConfirmByMajorMaterial.do")

## LightFundSettleController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightFundSettleController.java`
- @RequestMapping("/lightFundSettle")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping("doExport.do")
- @GetMapping("/reverse/downTemplate.do")
- @PostMapping("/reverse/importData.do")
- @RequestMapping("add.html")
- @RequestMapping("getSku.do")
- @RequestMapping(value = {"confirm.do"}, method = {RequestMethod.POST})
- @GetMapping("delete.do")

## LightStationInsuranceController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationInsuranceController.java`
- @RequestMapping("/lightStationInsurance")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @GetMapping("/downTemplate.do")
- @PostMapping("/importData.do")
- @PostMapping("uploadInsuranceFile.do")
- @PostMapping("/abolishedInsurance")
- @PostMapping("/rePushYuexiuInsuranceRenewal")

## LightSpOrderFinanceController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSpOrderFinanceController.java`
- @RequestMapping("/lightSpOrderFinance")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("orderFinanceDetail.html")
- @RequestMapping(value = {"/financeAudit.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"audit.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"confirm.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/querySpOrderTotalInfo.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"batchConfirm.do"}, method = {RequestMethod.POST})
- @RequestMapping("doExport.do")
- @RequestMapping(value = {"/forceAudit.html"}, method = {RequestMethod.GET})
- @PostMapping(value = {"/forceFinanceAudit.do"})
- @RequestMapping(value = "/fapRecordCreate.do", method = {RequestMethod.POST})

## PyInvoiceController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/PyInvoiceController.java`
- @RequestMapping("/pyInvoice")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("export.do")
- @RequestMapping(value = "/importData.do", method = RequestMethod.POST)
- @RequestMapping(value = "/batchConfirm.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/batchDelete.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/batchRePush.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/update.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/count.do", method = {RequestMethod.POST})

## LightInstantGridRewardController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightInstantGridRewardController.java`
- @RequestMapping("/lightInstantGridReward")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping("doExport.do")

## LightHighElecController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightHighElecController.java`
- @RequestMapping("/lightHighElec/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @PostMapping("confirm")
- @RequestMapping("detail.html")

## LightConstructionTeamController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightConstructionTeamController.java`
- @RequestMapping("/lightConstruction/")
- @RequestMapping("lightConTeam.html")
- @RequestMapping("lightConTeam.do")
- @RequestMapping("doExport.do")

## LightStationAmmeterController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationAmmeterController.java`
- @RequestMapping("/lightStationAmmeter")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downloadAmmeterError.do"}, method = {RequestMethod.GET})
- @RequestMapping("doExport.do")

## LightProjectFapRecordOfReceiptsController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightProjectFapRecordOfReceiptsController.java`
- @RequestMapping("/lightProjectFapRecordOfReceipts/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @PostMapping(value = {"/addVppFapRecord.do"})
- @GetMapping(value = {"/queryVppFapRecord.do"})
- @PostMapping(value = {"/cancelVppFapRecord.do"})

## LightComponentLibraryController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightComponentLibraryController.java`
- @RequestMapping("/lightComponentLibrary")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping("doExport.do")

## LightStationRentDeductController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationRentDeductController.java`
- @RequestMapping("/lightStationRentDeduct")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doCount.do")
- @RequestMapping("doExport.do")
- @RequestMapping("importData.do")
- @RequestMapping("doConfirm.do")
- @RequestMapping("doDel.do")

## ReviewMaterialController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/ReviewMaterialController.java`
- @RequestMapping("/reviewMaterial")
- @RequestMapping("reviewList.html")
- @RequestMapping("doReviewList.do")
- @RequestMapping("doExport.do")
- @RequestMapping(value = "showMaterial.do", method = { RequestMethod.GET })
- @RequestMapping("auditDetail.html")
- @RequestMapping(value = { "materialAuditOk.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "materialAuditFail.do" }, method = { RequestMethod.POST })

## ElectricCompetePriceInfoController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/ElectricCompetePriceInfoController.java`
- @RequestMapping("/electricCompete")
- @RequestMapping("priceInfoList.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping(value = {"/downloadTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping("importData.do")
- @RequestMapping("audit.do")
- @RequestMapping("batchAudit.do")

## LightSubStockChangeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSubStockChangeController.java`
- @RequestMapping("/lightSubStockChange")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightCenterPriceController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightCenterPriceController.java`
- @RequestMapping("/lightCenterPrice/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")

## LightStoreAddressController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStoreAddressController.java`
- @RequestMapping("/lightStoreAddress")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping(value = {"pass.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"reject.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"batchPassForSubCenter.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"batchRejectForSubCenter.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"batchPassForSupplyChain.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"batchRejectForSupplyChain.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"update.do"}, method = {RequestMethod.POST})

## LightStationSkillController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationSkillController.java`
- @RequestMapping("/lightStationSkill")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping("detail.html")
- @RequestMapping("audit.html")
- @RequestMapping(value = { "/planConfig.do" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/getLastRejectReason.do" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "materialAuditOk.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "materialAuditFail.do" }, method = { RequestMethod.POST })

## LightBusinessCustomerController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightBusinessCustomerController.java`
- @RequestMapping("/lightBusinessCustomer")
- @RequestMapping("list.html")
- @RequestMapping("/doList.do")
- @RequestMapping("add.html")
- @PostMapping("add.do")
- @RequestMapping("addProgress.html")
- @PostMapping("addProgress.do")
- @RequestMapping("findProgress.html")
- @RequestMapping("/doExport.do")
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})

## LightZhSettleController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightZhSettleController.java`
- @RequestMapping("/lightZhSettle")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping("doExport.do")
- @GetMapping("/reverse/downTemplate.do")
- @PostMapping("/reverse/importData.do")
- @RequestMapping("add.html")
- @RequestMapping("getSku.do")
- @RequestMapping(value = {"confirm.do"}, method = {RequestMethod.POST})
- @GetMapping("delete.do")

## LightStationWhiteListController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationWhiteListController.java`
- @RequestMapping("/lightStationWhiteList")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightCompanyManageRegionController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightCompanyManageRegionController.java`
- @RequestMapping("/lightCompanyManageRegion")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("processAudi.html")
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/areas.do"}, method = {RequestMethod.GET})
- @PostMapping("audiStatus.do")
- @RequestMapping("detail.html")
- @RequestMapping(value = {"/logs.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = "/enableData.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/detailEnableData.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/disableData.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/detailDisableData.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/logicDelete.do", method = {RequestMethod.POST})
- @RequestMapping("doExport.do")

## LightOverdueBlackListAuditLogController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightOverdueBlackListAuditLogController.java`
- @RequestMapping("/lightOverdueBlackListAuditLog")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("change.do")
- @PostMapping("add.do")

## LightSubOperationDataController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSubOperationDataController.java`
- @RequestMapping("/lightSubOperationData")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightSubSpController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSubSpController.java`
- @RequestMapping("/lightSubSp")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("/doExport.do")

## LightEnablePolicyController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightEnablePolicyController.java`
- @RequestMapping("/lightEnablePolicy/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("add.html")
- @PostMapping("add.do")
- @RequestMapping("detail.html")
- @RequestMapping("steepAudit.html")
- @PostMapping("batchSteepAudit.do")
- @RequestMapping("xwAudit.html")
- @PostMapping("batchXwAudit.do")
- @RequestMapping("financeAudit.html")
- @PostMapping("batchFinanceAudit.do")
- @PostMapping("steepAudit.do")
- @PostMapping("xwAudit.do")
- @PostMapping("financeAudit.do")
- @RequestMapping(value = {"/areas.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/nodeProp.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/items.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/logs.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/listProvince.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/listRegion.do"}, method = {RequestMethod.GET})
- @GetMapping("edit.html")
- @PostMapping("updatePolicy.do")
- @RequestMapping(value = {"cancel.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping("doExport.do")
- @RequestMapping("doExports.do")

## LightStationImgsController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationImgsController.java`
- @RequestMapping("/lightStationImgs")
- @RequestMapping("list.html")
- @RequestMapping("audit.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = {"delete.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"saveImgsTemp.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"audit.do"}, method = {RequestMethod.POST})
- @RequestMapping("stationImgsEdit.html")

## LightProjectElectricOrderStationController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightProjectElectricOrderStationController.java`
- @RequestMapping("/lightProjectElectricOrderStation")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightStationRepurchaseController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationRepurchaseController.java`
- @RequestMapping("/lightStationRepurchase")
- @RequestMapping("list.html")
- @RequestMapping("/doList.do")
- @RequestMapping("detail.html")
- @RequestMapping("audit.html")
- @RequestMapping("doAudit.do")
- @RequestMapping("/doExport.do")
- @RequestMapping("transferConfirm/list.html")
- @RequestMapping("transferConfirm/doList.do")
- @RequestMapping("transferConfirm/doExport.do")
- @RequestMapping("depositConfirm/list.html")
- @RequestMapping("depositConfirm/doList.do")
- @RequestMapping("depositConfirm/doExport.do")
- @RequestMapping("/financeConfrim.do")
- @GetMapping("findDepositBalance.do")
- @RequestMapping("/depositDeduct/list.html")
- @RequestMapping("/depositDeduct/doList.do")
- @RequestMapping("/depositDeduct/doExport.do")
- @RequestMapping("forceAdd.html")
- @RequestMapping("nextStep.html")
- @GetMapping("/findAddEcho.do")
- @RequestMapping("editforce.html")
- @RequestMapping("choosePay.html")
- @PostMapping("/cancel.do")
- @PostMapping(value = { "queryMdmCustom.do" })
- @PostMapping("/insertForce.do")
- @PostMapping(value = { "confirmPayType.do" })
- @RequestMapping("/deduction/list.html")
- @RequestMapping("/deduction/doList.do")
- @RequestMapping("/deduction/doExport.do")
- @RequestMapping("forceSoldAudit.html")
- @RequestMapping("doForceSoldAudit.do")
- @RequestMapping("uploadEamFile.do")
- @RequestMapping("doFinalForceSoldAudit.do")
- @RequestMapping(value = "/transferConfirm/fapRecordCreate.do", method = {RequestMethod.POST})

## LightBillFunnelDataController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightBillFunnelDataController.java`
- @RequestMapping("/lightBillFunnelData")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @RequestMapping("doExport.do")

## LightImageVerifyController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightImageVerifyController.java`
- @RequestMapping("/lightImage")
- @GetMapping("findOriginalImage.do")

## LightCmEpcStationBussinessController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightCmEpcStationBussinessController.java`
- @RequestMapping("lightCmEpcStationBussiness")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("audit.html")
- @RequestMapping(value = {"auditOk.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"auditFail.do"}, method = {RequestMethod.POST})
- @RequestMapping("doExport.do")

## LightElectricMonthSumController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightElectricMonthSumController.java`
- @RequestMapping("/lightElectricMonthSum")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping(value = "/confirmPaid.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/confirmIncome.do", method = {RequestMethod.POST})

## LightCapitalElectricOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightCapitalElectricOrderController.java`
- @RequestMapping("/capital/electricOrder")
- @RequestMapping("/list.html")
- @RequestMapping("/doList.do")
- @RequestMapping("doExport.do")

## lightStationNannyController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/lightStationNannyController.java`
- @RequestMapping("/lightStationNanny")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @PostMapping("bind.do")
- @RequestMapping(value = "/examine.do", method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})

## CmReportController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmReportController.java`
- @RequestMapping("/cmReport")
- @RequestMapping("/projectProgress/list.html")
- @RequestMapping("/projectProgress/doList.do")
- @RequestMapping("/projectProgress/doExport.do")
- @RequestMapping("/incomeProgress/list.html")
- @RequestMapping("/incomeProgress/doList.do")
- @RequestMapping("/incomeProgress/doExport.do")
- @RequestMapping("/incomeItem/list.html")
- @RequestMapping("/incomeItem/doList.do")
- @RequestMapping("/incomeItem/doExport.do")
- @RequestMapping("/investorPayment/list.html")
- @RequestMapping("/investorPayment/doList.do")
- @RequestMapping("/investorPaymentItem/list.html")
- @RequestMapping("/investorPaymentItem/doList.do")
- @RequestMapping("/investorPayment/doExport.do")
- @RequestMapping("/investorPaymentItem/doExport.do")
- @RequestMapping("/projectLifeCycle/list.html")
- @RequestMapping("/projectLifeCycle/doList.do")
- @RequestMapping("/projectLifeCycle/doTotalList.do")
- @RequestMapping("/projectLifeCycle/doExport.do")
- @RequestMapping("/signScale/list.html")
- @RequestMapping("/signScale/doList.do")
- @RequestMapping("/signScale/getTotal.do")
- @RequestMapping("/signScale/doExport.do")
- @RequestMapping("/actualIncome/list.html")
- @RequestMapping("/actualIncome/doList.do")
- @RequestMapping("/actualIncome/getTotal.do")
- @RequestMapping("/actualIncome/doExport.do")
- @RequestMapping("/engineeringManagerPerf/list.html")
- @RequestMapping("/engineeringManagerPerf/doList.do")
- @RequestMapping("/engineeringManagerPerf/getTotal.do")
- @RequestMapping("/engineeringManagerPerf/doExport.do")
- @RequestMapping("/projectIncomeCostLedger/list.html")
- @RequestMapping("/projectIncomeCostLedger/doList.do")
- @RequestMapping("/projectIncomeCostLedger/doExport.do")

## CmLightProjectIncomePolicyController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmLightProjectIncomePolicyController.java`
- @RequestMapping("/cmLightProjectIncomePolicy/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("detail.html")
- @RequestMapping("update.html")
- @RequestMapping("update.do")
- @RequestMapping("findItem.do")
- @RequestMapping("findIncomeNodeList.do")
- @RequestMapping("getProjectByCode.do")
- @RequestMapping("importPolicy.do")
- @RequestMapping("delete.do")
- @RequestMapping("audit.html")
- @RequestMapping("audit.do")
- @RequestMapping("downloadTemplate.do")

## LightOverduePolicyAreaController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightOverduePolicyAreaController.java`
- @RequestMapping("/lightOverduePolicyArea")
- @RequestMapping("list.html")
- @RequestMapping("LightOverduePolicyAreaDetailList.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping("doExport.do")

## LightAuxiliaryMaterialPlanConfigController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightAuxiliaryMaterialPlanConfigController.java`
- @RequestMapping("/light/material/planConfig")
- @RequestMapping("auxiliaryMaterialPlanConfig.html")
- @RequestMapping("/doList.do")
- @RequestMapping(value = { "/addMaterialPlanConfig.do" }, method = { RequestMethod.POST })
- @RequestMapping("auxiliaryMaterialPlanConfigDetailInfo.html")
- @GetMapping("/findByNoPage.do")

## CmLightProjectSignInfoController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmLightProjectSignInfoController.java`
- @RequestMapping("/cmLightProjectSignInfo")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("add.do")
- @RequestMapping("update.do")
- @RequestMapping("detail.do")
- @RequestMapping("audit.do")
- @GetMapping("getAttachmentTemplateList.do")

## LightCapitalInvoiceTemplateController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightCapitalInvoiceTemplateController.java`
- @RequestMapping("/lightCapitalInvoiceTemplate")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @PostMapping("audit.do")
- @PostMapping("uploadFile.do")
- @RequestMapping("doExport.do")

## lightStationNannyUserController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/lightStationNannyUserController.java`
- @RequestMapping("/lightStationNannyUser")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## CmProductionValueReportController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmProductionValueReportController.java`
- @RequestMapping("/cmPvReport")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("/doExport.do")

## LightSubBaseDataController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSubBaseDataController.java`
- @RequestMapping("/lightSubBaseData")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightCapitalRentPaymentController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightCapitalRentPaymentController.java`
- @RequestMapping("/lightCapitalRentPayment")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## CmStockController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmStockController.java`
- @RequestMapping("/cmStock/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("/doExport.do")
- @RequestMapping("/change/list.html")
- @RequestMapping("/change/doList.do")
- @RequestMapping("/change/doExport.do")

## LightSpUnionpayRentRecordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSpUnionpayRentRecordController.java`
- @RequestMapping("/lightSpUnionpayRentRecord")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("change.do")
- @PostMapping("add.do")

## LightDccCompanyModifyController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightDccCompanyModifyController.java`
- @RequestMapping("/lightDccCompanyModify")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")

## LightStationEnableRewardCacheController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationEnableRewardCacheController.java`
- @RequestMapping("/lightStationEnableRewardCache")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @GetMapping("detail.do")
- @RequestMapping("doExport.do")
- @RequestMapping(value = {"deal.do"}, method = {RequestMethod.POST})

## LightTransferSpApplyController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightTransferSpApplyController.java`
- @RequestMapping("/lightTransferSpApply")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("detail.html")
- @RequestMapping("audit.html")
- @RequestMapping("findSp.do")
- @RequestMapping("doAudit.do")
- @RequestMapping("batchAudit.do")
- @RequestMapping("/doExport.do")
- @RequestMapping("findStore.do")
- @RequestMapping("doSubList.do")
- @RequestMapping(value = "/getZoneBySpIdAndStoreId.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/getZoneById.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/check30Days.do", method = {RequestMethod.GET})

## LightElectTargetController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightElectTargetController.java`
- @RequestMapping("/lightElectTarget/")
- @RequestMapping("list.html")
- @RequestMapping("etAdd.html")
- @RequestMapping("etUpdate.html")
- @RequestMapping(value = "etList.do")
- @RequestMapping(value = "etDetail.do", method = {RequestMethod.GET})
- @RequestMapping(value = "etAdd.do", method = {RequestMethod.POST})
- @RequestMapping(value = "etUpdate.do", method = {RequestMethod.PUT})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @GetMapping("/downTemplate.do")

## CmProductionValueIncomeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmProductionValueIncomeController.java`
- @RequestMapping("/cmProductionValueIncome")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("detail.html")
- @GetMapping("getAddPreInfo.do")
- @RequestMapping("add.html")
- @RequestMapping("add.do")
- @RequestMapping("update.html")
- @RequestMapping("update.do")
- @PostMapping("delete.do")
- @PostMapping("reverse.do")
- @RequestMapping("audit.html")
- @RequestMapping("audit.do")
- @RequestMapping("/doExport.do")

## LightInvoiceTemplateController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightInvoiceTemplateController.java`
- @RequestMapping("/lightInvoiceTemplate")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @PostMapping("add.do")
- @PostMapping("change.do")
- @PostMapping("audit.do")
- @PostMapping("del.do")
- @PostMapping("uploadFile.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping("doExport.do")

## RepairTransferLogController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/RepairTransferLogController.java`
- @RequestMapping("repairTransferLog")

## LightCapitalProjectElectricOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightCapitalProjectElectricOrderController.java`
- @RequestMapping("/capital/projectElectricOrder")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping(value = "/confirmAll.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/confirmPaidAll.do", method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})

## LightSpServiceProvinceController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSpServiceProvinceController.java`
- @RequestMapping("/lightSpServiceProvince/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @PostMapping("audit.do")
- @RequestMapping("doExport.do")
- @RequestMapping(value = {"/logList.do"}, method = {RequestMethod.GET})

## DatabaseManagementController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/DatabaseManagementController.java`
- @RequestMapping("/databaseManagement")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = { "add.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = "/del", method = {RequestMethod.POST})
- @RequestMapping(value = "/upate", method = {RequestMethod.POST})

## CmProjectFinalAcceptanceController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmProjectFinalAcceptanceController.java`
- @RequestMapping("/cmProjectFinalAcceptance")
- @RequestMapping("list.html")
- @RequestMapping("/doList.do")
- @RequestMapping("add.html")
- @RequestMapping("/queryProjectData.do")
- @RequestMapping("next.html")
- @RequestMapping("add.do")
- @RequestMapping("update.html")
- @RequestMapping("update.do")
- @RequestMapping("detail.html")
- @RequestMapping("audit.html")
- @RequestMapping("audit.do")
- @RequestMapping("delete.do")
- @RequestMapping("/doExport.do")

## EaiOpenController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/EaiOpenController.java`
- @RequestMapping("/eaiopen/")
- @RequestMapping("eaiOpenList.html")
- @RequestMapping("eaiOpenList.do")
- @RequestMapping(value = { "enableEaiOpen.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "disableEaiOpen.do" }, method = { RequestMethod.POST })
- @RequestMapping("eaiOpenAdd.html")
- @RequestMapping(value = { "addEaiOpen.do" }, method = { RequestMethod.POST })

## CmLightProjectIncomeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmLightProjectIncomeController.java`
- @RequestMapping("/cmLightProjectIncome/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("add.html")
- @RequestMapping("add.do")
- @RequestMapping("detail.html")
- @RequestMapping("audit.html")
- @RequestMapping("audit.do")
- @RequestMapping("invoice.do")
- @RequestMapping("delete.do")
- @GetMapping("getProjectByCode.do")
- @GetMapping("getRate.do")
- @RequestMapping("update.html")
- @RequestMapping("update.do")

## LightPurchaseOrderRelatePreController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightPurchaseOrderRelatePreController.java`
- @RequestMapping("/lightPurchaseOrderRelatePre")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")

## YuexiuElectricityBillController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/YuexiuElectricityBillController.java`
- @RequestMapping("/yuexiuElectricityBill")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("/doExport.do")

## LightStationPolicyIncomeDetailController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationPolicyIncomeDetailController.java`
- @RequestMapping("/lightStationPolicyIncomeDetail")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping("doExport.do")

## LightStationOtherMaterialPolicyController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationOtherMaterialPolicyController.java`
- @RequestMapping("/lightStationOtherMaterialPolicy")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("change.do")
- @PostMapping("delete.do")
- @PostMapping("import.do")
- @RequestMapping("downloadTemplate.do")
- @PostMapping("audit.do")
- @PostMapping("updateStatus.do")
- @PostMapping("batchDelete.do")

## LightFinanceRecordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightFinanceRecordController.java`
- @RequestMapping("/lightFinanceRecord")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = "/audit.do", method = {RequestMethod.POST})

## LightStationYuexiuAccountController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationYuexiuAccountController.java`
- @RequestMapping("/lightStationYuexiuAccount/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @GetMapping("queryOpenAccountStatus.do")

## LightNegativeReducePolicyController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightNegativeReducePolicyController.java`
- @RequestMapping("/lightNegativeReducePolicy")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @PostMapping("auditOne.do")
- @PostMapping("auditTwo.do")
- @PostMapping("auditThree.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})

## LightStationInfoUpdateController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationInfoUpdateController.java`
- @RequestMapping("/lightStationInfoUpdate")
- @RequestMapping("listForSubCenter.html")
- @RequestMapping("listForHeader.html")
- @RequestMapping("log.html")
- @RequestMapping("detail.html")
- @RequestMapping("audit.html")
- @RequestMapping("doListForSubCenter.do")
- @RequestMapping("doList.do")
- @RequestMapping("doLogList.do")
- @RequestMapping("doExport.do")
- @RequestMapping("subCenterAudit.do")
- @RequestMapping("placeLeaderAudit.do")

## LightNewMerchantPolicyController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightNewMerchantPolicyController.java`
- @RequestMapping("/lightNewMerchantPolicy/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("add.html")
- @PostMapping("add.do")
- @PostMapping("delay.do")
- @RequestMapping("detail.html")
- @RequestMapping("steepAudit.html")
- @RequestMapping("steepDelayAudit.html")
- @RequestMapping("setDelay.html")
- @RequestMapping("xwAudit.html")
- @RequestMapping("xwDelayAudit.html")
- @RequestMapping("financeAudit.html")
- @RequestMapping("financeDelayAudit.html")
- @PostMapping("steepAudit.do")
- @PostMapping("steepDelayAudit.do")
- @PostMapping("xwAudit.do")
- @PostMapping("xwDelayAudit.do")
- @PostMapping("financeAudit.do")
- @PostMapping("financeDelayAudit.do")
- @RequestMapping(value = {"/logs.do"}, method = {RequestMethod.GET})

## LightStationBusinessController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationBusinessController.java`
- @RequestMapping("/lightStationBusiness")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping("detail.html")
- @RequestMapping("detailNew.html")
- @RequestMapping("audit.html")
- @RequestMapping("userInfoImageView.html")
- @RequestMapping("guarantorIdCardView.html")
- @RequestMapping("threeDaysGenDataView.html")
- @RequestMapping("gridSupplementDataView.html")
- @RequestMapping("signRelatedImageView.html")
- @RequestMapping("powerStationDesignView.html")
- @RequestMapping("purchaseSaleContractView.html")
- @RequestMapping("gridRecordCertificateView.html")
- @RequestMapping("bankCardImageView.html")
- @RequestMapping(value = { "materialAuditOk.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "materialAuditFail.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/planConfig.do" }, method = {RequestMethod.GET})
- @RequestMapping(value = {"getLastRejectReason.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"checkAuditSnap.do"}, method = {RequestMethod.POST})
- @RequestMapping("auditSnapDetail.html")

## LightBenefitConversionController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightBenefitConversionController.java`
- @RequestMapping("/lightBenefitConversion")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping("detail.html")
- @RequestMapping(value = "/deliver.do", method = {RequestMethod.POST})

## LightStationPartCompleteApplyController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationPartCompleteApplyController.java`
- @RequestMapping("/lightStationPartCompleteApply/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @GetMapping("detail.do")
- @PostMapping("audit.do")

## LightStationZhController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationZhController.java`
- @RequestMapping("/lightStatioZh")
- @RequestMapping("list.html")
- @RequestMapping("/doList.do")
- @RequestMapping(value = {"/detail.html"}, method = {RequestMethod.GET})
- @RequestMapping("/doExport.do")

## FinanceReportController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/FinanceReportController.java`
- @RequestMapping("/financeReport")
- @RequestMapping("/station/list.html")
- @RequestMapping("/station/doList.do")
- //    @RequestMapping("/station/doExport.do")
- @RequestMapping("/station/doExport.do")

## LightGroovyScriptController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightGroovyScriptController.java`
- @RequestMapping("/lightGroovyScript")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @PostMapping("save.do")
- @PostMapping("test.do")

## LightStationEnableRewardController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationEnableRewardController.java`
- @RequestMapping("/lightStationEnableReward")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @GetMapping("detail.do")
- @RequestMapping("doExport.do")

## LightStationYuexiuController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationYuexiuController.java`
- @RequestMapping("/lightStationYuexiu")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("contractList.html")
- @RequestMapping("doContractList.do")
- @RequestMapping("getContract.do")
- @RequestMapping("doExport.do")
- @RequestMapping(value = {"/imgAdd.do"}, method = {RequestMethod.GET})
- @PostMapping("createImg.do")
- @RequestMapping("detail.html")
- @PostMapping("rePushThisStationToRiskSurvey")
- @PostMapping("updateContractStatus.do")
- @PostMapping("cancelLease")
- @PostMapping("returnIncome")
- @PostMapping("rePushReturnIncome")
- @PostMapping("returnFinish")
- @PostMapping("rePushFollowClose")

## LightStationYuexiuSkController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationYuexiuSkController.java`
- @RequestMapping("/lightStationYuexiuSk")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @PostMapping("confirm.do")

## LightProjectAuthoritySpController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightProjectAuthoritySpController.java`
- @RequestMapping("/lightAuthSp/")
- @RequestMapping("authoritySp.html")
- @RequestMapping("authoritySpList.do")
- @RequestMapping(value = { "authority.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "freezeSp.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "deleteSp.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/findPartner.do" }, method = {RequestMethod.GET})

## EnergyElecPriceReportController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/EnergyElecPriceReportController.java`
- @RequestMapping("/energyElecPriceReport")
- @RequestMapping("regionList.html")
- @RequestMapping("doRegionList.do")
- @RequestMapping("doRegionExport.do")
- @RequestMapping("companyList.html")
- @RequestMapping("doCompanyList.do")
- @RequestMapping("doCompanyExport.do")
- @RequestMapping("provinceList.html")
- @RequestMapping("doProvinceList.do")
- @RequestMapping("doProvinceExport.do")

## LightCapitalProjectElectricOrderInvoiceController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightCapitalProjectElectricOrderInvoiceController.java`
- @RequestMapping("/lightProjectElectricOrderInvoice")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = "/confirmInvoice.do", method = {RequestMethod.POST})
- @RequestMapping("/doExport.do")

## RegionModifyAuditController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/RegionModifyAuditController.java`
- @RequestMapping("/regionModifyAudit")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("processAudi.html")
- @PostMapping("audiStatus.do")
- @RequestMapping("detail.html")

## LightEnablePolicySpPropController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightEnablePolicySpPropController.java`
- @RequestMapping("/lightEnablePolicySpProp")
- @RequestMapping("list.html")
- @PostMapping("audit.do")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @PostMapping("doDel.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})

## LightCapitalProjectElectricOrderV2Controller
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightCapitalProjectElectricOrderV2Controller.java`
- @RequestMapping("/capital/projectElectricOrderV2")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("batchAcknowledgeOrder.do")
- @RequestMapping("batchAcknowledgeOrderByBatchNo.do")
- @RequestMapping("findByBatchNumbersWaitConfirm.do")
- @RequestMapping(value = "/rejectOrder.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/rejectByBatchNumbers.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/rejectByInvoiceNumbers.do", method = {RequestMethod.POST})
- @RequestMapping("audit.html")
- @RequestMapping("auditZero.html")
- @RequestMapping("findByBatchNumbers.do")
- @RequestMapping(value = "/confirm.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/confirmAll.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/confirmPaid.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/confirmPaidAll.do", method = {RequestMethod.POST})
- @RequestMapping("checkBatchNoForConfirmSk.do")
- @RequestMapping(value = {"/downReceiptTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importReceiptData.do"}, method = {RequestMethod.POST})
- @RequestMapping("doExport.do")

## LightCoinRecordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightCoinRecordController.java`
- @RequestMapping("/lightCoinRecord")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")

## DispatchWorkOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/DispatchWorkOrderController.java`
- @RequestMapping("/dispatchWorkOrder/")
- @RequestMapping("list.html")
- @RequestMapping("dispatchWorkOrderList.do")
- @RequestMapping("doExport.do")

## LightShareBillRecordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightShareBillRecordController.java`
- @RequestMapping("/lightShareBillRecord")
- @RequestMapping("list.html")
- @RequestMapping("detail.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @RequestMapping("doExport.do")
- @RequestMapping(value = {"/importPayResult/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importPayResult/importData.do"}, method = {RequestMethod.POST})

## LightHdIncomePriceConfigController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightHdIncomePriceConfigController.java`
- @RequestMapping("/lightHdIncomePriceConfig")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")

## LightYuexiuIncomeBillController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightYuexiuIncomeBillController.java`
- @RequestMapping("/lightIncomeBill")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doListPro.do")
- @RequestMapping("doExport.do")

## LightStationAuditController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationAuditController.java`
- @RequestMapping("/station/audit")

## LightEnablePolicySpPropLogController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightEnablePolicySpPropLogController.java`
- @RequestMapping("/lightEnablePolicySpPropLog")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @PostMapping("change.do")
- @PostMapping("add.do")

## CmSimpleProjectController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmSimpleProjectController.java`
- @RequestMapping("/cmSimpleProject/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("add.html")
- @RequestMapping("add.do")
- @RequestMapping("getInvoice.do")
- @RequestMapping("detail.html")
- @RequestMapping("update.html")
- @RequestMapping("update.do")
- @RequestMapping("audit.html")
- @RequestMapping("audit.do")
- @RequestMapping(value = "/batchCancel.do", method = {RequestMethod.POST})
- @RequestMapping("/doExport.do")
- @RequestMapping(value = "getInvestorList.do", method = RequestMethod.POST)

## LightCmEpcStationTechController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightCmEpcStationTechController.java`
- @RequestMapping("lightCmEpcStationTech")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("audit.html")
- @RequestMapping(value = {"auditOk.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"auditFail.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"uploadOpinion.do"}, method = {RequestMethod.POST})
- @RequestMapping("doExport.do")

## LightUnionpayBillRecordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightUnionpayBillRecordController.java`
- @RequestMapping("/lightUnionpayBillRecord")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping("detailList.html")
- @RequestMapping("doDetailList.do")
- @RequestMapping("repay.do")
- @RequestMapping("detailDoExport.do")

## HhVerificationCodeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/HhVerificationCodeController.java`
- @RequestMapping("/hhVerificationCode")
- @RequestMapping("list.html")
- @RequestMapping("hhVerificationCodeList.do")
- @RequestMapping("/export.do")

## CmOwnerStationReportController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmOwnerStationReportController.java`
- @RequestMapping("/cmOwnerStationReport")
- @RequestMapping("list.html")
- @RequestMapping("doYearList.do")
- @RequestMapping("doMonthList.do")
- @RequestMapping("/doMonthExport.do")
- @RequestMapping("/doYearExport.do")

## CmNodeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmNodeController.java`
- @RequestMapping("/cmNode")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("add.do")
- @RequestMapping("enable.do")
- @RequestMapping("disable.do")

## LightSubStoreController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSubStoreController.java`
- @RequestMapping("/lightSubStore")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping("enable.do")
- @RequestMapping("disable.do")
- @RequestMapping(value = "/get.do", method = {RequestMethod.GET})

## LightProjectOwnerAccountController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightProjectOwnerAccountController.java`
- @RequestMapping("/lightProjectOwnerAccount")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("/doExport.do")

## LightShareBillRecordPayFailController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightShareBillRecordPayFailController.java`
- @RequestMapping("/lightShareBillRecordPayFail")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("checkRepayParam.do")
- @RequestMapping("repay.do")
- @RequestMapping("doExport.do")

## LightStationPersonInfoAuthController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationPersonInfoAuthController.java`
- @RequestMapping("/lightStationPersonInfoAuth")
- @RequestMapping("list.html")
- @RequestMapping("/doList.do")
- @RequestMapping("/doExport.do")

## LightOverdueListDetailController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightOverdueListDetailController.java`
- @RequestMapping("/lightOverdueListDetail")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @RequestMapping("doExport.do")

## LightLendController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightLendController.java`
- @RequestMapping("/lightLend/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightSensitiveDataChangeLogController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSensitiveDataChangeLogController.java`
- @RequestMapping("/lightSensitiveDataChangeLog")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping("doExport.do")

## LightCmEpcStationController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightCmEpcStationController.java`
- @RequestMapping("lightCmEpcStation")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = {"auditOk.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"auditFail.do"}, method = {RequestMethod.POST})

## LightUnionpayBillController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightUnionpayBillController.java`
- @RequestMapping("/lightUnionpayBill")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @GetMapping("queryBalance.do")
- @PostMapping("payBill.do")
- @PostMapping("confirm.do")
- @PostMapping("confirmByMoney.do")
- @PostMapping("batchConfirm.do")
- @RequestMapping("doExport.do")

## LightInstantRewardController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightInstantRewardController.java`
- @RequestMapping("/lightInstantReward")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping("doExport.do")

## EnergyLeasedStationAssetManagementController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/EnergyLeasedStationAssetManagementController.java`
- @RequestMapping("/assetManagement")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("export.do")
- @RequestMapping(value = "/importData.do", method = RequestMethod.POST)
- @RequestMapping(value = "/update.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/delete.do", method = {RequestMethod.POST})

## InsuranceRenewalController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/InsuranceRenewalController.java`
- @RequestMapping("/insuranceRenewal")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("export.do")
- @RequestMapping(value = "/count.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/stationInsuranceList.do", method = {RequestMethod.POST, RequestMethod.GET})
- @RequestMapping(value = "/batchRePush.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/pullYuexiuRenewalStatus.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/downloadInitTemplate.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/generateYuexiuRenewalBatchNo.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/splitFailedBatch.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/initCurrentYearRenewal.do", method = {RequestMethod.POST})

## LightStationPlanDesignController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationPlanDesignController.java`
- @RequestMapping("/lightPlanDesign")
- @RequestMapping(value = "/findByStationId.do", method = {RequestMethod.GET})

## LightCaseController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightCaseController.java`
- @RequestMapping("/lightCase/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @PostMapping("add.do")
- @PostMapping("update.do")
- @RequestMapping(value = { "/option.do" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/listProvince.do" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/listRegion.do" }, method = {RequestMethod.GET})

## LightCapitalUnionpayBillController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightCapitalUnionpayBillController.java`
- @RequestMapping("/capital/unionpayBill")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping("/record/list.html")
- @RequestMapping("/record/doList.do")
- @RequestMapping("/record/doExport.do")
- @RequestMapping("/record/detailList.html")
- @RequestMapping("/record/doDetailList.do")
- @RequestMapping("/record/detailDoExport.do")
- @RequestMapping("repay.do")

## LightEamYearBudgetController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightEamYearBudgetController.java`
- @RequestMapping("/lightEamYearBudget")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @PostMapping("getBudgetYearInfo.do")

## LightPreOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightPreOrderController.java`
- @RequestMapping("/lightPreOrder")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = "/confirm.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/invalid.do", method = {RequestMethod.POST})
- @RequestMapping("doExport.do")
- @RequestMapping("doPreOrderPurchaseOrderExport.do")

## LightProjectElectricOrderFapRecordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightProjectElectricOrderFapRecordController.java`
- @RequestMapping("/lightProjectElectricOrderFapRecord")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("/doExport.do")

## LightStationHuarunController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationHuarunController.java`
- @RequestMapping("/lightStationHuarun")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping("detail.html")
- @RequestMapping(value = "listPlanConfig.do", method = {RequestMethod.GET})
- @RequestMapping(value = "showRecord.do", method = {RequestMethod.GET})
- @RequestMapping(value = "downloadStationContractTemplate.do", method = {RequestMethod.GET})
- @RequestMapping("printReport.html")
- @RequestMapping("doExportBank.do")
- @RequestMapping(value = "listInverter.do", method = {RequestMethod.GET})
- @RequestMapping("contractRecordList.html")
- @RequestMapping("doContractRecordList.do")
- @RequestMapping("/contract/doExport.do")
- @RequestMapping(value = "showContract.do", method = {RequestMethod.GET})
- @RequestMapping(value = {"pushContract.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = "planInveterList.do", method = {RequestMethod.GET})
- @RequestMapping("branchList.html")
- @RequestMapping("doBranchList.do")
- @RequestMapping("doBranchExport.do")
- @RequestMapping("finalFirstAuditList.html")
- @RequestMapping("doFinalFirstAuditList.do")
- @RequestMapping("doFinalFirstAuditExport.do")

## LightAuxiliaryMakeOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightAuxiliaryMakeOrderController.java`
- @RequestMapping("/lightAuxiliaryMakeOrder")
- @RequestMapping("list.html")
- @RequestMapping("hrList.html")
- @RequestMapping("/doList.do")
- @PostMapping("rollBackAuxiliary")
- @PostMapping("auditOk")
- @PostMapping("/doAuxiliaryList.do")
- @RequestMapping("lightAuxiliaryBranchAuditView.html")
- @RequestMapping("hrMakeOrderAuxiliaryAudit.html")
- @GetMapping("hrMakeOrderDetail.html")
- @RequestMapping("lightAuxiliaryMakeOrderDetail.html")
- @GetMapping(value = "/auditLog.html")
- @RequestMapping(value = "lightPlanAuxiliaryMakeOrder.html", method = {RequestMethod.GET})
- @PostMapping("makePurchaseOrderDirectly.do")
- @RequestMapping(value = "/getDepositBySp.do", method = {RequestMethod.GET})
- @RequestMapping(value = "hrMakeOrderAuxiliaryDirectly.html", method = {RequestMethod.GET})
- @RequestMapping(value = "/getBySpIdAndRegionId.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/getSpExceptVip.do", method = {RequestMethod.GET})
- @PostMapping("hrMakePurchaseOrderDirectly.do")

## LightInstantRewardPolicyLogController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightInstantRewardPolicyLogController.java`
- @RequestMapping("/lightInstantRewardPolicyLog")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping("doExport.do")

## CmLightProjectController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmLightProjectController.java`
- @RequestMapping("/cmLightProject/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("add.html")
- @RequestMapping("add.do")
- @RequestMapping("detail.html")
- @RequestMapping("audit.html")
- @RequestMapping("sign.html")
- @RequestMapping("auditOne.do")
- @RequestMapping("auditTwo.do")
- @RequestMapping("sign.do")
- @RequestMapping("contractDetail.html")
- @GetMapping("getFunnel.do")
- @RequestMapping("confirmList.html")
- @RequestMapping("confirm/doList.do")
- @RequestMapping("showConfirm.html")
- @RequestMapping("confirm.do")
- @RequestMapping("showConfirmDetail.html")
- @PostMapping("pay.do")
- @RequestMapping("addProjectSet.do")
- @RequestMapping("doSetList.do")
- @RequestMapping("updateProject.do")
- @RequestMapping("auditProjectSet.do")
- @RequestMapping("addVote.do")
- @RequestMapping("doVoteList.do")
- @RequestMapping("updateVote.do")
- @RequestMapping("auditVote.do")
- @RequestMapping("detailNew.html")
- @RequestMapping("projectSetList.html")
- @RequestMapping("projectVoteList.html")
- @RequestMapping("projectSetDetail.html")
- @RequestMapping("auditProjectSet.html")
- @RequestMapping("updateProjectSet.html")
- @RequestMapping("addVote.html")
- @RequestMapping("voteDetail.html")
- @RequestMapping("auditVote.html")
- @RequestMapping("updateVote.html")
- @RequestMapping("projectSetTrack.html")
- @RequestMapping("projectVoteTrack.html")
- @RequestMapping("addReceiptMilestone.do")
- @RequestMapping("addPaymentMilestone.do")
- @RequestMapping("calcGrossMarginB.do")
- @RequestMapping("paymentMilestone/auditList.html")
- @RequestMapping("paymentMilestone/doAuditList.do")
- @RequestMapping("paymentMilestone/auditDetail.html")
- @RequestMapping("paymentMilestone/doAudit.do")
- @RequestMapping("paymentMilestone/updateDetail.html")
- @RequestMapping("paymentMilestone/doUpdate.do")
- @RequestMapping("confirmSettle/list.html")
- @RequestMapping("confirmSettle/doList.do")
- @RequestMapping("confirmSettle/confirm.do")
- @RequestMapping("grossMarginChange/list.html")
- @RequestMapping("grossMarginChange/doList.do")
- @RequestMapping("grossMarginChange/auditDetail.html")
- @RequestMapping("grossMarginChange/doAudit.do")
- @RequestMapping("saveEngineeringInfo.do")
- @RequestMapping(value = "getInvestorList.do", method = RequestMethod.POST)
- @RequestMapping(value = "/saveWorkStatus.do", method = {RequestMethod.POST})

## LightProjectPartnerController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightProjectPartnerController.java`
- @RequestMapping("/lightPartner/")
- @RequestMapping("partnerList.html")
- @RequestMapping("partnerList.do")
- @RequestMapping(value = { "auditOk.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "auditFail.do" }, method = { RequestMethod.POST })

## LightProjectElectricOrderOwnerController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightProjectElectricOrderOwnerController.java`
- @RequestMapping(value = "/lightProjectElectricOrderOwner")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")

## LightRoboAdvisorOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightRoboAdvisorOrderController.java`
- @RequestMapping("/roboAdvisor")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = "roboAdvisorOrderDetail.html", method = {RequestMethod.GET})
- @PostMapping("approve.do")
- @PostMapping("reject.do")

## LightStockTakingController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStockTakingController.java`
- @RequestMapping("/lightStockTaking")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = { "add.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "start.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = "detail.html", method = {RequestMethod.GET})
- @RequestMapping(value = "detail.do")
- @RequestMapping(value = "analysis.do", method = {RequestMethod.GET})
- @PostMapping("varianceAnalysis.do")
- @RequestMapping(value = "getAllNotCompleteStation.do", method = {RequestMethod.GET})
- @PostMapping("batchUpdateDetail.do")
- @RequestMapping(value = "analysis.html", method = {RequestMethod.GET})
- @RequestMapping(value = "detailAnalysis.do")
- @PostMapping("subCenterAudit.do")
- @PostMapping("closeLoop.do")
- @PostMapping("supplyChainAudit.do")
- @RequestMapping("download.do")
- @RequestMapping("downloadEmpty.do")
- @RequestMapping("doExport.do")
- @PostMapping("delete.do")
- @RequestMapping("summaryList.html")
- @RequestMapping("doSummaryList.do")
- @RequestMapping("doSummaryExport.do")
- @RequestMapping("doAnalysisExport.do")

## LightElectricOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightElectricOrderController.java`
- @RequestMapping("/lightElectricOrder")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightStationReportController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationReportController.java`
- @RequestMapping("/lightStationReport")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightCapitalProjectElectricInvoiceReverseRecordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightCapitalProjectElectricInvoiceReverseRecordController.java`
- @RequestMapping("/capital/electric/invoice/reverse/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightElectricDaySumController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightElectricDaySumController.java`
- @RequestMapping("/lightElectricDaySum")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightEnablePolicyFourItemController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightEnablePolicyFourItemController.java`
- @RequestMapping("/lightEnablePolicyFourItem/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("add.html")
- @PostMapping("add.do")
- @RequestMapping("detail.html")
- @RequestMapping("steepAudit.html")
- @RequestMapping("xwAudit.html")
- @RequestMapping("financeAudit.html")
- @PostMapping("steepAudit.do")
- @PostMapping("xwAudit.do")
- @PostMapping("financeAudit.do")
- @RequestMapping(value = {"/areas.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/items.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/logs.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/listProvince.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/listRegion.do"}, method = {RequestMethod.GET})
- @GetMapping("edit.html")
- @PostMapping("updatePolicy.do")

## LightOverdueBlackListController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightOverdueBlackListController.java`
- @RequestMapping("/lightOverdueBlackList")
- @RequestMapping("list.html")
- @RequestMapping("detail.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("change.do")
- @PostMapping("audit.do")
- @PostMapping("add.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping("doExport.do")

## LightInstantRewardItemController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightInstantRewardItemController.java`
- @RequestMapping("/lightInstantRewardItem")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping("doExport.do")

## OperationalAssetManagementController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/OperationalAssetManagementController.java`
- @RequestMapping("/operationalAssetManagement")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @PostMapping("delete.do")
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping("doExport.do")

## LightOptionController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightOptionController.java`
- @RequestMapping("/lightOption/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @PostMapping("add.do")
- @PostMapping("update.do")

## LightProjectCompanyAccountController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightProjectCompanyAccountController.java`
- @RequestMapping("/lightProjectCompanyAccount")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})

## LightSpWithdrawalApplicationVoucherController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSpWithdrawalApplicationVoucherController.java`
- @RequestMapping("/lightSpWithdrawalApplicationVoucher")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("add.html")
- @RequestMapping("detail.html")
- @GetMapping("detail.do")
- @PostMapping("add.do")
- @PostMapping("edit.do")
- @PostMapping("delete.do")
- @RequestMapping("doExport.do")
- @GetMapping("doExportDetails.do")

## TheoryElectHourController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/TheoryElectHourController.java`
- @RequestMapping("/theoryElectHour")
- @RequestMapping("list.html")
- @RequestMapping("update.html")
- @RequestMapping(value = "/list.do")
- @RequestMapping(value = "/update.do", method = {RequestMethod.PUT})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @GetMapping("/downTemplate.do")

## CmConstructionPlanController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmConstructionPlanController.java`
- @RequestMapping("/cmConstructionPlan")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("detail.html")
- @RequestMapping("audit.html")
- @RequestMapping("audit.do")
- @RequestMapping("/doExport.do")

## EnergySpDataController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/EnergySpDataController.java`
- @RequestMapping(value = "/EnergySpData")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightAuxiliaryMaterialQuotaExchangeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightAuxiliaryMaterialQuotaExchangeController.java`
- @RequestMapping("/lightAuxiliaryMaterialQuotaExchange")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("/doExport.do")

## LightZhSettleSumController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightZhSettleSumController.java`
- @RequestMapping("/lightZhSettleSum")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")

## CmOwnerStationWhiteListController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmOwnerStationWhiteListController.java`
- @RequestMapping("/cmOwnerStationWhiteList")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = {"/downloadTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping("importData.do")
- @PostMapping("delete.do")

## CmLightProjectReportController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmLightProjectReportController.java`
- @RequestMapping("/cmReport")
- @RequestMapping("/projectSummary/list.html")
- @RequestMapping("/projectSummary/doList.do")

## LightUseQueueController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightUseQueueController.java`
- @RequestMapping("/lightUseQueue")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")

## LightUnionpayUserController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightUnionpayUserController.java`
- @RequestMapping("/lightUnionpayUser/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping(value = "/pushUserInfo", method = {RequestMethod.POST})
- @RequestMapping(value = "/queryUserSign", method = {RequestMethod.POST})

## LightPreOrderRelatePurchaseController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightPreOrderRelatePurchaseController.java`
- @RequestMapping("/lightPreOrderRelatePurchase")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightEamAssetsController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightEamAssetsController.java`
- @RequestMapping("/LightEamAssets")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightUseOrderReverseController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightUseOrderReverseController.java`
- @RequestMapping("/lightUseOrderReverse")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @GetMapping("getCount.do")
- @RequestMapping("confirm.do")
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping("doExport.do")

## CmPaymentController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmPaymentController.java`
- @RequestMapping("/cmPayment/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = {"/findProject.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/findSettlementTargetList.do"}, method = {RequestMethod.GET})
- @RequestMapping("add.html")
- @RequestMapping("add.do")
- @RequestMapping("update.html")
- @RequestMapping("update.do")
- @PostMapping("delete.do")
- @RequestMapping("detail.html")
- @RequestMapping("audit.html")
- @RequestMapping("audit.do")
- @RequestMapping("/doExport.do")

## LightStationImageDownloadController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationImageDownloadController.java`
- @RequestMapping("/lightStationImageDownload/")
- @RequestMapping("list.html")
- @PostMapping("doList.do")
- @RequestMapping("add.html")
- @RequestMapping("doAdd.do")
- @RequestMapping(value = "exportStationCode.do",method = {RequestMethod.GET})
- @RequestMapping("doExport.do")
- @RequestMapping(value = "del.do",method = {RequestMethod.POST})

## CmLightUseController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmLightUseController.java`
- @RequestMapping("/cmLightUse")
- @RequestMapping("list.html")
- @RequestMapping("/doList.do")
- @RequestMapping("/doExport.do")

## LightProjectElectricOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightProjectElectricOrderController.java`
- @RequestMapping("/lightProjectElectricOrder")
- @RequestMapping("list.html")
- @RequestMapping("lightProjectElectricOrderInvoiceList.html")
- @RequestMapping("doList.do")
- @RequestMapping("doListWithInvoice.do")
- @RequestMapping("findByIds.do")
- @RequestMapping("checkOrderIdsBeforeAcknowledge.do")
- @RequestMapping("batchAcknowledgeOrder.do")
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/downReceiptTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = "/confirm.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/deleteAll.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/deleteByBatchAndInvoiceNos.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/confirmIncomeToSap.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/confirmAll.do", method = {RequestMethod.POST})
- @RequestMapping("doExport.do")
- @RequestMapping("doListWithInvoiceExport.do")
- @RequestMapping(value = "/confirmPaid.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/confirmPaidAll.do", method = {RequestMethod.POST})
- @RequestMapping("detail.html")
- @RequestMapping("/findAccounts")
- @RequestMapping("detailZero.html")
- @RequestMapping("audit.html")
- @RequestMapping("auditZero.html")
- @RequestMapping(value = "/editInfo.do", method = {RequestMethod.POST})
- @PostMapping("uploadFile.do")
- @RequestMapping("findByBatchNumbers.do")
- @RequestMapping("findByBatchNumbersWaitConfirm.do")
- @RequestMapping(value = {"/importReceiptData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = "/rejectOrder.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/rejectByBatchNumbers.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/rejectByInvoiceNumbers.do", method = {RequestMethod.POST})
- @RequestMapping("batchAcknowledgeOrderByBatchNo.do")
- @RequestMapping("checkBatchNoForConfirmSk.do")
- @RequestMapping("sumByInvoiceNumber.do")
- @RequestMapping("fapManual.do")
- @RequestMapping("fapManualOld.do")
- @PostMapping("/checkElecNoBound")

## LightProjectRentRecordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightProjectRentRecordController.java`
- @RequestMapping("/lightProjectRentRecord")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @PostMapping("confirm.do")
- @RequestMapping("doExport.do")

## CmInvoiceApplyController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmInvoiceApplyController.java`
- @RequestMapping("/cmInvoiceApply/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @GetMapping("getAddPreInfo.do")
- @GetMapping("getInvoiceInfo.do")
- @GetMapping("getCmInvoiceTaxClassificationData.do")
- @RequestMapping("findTaxClassificationList.do")
- @GetMapping("getEnableItemList.do")
- @RequestMapping("add.html")
- @RequestMapping("add.do")
- @RequestMapping("update.html")
- @RequestMapping("update.do")
- @PostMapping("delete.do")
- @GetMapping("getDepositAmountByCode.do")
- @RequestMapping("detail.html")
- @RequestMapping("audit.html")
- @RequestMapping("audit.do")
- @RequestMapping("/doExport.do")
- @GetMapping("/downloadInvoice.do")
- @GetMapping("/downloadXml.do")
- @GetMapping("/downloadOfd.do")
- @RequestMapping(value = {"/getCrossRegionalTaxRelatedData.do"}, method = {RequestMethod.GET})

## LightStationController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationController.java`
- @RequestMapping("/lightStation")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doListRefactor.do")
- @RequestMapping("sttionInervers.do")
- @RequestMapping(value = {"editInverter.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"auditOk.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"auditFail.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"getLastRejectReason.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"waitOrderAuditReject.do"}, method = {RequestMethod.POST})
- //    @RequestMapping("doExport.do")
- @RequestMapping("doExport.do")
- //    @RequestMapping("/doAsyncExport.do")
- @RequestMapping("detail.html")
- @RequestMapping("detailByStationCode.html")
- @RequestMapping("stationImgsEdit.html")
- @RequestMapping(value = "showRecord.do", method = {RequestMethod.GET})
- @RequestMapping(value = "getPlanBom.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/getMajorAndAuxiliaryBom", method = {RequestMethod.GET})
- @RequestMapping(value = "/findAllPlanDesignByConfigType.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/findMajorAndAuxiliarySummaryPlanConfig.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/findMajorAndAuxiliarySummaryPlanConfigByType.do", method = {RequestMethod.GET})
- @RequestMapping(value = "listPlanConfig.do", method = {RequestMethod.GET})
- @RequestMapping(value = "downloadStationContractTemplate.do", method = {RequestMethod.GET})
- @RequestMapping("acceptanceAudit.html")
- @RequestMapping("mobileReport.html")
- @PostMapping("acceptanceAuditOk.do")
- @RequestMapping(value = {"acceptanceAuditFail.do"}, method = {RequestMethod.POST})
- @RequestMapping("printReport.html")
- @RequestMapping("downloadReport.do")
- @RequestMapping("downloadReportPdf.do")
- @RequestMapping(value = {"signContract.do"}, method = {RequestMethod.POST})
- @RequestMapping("doExportBank.do")
- @RequestMapping(value = "listInverter.do", method = {RequestMethod.GET})
- @RequestMapping("contractRecordList.html")
- @RequestMapping("contractRecordLog.html")
- @RequestMapping("doContractRecordLogList.do")
- @RequestMapping("contractRevocateAndRestoreLog.html")
- @RequestMapping("doContractRevocateAndRestoreLogList.do")
- @RequestMapping(value = "/revokeSignature.do", method = RequestMethod.POST)
- @RequestMapping(value = "/restoreContract.do", method = RequestMethod.POST)
- @RequestMapping("doContractRecordList.do")
- @RequestMapping(value = {"/findNewOne.do"}, method = {RequestMethod.GET})
- @RequestMapping("/contract/doExport.do")
- @RequestMapping(value = "showContract.do", method = {RequestMethod.GET})
- @RequestMapping(value = "showContractHistory.do", method = {RequestMethod.GET})
- @RequestMapping(value = {"pushContract.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = "planInveterList.do", method = {RequestMethod.GET})
- @RequestMapping(value = {"changeInveter.do"}, method = {RequestMethod.POST})
- @RequestMapping("branchList.html")
- @RequestMapping("doBranchList.do")
- @RequestMapping("doBranchExport.do")
- @RequestMapping("finalFirstAuditList.html")
- @RequestMapping("doFinalFirstAuditList.do")
- @RequestMapping("doFinalFirstAuditExport.do")
- @RequestMapping(value = {"pushStationInstallContract.do"}, method = {RequestMethod.GET})
- @RequestMapping("downloadFile.do")
- @GetMapping("findByStationIdAndType.do")
- @GetMapping("queryBankNo.do")
- @GetMapping("queryModuleSn.do")

## LightCapitalCompanyInfoController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightCapitalCompanyInfoController.java`
- @RequestMapping("/lightCapitalCompanyInfo")
- @RequestMapping("list.html")
- @RequestMapping("/doList.do")
- @RequestMapping("/add.do")
- @RequestMapping("/freeze.do")
- @RequestMapping("/enable.do")

## LightInveterController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightInveterController.java`
- @RequestMapping("/lightInveter")
- @RequestMapping("list.html")
- @RequestMapping("listDws.html")
- @RequestMapping("doList.do")
- @RequestMapping("doListDws.do")
- @RequestMapping("doExport.do")
- @RequestMapping("detail.html")
- @GetMapping(value = "dayChart.do")
- @GetMapping(value = "ipvUpvdayChart.do")
- @GetMapping(value = "historyWeather.do")
- @GetMapping(value = "dayChartPro.do")
- @GetMapping(value = "dayChartProNew.do")
- @GetMapping(value = "monthChart.do")
- @GetMapping(value = "monthChartPro.do")
- @GetMapping(value = "monthChartProNew.do")
- @GetMapping(value = "yearChart.do")
- @GetMapping(value = "yearChartPro.do")
- @GetMapping(value = "yearChartProNew.do")
- @GetMapping(value = "totalChart.do")
- @GetMapping(value = "totalChartPro.do")
- @GetMapping(value = "totalChartProNew.do")
- @RequestMapping(value = {"unBind.do"}, method = {RequestMethod.POST})
- @GetMapping("checkUnbindCount.do")
- @GetMapping("checkInverterPower.do")
- @PostMapping("/doOcr.do")
- @GetMapping("/queryLastedOcrResult.do")

## LightVersionInformationController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightVersionInformationController.java`
- @RequestMapping("/lightVersionInformation")
- @RequestMapping(value = "/add", method = {RequestMethod.POST})

## LightElecHtRecordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightElecHtRecordController.java`
- @RequestMapping("/lightElecHtRecord")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping("doExport.do")

## LightStationYuexiuExchangeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationYuexiuExchangeController.java`
- @RequestMapping("/lightStationYuexiuExchange")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("detail.html")
- @RequestMapping("doExport.do")

## LightDepositController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightDepositController.java`
- @RequestMapping("/lightDeposit")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = "/transferConfirmPaid.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/confirmSap.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/cancelFap.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/fapRecordCreate.do", method = {RequestMethod.POST})
- @RequestMapping("doExport.do")

## LightTransferOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightTransferOrderController.java`
- @RequestMapping("/lightTransfer")
- @RequestMapping("list.html")
- @RequestMapping("doSubList.do")
- //    @RequestMapping("repairStore.do")
- @RequestMapping("doList.do")
- @PostMapping("cancel.do")
- @PostMapping("add.do")
- @PostMapping("audit.do")
- @PostMapping("updateAndCommitToOperation.do")
- @PostMapping("operationAudit.do")
- @PostMapping("supplyChainAudit.do")
- @GetMapping("getSkuName.do")
- @RequestMapping("doExport.do")
- @GetMapping("/downTemplate.do")
- @PostMapping("importData.do")
- @PostMapping("confirm.do")
- @RequestMapping("detail.html")
- @RequestMapping("findSnList.do")
- @RequestMapping("doExportSn.do")
- @RequestMapping(value = "/getBySpIdAndRegionId.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/getZoneBySpIdAndStoreId.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/getZoneById.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/getStoreAddressListByStoreId.do", method = {RequestMethod.GET})
- @RequestMapping(value = "/getStoreAddressByAddressId.do", method = {RequestMethod.GET})
- @RequestMapping("internalTransferOrderList.html")
- @RequestMapping("doInternalTransferList.do")
- @RequestMapping("doInternalTransferExport.do")
- @RequestMapping(value = "/getMainAnd2ndClassStoreListBySpId.do", method = {RequestMethod.GET})

## LightStationOwnerController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationOwnerController.java`
- @RequestMapping("/lightStationOwner")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping(value = "/pushToYuexiu.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/delete.do", method = {RequestMethod.POST})
- @RequestMapping(value = { "/info.do" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/editGuarantor.do" }, method = {RequestMethod.POST})
- @RequestMapping(value = { "/editInfo.do" }, method = {RequestMethod.POST})
- @RequestMapping(value = {"edit.html"}, method = {RequestMethod.GET})

## ZhPowerController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/ZhPowerController.java`
- @RequestMapping("/zhPower/")
- @RequestMapping("list.html")
- @RequestMapping("/doList.do")
- @RequestMapping("/doExport.do")

## StationChangeOperationController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/StationChangeOperationController.java`
- @RequestMapping("/stationChangeOperation")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("audit.html")
- @RequestMapping("detail.html")
- @GetMapping("detail.do")
- @PostMapping("audit.do")
- @RequestMapping("/doExport.do")

## CmProductionValueController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmProductionValueController.java`
- @RequestMapping("/cmProductionValue")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("detail.html")
- @GetMapping("getAddPreInfo.do")
- @RequestMapping("add.html")
- @RequestMapping("add.do")
- @RequestMapping("update.html")
- @RequestMapping("update.do")
- @PostMapping("delete.do")
- @RequestMapping("audit.html")
- @RequestMapping("audit.do")
- @RequestMapping("/doExport.do")

## LightManualIncomeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightManualIncomeController.java`
- @RequestMapping("/lightManualIncome")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = "/confirm.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/delete.do", method = {RequestMethod.POST})
- @RequestMapping("add.html")
- @RequestMapping(value = {"doAdd.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = { "/listProvince.do" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/listRegion.do" }, method = {RequestMethod.GET})
- @RequestMapping("detail.html")
- @RequestMapping(value = { "/invoice.do" }, method = {RequestMethod.GET})

## LightPurchaseOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightPurchaseOrderController.java`
- @RequestMapping("/lightPurchaseOrder")
- @RequestMapping("list.html")
- @RequestMapping("auxiliaryPurchaseOrderList.html")
- @RequestMapping("lightPlanAuxiliaryPurchaseOrderList.html")
- @GetMapping("auxiliaryPurchaseOrderDetail.html")
- @RequestMapping("doList.do")
- @RequestMapping("doAuxiliaryPurchaseOrderList.do")
- @RequestMapping("doPlanAuxiliaryPurchaseOrderList.do")
- @RequestMapping("doExport.do")
- @RequestMapping("doAuxiliaryExport.do")
- @RequestMapping("audit.do")
- @RequestMapping("auxiliaryPurchaseOrderAudit.do")
- @GetMapping("planAuxiliaryPurchaseOrderDetail.html")
- @RequestMapping(value = {"/cancel.do"}, method = { RequestMethod.POST })

## LightOrderInfoController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightOrderInfoController.java`
- @RequestMapping("/lightOrderInfo/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightStationYuexiuSettleController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightStationYuexiuSettleController.java`
- @RequestMapping("/lightStationYuexiuSettle")
- @RequestMapping("list.html")
- @GetMapping("/downTemplate.do")
- @RequestMapping("doList.do")
- @PostMapping("importData.do")
- @GetMapping("countBatch.do")
- @PostMapping("confirm.do")
- @RequestMapping("deprecatedDoExport.do")
- @RequestMapping("doExport.do")
- @GetMapping("getUrlLink.do")
- @GetMapping("/reverse/downTemplate.do")
- @PostMapping("/reverse/importData.do")
- @GetMapping("delete.do")

## LightPlanController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightPlanController.java`
- @RequestMapping("/lightPlan/")
- @RequestMapping("planList.html")
- @RequestMapping("planList.do")
- @RequestMapping(value = { "enablePlan.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "disablePlan.do" }, method = { RequestMethod.POST })
- @RequestMapping("planAdd.html")
- @RequestMapping(value = { "/downloadLightPlanDetailTemplate.do" }, method = { RequestMethod.GET })
- @RequestMapping(value = {"/importPlanDetail.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = { "addPlan.do" }, method = { RequestMethod.POST })

## CmChangeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmChangeController.java`
- @RequestMapping("/cmChange")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("detail.html")
- @RequestMapping("audit.html")
- @RequestMapping("audit.do")
- @RequestMapping("/doExport.do")

## LightSpMaterialPriceController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSpMaterialPriceController.java`
- @RequestMapping("/lightSpMaterialPrice")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @GetMapping("enable.do")
- @GetMapping("disable.do")
- @PostMapping("edit.do")
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping("doExport.do")
- @GetMapping("getRecordLog.do")

## CmStoreController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/CmStoreController.java`
- @RequestMapping("/cmStore/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("add.do")

## LightSpQuotaController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightSpQuotaController.java`
- @RequestMapping("/lightSpQuota")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("add.html")
- @PostMapping("add.do")
- @RequestMapping("detail.html")
- @RequestMapping(value = {"/configsPT.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/configsZJ.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/logList.do"}, method = {RequestMethod.GET})
- @RequestMapping("steepAudit.html")
- @PostMapping("steepAudit.do")
- @RequestMapping("xwAudit.html")
- @PostMapping("xwAudit.do")

## LightMaterialPackageController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightMaterialPackageController.java`
- @RequestMapping("/lightMaterialPackage")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = "materialPackageDetail.html", method = {RequestMethod.GET})
- @RequestMapping(value = "lightMaterialPackageAdd.html", method = {RequestMethod.GET})
- @PostMapping("add.do")
- @RequestMapping(value = "/importData.do", method = RequestMethod.POST)
- @RequestMapping(value = "/getPackageDetail.do", method = {RequestMethod.GET})
- @PostMapping("disable.do")
- @PostMapping("enable.do")
- @RequestMapping(value = "lightMaterialPackageEdit.html", method = {RequestMethod.GET})
- @PostMapping("edit.do")

## LightPolicyInterventionController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/LightPolicyInterventionController.java`
- @RequestMapping("/lightPolicyIntervention")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("findById.do")
- @PostMapping("add.do")
- @PostMapping("audit.do")
- @PostMapping("secondAudit.do")
- @PostMapping("countBeforeAudit.do")
- @PostMapping("uploadImgUrl.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping("doExport.do")

## LightStationCostSummaryController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/cost/LightStationCostSummaryController.java`
- @RequestMapping("/light/costSummary/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightBatchUploadController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/batchUpload/LightBatchUploadController.java`
- @RequestMapping("/lightBatchUpload")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = "/confirm.do", method = {RequestMethod.POST})
- @RequestMapping("doExport.do")

## LightSpecialOutboundApplyController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/wms/LightSpecialOutboundApplyController.java`
- @RequestMapping("/outboundApply/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping("detail.html")
- @RequestMapping("centerAudit.html")
- @RequestMapping("palaceLeaderAudit.html")
- @RequestMapping("completeCenterAudit.html")
- @RequestMapping("completeTecAudit.html")
- @RequestMapping("audit.do")

## LightSpecialOutboundServiceSapRecordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/wms/LightSpecialOutboundServiceSapRecordController.java`
- @RequestMapping("/outboundApply/sap/service")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightSpecialOutboundMaterialSapRecordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/wms/LightSpecialOutboundMaterialSapRecordController.java`
- @RequestMapping("/outboundApply/sap/material")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## DhSecondClassAccountController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/dh/DhSecondClassAccountController.java`
- @RequestMapping("/dh/account")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightStationElecTemplateMappingController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/electric/LightStationElecTemplateMappingController.java`
- @RequestMapping("/lightStationElecTemplateMapping/")
- @RequestMapping(value = "list.html", method = RequestMethod.GET)
- @RequestMapping(value = "list.do", method = RequestMethod.POST)
- @RequestMapping(value = {"importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = "downloadImportFailures.do", method = RequestMethod.GET)
- @RequestMapping(value = {"downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping("doExport.do")
- @GetMapping("changeStatus.do")
- @GetMapping("del.do")
- @PostMapping("preBatchDel.do")
- @PostMapping("batchDel.do")

## PuYinTradeIncomeSettleController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/puyin/PuYinTradeIncomeSettleController.java`
- @RequestMapping("/puyin/settle")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @GetMapping("/downTemplate.do")
- @PostMapping("importData.do")
- @RequestMapping("doExport.do")
- @GetMapping("countBatch.do")
- @PostMapping("confirm.do")
- @GetMapping("delete.do")
- @GetMapping("/reverse/downTemplate.do")
- @PostMapping("/reverse/importData.do")

## PuYinTradePriceConfigController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/light/puyin/PuYinTradePriceConfigController.java`
- @RequestMapping("/puyin/price")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("changeStatus.do")
- @RequestMapping("changePrice.do")
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping("doExport.do")
- @GetMapping("countBatch.do")
- @GetMapping("batchCancel.do")

## LightYueXiuIncomeBillExceptionController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/yuexiu/LightYueXiuIncomeBillExceptionController.java`
- @RequestMapping("/lightIncomeBill/exception")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## GhRentPayableChangeRecordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/gh/GhRentPayableChangeRecordController.java`
- @RequestMapping("/gh/rent/changeRecord")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## GhProjectCompanyAccountController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/gh/GhProjectCompanyAccountController.java`
- @RequestMapping("/gh/projectCompanyAccount")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("/save.do")
- @RequestMapping("/update.do")

## GhBindStationController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/gh/GhBindStationController.java`
- @RequestMapping("/gh/bindStation")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})

## GhSecondClassAccountBalanceController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/gh/GhSecondClassAccountBalanceController.java`
- @RequestMapping("/gh/account/balance")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## GhRentPayableSumController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/gh/GhRentPayableSumController.java`
- @RequestMapping("/gh/rent/payableSum")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## GhRentSettlementController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/gh/GhRentSettlementController.java`
- @RequestMapping("/gh/rent/settlement")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")

## GhFundsDivisionDetailController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/gh/GhFundsDivisionDetailController.java`
- @RequestMapping("/gh/funds/division")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## GhSecondClassAccountController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/gh/GhSecondClassAccountController.java`
- @RequestMapping("/gh/account")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping("/unbinding.do")

## GhAccountWithdrawRecordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/gh/GhAccountWithdrawRecordController.java`
- @RequestMapping("/gh/withdraw/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping("repay.do")

## GhSignWithholdingAgreementController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/gh/GhSignWithholdingAgreementController.java`
- @RequestMapping("/gh/sign")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping(value = {"/changeProjectCompany.do"}, method = {RequestMethod.POST})

## YzzGuideController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/yzz/YzzGuideController.java`
- @RequestMapping("/yzzGuide/")
- @RequestMapping("list.html")
- @RequestMapping(value = { "list.do" }, method = { RequestMethod.POST })
- @RequestMapping("listMember.html")
- @RequestMapping(value = { "listMember.do" }, method = { RequestMethod.POST })

## YzzWalletRechargeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/yzz/YzzWalletRechargeController.java`
- @RequestMapping("/yzzWalletRecharge/")
- @RequestMapping("list.html")
- @RequestMapping(value = "list.do", method = RequestMethod.GET)
- @RequestMapping(value = "confirmPayStatus.do", method = RequestMethod.POST)

## YzzLiveController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/yzz/YzzLiveController.java`
- @RequestMapping("/yzzLive/")
- @RequestMapping("list.html")
- @RequestMapping(value = { "list.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "enabled.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "enabledUser.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "disabled.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "setYzzShop.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "cancelYzzShop.do" }, method = { RequestMethod.POST })

## YzzShopController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/yzz/YzzShopController.java`
- @RequestMapping("/yzzShop/")
- @RequestMapping("list.html")
- @RequestMapping(value = { "list.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "linkYzz.do" }, method = { RequestMethod.POST })

## WorkOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/stationEvaluate/WorkOrderController.java`
- @RequestMapping("/workOrder/")
- @RequestMapping("list.html")
- @RequestMapping(value ={"doList.do"}, method = {RequestMethod.POST})
- @RequestMapping(value ={"export.do"})

## StationEvaluateFeedbackController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/stationEvaluate/StationEvaluateFeedbackController.java`
- @RequestMapping("/feedback/")
- @RequestMapping("list.html")
- @RequestMapping(value ={"doList.do"}, method = {RequestMethod.POST})
- @RequestMapping(value ={"export.do"})
- @RequestMapping("detail.html")

## StationEvaluateController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/stationEvaluate/StationEvaluateController.java`
- @RequestMapping("/evaluation/")
- @RequestMapping("list.html")
- @RequestMapping(value ={"doList.do"}, method = {RequestMethod.POST})
- @RequestMapping(value ={"export.do"})

## DhFirstInputPieceController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/dh/DhFirstInputPieceController.java`
- @RequestMapping("/dh/dhFirstInputPiece")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping(value = { "/dhFirstInputPiece.html" }, method = {RequestMethod.GET})

## DhBusinessOpportunityController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/dh/DhBusinessOpportunityController.java`
- @RequestMapping("/dh/dhBusinessOpportunity")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping(value = { "/dhBusinessOpportunityDetail.html" }, method = {RequestMethod.GET})

## DhLightStationController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/dh/DhLightStationController.java`
- @RequestMapping("/dh/dhLightStation")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")
- @RequestMapping("detail.html")
- @RequestMapping(value = "showRecord.do", method = {RequestMethod.GET})
- @RequestMapping(value = "getPlanBom.do", method = {RequestMethod.GET})
- @GetMapping("queryModuleSn.do")
- @GetMapping("getDesignByDetail")
- @RequestMapping(value = "listPlanConfig.do", method = {RequestMethod.GET})

## SupplierController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/supplier/SupplierController.java`
- @RequestMapping("/supplier/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = { "addSupplier.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/getMemberByMobile.do" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "merAppliSupplier.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "merAuditSupplier.do" }, method = { RequestMethod.POST })

## HroisPurchaseOrderListController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/haiwai/HroisPurchaseOrderListController.java`
- @RequestMapping("/hroisPurchaseOrder")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## HroisOrderListController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/haiwai/HroisOrderListController.java`
- @RequestMapping("/hroisOrder")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("operationContent.html")
- @RequestMapping(value = { "/operationContentList.do" }, method = {RequestMethod.GET})
- @RequestMapping("doExport.do")

## CbsHroisOrderBoxController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/haiwai/CbsHroisOrderBoxController.java`
- @RequestMapping("/cbsHroisOrderBox")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## HroisSendInfoUpdateController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/haiwai/HroisSendInfoUpdateController.java`
- @RequestMapping("/hroisSendInfoUpdate")
- @RequestMapping("hroisSendInfoUpdate.html")
- @RequestMapping("getList")
- @PostMapping("batchAudit")
- @RequestMapping("hroisSendInfoUpdateAdd.html")
- @GetMapping("getApplyList")
- @PostMapping("updateSendInfo")

## CardBatchRecordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/rank/CardBatchRecordController.java`
- @RequestMapping("/rank/cardBatch")
- @RequestMapping(value = "list.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/list.do", method = { RequestMethod.GET })
- @RequestMapping(value="/add.do",method = { RequestMethod.POST })
- @RequestMapping(value = "/export.do", method = { RequestMethod.GET })

## BenefitPackageController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/rank/BenefitPackageController.java`
- @RequestMapping("/rank/benefitPackage")
- @RequestMapping(value = "list.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/list.do",method = { RequestMethod.GET })
- @RequestMapping(value="/add.do",method = { RequestMethod.POST })
- @RequestMapping(value="/getDetail.do",method = { RequestMethod.GET })
- @RequestMapping(value="/update.do",method = { RequestMethod.POST })
- @RequestMapping(value = "/delete.do",method = { RequestMethod.POST })
- @RequestMapping(value = "/operateUpOrDown.do", method = { RequestMethod.POST })

## CardOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/rank/CardOrderController.java`
- @RequestMapping("/rank/cardOrder")
- @RequestMapping(value = "list.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/list.do")
- @PostMapping(value="/deliver.do")
- @RequestMapping(value = "/export.do", method = { RequestMethod.GET })
- @RequestMapping(value = {"/getCardList.do"},method = RequestMethod.GET)
- @RequestMapping(value = {"/getExpressList.do"},method = RequestMethod.GET)

## CardStockController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/rank/CardStockController.java`
- @RequestMapping("/rank/cardStock")
- @RequestMapping(value = "list.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/list.do", method = { RequestMethod.GET })

## BenefitOrderReportInfoController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/rank/BenefitOrderReportInfoController.java`
- @RequestMapping("/rank/benefitOrderReport")
- @RequestMapping(value = "list.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/list.do")

## BenefitController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/rank/BenefitController.java`
- @RequestMapping("/rank/benefit")
- @RequestMapping(value = "list.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/list.do")
- @PostMapping(value="/saveOrUpdate.do")
- @GetMapping("/getBreakevenPrice.do")
- @RequestMapping(value = "/operatess", method = { RequestMethod.POST })

## MemberBenefitController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/rank/MemberBenefitController.java`
- @RequestMapping("/rank/memberBenefit")
- @RequestMapping(value = "list.html", method = { RequestMethod.GET })
- @RequestMapping(value = "/list.do")
- @RequestMapping(value = "/consumerList.do", method = { RequestMethod.GET })

## InvoiceCheckController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/upp/InvoiceCheckController.java`
- @RequestMapping("/invoiceCheck/")
- @RequestMapping(value = {"invoiceCheck.html"}, method = {RequestMethod.GET})
- @RequestMapping("invoiceCheck.do")
- @RequestMapping(value = {"queryInvoiceForSettle.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = "addInvoice.html", method = {RequestMethod.GET})
- @RequestMapping(value = "getInvoiceInfo.do", method = {RequestMethod.POST})
- @PostMapping(value = "getInvoiceInfoForVpp.do")
- @RequestMapping(value = {"/addInvoices.do"}, method = {RequestMethod.POST})
- @PostMapping(value = {"/addInvoicesForVpp.do"})
- @RequestMapping(value = {"/updateInvoices.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/invoiceOccupy.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/deleteInvoice.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = "manualAddInvoice.html", method = {RequestMethod.GET})
- @RequestMapping(value = "getInvoiceInfoToCheck.do", method = {RequestMethod.POST})
- @RequestMapping(value = {"/manualAddInvoice.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/updateInvoiceXml.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = "batchGetInvoiceInfo.do", method = {RequestMethod.POST})
- @RequestMapping(value = "getBatchProgress.do", method = {RequestMethod.POST})
- @RequestMapping(value = "batchAddInvoice.html", method = {RequestMethod.GET, RequestMethod.POST})
- @PostMapping("findByIdForVpp.do")

## UppRecordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/upp/UppRecordController.java`
- @RequestMapping("/uppRecord/")
- @RequestMapping(value = {"uppRecord.html"}, method = {RequestMethod.GET})
- @RequestMapping("uppRecord.do")

## YbzRecordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/self/YbzRecordController.java`
- @RequestMapping("/ybzRecord/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("/doExport.do")

## SelfOrderIncomeRecordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/self/SelfOrderIncomeRecordController.java`
- @RequestMapping("/selfOrderIncomeRecord/")
- @RequestMapping(value = {"selfOrderIncome.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/querySelfOrderIncome.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"exportOrderToSapSelfAccount.do"}, method = {RequestMethod.GET})

## SapPurchaseController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/self/SapPurchaseController.java`
- @RequestMapping("/sapPurchase/")
- @RequestMapping(value = {"sapPurchaseRecord.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"querySapPurchaseRecord.do"}, method = {RequestMethod.GET})
- //    @RequestMapping(value = {"exportSapPurchaseRecord.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"exportSapPurchaseRecord.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"queryPurchaseForSettle.do"}, method = {RequestMethod.POST})
- @PostMapping(value = {"/addForVpp.do"})
- @PostMapping("findByIdForVpp.do")

## PurchaseApplySettleController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/self/PurchaseApplySettleController.java`
- @RequestMapping("/purchaseApplySettle/")
- @RequestMapping(value = {"purchaseApplySettle.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"queryPurchaseApplySettle.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"exportPurchaseApplySettle.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"gotoPurchaseApplySettleDetailView.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"gotoPurchaseApplySettleAddView.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryMdmSupplier.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/addPurchaseApplySettle.do"}, method = {RequestMethod.POST})
- @PostMapping(value = {"/addPurchaseApplySettleForVpp.do"})
- @RequestMapping(value = {"/gotoPurchaseApplySettleEditView.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/editPurchaseApplySettle.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/deletePurchaseApplySettle.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"purchaseApplyCheck.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryPurchaseApplyCheck.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/checkPurchaseApply.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"exportPurchaseApplyCheck.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"purchaseApplyConfirm.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"purchaseApplyRetentionMoney.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"queryPurchaseApplyConfirm.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"queryPurchaseApplyRetentionMoney.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryPurchaseApply.do"})
- @RequestMapping(value = {"/confirmPurchaseApply.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"exportPurchaseApplyConfirm.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"gotoPurchaseApplySettleAddPrepayView.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/addPurchaseApplySettlePrepay.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/editPurchaseApplySettlePrepay.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/gotoInvoiceCheckPrepayView.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/invoiceCheckPrepay.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"exportPurchaseApplyRetentionMoney.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/queryApplySettleTotalInfo.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/batchConfrim.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/createPurchaseSettlePdf.do"}, method = {RequestMethod.POST})
- @PostMapping("findByIdForVpp.do")
- @RequestMapping(value = {"/findPayBankList.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = "/queryContractNo.do", method = RequestMethod.GET)
- @RequestMapping(value = "/queryCmEpcBillUrl.do", method = RequestMethod.GET)

## PurchaseApplySettleDepositRefundController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/self/PurchaseApplySettleDepositRefundController.java`
- @RequestMapping("/purchaseApplySettleDepositRefund/")
- @RequestMapping(value = {"list.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"doList.do"}, method = {RequestMethod.GET})
- @RequestMapping("detail.html")
- @RequestMapping("audit.html")
- @RequestMapping("audit.do")
- @RequestMapping("/doExport.do")

## SapPurchaseFreezeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/self/SapPurchaseFreezeController.java`
- @RequestMapping("/sapPurchaseFreeze/")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("add.html")
- @RequestMapping(value = {"/add.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping("doExport.do")
- @GetMapping("queryTotalByBatchNo.do")
- @GetMapping("relateFile.do")
- @GetMapping("audit.do")

## FinanceInvoiceController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/self/FinanceInvoiceController.java`
- @RequestMapping("/financeInvoice/")
- @RequestMapping(value = {"financeInvoiceList.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"queryFinanceInvoiceSelf.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"exportSelfIncomeInvoice.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"queryFinanceInvoiceSeller.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"exportSellerInvoice.do"}, method = {RequestMethod.GET})

## SapRelationController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/self/SapRelationController.java`
- @RequestMapping("/sapRelation/")
- @RequestMapping(value = "/createOrderSapQueue.do", method = RequestMethod.GET)

## PayAccountQuotaConfigController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/self/PayAccountQuotaConfigController.java`
- @RequestMapping("payAccountQuotaConfig/")
- @RequestMapping(value = {"list.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"doList.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/add.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/update.do"}, method = {RequestMethod.POST})
- @RequestMapping("freeze.do")
- @RequestMapping("unFreeze.do")
- @RequestMapping("cancel.do")
- @RequestMapping("doExport.do")
- @RequestMapping(value = {"/report/list.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/report/doList.do"}, method = {RequestMethod.GET})
- @RequestMapping("/report/doExport.do")
- @RequestMapping(value = {"/findPayAccountConfigList.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/setDefaultPayType.do"}, method = {RequestMethod.GET})

## CustomerCommissionController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/self/CustomerCommissionController.java`
- @RequestMapping("/customerCommission/")
- @RequestMapping(value = {"customerCommission.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"queryCustomerCommissionDetails.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"exportCustomerCommissionDetails.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"queryCustomerCommissionSummary.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"queryCommissionDetailsByCustomerName.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"exportCustomerCommissionSummary.do"}, method = {RequestMethod.GET})

## PurchaseApplySettleNoPaperController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/self/PurchaseApplySettleNoPaperController.java`
- @RequestMapping("/purchaseApplySettleNoPaper/")
- @RequestMapping(value = {"list.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"doList.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"detail.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"audit.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"auditOk.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"auditFail.do"}, method = {RequestMethod.POST})
- @RequestMapping("doExport.do")

## PurchaseApplySettleQuotaAuditController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/self/PurchaseApplySettleQuotaAuditController.java`
- @RequestMapping("/purchaseApplySettleQuotaAudit/")
- @RequestMapping("list.html")
- @RequestMapping("/doList.do")
- @RequestMapping("add.html")
- @PostMapping("add.do")
- @RequestMapping("detail.html")
- @RequestMapping("audit.html")
- @RequestMapping("audit.do")
- @RequestMapping("update.html")
- @PostMapping("update.do")
- @GetMapping("export.do")

## DepositRecordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/self/DepositRecordController.java`
- @RequestMapping("/depositRecord/")
- @RequestMapping("list.html")
- @RequestMapping("/doList.do")
- @RequestMapping("/doExport.do")

## BccRebateController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/self/BccRebateController.java`
- @RequestMapping("/bccRebate/")
- @RequestMapping(value = {"bccRebate.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"queryBccRebate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"exportBccRebateRecord.do"}, method = {RequestMethod.GET})

## CashSelfOrderItemController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/self/CashSelfOrderItemController.java`
- @RequestMapping("/self/")
- @RequestMapping("cashSelfOrderItemList.html")
- @RequestMapping("selfOrderItem.do")
- @RequestMapping(value = {"exportCashSelfOrderItemList.do"}, method = {RequestMethod.GET})

## IncomeRecordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/self/IncomeRecordController.java`
- @RequestMapping("/incomeRecord/")
- @RequestMapping(value = {"/sapHandIncome.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = "/sapHandIncome.do", method = {RequestMethod.GET})
- @RequestMapping(value = {"/importSapHandIncome.do"}, method = {RequestMethod.POST})

## ReportIncomeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/report/ReportIncomeController.java`
- @RequestMapping("/report/")
- @RequestMapping(value = {"report.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"queryReportIncome.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"exportReportIncome.do"}, method = {RequestMethod.GET})

## LnThirdOrderController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/lnThirdOrder/LnThirdOrderController.java`
- @RequestMapping("/lnThirdOrder/")
- @RequestMapping(value = {"lnThirdOrder.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"queryLnThirdOrder.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"lnThirdCommissionPaymentRecord.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"queryLnThirdCommissionPaymentRecord.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"lnThirdFeeRecord.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"queryLnThirdFeeRecord.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/downloadLnThirdOrderTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importLnThirdOrder.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downloadLnThirdOrderError.do"}, method = {RequestMethod.GET})

## FinancialSolutionsController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/customerManagement/FinancialSolutionsController.java`
- @RequestMapping("/financialSolutions/")
- @RequestMapping(value = {"financialSolutions.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"queryFinancialSolutions.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"queryFinancialSolutionsDetails.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"confirmTicketed.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"exportFinancialSolutions.do"}, method = {RequestMethod.GET})

## CustomerOrderDetailsController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/customerManagement/CustomerOrderDetailsController.java`
- @RequestMapping("/customerOrderDetails/")
- @RequestMapping(value = {"customerOrderDetails.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"queryCustomerOrderDetails.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"receivableOrderDetails.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"findOrderDetailsList.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"customerOrderOverDue.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"queryCustomerOrderOverDue.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"findOverDueOrderDetailsList.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"exportCustomerOrderDetails.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"exportCustomerOrderOverDue.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"exportOrderDetailsList.do"}, method = {RequestMethod.GET})

## CreditCustomerController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/customerManagement/CreditCustomerController.java`
- @RequestMapping("/creditCustomer/")
- @RequestMapping(value = {"creditCustomer.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"queryCreditCustomerInfo.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"exportCreditCustomerInfo.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"queryQuotaAndAccount.do"}, method = {RequestMethod.GET})

## MdrCustomerController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/customerManagement/MdrCustomerController.java`
- @RequestMapping("/mdrCustomer/")
- @RequestMapping(value = {"mdrCustomer.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"queryMdrCustomerInfo.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"findMdrCustomerInfoById.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"findMdrCustomerLimitLog.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"findByCustomerName.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"exportMdrCustomerInfo.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"createMdrCustomerContractInfo.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"findContractList.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"createMdrCustomerInfo.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"queryCustomerInfoByMdm.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"syncMdrCustomerInfo.do"}, method = {RequestMethod.GET})

## FinanceErrorLogController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/error/FinanceErrorLogController.java`
- @RequestMapping("/financeErrorLog/")
- @RequestMapping(value = {"financeErrorLog.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"queryFinanceErrorLog.do"}, method = {RequestMethod.GET})

## ManualJob
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/job/ManualJob.java`
- @RequestMapping("/finance/job")
- @RequestMapping(value = "/downloadBillAlipay", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/checkAccountAlipay", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/downloadBillWechat", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/checkAccountWechat", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/downloadBillCcb", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/checkAccountCcb", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/pullBillTransfer", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/checkAccountTransfer", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/confirmOrderItem", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/confirmSettlement", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/summarySettlementVoucher", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/summarySettlements", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/cashSummery", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/syncSap", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/mpcRebate", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/queryMpcRebate", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/pullKjtChargeFee", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/checkKjtChargeFee", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/reverse", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/pullLnThirdOrder", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/checkLnThirdOrder", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/pullMdrCustomerInfo", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/pullCreditCustomerInfo", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/pullMdrCustomerOrderDetails", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/pullMdrFinancialSolutions", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/uppInvoiceCheck", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/createOrderSapQueue", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/createTransferOrder", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/pullHaierAccountList", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/manulInvoice", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/xiaoshunCommissionSummary", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/xiaoshunCommissionResult", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/pullReport", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/pullMdmCustomerInfo", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/gtmsRebate", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/queryGtmsRebate", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/kjtDownAndCheckHandle", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/payOrderQuery", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/payOrderQueryByCompany", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/electricOrderDaySum", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/electricOrderMonthSum", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/coinIncomeDaySum", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/energyCenterIncomeDay", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/cmPaymentSapDeliver", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
- @RequestMapping(value = "/income/reverse", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)

## SettlementThirdOrderItemController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/third/SettlementThirdOrderItemController.java`
- @RequestMapping("/thirdSettlement/")
- @RequestMapping("thirdOrderItemSettlement.html")
- @RequestMapping("orderItemThirdSettlement.do")
- @RequestMapping(value = {"exportOrderItemThirdSettlementList.do"}, method = {RequestMethod.GET})
- @RequestMapping("thirdSettlementCustomSum.do")
- @RequestMapping(value = {"exportThirdSettlementCustomSumList.do"}, method = {RequestMethod.GET})
- @RequestMapping("thirdSettlementDailySum.do")
- @RequestMapping(value = {"exportThirdSettlementDailySumList.do"}, method = {RequestMethod.GET})
- @RequestMapping("orderItemThirdRebate.do")
- @RequestMapping(value = {"exportOrderItemThirdRebateList.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"orderItemThirdSettlementListDetail.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"orderItemThirdSettlementListDetailSum.html"}, method = {RequestMethod.GET})

## CashPoolThirdController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/third/CashPoolThirdController.java`
- @RequestMapping("/cashPoolThird/")
- @RequestMapping("cashPoolThirdList.html")
- @RequestMapping("queryCashPoolThirdList.do")
- @RequestMapping(value = {"exportCashPoolThirdList.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"cashPoolThirdDetailsList.html"}, method = {RequestMethod.GET})

## MpcRebateRecordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/third/MpcRebateRecordController.java`
- @RequestMapping("/mpcRebates/")
- @RequestMapping("mpcRebateRecordList.html")
- @RequestMapping("mpcRebateRecordList.do")
- @RequestMapping("mpcRebateRecordLogBackList.do")
- @RequestMapping("dealRebatesLog.do")

## CashThirdOrderItemController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/third/CashThirdOrderItemController.java`
- @RequestMapping("/thirdCash/")
- @RequestMapping("orderItemFeeThirdList.html")
- @RequestMapping("orderItemFeeThird.do")
- @RequestMapping(value = {"exportOrderItemFeeThirdList.do"}, method = {RequestMethod.GET})
- @RequestMapping("cashThirdOrderItem.do")
- @RequestMapping(value = {"exportCashThirdOrderItemList.do"}, method = {RequestMethod.GET})
- @RequestMapping("cashThirdOrderItemDailySum.do")
- @RequestMapping(value = {"exportCashThirdOrderItemDailySumList.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"orderItemFeeThirdListDetail.html"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"cashThirdOrderItemListDetail.html"}, method = {RequestMethod.GET})

## BillController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/check/BillController.java`
- @RequestMapping("/bill/")
- @RequestMapping("thirdList.html")
- @RequestMapping("alipayList.do")
- @RequestMapping(value = {"exportAlipayList.do"}, method = {RequestMethod.GET})
- @RequestMapping("wechatList.do")
- @RequestMapping(value = {"exportWechatList.do"}, method = {RequestMethod.GET})
- @RequestMapping("ccbList.do")
- @RequestMapping(value = {"exportCcbList.do"}, method = {RequestMethod.GET})
- @RequestMapping("netPayList.do")
- @RequestMapping("selfList.html")
- @RequestMapping("billList.do")
- @RequestMapping(value = {"exportBillList.do"}, method = {RequestMethod.GET})

## CheckAccountErrorController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/check/CheckAccountErrorController.java`
- @RequestMapping("/checkAccount/")
- @RequestMapping("checkAccountErrorList.html")
- @RequestMapping("checkAccountError.do")

## OrderItemUnCashController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/check/OrderItemUnCashController.java`
- @RequestMapping("/unCash")
- @RequestMapping("orderItemUnCashList.html")
- @RequestMapping("orderItemUnCash.do")
- @RequestMapping(value = {"exportOrderItemUnCashList.do"}, method = {RequestMethod.GET})

## OutBusinessFeeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/finance/check/OutBusinessFeeController.java`
- @RequestMapping("/outBusiness")
- @RequestMapping("outBusinessFeeList.html")
- @RequestMapping("outBusinessFee.do")
- @RequestMapping(value = {"exportOutBusinessFeeList.do"}, method = {RequestMethod.GET})

## MemberVatInvoiceController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/invoice/MemberVatInvoiceController.java`
- @RequestMapping("/memberVatInvoiceQua/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"/exportMemberVatInv.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/auditSuccess.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/auditReject.do"}, method = {RequestMethod.POST})

## InvoiceListController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/invoice/InvoiceListController.java`
- @RequestMapping("/invoice")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## HrflcSyncPvInfoController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/hrflc/HrflcSyncPvInfoController.java`
- @RequestMapping("/hrflc/syncInfo")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("export.do")
- @RequestMapping(value = "/importData.do", method = RequestMethod.POST)
- @RequestMapping(value = "/getReSyncFile.do", method = RequestMethod.GET)
- @RequestMapping(value = "/rePushProject.do", method = RequestMethod.POST)
- @RequestMapping(value = "/allFileSync.do", method = RequestMethod.GET)
- @RequestMapping("hrflcSyncPvInfoDetail.html")

## HrflcPvPriceConfigController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/hrflc/HrflcPvPriceConfigController.java`
- @RequestMapping("/hrflc/price")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("export.do")
- @RequestMapping(value = "/count.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/batchDisable.do", method = {RequestMethod.POST})
- @RequestMapping(value = "/importData.do", method = RequestMethod.POST)

## HrflcPvFileRecordController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/hrflc/HrflcPvFileRecordController.java`
- @RequestMapping("/hrflc/file")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("export.do")

## HrflcReleCodeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/hrflc/HrflcReleCodeController.java`
- @RequestMapping("/hrflc/releCode")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("maintainInvoice.html")
- //    @RequestMapping(value = {"/submitUpload.do"}, method = {RequestMethod.POST})
- //    @PostMapping("submitUpload.do")
- @PostMapping("submitUpload.do")
- @RequestMapping("export.do")
- //    @RequestMapping(value = "/importData.do", method = RequestMethod.POST)
- //    @RequestMapping(value = "/getReSyncFile.do", method = RequestMethod.GET)
- //    @RequestMapping(value = "/rePushProject.do", method = RequestMethod.POST)
- //    @RequestMapping(value = "/allFileSync.do", method = RequestMethod.GET)
- //    @RequestMapping("hrflcSyncPvInfoDetail.html")

## HrflcAuditOwnerController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/hrflc/HrflcAuditOwnerController.java`
- @RequestMapping("/hrflc/auditOwner")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("export.do")

## HrflcStationController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/hrflc/HrflcStationController.java`
- @RequestMapping("/hrflcStation")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## GroupItemController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/group/GroupItemController.java`
- @RequestMapping("/groupItem/")
- @RequestMapping("list.html")
- @RequestMapping(value = {"list.do"}, method = { RequestMethod.POST })
- @RequestMapping(value = { "saveGroupItem.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "enabled.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "disabled.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "editSort.do" }, method = { RequestMethod.POST })

## PosthouseGroupController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/group/PosthouseGroupController.java`
- @RequestMapping("/posthouseGroup/")
- @RequestMapping("list.html")
- @RequestMapping(value = {"list.do"}, method = { RequestMethod.POST })
- @RequestMapping(value = { "saveGroup.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "editGroup.do" }, method = { RequestMethod.POST })

## GroupPurchaseController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/group/GroupPurchaseController.java`
- @RequestMapping("/group/")
- @RequestMapping("list.html")
- @RequestMapping(value = {"list.do"}, method = { RequestMethod.POST })
- @RequestMapping(value = { "auditOk.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "auditFail.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "enabled.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "disabled.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/listProvince.do" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/listRegion.do" }, method = {RequestMethod.GET})
- @RequestMapping(value= {"add.html"})
- @RequestMapping(value = { "/configInfo.do" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "saveConfig.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = {"/exportPosthouse.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = { "updateShop.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "batchUpdateShop.do" }, method = { RequestMethod.POST })

## LightSapDnQueueController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/gvs/LightSapDnQueueController.java`
- @RequestMapping("/gvs/dn")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightSapPoQueueController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/gvs/LightSapPoQueueController.java`
- @RequestMapping("/gvs/po")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightSapSoQueueController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/gvs/LightSapSoQueueController.java`
- @RequestMapping("/gvs/so")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## OrderForecastController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/orderForecast/OrderForecastController.java`
- @RequestMapping("/orderForecast")
- @RequestMapping("list.html")
- @RequestMapping(value ={"doList.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"addOrderForecast.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"updateOrderForecast.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"updateOrderForecastService.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping("detailList.html")
- @RequestMapping("detail.html")
- @RequestMapping("detailList.do")
- @RequestMapping("delete.do")
- @RequestMapping("audit.html")
- @RequestMapping("examine.html")
- @RequestMapping("audit.do")
- @RequestMapping("modify.html")
- @RequestMapping(value = {"/updateImportData.do"}, method = {RequestMethod.POST})
- @RequestMapping("monitorList.html")
- @RequestMapping("monitorServiceList.html")
- @RequestMapping("monitorServiceList.do")
- @RequestMapping("doExport.do")
- @RequestMapping("auditToMarket.do")
- @RequestMapping("subCenterExport.do")
- @RequestMapping("serviceExport.do")

## LightUnfinishedStationWarnController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/warn/LightUnfinishedStationWarnController.java`
- @RequestMapping("/station/warn")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("doExport.do")

## LightStationBankCardChangeController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/lightoperationbank/LightStationBankCardChangeController.java`
- @RequestMapping("/lightOperationBank")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @RequestMapping("firstAudit.do")
- @RequestMapping("finalAudit.do")
- @RequestMapping("/doExport.do")

## MemberTestMealController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/member/MemberTestMealController.java`
- @RequestMapping("/testMeal")
- @RequestMapping("list.html")
- @RequestMapping(value = "/getList.do")

## CommentController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/product/CommentController.java`
- @RequestMapping("/comment/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"firstMark.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"additionalMark.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"reply.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"additionalReply.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"exportCommentList.do"}, method = {RequestMethod.POST})

## CategoryDataController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/product/CategoryDataController.java`
- @RequestMapping("/categoryData/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"addCategory.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"updCategory.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = "addCategoryAttr.do", method = RequestMethod.POST, consumes = "application/json")
- @RequestMapping(value = {"findValueById.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"delCategory.do"}, method = {RequestMethod.POST})

## ProductDataController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/product/ProductDataController.java`
- @RequestMapping("/productData/")
- @RequestMapping("list.html")
- @RequestMapping("getSettleType")
- @RequestMapping("list.do")
- @RequestMapping(value = {"addProductData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = { "/querySupplier.do" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/getBySkuCode.do" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/downloadProductDataTemplate.do" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/importProductData.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = {"/downloadProductDataError.do"},method = {RequestMethod.GET})

## ShopSpuPlateformRateController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/product/ShopSpuPlateformRateController.java`
- @RequestMapping("/shopSpuPlateformRate/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"addShopPlateformRate.do"}, method = {RequestMethod.POST})

## ItemController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/product/ItemController.java`
- @RequestMapping("/item/")
- @RequestMapping("list.html")
- @RequestMapping(value = { "list.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "hideOperate.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "audit.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "batchAudit.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "updateSale.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/getSkuByItemId.do" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "/viewChange.do" }, method = {RequestMethod.GET})
- @RequestMapping(value = { "reIndex.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "exportItem.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = {"batchOff.do"}, method = {RequestMethod.POST})
- @RequestMapping("copyItemSku.do")

## ProductBreakevenPriceController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/product/ProductBreakevenPriceController.java`
- @RequestMapping(value = "/productBreakevenPrice/")
- @RequestMapping(value = "list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"addBreakevenPrice.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = { "/getMaterialCost.do" }, method = {RequestMethod.GET})
- @RequestMapping(value = {"updateBreakevenPrice.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downloadProductBreakevenPriceTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importProductBreakevenPrice.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downloadProductBreakevenPriceError.do"}, method = {RequestMethod.GET})

## SpuController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/product/SpuController.java`
- @RequestMapping("/spu/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = { "/listCategory.do" }, method = {RequestMethod.GET})
- @RequestMapping("selectCategory.html")
- @RequestMapping(value= {"add.html"})
- @RequestMapping(value = { "/listCategoryAttributeValue.do" }, method = {RequestMethod.GET})
- @RequestMapping(value = {"saveSpu.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"editPlateformRate.do"}, method = {RequestMethod.POST})
- @RequestMapping(value= {"edit.html"})
- @RequestMapping(value = { "/listSpuAttributeValue.do" }, method = {RequestMethod.GET})
- @RequestMapping(value = {"updateSpu.do"}, method = {RequestMethod.POST})

## CustomDrinksVoiceController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/product/CustomDrinksVoiceController.java`
- @RequestMapping("/customVoice/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"addVoice.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"editVoice.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"deleteVoice.do"}, method = {RequestMethod.POST})

## ProductPriceController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/product/ProductPriceController.java`
- @RequestMapping("/productPrice/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = { "delProductPrice.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "audit.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "/exportProductPrice.do" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/downloadProductPriceTemplate.do" }, method = { RequestMethod.GET })
- @RequestMapping(value = { "/importProductPrice.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = {"/downloadProductPriceError.do"},method = {RequestMethod.GET})
- @RequestMapping(value = { "/getLastEffectPriceBySkuCode.do" }, method = {RequestMethod.GET})
- @RequestMapping(value = {"batchAudit.do"}, method = {RequestMethod.POST})

## SkuRelateController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/product/SkuRelateController.java`
- @RequestMapping("/sku")
- @RequestMapping("skuRelateList.html")
- @RequestMapping("doSkuRelateList.do")
- @RequestMapping(value = "doSkuRelateAdd.do", method = {RequestMethod.POST})

## CustomDrinksController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/product/CustomDrinksController.java`
- @RequestMapping("/custom/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"findById.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"editRemark.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"linkOrderNo.do"}, method = {RequestMethod.POST})

## BrandController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/product/BrandController.java`
- @RequestMapping("/brand/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = { "addBrand.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "disabled.do" }, method = { RequestMethod.POST })
- @RequestMapping(value = { "enable.do" }, method = { RequestMethod.POST })

## ProductController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/product/ProductController.java`
- @RequestMapping("/product/")
- @RequestMapping("list.html")
- @RequestMapping("hello.do")

## ProductPurchaseCostController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/product/ProductPurchaseCostController.java`
- @RequestMapping("/productPurchaseCost/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"addProductPurchaseCost.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"delProductPurchaseCost.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/exportProductPurchaseCost.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/downloadTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})

## CmbLeasingStationController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/cmbeasing/CmbLeasingStationController.java`
- @RequestMapping("/cmbLeasingStation")
- @RequestMapping("list.html")
- @RequestMapping("doList.do")
- @GetMapping(value = {"/detail.html"})
- @GetMapping("operator.do")
- @PostMapping("change.do")
- @PostMapping("add.do")
- @RequestMapping(value = {"/importData.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/downTemplate.do"}, method = {RequestMethod.GET})
- @RequestMapping("doExport.do")
- @PostMapping("testPushFileInfo.do")
- @PostMapping("testPutFile.do")
- @PostMapping("testPushOrderInfo.do")
- @PostMapping("testBatchQueryOrderStatus.do")
- @PostMapping("testBatchCloseOrderList.do")
- @PostMapping("testFileInvalid.do")
- @PostMapping("closeOrder.do")
- @PostMapping("batchAuditOk.do")
- @PostMapping("importFileData.do")
- @PostMapping("pullUpStatus.do")

## CustomizedItemController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/carousel/CustomizedItemController.java`
- @RequestMapping("/customizedItem/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"addCustomizedItem.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"delete.do"}, method = {RequestMethod.POST})

## HomePageCustomZoneController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/carousel/HomePageCustomZoneController.java`
- @RequestMapping("/homePageCustomZone/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"delete.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"add.do"}, method = {RequestMethod.POST})

## HomePageHotItemController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/carousel/HomePageHotItemController.java`
- @RequestMapping("/homePageHotItem/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"delete.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"disable.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"enable.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"add.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"changeSort.do"}, method = {RequestMethod.POST})

## HomePageFloorImageController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/carousel/HomePageFloorImageController.java`
- @RequestMapping("/homePageFloorImage/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"delete.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"disable.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"enable.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"add.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"move.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"listFloorInfo.do"}, method = {RequestMethod.GET})
- @RequestMapping(value = {"getInfo.do"}, method = {RequestMethod.GET})

## AppVideoController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/carousel/AppVideoController.java`
- @RequestMapping("/appVideo/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"addAppImage.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"/addAppFiles.do"}, method = RequestMethod.POST, produces = "application/json;charset=utf-8")

## CarouselController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/carousel/CarouselController.java`
- @RequestMapping("/carousel/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"addCarousel.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"disable.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"enable.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"delete.do"}, method = {RequestMethod.POST})

## HomePageFloorItemController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/carousel/HomePageFloorItemController.java`
- @RequestMapping("/homePageFloorItem/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"disable.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"enable.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"add.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"changeSort.do"}, method = {RequestMethod.POST})

## HomePageRecommendController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/carousel/HomePageRecommendController.java`
- @RequestMapping("/homePageRecommend/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"delete.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"disable.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"enable.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"add.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"changeSort.do"}, method = {RequestMethod.POST})

## CnAppImageController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/carousel/CnAppImageController.java`
- @RequestMapping("/cnAppImage/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"addAppImage.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"delete.do"}, method = {RequestMethod.POST})

## ArticleItemController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/carousel/ArticleItemController.java`
- @RequestMapping("/articleItem/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"getDetail.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"editArticleItem.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"disable.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"enable.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"delete.do"}, method = {RequestMethod.POST})

## AppImageController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/carousel/AppImageController.java`
- @RequestMapping("/appImage/")
- @RequestMapping("list.html")
- @RequestMapping("yzzList.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"addAppImage.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"delete.do"}, method = {RequestMethod.POST})

## BulletinController
- 文件: `rrsjk-admin-web/src/main/java/com/rrsjk/admin/controller/carousel/BulletinController.java`
- @RequestMapping("/bulletin/")
- @RequestMapping("list.html")
- @RequestMapping("list.do")
- @RequestMapping(value = {"addBulletin.do"}, method = {RequestMethod.POST})
- @RequestMapping(value = {"delete.do"}, method = {RequestMethod.POST})

## CrawlScMembersUsersDetailController
- 文件: `vpp-data-platform/vpp-data-platform-biz/src/main/java/com/nahui/energy/controller/CrawlScMembersUsersDetailController.java`
- @RequestMapping("/platform/crawlScMembersUsersDetail")
- @GetMapping("/findByPage")
- @GetMapping("/export")

## TsKvController
- 文件: `vpp-data-platform/vpp-data-platform-biz/src/main/java/com/nahui/energy/controller/TsKvController.java`
- @RequestMapping("/platform/tskv")
- @PostMapping("/queryByPageWithTimeRange")

## FileUploadController
- 文件: `vpp-data-platform/vpp-data-platform-biz/src/main/java/com/nahui/energy/controller/FileUploadController.java`
- @RequestMapping("/platform/upload_file")
- @PostMapping(value = "/upload_file", consumes = MediaType.MULTIPART_FORM_DATA_VALUE)
- @GetMapping("/health")
- @GetMapping("/supported-types")

## GreenEnergyReportStationCityDayController
- 文件: `vpp-data-platform/vpp-data-platform-biz/src/main/java/com/nahui/energy/controller/GreenEnergyReportStationCityDayController.java`
- @RequestMapping("/platform/greenEnergyReportStationCityDay")
- @GetMapping("/findByPage")
- @GetMapping("/export")

## ElectricityPriceController
- 文件: `vpp-data-platform/vpp-data-platform-biz/src/main/java/com/nahui/energy/controller/ElectricityPriceController.java`
- @RequestMapping("/platform/electricityPrice")
- @PostMapping("/query")

## CrawlScMembersGenerationController
- 文件: `vpp-data-platform/vpp-data-platform-biz/src/main/java/com/nahui/energy/controller/CrawlScMembersGenerationController.java`
- @RequestMapping("/platform/crawlScMembersGeneration")
- @GetMapping("/findByPage")
- @GetMapping("/export")

## OdsDynamicQueryController
- 文件: `vpp-data-platform/vpp-data-platform-biz/src/main/java/com/nahui/energy/controller/OdsDynamicQueryController.java`
- @RequestMapping("/platform/dynamic")
- @PostMapping("/queryByPage")

## CrawlerDataController
- 文件: `vpp-data-platform/vpp-data-platform-biz/src/main/java/com/nahui/energy/controller/CrawlerDataController.java`
- @RequestMapping("/crawlerData")
- @PostMapping("/pushData")
