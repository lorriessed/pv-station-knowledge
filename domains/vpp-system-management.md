# VPP 系统管理模块

最后更新: 2026-05-14

## 1. 服务概述

**来源**: `vpp-api-system` (全量通读 ✅ 2026-05-14)

VPP 系统的核心基础服务，提供用户管理、部门管理、角色权限(RBAC)、菜单路由、租户管理、字典配置、国际化、OSS文件存储、SSO单点登录等系统级功能。是整个 VPP 平台的基础设施层。

### 1.1 技术栈 (重大升级)

- **Spring Boot 3.2.2 + JDK 17 + Jakarta EE 10** (与旧版 JDK 8 的 VPP 服务不同)
- Spring Cloud 2023.0.0 + Spring Cloud Alibaba 2023.0.1.0
- MyBatis-Plus + mybatis-plus-join (MPJ) + JSqlParser 4.4
- MapStruct 1.6.2 + Manifold (编译期增强)
- Nacos 多环境 + 新加坡(prod-sgp) 环境
- XXL-JOB 2.4.2
- Haier IAM Auth SDK 1.1.7 (海尔统一认证)
- Jasypt 加密
- OpenAPI 3 (springdoc, 非 Swagger2)

## 2. 核心业务模块

### 2.1 用户管理 (代码明确证明)

**来源**: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/sys/SysUserController.java`

- 用户 CRUD、分页查询
- Excel 导入/导出用户数据
- 修改密码
- 切换租户
- 用户头像上传 (通过 OSS)

### 2.2 部门管理 (代码明确证明)

**来源**: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/sys/SysDeptController.java`

- 部门树形结构 (ancestors 字段)
- 部门新增/修改/删除 (有下级或有用户时不允许删除)
- 部门禁用检查 (有未停用子部门或已分配用户时不允许)
- 国家列表 (内置 200+ 国家枚举)
- 当前用户的部门树

### 2.3 角色管理 (代码明确证明)

**来源**: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/sys/SysRoleController.java`

- 角色 CRUD
- 角色数据权限 (全部/自定义/本部门/本部门及以下/仅本人)
- 用户-角色授权 (批量分配/取消)
- 角色-部门权限绑定
- 修改角色时清理在线用户缓存

### 2.4 菜单管理 (代码明确证明)

**来源**: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/sys/SysMenuController.java`

- 菜单树形结构
- 获取当前用户路由 (`/getRouters`)
- 获取无门户路由 (`/getNoPortalRouters`)
- 获取指定门户路由 (`/getPortalRouters`)
- 按钮权限管理
- 用户权限集合 (`/getPermsByUserId`)

### 2.5 租户管理 (代码明确证明)

**来源**: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/sys/SysTenantController.java`

- 多租户架构 (AbstractTenantDO)
- 租户 CRUD
- 当前用户可见的租户列表
- 当前用户的当前租户切换

### 2.6 Token/认证管理 (代码明确证明)

**来源**: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/TokenController.java`

| 路径 | 方法 | 说明 |
|---|---|---|
| /getVppToken | POST | 获取VPP Token (Drcloud对接) |
| /token-login | POST | 用户登录 (密码/IDM) |
| /token-nonce-login | POST | 带秘钥登录 |
| /token-nonce-init | POST | 获取登录秘钥 |
| /SSO-login | POST | 统一登录 |
| /boundUser | POST | 三方平台绑定用户 |
| /getIdmTokenAndUserInfo | GET | 授权码换IDM Token和用户信息 |
| /getIdmToken | GET | 授权码换IDM Token |
| /getTokenByIdmToken | POST | IDM Token 换 VPP Token |
| /logout | DELETE | 用户登出 |
| /refresh | POST | 刷新Token |
| /getLoginUser | POST | 获取登录信息 |
| /findUserByUserTenantId | POST | 根据用户与租户id关联查询 |

### 2.7 SSO 单点登录 v1 (代码明确证明)

**来源**: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/sso/v1/SSOController.java`

| 路径 | 方法 | 说明 |
|---|---|---|
| /SSO/v1/verify | POST | 外部系统验证token有效性 |
| /SSO/v1/findTokenUser | POST | 外部系统通过token获取用户信息 |

### 2.8 国际化 (i18n) (代码明确证明)

**来源**: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/i18n/`

- 国际化资源 CRUD (key-value, 多语言)
- 按语言查询所有资源
- 按标签过滤资源
- 批量导入/导出 (Excel)
- 缓存刷新
- 前端专用接口 (返回 JSONObject 格式)

### 2.9 配置管理 (代码明确证明)

**来源**: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/sys/SysConfigController.java`

- 系统参数配置 (全局默认 + 租户配置)
- 按 key 查询配置值
- 导出配置
- 刷新配置缓存
- Feign 远程调用: `RemoteConfigService.getConfigKey()`

### 2.10 字典管理 (代码明确证明)

**来源**: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/sys/SysDictTypeController.java`, `SysDictDataController.java`

- 字典类型 CRUD
- 字典数据 CRUD
- 按字典类型查询字典数据
- 国际化字典 (带翻译的字典值)
- 删除字典缓存

### 2.11 OSS 文件存储 (代码明确证明)

**来源**: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/oss/OssController.java`

- 上传文件 (MultipartFile)
- 根据 URL 上传文件
- 获取上传签名 (Policy签名, 用于前端直传)
- 阿里云 OSS 集成

### 2.12 区域管理 (代码明确证明)

**来源**: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/sys/SysRegionController.java`

- 区域树形结构 (省-市-区)
- 查询所有省份
- 按父级ID查询下级区域

### 2.13 门户管理 (代码明确证明)

