# PVS 全量通读日报 2026-07-01 (第46轮)

## 通读概况

| 仓库 | 最后提交 | 业务文件数 | 状态 |
|------|---------|-----------|------|
| rrsjk-pay-service | 2026-04-10 | 56 | 重扫 — 已有完整文档(340行) |
| rrsjk-pay-web | 2022-12-19 | 25 | 重扫 — 已有完整文档 |
| rrsjk-pvbusiness-job-service | 2025-06-16 | 56 | **重扫 — 发现重大知识缺口，新建domain文件** |
| rrsjk-report-web | 2026-05-07 | 24 | 重扫 — 补充新增接口 |
| rrsjk-system-service | 2026-06-03 | 176 | 重扫 — 补充近期变更 |

## 知识库更新

### 新建文件
1. **`domains/pvbusiness-job-service.md`** (285行)
   - 光伏自有资产管理 (LightOwnAsset): 导入→推送HSCC→跟踪审批状态
   - @SingleJob 分布式锁框架: Redis锁 + 看门狗续期 + skipOnLockFail降级
   - HSCC资产接口集成: application-key + HMAC-SHA256签名认证
   - 超期库存管控报表: 4维度(总表/分中心/物料/基础数据) × 9个库龄段
   - GVS仓库库龄分析: 从GVS接口拉取库存数据
   - 7个数据源架构: local/light/report/elec/operation/shop/finance
   - Dubbo依赖关系: 引用17个外部服务

### 更新文件
2. **`domain-router.md`** — 新增"光伏业务定时任务"路由条目
3. **`domains/frontend-and-misc-services.md`** — report-web 新增工单数量统计接口 (2026-04-28)
4. **`domains/system-infra-service.md`** — 新增 rrsjk-system-service 2026-05~06 变更表 (HrflcBankInfo/GfMatchRegion/CalendarDay/OCR)
5. **`data/tables.md`** — 新增9张表:
   - light_own_asset, light_own_asset_status, light_asset_application_log, light_company_info
   - energy_overdue_inventory_control_summary/center/sku/data_base
   - gvs_warehouse_age_analysis, sap_sp_center_relation

## 关键业务发现

### 1. HSCC 资产管理系统对接 (代码明确证明)
- 光伏自有资产(使用权资产)通过 HTTP API 推送到海尔 HSCC 资产系统
- 接口地址: `hscapi.haier.net/Product/CBS-RightOfUseAsset/ApplicationInterface`
- 认证: application-key + HMAC-SHA256 签名
- 资产状态流转: IMPORTED → TRANSFERRED → WAIT_AUDIT → (审批结果)
- CBS编号规则: `LOA` + yyyyMMdd + 6位序号

### 2. @SingleJob 分布式锁框架 (代码明确证明)
- 自定义注解 + AOP切面，替代 XXL-JOB 的防重入机制
- 看门狗自动续期: 每 maxLockTime/3 刷新 Redis TTL
- 支持降级模式: skipOnLockFail=false 时即使锁获取失败也执行
- 全局开关: `single-job.enabled` 可禁用所有锁校验

### 3. 超期库存管控报表体系 (代码明确证明)
- 组件和逆变器分别统计，9个库龄分段(60d~3y+)
- 每个分段3个指标: quantity(数量)、amount(金额)、process(占比)
- 按分中心/物料/汇总3个维度展示

## 无新知识的仓库

- **rrsjk-pay-service**: 最后提交 2026-04-10 (版本修改)，已有340行完整文档
- **rrsjk-pay-web**: 最后提交 2022-12-19 (储能小程序)，已完全覆盖

## 统计
- 通读仓库: 5个
- 新建domain文件: 1个
- 更新KB文件: 4个
- 新增表记录: 9张
- 新增API端点: 1个 (getWorkOrderCount.do)
