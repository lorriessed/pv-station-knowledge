     1|# data/api-endpoints
     2|
     3|更新时间: 2026-05-10
     4|
     5|## 已确认知识
     6|
     7|### 年度规模政策 API (rrsjk-admin-web)
     8|**来源**: `LightAnnualScalePolicyController.java` (commit ee5b831 等)
     9|基础路径: `/annualScalePolicy`
    10|
    11|| 路径 | 方法 | 说明 | 权限 |
    12||---|---|---|---|
    13|| list.html | GET | 列表页面 | annualScalePolicy:read:list |
    14|| form.html | GET | 新增/编辑页面 | annualScalePolicy:read:edit |
    15|| showDetail.html | GET | 展示详情 | annualScalePolicy:showDetail |
    16|| datagrid.json | POST | 分页查询 | annualScalePolicy:read:list |
    17|| listEnable.json | POST | 查询有效政策列表 | - |
    18|| getById.json | POST | 根据ID查询 | - |
    19|| create.json | POST | 新增政策 | - |
    20|| update.json | POST | 更新政策 | - |
    21|| delete.json | POST | 删除政策 | - |
    22|| changeStatus.json | POST | 启用/禁用 | - |
    23|| stagingList.html | GET | 月度暂存列表页 | annualScalePolicy:staging:list |
    24|| stagingDatagrid.json | POST | 月度暂存分页 | annualScalePolicy:staging:list |
    25|| monthlyList.html | GET | 月度暂估列表页 | annualScalePolicy:monthly:list |
    26|| monthlyDatagrid.json | POST | 月度暂估分页 | annualScalePolicy:monthly:list |
    27|| monthlyDetail.html | GET | 月度暂估详情页 | annualScalePolicy:monthly:list |
    28|| monthlyDetail.json | POST | 月度暂估详情分页 | annualScalePolicy:monthly:list |
    29|| autoCalculate.json | POST | 手动触发当月核算 | annualScalePolicy:calculate |
    30|| autoCalculateByMonth.json | POST | 手动触发指定月核算 | annualScalePolicy:calculate |
    31|| realSettleList.html | GET | 实际兑现列表页 | annualScalePolicy:realSettle:list |
    32|| confirmRealSettle.json | POST | 确认兑现 | annualScalePolicy:realSettle:confirm |
    33|| cancelMonthlyEstimate.json | POST | 冲销月度暂估 | annualScalePolicy:realSettle:cancel |
    34|| reportList.html | GET | 年度兑现报表页 | annualScalePolicy:report:list |
    35|| reportDatagrid.json | POST | 年度兑现报表数据 | annualScalePolicy:report:list |
    36|| monthlyExport.do | GET | 月度暂估结果导出 | annualScalePolicy:monthly:export |
    37|
    38|### 服务商保证金变更 API (rrsjk-admin-web)
    39|**来源**: `LightMerchantDepositChangeController.java` (新增文件)
    40|基础路径: `/merchantDepositChange`
    41|
    42|| 路径 | 说明 | 权限 |
    43||---|---|---|
    44|| list.html | 列表页面 | merchantDepositChange:read:list |
    45|| datagrid.json | 分页查询 | merchantDepositChange:read:list |
    46|
    47|### 审核派单时间配置 API (rrsjk-admin-web)
    48|**来源**: `LightAuditDispatchTimeConfigController.java` (新增文件)
    49|基础路径: `/dispatch/time/config/`
    50|
    51|| 路径 | 说明 | 权限 |
    52||---|---|---|
    53|| list.html | 列表页面 | dispatch:timeConfig:read |
    54|| doList.do | 列表查询 | dispatch:timeConfig:read |
    55|
    56|### 电费收益（非户用）完整 API (rrsjk-admin-web)
    57|**来源**: `LightProjectElectricOrderController.java` (基础路径 `/lightProjectElectricOrder`)
    58|
    59|| 路径 | 方法 | 说明 | 权限 |
    60||---|---|---|---|
    61|| list.html | GET | 列表页面 | lightProjectElectricOrder:read:list |
    62|| doList.do | POST | 分页查询 | lightProjectElectricOrder:read:list |
    63|| doListWithInvoice.do | POST | 带发票信息的分页查询 | lightProjectElectricOrder:read:list |
    64|| detail.html | GET | 详情页 | - |
    65|| detailZero.html | GET | 零碳详情页 | - |
    66|| audit.html | GET | 审核页 | - |
    67|| auditZero.html | GET | 零碳审核页 | - |
    68|| findByIds.do | POST | 根据ID列表查询 | - |
    69|| checkOrderIdsBeforeAcknowledge.do | POST | 签收前校验订单ID | - |
    70|| batchAcknowledgeOrder.do | POST | 批量签收订单 | - |
    71|| batchAcknowledgeOrderByBatchNo.do | POST | 按批次号批量签收 | - |
    72|| confirm.do | POST | 单条审核确认 | lightProjectElectricOrder:write:confirm |
    73|| confirmAll.do | POST | 批量审核确认 | lightProjectElectricOrder:write:confirm |
    74|| confirmIncomeToSap.do | POST | 批量SAP收入记账 | lightProjectElectricOrder:write:confirm |
    75|| confirmPaid.do | POST | 确认收款 | lightProjectElectricOrder:write:confirm |
    76|| confirmPaidAll.do | POST | 批量确认收款 | lightProjectElectricOrder:write:confirm |
    77|| doExport.do | GET | 导出(限流) | @LimitationExport |
    78|| doListWithInvoiceExport.do | GET | 带发票导出 | - |
    79|| importData.do | POST | 导入数据(xls) | - |
    80|| importReceiptData.do | POST | 导入收款数据 | - |
    81|| downTemplate.do | GET | 下载导入模板 | - |
    82|| downReceiptTemplate.do | GET | 下载收款模板 | - |
    83|| deleteAll.do | POST | 批量删除 | lightProjectElectricOrder:write:delete |
    84|| deleteByBatchAndInvoiceNos.do | POST | 按批次+开票序号删除 | lightProjectElectricOrder:write:delete |
    85|| rejectOrder.do | POST | 拒绝订单 | - |
    86|| rejectByBatchNumbers.do | POST | 按批次号拒绝 | - |
    87|| rejectByInvoiceNumbers.do | POST | 按开票序号拒绝 | - |
    88|| uploadFile.do | POST | 上传影像文件 | - |
    89|| editInfo.do | POST | 编辑信息 | - |
    90|| findByBatchNumbers.do | POST | 按批次号查询(WAIT状态) | - |
    91|| findByBatchNumbersWaitConfirm.do | POST | 按批次号查询(WAIT_CONFIRM状态) | - |
    92|| findAccounts | POST | 查询收款账户 | - |
    93|| sumByInvoiceNumber.do | POST | 按开票序号汇总 | - |
    94|| fapManual.do | POST | 发票手工处理 | - |
    95|| checkElecNoBound | POST | 检查发电户号绑定 | - |
    96|| checkBatchNoForConfirmSk.do | POST | 批次号确认前校验 | - |
    97|| lightProjectElectricOrderInvoiceList.html | GET | 发票列表页 | lightProjectElectricOrder:read:list |
    98|
    99|**导出逻辑** (2026-05-07 重构):
   100|- 导出接口已切换到 report-service ODS 数据源
   101|- 保留原有 light-service 用于其他 CRUD 操作
   102|- 增加导出限制功能
   103|
   104|
