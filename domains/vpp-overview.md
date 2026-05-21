# VPP 项目概述与架构

最后更新: 2026-05-13

## 1. 项目定位

VPP (Virtual Power Plant，虚拟电厂) 是海尔新能源在光伏业务之外的另一条产品线，主要面向电力交易、需求响应、储能调度等场景。**同时承载绿证(GEC)交易业务和纳光宝APP数据大屏**。

## 2. 技术栈

- **后端 (新版)**: Spring Boot 3.2.2 + JDK 17 + Jakarta EE 10 + Spring Cloud 2023.0.0 (vpp-api-common, vpp-api-gect)
- **后端 (旧版)**: Spring Boot 2.x + JDK 8 + javax + Spring Cloud 2020.0.4/Hoxton (vpp-api-elecbusiness, vpp-api-ems, vpp-api-gateway)
- **数据库**: MySQL 8.0.33 + Druid 连接池 + MyBatis-Plus
- **数据平台**: Python (爬虫 + 数据处理)
- **前端**: Vue/H5 + React Native (移动端) + Flutter
- **注册中心/配置中心**: Nacos (多环境)
- **定时任务**: XXL-JOB
- **缓存**: Redis (Lettuce, RESP2协议, FastJson2序列化)
- **网关**: Spring Cloud Gateway (WebFlux 响应式)
- **国际化**: 6语言支持 (zh_CN, zh_HK, en_US, de_DE, it_IT, uk_UA)

## 3. 核心业务模块

### 3.1 API 后端模块

| 模块 | 仓库 | 职责 | 技术栈 |
|---|---|---|---|
| 通用基础 | vpp-api-common | 实体/DTO/枚举/异常/Redis/日期解析/i18n | SB 3.2.2 + JDK 17 |
| 绿证交易 | vpp-api-gect | 客户/订单/采购/发票/SAP/绿证进度/项目管理 | SB 3.2.2 + JDK 17 |
| 认证授权 | vpp-api-auth | 用户认证、Token 管理 | 待通读 |
| 系统管理 | vpp-api-system | 租户、部门、用户、权限 | 待通读 |
| 电力交易 | vpp-api-elecbusiness | Drcloud数据对接/纳光宝大屏/i18n | SB 2.5.5 + JDK 8 |
| 储能管理 | vpp-api-ems | 代理商管理/终端用户/能控 | SB 2.3.12 + JDK 8 |
| 网关 | vpp-api-gateway | API网关/路由/JWT鉴权/跨域 | SB 2.5.5 + JDK 17 |
| 电力市场 | vpp-api-gpower | 绿电收益管理/电网公司/MDM主数据/SAP记账 | SB 2.5.5 + JDK 8 |
| 知识管理 | vpp-api-km | 知识库目录/文件管理/标签/权限 | SB 2.5.5 + JDK 8 |
| 元数据 | vpp-api-meta | 产品管理/出货日志/Excel导入 | SB 2.5.5 + JDK 8 |
| 系统管理 | vpp-api-system | 用户/部门/角色/菜单/租户/字典/i18n/SSO | SB 3.2.2 + JDK 17 |
| 模板 | vpp-api-template | 发票管理模板 (Invoice 模块) | SB 2.5.5 + JDK 8 |
| 开放API | vpp-openapi | AK/SK管理/权限控制/Drcloud推送 | SB 3.2.2 + JDK 17 |
| 海外光伏 | vpp-pv-oversea | 电站/采购/销售/付款/SAP/云报账 | SB 3.2.2 + JDK 17 |

### 3.2 数据平台

| 模块 | 仓库 | 职责 |
|---|---|---|
| 数据平台 | vpp-data-platform | 动态查询、数据白名单、文件上传、爬虫数据接收、时序数据查询 |
| 爬虫 | vpp-crawler | 四川电力交易中心数据采集、任务调度、MySQL/Doris双写 |

### 3.3 前端/H5

| 模块 | 仓库 | 职责 |
|---|---|---|
| 管理后台 H5 | he-vpp.admin-h5 | VPP 管理后台，含售电交易/发票管理/订单管理/审批模块 |
| 湖南政策 H5 | he-vpp.hnzl-h5 | 湖南政策相关 H5 |
| 泰国大屏 | vpp-thai-dashboard | 泰国市场数据大屏, 华为FusionSolar北向API集成, 定时采集电站/设备数据 |
| 模板 UI | vpp-template-ui | 前端组件模板 (pnpm monorepo, 仅 pnpm-workspace.yaml) |

### 3.4 移动端

