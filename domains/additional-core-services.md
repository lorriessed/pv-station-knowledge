# 核心服务补充分析

本文档分析 PVS 光伏电站系统中 5 个核心服务的架构、API、业务流程、数据模型和依赖关系。

所有 5 个服务均采用 **Dubbo RPC 服务架构**（无 HTTP Controller），通过 `dubbo:service` 暴露 Dubbo 接口，通过 `dubbo:reference` 引用其他服务。数据层使用 MyBatis XML Mapper。

---

## 1. repairs - 维修工单服务

### 1.1 服务定位

**维修工单与备件管理服务**，是 PVS 运维体系的核心业务服务。负责管理逆变器/设备维修工单的全生命周期，包括工单创建、备件申请、借件/调拨/补库/回购等订单流程、仓库出入库管理、财务结算以及与 SAP/OMS/GVS 等外部系统的对接。

Dubbo 应用名：`repairs-service`

### 1.2 核心 Dubbo 服务暴露（50+ 接口）

**工作流服务（Flowable）**：
- `IWfTaskService` - 任务管理
- `IWfProcessService` - 流程管理
- `IWfModelService` - 流程模型
- `IWfInstanceService` - 流程实例
- `IWfFormService` - 表单管理
- `IWfDeployService` - 流程部署
- `IWfCopyService` - 抄送管理
- `IWfCategoryService` - 分类管理
- `IWfDeployFormService` - 部署表单
- `ActWorkflowInfoService` - 工作流信息

**基础数据**：
- `CdBranchInfoService` - 组织架构（服务商信息）
- `CdWarehouseService` - 仓库管理
- `CdWarehouseAddressService` - 仓库地址
- `CdWarehouseRouteService` - 调拨圈/调拨路线
- `CdMaterialService` - 备件/物料属性
- `CdMaterialWarrantService` - 备件保修期
- `CdMaterialSubstituteService` - 备件替换关系
- `CdDictDataService` - 字典数据
- `CdPosService` - 岗位信息

**订单管理**：
- `SpOrderService` - 工单主表（维修/补库/调拨/差额补库/借件等）
- `SpOrderDetailService` - 工单明细
- `SpOrderBackService` - 回购订单
- `SpOrderBorrowService` - 借件订单
- `SpOrderBorrowSnService` - 借件SN管理
- `SpTranService` - 出入库/调拨单
- `SpTranDetailService` - 出入库明细
- `SpTranSnService` - 出入库SN
- `SpTranSnDetailService` - 出入库SN明细
- `SpOldbackListsService` - 旧件退回清单
- `SpOldbackListsDetailService` - 旧件退回明细
- `SpQualityInspectService` - 质检单
- `SpQualityInspectDetailService` - 质检明细
- `SpReserveAllocationOrderService` - 备品分配单
- `SpReserveAllocationOrderDetailService` - 备品分配明细
- `WoPartService` - 工单备件信息
- `SpNscoTraceService` - NCSO追溯
- `SpIssueJobLogService` - 发件日志

**资金管理**：
- `SpForegiftService` - 账单流水/保证金
- `SpStoreageService` - 现有库存
- `SpPurchaseService` - 采购单
- `SpPurchaseDetailService` - 采购明细
- `SpWarehouseAttachService` - 仓库附件
- `SpTranSnDetailShService` - 上海出入库SN明细

**财务管理**：
- `SpAdvancePaymentService` - 预付款管理
- `SpAccountsPayableService` - 应付账款
- `SpAccountsPayableDetailService` - 应付明细
- `SpAccountsReceivableService` - 应收账款
- `SpAccountsReceivableDetailService` - 应收明细
- `SpAccountsDccService` - DCC账务
- `SpAdvanceClearEntityService` - 预付款清算
- `SpSapAccountService` - SAP账务
- `SpSettlementDataService` - 结算数据
- `RepairsRequestFundService` - 维修资金申请

**报表/其他**：
- `SpReportService` - 报表服务
- `SpSupplierPartsCostService` - 供应商备件成本
- `SpInverterInfoService` - 逆变器信息
- `SpInverterSnInfoService` - 逆变器SN信息
- `SpExpressCompanyService` - 快递公司
- `SpExpressRoutingService` - 快递路由
- `SpRoutingLogService` - 路由日志
- `RepairsAndRrsService` - OMS对接（中心备件）

### 1.3 业务流程

