# CBS 管理后台

更新时间: 2026-05-23

## 概述

CBS (Central Business System) 管理后台是 PVS 光伏系统的**综合管理平台**，提供用户管理、分中心管理、定时任务管理、菜单权限等后台管理功能。

- **仓库**: `cbs-web`
- **分支**: `dev` (日常开发) / `master` (生产)
- **技术栈**: Java + Spring MVC + Shiro + Velocity/FreeMarker 模板
- **部署**: `ROOT` (war包部署到 Tomcat)

> **证据等级**: 代码明确证明 (2026-05-20 增量扫描确认)

---

## 分中心管理 (2026-05-20 新增)

**来源**: `cbs-web` → `SysSubCenterController.java`, `subCenter_list.vm`, `subCenterUser_edit.vm`
**Commits**: 538bf97d/166d577d/db7e82dd/067f144f, 开发者: 德, 2026-05-19~20
**分支**: `feature/202605/regionUnlimit` → dev
**证据等级**: 代码明确证明

> **⚠️ 迁移中 (2026-06-03)**: 旧版 CBS 分中心管理 (`cbs-web`) 正在迁移到新一代 BFF 架构 (`rrsjk-admin-bff` → `subcentermanagement` 模块)。新架构通过 Dubbo 调用 `system-service` 提供 REST API 给 `rrsjk-admin-web-next` (Vue3) 前端。详见 `domains/admin-authz.md` §12。

### Controller 路由

| 路由 | 方法 | 功能 | 模板 |
|---|---|---|---|
| `/sysSubCenter/subCenter.html` | GET | 分中心列表页面 | `subCenter/subCenter_list.vm` |
| `/sysSubCenter/subCenterUser.html` | GET | 分中心人员管理页面 | `subCenter/subCenterUser_edit.vm` |
| `/sysSubCenter/subCenterList` | GET | 分中心列表数据(分页) | - |
| `/sysSubCenter/subCenterUserList` | GET | 分中心人员列表 | - |
| `/sysSubCenter/addSubCenterUser` | POST | 添加分中心人员 | - |

### 查询参数

**分中心列表** (`/sysSubCenter/subCenterList`):
- `q_code`: 分中心编码 (模糊匹配)
- `q_name`: 分中心名称 (模糊匹配)

**分中心人员列表** (`/sysSubCenter/subCenterUserList`):
- `q_subCenterId`: 分中心ID (必填)

**添加分中心人员** (`/sysSubCenter/addSubCenterUser`):
- `q_subCenterId`: 分中心ID (必填)
- `q_users`: 用户列表，格式 `userId:userName:mobile,userId:userName:mobile`

### 实体类

| 类名 | 包路径 | 说明 |
|---|---|---|
| `SysSubCenter` | `com.haier.cbs.system.entity` | 分中心实体 |
| `SysSubCenterUser` | `com.haier.cbs.system.entity` | 分中心用户实体 |
| `SubCenterUserDTO` | `com.haier.cbs.system.dto` | 分中心用户传输对象 |

### Service

| Service | 方法 | 说明 |
|---|---|---|
| `SysSubCenterService` | `findByPager(criteria, pager)` | 分中心分页查询 |
| `SysSubCenterService` | `getUsersBySubCenterId(subCenterId)` | 按分中心ID查询用户 |
| `SysSubCenterService` | `batchAddUsers(subCenterId, userList, operator)` | 批量添加分中心用户（自动跳过已存在, 2026-05-20 新增） |
| `SysSubCenterService` | `batchRemoveUsers(subCenterId, userIdList, operator)` | 批量移除分中心用户（逻辑删除, 2026-05-20 新增） |
| `SysSubCenterService` | `setMembers(subCenterId, userList, operator)` | 全量设置分中心成员（差量计算: 移除不在新列表中的旧成员 + 添加新成员, 2026-05-20 新增） |
| `SysSubCenterService` | `getSubCentersByUserId(userId)` | 按用户ID查询所属分中心列表 |
| `SysSubCenterService` | `getUsersBySubCenterIds(subCenterIdList)` | 按分中心ID列表批量查询用户 |

**2026-05-20 变更** (代码明确证明, commits: fc0aedb/b19a9f6/3236e0c/be46e83/e8d2b21):
- `SubCenterUserDTO` 实现 `Serializable`，支持 Dubbo 序列化传输（含 userId/userName/mobile 字段）
- 分中心用户批量操作接口从简单 userId 列表重构为完整 `SubCenterUserDTO` 列表，支持传递用户名和手机号
- `SysSubCenter` 实体移除软删除字段（`delFlag`/`deleted`）和相关查询条件

### Spring 配置

- `src/main/resources/spring-config/service.xml` 中注册了 `sysSubCenterService`

---

