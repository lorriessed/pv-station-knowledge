     1|# PVS 业务域路由表
     2|
     3|用于把用户问题快速路由到知识库、代码入口、表和生产查询模板。
     4|
     5|## 电站生命周期
     6|
     7|- 关键词：电站状态、录单、审核、配方案、下单、施工、完工、并网、启用、终止、回购。
     8|- 知识库：`domains/station-lifecycle.md`、`domains/approval.md`
     9|- 代码索引：`source-map/java-symbols.md` 搜 `LightStationServiceImpl`、`StationHandleStrategy`
    10|- 常见表：`light_station`、`light_station_audit`、`light_station_operate_log`、`light_station_confirm_img`
    11|- 生产验证：按 `station_code` 查电站主表和审核/操作日志。
    12|
    13|## 审核审批
    14|
    15|- 关键词：一审、二审、总部审核、商务审核、技术审核、越秀审核、驳回。
    16|- 知识库：`domains/approval.md`
    17|- 代码入口：`LightStationServiceImpl`、各资方 `StationHandleStrategy`
    18|- 常见表：`light_station_audit`、`light_station`、`light_service_provider`
    19|- 生产验证：查审核记录倒序。
    20|
    21|## 服务商与区域授权
    22|
    23|- 关键词：服务商、授权区域、冻结、运营中、员工、token、分中心。
    24|- 知识库：`domains/approval.md`、`data/tables.md`
    25|- 代码入口：`LightSpStaffServiceImpl`、`LightServiceProvider`
    26|- 常见表：`light_service_provider`、`light_sub_sp_region`、`light_sp_authority_zone`
    27|
    28|## 订单与辅材
    29|
    30|- 关键词：辅材、保证金、额度、兑换、冻结、签收、核销、S3、S8、S11、D13。
    31|- 知识库：`domains/inventory.md`、`domains/settlement.md`
    32|- 代码入口：搜索 `AuxiliaryMaterial`、`Quota`、`Deposit`
    33|- 常见表：`light_sp_order`、`light_sp_order_item`、`light_auxiliary_material_quota_flow`
    34|- 生产验证：按 `sp_code`、`order_no`、`business_no` 查询。
    35|
    36|## SAP 与财务
    37|
    38|- 关键词：SAP、记账、凭证、belnr、A40、A41、A42、A92、能源币、收款。
    39|- 知识库：`domains/settlement.md`
    40|- 代码入口：`SapClient`、`LightSapServiceImpl`、`SapRecordService`
    41|- 常见表：`sap_record`、业务来源表
    42|- 生产验证：按 `source_no`、`belnr` 查询。
    43|
    44|## 租金/结算/电费
    45|
    46|- 关键词：租金、结算、电费账单、对账、发电收益、收款。
    47|- 知识库：`domains/settlement.md`
    48|- 代码入口：`LightRentService`、各资方 settle service
    49|- 常见表：`light_rent`、`light_station_settle_sum`
    50|
    51|## 电费收益（非户用工商业）
    52|
    53|- 关键词：电费收益、电费订单、发票开具、SAP 收入记账、收款确认、发票冲销、发电户号、批次号。
    54|- 知识库：`domains/electric-fee-revenue.md`
    55|- 代码入口：`LightProjectElectricOrderController`、`LightProjectElectricOrderServiceImpl`、`ProjectElectricOrderSapModel`
    56|- 常见表：`light_project_electric_order`、`light_project_electric_order_owner`、`light_project_electric_order_temporarily`、`light_project_electric_invoice_reverse_record`
    57|
    58|## 政策
    59|
    60|- 关键词：政策、公司政策、补贴、项目公司、政策收入。
    61|- 知识库：`domains/policy.md`
    62|- 代码入口：搜索 `Policy`、`CompanyPolicy`
    63|- 常见表：`light_company_policy`、`light_project_company`
    64|
    65|## 逆变器与发电数据
    66|
    67|- 关键词：逆变器、爱士维、能控云、发电数据、采集、MNS、Kafka、性能、国电投、CQ_GDT。
    68|- 知识库：`domains/inverter-data.md`
    69|- 代码入口：`LightInverterCommon`、`ConsumerMessageService`、`HighPerformanceAisweiListenerFixThread`、`InverterController`(rrsjk-hds-web)、`LightInveterDataService`(rrsjk-light-data-service)
    70|- 常见表：`light_inveter_data`、`light_inveter_record`、`light_station`
    71|- MCP：优先 `electric_pv_mysql_prod`
    72|- **已知电站模式**: ZH(户用)、CQ_GDT(重庆国电投) 有专用逆变器查询链路
    73|
    74|## 报表和大屏
    75|
    76|- 关键词：大屏、报表、导出、日报、月报、资产屏。
    77|- 知识库：`domains/*`、`ops/*`
    78|- 代码入口：`rrsjk-light-report-service`、`rrsjk-report-web`、Mapper XML
    79|- 常见表：先查 `data/sql-table-refs.md`
    80|
    81|## 云效需求/MR/流水线
    82|
    83|- 关键词：需求、缺陷、负责人、MR、合并、流水线、日报、周报、人员负载。
    84|- MCP：`yunxiao_devops`
    85|- 知识库：`runbooks/`、周报/日报任务记录
    86|- 回答要求：给出需求编号、负责人、状态、MR 标题或流水线名称。
    87|
