# 枚举

更新时间: 2026-05-09

## 已确认知识

### 电站类型
COMMON 普通户用；HOUSEHOLD 户用租赁；PUB_BUILD 公共租赁；WHOLE_VILLAGE 整村推进；CM 工商业。

### 合作模式/资方模式
已知包括 HR 华润、YX 越秀、ZH 中核、DH 顶好、CHD 华电、GF 广发、EPC、CQ 国电投、HUARONG 华融 EPC。

### 营销奖励枚举
MONTH_POWER、BN_AGEING、BN_AGEING_PROJECT、BN_AGEING_NEGATIVE、INSTALL_ADVANCE。

### 储能安装维修状态 (2026-05-11 新增，代码证明)
- **来源**: rrsjk-energystorage-service, `InstallMaintenanceInfo.java`
- `InstallMaintenanceInfo.Status`: `WAIT_RATE` (待评价), `COMPLETED` (已完成)
- `InstallMaintenanceInfo.RateStatus`: `AUTO` (自动评价)
- **使用场景**: 安装维修工单完成后进入 WAIT_RATE 状态，15天未评价自动变为 COMPLETED + rateStar=5 + rateStatus=AUTO

### 储能收益测算相关 (2026-05-11 新增，代码证明)
- **来源**: rrsjk-energystorage-service, commits 2023-05-30 ~ 2023-06-15
- 预算枚举: `ConsultationDetail` 中的预算相关枚举字段
- 充放策略: 时段划分 (尖/峰/平/谷)

### VPP 基础枚举 (vpp-api-common, 2026-05-13 代码明确证明)
- **来源**: `vpp-api-common/vpp-api-base/src/main/java/com/nahui/energy/enums/`
- `DelFlagEnum`: `0`=有效, `1`=删除
- `BooleanTypeEnum`: `FALSE`(0, 否), `TRUE`(1, 是)
- `DataScopeEnum`: `1`=全部权限, `2`=自定义, `3`=本部门, `4`=本部门及以下, `5`=仅本人 (order值大的生效)
- `UserTypeEnum`: `sys_user`=普通系统用户, `tenant_admin`=租户管理员, `super_admin`=超级管理员
- `CacheTypeEnum`: `0`=所有人可用, `1`=同角色可用, `3`=不可用
- `ServiceCode`: `200`=操作成功, `201`=缓存成功, `400`=前台传值错误, `401`=无权限, `402`=登录过期, `403`=未登录, `408`=断言异常, `500`=服务器内部错误

### VPP 设备故障码 (vpp-api-elecbusiness, 2026-05-13 代码明确证明)
- **来源**: `vpp-api-elecbusiness-biz/src/main/resources/lang/language_zh_CN.properties`
- 阳台3.0告警: b0=硬件故障, b1=PCS过温, b2=交流电压故障, b3=电池电压故障, b4=PCS与主控通讯故障
- 阳台3.0故障: b0=风扇锁死, b1=系统过温, b2=逆变器过温, b3=控制器过温, b4=交流输出短路, b5=交流输入异常, b6=光伏输入故障, b7=光伏驱动击穿, b8=电池节数错误, b9=交流输出过载, b10=控制器与逆变器通讯故障, b11=光伏输入过压, b12=光伏输入过流, b13=电池电压高, b14=电池电压低
- 英威腾并网故障: 100+种故障码 (PV电压/总线电压/逆变过流/温度异常/通讯故障/电网电压异常等)

### VPP EMS 代理商类型 (vpp-api-ems, 2026-05-13 代码推断)
- **来源**: `vpp-api-ems/vpp-biz/src/main/java/com/nahui/energy/service/login/impl/LoginServiceImpl.java`
- `100` = 超级管理员 (全部数据权限)
- `201` = 已删除
- `>500` = 已禁用

### VPP 绿电收益枚举 (vpp-api-gpower, 2026-05-14 代码明确证明)
- **来源**: `vpp-api-gpower/vpp-gpower-biz/src/main/java/com/nahui/energy/enums/`
- `GreenElectricityStatusEnum`: DRAFT(待提交审核), PENDING_FINANCE(待财务审核), FINANCE_REJECTED(财务驳回), APPROVED(已审核)
- `AccountingStatusEnum`: NOT_POSTED(未记账), POSTING(记账中), POSTED(已记账)
- `PaymentStatusEnum`: UNPAID(未收款), PAID(已收款)
- `InvoiceStatusEnum`(gpower): PENDING(待传), SENT(已传), ISSUED(已开)
- `AuditResultEnum`: APPROVED(通过), REJECTED(驳回)

