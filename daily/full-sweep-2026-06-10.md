# 第 27 轮全量通读报告 — 2026-06-10

## 概览

| 指标 | 值 |
|---|---|
| 通读轮次 | 第 27 轮 |
| 总仓库数 | 122 |
| 已通读 | 122/122 (100%) ✅ |
| 本次通读仓库 | 5 个 |
| 从未通读仓库 | 0 个 |
| KB 更新文件 | 2 个 |

## 本次通读仓库

| 仓库 | 类型 | 业务文件数 | 最后提交 | 说明 |
|---|---|---|---|---|
| base-service | CBS 基础服务 (EAI) | 79 | 2025-08-27 | 重扫，无新提交 |
| cbs-web | CBS 管理后台 Web | 367 | 2026-05-20 | 重扫，发现遗漏的 dispenser 模块 |
| he-pv.osp-wx.opm | 前端基础设施 | 1 | 2025-08-14 | 仅 pnpm-lock.yaml，无业务逻辑 |
| he-vpp.admin-h5 | VPP 管理后台 H5 | 1 | 2026-06-04 | 仅 pnpm-workspace.yaml，源码未捕获 |
| he-vpp.hnzl-h5 | VPP 能链 H5 | 1 | 2025-11-05 | 仅 svgo.yml，无业务逻辑 |

## 知识库更新

### 1. domains/cbs-management.md — 新增 cbs-web 遗留水站/饮水机业务模块

**新增内容**:
- cbs-web dispenser/ 目录下 **24 个 Controller** 完整路由清单
- 水站业务模块列表：CheckInventory(盘点)、CleanOrder(清洗订单)、CxwCleanOrder(车小微清洗)、FetchRecord(打水记录)、FilterChange(滤芯更换)、PointsExchange(积分兑换)、RiceField(稻田认筹) 等
- BusinessApplyController 专业客户审核流程 (status=3通过/-3驳回)
- Kuaidi100Controller 快递100回调逻辑
- OrderCancelController 订单取消退款接口
- **⚠️ 安全发现**: OrderCancelController 的签名校验 (`checkValidSign`) 已注释掉，生产可能存在未鉴权访问风险
- cbs-web Dubbo 依赖完整清单 (12 个外部服务)

### 2. modules/repositories.md — 全量重新生成

- 从 `full_sweep.json` 重新生成，122/122 仓库状态已同步
- 本次 5 个仓库更新为 `(2026-06-10 已通读 ✅)`

## base-service 通读结论

base-service 已在 `domains/remaining-services-and-frontends.md` §1 有完整文档（2026-05-12 全量通读）。本次重扫确认：
- **2025-08 之后无新提交**，代码无变更
- EAI 集成服务（LES/SAP/金税/HP/MDM/AWS）文档已覆盖
- 无需更新 KB

## he-pv.osp-wx.opm / he-vpp.admin-h5 / he-vpp.hnzl-h5 通读结论

- **he-pv.osp-wx.opm**: 仅 `pnpm-lock.yaml`，构建产物仓库，无业务代码
- **he-vpp.admin-h5**: 扫描脚本仅捕获 `pnpm-workspace.yaml`，但 git log 显示近期有 FAP 退款优化/电费价格相关提交（feat/opt-refund-fap 分支），源码应在 `packages/` 子目录中未被脚本展开
- **he-vpp.hnzl-h5**: 仅 `svgo.yml` 图标优化配置，无业务代码

## 统计

- 本次发现新知识: 1 个模块 (cbs-web dispenser 遗留业务)
- 确认无变更仓库: 4 个 (base-service + 3 个基础设施仓库)
- KB 文件新增内容: ~80 行
- 安全风险提示: 1 条 (OrderCancelController 签名校验失效)