## 登录认证

**来源**: `cbs-web` → `HomeController.java`, `HaiershuiRealm.java`
**证据等级**: 代码明确证明

### 登录接口

| 路由 | 方法 | 功能 |
|---|---|---|
| `/sys/login.do` | POST | Shiro 登录认证 |

### 登录参数

| 参数 | 必填 | 说明 |
|---|---|---|
| `loginId` | 是 | 登录账号 |
| `password` | 是 | 密码 |
| `randomCode` | ~~是~~ **否** | 验证码 (2026-05-20 改为非必填) |
| `redirect` | 否 | 登录成功后跳转地址 |
| `token` | 否 | 包含 mobileReport.html 时跳转移动报表 |

### 密码规则

- 10位以上
- 包含数字、大小写字母、特殊字符
- 正则校验: `PasswordRegexCheckUtil.isPasswordCheckOK()`

### 忘记密码

| 路由 | 方法 | 功能 |
|---|---|---|
| `/sys/forgetPassword.do` | POST | 通过手机验证码重置密码 |

### Shiro Realm

- `HaiershuiRealm`: CBS 自定义 Shiro Realm，处理认证和授权
- 测试环境支持去掉验证码 (commit 422e4e35, mabin, 2025-07-17)

### 登录页面增强 (2026-06-13 增量扫描发现)
- **阿里云 RUM 监控 SDK**: 登录页 (`login.ftl`) 集成阿里云 ARMS RUM 前端监控，支持用户追踪和性能采集 (commits ca7c717d~114f10cd, yumiao, 2025-12-17~19)
- **品牌更新**: 页面品牌名称从"日日顺"统一更新为"海尔" (commit 3163f1ee, yumiao, 2026-01-15)
- **新版体验入口**: 登录页新增"新版体验"入口链接，引导用户试用新版 CBS (commits d9dbbc61~5f3fc0ea, yumiao, 2026-06-05)

---

## 定时任务管理

**来源**: `cbs-web` → `JobLogController.java`, `JobModel.java`
**证据等级**: 代码明确证明

### 路由

| 路由 | 方法 | 功能 |
|---|---|---|
| `/loadJobLogPage.html` | GET | 定时任务日志列表页面 |
| `/getJobLogList.html` | GET | 定时任务日志数据(分页) |

### 查询参数

- `jobId`: 任务ID
- `name`: 任务名称 (模糊匹配)
- `status`: 任务状态
- `pageIndex`: 页码

### 实体

- `SysJobLogEx`: 定时任务日志扩展实体
- `SysJobEx`: 定时任务实体 (jobId, cfgDataStr, cron, jobName, jobType, jobStatus)

### DubboJob 一次性任务自动停止 (2026-06-13 增量扫描发现)
- **功能**: Dubbo 类型定时任务支持执行一次后自动停止
- **实现**: `DubboJobLoader` 新增 `delete` 字段 (从 cfgData JSON 解析)，`DubboJob.execute()` 执行完毕后检查 `delete==1` 则调用 `jobProvider.stopJob(job)` 停止任务
- **配置**: sys_job 表 cfgData 新增 `"delete": 1` 字段即可标记为一次性任务
- **数据库加密**: job-service 使用 `aliyun-encdb-mysql-jdbc` 的 `EncDriver` 替代标准 MySQL 驱动
- **来源**: `job-service/DubboJob.java`, `DubboJobLoader.java` (commit cbb0274a, 20022445, 2024-07-15; 代码明确证明)

---

## 配置信息

### 测试环境 URL

| 配置项 | 值 | 说明 |
|---|---|---|
| `pom.uri-host-and-port` | `http://cbstest.rrsjk.com` | CBS 测试环境地址 (2026-05-20 从 `cbs.rrsjk.com:44444` 变更) |
| `dubbo.registry.address` | `zookeeper://10.2.192.154:2181` | 注册中心 |
| `pom.cookie-domain` | `rrsjk.com` | Cookie 域名 |

---

### 分中心用户编辑模板兼容 (2026-05-20)
- **来源**: `cbs-web` → `src/main/webapp/WEB-INF/templates/subCenter/subCenterUser_edit.vm` (commit e651a0a0, 德, 2026-05-20)
- **变更**: 解决用户表格数据兼容性问题，21 insertions, 26 deletions
- **证据等级**: 代码明确证明

---

## 待确认

- CBS 生产环境部署地址和端口
- CBS 与 PVS 核心服务(rrsjk-light-service等)的数据交互方式
- 分中心(`SysSubCenter`)与 PVS 分中心的关联关系
- `SysSubCenterService` 的完整接口定义和实现

