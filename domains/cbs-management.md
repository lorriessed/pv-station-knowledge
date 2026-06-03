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
| `SysSubCenterService` | `addSubCenterUser(subCenterId, users)` | 添加分中心人员 |
| `SysSubCenterService` | `removeSubCenterUser()` | 移除分中心人员 |
| `SysSubCenterService` | `editSubCenterUser()` | 编辑分中心人员 |
| `SysSubCenterService` | `searchSubCenterUser()` | 搜索分中心人员 |

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