### VPP 审批角色 (vpp-api-gpower, 2026-05-14 代码明确证明)
- **来源**: `ApproveRolesEnum.java`
- 通用审批: 发起人(fqr,0)→业务负责人(1)→副总经理(2)→总经理(3)
- 回款审批: 业务负责人(1)→财务(2)→税务负责人(3)

### VPP 发票枚举 (vpp-api-gpower, 2026-05-14 代码明确证明)
- **来源**: `vpp-api-gpower/.../enums/invoice/`
- `InvoiceStatusEnum`(invoice包): NONE(无需), WAIT(待开票), INVOICING, SUCCESS(已开票), FAIL, WAIT_INVALID(待作废), INVALID(已作废), CANCEL, WAIT_RED(待红冲), RED(已红冲)
- `InvoiceTypeEnum`: VAT(1,专票), NORMAL(2,普票), ELEC_GENERAL_INVOICE(3,电普票), ALL_ELEC_SPECIAL_INVOICE(81,全电专票), ALL_ELEC_NORMAL_INVOICE(82,全电普票)
- `ChannelTypeEnum`: TECH(技术服务费), Vpp_Agent(中介费), Vpp_Agent_Haier(海尔中介费), Vpp_Company_Sell(项目公司卖出)
- `CompanyCodeEnum`: 1Q80(青岛海尔新能源), 1PG0(青岛海尔光伏), 0LC0(日日顺科技), 0W50(日日顺乐农), 4300(小天将), 4110(乐农物联网), 1TP0(海尔智能), 1QJ0(海尔绿色能源)

### VPP 知识管理枚举 (vpp-api-km, 2026-05-14 代码明确证明)
- **来源**: `vpp-api-km/vpp-biz/src/main/java/com/nahui/energy/enums/`
- `KnowledgeDirectoryRolesEnum`: chan_pin_jing_li(产品经理, 可查看所有目录), superadmin(超级管理员, 所有权限)
- `BusinessTypeEnum`: INSERT(入库), UPDATE(修改), DELETE(删除), QUERY(查询), IMPORT(导入), EXPORT(导出)

## 来源
- Hermes MEMORY.md，2026-05-09 迁移。

### 电站状态 (rrsjk-openapi-web, 2026-05-16 代码明确证明)
- **来源**: `StationStatusResponse.PowerStationStatusEnum.java`
- `0` = 正常, `1` = 故障, `2` = 离线, `3` = 待机, `4` = 异常
- **使用场景**: 招银租赁租后查询接口返回的电站状态值

### VPP 泰国大屏枚举 (vpp-thai-dashboard, 2026-05-16 代码明确证明)
- **来源**: `vpp-thai-dashboard/vpp-thai-dashboard-biz/src/main/java/com/nahui/energy/enums/`
- `StationHealthStateEnum`: `1`=断连, `2`=故障, `3`=健康
- `DeviceTypeEnum`: 28种设备类型 (组串式逆变器=1, 数采=2, 箱变=8, 关口电表=17, 储能=39, 市电=60001, EMMA=23070 等)
- `PrivilegeEnum`: `100`=自己, `200`=本级, `300`=本级及以下

### 招银进件技术方案枚举 V2 (rrsjk-light-service, TAEI-3101, 2026-05-15 代码明确证明)
- **来源**: `CmbPushOrderInfoRequest.java` — `TechnicalSchemeEnumV2`
- 映射关系: houseType → 技术方案
  - `A001`=阵列式 (FLAT平面, SLOPE斜面)
  - `A002`=双面坡 (DOUBLE_SLOPE)
  - `B001`=阳光房 (YGF)
  - `C001`=院内地面 (GROUND)
  - `D001`=院落式桁架15度方案 (GROUND_DOUBLE_SLOPE)

### 招银进件租赁屋顶类型枚举 V2 (rrsjk-light-service, TAEI-3101, 2026-05-15 代码明确证明)
- **来源**: `CmbPushOrderInfoRequest.java` — `LeaseRoofTypeEnumV2`
- 映射关系: 技术方案 → 租赁屋顶类型
  - `A`=阵列式 (A001, A002)
  - `B`=阳光房 (B001)
  - `C`=庭院房 (C001, D001)

### SAP记账类型 (rrsjk-light-service, TAEI-2709/2729/2730, 2026-01-29 代码明确证明)
- **来源**: `OperationMaintenanceServiceImpl.java` commits 16204c93, 357c5eed, 09510d6f
- `BookkeepingType`:
  - `A48`: 运维商政策兑现记账（原本A48记账后会自动关联A51数据暂估确认，2026-01-29已注释掉自动关联逻辑）
  - `A51`: 暂估记账类型
