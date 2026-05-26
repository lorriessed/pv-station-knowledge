# 派单定时任务关联机制 (TAEI-3078)

**来源**: `rrsjk-light-service` → `LightAuditDispatchJobServiceImpl.java`, `LightAuditDispatchTimeConfigServiceImpl.java`, `LightAuditDispatchLogServiceImpl.java`; `rrsjk-admin-web` → `LightAuditDispatchTimeConfigController.java` (解钦, 2026-05-11~05-14)

## 一、整体架构

```
┌───────────────────────────────────────────────────────────────────┐
│                         Admin 管理后台                             │
│  LightAuditDispatchTimeConfigController                           │
│    ├── addConfig() → 新增非工作日派单时间配置 + 注册一次性cron任务  │
│    ├── terminateConfig() → 终止配置 + 删除cron任务                  │
│    └── deleteConfig() → 删除配置 + 删除cron任务                     │
├───────────────────────────────────────────────────────────────────┤
│                         定时任务调度                               │
│  JobService (CBS定时任务引擎)                                      │
│    ├── 每日8:30: dispatchOrderForPlanAudit/TechCheck/WaitFirstAudit│
│    └── 一次性cron: dispatchBacklogByConfigId(configId)             │
├───────────────────────────────────────────────────────────────────┤
│                         派单服务层                                 │
│  LightAuditDispatchJobServiceImpl                                 │
│    ├── dispatchOrderForPlanAudit() → 方案审核派单                   │
│    ├── dispatchOrderForTechCheck() → 技术验收派单                   │
│    ├── dispatchOrderForWaitFirstAudit() → 商务审核派单              │
│    └── dispatchBacklogByConfigId(configId) → 积压工单补跑           │
├───────────────────────────────────────────────────────────────────┤
│                         派单执行层                                 │
│  LightAuditDispatchLogServiceImpl.dispatchOrder(request, skip)     │
│    ├── 1. Redis分布式锁防并发                                      │
│    ├── 2. 校验是否在派单时间范围内 (isWithinDispatchTime)           │
│    ├── 3. 检查是否已存在待处理派单                                  │
│    ├── 4. 获取有效审核人员列表                                      │
│    ├── 5. 确定派单类型（首派/转派/积压补派）                         │
│    ├── 6. 轮询选择审核员                                           │
│    └── 7. 创建派单日志 + 更新审核表                                │
└───────────────────────────────────────────────────────────────────┘
```

## 二、三种审核派单定时任务

| 定时任务 | 审核类型 | 对应AuditType枚举 | 查询条件 |
|---------|---------|-----------------|---------|
| `dispatchOrderForPlanAudit` | 方案审核派单 | PLAN_AUDIT | `findNeedDispatchByPlanAudit()` |
| `dispatchOrderForTechCheck` | 技术验收派单 | TECH_CHECK | `findNeedDispatchByTechCheck()` |
| `dispatchOrderForWaitFirstAudit` | 商务审核派单 | WAIT_FIRST_AUDIT | `findNeedDispatchByWaitFirstAudit()` |

**执行时间**: 每天 08:30
**前置校验**: `isHoliday()` — 通过 `CalendarDayService` 查询日历，休息日不执行

## 三、非工作日派单时间配置

### 表: `light_audit_dispatch_time_config`

| 字段 | 类型 | 说明 |
|---|---|---|
| id | Long | 主键 |
| config_date | date | 配置日期 |
| audit_type | varchar | 审核类型: PLAN_AUDIT/TECH_CHECK/WAIT_FIRST_AUDIT |
| start_time | varchar | 开始时间 (HH:mm) |
| end_time | varchar | 结束时间 (HH:mm) |
| status | int | 状态: 0=禁用, 1=启用, 2=已完成 |
| description | varchar | 描述说明 |
| terminated_at | datetime | 终止时间 |
| terminated_by | varchar | 终止人工号 |

### 状态流转
```
新增 → ENABLED(1, 启用)
         ↓ (配置日期+时间到期后，动态标记)
       COMPLETED(2, 已完成)
         ↓ (手动终止)
       DISABLED(0, 禁用)
```

**动态状态标记**: `markExpiredAsCompleted()` 方法在列表查询时动态判断，如果当前时间超过配置日期+结束时间，返回状态为"已完成"（不写库）。

