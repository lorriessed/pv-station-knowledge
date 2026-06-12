# 政策与营销奖励

更新时间: 2026-05-10

## 已确认知识

### 政策收入类型
政策收入已知包括 14 类：逆变器费用补贴、营销政策完成段、营销政策启用段、并网月度规模、并网时效户用、并网时效项目、并网时效负向、安装提升、新商政策、营销 2.0 A 段、营销 2.0 B 段、正负激励、服务商共建费、新商完成政策。

### SAP 凭证规则
集团外正向使用 B15，集团外逆向使用 B16；集团内正向使用 A56，集团内逆向使用 A44。客户编码以 9 开头视为集团内。

### 税率
政策收入相关税率为 9%，电费相关税率为 13%。

## 营销奖励漏斗功能下线 (TAEI-3176/3177, 代码明确证明, 2026-06-04)
**来源**: `rrsjk-light-service/LightStationEnableRewardJobServiceImpl.java` (龙龙/商轶龙, commit: 0f1fa502fd)
- **下线范围**: 营销奖励暂缓单、分段( PROP1/PROP2 双节点)、漏斗三个功能全部下线
- **修改位置**: `LightStationEnableRewardJobServiceImpl.java`
  - 注释掉 `billFunnelCacheService.checkIfPendingListNeeded()` 漏斗检查逻辑
  - 注释掉 `intoCache()` 暂缓单生成逻辑（金额检查+缓存单）
  - 新奖励直接生成 100% 比例的 COMPLETED 节点奖励
  - 保留 `confirmEnableNode()` 和 `intoCache()` 方法本身，用于处理历史已分段数据
- **历史兼容**: 旧代码注释保留（不删除），`confirmEnableNode` 方法完整保留处理历史 ENABLE 分段数据
- **修改人**: 商轶龙（需求TAEI-3176注释标注），龙龙提交代码
- **分支**: `origin/20260520_longlong_pub_build_policy`

---

## 营销奖励政策类型
营销奖励包括 MONTH_POWER、BN_AGEING、BN_AGEING_PROJECT、BN_AGEING_NEGATIVE、INSTALL_ADVANCE。

### 防重
营销奖励存在电站、订单、组件 SN 三级防重。

### 年度规模阶梯政策 (2025-12-25 初始创建 + 2026-04-28~04-30 升级)
- **来源(初始)**: `rrsjk-light-service` + `rrsjk-merchant-web` (需求 TAEI-2788, commits 8ade82b/16af8b4/580ec61, 2025-12-25~26, 解钦/A2001357/龙龙)
- **初始创建内容**:
  - **实体体系**: `LightAnnualScalePolicy`(主表) → `LightAnnualScalePolicyDetail`(规则明细) → `LightAnnualScalePolicyStaging`(服务商年度暂存总表) → `LightAnnualScalePolicyStagingDetail`(电站级暂存明细) → `LightAnnualScalePolicyMonthly`(服务商月度暂估) → `LightAnnualScalePolicyMonthlyDetail`(电站级月度暂估详情)
  - **主表关键字段**: policyNo, policyName, executionYear, executionStartDate/StopDate, depositThreshold(保证金门槛), minPolicyScale/maxPolicyScale/stepScale(阶梯规模), monthPolicyAmount(月度暂估单价), maxPolicyAmount(最大兑现单价)
  - **暂存总表**: merchantId/merchantCode/merchantName, policyId, year, totalCapacity(累计并网总容量W), totalEstimateAmount(累计暂估), totalRealAmount(实际兑现), diffAmount(差额=实际-暂估), settled(是否兑现), sapPurchaseGenerated(SAP采购单是否生成), ceilingReached(是否封顶), currentUnitPrice(当前适用单价)
  - **月度暂估**: status状态机(0-未核算, 1-已核算/已暂估, 2-已兑现, 3-已冲销), 含冲销原因/时间、兑现时间
  - **月度暂估详情**: 每电站每月一条, 含capacity(并网容量W), estimateAmount(暂估金额), voucher/reserveVoucher/costVoucher(SAP凭证号)
  - **阶梯规则明细**: minScale/maxScale(达标规模区间), rewardAmount(奖励金额), formula(计算公式)
  - **Dubbo服务**: lightAnnualScalePolicyService, lightAnnualScalePolicyStagingService 通过 service.xml 发布
