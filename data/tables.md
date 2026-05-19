# 表与字段

更新时间: 2026-05-13

## 已确认知识

### 核心表 (PVS)
- light_station：电站主表。
- light_station_audit：电站审核。
- light_station_plan_config：方案配置。
- light_use_order：领用单。
- light_make_order：制作订单。
- light_transfer_order：调拨单。
- light_station_inverter：电站逆变器完工绑定。
- light_inveter：逆变器日数据。
- light_inveter_small：逆变器明细数据。
- light_inveter_data：逆变器发电统计/发电绑定。
- light_policy_income_record：政策收入。
- light_sp_grid_award_order：营销奖励。
- light_share_bill：共享账单。
- light_project_rent_record：租金记录。

### VPP 电站/设备表 (vpp-api-elecbusiness)
- station_info：站点基础数据表
- device_info：设备基础数据表
- gen_realtime_data：发电设备实时数据表 (active_power_a/b/c)
- storage_realtime_data：储能设备实时数据表 (battery_soc, battery_soh)
- load_realtime_data：负荷设备实时数据表
- charge_gun_realtime_data：充电桩设备实时数据表 (in_active_power_a/b/c)
- measure_ele_realtime_data：电测量设备实时数据表
- measure_we_realtime_data：气象测量设备实时数据表
- device_statistic：设备统计数据表
- station_statistic：站点统计数据表 (generation, es_charge, es_discharge, co2_reduce, charger_consumption, charger_fee, gen_profit, es_net_profit, charge_service)
- dev_forecast：设备预测数据表
- station_alarm：站点告警数据表

### VPP 纳光宝表 (vpp-api-elecbusiness)
- ngb_station_base：纳光宝电站基本信息
- ngb_station_robot：纳光宝智能调度机器人
- ngb_station_social_contribution：纳光宝社会贡献
- ngb_operation_photovoltaic：纳光宝光伏运营
- ngb_operation_energy_storage：纳光宝储能运营
- ngb_operation_charging_station：纳光宝充电桩运营
- ngb_generation_power：纳光宝发电功率
- ngb_generation_energy：纳光宝储能充放电功率
- ngb_generation_load：纳光宝负载功率
- ngb_station_income：纳光宝收入表
- ngb_station_income_day：纳光宝日收入表
- ngb_station_income_month：纳光宝月收入表
- ngb_station_income_year：纳光宝年收入表
- ngb_station_user：纳光宝电站用户权限

### VPP 绿证交易表 (vpp-api-gect)
- customer：客户信息表
- customer_invoice_info：客户发票信息表
- intend_customer：意向客户表
- intend_customer_item：意向客户明细表
- intend_customer_audit_log：意向客户审批日志
- order_management_info：订单管理主表
- order_management_item：订单明细表
- order_management_item_gec：订单明细关联库存表
- order_contract_audit_log：合同审核日志
- order_voucher_audit_log：划证凭证审核日志
- payback_management_info：回款管理表
- payback_confirm_audit_log：回款凭证审核日志
- gec_purchase_order：绿证采购单
- gec_purchase_order_item：采购明细
- gec_purchase_order_item_receipt_voucher：采购收货凭证
- gec_purchase_contract：采购合同
- gec_purchase_apply_settle：采购请款结算
- gec_purchase_audit_log：采购审核日志
- project：主项目表
- sub_project：子项目表
- sales_entity_company：主体公司表
- project_company_trade_type：项目公司交易类型
- light_station_green_certificate_progress：电站绿证进度表
- import_task：导入任务日志
- invoice：发票表
- invoice_item：发票详情表
- invoice_attachment：发票附件表
- gec_invoice_check：绿证发票校验表
- sap_record：SAP记账记录
- sap_item_record：SAP记账子记录

### VPP 系统基础表 (vpp-api-common)
- sys_user：用户表
- sys_dept：部门表
- sys_role：角色表
- sys_menu：菜单权限表
- sys_post：岗位信息表
- sys_tenant：租户信息表
- sys_user_tenant：用户租户关联
- sys_user_role：用户角色关联
- sys_role_menu：角色菜单关联
- sys_role_dept：角色部门关联
- sys_user_post：用户岗位关联
- sys_dict_data：字典数据表
- sys_dict_type：字典类型表
- i18n_message：国际化消息表
- lan：语言配置表

### VPP 绿电收益表 (vpp-api-gpower, 2026-05-14)
- green_electricity_revenue：绿电收益主表 (order_no单号, status状态机, accounting_status记账状态)
- green_electricity_audit_log：绿电收益审核日志表
- power_grid_company：电网公司主数据表 (supplier_code, customer_code, unified_social_credit_code)
- power_grid_contract：电网公司合同表
- sap_record：SAP财务记账记录 (bid业务主键+ywms业务模式联合主键, flag返回状态)
- sap_item_record：SAP财务记账子记录 (dmbtr总额, dmbtr1手续费, dmbtr2税金, dmbtr3成本, dmbtr4收款)

