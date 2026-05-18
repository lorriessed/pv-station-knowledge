# data/api-endpoints

更新时间: 2026-05-10

## 已确认知识

### 年度规模政策 API (rrsjk-admin-web)
**来源**: `LightAnnualScalePolicyController.java` (commit ee5b831 等)
基础路径: `/annualScalePolicy`

| 路径 | 方法 | 说明 | 权限 |
|---|---|---|---|
| list.html | GET | 列表页面 | annualScalePolicy:read:list |
| form.html | GET | 新增/编辑页面 | annualScalePolicy:read:edit |
| showDetail.html | GET | 展示详情 | annualScalePolicy:showDetail |
| datagrid.json | POST | 分页查询 | annualScalePolicy:read:list |
| listEnable.json | POST | 查询有效政策列表 | - |
| getById.json | POST | 根据ID查询 | - |
| create.json | POST | 新增政策 | - |
| update.json | POST | 更新政策 | - |
| delete.json | POST | 删除政策 | - |
| changeStatus.json | POST | 启用/禁用 | - |
| stagingList.html | GET | 月度暂存列表页 | annualScalePolicy:staging:list |
| stagingDatagrid.json | POST | 月度暂存分页 | annualScalePolicy:staging:list |
| monthlyList.html | GET | 月度暂估列表页 | annualScalePolicy:monthly:list |
| monthlyDatagrid.json | POST | 月度暂估分页 | annualScalePolicy:monthly:list |
| monthlyDetail.html | GET | 月度暂估详情页 | annualScalePolicy:monthly:list |
| monthlyDetail.json | POST | 月度暂估详情分页 | annualScalePolicy:monthly:list |
| autoCalculate.json | POST | 手动触发当月核算 | annualScalePolicy:calculate |
| autoCalculateByMonth.json | POST | 手动触发指定月核算 | annualScalePolicy:calculate |
| realSettleList.html | GET | 实际兑现列表页 | annualScalePolicy:realSettle:list |
| confirmRealSettle.json | POST | 确认兑现 | annualScalePolicy:realSettle:confirm |
| cancelMonthlyEstimate.json | POST | 冲销月度暂估 | annualScalePolicy:realSettle:cancel |
| reportList.html | GET | 年度兑现报表页 | annualScalePolicy:report:list |
| reportDatagrid.json | POST | 年度兑现报表数据 | annualScalePolicy:report:list |
| monthlyExport.do | GET | 月度暂估结果导出 | annualScalePolicy:monthly:export |

### 服务商保证金变更 API (rrsjk-admin-web)
**来源**: `LightMerchantDepositChangeController.java` (新增文件)
基础路径: `/merchantDepositChange`

| 路径 | 说明 | 权限 |
|---|---|---|
| list.html | 列表页面 | merchantDepositChange:read:list |
| datagrid.json | 分页查询 | merchantDepositChange:read:list |

### 审核派单时间配置 API (rrsjk-admin-web)
**来源**: `LightAuditDispatchTimeConfigController.java` (新增文件)
基础路径: `/dispatch/time/config/`

| 路径 | 说明 | 权限 |
|---|---|---|
| list.html | 列表页面 | dispatch:timeConfig:read |
| doList.do | 列表查询 | dispatch:timeConfig:read |

### 电费收益（非户用）完整 API (rrsjk-admin-web)
**来源**: `LightProjectElectricOrderController.java` (基础路径 `/lightProjectElectricOrder`)

