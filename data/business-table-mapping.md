# PVS 业务 → 数据库表映射

> 自动生成于 2026-05-29，基于 3,402+ 个 MyBatis Mapper XML 扫描
> 核心库: rrsjk_light(805表), rrsjk_finance(196), rrsjk_light_report(171),
> rrsjk_light_operation(124), rrsjk_trade(82), pvs_repairs(98) 等

## 使用说明
- **Mapper引用数** = 该表被多少个 Mapper XML 文件引用，反映业务代码中的活跃程度
- 回答业务问题时，根据下表定位涉及的数据库表和所属库

## 电站生命周期

| 表名 | 库 | 说明 | Mapper引用数 |
|------|-----|------|-------------|
| `light_station` | rrsjk_light |  | 162 |
| `light_station_plan_config` | rrsjk_light |  | 32 |
| `light_station_audit` | rrsjk_light |  | 24 |
| `light_station_white_list` | rrsjk_light |  | 22 |
| `light_station_yuexiu` | rrsjk_light |  | 20 |
| `light_inveter_data` | rrsjk_light |  | 16 |
| `light_station_contract_record` | rrsjk_light |  | 15 |
| `light_station_inverter` | rrsjk_light |  | 14 |
| `light_station_white_list_simple` | rrsjk_light |  | 14 |
| `light_station_epc` | rrsjk_light |  | 12 |
| `light_station_elec_day_report_new` | rrsjk_light |  | 8 |
| `light_station_elec_day_report` | rrsjk_light |  | 6 |
| `light_station_elec` | rrsjk_light |  | 6 |
| `light_inveter` | rrsjk_light |  | 6 |
| `light_station_operate_log` | rrsjk_light |  | 6 |
| `light_station_bank` | rrsjk_light |  | 6 |
| `light_inveter_err` | rrsjk_light |  | 4 |
| `light_station_change_operation` | rrsjk_light |  | 4 |
| `light_station_change_record` | rrsjk_light |  | 4 |
| `light_station_settle` | rrsjk_light |  | 4 |
| `light_station_yuexiu_account` | rrsjk_light |  | 4 |
| `light_station_repurchase` | rrsjk_light |  | 4 |
| `light_station_contract_share_rule` | rrsjk_light |  | 4 |
| `light_station_policy_no` | rrsjk_light |  | 2 |
| `light_inveter_alarm` | rrsjk_light |  | 2 |
| `light_inveter_base` | rrsjk_light |  | 2 |
| `light_inveter_data_record` | rrsjk_light |  | 2 |
| `light_station_policy` | rrsjk_light |  | 2 |
| `light_station_rent_deduct` | rrsjk_light |  | 2 |
| `light_station_person_info_auth` | rrsjk_light |  | 2 |
| `light_station_owner` | rrsjk_light |  | 2 |
| `light_station_repurchase_log` | rrsjk_light |  | 2 |
| `light_station_plan_change` | rrsjk_light |  | 2 |
| `light_station_plan_change_audit_log` | rrsjk_light |  | 2 |
| `light_station_confirm_img` | rrsjk_light |  | 2 |
| `light_station_elec_contract_ocr` | rrsjk_light |  | 2 |
| `light_station_module_angle_ocr` | rrsjk_light |  | 2 |
| `light_station_info_update_audit_log` | rrsjk_light |  | 2 |
| `light_station_baiduai_log` | rrsjk_light |  | 2 |
| `light_station_info_update_log` | rrsjk_light |  | 2 |
| `light_station_inverter_ocr` | rrsjk_light |  | 2 |
| `light_station_master_contract_ocr` | rrsjk_light |  | 2 |
| `light_station_insurance` | rrsjk_light |  | 2 |
| `light_station_yuexiu_exchange` | rrsjk_light |  | 2 |
| `light_station_register_draft` | rrsjk_light |  | 2 |
| `light_station_info_update` | rrsjk_light |  | 2 |
| `light_station_contract_info` | rrsjk_light |  | 2 |
| `light_station_nanny_user` | rrsjk_light |  | 2 |
| `light_station_yuexiu_settle` | rrsjk_light |  | 2 |
| `light_station_nanny` | rrsjk_light |  | 2 |
| `light_station_transfer_order` | rrsjk_light |  | 1 |
| `light_station_other_material_policy` | rrsjk_light |  | 1 |
| `light_station_transfer_order_log` | rrsjk_light |  | 1 |
| `light_station_house_certificate_ocr` | rrsjk_light |  | 1 |
| `light_station_hrflc` | rrsjk_light |  | 1 |

## 审核审批(CBS)

| 表名 | 库 | 说明 | Mapper引用数 |
|------|-----|------|-------------|
| `cmb_leasing_station` | rrsjk_light |  | 32 |
| `boc_leasing_light_station` | rrsjk_light |  | 12 |

## 服务商体系

