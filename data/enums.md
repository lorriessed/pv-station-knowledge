     1|# 枚举
     2|
     3|更新时间: 2026-05-09
     4|
     5|## 已确认知识
     6|
     7|### 电站类型
     8|COMMON 普通户用；HOUSEHOLD 户用租赁；PUB_BUILD 公共租赁；WHOLE_VILLAGE 整村推进；CM 工商业。
     9|
    10|### 合作模式/资方模式
    11|已知包括 HR 华润、YX 越秀、ZH 中核、DH 顶好、CHD 华电、GF 广发、EPC、CQ 国电投、HUARONG 华融 EPC。
    12|
    13|### 营销奖励枚举
    14|MONTH_POWER、BN_AGEING、BN_AGEING_PROJECT、BN_AGEING_NEGATIVE、INSTALL_ADVANCE。
    15|
    16|### 储能安装维修状态 (2026-05-11 新增，代码证明)
    17|- **来源**: rrsjk-energystorage-service, `InstallMaintenanceInfo.java`
    18|- `InstallMaintenanceInfo.Status`: `WAIT_RATE` (待评价), `COMPLETED` (已完成)
    19|- `InstallMaintenanceInfo.RateStatus`: `AUTO` (自动评价)
    20|- **使用场景**: 安装维修工单完成后进入 WAIT_RATE 状态，15天未评价自动变为 COMPLETED + rateStar=5 + rateStatus=AUTO
    21|
    22|### 储能收益测算相关 (2026-05-11 新增，代码证明)
    23|- **来源**: rrsjk-energystorage-service, commits 2023-05-30 ~ 2023-06-15
    24|- 预算枚举: `ConsultationDetail` 中的预算相关枚举字段
    25|- 充放策略: 时段划分 (尖/峰/平/谷)
    26|
    27|### VPP 基础枚举 (vpp-api-common, 2026-05-13 代码明确证明)
    28|- **来源**: `vpp-api-common/vpp-api-base/src/main/java/com/nahui/energy/enums/`
    29|- `DelFlagEnum`: `0`=有效, `1`=删除
    30|- `BooleanTypeEnum`: `FALSE`(0, 否), `TRUE`(1, 是)
    31|- `DataScopeEnum`: `1`=全部权限, `2`=自定义, `3`=本部门, `4`=本部门及以下, `5`=仅本人 (order值大的生效)
    32|- `UserTypeEnum`: `sys_user`=普通系统用户, `tenant_admin`=租户管理员, `super_admin`=超级管理员
    33|- `CacheTypeEnum`: `0`=所有人可用, `1`=同角色可用, `3`=不可用
    34|- `ServiceCode`: `200`=操作成功, `201`=缓存成功, `400`=前台传值错误, `401`=无权限, `402`=登录过期, `403`=未登录, `408`=断言异常, `500`=服务器内部错误
    35|
    36|### VPP 设备故障码 (vpp-api-elecbusiness, 2026-05-13 代码明确证明)
    37|- **来源**: `vpp-api-elecbusiness-biz/src/main/resources/lang/language_zh_CN.properties`
    38|- 阳台3.0告警: b0=硬件故障, b1=PCS过温, b2=交流电压故障, b3=电池电压故障, b4=PCS与主控通讯故障
    39|- 阳台3.0故障: b0=风扇锁死, b1=系统过温, b2=逆变器过温, b3=控制器过温, b4=交流输出短路, b5=交流输入异常, b6=光伏输入故障, b7=光伏驱动击穿, b8=电池节数错误, b9=交流输出过载, b10=控制器与逆变器通讯故障, b11=光伏输入过压, b12=光伏输入过流, b13=电池电压高, b14=电池电压低
    40|- 英威腾并网故障: 100+种故障码 (PV电压/总线电压/逆变过流/温度异常/通讯故障/电网电压异常等)
    41|
    42|### VPP EMS 代理商类型 (vpp-api-ems, 2026-05-13 代码推断)
    43|- **来源**: `vpp-api-ems/vpp-biz/src/main/java/com/nahui/energy/service/login/impl/LoginServiceImpl.java`
    44|- `100` = 超级管理员 (全部数据权限)
    45|- `201` = 已删除
    46|- `>500` = 已禁用
    47|
    48|### VPP 绿电收益枚举 (vpp-api-gpower, 2026-05-14 代码明确证明)
    49|- **来源**: `vpp-api-gpower/vpp-gpower-biz/src/main/java/com/nahui/energy/enums/`
    50|- `GreenElectricityStatusEnum`: DRAFT(待提交审核), PENDING_FINANCE(待财务审核), FINANCE_REJECTED(财务驳回), APPROVED(已审核)
    51|- `AccountingStatusEnum`: NOT_POSTED(未记账), POSTING(记账中), POSTED(已记账)
    52|- `PaymentStatusEnum`: UNPAID(未收款), PAID(已收款)
    53|- `InvoiceStatusEnum`(gpower): PENDING(待传), SENT(已传), ISSUED(已开)
    54|- `AuditResultEnum`: APPROVED(通过), REJECTED(驳回)
    55|
    56|### VPP 审批角色 (vpp-api-gpower, 2026-05-14 代码明确证明)
    57|- **来源**: `ApproveRolesEnum.java`
    58|- 通用审批: 发起人(fqr,0)→业务负责人(1)→副总经理(2)→总经理(3)
    59|- 回款审批: 业务负责人(1)→财务(2)→税务负责人(3)
    60|
    61|### VPP 发票枚举 (vpp-api-gpower, 2026-05-14 代码明确证明)
    62|- **来源**: `vpp-api-gpower/.../enums/invoice/`
    63|- `InvoiceStatusEnum`(invoice包): NONE(无需), WAIT(待开票), INVOICING, SUCCESS(已开票), FAIL, WAIT_INVALID(待作废), INVALID(已作废), CANCEL, WAIT_RED(待红冲), RED(已红冲)
    64|- `InvoiceTypeEnum`: VAT(1,专票), NORMAL(2,普票), ELEC_GENERAL_INVOICE(3,电普票), ALL_ELEC_SPECIAL_INVOICE(81,全电专票), ALL_ELEC_NORMAL_INVOICE(82,全电普票)
    65|- `ChannelTypeEnum`: TECH(技术服务费), Vpp_Agent(中介费), Vpp_Agent_Haier(海尔中介费), Vpp_Company_Sell(项目公司卖出)
    66|- `CompanyCodeEnum`: 1Q80(青岛海尔新能源), 1PG0(青岛海尔光伏), 0LC0(日日顺科技), 0W50(日日顺乐农), 4300(小天将), 4110(乐农物联网), 1TP0(海尔智能), 1QJ0(海尔绿色能源)
    67|
    68|### VPP 知识管理枚举 (vpp-api-km, 2026-05-14 代码明确证明)
    69|- **来源**: `vpp-api-km/vpp-biz/src/main/java/com/nahui/energy/enums/`
    70|- `KnowledgeDirectoryRolesEnum`: chan_pin_jing_li(产品经理, 可查看所有目录), superadmin(超级管理员, 所有权限)
    71|- `BusinessTypeEnum`: INSERT(入库), UPDATE(修改), DELETE(删除), QUERY(查询), IMPORT(导入), EXPORT(导出)
    72|
    73|## 来源
    74|- Hermes MEMORY.md，2026-05-09 迁移。
    75|
    76|### 电站状态 (rrsjk-openapi-web, 2026-05-16 代码明确证明)
    77|- **来源**: `StationStatusResponse.PowerStationStatusEnum.java`
    78|- `0` = 正常, `1` = 故障, `2` = 离线, `3` = 待机, `4` = 异常
    79|- **使用场景**: 招银租赁租后查询接口返回的电站状态值
    80|
    81|### VPP 泰国大屏枚举 (vpp-thai-dashboard, 2026-05-16 代码明确证明)
    82|- **来源**: `vpp-thai-dashboard/vpp-thai-dashboard-biz/src/main/java/com/nahui/energy/enums/`
    83|- `StationHealthStateEnum`: `1`=断连, `2`=故障, `3`=健康
    84|- `DeviceTypeEnum`: 28种设备类型 (组串式逆变器=1, 数采=2, 箱变=8, 关口电表=17, 储能=39, 市电=60001, EMMA=23070 等)
    85|- `PrivilegeEnum`: `100`=自己, `200`=本级, `300`=本级及以下
    86|
    87|### 招银进件技术方案枚举 V2 (rrsjk-light-service, TAEI-3101, 2026-05-15 代码明确证明)
    88|- **来源**: `CmbPushOrderInfoRequest.java` — `TechnicalSchemeEnumV2`
    89|- 映射关系: houseType → 技术方案
    90|  - `A001`=阵列式 (FLAT平面, SLOPE斜面)
    91|  - `A002`=双面坡 (DOUBLE_SLOPE)
    92|  - `B001`=阳光房 (YGF)
    93|  - `C001`=院内地面 (GROUND)
    94|  - `D001`=院落式桁架15度方案 (GROUND_DOUBLE_SLOPE)
    95|
    96|### 招银进件租赁屋顶类型枚举 V2 (rrsjk-light-service, TAEI-3101, 2026-05-15 代码明确证明)
    97|- **来源**: `CmbPushOrderInfoRequest.java` — `LeaseRoofTypeEnumV2`
    98|- 映射关系: 技术方案 → 租赁屋顶类型
    99|  - `A`=阵列式 (A001, A002)
   100|  - `B`=阳光房 (B001)
   101|  - `C`=庭院房 (C001, D001)
   102|
   103|### SAP记账类型 (rrsjk-light-service, TAEI-2709/2729/2730, 2026-01-29 代码明确证明)
   104|- **来源**: `OperationMaintenanceServiceImpl.java` commits 16204c93, 357c5eed, 09510d6f
   105|- `BookkeepingType`:
   106|  - `A48`: 运维商政策兑现记账（原本A48记账后会自动关联A51数据暂估确认，2026-01-29已注释掉自动关联逻辑）
   107|  - `A51`: 暂估记账类型
   108|- **冲销状态**: `OperationMaintenance.Status.COVERED` = 已冲销
   109|- **冲销流程**: 原relationNo + "_C" → lightSapService.coverOperationMaintenanceA51() → 更新coverVoucher(冲销凭证号) + coverAt(冲销时间) + status=COVERED
   110|
   111|### 派单管理枚举 (rrsjk-light-service, TAEI-2733/2735/2736, 2026-01-29 代码明确证明)
   112|- **来源**: `LightAuditDispatchLog.java` commit 88003e2b
   113|- `TaskTypeEnum`: `DISPATCH`=派单, `GRAB_ORDER`=抢单
   114|- `DealFlagEnum`: `PASSED`=审核通过, `REJECTED`=审核驳回
   115|- **时间维度字段**: dispatchYear/Month/Day(派单时间维度), dealYear/Month/Day(处理时间维度)，用于按年月日统计派单时效
   116|
   117|### 零碳适家SKU类型 (rrsjk-light-service, TAEI-2738/2739, 2026-01-23 代码明确证明)
   118|- **来源**: `LightZeroCarbonSkuData.java` commit 64aeceb8
   119|- 新增: `CHARGING_PILE`="充电桩"
   120|- 已有: `REVERSE_FLOW_METER`="防逆流电表"
   121|
