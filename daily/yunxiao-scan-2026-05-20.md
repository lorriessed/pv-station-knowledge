# 云效驱动代码学习报告 — 2026-05-20

## 扫描范围
- **云效需求**: 20 个（近7天修改，updateStatusAt >= 2026-05-13）
- **涉及人员**: 孙志男、徐晓凤、王斌、解钦、于淼、付凯善、马金虎、王金浩、商轶龙、杨辉、王希然、袁睿林、姜传德、包鑫、laowang(未知)
- **Git 仓库**: 100 个（扫描35个核心仓库 + CBS仓库）
- **Git 提交**: 171 个（去重后）

## 需求 → 代码关联

| 需求号 | 标题 | 状态 | 负责人 | 开发人员 | 相关提交数 | 涉及仓库 |
|---|---|---|---|---|---|---|
| TAEI-3066 | 展会-运维大屏 | 开发中 | 高媛 | 孙志男 | 21 | rrsjk-light-operation-service, rrsjk-light-service, rrsjk-trade-service |
| TAEI-3112 | 招银-运维相关数据信息接口开发 | 开发中 | 高媛 | 孙志男 | (同上) | rrsjk-light-operation-service, rrsjk-trade-service |
| TAEI-3100 | 【报表】自持电站报表优化 | 测试完成 | 徐晓凤 | 王斌, 徐晓凤 | 18 | rrsjk-light-service, rrsjk-admin-web |
| TAEI-3085 | 【收入】增加上收限制 | 测试完成 | 杨越越 | 解钦 | 23 | rrsjk-light-service, rrsjk-admin-web |
| TAEI-3083 | 【建站】完工前变更方案审批流变更 | 开发中 | 徐晓凤 | 王斌, 付凯善 | (同上) | rrsjk-light-service, rrsjk-admin-web |
| TAEI-3044 | 【户用光伏】华融上收入多记质保金 | 待测试 | 刘艺 | 于淼 | 36 | rrsjk-light-service, rrsjk-admin-web, rrsjk-light-data-service |
| TAEI-3068 | 【户用光伏】广发业主信息更正接口 | 开发中 | 刘艺 | 付凯善, 马金虎, 袁睿林 | 32 | rrsjk-light-service, rrsjk-admin-web |
| TAEI-3053 | 【建站】一商做全国 | 开发中 | 杨越越 | 于淼, 姜传德, 解钦, 商轶龙, 包鑫 | 多作者 | rrsjk-light-service, rrsjk-admin-web, system-service |
| TAEI-3107 | 【风电】风电产值法兼容1.0 | 开发中 | 杨越越 | 王斌, 解钦, 杨辉 | (同上) | rrsjk-light-service, rrsjk-admin-web |
| TAEI-3102 | 【户用光伏】CBS招投标流程 | 开发中 | 刘艺 | 王金浩 | 9 | rrsjk-light-service, rrsjk-admin-web, rrsjk-light-report-service |
| TAEI-3109 | 【P1】光伏对账单查询性能优化 | 阻塞 | 王希然 | 王希然 | 11 | rrsjk-light-service, rrsjk-light-data-service |
| TAEI-3087 | 【资方】国电投账号 | 已完成 | 杨越越 | 于淼, 王希然 | (同上) | rrsjk-light-service, rrsjk-admin-web |
| TAEI-3089 | 【结算】A端政策结算逻辑调整 | 测试中 | 杨越越 | 商轶龙 | sparse | - |
| TAEI-3042 | 【政策】大商政策暂估及兑现逻辑 | 已完成 | 杨越越 | 商轶龙 | sparse | - |
| TAEI-3117 | 运维商押金/备件押金上线集团FAP | 待处理 | 高媛 | 孙志男 | (未开始) | - |
| TAEI-3114 | 【结算】项目类新建公共租赁类政策 | 待处理 | 杨越越 | 商轶龙 | (未开始) | - |
| TAEI-3079 | 【电费】电费收益相关优化 | 开发中 | 徐晓凤 | 王金浩, 付凯善 | 9(龙龙) | rrsjk-light-service, rrsjk-admin-web |
| TAEI-3090 | 【结算】公共建筑立项兼容其他政策 | 已取消 | 杨越越 | - | - | - |

## 业务链分析

### 1. TAEI-3066 展会-运维大屏 (孙志男)
**完整业务链**:
- **数据模型层** (`rrsjk-light-operation-service`):
  - `OperationScreenModel` — 运维会展大屏核心指标（健康等级、发电量、容量、功率、在线/离线/异常统计）
  - `OperationElecMonthModel` — 资方年月发电量统计
  - `OperationModelStation` — 新增 `specialFlag` 资方标识字段
  - `ComprehensiveHealthScore` — 健康等级枚举
- **业务逻辑层**: 分页查询、CRUD 完整服务
- **数据访问层**: MyBatis Mapper XML + DAO 实现
- **前端展示**: admin-web 运维大屏页面
- **关联需求**: TAEI-3112 招银运维接口也在同一分支开发

### 2. TAEI-3107 风电产值法兼容1.0 (解钦)
**完整业务链**:
- **数据库变更**: `cm_light_project.confirm_method` → `income_method`（字段重命名）
- **枚举变更**: `ConfirmMethodEnum` → `IncomeMethodEnum`
- **DTO**: `CmLightProjectNewRequest` 新增 `incomeMethod` 字段
- **Service**: `CmLightProjectIncomePolicyServiceImpl.findPolicyByNodeId()` — 两种计收方法的政策匹配逻辑：
  - 终验法（默认）: 按 nodeId + engineeringType 查找
  - 产值确认法: 按 projectCode 查找项目定制政策
