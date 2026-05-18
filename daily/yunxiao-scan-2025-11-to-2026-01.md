# 云效驱动代码学习报告 — 2025-11 ~ 2026-01

## 扫描范围
- 云效需求: 108 个（TAEI-2694 ~ TAEI-2778，createdAfter=2025-11-17, createdBefore=2026-02-01）
- 筛选后（已完成100014/开发中142838）: 约 100 个
- 涉及仓库: rrsjk-light-service, rrsjk-admin-web, rrsjk-light-report-service, rrsjk-finance-service, rrsjk-light-operation-service, rrsjk-async-import-export 等
- 识别相关提交: 约 150+ 个（核心开发人员）

## 需求 → 代码关联

| 需求号 | 标题 | 负责人 | 参与人(开发) | 相关提交仓库 |
|---|---|---|---|---|
| TAEI-2694 | HDS-电费管理新增分中心/项目公司/资方维度的3个报表 | 高媛(PM) | 孙志男 | rrsjk-light-service, rrsjk-light-report-service |
| TAEI-2695 | 合同已生成租金账单的电站重新签署沿用老租金政策 | 杨越越(PM) | 包鑫 | rrsjk-light-service |
| TAEI-2696 | 服务商申请配货限制为电站方案审核通过后 | 杨越越(PM) | 王斌 | rrsjk-light-service, rrsjk-admin-web |
| TAEI-2698 | 对已完工电站运维商所属管理逻辑优化 | 高媛(PM) | 孙志男 | rrsjk-light-operation-service |
| TAEI-2699 | 运维商入驻流程优化 | 高媛(PM) | 孙志男 | rrsjk-light-service |
| TAEI-2700 | 第三方社会化电站逆变器数据对接 | 高媛(PM) | 孙志男, 于淼 | rrsjk-light-service |
| TAEI-2702 | 银联接口增加字段 | 杨越越(PM) | 于淼, 商轶龙 | rrsjk-light-service |
| TAEI-2704 | 方案审核/完工/技术/商务审核记录审核人IP | 杨越越(PM) | 于淼 | rrsjk-light-service |
| TAEI-2705 | AI电站编码/业主姓名/地址/项目公司 | 杨越越(PM) | 于淼 | rrsjk-light-service |
| TAEI-2709 | 运维商政策兑现-(户用)负向政策兑现功能优化 | 高媛(PM) | 孙志男 | rrsjk-light-service (SAP A48/A51) |
| TAEI-2711 | 越秀变更银行卡更换模版 | 徐晓凤 | 王金浩 | rrsjk-light-service |
| TAEI-2713 | 工商业场景踏勘设计物料选择增加模糊搜索 | 高媛(PM) | 杨辉 | rrsjk-light-service |
| TAEI-2716 | 共享支付创建支付明细取电站银行卡联行号支行 | 杨越越(PM) | 王斌, 商轶龙 | rrsjk-light-service |
| TAEI-2717 | 三种考核组件库存/逆变器库存/整改时效机制白名单优化 | 杨越越(PM) | 代继宁, 商轶龙 | rrsjk-light-service |
| TAEI-2722 | 合同时效系统修改 | 杨越越(PM) | 解钦 | rrsjk-light-service |
| TAEI-2723 | 并网时效每日生成 | 杨越越(PM) | 商轶龙 | rrsjk-light-service |
| TAEI-2724 | 商户通/小程序/APP端显示共享支付成功/失败记录 | 杨越越(PM) | 代继宁, 商轶龙 | rrsjk-light-service |
| TAEI-2727 | 共享支付退汇和退回处理 | 杨越越(PM) | 王斌 | rrsjk-light-service |
| TAEI-2728 | AI识别房产证 | 杨越越(PM) | 陈国栋, 付凯善, 马斌 | **开发中** |
| TAEI-2729 | 运维商政策兑现-(户用)负向政策兑现功能优化 | 高媛(PM) | 孙志男 | rrsjk-light-service (SAP A51冲销) |
| TAEI-2730 | 商户通及HDS运维商特殊费用模块优化 | 高媛(PM) | 孙志男 | rrsjk-light-operation-service |
| TAEI-2731 | 越秀对接"农户固定收益异常支付信息查询" | 杨越越(PM) | 解钦 | rrsjk-light-service |
| TAEI-2733 | 零碳适家-店铺管理商品管理套餐库存计划 | 刘艺(PM) | 代继宁, 杨辉 | rrsjk-light-service, rrsjk-admin-web |
| TAEI-2734 | 绿证交易票税通接口新增合同附件和合同编码 | 刘艺(PM) | 商轶龙, 马斌 | rrsjk-light-service |
| TAEI-2735 | 零碳适家-订单超时24h自动取消归还库存 | 刘艺(PM) | 代继宁, 包鑫 | rrsjk-light-service |
| TAEI-2736 | 零碳适家-商户通套餐管理新增删除 | 刘艺(PM) | 代继宁, 杨辉 | rrsjk-light-service, rrsjk-admin-web |
| TAEI-2737 | 绿证交易部分审批流调整 | 刘艺(PM) | 商轶龙, 张硕文 | rrsjk-light-service |
| TAEI-2738 | 零碳适家-CBS采购单优化 | 刘艺(PM) | 姜传德 | rrsjk-light-service |
| TAEI-2739 | 零碳适家-保证金管理、订单批量确认回款 | 刘艺(PM) | 姜传德 | rrsjk-light-service |
| TAEI-2745 | 零碳适家-施工环节与energy对接 | 刘艺(PM) | 姜传德 | rrsjk-light-service |
| TAEI-2747 | App二期需求 | 徐晓凤 | 包鑫, 姜廷, 杨辉, 褚福贺 | rrsjk-admin-web |
| TAEI-2748 | 发电户号变更优化和逆变器优化 | 徐晓凤 | 王金浩, 马金虎 | rrsjk-light-service |
| TAEI-2749 | 技术建站需求二期 | 徐晓凤 | 王希然, 付凯善, 袁睿林 | rrsjk-light-service |
| TAEI-2751 | 大屏界面优化 | 徐晓凤 | 代继宁, 姜传德 | rrsjk-admin-web |
| TAEI-2752 | App&小程序新增水印相机 | 徐晓凤 | 于淼, 马斌, 王金浩, 付凯善 | rrsjk-light-service |
| TAEI-2753 | 电费管理模块功能迭代 | 高媛(PM) | 孙志男 | rrsjk-light-service |
| TAEI-2756 | 工商业竣工图/施工图纸上传G级大文件 | 杨越越(PM) | 于淼 | rrsjk-light-service |
| TAEI-2757 | 验收报告印模分段使用海尔光伏 | 杨越越(PM) | 于淼 | rrsjk-light-service |
| TAEI-2758 | 新商政策优化 | 杨越越(PM) | 代继宁, 商轶龙 | rrsjk-light-service |
| TAEI-2760 | 撤销和恢复合同记录原因和日志 | 杨越越(PM) | 包鑫 | rrsjk-light-service |
| TAEI-2761 | 电费报表(资方)取数逻辑优化 | 高媛(PM) | 孙志男 | rrsjk-light-report-service |
| TAEI-2763 | 验收页面整改 | 杨越越(PM) | 于淼, 付凯善, 马金虎 | rrsjk-light-service |
| TAEI-2772 | 报表电站成本核算报表增加新商政策兑现金额 | 杨越越(PM) | 解钦 | rrsjk-light-report-service |
| TAEI-2773 | HDS工单大厅新增资方运维工单(越秀)模块 | 高媛(PM) | 孙志男 | rrsjk-light-operation-service |
| TAEI-2774 | 银联支付合计修改生成银联采购单金额 | 杨越越(PM) | 商轶龙 | rrsjk-light-service |
| TAEI-2777 | 工商业开票支持小EPC | 杨越越(PM) | - | rrsjk-light-service (中转仓) |
| TAEI-2778 | 运维商商户通电站列表加更新时间 | 高媛(PM) | 孙志男 | rrsjk-light-service |