### nahui-dicts-serve 枚举清理 (2026-04-30~2026-05-12)
- **来源**: `nahui-dicts-serve` (commits 17bac12/ca5e24e, 李宁, 2026-04-30~2026-05-12)
- 已删除的枚举字典文件:
  - `apv/purchase/complainStatusList.js` (投诉状态, 30行)
  - `apv/purchase/warningStatusList.js` (预警状态, 42行)
  - `apv/station/contractStatus.js` (电站合同状态, 60行)
  - `apv/station/modeStatus.js` (电站模式状态, 48行)
  - `shop/store/saleChannelList.js` (销售渠道, 24行)
  - `zch/station/status.js` (零碳电站状态, 18行)
- **恢复文件** (2026-05-19, 袁睿林, commit 4e20c548):
  - `apv/finance/purchaseAuditStatus.js` (30行, 请款申请审核状态) — **2026-05-12 删除后恢复**
- 保留并修改: `purchaseAuditStatusList.js`, `purchaseTypeList.js` (APV+ZCH), `applyTypeList.js`, `customerPurchaseStatus.js`, `invoiceStatusList.js`, `invoiceTypeList.js`, `orderStatusList.js`, `payStatusList.js`, `payTypeList.js`
- **影响**: 这些枚举可能被迁移到其他数据管理方式（如后端字典接口），或相关功能已废弃
   134|
   135|### 运维商授权区域状态 (rrsjk-light-service, TAEI-2698/2699, 2025-11-17~2025-12-07 代码明确证明)
   136|- **来源**: `LightOpAuthorityZone.java` → `StatusEnum`
   137|- `WAIT_AUDIT`="待审核", `REJECT`="已拒绝", `WAIT_SIGN`="待签协议", `WAIT_PAY`="待支付保证金", `ENABLE`="已授权", `DISABLE`="禁用"
   138|- 授权区域状态流转: WAIT_AUDIT → WAIT_SIGN → WAIT_PAY → ENABLE (正常流程)
   139|
   140|### 运维商合同类型 (rrsjk-light-service, 2025-11-17~2025-12-07 代码明确证明)
   141|- **来源**: `LightOpContractRecord.java` → `TypeEnum`, `StatusEnum`
   142|- 合同类型: `OP_MASTER`="主合同", `OP_AUTHORITY`="服务区域授权补充协议合同", `OP_NEW_MASTER`="新政策主合同", `OP_ZERO_CARBON_MASTER`="零碳适家户储电站运维合同", `OP_ZERO_CARBON_AUTHORITY`="零碳适家运维服务区域授权补充协议", `OP_AUTHORITY_REMOVE`="运维商服务区域授权减少补充协议", `OP_AUTHORITY_ADD`="运维商服务区域授权增加补充协议"
   143|- 合同状态: `WAIT_SIGN`="待签署", `SIGNED`="已签署"
   144|
   145|### 共享账单审核状态 (rrsjk-light-service, TAEI-2716/2724/2727, 2025-11-17~2025-12-07 代码明确证明)
   146|- **来源**: `LightShareBill.java` → `AuditStatusEnum`, `StatusEnum`
   147|- 审核状态: `WAIT_FINANCE_AUDIT`="待财务审核", `WAIT_CHAINLEAD_AUDIT`="待链群主审核", `AUDIT_PASS`="审核通过", `AUDIT_NOT_PASS`="审核未通过"
   148|- 账单状态: `INIT`="初始化", `CONFIRM`="已确认"
   149|