- **商户端API** (`rrsjk-merchant-web` → `LightAnnualScalePolicyController`):
  - `GET /annualScalePolicy/getCurrentPolicy.do` — 获取当前年度生效政策(按登录用户服务商身份)
  - `GET /annualScalePolicy/getMySettleInfo.do?year=` — 获取当前服务商年度累计奖励信息
  - `GET /annualScalePolicy/findByExecuteYear.do?executeYear=` — 按年度查询政策详情
- **月度暂估→兑现→SAP流程** (代码明确证明):
  - 月度暂估按服务商+月份聚合, 计算当月新增并网容量和暂估金额
  - 暂估通过SAP生成领用凭证(voucher)、冲销凭证(reserveVoucher)、成本凭证(costVoucher)
  - 年度结束后进行实际兑现, 计算差额(diffAmount = 实际 - 暂估), 多退少补
  - SAP采购单生成失败时记录 sapGenerateError
- **中银交易收益结算** (TAEI-2753): `ZhongYinTradeIncomeSettleService` Dubbo服务 (commit d9858ee, 龙龙, 2025-12-23)
  - 功能: 数据导入(importSettleData)、确认上收入(confirmIncome)、批次删除(deleteByBatchNo)、冲销后处理(reverseAfter)、SAP定时任务(incomeSapJob)、电站上收入校验(checkIncomeByStationCode)、收入冲销(incomeReverse)
- **超期考核政策区域过滤** (TAEI-2758): `LightOverduePolicyAreaService` Dubbo服务 (commit d9858ee, 龙龙, 2025-12-23)
- **月度暂估体系**: 支持月度暂存(staging)和月度暂估(monthly)两层管理
  - 暂存列表: `/annualScalePolicy/stagingList.html` + `stagingDatagrid.json`
  - 暂估列表: `/annualScalePolicy/monthlyList.html` + `monthlyDatagrid.json`
  - 暂估详情: `/annualScalePolicy/monthlyDetail.html` + `monthlyDetail.json`
- **自动核算**: 手动触发当前月/指定月核算 `autoCalculate.json` / `autoCalculateByMonth.json`
- **实际兑现**: 确认兑现 `confirmRealSettle.json`、冲销月度暂估 `cancelMonthlyEstimate.json`
- **报表**: 年度兑现报表 `reportList.html` / `reportDatagrid.json`
- **导出**: 月度暂估结果导出 `monthlyExport.do`
- **780W 模块类型**: 2026-04-30 新增支持 (commit c19b3cd)
- **790W 模块类型**: 2026-06-01 新增支持 — `rrsjk-light-service/LightEnablePolicyItem.java` (commit 87abb470, 龙龙) + `rrsjk-admin-web/lightEnablePolicyAdd.ftl` / `lightEnablePolicyEdit.ftl` (commit 30957cd0)

### 电站启用奖励 (代码明确证明)
**来源**: `rrsjk-light-service` → `LightStationEnableRewardJobServiceImpl.java`, `LightStationEnableRewardDao.java`, `LightStationEnableReward.xml`, `EnableRewardRegisterListener.java`, `LightEnablePolicyItem.java` (commits b8731bd/f9b21b4/736f9c0/1957d32/0986922, 2026-05-12)
- 新增启用节点奖励自动确认功能
- 修复奖励启用任务中的异常处理问题
- 修正启用奖励查询中的站点代码过滤条件
- 优化电站完成奖励确认MQ监听器逻辑
- 添加725W模块类型支持（`LightEnablePolicyItem`）

## 待确认
- 每类政策收入的启用条件、计算公式、适用资方。
- 越秀、中核、华融等资方特殊政策规则。
- 年度规模阶梯政策的暂估→兑现具体核算逻辑和 SAP 记账规则。

---