### 电站合同 API (rrsjk-merchant-web / rrsjk-admin-web)
**来源**: 代码扫描 2026-05-18

#### 商户通合同管理 (`rrsjk-merchant-web`)
| 路径 | 方法 | 说明 | Controller |
|---|---|---|---|
| `/lightStationContractInfo/findNewOne.do` | GET | 查询合同信息最新记录 | `LightStationContractInfoController` |
| `/lightOpContractRecord/list.do` | GET | 运维合同列表 | `LightOpContractRecordController` |

#### 商户通 H5 合同 (`rrsjk-merchant-h5`)
- 合同列表: `src/views/apv/pro/contractList.vue`
- 支持筛选: 电站编码、业主姓名、审核时间、签约时间、状态、合同类型
- 操作: 查看详情、重发短信、下载合同

#### DCC 签章 API (第三方)
| 配置项 | 说明 |
|---|---|
| `dcc.addContract` | 添加合同/用印申请接口 |
| `dcc.singUrlByTaskNoKjq` | 获取快捷签签署链接 |
| `dcc.signedNotifyUrl` | 签署完成回调地址 |
| `dcc.companyCheck` | 企业认证接口 |
| `dcc.personalRegister` | 个人注册接口 |

### 短信模板映射
| 模板 ID | 用途 | 参数 |
|---|---|---|
| 1133 | 主合同签署通知 | user(姓名), signUrl(签署链接) |
| 1134 | 装机协议签署通知 | user(姓名), signUrl(签署链接) |
| 1135 | 结算协议签署通知 | user(姓名), signUrl(签署链接) |
| 1146 | 权属证明签署通知 | user(姓名), signUrl(签署链接) |

