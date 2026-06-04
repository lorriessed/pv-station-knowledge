# 云效驱动代码学习报告 — 2026-05-11 至 2026-05-17

> 回补任务 | 生成时间: 2026-06-04 | 时间窗口: updateStatusAt 2026-05-11 ~ 2026-05-17

## 扫描范围

- **云效需求**: 20 个（含 2 个已取消、1 个待处理）
- **有效需求**: 17 个
- **涉及开发人员**: 孙志男、包鑫、解钦、马斌、马金虎、王斌(龙龙)、王希然、于淼、张硕文、李培龙、付凯善、杨辉、刘飞、王金浩(laowang)、姜廷、董学强、袁睿林、徐晓凤、商轶龙、魏秋阳
- **Git 提交**: 321 条（覆盖 22 个仓库）
- **核心业务仓库**: rrsjk-light-service(115), rrsjk-light-operation-service(46), rrsjk-admin-web(43), rrsjk-light-data-service(23), rrsjk-light-report-service(18), rrsjk-finance-service(7)

## 知识覆盖分析

| 需求号 | 标题 | 状态 | 图谱覆盖情况 | 学习深度 |
|---|---|---|---|---|
| TAEI-3086 | HDS/商户通/APP添加共享支付账单查询 | 已完成 | ✅ 已覆盖(Domain:cm-business) | 完整分析 |
| TAEI-2975 | 【政策优化】变更房型类优化 2026-03-30 | 已完成 | ✅ 已覆盖(Domain:policy) | 增量更新 |
| TAEI-3076 | 【记账】政策传SAP记账带上电站编码和订单号 | 已完成 | ✅ 已覆盖(Domain:settlement) | 完整分析 |
| TAEI-3078 | 【派单3.1】派单优化 | 已完成 | ✅ 已覆盖(Domain:approval) | 完整分析 |
| TAEI-3088 | 【合同】云南能源局合同 扩展区域 | 已完成 | ✅ 已覆盖(Domain:contract) | 增量更新 |
| TAEI-3095 | 【合同】业主合同去掉质押类条款 | 已完成 | ✅ 已覆盖(Domain:contract) | 增量更新 |
| TAEI-3063 | 【户用光伏】广发过程进件 | 已完成 | ✅ 已覆盖(Domain:income-mode-strategies) | 完整分析 |
| TAEI-3059 | 【建站】建站相关优化 | 已完成 | ✅ 已覆盖(Domain:station-lifecycle) | 增量更新 |
| TAEI-2431 | CBS 审核时照片旋转查看 | 已完成 | ✅ 已覆盖(Domain:admin-authz) | 增量更新 |
| TAEI-3062 | 【报表】审核派单「闭环率报表」优化 | 已完成 | ✅ 已覆盖 | 增量更新 |
| TAEI-3081 | 【建站】完工节点增加字段 | 已完成 | ✅ 已覆盖(Domain:station-lifecycle) | 增量更新 |
| TAEI-3098 | 图片验真唯一码入库前增加重复检查 | 已完成 | ✅ 已覆盖(Domain:station-lifecycle) | 完整分析 |
| TAEI-3036 | 【电站】APP商户通电站列表优化 | 已完成 | ✅ 已覆盖 | 增量更新 |
| TAEI-3043 | 【工商业】自持电站损益报表 | 已完成 | ✅ 已覆盖(Domain:cm-business) | **深度分析(13 commits)** |
| TAEI-3061 | 【建站】已完工电站方案变更逻辑优化 | 已完成 | ✅ 已覆盖(Domain:station-lifecycle) | **深度分析** |
| TAEI-3074 | 【户用光伏】商机管理支持页面弃置流程 | 已完成 | ✅ 已覆盖(Domain:station-lifecycle) | 增量更新 |
| TAEI-3017 | 【户用光伏】广发过程进件——审核、进件 | 已完成 | ✅ 已覆盖(Domain:income-mode-strategies) | 完整分析 |

### 已取消/待处理（跳过）
- TAEI-3091 【工商业】风电类上领用逻辑整理 — **已取消**
- TAEI-3105 【性能优化】LightStationEnableRewardJobService — **已取消**
- TAEI-3099 【户用光伏】部分中核电站发电户号重推 — **待处理**

## 需求 → 代码关联

