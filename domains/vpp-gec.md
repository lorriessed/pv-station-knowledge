# VPP 绿证交易业务 (GEC - Green Energy Certificate)

最后更新: 2026-05-13

**来源**: `vpp-api-gect` 全量通读 (2026-05-13)

## 1. 仓库概览

- **仓库**: `vpp-api-gect`
- **业务文件数**: 341
- **版本**: Spring Boot 3.2.2 + JDK 17 + MyBatis-Plus 3.5.5 + Spring Cloud 2023.0.0
- **依赖**: vpp-api-base (2.0.5-vpp), vpp-api-bus, vpp-api-tenant, vpp-api-permission, vpp-api-elegant-controller
- **特殊依赖**: jaxws-rt (旧版SAP兼容), XStream 1.4.11.1 (XML处理)
- **代码明确证明**: `vpp-api-gect/pom.xml`

## 2. 核心业务模块

### 2.1 客户管理 (customer)

**来源**: `vpp-api-gect-biz/src/main/java/com/nahui/energy/controller/customer/`

| 控制器 | 基础路径 | 职责 |
|---|---|---|
| CustomerController | `/customer` | 最终客户/中介客户CRUD, 按类型查询, 导出 |
| CustomerInvoiceController | `/customerInvoice` | 客户发票信息查询, MDM发票信息获取 |
| IntendCustomerController | `/intendCustomer` | 意向客户管理(提交审核/审批通过/审批驳回/变更/撤回) |

**关键业务逻辑**:
- 客户分为 **最终客户**(endCustomer) 和 **中介客户**(intermediaryClients) 两种类型
- 意向客户有完整的审批流程: 暂存 → 提交审核 → 审批通过/驳回 → 变更 → 撤回
- 意向客户关联订单项 (`IntendCustomerItemDTO`)
- 审批按钮展示由 `ApproveService` 控制, 基于角色 (`ApproveRolesEnum`)
- 客户发票信息可对接MDM主数据系统获取

**涉及表** (代码明确证明):
- `customer` - 客户信息表
- `customer_invoice_info` - 客户发票信息表
- `intend_customer` - 意向客户表
- `intend_customer_item` - 意向客户明细表
- `intend_customer_audit_log` - 意向客户审批日志表

### 2.2 订单管理 (order)

**来源**: `vpp-api-gect-biz/src/main/java/com/nahui/energy/controller/order/`

| 控制器 | 基础路径 | 职责 |
|---|---|---|
| OrderManagementInfoController | `/order` | 销售订单全流程管理(合同/发票/绿证选择/划证凭证缓存+审核) |
| OrderContractLogController | `/order/contractLog` | 合同审核日志查询 |
| OrderVoucherLogController | `/order/voucherLog` | 划证凭证审核日志查询 |
| OrderManagementItemGecController | `/OrderManagementItemGec` | 订单明细关联库存表CRUD |

**订单完整生命周期**:
1. **订单注册** → `cacheOrderInfo` (缓存整个订单信息)
2. **合同签署** → `cacheContract` / `getContractCache` / `contractAudit` (合同审核)
3. **发票信息** → `cacheInvoice` / `getInvoiceCache`
4. **绿证选择** → `cacheGecSelection` / `getGecSelectionCache`
5. **划证凭证** → `cacheVoucher` / `getVoucherCache` / `payVoucherAudit`
6. **回款管理** → `uploadPayVoucher` / `payVoucherAudit` / `manualCreateInvoice` / `invoiceOffLine`

**关键业务逻辑**:
- 订单阶段 (`orderStage`) 和审核节点 (`contractNode`, `voucherNode`) 通过 `ApproveRolesEnum` 枚举管理
- 采用**缓存先行**模式: 前端分步填写, 先缓存到Redis, 最后统一提交
- 订单查询时自动计算: 总价(sumPrice)、总数量(sumNum)、平均价格(avgPrice)
- 合同和划证凭证各有独立的审核日志表

**涉及表** (代码明确证明):
- `order_management_info` - 订单管理主表
- `order_management_item` - 订单明细表
- `order_management_item_gec` - 订单明细关联库存表
- `order_contract_audit_log` - 合同审核日志
- `order_voucher_audit_log` - 划证凭证审核日志

### 2.3 回款/资金管理 (fund)

**来源**: `vpp-api-gect-biz/src/main/java/com/nahui/energy/controller/fund/`

| 控制器 | 基础路径 | 职责 |
|---|---|---|
| PaybackManageController | `/fund` | 回款管理(上传打款凭证/审核/手动开票/线下开票/导出) |
| PaybackConfirmAuditLogController | `/fund/confirmLog` | 回款凭证审核日志 |