### 项目公司"是否股转"字段 (代码明确证明, 2026-05-23 补漏第7期)
**来源**: `rrsjk-light-service`, `rrsjk-admin-web` (TAEI-2974, tn_wangb, 2026-03-25~04-10)
- CBS项目公司配置列表页面和导出增加"是否股转"字段显示
- 用于区分股转类公司与普通公司，影响FAP对账流程
- 股转非统众乐道公司的电费单据传集团FAP对账，非股转公司走不同流程
- 对应需求: TAEI-2974 (股转类非乐道非统众电费单据传集团FAP对账)

### 分中心改造 — 跨服务扩展 (代码明确证明, 2026-05-22)
**来源**: `rrsjk-light-service` + `system-service` (commits: dc25078/a515ab/552754/c73ea8/56e11d/fc0aed/b19a9f/3236e0, 德+yumiao, 分支 feature/202605/regionUnlimit)
- **rrsjk-light-service (wms)**: 二级库房创建/修改请求新增分中心信息字段
- **rrsjk-light-service (address)**: 地址管理新增分中心校验功能
- **rrsjk-light-service (system)**: 系统用户同步逻辑优化，添加并发处理
- **system-service**: 分中心用户DTO重构，支持完整用户信息传递；批量操作接口支持完整用户信息
- **涉及范围**: 分中心管理从CBS前端扩展到light-service和system-service，形成完整的分中心组织体系
- **证据等级**: 代码明确证明

### 分中心改造 — admin-web 全面适配 (代码明确证明, 2026-06-06 regionUnlimit 合入 master)
**来源**: `rrsjk-admin-web` (分支 `feature/202605/regionUnlimit` → master, merge commit beb8da50, 2026-06-06)
**开发者**: yumiao, 德, baoxin

#### AbstractController 权限方法重构
- **`putSubCenter(params, request)`**: 改为直接调用 `putSubCenterNew`，旧版 `SysPartyService` 查询逻辑被注释掉
- **`putSubCenterNew(params, request)`**: 新增方法，通过 `sysSubCenterService.getSubCentersByUserId(userId)` 查询新版分中心，将 `subCenterCode`/`subCenterName` 写入 `branchList`/`branchNameList`；若无权限则写入 `["-1"]`
- **`putSubCenterBoth(params, request)`**: 新增方法，**合并新旧两套分中心权限** — 先查新版 `SysSubCenterService`，再查旧版 `SysPartyService`，结果合并去重后写入 `branchList`/`branchNameList`；admin 用户跳过旧版查询
- **`SysSubCenterService` 注入**: AbstractController 新增 `@Autowired private SysSubCenterService sysSubCenterService`

#### 新增 Controller: 服务商省份授权
- **`LightSpServiceProvinceController`** (新增文件, 220行): 服务商省份授权管理
  - 路由前缀: `/light/lightSpServiceProvince/`
  - 功能: 服务商可授权经营省份的增删查改 + 导出
  - DTO: `LightSpServiceProvinceQueryRequest`, `LightSpServiceProvinceExportExcel`, `LightSpRegionExportExcel`
  - 模板: `lightSpServiceProvinceList.ftl` (472行)

#### 已适配新分中心的 Controller 列表
以下 Controller 均已从旧版 `putSubCenter` (SysPartyService) 迁移到新版分中心查询：
- `LightStationController` — 电站列表新增 citySubCenters.do 接口
- `LightStationInfoUpdateController` — 基本信息列表分中心查询
- `LightConfirmOrderController` — 订单确认分中心逻辑
- `LightMakeOrderController` — 下单分中心逻辑
- `LightFreezeSettleController` — 冻结结算分中心查询
- `LightSpController` — EPC服务商分中心筛选
- `LightSpOrderCenterController` — 服务商订单中心
- `LightSpGridAwardOrderDetailController` — 网格奖励订单
- `LightTransferSpApplyController` — 服务商调拨申请
- `LightSpStoreController` — 二级库房
- `ReviewMaterialController` — 审核材料导出
- `LightElectricUnusualController` — 发电异常列表
- `LightStationYuexiuController` — 越秀电站管理 (2026-06-06 适配)
- `LightStopStationController` — 电站终止管理 (2026-06-06 适配)
- `LightProjectElectricOrderController` — 电费收益 (2026-06-06 多次回退/调整分页)

#### 2026-06-06 当天变更
- **电费收益分中心回退**: `LightProjectElectricOrderController` 多次 revert + 导出分页大小调整 (commits 078ef9e/9fd53b0/15141ea)
- **越秀管理/终止管理适配新分中心**: `LightStationYuexiuController` + `LightStopStationController` (commits b4e93b2/2a35dfd)
- **证据等级**: 代码明确证明

