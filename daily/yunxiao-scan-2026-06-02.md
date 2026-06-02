# 云效驱动代码学习报告 — 2026-06-02

## 扫描范围
- **云效需求**: 31 个（updateStatusAt >= 2026-05-26）
- **涉及开发人员**: 14 人（代继宁、马斌、王斌(tn_wangb)、德(syj)、马金虎、解钦、李龙、龙龙、包鑫、李培龙、张硕文、杨辉、魏秋阳、孙志男）
- **Git 提交**: 994 条（含 BFF 层 436 条噪音）
- **核心业务提交**: 271 条（排除 BFF 后）

## 需求 → 代码关联

| 需求号 | 标题 | 负责人 | 实际开发 | 相关提交数 | 涉及仓库 | 状态 |
|---|---|---|---|---|---|---|
| TAEI-3146 | 发电数据取数逻辑切换大数据平台 | 于淼 | 马金虎 | 22 | light-data-service, admin-web | 开发中 |
| TAEI-3092 | 农户租金类个税报表及记账 | 杨越越 | 代继宁 | 21 | light-service, admin-web | 测试中 |
| TAEI-3107 | 风电产值法兼容1.0 | 杨越越 | 王斌/解钦 | 32 | light-service, admin-web, merchant-web | 已完成 |
| TAEI-3159 | 工商业放开产值确认法收入闸口 | 杨越越 | 王斌 | 1 | light-service | 已完成 |
| TAEI-3168 | 零碳适家退商材料申请流程 | 刘艺 | 王斌 | 2 | light-service | 开发中 |
| TAEI-3157 | 金蝶冲销接口优化 | 马斌 | 马斌 | 5 | finance-service, light-service | 已完成 |
| TAEI-3165 | 海外系统BUG修改 | 杨越越 | 马斌 | 4 | admin-web, light-service | 已完成 |
| TAEI-3145 | 逆变器详情速度优化 | 于淼 | 马金虎 | 2 | admin-web | 已完成 |
| TAEI-3141 | 优化电站连续三天发电刷新逻辑 | 于淼 | 马金虎 | 2 | admin-web, light-data-service | 已完成 |
| TAEI-3079 | 电费收益相关优化 | 徐晓凤 | 王金浩(yumiao) | 3 | light-service, admin-bff | 待测试 |
| TAEI-3125/3126 | 商户通自定义字段+图片旋转 | 徐晓凤 | 袁睿林(零提交) | 0 | - | 待测试 |
| TAEI-3101 | 招银组件功率匹配价格 | 刘艺 | 李龙 | 0 | - | 已完成 |
| TAEI-3130 | 技术部巡检需求 | 徐晓凤 | 王金浩(yumiao) | 25+ | admin-bff(400+) | 开发中 |
| TAEI-3057 | 审核驳回按单张图片驳回 | 徐晓凤 | 杨辉/王希然 | - | - | 开发中 |
| TAEI-3150 | 大商政策监控报表1.5期 | 商轶龙 | yumiao | 436 | admin-bff | 开发中 |
| TAEI-3005 | 金蝶总账接口开发 | 杨越越 | 商轶龙/马斌 | 23+ | light-report-service, finance-service | 测试完成 |
| TAEI-3102 | CBS招投标流程 | 刘艺 | laowang | 25 | admin-bff | 测试中 |
| TAEI-3123 | 完工驳回支持驳回到方案审核 | 徐晓凤 | 魏秋阳/王希然 | - | - | 已完成 |
| TAEI-3163 | 股转后A51/A48账单处理 | 高媛 | 孙志男 | 2 | hds-web, light-operation-service | 已完成 |
| TAEI-3053 | 一商做全国 | 杨越越 | 于淼/解钦/商轶龙/包鑫 | - | - | 测试完成 |
| TAEI-2728 | AI识别房产证 | 杨越越 | 魏秋阳/陈国栋/马斌 | 18+ | admin-web, light-service | 测试完成 |
| TAEI-3066 | 展会运维大屏 | 高媛 | 魏秋阳/孙志男/李培龙 | 18+ | hds-web, light-operation-service | 已完成 |
| TAEI-3044 | 华融上收入多1个账(B43质量保证金) | 刘艺 | 于淼 | - | - | 已完成 |

## 重点业务链分析

