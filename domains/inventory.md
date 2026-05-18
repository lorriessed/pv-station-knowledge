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

## 待确认
- 各调拨类型对应库存扣减和在途库存规则。
- 商内调拨与普通调拨的财务/权限差异。
- 组件订单不指定SN出库后，后续追溯和质保如何管理。

## 来源
- Hermes MEMORY.md，2026-05-09 迁移。
- repairs 代码扫描 2026-05-10，日日顺出库和备件网单号变更。
