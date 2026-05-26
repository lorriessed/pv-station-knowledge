# 云效驱动代码学习报告 — 第10期 (2026-05-08 ~ 2026-05-17)

## 扫描范围
- 云效需求: 29 个 | 涉及人员: 解钦、孙志男、李龙、于淼、马斌、王斌、包鑫、代继宁、王希然、姜传德、马金虎、laowang 等
- Git 提交: 477 个 | 涉及仓库: 14 个（rrsjk-light-service 185、rrsjk-admin-web 142、rrsjk-light-operation-service 47、rrsjk-light-report-service 33、rrsjk-light-data-service 24、rrsjk-hds-web 14、rrsjk-merchant-web 11、rrsjk-finance-service 8、rrsjk-light-openapi-service 4、rrsjk-trade-service 3、vpp-pv-oversea 2、rrsjk-system-service 2、rrsjk-openapi-web 1、job-service 1）

## 需求 → 代码关联

| 需求号 | 标题 | 状态 | 开发人员 | 相关提交 | 涉及仓库 |
|---|---|---|---|---|---|
| TAEI-3074 | 商机管理支持页面弃置流程 | 已完成 | 付凯善, 袁睿林, 马金虎 | discardStatus 字段相关 | rrsjk-light-service, rrsjk-admin-web |
| TAEI-3076 | 政策传SAP记账带上电站编码和订单号 | 已完成 | 解钦, 商轶龙 | 72283a8 (xref3改stationCode) | rrsjk-light-service |
| TAEI-3078 | 派单3.1 派单优化 | 已完成 | 解钦 | dispatch-order-3.1 系列 | rrsjk-light-service, rrsjk-admin-web, job-service |
| TAEI-3079 | 电费收益相关优化 | 开发中 | 徐晓凤, 王金浩, 商轶龙 | 统众电费批量确认等 | rrsjk-admin-web |
| TAEI-3080 | 新增公建和整村租金支付功能 | 待测试 | 商轶龙 | 共享支付查询修复 | rrsjk-light-operation-service |
| TAEI-3081 | 完工节点增加字段 | 已完成 | 徐晓凤, 王金浩, 张硕文, 付凯善 | 完工节点相关 | - |
| TAEI-3083 | 完工前变更方案审批流变更 | 已完成 | 徐晓凤, 王斌, 付凯善 | wb-planChange 分支 | rrsjk-admin-web |
| TAEI-3084 | 中银租后接口对接 | 开发中 | 马斌 | zhongYinLease 总发电量查询 | rrsjk-light-openapi-service, rrsjk-openapi-web |
| TAEI-3085 | 增加上收限制 | 已完成 | 解钦 | station-income-constrain 重构 | rrsjk-light-service |
| TAEI-3086 | HDS/商户通/APP添加共享支付账单查询 | 已完成 | 孙志男, 魏秋阳, 李培龙 | 共享账单查询 | rrsjk-light-service, rrsjk-light-operation-service, rrsjk-hds-web |
| TAEI-3087 | 国电投账号 | 已完成 | 魏秋阳, 于淼, 王希然, 李培龙 | CQ_GDT 逆变器查询/导出 | rrsjk-hds-web, rrsjk-light-data-service |
| TAEI-3088 | 云南能源局合同扩展区域 | 已完成 | 包鑫 | 云川合同区域新增保山市隆阳区 | rrsjk-light-service |
| TAEI-3089 | A端政策结算逻辑调整 | 测试中 | 商轶龙 | 基金安装科目A40→A41 | rrsjk-light-service |
| TAEI-3092 | 农户租金类个税报表及记账 | 开发中 | 代继宁 | FAP/报表相关 | rrsjk-light-service, rrsjk-light-report-service |
| TAEI-3095 | 业主合同去掉质押类条款 | 已完成 | 包鑫 | 修改公司备案合同 | rrsjk-light-service |
| TAEI-3096 | 零碳适家调用energy系统建站接口 | 测试中 | 魏秋阳, 王金浩 | 省市区字段支持 | rrsjk-light-service, rrsjk-admin-web |
| TAEI-3098 | 图片验真唯一码入库前增加重复检查 | 已完成 | 马斌 | queryLastedByUniqueKey | rrsjk-light-service |
| TAEI-3100 | 自持电站报表优化 | 已完成 | 徐晓凤, 王斌 | 工商业自持电站损益报表 | rrsjk-light-service, rrsjk-admin-web, rrsjk-light-report-service |
| TAEI-3101 | 招银组件功率匹配价格 | 待测试 | 李龙 | CmbElectricPriceV2 新实体 | rrsjk-light-service, rrsjk-admin-web |
| TAEI-3102 | CBS招投标流程 | 开发中 | 魏秋阳, 王金浩 | 招投标管理实体 | rrsjk-light-service, rrsjk-admin-web |
| TAEI-3103 | 电站业主租金停付管理 | 开发中 | 孙志男, 魏秋阳, 李培龙 | 共享支付/租金停付 | rrsjk-light-service, rrsjk-light-operation-service |
| TAEI-3104 | light_unionpay_rent表唯一键冲突 | 已完成 | 商轶龙 | 唯一键冲突修复 | - |
| TAEI-3107 | 风电产值法兼容1.0 | 测试中 | 王斌, 解钦, 杨辉 | 风电产值法 | - |