| 模块 | 仓库 | 技术 | 职责 |
|---|---|---|---|
| 纳光宝 APP | nahuipv_business_flutter | Flutter | 终端用户光伏运营(电站列表/发电数据/收入) |
| 通用业务组件 | nhpv_common_business | Flutter | 纳光宝等多端复用的通用组件库 |
| 湖南 RN | nahuipv-vpp-hnzl-rn | React Native | ⚠️ 空壳仓库，2025-08 初始化后无业务代码 |
| 绿能管理 Flutter | nahuipv-greenergy-management-flutter | Flutter | ⚠️ 骨架项目，无 Dart 业务代码 |
| 绿能 Flutter | nahuipv_greenergy_flutter | Flutter | 海尔绿能APP (v2.2.2)，含 DJI 无人机 SDK 集成 |
| 湖南智充 Android | nahuipv-hnzc-app-android | 原生 Android | ⚠️ 充电桩APP (非光伏业务) |
| 湖南智充 iOS | nahuipv-hnzc-app-ios | 原生 iOS | ⚠️ 充电桩APP (非光伏业务) |

### 3.5 Cordova H5 桥接应用 (非VPP业务)

| 模块 | 仓库 | 技术 | 职责 |
|---|---|---|---|
| 海尔 H5 桥接 (Android) | esp-mag-haier-android-main | Android+Cordova | 内部运维管理 H5 容器 |
| 海尔 H5 桥接 (iOS) | esp-mag-haier-ios-main | iOS+Cordova | 内部运维管理 H5 容器 |
| H5 Portal | esp-mag-haier-h5-portal | H5 | 空壳交付 |

> ⚠️ **注意**: esp-mag-* 仓库是海尔通用 H5 桥接方案，不属于 VPP 或 PVS 光伏业务。
> 其登录接口指向 `eunomia-server`(统一认证) 和 `allinone-server`(会员体系)，与光伏业务无关。

## 4. 与 PVS 的关系

| 维度 | PVS | VPP |
|---|---|---|
| 业务 | 光伏电站全生命周期 | 虚拟电厂/电力交易 |
| 用户 | 服务商、资方、运维人员 | 电力交易员、调度员 |
| 数据 | 电站、逆变器、政策、结算 | 电力市场、储能、需求响应 |
| 代码仓库 | 72 个 | 24 个 |
| 部署 | 10.2.160.228-236 | 待确认 |

## 5. 关键业务概念

- **租户体系**: 多租户架构 (`AbstractTenantDO`, `TenantDTO`), 不同租户数据隔离
- **绿证交易(GEC)**: 绿证采购/销售全流程, 包含客户管理→订单→采购→发票→SAP记账
- **纳光宝**: 面向终端用户的APP, 展示电站运营数据(发电/储能/负载/收入)
- **Drcloud对接**: 第三方平台数据推送接口, 支持12种事件类型实时接入
- **电力市场**: 现货市场、中长期市场、辅助服务市场
- **储能调度**: 充放电策略、峰谷套利
- **需求响应**: 负荷聚合、削峰填谷

## 6. VPP 定时任务 (XXL-JOB)

**来源**: `vpp-api-elecbusiness/TaskSchedule.java` (代码明确证明)

| JobHandler | 业务 | 说明 |
|---|---|---|
| stationBaseJobHandler | 电站基本信息 | 从外部系统同步电站基础数据 |
| stationRobotJobHandler | 智能调度机器人 | 同步机器人配置 |
| socialContributionJobHandler | 社会贡献 | 环保贡献数据 |
| operationPhotovoltaicJobHandler | 光伏运营 | 发电运营数据 |
| operationEnergyStorageJobHandler | 储能运营 | 储能充放电数据 |
| operationChargingStationJobHandler | 充电桩运营 | 充电桩数据 |
| generationPowerJobHandler | 发电功率 | 发电功率时序数据 |
| generationEnergyJobHandler | 储能充放电功率 | 储能功率时序 |
| generationLoadJobHandler | 负载功率 | 负载功率时序 |
| incomeDayJobHandler | 日收入 | 日级别收入统计 |
| incomeMonthJobHandler | 月收入 | 月级别收入统计 |
| incomeYearJobHandler | 年收入 | 年级别收入统计 |

## 7. VPP 数据库表汇总 (代码明确证明)

### 7.1 电站/设备数据 (vpp-api-elecbusiness)