### VPP 知识管理表 (vpp-api-km, 2026-05-14)
- knowledge_directory：知识库目录表 (树形结构, parent_id, publish_status)
- knowledge_file：知识库文件表 (tag标签逗号分隔, audit_staus审批状态)
- knowledge_file_mapping：目录-文件关联表 (多对多)
- knowledge_file_log：文件操作日志表
- knowledge_user：用户-知识库权限关联表 (checked=1选中/0未选中)

### VPP 产品出货表 (vpp-api-meta, 2026-05-14)
- t_product：产品表 (mdn产品型号唯一, dev_type=自研/供应商)
- t_product_image：产品图片表 (一对多)
- t_shipment_log：出货日志表 (关联product_id, hr_sn海尔SN, supplier_sn供应商SN)

### 关键字段
- first_three_power_at：首次连续三天发电时间，是业务"并网"口径的重要字段。
- enable_at：电站启用时间。

### VPP 海外光伏表 (vpp-pv-oversea, 2026-05-15)
- pv_station_info：电站数据主表 (pv_code, pv_status, pv_type, pay_status, invoice_status)
- pv_station_info_history：电站历史数据表
- pv_station_material：电站建站材料明细
- pv_station_pay_plan：电站付款计划 (plan_no, confirm_status, loan_or_not, pay_type)
- pv_station_invoice：发票信息表
- pv_service_provider：服务供应商表 (sp_code, sp_id)
- pv_service_provider_contract：服务商合同关系表
- service_provider_deposit：服务商押金表
- pv_purchase_order：采购单 (purchase_no, purchase_type, confirm_status)
- pv_picking_order：配货单 (picking_no, picking_status)
- pv_sale_order：销售单 (sale_order_no, sale_status, allocation_method, payment_status)
- pv_system_interaction_log：系统交互日志表
- oversea_request_log：外部API请求日志
- oversea_ybz_settlement_callback：云报账异步回调记录

### VPP 数据平台表 (vpp-data-platform, 2026-05-15)
- dynamic_query_user_whitelist：动态查询用户白名单
- dynamic_query_user_whitelist_rule：动态查询权限规则
- dynamic_query_audit_log：动态查询审计日志
- ts_kv_cf：时序键值对数据表 (SelectDB, entity_id, entity_type, key, ts, bool_v, str_v, long_v, dbl_v, json_v)
- electricity_price_data_clearing：电价数据表 (SelectDB, data_region_name, info_date, info_time, day_ahead, real_time, regulate)
- green_energy_report_station_city_day：绿能分时发电量日报表 (SelectDB ADS层)

### VPP 爬虫表 (vpp-crawler, 2026-05-15)
- crawl_sc_members_users：电力用户列表 (四川电力交易中心)
- crawl_sc_members_users_detail：电力用户明细
- crawl_sc_members_generation：发电企业列表
- crawl_sc_members_generation_detail：发电企业明细
- crawl_sc_members_sales：售电公司列表
- crawl_sc_members_sales_detail：售电公司明细
- crawl_sc_curve_load_forecast/actual：负荷预测/实际曲线 (96点)
- crawl_sc_curve_hydro_forecast/actual：水电出力预测/实际曲线
- crawl_sc_curve_power_forecast/actual：火电出力预测/实际曲线
- crawl_sc_curve_renewable_forecast/actual：新能源出力预测/实际曲线
- task_template：任务模板表
- task_instance：任务实例表
- crawl_sc_token_renewal_log：Token 续约日志
- crawl_sc_login_session：登录会话 (60分钟有效期)

## 招银租赁相关表 (rrsjk-light-service, 2026-05-15 代码明确证明)
- cmb_electric_price：招银电价配置表。V1 查询维度: province_name + city_name + 技术方案描述；V2 新增 region_name(区县) + lease_roof_type(租赁屋顶类型) + module_type(组件类型)，5维精确匹配
- cmb_leasing_station：招银电站进件状态表。状态流转: PUSH_FILE_INFO("B01") → PUSH_FILE("B02") → PUSH_STATION_INFO("B03", 电站进件推送) → PENDING_REVIEW("001", 待审核) → REVIEWING("002") → APPROVED("003")
- cmb_channel_log：招银渠道操作日志
- cmb_base_region：招银区域基础数据

