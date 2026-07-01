# 表与字段

更新时间: 2026-05-30

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
|- ngb_station_user：纳光宝电站用户权限

### Admin 认证授权表 (rrsjk-admin-authz-service)
**来源**: `rrsjk-admin-authz-service/rrsjk-admin-authz-impl/src/main/resources/mybatis/mapper/AuthzRepositoryMapper.xml` (2026-05-30 全量通读)
**数据库**: rrsjk_admin_authz @ pv-mysql-prod (rm-m5ebm056ct14p18zu)

| 表名 | 用途 |
|---|---|
| authz_user | 用户主表 (userId, loginId, username, company, chainGroup, centerCode...) |
| authz_role | 角色表 (roleId, roleCode, roleName, enabled) |
| authz_menu | 菜单树 (menuId, menuKey, parentKey, title, path, component, menuType, sortNo, legacyUrl) |
| authz_permission | 权限定义 (permissionId, permissionKey, permissionName, permissionType, resourceKey, enabled) |
| authz_user_role | 用户-角色关联 (userId, roleCode) |
| authz_role_permission | 角色-权限关联 (roleCode, clientType, permissionKey) |
| authz_user_permission | 用户-直接权限关联 (userId, clientType, permissionKey) |

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
|- gec_invoice_check：绿证发票校验表
|- sap_record：SAP记账记录
|- sap_item_record：SAP记账子记录
|- light_fap_record：FAP制证记录表 (2026-06-05新增, 关联CBS财务制证平台, 状态: WAIT_SENT/SENT/SUCCESS/FAIL/CANCEL)

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
- sub_center_name / sub_center_name_new：**TAEI-3053「一商做全国」上线后，新分中心数据直接写入 `sub_center_name`，`sub_center_name_new` 废弃（始终为 NULL）**。报表、聚合、关联 `energy_summary_target` 时必须用 `sub_center_name`，用 `sub_center_name_new` 会导致数据全被过滤。（2026-06-07 生产故障验证）

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

### HDS H5 新能源收入日清报表体系 (2026-05-30, 代码明确证明)
- **前端**: `nahui-pv.hds-h5`
- **后端**: `rrsjk-light-report-service`
- **数据源**: Doris (SelectDB) + MySQL (rrsjk_light_report) + SAP 接口

#### 报表1: 全球收入 (subchainGroup, chainGroupIncome)
- **前端路由**: `/global` → `src/views/reports/global.vue`
- **后端 API**: `/hdsapi/report/subchainGroup/findByDayAt` (旧) / `/hdsapi/report/chainGroupIncome/findByDayAt` (新)
- **数据源**: Doris/ads.energy_chain_group_income + energy_chain_group_income_comment
- **含义**: 最宏观的链群维度全球收入报表，可按产业（新能源合计/绿能/储能/智控器）和链群下钻
- **特点**: 含预实评估（预实零差/小差/有差/大差）、环比同比、评价备注
- **可修改**: 支持手动修改月实际收入 → 递归调整父级合计

#### 报表2: 模式流程日清 (modeRiqing)
- **前端路由**: `/modeRiqing` → `src/views/reports/modeRiqing.vue`
- **3个Tab**: 越秀模式日清 / 中核模式日清 / BT模式日清
- **数据源**: 后端实时统计 light_station + SAP 收入接口
- **含义**: 按资方模式分类的日常运营驾驶舱，统计各阶段业务量（获单/安装/并网/投放/过审）
- **中核模式日清**: 按分中心维度，含收入列（来自 SAP `sapToReportService.findZHIncomeByStationList`）
- **BT模式日清**: 按项目公司维度，统计并网/施工完成待并网/已安装/施工中/获单等(MW)
- **越秀模式日清**: 按整体+分中心+服务商三层，含开户/进件/签合同/安装/并网/投放/过审/通过率

#### 报表3: 绿能产业日清报表 (greenEnergyDayReport)
- **前端 API**: `/hdsapi/greenEnergyDayReport/chainGroupIncome/findList`
- **后端**: `GreenEnergyChainGroupIncomeServiceImpl` 
- **数据源**: MySQL (rrsjk_light_report).green_energy_chain_group_income ← 实际从 Doris 的 energy_chain_group_income 转存
- **含义**: ②链群收入中绿能板块的重新映射，命名更简洁，增加了全月完成率维度
- **特点**: 含链群责任人、月同比、年同比

