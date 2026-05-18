# 云效历史需求补漏 - 第1期 (2025-11-17 ~ 2025-12-07)

扫描日期: 2026-05-18

## 需求概览

共扫描 31 条需求

- [TAEI-2694] HDS-电费管理新增分中心/项目公司/资方维度的3个报表 (状态: 已完成)
- [TAEI-2695] 【建站】合同 已生成租金账单的电站，CBS 合同管理菜单，点击重新签署合同需要沿用老租金政策 (状态: 已完成)
- [TAEI-2696] 【工商业】服务商申请配货  限制为电站方案审核通过后 (状态: 已完成)
- [TAEI-2697] 【工商业】替换开工资料为最新版本 (状态: 已完成)
- [TAEI-2698] 对已完工电站运维商所属管理逻辑优化 (状态: 已完成)
- [TAEI-2699] 运维商入驻流程优化 (状态: 已完成)
- [TAEI-2700] 第三方社会化电站逆变器数据对接 (状态: 已完成)
- [TAEI-2702] 【银联】银联接口 -接口增加字段 (状态: 已完成)
- [TAEI-2703] 【小程序端 】C端业务可以查询电费支付情况 (状态: 已取消)
- [TAEI-2704] 【建站】方案审核、完工分中心审核、技术审核、商务审核，记录审核人的 IP地址 (状态: 已完成)
- [TAEI-2705] 【AI】电站编码 业主姓名 地址 项目公司    AI业主姓名 AI地址  AI项目公司 (状态: 已完成)
- [TAEI-2706] 【验收考核】白名单 (状态: 已取消)
- [TAEI-2707] 【GDE】泰语翻译 (状态: 已完成)
- [TAEI-2708] 【建站】房屋照片:增加字段“装修承诺函 ” ，非必填，华融通过B2传送 (状态: 已完成)
- [TAEI-2709] 运维商政策兑现-(户用)模块 负向政策兑现功能优化 (状态: 已完成)
- [TAEI-2710] 【共享支付】云报账接口增加字段：支付还是代付 (状态: 已完成)
- [TAEI-2711] 【建站】越秀变更银行卡更换模版 (状态: 已完成)
- [TAEI-2713] 工商业场景-踏勘设计物料选择增加模糊搜索功能 (状态: 已完成)
- [TAEI-2716] 【共享支付】创建支付明细时取电站上的银行卡、联行号、支行名称 (状态: 已完成)
- [TAEI-2717] 【政策】三种考核组件库存、逆变器库存、整改时效机制白名单优化 (状态: 已完成)
- [TAEI-2722] 【政策】合同时效系统修改 (状态: 已完成)
- [TAEI-2723] 【政策】并网时效每日生成 (状态: 已完成)
- [TAEI-2724] 【租金】商户通、小程序、APP端增加显示电站由共享支付的成功明细/ 支付失败记录 (状态: 已完成)
- [TAEI-2725] 【大屏】光伏资产管理大屏、 增加展示运维侧大屏展示、工商业大屏 (状态: 已完成)
- [TAEI-2726] 【AI】房产证AI提取 (状态: 已取消)
- [TAEI-2727] 【共享支付】退汇和退回处理 (状态: 已完成)
- [TAEI-2728] 【AI】AI识别房产证 (状态: 开发中)
- [TAEI-2729] 运维商政策兑现-(户用)模块 负向政策兑现功能优化 (状态: 已完成)
- [TAEI-2730] 商户通及HDS系统 - 运维商特殊费用模块功能优化 (状态: 已完成)
- [TAEI-2731] 【越秀】对接“农户固定收益异常支付信息查询” (状态: 已完成)
- [TAEI-2732] 【新商政策】升级 (状态: 已取消)

## Git 提交与业务分析

识别 71 个业务变更

### he-vpp.admin-h5: opt:增加去除控制指令，优化客户管理等业务输入框

- Hash: `fde2c51a` | 日期: 2025-12-02 | 作者: 张硕文
- 业务域: 调度, 审核, 合同, 订单
- 文件: src/plugins/app.ts, src/utils/trimDirective.ts, .../modules/customer-operate-modal.vue, .../orderManage/modules/contract-form.vue, .../orderManage/modules/customer-info.vue, .../orderManage/modules/voucher-form.vue, .../modules/stage-contract-sign.vue, .../modules/stage-receipt-voucher.vue

### he-vpp.admin-h5: fix:修复按钮状态

- Hash: `b10ee217` | 日期: 2025-11-20 | 作者: 张硕文
- 业务域: BT, 审核, 合同, 订单
- 文件: 

### he-vpp.admin-h5: opt:订单增加防连点