### 合同类型枚举 (LightStationContractRecord.ContractTypeEnum)
| 枚举值 | 说明 | 短信模板 | 合同号前缀 |
|---|---|---|---|
| MASTER | 主合同 (整村分布式) | 1133 | FS |
| ZH_MASTER | 中核主合同 | 1133 | FS |
| CHD_MASTER | 华电主合同 | 1133 | FS |
| INSTALL | 装机补充协议 | 1134 | FSI |
| FINANCE | 结算补充协议 | 1135 | FSF |
| STOP | 终止协议 | - | FSS |
| OWNERSHIP_PROVE | 权属证明 (华润) | 1146 | FSO |
| DH_MASTER | 顶好主合同 | - | - |
| GF_MASTER | 广发主合同 | - | - |
| TP_PAYMENT_AGENCY | 共建合同 | - | - |
| PF_INFO_AUTH | 浦银信息授权协议 | - | - |
| CREDIT_AUTH | 信用授权协议 | - | - |
| GF_INFO_AUTH | 广发展信息授权协议 | - | - |
| HRFLC_INFO_AUTH | 华融信息授权协议 | - | - |
| HRFLC_EPC_MASTER | 华融EPC业主主合同 | - | - |

### 合同状态枚举 (LightStationContractRecord.StatusEnum)
| 枚举值 | 说明 |
|---|---|
| INIT | 初始 |
| WAIT_SIGN | 待签合同 |
| WAIT_USER_SIGN | 待用户签合同 |
| WAIT_PARTNER_SIGN | 待合伙人签合同 |
| SIGNED | 已签署 |
| DISABLE | 已作废 |