#### 核心报表关系图
```
Doris (ads.energy_chain_group_income) ──┬── ① 全球收入报表 (global.vue)
                                          ├── ② 新能源链群收入报表 (chainGroupIncome)
                                          └──→ MySQL → ③ 绿能产业日清报表 (greenEnergyDayReport)
                                              (转存/重映射)
MySQL (rrsjk_light + rrsjk_light_report) ── ④ 模式流程日清 (modeRiqing)
                                              ├── 越秀模式 (financial leasing)
                                              ├── 中核模式 (CNNC JV, 收入来自SAP)
                                              └── BT模式 (Build-Transfer)
```

#### Doris 表: ads.energy_chain_group_income
- **数据库**: ads (SelectDB/Doris)
- **连接**: selectdb-cn-1wy4d12u002.selectdbfe.rds.aliyuncs.com:9030, user=dev
- **MCP查询**: 通过 doris MCP 或 pymysql 直连
- **服务端**: `rrsjk-light-report-service` → `com.rrsjk.report.dao.ads.EnergyChainGroupIncomeDao`
| 字段 | 类型 | 说明 |
|------|------|------|
| id | bigint | 主键 |
| industry | varchar | 产业（新能源合计/绿能/储能/智控器/列示） |
| chain_group | varchar | 链群名称（小计/1.1-家庭链群/农村户用等） |
| responsible_person | varchar | 责任人 |
| year_target | decimal | 年目标（万） |
| year_progress | decimal | 年进度（小数，如0.2895=28.95%） |
| year_cumulative_target | decimal | 年累计目标（万） |
| year_actual_income | decimal | 年实际收入（万） |
| year_completion_rate | decimal | 年完成率（小数） |
| year_evaluation | varchar | 年评估（预实零差/小差/有差/大差） |
| month_target | decimal | 月目标（万） |
| month_cumulative_target | decimal | 月累计目标（万） |
| month_actual_income | decimal | 月实际收入（万） |
| month_completion_rate | decimal | 月完成率（小数） |
| entire_month_completion_rate | decimal | 全月完成率（小数） |
| month_evaluation | varchar | 月评估 |
| last_month_actual_income | decimal | 上月实际收入（万） |
| month_on_month_comparison | decimal | 环比（小数，-0.4233=下降42.33%） |
| month_on_month_evaluation | varchar | 环比评估（增长/下降/保持） |
| last_year_actual_income | decimal | 上年实际收入（万） |
| year_on_year_comparison | decimal | 同比（小数） |
| day_at | date | 数据日期 |
| sort | int | 排序 |
| created_by | varchar | 创建人 |
| created_at | datetime | 创建时间 |
| updated_by | varchar | 更新人 |
| updated_at | datetime | 更新时间 |

#### MySQL 表: rrsjk_light_report.green_energy_chain_group_income
- **数据库**: rrsjk_light_report (MySQL)
- **服务端**: `rrsjk-light-report-service` → `com.rrsjk.report.dao.local.GreenEnergyChainGroupIncomeDao`
- **数据来源**: 从 Doris energy_chain_group_income 转存（仅绿能板块），由 GreenEnergyChainGroupIncomeServiceImpl.create() 定时生成
| 字段 | 类型 | 说明 |
|------|------|------|
| id | bigint | 主键 |
| chain_group | varchar | 链群（海尔绿能/1.户用/2.零碳&移动场景等） |
| responsible_person | varchar | 责任人 |
| year_target | decimal | 年目标（万） |
| year_actual_income | decimal | 年实际收入（万） |
| month_target | decimal | 月目标（万） |
| month_actual_income | decimal | 月实际收入（万） |
| entire_month_completion_rate | decimal | 全月完成率（百分比，如68.83=68.83%） |
| month_on_month_comparison | decimal | 环比（百分比，如-40.25=-40.25%） |
| year_on_year_comparison | decimal | 同比（百分比） |
| day_at | datetime | 数据日期 |
| sort | int | 排序 |
| created_by | varchar | 创建人 |
| created_at | datetime | 创建时间 |
| updated_by | varchar | 更新人 |
| updated_at | datetime | 更新时间 |

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
- **report_screen_map_model** (2026-05-25 新增): 地图省市电站数量分布 — 为运维会展大屏提供按省市维度的电站数量统计 (Mapper: `ReportScreenMapModel.xml`, Service: `ReportScreenMapModelService`)
- **business_cooperation_intention** (2026-05-25 确认): 商务合作意向记录 — 会展大屏"联系我们"表单提交 (Entity: `BusinessCooperationIntention`, 95行)
- **light_inverter_model** (2026-05-25 确认): 逆变器数据模型表 — 会展大屏逆变器数据柱状图查询 (Mapper: `LightInverterModel.xml`)