## 风电产值法兼容1.0 (代码明确证明, 2026-05-19)
**来源**: `rrsjk-light-service` → `CmLightProjectIncomePolicyServiceImpl.java`, `CmLightProject.java`, `CmNode.java` (commit 704eff2a, 解钦, 2026-05-18)
**需求**: TAEI-3107 【风电】风电产值法兼容1.0

- **新增业务域**: 风电(wind electric) — 首次接入工商业政策体系
- **Entity 变更**:
  - `CmLightProject` +30行风电相关字段
  - `CmLightProjectIncomePolicy` +64行风电政策字段
  - `CmLightProjectIncomePolicyItem` +12行
  - `CmNode` +69行节点管理扩展
- **Service 重构**: `CmLightProjectIncomePolicyServiceImpl` 大规模重构 (+206/-61行)
- **测试**: 新增 `CmWindPowerIntegrationTest` (301行) — 完整测试覆盖
- **Mapper**: CmLightProjectIncomePolicy.xml +36, CmLightProjectIncomePolicyItem.xml +34, CmNode.xml +16
- **前端**: admin-web 新增"工商业收入政策配置"新增按钮
- **推断**: 兼容1.0模式意味着支持旧版风电项目数据迁移

---

## 电站收入限制策略重构 (代码明确证明, 2026-05-19)
**来源**: `rrsjk-light-service` → 8种资方模式的 ServiceImpl (commits e4982fee, 04049063, 解钦, 2026-05-12~14)

- **设计模式**: 策略接口 + 工厂类扩展
- **覆盖8种资方模式**:
  - HuaRongTradeIncomeSettle (华融)
  - LightFundSettle (基金)
  - LightHdIncome (户电)
  - LightStationYuexiuSettle (越秀)
  - LightZhSettle (ZH)
  - ZhaoYinTradeIncomeSettle (招银)
  - ZhongYinTradeIncomeSettle (中银)
  - PuYinTradeIncomeSettle (浦银)
- **重构内容**: 电站不同模式是否上收入的策略判断，每种模式新增 Dao + Service 方法
- **校验增强**: 八种模式导入收入时校验电站状态

---

## A端政策结算逻辑调整 (代码明确证明, 2026-05-19)
**来源**: `rrsjk-light-service` (commits d73aba1d, eb8bd383, c0935ef2, 解钦, 2026-05-14~18)
**需求**: TAEI-3089 【结算】A端政策结算逻辑调整

- **基金科目修复**: `FundStationIncomeHandleStrategy` 安装费科目从 A40 修正为 A41
- **电站回退**: `ReverseUseStrategy` 兼容完工前领用不创建SO出库队列的情况
- **越秀租金修复**: `LightYuexiuIncomeBillJobServiceImpl` 租金收益拉取+列表展示 (+110/-52行)

---

## A 段政策按省份区分 (代码明确证明, 2026-06-03)

