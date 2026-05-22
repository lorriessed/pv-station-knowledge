# 云效驱动代码学习报告 — 第7期补漏 (2026-03-23 ~ 2026-04-12)

## 扫描范围
- 云效需求: 30 个 (TAEI-2953 ~ TAEI-2986)
- 涉及开发人员: 孙志男、于淼、马金虎、代继宁、王希然、包鑫、王斌(龙龙)、马斌、解钦、姜传德(德)、laowang
- Git 提交: 967 条 (去重后 ~600+ 条)
- 涉及仓库: 16 个 (rrsjk-light-service 438条, rrsjk-admin-web 157条, rrsjk-light-report-service 82条, rrsjk-finance-service 66条, rrsjk-hds-web 60条, rrsjk-light-data-service 57条, rrsjk-merchant-web 38条, vpp-pv-oversea 18条 等)

## 需求 → 代码关联

| 需求号 | 标题 | 负责人 | 开发人员 | 相关提交数 | 涉及仓库 |
|---|---|---|---|---|---|
| TAEI-2953 | HDS运维收入成本管理：新增保发考核账单记账管理 | 高媛 | 孙志男、魏秋阳、李培龙 | ~50 | rrsjk-light-service, rrsjk-hds-web |
| TAEI-2954 | 零碳商城用户签收不通知储能 | 刘艺 | 王金浩 | 0 | (未检测到提交) |
| TAEI-2955 | 电费机制电价管理：主列表及导出增加字段 | 杨越越 | 马斌 | ~5 | rrsjk-light-service |
| TAEI-2956 | 商城1PG0增加利润中心 | 杨越越 | 包鑫 | ~63 | rrsjk-light-report-service, rrsjk-light-service |
| TAEI-2957 | 领用逻辑优化 | 杨越越 | 解钦 | ~51 | rrsjk-light-service, rrsjk-admin-web, rrsjk-light-report-service |
| TAEI-2958 | 电费结算单价统计表（区域/项目公司维度） | 杨越越 | 包鑫 | ~40 | rrsjk-light-report-service |
| TAEI-2959 | 电费暂估逻辑变更 | 杨越越 | 包鑫 | ~40 | rrsjk-light-report-service |
| TAEI-2960 | 电费结算单价统计表（省维度） | 杨越越 | 包鑫 | ~40 | rrsjk-light-report-service |
| TAEI-2961 | 发电户号修改逻辑调整 | 徐晓凤 | 王希然、付凯善 | ~80 | rrsjk-light-data-service, rrsjk-admin-web |
| TAEI-2962 | 电费收益优化 | 徐晓凤 | 王希然、商轶龙、马金虎 | ~116 | rrsjk-light-service, rrsjk-admin-web, rrsjk-light-data-service |
| TAEI-2963 | 市场部发电管理报表-HDS | 徐晓凤 | 王希然、李培龙 | ~80 | rrsjk-light-data-service, rrsjk-hds-web |
| TAEI-2964 | HDS-数字报表-运营商日清优化 | 徐晓凤 | 王希然、李培龙 | ~80 | rrsjk-light-data-service, rrsjk-hds-web |
| TAEI-2965 | APP水印相机二期 | 徐晓凤 | 马斌、姜廷、杨辉、董学强 | ~54 | vpp-pv-oversea, rrsjk-light-service |
| TAEI-2967 | 完工后终止电站 | 杨越越 | 解钦、袁睿林 | ~51 | rrsjk-light-service, rrsjk-admin-web |
| TAEI-2968 | 派单3.0优化 | 杨越越 | 解钦 | ~51 | rrsjk-light-service, rrsjk-admin-web |
| TAEI-2969 | HDS-运维收入成本管理-账单电站明细覆盖更新 | 高媛 | 孙志男、魏秋阳、李培龙 | ~244 | rrsjk-hds-web, rrsjk-light-service |
| TAEI-2970 | HDS-电费报表(项目公司) 公司备案优化 | 高媛 | 孙志男、魏秋阳、李培龙 | ~244 | rrsjk-hds-web, rrsjk-light-service |
| TAEI-2971 | HDS-电费列表 公司备案优化 | 高媛 | 孙志男、魏秋阳、李培龙 | ~244 | rrsjk-hds-web, rrsjk-light-service |
| TAEI-2974 | 股转类非乐道非统众电费单据传集团FAP对账 | 杨越越 | 王斌 | ~101 | rrsjk-light-service, rrsjk-admin-web |
| TAEI-2975 | 政策优化-变更房型类优化 | 杨越越 | 包鑫 | ~63 | rrsjk-light-report-service |
| TAEI-2977 | GDE即采即销临时流程 | 杨越越 | 马斌、张硕文 | ~54+18 | vpp-pv-oversea, rrsjk-light-service |
| TAEI-2979 | 招银电费账单接口 | 刘艺 | 姜传德 | ~37 | rrsjk-light-openapi-service, rrsjk-light-service |
| TAEI-2984 | 运维收入成本管理-账单合并确认收款 | 高媛 | 孙志男、魏秋阳、李培龙 | ~244 | rrsjk-hds-web, rrsjk-light-service |
| TAEI-2985 | 广发合规进件 | 刘艺 | 于淼、杨辉、王希然、王金浩、付凯善、袁睿林、董学强、马金虎 | ~103+116 | rrsjk-light-service, rrsjk-admin-web, rrsjk-light-data-service |
| TAEI-2986 | 工商业产值单+产值确认法+产值报表 | 杨越越 | 王斌 | ~101 | rrsjk-light-service, rrsjk-admin-web |