| 表名 | 库 | 说明 | Mapper引用数 |
|------|-----|------|-------------|
| `light_sub_sp` | rrsjk_light |  | 56 |
| `light_service_provider` | rrsjk_light |  | 30 |
| `light_sp_staff` | rrsjk_light |  | 25 |
| `light_sp_authority_zone` | rrsjk_light |  | 13 |
| `light_sp_store` | rrsjk_light |  | 12 |
| `light_sub_sp_region` | rrsjk_light |  | 7 |
| `light_sp_ops_settle` | rrsjk_light |  | 6 |
| `light_sp_ops_settle_iac` | rrsjk_light |  | 6 |
| `light_sp_ops_settle_dcc` | rrsjk_light |  | 4 |
| `light_sp_order` | rrsjk_light |  | 4 |
| `light_sp_share_quota` | rrsjk_light |  | 4 |
| `light_sp_authority_zone_log` | rrsjk_light |  | 2 |
| `light_sp_order_item` | rrsjk_light |  | 2 |
| `light_sp_ops_positive_excitation` | rrsjk_light |  | 2 |
| `light_sp_share_quota_audit_log` | rrsjk_light |  | 2 |
| `light_sp_zone_street` | rrsjk_light |  | 2 |
| `light_sp_staff_sub_relation` | rrsjk_light |  | 2 |
| `light_sp_contract_record` | rrsjk_light |  | 2 |
| `light_sp_auclon_store` | rrsjk_light |  | 2 |
| `light_sp_staff_region` | rrsjk_light |  | 2 |
| `light_sp_grid_award_order_item` | rrsjk_light |  | 2 |
| `light_sp_op_group_sum` | rrsjk_light |  | 2 |
| `light_sp_op_group_sum_log` | rrsjk_light |  | 2 |
| `light_service_provider_audit_type` | rrsjk_light |  | 1 |

## 运维运营

| 表名 | 库 | 说明 | Mapper引用数 |
|------|-----|------|-------------|
| `light_operation_provider` | rrsjk_light_operation |  | 12 |
| `light_work_order` | rrsjk_light_operation |  | 10 |
| `light_operation_bidding_registration` | rrsjk_light_operation |  | 10 |
| `light_operation_station` | rrsjk_light_operation |  | 10 |
| `light_operation_work_order` | rrsjk_light_operation |  | 8 |
| `light_operation_bidding_project` | rrsjk_light_operation |  | 8 |
| `light_operation_bidding_rating_record` | rrsjk_light_operation |  | 6 |
| `light_operation_exam` | rrsjk_light_operation |  | 6 |
| `light_operation_bidding_company` | rrsjk_light_operation |  | 4 |
| `light_operation_work_order_statistics` | rrsjk_light_operation |  | 4 |
| `light_operation_question_bank` | rrsjk_light_operation |  | 4 |
| `light_operation_external_inverter_inefficiency_psh_results` | rrsjk_light_operation |  | 4 |
| `operation_maintenance_station` | rrsjk_light |  | 4 |
| `operation_maintenance` | rrsjk_light |  | 4 |
| `light_operation_inspection_work_order` | rrsjk_light_operation |  | 3 |
| `light_operation_rating_table` | rrsjk_light_operation |  | 2 |
| `light_operation_bidding_evaluator` | rrsjk_light_operation |  | 2 |
| `light_operation_rating_grade` | rrsjk_light_operation |  | 2 |
| `light_operation_bidding_registration_engineer` | rrsjk_light_operation |  | 2 |
| `light_operation_region_block_release` | rrsjk_light_operation |  | 2 |
| `light_operation_rating_point` | rrsjk_light_operation |  | 2 |
| `light_operation_rating_item` | rrsjk_light_operation |  | 2 |
| `light_operation_region_block` | rrsjk_light_operation |  | 2 |
| `light_operation_region_block_area` | rrsjk_light_operation |  | 2 |
| `light_operation_work_order_fault_info` | rrsjk_light_operation |  | 2 |
| `light_operation_report_config` | rrsjk_light_operation |  | 2 |
| `light_operation_report_data_field` | rrsjk_light_operation |  | 2 |
| `light_operation_inspection_plan` | rrsjk_light_operation |  | 2 |
| `light_operation_exam_answer` | rrsjk_light_operation |  | 2 |
| `light_operation_station_elec_bill` | rrsjk_light_operation |  | 2 |
| `light_operation_station_tag` | rrsjk_light_operation |  | 2 |
| `light_operation_solution_category` | rrsjk_light_operation |  | 2 |
| `light_operation_fault` | rrsjk_light_operation |  | 2 |
| `light_operation_question_category` | rrsjk_light_operation |  | 2 |
| `light_operation_question` | rrsjk_light_operation |  | 2 |
| `light_operation_fault_code` | rrsjk_light_operation |  | 2 |
| `light_operation_external_inverter_inefficiency_diagnosis_results` | rrsjk_light_operation |  | 2 |
| `light_operation_loss_management` | rrsjk_light_operation |  | 2 |
| `light_operation_elec_price` | rrsjk_light_operation |  | 2 |
| `light_operation_station_tag_definition` | rrsjk_light_operation |  | 1 |
| `light_operation_zero_carbon_station_stat` | rrsjk_light_operation |  | 1 |

## 订单/交易