## 四、派单时间校验逻辑

`LightAuditDispatchLogServiceImpl.isWithinDispatchTime()`:

```
休息日/节假日?
    ↓ YES → 只查非工作日配置表 (isWithinNonWorkdayDispatchTime)
    ↓ NO
工作日正常时间(8:30~17:30/18:00)?
    ↓ YES → 直接放行 ✅
    ↓ NO
    查非工作日配置表 (isWithinNonWorkdayDispatchTime)
```

**审核类型对应的工作时间**:
- 商务审核 (WAIT_FIRST_AUDIT): 8:30 ~ 17:30
- 方案审核/技术审核 (PLAN_AUDIT/TECH_CHECK): 8:30 ~ 18:00

**工作日额外派单时间校验**: `validateConfigRule()` — 工作日只能在正常工作时间之外配置时间段，确保不会与正常派单冲突。

## 五、积压工单补跑定时任务机制

### 创建流程

```
1. Admin新增非工作日派单时间配置 → addConfig.do
2. Controller调用 lightAuditDispatchTimeConfigService.addConfig(config) → 返回configId
3. Controller调用 scheduleBacklogDispatchJob(configId, config):
   ├── 构造 cron: "0 {minute} {hour} {day} {month} ? {year}"
   ├── jobType: "dubbo"
   ├── interface: "com.rrsjk.light.service.dispatch.LightAuditDispatchJobService"
   ├── method: "dispatchBacklogByConfigId"
   ├── param: configId
   └── 通过 JobService.insertJob(job) 注册
4. 到指定时间，CBS定时任务引擎触发 → dispatchBacklogByConfigId(configId)
5. 验证配置是否仍为ENABLED状态 → 执行对应审核类型的派单
6. 执行完毕后，JobService自动删除一次性任务（delete=1配置）
```

### Cron 格式示例
配置: 2026-05-18 10:00
Cron: `0 0 10 18 5 ? 2026`

**特点**: 这是**一次性定时任务**，只执行一次。

### 删除流程

```
1. 终止配置 → terminateConfig.do → deleteBacklogDispatchJob(configId)
2. 删除配置 → deleteConfig.do → deleteBacklogDispatchJob(configId)
3. 调用 jobService.deleteByJobName("非工作日派单补跑-{configId}")
```

## 六、补跑执行流程

`dispatchBacklogByConfigId(configId)`:
```
1. 根据configId查询配置
2. 校验: 配置存在且状态=ENABLED
3. 根据auditType路由到对应派单方法:
   ├── PLAN_AUDIT → doDispatchOrderForPlanAudit()
   ├── TECH_CHECK → doDispatchOrderForTechCheck()
   └── WAIT_FIRST_AUDIT → doDispatchOrderForWaitFirstAudit()
4. 执行派单逻辑（与日常定时任务相同）
```

**与日常定时任务的区别**: 补跑不执行 `isHoliday()` 校验，即使当天是工作日也会执行。这是因为补跑配置可能在非休息日添加（如下班后的额外派单时段）。

## 七、派单执行核心逻辑

`dispatchOrder(request, skipTimeCheck)`:

1. **Redis分布式锁**: `LOCK_KEY + stationId + ":" + auditType`，防止同一电站同一审核类型并发派单
2. **时间校验** (skipTimeCheck=false时): 调用 `isWithinDispatchTime()` 判断当前时间是否允许派单
3. **重复派单检查**: 如果存在 `dealFlag=WAIT` 的派单日志，拒绝再次派单
4. **有效审核人员**: 查询启用的审核人员列表，为空则派单失败
5. **派单类型确定**:
   - 首派: 无历史派单记录
   - 转派: 上次派单超时未处理
   - 积压补派: 通过配置补跑
6. **审核员轮询选择**: 使用 `RoundRobinQueueRedisUtil` 实现审核员轮询分配
7. **创建派单日志** + **更新审核表**: 事务性写入

## 八、关键数据表

| 表名 | 用途 |
|---|---|
| `light_audit_dispatch_log` | 派单日志记录 |
| `light_audit_dispatch_time_config` | 非工作日派单时间配置 |
| `light_station_audit` | 电站审核表（派单信息写入此表） |
| `light_tech_auditor` | 审核人员配置 |