| 表名 | Mapper | 说明 |
|---|---|---|
| station_info | StationInfoMapper | 站点基础数据表 |
| device_info | DeviceInfoMapper | 设备基础数据表 |
| gen_realtime_data | GenRealtimeDataMapper | 发电设备实时数据表 |
| storage_realtime_data | StorageRealtimeDataMapper | 储能设备实时数据表 |
| load_realtime_data | LoadRealtimeDataMapper | 负荷设备实时数据表 |
| charge_gun_realtime_data | ChargeGunRealtimeDataMapper | 充电桩设备实时数据表 |
| measure_ele_realtime_data | MeasureEleRealtimeDataMapper | 电测量设备实时数据表 |
| measure_we_realtime_data | MeasureWeRealtimeDataMapper | 气象测量设备实时数据表 |
| device_statistic | DeviceStatisticMapper | 设备统计数据表 |
| station_statistic | StationStatisticMapper | 站点统计数据表(含发电/充电/收益/CO2减排) |
| dev_forecast | DevForecastMapper | 设备预测数据表 |
| station_alarm | StationAlarmMapper | 站点告警数据表 |
| ngb_station_base | NgbStationBaseMapper | 纳光宝电站基本信息 |
| ngb_station_robot | NgbStationRobotMapper | 纳光宝智能调度机器人 |
| ngb_station_social_contribution | NgbStationSocialContributionMapper | 纳光宝社会贡献 |
| ngb_operation_photovoltaic | NgbOperationPhotovoltaicMapper | 纳光宝光伏运营 |
| ngb_operation_energy_storage | NgbOperationEnergyStorageMapper | 纳光宝储能运营 |
| ngb_operation_charging_station | NgbOperationChargingStationMapper | 纳光宝充电桩运营 |
| ngb_generation_power | NgbGenerationPowerMapper | 纳光宝发电功率 |
| ngb_generation_energy | NgbGenerationEnergyMapper | 纳光宝储能充放电功率 |
| ngb_generation_load | NgbGenerationLoadMapper | 纳光宝负载功率 |
| ngb_station_income | NgbStationIncomeMapper | 纳光宝收入表 |
| ngb_station_income_day | NgbStationIncomeDayMapper | 纳光宝日收入表 |
| ngb_station_income_month | NgbStationIncomeMonthMapper | 纳光宝月收入表 |
| ngb_station_income_year | NgbStationIncomeYearMapper | 纳光宝年收入表 |
| ngb_station_user | NgbStationUserMapper | 纳光宝电站用户权限 |

### 7.2 绿证交易 (vpp-api-gect)

| 表名 | Mapper | 说明 |
|---|---|---|
| customer | CustomerDao | 客户信息表 |
| customer_invoice_info | CustomerInvoiceInfoDao | 客户发票信息表 |
| intend_customer | IntendCustomerDao | 意向客户表 |
| intend_customer_item | IntendCustomerItemMapper | 意向客户明细表 |
| intend_customer_audit_log | IntendCustomerAuditLogDao | 意向客户审批日志 |
| order_management_info | OrderManagementInfoDao | 订单管理主表 |
| order_management_item | OrderManagementItemDao | 订单明细表 |
| order_management_item_gec | OrderManagementItemGecMapper | 订单明细关联库存 |
| order_contract_audit_log | OrderContractAuditLogDao | 合同审核日志 |
| order_voucher_audit_log | OrderVoucherAuditLogDao | 划证凭证审核日志 |
| payback_management_info | PaybackManagementInfoDao | 回款管理表 |
| payback_confirm_audit_log | PaybackConfirmAuditLogDao | 回款凭证审核日志 |
| gec_purchase_order | GecPurchaseOrderDao | 绿证采购单 |
| gec_purchase_order_item | GecPurchaseOrderItemDao | 采购明细 |
| gec_purchase_order_item_receipt_voucher | GecPurchaseOrderItemReceiptVoucherMapper | 采购收货凭证 |
| gec_purchase_contract | GecPurchaseContractDao | 采购合同 |
| gec_purchase_apply_settle | GecPurchaseApplySettleMapper | 采购请款结算 |
| gec_purchase_audit_log | GecPurchaseAuditLogMapper | 采购审核日志 |
| project | ProjectDao | 主项目表 |
| sub_project | SubProjectDao | 子项目表 |
| sales_entity_company | SalesEntityCompanyDao | 主体公司表(项目公司+1PG0) |
| project_company_trade_type | ProjectCompanyTradeTypeMapper | 项目公司交易类型 |
| light_station_green_certificate_progress | LightStationGreenCertificateProgressDao | 电站绿证进度 |
| import_task | ImportTaskMapper | 导入任务日志 |
| invoice | InvoiceDao | 发票表 |
| invoice_item | InvoiceItemMapper | 发票详情表 |
| invoice_attachment | InvoiceAttachmentDao | 发票附件表 |
| gec_invoice_check | GecInvoiceCheckDao | 绿证发票校验表 |
| sap_record | SapRecordDao | SAP记账记录 |
| sap_item_record | SapItemRecordMapper | SAP记账子记录 |

### 7.3 系统基础 (vpp-api-common/vpp-api-base)

| 隐含表名 | 对应DTO | 说明 |
|---|---|---|
| sys_user | UserDTO | 用户表 |
| sys_dept | DeptDTO | 部门表 |
| sys_role | RoleDTO | 角色表 |
| sys_menu | MenuDTO | 菜单权限表 |
| sys_post | PostDTO | 岗位信息表 |
| sys_tenant | TenantDTO | 租户信息表 |
| sys_user_tenant | UserTenantDTO | 用户租户关联 |
| sys_user_role | UserRoleDTO | 用户角色关联 |
| sys_role_menu | RoleMenuDTO | 角色菜单关联 |
| sys_role_dept | RoleDeptDTO | 角色部门关联 |
| sys_user_post | UserPostDTO | 用户岗位关联 |
| sys_dict_data | DictDataDTO | 字典数据表 |
| sys_dict_type | DictTypeDTO | 字典类型表 |
| i18n_message | I18nMessageMapper | 国际化消息表 |
| lan | LanMapper | 语言配置表 |