**工单主流程**：
```
工单来源（RRSJK/Light Operation）→ 创建工单(SpOrder) → 备件申请(WoPart)
→ 仓库发货(SpTran/SpTranDetail) → 物流跟踪(SpExpressRouting)
→ 服务商签收 → 维修完成 → 旧件退回(SpOldbackLists)
→ 财务结算(SpAccountsPayable/Receivable) → SAP对接
```

**借件流程**（BorrowOrderStatusEnum）：
```
运维商录入(0) → 待中心经理审批(1) → 待总部审批(3)
→ 待运维商/供应商认责 → 认责后生成回购单或转售后发货
→ 建站商发货 → 运维商入库 → 订单关闭
```

**回购流程**（BackOrderStatusEnum）：
```
初始(0) → 待分中心审核(1) → 待财务审核(2) → 待支付(3)
→ 打款提交(5) → 收款成功(6)/收款失败(7)
```

**旧件退回流程**（OldbackOrderStatusEnum）：
```
初始(0) → 审批中(1) → 确认退返(2) → 厂家签收(3)/厂家拒收(4)
→ 入库完成(8)/超期未回退(9)
```

### 1.4 数据库表

| 模块 | 表名 | 说明 |
|------|------|------|
| **基础数据** | cd_branch_info | 服务商/分支机构信息 |
| | cd_warehouse | 仓库信息 |
| | cd_warehouse_address | 仓库地址 |
| | cd_warehouse_center | 中心仓库 |
| | cd_warehouse_route | 调拨圈/路线 |
| | cd_material | 备件/物料信息 |
| | cd_material_warrant | 备件保修期 |
| | cd_material_substitute | 备件替换关系 |
| | cd_dict_data | 字典数据 |
| | cd_pos | 岗位信息 |
| | cd_file | 文件管理 |
| **订单管理** | sp_order | 工单主表 |
| | sp_order_detail | 工单明细 |
| | sp_order_back | 回购订单 |
| | sp_order_back_invoice | 回购发票 |
| | sp_order_borrow | 借件订单 |
| | sp_order_borrow_sn | 借件SN |
| | sp_order_borrow_detail | 借件明细 |
| | sp_tran | 出入库/调拨单 |
| | sp_tran_detail | 出入库明细 |
| | sp_tran_sn | 出入库SN |
| | sp_tran_sn_detail | 出入库SN明细 |
| | sp_tran_sn_detail_sh | 上海出入库SN明细 |
| | sp_tran_out | 出库记录 |
| | sp_oldback_lists | 旧件退回清单 |
| | sp_oldback_lists_detail | 旧件退回明细 |
| | sp_quality_inspect | 质检单 |
| | sp_quality_inspect_detail | 质检明细 |
| | sp_reserve_allocation_order | 备品分配单 |
| | sp_reserve_allocation_order_detail | 备品分配明细 |
| | wo_part | 工单备件 |
| | sp_nsco_trace | NCSO追溯 |
| | sp_issue_job_log | 发件日志 |
| **资金/财务** | sp_foregift | 保证金/账单流水 |
| | sp_storeage | 现有库存 |
| | sp_storeage_log | 库存日志 |
| | sp_purchase | 采购单 |
| | sp_purchase_detail | 采购明细 |
| | sp_warehouse_attach | 仓库附件 |
| | sp_advance_payment | 预付款 |
| | sp_accounts_payable | 应付账款 |
| | sp_accounts_payable_detail | 应付明细 |
| | sp_accounts_receivable | 应收账款 |
| | sp_accounts_receivable_detail | 应收明细 |
| | sp_accounts_dcc | DCC账务 |
| | sp_advance_clear_entity | 预付款清算 |
| | sp_sap_account | SAP账务 |
| | sp_settlement_data | 结算数据 |
| **逆变器** | sp_inverter_info | 逆变器信息 |
| | sp_inverter_sn_info | 逆变器SN信息 |
| **快递** | sp_express_company | 快递公司 |
| | sp_express_routing | 快递路由 |
| | sp_routing_log | 路由日志 |
| **工作流** | act_workflow_info | 工作流信息 |
| | wf_form | 工作流表单 |
| | wf_category | 流程分类 |
| | wf_copy | 抄送记录 |
| | wf_deploy_form | 部署表单 |
| **其他** | sp_file | 文件表 |
| | sp_interface_log | 接口日志 |
| | sp_material_num | 物料编号 |
| | sp_supplier_parts_cost | 供应商备件成本 |

