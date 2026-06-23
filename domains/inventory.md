# 仓储与调拨

更新时间: 2026-05-10

## 已确认知识

### 调拨类型
仓储调拨已知 5 种类型：ORDINARY_TRANSFER 普通调拨、FROM_TRANSIT 中转仓发货、FROM_TRANSIT_TO_TRANSIT 中转仓调中转仓、REPAIR_TRANSFER 备件调拨、INTERNAL_TRANSFER 商内调拨。

### 调拨状态机
主状态机：WAIT_AUDIT -> WAIT_TRANSFER -> TRANSFERED -> COMPLETED。

### 审核状态机
审核状态机：INIT -> WAIT_OPERATION_AUDIT -> WAIT_SUPPLY_CHAIN_AUDIT -> FINISHED。

### 日日顺组件出库规则变更 (2026-04-29)
- **来源**: repairs, `RepairsAndRrsServiceImpl.java`, commit 1bda3e4 (A0026566, 2026-04-29)
- 下发日日顺的**组件订单不再指定SN码出库**，原SN传递逻辑被整体注释掉
- 原因：20260429韩程需求
- 补库类订单SN码存在StoreageList中、维修类借件申请SN码存在batchNum中的逻辑均被注释

### 备件网单号类型变更 (2026-04-28 → 2026-05-13 再次变更)
- **来源**: repairs, `WoPartDao.java`/`OrderWoPart.java`/`WoPartServiceImpl.java`, commits fbd53f4/5ce1f03/db702cd + 1149a9fe
- WoPart 表主键 `getById` 方法参数从 `Long` 改为 `String`
- `selectIdByWoIdIncrement()` 返回类型从 `Long` 改为 `String` (2026-05-13)
- 备件网单号改为取工单的去除字母后的数据
- 小象工单生成规则优化网单号生成序列

### 工单维修代码清理 (2026-05-13)
- **来源**: `repairs` → `SpOrderServiceImpl.java`, `SpTranSnServiceImpl.java`, `WoPartServiceImpl.java` (commit 1149a9fe, 徐勇, 2026-05-13)
- 删除 `createRepairOrderForXiaoXiang` 方法 (226行)
- 删除 `SpTranSnServiceImpl` 相关代码 (162行)
- 移除 `rrsjk-light-data-api` 依赖
- `WoPartServiceImpl` 大幅精简 (241行 → 精简)

### 辅材额度流水
辅材额度已知 4 类流水：S3 保证金总额和可用额度增加；S8 下单时可用额度减少、冻结额度增加；S11 签收时冻结额度减少、签收额度增加；D13 核销时可用额度增加、已核销额度增加。

### 完工前领用单 (LightUseOrder)
**来源**: rrsjk-merchant-web → `LightUseOrderController.java`
- 路径: `/lightUseOrder/`
- 功能: 服务商视角的完工前物料领用管理
- 接口:
  - `completeBeforeDoList.do` - 完工前领用列表 (按电站编码/业主姓名/领用状态筛选)
  - `completeBeforeExport.do` - 导出Excel (3000条/页)
  - `manualOutStock.do` - 服务商手动出库 (防重复提交: 10秒间隔)
- 权限校验: 需要 OAuth2 认证，通过 memberId 构建权限条件
- 导出字段: 电站编码、业主姓名、电话、省市区、地址、SKU编码/名称、数量、电站状态、领用状态、凭证时间、备注

### 领用异常队列 (LightUseQueue)
**来源**: rrsjk-merchant-web → `LightUseQueueController.java`
- 路径: `/lightUseQueue/`
- 功能: 领用异常列表查询与导出
- 查询条件: 电站编码、创建时间范围、处理状态 (success: 0=待处理, 1=已处理)
- 通过 `getAllStationCodeByMemberId()` 按会员权限过滤电站范围