#### 2026-06-07 后续查漏补缺 (regionUnlimit 合入后修复)
**来源**: `rrsjk-admin-web` (commits: 3e80678/08e8240, yumiao, 2026-06-07)
- **`DispatchWorkOrderController`**: 派工单导出接口从内联 SysPartyService 查询改为 `super.putSubCenterNew(params, httpServletRequest)`
- **`LightSpController`**: `branchSpList.do` (分中心服务商列表) 从内联 SysPartyService 查询改为 `super.putSubCenterNew(params, request)`
- **`lightStationNannyUserController`**: `doList.do` + `doExport.do` (绿能站长屋顶推荐) 从 `this.getSubCenterCodeList(request)` 改为 `super.getSubCenterCodesNewVersion(request)`
- **证据等级**: 代码明确证明

---

## CBS 招投标管理 (TAEI-3102, 2026-05-20~22 代码明确证明)

**来源**: `cbs-web` + `rrsjk-light-service` + `rrsjk-admin-web` (commits: laowang 18个, 分支 `20260520-wjh-toubiaogl`)
**关联需求**: TAEI-3102 【户用光伏】CBS招投标流程
**参与人**: 刘艺(assigned), 魏秋阳, 薛荣基, 王金浩

### 功能概述
CBS 管理后台新增招投标管理模块，支持招标项目的全流程管理：
- 招标项目新增、编辑、查询
- 多阶段上传和审核（各阶段有独立的上传人、审核人、状态）
- 当前阶段标识（待提交、进行中、已完成等）
- 审核功能（通过/驳回，带日志关联）

### Controller 路由 (cbs-web)
| 路由 | 方法 | 功能 |
|---|---|---|
| 招投标新增接口 | POST | 创建招标项目 |
| 招投标编辑接口 | POST | 编辑招标项目(多阶段表单) |
| 招投标详情接口 | GET | 查看招标项目详情 |
| 招投标审核接口 | POST | 审核招标项目阶段 |

### 数据模型 (rrsjk-light-service)
- **招标管理当前阶段标识字段**: 标识当前处于哪个阶段
- **审核下一阶段标志字段及枚举**: 控制审核流程的状态流转
- **各阶段上传人和审核人字段**: 记录每个阶段的操作人
- **电站地区信息字段**: 关联招标项目所属地区
- **零碳能源代理商请求地区字段**: 零碳相关扩展

### 前端页面 (rrsjk-admin-web)
- 招标管理列表页面
- 多阶段编辑表单（支持各阶段独立编辑）
- 审核弹窗（阶段按钮及文件上传交互）
- 详情页面样式

### 业务规则
- 多阶段审核流程，每个阶段独立提交和审核
- 审核时需关联日志记录（修复了日志关联错误ID的问题）
- 支持地区字段扩展（零碳能源代理商请求地区）

### 最新迭代更新 (2026-05-25~29, 代码明确证明)
**来源**: `rrsjk-light-service` + `rrsjk-admin-web` (laowang/王金浩, branch: origin/20260515-wjh-toubiaogl + origin/20260520-wjh-toubiaogl)
- **价值链审核回传材料** (commit 402f51f0): 新增 `vcatmAuditDetail` 字段，支持存储和展示审核回传材料；修复上传材料时错误写入审核状态字段的Bug；修复MyBatis动态更新SQL中缺少逗号的问题
- **审核备注字段** (commit 688bdff6): 招投标审核各阶段新增审核备注字段（4 files, 107行新增）
- **待提交状态修复** (commit 87219c04): 修复WAIT状态误生成审核日志的Bug，审核同意后将当前阶段状态重置为WAIT
- **文件URL与名称合并** (commit 62a68ee6): `refactor(tender)`: 合并文件URL与名称为组合字段存储
- **前端弹窗修复** (rrsjk-admin-web, 15+ commits): 修复弹窗高度溢出、滚动策略、尺寸自适应、编辑按钮显示等问题
- **放开销方校验** (commit 75cbe636/1b0dbb30): 放开销方校验支持历史项目名称（dev分支 + fdss分支）

### 大文件分片上传支持 (代码明确证明, 2026-06-02)
**来源**: `rrsjk-admin-web` → `OssImageController.java` (commits 1365d99/58f7049/eeabb9e, laowang, 2026-06-01~02)

- **新增 4 个分片上传端点** (为招投标管理的大文件PDF上传提供支持):
  - `POST /oss/image/initiateMultipartUpload.do` — 初始化分片上传，返回 uploadId + objectKey + imageUrl
  - `POST /oss/image/uploadPart.do` — 上传单个分片 (uploadId, objectKey, partNumber, file)
  - `POST /oss/image/completeMultipartUpload.do` — 完成分片上传（合并分片，partETags 格式 "1:eTag1,2:eTag2"）
  - `POST /oss/image/abortMultipartUpload.do` — 取消分片上传（关闭弹窗时自动中断）
