# 云效驱动代码学习报告 — 2026-05-18 至 2026-05-24 (历史补漏重跑)

## 扫描范围
- **时间窗口**: updateStatusAtAfter=2026-05-18T00:00:00 ~ updateStatusAtBefore=2026-05-24T23:59:59
- **云效需求**: 19 个
- **涉及人员**: 于淼、包鑫、解钦、姜传德(德)、代继宁、马金虎、王斌、孙志男、李培龙、马斌、laowang(王金浩)、王希然、张硕文、龙龙(王斌)、付凯善、majinhu
- **Git 提交**: 337 个 (排除 BFF 层后约 310 个)

## 知识覆盖分析

| 需求号 | 标题 | 状态 | 图谱覆盖 | 学习深度 |
|---|---|---|---|---|
| TAEI-3021 | 零碳适家 保证金/订单收款接FAP | 测试中 | ❌ 新知识 | 完整分析 |
| TAEI-3022 | 绿证交易 订单收款接FAP | 测试中 | ❌ 新知识 | 完整分析 |
| TAEI-3025 | BT报表项目 | 测试中 | ✅ 部分覆盖(BT报表域) | 增量更新 |
| TAEI-3031 | 绿电开票要求优化 | 已完成 | ✅ 已覆盖(绿电/开票) | 增量更新 |
| TAEI-3042 | 大商政策暂估及兑现监控报表 | 已完成 | ✅ 已覆盖(政策域) | 增量更新 |
| TAEI-3060 | 大屏新增告警 | 开发中 | ✅ 已覆盖(HDS域) | 增量更新 |
| TAEI-3068 | 广发业主信息更正接口 | 开发中 | ❌ 新知识(广发) | 完整分析 |
| TAEI-3073 | 广发并网进件-附件改造 | 测试中 | ❌ 新知识(广发) | 完整分析 |
| TAEI-3083 | 完工前变更方案审批流变更 | 已完成 | ✅ 已覆盖(审批流) | 增量更新 |
| TAEI-3085 | 增加上收限制 | 已完成 | ✅ 已覆盖(收入/结算) | 增量更新 |
| TAEI-3087 | 国电投账号 | 已完成 | ❌ 新知识(国电投) | 完整分析 |
| TAEI-3090 | 公共建筑立项兼容 | 已取消 | - | 跳过 |
| TAEI-3093 | 电站图片模板组数据库存储 | 待处理 | ❌ 新知识(图片模板) | 完整分析 |
| TAEI-3096 | 零碳适家 energy系统建站接口 | 测试中 | ✅ 已覆盖(零碳) | 增量更新 |
| TAEI-3100 | 自持电站报表优化 | 已完成 | ✅ 已覆盖(报表) | 增量更新 |
| TAEI-3103 | 电站业主租金停付管理 | 开发中 | ❌ 新知识(租金停付) | 完整分析 |
| TAEI-3104 | light_unionpay_rent唯一键冲突 | 已完成 | ❌ 新知识(银联租金) | 完整分析 |
| TAEI-3109 | 光伏对账单性能优化 | 已完成 | ❌ 未找到对应提交 | 需后续排查 |
| TAEI-3008 | 华融EPC流程搭建 | 已完成 | ✅ 已覆盖(华融) | 增量更新 |

---

## 需求 → 代码关联详情

### 1. TAEI-3021/TAEI-3022 — FAP收款集成 (零碳适家 + 绿证交易)

**状态**: 测试中 | **负责人**: 刘艺 | **参与人**: 代继宁、魏秋阳、王斌、薛荣基

**关键提交** (代继宁, 7个核心提交):
- `rrsjk-light-service`:
  - `34fc750e` feat(fap): 添加FAP凭证补偿机制并优化客户信息更新逻辑 (+137行, LightFapRecordServiceImpl)
  - `0e7e2f5e` refactor(fap): 优化FAP记录处理逻辑并移除补偿状态相关代码 (-239行/+192行)
  - `dd2ef5c8` fix(fap): 修复取消FAP记录时状态丢失问题
  - `928cde94` fix(fap): 优化FAP接口响应处理和记录逻辑
  - `69bc8d8e` fix(light): 优化订单推送结果消息处理
  - `e1c7b3c9` refactor(light): 优化分页查询逻辑
  - `597db042` feat(fap): 添加凭证更新补偿功能支持
