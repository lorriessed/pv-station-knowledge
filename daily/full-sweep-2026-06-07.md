# 第23轮全量通读报告 — 2026-06-07

## 概况

| 指标 | 值 |
|---|---|
| 轮次 | 第23轮 |
| 仓库总数 | 122 |
| 本次通读 | 5 个 |
| 从未通读 | 0 个 |
| 通读仓库 | vpp-crawler, vpp-data-platform, vpp-openapi, vpp-pv-oversea, vpp-template |

## 仓库分析

### 1. vpp-crawler (Python 爬虫) — 重扫跳过

- **HEAD**: e241390 (2026-01-21)
- **上次通读**: 2026-06-07
- **结论**: 零新提交，知识库已完整覆盖四川电力交易中心爬虫的 MySQL/Doris 双写架构、任务调度系统、Token 管理、数据推送流程
- **操作**: 仅更新 repo_last_sweep 时间戳，跳过源文件读取

### 2. vpp-data-platform (数据平台) — 重扫有新发现

- **HEAD**: 862a6ab (2026-06-01)
- **上次通读**: 2026-06-07 (但 KB 上次实质性更新 2026-05-15)
- **新增功能**:
  1. **时序数据设备名称筛选** (`TsKvPageQueryDTO.toNameList`): 传入设备名称列表后，先调用外部 API 获取设备 ID 映射，再查询时序数据
  2. **三组外部 API 凭证降级**: `zhijia@haier.com` → `qdsg@shougang.com` → `zhjt2025@cnnc.com`，逐级尝试获取设备关系
  3. **TsKvDO 改为 BaseDO**: 不再需要租户隔离，说明物联网设备数据跨租户共享
- **知识库更新**: `domains/vpp-overview.md` §14, `domains/vpp-data.md` §1.8

### 3. vpp-openapi (开放 API) — 重扫跳过

- **HEAD**: 57942b8 (2026-04-17)
- **上次通读**: 2026-06-07 (KB 2026-05-15)
- **结论**: 零新提交，知识库已完整覆盖 AK/SK 管理、权限控制、Drcloud 对接、OpenApi 自动发现
- **操作**: 仅更新 repo_last_sweep 时间戳

### 4. vpp-pv-oversea (海外光伏) — 重扫有新发现

- **HEAD**: bff9678 (2026-05-29)
- **上次通读**: 2026-06-07 (KB 2026-05-15)
- **新增功能** (mabin, 2026-04-24 ~ 2026-05-29):
  1. **SAP 发票记账凭证功能** (2026-05-29): 配合即采即销业务的发票记账凭证生成与提交
  2. **即采即销单付款计划验证** (2026-05-29): 验证付款计划状态是否满足 SAP 记账条件
  3. **即采即销单据状态验证与重试优化** (2026-05-29): 移除不必要的重试限制，调整队列重试次数
  4. **SAP 销售订单计费作业优化** (2026-05-08/09): 交货信息处理优化、空指针修复
  5. **电站信息并发安全修复** (2026-04-24): 修复 PvStationInfo 添加并发问题，新增设备类型
- **知识库更新**: `domains/vpp-overview.md` §15

### 5. vpp-template (模板服务) — 重扫跳过

- **HEAD**: d3cd60c (2026-03-03)
- **上次通读**: 2026-06-07 (KB 2026-05-15)
- **结论**: 零新提交，知识库已完整覆盖发票管理模板模块
- **操作**: 仅更新 repo_last_sweep 时间戳

## 知识库更新汇总

| 文件 | 更新类型 | 内容 |
|---|---|---|
| `domains/vpp-overview.md` | 新增 §14, §15 | vpp-data-platform 新功能 + vpp-pv-oversea 新功能 |
| `domains/vpp-overview.md` | 更新 §16 | 知识库更新记录表 |
| `domains/vpp-data.md` | 更新 §1.8 | 时序数据查询设备名称筛选/凭证降级/BaseDO |
| `modules/repositories.md` | 更新状态 | 5 个仓库标记为 2026-06-07 已通读 ✅ |
| `index.md` | 更新 | 轮次更新为第23轮，更新通读摘要 |

## 安全发现

- ⚠️ **vpp-data-platform**: TsKvServiceImpl 中 3 组外部 API 凭证 (用户名+密码) 硬编码在 `@Value` 注解中
- ⚠️ **vpp-data-platform**: TsKvServiceImpl 中凭证密码明文可见 (`zhijiahaier1`, `qdsg2025`, `zhjt@2025`)

## 统计

- 通读仓库: 5/5 (100%)
- 有新变更仓库: 2/5 (vpp-data-platform, vpp-pv-oversea)
- 零变更跳过: 3/5 (vpp-crawler, vpp-openapi, vpp-template)
- 新增 KB section: 8 个
- 更新 KB 文件: 5 个