### cm_light_project 字段变更 (rrsjk-light-service, 解钦, 2026-05-19)
- **来源**: TAEI-3107 【风电】风电产值法兼容1.0
- **字段重命名**: `confirm_method` → `income_method`（计收方法）
- **枚举**: `IncomeMethodEnum` (FINAL_INSPECTION/OUTPUT_VALUE)
- **业务类型**: 支持 `WIND_POWER`（风电）

### 招投标管理审核表 (rrsjk-light-service, laowang, 2026-05-15~19)
- **来源**: TAEI-3102 【户用光伏】CBS招投标流程
- **tender_managment_audit**: 招投标管理审核 — 项目分类、项目名称、容量、地理信息、多级审核状态（附件/招标文件/价值链材料）、初审/终审标书

### 新增数据表 (2026-05-14~21 云效驱动扫描)

#### DWS数据源相关 (rrsjk-light-data-service, yumiao, 2026-05-20, Epic2)
- **dws_inveter_data** (推断): DWS数据源逆变器数据表 — 映射到 DwsInveterData 实体
  - 字段: inverter_sn, sp_id, station_code, station_name, brand_id, inverter_state, collector_sn, pac, full_hour, power, elec_day/month/year/total, data_time_at, bind_status, usage_status, first_link_at, station_submitter, data_source
  - 数据源: `spring.dws.datasource` (Doris/DWS库)
  - Mapper: `mybatis/mapper/dws/DwsInveterData.xml`

#### 广发并网进件相关 (rrsjk-light-service, majinhu, 2026-05-19~20, TAEI-3073)
- **gf_merge_grid_input_piece**: 广发并网进件 — station_code, input_piece_id, voltage_level, merge_type, feecollect_type, elec_account_num, ele_factory_num
- **gf_business_opportunity**: 广发商机注册
- **gf_first_input_piece**: 广发首次进件
- **gf_complete_input_piece**: 广发过程进件（施工验收）
- **gf_light_station**: 广发电站
- **gf_light_station_confirm_img**: 广发电站确认影像

#### AI房产证识别 (rrsjk-light-service, mabin, 2026-05-18~20, TAEI-2728)
- **light_station_house_certificate_ocr**: 房产证OCR识别记录 — station_code, house_certificate_url, ocr_status, ocr_result(JSON), source_station_name, ocr_station_name, source_id_no, ocr_id_no, source_address, ocr_address

#### 发电户号电费模板映射 (rrsjk-light-service, lilong, 2026-05-20)
- **light_station_elec_template_mapping**: 发电户号与电费模板映射 — 建立发电户号(elec_no)与电费模板的关联关系

### 逆变器字段变更 (2026-02-13, sunzn)
- **light_inveter**: 新增 `overvoltage_threshold_stage1` (电网过压一级保护阈值V), `output_limit` (有功功率输出限制)
- **light_inveter_data**: 新增同上两个字段
- **light_inveter_record**: 新增同上两个字段
- 来源: 爱仕维(AISWEI)数据接入 + 能控云数据拉取

### 方案变更次数统计字段 (2026-02-24~25, 解钦, TAEI-2869)
- **light_station_plan_change_extra**: 新增 `complete_before_change_num` (完工前变更次数), `complete_after_change_num` (完工后变更次数)
- 统计逻辑: `COUNT(*) FROM light_station_plan_change WHERE status='CHANGE_FINISH' AND change_node='COMPLETE_BEFORE/COMPLETE_AFTER' AND id < a.id`

### 电站查询扩展条件 (2026-02-09, 解钦)
- **light_station.xml**: 新增 `specialFlagList` (资产所属多值IN查询), `first_three_power_at` 范围查询

### FAP收款记录相关表变更 (TAEI-3021/3022/3092, 2026-05-18~21 代码明确证明)
**来源**: 代继宁 25个提交, 跨4个后端仓库
- **订单表** (rrsjk-trade-service): 新增记账状态字段、发票号设置、订单编号设置
- **FAP记录表**: 凭证补偿机制相关字段、取消FAP记录时的状态处理
- **涉及表**: 订单相关表 (trade-service), FAP凭证记录表 (light-service), 财务相关表 (finance-service)
- **关键变更**: 订单记账状态字段跟踪订单是否已记账, FAP凭证补偿确保接口调用失败时可重试