- `rrsjk-admin-web`: 3个提交 (FAP状态显示、推送逻辑、收款记录导出)
- `rrsjk-merchant-web`: 1个提交 (修复FAP订单取消逻辑)
- `rrsjk-trade-service`: 3个提交 (FAP凭证更新日志、同步方法清理)

**业务链分析**:
- **核心实体**: `LightFapRecord` (FAP凭证记录表，rrsjk_light库)
- **变更内容**:
  1. **新增凭证补偿机制**: 支持物料回购、站点回购、服务押金等多种业务类型的补偿处理
  2. **移除补偿状态字段**: 从 `LightFapRecord` 实体删除补偿状态枚举及相关字段 (-54行)
  3. **优化取消逻辑**: 增加状态检查和本地标记机制，防止重复取消
  4. **新增实时查询**: `queryFapInfoFromFapSys` 方法从FAP系统实时查询制证状态
  5. **批量处理**: FAP推送和查询定时任务增加批量处理和异常处理
  6. **易取消业务类型识别**: `isCancelProneBizType` 方法识别高风险业务类型

**⚠️ FAP同步解耦反模式风险预警**:
- 代继宁移除了 `LightFapRecord` 中的补偿状态字段和补偿凭证任务相关代码
- **需确认**: 旧补偿逻辑已停，新实时查询(`queryFapInfoFromFapSys`)是否已完全替代旧补偿机制？
- 当前代码中未见 `operationalAssetManagementService` 相关调用声明

**Neo4j更新**: ✅ 新增 `light_fap_record` 表 + `dws` 数据库 + Service关系

---

### 2. TAEI-3025 — BT报表项目

**状态**: 测试中 | **负责人**: 刘艺 | **参与人**: 于淼、魏秋阳、薛荣基、包鑫、李龙

**关键提交**:
- **yumiao** (rrsjk-admin-web):
  - `c9d923c3` feat(Epic2): 新增逆变器列表(DWS)页面 (+994行 lightInveterListDws.ftl)
  - `3310ac11` feat(Epic2): 新增逆变器列表(DWS)查询接口 (LightInveterController +179行)
  - `fbb0720a` feat: 发电数据dws切换
  - `e5b9b7e5` feat: 电站分中心初审替换新版分中心
  - `dd6b0726` fix: 华融质保金页面权限点复用华融交易收入
- **majinhu** (rrsjk-light-data-service):
  - `030fa75d` feat: 优化三天发电定时任务 (LightInveterDataServiceImpl +69/-44行)
  - `7db3df5e` feat: 增加状态日志
  - `8736e2c5` feat: 增加连续3天有发电数据日志排查

**业务链分析**:
- **DWS数据源接入**: 新增 DwsInveterData 实体、DAO/Service层及字段映射转换器
- **新增查询接口**: `doListDws.do` → `findByPageDws` (参数与旧版一致)
- **前端页面**: `lightInveterListDws.ftl` (994行，复制自旧版)
- **多数据源配置**: DWS多数据源接入，通过 `DwsInveterDataService` 代理调用

**Neo4j更新**: ✅ 新增 `Database:dws` + `Table:DwsInveterData`

---

### 3. TAEI-3085 — 增加上收限制

**状态**: 已完成 | **负责人**: 杨越越 | **参与人**: 解钦、薛荣基

**关键提交** (解钦, rrsjk-light-service):
- `880f3d11` feat(income-constrain): 收入限制修复 (8个资方结算ServiceImpl, 各+1/-1行)
- `2c238863` feat(income-constrain): 中核收入增加限制问题修复
- `eb6bb79b` feat(cm-wind-electric): 收入政策并行审核方案实现