## 业务链分析

### 1. SAP A48/A51 冲销暂估机制 (TAEI-2709/2729/2730)
**开发者**: 孙志男 (sunzn)
**仓库**: rrsjk-light-service

**业务逻辑**:
- `operation_maintenance` 表记录运维管理单据
- `bookkeepingType` = `A48` (运维商政策兑现记账) 或 `A51` (暂估记账)
- 原有逻辑: A48记账成功后自动关联A51数据做暂估确认 (2026-01-29 已注释掉)
- 新增 `operationCoverA51()` 方法: 支持手动指定A51管理单号进行冲销
- 冲销流程: relationNo + "_C" → `lightSapService.coverOperationMaintenanceA51()` → 更新 coverVoucher + coverAt + status=COVERED
- 涉及SAP集成服务: `LightSapService.coverOperationMaintenanceA51()`

**关键代码**:
- `OperationMaintenanceServiceImpl.operationCoverA51()` (commit 16204c93)
- `OperationMaintenanceServiceImpl.operationMaintenanceSapAccount()` (commit 357c5eed, A48自动关联逻辑已注释)
- `OperationMaintenanceServiceImpl.findA51New()` (查找对应A51数据)

### 2. 派单管理/调度报告时效 (TAEI-2733/2735/2736/2744)
**开发者**: 代继宁
**仓库**: rrsjk-light-service, rrsjk-admin-web, rrsjk-light-report-service