### 1. TAEI-3146 发电数据取数逻辑切换大数据平台（重大架构变更）
**开发**: 马金虎 | **提交**: 22+ | **分支**: origin/feature/202605/ods_electroc_data

**完整业务链**：
```
admin-web (前端页面)
  ↓ Dubbo
light-data-service (发电数据服务)
  ├─ 新增 ADS 数据源 (MybatisConfig.getAdsDataSource())
  ├─ 新增 AbstractAdsDao 基类
  ├─ 新增 6 张 ADS 实体类 (AdsReportInveterChartDay/Month/Year/Total/PacDay)
  ├─ 新增 6 张 ADS Mapper XML (mybatis/mapper/ads/)
  ├─ 新增 *Ads() 方法（与原DWS方法并行）
  ├─ 字段修正: inveter_sn → inverter_sn
  └─ 解绑定时任务 (6 commits, 2026-06-01)
```

**关键表映射**：
| ADS 表 (新) | DWS 表 (旧) | 数据库 | 差异 |
|---|---|---|---|
| ads.green_energy_report_light_inverter_chart_day | report_inveter_chart_day | ads vs rrsjk_light_data | 无 id 字段 |
| ads.green_energy_report_light_inverter_chart_month | report_inverter_chart_month | ads | 无 id 字段 |
| ads.green_energy_report_light_inverter_chart_year | report_inverter_chart_year | ads | 无 id 字段 |
| ads.green_energy_report_light_inverter_chart_total | report_inverter_chart_total | ads | 无 id 字段 |
| ads.green_energy_report_light_inverter_pac_chart_day | report_inverter_pac_chart_day | ads | 无 id 字段 |
| ads.green_energy_report_light_station_realtime_current | light_station_elec | ads | 新增 |

**影响面**：逆变器图表查询、电站发电列表/详情、月报表、连续三天发电逻辑。当前新旧两套数据源并行，需关注切换时机。

### 2. TAEI-3107 风电产值法兼容1.0 + TAEI-3159 工商业收入闸口放开
**开发**: 王斌(tn_wangb) | **提交**: 32+ | **分支**: origin/feature-cm-wind-electric

**代码变更核心**：
- **字段解耦**: `nodeFinishPct` 替代 `majorMaterialUsePct`/`auxiliaryMaterialUsePct`/`constructionServiceUsePct`/`designServiceUsePct`
  - 影响文件: `CmGvsServiceImpl.java`, `CmLightUseServiceImpl.java`
  - 业务语义: 工商业辅材领用、施工服务领用、设计服务领用统一使用节点完成百分比
- **收入闸口放开**: `CmProductionValueIncomeServiceImpl.java` 注释掉 3 项收入超限校验
  - 注释掉的校验: 材料收入、施工服务收入、设计收入超出产值不可提交
  - 保留的校验: 材料成本超限校验（仍有效）
  - 业务影响: 工商业项目上收入时不再受产值金额上限约束

### 3. TAEI-3092 农户租金类个税报表及记账
**开发**: 代继宁 | **提交**: 21 | **分支**: origin/featrue-20260525-rentTaxReport/TAEI-3092

**业务链**：
- `light-service`: 租金个税批量确认接口、SAP记账接口适配、定时任务月份计算优化
- `admin-web`: 租金个税明细/合计导出、记账按钮显示逻辑、批量确认接口
- 关键修复: 执行不存在的 SQL 导致报错 → 已修复
- SAP 记账: 记账成功后错误信息置空、交易类型传参修改

### 4. TAEI-3157 金蝶冲销接口优化 + TAEI-3005 金蝶总账接口
**开发**: 马斌 | **分支**: origin/20250525-jindieRepeatFix

**关键变更**：
- 金蝶凭证过账功能: 先调用过账接口再执行冲销 (`postingVoucherForReverse`)
- 新增 `postVoucherUrl` 配置
- SAP 同步: 日志 orderId 替换为 orderNo、重复校验和错误处理优化
- 消息长度限制: 防止数据库字段溢出

### 5. 电站转单功能持续开发（德/syj）
**分支**: origin/station-transfer-sub-account-20260525
**新发现**: 
- 新增街道字段 (`c7387433`)
- 按负责人/承接商名称查询功能
- 商户端转出转入接口权限校验
- 转单新参数传递