- Hash: `0373c6de` | 日期: 2025-11-20 | 作者: 张硕文
- 业务域: 电费, 合同, 支付, 订单, BT, 审核
- 文件: .../orderManage/modules/order-create-modal.vue, .../orderManage/modules/voucher-form.vue, .../modules/stage-contract-sign.vue, .../modules/stage-invoice-upload.vue, .../modules/stage-receipt-voucher.vue, .../modules/stage-settlement-apply.vue, 8 files changed, 251 insertions(+), 144 deletions(-)

### he-vpp.admin-h5: opt:回款审批提交增加防连点

- Hash: `58b91063` | 日期: 2025-11-20 | 作者: 张硕文
- 业务域: 支付, 审核, 订单
- 文件: 

### he-vpp.admin-h5: feat:pdf预览

- Hash: `6f1d30d3` | 日期: 2025-11-20 | 作者: 张硕文
- 业务域: 电价, 合同, 订单, 租金, 审核
- 文件: src/locales/langs/en-us.ts, src/locales/langs/zh-cn.ts, 4 files changed, 104 insertions(+), 82 deletions(-)

### he-vpp.admin-h5: feat:修改对账单线下模板

- Hash: `4341cace` | 日期: 2025-11-20 | 作者: 张硕文
- 业务域: 审核, 结算, 订单
- 文件: 2 files changed, 19 insertions(+), 1 deletion(-)

### he-vpp.admin-h5: opt:删除历史无用接口调用

- Hash: `5104ac97` | 日期: 2025-11-19 | 作者: 张硕文
- 业务域: 租金
- 文件: 2 files changed, 26 deletions(-)

### he-vpp.admin-h5: opt:回款管理确认增加可配置权限

- Hash: `42670420` | 日期: 2025-11-19 | 作者: 张硕文
- 业务域: 支付, 审核
- 文件: 2 files changed, 5 insertions(+), 2 deletions(-)

### he-vpp.admin-h5: fix:采购管理绿证咨询服务时隐藏收货凭证

- Hash: `0e1d3994` | 日期: 2025-11-19 | 作者: 张硕文
- 业务域: EPC, 结算, 合同
- 文件: 

### he-vpp.admin-h5: opt:调整代码判断

- Hash: `f26d11de` | 日期: 2025-11-18 | 作者: 张硕文
- 业务域: 订单
- 文件: 

### he-vpp.admin-h5: opt:优化代码逻辑

- Hash: `30a0579b` | 日期: 2025-11-18 | 作者: 张硕文
- 业务域: 订单
- 文件: 2 files changed, 2 insertions(+), 2 deletions(-)

### he-vpp.admin-h5: fix:增加错误数据阻断

- Hash: `14264fb3` | 日期: 2025-11-18 | 作者: 张硕文
- 业务域: EPC, 合同, 订单, BT, 审核, 结算
- 文件: 2 files changed, 45 insertions(+), 44 deletions(-)

### he-vpp.admin-h5: feat:供应商V码改为必填

- Hash: `2d2f68cb` | 日期: 2025-11-18 | 作者: 张硕文
- 业务域: 电费
- 文件: 

### he-vpp.admin-h5: opt:优化上传组件数量限制提示

- Hash: `d9451de6` | 日期: 2025-11-18 | 作者: 张硕文
- 业务域: 租金
- 文件: 

### he-vpp.admin-h5: fix:恢复文件上传数量限制

- Hash: `b190e9d1` | 日期: 2025-11-18 | 作者: 张硕文
- 业务域: BT, 合同, 订单
- 文件: 

### he-vpp.admin-h5: opt:回款列表取值，调整业务列表空值展示

- Hash: `3f68b79b` | 日期: 2025-11-18 | 作者: 张硕文
- 业务域: BT, 订单
- 文件: src/views/businessManage/intentionManage/index.vue, .../modules/intention-operate-modal.vue, src/views/businessManage/orderManage/index.vue, .../orderManage/modules/certificate-selection.vue, .../orderManage/modules/contract-form.vue, .../orderManage/modules/customer-info.vue, .../orderManage/modules/log-list.vue, .../orderManage/modules/order-create-modal.vue

### he-vpp.admin-h5: opt:文件上传组件改造，手机端适配优化，增加网络检测工具

- Hash: `fb1c3963` | 日期: 2025-11-17 | 作者: 张硕文
- 业务域: 租金, BT, 订单
- 文件: .../global-header/components/portal-current.vue, .../global-header/components/user-avatar.vue, src/locales/langs/en-us.ts, src/locales/langs/zh-cn.ts, src/main.ts, src/plugins/networkMonitor.ts, src/styles/scss/element-plus.scss, src/typings/components.d.ts