### 签署方式枚举 (LightStationContractRecord.SignTypeEnum)
| 枚举值 | 说明 |
|---|---|
| ONLINE | 线上签署 (DCC 电子签章) |
| OFFLINE | 线下签署 (纸质合同) |

---

## 补漏第3期新增枚举 (2026-01-18 扫描)

### 审核类型枚举 (LightAuditDispatchLog.AuditTypeEnum)
**来源**: `rrsjk-light-api/src/main/java/com/rrsjk/light/entity/dispatch/LightAuditDispatchLog.java` (解钦, 2026-01-14)
| 枚举值 | 说明 |
|---|---|
| PLAN_AUDIT | 方案审核 |
| TECH_AUDIT | 技术审核 |
| BUSINESS_AUDIT | 商务审核 |

### 派单类型枚举 (LightAuditDispatchLog.DispatchTypeEnum)
**来源**: 同上
| 枚举值 | 说明 |
|---|---|
| MANUAL | 人工派单 |
| AUTO | 自动派单 |

### 处理标识枚举 (LightAuditDispatchLog.OperateTypeEnum)
**来源**: 同上
| 枚举值 | 说明 |
|---|---|
| SELF_AUDIT | 主动审核 |
| SNAP_INVALID | 抢单作废 |
| RE_DISPATCH | 人工改派 |

