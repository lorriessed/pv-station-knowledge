     1|# source-map/files
     2|
     3|更新时间: 2026-05-11
     4|
     5|## 已确认知识
     6|
     7|### 水印相机插件
     8|- **仓库**: nhpv_watermark_camera (Flutter plugin)
     9|- **描述**: 运维/安装场景使用的水印相机，支持二维码水印、GPS/时间戳水印
    10|- **关键文件**:
    11|  - `lib/nhpv_camera.dart` - Dart API 入口
    12|  - `android/libs/camera-sdk-release.aar` - Android SDK (2.0.4)
    13|  - `ios/Frameworks/WatermarkCamera.framework` - iOS SDK
    14|  - `pubspec.yaml` - version: 2.0.4
    15|- **扫描日期**: 2026-05-11
    16|
    17|### 储能服务 (rrsjk-energystorage-service)
    18|- **仓库**: rrsjk-energystorage-service (Java/Spring Cloud 微服务)
    19|- **描述**: 储能小程序后端服务，包含安装维修、收益测算、充放策略等功能
    20|- **安装维修模块**:
    21|  - `entity/installMaintenance/InstallMaintenanceInfo.java` - 安装维修实体
    22|  - `entity/installMaintenance/ConsultationDetail.java` - 项目咨询实体
    23|  - `service/installMaintenance/InstallMaintenanceInfoService.java` - 安装维修服务
    24|  - `service/installMaintenance/InstallMaintenanceInfoJobService.java` - 安装维修定时任务 (15天自动好评)
    25|  - `jobModel/installMaintenanceInfo/InstallMaintenanceInfoModel.java` - 自动好评逻辑
    26|  - `mybatis/mapper/InstallMaintenanceInfo.xml` - MyBatis 映射
    27|  - `mybatis/mapper/ConsultationDetail.xml` - 咨询详情映射
    28|- **收益测算模块**:
    29|  - `service/incomecalc/CnIncomeCalcInfoServiceImpl.java` - 收益测算
    30|  - `service/incomecalc/CnChargeBaseDetailServiceImpl.java` - 充放策略基础配置
    31|  - `service/incomecalc/CnPeriodDivisionDetailServiceImpl.java` - 时段划分配置
    32|- **首页模块**:
    33|  - `entity/index/EnergyCase.java` - 经典案例
    34|  - `entity/index/CooperationInfo.java` - 加盟合作
    35|  - `entity/index/HotNews.java` - 热点资讯
    36|- **扫描日期**: 2026-05-11
    37|
    38|### 汇流组管理
    39|- **仓库**: rrsjk-light-service + rrsjk-merchant-web
    40|- **描述**: 整村推进/汇流组管理功能
    41|- **关键文件**:
    42|  - `rrsjk-light-impl/src/main/resources/mybatis/mapper/WholeVillageTogether.xml` - 汇流组 SQL (含 authorityMobileList 手机端权限过滤)
    43|  - `rrsjk-merchant-web/.../controller/light/WholeVillageTogetherController.java` - 汇流组控制器 (使用 buildNewAuthorityCondition)
    44|- **扫描日期**: 2026-05-11
    45|
    46|### 逆变器数据采集
    47|- **仓库**: rrsjk-light-data-service
    48|- **描述**: 锦浪等逆变器数据采集和处理
    49|- **关键文件**:
    50|  - `LightInveterServiceImpl.java` - 逆变器数据处理 (锦浪数据采集，含日志增强)
    51|- **扫描日期**: 2026-05-11
    52|
    53|### 分中心利润报表
    54|- **仓库**: rrsjk-light-report-service
    55|- **描述**: 分中心利润实际数据生成
    56|- **关键文件**:
    57|  - `CenterProfitActualModel.java` - 利润计算模型 (含硬编码收入和成本常量)
    58|- **扫描日期**: 2026-05-11
    59|
    60|## 待确认
    61|- 储能数据库表名映射 (InstallMaintenanceInfo → ? 表)
    62|- 汇流组数据库表名
    63|
    64|## 来源
    65|- 代码扫描 2026-05-11。
    66|

### 合同相关文件 (rrsjk-light-service)
- `rrsjk-light-api/.../entity/LightStationContractRecord.java` - 合同记录实体
- `rrsjk-light-api/.../entity/LightStationContractRecordLog.java` - 合同日志实体
- `rrsjk-light-api/.../service/LightStationContractRecordService.java` - 合同服务接口
- `rrsjk-light-impl/.../dao/LightStationContractRecordDao.java` - 合同 DAO
- `rrsjk-light-impl/.../service/impl/LightStationContractRecordServiceImpl.java` - 合同服务实现
- `rrsjk-light-impl/.../service/event/LightStationDccContractEvent.java` - 合同事件
- `rrsjk-light-impl/.../service/event/listener/LightStationDccContractListener.java` - 合同监听器
- `rrsjk-light-impl/.../service/model/dcc/DccContractModel.java` - DCC 模型
- `rrsjk-light-impl/.../service/model/dcc/StationSignSendSmsModel.java` - 短信模型
- `rrsjk-light-impl/.../resources/mybatis/mapper/LightStationContractRecord.xml` - 合同 Mapper
- `rrsjk-light-impl/.../resources/mybatis/mapper/LightStationContractRecordLog.xml` - 合同日志 Mapper
