# 云效驱动代码学习报告 — 第5期 (2026-02-09 ~ 2026-03-01)

**扫描时间**: 2026-02-09 ~ 2026-03-01
**生成时间**: 2026-05-21 04:00

## 扫描范围
- 云效需求: 3 个 (TAEI-2868, TAEI-2869, TAEI-2870)
- 涉及人员: 魏秋阳, 孙志男(sunzn), 解钦, 袁睿林, 商轶龙
- 实际有提交: 孙志男(67条), 解钦(27条) = 93条提交
- 涉及仓库: rrsjk-light-operation-service(26), rrsjk-light-service(22), rrsjk-hds-web(16), rrsjk-admin-web(13), rrsjk-light-data-service(12), repairs(3), rrsjk-trade-service(3)

## 需求 → 代码关联

| 需求号 | 标题 | 负责人 | 参与人 | 相关提交 | 涉及仓库 |
|---|---|---|---|---|---|
| TAEI-2868 | 工单备件登记逆变器及电站数据变更同步提报逻辑优化 | 高媛(PM) | 魏秋阳, 孙志男 | sunzn 67条 | repairs, rrsjk-light-operation-service, rrsjk-light-data-service, rrsjk-hds-web, rrsjk-light-service, rrsjk-merchant-web |
| TAEI-2869 | 【电站变更优化】新增界面和审核界面增加变更次数提示，组件编码校验 | 杨越越(PM) | 解钦, 薛荣基, 袁睿林 | 解钦 27条 | rrsjk-light-service, rrsjk-admin-web, rrsjk-trade-service |
| TAEI-2870 | 【政策】B段政策介入优化 | 杨越越(PM) | 薛荣基, 商轶龙 | 无(商轶龙零提交) | - |

## 业务链分析

### 1. 工单备件登记逆变器变更优化 (TAEI-2868)

**核心变更链路**:
1. **repairs 工单备件服务** → `WoPartServiceImpl`: 新增 `NO_CREATE_REGISTER = -1L` 常量，允许备件登记时不创建逆变器变更信息
2. **rrsjk-light-operation-service 逆变器变更** → `LightStationInverterChangeServiceImpl`: 新增多维度校验（旧逆变器绑定关系、唯一性、与报警电站绑定、新逆变器不能已绑定）
3. **rrsjk-light-data-service 锦浪逆变器** → 修复数据采集超时、解析异常、分页查询逻辑
4. **rrsjk-light-data-service 逆变器新字段** → 新增 `overvoltageThresholdStage1`(过压保护阈值) + `outputLimit`(功率输出限制)，覆盖3个实体表

**涉及表**:
- `light_station_inverter_change`: 逆变器变更记录表
- `light_inveter` / `light_inveter_data` / `light_inveter_record`: 逆变器数据表（新增2字段）

**涉及分支**: `szn_change_inverter_youhua_20260210`, `szn_jinlong_youhua_20260210`, `szn_socia_contract_20260130`, `szn_contract_youhua_20260205`, `szn_loss_management_20260115`, `szn_socialization_20251117`

### 2. 电站变更优化 — 变更次数统计 & 组件编码校验 (TAEI-2869)

**核心变更链路**:
1. **rrsjk-light-service 方案变更** → `LightStationPlanChangeServiceImpl`: 新增 `checkAuditProcessingPlan()` 防止并发变更
2. **变更次数统计** → `LightStationPlanChangeExtra` + SQL子查询统计 `completeBeforeChangeNum` / `completeAfterChangeNum`
3. **组件编码校验** → `LightModuleSnServiceImpl`: 校验组件SN对应物料号与新方案一致
4. **派单2.0** → `BaseLightStationMode` 方案变更后清空审核字段(audit_by, audit_at等6字段)，`DispatchOrderAspect` 提交订单时动态检查技术审核状态
5. **rrsjk-admin-web 前端展示** → 4个FreeMarker模板新增变更次数展示区域
6. **发票红冲** → `InvoiceJobServiceImpl`: 用 `LightCompanyInfoService.isStockTransfer()` 替代 `SystemCode` 判断股转

**涉及表**:
- `light_station_plan_change`: 方案变更表（新增 `complete_before_change_num`, `complete_after_change_num` 统计字段）
- `light_station_audit`: 审核表（新增 `updateForClearAuditInfo` SQL）
- `light_audit_dispatch_log`: 派单日志表（新增 `findWaitDispatchLogByStationIdAndAuditType` 查询）

**涉及分支**: `xq-feature-20260224-small-change`, `xq-feature-cost-report-find`, `20260113-feature-tech-dispatch-order`

### 3. 政策B段介入优化 (TAEI-2870)
- 负责人杨越越(PM)，参与人薛荣基(PM)+商轶龙
- 商轶龙在此时间段内零Git提交
- 无法定位相关代码变更，可能需求尚未开发或通过其他人员完成

### 4. 社会化电站导入优化 (分支: szn_socia_contract_20260130)
- **rrsjk-hds-web**: 必填字段校验、手机号/身份证格式校验、ZIP中文编码修复
- **rrsjk-light-operation-service**: 社会化电站枚举更新、合同年限字段类型修改

### 5. 新旧区域映射校验 (分支: szn_contract_youhua_20260205)
- **rrsjk-light-service**: Redis存储新旧区域ID映射(`new_region_id_old_region_id`)
- **rrsjk-hds-web**: 新增区域映射关系接口

### 6. 运营损耗管理优化 (分支: szn_loss_management_20260115)
- **rrsjk-admin-web**: 轻量化运营损失管理页面下拉框优化

### 7. 其他修复
- 工单申诉超期状态重置 (`LightOperationWorkOrderServiceImpl`)
- 电量账单统计DISTINCT去重 (`LightOperationStationElecBill.xml`)
- 电费结算NULL值判断修复
- 资产所属分类生成 (`SpecialFlagEnum.generateSpecialFlagOptions()`)
- MyBatis XML特殊字符转义修复

## 知识库更新

| 操作 | 文件 | 内容摘要 |
|---|---|---|
| 追加 | `domains/approval.md` | 派单2.0审核清空字段、技术审核状态检查、并网资料校验、方案变更次数统计 |
| 追加 | `domains/inverter-data.md` | 逆变器变更校验逻辑、工单备件不创建变更场景、逆变器新字段(过压/功率)、锦浪修复 |
| 追加 | `domains/settlement.md` | 发票红冲股权转移判断、电量账单DISTINCT去重、电费结算NULL修复 |
| 追加 | `domains/station-lifecycle.md` | 组件编码校验、新旧区域映射、社会化电站导入、SpecialFlag生成、工单申诉超期修复 |
| 追加 | `data/tables.md` | 逆变器新字段、方案变更次数字段、电站查询扩展条件 |
| 追加 | `data/enums.md` | ChangeNodeEnum(完工前/后变更)、审核类型枚举 |

## 未覆盖项
- **TAEI-2870 (政策B段)**: 商轶龙零提交，未能定位代码变更
- **魏秋阳、袁睿林**: 映射表中无已知Git author，使用中文名扫描无结果
- 可能使用海尔工号或其他别名，需要后续补充扫描