### 共建费模式枚举 (LightCompanyInfo.JointConstructionFeeModelEnum)
**来源**: `rrsjk-light-service` (majinhu, 2025-12-29)
| 枚举值 | 说明 |
|---|---|
| SUPPORT | 支持共建费模式 |
| NOT_SUPPORT | 不支持共建费模式 |

### 合同类型新增 (LightStationContractRecord.ContractTypeEnum)
**来源**: 同上
| 枚举值 | 说明 |
|---|---|
| TP_PAYMENT_AGENCY | 共建专项合同 (值=33) |

---

## 计收方法枚举 (代码明确证明, 2026-05-20)
**来源**: `rrsjk-light-service` → `CmLightProject.IncomeMethodEnum` (commit: 解钦 db25723, 2026-05-19)
**需求**: TAEI-3107 【风电】风电产值法兼容1.0

| 枚举值 | 说明 |
|---|---|
| FINAL_INSPECTION | 终验法（默认） |
| OUTPUT_VALUE | 产值确认法 |

> 原 `ConfirmMethodEnum` 重命名为 `IncomeMethodEnum`，数据库字段 `confirm_method` → `income_method`

---

## 招投标审核状态枚举 (代码明确证明, 2026-05-20)
**来源**: `rrsjk-light-service` → `TenderManagmentAudit.java` (commit: laowang f2eabc2, 2026-05-15)
**需求**: TAEI-3102 【户用光伏】CBS招投标流程

| 枚举值 | 说明 | 适用范围 |
|---|---|---|
| AGREE | 通过 | 所有审核环节 |
| DISAGREE | 驳回 | 所有审核环节 |
| REJECT | 拒绝 | 仅首次附件审核 |

---

## 项目分类枚举 (代码明确证明, 2026-05-20)
**来源**: `rrsjk-light-service` → `TenderManagmentAudit.projectCategory` (commit: laowang f2eabc2, 2026-05-15)
**需求**: TAEI-3102 【户用光伏】CBS招投标流程

| 枚举值 | 说明 |
|---|---|
| FD | 风电 |
| GSY | 工商业 |
|| HYEPC | 户用EPC |
|| YW | 运维 |
|| LTSJ | 零碳世家 |

### 方案变更节点枚举
**来源**: `rrsjk-light-service` → `LightStationPlanChange.java`
| 枚举值 | 说明 |
|---|---|
| COMPLETE_BEFORE | 完工前变更 |
| COMPLETE_AFTER | 完工后变更 |

### 审核类型枚举 (代码确认)
**来源**: `rrsjk-light-service` → `LightStationAudit.java`
| 枚举值 | 说明 |
|---|---|
| TECH_CHECK | 技术审核 |
| WAIT_FIRST_AUDIT | 一审(商务审核) |

---

## nahui-dicts-serve 前端数据字典索引 (配置证明, 2026-05-22 扫描)

> 以下字典来自 `nahui-dicts-serve` 前端数据字典仓库，2026-03~2026-05 期间大量新增。
> 这些是前端展示用的下拉选项值，实际业务逻辑以 rrsjk-light-service 后端 Java 枚举为准。
> 来源: `nahui-dicts-serve/src/data/` (commits 2026-03~2026-05, 袁睿林/李培龙/杨辉)

### 电站状态相关
- `apv/station/statusList.js` — 电站状态（含"待三方审核"）
- `apv/station/businessReviewStatus.js` — 商务审核状态
- `apv/station/technicalReviewStatus.js` — 技术审核状态
- `apv/station/manageEditStatus.js` — 实施方案变更状态
- `apv/station/abnormal.js` — 异常状态
- `apv/station/alarmStatusList.js` — 告警状态
- `apv/station/dispatchStatusList.js` — 派单状态
- `apv/station/startWorkStatusList.js` — 开工状态
- `apv/station/roadWorkStatusList.js` — 施工进度状态
- `apv/station/feedbackStatusList.js` — 反馈状态
- `apv/station/feedbackTypeList.js` — 反馈类型
- `apv/station/changeNodeList.js` — 变更节点
- `apv/station/changeTypeList.js` — 变更类型
- `apv/station/inverterChangeStatusList.js` — 逆变器变更状态
- `apv/station/convergingStatusList.js` — 汇聚状态
- `apv/station/convergingStationStatusList.js` — 汇聚电站状态
- `apv/station/personInfoAuthStatusList.js` — 个人信息授权状态
- `apv/station/transStationstatus.js` — 电站转单状态（WAIT_OUT_CONFIRM待确认转出 / WAIT_IN_CONFIRM待确认转入 / COMPLETED转单完成 / OUT_REJECTED拒绝转出 / IN_REJECTED拒绝转入）(2024-11-21 创建, 前端配置证明)