## 电站合同 (`domains/station-contract.md`)
- 关键词：合同、签约、DCC、用印、短信、签署、快捷签。
- 核心表：`light_station_contract_record`、`light_station_contract_record_log`、`light_elec_contract`
- 常见枚举：`ContractTypeEnum` (MASTER/INSTALL/FINANCE/STOP/OWNERSHIP_PROVE 等)
- 签署方式：ONLINE(线上 DCC 签章)、OFFLINE(线下纸质)
- 短信模板：1133(主合同)、1134(装机)、1135(结算)、1146(权属证明)
- 事件总线：`LightStationDccContractEvent` → `LightStationDccContractListener`

## CBS 管理后台 (`domains/cbs-management.md`)
- 关键词：CBS、分中心、分中心用户、后台管理、定时任务日志、登录认证、菜单管理。
- 知识库：`domains/cbs-management.md`
- 代码入口：`cbs-web` → `SysSubCenterController`(分中心管理), `HomeController`(登录), `JobLogController`(定时任务日志), `MenuController`(菜单)
- 路由前缀：`/sysSubCenter/`(分中心), `/sys/login.do`(登录)
|- 技术栈：Java + Spring MVC + Shiro + Velocity/FreeMarker
- **分中心管理**: `/sysSubCenter/subCenterList`(列表), `/sysSubCenter/subCenterUserList`(人员), `/sysSubCenter/addSubCenterUser`(添加人员)
- **登录**: 验证码(randomCode)已改为非必填 (2026-05-20)

## Admin 认证授权 (`domains/admin-authz.md`)
- 关键词：admin-authz、认证、授权、菜单权限、角色管理、OIDC、BFF、OAuth2。
- 知识库：`domains/admin-authz.md` (✅ 已创建, 2026-05-30 全量通读)
- 代码入口：
  - `rrsjk-admin-auth-server` → OAuth2/OIDC 认证服务器 (port 9000, Spring Boot 3.5.14)
  - `rrsjk-admin-authz-service` → Dubbo 授权服务 (用户/角色/菜单/权限/快照, 7 张 authz 表)
  - `rrsjk-admin-bff` → BFF 层 (port 8081, OAuth2 Client, 资产/结算/仓储等业务 Controller)
  - `rrsjk-admin-web-next` → Vue3 新管理后台前端
- **核心表**: `authz_user`, `authz_role`, `authz_menu`, `authz_permission`, `authz_user_role`, `authz_role_permission`, `authz_user_permission`
- **实例**: pv-mysql-prod (rm-m5ebm056ct14p18zu)

## 工商业(CM) (`domains/cm-business.md`)
- 关键词：工商业、风电、终验法、施工进度审核、收入政策、投决审核、项目立项。
- 知识库：`domains/cm-business.md`
- 代码入口：`rrsjk-admin-web` → `CmConstructionProgressAuditController`(施工进度审核), `CmLightProjectIncomePolicyController`(收入政策), `CmLightProjectSignInfoController`(签约信息), `CmLightUseController`, `CmNodeController`
- 路由前缀：`/cmConstructionProgress/`, `/cmLightProjectIncomePolicy/`
- 核心实体：`CmConstructionProgressAudit`(施工进度审核), `CmLightProjectIncomePolicy`(收入政策), `CmLightProject`(项目)
- 业务特征：风电与光伏区分、终验法确认收入、并行审核方案、账务信息模块

