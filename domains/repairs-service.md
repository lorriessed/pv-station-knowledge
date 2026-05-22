# 光伏备件运维服务 (repairs)

更新时间: 2026-05-22 (第9轮全量通读)

## 仓库概述

**仓库**: `repairs` (`/data/pvcode/repairs`)
**架构**: Java/Spring Boot + MyBatis + Dubbo + Flowable 工作流
**模块**: `repairs-api` (接口定义) + `repairs-impl` (实现)
**数据库**: `pvs_repairs`
**父 POM**: `com.haier:rrs-parent:8.0.5`
**技术栈**: Spring Boot 2.2.4, Dubbo 2.7.4.1, Flowable 6.8.0, MyBatis 3.5.3, Hutool 5.8.20

### 外部依赖服务
- `rrsjk-system-api` — 系统服务
- `rrsjk-member-api` — 会员服务
- `rrsjk-item-api` — 商品/物料服务
- `rrsjk-light-operation-api` — 光伏运维运营服务
- `rrs-dispenser-api` — 水站设备 API
- `shoppingmall-basic-service` — 商城基础服务
- **日日顺(RRS)** — 物流/仓储/出入库 (通过 OMS 接口)
- **SAP** — 财务记账
- **GVS** — 库存管理
- **建站系统** — 借件订单交互
- **快递100** — 物流轨迹查询

---

## 1. 借件订单业务 (Borrow Order)

**来源**: `repairs-api` → `BorrowOrderStatusEnum.java`, `SpOrderBorrowService.java`, `SpOrderBorrow.java`

### 借件订单状态机 (18 种状态)

| 状态码 | 状态名 | 说明 |
|--------|--------|------|
| 0 | 初始 | 运维商录入订单 |
| 1 | 待中心经理审批 | 运维商提交订单 |
| 2 | 中心经理驳回 | 中心驳回 |
| 3 | 待总部审批 | 中心经理提交通过 |
| 4 | 总部审批通过 | 总部审批通过 |
| 5 | 总部驳回 | 总部审批驳回 |
| 6 | 待运维商认责 | 总部审批通过，责任方是运维商 |
| 7 | 运维商认责 | 运维商同意认责，生成回购单 |
| 8 | 运维商不认责 | 流程结束 |
| 9 | 待供应商认责 | 总部审批通过，责任方是供应商 |
| a | 供应商认责 | 供应商同意认责，转售后订单发货 |
| b | 供应商不认责 | 退回中心经理重新判责 |
| c | 建站商通过 | 建站商发货触发运维商系统生成入库单 |
| d | 建站商驳回 | 退回中心经理重新审批（指派其他建站商） |
| e | 建站商发货 | 建站商发货触发运维商系统生成入库单 |
| f | 运维商入库 | 运维商系统接收入库，生成工单备件申请记录 |
| g | 订单关闭 | 备件接收入库后，订单状态更新为关闭 |
| h | 取消借件 | 运维商取消（待中心经理审批/中心经理驳回时可操作） |
| i | 提交建站借件成功 | — |
| j | 提交建站借件失败 | — |
| k | 中心仓订单创建成功 | — |
| l | 中心仓发货 | — |

### 核心业务流程

```
运维商录入(0) → 待中心经理审批(1) → 中心驳回(2) / 通过 → 待总部审批(3)
  → 总部驳回(5) / 通过(4) → 判责分支:
    ├── 运维商认责: 待认责(6) → 认责(7) → 生成回购单
    ├── 运维商不认责(8) → 流程结束
    ├── 供应商认责: 待认责(9) → 认责(a) → 转售后订单发货
    └── 供应商不认责(b) → 退回中心经理重新判责
  → 建站借件分支: 建站商通过(c)/驳回(d)/发货(e) → 运维商入库(f) → 订单关闭(g)
```

### 借件订单 Service 接口

**来源**: `repairs-api` → `SpOrderBorrowService.java`