### 采购与物料管理 (repairs, 2026-05-22 代码明确证明)
- **来源**: `repairs` → `CdMaterialService.java`, `SpPurchaseService.java`, `CdMaterialSubstituteService.java`
- **物料主数据同步**: `CdMaterialService.synchronousRrsMaterialJob()` 定时同步日日顺备件信息（物料主数据）
- **物料替代**: `CdMaterialSubstituteService` 管理物料替代关系
- **物料质保**: `CdMaterialWarrantService` 管理物料质保期
- **采购单**: `SpPurchaseService` — 新增/编辑/提交/删除采购单
- **安全库存**: `SpWarehouseAttachService.SynchronizeJob()` 定时同步安全库存

### 备件款账单流水 (repairs, 2026-05-22 代码明确证明)
- **来源**: `repairs` → `CdWarehouseService.partsPaymentFlow()`
- 记录订单交款/回退/认责等财务流水
- 参数: `orderCode`(业务订单号), `sourceId`(业务ID), `warehouseId`, `operType`(账单类型), `businessAmount`, `businessDesc`, `materialId`, `detailId`, `userInfo`

### 库存管理 (repairs, 2026-05-22 代码明确证明)
- **来源**: `repairs` → `SpStoreageService.java`, `SpStoreage.java`
- `getStoreageList()` — 查询仓库可用库存
- `getStoreageTotalList()` — 查询仓库总库存
- `delete()` / `deleteBatchnum()` — 删除库存/按批次号删除

### 仓库调拨路线 (repairs, 2026-05-22 代码明确证明)
- **来源**: `repairs` → `CdWarehouseRouteService.java`
- `queryRoute()` — 调出仓库列表，关联调拨圈，如果维护了就展示维护服务商，没有维护则返回空

### 完工前领用物料状态 (前端配置证明, 2026-05-22 扫描)
**来源**: `nahui-dicts-serve` → `src/data/apv/store/useStatusList.js` (袁睿林, 2026-03-19)
|- 新增出库管控(完工前领用)页面物料领用状态数据字典
- 关联接口: `rrsjk-merchant-web` → `LightUseOrderController.completeBeforeDoList.do`

### 服务商入库附件保存与供应商审核附件展示 (前端变更, 2026-05-26)
**来源**: `nahui-pv.merchant-micro.osp` → `src/views/ospSpare/stockManage/damageListSupplier/addEditPop.vue`, `src/views/ospSpare/stockManage/serviceStock/addEditPop.vue` (A0026566, commit 376e0e0b, 2026-05-26)
- OSP商户端备件管理: 服务商入库新增附件保存功能
- 供应商审核页面增加附件展示
- 97行变更: 2个Vue组件修改

### 领用逻辑优化 — 库龄分析报表 (代码明确证明, 2026-05-23 补漏第7期)
**来源**: `rrsjk-light-report-service`, `rrsjk-admin-web` (TAEI-2957, 解钦, 2026-03-27~03-30)
- 新增已领料未完工材料库龄分析报表
- 报表新增字段: 公司、品牌、物料组、产品组
- 领用明细列表重构 (origin/xq-feature-use-deal-history)
- 领用单新增 `completeFlag` 字段 — 用于确认完工前领用是否完工
- 完工前领用处理历史电站数据 (含定时任务)
- 完工节点兼容出库事务执行的逻辑变化，电站终止逻辑同步变更

## 待确认
|- 各调拨类型对应库存扣减和在途库存规则。
|- 商内调拨与普通调拨的财务/权限差异。
|- 组件订单不指定SN出库后，后续追溯和质保如何管理。
|- 发货后的快递签收与 WMS 系统交互的完整状态机。