### 220KV变电站名称字段 (TAEI-2880, 2026-03-04~12)
- **light_station.substation220kvName**: 220KV变电站名称 — 并网节点新增字段
  - 关联DTO: `LightStationConfirmDto.substation220kvName`
  - 校验: 长度校验 (wangxiran, 2026-03-06)
  - **来源**: `rrsjk-light-service` → `LightStation.java`, `AcceptanceConfirmService.java`
  - **证据等级**: 代码明确证明

### 运维收入冲销字段 (TAEI-2871/2876, 2026-03-02~20)
- **operation_maintenance.isReverse**: 是否已冲销 — "0"=已冲销, "1"=未冲销
- **operation_maintenance.reverseBy**: 冲销操作人
- **operation_maintenance.reverseAt**: 冲销时间
  - **来源**: `rrsjk-light-service` → `OperationMaintenance.java`, `OperationMaintenance.xml`
  - **证据等级**: 代码明确证明

### 运维收入SAP记账日志表 (TAEI-2984, 2026-04-08 代码明确证明)
- **operation_maintenance_sap_log**: 运维收入管理记账日志
  - `id`: 主键
  - `allOrderNo`: 合并收款总单号
  - 记账凭证、记账状态、凭证号等字段
  - **来源**: `rrsjk-light-api` → `OperationMaintenanceSapLog.java` (sunzn)
  - **证据等级**: 代码明确证明

### 暂估电价表 (TAEI-2959, 2026-04-08 代码明确证明)
- **light_estimate_city_elec_price**: 暂估电价表（按省市区维度）
  - `id`: 主键
  - `provinceId`: 省份ID
  - `provinceName`: 省份名称
  - `cityId`: 城市ID
  - `cityName`: 城市名称
  - `elecPrice`: 电价 (BigDecimal)
  - **来源**: `rrsjk-light-report-api` → `LightEstimateCityElecPrice.java` (baoxin)
  - **证据等级**: 代码明确证明

### 服务商省份授权表 (2026-05-19~21 代码明确证明)
**来源**: `rrsjk-light-service` dev 分支, `LightSpServiceProvince.java`, `LightSpServiceProvince.xml` (commits: 包鑫 40个提交, branch: 涉及 regionUnlimit 等分支)
- **light_sp_service_province**: 服务商省份授权申请表
  - `id`: 主键
  - `sp_id`: 服务商id
  - `member_id`: 会员id
  - `login_id`: 登录账号
  - `sp_name`: 服务商名称
  - `province_id`: 省id
  - `province_name`: 省名称
  - `city_id`: 意向市id
  - `city_name`: 意向市名称
  - `sub_center_code`: 分中心编码
  - `sub_center_name`: 分中心名称
  - `apply_at`: 申请时间
  - `status`: 状态
  - `approve_status`: 审批状态
  - `activate_at`: 激活时间
  - `reject_at`: 驳回时间
  - `reject_reason`: 驳回原因
  - `description`: 描述
  - **Mapper**: `LightSpServiceProvinceDao` → `LightSpServiceProvince.xml`
- **light_sp_service_province_audit_log**: 服务商省份授权审批日志表
  - 记录审批操作流水
- **业务逻辑**:
  - 服务商可申请指定省/市的授权，关联分中心
  - 支持审批流程（申请→审批→激活/驳回）
  - admin-web 前端批量修复省份授权相关显示问题（40次提交迭代）
  - 关联 `LightSpAuthorityZone` 表（授权区域），新增省份授权后同步更新
- **证据等级**: 代码明确证明

### 租金停付管理相关表 (TAEI-3103, 代码明确证明, 2026-05-25~27)
**来源**: `rrsjk-light-service` dev 分支 (sunzn, branch: origin/szn_rent_stop_20260525)
- **rent_suspend_application**: 租金停付申请表
  - 字段: id, member_id, application_no, station_code, owner_name, station_status
  - 审核: first_auditor_id/name/at/remark, final_auditor_id/name/at/remark
  - 恢复: resume_auditor_id/name/at/remark, deduct_month_count(扣除月数)
  - 撤销: cancel_by, cancel_at
- **rent_suspend_application_record**: 租金停付关联记录表（关联租金计划记录）
- **light_unionpay_rent_record**: 租金记录表（新增 `SUSPEND` 支付状态枚举）

### 审核单图驳回记录表 (TAEI-3057, 代码明确证明, 2026-05-21~27)
**来源**: `rrsjk-light-service` (wangxiran, branch: origin/feature-wxr-audit-20260519)
- **light_audit_image_reject_record**: 审核单图驳回记录表
  - 关联审核记录，存储单张图片驳回明细
  - DAO: `LightAuditImageRejectRecordDao`（含 `findByAuditId` 方法）