| 方法 | 说明 |
|------|------|
| `getPage()` | 分页查询借件订单 |
| `getListInfo()` | 列表查询 |
| `getPageSupplier()` | 供应商视角分页查询 |
| `getInfoById()` | 查询详情 |
| `getInfoByOrderNo()` | 按订单号查询 |
| `save()` | 新增订单 |
| `update()` | 编辑订单 |
| `delete()` | 删除订单 |
| `submitOrder()` | 提交订单 |
| `zxjlApproval()` | 中心经理审批（HDS） |
| `zbApproval()` | 总部审批（HDS） |
| `ywsApproval()` | 运维商审批（商户通） |
| `gysApproval()` | 供应商审批（商户通） |
| `createLightLend()` | 建站借件订单创建 |
| `approvalLightLend()` | 建站服务商确认 |
| `cancel()` | 取消借件订单 |
| `repairsToRrsOrder()` | 传日日顺订单信息 |

---

## 2. 回购订单业务 (Back Order)

**来源**: `repairs-api` → `BackOrderStatusEnum.java`, `SpOrderBackService.java`

### 回购订单状态机 (8 种状态)

| 状态码 | 状态名 | 说明 |
|--------|--------|------|
| 0 | 初始 | — |
| 1 | 待分中心审核 | 回购单传入 CBS 系统，由中心经理-总部财务审核确认 |
| 2 | 待财务审核 | CBS 审核通过，中心经理、总部财务审核通过 |
| 3 | 待支付 | CBS 审核通过，中心经理、总部财务审核通过 |
| 4 | 审核驳回 | 运维商允许编辑，修改发票信息 |
| 5 | 打款提交 | 等待记账 |
| 6 | 收款成功 | 生成借件订单信息 |
| 7 | 收款失败 | — |

### CBS 交互

**来源**: `repairs-api` → `SpOrderBackService.java`

| 方法 | 说明 |
|------|------|
| `cbsApprovalOrder()` | CBS 审核回传回购订单审批 |
| `cbsOrderAccounting()` | CBS 接收记账信息 |
| `submitOrderPay()` | CBS 总部财务审核通过，上传打款附件 |

---

## 3. 旧件回退业务 (Oldback)

**来源**: `repairs-api` → `OldbackOrderStatusEnum.java`, `SpOldbackListsService.java`, `SpOldbackListsDetailService.java`

### 旧件回退状态机 (11 种状态)

| 状态码 | 状态名 |
|--------|--------|
| 0 | 初始 |
| 1 | 审批中 |
| 2 | 确认退返 |
| 3 | 厂家签收 |
| 4 | 厂家拒收 |
| 5 | 无需退返 |
| 6 | 审批通过 |
| 7 | 审批驳回 |
| 8 | 入库完成 |
| 9 | 超期未回退 |
| a | 撤销审批 |

### 判责业务

**来源**: `repairs-api` → `SpOldbackListsDetailService.java`

| 方法 | 说明 |
|------|------|
| `getSupplierPage()` | 供应商判责列表 |
| `judgeResponsibilityInfo()` | 保修判责详情 |
| `judgeResponsibilitySubmit()` | 保修判责-提交 |
| `providerAppeal()` | 运维商申诉 |
| `providerAdmittingResponsibility()` | 运维商认责 |
| `dutyAuditSubmit()` | 总部终审 |
| `autoJjudgeResponsibilityJob()` | 定时任务 — 运维商超时未处理自动判责 |
| `autoOldbackOverdueJob()` | 定时任务 — 超 30 天不回退默认超期未回退 |
| `autoSupplierWriteOffJob()` | 定时任务 — 供应商超时未处理自动销账 |

---

## 4. 逆变器维修业务 (Inverter Repair)

**来源**: `repairs-api` → `InverterStatusEnum.java`, `SpInverterInfoService.java`

### 逆变器维修状态机 (9 种状态)

| 状态码 | 状态名 |
|--------|--------|
| 0 | 初始 |
| 1 | 已提交 |
| 2 | 供应商通过 |
| 3 | 供应商驳回 |
| 4 | 运维商寄回 |
| 5 | 供应商签收 |
| 6 | 供应商发货 |
| 7 | 运维商签收 |
| 8 | 取消 |