**关键业务逻辑**:
- 打款凭证缓存机制: `setPayVoucherCache` / `getPayVoucherCache`
- 审核节点可上传交易类型: `paybackManagementAuditStatusForUploadTradeType`
- 支持手动开票 (`manualCreateInvoice`) 和线下开票 (`invoiceOffLine`)

**涉及表** (代码明确证明):
- `payback_management_info` - 回款管理表
- `payback_confirm_audit_log` - 回款确认审核日志

### 2.4 采购管理 (purchase)

**来源**: `vpp-api-gect-biz/src/main/java/com/nahui/energy/controller/purchase/`

| 控制器 | 基础路径 | 职责 |
|---|---|---|
| GecPurchaseOrderController | `/purchase` | 绿证采购单(查询/作废/采购审核/合同审核/发票/结算审核/收货凭证) |
| GecPurchaseOrderItemController | `/purchase/item` | 采购明细 |
| GecPurchaseOrderItemReceiptVoucherController | `/GecPurchaseOrderItemReceiptVoucher` | 采购明细收货凭证 |
| GecPurchaseContractController | `/purchase/contract` | 采购合同(暂存/提交) |
| GecPurchaseApplySettleController | `/purchaseApplySettle` | 采购请款结算(暂存/提交) |
| GecPurchaseAuditLogController | `/GecPurchaseAuditLog` | 采购审核日志 |

**采购单审核流程** (代码明确证明: `GecPurchaseOrderController.java`):
1. **申请采购阶段** → `purchaseAudit` (业务负责人/财务/总经理三级审核)
2. **合同签署阶段** → `contractAudit` (业务负责人审核, 权限: `contractAudit:ye_wu_fu_ze_ren:audit`)
3. **发票阶段** → `temporarySaveInvoice` / `saveInvoice`
4. **结算申请阶段** → `applySettleAudit`
5. **收货凭证阶段** → `submitReceiptVoucher` / `auditReceiptVoucher`

**涉及表** (代码明确证明):
- `gec_purchase_order` - 绿证采购单主表
- `gec_purchase_order_item` - 采购明细表
- `gec_purchase_order_item_receipt_voucher` - 采购明细收货凭证表
- `gec_purchase_contract` - 绿证采购合同表
- `gec_purchase_apply_settle` - 绿证采购请款结算表
- `gec_purchase_audit_log` - 采购审核日志表

### 2.5 项目管理 (project)

**来源**: `vpp-api-gect-biz/src/main/java/com/nahui/energy/controller/project/`

| 控制器 | 基础路径 | 职责 |
|---|---|---|
| ProjectController | `/Project` | 主项目管理(增删改查/导入/导出) |
| SubProjectController | `/subProject` | 子项目管理(增删改查/导入/导出/删除前检查库存) |
| SalesEntityCompanyController | `/SalesEntityCompany` | 主体公司信息管理(项目公司+海尔光伏1PG0)/MDM客户查询 |
| ProjectCompanyTradeTypeController | `/ProjectCompanyTradeType` | 项目公司对应交易类型 |

**关键业务逻辑**:
- 主体公司 = 项目公司 + 海尔光伏(编码1PG0) — 代码注释明确说明
- 子项目删除前需检查是否存在绿证库存 (`checkExistGecStock`)
- 导入支持失败原因回写: 在原Excel最后一列添加失败原因, 上传OSS后记录导入任务
- SalesEntityCompany 可对接MDM主数据系统查询供应商信息

**涉及表** (代码明确证明):
- `project` - 主项目表
- `sub_project` - 子项目表
- `sales_entity_company` - 主体公司表
- `project_company_trade_type` - 项目公司交易类型表

### 2.6 绿证进度管理 (progressGreen)

**来源**: `vpp-api-gect-biz/src/main/java/com/nahui/energy/controller/progressgreen/`

| 控制器 | 基础路径 | 职责 |
|---|---|---|
| LightStationGreenCertificateProgressController | `/progressGreen` | 绿证进度管理(查询/建档立卡导入/绿证核发导入/导出) |

**关键业务逻辑**:
- 两种导入类型: `建档立卡进度导入` (PBP_IMPORT_TYPE) 和 `绿证核发进度导入` (PGF_IMPORT_TYPE)
- 导入失败处理: 在原Excel最后一列添加失败原因, 重新上传OSS, 记录导入任务日志
- 特殊标志 (`specialFlag`): 资产所属枚举
- 状态 (`status`): 状态枚举
- 备案方式 (`fieldMethod`): 备案方式枚举
- 建档立卡进度 (`progressBuildingPovertyfiles`): "1"=已完成, 其他=未完成
- 绿证核发进度 (`progressGreenCertificate`): "1"=已开始, 其他=未开始

