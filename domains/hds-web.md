# HDS Web 后端服务

更新时间: 2026-05-24

> **来源**: `rrsjk-hds-web` 全量通读 (2026-05-24)
> **证据等级**: 代码明确证明

## 服务定位

`rrsjk-hds-web` 是**海尔新能源 HDS (Haier Digital Station) Web 后端服务**，提供多个业务模块的 HTTP API 接口。主要服务于 CBS 管理后台和部分前端应用，涵盖电站管理、EPC 项目管理、运维管理、储能收入统计、文件上传等功能。

## 技术架构

- **框架**: Spring Boot 2.2.4 + Spring Security OAuth2 + Swagger 2.9.2
- **认证**: JWT Token (RSA 公钥验证) + OAuth2
- **依赖**: 通过 Dubbo 调用 rrsjk-light-api, rrsjk-finance-api, rrsjk-light-operation-api, rrsjk-light-report-api, rrsjk-light-data-api 等
- **安全过滤器链**: CorsFilter(90) → IpWhitelistFilter(95) → DashboardTokenFilter(85) → AccessTokenCheckFilter(100) → ActuatorEndpointFilter(105)

## 核心业务模块

### 1. 电站管理 (LightStation)

**Controller**: `LightStationController` (`/light/station/`)

提供电站查询、详情、审核、变更等操作。依赖 Dubbo 服务 `LightStationService`。

### 2. EPC 项目管理 (CmLightProject)

**Controller**: `CmLightProjectController` (`/light/cmProject/`)

| 路由 | 方法 | 说明 |
|---|---|---|
| `/findProjectList.do` | GET | 项目列表分页查询 |
| `/doExportProject.do` | GET | 导出项目列表 Excel |
| `/doExport` | GET | 导出项目物料清单 |
| `/getDraftProject.do` | GET | 查看草稿 |
| `/getProject.do` | GET | 查看项目信息 |
| `/temporaryProject.do` | POST | 暂存项目信息 |
| `/saveProject.do` | POST | 保存项目信息（下一步） |
| `/findReceiptList.do` | GET | 查询收款里程碑 |
| `/temporaryReceipt.do` | POST | 暂存收款里程碑 |

**Controller**: `CmLightContractController` (`/light/cmContract/`)
- 项目合同管理（查看/保存/按项目查询）
- 安装商查询（过滤只有 `cm_installer` 角色的服务商）
- 供应商查询

**Controller**: `CmLightMilestoneCheckController` (`/light/cmCheck/`)
- 付款里程碑验收/申请付款
- 收款里程碑验收/上传凭证
- 查看里程碑资料/发票

**Controller**: `LightStationEpcController` (`/lightStation/epc`)
- EPC 电站管理查询
- EPC 审核 (`approval`)
- EPC 终审二验 (`approvalFinal`)

### 3. 资方专属电站管理

**中银电站** (`BocLightStationController`, `/bocLightStation`):
- `queryPage` — 中银电站列表
- `getStationDetail` — 电站详情（含合同、验收确认、方案配置）
- `showRecord.do` — 电站审核记录（特殊电站ID会掩盖驳回记录）

**华电电站** (`CHDEpcLightStationController`, `/CHDEpcLightStation`):
- 同中银接口结构

**招银金租** (`CmbLeasingStationController`, `/cmbLeasingStation`):
- `queryPage` — 招银金租电站列表

### 4. 运维管理

**Controller**: `CreateOperationMaintenanceStationController` (`/createOperationMaintenanceStation`)
- `importData.do` — 运维收入管理历史数据导入（Excel）
- `importDataByHuaRong.do` — 华融电站数据导入
- `simpleImportData.do` — 运维收入管理导入（只做冲销及主数据状态回退）
- `importDataTwo.do` — 运维收入管理导入格式2
- `removeOpAuth.do` — 招商触发移除区域
- `createSupplementContract.do` — 招商区域触发补充信息新增
- `downTemplateByChongXiao` — 下载冲销导入模板

**Controller**: `OperationHistorySettleController` (`/operationHistorySettle`)
- `import.do` — 历史账单运维商导入

### 5. 储能收入统计

**Controller**: `EnergyStatisticIncomeController` (`/energy`)

| 路由 | 方法 | 说明 |
|---|---|---|
| `/getScopeDataByDate` | GET | 储能收入数据查询（市场分类） |
| `/getDetail` | GET | 储能收入明细查询 |
| `/exportDetail` | GET | 导出储能收入明细 Excel |

查询类型: `yearIncome`(年收入), `monthIncome`(月收入), `dayIncome`(日收入), `yearOrder`(年订单), `dayOrder`(日订单)
产品类型: `GSYQY`(工商业-区域), `GSYDKH`(工商业-大客户), `BXS`(便携式)

### 6. 文件上传 (OSS)

| Controller | 路由前缀 | 说明 |
|---|---|---|
| `OssFileController` | `/oss/file/` | 通用文件上传 |
| `OssImageController` | `/oss/image/` | 图片上传 |
| `OssApkFileController` | `/oss/apkFile/` | APK 文件上传 |

**APK 上传分类**:
- `uploadLvFile.do` — 绿能 V5 APK
- `uploadLvV4File.do` — 绿能 V4 APK
- `uploadNgbFile.do` — 纳光宝 APK
- `uploadOpsFile.do` — 海尔绿能运维 APK

### 7. 项目公司管理

**Controller**: `LightCompanyInfoController` (`/light/company`)
- `queryCompanyList` — 查询项目公司列表（按省份过滤）
- `queryRelateCompanyInfo` — 获取用户关联的项目公司

### 8. 逆变器信息