| 表名 | 库 | 说明 | Mapper引用数 |
|------|-----|------|-------------|
| `light_purchase_order` | rrsjk_light |  | 14 |
| `sp_order` | pvs_repairs |  | 11 |
| `cm_light_project` | rrsjk_light |  | 10 |
| `cm_light_project_income` | rrsjk_light |  | 10 |
| `cm_light_project_income_amount` | rrsjk_light |  | 10 |
| `order_item` | rrsjk_trade |  | 9 |
| `cm_construction_plan` | rrsjk_light |  | 9 |
| `cm_contract_manage` | rrsjk_light |  | 8 |
| `cm_construction_plan_item` | rrsjk_light |  | 8 |
| `order_item_fee_third` | rrsjk_trade |  | 8 |
| `sp_order_detail` | pvs_repairs |  | 7 |
| `light_transfer_order` | rrsjk_light |  | 6 |
| `order_item_fee_self` | rrsjk_trade |  | 6 |
| `sp_order_borrow` | pvs_repairs |  | 6 |
| `light_transfer_order_sn` | rrsjk_light |  | 4 |
| `cm_light_project_income_confirm` | rrsjk_light |  | 4 |
| `light_make_order` | rrsjk_light |  | 4 |
| `light_use_order` | rrsjk_light |  | 3 |
| `sp_order_borrow_detail` | pvs_repairs |  | 3 |
| `cm_light_project_sign_info` | rrsjk_light |  | 2 |
| `order_item_un_cash` | rrsjk_trade |  | 2 |
| `light_use_order_age_analysis` | rrsjk_light |  | 2 |
| `order_item_fee` | rrsjk_trade |  | 1 |
| `cm_construction_progress_audit` | rrsjk_light |  | 1 |
| `sp_order_back` | pvs_repairs |  | 1 |
| `sp_order_back_invoice` | pvs_repairs |  | 1 |
| `sp_order_borrow_sn` | pvs_repairs |  | 1 |

## 财务/结算/收益

| 表名 | 库 | 说明 | Mapper引用数 |
|------|-----|------|-------------|
| `light_project_electric_order` | rrsjk_light |  | 10 |
| `settlement_third_order_item_commission` | rrsjk_finance |  | 10 |
| `light_project_electric_order_owner` | rrsjk_light |  | 8 |
| `settlement_third_order_item` | rrsjk_finance |  | 6 |
| `light_share_bill_record` | rrsjk_light |  | 5 |
| `light_project_rent_record` | rrsjk_light |  | 2 |
| `light_project_electric_order_temporarily` | rrsjk_light |  | 2 |
| `settlement_third_order_item_commission_daily_sum` | rrsjk_finance |  | 2 |
| `light_project_rent` | rrsjk_light |  | 2 |
| `settlement_queue` | rrsjk_finance |  | 1 |

## 报表

| 表名 | 库 | 说明 | Mapper引用数 |
|------|-----|------|-------------|
| `green_energy_light_station_elec_day_report_new` |  |  | 8 |
| `green_energy_light_station` |  |  | 6 |
| `green_energy_boc_leasing_light_station` |  |  | 5 |
| `green_energy_cmb_leasing_station` |  |  | 4 |
| `green_energy_light_station_operate_log` |  |  | 4 |
| `green_energy_cnnc_leasing_light_station` |  |  | 4 |
| `green_energy_energy_leased_station_asset_management` |  |  | 4 |
| `green_energy_light_city_elec_price` |  |  | 4 |
| `green_energy_yuexiu_leasing_light_station` |  |  | 4 |
| `green_energy_light_zero_carbon_sku_data` |  |  | 2 |
| `green_energy_light_inveter_data` |  |  | 2 |
| `green_energy_chain_group` |  |  | 2 |
| `green_energy_sign_and_grid_scale_target` |  |  | 2 |
| `green_energy_market_scale_target` |  |  | 2 |
| `green_energy_chain_group_income` |  |  | 2 |
| `green_energy_hrflc_sync_pv_info` |  |  | 2 |
| `green_energy_sap_purchase_record` |  |  | 2 |
| `green_energy_light_sp_grid_award_order` |  |  | 2 |
| `green_energy_light_sub_sp_region` |  |  | 2 |
| `green_energy_light_sp_authority_zone` |  |  | 2 |
| `green_energy_light_sp_inspire` |  |  | 2 |
| `green_energy_light_sub_sp` |  |  | 2 |
| `green_energy_light_zero_carbon_e_station_sku` |  |  | 1 |
| `green_energy_report_light_station_chart_total` |  |  | 1 |
| `green_energy_report_light_inverter_chart_total` |  |  | 1 |
| `green_energy_report_light_inverter_chart_year` |  |  | 1 |
| `green_energy_report_light_station_chart_year` |  |  | 1 |
| `green_energy_report_light_inverter_chart_day` |  |  | 1 |
| `green_energy_report_light_station_chart_month` |  |  | 1 |
| `green_energy_report_light_inverter_pac_chart_day` |  |  | 1 |
| `green_energy_report_light_inverter_chart_month` |  |  | 1 |
| `green_energy_report_light_station_chart_day` |  |  | 1 |
| `green_energy_light_station_realtime_current` |  |  | 1 |
| `green_energy_inverter_current` |  |  | 1 |

## 政策

| 表名 | 库 | 说明 | Mapper引用数 |
|------|-----|------|-------------|
| `light_elec_contract` | rrsjk_light |  | 12 |
| `cmb_electric_price` | rrsjk_light |  | 10 |
| `light_elec_contract_sku_relation` | rrsjk_light |  | 2 |

## 零碳适家

| 表名 | 库 | 说明 | Mapper引用数 |
|------|-----|------|-------------|
| `light_zero_carbon_station` | rrsjk_light |  | 10 |
| `light_zero_carbon_station_audit` | rrsjk_light |  | 6 |
| `light_zero_carbon_station_register_draft` | rrsjk_light |  | 6 |
| `light_zero_carbon_operation_provider` | rrsjk_light |  | 4 |
| `light_zero_carbon_energy_connection_inverter` | rrsjk_light |  | 2 |
| `light_zero_carbon_e_station_audit_log` | rrsjk_light |  | 2 |
| `light_zero_carbon_e_station_sku` | rrsjk_light |  | 2 |
| `light_zero_carbon_component_library` | rrsjk_light |  | 2 |
| `light_zero_carbon_e_station_confirm_img` | rrsjk_light |  | 2 |
| `light_zero_carbon_installation_fee` | rrsjk_light |  | 2 |
| `light_zero_carbon_e_station` | rrsjk_light |  | 2 |