### 电站基础信息
- `apv/station/beiAnType.js` — 备案类型
- `apv/station/proTypeList.js` — 项目类型
- `apv/station/contractTypeList.js` — 合同类型（含广发主合同、华融EPC等）
- `apv/station/componentSizeList.js` — 组件尺寸
- `apv/station/houseTypeList.js` — 房屋类型
- `apv/station/installList.js` — 安装方式（大更新）
- `apv/station/installPlanList.js` — 安装计划
- `apv/station/moduleList.js` — 组件列表
- `apv/station/shapeList.js` — 形状列表
- `apv/station/gridTypeList.js` — 并网类型
- `apv/station/docTypeList.js` — 文档类型
- `apv/station/roofStyleList.js` — 屋顶样式
- `apv/station/stationMode.js` — 电站模式
- `apv/station/distributionList.js` — 配送列表
- `apv/station/peirodList.js` — 期间列表

### 押金/额度管理 (bail)
- `apv/bail/shareQuotaStatus.js` — 共享额度状态
- `apv/bail/auxiliaryQuotaAuditStatus.js` — 辅材额度审核状态
- `apv/bail/bailType.js` — 押金类型
- `apv/bail/payChannel.js` — 支付渠道
- `apv/bail/payStatus.js` — 支付状态

### 财务/请款
- `apv/finance/purchaseTypeList.js` — 请款申请类型
- `apv/finance/purchaseAuditStatus.js` — 请款申请审核状态
- `apv/finance/purchaseAuditStatusList.js` — 审核状态列表
- `apv/finance/moduleList.js` — 模块列表
- `apv/finance/nodeTypeList.js` — 节点类型
- `apv/finance/policyStandardList.js` — 政策标准

### 采购/库存
- `apv/purchase/applyTypeList.js` — 申请类型
- `apv/purchase/orderStatusList.js` — 订单状态
- `apv/purchase/payStatusList.js` — 支付状态
- `apv/purchase/payTypeList.js` — 支付类型
- `apv/purchase/invoiceStatusList.js` — 发票状态
- `apv/purchase/invoiceTypeList.js` — 发票类型
- `apv/purchase/customerPurchaseStatus.js` — 客户采购状态
- `apv/purchase/specialOutboundStatus.js` — 特殊出库状态
- `apv/purchase/stockUpStatus.js` — 备货状态
- `apv/purchase/repurchaseReasonList.js` — 回购原因

### 业主租金
- `apv/owenrRental/receiptRecordStatus.js` — 收款记录状态
- `apv/owenrRental/rentalPaymentStatus.js` — 租金支付状态
- `apv/owenrRental/rentalSignTypeList.js` — 租金签约类型

### 政策
- `apv/policy/policyMode.js` — 政策模式
- `apv/policy/policyStandardList.js` — 政策标准
- `apv/policy/policyPointList.js` — 政策积分
- `apv/policy/policyExeStandardList.js` — 政策执行标准
- `apv/policy/documentDetailStatusList.js` — 文档详情状态

### 超期考核
- `apv/overdue/overdueInventory.js` — 超期库存
- `apv/overdue/overdueStatus.js` — 超期状态

### 服务商/仓储
- `apv/base/spContractStatus.js` — 服务商合同状态
- `apv/base/spWhitelist.js` — 服务商白名单（769行）
- `apv/store/serviceProviderTypeList.js` — 服务商类型
- `apv/store/useStatusList.js` — 物料领用状态（完工前领用）

### 零碳适家 (zch)
- `zch/base/businessModelTypeList.js` — 业务模式类型（LIGHT_STORAGE光储 / E_STATION零碳E站）
- `zch/base/businessModelStatus.js` — 业务模式审核状态（WAIT_AUDIT/AUDIT_REJECT/WAIT_SIGN/ENABLE）
- `zch/finance/sapPurchaseStatusList.js` — SAP对账单状态
- `zch/finance/operateTypeList.js` — 操作类型
- `zch/finance/purchaseTypeList.js` — 请款申请类型
- `zch/finance/checkStatus.js` — 核对状态
- `zch/finance/confirmStatusList.js` — 确认状态
- `zch/finance/invoiceRelevanceList.js` — 发票关联
- `zch/finance/invoiceStatusList.js` / `invoiceTypeList.js` — 发票状态/类型
- `zch/finance/purchaseAuditStatusList.js` — 审核状态列表