**涉及表** (代码明确证明):
- `light_station_green_certificate_progress` - 电站绿证进度表
- `import_task` - 导入任务日志表

### 2.7 发票管理 (invoice)

**来源**: `vpp-api-gect-biz/src/main/java/com/nahui/energy/controller/invoice/`

| 控制器 | 基础路径 | 职责 |
|---|---|---|
| InvoiceController | `/invoice` | 票税通发票查询/发送/结果查询 |
| InvoiceItemController | `/InvoiceItem` | 发票详情CRUD |
| InvoiceAttachmentController | `/InvoiceAttachment` | 发票附件CRUD |
| GecInvoiceCheckController | `/invoiceCheck` | 绿证发票校验(OCR识别/CBS对接) |

**关键业务逻辑**:
- 发票发送定时任务: `sendInvoiceJob` / `queryInvoiceResultJob`
- 发票校验可调用CBS接口获取: `acquireInvoiceInfoFromCbs`
- 发票校验同步CBS: `addInvoiceCheckToCbs`
- 按申请单号查询发票校验: `queryByPurchaseOrderNo`

**涉及表** (代码明确证明):
- `invoice` - 发票表
- `invoice_item` - 发票详情表
- `invoice_attachment` - 发票附件表
- `gec_invoice_check` - 绿证发票校验表

### 2.8 SAP财务记账 (sap)

**来源**: `vpp-api-gect-biz/src/main/java/com/nahui/energy/controller/sap/`

| 控制器 | 基础路径 | 职责 |
|---|---|---|
| SapController | `/sap` | SAP财务记账(冲销/重新记账) |
| SapItemRecordController | `/sapItemRecord` | SAP记账子记录CRUD |

**关键业务逻辑**:
- 冲销记账: `reserve`
- 重新记账: `reSap` (C10/C12) + `reSapByOrderNo` (C10/C12/C01/C02)
- 记账类型代码: C01, C02, C10, C12
- 使用 JAX-WS SOAP 客户端对接SAP (pom.xml 中有 `jaxws-rt` 依赖)

**涉及表** (代码明确证明):
- `sap_record` - SAP记账记录表
- `sap_item_record` - SAP记账子记录表

### 2.9 导入任务管理

**来源**: `vpp-api-gect-biz/src/main/java/com/nahui/energy/controller/ImportTaskController.java`

| 路径 | 方法 | 说明 |
|---|---|---|
| `/ImportTask/add` | POST | 新增导入任务 |
| `/ImportTask/remove` | POST | 删除导入任务 |
| `/ImportTask/queryByPage` | GET | 分页查询(按创建时间倒序, 数据范围权限) |
| `/ImportTask/queryById` | GET | 根据ID查询 |

## 3. VPP API 技术栈 (代码明确证明)

### 3.1 版本对比

| 仓库 | Spring Boot | JDK | MyBatis-Plus | Spring Cloud |
|---|---|---|---|---|
| vpp-api-common | 3.2.2 | 17 | 3.5.5 | 2023.0.0 |
| vpp-api-gect | 3.2.2 | 17 | 3.5.5 | 2023.0.0 |
| vpp-api-elecbusiness | 2.5.5 | 8 | 3.5.3.1 | 2020.0.4 |
| vpp-api-ems | 2.3.12 | 8 | 3.5.3.1 | Hoxton.SR12 |
| vpp-api-gateway | 2.5.5 | 17→8混用 | 3.5.3.1 | 2020.0.4 |

**关键发现**: VPP 仓库存在**两套技术栈**:
- **新版** (vpp-api-common, vpp-api-gect): Spring Boot 3.2.2 + JDK 17 + Jakarta EE 10
- **旧版** (vpp-api-elecbusiness, vpp-api-ems, vpp-api-gateway): Spring Boot 2.x + JDK 8 + javax

### 3.2 公共组件 (vpp-api-base)

**来源**: `vpp-api-common/vpp-api-base/src/main/java/`