| 路径 | 方法 | 说明 | 权限 |
|---|---|---|---|
| list.html | GET | 列表页面 | lightProjectElectricOrder:read:list |
| doList.do | POST | 分页查询 | lightProjectElectricOrder:read:list |
| doListWithInvoice.do | POST | 带发票信息的分页查询 | lightProjectElectricOrder:read:list |
| detail.html | GET | 详情页 | - |
| detailZero.html | GET | 零碳详情页 | - |
| audit.html | GET | 审核页 | - |
| auditZero.html | GET | 零碳审核页 | - |
| findByIds.do | POST | 根据ID列表查询 | - |
| checkOrderIdsBeforeAcknowledge.do | POST | 签收前校验订单ID | - |
| batchAcknowledgeOrder.do | POST | 批量签收订单 | - |
| batchAcknowledgeOrderByBatchNo.do | POST | 按批次号批量签收 | - |
| confirm.do | POST | 单条审核确认 | lightProjectElectricOrder:write:confirm |
| confirmAll.do | POST | 批量审核确认 | lightProjectElectricOrder:write:confirm |
| confirmIncomeToSap.do | POST | 批量SAP收入记账 | lightProjectElectricOrder:write:confirm |
| confirmPaid.do | POST | 确认收款 | lightProjectElectricOrder:write:confirm |
| confirmPaidAll.do | POST | 批量确认收款 | lightProjectElectricOrder:write:confirm |
| doExport.do | GET | 导出(限流) | @LimitationExport |
| doListWithInvoiceExport.do | GET | 带发票导出 | - |
| importData.do | POST | 导入数据(xls) | - |
| importReceiptData.do | POST | 导入收款数据 | - |
| downTemplate.do | GET | 下载导入模板 | - |
| downReceiptTemplate.do | GET | 下载收款模板 | - |
| deleteAll.do | POST | 批量删除 | lightProjectElectricOrder:write:delete |
| deleteByBatchAndInvoiceNos.do | POST | 按批次+开票序号删除 | lightProjectElectricOrder:write:delete |
| rejectOrder.do | POST | 拒绝订单 | - |
| rejectByBatchNumbers.do | POST | 按批次号拒绝 | - |
| rejectByInvoiceNumbers.do | POST | 按开票序号拒绝 | - |
| uploadFile.do | POST | 上传影像文件 | - |
| editInfo.do | POST | 编辑信息 | - |
| findByBatchNumbers.do | POST | 按批次号查询(WAIT状态) | - |
| findByBatchNumbersWaitConfirm.do | POST | 按批次号查询(WAIT_CONFIRM状态) | - |
| findAccounts | POST | 查询收款账户 | - |
| sumByInvoiceNumber.do | POST | 按开票序号汇总 | - |
| fapManual.do | POST | 发票手工处理 | - |
| checkElecNoBound | POST | 检查发电户号绑定 | - |
| checkBatchNoForConfirmSk.do | POST | 批次号确认前校验 | - |
| lightProjectElectricOrderInvoiceList.html | GET | 发票列表页 | lightProjectElectricOrder:read:list |

**导出逻辑** (2026-05-07 重构):
- 导出接口已切换到 report-service ODS 数据源
- 保留原有 light-service 用于其他 CRUD 操作
- 增加导出限制功能

## 待确认
- 更多业务模块的 API 端点整理。

### 资方主数据 API (rrsjk-admin-web)
**来源**: `InvestorMasterDataController.java`
基础路径: `/investor/`

| 路径 | 方法 | 说明 | 权限 |
|---|---|---|---|
| investorMasterData.html | GET | 资方信息管理页面(含统计) | investor:read:list |
| add.html | GET | 新增资方页面 | investor:write:create |
| investorMasterData.do | POST | 分页查询资方信息 | investor:read:list |
| addInvestor.do | POST | 新增资方 | investor:write:create |
| update.html | GET | 编辑资方页面 | investor:write:update |
| updateInvestor.do | POST | 更新资方信息 | investor:write:update |
| updateCooperation.html | GET | 编辑合作信息页面 | investor:write:update |
| updateCooperation.do | POST | 更新合作信息 | investor:write:update |
| delete.do | POST | 删除资方 | investor:write:delete |
| updateRating.do | POST | 修改资方评级 | investor:write:rating |
| updateCooperationStatus.do | POST | 更新合作状态 | investor:write:cooperation |
| getInvestorById.do | POST | 根据ID查询 | investor:read:detail |
| getInvestorByName.do | POST | 根据名称查询 | - |
| exportInvestor.do | GET | 导出资方数据 | investor:read:export |
| getProvinceList.do | POST | 获取省份列表 | investor:read:list |
| getStatistics.do | POST | 获取统计数据 | investor:read:list |

### 电费账单 API (rrsjk-admin-web)
**来源**: `EnergyElecOrderController.java`
基础路径: `/energyElecOrder/`

| 路径 | 说明 | 权限 |
|---|---|---|
| list.html | 列表页面 | energyElecOrder:list |
| list.do | 分页查询 | energyElecOrder:list |
| doExport.do | 导出电费账单 | @LimitationExport(3次/50秒) |

### 配货申诉审核 API (rrsjk-admin-web)
**来源**: `PurchaseAppealsAuditController.java`
基础路径: `/purchaseAppealsAudit/`

| 路径 | 说明 | 权限 |
|---|---|---|
| list.html | 列表页面 | purchaseAppealsAudit:read:list |
| doList.do | 分页查询 | purchaseAppealsAudit:read:list |
| doExport.do | 导出 | purchaseAppealsAudit:read:export |
| batchAudit.do | 批量审核 | purchaseAppealsAudit:read:audit |
| auditSingle.do | 单条审核 | purchaseAppealsAudit:read:audit |