**业务链分析**:
- **性能优化**: 将 `Assert.isTrue` 的 eager 字符串拼接改为 lazy Supplier (`() -> "..."`)
- **涉及Service** (8个): HuaRongTradeIncomeSettleServiceImpl, LightFundSettleServiceImpl, LightHdIncomeServiceImpl, LightStationYuexiuSettleServiceImpl, LightZhSettleServiceImpl, PuYinTradeIncomeSettleServiceImpl, ZhaoYinTradeIncomeSettleServiceImpl, ZhongYinTradeIncomeSettleServiceImpl
- **影响**: 避免断言通过时的无谓字符串拼接，提升批量导入性能

---

### 4. TAEI-3093 — 电站图片模板组数据库存储

**状态**: 待处理 | **负责人**: haier47@aliyun.com | **参与人**: 于淼、王希然

**关键提交** (wangxiran, rrsjk-light-service):
- `4218656a` feat(light-station): 添加电站图片变更检查功能 (+63行, LightStationPlanChangeServiceImpl)
- `029cb4cf` / `74c1b3b9` (同功能重复提交)

**业务链分析**:
- **新增方法**: `checkStationImagesNoChange()` — 比较电站图片是否发生变化
- **图片类型**: 屋顶尺寸图片、模块结构图片、产权证书、载荷报告图片
- **URL标准化**: `normalizeImageUrl()` 方法处理图片URL标准化
- **业务语义**: 图片无变化时可跳过审核流程，减少不必要的审批

---

### 5. TAEI-3100 — 自持电站报表优化

**状态**: 已完成 | **负责人**: 徐晓凤 | **参与人**: 王斌、薛荣基

**关键提交** (tn_wangb, rrsjk-admin-web):
- `eac6ccd4` 工商业自持电站损益报表优化 (10个FTL模板, +117/-101行)
- `a9393c17` 工商业自持电站损益报表优化 (CmOwnerStationWhiteListImportExcel)
- `51731715` 工商业收款切换fap
- `a230dde6` 工商业风电项目终验法

**业务链分析**:
- 前端模板批量更新: cmChangeAudit.ftl, cmChangeDetail.ftl, cmConstructionPlanAudit.ftl 等10个工商业模板
- 白名单导入Excel字段修正
- 工商业收款从旧逻辑切换到FAP

---

### 6. TAEI-3083 — 完工前变更方案审批流变更

**状态**: 已完成 | **负责人**: 徐晓凤 | **参与人**: 王斌、付凯善

**关键提交** (解钦, rrsjk-light-service):
- `eb8bd383` feat(电站回退): 处理冲销领用时兼容完工前领用不创建SO出库队列
- `789fff6c` feat(电站回退): 处理冲销领用时兼容完工前领用不创建SO出库队列
- `2fbdd007` fix: 修复电站回退领用未考虑完工前领用的问题
- `e5c03619` fix: 电站回退重新领用兼容完工前领用的情况
- `eb6bb79b` feat(cm-wind-electric): 收入政策并行审核方案实现

**业务链分析**:
- **核心场景**: 电站回退重新领用时，需要区分"完工前领用"和"完工后领用"
- **旧逻辑缺陷**: 完工前领用不创建SO出库队列，回退冲销时未处理导致异常
- **新增**: 并行审核方案支持 (CmLightProjectIncomePolicy 实体修改)

---

### 7. TAEI-3068/TAEI-3073 — 广发业主信息更正 + 广发并网进件

**状态**: 开发中/测试中 | **负责人**: 刘艺 | **参与人**: 薛荣基、袁睿林、马金虎

**关键提交** (majinhu, rrsjk-light-data-service):
- DWS数据源接入: 新增 dws 多数据源配置、DwsInveterData 实体
- 三天发电定时任务优化: 连续三天有发电数据日志排查

**关联**: 与 TAEI-3025 BT报表共用 DWS 数据源切换逻辑