**业务逻辑**:
- `light_audit_dispatch_log` 表记录审核派单日志
- 新增 dispatchYear/Month/Day 和 dealYear/Month/Day 时间维度字段，用于按年/月/日统计派单时效
- 派单类型: DISPATCH(派单) / GRAB_ORDER(抢单)
- 处理状态: PASSED(通过) / REJECTED(驳回)
- `handleDateTime()` 方法自动解析 LocalDateTime 并设置年月日字段
- 报表服务: 技术审核时效报表、审计分发日志统计

**关键代码**:
- `LightAuditDispatchLog.java` (commit 88003e2b) - 实体新增字段
- `LightAuditDispatchLogServiceImpl.handleDateTime()` - 时间解析
- rrsjk-light-report-service: 报表SQL修改支持年月日统计

### 3. 零碳适家业务 (TAEI-2738/2739/2745)
**开发者**: 姜传德(德), 代继宁
**仓库**: rrsjk-light-service

**业务逻辑**:
- `LightZeroCarbonSkuData` SKU枚举新增 CHARGING_PILE(充电桩)
- CBS采购单优化
- 保证金管理、订单批量确认回款
- 零碳电站SKU重复性校验
- 零碳e站对接能源管理(还原)
- 子服务商相关字段支持

### 4. 工商业中转仓发货 (TAEI-2777)
**开发者**: 王斌 (tn_wangb)
**仓库**: rrsjk-light-service, rrsjk-admin-web

**业务逻辑**:
- `CmPreOrderServiceImpl.transit2CmStore()` 中转仓发货
- 修复: 收货人信息从 cmStore(门店) 改为从 cmPreOrder(采购单) 取
- 涉及 `light_transfer_order` 调拨单创建

### 5. 工商业开票/小EPC (TAEI-2777)
**开发者**: 王斌
**仓库**: rrsjk-finance-service

**业务逻辑**:
- 租金支付明细支付成功二次确认
- 租金查凭证逻辑更改
- 26年之前的请款单走老影像接口

### 6. 招银租赁/电费查询 (TAEI-2748)
**开发者**: 马金虎 (majinhu)
**仓库**: rrsjk-light-service, rrsjk-finance-service

**业务逻辑**:
- 招银东莞306个电站并网时间常量配置
- 电费编号查询条件修正
- 租赁记录查询站点筛选
- 电站变更策略发电解绑逻辑优化

## 知识库更新
| 操作 | 文件 | 内容摘要 |
|---|---|---|
| 追加 | data/enums.md | SAP记账类型(A48/A51)、派单管理枚举、零碳适家SKU类型 |
| 追加 | data/tables.md | operation_maintenance表、light_audit_dispatch_log表、零碳适家表、工商业采购表 |
| 新建 | daily/yunxiao-scan-2025-11-to-2026-01.md | 本报告 |

## 开发人员提交统计

| 开发者 | Git Author | 提交数(估算) | 主要涉及业务 |
|---|---|---|---|
| 孙志男 | sunzn | 30+ | SAP A48/A51冲销、运维商政策兑现、社会化合同、买损管理、越秀工单 |
| 于淼 | yumiao | 25+ | 电站编辑、零碳适家、发票核销、大文件上传、验收整改 |
| 代继宁 | 代继宁 | 20+ | 派单管理、调度报告、零碳适家、新商政策 |
| 王斌 | tn_wangb | 15+ | 工商业中转仓、租金支付、共享支付 |
| 解钦 | 解钦 | 15+ | 中核电站冲销、派单功能、SAP记账、报表优化 |
| 包鑫 | baoxin | 10+ | 采销订单、报表、GTMS返款、产品主数据 |
| 马斌 | mabin | 10+ | 商务验收、图片验真、二级商数据看板 |
| 姜传德 | 德 | 10+ | 零碳适家、子服务商、能源管理对接 |
| 马金虎 | majinhu | 10+ | 招银租赁、电费查询、电站变更 |
| 王希然 | wangxiran | 5+ | 方案变更、银行卡变更、完工审核 |
| 商轶龙 | 商轶龙 | 需进一步扫描 | 银联接口、并网时效、新商政策、绿证交易 |

## 发现与经验
- **A48/A51自动关联逻辑已下线**: 2026-01-29提交中注释掉了A48自动关联A51的逻辑，改为手动 `operationCoverA51()` 方法。这可能是业务调整，需要了解原因。
- **派单时间维度细化**: `light_audit_dispatch_log` 表新增年月日字段，说明业务需要更细粒度的派单时效统计。
- **零碳适家是新业务域**: 充电桩SKU、CBS采购优化、保证金管理等，是一个相对独立的新业务模块。
- **工商业场景持续迭代**: 中转仓发货、小EPC开票、大文件上传等，工商业(CM)业务在持续优化。
- **映射表完整性**: Git author映射表基本覆盖核心13人，但部分参与者（杨辉、姜廷、褚福贺、付凯善、袁睿林、陈国栋、张硕文、刘飞等）不在映射表中，需要补充。
