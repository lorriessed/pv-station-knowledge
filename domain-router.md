# PVS 业务域路由表

用于把用户问题快速路由到知识库、代码入口、表和生产查询模板。

## 电站生命周期

- 关键词：电站状态、录单、审核、配方案、下单、施工、完工、并网、启用、终止、回购。
- 知识库：`domains/station-lifecycle.md`、`domains/approval.md`
- 代码索引：`source-map/java-symbols.md` 搜 `LightStationServiceImpl`、`StationHandleStrategy`
- 常见表：`light_station`、`light_station_audit`、`light_station_operate_log`、`light_station_confirm_img`
- 生产验证：按 `station_code` 查电站主表和审核/操作日志。

## 审核审批

- 关键词：一审、二审、总部审核、商务审核、技术审核、越秀审核、驳回。
- 知识库：`domains/approval.md`
- 代码入口：`LightStationServiceImpl`、各资方 `StationHandleStrategy`
- 常见表：`light_station_audit`、`light_station`、`light_service_provider`
- 生产验证：查审核记录倒序。

## 服务商与区域授权

- 关键词：服务商、授权区域、冻结、运营中、员工、token、分中心。
- 知识库：`domains/approval.md`、`data/tables.md`
- 代码入口：`LightSpStaffServiceImpl`、`LightServiceProvider`
- 常见表：`light_service_provider`、`light_sub_sp_region`、`light_sp_authority_zone`

## 订单与辅材

- 关键词：辅材、保证金、额度、兑换、冻结、签收、核销、S3、S8、S11、D13。
- 知识库：`domains/inventory.md`、`domains/settlement.md`
- 代码入口：搜索 `AuxiliaryMaterial`、`Quota`、`Deposit`
- 常见表：`light_sp_order`、`light_sp_order_item`、`light_auxiliary_material_quota_flow`
- 生产验证：按 `sp_code`、`order_no`、`business_no` 查询。

## SAP 与财务

- 关键词：SAP、记账、凭证、belnr、A40、A41、A42、A92、能源币、收款。
- 知识库：`domains/settlement.md`
- 代码入口：`SapClient`、`LightSapServiceImpl`、`SapRecordService`
- 常见表：`sap_record`、业务来源表
- 生产验证：按 `source_no`、`belnr` 查询。

## 租金/结算/电费

- 关键词：租金、结算、电费账单、对账、发电收益、收款。
- 知识库：`domains/settlement.md`
- 代码入口：`LightRentService`、各资方 settle service
- 常见表：`light_rent`、`light_station_settle_sum`

## 电费收益（非户用工商业）

- 关键词：电费收益、电费订单、发票开具、SAP 收入记账、收款确认、发票冲销、发电户号、批次号。
- 知识库：`domains/electric-fee-revenue.md`
- 代码入口：`LightProjectElectricOrderController`、`LightProjectElectricOrderServiceImpl`、`ProjectElectricOrderSapModel`
- 常见表：`light_project_electric_order`、`light_project_electric_order_owner`、`light_project_electric_order_temporarily`、`light_project_electric_invoice_reverse_record`

## 政策

- 关键词：政策、公司政策、补贴、项目公司、政策收入。
- 知识库：`domains/policy.md`
- 代码入口：搜索 `Policy`、`CompanyPolicy`
- 常见表：`light_company_policy`、`light_project_company`

## 逆变器与发电数据

- 关键词：逆变器、爱士维、能控云、发电数据、采集、MNS、Kafka、性能、国电投、CQ_GDT。
- 知识库：`domains/inverter-data.md`
- 代码入口：`LightInverterCommon`、`ConsumerMessageService`、`HighPerformanceAisweiListenerFixThread`、`InverterController`(rrsjk-hds-web)、`LightInveterDataService`(rrsjk-light-data-service)
- 常见表：`light_inveter_data`、`light_inveter_record`、`light_station`
- MCP：优先 `electric_pv_mysql_prod`
- **已知电站模式**: ZH(户用)、CQ_GDT(重庆国电投) 有专用逆变器查询链路

## 报表和大屏

- 关键词：大屏、报表、导出、日报、月报、资产屏。
- 知识库：`domains/*`、`ops/*`
- 代码入口：`rrsjk-light-report-service`、`rrsjk-report-web`、Mapper XML
- 常见表：先查 `data/sql-table-refs.md`

## 云效需求/MR/流水线

- 关键词：需求、缺陷、负责人、MR、合并、流水线、日报、周报、人员负载。
- MCP：`yunxiao_devops`
- 知识库：`runbooks/`、周报/日报任务记录
- 回答要求：给出需求编号、负责人、状态、MR 标题或流水线名称。