- **新增接口**: `POST /oss/image/uploadFileMime.do` — 支持 docx 等特殊 MIME 类型的文件上传（@RequestParam 直接绑定）
- **前端配套**: 支持取消分片上传并在关闭弹窗时自动中断、大文件PDF分片上传、docx专用上传接口

### 零碳世家 → 零碳适家重命名 (代码明确证明, 2026-06-02)
**来源**: `rrsjk-admin-web` → `TenderManagementController.java`, `tenderManagement.ftl` (commits 65b13b1/29e6bea, laowang, 2026-06-02)

- 招投标管理中"零碳世家"重命名为"零碳适家"
- 增加当前步骤筛选功能
- **影响**: `TenderManagmentAudit.projectCategory` 枚举值 LTSJ 的业务含义应理解为"零碳适家"（原"零碳世家"）

**证据等级**: 代码明确证明

### TAEI-3102 招投标管理最新迭代 (2026-06-01~02, 代码明确证明)
**来源**: `rrsjk-light-service` (laowang/王金浩, branch: origin/20260529-wjh-dev)
- **项目名称重复校验 2.0** (commit 7db6bf5b): `TenderManagmentAuditServiceImpl` 优化重复校验逻辑
- **修复审核状态及日志记录** (commit 9fd1d414): 修复招投标审核状态及日志记录逻辑
- **业务规则**: 招标项目名称不能重复，审核流程需记录完整的操作日志
- **证据等级**: 代码明确证明

---

## CBS 领用/成本记账时间字段 (代码明确证明, 2026-04-22)
**来源**: `rrsjk-light-service` → 安装费相关实体及DAO (commit 10aa90c956, 龙龙, 2026-04-14~22, TAEI-3035 CBS界面展示：安装及并网、营销、超期考核和新商 增加领用、成本记账时间展示)

### 新增字段
- `voucherAt` — 领用时间 (领用凭证时间)
- `costVoucherAt` — 成本记账时间
- **填充逻辑**: 所有填充点都已添加自动回填时间
- **前端展示**: CBS安装及并网、营销、超期考核和新商列表页和Excel导出新增这两列

---

## system-service — CBS 基础系统服务 (2026-06-03 全量通读新增)

**来源**: `system-service` → `system-impl/src/main/java/com/haier/cbs/system/` (代码明确证明)
**仓库**: `/data/pvcode/system-service`
**分支**: master | HEAD: 3777c3bef8f9

> **服务定位**: CBS 系统最基础的系统管理服务，提供用户、角色、菜单、权限、访问日志、消息、团体/组织架构等基础能力。被多个上层服务通过 Dubbo 引用。

### 技术栈
- Spring + Dubbo + MyBatis + Jedis (Redis)
- 双数据源: `dsSystem` (系统库) + `shopSystem` (Shop库)
- Zookeeper 注册中心 (dev: 10.2.192.154:2181, prod: 10.2.160.242-244:2181)

### 核心 Dubbo 服务接口

| Dubbo Service | 说明 |
|---|---|
| `SystemService` | 用户/角色/菜单/权限/会话管理 |
| `SysPartyService` | 团体/组织架构管理 |
| `V3BranchRegionService` | V3 分中心-区域映射 |

### SystemService — 用户/角色/菜单/权限

**来源**: `SystemModel.java`, `SystemServiceImpl.java`

#### 用户管理
- `findUser(name, loginId, status, pager)` — 分页查询用户
- `getUser(userId)` — 获取用户详情
- `createUser(user, optUserId)` — 创建用户 (密码使用 Guava Hashing.murmur3_128 加密)
- `updateUser(user, optUserId)` — 更新用户
- `getByLoginId(loginId)` — 根据登录ID查询
- `updatePasswordByUserId(userId, newPassword)` — 修改密码

#### 角色管理
- `findRole(name, status, pager)` — 分页查询角色
- `assignUserRole(userId, roleIds)` — 给用户分配角色
- `unassignUserRole(userId, roleId)` — 取消用户角色
- `findUserRoleAssigned(userId)` — 用户已分配角色
- `findUserRoleUnAssigned(userId)` — 用户未分配角色

#### 菜单权限
- `loadUserMenu(userId)` — 加载用户有权限的菜单（用户直接权限 + 角色权限合并）
- `loadUserAllResMenu(userId)` — 加载用户所有资源菜单（不限制类型）
- `loadUserHdsResMenu(userId)` — 加载 HDS 系统专属菜单
- `findAllMenuTree()` — 获取所有菜单树状结构
- 菜单类型: `mdl`(模块), `app`(应用), `url`(链接), `button`(按钮)
- 权限所有者类型: `OWNER_USER`(用户), `OWNER_ROLE`(角色)
- 权限资源类型: `RESOURCE_MENU`(菜单)