**来源**: `rrsjk-admin-web` → `LightInstantRewardController.java`, `LightInstantRewardPolicyController.java`, `LightInstantRewardPolicyMonthController.java` (commits by 龙龙, 2026-05-13 ~ 2026-06-03, merge #584 from `20260601_longlong_A段政策按省份区分`)
**最新提交**: commit fcb2414 (龙龙, 2026-06-03) — Mapper SQL修复: columns/create/batchInsert/update 均添加 `accurate_to_region` 字段

### 字段变更

- **"是否精确到区" → "模式"**: 字段标题从"是否精确到区"改为"模式"，显示值从"是/否"改为"单商单县/单商单省"
  - 影响范围：列表页、新增弹窗、Excel 导入导出
- **新增省市区字段**:
  - `provinceId`/`provinceName`: 省
  - `cityId`/`cityName`: 市
  - `regionId`/`regionName`: 区
  - 影响实体：`LightInstantRewardExcel`, `LightInstantRewardPolicyExcel`, `LightInstantRewardPolicyMonthExcel`
- **Excel 导出**: `LightInstantRewardExcel` 新增 provinceName/cityName/regionName 三列
- **查询筛选**: `LightInstantRewardController` 新增省市区筛选条件（支持按 provinceId/cityId/regionId 或名称模糊匹配）
- **月度合计模式**: "月合计模式"字段完整实现（自身表存储+生成时填充）
- **导入模板**: 模式列添加下拉框选项（单商单省/单商单县）
- **隐藏功能**: 彻底隐藏"并网规模奖励"（JS 层面所有 show() 改为 hide()，涉及 pmAdd.ftl/pmEdit.ftl）
- **移除功能**: 移除 Excel 导出中的下拉选项数据验证功能

### 涉及 Controller

| Controller | 变更 |
|---|---|
| `LightInstantRewardController` | Excel 导出新增省市区列，查询条件新增省市区筛选 |
| `LightInstantRewardPolicyController` | 模式字段变更，省市区字段支持 |
| `LightInstantRewardPolicyMonthController` | 月合计模式字段完整实现 |


## 来源
- Hermes MEMORY.md，2026-05-09 迁移。
- 旧 cron 输出 2026-05-09 提到政策获取由 elecContractId 转向 stationCode，并按屋顶类型取值，待从代码复核。
- rrsjk-admin-web 代码扫描 2026-05-10，年度规模阶梯政策全面升级。

---

## 工商业风电项目计收方法扩展 (代码明确证明, 2026-05-20)
**来源**: `rrsjk-light-service` → `CmLightProject.java`, `CmLightProjectIncomePolicyServiceImpl.java` (commits: 解钦 db25723, 704eff2, 2026-05-19)
**需求**: TAEI-3107 【风电】风电产值法兼容1.0

- **字段重命名**: `CmLightProject.confirmMethod` → `CmLightProject.incomeMethod`（计收方法）
  - 枚举同步重命名: `ConfirmMethodEnum` → `IncomeMethodEnum`
  - 数据库字段: `confirm_method` → `income_method`
- **计收方法枚举值**:
  - `FINAL_INSPECTION` — 终验法（默认）
  - `OUTPUT_VALUE` — 产值确认法
- **业务类型扩展**: `CmLightProject.businessType` 支持 `WIND_POWER`（风电），原有 `LIGHT`（光伏）
- **政策匹配逻辑**: `CmLightProjectIncomePolicyServiceImpl.findPolicyByNodeId()`:
  - 终验法（默认）: 按 nodeId + engineeringType 查找政策
  - 产值确认法: 按 projectCode 查找项目制定政策（需项目级别配置）
- **前端DTO**: `CmLightProjectNewRequest` 新增 `incomeMethod` 字段
- **MyBatis映射**: `CmLightProject.xml` 新增 `income_method` 字段到 resultMap、INSERT、UPDATE 语句
- **兼容处理**: 默认终验法保持向后兼容，不影响已有光伏项目

### 工商业风光电收入政策 (代码明确证明, 2026-05-18~20)
**来源**: `rrsjk-admin-web` → 解钦 commits (cm-wind-electric), `rrsjk-light-service` → cm-wind-electric 相关代码 (commits d07a3cb/621fb47/5f8c717/cd2942a/77d2442/b499350/d6876d0/9c5ec6c/d1971e9, 解钦, 2026-05-18~20, branch: feature-cm-wind-electric)
- **立项预审**: 工商业立项预审页面新增计收方法字段（incomeMethod）
- **收入政策配置**: 工商业收入政策新增功能，支持新增按钮和配置管理
- **导入功能**: 收入政策导入和状态问题处理
- **业务类型**: 支持风电(WIND_POWER)和光伏(LIGHT)两种业务类型
- **计收方法**: 终验法(FINAL_INSPECTION) / 产值确认法(OUTPUT_VALUE)
- **证据等级**: 代码明确证明

### 工商业风电 — 收入政策并行审核与产值收入法 (TAEI-3089等, 2026-05-21 代码明确证明)
**来源**: `rrsjk-light-service` (commits eb6bb79b1b/70d878b337/37a61acc36, 解钦), (commits 34ba647038/3f623d59d0/aebab86a81/ed664f5002, tn_wangb/龙龙), `rrsjk-admin-web` (解钦 + tn_wangb)
- **并行审核方案**: 收入政策支持并行审核（非串行），`feat(cm-wind-electric): 收入政策并行审核方案实现`
- **项目定制政策编码**: 项目定制类型的政策编码自动生成
- **政策状态与子政策**: 收入政策的状态修改 + 生成的子政策字段设置
- **导入校验**: 增加收入政策导入的校验逻辑
- **产值收入法**: 工商业风电项目新增产值收入法确认方式 (tn_wangb)
- **终验法**: 工商业风电项目终验法 (tn_wangb, admin-web)
- **损益报表**: 工商业自持电站损益报表二期优化 (tn_wangb, 5 commits)
- **方案变更**: 方案变更修改功能 (tn_wangb)
- **分支**: `origin/feature-cm-wind-electric`, `origin/20260506-wb-cmOwnerStationReport`, `origin/20260514-wb-planChange`
- **证据等级**: 代码明确证明

### 工商业风电 — 产值收入法进度管控与历史数据处理 (2026-05-25~26 代码明确证明)
**来源**: `rrsjk-light-service` → `CmConstructionProgressAuditServiceImpl.java`, `CmConstructionPlanServiceImpl.java` (commits 8cf41123/f5da1b1b/1d356948/19a4df77, tn_wangb, branch: origin/feature-cm-wind-electric)
- **进度维护限制**: 产值收入法(`OUTPUT_VALUE`)的风电项目暂时只能维护到 100%，不允许填写部分进度
- **进度倍数校验**: 产值收入法项目进度必须是 10% 的倍数
- **已完成进度计算**: 产值收入法项目从 `cm_construction_progress_audit` 表查询 `AUDIT_OK` 状态的记录，累加 `addProgress` 计算已完成进度（非旧版的 stream reduce 方式）
- **历史数据补录** (`historyHandle()` 方法):
  - 遍历所有 `cm_construction_plan_item`，如果已有审核记录则跳过
  - 从 `cm_operate_log` 中查找包含 "100" 的操作日志，提取操作人和操作时间
  - 自动创建 `AUDIT_OK` 状态的进度审核记录，progress=100
  - **业务意义**: 将旧的完工审核状态数据迁移到新的进度审核体系，确保风电产值收入法项目历史数据可用
- **收款里程碑**: 收款里程碑导入要求收入政策配置者为工程经理 (commits c6e4cae6/34c3a147)
- **分支已合并**: `feature-cm-wind-electric` 已合入 master (Merge #661)
- **证据等级**: 代码明确证明

### 公共建筑类电站政策配置 (2026-05-20~21 代码明确证明)
**来源**: `rrsjk-light-service` (commits c3713349f9/ec4aa571aa, 龙龙=王斌), `rrsjk-merchant-web` (commits a35d75b9be/22fd7029e0, 龙龙)
- **政策配置**: 新增公共建筑类电站政策配置功能
- **省份筛选**: 支持按省份ID列表查询即时奖励政策
- **A端政策**: 支持按省市区三级筛选 (accurateToRegion, cityName, regionName)
- **导出增强**: Excel导出新增省市区字段注解和映射
- **Swagger**: 所有筛选参数带Swagger注解，方便前端对接
- **分支**: `origin/20260520_longlong_pub_build_policy`, `origin/feature/202605/regionUnlimit`
- **证据等级**: 代码明确证明

### 政策字典体系 (前端配置证明, 2026-05-22 扫描)
**来源**: `nahui-dicts-serve` → `src/data/apv/policy/` (袁睿林, 2026-03~2026-05)
- `policyMode.js` — 政策模式（60行）
- `policyStandardList.js` — 政策标准
- `policyPointList.js` — 政策积分
- `policyExeStandardList.js` — 政策执行标准
- `documentDetailStatusList.js` — 文档详情状态

### 电站完工匹配政策区位码 (代码明确证明, 2026-05-23 补漏第7期)
**来源**: `rrsjk-light-service` (TAEI-2967, 解钦, 2026-04-10~04-11)
- 电站完工时重新匹配policyCode，区分不同模式、电站类型
- 原policyCode保存到电站信息扩展表中（保留历史记录）
- 电站完工时间和签约时间大于60天才重新匹配新的区位码
- 完工匹配政策区位码回退机制
- 对应需求: TAEI-2967 (完工后终止电站) + 政策匹配优化

### TAEI-3089 A端政策结算逻辑调整 — 政策收入批处理重构 (代码明确证明, 2026-05-28)
**来源**: `rrsjk-light-service` (龙龙=王斌, commit: 3e7fd0baa8, 2026-05-28, branch: yyyyMMdd_longlong_fix)
- **负责人**: 杨越越 | **实际开发**: 王斌(tn_wangb/龙龙) | **参与人**: 商轶龙
- **核心变更**: 政策收入处理器从 `AbstractPolicyIncomeHandler` 重构为 `AbstractPolicyBatchIncomeHandler`
  - `EnablePolicyCompleteIncomeHandlerImpl` — 已完工政策收入处理
  - `EnablePolicyEnableIncomeHandlerImpl` — 已生效政策收入处理
- **批处理模式新增**:
  - `reverseIncomeSapRecord()` — 冲收入账单功能
  - `findCompleteByNotCostVoucherByStationCode()` / `findEnableByNotCostVoucherByStationCode()` — 按电站编码批量查询
  - `findByOrderNo()` — 按订单号查询
  - `findByStationCodeAndNodeType()` — 返回类型从单条改为 List
- **服务层增强**: `LightStationEnableRewardService` 新增 33 行方法
- **Mapper XML**: `LightStationEnableReward.xml` 新增 22 行批量查询 SQL
- **业务语义**: 政策结算从逐条处理改为批处理模式，支持冲正和历史数据兼容
- **关联需求**: TAEI-3089 (A端政策结算逻辑调整) + 方案变更政策回退兼容 (ed4cec51d5)
- **证据等级**: 代码明确证明

---

## TAEI-3190 营销政策预测报表 — 新增预测报表体系 (代码明确证明, 2026-06-11)
**来源**: `rrsjk-light-report-service`, `rrsjk-light-service`, `rrsjk-admin-web` (龙龙=王斌, 28 commits, 2026-06-10~11)
- **负责人**: 薛荣基 | **实际开发**: 王斌(tn_wangb/龙龙)
- **分支**: `origin/20260610_longlong_taei_3190_report_config`
- **业务背景**: 新增营销政策预测报表，支持政策区域快照、低效区域标记、发电汇总报表、Excel导出
- **架构设计**: ODS读 + local写模式，预测数据存储在local库（rrsjk_light_local）而非light主库

### 一期：报表配置管理
- 4个报表配置页面（FTL+JS+Controller）
- `ReportConfigQueryDao` — 报表配置查询DAO（light库）
- Excel DTO + 模板下载 + 省市区ID转换（RegionService）
- Dubbo服务注册到 service.xml
- 20个方法添加 @RequiresPermissions 权限控制

### 二期：市/区发电汇总报表
- Entity/Dao/Mapper/Service/Job 完整链路
- 数据库映射移到local库
- 补充低效区域标记逻辑（regionUnlimit 分支合并）
- 修复代码审计问题：Entity风格、DAO风格、@Transactional、Date→LocalDate

### 三期：营销政策预测报表核心
- **新增实体**: `ReportPolicyForecast` — 政策预测报表实体（local库，127行）
- **新增服务**: `ReportPolicyForecastService` + `ReportPolicyForecastServiceImpl`（353行）
- **新增DAO**: `ReportPolicyForecastDao`（local库，31行）
- **新增Mapper**: `ReportPolicyForecastMapper.xml`（104行SQL）
- **新增定时任务**: `PolicyForecastJob` — 预测报表计算Job
- **内部类**: `ProvinceCityInfo` — 省市区信息封装

### 四期：导出与权限分离
- Phase2导出功能
- 预测报表Excel公式导出
- 权限分离

**数据流**: 政策数据从ODS层读取 → 写入local库 → PolicyForecastJob定时计算 → 前端报表展示/Excel导出
- **证据等级**: 代码明确证明