### 广发商机 (gf)
- `gf/station/towardsList.js` — 朝向
- `gf/station/designTypeList.js` — 设计方案
- `gf/station/inverterBrandNameList.js` — 逆变器品牌
- `gf/station/moduleBrandNameList.js` — 组件品牌
- `gf/station/mainBeamTypeList.js` — 主梁类型
- `gf/station/pitchedRoofFaceTypeList.js` — 坡屋面朝向
- `gf/station/roofStructureTypeList.js` — 屋顶结构
- `gf/station/tileTypeList.js` — 瓦片类型
- `gf/station/towardsList.js` — 朝向
- `gf/station/houseTypeList.js` — 房屋类型（通过 apv 共享）

### 运维/HDS (osp/hds)
- `osp/hds/importTaskOperation.js` — 导入任务操作（CONFIRMED确认暂估 / CONFIRM_INCOME确认实际 / BATCH_COVER批量覆盖 / ALL_STATION_DETAIL / A48_STATION_DETAIL / A51_STATION_DETAIL）
- `osp/hds/importTaskStatus.js` — 导入任务状态（PROCESSING/COMPLETED/FAILED）
- `osp/hds/houseType.js` — 房屋类型

### 运维通用 (osp/general) — 停付管理字典 (2026-06-01~08 前端配置证明)
> 以下字典对应后端 `RentSuspendApplication` 停付管理功能 (TAEI-3103)。后端枚举已在上方"租金停付管理枚举"章节记录，此处为前端展示层字典。
- `osp/general/stopPayOwnerReason.js` — 业主申请停付原因（OWNER_CHANGE业主变更 / BLACK_ACCOUNT黑户 / OTHER其他原因）
- `osp/general/stopPayOwnerR.js` — 业主申请恢复原因（TRANSFER_SUCCESSFUL换户成功 / OTHER其他原因）
- `osp/general/stopPayDisputeReason.js` — 纠纷停付原因（原 stopPayReason.js, 2026-06-01 R070 重命名）
- `osp/general/stopPayDisputeR.js` — 纠纷恢复原因（原 stopPayRecoverReason.js, 2026-06-03 R062 重命名）
- `osp/general/stopPayStatus.js` — 租金停付状态（对应后端 StatusEnum 9个状态）
- `osp/general/stopPayType.js` — 租金停付类型（OWNER_APPLY业主申请 / DISPUTE_SUSPEND纠纷停付）

### 华融 (hr)
- `hr/userInfoStatus.js` — 华融用户信息登记状态

### 业主银行卡变更 (osp/merchant)
- `osp/merchant/bankInfoStatus.js` — 业主银行卡变更状态
- `osp/merchant/bankBentPaymentMode.js` — 银行卡变更打款模式
- `osp/merchant/bankFieldMethod.js` — 银行卡变更字段方法

### 服务商省份授权 (2026-05-19~21 代码明确证明)
**来源**: `rrsjk-light-service` → `LightSpServiceProvince.java` (dev分支, commits: 包鑫, branch: regionUnlimit)
- **StatusEnum** (审核状态):
  - `WAIT_CENTER_AUDIT` — 待分中心审核
  - `CENTER_AUDIT_REJECTED` — 分中心审核驳回
  - `WAIT_HD_AUDIT` — 待总部审核
  - `HD_AUDIT_REJECTED` — 总部审核驳回
  - `AUDIT_OK` — 审核通过
- **ApproveStatusEnum** (开通状态):
  - `NO_APPROVE` — 未开通
  - `APPROVED` — 已开通
- **业务含义**: 服务商申请指定省/市的服务授权后，先经分中心审核，再经总部审核，审核通过后开通授权
- **证据等级**: 代码明确证明