### 逆变器维修流程

```
运维商创建申请 → 提交(1) → 供应商审批 → 通过(2)/驳回(3)
  → 运维商寄回(4) → 供应商签收(5) → 维修 → 供应商发货(6) → 运维商签收(7)
```

### Service 接口

**来源**: `repairs-api` → `SpInverterInfoService.java`

| 方法 | 说明 |
|------|------|
| `save()` | 新增逆变器维修申请 |
| `update()` | 更新 |
| `submitOrder()` | 提交订单 |
| `delete()` | 删除 |
| `withdrawn()` | 撤回 |
| `supplierApproval()` | 供应商审批 |
| `operationAndMaintenanceVendorsPost()` | 运维商邮寄 |
| `supplierSign()` | 供应商签收 |
| `supplierDelivery()` | 供应商发货 |
| `operationAndMaintenanceVendorsSign()` | 运维商签收 |

---

## 5. 仓储管理 (Warehouse)

**来源**: `repairs-api` → `CdWarehouseService.java`, `CdWarehouseRouteService.java`, `SpStoreageService.java`

### 仓储 Service

| Service | 核心方法 | 说明 |
|---------|----------|------|
| `CdWarehouseService` | `addCdWarehosue()`, `serviceProviderSyncJob()`, `serviceSupplierSyncJob()` | 仓库 CRUD + 服务商/供应商信息同步 |
| `CdWarehouseService` | `partsPaymentFlow()` | **备件款账单流水记录** — 记录订单交款/回退/认责等财务流水 |
| `CdWarehouseRouteService` | `queryRoute()` | 调出仓库列表 — 关联调拨圈，维护了就展示维护服务商 |
| `CdWarehouseAddressService` | `updateDefault()` | 修改默认仓库地址 |
| `SpStoreageService` | `getStoreageList()`, `getStoreageTotalList()` | 查询仓库可用库存/总库存 |
| `SpStoreageService` | `delete()`, `deleteBatchnum()` | 删除库存/按批次号删除 |
| `SpWarehouseAttachService` | `SynchronizeJob()` | 安全库存定时任务 |

### 备件款账单流水 (`partsPaymentFlow`)

**来源**: `repairs-api` → `CdWarehouseService.java`

参数: `orderCode`(业务订单号), `sourceId`(业务ID), `warehouseId`, `operType`(账单类型), `businessAmount`, `businessDesc`, `materialId`, `detailId`, `userInfo`

---

## 6. 财务与结算 (Finance)

**来源**: `repairs-api` → finance/ 目录下各 Service

### 6.1 服务商清欠 (SpAdvanceClearEntity)

**来源**: `repairs-api` → `SpAdvanceClearEntityService.java`, `AdvanceClearStatusEnum.java`

#### 清欠审批状态机 (9 种状态)

| 状态码 | 状态名 |
|--------|--------|
| 0 | 初始 |
| 1 | 已提交 |
| 2 | 中心通过 |
| 3 | 中心驳回 |
| 4 | 业务部通过 |
| 5 | 业务部驳回 |
| 6 | 财务通过 |
| 7 | 财务驳回 |
| 8 | 取消 |

#### 三级审批流程

1. **中心审批** → `centerApproval()` — 中心经理审核
2. **业务部审批** → `businessDepartmentApproval()` — 总部业务部审核
3. **财务审批** → `financeApproval()` — 财务审核

### 6.2 预付/交款 (SpAdvancePayment)

**来源**: `repairs-api` → `SpAdvancePaymentService.java`, `AdvanceStatusEnum.java`

| 状态码 | 状态名 |
|--------|--------|
| 0 | 初始 |
| 1 | 已提交 |
| 2 | 交款成功 |
| 3 | 交款失败 |
| 4 | 审批通过 |
| 5 | 审批驳回 |
| 6 | 退款成功 |
| 7 | 退款失败 |