### 1.5 状态/枚举

| 枚举类 | 说明 |
|--------|------|
| `BackOrderStatusEnum` | 回购订单状态：初始→分中心审核→财务审核→待支付→打款→收款成功/失败 |
| `BorrowOrderStatusEnum` | 借件订单状态：初始→中心经理审批→总部审批→认责→发货→入库→关闭（14种状态） |
| `OldbackOrderStatusEnum` | 旧件退回状态：初始→审批中→确认退返→厂家签收/拒收→入库完成/超期 |
| `AdvanceStatusEnum` | 预付款状态 |
| `AdvanceClearStatusEnum` | 预付款清算状态 |
| `InverterStatusEnum` | 逆变器状态 |
| `RrsBackStatusEnum` | RRS退回状态 |
| `SapBillTypeEnum` | SAP账单类型 |
| `IssueJobLogEnum` | 发件日志类型（GVS释放库存） |

### 1.6 外部依赖（Dubbo 引用）

| 依赖服务 | 接口 | 用途 |
|----------|------|------|
| cbs-system | `SystemService` | 系统服务 |
| cbs-system | `SysPartyService` | 组织信息 |
| rrsjk-item-service | `ProductDataService` | 产品主数据 |
| rrsjk-light-service | `LightOperationProviderService` | 光伏运维服务 |
| rrsjk-light-service | `LightWorkOrderService` | 光伏工单 |
| rrsjk-light-service | `LightStationService` | 电站信息 |
| rrsjk-light-service | `LightOpStaffService` | 运维人员 |
| rrsjk-light-service | `LightOpOrderService` | 运维订单 |
| rrsjk-light-service | `LightLendService` | 借件服务 |
| rrsjk-light-service | `LightModuleSnService` | 组件SN |
| rrsjk-light-service | `LightStationInverterChangeService` | 逆变器更换 |
| rrsjk-light-service | `LightSparePartsDepositService` | 备件押金 |
| rrsjk-light-service(v2) | `LightOperationWorkOrderService` | 运维工单v2 |
| rrsjk-merchant-service | `SupplierService` | 供应商服务 |
| rrsjk-merchant-service | `TransMdmCustomerAndSupplierService` | MDM客户/供应商同步 |
| rrsjk-finance-service | `SapRecordService` | SAP记录 |
| rrsjk-finance-service | `SapPurchaseRecordService` | SAP采购记录 |
| rrsjk-finance-service | `InvoiceService` | 发票服务 |
| rrsjk-finance-service | `MdrCustomerService` | 客户管理 |

---

## 2. rrsjk-item-service - 商品/物料服务

### 2.1 服务定位

**商品/产品管理服务**，负责商城商品（SPU/SKU）的全生命周期管理，包括商品发布、类目管理、价格管理、库存管理、搜索索引、评论收藏等。同时管理光伏相关的零碳套餐产品。

Dubbo 应用名：`rrsjk-item-service`

### 2.2 核心 Dubbo 服务暴露

**商品管理**：
- `ItemService` - 商品服务
- `ItemSkuService` - 商品SKU服务
- `ItemIndexService` - 商品索引
- `ItemSearchService` - 商品搜索
- `NewItemSearchService` - 新搜索服务
- `ItemSearchRecordService` - 搜索记录
- `ItemDetailService` - 商品详情
- `ItemDetailPreviewService` - 商品详情预览
- `ReleaseItemService` - 商品发布
- `ReleaseItemInitService` - 商品发布初始化
- `ItemOperateLogService` - 商品操作日志（隐式）

**SPU/SKU管理**：
- `SpuService` - SPU服务
- `SkuService` - SKU服务
- `SkuMealService` - SKU套餐
- `SkuRelateService` - SKU关联
- `SkuLimitedService` - SKU限购

**类目管理**：
- `CategoryService` - 类目服务
- `CategoryAttributeService` - 类目属性
- `CategoryMappingService` - 类目映射
- `FrontCategoryService` - 前台类目
- `FrontCategoryCarouselService` - 前台类目轮播
- `FrontCategoryTopItemService` - 前台置顶商品

**价格/成本**：
- `ProductDataService` - 产品主数据
- `ProductPriceService` - 产品价格
- `ProductPurchaseCostService` - 产品采购成本
- `ProductBreakevenPriceService` - 产品盈亏平衡价
- `BrandService` - 品牌管理
- `SettleTypeService` - 结算类型