## 电站转单功能 (代码明确证明, 2026-05-29)
**来源**: `rrsjk-light-service` → `LightStationTransferOrder.java`, `LightStationTransferOrderDao.java`, `LightStationTransferOrderServiceImpl.java`, `LightStationTransferOrder.xml`, `LightStationTransferOrderLog.xml` (commits: 德, 2026-05-29, branch: station-transfer-sub-account-20260525)
**前端**: `nahui-pv.mobile-h5` → `src/views/apv/transferOrder/index.jsx`, `src/api/apv.js`, `src/router/modules/apv.jsx` (commits: yanghui, 2026-05-29)
- **实体**: `LightStationTransferOrder` — 电站转单主表，包含负责人/承接商名称查询
- **前端页面**: 移动H5新增 `/apv/transferOrder` 路由，转单管理页面（193行新增）
- **API**: `src/api/apv.js` 新增转单相关接口（15行新增）
- **Mapper**: 新增按负责人或承接商名称查询功能，修复id问题
- **LightStation实体变更**: 转单功能修改涉及 `LightStation.java` 字段调整
- **子中心查询**: 转单功能添加子中心列表查询条件
- **证据等级**: 代码明确证明

## 关联文件
- **下单-配货-发货全链路**: `domains/order-dispatch-delivery.md` — 方案审核通过后的下单、配货、发货、仓库、库存、额度的完整业务流程（2026-05-24 新增）
- 调拨类型/状态机/审核状态机仍保留在本文件

### 备件借件订单自提与无组件SN原因 (2026-06-10)
**来源**: `nahui-pv.merchant-micro.osp` (A0026566, commits: dfab290/cfb5b2a/3a2f266, 2026-06-10)
**证据等级**: 前端配置证明
- **组件订单详情**: 新增 `是否自提` 字段展示、`特殊原因` 字段展示
- **组件订单保存**: 建站商和中心仓出库都可以录入无组件SN原因
- **借件订单**: 新增保存取分中心逻辑调整
- **涉及页面**: `src/views/ospSpare/orderManage/lendOrder/details.vue`、`addEditPop.vue`
- **配套后端**: `repairs` 同步新增中心仓出库备件 SAP 记账重传接口（见 `domains/settlement.md`）

### HDS 借件订单自提字段与报表下载 (2026-06-10)
**来源**: `nahui-pv.hds-h5` (李培龙/A0026566, commits: d00f9f0/2dd10cd/6b36f5e, 2026-06-10)
**证据等级**: 前端配置证明
- **借件订单详情**: 增加 `是否自提` 字段展示 (`sparePartMonitor/lendOrderAudit/components/detailComponent.vue`)
- **报表**: 新增户用业绩报表下载、优化报表展示与下载逻辑 (`reports/board.vue`)

## 来源
- Hermes MEMORY.md，2026-05-09 迁移。
- repairs 代码扫描 2026-05-10，日日顺出库和备件网单号变更。

---

### 中心仓出库备件供应商编码改日日顺 + SO发货失败重传 (2026-06-11)
**来源**: `repairs/SpOrderBorrowServiceImpl.java` + `SpTranSnServiceImpl.java` (A0026566, commit 5d6c10b7, 2026-06-11) + `rrsjk-hds-web/SpOrderBorrowController.java` (16bbaaef, 2026-06-11)
**证据等级**: 代码明确证明

**变更**:
1. **供应商编码**: 中心仓出库备件创建 SO 发货时，供应商编码从原值改为传**日日顺编码**
   - 涉及: `SpOrderBorrowService.java`, `SpTranSnService.java` 及其 Impl
2. **SO发货失败重传接口**: 新增手工重传接口，用于 SO 发货失败后重新提交
   - HDS 端入口: `SpOrderBorrowController` 新增重传 endpoint
   - 业务场景: SAP 记账失败后运维人员可手动触发重传，无需开发介入

### 逆变器变更控制器权限优化 (2026-06-11)
**来源**: `rrsjk-hds-web/LightStationInverterChangeController.java` (sunzn/于淼, commits d0370d9/b7ecaab, 2026-06-11)
**证据等级**: 代码明确证明
- 优化用户权限处理逻辑，移除未使用代码

### 光伏调拨入库前端字典体系 (前端配置证明, 2026-06-09)
**来源**: `nahui-dicts-serve/src/data/apv/store/` (yuanruilin, commit 77cef18, 2026-06-09)
**新增 4 个字典文件**，对应光伏仓储调拨模块的前端展示层：