### 6.3 应付账款 (SpAccountsPayable)

**来源**: `repairs-api` → `SpAccountsPayableService.java`

| 方法 | 说明 |
|------|------|
| `monthStartAccountsPayableJob()` | 月初统计应付账款定时任务 |
| `monthStartAccountsPayable()` | 指定统计某月账单 |
| `confirmSettle()` | 确认账单 |
| `saveContractInfo()` / `updateContractInfo()` | 应付账单合同信息保存/更新 |
| `getSignUrl()` | 商户通获取电签链接 |
| `getBillUrl()` | 获取账单链接 |
| `requestPayment()` | 应付账单请款 |
| `signCallback()` | 签章回调流程 |
| `updateSettleStatus()` | 定时更新付款状态 |

### 6.4 应收账款 (SpAccountsReceivable)

**来源**: `repairs-api` → `SpAccountsReceivableService.java`

| 方法 | 说明 |
|------|------|
| `monthStartAccountsReceivableJob()` | 月初统计应收账款定时任务 |
| `monthStartAccountsReceivable()` | 指定统计某月账单 |
| `confirm()` | 确认账单 |
| `getSignUrl()` | 商户通获取电签链接 |
| `signCallback()` | 签章回调流程 |

### 6.5 SAP 记账 (SpSapAccount)

**来源**: `repairs-api` → `SpSapAccountService.java`, `SapBillTypeEnum.java`

#### SAP 业务类型

| 业务类型码 | 名称 | 说明 |
|------------|------|------|
| B07 | 入库记账 | — |
| B25 | 领用记账 | — |
| B23 | 扣除押金记账 | 运维商责任 |
| B24 | 厂家责任记账 | 供应商责任 |

| 方法 | 说明 |
|------|------|
| `addSpSapAccountTranSn()` | 新增 SAP 信息（调拨/服务订单） |
| `addSpSapAccountTranSnDetailSh()` | 货损插销时新增 SAP 信息 |
| `addSpSapAccountOldbackListsDetail()` | 旧件回退作废新增 SAP 信息 |
| `addSpSapAccountOldbackListsDetailBySummaryNo()` | 按应收汇总单号获取明细新增 SAP |
| `sendSapByOrderNo()` | 单条同步 SAP 信息 |
| `synchronizationSapAccountJob()` | 同步 SAP 信息定时任务 |

### 6.6 保外收入统计

**来源**: `repairs-api` → `SpSettlementDataService.java`

| 方法 | 说明 |
|------|------|
| `warrantIncomeCountJob()` | 保外收入数据统计定时任务 |

---

## 7. Flowable 工作流集成

**来源**: `repairs-api` → `flowable/` 目录

### 工作流 Service 接口

| Service | 说明 |
|---------|------|
| `IWfCategoryService` | 流程分类管理 |
| `IWfModelService` | 流程模型管理（创建/编辑/部署/版本） |
| `IWfFormService` | 表单管理 |
| `IWfDeployService` | 流程部署管理 |
| `IWfDeployFormService` | 流程实例关联表单 |
| `IWfProcessService` | 流程实例管理（启动/查询/删除） |
| `IWfTaskService` | 任务管理（审批/拒绝/退回/认领/转办/委派/撤回） |
| `IWfInstanceService` | 流程实例管理（结束/挂起/删除） |
| `IWfCopyService` | 流程抄送 |

### 任务操作

**来源**: `repairs-api` → `IWfTaskService.java`

| 操作 | 方法 |
|------|------|
| 审批 | `complete()` |
| 拒绝 | `taskReject()` |
| 服务商撤回 | `taskRejectWarehouse()` |
| 退回 | `taskReturn()` |
| 获取可回退节点 | `findReturnTaskList()` |
| 删除任务 | `deleteTask()` |
| 认领/签收 | `claim()` |
| 取消认领 | `unClaim()` |
| 委派 | `delegateTask()` |
| 转办 | `transferTask()` |
| 取消申请 | `stopProcess()` |
| 撤回流程 | `revokeProcess()` |