### 6. TAEI-3168 零碳适家退商材料（早期开发）
**开发**: 王斌(tn_wangb) | **分支**: origin/20260601-zeroCarbonMerchantQuit/TAEI-3168
**变更**: `CmLightProject.P6` 枚举修复空格 + `LightEpcStationModel` 写入项目编码/名称
**注意**: 当前仅有少量提交，退商材料核心逻辑尚未开始

## 知识覆盖分析

### 已覆盖（图谱已有，仅增量更新）
| 需求号 | 标题 | 图谱覆盖情况 | 学习深度 |
|---|---|---|---|
| TAEI-3146 | 发电数据切换大数据平台 | ✅ 已覆盖(Domain:逆变器, 5 ADS表) | 增量更新 |
| TAEI-3092 | 租金个税报表 | ✅ 已覆盖(Domain:结算) | 增量更新 |
| TAEI-3107 | 风电产值法 | ✅ 已覆盖(Domain:工商业) | 增量更新 |
| TAEI-3159 | 收入闸口放开 | ✅ 已覆盖(Domain:工商业) | 增量更新 |
| 电站转单 | 持续开发中 | ✅ 已覆盖(Domain:电站生命周期) | 增量更新 |

### 未覆盖（新知识/盲区，需重点学习）
| 类型 | 名称 | 原因 |
|---|---|---|
| 需求 | TAEI-3168 零碳退商材料 | 仅早期少量提交，核心逻辑未开发 |
| 需求 | TAEI-3125/3126 商户通自定义+图片旋转 | 负责人袁睿林零Git提交，实际开发者未识别 |
| 需求 | TAEI-3101 招银组件功率匹配 | 李龙的近期提交全是AI智能对账，非招银组件 |

## Neo4j 图谱更新

| 操作 | 实体类型 | 实体名称 | 关联关系 |
|---|---|---|---|
| 新增 | Table | report_inveter_chart_day | database=rrsjk_light_data, source=TAEI-3146 |
| 新增 | Table | report_inveter_pac_chart_day | database=rrsjk_light_data, source=TAEI-3146 |
| 更新 | Table | report_inveter_chart_month | database=rrsjk_light_data, source=TAEI-3146 |
| 更新 | Table | report_inveter_chart_total | database=rrsjk_light_data, source=TAEI-3146 |
| 更新 | Table | report_inveter_chart_year | database=rrsjk_light_data, source=TAEI-3146 |
| 更新 | Table | green_energy_light_station_realtime_current | database=ads, source=TAEI-3146 |
| 更新 | Table | green_energy_light_station_elec_day_report_new | database=ads, source=TAEI-3146 |

## 新发现

### Git 行为模式
1. **代继宁零提交 ≠ 零开发**: 代继宁在 TAEI-3168 中零提交，但在 TAEI-3092 中有 21 条提交（租金个税）。PM/需求管理角色与开发者角色的差异需要按需求区分。
2. **TAEI-3101 招银组件**: 李龙的近期 18 条提交全是"AI智能对账"映射模板开发（branch: origin/20260519-alone-electricAI），**非招银组件功率匹配**。招银组件的变更可能已完成或尚未进入当前扫描窗口。
3. **王斌(tn_wangb) 多线程开发**: 同一时期在 4 个分支并行开发:
   - `origin/feature-cm-wind-electric` → TAEI-3107 风电
   - `origin/20260601-zeroCarbonMerchantQuit/TAEI-3168` → TAEI-3168 零碳退商
   - `origin/20260527-wb` → 退质保金
   - `origin/20260601-wb-lightSpOrder` → SAP取数逻辑优化
4. **yumiao BFF 层 423+ 提交**: 主要是 TAEI-3150 大商政策监控报表 1.5期，涉及 30+ 新模块。真正业务逻辑需追踪到 Dubbo 层。

### 业务风险预警
1. **TAEI-3146 ADS 迁移**: 新旧两套数据源并行运行，需关注切换策略和回滚方案。当前 ADS 表无 `id` 字段，所有依赖 id 的逻辑需要确认已适配。
2. **TAEI-3159 收入闸口放开**: 注释掉 3 项收入超限校验但保留成本校验，这是业务规则的重大变更，需确认是否符合财务合规要求。
3. **TAEI-3125/3126 商户通**: 需求状态已为"待测试"，但近 7 天零 Git 提交（袁睿林零提交），需确认代码是否已合入或延期。