### nahui-dashboad-h5: opt:调整电站窗口元素大小自适应

- Hash: `64b031cd` | 日期: 2025-12-05 | 作者: 张硕文
- 业务域: 功率, 招银, 电站, 订单, 租金
- 文件: src/components/capital/cityInfo.vue, src/components/capital/cityInfoOverView.vue, src/components/cmb/accumulatedPower.vue, src/components/cmb/cityInfo.vue, src/components/cmb/cityInfoOverView.vue, src/components/spdb/accumulatedPower.vue, src/components/spdb/cityInfo.vue, src/components/spdb/cityInfoOverView.vue

### nahui-dashboad-h5: opt:调整电站弹窗样式，增加可视内容，根据系统缩放调整图片最大高度，资方大屏查看其他大屏时跳转标签页改为弹窗查看

- Hash: `45d28eb5` | 日期: 2025-12-05 | 作者: 张硕文
- 业务域: 招银, 功率, 电站, 订单
- 文件: src/components/capital/cityInfo.vue, src/components/capital/cityInfoOverView.vue, src/components/capital/cityInfoRecord.vue, src/components/cmb/Core.vue, src/components/cmb/cityInfo.vue, src/components/cmb/cityInfoOverView.vue, src/components/cmb/cityInfoRecord.vue, src/components/spdb/Core.vue

### nahui-dashboad-h5: opt:累计数据概览和总实时功率与发电量数值改为保留两位小数

- Hash: `febafc90` | 日期: 2025-11-19 | 作者: 张硕文
- 业务域: 招银, 电价
- 文件: src/components/spdb/Realtime.vue, src/components/spdb/Total.vue, 4 files changed, 22 insertions(+), 4 deletions(-)

## 深度业务链分析

### 1. 运维商自动划转机制 (TAEI-2698/2699/2700)
**核心发现**: 电站完工后通过 `autoTransferStationOp()` 方法自动将电站划转给运维商
- **触发点**: 完工确认审核通过(auditOk)、EPC模式下单、华润模式确认、线下电站审核通过
- **划转依据**: 根据电站所在区域(regionId)查询已中标的运维授权区域(status=ENABLE, isInvestment=0)
- **同步更新**: 电站opMemberId + 运维承接时间(opTime) + LightOperationStation记录
- **合同关联**: 每5个运维区域自动生成一份"服务区域授权补充协议"
- **影响范围**: 46+ 引用CompleteConfirmService的文件，涉及排单调度(DispatchOrderAspect)、越秀状态机、华润EPC模式、银联租金队列

### 2. 共享支付体系 (TAEI-2710/2716/2724/2727)
**核心发现**: 共享支付是一个完整的支付管理子系统
- **实体体系**: LightShareBill(账单) → LightShareBillRecord(明细) → LightShareBillPayFailRecord(失败记录)
- **审核流程**: WAIT_FINANCE_AUDIT → WAIT_CHAINLEAD_AUDIT → AUDIT_PASS/AUDIT_NOT_PASS
- **账单状态**: INIT → CONFIRM(一审→二审确认后)
- **支付账户**: 从电站银行卡信息取账户数据(银行卡号、联行号、支行名称)
- **失败处理**: 记录失败原因、支持重新支付、记录处理结果
- **前端展示**: 商户通/小程序/HDS增加支付成功/失败记录展示
- **退汇处理**: 支持退汇和退回业务流程

### 3. 银联/通联支付 (TAEI-2702)
**核心发现**: 银联接口有235+ 相关Java文件，是核心支付通道
- 涉及实体: LightUnionpayBill/BillRecord/Mch/User/RentRecord
- 接口增加字段: 在运维商授权区域新增招商标识字段
- 常量: TangConstants(通联支付)

### 4. HDS电费报表 (TAEI-2694)
**核心发现**: HDS系统新增分中心/项目公司/资方三个维度的电费报表
- 涉及rrsjk-light-report-service和nahui-pv.hds-h5前端
- 关键优化: 浦银发电统计SQL、电费暂估逻辑
- 前端变更: 李培龙负责，涉及API命名、电费字段、数据字典

### 5. 运维商政策兑现 (TAEI-2709/2729/2730)
**核心发现**: 运维商激励政策分正向和负向
- 正向: LightSpOpsPositiveIac(运维商正向政策)
- 负向: 负向政策兑现功能优化
- 处理器: SpInspirePolicyIncomeHandlerImpl(政策收入处理)
- 特殊费用: OperationMaintenanceServiceImpl运维商特殊费用模块