### 7.4 绿电收益 (vpp-api-gpower, 2026-05-14 代码明确证明)

| 表名 | Mapper | 说明 |
|---|---|---|
| green_electricity_revenue | GreenElectricityRevenueMapper | 绿电收益主表 (状态机: DRAFT→PENDING_FINANCE→APPROVED) |
| green_electricity_audit_log | GreenElectricityAuditLogMapper | 绿电收益审核日志表 |
| power_grid_company | PowerGridCompanyMapper | 电网公司主数据表 |
| power_grid_contract | PowerGridContractMapper | 电网公司合同表 |
| sap_record | SapRecordDao | SAP财务记账记录表 |
| sap_item_record | SapItemRecordDao | SAP财务记账子记录表 (dmbtr收款/dmbtr1手续费/dmbtr2税金) |

### 7.5 知识管理 (vpp-api-km, 2026-05-14 代码明确证明)

| 表名 | Mapper | 说明 |
|---|---|---|
| knowledge_directory | KnowledgeDirectoryMapper | 知识库目录表 (树形结构, parent_id) |
| knowledge_file | KnowledgeFileMapper | 知识库文件表 (标签tag, 审批状态) |
| knowledge_file_mapping | KnowledgeFileMappingMapper | 目录-文件关联表 (多对多) |
| knowledge_file_log | KnowledgeFileLogMapper | 文件操作日志表 |
| knowledge_user | KnowledgeUserMapper | 用户-知识库关联表 (权限控制) |

### 7.6 产品与出货 (vpp-api-meta, 2026-05-14 代码明确证明)

| 表名 | Mapper | 说明 |
|---|---|---|
| t_product | ProductMapper | 产品表 (mdn唯一, dev_type=自研/供应商) |
| t_product_image | ProductMapper | 产品图片表 (一对多) |
| t_shipment_log | ShipmentLogMapper | 出货日志表 (关联product_id, hr_sn, supplier_sn) |

### 7.7 系统基础 (vpp-api-system, 2026-05-14 代码明确证明)

| 表名 | 对应DTO | 说明 |
|---|---|---|
| sys_user | UserDTO | 用户表 |
| sys_dept | DeptDTO | 部门表 (ancestors祖级列表) |
| sys_role | RoleDTO | 角色表 |
| sys_menu | MenuDTO | 菜单权限表 |
| sys_post | PostDTO | 岗位信息表 |
| sys_tenant | TenantDTO | 租户信息表 |
| sys_user_tenant | UserTenantDTO | 用户租户关联 |
| sys_dict_data | DictDataDTO | 字典数据表 |
| sys_dict_type | DictTypeDTO | 字典类型表 |
| sys_config | ConfigDTO | 参数配置表 |
| sys_region | RegionDTO | 区域表 (省市区) |
| sys_portal | SysPortalDTO | 门户表 |
| sys_out_system | SysOutSystemDTO | 外部系统表 |
| sys_i18n_resource | SysI18nResourceDTO | 国际化资源表 |
| sys_i18n_tag_link | SysI18nTagLinkDTO | 国际化资源-标签关联表 |
| sys_language | SysLanguageDTO | 支持的语言表 |
| sys_oss_config | OssConfigDTO | OSS配置表 |

## 8. 知识库更新记录

| 日期 | 更新内容 | 来源 |
|---|---|---|
| 2026-05-14 | 全量通读5个VPP仓库: gpower(绿电收益)/km(知识管理)/meta(产品出货)/system(系统管理)/template | domains/vpp-green-electricity.md, domains/vpp-knowledge-management.md, domains/vpp-product-shipment.md, domains/vpp-system-management.md |
| 2026-05-13 | 重写VPP项目概述: 技术栈/业务模块/定时任务/数据库表 | 全量通读5个VPP仓库 |
| 2026-05-12 | 创建 VPP 项目概述 | 代码仓库扫描 |

## 8. VPP OpenAPI 开放平台 (vpp-openapi, 2026-05-15 代码明确证明)

### 8.1 定位
VPP 系统的对外开放 API 网关，提供 AK/SK 凭证管理和权限控制，用于第三方系统对接 VPP 内部服务。

### 8.2 核心功能
- **AK/SK 凭证管理**: 用户申请 AccessKey/SecretKey 凭证，用于 API 鉴权
- **权限配置**: 为每个 AK 配置允许访问的 API 路径和调用频率限制
- **Drcloud 对接**: 接收第三方 Drcloud 平台的数据推送
- **OpenApi 自动发现**: 从 Nacos 注册中心自动发现各服务的 OpenApi 注解接口

### 8.3 Controller 路由