**用户互动**：
- `CommentService` - 评论服务
- `CollectService` - 收藏服务

**零碳/光伏套餐**：
- `ZeroCarbonItemSetMealService` - 零碳商品套餐
- `ZeroCarbonItemSetMealStockService` - 零碳套餐库存
- `ZeroCarbonItemSetMealStockChangeLogService` - 零碳套餐库存变更日志

**其他**：
- `YzzCategoryService` - 驿站类目
- `YzzCategoryItemService` - 驿站类目商品
- `YzzOptItemService` - 驿站运营商品
- `CustomDrinksService` - 定制饮品
- `CustomDrinksVoiceService` - 定制饮品语音
- `SaleAreaService` - 销售区域
- `ShopSpuPlateformRateService` - 店铺SPU平台费率

### 2.3 核心业务逻辑

- **商品发布流程**：ReleaseItemInitService 初始化 → ReleaseItemService 发布 → ItemService 管理
- **搜索服务**：ItemSearchService/ItemIndexService 支持关键词搜索，记录搜索历史
- **价格管理**：ProductPriceService 管理商品价格，ProductPriceChangeLog 记录变更
- **零碳套餐**：ZeroCarbon 系列服务管理光伏零碳套餐商品及其库存

### 2.4 数据库表

| 模块 | 表名 | 说明 |
|------|------|------|
| **商品** | item | 商品表 |
| | item_sku | 商品SKU |
| | item_extras | 商品扩展 |
| | item_image | 商品图片 |
| | item_operate_log | 商品操作日志 |
| | item_page | 商品页面 |
| | item_search_record | 搜索记录 |
| | item_sale_channel | 商品销售渠道 |
| | item_chuneng | 淳能商品 |
| | item_audit_apply | 商品审核申请 |
| | item_audit_record | 商品审核记录 |
| **SPU** | spu | SPU表 |
| | spu_image | SPU图片 |
| | spu_attribute_value | SPU属性值 |
| | cbs_item_sku | CBS商品SKU |
| **SKU** | sku | SKU表 |
| | sku_meal | SKU套餐 |
| | sku_relate | SKU关联 |
| | sku_limited | SKU限购 |
| **类目** | category | 类目表 |
| | category_attribute | 类目属性 |
| | category_attribute_value | 类目属性值 |
| | category_mapping | 类目映射 |
| | front_category | 前台类目 |
| | front_category_carousel | 前台类目轮播 |
| | front_category_top_item | 前台置顶商品 |
| **价格/产品** | product_data | 产品主数据 |
| | product_price | 产品价格 |
| | product_price_change_log | 价格变更日志 |
| | product_purchase_cost | 产品采购成本 |
| | product_breakeven_price | 产品盈亏平衡价 |
| | brand | 品牌表 |
| | settle_type | 结算类型 |
| | sale_area | 销售区域 |
| | sale_channel | 销售渠道 |
| | shop_type_sale_channel | 店铺类型销售渠道 |
| | shop_spu_plateform_rate | 店铺SPU平台费率 |
| **用户互动** | comment | 评论表 |
| | comment_image | 评论图片 |
| | collect | 收藏表 |
| **零碳套餐** | zero_carbon_item_set_meal | 零碳套餐 |
| | zero_carbon_item_set_meal_content | 零碳套餐内容 |
| | zero_carbon_item_set_meal_stock | 零碳套餐库存 |
| | zero_carbon_item_set_meal_stock_change_log | 库存变更日志 |
| **驿站** | yzz_category | 驿站类目 |
| | yzz_category_item | 驿站类目商品 |
| | yzz_opt_item | 驿站运营商品 |
| **定制饮品** | custom_drinks | 定制饮品 |
| | custom_drinks_detail | 定制饮品明细 |
| | custom_drinks_voice | 定制饮品语音 |

### 2.5 外部依赖

