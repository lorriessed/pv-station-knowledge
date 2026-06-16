# PVS 全量通读报告 2026-06-16 (第32轮)

## 通读概况

| 项目 | 值 |
|------|-----|
| 仓库总数 | 122 |
| 本轮通读 | 5 个 |
| 从未通读 | 0 个 (100%覆盖) |
| 通读轮次 | 第32轮 (全部为重扫) |

## 本轮通读仓库

### 1. pv.ospboard-h5
- **类型**: Vue 3 H5 大屏项目
- **业务价值**: 低 — 仅 `pnpm-workspace.yaml` 配置文件，无业务代码
- **最后提交**: 2025-12-23 (fix:电站统计当月新增电站数字段调整)
- **技术栈**: Vite 6 + Vue 3.5 + UnoCSS + ECharts + Pinia
- **结论**: 无新业务逻辑，跳过

### 2. r_upgrade
- **类型**: Flutter 应用升级插件
- **业务价值**: 低 — 通用 Flutter 插件 (pub.dev 发布)，非 PVS 业务代码
- **最后提交**: 2024-10-09
- **功能**: Android APK 下载/安装/热更新，支持 Google Play/小米/腾讯应用商店版本检查
- **结论**: 无 PVS 业务知识，跳过

### 3. repairs ⭐ (重点)
- **类型**: 光伏备件运维服务 (核心业务服务)
- **业务价值**: 高 — 覆盖借件/回购/旧件回退/逆变器维修/仓储/财务/SAP
- **最后提交**: 2026-06-11 (活跃开发中)
- **本轮新增知识**:

#### 2026-06-11: 中心仓出库备件SO发货供应商编码变更
- **来源**: `repairs` → `SpTranSnServiceImpl.java` (commit 5d6c10b7, A0026566)
- **变更**: GVS SO发货时 `XREF2`(业务伙伴参考码) 从传运维商编码改为传日日顺供应商编码 `V98666`
- **原因**: 财务中心要求
- **新增接口**: `SpOrderBorrowService.centerBorrowSapToSparePart(orderNo)` — SO发货失败重传
  - 校验: 订单存在 + 中心仓出库(`borrowWarehouse=0`) + 记账失败(`accountingStatus=0`)
  - 实现: 调用 `SpTranSnService.centerBorrowSapToSparePart()` → `lendSapToSparePart()`

#### 2026-06-08: 旧件判责接收状态更新
- **来源**: `repairs` → `SpOldbackListsDetailServiceImpl.java` (commit d8871b51, A0026566)
- **变更**: 判责提交后新增 `receiveStatus=2`(已接收) + `receiveDate` 赋值
- **新增**: 判责完成后调用 `judgeOldbackStatus()` 判断更新回退主单状态

#### 2026-06-08: 旧件核销防重复销账修复
- **来源**: `repairs` → `SpOldbackListsServiceImpl.java` (commit f6f5e8f8, A0026566)
- **Bug**: `partsPaymentFlow()` 的 `sourceId` 传回退主单ID，导致同一明细可能被重复销账
- **修复**: `sourceId` 改为传回退明细主键ID (`spOldbackListsDetail.getId()`)
- **附带**: 魔法值 `"5"` 替换为 `OldbackOrderStatusEnum.WXTF.getCode()`

#### 2026-06-08: 工单备件列表增加取消字段
- **来源**: `repairs` → `OrderWoPart.java` + `WoPart.xml` (commit 95e89247, A0026566)
- **新增字段**: `cancelReason`、`cancelTime`

### 4. rrs-dispenser-server
- **类型**: 水站设备 IoT 服务器 (Netty)
- **业务价值**: 无 — 非 PVS 光伏业务，属于日日顺(RRS)水站项目遗留代码
- **最后提交**: 2023-03-16 (已3年无更新)
- **技术栈**: Spring 4.3 + Netty 3.9 + ActiveMQ + Dubbo 2.5.8 + JSW 部署
- **功能**: 格美(Gemei)水站协议解析 — 心跳/刷卡/状态/广告/GPS/报警/双出水
- **结论**: 非 PVS 业务，仅记录架构信息

### 5. rrsjk-activity-service
- **类型**: 接龙活动服务 (微信小程序)
- **业务价值**: 低 — 非核心光伏业务，社交电商功能
- **最后提交**: 2022-06-08 (已4年无更新)
- **技术栈**: Spring Boot 2.2 + Dubbo 2.7 + MyBatis + Redis + Guava EventBus
- **功能**: 接龙活动创建/编辑/下单/库存扣减/领取
- **数据库表**: `activity`, `item`, `orders`, `order_item`
- **结论**: 非核心业务，仅记录架构信息

## 知识库更新

| 文件 | 操作 | 说明 |
|------|------|------|
| `domains/repairs-service.md` | 更新 | 新增4条变更记录(2026-06-08/06-11)，新增 `centerBorrowSapToSparePart` 接口文档 |
| `modules/repositories.md` | 更新 | 5个仓库标记 2026-06-16 已通读 |
| `state/full_sweep.json` | 更新 | 5个仓库 `repo_last_sweep` 更新为当前时间 |

## 统计

- 有业务变更的仓库: 1 (repairs)
- 无业务变更的仓库: 4 (pv.ospboard-h5, r_upgrade, rrs-dispenser-server, rrsjk-activity-service)
- 新增/更新知识库文件: 3
