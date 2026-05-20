# CBS 管理后台

更新时间: 2026-05-20

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

## 待确认

- CBS 生产环境部署地址和端口
- CBS 与 PVS 核心服务(rrsjk-light-service等)的数据交互方式
- 分中心(`SysSubCenter`)与 PVS 分中心的关联关系
- `SysSubCenterService` 的完整接口定义和实现
