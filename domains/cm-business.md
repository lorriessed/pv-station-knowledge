# 工商业(CM)业务域

更新时间: 2026-05-26

## 概述

工商业(CM = Commercial)是独立于户用光伏的另一条业务线，涉及项目立项、方案设计、施工进度管理、收入政策配置、投决审核等全流程管理。

## 核心Controller与入口

### CmConstructionProgressAuditController — 施工进度审核 (代码明确证明, 2026-05-26)
**来源**: `rrsjk-admin-web` → `CmConstructionProgressAuditController.java` (commit 012b6f14, tn_wangb, 2026-05-26)
- **路径前缀**: `/cmConstructionProgress`
- **权限**: `cmConstructionProgress:list`, `cmConstructionProgress:audit`, `cmConstructionProgress:export`
- **接口列表**:
  - `list.html` — 施工进度完工列表页面
  - `doList.do` — 分页查询，支持: projectCode, projectName, finishAuditStatus, createdStart/End, auditStart/End
  - `detail.html` — 审核详情页面，展示附件模板、历史附件(按进度百分比分组)
  - `audit.html` — 审核操作页面
  - `audit.do` — 提交审核，`BaseAuditRequset` 入参
  - `projectTrack.html` — 项目跟踪页面，展示项目详情+节点记录+方案计划
  - `doExport.do` — 导出Excel，使用 EasyExcel 分页导出(每页5000条)
- **导出实体**: `CmConstructionProgressExcel` — 包含状态、项目编码、名称、地址、工程类型、进度阶段、节点名称、总进度、新增进度、完工时间/人、审核时间/人、备注
- **附件展示**: 按 `CmNodeAttachmentTemplate` 模板分组展示，支持多文件模式(`ModeEnum.MULTI`)
- **历史附件**: 按 `processStage`(进度百分比) 分组，如 "项目进度50%"

### CmLightProjectIncomePolicyController — 收入政策配置 (代码明确证明, 2026-05-26)
**来源**: `rrsjk-admin-web` → `CmLightProjectIncomePolicyController.java` (解钦, 多个commit, 2026-05-18~26)
- **路径前缀**: `/cmLightProjectIncomePolicy/`
- **权限**: `cmLightProjectIncomePolicy:list`, `cmLightProjectIncomePolicy:update`
- **接口列表**:
  - `list.html` / `doList.do` — 列表查询，支持 policyCode, **policyType**, **status** 筛选
  - `detail.html` — 政策详情，展示政策明细项(CmLightProjectIncomePolicyItem)
  - `update.html` — 政策修改页面
- **导入功能** (2026-05-26 新增):
  - 导入增加表头校验
  - 下载模板增加对业务类型的判断
  - 导入增加对项目的校验
- **新增依赖**: `CmLightProjectService`, `CmNodeService`, `CmIncomePolicyTemplateExcel`
- **并行审核方案** (2026-05-21): 新增 `cmLightProjectIncomePolicyAudit.ftl`

### CmLightProjectSignInfoController — 项目签约信息 (代码明确证明, 2026-05-26)
**来源**: `rrsjk-admin-web` → `CmLightProjectSignInfoController.java` (tn_wangb, commit 012b6f14, 2026-05-26)
- 工商业风电项目终验法相关

### CmLightUseController — 工商业项目使用 (代码明确证明, 2026-05-26)
**来源**: `rrsjk-admin-web` → `CmLightUseController.java` (tn_wangb, commit 012b6f14, 2026-05-26)
- 4行变更，配合终验法功能

### CmNodeController — 节点管理 (代码明确证明, 2026-05-26)
**来源**: `rrsjk-admin-web` → `CmNodeController.java` (解钦, commit 08e979f8, 2026-05-18)
- 3行变更，配合工商业兼容风电

## 关键实体