## 运维管理/派单相关表 (rrsjk-light-service, TAEI-2709/2729/2730/2733/2735/2736, 2026-01-23~2026-01-30 代码明确证明)
- **来源**: `OperationMaintenanceServiceImpl.java`, `LightAuditDispatchLog.java`, `LightAuditDispatchLogServiceImpl.java`
- `operation_maintenance`: 运维管理表。字段: orderNo(管理单号), bookkeepingType(A48政策兑现/A51暂估), coverVoucher(冲销凭证号), coverAt(冲销时间), status(状态: COVERED=已冲销, CONFIRMED=已确认)
- `light_audit_dispatch_log`: 审核派单日志表。新增字段: dispatchYear/Month/Day(派单时间维度), dealYear/Month/Day(处理时间维度), dispatchType(派单类型), taskType(DISPATCH派单/GRAB_ORDER抢单), dealFlag(PASSED通过/REJECTED驳回)

## 零碳适家相关表 (rrsjk-light-service, TAEI-2738/2739/2745, 2026-01-22~2026-01-30 代码明确证明)
- **来源**: `LightZeroCarbonSkuData.java`, `CmPreOrderServiceImpl.java`
- `light_zero_carbon_sku_data`: 零碳适家SKU数据表。SKU类型: CHARGING_PILE(充电桩), REVERSE_FLOW_METER(防逆流电表)
- 零碳适家业务涉及: CBS采购单优化、保证金管理、订单批量确认回款、施工环节与energy对接

## 工商业采购/中转仓相关表 (rrsjk-light-service, TAEI-2777, 2026-01-20~2026-01-30 代码明确证明)
- **来源**: `CmPreOrderServiceImpl.java` commits fe2aadb3, 014e9fce
- `cm_pre_order`: 工商业采购单。字段: preOrderNo, consignee(收货人), provinceName/cityName/regionName/address(收货地址), mobile(联系电话)
- `light_transfer_order`: 调拨单。中转仓发货时从cmStore收货人信息改为从cmPreOrder取

## 来源
- PVS 部分: Hermes MEMORY.md，2026-05-09 迁移。
- VPP 部分: vpp-api-common/elecbusiness/ems/gateway/gect 全量通读, 2026-05-13。
- VPP 续: vpp-api-gpower/km/meta/system/template/openapi/pv-oversea/data-platform/crawler 全量通读, 2026-05-15。

## 新增来源 (2026-05-17 云效需求驱动扫描)
 - TAEI-2694~TAEI-2778 云效需求关联提交分析, rrsjk-light-service/rrsjk-admin-web/rrsjk-light-report-service/rrsjk-finance-service/rrsjk-light-operation-service

## 新增来源 (2026-05-18 历史补漏第1期: 2025-11-17~2025-12-07)
### 共享支付相关表 (rrsjk-light-service, TAEI-2716/2724/2727, 2025-11-17~2025-12-07 代码明确证明)
- **来源**: `LightShareBill.java`, `LightShareBillPayFailRecord.java`, `LightShareBillRecord.java`, `LightShareBillServiceImpl.java`, `ShareProjectPaymentAccount.java`
- `light_share_bill`: 共享账单表。字段: billNo(合计编码), projectCompanyCode/Name, subCenterCode/Name, createOrderAt(创单日期), num(数量), amount(金额), amountTax(服务费), totalAmount(总金额), status, confirmAt(确认时间), confirmBy(确认人), confirmPayAt(确认付款时间)
- `light_share_bill_record`: 共享支付明细表。关联 billNo，记录每笔支付明细
- `light_share_bill_pay_fail_record`: 共享支付失败记录表。字段: dealStatus(重新支付处理状态), dealAt(重复支付时间), dealBy(重新支付操作人), dealResult(重新支付结果), billRecordId/billNo/billRecordNo, stationCode, name(业主), phone, idCardNumber, bankAccount
- `light_share_bill_audit_log`: 共享账单审核日志
- `light_share_bill_record_fail_log`: 共享支付明细失败日志
- `light_share_bill_record_status_imp_rec`: 共享支付明细状态导入记录
- `share_project_payment_account`: 项目公司支付账户表。用于共享支付时取电站上的银行卡、联行号、支行名称(TAEI-2716)
- 业务流程: 创建支付明细时从电站银行卡信息取账户数据 → 支付成功/失败记录 → 失败时可重新支付并记录处理结果