### 租金个税报表相关表 (TAEI-3092, 代码明确证明, 2026-05-25~27)
**来源**: `rrsjk-light-service` (代继宁, branch: origin/featrue-20260525-rentTaxReport/TAEI-3092)
- **rent_tax_amount_record**: 租金个税明细记录表
- **rent_tax_amount_summary**: 租金个税汇总表
- **tax_amount_calculate_source_data**: 个税计算源数据表（底表）
- **tax_amount_calculate_source_data_temp**: 个税计算中间表 (2026-06-04 新增)
  - 用途: 分批处理中间存储，减少内存占用
  - 实体: `TaxAmountCalculateSourceDataTemp.java` (64行)
  - DAO: `TaxAmountCalculateSourceDataTempDao`
  - 操作: truncate → INSERT FROM light_share_bill_record → 按公司编码迭代处理
  - 唯一键: `rentDate_stationCode` 组合

### FAP凭证记录表 (TAEI-3021/TAEI-3022, 代码明确证明, 2026-05-18~24)
**来源**: `rrsjk-light-service` (代继宁)
- **light_fap_record**: FAP凭证记录表 (rrsjk_light库)
  - 用途: 记录零碳适家/绿证交易订单收款对接FAP系统的凭证信息
  - 2026-05-18~24变更: 移除补偿状态字段，新增凭证补偿机制、实时查询方法
  - DAO: `LightSpOrderItemDao` (新增通过订单项目编号查询订单项目方法)
  - Service: `LightFapRecordServiceImpl` (补偿机制、取消逻辑、批量处理)

### 工商业收入政策表 (TAEI-3083/TAEI-3085, 代码明确证明, 2026-05-19~21)
**来源**: `rrsjk-light-service` (解钦)
- **cm_light_project_income_policy**: 工商业电站项目收入政策表 (rrsjk_light库)
  - 用途: 管理工商业电站项目的收入政策配置和审核流程
  - 2026-05-19~21变更: 支持并行审核方案、政策编码生成、导入校验
  - 实体: `CmLightProjectIncomePolicy.java`

### 工商业自持电站损益报表相关表 (TAEI-3043, 代码明确证明, 2026-05-11~17)
**来源**: `rrsjk-light-service` (王斌/龙龙)
- **cm_owner_station_report**: 工商业自持电站损益报表主表 (rrsjk_light库)
  - 用途: 存储工商业自持电站的月度损益报表数据
  - 2026-05-11~17变更: 新增第三方日志关联、毛利率除零保护、发电来源字段非必填
- **cm_owner_station_white_list**: 工商业电站白名单表 (rrsjk_light库)
  - 用途: 管理工商业电站项目属性（如充电桩CDZ）、发电户号映射
  - 2026-05-11~17变更: 扩展字段支持报表二期需求
- **cm_owner_station_report_third_log**: 工商业自持电站损益报表第三方日志表 (rrsjk_light库) **【新表】**
  - 用途: 记录从第三方系统（大数据库）查询发电量的日志
  - Mapper: `CmOwnerStationReportThirdLog.xml` (214行新增)
  - 实体: `CmOwnerStationReportThirdLog.java`
- **light_high_elec**: 高压电费表 (rrsjk_light库)
  - 2026-05-11~17变更: 新增 `queryMonth` 参数过滤

### 派单配置表 (TAEI-3078, 代码明确证明, 2026-05-11~17)
**来源**: `rrsjk-light-service` (解钦)
- **light_audit_dispatch_time_config**: 审核派单时间配置表 (rrsjk_light库)
  - 用途: 配置非工作日派单时间段，支持定时任务补跑积压工单
  - 2026-05-11~17变更: `addConfig` 返回 `Long` (configId)，查询增加 `status=1` 过滤
- **light_station_plan_change**: 电站方案变更表 (rrsjk_light库)
  - 2026-05-11~17变更: 新增 `NO_NEED_AUDIT` 状态枚举，支持完工前仅品牌变更自动审核

### 图片验真表 (TAEI-3098, 代码明确证明, 2026-05-11~17)
**来源**: `rrsjk-light-service` (马斌)
- **light_image_verification**: 图片验真记录表 (rrsjk_light库)
  - 2026-05-11~17变更: 新增 `uniqueImageKey` 重复上传检查，入库前查询已存在记录并拦截