- **冲销状态**: `OperationMaintenance.Status.COVERED` = 已冲销
- **冲销流程**: 原relationNo + "_C" → lightSapService.coverOperationMaintenanceA51() → 更新coverVoucher(冲销凭证号) + coverAt(冲销时间) + status=COVERED

### 派单管理枚举 (rrsjk-light-service, TAEI-2733/2735/2736, 2026-01-29 代码明确证明)
- **来源**: `LightAuditDispatchLog.java` commit 88003e2b
- `TaskTypeEnum`: `DISPATCH`=派单, `GRAB_ORDER`=抢单
- `DealFlagEnum`: `PASSED`=审核通过, `REJECTED`=审核驳回
- **时间维度字段**: dispatchYear/Month/Day(派单时间维度), dealYear/Month/Day(处理时间维度)，用于按年月日统计派单时效

### 零碳适家SKU类型 (rrsjk-light-service, TAEI-2738/2739, 2026-01-23 代码明确证明)
- **来源**: `LightZeroCarbonSkuData.java` commit 64aeceb8
- 新增: `CHARGING_PILE`="充电桩"
- 已有: `REVERSE_FLOW_METER`="防逆流电表"

### nahui-dicts-serve 枚举清理 (2026-04-30~2026-05-12)
- **来源**: `nahui-dicts-serve` (commits 17bac12/ca5e24e, 李宁, 2026-04-30~2026-05-12)
- 已删除的枚举字典文件:
  - `apv/finance/purchaseAuditStatus.js` (采购审核状态, 30行)
  - `apv/purchase/complainStatusList.js` (投诉状态, 30行)
  - `apv/purchase/warningStatusList.js` (预警状态, 42行)
  - `apv/station/contractStatus.js` (电站合同状态, 60行)
  - `apv/station/modeStatus.js` (电站模式状态, 48行)
  - `shop/store/saleChannelList.js` (销售渠道, 24行)
  - `zch/station/status.js` (零碳电站状态, 18行)
- 保留并修改: `purchaseAuditStatusList.js`, `purchaseTypeList.js`, `applyTypeList.js`, `customerPurchaseStatus.js`, `invoiceStatusList.js`, `invoiceTypeList.js`, `orderStatusList.js`, `payStatusList.js`, `payTypeList.js`
- **影响**: 这些枚举可能被迁移到其他数据管理方式（如后端字典接口），或相关功能已废弃

### 运维商授权区域状态 (rrsjk-light-service, TAEI-2698/2699, 2025-11-17~2025-12-07 代码明确证明)
- **来源**: `LightOpAuthorityZone.java` → `StatusEnum`
- `WAIT_AUDIT`="待审核", `REJECT`="已拒绝", `WAIT_SIGN`="待签协议", `WAIT_PAY`="待支付保证金", `ENABLE`="已授权", `DISABLE`="禁用"
- 授权区域状态流转: WAIT_AUDIT → WAIT_SIGN → WAIT_PAY → ENABLE (正常流程)

### 运维商合同类型 (rrsjk-light-service, 2025-11-17~2025-12-07 代码明确证明)
- **来源**: `LightOpContractRecord.java` → `TypeEnum`, `StatusEnum`
- 合同类型: `OP_MASTER`="主合同", `OP_AUTHORITY`="服务区域授权补充协议合同", `OP_NEW_MASTER`="新政策主合同", `OP_ZERO_CARBON_MASTER`="零碳适家户储电站运维合同", `OP_ZERO_CARBON_AUTHORITY`="零碳适家运维服务区域授权补充协议", `OP_AUTHORITY_REMOVE`="运维商服务区域授权减少补充协议", `OP_AUTHORITY_ADD`="运维商服务区域授权增加补充协议"
- 合同状态: `WAIT_SIGN`="待签署", `SIGNED`="已签署"

### 共享账单审核状态 (rrsjk-light-service, TAEI-2716/2724/2727, 2025-11-17~2025-12-07 代码明确证明)
- **来源**: `LightShareBill.java` → `AuditStatusEnum`, `StatusEnum`
- 审核状态: `WAIT_FINANCE_AUDIT`="待财务审核", `WAIT_CHAINLEAD_AUDIT`="待链群主审核", `AUDIT_PASS`="审核通过", `AUDIT_NOT_PASS`="审核未通过"
- 账单状态: `INIT`="初始化", `CONFIRM`="已确认"