| 依赖服务 | 接口 | 用途 |
|----------|------|------|
| rrsjk-system-service | `MessageService` | 消息服务 |
| rrsjk-system-service | `XiaoweiService` | 小微服务 |
| rrsjk-system-service | `BizRoleService` | 业务角色 |
| rrsjk-system-service | `RegionService` | 区域服务 |
| rrsjk-merchant-service | `ShopService` | 店铺服务 |
| rrsjk-merchant-service | `CountyShopService` | 县域店铺 |
| rrsjk-merchant-service | `PosthouseService` | 驿站服务 |
| rrsjk-merchant-service | `PosthouseConfigService` | 驿站配置 |
| rrsjk-merchant-service | `PosthouseGroupService` | 驿站分组 |
| rrsjk-merchant-service | `YzzShopService` | 驿站店铺 |
| rrsjk-member-service | `MemberService` | 会员服务 |
| rrsjk-trade-service | `BenefitPackageService` | 权益包服务 |
| rrs-dispenser-service | `WaterPointsOperatorService` | 水站运营服务 |

---

## 3. rrsjk-system-service - 系统服务

### 3.1 服务定位

**基础系统服务**，提供全平台共享的基础能力，包括：第三方账号集成（支付宝/微信/建行/百度等）、字典/区域/银行等基础数据、短信/邮件消息服务、定时任务管理、Token管理、敏感词过滤、OCR识别等。

Dubbo 应用名：`rrsjk-system-service-impl`

配置文件分拆为：`service-basic.xml`、`service-message.xml`、`service-task.xml`、`service-account.xml`、`service-token.xml`

### 3.2 核心 Dubbo 服务暴露

**账号服务**：
- `AccountService` - 账号服务
- `AccountAlipayService` - 支付宝账号
- `AccountWechatService` - 微信账号
- `AccountCcbService` - 建行账号
- `AccountKjtService` - 快检通账号
- `AccountBaiduService` - 百度账号
- `AccountTransferService` - 转账服务

**基础数据**：
- `RegionService` - 区域/行政区划
- `BankService` - 银行信息
- `BankAreaService` - 银行区域
- `BankNumberService` - 银行行号
- `BizRoleService` - 业务角色
- `DictTypeService` - 字典类型
- `DictValueService` - 字典值
- `CodeService` - 编码生成
- `ExpressService` - 快递服务
- `CalendarDayService` - 日历
- `ChainGroupService` - 连锁分组
- `XiaoweiService` - 小微服务
- `SubCenterInfoService` - 分中心信息
- `SensitiveWordService` - 敏感词
- `Oauth2ClientService` - OAuth2客户端
- `PageHtmlService` - 页面HTML
- `IdCardRecognizedService` - 身份证识别
- `OcrAnalyseRecordService` - OCR分析记录
- `DhMatchRegionService` - 电商匹配区域
- `GfMatchRegionService` - 光伏匹配区域

**消息服务**：
- `MessageService` - 统一消息服务
- `SmsTemplateService` - 短信模板
- `SmsLogService` - 短信日志
- `SmsBlacklistService` - 短信黑名单
- `EmailTemplateService` - 邮件模板
- `EmailLogService` - 邮件日志

**任务服务**：
- `JobService` - 定时任务管理

**Token服务**：
- `AccessTokenService` - 访问令牌
- `AccessTokenRefreshService` - Token刷新

### 3.3 数据库表

| 模块 | 表名 | 说明 |
|------|------|------|
| **账号** | account_alipay | 支付宝账号 |
| | account_wechat | 微信账号 |
| | account_ccb | 建行账号 |
| | account_kjt | 快检通账号 |
| | account_baidu | 百度账号 |
| | account_transfer | 转账记录 |
| **基础数据** | region | 区域/行政区划 |
| | bank_info | 银行信息 |
| | bank_area | 银行区域 |
| | bank_area_history | 银行区域历史 |
| | bank_number | 银行行号 |
| | biz_role | 业务角色 |
| | dict_type | 字典类型 |
| | dict_value | 字典值 |
| | code | 编码 |
| | express | 快递信息 |
| | calendar_day | 日历 |
| | chain_group | 连锁分组 |
| | xiaowei | 小微信息 |
| | sub_center_info | 分中心信息 |
| | sensitive_word | 敏感词 |
| | oauth2_client | OAuth2客户端 |
| | page_html | 页面HTML |
| | id_card_recognized | 身份证识别 |
| | ocr_analyse_record | OCR分析记录 |
| | dh_match_region | 电商匹配区域 |
| | gf_match_region | 光伏匹配区域 |
| | hrflc_bank_info | 华融银行信息 |
| **消息** | sms_template | 短信模板 |
| | sms_log | 短信日志 |
| | sms_blacklist | 短信黑名单 |
| | email_template | 邮件模板 |
| | email_log | 邮件日志 |
| **任务** | job | 定时任务 |
| **Token** | access_token | 访问令牌 |
| **API** | api_open | 开放API |
| **Area** | area_info | 区域信息 |