#### 菜单渲染架构变更 (2026-06-13 增量扫描发现)
- **变更**: `MenuController.menus()` 从固定二级菜单升级为**递归 N 级菜单**
- **旧逻辑**: 仅遍历 module → children (type=url)，最多二级
- **新逻辑**: 新增 `buildMenuDataChildren(List<SysMenu>)` 递归方法，支持任意深度嵌套
- **新增菜单类型**: `isFolder=YES` — 文件夹节点，可包含子菜单，图标使用 `icon-chart_bar`
- **过滤条件变更**: 原仅处理 `menuItemtype=url`，现同时处理 `isFolder=YES` 的 mdl 类型节点
- **HDS 菜单排除**: `hdsMenuIdList()` 获取 HDS 一级菜单 ID 列表，这些菜单在 HDS 系统独立展示，不在 CBS 主菜单中渲染
- **来源**: `cbs-web/MenuController.java` (commit c0f332b2, mabin, 2025-07-08; 代码明确证明)

#### 访问日志
- `AccessLogDao.create(accessLog)` — 记录访问日志
- `find(startTime, endTime, clientIp, visitUrl, userName, sessionId)` — 查询访问日志

#### 会话管理
- `SysSessionDao` — 会话 CRUD，存储 sessionId → userId 映射

### SysPartyService — 团体/组织架构

**来源**: `SysPartyModel.java`, `SysPartyServiceImpl.java`

#### 团体类型 (SysParty.PartyType)
- `DEPARTMENT` — 部门
- `TEAM` — 团队
- `PERSONAL` — 个人
- `TRADE` — 工贸
- `AREA` — 区域

#### 核心功能
- `insertPartyUser(partyUserList)` — 添加团体成员 (同时清除 Redis 缓存)
- `updatePartyUser(partyUser)` — 更新团体成员
- `findPartyUserByPager(params, pager)` — 分页查询团体成员
- `getPartyUserByUserId(userId)` — 查询用户所属团体
- `getUserPartyAuthority(userId)` — 获取用户团体权限维度详情 (优先读 Redis)
- `updateParentInfo(idList, parentId, updatedBy)` — 更新团体的上级信息

#### Redis 缓存 (Dispenser 水站相关)
**来源**: `RedisDao.java`
- `setDispenserUserParty(userId, value)` — 设置用户团体缓存
- `getDispenserUserParty(userId)` — 获取用户团体缓存
- `setDispenserAuthorityUser(userId, partyId, value)` — 设置团体下成员缓存
- `delDispenserUserParty(userId)` — 删除用户团体缓存 (团体成员变更时触发)
- Key 生成规则: `KeyUtils.dispenserPartyKey(userId)`, `KeyUtils.setDispenserAuthorityUser(userId, partyId)`

### V3BranchRegionService — 分中心-区域映射

**来源**: `V3BranchRegionModel.java`, `V3BranchRegionServiceImpl.java`
- `getByRegionId(provinceId, cityId, regionId)` — 根据区域ID查询分中心映射
- `getRegionByBranchCode(branchCode)` — 根据分中心编码查询区域
- `getRegionByRegionList(regionList)` — 批量查询
- `getByRegionCode(regionCode)` — 根据区域编码查询
- 数据来自 Shop 库 (非 System 库)

### 数据库表 (System 库)

| 表名 | 说明 | Mapper |
|---|---|---|
| `sys_user` | 用户表 | SysUserMapper.xml |
| `sys_role` | 角色表 | SysRoleMapper.xml |
| `sys_menu` | 菜单表 | SysMenuMapper.xml |
| `sys_action` | 操作/功能表 | SysActionMapper.xml |
| `sys_permission` | 权限表 | SysPermissionMapper.xml |
| `sys_session` | 会话表 | SysSessionMapper.xml |
| `sys_access_log` | 访问日志表 | SysAccessLogMapper.xml |
| `sys_party` | 团体表 | SysPartyMapper.xml |
| `sys_party_user` | 团体-用户关联表 | SysPartyUserMapper.xml |
| `sys_party_relevance` | 团体-对象关联表 | SysPartyRelevanceMapper.xml |
| `sys_message` | 消息表 | SysMessageMapper.xml |
| `sys_message_permission` | 消息权限表 | SysMessagePermissionMapper.xml |

### 数据库表 (Shop 库)

| 表名 | 说明 | Mapper |
|---|---|---|
| `v3_branch_region` | V3分中心-区域映射 | V3BranchRegionMapper.xml |
| `Regions` | 地区表 | RegionsMapper.xml |

---

## cbs-web 遗留水站/饮水机业务模块 (代码明确证明, 2026-06-10 全量通读)