---

## 8. 日日顺(RRS)集成

**来源**: `repairs-api` → `RepairsAndRrsService.java`, `RrsBackStatusEnum.java`, `InterfaceNameEnum.java`, `InterfaceMethodNameEnum.java`

### 接口交互方向

| 方向 | 编码 | 说明 |
|------|------|------|
| 被其他系统调用 | BDY-QT | — |
| 光伏备件调用日日顺 | REPAIRS_RRS | 下发订单/取消/拦截 |
| 日日顺调用光伏备件 | RRS_REPAIRS | 状态回传/出入库流水 |
| 光伏备件调用建站 | REPAIRS_JZ_SAP | 建站系统交互 |
| 光伏备件调用 GVS | REPAIRS_GVS | GVS 库存查询 |

### 接口方法

| 方法码 | 名称 |
|--------|------|
| BJKHD | 备件款收款回调 |
| rrs_statusback | RRS 订单状态/节点回传 |
| rrs_outinstore | RRS 出入库流水 |
| rrs_productdata | 产品主数据 |
| rrs_reject | 确认出入库 |
| rrs_order | 用户下发订单 |
| rrs_cancel | 用户取消订单 |
| rrs_intercept | 用户拦截订单 |
| sapLedger | SAP 记账 |
| GVS | GVS 库存 |

### 日日顺回传状态

**来源**: `repairs-api` → `RrsBackStatusEnum.java`

| 状态码 | 含义 |
|--------|------|
| WMS_ACCEPT | 接单 |
| CR | 订单已创建 |
| CK | 出库 |
| PC | 配车 |
| JS | 拒收 |
| QS | 签收 |
| FD | 返单 |
| RK | 入库 |
| ZP | 货损附件 |

### 核心交互方法

**来源**: `repairs-api` → `RepairsAndRrsService.java`

| 方法 | 说明 |
|------|------|
| `receiveRrsOrderInfo()` | 日日顺回调 — 接收订单信息 |
| `receiveRrsOrderStatus()` | RRS 订单状态回传 |
| `receiveRrsOrderOutinStore()` | RRS 出入库流水 |
| `receiveRrsOrderReject()` | RRS 确认出入库 |
| `repairsToRrsOrder()` | 下发订单到日日顺 |
| `repairsToRrsOrderTransfer()` | 中心仓调拨出库下发 |
| `repairsToRrsOldbackList()` | 运维商呆滞回退审批流程下发 |
| `repairsToRrsCancelOrder()` | 取消订单 |
| `repairsToRrsInterceptOrder()` | 拦截订单 |
| `repairsToRrsProductdata()` | 产品主数据接口 |

---

## 9. 快递100 集成

**来源**: `repairs-api` → `SpExpressRoutingService.java`

| 方法 | 说明 |
|------|------|
| `QueryTrack()` | 订阅快递单号查询 |
| `expressCallback()` | 快递100 订阅回调 |

---

## 10. GVS 下发任务

**来源**: `repairs-api` → `SpIssueJobLogService.java`, `IssueJobLogEnum.java`

### 下发日志枚举

| 系统 | 代码 | 说明 |
|------|------|------|
| GVS | 1 | 释放库存 |

| 方法 | 说明 |
|------|------|
| `issueGvsJob()` | GVS 下发数据定时任务 |
| `issueJob()` | 按方法类型+订单号下发数据 |
| `insertOrUpdate()` | 根据类型及订单号插入或更新数据 |
| `gvsOrderDateOrderBack()` | 回购单调用 GVS 释放库存存入 job |

---

## 11. 订单主业务 (Order)

**来源**: `repairs-api` → `SpOrderService.java`