## 商品/配置

| 表名 | 库 | 说明 | Mapper引用数 |
|------|-----|------|-------------|
| `light_sku_data` | rrsjk_light |  | 9 |

## 其他/待分类

| 表名 | 库 | 说明 | Mapper引用数 |
|------|-----|------|-------------|
| `orders` |  |  | 25 |
| `orderproducts` |  |  | 25 |
| `cd_material` |  |  | 22 |
| `cd_warehouse` |  |  | 22 |
| `report_station_chart_month` |  |  | 14 |
| `hrflc_sync_pv_info` |  |  | 14 |
| `energy_leased_station_asset_management` |  |  | 14 |
| `user_message_relations` |  |  | 10 |
| `gf_business_opportunity` |  |  | 10 |
| `city` |  |  | 10 |
| `light_company_info` |  |  | 9 |
| `cd_dict_data` |  |  | 9 |
| `sp_tran_sn` |  |  | 8 |
| `cnnc_leasing_light_station` |  |  | 8 |
| `yuexiu_leasing_light_station` |  |  | 8 |
| `vomproductdata` |  |  | 7 |
| `gvs_warehouse_age_analysis` |  |  | 7 |
| `sp_tran` |  |  | 7 |
| `light_yuexiu_income_bill` |  |  | 6 |
| `light_unionpay_bill_record` |  |  | 6 |
| `light_electric_order` | rrsjk_light |  | 6 |
| `light_staging_records` |  |  | 6 |
| `sap_item_record` |  |  | 6 |
| `light_module_sn` |  |  | 6 |
| `dh_business_opportunity` |  |  | 6 |
| `energy_summary_target` |  |  | 6 |
| `cm_simple_project` | rrsjk_light |  | 6 |
| `zero_carbon_station_relate_file` |  |  | 6 |
| `cm_receipt_milestone` | rrsjk_light |  | 6 |
| `light_unionpay_rent` |  |  | 6 |
| `purchase_apply_settle` |  |  | 6 |
| `sp_tran_sn_detail` |  |  | 6 |
| `zero_carbon_service_provider` |  |  | 5 |
| `energy_overdue_inventory_control_data_base` |  |  | 5 |
| `sap_sp_center_relation` |  |  | 5 |
| `energy_overdue_inventory_control_summary` |  |  | 5 |
| `invoices` |  |  | 5 |
| `rrsv3_store` |  |  | 5 |
| `orderrepairs` |  |  | 5 |
| `sp_express_company` |  |  | 5 |
| `item` |  |  | 4 |
| `station_code` |  |  | 4 |
| `report_inveter_chart_month` |  |  | 4 |
| `report_station_chart_total` |  |  | 4 |
| `name` |  |  | 4 |
| `sub_center_code` |  |  | 4 |
| `approval_message` |  |  | 4 |
| `document_message` |  |  | 4 |
| `urgent_message_scope` |  |  | 4 |
| `chd_light_station` |  |  | 4 |
| `light_stock_taking_detail` |  |  | 4 |
| `light_stock_change` |  |  | 4 |
| `light_component_library` |  |  | 4 |
| `light_company_manage_region` |  |  | 4 |
| `change_station_tmp` |  |  | 4 |
| `light_limit_final_check` |  |  | 4 |
| `light_rent` |  |  | 4 |
| `cm_payment_milestone_audit` | rrsjk_light |  | 4 |
| `light_manual_income` |  |  | 4 |
| `light_unionpay_rent_record` |  |  | 4 |
| `light_yue_xiu_income_bill_exception` |  |  | 4 |
| `light_purchase_pre` | rrsjk_light |  | 4 |
| `light_instant_reward_item` |  |  | 4 |
| `light_stock_taking_variance_analysis` |  |  | 4 |
| `light_stock_taking` |  |  | 4 |
| `light_instant_grid_reward` |  |  | 4 |
| `light_deposit` |  |  | 4 |
| `sub_goal` |  |  | 4 |
| `zero_carbon_sub` |  |  | 4 |
| `hrflc_station_elec_push_now` |  |  | 4 |
| `light_annual_scale_policy` |  |  | 4 |
| `out_business_fee` |  |  | 4 |
| `bill` |  |  | 4 |
| `cash_self_order_item` |  |  | 4 |
| `sap_purchase_record` |  |  | 4 |
| `light_income_record` |  |  | 4 |
| `memberinvoices` |  |  | 4 |
| `vompurchaseorder` |  |  | 4 |
| `regions` |  |  | 4 |
| `sp_nsco_trace` |  |  | 4 |
| `sp_tran_detail` |  |  | 4 |
| `sp_oldback_lists_detail` |  |  | 4 |
| `sp_oldback_lists` |  |  | 4 |
| `light_city_elec_price` |  |  | 4 |
| `obs_order` |  |  | 4 |
| `sp_sub_build_evaluate_dashboard` |  |  | 4 |
| `vom_product_price` |  |  | 3 |
| `warehousestraightproducts` |  |  | 3 |
| `invoice` |  |  | 3 |
| `light_zero_material_manage_serial` | rrsjk_light |  | 3 |
| `light_zero_material_purchase_order` | rrsjk_light |  | 3 |
| `zero_carbon_sub_new` |  |  | 3 |
| `light_zero_material_manage` | rrsjk_light |  | 3 |
| `sp_sub_base_data_dashboard` |  |  | 3 |
| `light_project_management` | rrsjk_light |  | 3 |
| `light_invoice_template` |  |  | 3 |
| `sap_hand_income` |  |  | 3 |
| `sap_record` |  |  | 3 |
| `light_own_asset_status` |  |  | 3 |
| `light_own_asset` |  |  | 3 |
| `invoicesaplogs` |  |  | 3 |
| `membervatinvoice` |  |  | 3 |
| `members` |  |  | 3 |
| `jde_selfaccount` |  |  | 3 |
| `rrsv3_stock` |  |  | 3 |
| `orderworkflows` |  |  | 3 |
| `wo_part` |  |  | 3 |
| `category` |  |  | 2 |
| `socialization_station` |  |  | 2 |
| `light_cs_order` |  |  | 2 |
| `light_repair_order` |  |  | 2 |
| `inverter_error_dict` |  |  | 2 |
| `report_inveter_chart_total` |  |  | 2 |
| `total_evaluators` |  |  | 2 |
| `item_score` |  |  | 2 |
| `report_screen_grid` |  |  | 2 |
| `report_asset_screen_work_order` |  |  | 2 |
| `report_screen_month_elec` |  |  | 2 |
| `report_screen_county` |  |  | 2 |
| `light_wv_rent_record` |  |  | 2 |
| `station_stats` |  |  | 2 |
| `mv_station_power_trend_daily` |  |  | 2 |
| `inverter_inefficiency_diagnosis_results` |  |  | 2 |
| `daily_station_stats` |  |  | 2 |
| `monthly_station_stats` |  |  | 2 |
| `t_product` |  |  | 2 |
| `message_search_history` |  |  | 2 |
| `urgent_message` |  |  | 2 |
| `policy_message` |  |  | 2 |
| `elec` |  |  | 2 |
| `station_name` |  |  | 2 |
| `unbind_operation_log` |  |  | 2 |
| `report_problem_station` |  |  | 2 |
| `report_inveter_chart_year` |  |  | 2 |
| `bank_info` |  |  | 2 |
| `hrflc_bank_info` |  |  | 2 |
| `customer` |  |  | 2 |
| `sub_project` |  |  | 2 |
| `gec_stock` |  |  | 2 |
| `merchant_region` |  |  | 2 |
| `internal_purchase_order` |  |  | 2 |
| `light_purchase_sales_purchase_order` | rrsjk_light |  | 2 |
| `light_purchase_sales_order` | rrsjk_light |  | 2 |
| `hh_register` |  |  | 2 |
| `light_instant_reward` |  |  | 2 |
| `business_audit_snap_shot` |  |  | 2 |
| `py_invoice` |  |  | 2 |
| `light_order_forecast` |  |  | 2 |
| `capital_data_party` |  |  | 2 |
| `yuexiu_interactive_log` |  |  | 2 |
| `light_project_sp_partner` | rrsjk_light |  | 2 |
| `light_project_authority_sp` | rrsjk_light |  | 2 |
| `innodb_trx` |  |  | 2 |
| `innodb_locks` |  |  | 2 |
| `processlist` |  |  | 2 |
| `light_project_funnel_management` | rrsjk_light |  | 2 |
| `light_benefit_conversion` |  |  | 2 |
| `light_commodity` |  |  | 2 |
| `light_new_merchant_policy` |  |  | 2 |
| `light_construction_team` |  |  | 2 |
| `light_auxiliary_make_order` |  |  | 2 |
| `light_company_policy` |  |  | 2 |
| `station_user_ocr_record` |  |  | 2 |
| `light_elec_ocr` | rrsjk_light |  | 2 |
| `station_change_operation` |  |  | 2 |
| `light_unionpay_user` |  |  | 2 |
| `yantu_request_log` |  |  | 2 |
| `light_rent_record` |  |  | 2 |
| `capital_data_management` |  |  | 2 |
| `light_award_appeal_item` |  |  | 2 |
| `light_lend` |  |  | 2 |
| `py_invoice_log` |  |  | 2 |
| `save_file_three` |  |  | 2 |
| `save_file` |  |  | 2 |
| `light_project_owner_account` | rrsjk_light |  | 2 |
| `share_project_payment_account` |  |  | 2 |
| `capital_data_contract` |  |  | 2 |
| `whole_village_together_detail` |  |  | 2 |
| `light_capital_company_info` |  |  | 2 |
| `light_award_appeal` |  |  | 2 |
| `light_epc_sp_info` |  |  | 2 |
| `light_stock_taking_operate_log` |  |  | 2 |
| `light_op_contract_config` |  |  | 2 |
| `light_op_contract_record` |  |  | 2 |
| `light_enable_policy_area` |  |  | 2 |
| `light_enable_policy_sp` |  |  | 2 |
| `light_enable_policy` |  |  | 2 |
| `light_ocr_xls` |  |  | 2 |
| `light_overdue_list_detail_reject_other` |  |  | 2 |
| `light_overdue_list_detail` |  |  | 2 |
| `operation` |  |  | 2 |
| `light_stock` |  |  | 2 |
| `light_store_address` |  |  | 2 |
| `light_image_verify_log` |  |  | 2 |
| `light_image_verification` |  |  | 2 |
| `electric_compete_price_info` |  |  | 2 |
| `insurance_push_data` |  |  | 2 |
| `light_confirm_order` |  |  | 2 |
| `light_company_info_update_log` |  |  | 2 |
| `station_img` |  |  | 2 |
| `light_coin` |  |  | 2 |
| `chui_yang_request_log` |  |  | 2 |
| `cm_invoice_apply` | rrsjk_light |  | 2 |
| `zero_carbon_message` |  |  | 2 |
| `zero_carbon_sp_business_model` |  |  | 2 |
| `zero_carbon_order_policy` |  |  | 2 |
| `zero_carbon_sp_deposit` |  |  | 2 |
| `zero_carbon_order_policy_service_provider` |  |  | 2 |
| `light_zero_merchant_notice` | rrsjk_light |  | 2 |
| `zero_carbon_order_policy_cash` |  |  | 2 |
| `light_zero_merchant_notice_operate_log` | rrsjk_light |  | 2 |
| `zero_carbon_elec_contract` |  |  | 2 |
| `zero_carbon_elec_seal_use` |  |  | 2 |
| `gf_light_station` |  |  | 2 |
| `light_special_outbound_apply_detail` |  |  | 2 |
| `light_special_outbound_apply` |  |  | 2 |
| `dh_second_class_account` |  |  | 2 |
| `cmb_base_region` | rrsjk_light |  | 2 |
| `cmb_channel_log` | rrsjk_light |  | 2 |
| `hrflc_station_elec_push_history` |  |  | 2 |
| `hrflc_relecode_detail_info` |  |  | 2 |
| `hrflc_station_elec_push_record` |  |  | 2 |
| `hrflc_relecode_invoice_info` |  |  | 2 |
| `huarong_id_card_info` |  |  | 2 |
| `hrflc_sync_pv_result_query_new` |  |  | 2 |
| `light_annual_scale_policy_monthly` |  |  | 2 |
| `sp_sku_inventory_age` |  |  | 2 |
| `total_inventory_age` |  |  | 2 |
| `purchase_apply_settle_log` |  |  | 2 |
| `purchase_apply_settle_no_paper` |  |  | 2 |
| `purchase_apply_settle_deposit_refund` |  |  | 2 |
| `haier_recruit_xs_summary` |  |  | 2 |
| `haier_recruit_settle_detail` |  |  | 2 |
| `haier_recruit_pay_detail` |  |  | 2 |
| `zero_carbon_apply_settle` |  |  | 2 |
| `zero_carbon_install_bill` |  |  | 2 |
| `report_income_record` |  |  | 2 |
| `cloud_wisdom_user_wallet` |  |  | 2 |
| `cloud_wisdom_user_wallet_log` |  |  | 2 |
| `cloud_wisdom_wallet_recharge` |  |  | 2 |
| `order_date` |  |  | 2 |
| `mpc_rebate_record` |  |  | 2 |
| `credit_customer_info` |  |  | 2 |
| `mdr_customer_contract_info` |  |  | 2 |
| `mdr_customer_info` |  |  | 2 |
| `mdr_customer_order_details` |  |  | 2 |
| `task` |  |  | 2 |
| `finance_error_log` |  |  | 2 |
| `seller_order_invoice` |  |  | 2 |
| `bill_net_pay` |  |  | 2 |
| `ybz_record` |  |  | 2 |
| `sap_relation` |  |  | 2 |
| `joint_company_order_refund` |  |  | 2 |
| `sap_self_account` |  |  | 2 |
| `invoicechangelogs` |  |  | 2 |
| `packageproducts` |  |  | 2 |
| `couponreceivedbyorderlogs` |  |  | 2 |
| `express_record` |  |  | 2 |
| `storages` |  |  | 2 |
| `producttypes` |  |  | 2 |
| `products` |  |  | 2 |
| `orderandopextattr` |  |  | 2 |
| `reservationshipping` |  |  | 2 |
| `water_article` |  |  | 2 |
| `live_replay` |  |  | 2 |
| `sp_reserve_allocation_order` |  |  | 2 |
| `sp_purchase` |  |  | 2 |
| `sp_tran_sn_detail_sh` |  |  | 2 |
| `cd_branch_info` |  |  | 2 |
| `sp_storeage` |  |  | 2 |
| `cd_pos` |  |  | 2 |
| `sp_purchase_detail` |  |  | 2 |
| `cd_material_substitute` |  |  | 2 |
| `yuexiu_electricity_bill` |  |  | 2 |
| `light_audit_dispatch_log` |  |  | 2 |
| `pu_yin_trade_income_settle` |  |  | 2 |
| `light_zh_settle` |  |  | 2 |
| `light_rent_policy` |  |  | 2 |
| `report_station_chart_year` |  |  | 2 |
| `station_capacity` |  |  | 2 |
| `enabled_inverters` |  |  | 2 |
| `energy_chain_group_income` |  |  | 2 |
| `energy_light_estimate_station` |  |  | 2 |
| `energy_trade_income_info` |  |  | 2 |
| `obs_order_item` |  |  | 2 |
| `center_mapping` |  |  | 2 |
| `energy_statistic_income_report` |  |  | 2 |
| `energy_zhengzhou_sp_leader` |  |  | 2 |
| `sp_sub_operation_evaluate_dashboard` |  |  | 2 |
| `energy_light_estimate_test` |  |  | 2 |
| `light_tech_audit_time_liness_report` |  |  | 2 |
| `energy_inventory_turnover_control_sub_center` |  |  | 2 |
| `energy_grid_income_target` |  |  | 2 |
| `energy_inventory_turnover_control_sku` |  |  | 2 |
| `data_at` |  |  | 2 |
| `energy_center_profit_cost` |  |  | 2 |
| `energy_capital_data` |  |  | 2 |
| `energy_elec_order` |  |  | 2 |
| `energy_household_station_income` |  |  | 2 |
| `light_elect_target_month_report` | rrsjk_light |  | 2 |
| `energy_statistic_income_target` |  |  | 2 |
| `energy_light_estimate_station_test` |  |  | 2 |
| `energy_subchain_group_same_time` |  |  | 2 |
| `light_tech_audit_closed_report` |  |  | 2 |
| `energy_light_estimate` |  |  | 2 |
| `energy_inventory_turnover_control_sp` |  |  | 2 |
| `energy_elec_warning_detail` |  |  | 2 |
| `energy_center_profit` |  |  | 2 |
| `report_puyin_screen_month_elec` |  |  | 2 |
| `energy_capital_data_detail` |  |  | 2 |
| `energy_jinan_sp_leader` |  |  | 2 |
| `energy_center_network_build_target` |  |  | 2 |
| `vm_order_bill` |  |  | 2 |
| `vm_order` |  |  | 2 |
| `product_breakeven_price` |  |  | 1 |
| `product_breakeven_price_change_notice_obs` |  |  | 1 |
| `zero_carbon_item_set_meal_stock_change_log` |  |  | 1 |
| `zero_carbon_item_set_meal_stock` |  |  | 1 |
| `front_category_top_item` |  |  | 1 |
| `front_category` |  |  | 1 |
| `logininfo` |  |  | 1 |
| `breakevenprices` |  |  | 1 |
| `product_order` |  |  | 1 |
| `security_user` |  |  | 1 |
| `organization` |  |  | 1 |
| `energy_elec_price_report_province` |  |  | 1 |
| `light_estimate_city_elec_price` |  |  | 1 |
| `energy_elec_price_report_region` |  |  | 1 |
| `tag_code` |  |  | 1 |
| `t_product_image` |  |  | 1 |
| `t_shipment_log` |  |  | 1 |
| `hot_news` |  |  | 1 |
| `cn_period_division_detail` |  |  | 1 |
| `cn_charge_base_detail` |  |  | 1 |
| `cn_charge_base_hour` |  |  | 1 |
| `cn_period_division_hour` |  |  | 1 |
| `cn_tou_elec_price` |  |  | 1 |
| `base_url_dict` |  |  | 1 |
| `energy_case` |  |  | 1 |
| `cooperation_info` |  |  | 1 |
| `echannel_trade_order` |  |  | 1 |
| `sap_queue` |  |  | 1 |
| `v3_branch_region` |  |  | 1 |
| `email_template` |  |  | 1 |
| `sms_template` |  |  | 1 |
| `area_info` |  |  | 1 |
| `dict_type` |  |  | 1 |
| `bank_area` |  |  | 1 |
| `dict_value` |  |  | 1 |
| `customer_invoice_info` |  |  | 1 |
| `intend_customer` |  |  | 1 |
| `gec_stock_change_record` |  |  | 1 |
| `order_contract_audit_log` |  |  | 1 |
| `order_voucher_audit_log` |  |  | 1 |
| `payback_management_info` |  |  | 1 |
| `payback_confirm_audit_log` |  |  | 1 |
| `shop` |  |  | 1 |
| `your` |  |  | 1 |
| `merchantinfoaudit` |  |  | 1 |
| `expert_customer` |  |  | 1 |
| `professional_customer` |  |  | 1 |
| `corporate_client` |  |  | 1 |
| `merchant` |  |  | 1 |
| `merchant_extras` |  |  | 1 |
| `industry_commerce` |  |  | 1 |
| `member_fitness` |  |  | 1 |
| `member` |  |  | 1 |
| `member_test_meal` |  |  | 1 |
| `member_fitness_sign` |  |  | 1 |
| `light_log_off` |  |  | 1 |
| `member_energy` |  |  | 1 |
| `dev_forecast` |  |  | 1 |
| `i18n_message` |  |  | 1 |
| `lan_id` |  |  | 1 |
| `ngb_station_user` |  |  | 1 |
| `device_info` |  |  | 1 |
| `electricity_price_data_node_hourly_avg` |  |  | 1 |
| `electricity_price_data_spot_hourly_avg` |  |  | 1 |
| `coupon` |  |  | 1 |
| `stock_report` |  |  | 1 |
| `hrois_order_box` |  |  | 1 |
| `hrois_order_item` |  |  | 1 |
| `light_purchase_sales_item_order` | rrsjk_light |  | 1 |
| `address_operation_log` |  |  | 1 |
| `activity` |  |  | 1 |
| `activity_pic` |  |  | 1 |
| `net_pay_log` |  |  | 1 |
| `order_invoice` |  |  | 1 |
| `benefit_consumer` |  |  | 1 |
| `rank_card` |  |  | 1 |
| `member_benefit` |  |  | 1 |
| `benefit_package_detail` |  |  | 1 |
| `benefit` |  |  | 1 |
| `light_stop_station` |  |  | 1 |
| `cm_owner_station_report` | rrsjk_light |  | 1 |
| `hrflc_audit_owner` |  |  | 1 |
| `rent_tax_amount_summary` |  |  | 1 |
| `rent_tax_amount_record` |  |  | 1 |
| `tax_amount_calculate_source_data` |  |  | 1 |
| `tax_amount_calculate_source_data_temp` |  |  | 1 |
| `light_annual_scale_policy_staging` |  |  | 1 |
| `light_annual_scale_policy_monthly_detail` |  |  | 1 |
| `light_annual_scale_policy_staging_detail` |  |  | 1 |
| `light_merchant_deposit_change` |  |  | 1 |
| `budget_occupation_sub_flow_record` |  |  | 1 |
| `ybz_bill_query_result` |  |  | 1 |
| `zero_carbon_deposit_record` |  |  | 1 |
| `budget_occupation_response_record` |  |  | 1 |
| `zero_carbon_apply_settle_no_paper` |  |  | 1 |
| `ybz_bill_main_response_record` |  |  | 1 |
| `zero_carbon_apply_settle_deposit_refund` |  |  | 1 |
| `zero_carbon_apply_settle_log` |  |  | 1 |
| `budget_occupation_request_record` |  |  | 1 |
| `ybz_bill_main_request_record` |  |  | 1 |
| `ybz_bill_request_param_record` |  |  | 1 |
| `king_die_sap_item_record` |  |  | 1 |
| `deposit_record` |  |  | 1 |
| `hp_record` |  |  | 1 |
| `http_interface_info` |  |  | 1 |
| `invoiceapilogs` |  |  | 1 |
| `order2ths` |  |  | 1 |
| `order4invoices` |  |  | 1 |
| `invoiceelectriclogs` |  |  | 1 |
| `sapproofs` |  |  | 1 |
| `posproofs` |  |  | 1 |
| `menu_tree` |  |  | 1 |
| `presale` |  |  | 1 |
| `stock_wly_sku` |  |  | 1 |
| `jde_orderrecord` |  |  | 1 |
| `op2jdesharing` |  |  | 1 |
| `forecast_order` |  |  | 1 |
| `manage_forecast` |  |  | 1 |
| `manage_forecast_detail` |  |  | 1 |
| `forecast_order_detail` |  |  | 1 |
| `jdeoffsettask` |  |  | 1 |
| `company_extras` |  |  | 1 |
| `order_relation` |  |  | 1 |
| `express_register` |  |  | 1 |
| `rrsv3_freezestock` |  |  | 1 |
| `orderoperatelogs` |  |  | 1 |
| `ord_wf_exception_config` |  |  | 1 |
| `ord_wf_order_exception` |  |  | 1 |
| `branch_id` |  |  | 1 |
| `cmt_comment_order_products` |  |  | 1 |
| `storageproducts` |  |  | 1 |
| `hp_regions_info` |  |  | 1 |
| `internal_buy` |  |  | 1 |
| `order_relation_queue` |  |  | 1 |
| `income_forecast` |  |  | 1 |
| `month_amount` |  |  | 1 |
| `income_actual` |  |  | 1 |
| `rrsv3_store_city` |  |  | 1 |
| `lesqueues` |  |  | 1 |
| `hpqueues` |  |  | 1 |
| `installationcost` |  |  | 1 |
| `budget` |  |  | 1 |
| `ms_linkage` |  |  | 1 |
| `stock_frozen_queues` |  |  | 1 |
| `order_queues` |  |  | 1 |
| `target` |  |  | 1 |
| `rrs_income_data_finance` |  |  | 1 |
| `ecological_income_cate_name2019` |  |  | 1 |
| `rrs_income_data_finance2019` |  |  | 1 |
| `orderrepairlesqueues` |  |  | 1 |
| `internal_buy_order` |  |  | 1 |
| `hp_bcc_pay` |  |  | 1 |
| `ehaierqueues` |  |  | 1 |
| `sap_reverse_record` |  |  | 1 |
| `service_income_record_detail` |  |  | 1 |
| `service_income_record` |  |  | 1 |
| `netpoints` |  |  | 1 |
| `jde_yb_product` |  |  | 1 |
| `rrsv3_stock_record` |  |  | 1 |
| `purchasecost` |  |  | 1 |
| `weekly_product` |  |  | 1 |
| `video` |  |  | 1 |
| `cookbook` |  |  | 1 |
| `cook_day` |  |  | 1 |
| `knowledge_user` |  |  | 1 |
| `sp_reserve_allocation_order_detail` |  |  | 1 |
| `sp_inverter_service_sn` |  |  | 1 |
| `sp_supplier_parts_cost` |  |  | 1 |
| `wf_form` |  |  | 1 |
| `wf_deploy_form` |  |  | 1 |
| `sp_express_routing` |  |  | 1 |
| `sp_foregift` |  |  | 1 |
| `sp_warehouse_attach` |  |  | 1 |
| `cd_material_warrant` |  |  | 1 |
| `cd_warehouse_route` |  |  | 1 |
| `light_tech_auditor_operation_log` |  |  | 1 |
| `charging_station_t_order_settle_info` |  |  | 1 |
| `charging_station_t_order_charging_history` |  |  | 1 |
| `haier_energy_t_self_report_metric` |  |  | 1 |
| `pricerules` |  |  | 1 |
| `lesfiveyards` |  |  | 1 |