- **实体层**: `BaseDO` (审计字段: createBy, createTime, updateBy, updateTime, delFlag), `BaseIdDO` (UUID主键), `AbstractTenantDO` (租户隔离)
- **DTO层**: `IdDTO`, `AbstractTenantDTO`, `UserDTO`, `RoleDTO`, `DeptDTO`, `MenuDTO`, `PostDTO`, `TenantDTO`
- **枚举**: `DelFlagEnum`(0有效/1删除), `DataScopeEnum`(全部/自定义/本部门/本部门及以下/仅本人), `BooleanTypeEnum`, `UserTypeEnum`(sys_user/tenant_admin/super_admin)
- **异常处理**: `GlobalExceptionHandler` — 支持 i18n 国际化异常翻译, MyBatis系统异常特殊处理
- **日期解析**: `DateTimeParser` — 支持时间戳(10位秒/13位毫秒) + 8种日期格式自动识别
- **Redis**: FastJson2序列化, RESP2协议, 支持手机验证码校验
- **定时任务**: XXL-JOB 集成 (`XxlJobConfig`, `XxlJobLogFilter`)
- **Entity架构**: `AbstractDoEntity<T>` — 领域实体模式, Entity-DO-DTO三层转换

### 3.3 多环境配置

**来源**: `vpp-api-gect/pom.xml` profiles

| 环境 | Nacos地址 | Namespace | 用户名 | SAP URL |
|---|---|---|---|---|
| local/dev | 10.162.105.9:8848 | 266fa059/49256502 | nacos | CBS测试环境 |
| test | 10.162.105.9:8848 | 8bc7450c | nacos | - |
| prod | nlb-sfypp5bxa7wquowavs.cn-qingdao.nlb.aliyuncsslb.com:8848 | 6e1ce568 | vpp | - |
| jk-prod | - | - | - | `http://58.56.128.10:19001/GVS/GVS/...` |

## 4. 定时任务 (XXL-JOB)

### 4.1 vpp-api-elecbusiness 定时任务

**来源**: `vpp-api-elecbusiness-biz/src/main/java/com/nahui/energy/schedule/TaskSchedule.java`

| JobHandler | 执行逻辑 | 说明 |
|---|---|---|
| `stationBaseJobHandler` | 同步电站基本信息 | 从外部系统同步电站基础数据 |
| `stationRobotJobHandler` | 同步智能调度机器人 | 同步机器人配置/状态 |
| `socialContributionJobHandler` | 同步电站社会贡献 | 环保贡献数据同步 |
| `operationPhotovoltaicJobHandler` | 同步光伏运营信息 | 光伏发电运营数据 |
| `operationEnergyStorageJobHandler` | 同步储能运营 | 储能充放电运营数据 |
| `operationChargingStationJobHandler` | 同步充电桩运营 | 充电桩运营数据 |
| `generationPowerJobHandler` | 同步发电功率 | 发电功率时序数据 |
| `generationEnergyJobHandler` | 同步储能充放电功率 | 储能功率时序数据 |
| `generationLoadJobHandler` | 同步负载功率 | 负载功率时序数据 |
| `incomeDayJobHandler` | 同步日收入 | 日级别收入统计 |
| `incomeMonthJobHandler` | 同步月收入 | 月级别收入统计 |
| `incomeYearJobHandler` | 同步年收入 | 年级别收入统计 |

### 4.2 vpp-api-elecbusiness 纳光宝大屏数据

**来源**: `vpp-api-elecbusiness-biz/src/main/java/com/nahui/energy/controller/vpp/NgbController.java`

**基础路径**: `/ngb/appShow` — 纳光宝APP数据大屏展示

| 路径 | 说明 | 返回类型 |
|---|---|---|
| `/queryNgbStationBase` | 电站基本信息分页 | Page<NgbStationBase> |
| `/robot/{stationId}` | 智能调度机器人数据 | NgbStationRobot |
| `/socialContribution/{stationId}` | 社会贡献数据 | NgbStationSocialContribution |
| `/operation/photovoltaic/{stationId}` | 光伏运营信息 | NgbOperationPhotovoltaic |
| `/operation/energyStorage/{stationId}` | 储能运营信息 | NgbOperationEnergyStorage |
| `/operation/chargingstation/{stationId}` | 充电桩运营信息 | NgbOperationChargingStation |
| `/generation/power` | 发电功率(按日) | EchartsData |
| `/generation/energy` | 储能充放电功率(按日) | EchartsData |
| `/generation/load` | 负载功率(按日) | EchartsData |
| `/income/day` | 日收入 | EchartsData |
| `/income/month` | 月收入 | EchartsData |
| `/income/year` | 年收入 | EchartsData |
| `/income/all` | 全生命周期收入 | EchartsData |

## 5. Drcloud 平台数据对接

**来源**: `vpp-api-elecbusiness-biz/src/main/java/com/nahui/energy/controller/vpp/DrcloudController.java`

**基础路径**: `/drcloud/data/push` (POST)