| 路由 | 方法 | 功能 | 权限 |
|---|---|---|---|
| `/SysAccessKey/apply` | POST | 申请AK/SK凭证 | 登录用户 |
| `/SysAccessKey/remove` | POST | 删除AK/SK凭证 | 管理员 |
| `/SysAccessKey/queryByPage` | GET | 分页查询AK/SK | 管理员 |
| `/SysAccessKey/querySelfAk` | GET | 查询自己的AK/SK | 登录用户 |
| `/SysPermission/apply` | POST | 申请API权限 | 登录用户 |
| `/SysPermission/remove` | POST | 删除权限 | 管理员 |
| `/SysPermission/queryByAk` | GET | 根据AK查询权限列表 | - |
| `/SysPermission/allUrlInfo` | GET | 查询所有可用OpenApi接口 | - |
| `/auth/token` | GET | Drcloud获取Token | 签名鉴权 |
| `/data/push` | POST | Drcloud数据推送 | 签名鉴权 |

### 8.4 数据库表

| 表名 | 说明 |
|---|---|
| `sys_access_key` | AK/SK凭证存储表 (access_key, secret_key_hash, expires_at, status, user_tenant_id) |
| `sys_permission` | AK权限配置表 (ak_id, allowed_api, rate_limit, status) |

### 8.5 关键流程

**AK/SK申请流程**:
1. 用户调用 `/SysAccessKey/apply` 提交申请
2. 系统生成 AccessKey 和 SecretKey 哈希
3. 存入 `sys_access_key` 表，状态为 ENABLE
4. 返回真实 SK 给用户（仅初始化时可见）

**权限申请流程**:
1. 用户调用 `/SysPermission/apply`，传入 AK 和 API 路径
2. 校验 AK 是否存在且有效
3. 创建权限记录到 `sys_permission` 表
4. 支持配置每分钟调用频率限制 (rateLimit)

**Drcloud数据推送**:
- 使用签名鉴权 (`Authorization` header)
- 接收事件类型 (`eventType`) 和数据负载 (`payload`)
- 通过 Feign 转发到 `vpp-api-elecbusiness` 服务处理

### 8.6 技术栈
- Spring Boot 3.2.2 + JDK 17 + Jakarta EE 10
- OkHttp3 作为 HTTP 客户端
- OpenFeign 服务间调用
- mybatis-plus-join (MPJ) 支持复杂查询
- Manifold 编译期运算符重载
- Nacos 服务发现 + 配置中心

## 9. VPP 海外光伏 (vpp-pv-oversea, 2026-05-15 代码明确证明)

### 9.1 定位
海外光伏电站全生命周期管理，覆盖服务商管理、电站信息管理、采购/销售订单、付款计划、发票管理、SAP 集成、云报账集成等完整业务流程。

### 9.2 模块结构
```
vpp-pv-oversea/
├── vpp-pv-oversea-biz/     # 核心业务逻辑
├── vpp-pv-oversea-starter/ # 启动模块
└── vpp-pv-ex-api/          # 外部API (云报账回调/请求日志)
```

### 9.3 Controller 路由汇总

| 路由 | 方法 | 功能 | 业务域 |
|---|---|---|---|
| `/PvStationInfo/add` | POST | 新增电站数据 | 电站管理 |
| `/PvStationInfo/changeByPvStationCode` | POST | 修改电站信息 | 电站管理 |
| `/PvStationInfo/queryByPage` | GET | 分页查询电站 | 电站管理 |
| `/PvStationInfo/queryById` | GET | 查询电站详情 | 电站管理 |
| `/PvStationInfo/export` | GET | 导出电站数据 | 电站管理 |
| `/PvStationInfoHistory/add` | POST | 新增电站历史 | 电站管理 |
| `/PvStationInfoHistory/queryByPage` | GET | 查询电站历史 | 电站管理 |
| `/PvStationMaterial/add` | POST | 新增电站材料 | 电站管理 |
| `/PvStationMaterial/changeMaterialByPvStationCode` | POST | 修改电站材料 | 电站管理 |
| `/PvStationPayPlan/add` | POST | 新增付款计划 | 结算管理 |
| `/PvStationPayPlan/changeByPlanNo` | POST | 修改付款计划 | 结算管理 |
| `/PvStationPayPlan/export` | GET | 导出付款计划 | 结算管理 |
| `/PvStationInvoice/add` | POST | 新增发票数据 | 发票管理 |
| `/PvStationInvoice/changeByPvStationCode` | POST | 修改发票信息 | 发票管理 |
| `/PvStationInvoice/export` | GET | 导出发票列表 | 发票管理 |
| `/PvServiceProvider/add` | POST | 新增服务供应商 | 服务商管理 |
| `/PvServiceProvider/changeBySpId` | POST | 修改服务供应商 | 服务商管理 |
| `/PvServiceProvider/getSpMdmInfo` | POST | 查询服务商MDM信息 | 服务商管理 |
| `/PvServiceProvider/getSpMdmBankInfo` | POST | 查询服务商银行信息 | 服务商管理 |
| `/PurchaseOrder/add` | POST | 新增采购单 | 采购管理 |
| `/PurchaseOrder/changeByPurchaseNo` | POST | 修改采购单 | 采购管理 |
| `/PvPickingOrder/add` | POST | 新增配货单 | 仓储管理 |
| `/PvPickingOrder/changeByPickingNo` | POST | 修改配货单 | 仓储管理 |
| `/PvSaleOrder/add` | POST | 新增销售单 | 销售管理 |
| `/PvSaleOrder/changeBySaleOrderNo` | POST | 修改销售单 | 销售管理 |
| `/pvLog/queryByPage` | GET | 查询系统交互日志 | 运维 |
| `/OverseaYbzSettlementCallback/callback` | POST | 云报账回调接口 | 外部集成 |
| `/SelfInsertData/addPvStation` | POST | 手动新增电站 | 测试/运维 |