### TAEI-3086: HDS/商户通/APP添加共享支付账单查询
- **负责人**: 高媛 | **参与人**: 魏秋阳, 孙志男, 李培龙
- **相关提交**: sunzn 19 条 (light-operation-service, light-service, hds-web), 李培龙 2 条 (pv.osp-uni), wangxiran 1 条 (light-data-service)
- **涉及仓库**: rrsjk-light-operation-service, rrsjk-light-service, rrsjk-hds-web, pv.osp-uni
- **变更内容**:
  - `light-operation-service`: 共享账单记录查询逻辑重构 (`refactor(light-operation): 优化共享账单记录查询逻辑`)
  - `light-operation-service`: 修正共享支付查询中的租用月份参数 (4 commits)
  - `light-operation-service`: 添加电站租金记录的备注和账单日期字段
  - `light-service`: 添加共享账单记录明细查询功能 (`feat(light-rent)`)
  - `pv.osp-uni`: 添加共享支付账单查询 (前端入口)
  - `hds-web`: 修复 A51 暂估业务逻辑 (sunzn)

### TAEI-3076: 政策传SAP记账带上电站编码和订单号
- **负责人**: 杨越越 | **参与人**: 解钦, 商轶龙
- **相关提交**: 解钦 6 条 (light-service)
- **涉及仓库**: rrsjk-light-service
- **变更内容**:
  - `feat(电站收入限制)`: 上收入的时候传递 xref3 字段传递电站编码
  - `feat(电站收入限制)`: 八种模式导入收入的时候校验电站状态
  - `feat(station-income-constrain)`: 电站不同模式是否上收入的策略接口重构，增加工厂类扩展
  - `feat(station-income-constrain)`: 重构不同的收入模式的电站查询
  - `feat(station-income-constrain)`: 导入收入异常判断重构
  - `fix(电站回退基金收入)`: 基金重上收入安装费科目修复，A40 → A41
- **业务影响**: 收入策略模式重构（工厂类），SAP 记账增加电站编码关联

### TAEI-3078: 派单3.1 派单优化
- **负责人**: 杨越越 | **参与人**: 解钦, 薛荣基
- **相关提交**: 解钦 8 条 (light-service 6 + admin-web 2)
- **涉及仓库**: rrsjk-light-service, rrsjk-admin-web
- **变更内容**:
  - `LightAuditDispatchTimeConfigService.addConfig` 返回值从 `boolean` 改为 `Long`（返回配置 ID）
  - 非工作日配置查询增加 `status = 1` 过滤（只看启用状态）
  - `dispatchBacklogByConfigId` 参数从 `Long` 改为 `String`
  - `CompleteConfirmServiceImpl.auditOk` 修复：前辈校验 bug，增加电站 ID 非空检查 + 提前查询电站信息
  - **Bug 修复**: `validStopStatusList.contains` 逻辑取反（`!` 修复），终止流程中的电站不允许审核
  - admin-web 侧配合：station-complete-stop 状态管理和定时任务创建使用 configId

### TAEI-3043: 工商业自持电站损益报表（重点需求）
- **负责人**: 徐晓凤 | **参与人**: 王斌, 薛荣基
- **相关提交**: tn_wangb(龙龙) 13 条 (light-service 9 + light-report-service 1 + light-data-service 1 + admin-web 6)
- **涉及仓库**: rrsjk-light-service, rrsjk-light-report-service, rrsjk-light-data-service, rrsjk-admin-web
- **变更内容（深度分析）**:
  - **新增实体**: `CmOwnerStationReportThirdLog`（第三方日志记录表）+ 对应 Mapper XML（214 行新增）
  - **报表核心逻辑重构**: `CmOwnerStationReportServiceImpl` 经历多次迭代（159+/47+ 行变更）
  - **充电桩发电量查询优化**: 从 for 循环逐个查 `chargingStationService.getPvGenerationByMonth` 改为批量查询
  - **新增字段**: `cm_owner_station_white_list` 表扩展
  - **高压电费查询**: 新增 `queryMonth` 参数过滤 (`LightHighElec.xml`)
  - **新增枚举**: `LightStationPlanChange.StatusEnum.NO_NEED_AUDIT`（完工前方案变更，仅品牌变更无需审核）
  - **方案变更逻辑**: `LightStationPlanChangeServiceImpl` 增加 skipAudit 逻辑（仅变更品牌时自动审核通过）
  - **发电来源字段非必填**: 兼容 1PG0 公司导入
  - **毛利率除零保护**: `totalIncomeAmount == 0` 时毛利率设为 0
  - **PCS 接口**: 开发环境地址更新为测试环境

### TAEI-3098: 图片验真唯一码入库前增加重复检查
- **负责人**: 马斌
- **相关提交**: mabin 10 条 (light-service 8 + finance-service 3 + light-openapi-service 5 + light-report-service 4)
- **涉及仓库**: rrsjk-light-service, rrsjk-finance-service, rrsjk-light-openapi-service, rrsjk-light-report-service
- **变更内容**:
  - `LightImageVerificationServiceImpl`: 入库前通过 `queryLastedByUniqueKey` 查询是否已存在，存在则返回错误
  - `组串开路电压移除验真`: 组串开路电压图片模板不再需要验真
  - **金蝶SAP相关**: 注释 → Revert → 放开限制（处理历史数据重传金蝶记账）
  - **华融EPC**: 电站状态更新逻辑修复 + 审核流程优化
  - `rrsjk-light-openapi-service`: 中银电站维度查询、招银租后总发电量查询