### 电站迁移 API (rrsjk-admin-web)
**来源**: `SwitchModeController.java`
基础路径: `/switchMode/`

| 路径 | 说明 |
|---|---|
| list.html | 列表页面 |
| queryPage.do | 分页查询 |
| confirm | 片长批量审核 |
| confirmMarketing | 市场总监批量审核 |
| confirmAsset | 资产部批量审核 |
| doExport.do | 导出(限流: 1次/50秒) |
| importData.do | 导入数据(xls) |
| downTemplate.do | 下载导入模板 |

### 共享付款失败记录 API (rrsjk-admin-web)
**来源**: `LightShareBillRecordFailLogController.java`
基础路径: `/lightShareBillRecordFailLog/`

| 路径 | 说明 | 权限 |
|---|---|---|
| list.html | 列表页面 | LightShareBillRecordFailLog:list |
| doList.do | 分页查询 | LightShareBillRecordFailLog:list |
| findById.do | 根据ID查询 | LightShareBillRecordFailLog:list |
| change.do | 修改记录 | LightShareBillRecordFailLog:change |
| add.do | 新增记录 | LightShareBillRecordFailLog:add |
| downTemplate.do | 下载导入模板 | - |

### 顶好商机 API (rrsjk-merchant-web)
**来源**: `DhBusinessOpportunityController.java`
基础路径: `/dhBusinessOpportunity`

| 路径 | 说明 |
|---|---|
| queryTableList | 商机分页列表 |
| selectOption | 商机下拉框(建站用) |
| add | 录入商机 |
| edit | 修改商机 |
| getDetailById | 根据ID获取详情 |
| delete | 删除商机(按stationNo) |
| getByInputPieceId | 按进件序号获取详情 |

### 领用单 API (rrsjk-merchant-web)
**来源**: `LightUseOrderController.java`
基础路径: `/lightUseOrder`

| 路径 | 说明 |
|---|---|
| completeBeforeDoList.do | 完工前领用列表 |
| completeBeforeExport.do | 完工前领用导出 |
| manualOutStock.do | 手动出库(防重:10s) |

### 领用异常 API (rrsjk-merchant-web)
**来源**: `LightUseQueueController.java`
基础路径: `/lightUseQueue`

| 路径 | 说明 |
|---|---|
| doList.do | 领用异常列表 |
| doExport.do | 领用异常导出 |

### AI助手 API (rrsjk-merchant-web)
**来源**: `ChatMessageController.java`, `UserProblemManagementController.java`
基础路径: `/api/chat`, `/api/assistant/userProblemManagement`

| 路径 | 说明 |
|---|---|
| /api/chat/messages | 接收AI聊天消息 |
| /api/chat/test | 测试接口 |
| /api/assistant/userProblemManagement/page | 分页查询问题记录 |
| /api/assistant/userProblemManagement/{id} | 根据ID查询 |
| POST /api/assistant/userProblemManagement | 创建问题记录 |
| PUT /api/assistant/userProblemManagement/{id} | 更新问题记录 |
| PUT /api/assistant/userProblemManagement/{id}/solved | 更新解决状态 |
| /api/assistant/userProblemManagement/user/{userAccount} | 按用户账号查询 |
| /api/assistant/userProblemManagement/subCenter/{subCenterCode} | 按分中心查询 |
| POST /api/assistant/userProblemManagement/batch | 批量插入 |

### 图片百度AI识别 API (rrsjk-merchant-web)
**来源**: `ImageRecognizeController.java`
基础路径: `/light/imageRecognize`

| 路径 | 说明 |
|---|---|
| imageNum.do | 图像AI识别太阳板数量 |

## 来源
- rrsjk-admin-web 代码扫描 2026-05-10。

### 招银租赁租后 API (rrsjk-openapi-web)
**来源**: `ZhaoYinLeaseController.java` (2026-05-16 全量通读, 代码明确证明)
基础路径: `/openapi/zhaoyin`

| 路径 | 方法 | 说明 | 限流 QPS |
|---|---|---|---|
| `/api/v1/plant/daily-power` | POST | 电站日发电量查询 | 7 |
| `/api/v1/plant/status` | POST | 电站状态查询 | 7 |
| `/api/v1/electricity/bill` | POST | 电站电费账单查询 | 7 |
| `/api/v1/inverter/real-time-power` | POST | 逆变器发电功率查询 (已注释停用) | 7 |

**服务配置**: 端口 8083, context-path `/openapi`, Dubbo + Zookeeper 注册中心, OAuth2 JWT 认证