### CmConstructionProgressAudit — 施工进度审核
- **字段**: projectCode, projectName, address, engineeringType, processStage, processStageName, nodeId, nodeName, totalProgress, addProgress, finishAuditStatus, status, remark, createdAt, createdBy, auditAt, auditBy
- **状态枚举**: `StatusEnum` (通过代码推断，具体值待确认)
- **关联**: `CmLightProject`(项目信息), `CmNodeAttachmentTemplate`(附件模板), `CmConstructionProgressHisAtchDto`(历史附件)

### CmLightProjectIncomePolicy — 收入政策
- **关联**: `CmLightProjectIncomePolicyItem`(政策明细项)
- **筛选维度**: policyType, status

## 前端模板

| 模板文件 | 用途 |
|---|---|
| `cmConstructionProgressAuditList.ftl` | 施工进度审核列表 (326行) |
| `cmConstructionProgressAuditDetail.ftl` | 施工进度审核详情 (296行) |
| `cmConstructionProgressAuditAudit.ftl` | 施工进度审核操作页面 (367行) |
| `cmLightProjectIncomePolicyList.ftl` | 收入政策列表 (515行，大幅修改) |
| `cmLightProjectIncomePolicyDetail.ftl` | 收入政策详情 (140行) |
| `cmLightProjectIncomePolicyUpdate.ftl` | 收入政策修改 (303行) |
| `cmLightProjectIncomePolicyAudit.ftl` | 收入政策审核页面 (187行) |
| `cmLightProjectSimpleDetail.ftl` | 项目简易详情 (947行) |
| `cmLightProjectSetAdd.ftl` | 项目立项新增 |
| `cmLightProjectSetDetail.ftl` | 项目立项详情 |
| `cmLightProjectSetAudit.ftl` | 项目立项审核 |
| `cmLightProjectSetTrack.ftl` | 项目立项跟踪 |
| `cmLightProjectVoteTrack.ftl` | 投决审核跟踪 (含账务信息) |
| `cmLightProjectVoteAdd.ftl` | 投决新增 (含账务信息) |
| `cmLightProjectVoteAudit.ftl` | 投决审核 (含账务信息) |
| `cmLightProjectVoteDetail.ftl` | 投决详情 (含账务信息) |
| `cmLightProjectVoteUpdate.ftl` | 投决修改 (含账务信息) |
| `cmConstructionProgressAudit.ftl` | 施工进度审核 |
| `cmConstructionProgressDetail.ftl` | 施工进度详情 |
| `cmConstructionPlanAudit.ftl` | 施工计划审核 |
| `cmConstructionPlanDetail.ftl` | 施工计划详情 |
| `cmChangeAudit.ftl` | 变更审核 |
| `cmChangeDetail.ftl` | 变更详情 |
| `cmLightUseList.ftl` | 工商业使用列表 |
| `cmNodeList.ftl` | 节点管理列表 |
| `cmLightProjectSignInfoList.ftl` | 项目签约信息列表 |

## 业务特征

### 风电与光伏区分
- 2026-05-26 前端 `nahui-pv.epcb-mini` 增加风电与光伏项目区分
- 收入政策配置、收款里程碑等页面兼容风电业务类型
- 工程类型(`engineeringType`)字段用于区分风电/光伏

### 终验法
- 工商业风电项目采用终验法确认收入
- 涉及 `CmConstructionProgressAuditController` 新增和多个模板文件

### 账务信息模块
- 投决审核页面(Add/Audit/Detail/Update)增加账务信息模块
- EPC项目跟踪页面增加账务信息

### 并行审核
- 收入政策配置支持并行审核方案
- 新增审核页面 `cmLightProjectIncomePolicyAudit.ftl`

## 待确认

- `CmConstructionProgressAudit` 的 `StatusEnum` 完整枚举值
- `engineeringType` 的完整枚举值(WIND/SOLAR等)
- 收入政策 `policyType` 和 `status` 的枚举定义
- 施工进度审核与户用电站完工确认的关系
- 终验法的具体业务规则和触发条件
- `CmConstructionProgressAuditService` 的完整接口定义
- 工商业项目(`CmLightProject`)与户用电站(`LightStation`)的数据模型关系