### 9.4 数据库表

| 表名 | 说明 | 来源模块 |
|---|---|---|
| `pv_station_info` | 电站数据主表 (pv_code, pv_status, pv_type, pay_status, invoice_status) | vpp-pv-oversea-biz |
| `pv_station_info_history` | 电站历史数据表 | vpp-pv-oversea-biz |
| `pv_station_material` | 电站建站材料明细 | vpp-pv-oversea-biz |
| `pv_station_pay_plan` | 电站付款计划 (plan_no, confirm_status, loan_or_not, pay_type) | vpp-pv-oversea-biz |
| `pv_station_invoice` | 发票信息表 (invoice_no, invoice_status) | vpp-pv-oversea-biz |
| `pv_service_provider` | 服务供应商表 (sp_code, sp_id) | vpp-pv-oversea-biz |
| `pv_service_provider_contract` | 服务商合同关系表 | vpp-pv-oversea-biz |
| `service_provider_deposit` | 服务商押金表 | vpp-pv-oversea-biz |
| `pv_purchase_order` | 采购单 (purchase_no, purchase_type, confirm_status, purchase_document_type) | vpp-pv-oversea-biz |
| `pv_picking_order` | 配货单 (picking_no, picking_status) | vpp-pv-oversea-biz |
| `pv_sale_order` | 销售单 (sale_order_no, sale_status, allocation_method, payment_status) | vpp-pv-oversea-biz |
| `pv_system_interaction_log` | 系统交互日志表 | vpp-pv-oversea-biz |
| `oversea_request_log` | 外部API请求日志 | vpp-pv-ex-api |
| `oversea_ybz_settlement_callback` | 云报账异步回调记录 | vpp-pv-ex-api |

### 9.5 外部系统集成

| 系统 | 配置类 | 用途 |
|---|---|---|
| **SAP** | `SapGvsConfig` | GVS采购订单、财务收款(已废弃→ESAP)、销售订单创建/发货/计费 |
| **云报账(YBZ)** | `YbzConfig` | 报账单创建、状态查询、影像系统同步 |
| **HBC预算中心** | `HbcConfig` | 预算占用、预算执行 |
| **MDM主数据** | `MdmConfig` | 供应商实时查询、银行账号查询 |

### 9.6 业务服务流程枚举 (BusinessServiceFlowEnum)

完整的财务记账流程分类:

| 前缀 | 业务域 | 示例 |
|---|---|---|
| **S01-S16** | 商务人员流程 | 第三方店铺技术服务费收款/智能记账/退款 |
| **A01-A33** | 自营商铺/客售流程 | 自营商铺收款/发货/收入成本/退款/0元单 |
| **W01-W23** | 水站/服务/广告/委约/生态 | 水站收款/技术服务费/预充值/乐农订单/安装服务 |
| **L01-L06/X01-X05** | 系统上行业务 | 第三方订单转代付/银行收款/平台收入 |

### 9.7 枚举值定义

| 枚举类 | 说明 | 值 |
|---|---|---|
| `ConfirmStatusEnum` | 确认状态 | `0`=未确认, `1`=已确认 |
| `DocumentTypeEnum` | 单据类型 | `DIRECT_PURCHASE_SALES_ORDER`=即采即销单, `STATION_CONSTRUCTION_ORDER`=建站单 |
| `AcceptTypeEnum` | 承兑类型 | `AC01`=银承, `AC02`=商承, `AC99`=电子债券凭证 |
| `ExpenseEnum` | 费用类型 | `7010101`=材料款, `7010102`=OEM采购, `7010103`=备件款, `6666041301`=增值交互 |
| `PayChannelEnum` | 支付渠道 | `2`=外部银行 |
| `PayPeriodEnum` | 付款周期 | `xlink_kj01`~`xlink_kj06` (1~6个月) |
| `PayTypeEnum` | 付款方式 | `TTRT`=电汇, `CHEQUE`=支票, `BKDB`=银行扣款 |
| `PayeeScdFlagEnum` | 收款方标志 | `0`=网银, `1`=供票平台 |
| `TicketTypeEnum` | 票据类型 | `H12`=新一代票据, `H21`=供应链票据, `H31`=鑫链 |
| `TransactionTypeEnum` | SAP交易类型(公司代码4110) | `A`=支付宝, `B`=快捷通, `C`=微信PC, `D`=微信健康水站, `E`=微信小顺管家, `F`=微信新账号, `G`=POS支付, `Y`=银联, `W`=财付通, `U`=转账汇款-基本户, `V`=转账汇款-一般户 |

