# VPP 知识管理模块

最后更新: 2026-05-14

## 1. 服务概述

**来源**: `vpp-api-km` (全量通读 ✅ 2026-05-14)

知识库管理模块，提供知识文档的目录管理、文件上传、标签打标、权限控制、操作日志等功能。采用树形目录结构组织知识内容，支持用户级别的目录访问权限控制。

### 1.1 技术栈

- Spring Boot 2.5.5 + JDK 8 + Spring Cloud 2020.0.4
- MyBatis-Plus 3.5.3.1 + Druid 1.2.23
- Nacos 配置中心
- Redis 缓存 (Lettuce RESP2, FastJson2序列化)
- Apache POI (Excel 导入导出)

## 2. 核心业务流程

### 2.1 目录树结构 (代码明确证明)

**来源**: `vpp-api-km/vpp-biz/src/main/java/com/nahui/energy/service/impl/km/KnowledgeDirectoryServiceImpl.java`

- 知识库采用**树形目录结构**，通过 `parent_id` 字段构建父子关系
- 目录有 `publish_status` 发布状态控制
- 删除目录前检查：不能有下级目录、不能有挂载文件
- 同级目录下不允许有相同名称的目录

### 2.2 文件-目录关联 (代码明确证明)

**来源**: `vpp-api-km/vpp-biz/src/main/java/com/nahui/energy/service/impl/km/KnowledgeFileMappingServiceImpl.java`

- 文件通过 `knowledge_file_mapping` 表与目录关联 (多对多关系)
- 查询子目录和文件时，先查 mapping 表获取 fileId 列表，再查 knowledge_file 表
- 删除文件时同时删除所有 mapping 记录

### 2.3 权限控制 (代码明确证明)

**来源**: `vpp-api-km/vpp-biz/src/main/java/com/nahui/energy/service/impl/km/KnowledgeDirectoryServiceImpl.java`

- `knowledge_user` 表维护用户与知识库目录的关联关系
- `checked` 字段：1=选中(有权限), 0=未选中
- 查询目录时根据 userId 过滤，只能看到有权限的目录
- **超级管理员** (`superadmin`) 和 **产品经理** (`chan_pin_jing_li`) 角色拥有全部目录可见权限
- 普通用户需要通过 `KnowledgeUser` 表授权才能看到目录

### 2.4 文件操作流程

1. **上传文件**: 创建文件记录 + 创建目录映射关系 (事务)
2. **删除文件**: 删除文件记录 + 删除所有映射关系 (事务)
3. **打标**: 修改文件的 tag 字段 (逗号分隔)
4. **日志记录**: `knowledge_file_log` 记录所有操作 (增加/修改/删除/查看)

## 3. 数据库表 (代码明确证明)

**来源**: `vpp-api-km/vpp-biz/src/main/java/com/nahui/energy/pojo/Do/km/`

| 表名 | DO类 | 说明 |
|---|---|---|
| `knowledge_directory` | KnowledgeDirectoryDO | 知识库目录表 (树形结构) |
| `knowledge_file` | KnowledgeFileDO | 知识库文件表 |
| `knowledge_file_mapping` | KnowledgeFileMappingDO | 目录-文件关联表 (多对多) |
| `knowledge_file_log` | KnowledgeFileLogDO | 文件操作日志表 |
| `knowledge_user` | KnowledgeUserDO | 用户-知识库关联表 (权限控制) |

### 3.1 knowledge_directory 核心字段

| 字段 | 说明 |
|---|---|
| name | 知识库名称 |
| parent_id | 父目录ID |
| publish_status | 发布状态 |
| introduce | 介绍 |
| create_dept_name | 创建部门名称 |
| create_by_name | 创建者名称 |

### 3.2 knowledge_file 核心字段

| 字段 | 说明 |
|---|---|
| file_name | 文件名称 |
| path | 文件路径 |
| size | 文件大小 |
| type | 文件类型 |
| publish_status | 发布状态 |
| audit_staus | 审批状态 (注意拼写: audit_staus) |
| tag | 标签逗号隔开 |
| del_flag | 删除位 |

### 3.3 knowledge_user 核心字段

| 字段 | 说明 |
|---|---|
| user_id | 用户ID |
| km_id | 知识库ID |
| checked | 是否选中 1=选中; 0=未选中 |

## 4. Controller/API 路由 (代码明确证明)

**来源**: `vpp-api-km/vpp-biz/src/main/java/com/nahui/energy/controller/km/`

### 4.1 知识库目录 `/knowledgeDirectory`

| 路径 | 方法 | 说明 |
|---|---|---|
| /add | POST | 新增/修改知识库目录 |
| /remove | POST | 删除知识库目录 |
| /queryByPage | GET | 分页查询知识库目录 |
| /queryById | GET | 根据ID查询知识库目录 |
| /queryPathById | GET | 根据ID查询上级路径 |
| /querySubDirectoryAndFileById | GET | 查询子目录和对应文件 |
| /trees | GET | 获取知识库树列表 |
| /treeSelect | GET | 获取知识库下拉树列表 |

### 4.2 知识库文件 `/knowledgeFile`

| 路径 | 方法 | 说明 |
|---|---|---|
| /add | POST | 新增知识库文件 (+映射) |
| /remove | POST | 删除知识库文件 (+映射) |
| /queryByPage | GET | 分页查询知识库文件 |
| /queryById | GET | 根据ID查询知识库文件 |
| /edit | POST | 修改名称或打标 |

### 4.3 文件日志 `/knowledgeFileLog`

| 路径 | 方法 | 说明 |
|---|---|---|
| /queryByPage | GET | 分页查询文件日志 |
| /queryById | GET | 根据ID查询日志详情 |

### 4.4 目录-文件映射 `/knowledgeFileMapping`

| 路径 | 方法 | 说明 |
|---|---|---|
| /add | POST | 新增映射 |
| /remove | POST | 删除映射 |
| /queryByPage | GET | 分页查询映射 |
| /queryById | GET | 根据ID查询映射 |

### 4.5 用户权限 `/KnowledgeUser`

| 路径 | 方法 | 说明 |
|---|---|---|
| /add | POST | 新增用户-知识库关联 |
| /remove | POST | 删除关联 |
| /queryByPage | GET | 分页查询关联 |
| /queryById | GET | 根据ID查询关联 |
| /queryCheckedByUserId | GET | 根据用户ID查询选中的知识库 |
| /updateByUserId | POST | 更新用户知识库权限 (批量) |

## 5. 枚举定义 (代码明确证明)

**来源**: `vpp-api-km/vpp-biz/src/main/java/com/nahui/energy/enums/`

### 5.1 知识库角色

| 角色 | code | 说明 |
|---|---|---|
| 产品经理 | chan_pin_jing_li | 可查看知识目录 |
| 超级管理员 | superadmin | 所有权限 |

### 5.2 业务操作类型 (BusinessTypeEnum)

| 值 | 说明 |
|---|---|
| INSERT | 入库 |
| UPDATE | 修改 |
| DELETE | 删除 |
| QUERY | 查询 |
| IMPORT | 导入 |
| EXPORT | 导出 |

## 6. @FileLog 注解 (代码明确证明)

**来源**: `vpp-api-km/vpp-biz/src/main/java/com/nahui/energy/annotation/FileLog.java`

- 自定义日志注解，用于 Controller 方法
- 记录操作标题、业务类型
- 与 `knowledge_file_log` 表配合使用

## 7. 知识库更新记录

| 日期 | 更新内容 | 来源 |
|---|---|---|
| 2026-05-14 | 创建知识管理完整业务文档 | vpp-api-km 全量通读 |