### TAEI-3063 + TAEI-3017: 广发过程进件
- **负责人**: 刘艺 | **参与人**: 杨辉, 付凯善, 董学强 (TAEI-3063) / 薛荣基, 王希然, 王金浩, 袁睿林, 马金虎 (TAEI-3017)
- **相关提交**: majinhu 15 条 (light-service 14 + admin-web 4), wangxiran 5 条 (light-service)
- **涉及仓库**: rrsjk-light-service, rrsjk-admin-web
- **变更内容**:
  - 并网进件: 电厂编号、电压等级校验 + 商务审核通过后修改并网推送状态
  - 合规进件: 房屋屋顶类新增【屋顶测量厚度照片（平屋顶）】模板 `FS_GZFZFR_200020_1110`
  - 并网状态查询 + 保险新增字段（投保方、被保方）
  - 完工进件/并网进件: 拦截退回驳回状态
  - 验收报告图片分类修改
  - CBS 广发电站并网查询 + mergeStatus 字段类型修复
  - 发电量校验新增
  - `first_three_power_at` 从 `light_station` 表返回

### TAEI-3061: 已完工电站方案变更逻辑优化
- **负责人**: 徐晓凤 | **参与人**: 付凯善, 马金虎
- **涉及仓库**: rrsjk-light-service
- **变更内容**: `LightStationPlanChange` 新增 `NO_NEED_AUDIT` 枚举值，完工前方案变更如仅品牌变更则自动审核通过（skipAudit 逻辑，审核人为"王红凯"）

### TAEI-3059: 建站相关优化
- **负责人**: 徐晓凤 | **参与人**: 杨辉, 王希然, 张硕文, 付凯善
- **相关提交**: wangxiran 5 条 (light-service 组件装机功率字段 + light-data-service 首次功率记录时间), 张硕文 2 条 (construction-mini)
- **变更内容**:
  - `light_station` 表新增组件装机功率相关字段和数据填充
  - 逆变器数据新增 `firstThreePowerAt` 字段
  - 经纬度坐标字段支持

### TAEI-2431: CBS 审核时照片旋转查看
- **负责人**: 徐晓凤 | **参与人**: 于淼, 刘飞, 王希然
- **相关提交**: yumiao 12 条 (admin-web image-viewer)
- **变更内容**:
  - admin-web 图片预览增强：滚轮缩放、拖拽平移、单击缩放
  - CSS 旋转后布局尺寸修复
  - 超大图片（>4096px）旋转改用 CSS transform
  - OSS 加 quality,q_75 压缩参数加速加载
  - OSS 旋转前加 auto-orient 消除 EXIF 双旋转

### TAEI-3088: 云南能源局合同扩展区域
- **负责人**: 杨越越 | **参与人**: 包鑫
- **相关提交**: baoxin 3 条 (light-service)
- **变更内容**: 云川合同区域新增"保山市隆阳区"，公司备案合同修改

### TAEI-3074: 商机管理支持页面弃置流程
- **负责人**: 刘艺 | **参与人**: 付凯善, 袁睿林, 马金虎
- **变更内容**: `light_station` 新增弃置状态相关逻辑（`discardStatus`），majinhu 提交中 `feat：默认弃置状态为0`

### 零碳电站相关（跨需求，马斌/dengqiu）
- `rrsjk-light-operation-service` (dengqiu 7 条): 零碳电站接口完善、保发管理、年度保发导出
- `rrsjk-hds-web` (dengqiu 4 条): 零碳电站接口字段补充、保发管理功能完善
- `rrsjk-light-service` (laowang 3 条): 屋顶测量厚度照片展示、招投标管理审核实体类

## 业务链分析（关键变更深读）

### 1. 收入策略重构（TAEI-3076）
```
解钦 station-income-constrain 重构链路:
  └─ 收入模式策略接口 → 工厂类扩展 → 八种模式电站状态校验
     └─ xref3 字段传递电站编码 → SAP 记账关联
        └─ 基金重上收入科目修复 A40→A41
```
**影响面**: 涉及 8 种收入模式（A02/H01/H05/H06 等），策略模式重构后更易扩展新收入模式。