### 运维商授权区域相关表 (rrsjk-light-service, TAEI-2698/2699, 2025-11-17~2025-12-07 代码明确证明)
- **来源**: `LightOpAuthorityZone.java`, `LightOpAuthorityZoneServiceImpl.java`, `LightOpContractRecord.java`
- `light_op_authority_zone`: 运维商授权区域表。字段: regionId(区域ID), memberId(运维商成员ID), status(状态: ENABLE=启用), isInvestment(是否投资), opContractId(运维合同ID), isRepair(是否修复)
- `light_op_authority_zone_remove`: 运维商移除区域记录表
- `light_op_contract_record`: 运维合同记录表。字段: opId(运维商ID), contractName(合同名), type(OP_AUTHORITY=区域授权), status(WAIT_SIGN=待签署), signYear(签署年份), isDel
- 核心方法 `autoTransferStationOp`: 电站完工后自动划转运维商。逻辑: 查询电站regionId下已中标的运维区域(状态ENABLE且非投资) → 取最新区域 → 更新电站opMemberId → 更新运维承接时间。调用方: CompleteConfirmServiceImpl(完工确认审核通过), LightStationEpcServiceImpl(EPC模式), HrflcEpcStationMode(华润模式), OffLineStationFlowServiceImpl(线下电站流程)
- 合同生成: 每5个区域生成一份"服务区域授权补充协议"，状态WAIT_SIGN

### 第三方社会化电站逆变器数据 (rrsjk-light-service, TAEI-2700, 2025-11-18 代码明确证明)
- **来源**: `CompleteConfirmServiceImpl.java`, `LightStationConfirmImg.java`
- 涉及实体: LightStationConfirmImg(电站确认图片), LightStationAudit(电站审核)
- 业务流程: 第三方社会化电站的逆变器数据对接，通过确认图片服务(CompleteConfirmService)处理

### HDS电费报表 (rrsjk-light-report-service, TAEI-2694, 2025-11-17 代码明确证明)
- **来源**: 提交 92d35f09, 4abc050b, b72f8c3b
- 涉及功能: 分中心/项目公司/资方维度的电费报表、电费暂估优化、APP报表
- 关键变更: 浦银发电统计SQL优化、电费暂估逻辑优化

### 银联接口 (rrsjk-light-service, TAEI-2702, 2025-11-18 代码明确证明)
- **来源**: `LightOpAuthorityZone.java`, `TangConstants`, `LightUnionpayBillRecord.java`
- 银联接口增加字段: 在 LightOpAuthorityZone 新增招商标识字段
- 涉及常量: TangConstants(通联支付相关常量)
- 银联相关实体: LightUnionpayBill(银联账单), LightUnionpayBillRecord(银联账单记录), LightUnionpayMch(银联商户), LightUnionpayUser(银联用户), LightUnionpayRentRecord(银联租金记录)

### 运维商政策兑现 (rrsjk-light-service, TAEI-2709/2729/2730, 2025-11-17~2025-12-07 代码明确证明)
- **来源**: `LightSpInspire.java`, `LightSpOpsPositiveIac.java`, `SpInspirePolicyIncomeHandlerImpl.java`
- `light_sp_inspire`: 运维商激励政策表
- `light_sp_ops_positive_iac`: 运维商正向政策表
- `light_station_cost_summary`: 电站费用汇总表
- 负向政策兑现功能优化: 涉及政策收入处理器 SpInspirePolicyIncomeHandlerImpl
- 特殊费用模块: OperationMaintenanceServiceImpl 运维商特殊费用

### 合同时效系统 (rrsjk-light-service, TAEI-2722, 2025-11-20 代码明确证明)
- **来源**: 解钦提交
- 合同时效系统修改，涉及合同签署时效相关的业务逻辑

### 越秀对接 (rrsjk-light-service, TAEI-2731, 2025-12-05 代码明确证明)
- **来源**: 解钦提交
- 对接"农户固定收益异常支付信息查询"

### 备件保证金 (rrsjk-light-service, 孙志男, 2025-12-02 代码明确证明)
- **来源**: 提交 8e804d74, 6ddc9d0c
- 备件保证金单新增业务类型字段

---

### 运维会展大屏相关表 (rrsjk-light-operation-service, 孙志男, 2026-05-19)
- **来源**: TAEI-3066 展会-运维大屏
- **operation_screen_model**: 运维会展大屏数据模型 — 综合健康等级、发电量、容量、实时功率、在线/离线/异常统计、资方标识等
- **operation_elec_month_model**: 资方年月发电量统计 — 按资方+年月的发电量数据
- **operation_model_station**: 电站模型站点表 — 新增 `special_flag` 字段（资产所属标识）

### cm_light_project 字段变更 (rrsjk-light-service, 解钦, 2026-05-19)
- **来源**: TAEI-3107 【风电】风电产值法兼容1.0
- **字段重命名**: `confirm_method` → `income_method`（计收方法）
- **枚举**: `IncomeMethodEnum` (FINAL_INSPECTION/OUTPUT_VALUE)
- **业务类型**: 支持 `WIND_POWER`（风电）

### 招投标管理审核表 (rrsjk-light-service, laowang, 2026-05-15~19)
- **来源**: TAEI-3102 【户用光伏】CBS招投标流程
- **tender_managment_audit**: 招投标管理审核 — 项目分类、项目名称、容量、地理信息、多级审核状态（附件/招标文件/价值链材料）、初审/终审标书
