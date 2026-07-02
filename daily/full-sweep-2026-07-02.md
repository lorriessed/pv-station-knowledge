# PVS 全量代码通读报告 — 2026-07-02 (第46轮)

## 通读概况

| 仓库 | 最后提交 | 业务文件数 | 状态 |
|---|---|---|---|
| rrsjk-trade-service | 2026-07-01 | 571 | ✅ 重扫，有新变更 |
| system-service | 2026-05-20 | 62 | ✅ 重扫，有新变更 |
| uni-choose-file-android | 2026-02-03 | 14 | ✅ 外围 Android SDK，无 PVS 业务 |
| uni-choose-file-ios | 2026-01-20 | 0 | ✅ 外围 iOS SDK，空仓库 |
| vpp-api-auth | 2025-03-10 | 27 | ✅ 重扫，无新变更（KB 已全覆盖） |

## 关键业务发现

### 1. 储能订单推送条件收紧 (rrsjk-trade-service, 2026-07-01)
- **commit**: 03a0b6e0 (laowang)
- **变更**: `LightPurchaseSalesPurchaseOrderServiceImpl.java` 中储能订单推送条件从仅检查 `supplierCode == "V99694"` 改为同时检查 `supplierCode == "V99694" AND companyCode == "1QJ0"`
- **影响**: 只有公司 1QJ0 的供应商 V99694 订单才会推送到储能系统
- **KB 更新**: `domains/order-and-trade.md` §订单推送队列

### 2. 零碳套餐库存手动下调 — Trade Service 入口 (rrsjk-trade-service, 2026-06-17, TAEI-3144)
- **commit**: 35a02481 (代继宁)
- **新增接口**: `LightPurchaseSalesOrderService.reduceSetMealPlanStock(setMealCode, orderNo, quantity)`
- **调用链**: reduceSetMealPlanStock → SetMealStockOperate.setMealStock → ZeroCarbonItemSetMealStockService.updateStock
- **changeType=3**: 手动下调走与下单扣减 (changeType=1) 相同的 updateStock 路径
- **KB 更新**: `domains/zero-carbon-station.md` §零碳套餐库存手动下调

### 3. 零碳发票重推 — 订单号列表更新 (rrsjk-trade-service, 2026-06-26)
- **commit**: 5e837a0e (baoxin)
- **变更**: CloudInvoiceCreateModel/CloudInvoiceQueryModel 中硬编码的待重推订单号列表更新为新一批 (LPSOI260513/LPSOI260525/LPSOI260526 系列)
- **性质**: 临时运维操作，非业务逻辑变更，不写入 KB

### 4. 分中心管理批量操作重构 (system-service, 2026-05-19~20)
- **commits**: e8d2b21/be46e83/3236e0c/b19a9f6/fc0aedb (德)
- **变更**:
  - SubCenterUserDTO 实现 Serializable
  - 批量操作接口从 userId 列表重构为 SubCenterUserDTO 列表（含 userName/mobile）
  - 新增 batchAddUsers/batchRemoveUsers/setMembers 方法
  - SysSubCenter 实体移除软删除字段
- **KB 更新**: `domains/cbs-management.md` §分中心管理 Service 表

### 5. 微智慧开票测试环境地址 (rrsjk-trade-service, 2026-06-25)
- **commit**: dcff5acf (解钦)
- **变更**: application-dev.yml 中微智慧开票 URL 更新
- **性质**: 环境配置变更，不影响生产，不写入 KB

## 外围仓库快速分类

| 仓库 | 分类 | 理由 |
|---|---|---|
| uni-choose-file-android | 外围移动端 SDK | Android 文件选择器 + BLE OTA 功能，HaierEnergyNative 应用组件，非 PVS 核心业务 |
| uni-choose-file-ios | 外围移动端 SDK | 空仓库，仅 1 个初始化 commit |
| vpp-api-auth | VPP 认证服务 | JWT Token 管理 + DrCloud 第三方 Token 接口，KB 已全覆盖（vpp-overview.md），最后提交 2025-03 |

## KB 更新汇总

| 文件 | 操作 | 新增内容 |
|---|---|---|
| `domains/order-and-trade.md` | patch | 储能订单推送触发条件 (V99694 + 1QJ0) |
| `domains/zero-carbon-station.md` | patch | 零碳套餐库存手动下调 Trade Service 入口 + 调用链 |
| `domains/cbs-management.md` | patch | SysSubCenterService 批量操作方法 + SubCenterUserDTO 序列化 + 软删除移除 |

## 统计
- 通读仓库: 5 个
- 有业务变更: 2 个 (rrsjk-trade-service, system-service)
- 外围跳过: 3 个 (uni-choose-file-android, uni-choose-file-ios, vpp-api-auth)
- KB 文件更新: 3 个
- 新增业务规则: 3 条
