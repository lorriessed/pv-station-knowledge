# PVS 全量代码通读报告 2026-06-25 (第41轮)

## 通读概况

| 指标 | 值 |
|---|---|
| 仓库总数 | 138 |
| 本轮通读 | 5 个 |
| 从未通读 | 0 个 |
| 全轮跳过(零提交) | 4 个 |
| 有新增知识 | 1 个 |

## 通读仓库详情

### 1. rrsjk-merchant-h5
- **分支**: master | **HEAD**: f163bce8af22
- **最后提交**: 2026-06-25 (今天)
- **业务文件数**: 3 (仅 openspec 配置文件)
- **结论**: 纯前端 H5 项目，本次扫描仅捕获 openspec YAML 配置，无业务逻辑变更
- **处理**: 跳过，更新时间戳

### 2. rrsjk-merchant-service
- **分支**: master | **HEAD**: c10af9f5f82c
- **最后提交**: 2025-10-23 (8个月前)
- **业务文件数**: 182
- **结论**: 零提交跳过。已有完整文档(494行 merchant-service.md)，覆盖企业客户/押金/牛人客户/工商业/驿站/配送/供应商/MDM等全部模块
- **处理**: 跳过，更新时间戳

### 3. rrsjk-merchant-web ⭐
- **分支**: master | **HEAD**: e0a582b2c815
- **最后提交**: 2026-06-25 (今天)
- **业务文件数**: 418
- **结论**: 活跃开发中。349个Controller文件，已有351条路由索引
- **新增知识**:
  - `ZeroCarbonItemSetMealStockController` 新增2个接口:
    - `GET /zerocarbon/itemSetMealStock/getSetMealInfoByKeyword` — 关键字查询套餐库存
    - `POST /zerocarbon/itemSetMealStock/reduceStock` — 手动下调套餐库存 (TAEI-3144)
  - 逆变器数据合并逻辑优化 (commit: 89a62f9f4, wangxiran)
  - 领用相关权限调整 (commit: 4067c5fc8)
  - 旧件回退出库增加保存并提交接口 (commit: d137e3ff2)
- **KB更新**: zero-carbon-station.md 追加套餐库存管理章节; merchant-service.md 追加更新记录

### 4. rrsjk-migration-member
- **分支**: master | **HEAD**: 7cea47898e66
- **最后提交**: 2025-04-07 (14个月前)
- **业务文件数**: 43
- **结论**: 零提交跳过。Canal 数据迁移服务，已有完整文档
- **处理**: 跳过，更新时间戳

### 5. rrsjk-migration-mix
- **分支**: master | **HEAD**: 9783d7e9dea8
- **最后提交**: 2025-04-07 (14个月前)
- **业务文件数**: 196
- **结论**: 零提交跳过。Canal 多域数据迁移服务，已有完整文档
- **处理**: 跳过，更新时间戳

## 知识库更新汇总

| 文件 | 操作 | 内容 |
|---|---|---|
| `domains/zero-carbon-station.md` | patch 追加 | 零碳套餐库存管理 (2个新接口) |
| `domains/merchant-service.md` | patch 追加 | 第41轮更新记录 |

## 统计

- 本轮实际知识产出: 1 个新业务规则 (零碳套餐库存手动下调)
- 跳过仓库: 4/5 (零提交或无业务逻辑)
- KB 文件总更新: 2 个文件
