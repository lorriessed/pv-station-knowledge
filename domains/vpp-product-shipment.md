# VPP 产品与出货管理

最后更新: 2026-05-14

## 1. 服务概述

**来源**: `vpp-api-meta` (全量通读 ✅ 2026-05-14)

产品管理和出货管理模块，负责产品主数据维护、产品图片管理、出货日志记录及导入。属于 VPP 元数据基础服务。

### 1.1 技术栈

- Spring Boot 2.5.5 + JDK 8 + Spring Cloud 2020.0.4
- MyBatis-Plus 3.5.3.1 + Druid 1.2.23
- Nacos 配置中心 (多环境: local/dev/test/prd)
- Redis 缓存

## 2. 核心业务流程

### 2.1 产品管理 (代码明确证明)

**来源**: `vpp-api-meta/vpp-biz/src/main/java/com/nahui/energy/controller/ProductController.java`

- 产品 CRUD 操作
- MDN (产品型号编码) 唯一性校验
- 产品图片管理 (一对多关系)
- 产品状态变更

### 2.2 出货管理 (代码明确证明)

**来源**: `vpp-api-meta/vpp-biz/src/main/java/com/nahui/energy/controller/ShipmentLogController.java`

- 出货日志分页查询
- Excel 导入出货信息 (校验 MDM 产品是否存在)
- 手动新增出货记录
- 删除出货记录 (状态为 0 才可删除)

### 2.3 出货导入校验规则 (代码明确证明)

**来源**: `vpp-api-meta/vpp-biz/src/main/java/com/nahui/energy/service/impl/ShipmentLogServiceImpl.java`

1. 海尔SN (`hr_sn`) 不能为空
2. MDN 必须在产品表中存在 (通过 `queryByWdn` 校验)
3. 非自研产品 (dev_type != "自研") 必须填写供应商SN
4. 导入时记录操作人 (从 SecurityUtils 获取当前用户名)

## 3. 数据库表 (代码明确证明)

**来源**: `vpp-api-meta/vpp-biz/src/main/resources/mapper/`

| 表名 | Mapper | 说明 |
|---|---|---|
| `t_product` | ProductMapper | 产品表 |
| `t_product_image` | ProductMapper (insertBatchProductImage) | 产品图片表 |
| `t_shipment_log` | ShipmentLogMapper | 出货日志表 |

### 3.1 t_product 核心字段

| 字段 | 说明 |
|---|---|
| product_name | 产品名称 |
| mdn | MDN (产品型号编码, 唯一) |
| dtc | DTC编码 |
| dev_type | 设备类型 (自研/供应商) |
| device_type | 设备类型 |
| sub_type | 子类型 |
| status | 状态 |
| supplier | 供应商 |
| connect_type | 连接类型 |

### 3.2 t_product_image 核心字段

| 字段 | 说明 |
|---|---|
| product_id | 产品ID |
| image_url | 图片URL |

### 3.3 t_shipment_log 核心字段

| 字段 | 说明 |
|---|---|
| product_id | 产品ID (关联 t_product) |
| supplier_sn | 供应商SN |
| mdn | MDN |
| hr_sn | 海尔SN |
| category | 类别 |
| ship_time | 出货时间 |
| status | 状态 (0=可删除, 非0=已绑定不可删除) |

## 4. Controller/API 路由 (代码明确证明)

### 4.1 产品管理 `/product`

| 路径 | 方法 | 说明 |
|---|---|---|
| /page | GET | 分页查询产品信息 |
| /{id} | GET | 根据ID查询产品详情 |
| / (POST) | POST | 添加产品信息 |
| / (PUT) | PUT | 修改产品信息 |
| /changeStatus | PUT | 修改产品状态 |

### 4.2 出货管理 `/shipment`

| 路径 | 方法 | 说明 |
|---|---|---|
| /page | GET | 分页查询出货日志 |
| /importData | POST | 导入出货信息 (Excel) |
| /{id} | DELETE | 删除出货记录 |
| /add | POST | 新增出货记录 |

## 5. 知识库更新记录

| 日期 | 更新内容 | 来源 |
|---|---|---|
| 2026-05-14 | 创建产品与出货管理文档 | vpp-api-meta 全量通读 |