**调拨签收单状态** (`signStoreStatus.js`):
- WAIT_AUDIT 待审核 → AUDIT_OK 已审核 / AUDIT_REJECT 已驳回 → CONTRACT_SIGNED 已签 / CONTRACT_NOT_SIGNED 未签

**调拨仓库状态** (`storeStatus.js`):
- WAIT_SEND_GOODS 待发货 → WAIT_DELIVERY 待上传送货单 → WAIT_IN 待签收 → FINISHED 已签收 (可 CANCELED 已取消)

**调拨单状态** (`transferStatusList.js`):
- WAIT_TRANSFER 待调出 → TRANSFERED 已调出 → COMPLETED 调拨完成 (可 CANCELED 已取消)

**调拨单类型** (`transferTypeList.js`):
- ORDINARY_TRANSFER 普通调拨
- FROM_TRANSIT 中转仓发货

> 注: 后端调拨类型已知 5 种 (ORDINARY_TRANSFER/FROM_TRANSIT/FROM_TRANSIT_TO_TRANSIT/REPAIR_TRANSFER/INTERNAL_TRANSFER)，前端此处仅展示 2 种，说明光伏调拨入库模块当前仅支持普通调拨和中转仓发货两种场景。

### 零碳采购单 SKU 类型枚举 (代码明确证明, 2026-06-15)
**来源**: `rrsjk-trade-service/LightPurchaseSalesPurchaseOrder.java` (包鑫, commit 96324f57, 2026-06-15)
- **SkuTypeEnum** — 零碳采购销售单 SKU 类型:
  - MODULE 组件 / INVERTER 逆变器 / OPTIMIZER 优化器 / INTELLIGENT_SOCKET 智能插座
  - STORAGE_BATTERY 储能 / AUXILIARY_MATERIAL_PACKAGE 辅材包 / DATA_GATEWAY 数据网关
  - REVERSE_FLOW_METER 防逆流电表 / CHARGING_PILE 充电桩
- **新增字段**: customerCode/customerName (客户), subCenterCode/subCenterName (分中心)

---

## 旧件回退整合接口 updateAndConfirmReturn (代码明确证明, 2026-06-23)

**来源**: `repairs` → `SpOldbackListsServiceImpl.java` (commit: 1b39807, A0026566, 2026-06-23)

### 接口定义
`SpOldbackListsService.updateAndConfirmReturn(SpOldbackLists, String userName)` → `ExecuteResult`

### 业务流程
将"编辑物流信息"和"确认退返"合并为单一事务接口，减少前端调用次数。

1. **基础校验**: 订单ID非空
2. **物流信息校验**: 快递单号 6~32 字符
3. **回退单类型校验**: backType ∈ {1(旧件回退), 7(旧件报废), 9(无旧件返还)}
4. **回退单状态校验**: backStatus ∈ {0(初始), 4}
5. **明细校验**: 实际退返数量 ≤ 应退返数量
6. **服务商报废校验** (backType=7): 确认回退数量 ≥ 应回退数量
7. **快递100推送**: 物流公司+单号非空时推送快递订阅，记录 expressDate/expressErult/expressStatus
8. **事务操作**:
   - 更新回退单明细（支持传入明细或使用数据库已有明细）
   - 更新主单: backStatus=2(已退返), backDate, backapplyDate
   - backType=7 时调用 `coreReceipt2()` 备件退返签收

### 关键变更
- **注释掉库存删除逻辑**: 原 `confirmReturn` 中按仓库id+备件id+旧件唯一码查询库存并删除（备份至 sp_storeage_del）的逻辑被注释掉。新接口不再在确认退返时直接删除库存。
- **前端配合**: `nahui-pv.merchant-micro.osp` 的 `returnStockOut/addEditPop.vue` 同步新增保存并提交功能

### 相关表
- `sp_oldback_lists` — 旧件回退单主表
- `sp_oldback_lists_detail` — 旧件回退单明细
- `sp_storeage` / `sp_storeage_del` — 库存表 / 库存删除备份表