### Admin 操作日志表 (代码明确证明, 2026-06-20)
**来源**: `rrsjk-admin-operation-log-service`, 数据库 `rrsjk_admin_operation_log`
- **admin_oper_log**: 后台操作日志 (log_id PK, title, business_type, method, request_method, oper_name, user_id, oper_url, oper_ip, oper_param longtext, json_result longtext, status, error_msg, cost_time, trace_id, oper_time)
- **admin_login_log**: 后台登录日志 (info_id PK, user_id, user_name, status, ipaddr, login_location, browser, os, msg, login_type APP/WEB, trace_id, login_time)
- **admin_log_body_detail**: 日志正文详情 (detail_id PK, parent_type LOGIN/OPERATION, parent_id, request_body longtext, response_body longtext, request/response_body_size, request/response_truncated)

### 发电数据省份路由表 (代码明确证明, 2026-06-23)
**来源**: `rrsjk-light-data-service` → `SnProvinceConfig.java`, `SnProvinceConfigDao.java`
- **sn_province_config**: 逆变器SN-省份编码映射表 (rrsjk_light_data库)
  - `id` Long PK, `inverter_sn` String 逆变器SN码, `province_code` String 省份编码(如440000), `province_name` String 省份名称, `created_at` datetime, `updated_at` datetime
  - 用途: Kafka省份Topic双写时按SN查询省份编码，分组发送到`{provinceCode}-vpp-electric` topic
  - 关联: `KafkaProducerService.sendToProvinceDoubleWriteQueue()` 批量查询

### 光伏自有资产表 (代码明确证明, 2026-07-01)
**来源**: `rrsjk-pvbusiness-job-service` → `LightOwnAsset.xml`, `LightOwnAssetStatus.xml`
- **light_own_asset**: 光伏自有资产主表 (rrsjk_light库 via pvbusiness-job-service)
  - `id` Long PK, `cbs_id` CBS主键(LOA+日期+序号), `contract_number` 合同编号, `contract_name` 合同名称, `lessor_code` 出租方, `lessee_code` 承租方, `asset_type` 资产类型, `cbs_type` CBS类型(STATION), `status` 状态(IMPORTED/TRANSFERRED/WAIT_AUDIT/ERROR), `uuid` 租赁系统主键, `serial_number` 单据号, `belnr` SAP凭证号, `rent_total` 租金合计, `rent` 租金, `tax_flag` 保税标志, `invoice_method` 发票选项, `invoice_type` 发票类型, `payment_type` 付款类型, `lease_type` 付款周期
  - 关联: `light_company_info.company_code` = `lessee_code`
- **light_own_asset_status**: 资产审批状态变更记录 (rrsjk_light库)
  - `id` Long PK, `cbs_id`, `uuid`, `serial_number`, `contract_number`, `status`, `reject_time`, `reject_node`, `rejecter_name`, `rejecter`, `reject_reason`, `approval_node`, `approver_name`, `approver`, `approval_time`, `belnr`, `error_msg`, `created_at`
- **light_asset_application_log**: HSCC接口调用日志 (local库)
  - `id` Long PK, `url` 请求地址, `request` 请求体, `response` 响应体, `created_at`
- **light_company_info**: 项目公司信息 (rrsjk_light库)
  - 含 `company_code`, `cost_center_code`, `cost_center_name`, `profit_center_code`, `bank_account` 等银行/财务信息

### 超期库存管控表 (代码明确证明, 2026-07-01)
**来源**: `rrsjk-pvbusiness-job-service` → `EnergyOverdueInventoryControl*.xml`
- **energy_overdue_inventory_control_summary**: 超期库存汇总 (report库)
- **energy_overdue_inventory_control_center**: 超期库存-分中心维度 (report库)
  - 含组件/逆变器各库龄段(60d/90d/120d/150d/180d/360d/1y/2y/3y+)的 quantity/amount/process
- **energy_overdue_inventory_control_sku**: 超期库存-物料维度 (report库)
- **energy_overdue_inventory_control_data_base**: 超期库存基础数据 (report库)

### GVS库龄分析表 (代码明确证明, 2026-07-01)
**来源**: `rrsjk-pvbusiness-job-service` → `GvsWarehouseAgeAnalysis.xml`
- **gvs_warehouse_age_analysis**: GVS仓库库龄分析 (report库)
  - 含工厂/物料/库存地点/品牌/各库龄段数量金额
- **sap_sp_center_relation**: SAP SP与分中心关联 (report库)