### 3.4 外部依赖

system-service 作为基础服务，主要**被其他服务调用**，自身对外部 Dubbo 服务的依赖较少。

---

## 4. rrsjk-pay-service - 支付服务

### 4.1 服务定位

**统一支付服务**，提供支付、退款、回调通知等核心支付能力。对接多种支付渠道（支付宝、微信、建行、百度等），支持商城订单支付、水站充值支付、光伏押金支付等场景。

Dubbo 应用名：`rrsjk-pay-service`

### 4.2 核心 Dubbo 服务暴露

- `PaymentService` - 支付服务（核心，timeout=5000）
- `PayService` - 支付下单服务
- `PayNotifyService` - 支付回调通知
- `RefundService` - 退款服务（timeout=7000）
- `RefundNotifyService` - 退款回调通知
- `PayDispenserService` - 水站支付服务
- `PayDispenserNotifyService` - 水站支付回调

### 4.3 核心业务逻辑

- **支付流程**：PayService 创建支付 → 调用对应支付渠道 → PaymentService 管理支付单 → 支付完成后 PayNotifyService 处理回调
- **退款流程**：RefundService 发起退款 → 调用对应渠道退款 → RefundNotifyService 处理退款回调
- **水站支付**：PayDispenserService 专门处理水站充值/购水场景的支付
- **多渠道支持**：通过引用 system-service 的各账号服务（支付宝/微信/建行等）实现多渠道支付

### 4.4 数据库表

| 表名 | 说明 |
|------|------|
| payment | 支付记录表 |

### 4.5 外部依赖

| 依赖服务 | 接口 | 用途 |
|----------|------|------|
| rrsjk-system-service | `MessageService` | 消息通知 |
| rrsjk-system-service | `XiaoweiService` | 小微服务 |
| rrsjk-system-service | `AccountAlipayService` | 支付宝支付 |
| rrsjk-system-service | `AccountWechatService` | 微信支付 |
| rrsjk-system-service | `AccountCcbService` | 建行支付 |
| rrsjk-system-service | `AccountKjtService` | 快检通支付 |
| rrsjk-system-service | `AccountTransferService` | 转账 |
| rrsjk-system-service | `AccountBaiduService` | 百度支付 |
| rrsjk-member-service | `MemberService` | 会员信息 |
| rrsjk-trade-service | `OrderService` | 订单服务 |
| rrsjk-trade-service | `OrderItemService` | 订单项 |
| rrsjk-trade-service | `OrderStatusService` | 订单状态 |
| rrsjk-trade-service | `OrderItemBuyerService` | 买家订单 |
| rrsjk-trade-service | `OrderTransferService` | 订单转移 |
| rrsjk-trade-service | `OrderRepairService` | 维修订单 |
| rrsjk-trade-service | `OrderLogService` | 订单日志 |
| rrsjk-finance-service | `CloudWisdomUserWalletChangeService` | 云智慧钱包变更 |
| rrsjk-light-service | `LightDepositService` | 光伏押金 |
| rrs-dispenser-service | `WaterCardMultiPaidService` | 水卡多支付 |
| shoppingmall-order | `PaymentDocumentService` | JK商城支付单据 |

---

## 5. rrsjk-merchant-service - 商户服务

### 5.1 服务定位

**商户/店铺管理服务**，管理商户入驻、店铺运营、驿站管理、供应商管理、客户关系、企业客户等。是平台商户体系的核心服务，支撑商城、光伏、水站等多业务线的商户管理需求。

Dubbo 应用名：`rrsjk-merchant-service`

### 5.2 核心 Dubbo 服务暴露

**商户管理**：
- `MerchantService` - 商户服务
- `MerchantResourceService` - 商户资源
- `IndustryCommerceService` - 工商服务

**供应商**：
- `SupplierService` - 供应商服务
- `SupplierCompanyService` - 供应商公司
- `ParkService` - 智慧园区服务

**店铺管理**：
- `ShopService` - 店铺服务
- `ShopExpressService` - 店铺快递
- `ShopCarouselService` - 店铺轮播
- `ShopCustomerService` - 店铺客户

