# 云效驱动代码学习报告 — 第2期 (2025-12-08 ~ 2025-12-28)

## 扫描范围
- **时间窗口**: 2025-12-08 ~ 2025-12-28 (21天)
- **云效需求**: 44个 (TAEI-2733 ~ TAEI-2799)
- **涉及人员**: 代继宁、杨辉、商轶龙、马斌、姜传德、魏秋阳、袁睿林、张硕文、姜廷、褚福贺、包鑫、王金浩、马金虎、王希然、付凯善、孙志男、李培龙、解钦、王斌、于淼、徐晓凤、刘飞、董学强、majinhu、yumiao、sunzn、mabin、22081194、龙龙、dengqiu、tn_wangb、laowang、20022445、A2001357、A2001566
- **Git仓库**: 27个有变更的仓库 (964个提交)
- **核心后端仓库**: rrsjk-light-service(379提交), rrsjk-admin-web(194), rrsjk-light-operation-service(53), rrsjk-merchant-web(47), rrsjk-light-data-service(40), rrsjk-finance-service(35), nahui-dashboad-h5(52)

## 需求 → 代码关联

| 需求号 | 标题 | 状态 | 开发参与人 | 核心仓库 | 关键提交 |
|---|---|---|---|---|---|
| TAEI-2733 | 【零碳适家】新建菜单：套餐库存计划 | 已完成 | 代继宁/杨辉 | cbs-web | 菜单/权限配置 |
| TAEI-2734 | 【绿证交易】票税通接口新增合同附件和编码 | 已完成 | 商轶龙/马斌 | vpp-pv-oversea | 合同附件字段 |
| TAEI-2735 | 【零碳适家】订单超时24h自动取消 | 已完成 | 代继宁/包鑫 | rrsjk-trade-service | 定时任务/库存归还 |
| TAEI-2736 | 【零碳适家】商户通套餐管理新增删除 | 已完成 | 代继宁/杨辉 | cbs-web | 套餐CRUD |
| TAEI-2737 | 【绿证交易】审批流调整 | 已完成 | 张硕文/商轶龙 | he-vpp.admin-h5 | 前端审批页面 |
| TAEI-2738 | 【零碳适家】CBS采购单优化 | 已完成 | 姜传德 | rrsjk-trade-service | 采购单逻辑 |
| TAEI-2739 | 【零碳适家】保证金管理、批量确认回款 | 已完成 | 姜传德 | rrsjk-trade-service | 保证金/回款 |
| TAEI-2744 | 【华融大屏】海尔新能源资产管理平台 | 已完成 | 代继宁/张硕文 | nahui-dashboad-h5 | 大屏前端 |
| TAEI-2745 | 【零碳适家】施工环节与energy对接 | 已完成 | 姜传德/魏秋阳 | rrsjk-light-service | 施工对接 |
| TAEI-2747 | 【APP】App二期需求 | 已完成 | 姜廷/褚福贺/杨辉/包鑫 | nahui-pv.merchant-micro.osp | App功能 |
| TAEI-2748 | 【建站】发电户号变更优化和逆变器优化 | 已完成 | 王金浩/马金虎 | rrsjk-light-service, rrsjk-light-data-service | 逆变器替换逻辑重构 |
| TAEI-2749 | 【建站】技术建站需求二期 | 已完成 | 王希然/付凯善/袁睿林 | rrsjk-light-service | 建站流程 |
| TAEI-2751 | 【大屏】界面优化 | 已完成 | 代继宁/姜传德/张硕文 | nahui-dashboad-h5 | 大屏UI |
| TAEI-2752 | 【AI】App&小程序新增水印相机 | 已完成 | 姜廷/于淼/王金浩/付凯善/马斌 | nahui-pv.merchant-micro.osp | 水印相机 |
| TAEI-2753 | 电费管理模块功能迭代 | 已完成 | 孙志男/李培龙 | rrsjk-light-service, rrsjk-finance-service | 中银交易收益结算 |
| TAEI-2756 | 【工商业】竣工图/施工图纸G级大文件上传 | 已完成 | 于淼/袁睿林 | rrsjk-light-service | 大文件上传 |
| TAEI-2757 | 【建站】验收报告印模以2024-11-05分段 | 已完成 | 于淼 | rrsjk-light-service | 验收报告模板 |
| TAEI-2758 | 【政策】新商政策优化 | 已完成 | 代继宁/商轶龙 | rrsjk-light-service, rrsjk-merchant-web | 超期考核区域过滤 |
| TAEI-2760 | 【合同】撤销和恢复合同，记录原因和日志 | 已完成 | 包鑫 | rrsjk-light-service | 合同撤销恢复日志 |
| TAEI-2761 | 电费报表（资方）取数逻辑优化 | 已完成 | 孙志男 | rrsjk-light-service | 报表取数 |
| TAEI-2763 | 【建站】验收页面整改 | 已完成 | 于淼/付凯善/马金虎 | rrsjk-light-service | 验收页面 |
| TAEI-2764 | 【大屏】四合一大屏 | 已完成 | 张硕文 | nahui-dashboad-h5 | 四合一大屏前端 |
| TAEI-2772 | 【报表】电站成本核算报表增加新商政策兑现金额 | 已完成 | 解钦 | rrsjk-light-service | 报表扩展 |
| TAEI-2773 | HDS-工单大厅：新增资方运维工单(越秀) | 已完成 | 孙志男/李培龙 | rrsjk-light-operation-service, nahui-pv.hds-h5 | 越秀工单模块 |
| TAEI-2774 | 【支付】银联支付合计修改生成采购单金额 | 已完成 | 商轶龙 | rrsjk-light-service | 银联支付 |
| TAEI-2777 | 【工商业】开票支持小EPC | 已完成 | — | rrsjk-light-service | 小EPC开票 |
| TAEI-2778 | 运维商商户通：电站列表加更新时间 | 已完成 | 孙志男/李培龙 | nahui-pv.merchant-micro.osp | 更新时间字段 |
| TAEI-2779 | 【建站】激励管理/项目公司政策/电站详情优化 | 已完成 | 王希然/付凯善/李培龙 | rrsjk-light-service | 激励管理 |
| TAEI-2780 | 【仓库】CBS组件库SN码仅与配货服务商一级仓绑定 | 已完成 | 姜传德 | rrsjk-trade-service | SN码绑定 |
| TAEI-2781 | hds运维管理-变更管理模块优化 | 已完成 | 孙志男 | rrsjk-light-operation-service | 变更管理 |
| TAEI-2782 | 商户通-运维服务-电站列表增加"承接运维时间" | 已完成 | 孙志男/李培龙 | rrsjk-light-operation-service | 承接时间字段 |
| TAEI-2783 | 【支付】扣应付请款单增加PDF和律师函 | 已完成 | 王斌 | rrsjk-light-service | 请款单附件 |
| TAEI-2784 | 商户通/HDS/APP-电站数据变更流程升级 | 已完成 | 孙志男/李培龙 | rrsjk-light-operation-service, nahui-pv.merchant-micro.osp | 数据变更流程 |
| TAEI-2788 | 【政策】发布年度规模政策 | 已完成 | 解钦 | rrsjk-light-service, rrsjk-merchant-web | 年度规模政策实体+API |
| TAEI-2789 | 【合同】合同归档接口替换 | 已完成 | 包鑫/于淼 | rrsjk-light-service | 合同归档接口 |
| TAEI-2790 | 【报表】2026年报表目标更换 | 已完成 | 王斌/包鑫 | rrsjk-light-service | 报表目标 |
| TAEI-2792 | 运维收入成本管理记账逻辑迭代 | 已完成 | 孙志男/李培龙 | rrsjk-light-service, rrsjk-finance-service | 记账逻辑 |
| TAEI-2794 | 【零碳适家】CBS详情页返回列表保留搜索条件 | 已完成 | 包鑫 | cbs-web | 搜索状态保持 |
| TAEI-2795 | 【零碳商城】增票资质审核列表图片放大 | 已完成 | 包鑫 | cbs-web | 图片预览 |
| TAEI-2796 | 【零碳适家】名称类筛选添加模糊搜索 | 已完成 | 包鑫 | cbs-web | 模糊搜索 |
| TAEI-2797 | 【电力交易】山东报表管理 | 已完成 | 张硕文/包鑫 | nahui-dashboad-h5 | 山东报表前端 |
| TAEI-2799 | 【零碳适家】26年E站政策 | 已完成 | 王希然 | rrsjk-light-service | E站政策 |

