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

---

## CBS 领用/成本记账时间字段 (代码明确证明, 2026-04-22)
**来源**: `rrsjk-light-service` → 安装费相关实体及DAO (commit 10aa90c956, 龙龙, 2026-04-14~22, TAEI-3035 CBS界面展示：安装及并网、营销、超期考核和新商 增加领用、成本记账时间展示)

### 新增字段
- `voucherAt` — 领用时间 (领用凭证时间)
- `costVoucherAt` — 成本记账时间
- **填充逻辑**: 所有填充点都已添加自动回填时间
- **前端展示**: CBS安装及并网、营销、超期考核和新商列表页和Excel导出新增这两列
