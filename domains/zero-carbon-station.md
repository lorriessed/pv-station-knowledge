# 零碳电站（Zero Carbon Station）

更新时间: 2026-05-13

## 已确认知识

### 零碳电站服务架构
**来源**: `rrsjk-hds-web` → `LightOperationZeroCarbonStationController.java` (commits 9ca7b10/63a7bf7, dengqiu, 2026-05-12)
- 零碳电站接口位于 `rrsjk-hds-web` 服务
- Controller: `LightOperationZeroCarbonStationController` (v2 版本)
- 持续完善接口字段和设备相关接口

### 零碳电站设备与逆变器
**来源**: `rrsjk-light-operation-service` → `HaierEnergyInverterRealtimeService.java`, `LightZeroCarbonOdsStationServiceImpl.java`, 各 `HaierDeviceType*RealtimeAdapter.java`, `MpptRealtimeDto.java` (commit 8818b2b, dengqiu, 2026-05-12)
- 零碳电站设备相关接口完善
- 海尔能源逆变器实时数据服务：`HaierEnergyInverterRealtimeService`
- 设备类型适配器：`HaierDeviceType50100RealtimeAdapter`, `HaierDeviceType50300RealtimeAdapter`, `HaierDeviceType60419RealtimeAdapter`, `HaierDeviceType65323RealtimeAdapter`
- 新增 `MpptRealtimeDto`（MPPT实时数据）
- ODS 站数据查询：`LightZeroCarbonOdsStationQuery`, `LightZeroCarbonOdsStationCardDto`, `LightZeroCarbonOdsStationSkuDetailDto`
- Mapper: `LightZeroCarbonOdsStation.xml`, `LightZeroCarbonOdsStationSku.xml`, `LightZeroCarbonOdsEStation.xml`

### 业务合作意向与逆变器查询
**来源**: `rrsjk-hds-web` → `BusinessCooperationIntentionController.java` (commit f7d0d55, sunzn, 2026-05-12)
- 业务合作意向控制器支持逆变器数据查询

## 待确认
- 零碳电站的完整业务流程（录单→审核→并网→运营）
- 零碳电站与普通电站的数据模型差异
- ODS 数据源的接入方式和同步频率
- 零碳适家结算与安装费结算的关系

### 零碳适家请款申请数据字典过滤 (代码明确证明, 2026-05-20)
**来源**: `nahui-pv.merchant-micro.zch` → `src/views/zeroCarbon/settlement/addPaymentRequest.vue`
**Commit**: c3c420d1, 开发者: yuanruilin, 2026-05-20

- 请款申请页(purchaseTypeList)的数据字典过滤从 **按label过滤** (`e.label === '工程安装'`) 改为 **按value过滤** (`e.value === '13'`)
- 数据字典查询: `getDicts("zch/finance", "purchaseTypeList")`
- **影响**: `value='13'` 对应工程安装类型，改用value过滤更稳定(label可能被修改)

### 零碳结算管理页面角色扩展 (代码明确证明, 2026-05-25)
**来源**: `nahui-pv.merchant-micro.zch` → `src/router/zeroCarbon.js`, `src/store/modules/index/_type_zeroCarbon.js`
**Commit**: ba04ae91/df23481f, 开发者: yuanruilin, 2026-05-25, branch `dev-yrl-sapPurchase`

- 零碳结算管理相关页面路由角色新增 **"ZERO_CARBON_E_STATION"**
- 涉及路由文件: `src/router/zeroCarbon.js` (12行变更)
- 涉及 store 类型文件: `src/store/modules/index/_type_zeroCarbon.js` (8行变更)
- **影响**: ZERO_CARBON_E_STATION 角色可访问零碳结算管理页面，可能是零碳适家电站的独立角色