## 九、派单3.1 近期更新 (2026-05-18)
**来源**: TAEI-3078, `rrsjk-light-service` + `rrsjk-admin-web` (解钦, 2026-05-11~05-14)

### 9.1 完工审核状态字段判断规则修复
- commit `57f24cf` (2026-05-12): 修复状态字段的判断规则
- commit `f865fbc` (2026-05-13): 解决完工审核时校验电站信息时抛出异常导致捕获异常时 dbStation 为空的问题

### 9.2 配置数据校验优化
- commit `e36835c` (2026-05-11): 新增和更新配置时校验数据只看启用的记录，忽略已删除/禁用的
- commit `0fe1534` (2026-05-12): 创建定时任务时使用 configId 而非其他标识

### 9.3 电站完工终止时删除定时任务
- commit `3e64946` (2026-05-11): `station-complete-stop` 功能 — 电站终止时自动删除关联的定时任务
- **关键方法**: 在 `CompleteConfirmServiceImpl` 中，当电站被终止时调用 `jobService.deleteByJobName()` 清理一次性cron任务

### 9.4 审核问题修复
- commit `ff4e6cd` (2026-05-14): 修复审核问题 — 具体涉及审核状态值拼写错误（姜传德同步修复，commit `06e1916c`/`f81eac4f`）

### 9.5 审核状态枚举修正
**来源**: `rrsjk-admin-web` (姜传德, 2026-05-15)
- `06e1916c`: 修复审核状态值拼写错误
- `f81eac4f`: 修正审核状态枚举值和显示逻辑

### 9.6 非工作日派单时间配置 — 时间段重叠校验 (2026-05-09)
**来源**: `rrsjk-light-service` (解钦, commit: b06f33b, 2026-05-09)
**代码明确证明**

**新增功能**: 新增/更新非工作日派单时间配置时，校验同一日期同一审核类型的已有配置是否存在时间段重叠。

**重叠判断逻辑**:
```java
// 两个区间 [s1, e1) 和 [s2, e2) 满足 s1 < e2 && s2 < e1 即为重叠
LocalTime newStart = LocalTime.parse(startTime);
LocalTime newEnd = LocalTime.parse(endTime);
LocalTime existStart = LocalTime.parse(existing.getStartTime());
LocalTime existEnd = LocalTime.parse(existing.getEndTime());
if (newStart.isBefore(existEnd) && existStart.isBefore(newEnd)) {
    throw new AssertException("时间段存在重叠，请调整后重试");
}
```

**新增方法**: `validateTimeOverlap(excludeId, configDate, auditType, startTime, endTime)`
- 新增配置: `excludeId=null`，检查所有已有配置
- 更新配置: `excludeId=config.getId()`，排除自身后检查

**影响范围**: `LightAuditDispatchTimeConfigServiceImpl.addConfig()` 和 `updateConfig()` 均增加了 `validateTimeOverlap` 调用。

### 9.7 派单时间范围判断逻辑重构 (2026-05-09)
**来源**: `rrsjk-light-service` (解钦, commit: b06f33b, 2026-05-09)
**代码明确证明**

**旧逻辑**:
```java
// 非工作日查配置，工作日直接用固定时间(08:30~17:30/18:00)
if (isHoliday(dispatchAt)) {
    return lightAuditDispatchTimeConfigService.isWithinNonWorkdayDispatchTime(auditType);
}
return !currentTime.isBefore(startTime) && currentTime.isBefore(endTime);
```

**新逻辑**:
```java
// 休息日：只查配置表
if (isHoliday(dispatchAt)) {
    return lightAuditDispatchTimeConfigService.isWithinNonWorkdayDispatchTime(auditType);
}
// 工作日：先检查正常工作时间
if (!currentTime.isBefore(startTime) && currentTime.isBefore(endTime)) {
    return true;
}
// 工作日非正常工作时间：也查配置表（下班后额外派单时间段）
return lightAuditDispatchTimeConfigService.isWithinNonWorkdayDispatchTime(auditType);
```

**关键区别**: 工作日的非正常工作时间（如晚上/清晨）也可以配置额外派单时间段，不再直接拒绝。