## 业务链分析

### 1. SAP 记账 xref3 字段变更 (TAEI-3076)
**核心变更**: 所有资方收入结算服务的 SAP 记账 xref3 字段从 `bid` 改为 `stationCode`
**影响**: 华融、越秀、普音、招银、中银 5 个结算服务
**业务价值**: SAP 侧可通过电站编码直接追溯收入记录

### 2. 收入上收限制重构 (TAEI-3085)
**核心变更**: 回购电站检查从状态字段改为独立回购记录表查询；错误提示优化
**影响**: 6 个收入导入服务（华融、基金、户用、普音、招银、中银）
**新增 DAO**: `LightStationRepurchaseDao.findActiveRepurchaseStationCodes()`

### 3. 派单3.1 时间配置优化 (TAEI-3078)
**核心变更**: 
- 新增时间段重叠校验（`validateTimeOverlap`）
- 工作日非正常工作时间也支持配置派单时间段
- 电站终止时自动删除关联定时任务

### 4. 招银组件功率匹配价格 V2 (TAEI-3101)
**核心变更**: 
- 新实体 `CmbElectricPriceV2`（增加 regionName、moduleType 维度）
- 新枚举 `TechnicalSchemeEnumV2`（5种方案）和 `LeaseRoofTypeEnumV2`（3种类型）
- 电价查询从 3 维提升到 5 维（省+市+区县+屋顶类型+组件类型）

### 5. 共享支付账单查询 (TAEI-3086)
**核心变更**: 租金查询新增 `source=4` 分支，支持 `LightShareBillRecord` 共享账单查询
**前端**: HDS、商户通、APP 三端覆盖

### 6. 中银租后总发电量查询 (TAEI-3084)
**核心变更**: `findZhongYinTotalElec` 接口，查询所有中银电站的总发电量汇总
**SQL**: `sum(elec_day)` 按日期分组，从 `ods_light_station_elec` 表查询

### 7. 图片验真唯一码重复检查 (TAEI-3098)
**核心变更**: 插入前检查 `uniqueImageKey` 是否已存在，避免唯一键冲突
**触发**: TAEI-3104（`light_unionpay_rent` 表 `uni_station_id` 唯一键冲突）

## 知识库更新

| 操作 | 文件 | 内容摘要 |
|---|---|---|
| 追加 | domains/income-mode-strategies.md | §九: 收入上收限制重构 — 回购电站拦截+错误提示优化 |
| 追加 | domains/dispatch-order-scheduled-tasks.md | §9.6-9.7: 时间段重叠校验 + 派单时间范围判断重构 |
| 追加 | domains/settlement.md | SAP xref3 字段变更 + 共享支付账单查询后端实现 |
| 追加 | domains/inverter-data.md | CQ_GDT 新增字段 firstThreePowerAt + HDS前端查询导出 |
| 追加 | domains/station-lifecycle.md | 图片验真唯一码重复检查 |

## 备注
- 本期为 10 天补漏计划的**最后一期**（第10期: 2026-05-08 ~ 2026-05-17）
- 完成后应删除 cronjob `228ca084f26a`
