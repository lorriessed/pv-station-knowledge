# 零碳电站（Zero Carbon Station）

更新时间: 2026-05-13

## 已确认知识

### 零碳电站服务架构
**来源**: `rrsjk-hds-web` → `LightOperationZeroCarbonStationController.java` (commits 9ca7b10/63a7bf7, dengqiu, 2026-05-12)
- 零碳电站接口位于 `rrsjk-hds-web` 服务
- Controller: `LightOperationZeroCarbonStationController` (v2 版本)
- 持续完善接口字段和设备相关接口

### 零碳电站设备与逆变器
**来源**: `rrsjk-light-operation-service` → `HaierEnergyInverterRealtimeService.java`, `LightZeroCarbonOdsStationServiceImpl.java`, 各 `HaierDeviceType*RealtimeAdapter.java`, `MpptRealtimeDto.java` (commit 8818b2b, dengqiu, 2026-05-12)
- 零碳电站设备相关接口完善
- 海尔能源逆变器实时数据服务：`HaierEnergyInverterRealtimeService`
- 设备类型适配器：`HaierDeviceType50100RealtimeAdapter`, `HaierDeviceType50300RealtimeAdapter`, `HaierDeviceType60419RealtimeAdapter`, `HaierDeviceType65323RealtimeAdapter`
- 新增 `MpptRealtimeDto`（MPPT实时数据）
- ODS 站数据查询：`LightZeroCarbonOdsStationQuery`, `LightZeroCarbonOdsStationCardDto`, `LightZeroCarbonOdsStationSkuDetailDto`
- Mapper: `LightZeroCarbonOdsStation.xml`, `LightZeroCarbonOdsStationSku.xml`, `LightZeroCarbonOdsEStation.xml`

### 业务合作意向与逆变器查询
**来源**: `rrsjk-hds-web` → `BusinessCooperationIntentionController.java` (commit f7d0d55, sunzn, 2026-05-12)
- 业务合作意向控制器支持逆变器数据查询

## 待确认
- 零碳电站的完整业务流程（录单→审核→并网→运营）
- 零碳电站与普通电站的数据模型差异
- ODS 数据源的接入方式和同步频率
- 零碳适家结算与安装费结算的关系

## 来源
- 每日代码扫描 2026-05-13，rrsjk-hds-web, rrsjk-light-operation-service