**支持的事件类型** (12种):
1. `STATION_INFO` — 站点基础数据 → `station_info` 表
2. `DEVICE_INFO` — 设备基础数据 → `device_info` 表
3. `GEN` — 发电实时数据 → `gen_realtime_data` 表
4. `STORAGE` — 储能实时数据 → `storage_realtime_data` 表
5. `LOAD` — 负荷实时数据 → `load_realtime_data` 表
6. `CHARGE_GUN` — 充电桩实时数据 → `charge_gun_realtime_data` 表
7. `MEASURE_ELE` — 电测量实时数据 → `measure_ele_realtime_data` 表
8. `MEASURE_WE` — 气象测量实时数据 → `measure_we_realtime_data` 表
9. `DEVICE_STATISTIC` — 设备统计数据 → `device_statistic` 表
10. `STATION_STATISTIC` — 站点统计数据 → `station_statistic` 表
11. `DEV_FORECAST` — 设备预测数据 → `dev_forecast` 表 (批量)
12. `STATION_ALARM` — 站点告警数据 → `station_alarm` 表

## 6. VPP Gateway 网关

**来源**: `vpp-api-gateway/vpp-gateway-biz/src/main/java/`

- **端口**: 8084, Context Path: `/api`
- **技术**: Spring Cloud Gateway + WebFlux (响应式)
- **核心组件**:
  - `CacheRequestFilter` — 解决WebFlux流不可重复读取问题, 缓存GET/DELETE以外的请求body
  - `GatewayExceptionHandler` — 统一异常处理, AuthException返回401, 其他返回500
  - `TokenService` — JWT Token管理, Redis缓存登录用户, 120分钟自动刷新
  - `CorsConfig` — 全路径跨域允许(*)

## 7. VPP EMS 能控系统

**来源**: `vpp-api-ems/vpp-biz/src/main/java/`

- **端口**: 10008 (dev), Context Path: `/nahui-ems`
- **服务名**: `ems-provider`
- **核心功能**:
  - 代理商管理 (`/admin/agent`) — 分页查询、树形结构(按clientId)
  - 代理商登录 (`/auth/agent/verify/login`) — 邮箱密码校验, 更新最后登录时间
  - 终端用户管理 (`/admin/user`) — 分页查询、邮箱模糊搜索
  - 数据范围控制: 非超级管理员(agentType!=100)只能看自己及下属的数据

**代理商类型** (代码推断):
- `100` = 超级管理员 (全部数据权限)
- `201` = 已删除
- `>500` = 已禁用

## 8. 国际化 (i18n) 体系

**来源**: `vpp-api-elecbusiness-biz/src/main/resources/lang/`

支持语言: zh_CN(中文简体), zh_HK(繁体中文), en_US(英文), de_DE(德文), it_IT(意大利文), uk_UA(乌克兰文)

**关键国际化Key**:
- `system.success` — 请求成功
- `user.exist/delete/disabled/not.login` — 用户状态
- `device.exist/no.exist/offline/upgrade.failed` — 设备状态
- `system.global.error/no.authority` — 系统错误/无权限

**设备故障码** (代码明确证明: `language_zh_CN.properties`):
- 阳台3.0告警: PCS硬件故障/过温/交流电压故障/电池电压故障/通讯故障
- 阳台3.0故障: 风扇锁死/系统过温/逆变器过温/控制器过温/交流输出短路等15种
- 阳台2.0故障: 充电MOSFET损坏/散热器温度过高/充电过流等23种
- 英威腾并网故障: PV电压/总线电压/逆变过流/温度异常等100+种故障码

## 9. 知识库更新记录

| 日期 | 更新内容 | 来源 |
|---|---|---|
| 2026-05-13 | 创建VPP绿证交易完整业务文档 | vpp-api-gect全量通读 |
| 2026-05-13 | 新增VPP API技术栈对比 | vpp-api-common + gect + elecbusiness + ems + gateway |
| 2026-05-13 | 新增Drcloud数据对接12种事件类型 | vpp-api-elecbusiness DrcloudController |
| 2026-05-13 | 新增纳光宝大屏数据接口 | vpp-api-elecbusiness NgbController |
| 2026-05-13 | 新增VPP XXL-JOB定时任务列表 | vpp-api-elecbusiness TaskSchedule |
| 2026-05-13 | 新增VPP Gateway网关架构 | vpp-api-gateway |
| 2026-05-13 | 新增VPP EMS能控系统 | vpp-api-ems |
| 2026-05-13 | 新增设备故障码国际化对照表 | vpp-api-elecbusiness lang/*.properties |
