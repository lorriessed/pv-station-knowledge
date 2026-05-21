# 政策与营销奖励

更新时间: 2026-05-10

## 已确认知识

### 政策收入类型
政策收入已知包括 14 类：逆变器费用补贴、营销政策完成段、营销政策启用段、并网月度规模、并网时效户用、并网时效项目、并网时效负向、安装提升、新商政策、营销 2.0 A 段、营销 2.0 B 段、正负激励、服务商共建费、新商完成政策。

### SAP 凭证规则
集团外正向使用 B15，集团外逆向使用 B16；集团内正向使用 A56，集团内逆向使用 A44。客户编码以 9 开头视为集团内。

### 税率
政策收入相关税率为 9%，电费相关税率为 13%。

### 营销奖励类型
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

### 公共建筑类电站政策配置 (2026-05-20~21 代码明确证明)
**来源**: `rrsjk-light-service` (commits c3713349f9/ec4aa571aa, 龙龙=王斌), `rrsjk-merchant-web` (commits a35d75b9be/22fd7029e0, 龙龙)
- **政策配置**: 新增公共建筑类电站政策配置功能
- **省份筛选**: 支持按省份ID列表查询即时奖励政策
- **A端政策**: 支持按省市区三级筛选 (accurateToRegion, cityName, regionName)
- **导出增强**: Excel导出新增省市区字段注解和映射
- **Swagger**: 所有筛选参数带Swagger注解，方便前端对接
- **分支**: `origin/20260520_longlong_pub_build_policy`, `origin/feature/202605/regionUnlimit`
- **证据等级**: 代码明确证明