| 方法 | 说明 |
|------|------|
| `save()` / `update()` / `delete()` | 订单 CRUD |
| `importSave()` | 导入新增订单 |
| `submitOrder()` | 提交订单 |
| `serviceCancelOrder()` | 服务订单取消 |
| `singleCancel()` | 单件取消 |
| `ordeMatching()` | 订单匹配 |
| `ordeMatchingJob()` | 订单匹配定时任务 |
| `createRepairOrder()` | 创建维修工单 |
| `addServicePIT()` / `updateServicePIT()` / `submitServicePIT()` | 服务商库存调拨 |
| `approvalServicePIT()` | 服务商库存调拨审批 |
| `approvalServiceCenterPIT()` | 中心仓调拨审批 |
| `addRrsBuyLoss()` / `updateRrsBuyLoss()` / `submitRrsBuyLoss()` | 日日顺买损 |
| `nodeInfo()` | 获取当前订单节点信息 |
| `ordeDetailMatching()` | 匹配库存 |

---

## 12. 基础数据管理

**来源**: `repairs-api` → `base/` 目录

| Service | 说明 |
|---------|------|
| `CdBranchInfoService` | 分中心信息管理 |
| `CdDictDataService` | 字典数据管理 |
| `CdFileService` | 文件管理（备件属性、工单备件登记、出入库、借件入库、调拨等文件类型） |
| `CdMaterialService` | 物料主数据管理 — 同步日日顺备件信息 |
| `CdMaterialSubstituteService` | 物料替代管理 |
| `CdMaterialWarrantService` | 物料质保管理 |
| `CdPosService` | 库位管理 |

### 文件类型枚举

**来源**: `repairs-api` → `FIleTypeEnum.java`

| 编码 | 类型 |
|------|------|
| BJSX | 备件属性 |
| GDBJDJ | 工单备件登记 |
| FWDCK | 服务订单出入库、货损货差 |
| JJRK | 借件入库 |
| CBKDB | 储备库调拨订单 |
| FWD_BJSQ | 服务订单-备件申请 |
| loadTtruckPic | 储备调拨-装车照片 |
| signInPic | 储备调拨-组件入库签收单 |
| warehousingPic | 储备调拨-入库存放照片 |
| TFK_GYSPZ | 退返件-供应商判责 |
| qualityInspect_inout | 采购质检-入库 |
| inverterInfo | 逆变器维修 |
| rrs_statusback | RRS 订单状态/节点回传 |

---

## 13. 定时任务汇总

| 任务 | Service | 说明 |
|------|---------|------|
| 订单匹配 | `SpOrderService.ordeMatchingJob()` | 自动匹配订单库存 |
| GVS 下发 | `SpIssueJobLogService.issueGvsJob()` | GVS 释放库存 |
| SAP 同步 | `SpSapAccountService.synchronizationSapAccountJob()` | 同步 SAP 记账信息 |
| 月初应付统计 | `SpAccountsPayableService.monthStartAccountsPayableJob()` | 月初统计应付账款 |
| 月初应收统计 | `SpAccountsReceivableService.monthStartAccountsReceivableJob()` | 月初统计应收账款 |
| 付款状态更新 | `SpAccountsPayableService.updateSettleStatus()` | 定时更新付款状态 |
| 保外收入统计 | `SpSettlementDataService.warrantIncomeCountJob()` | 保外收入数据统计 |
| 安全库存同步 | `SpWarehouseAttachService.SynchronizeJob()` | 安全库存定时任务 |
| 物料同步 | `CdMaterialService.synchronousRrsMaterialJob()` | 同步日日顺备件信息（物料主数据） |
| 服务商同步 | `CdWarehouseService.serviceProviderSyncJob()` | 服务商信息同步 |
| 供应商同步 | `CdWarehouseService.serviceSupplierSyncJob()` | 供应商信息同步 |
| 自动判责 | `SpOldbackListsDetailService.autoJjudgeResponsibilityJob()` | 运维商超时未处理自动判责 |
| 旧件超期 | `SpOldbackListsDetailService.autoOldbackOverdueJob()` | 超 30 天不回退默认超期未回退 |
| 供应商销账 | `SpOldbackListsService.autoSupplierWriteOffJob()` | 供应商超时未处理自动销账 |

---

