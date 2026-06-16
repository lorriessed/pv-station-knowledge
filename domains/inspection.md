---
name: 巡检管理
domain: 运维管理
status: active
last_updated: 2026-06-15
sources:
  - rrsjk-light-service (laowang/王金浩, 2026-06-11~12, 分支 origin/20260604-wjh-jsxj)
---

# 巡检管理 (Patrol Inspection)

## 概述
光伏电站巡检抽检功能，支持按地区装机量查询、抽检样本选择、巡检任务分配、记录查询等。

## 核心实体 (代码明确证明)

### PatrolInspectionRequired
- **路径**: `rrsjk-light-api/src/main/java/com/rrsjk/light/entity/inspection/PatrolInspectionRequired.java`
- **用途**: 巡检需求/任务定义
- **DAO**: `PatrolInspectionRequiredDao`
- **Mapper**: `mybatis/mapper/inspection/PatrolInspectionRequired.xml`

### PatrolInspectionQuestionDetail
- **路径**: `rrsjk-light-api/src/main/java/com/rrsjk/light/entity/inspection/PatrolInspectionQuestionDetail.java`
- **用途**: 巡检问题明细
- **DAO**: `PatrolInspectionQuestionDetailDao`
- **Mapper**: `mybatis/mapper/inspection/PatrolInspectionQuestionDetail.xml`

### AddressQuantity
- **路径**: `rrsjk-light-api/src/main/java/com/rrsjk/light/entity/inspection/AddressQuantity.java`
- **用途**: 地区装机量统计（用于抽检样本选择）

## 功能模块 (代码明确证明, 2026-06-15)
**来源**: rrsjk-light-service (commits: ecfbd584, e042b1aa, a86879f6, bed8a270, 4c353feb, laowang, 2026-06-11~12)

1. **地区装机量查询**: 按地区统计装机容量，用于确定抽检样本分布
2. **抽检样本选择**: 基于装机量的随机/分层抽检
3. **巡检任务分页查询**: 支持条件筛选、分页
4. **巡检记录与详情**: 任务详情、巡检记录查询
5. **操作日志**: 巡检操作审计追踪
6. **样本审核**: 抽检样本的审核流程

## 技术特征
- 新增 `inspection` 包（entity + dao + mapper），独立于现有业务模块
- 使用 MyBatis Mapper XML 定义 SQL
- 分页查询支持（具体分页参数待确认）