## 业务链分析

### 业务链1: 运维电站承接时间体系 (TAEI-2782, TAEI-2784)
**完整链路**: 运维商签署主合同 → `DccSignedCallbackService` 回调 → `updateStationOpTime(memberId)` 批量更新自有电站承接时间 → 商户通/HDS电站列表展示 `specialTime` 字段

**核心变更**:
- `LightOperationStation` 新增 `spMemberId`(建站商会员ID) + `specialTime`(承接运维时间)
- 新增 `updateStationOpTimeAndMemberId` 方法: 运维招商场景下单电站更新承接时间
- 新增 `refreshHistoryOpSpecialTime` 定时Job: 刷历史电站承接时间
- 服务商身份类型逻辑优化: 区分建站商/运维商, 避免公司名重复同步

**涉及文件**:
- `rrsjk-light-operation-api/.../entity/v2/LightOperationStation.java` (spMemberId, specialTime)
- `rrsjk-light-operation-api/.../service/v2/LightOperationStationService.java` (2个新方法)
- `rrsjk-light-operation-impl/.../impl/LightOperationStationServiceImpl.java` (56行新增)
- `rrsjk-light-operation-impl/.../job/LightOperationScheduledJobServiceImpl.java` (刷新Job)
- `rrsjk-light-operation-impl/.../impl/LightOperationProviderServiceImpl.java` (身份类型)