## 待确认
   105|- 更多业务模块的 API 端点整理。
   106|
   107|### 资方主数据 API (rrsjk-admin-web)
   108|**来源**: `InvestorMasterDataController.java`
   109|基础路径: `/investor/`
   110|
   111|| 路径 | 方法 | 说明 | 权限 |
   112||---|---|---|---|
   113|| investorMasterData.html | GET | 资方信息管理页面(含统计) | investor:read:list |
   114|| add.html | GET | 新增资方页面 | investor:write:create |
   115|| investorMasterData.do | POST | 分页查询资方信息 | investor:read:list |
   116|| addInvestor.do | POST | 新增资方 | investor:write:create |
   117|| update.html | GET | 编辑资方页面 | investor:write:update |
   118|| updateInvestor.do | POST | 更新资方信息 | investor:write:update |
   119|| updateCooperation.html | GET | 编辑合作信息页面 | investor:write:update |
   120|| updateCooperation.do | POST | 更新合作信息 | investor:write:update |
   121|| delete.do | POST | 删除资方 | investor:write:delete |
   122|| updateRating.do | POST | 修改资方评级 | investor:write:rating |
   123|| updateCooperationStatus.do | POST | 更新合作状态 | investor:write:cooperation |
   124|| getInvestorById.do | POST | 根据ID查询 | investor:read:detail |
   125|| getInvestorByName.do | POST | 根据名称查询 | - |
   126|| exportInvestor.do | GET | 导出资方数据 | investor:read:export |
   127|| getProvinceList.do | POST | 获取省份列表 | investor:read:list |
   128|| getStatistics.do | POST | 获取统计数据 | investor:read:list |
   129|
   130|### 电费账单 API (rrsjk-admin-web)
   131|**来源**: `EnergyElecOrderController.java`
   132|基础路径: `/energyElecOrder/`
   133|
   134|| 路径 | 说明 | 权限 |
   135||---|---|---|
   136|| list.html | 列表页面 | energyElecOrder:list |
   137|| list.do | 分页查询 | energyElecOrder:list |
   138|| doExport.do | 导出电费账单 | @LimitationExport(3次/50秒) |
   139|
   140|### 配货申诉审核 API (rrsjk-admin-web)
   141|**来源**: `PurchaseAppealsAuditController.java`
   142|基础路径: `/purchaseAppealsAudit/`
   143|
   144|| 路径 | 说明 | 权限 |
   145||---|---|---|
   146|| list.html | 列表页面 | purchaseAppealsAudit:read:list |
   147|| doList.do | 分页查询 | purchaseAppealsAudit:read:list |
   148|| doExport.do | 导出 | purchaseAppealsAudit:read:export |
   149|| batchAudit.do | 批量审核 | purchaseAppealsAudit:read:audit |
   150|| auditSingle.do | 单条审核 | purchaseAppealsAudit:read:audit |
   151|
   152|### 电站迁移 API (rrsjk-admin-web)
   153|**来源**: `SwitchModeController.java`
   154|基础路径: `/switchMode/`
   155|
   156|| 路径 | 说明 |
   157||---|---|
   158|| list.html | 列表页面 |
   159|| queryPage.do | 分页查询 |
   160|| confirm | 片长批量审核 |
   161|| confirmMarketing | 市场总监批量审核 |
   162|| confirmAsset | 资产部批量审核 |
   163|| doExport.do | 导出(限流: 1次/50秒) |
   164|| importData.do | 导入数据(xls) |
   165|| downTemplate.do | 下载导入模板 |
   166|
   167|### 共享付款失败记录 API (rrsjk-admin-web)
   168|**来源**: `LightShareBillRecordFailLogController.java`
   169|基础路径: `/lightShareBillRecordFailLog/`
   170|
   171|| 路径 | 说明 | 权限 |
   172||---|---|---|
   173|| list.html | 列表页面 | LightShareBillRecordFailLog:list |
   174|| doList.do | 分页查询 | LightShareBillRecordFailLog:list |
   175|| findById.do | 根据ID查询 | LightShareBillRecordFailLog:list |
   176|| change.do | 修改记录 | LightShareBillRecordFailLog:change |
   177|| add.do | 新增记录 | LightShareBillRecordFailLog:add |
   178|| downTemplate.do | 下载导入模板 | - |
   179|
   180|### 顶好商机 API (rrsjk-merchant-web)
   181|**来源**: `DhBusinessOpportunityController.java`
   182|基础路径: `/dhBusinessOpportunity`
   183|
   184|| 路径 | 说明 |
   185||---|---|
   186|| queryTableList | 商机分页列表 |
   187|| selectOption | 商机下拉框(建站用) |
   188|| add | 录入商机 |
   189|| edit | 修改商机 |
   190|| getDetailById | 根据ID获取详情 |
   191|| delete | 删除商机(按stationNo) |
   192|| getByInputPieceId | 按进件序号获取详情 |
   193|
   194|### 领用单 API (rrsjk-merchant-web)
   195|**来源**: `LightUseOrderController.java`
   196|基础路径: `/lightUseOrder`
   197|
   198|| 路径 | 说明 |
   199||---|---|
   200|| completeBeforeDoList.do | 完工前领用列表 |
   201|| completeBeforeExport.do | 完工前领用导出 |
   202|| manualOutStock.do | 手动出库(防重:10s) |
   203|
   204|### 领用异常 API (rrsjk-merchant-web)
   205|**来源**: `LightUseQueueController.java`
   206|基础路径: `/lightUseQueue`
   207|
   208|| 路径 | 说明 |
   209||---|---|
   210|| doList.do | 领用异常列表 |
   211|| doExport.do | 领用异常导出 |
   212|
   213|### AI助手 API (rrsjk-merchant-web)
   214|**来源**: `ChatMessageController.java`, `UserProblemManagementController.java`
   215|基础路径: `/api/chat`, `/api/assistant/userProblemManagement`
   216|
   217|| 路径 | 说明 |
   218||---|---|
   219|| /api/chat/messages | 接收AI聊天消息 |
   220|| /api/chat/test | 测试接口 |
   221|| /api/assistant/userProblemManagement/page | 分页查询问题记录 |
   222|| /api/assistant/userProblemManagement/{id} | 根据ID查询 |
   223|| POST /api/assistant/userProblemManagement | 创建问题记录 |
   224|| PUT /api/assistant/userProblemManagement/{id} | 更新问题记录 |
   225|| PUT /api/assistant/userProblemManagement/{id}/solved | 更新解决状态 |
   226|| /api/assistant/userProblemManagement/user/{userAccount} | 按用户账号查询 |
   227|| /api/assistant/userProblemManagement/subCenter/{subCenterCode} | 按分中心查询 |
   228|| POST /api/assistant/userProblemManagement/batch | 批量插入 |
   229|
   230|### 图片百度AI识别 API (rrsjk-merchant-web)
   231|**来源**: `ImageRecognizeController.java`
   232|基础路径: `/light/imageRecognize`
   233|
   234|| 路径 | 说明 |
   235||---|---|
   236|| imageNum.do | 图像AI识别太阳板数量 |
   237|
   238|## 来源
   239|- rrsjk-admin-web 代码扫描 2026-05-10。
   240|
   241|### 招银租赁租后 API (rrsjk-openapi-web)
   242|**来源**: `ZhaoYinLeaseController.java` (2026-05-16 全量通读, 代码明确证明)
   243|基础路径: `/openapi/zhaoyin`
   244|
   245|| 路径 | 方法 | 说明 | 限流 QPS |
   246||---|---|---|---|
   247|| `/api/v1/plant/daily-power` | POST | 电站日发电量查询 | 7 |
   248|| `/api/v1/plant/status` | POST | 电站状态查询 | 7 |
   249|| `/api/v1/electricity/bill` | POST | 电站电费账单查询 | 7 |
   250|| `/api/v1/inverter/real-time-power` | POST | 逆变器发电功率查询 (已注释停用) | 7 |
   251|
   252|**服务配置**: 端口 8083, context-path `/openapi`, Dubbo + Zookeeper 注册中心, OAuth2 JWT 认证
   253|