**来源**: `cbs-web` → `src/main/java/com/haier/cbs/web/controller/dispenser/`
**证据等级**: 代码明确证明
**⚠️ 与光伏业务无关**: 这些是 CBS 系统承载的海尔净水器/水站(Dispenser)业务模块，属于历史遗留业务线。PVS 光伏系统与之共享同一套 CBS 基础设施，但业务逻辑完全独立。

### Controller 路由汇总

| Controller | 路由前缀 | 业务功能 | 依赖 Service |
|---|---|---|---|
| `BackCategoryChangeController` | `/categoryAdd`, `/categoryDel`, `/categoryUpdate` | 后台类目迁移管理 | `BackCategoryService` |
| `BusinessApplyController` | `/businessApplyList`, `/auditBusinessApply`, `/uploadZip` | 专业客户业务申请审核 | `BusinessApplyService`, `PortalBusinessAuditorService` |
| `CheckInventoryController` | `/checkInventoryList`, `/exportCheckInventory` | 水站盘点记录查询+导出 | `CheckInventoryService` |
| `CleanServerOrderManagementController` | `/cleanServerOrderList`, `/exportCleanOrder` | 清洗服务订单管理+导出 | `CleanOrderService` |
| `CxwCleanOrderManagementController` | `/cxwCleanOrderList`, `/exportCxwCleanOrder` | 车小微家电清洗订单管理 | `CxwCleanOrderService` |
| `FetchRecordController` | `/fetchRecordList` | 打水记录管理 | `WaterFetchRecordService` |
| `FilterChangeController` | 滤芯更换管理 | 滤芯更换记录 | - |
| `FlowableConfigController` | 审核流程配置 | Flowable 流程引擎配置 | - |
| `FlowableUserConfigController` | 审核人员配置 | Flowable 用户配置 | - |
| `HaierRecruitApplyController` | 海尔招聘申请 | 招聘流程管理 | - |
| `HaierRecruitProcessController` | 海尔招聘流程 | 招聘流程处理 | - |
| `HpOrderInfoController` | HP 订单信息 | HP 系统订单管理 | - |
| `JointVentureOrderController` | 合资公司下单 | 合资公司订单管理 | - |
| `LnAppRegisterReportController` | 乐农APP注册报表 | 注册数据统计 | - |
| `LnEhrKpiController` | 乐农EHR KPI | 绩效考核 | - |
| `LnKpiImportController` | KPI 导入 | KPI 数据批量导入 | - |
| `LnKpiSourceController` | KPI 数据源 | KPI 来源管理 | - |
| `OperatorRealNameController` | 运营商实名认证 | 操作员实名校验 | - |
| `PointsExchangeProductController` | 积分兑换商品 | 积分商城兑换 | - |
| `ProcessDispenserIssueController` | 水站问题处理 | 水站问题工单 | - |
| `ProductShareRebateController` | 产品分享返利 | 分享推广返利 | - |
| `ReportImportController` | 报表导入 | 报表数据导入 | - |
| `RiceFieldDynamicManageController` | 稻田动态管理 | 稻田认筹动态 | - |
| `RiceFieldRecognizeManageController` | 稻田认筹管理 | 稻田认筹审核 | - |

### 关键业务逻辑

**BusinessApplyController — 专业客户审核**:
- 审核通过: `status=3` → `businessApplyService.auditPassAndContract()` (记录审核人、合同起止日期、合同URL)
- 审核驳回: `status=-3` → `businessApplyService.auditReject()`
- 权限校验: 查询 `PortalBusinessAuditorService.getByUserId()` 判断用户是否有审核权限
- 合同附件: 支持 ZIP 上传到 MongoDB (`MongoUtils.save()`)

**CleanServerOrderManagementController — 清洗服务订单**:
- 支持超时未接单查询 (`overTimeStatus` + 当前时间对比)
- 综合评价维度: 服务态度/服务速度/服务质量
- 确认方式: 服务确认方式枚举
- 支持 Excel 导出 (jxl 库)

**Kuaidi100Controller — 快递100回调**:
- 路由: `POST /kuaidi100.do`
- 处理快递签收状态 (`state=3` → `orderOperationService.acceptExpressStatus()`)
- 同步滤芯兑换单物流状态 (`filterExchangeKeyService.expressStatusHandle()`)
- 快递异常处理 (`status=abort` → `ExpressAbortService`)

**OrderCancelController — 订单取消退款**:
- `/cancelOrder` — 单个网单取消退款 (`orderService.cancelOrderProductAndRefund(opid)`)
- `/cancelWholeOrder` — 整单取消退款 (`orderService.cancelWholeOrderAndRefund(oid)`)
- `/pushRepairOrder` — 已签收订单下发退货单到 VOM (`orderService.cancelSignedOrderToVOM(opid)`)
- ⚠️ 签名校验 (`checkValidSign`) 已注释掉，生产可能存在未鉴权访问风险