### 9.8 请求日志切面 (RequestLogAspect)

- 使用 `@RequestLog` 注解标记需要记录日志的 Controller 方法
- 异步保存请求日志 (orderNo, requestTime, responseTime, duration, requestBody, responseBody)
- 支持 GET 和 POST 请求参数提取
- 日志表: `pv_system_interaction_log`

## 10. VPP 数据平台深度分析 (vpp-data-platform, 2026-05-15 代码明确证明)

### 10.1 定位
VPP 数据平台是连接爬虫数据与业务系统的中间层，负责接收爬虫推送数据、提供动态查询能力、管理数据白名单，并将数据分发到下游 Kafka。

### 10.2 核心功能模块

| 模块 | 说明 |
|---|---|
| **爬虫数据接收** | 接收爬虫推送数据，经 Kafka 转发到光伏数据流 |
| **动态查询** | 支持指定数据库(test/ods/dwd/dwt/ads/metadata/ai)和表名进行动态分页查询 |
| **白名单校验** | 操作人必须配置白名单才能查询指定库表 |
| **时序数据查询** | 基于 SelectDB 的 ts_kv_cf 表查询设备时序数据 |
| **文件上传** | CSV/TXT 文件上传，自动解析写入 SelectDB ODS 库 |
| **电价查询** | 查询日前电价和实时电价数据 |
| **绿能报表** | 绿能分时发电量日报表查询 |
| **爬虫数据查询** | 发电企业、电力用户基本信息查询(四川电力交易中心) |

### 10.3 Controller 路由

| 路由 | 方法 | 功能 |
|---|---|---|
| `/platform/crawlScMembersGeneration/findByPage` | GET | 发电企业分页查询 |
| `/platform/crawlScMembersGeneration/export` | GET | 发电企业导出 |
| `/platform/crawlScMembersUsersDetail/findByPage` | GET | 电力用户分页查询 |
| `/platform/crawlScMembersUsersDetail/export` | GET | 电力用户导出 |
| `/crawlerData/pushData` | POST | 接收爬虫推送数据 |
| `/platform/electricityPrice/query` | POST | 电价数据查询 |
| `/platform/upload_file/upload_file` | POST | 文件上传(写入ODS) |
| `/platform/dynamic/queryByPage` | POST | 动态分页查询 |
| `/platform/tskv/queryByPageWithTimeRange` | POST | 时序数据分页查询 |
| `/platform/greenEnergyReportStationCityDay/findByPage` | GET | 绿能分时发电量日报表 |

### 10.4 多数据源配置

| 数据源 | Bean 名 | 用途 |
|---|---|---|
| ODS | `odsDataSource` / `odsSqlSessionFactory` | 操作数据层 (MyBatis-Plus) |
| ADS | `adsDataSource` / `adsSqlSessionFactory` | 应用数据层 (MyBatis-Plus) |
| SelectDB | `selectDbDataSource` / `selectDbJdbcTemplate` | SelectDB 分析型数据库 |
| Test | `testDataSource` / `testJdbcTemplate` | 测试数据库 |
| DWD | `dwdDataSource` / `dwdJdbcTemplate` | 数据仓库明细层 |
| DWT | `dwtDataSource` / `dwtJdbcTemplate` | 数据仓库主题层 |
| Metadata | `metadataDataSource` / `metadataJdbcTemplate` | 元数据库 (白名单/审计) |
| AI | `aiDataSource` / `aiJdbcTemplate` | AI 数据 |

### 10.5 Kafka 配置
- 目标 Kafka: Haier Energy 公网 Kafka
- 生产者 Topic: 光伏数据 Topic
- 异步发送，带线程池和重试机制

### 10.6 白名单机制
- 用户白名单表: `dynamic_query_user_whitelist` (username, is_active)
- 规则表: `dynamic_query_user_whitelist_rule` (username, database_name, table_name, is_active, expires_at)
- 支持 `*` 通配符匹配数据库名和表名
- 规则可设置过期时间
- 每次查询前校验操作人是否有权限

### 10.7 审计日志
- 每次动态查询(成功/失败)都记录到 `dynamic_query_audit_log` 表
- 记录内容: 操作人、数据库、表名、查询字段、筛选条件、分页参数、耗时、错误信息

## 11. VPP 爬虫深度分析 (vpp-crawler, 2026-05-15 代码明确证明)

### 11.1 定位
Python 爬虫系统，从四川电力交易中心爬取市场主体数据(电力用户、发电企业、售电公司)和电力市场曲线数据，存储到 MySQL + Doris 双写。

### 11.2 数据库表 (MySQL)