- **业务类型**: `CmLightProject.businessType` 扩展支持 `WIND_POWER`
- **前端**: admin-web 工商业立项预审页面新增计收方法字段
- **兼容性**: 默认终验法保持向后兼容

### 3. TAEI-3085 收入增加上收限制 (解钦)
**完整业务链**:
- **性能优化**: 8个资方 SettleService 的 Assert 错误消息改为 lambda 懒加载
- **业务语义**: 收入导入时跨业务模式冲突检测 — `incomeConflicts.containsKey(stationCode)`
- **涉及资方**: 华融、基金、弘德、越秀、中核、普银、招银、中银
- **冲突检测逻辑**: 检查电站是否已在其他业务模式下存在收入记录，防止重复上收入

### 4. TAEI-3083 完工前变更方案审批流变更 (解钦)
**完整业务链**:
- **核心修复**: 电站回退重新领用时兼容「完工前领用」场景
- **完工前领用特点**: 不创建 SO 出库队列，冲销时不需处理出库
- **基金科目**: A40 → A41（安装费科目调整）
- **状态流转**: `BusinessStatusMode.offLineChoose` 参数改为 `@Nullable`，支持线下验收与技术/商务并行
- **审核流程**: `CompleteConfirmServiceImpl.stationAudit()` 增加 stationCode 字段设置

### 5. TAEI-3044 华融B43模式上收入记质保金 (于淼)
**完整业务链**:
- **业务规则**: B43 融资租赁模式下，收入结算时额外记一笔质量保证金账
- **计算公式**: DMBTR = 收入金额(应收账款) × 质量保证金比例
- **服务**: `HuaRongIncomeQualityGuaranteeServiceImpl`
- **修复**: `findLatestByStationCode` 使用 B43 记录的电站码而非 entity 的
- **前端**: admin-web 华融质保金页面权限点复用华融交易收入

### 6. TAEI-3102 CBS招投标流程 (laowang/王金浩)
**完整业务链**:
- **实体**: `TenderManagmentAudit` — 招投标管理审核
- **项目分类**: FD(风电) / GSY(工商业) / HYEPC(户用EPC) / YW(运维) / LTSJ(零碳世家)
- **多级审核**: 附件审核 → 招标文件审核 → 价值链材料审核 → 初审标书 → 终审标书
- **地理信息拆分**: 代理商地区 + 电站地区分别记录（2.0版本）
- **零碳能源**: `ZeroCarbonEnergyAgentRequest` 地区字段从单套拆分为双套

### 7. TAEI-3100 自持电站报表优化 (王斌)
**完整业务链**:
- **报表服务**: `CmOwnerStationReportServiceImpl` — 工商业自持电站损益报表
- **二期需求**: 报表逻辑优化、数据查询调整
- **前端**: admin-web `CmOwnerStationReportController` — 按年/月拆分接口（已在之前扫描中记录）

## 知识库更新

| 操作 | 文件 | 内容摘要 |
|---|---|---|
| 追加 | `domains/settlement.md` | 华融B43质保金逻辑、收入Assert懒加载优化、电站回退领用兼容、中核收入限制修复、基金科目A40→A41 |
| 追加 | `domains/station-lifecycle.md` | 线下验收结合技术商务并行状态流转优化 |
| 追加 | `domains/operation-and-data.md` | 运维会展大屏数据模型、资方年月发电量统计表 |
| 追加 | `domains/policy.md` | 工商业风电项目计收方法扩展（confirmMethod→incomeMethod） |
| 追加 | `domains/zero-carbon-station.md` | 招投标管理审核模块、零碳能源代理商地区字段拆分 |
| 追加 | `data/enums.md` | 计收方法枚举、招投标审核状态枚举、项目分类枚举 |
| 追加 | `data/tables.md` | 运维会展大屏相关表、cm_light_project字段变更、招投标管理审核表 |

## 新发现

### Git Author 别名补充
- **laowang** (1162359451@qq.com): CBS/零碳团队开发，高频提交。实际身份为 CBS 团队成员，负责招投标管理和零碳能源模块
- **龙龙**: 确认为王斌（`tn_wangb龙龙` 的简称），本次扫描发现9个提交

### 业务逻辑发现
1. **收入冲突检测覆盖8大资方**: 华融、基金、弘德、越秀、中核、普银、招银、中银 — 所有资方统一使用 `incomeConflicts` 进行跨模式收入冲突检测
2. **计收方法从 confirmMethod 重命名为 incomeMethod**: 反映业务语义从"确认方式"到"计收方法"的转变，与风电产值法需求相关
3. **完工前领用特殊处理**: 电站在完工前领用时不创建 SO 出库队列，这是电站生命周期中的一个关键分支逻辑
4. **代理商地区与电站地区分离**: 零碳能源业务中，代理商所在地和电站安装地可能不同，需要分别记录

### 需求状态分布
- 开发中: 8 个
- 测试中/测试完成/待测试: 5 个
- 已完成: 2 个
- 待处理/待评审: 4 个
- 阻塞: 1 个 (TAEI-3109 性能优化)
- 已取消: 1 个 (TAEI-3090)
