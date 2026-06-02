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

### TAEI-3168 零碳适家退商材料申请流程（开发中, 2026-06-01 追加）
**来源**: `rrsjk-light-service` (tn_wangb/王斌, branch: origin/20260601-zeroCarbonMerchantQuit/TAEI-3168)
- **负责人**: 刘艺(PM) | **实际开发**: 王斌(tn_wangb) | **参与人**: 代继宁、薛荣基
- **早期变更**: `CmLightProject.P6` 枚举修复空格 + `LightEpcStationModel.createOrUpdateStation()` 新增写入 `projectCode`/`projectName`
- **业务语义**: 工商业电站创建/更新时同步写入项目编码和名称，为后续退商材料申请流程做数据准备
- **状态**: 仅 2 条提交，核心退商材料逻辑尚未开始开发
- **证据等级**: 代码明确证明