### 业务链2: 逆变器替换优化 (TAEI-2748)
**完整链路**: 发电户号变更 → 逆变器解绑 → 新逆变器绑定 → 发电数据迁移

**核心变更**:
- `LightInveterDataServiceImpl.unbindAndReBindInverter` 逻辑大幅简化(80行→35行)
- 移除"零碳适家电站暂不支持解绑"的硬编码限制
- 新增逆变器替换校验 `validateInverterReplace` + 占用校验
- CompleteConfirmService事务优化, 移除OCR验证代码

### 业务链3: 年度规模阶梯政策 (TAEI-2788)
**完整链路**: 管理员创建政策(年度+阶梯规则) → 服务商签署后生效 → 月度暂估(按并网容量) → SAP生成凭证 → 年度兑现(多退少补)

**核心变更**:
- 6个新实体: Policy主表 + Detail规则 + Staging暂存总表 + StagingDetail暂存明细 + Monthly月度暂估 + MonthlyDetail月度详情
- 商户端API: getCurrentPolicy.do / getMySettleInfo.do / findByExecuteYear.do
- 阶梯计算: minScale→maxScale 区间, stepScale步长, monthPolicyAmount月度暂估单价
- SAP集成: voucher(领用凭证), reserveVoucher(冲销凭证), costVoucher(成本凭证)
- 中银交易收益结算: `ZhongYinTradeIncomeSettleService` (导入/确认/删除/冲销/SAP定时任务)

### 业务链4: 合同撤销恢复 (TAEI-2760)
**核心变更**: 新增 `LightContractRevocateAndRestoreLog` 实体, 记录 REVOCATE/RESTORE 操作日志, 包含原因和操作人

### 业务链5: 越秀收入账单扩展 (TAEI-2753, TAEI-2761)
**核心变更**: 
- 新增越秀农户收益异常支付查询(138行Mapper SQL)
- 新增收入账单扩展查询(246行Mapper SQL)
- 异常数据统计/排序/支付进度查询条件完善

## 知识库更新

| 操作 | 文件 | 内容摘要 |
|---|---|---|
| 追加 | `domains/policy.md` | 年度规模阶梯政策完整实体体系(6个实体)、商户端API(3个接口)、月度暂估→兑现→SAP流程、中银交易收益结算服务 |
| 追加 | `domains/settlement.md` | 中银交易收益结算(ZhongYinTradeIncomeSettleService 7个方法)、合同撤销恢复(LightContractRevocateAndRestoreLog)、运维收入成本记账 |
| 追加 | `domains/station-lifecycle.md` | 运维电站承接时间体系(spMemberId/specialTime/5个实体字段/2个Service方法/1个Job)、逆变器替换优化(解绑逻辑简化/OCR移除) |

## 扫描统计
- **总提交数**: 964
- **有业务价值的核心提交**: ~200 (其余为依赖更新、配置调整、JVM优化等)
- **新发现业务概念**: 承接运维时间(specialTime)、建站商/运维商身份区分、中银交易收益结算、合同撤销恢复日志、年度规模阶梯政策完整体系
- **新发现Dubbo服务**: ZhongYinTradeIncomeSettleService, LightOverduePolicyAreaService, LightAnnualScalePolicyService, LightAnnualScalePolicyStagingService