### Dubbo 依赖 (cbs-web pom.xml)

| 依赖 | 说明 |
|---|---|
| `system-service` | CBS 用户/角色/菜单/权限/团体 |
| `order-service` | 订单服务 |
| `base-service` | EAI 基础服务 (发票/LES/HP/MDM) |
| `rrs-dispenser-api` | 水站业务 API |
| `rrsjk-system-api` | 新能源系统 API |
| `rrsjk-cms-api` | CMS API |
| `rrsjk-flowable-api` | Flowable 流程引擎 API |
| `shoppingmall-*` | 商城系列服务 (order/member/item/core) |
| `stock-service` | 库存服务 |
| `job-service` | 定时任务服务 |
| `item-service` | 商品服务 |
| `kuaidi100-sdk` | 快递100 SDK |

---

## TAEI-3186 方案审核/完工审核新增一级商审 (代码明确证明, 2026-06-09)
**来源**: `rrsjk-light-service` (解钦, branch: xq-feature-service-provider-confirm-plan)
- **负责人**: 徐晓凤 | **实际开发**: 解钦 | **参与人**: 薛荣基, 袁睿林
- **状态**: 开发中
- **业务背景**: 在方案审核和完工审核流程中新增一级商审节点
- **证据等级**: 代码明确证明

## 仓储相关变更 (2026-06-05~12)
### TAEI-3129 商户通入库导出物流信息
- **开发者**: 王希然 | **状态**: 待测试
- 商户通入库管理导出时增加物流信息字段

### TAEI-3082 调拨入库展示仓库名称
- **开发者**: 王希然 | **状态**: 待测试
- 调拨入库列表新增仓库名称展示
- `feat(order): 添加采购订单和调拨订单的仓库及团队信息功能`

### TAEI-3191 公建租金付款流程
- **开发者**: 薛荣基, 马斌 | **状态**: 待评审
- 仅做流程不记账和传云报账

## 商户通用户信息 — 子中心分组扩展 (代码明确证明, 2026-06-15)
**来源**: `rrsjk-merchant-web` → `MerchantUserInfoController.java` (commit fd75e95c, wangxiran/王希然, 2026-06-13, 分支 origin/hotfix-wxr-20260613)

### 变更内容
商户通用户信息控制器中的子中心分组硬编码列表扩展：

**SUB_CENTER1** (新增 2 个):
- 原有: 上海,成都,南宁,广州,长沙,南昌,福州,武汉,海口,襄樊,昆明,厦门,贵阳,重庆,无锡,深圳,西宁,广州
- 新增: **福州**, **江苏II(苏南)**

**SUB_CENTER2** (新增 10 个):
- 原有: 青岛,济宁,济南,徐州,石家庄,烟台,郑州,天津,合肥,太原,西安,南京,沈阳,北京,内蒙,宁波,唐山,兰州,银川,杭州,河北
- 新增: **山东II**, **山东I**, **江苏I(苏北)**, **合肥II(皖南)**, **江苏II(苏南)**, **辽宁**, **蒙西**, **杭州上海**, **杭州&上海**

### 业务含义
- 商户通用户信息接口 (`/getMemberId`) 根据子中心名称将用户分配到不同分组
- 新增的子中心反映了组织架构调整：山东/江苏/合肥/辽宁/蒙西等地区拆分出更细粒度的子中心
- **注意**: 这是硬编码常量，新增子中心需要修改代码重新发版

### 区域业务报表恢复
**来源**: `rrsjk-merchant-web` → `RegionBusinessReportController.java` (commits 1f606ee3/d4da9718, yumiao/王金浩, 2026-06-13)
- 整个 Controller 从全注释状态恢复为活跃代码（953行取消注释）
- 区域业务报表功能重新上线

## HDS 审核状态报表 — 分中心数据源迁移 (2026-06-22, 代码明确证明)

**来源**: `rrsjk-hds-web` → `EnergyAuditStatusReportController.java` (commit dda2b48b, yumiao, 2026-06-22)

### 变更内容
`/report/auditStatus/findParty` 接口的分中心数据源从报表库迁移到 CBS 系统库：
- **变更前**: `energyAuditStatusReportService.findParty(likeName)` — 从报表库查询
- **变更后**: `sysSubCenterService.findByPager(criteria)` / `sysSubCenterService.findAll()` — 从 CBS system-service 查询
- **新增**: `toSysPartyList(List<SysSubCenter>)` 转换方法，将 `SysSubCenter` 适配为前端已有的 `SysParty` 结构
- **业务意义**: 分中心主数据统一从 CBS 系统库获取，避免报表库分中心数据不同步