**Controller**: `LightInverterController` (`/inverter`)
- 目前为空壳 Controller，具体逻辑在 `rrsjk-light-data-service` 中

## 安全配置

### OAuth2 认证
- JWT Token Store（RSA 公钥验证）
- 公钥文件位置: `{profile}/key/rsa_public_key.pem`
- `AbstractController` 提供 `currentUserDetail()`, `currentUserName()`, `getIp()` 等工具方法

### 管理员白名单
`canLookAll()` 方法硬编码了13个可以查看所有数据的账号：
```
shaozhuqing@haier.com, jxj@haier.com, 00080789, liuyp, 00627371,
01510428, 01067661, 00980722, 00047610, epc_admin, 00080770
```

### IP 白名单
`IpWhitelistFilter` 提供 IP 级别访问控制。

### XSS 过滤
`XssFilter` 拦截所有请求，排除静态资源路径。

## 特殊电站 ID 列表

中银/华电电站 Controller 中硬编码了一组特殊电站 ID（48个），这些电站的审核记录会被修改：
```
5440, 6026, 7220, 8843, 9071, 9527, 10577, 10677, 10778, 10783,
10785, 10977, 11305, 11604, 11776, 11930, 12174, 12277, 12384,
13505, 13606, 14151, 14255, 14261, 14287, 14334, 14438, 14439,
14440, 14551, 14570, 14579, 15862, 17371, 18246, 18299, 18434,
18436, 18438, 22917, 23646, 24021, 24307, 25052, 26761
```
这些电站的"终审一验驳回"记录会被自动改为"通过"。

## 运维资产所属转换

`trantsSpecialFlag()` 方法处理运维资产所属标记转换：
- `PF_ALL` → 转换为所有以 `PF_` 开头的 SpecialFlag

## 与光伏业务的关系

HDS Web 是光伏业务的**重要 HTTP API 入口层**，特别是 EPC 项目管理、电站管理、运维收入管理等核心业务。它不直接操作数据库，而是通过 Dubbo 调用底层微服务。

### 业务合作意向与逆变器数据过滤修复 (代码明确证明, 2026-05-25)
**来源**: `rrsjk-hds-web` → `BusinessCooperationIntentionController.java` (sunzn, commits 69b1a343/144b80b5/3db84380, 2026-05-25)
- 修复逆变器数据过滤逻辑错误
- 修复数据时间戳过滤逻辑错误
- 移除硬编码的测试数据
- **影响**: 业务合作意向模块的逆变器数据查询准确性

### 运维租金停付 Controller (代码明确证明, 2026-06-22)
**来源**: `rrsjk-hds-web` → `RentSuspendApplicationController.java` (sunzn, 2026-05-27 创建, 2026-06-22 合入 master)
**路由**: `/rentSuspendApplication/*`
**业务**: 业主租金停付申请管理

**接口列表**:
- `GET /list.do` — 分页查询租金停付列表 (按电站编码/业主名称/状态筛选)
- `POST /import.do` — Excel 批量导入停付申请
- `GET /export.do` — 导出停付申请列表 (EasyExcel)
- 依赖: `RentSuspendApplicationService` (Dubbo), `LightOperationBaseController` (基类)

**Excel 模板字段**: `RentSuspendApplicationExcel.java` (197行) — 包含电站编码、业主姓名、身份证号(脱敏)、停付原因、停付金额等

### 分中心数据源切换 (代码明确证明, 2026-06-22)
**来源**: `rrsjk-hds-web` → `AbstractController.java` (commit: dda2b48b, yumiao, 2026-06-22)

**变更**: 新增 `getSubCenterCodesNewVersion(Long userId)` 方法，使用 `SysSubCenterService.getSubCentersByUserId()` (来自 system-service) 替代旧的分中心查询方式。

**影响**: 所有继承 AbstractController 的 HDS Controller 可统一使用新方法获取当前用户关联的分中心编码列表。当用户无分中心关联时返回 `["-1"]` 作为空标记。

### 手动生成签约与并网规模报表 (代码明确证明, 2026-06-18)
**来源**: `rrsjk-hds-web` (commit: e140c26d, baoxin, 2026-06-18)
- 新增手动触发签约与并网规模报表生成接口

---

## 电站电费报表模块 (代码明确证明, 2026-06-23)

**来源**: `nahui-pv.hds-h5` (commits: fc29919..bce412a, 李培龙, 2026-06-16~23)

### 新增页面
| 文件 | 行数 | 功能 |
|---|---|---|
| `src/views/maintainance/elecBill/electricity/eleStation.vue` | 873 | 电站电费报表列表 |
| `src/views/maintainance/elecBill/electricity/eleStationDetail.vue` | 423 | 电站电费详情 |
| `src/views/maintainance/elecBill/electricity/components/ElecReportChart.vue` | 382 | 电费报表图表组件 |
| `src/views/maintainance/elecBill/electricity/components/ExportTaskDialog.vue` | 262 | 异步导出任务管理弹窗 |

### 路由
`src/router/maintainance.js` 新增 `elecBill/electricity` 路由

### API
`src/api/maintainance.js` 新增:
- `getExportList` — 导出任务列表查询
- `cancelExport` — 取消导出任务
- 电费报表数据查询接口

### 异步导出机制
- **taskType**: `STATION_ELEC_REPORT`
- **状态流转**: PENDING → PROCESSING → COMPLETED / FAILED / CANCELLED
- **自动刷新**: 有 PENDING/PROCESSING 任务时每 5 秒自动刷新列表
- **下载链接有效期**: 24 小时
- **文件清理**: 7 天后自动清理

### Bug 修复
- 仓库信息编辑时，仓库等级改为根据选中行的等级赋值（原来赋值逻辑有误）
- 库存监控页面取消重复的查询条件