**驿站**：
- `PosthouseService` - 驿站服务
- `PosthouseConfigService` - 驿站配置
- `PosthouseGroupService` - 驿站分组
- `YzzShopService` - 驿站店铺
- `YzzGuideService` - 驿站导购
- `YzzShopMemberService` - 驿站店铺会员

**企业客户**：
- `CorporateClientService` - 企业客户
- `CorporateClientProcessLogService` - 企业客户流程日志
- `CorporateClientDepositService` - 企业客户押金

**专业客户**：
- `ProfessionalCustomerService` - 专业客户
- `ExpertCustomerService` - 专家客户
- `ExpertCustomerContactsService` - 专家客户联系人

**配送**：
- `DriverDeliveryService` - 司机配送

**混合/关联**：
- `CountyShopService` - 县域店铺
- `UserOperatorRelationService` - 用户-运营商关系
- `OperatorShopRelationService` - 运营商-店铺关系

**定时任务**：
- `UserOperatorRelationJobService` - 用户运营商关系定时任务
- `OperatorShopRelationJobService` - 运营商店铺关系定时任务

**MDM 同步**：
- `TransMdmCustomerAndSupplierService` - MDM客户/供应商同步

### 5.3 核心业务逻辑

- **商户入驻流程**：商户申请 → 资质审核 → 创建店铺 → 配置快递 → 上线运营
- **驿站体系**：驿站创建 → 分组管理 → 配置管理 → 导购分配 → 店铺关联
- **企业客户**：企业客户申请 → 流程审批 → 押金管理 → 合同签订 → 信用管理
- **运营商关系**：UserOperatorRelation 和 OperatorShopRelation 管理用户、运营商、店铺之间的多对多关系，通过定时任务同步维护

### 5.4 数据库表

| 模块 | 表名 | 说明 |
|------|------|------|
| **商户** | merchant | 商户表 |
| | merchant_extras | 商户扩展 |
| | merchant_region | 商户区域 |
| | merchant_black_list_notice_record | 商户黑名单通知记录 |
| **供应商** | supplier | 供应商表 |
| | supplier_company | 供应商公司 |
| | supplier_contract | 供应商合同 |
| **园区** | park | 园区表 |
| | park_appraise | 园区评价 |
| | park_appraise_up | 园区评价-上级 |
| | park_appraise_two | 园区评价-二级 |
| **店铺** | shop | 店铺表 |
| | shop_extras | 店铺扩展 |
| | shop_cbs | 店铺CBS |
| | shop_express | 店铺快递 |
| | shop_carousel | 店铺轮播 |
| | shop_customer | 店铺客户 |
| **驿站** | posthouse | 驿站表 |
| | posthouse_config | 驿站配置 |
| | posthouse_group | 驿站分组 |
| | yzz_shop | 驿站店铺 |
| | yzz_shop_cbs | 驿站店铺CBS |
| | yzz_shop_member | 驿站店铺会员 |
| | yzz_guide | 驿站导购 |
| | yzz_guide_cbs | 驿站导购CBS |
| **企业客户** | corporate_client | 企业客户 |
| | corporate_client_process_log | 企业客户流程日志 |
| | corporate_client_deposit | 企业客户押金 |
| **专业客户** | professional_customer | 专业客户 |
| | expert_customer | 专家客户 |
| | expert_customer_contacts | 专家客户联系人 |
| | expert_customer_contract | 专家客户合同 |
| | expert_customer_contract_image | 专家客户合同图片 |
| | expert_customer_credit_use_detail | 专家客户信用使用明细 |
| **配送** | driver_delivery | 司机配送 |
| | driver_delivery_region | 司机配送区域 |
| **关联关系** | user_operator_relation | 用户-运营商关系 |
| | operator_shop_relation | 运营商-店铺关系 |
| **工商** | industry_commerce | 工商信息 |
| **商户资源** | merchant_resource | 商户资源 |

### 5.5 外部依赖