## 业务链分析

### 1. HDS运维收入成本管理（TAEI-2953/2969/2972/2984）
**核心变更**:
- 新增 `OperationMaintenanceSapLog` 实体 — 运维收入管理记账日志表，记录SAP记账凭证、记账状态、凭证号等
- `OperationMaintenance` 实体新增 `allOrderNo` 字段 — 合并收款总单号
- 新增 `mergeSk` 方法 — 合并收款功能，将多条运维收入记录合并为一笔收款并推送SAP
- 保发考核账单记账管理 — 新增保发账单确认实际功能、保发订单电站导入功能
- 批量覆盖电站功能 — 支持用导入的电站数据覆盖已有账单电站明细

**涉及文件**:
- `rrsjk-light-api/.../entity/OperationMaintenanceSapLog.java` (新建)
- `rrsjk-light-api/.../entity/OperationMaintenance.java` (allOrderNo字段)
- `rrsjk-light-impl/.../dao/OperationMaintenanceSapLogDao.java` (新建)
- `rrsjk-light-impl/.../service/impl/OperationMaintenanceServiceImpl.java` (mergeSk方法)
- `rrsjk-light-impl/.../mybatis/mapper/OperationMaintenanceSapLog.xml` (新建)
- `rrsjk-hds-web` 前端对应Controller和页面

### 2. 电费暂估逻辑变更（TAEI-2959）
**核心变更**:
- 暂估电价查询从 `LightCityElecPrice` (通用城市电价表) 改为 `LightEstimateCityElecPrice` (独立暂估电价表)
- 新增 `LightEstimateCityElecPrice` 实体和DAO — 按省市区维度维护暂估电价
- `LightEstimateStationServiceImpl` 中电价Map构建逻辑变更

**涉及文件**:
- `rrsjk-light-report-api/.../entity/local/LightEstimateCityElecPrice.java` (新建)
- `rrsjk-light-report-impl/.../dao/local/LightEstimateCityElecPriceDao.java` (新建)
- `rrsjk-light-report-impl/.../service/impl/LightEstimateStationServiceImpl.java` (逻辑变更)
- `rrsjk-light-report-impl/.../mapper/local/LightEstimateCityElecPrice.xml` (新建)