---

### 8. TAEI-3060 — 大屏新增告警

**状态**: 开发中 | **负责人**: 徐晓凤 | **参与人**: 于淼

**关键提交** (李培龙, nahui-pv.hds-h5):
- 15+ 前端优化提交: 资方地图更新、电站健康状态分布图表变更、依赖版本更新
- `baed073c` feat: 变更电站健康状态分布图表
- `52604235` feat: 更新资方下拉，优化依赖版本

---

### 9. TAEI-3008 — 华融EPC流程搭建

**状态**: 已完成 | **负责人**: 杨越越 | **参与人**: 姜传德、杨辉、薛荣基、李培龙、马斌、董学强

**关键提交**:
- `majinhu` (rrsjk-light-service): fix: 华融上收入记质保金增加防御性校验 (2026-05-18)
- `tn_wangb` (rrsjk-admin-web): 工商业收款切换fap (2026-05-22)

---

### 10. TAEI-3090 — 分中心用户管理 (已取消)

**状态**: 已取消 | **代码提交**: 德(姜传德), cbs-web, 10个提交
- 分中心管理功能: 用户添加、搜索、编辑、移除
- 分支: `origin/feature/202605/regionUnlimit`
- **注意**: 需求已取消，但代码已提交，需确认是否回滚

---

## 图谱更新记录

| 操作 | 实体类型 | 实体名称 | 属性 | 关联关系 |
|---|---|---|---|---|
| 新增 | Database | dws | description='阿里云大数据平台DWS层', source='TAEI-3025/3068/3073' | - |
| 新增 | Table | light_fap_record | database='rrsjk_light', description='FAP凭证记录表' | rrsjk-light-service USES_TABLE, rrsjk-trade-service USES_TABLE |
| 新增 | Table | cm_light_project_income_policy | database='rrsjk_light', description='工商业电站项目收入政策表' | - |
| 新增 | Table | DwsInveterData | database='dws', type='external_source' | - |
| 更新 | Table | cm_light_project | description='工商业电站项目表', source='TAEI-3085' | - |
| 更新 | Service | rrsjk-light-data-service | domain='inverter-data' | - |
| 更新 | Service | rrsjk-trade-service | domain='trade' | USES_TABLE light_fap_record |
| 更新 | Service | rrsjk-merchant-web | domain='merchant' | - |
| 更新 | Service | rrsjk-admin-web | domain='admin' | - |

## 知识缺口（待后续学习）

| 类型 | 名称 | 原因 |
|---|---|---|
| 新表 | light_unionpay_rent | TAEI-3104提及的唯一键冲突表，图谱中无记录 |
| 新接口 | 广发业主信息更正接口 | TAEI-3068的接口定义未在代码中找到 |
| 需求关联 | TAEI-3109 对账单性能优化 | 窗口内未找到对应Git提交，可能在此之前已完成 |
| 业务域 | 国电投账号管理 | TAEI-3087相关业务逻辑未深入分析 |
| 风险确认 | FAP补偿机制替代 | 旧补偿逻辑已移除，需确认新实时查询是否完全替代 |

## 代码质量风险预警

| 风险类型 | 位置 | 描述 | 需求关联 |
|---|---|---|---|
| FAP补偿逻辑缺失 | LightFapRecordServiceImpl | 补偿状态字段已删除，补偿任务代码已移除，新实时查询机制需验证覆盖所有场景 | TAEI-3021/3022 |
| 已取消需求代码残留 | cbs-web/subCenter | TAEI-3090已取消但分中心用户管理代码已提交(10 commits) | TAEI-3090 |
| DWS数据源双路径 | rrsjk-light-data-service | 旧MySQL数据源和新DWS数据源并存，需确认切换策略 | TAEI-3025/3068 |
| 图片模板配置硬编码 | LightStationPlanChangeServiceImpl | 图片验真接口URL在配置中，模板配置可能硬编码 | TAEI-3093 |