### 零碳结算管理角色扩展确认 (代码明确证明, 2026-05-26)
**来源**: `nahui-pv.merchant-micro.zch` → `src/router/zeroCarbon.js`, `src/store/modules/index/_type_zeroCarbon.js` (扫描确认, 2026-05-26)
- 该变更已通过 master 合入 (李宁 merge #72 into master from dev-yrl-sapPurchase)
- 同时包含 node16 版本兼容修复 (`package.json` 变更)

## 来源
- 每日代码扫描 2026-05-13，rrsjk-hds-web, rrsjk-light-operation-service

---

## 招投标管理审核模块 (代码明确证明, 2026-05-20)
**来源**: `rrsjk-light-service` → `TenderManagmentAudit.java` (commits: laowang f2eabc2, cb11fc9, 2c2caf7, 4d9ec27, 2026-05-14~19)
**需求**: TAEI-3102 【户用光伏】CBS招投标流程

- **TenderManagmentAudit 实体**: 招投标管理审核，位于 `rrsjk.light.entity.tenderManagement` 包
- **项目分类** (`projectCategory`): FD(风电) / GSY(工商业) / HYEPC(户用EPC) / YW(运维) / LTSJ(零碳适家) ~~零碳世家~~ (2026-06-02 重命名)
- **审核流程**:
  1. 首次附件审核: `auditStatus` — AGREE(通过) / DISAGREE(驳回) / REJECT(拒绝)
  2. 招标文件审核: `tenderFileAuditStatus` — AGREE / DISAGREE
  3. 价值链及投标材料审核: `valueChainAndTenderMaterialAuditStatus` — AGREE / DISAGREE
  4. 初审版标书: `firstDraftTenderFileUrl`
  5. 终审版标书: `finalDraftTenderFileUrl`
- **地理信息拆分** (2.0版本): 零碳能源代理商请求的地区字段从单一套拆分为两套：
  - 代理商地区: `agentCountryId`, `agentProvinceId`, `agentCityId`, `agentDistrictId`
  - 电站地区: `plantCountryId`, `plantProvinceId`, `plantCityId`, `plantDistrictId`
- **原因**: 代理商所在地与电站所在地可能不同，需要分别记录

---

## 零碳能源代理商地区字段拆分 (代码明确证明, 2026-05-20)
**来源**: `rrsjk-light-service` → `ZeroCarbonEnergyAgentRequest.java`, `ZeroCarbonEnergyApi.java` (commit: laowang 4d9ec27, 2026-05-19)
**需求**: TAEI-3102 【户用光伏】CBS招投标流程

- **字段拆分**: `countryId/provinceId/cityId/districtId` → `agentCountryId/agentProvinceId/agentCityId/agentDistrictId` + `plantCountryId/plantProvinceId/plantCityId/plantDistrictId`
- **API变更**: `ZeroCarbonEnergyApi` 中上传电站和安装商信息时，地区字段从 provider 信息映射到 agent 地区字段
- **国家ID硬编码**: `agentCountryId = 129065`（中国）

### 零碳适家FAP收款接入 (代码明确证明, 2026-05-19~20)
**来源**: `rrsjk-light-service` → 代继宁 commits, `rrsjk-admin-web` → 代继宁 commits
**关联需求**: TAEI-3021 【零碳适家】保证金收款接FAP、订单收款接FAP
- 零碳适家业务的保证金收款和订单收款接入FAP财务系统
- 与TAEI-3022绿证交易订单收款接FAP共享相同的技术实现
- 代继宁负责后端开发，前端在rrsjk-admin-web中实现
- 涉及FAP凭证补偿机制、状态常量修复、客户信息更新优化
- **证据等级**: 代码明确证明

### 零碳适家业务模式 (前端配置证明, 2026-05-22 扫描)
**来源**: `nahui-dicts-serve` → `src/data/zch/base/` (袁睿林, 2026-04-17)
- `businessModelTypeList.js`: `LIGHT_STORAGE`=零碳适家-光储, `E_STATION`=零碳E站, `ALL`=所有模式
- `businessModelStatus.js`: `WAIT_AUDIT`待审核 → `AUDIT_REJECT`审批不通过 → `WAIT_SIGN`待签署 → `ENABLE`已授权

### 零碳能源电站容量计算修正 (代码明确证明, 2026-04-28)
**来源**: `rrsjk-light-service` → `ZeroCarbonEnergyApi.java` (commit 37dc5f00c9, 德/姜传德, 2026-04-28)
**关联需求**: TAEI-3056 【零碳适家】建站方案登记支持不同品牌不同规格组件混用
- **Bug修复**: 电站容量计算从 `planQuantity * planPower` 改为仅使用 `planPower`
- 原逻辑: `.plantCapacity(BigDecimal.valueOf(station.getPlanQuantity()).multiply(BigDecimal.valueOf(station.getPlanPower())).toString())`
- 修复后: `.plantCapacity(station.getPlanPower().toString())`
- **业务含义**: `planPower` 已是总装机容量(kW)，不应再乘以组件数量
- **证据等级**: 代码明确证明

### TAEI-3168 零碳适家退商材料申请流程（开发中, 2026-06-04 阻塞状态）
**来源**: `rrsjk-light-service` (代继宁, branch: origin/20260601-zeroCarbonMerchantQuit/TAEI-3168)
- **负责人**: 刘艺(PM) | **实际开发**: 代继宁 | **参与人**: 王斌、薛荣基
- **最新提交**: 81c6958(更新零碳订单/逆变器销售确认收款人), 3f56411(FAP单号查询为空bug修复), e660aef(解决冲突) — 2026-06-03
- **状态**: 阻塞 (2026-06-04 云效状态为"阻塞")
- **新增 DTO**: `ZeroCarbonSpWithdrawalCheckResult` (rrsjk-light-api)
  - `pass`: Boolean — 是否通过退商校验
  - `blockMsg`: String — 阻塞信息（未签收订单或未结算费用）
  - `warnMsg`: String — 警告信息（未消耗库存，提示5秒）
- **新增 Dubbo 接口**: `ZeroCarbonServiceProviderService.withdrawalCheck(spId)` → `ExecuteResult<ZeroCarbonSpWithdrawalCheckResult>`
- **校验规则**:
  1. 检查是否有未签收的采购订单 → `light_zero_carbon_purchase_order` → 阻塞
  2. 检查是否有未结算的安装费 → `light_zero_carbon_installation_fee` → 阻塞
  3. 检查是否有未消耗库存 → `light_zero_material_manage.countOfUnUseStockBySpu(spId)` → 仅警告
- **涉及 DAO 新增方法**:
  - `LightZeroCarbonInstallationFeeDao.findDistinctOrderNos()`
  - `LightZeroMaterialManageMapper.countOfUnUseStockBySpu(spId)`
- **外部服务依赖**: `ZeroCarbonInstallBillService` (finance-service, Dubbo 调用)
- **证据等级**: 代码明确证明
- **关联表**: `light_zero_carbon_purchase_order`, `light_zero_carbon_installation_fee`, `light_zero_material_manage`
- **证据等级**: 代码明确证明
## 零碳完工确认支持多组件多逆变器序列号 (代码明确证明, 2026-06-11)
**来源**: `rrsjk-light-service` (德=姜传德, commit a8e7186, branch: origin/zero_carbon_multi_module_20260421)
- **变更内容**: 零碳完工确认从"单一类型汇总数量校验"改为"按SKU逐个校验序列号"
- **旧逻辑**: `moduleList`/`inverterList` 类型为 `List<LightZeroCarbonSkuRequest>`, 只校验总数量 == 方案配置总量
- **新逻辑**:
  - `moduleList`/`inverterList` 类型改为 `List<LightZeroCarbonCompleteSkuRequest>`（含 `skuCode` + `snList`）
  - 遍历 `LightZeroCarbonStationPlanConfig`，按 SKU 匹配对应的序列号列表
  - 每个 SKU 独立校验：序列号数量 == 该 SKU 方案配置数量
  - 所有 SKU 的 SN 合并到 `moduleSnList`/`inverterSnList` 用于后续入库
- **关键代码**: `ZeroCarbonCompleteConfirmServiceImpl.java` 第 534~635 行
- **业务意义**: 支持零碳电站使用多种型号组件/逆变器混合完工，每种型号独立提交序列号
- **证据等级**: 代码明确证明

### 退商流程事务原子性修复 (代码明确证明, 2026-06-17)

**来源**: `rrsjk-light-service/ZeroCarbonServiceProviderServiceImpl.java` (commit: ccb83b0e0a, 代继宁, 2026-06-17)
**关联需求**: TAEI-3185 (退商流程优化)

**修复内容**:
- 修复前: 退商申请创建(`zeroCarbonSpWithdrawalDao.create`) 和 服务商状态更新(`setStatus(QUITING)`) 在不同事务中
- 修复后: 使用编程式事务 (`TransactionManager.getTransaction/commit/rollback`) 保证原子性
- 附件保存也纳入同一事务
- 同时修复了审核拒绝时的状态恢复逻辑

### 零碳智能投站服务接口 (代码明确证明, 2026-06-17)

**来源**: `rrsjk-light-service` (commit: 363306511d, mabin/马斌, 2026-06-17)
**分支**: origin/20260615-zeroSmart

**新增**: 零碳智能投站服务接口（具体接口定义需进一步确认）。马斌参与零碳模块开发。

### 零碳套餐库存管理 (代码明确证明, 2026-06-17/25)

**来源**: `rrsjk-merchant-web` → `ZeroCarbonItemSetMealStockController.java` (commit: 1815c2503, 代继宁, 2026-06-17; d616bd29e, 2026-06-18)

**新增接口** (2026-06-17):
- `GET /zerocarbon/itemSetMealStock/getSetMealInfoByKeyword?keyword=` — 关键字查询套餐库存（按名称模糊搜索）
- `POST /zerocarbon/itemSetMealStock/reduceStock` — 手动下调套餐库存（ body: `SetMealStockParamDto`，含 setMealCode）
  - 关联需求: TAEI-3144 (套餐计划库存下调)
  - 订单号生成规则: 手动下调时使用特定规则生成订单号

**业务说明**: 零碳适家服务商可通过商户通后台手动下调套餐库存（如库存损坏/报损场景），并通过关键字快速检索套餐信息。

### 零碳套餐库存扣减类型扩展 (代码明确证明, 2026-06-17~25, TAEI-3144)
**来源**: `rrsjk-item-service` → `ZeroCarbonItemSetMealStockServiceImpl.java`, `ZeroCarbonItemSetMealStockService.java`, `ZeroCarbonItemSetMealStockDao.java`, `ZeroCarbonItemSetMealStockMapper.xml` (代继宁, commits 37d98614/1f1d160b/f4e601d8, 2026-06-17~25)
- **changeType 扩展**: `updateStock()` 的 `changeType` 从仅支持 `1`（正常扣减）扩展为支持 `1` 和 `3`（新增扣减类型）
- **新增接口**: `findGroupByKeyword(Map<String, Object> params)` — 按套餐编码分组查询可用库存汇总，支持套餐编码/标题模糊查询
- **新增校验**: 套餐数量不能为负数（`changeStock <= 0` → RS0008）
- **重复操作处理**: 幂等检查命中时返回明确错误信息 RS0009（"已更新过零碳适家套餐库存，请勿再重复执行"）
- **流水记录**: `changeLog.setChangeType()` 从硬编码 `1` 改为使用 `setMealStockParamDto.getChangeType()`，支持记录不同类型的扣减

### 零碳套餐起购字段移除 (代码明确证明, 2026-06-25, TAEI-3144)
**来源**: `rrsjk-item-service` → `ZeroCarbonItemSetMealRequest.java` (代继宁, commit `f4e601d8`, 2026-06-25)
- **移除字段**: `minimumPurchaseType`（起购类型）和 `minimumPurchaseQuantity`（起购量）从 `ZeroCarbonItemSetMealRequest` DTO 中删除
- **业务含义**: 零碳套餐不再需要起购类型和起购量配置，简化了套餐创建/编辑的请求参数
- **配套变更**: rrs-parent 版本从 8.0.5 降回 7.0.2；移除 `aliyun-encdb-mysql-jdbc` 数据库加密驱动包依赖