**来源**: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/sys/SysPortalController.java`

- 门户 CRUD
- 当前用户有权限的门户列表
- 根据路由路径获取对应门户

### 2.14 外部系统管理 (代码明确证明)

**来源**: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/controller/sys/SysOutSystemController.java`

- 外部系统申请
- 外部系统审核 (管理员权限)
- 分页查询

### 2.15 其他

| 模块 | 路径 | 说明 |
|---|---|---|
| Jasypt加密 | /jasypt/encrypt | 加密字符串 |
| Jasypt解密 | /jasypt/decrypt | 解密字符串 |
| 邮件验证码 | /sendEmailCode | 发送邮箱验证码 |

## 3. Feign 远程服务调用 (代码明确证明)

**来源**: `vpp-api-system/vpp-system-api/src/main/java/com/nahui/energy/fegin/`

| Service | 路径 | 说明 |
|---|---|---|
| RemoteConfigService | /system/config/configKey/{key} | 查询系统配置 |
| RemoteI18nService | /i18nMessage/getAllMessageSource | 获取国际化资源 |
| RemoteOssService | /system/oss/upload | 文件上传 |
| RemoteRegionService | /system/region/* | 区域查询 |
| RemoteTokenService | /system/token/findUserByUserTenantId | 查询用户信息 |
| ConfigUtil | - | 配置工具类 (通过Feign远程获取配置) |

## 4. 数据库表 (代码明确证明)

### 4.1 系统基础表

| 表名 | 对应DTO | 说明 |
|---|---|---|
| sys_user | UserDTO | 用户表 |
| sys_dept | DeptDTO | 部门表 (ancestors 字段存祖级列表) |
| sys_role | RoleDTO | 角色表 |
| sys_menu | MenuDTO | 菜单权限表 |
| sys_post | PostDTO | 岗位信息表 |
| sys_tenant | TenantDTO | 租户信息表 |
| sys_user_tenant | UserTenantDTO | 用户租户关联 |
| sys_user_role | UserRoleDTO | 用户角色关联 |
| sys_role_menu | - | 角色菜单关联 |
| sys_role_dept | - | 角色部门关联 |
| sys_user_post | - | 用户岗位关联 |
| sys_dict_data | DictDataDTO | 字典数据表 |
| sys_dict_type | DictTypeDTO | 字典类型表 |
| sys_config | ConfigDTO | 参数配置表 |
| sys_region | RegionDTO | 区域表 (省市区) |
| sys_portal | SysPortalDTO | 门户表 |
| sys_out_system | SysOutSystemDTO | 外部系统表 |

### 4.2 国际化表

| 表名 | 对应DTO | 说明 |
|---|---|---|
| sys_i18n_resource | SysI18nResourceDTO | 国际化资源表 |
| sys_i18n_tag_link | SysI18nTagLinkDTO | 国际化资源-标签关联表 |
| sys_language | SysLanguageDTO | 支持的语言表 |

### 4.3 OSS 配置表

| 表名 | 对应DTO | 说明 |
|---|---|---|
| sys_oss_config | OssConfigDTO | OSS配置表 |

## 5. 枚举定义 (代码明确证明)

**来源**: `vpp-api-system/vpp-system-biz/src/main/java/com/nahui/energy/enums/`

| 枚举 | 值 | 说明 |
|---|---|---|
| BoundTypeEnum | - | 绑定类型 |
| GrantTypeEnum | USER_PASSWORD, HAIER_TOKEN | 授权类型 (密码登录/海尔IDM Token) |
| LanguageStatusEnum | - | 语言状态 |

**继承自 vpp-api-common**: DelFlagEnum, BooleanTypeEnum, DataScopeEnum, UserTypeEnum 等

## 6. 关键架构发现

### 6.1 JDK 17 升级 (代码明确证明)

**来源**: `vpp-api-system/pom.xml`

- vpp-api-system 已升级到 Spring Boot 3.2.2 + JDK 17 + Jakarta EE 10
- 使用 `jakarta.servlet`, `jakarta.validation` (非 javax)
- 使用 springdoc-openapi (OpenAPI 3) 替代 Swagger2
- MyBatis-Plus 配置中增加了 JDK 17 反射兼容配置
- 使用 Manifold 编译期增强

### 6.2 多环境 Nacos 配置

| 环境 | Nacos地址 | Namespace |
|---|---|---|
| local | 10.162.105.9:8848 | 266fa059-8199-4072-8ae4-821bcb7f8048 |
| dev | 10.162.105.9:8848 | 49256502-3dd8-44aa-822d-bdffcd00b018 |
| test | 10.162.105.9:8848 | 8bc7450c-8948-47a7-b3da-f1c718b275b8 |
| prod | nlb-sfypp5bxa7wquowavs.cn-qingdao.nlb.aliyuncsslb.com:8848 | 6e1ce568-517d-4816-9d1a-8d2861c8cbd9 |
| prod-sgp | nlb-a94k3st1cvni6eeu9c.ap-southeast-1.nlb.aliyuncsslbintl.com:8848 | vpp-sgp |

### 6.3 登录流程

1. 密码登录: `/token/token-login` (grantType=USER_PASSWORD)
2. 海尔IDM登录: `/token/token-login` (grantType=HAIER_TOKEN)
3. 授权码登录: 先 `/getIdmTokenAndUserInfo?code=xxx` 换取IDM Token, 再 `/getTokenByIdmToken?idmToken=xxx` 换取VPP Token
4. 秘钥登录: `/token-nonce-init` 获取秘钥 → `/token-nonce-login` 登录
5. SSO登录: `/SSO-login`
6. 三方绑定: `/boundUser`

## 7. 知识库更新记录

| 日期 | 更新内容 | 来源 |
|---|---|---|
| 2026-05-14 | 创建 VPP 系统管理完整文档 | vpp-api-system 全量通读 |