### 2. 工商业自持电站损益报表（TAEI-3043）
```
CmOwnerStationReportServiceImpl 变更链路:
  └─ 总发电量查询 → 充电桩从大数据库取 → 批量查询优化
     └─ 新增 CmOwnerStationReportThirdLog 第三方日志表
        └─ 高压电费查询新增 queryMonth 过滤
           └─ 毛利率除零保护
              └─ PCS 接口地址切换（dev → test）
```
**新增实体**: `CmOwnerStationReportThirdLog` (entity + mapper 214 行), `LightStationPlanChange.StatusEnum.NO_NEED_AUDIT`

### 3. 派单3.1 审核修复（TAEI-3078）
```
LightAuditDispatchTimeConfigService:
  └─ addConfig 返回 Long (configId) → 定时任务使用 configId 补跑积压派单
     └─ 非工作日配置查询增加 status=1 过滤
        └─ CompleteConfirmServiceImpl.auditOk 修复:
           ├─ 电站 ID 非空校验
           ├─ validStopStatusList.contains 取反修复
           └─ 终止流程中电站不允许审核
```

### 4. 图片验真防护（TAEI-3098）
```
LightImageVerificationServiceImpl:
  └─ 入库前 queryLastedByUniqueKey(uniqueImageKey)
     └─ 存在 → 返回错误 "该图片已上传过，请勿重复上传"
     └─ 不存在 → 正常 insert
```
**同时**: 组串开路电压图片模板移除验真要求

### 5. 完工方案变更自动审核（TAEI-3061）
```
LightStationPlanChangeServiceImpl:
  └─ 变更类型=STATION_PLAN_CHANGE 或 ALL
     └─ 变更节点=COMPLETE_BEFORE (完工前)
        └─ checkNeedAudit(oriConfigList, planConfigList) → 仅品牌变更
           └─ skipAudit=true → 自动执行 executePlanChangeCompleteBefore
              └─ status=NO_NEED_AUDIT, auditBy="王红凯"
```

## Neo4j 图谱同步

### 图谱更新状态
- **MCP 写保护**: Neo4j MCP server 为只读模式，写操作被拒绝
- **替代方案**: 通过 Markdown 文件更新 → 每日 02:00 `neo4j-kb-daily-sync.py` 自动同步到图谱

### 已更新的知识库文件（将在下次 02:00 同步到图谱）
| 文件 | 更新内容 | 新增实体 |
|---|---|---|
| `data/tables.md` | +31 行：工商业报表表、派单配置表、图片验真表 | Table: cm_owner_station_report_third_log (新) |
| `data/java-enums.md` | +7 行：LightStationPlanChange.StatusEnum.NO_NEED_AUDIT | Enum: NO_NEED_AUDIT (新) |
| `domains/station-lifecycle.md` | +25 行：方案变更自动审核、共享支付账单查询 | 业务规则 2 条 |
| `domains/approval.md` | +16 行：派单3.1 配置优化与审核 Bug 修复 | 业务规则 1 条 |
| `domains/cm-business.md` | +24 行：工商业自持电站损益报表 | 实体 1 条 + 风险 3 条 |
| `domains/income-mode-strategies.md` | +13 行：SAP 记账 xref3 电站编码关联 | 业务规则 1 条 |

### 待图谱同步的 Cypher 操作（下次 02:00 自动执行）
```cypher
-- 新增表
MERGE (t:Table {name:"cm_owner_station_report_third_log"})
SET t.database="rrsjk_light", t.source="TAEI-3043", t.description="工商业自持电站损益报表第三方日志表"

-- 补全已有表属性
MATCH (t:Table {name:"cm_owner_station_white_list"}) SET t.database="rrsjk_light", t.source="TAEI-3043"
MATCH (t:Table {name:"light_audit_dispatch_time_config"}) SET t.database="rrsjk_light", t.source="TAEI-3078"

-- 新增枚举
MERGE (e:Enum {name:"LightStationPlanChange.StatusEnum.NO_NEED_AUDIT"})
SET e.value="NO_NEED_AUDIT", e.label="无需审核", e.source="TAEI-3061"
```

## 代码质量风险

| 风险类型 | 位置 | 描述 | 建议 |
|---|---|---|---|
| 硬编码审核人 | LightStationPlanChangeServiceImpl | skipAudit 时 auditBy="王红凯" 硬编码 | 改为配置化或系统账号 |
| 逻辑取反修复 | CompleteConfirmServiceImpl | validStopStatusList.contains 取反是事后修复，上线前是否测试 | 补充单元测试 |
| SAP 服务注释/Revert | finance-service + light-service | 马斌多次注释/Revert 金蝶服务，历史数据重传逻辑复杂 | 确认生产环境最终状态 |
| PCS 接口地址 | application-dev.yml | 开发环境地址改为测试环境，需确认发版前是否回切 | 检查 prod 配置 |
| 基金科目变更 | 解钦 | A40 → A41 科目变更，需确认财务是否已同步 | 财务确认 |

## 图谱更新执行