### 3. 股转FAP对账（TAEI-2974）
**核心变更**:
- 新增"是否股转"字段到项目公司配置 — CBS管理后台和导出增加显示
- 电费收益收款：股转非统众乐道公司传旧FAP接口
- 新增FAP状态枚举
- 手工传FAP接口
- FAP对账状态回调接口改造
- 电费收益确认收款不记账逻辑（股转/非股转分别处理）

**涉及文件**:
- `rrsjk-light-service` FAP相关Service和Controller
- `rrsjk-admin-web` 项目公司配置页面

### 4. 领用逻辑优化（TAEI-2957）
**核心变更**:
- 领用明细列表重构
- 新增已领料未完工材料库龄分析报表
- 领用单新增 `completeFlag` 字段 — 用于确认完工前领用是否完工
- 完工节点兼容出库事务执行的逻辑变化
- 电站终止逻辑变更

**涉及文件**:
- `rrsjk-admin-web` 领用相关页面
- `rrsjk-light-report-service` 库龄分析报表
- `rrsjk-light-service` 领用Service和Mapper

### 5. GDE即采即销临时流程（TAEI-2977）
**核心变更**:
- vpp-pv-oversea SAP集成增强 — 销售订单创建、客户编码获取、冲销接口
- 付款计划、销售订单和采购订单确认功能
- SAP发票账户生成中的客户编号处理

**涉及文件**:
- `vpp-pv-oversea` SAP相关Controller和Service

### 6. 招银电费账单接口（TAEI-2979）
**核心变更**:
- 新增招银电费账单查询功能
- 招银租赁查询关联查询支持

**涉及文件**:
- `rrsjk-light-openapi-service` report相关接口

### 7. 工商业收入成本台账报表（TAEI-2986）
**核心变更**:
- 工商业收入成本台账报表取数逻辑
- 工商业2.0查已上收入过滤已冲销的
- 工商业终验法申请/设计成本计算修改

**涉及文件**:
- `rrsjk-light-service/.../CmReportServiceImpl.java`
- `rrsjk-admin-web` 工商业相关页面

## 知识库更新

### domains/settlement.md 追加
- **运维收入合并收款功能** — OperationMaintenance.allOrderNo合并收款总单号 + OperationMaintenanceSapLog记账日志表 + mergeSk方法 (TAEI-2984, sunzn, 2026-04-08)
- **暂估电价独立表** — LightEstimateCityElecPrice实体，按省市区维度维护暂估电价，替代原LightCityElecPrice通用表 (TAEI-2959, baoxin, 2026-04-08)

### domains/inventory.md 追加
- **领用单completeFlag字段** — 用于确认完工前领用是否完工 (TAEI-2957, 解钦, 2026-03-31)
- **库龄分析报表** — 已领料未完工材料库龄分析，新增公司/品牌/物料组/产品组字段 (TAEI-2957, 解钦, 2026-03-27)

### data/tables.md 追加
- **OperationMaintenanceSapLog** — 运维收入管理记账日志表 (id, 记账凭证, 记账状态, allOrderNo等) (TAEI-2984)
- **LightEstimateCityElecPrice** — 暂估电价表 (id, provinceId, provinceName, cityId, cityName, elecPrice) (TAEI-2959)

### domains/cbs-management.md 追加
- **项目公司"是否股转"字段** — CBS项目公司配置列表和导出增加是否股转字段显示，用于区分股转类公司与普通公司 (TAEI-2974, tn_wangb, 2026-03-25~04-10)

### domains/vpp-api.md 追加
- **GDE即采即销SAP集成** — vpp-pv-oversea中销售订单创建、客户编码获取、冲销接口、FAP相关功能 (TAEI-2977, mabin, 2026-03-31~04-01)

### domains/policy.md 追加
- **电站完工匹配政策区位码** — 完工时间和签约时间大于60天才重新匹配新区位码，完工时重新匹配policyCode并保存原policyCode到扩展表 (TAEI-2967, 解钦, 2026-04-10~04-11)