| 依赖服务 | 接口 | 用途 |
|----------|------|------|
| rrsjk-system-service | `MessageService` | 消息服务 |
| rrsjk-member-service | `MemberService` | 会员服务 |
| rrsjk-member-service | `MemberRoleService` | 会员角色 |
| rrsjk-member-service | `MemberAddressService` | 会员地址 |
| rrsjk-finance-service | `CustomerFinanceService` | 客户财务 |
| rrsjk-finance-service | `LightIncomeRecordService` | 光伏收入记录 |
| rrsjk-finance-service | `EaiOpenService` | EAI开关 |
| rrs-dispenser-service | `WaterSharePointsService` | 水站积分 |
| rrs-dispenser-service | `WaterCardService` | 水卡服务 |
| rrs-dispenser-service | `WaterDispenserOperatorService` | 水站运营商 |
| rrs-dispenser-service | `WaterDispenserAgentService` | 水站代理商 |
| rrs-dispenser-service | `WaterDispenserOperatorApplyService` | 水站运营商申请 |
| shoppingmall | `BasicService` | 商城基础服务 |

---

## 服务间依赖关系总览

```
┌─────────────────────────────────────────────────────────────┐
│                    rrsjk-system-service                      │
│   (账号/字典/区域/消息/任务/Token - 基础服务，被所有引用)       │
└──────┬──────────┬──────────┬──────────┬──────────────────────┘
       │          │          │          │
       ▼          ▼          ▼          ▼
┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────────────┐
│repairs   │ │item-     │ │pay-      │ │merchant-         │
│service   │ │service   │ │service   │ │service           │
│          │ │          │ │          │ │                  │
│依赖:     │ │依赖:     │ │依赖:     │ │依赖:             │
│item(PD)  │ │system    │ │system    │ │system            │
│merchant  │ │merchant  │ │member    │ │member            │
│light*    │ │member    │ │trade*    │ │finance           │
│finance   │ │trade     │ │light     │ │dispenser         │
│light(v2) │ │dispenser │ │finance   │ │shoppingmall      │
└──────────┘ └──────────┘ └──────────┘ └──────────────────┘
       │          │          │          │
       └──────────┴──────────┴──────────┘
                      │
          ┌───────────┼───────────┐
          ▼           ▼           ▼
    rrsjk-light   rrsjk-trade  rrsjk-finance
    rrsjk-member  rrs-dispenser shoppingmall
```

## 技术架构总结

| 维度 | 详情 |
|------|------|
| **通信协议** | Dubbo RPC（全部服务均无 HTTP Controller） |
| **数据层** | MyBatis XML Mapper |
| **服务拆分** | API/Impl 两层（*-api 定义接口和实体，*-impl 实现和配置） |
| **工作流** | repairs 集成 Flowable 工作流引擎 |
| **Dubbo 分组** | repairs 使用 `hds`、`mobile` 分组提供多版本服务 |
| **主要数据库** | MySQL（通过 JDBC 数据源配置） |

---

## CBS招投标管理审核模块 (代码明确证明, 2026-05-19)
**来源**: `rrsjk-light-service` → `TenderManagmentAudit.java`, `TenderManagmentAuditDto.java`, `TenderManagmentAuditServiceImpl.java`, `tenderManagmentAudit.xml` (commits f2eabc25, cb11fc99, laowang, 2026-05-15~18)
**需求**: TAEI-3102 【户用光伏】CBS招投标流程

- **Entity**: `TenderManagmentAudit` — 455行实体类 (注意拼写是 managment 而非 management)
- **DTO**: `TenderManagmentAuditDto` — 490行数据传输对象
- **Service**: `TenderManagmentAuditService` + `TenderManagmentAuditServiceImpl`
- **DAO**: `TenderManagmentAuditDao` — 67行，完整CRUD
- **Mapper**: `tenderManagmentAudit.xml` — 283行SQL映射
- **推断表**: `tender_managment_audit`
- **Git Author**: `laowang` (1162359451@qq.com) — 新发现，映射表中未记录
- **业务域**: CBS (招投标管理) — 新增模块

---

## 广发(GF)业务扩展 (代码明确证明, 2026-05-19)
**来源**: `rrsjk-light-service` → gf 包下多个文件 (commits 95e6085b, 78c868d4, 9ef2445c, e21d8269, 7a3fbe26, majinhu, 2026-05-12~18)

- **并网保险**: `GfMergeGridInputPieceRequest` +91行，`GfMergeGridInputPieceProcess` 新增投保方/被保方字段
- **CBS对接**: 广发电站并网查询 (`mergeStatus` 修复字段类型)
- **购售电合同**: `updateGfBusinessOpportunityInputPieceResult` 业主信息修改更正结果查询
- **技术审核**: 状态检查逻辑更新 (`refactor(gf)`)
- **状态拦截**: 完工进件、并网进件拦截退回驳回状态