| 表名 | 说明 |
|---|---|
| `crawl_sc_members_users` | 电力用户列表 (members_id, members_name, user_type, voltage, market_date) |
| `crawl_sc_members_users_detail` | 电力用户明细 (统一社会信用代码、经营范围、用电信息) |
| `crawl_sc_members_generation` | 发电企业列表 (generator_types, group_id, group_name) |
| `crawl_sc_members_generation_detail` | 发电企业明细 (机组信息、额定容量、集团信息) |
| `crawl_sc_members_sales` | 售电公司列表 (total_asset, sale_type, zt_jy交易状态) |
| `crawl_sc_members_sales_detail` | 售电公司明细 (资产/人员/股权信息JSON) |
| `crawl_sc_curve_load_forecast` | 负荷预测曲线 (96点数据) |
| `crawl_sc_curve_load_actual` | 负荷实际曲线 |
| `crawl_sc_curve_hydro_forecast` | 水电出力预测曲线 |
| `crawl_sc_curve_hydro_actual` | 水电出力实际曲线 |
| `crawl_sc_curve_power_forecast` | 火电出力预测曲线 |
| `crawl_sc_curve_power_actual` | 火电出力实际曲线 |
| `crawl_sc_curve_renewable_forecast` | 新能源出力预测曲线 |
| `crawl_sc_curve_renewable_actual` | 新能源出力实际曲线 |
| `crawl_sc_curve_nonmarket_forecast` | 非市场机组出力预测曲线 |
| `task_template` | 任务模板表 (template_code, task_type, schedule_rule, depends_on) |
| `task_instance` | 任务实例表 (instance_id, batch_date, status, progress, depends_on) |
| `crawl_sc_token_renewal_log` | Token 续约日志表 |
| `crawl_sc_task_status` | 任务执行状态表 (Doris) |
| `crawl_sc_task_logs` | 任务执行日志表 (Doris) |
| `crawl_sc_login_session` | 登录会话缓存表 (x_ticket, admin_token, 60分钟有效期) |

### 11.3 任务调度系统

**任务模板 (task_template)**:
- 定义任务类型 (download/push) 和分类 (users/generation/curves)
- 调度规则: daily (每日)、monthly_1st (每月1日)、weekly_mon (每周一)
- 支持任务依赖 (depends_on JSON 数组)
- 省份级别隔离 (province_code)

**任务实例 (task_instance)**:
- 由调度器根据模板自动生成
- 状态: PENDING → RUNNING → SUCCESS/FAILED/SKIPPED
- 支持依赖关系 (depends_on 实例ID列表)
- 重试机制 (max_retry_times, retry_count)
- 进度追踪 (progress, total_records, processed_records)

**调度配置** (`config.example.yaml`):
- 任务生成: 每天凌晨 0:05 (Asia/Shanghai)
- 轮询间隔: 30秒
- 最大并发: 3 个任务

### 11.4 技术架构
- **MySQL**: 业务数据、任务状态、登录会话
- **Apache Doris**: 大规模曲线数据存储 (DISTRIBUTED BY HASH)
- **RocketMQ**: 消息队列 (docker-compose 部署)
- **Token 续约**: 自动续约机制，记录到 `crawl_sc_token_renewal_log`

### 11.5 VPP 数据推送流程
```
爬虫抓取 → MySQL/Doris存储 → 推送API → vpp-data-platform → Kafka → 下游消费
```

## 12. VPP 模板服务 (vpp-template, 2026-05-15 代码明确证明)

### 12.1 定位
VPP 项目的代码模板/参考项目，包含一个完整的发票管理模块 (Invoice)，用于新建服务时复制参考。

### 12.2 发票管理 (Invoice)
- **表**: `invoice` (发票号、订单号、发票状态、开票类型、金额、税额等)
- **发票状态**: WAIT(待开票)、SUCCESS(已开票)、INVALID(已作废)、CANCEL(取消开票)
- **发票类型**: 1=专用发票, 2=普通发票
- **开票系统**: TAX_INVOICE_CLOUD(税票云)、GOLDEN_TAX(金税)、BEST_WONDER(百旺金赋)
- **归档状态**: NONE(无需归档)、WAIT(待归档)、ARCHIVE(已归档)
- **路由**: `/Invoice/add`, `/Invoice/remove`, `/Invoice/queryByPage`, `/Invoice/queryById`
- **端口**: 8086, context-path: `/template`
- **Nacos服务名**: `vpp-api-template`

## 13. 知识库更新记录

| 日期 | 更新内容 | 来源 |
|---|---|---|
| 2026-05-15 | 全量通读5个VPP仓库: crawler(爬虫)/data-platform(数据平台)/openapi(开放API)/pv-oversea(海外光伏)/template(模板) | 本节全部内容 |
| 2026-05-14 | 全量通读5个VPP仓库: gpower(绿电收益)/km(知识管理)/meta(产品出货)/system(系统管理)/template | domains/vpp-green-electricity.md 等 |
| 2026-05-13 | 重写VPP项目概述: 技术栈/业务模块/定时任务/数据库表 | 全量通读5个VPP仓库 |
| 2026-05-12 | 创建 VPP 项目概述 | 代码仓库扫描 |