## 14. 数据库表汇总 (从代码推断)

**来源**: MyBatis Mapper XML + Entity 类扫描

### 核心表

| 表名 | 说明 | 主要 Mapper |
|------|------|-------------|
| `sp_order` | 订单主表 | `SpOrder.xml` |
| `sp_order_detail` | 订单明细 | `SpOrderDetail.xml` |
| `sp_order_borrow` | 借件订单主表 | — |
| `sp_order_borrow_sn` | 借件订单 SN | — |
| `sp_order_back` | 回购订单 | — |
| `sp_oldback_lists` | 旧件回退汇总单 | — |
| `sp_oldback_lists_detail` | 旧件回退明细 | — |
| `sp_tran_sn` | 调拨 SN | — |
| `sp_tran_sn_detail_sh` | 调拨 SN 明细货损 | — |
| `sp_storeage` | 库存表 | `SpStoreage.xml` |
| `sp_purchase` | 采购单 | `SpPurchase.xml` |
| `sp_purchase_detail` | 采购明细 | — |
| `sp_foregift` | 押金/保证金 | `SpForegift.xml` |
| `sp_accounts_payable` | 应付账款 | — |
| `sp_accounts_payable_detail` | 应付明细 | — |
| `sp_accounts_receivable` | 应收账款 | — |
| `sp_accounts_receivable_detail` | 应收明细 | — |
| `sp_accounts_dcc` | 账单合同 | — |
| `sp_advance_payment` | 预付款/交款 | — |
| `sp_advance_clear_entity` | 服务商清欠 | — |
| `sp_sap_account` | SAP 记账 | — |
| `sp_settlement_data` | 结算数据 | — |
| `sp_inverter_info` | 逆变器维修申请 | — |
| `sp_inverter_sn_info` | 逆变器 SN | — |
| `sp_express_company` | 快递公司 | — |
| `sp_express_routing` | 快递轨迹 | `SpExpressRouting.xml` |
| `sp_routing_log` | 路由日志 | — |
| `sp_warehouse_attach` | 安全库存设置 | — |
| `sp_storeage_log` | 库存日志 | — |
| `sp_issue_job_log` | 下发任务日志 | — |
| `cd_warehouse` | 仓库主数据 | `CdWarehouse.xml` |
| `cd_warehouse_route` | 仓库调拨路线 | `CdWarehouseRoute.xml` |
| `cd_warehouse_address` | 仓库地址 | — |
| `cd_warehouse_center` | 仓库中心 | — |
| `cd_material` | 物料主数据 | `CdMaterial.xml` |
| `cd_material_substitute` | 物料替代 | `CdMaterialSubstitute.xml` |
| `cd_material_warrant` | 物料质保 | `CdMaterialWarrant.xml` |
| `cd_dict_data` | 字典数据 | `CdDictData.xml` |
| `cd_branch_info` | 分中心信息 | `CdBranchInfo.xml` |
| `cd_pos` | 库位 | `CdPos.xml` |
| `cd_file` | 文件 | `CdFile.xml` |
| `light_service_provider` | 服务商信息 | — |
| `wo_part` | 工单备件 | `WoPart.xml` |

---

## 15. 近期变更记录 (2026-05)

| 日期 | 变更 | 提交人 |
|------|------|--------|
| 2026-05-21 | 发货查询使用强制索引提高效率 | A0026566 |
| 2026-05-13 | 工单备件网单号字段类型修改 String | A0026566 |
| 2026-05-12 | woPart.id 字段从 long 改为 String，解决 long 值转 String 丢失精度 | A0026566 |
| 2026-05-07 | 订单入库添加 null 值检查 | A0026566 |
| 2026-04-29 | 下发日日顺的组件订单不指定 SN 出库 | A0026566 |

---

## 来源

- `repairs` 全量通读 2026-05-22 (第9轮)
- 代码明确证明: `repairs-api/` 下所有 Service 接口、Entity 类、Enum 类
- 证据等级: **代码明确证明** (直接读取源代码)
