# source-map/files

更新时间: 2026-05-11

## 已确认知识

### 水印相机插件
- **仓库**: nhpv_watermark_camera (Flutter plugin)
- **描述**: 运维/安装场景使用的水印相机，支持二维码水印、GPS/时间戳水印
- **关键文件**:
  - `lib/nhpv_camera.dart` - Dart API 入口
  - `android/libs/camera-sdk-release.aar` - Android SDK (2.0.4)
  - `ios/Frameworks/WatermarkCamera.framework` - iOS SDK
  - `pubspec.yaml` - version: 2.0.4
- **扫描日期**: 2026-05-11

### 储能服务 (rrsjk-energystorage-service)
- **仓库**: rrsjk-energystorage-service (Java/Spring Cloud 微服务)
- **描述**: 储能小程序后端服务，包含安装维修、收益测算、充放策略等功能
- **安装维修模块**:
  - `entity/installMaintenance/InstallMaintenanceInfo.java` - 安装维修实体
  - `entity/installMaintenance/ConsultationDetail.java` - 项目咨询实体
  - `service/installMaintenance/InstallMaintenanceInfoService.java` - 安装维修服务
  - `service/installMaintenance/InstallMaintenanceInfoJobService.java` - 安装维修定时任务 (15天自动好评)
  - `jobModel/installMaintenanceInfo/InstallMaintenanceInfoModel.java` - 自动好评逻辑
  - `mybatis/mapper/InstallMaintenanceInfo.xml` - MyBatis 映射
  - `mybatis/mapper/ConsultationDetail.xml` - 咨询详情映射
- **收益测算模块**:
  - `service/incomecalc/CnIncomeCalcInfoServiceImpl.java` - 收益测算
  - `service/incomecalc/CnChargeBaseDetailServiceImpl.java` - 充放策略基础配置
  - `service/incomecalc/CnPeriodDivisionDetailServiceImpl.java` - 时段划分配置
- **首页模块**:
  - `entity/index/EnergyCase.java` - 经典案例
  - `entity/index/CooperationInfo.java` - 加盟合作
  - `entity/index/HotNews.java` - 热点资讯
- **扫描日期**: 2026-05-11

### 汇流组管理
- **仓库**: rrsjk-light-service + rrsjk-merchant-web
- **描述**: 整村推进/汇流组管理功能
- **关键文件**:
  - `rrsjk-light-impl/src/main/resources/mybatis/mapper/WholeVillageTogether.xml` - 汇流组 SQL (含 authorityMobileList 手机端权限过滤)
  - `rrsjk-merchant-web/.../controller/light/WholeVillageTogetherController.java` - 汇流组控制器 (使用 buildNewAuthorityCondition)
- **扫描日期**: 2026-05-11

### 逆变器数据采集
- **仓库**: rrsjk-light-data-service
- **描述**: 锦浪等逆变器数据采集和处理
- **关键文件**:
  - `LightInveterServiceImpl.java` - 逆变器数据处理 (锦浪数据采集，含日志增强)
- **扫描日期**: 2026-05-11

### 分中心利润报表
- **仓库**: rrsjk-light-report-service
- **描述**: 分中心利润实际数据生成
- **关键文件**:
  - `CenterProfitActualModel.java` - 利润计算模型 (含硬编码收入和成本常量)
- **扫描日期**: 2026-05-11

## 待确认
- 储能数据库表名映射 (InstallMaintenanceInfo → ? 表)
- 汇流组数据库表名

## 来源
- 代码扫描 2026-05-11。