### 租金停付管理枚举 (TAEI-3103, 代码明确证明, 2026-05-25~27)
**来源**: `rrsjk-light-service` dev 分支 → `RentSuspendApplication.java` (sunzn, branch: origin/szn_rent_stop_20260525)
- **StatusEnum** (9个状态):
  - `SUSPEND_WAIT_FIRST_AUDIT` — 申请停付待初审
  - `SUSPEND_FIRST_AUDIT_REJECTED` — 申请停付初审驳回
  - `SUSPEND_WAIT_FINAL_AUDIT` — 申请停付待终审
  - `SUSPEND_FINAL_AUDIT_REJECTED` — 申请停付终审驳回
  - `SUSPEND_FINAL_AUDIT_APPROVED` — 申请停付终审通过
  - `SUSPEND_CANCELED` — 申请停付已撤销
  - `RESUME_WAIT_AUDIT` — 申请恢复待审核
  - `RESUME_AUDIT_REJECTED` — 申请恢复审核驳回
  - `RESUME_AUDIT_APPROVED` — 申请恢复审核通过
- **RentSuspendTypeEnum** (停付类型):
  - `OWNER_APPLY` — 业主申请
  - `DISPUTE_SUSPEND` — 纠纷停付
- **SourceEnum** (业务来源):
  - `PV_OPERATOR` — 光伏运维商
- **SuspendReasonEnum** (停付原因):
  - `OWNER_CHANGE` — 业主变更
  - `BLACK_ACCOUNT` — 黑户
  - `INITIAL_INSTALL_FEE` — 初装费
  - `RENT` — 租金
  - `DISPUTE` — 纠纷
  - `OTHER` — 其他原因
- **LightUnionpayRentRecord 新增状态**: `SUSPEND` — 暂停支付

### 招银金租电站状态 (TAEI-3101, 代码明确证明, 2026-05-22~23)
**来源**: `rrsjk-light-service` → `CmbLeasingStation.java` (lilong, branch: origin/20260515-alone-zhaoyin-price)
- **StatusEnum**: 招银金租电站状态（用于push区分）
- **retransFlagEnum**: 重传标识枚举
- **新旧数据区分**: 从 pushTime 改为 createdAt 作为新旧逻辑区分字段

### 电站转移状态 (TAEI-3058, 代码明确证明, 2026-05-26~28)
**来源**: `rrsjk-light-service` → `LightStationTransferOrder.java`, `LightStationTransferOrderLog.java` (德/姜传德, branch: origin/station-transfer-sub-account-20260525)
- **StatusEnum** (5个状态):
  - `WAIT_OUT_CONFIRM` — 待确认转出
  - `WAIT_IN_CONFIRM` — 待确认转入
  - `COMPLETED` — 转单完成
  - `OUT_REJECTED` — 拒绝转出
  - `IN_REJECTED` — 拒绝转入
- **ActionTypeEnum** (5个动作):
  - `SUBMIT` — 发起转单
  - `CONFIRM_OUT` — 确认转出
  - `REJECT_OUT` — 拒绝转出
  - `CONFIRM_IN` — 确认转入
  - `REJECT_IN` — 拒绝转入

### 运维保证金 FAP 状态 (TAEI-3117, 代码明确证明, 2026-06-05)
**来源**: `rrsjk-light-service` → `LightOperationDeposit.java` (sunzn, commit 1a5e72e8b3)
- **FapStatusEnum**:
  - `WAIT_SENT` — 待传FAP
  - `SENT` — 已传FAP
  - `CANCEL` — 已作废
- **Status 新增**: `CANCEL("已作废")` — 保证金订单作废状态
- **LightFapRecord.BizTypeEnum 新增**: `OPERATION_DEPOSIT("运维保证金", "TY010031", "收-保证金-其他应付款（先收后退）")`

### 审核影像驳回标记语义变更 (TAEI-3127, 代码明确证明, 2026-06-08)
**来源**: `rrsjk-light-service` → `LightStationRelateFile.java`, `AcceptanceConfirmServiceImpl.java`, `CompleteConfirmServiceImpl.java` (王希然, commit 930ffb2dae + 855dca0451)
- **变更前**: 三态驳回 — `null=未初始化, "1"=驳回, "0"=未驳回`（基于白名单判定）
- **变更后**: 二态驳回 — `null=未驳回, "0"=驳回`
- **Boolean映射** (855dca0451修复):
  - `Boolean.TRUE` → `"0"` (驳回) [原为"1"]
  - `Boolean.FALSE` → `"1"` (未驳回) [原为"0"]
- **影响范围**: 方案审核、完工审核、技术审核的所有影像驳回逻辑
- **注意**: 历史数据中 `reject_flag="1"` 的记录需确认语义迁移

