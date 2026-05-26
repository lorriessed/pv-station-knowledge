# 电站收入上收限制 — 8种资方模式完整分析 (TAEI-3085)

**来源**: `rrsjk-light-service` → 8个 `StationIncomeModeCheckStrategy` + 8个 `StationIncomeHandleStrategy` (解钦, 2026-05-12~05-16)

## 一、整体架构

两层策略 + 一层工厂：

```
Consumer Layer (消费者)
    ↓
Mode Check Layer (校验层) — 判断电站属于哪种资方模式
    ↓ 8个策略自动注入
Handle Layer (处理层) — 实际执行收入/冲销/重上
    ↓ 通过 Factory 获取对应策略
Factory Layer — Map<StationModeEnum, StationIncomeHandleStrategy>
```

## 二、各模式对应的收入表

| 模式 | 枚举 | 资方 | 收入结算表 |
|------|------|------|-----------|
| YX | YX | 越秀 | `LightStationYuexiuSettle` |
| ZH | ZH | 中核 | `LightZhSettle` + `LightZhSettleQueue` |
| PY | PY | 浦银 | `PuYinTradeIncomeSettle` |
| ZY | ZY | 招银 | `ZhaoYinTradeIncomeSettle` |
| HD | HD | 华电 | `LightHdIncome` |
| HR | HR | 华融 | `HuaRongTradeIncomeSettle` |
| ZHY | ZHY | 中银 | `ZhongYinTradeIncomeSettle` |
| FUND | FUND | 基金 | `LightFundSettle` |

## 三、8种资方 SAP 记账参数

| 资方 | ywms（业务模式） | jylx（交易类型） | bukrs（公司代码） | 科目数 | 特殊说明 |
|------|-----------------|-----------------|------------------|-------|---------|
| **越秀** | A55（上收入）/ A40（冲销） | A6 | 1PG0 | 1种 | 冲销用A40，重上时用A55 |
| **中核** | A41（服务安装）+ A42（设备材料）+ W25（服务费） | — | — | 3种 | 每科目独立冲销 |
| **浦银** | A55 | A6 | 1PG0 | 1种 | 有结算队列 |
| **招银** | A55 | A6 | 1PG0 | 1种 | getLatestIncomeTime 返回 null |
| **华电** | A41（安装）+ A42（设备）+ W25（服务） | A6 | 动态 | 3种 | 动态利润中心，税率不同（A42=1.13, A41=1.09, W25=1.06） |
| **华融** | A55 | A6 | 1PG0 | 1种 | 单科目统一收入 |
| **中银** | A55 | A6 | 1PG0 | 1种 | 单科目统一收入 |
| **基金** | A40（安装收入）+ A42（设备收入） | A6 | 动态 | 2种 | 安装1.09税率，设备1.13税率，动态利润中心 |

## 四、收入校验逻辑

**校验接口** (`StationIncomeModeCheckStrategy`):
- `checkIfExists(stationCode)` → 调用对应 DAO 的 `existsByStationCode()`
- `getLatestIncomeTime(stationCode)` → 调用对应 DAO 的 `getLatestIncomeTime()`

**模式判定**: 遍历8个策略，取收入时间最新的模式作为当前模式。
**⚠️ 招银特殊**: Zy 的 `getLatestIncomeTime()` 返回 null，永远不会被判定为"当前模式"。

## 五、收入导入/冲销/重上流程

### 冲销状态机
```
查询结算表记录 → 判断结算状态
  ├── WAIT_CONFIRM/CONFIRM → 跳过
  ├── FINISHED/PART_FINISHED/WAIT_REVERSE → 冲销SAP凭证 → 更新状态为REVERSED → 移动Redis单号
  ├── REVERSED → 跳过
  └── 其他 → 抛异常
```

### 重上状态机
```
查询结算表记录 → 判断结算状态
  ├── WAIT_CONFIRM/CONFIRM/WAIT_REV → 抛异常
  ├── FINISHED/PART_FINISHED → 跳过
  ├── REVERSED → 创建新结算 → 调用SAP记账 → 更新状态为FINISHED
  └── 其他 → 抛异常
```

## 六、关键设计特点
1. **Redis 单号递进**: 每次冲销后移动到下一级，确保重上使用不同 bid
2. **冲销次数编码**: A-Z 前缀，支持最多 26 次重上
3. **部分冲销容错**: 中核/华电/基金的多科目模式，只冲销未冲销的凭证
4. **事务保护**: 重上流程在事务中执行

## 七、新增：收入模式策略工厂 (2026-05-14)

**来源**: TAEI-3089/TAEI-3085, `StationIncomeModeCheckStrategyFactory.java` (commit: 70186ba0, 解钦, 2026-05-14)
**代码明确证明**: `rrsjk-light-service/rrsjk-light-impl/src/main/java/com/rrsjk/light/service/impl/income/factory/mode/StationIncomeModeCheckStrategyFactory.java`

### 工厂类功能
```java
@Component
public class StationIncomeModeCheckStrategyFactory {
    // Spring 自动注入所有 StationIncomeModeCheckStrategy
    private final Map<StationModeEnum, StationIncomeModeCheckStrategy> strategies;
    
    // 批量查询电站在其他模式下的收入冲突
    Map<String, StationModeEnum> batchFindConflictModes(
        Collection<String> stationCodes, StationModeEnum currentMode);
    
    // 根据电站编码获取到上收入的电站模式（取最近收入时间对应的模式）
    StationModeEnum getModeByLatestIncomeTime(String stationCode);
}
```

### 重构内容
- 从逐个遍历8个策略 → 工厂类统一管理，通过 `StationModeEnum` 索引
- `batchFindConflictModes`: 批量检查电站在不同模式下是否有收入冲突（排除自身模式）
- `getModeByLatestIncomeTime`: 取最近收入时间对应的模式，替代原来的遍历逻辑

## 八、基金安装业务科目修正 (2026-05-16)

**来源**: TAEI-3089, commit: d73aba1d (解钦, 2026-05-16)
**代码明确证明**: `FundStationIncomeHandleStrategy.java` 中 `FUND_INSTALL_YWMS` 从 `"A40"` 改为 `"A41"`

- **旧值**: `FUND_INSTALL_YWMS = "A40"` (安装收入)
- **新值**: `FUND_INSTALL_YWMS = "A41"` (服务安装)
- **原因**: 基金安装业务科目需要从A40调整为A41，与SAP记账科目对齐

## 九、收入上收限制重构 — 回购电站拦截 + 错误提示优化 (TAEI-3085, 2026-05-14)

**来源**: `rrsjk-light-service` (解钦, commits: c06ff46, 70186ba, 0404906, 2026-05-14)
**代码明确证明**

### 9.1 回购电站状态检查优化

**变更**: 从直接检查 `LightStation.Status.REPURCHASE` 改为通过 `LightStationRepurchaseDao.findActiveRepurchaseStationCodes()` 批量查询活跃回购电站。

**涉及文件**:
- `HuaRongTradeIncomeSettleServiceImpl.java` — 华融收入导入
- `LightFundSettleServiceImpl.java` — 基金收入导入
- `LightHdIncomeServiceImpl.java` — 户用收入导入
- `PuYinSettleQueueJobServiceImpl.java` — 普yin结算
- `ZhaoYinTradeIncomeSettleServiceImpl.java` — 招银收入导入
- `ZhongYinTradeIncomeSettleServiceImpl.java` — 中银收入导入

**旧逻辑**:
```java
Assert.isTrue(!lightStation.getStatus().equals(LightStation.Status.REPURCHASE.name()),
    stationCode + "的电站已被回购, 不能导入");
```

**新逻辑**:
```java
Set<String> repurchaseStationCodes = lightStationRepurchaseDao.findActiveRepurchaseStationCodes(stationCodeList);
Assert.isTrue(!repurchaseStationCodes.contains(stationCode),
    "电站编码" + stationCode + "为回购中电站不可交易，请检查数据后导入");
```

**关键区别**: 旧逻辑只检查电站表状态字段是否为 REPURCHASE，新逻辑通过独立的回购记录表 (`light_station_repurchase`) 查询"活跃回购中"的电站，覆盖更精确。

### 9.2 收入冲突错误提示优化

**旧错误信息**: `"以下电站已在其他模式存在收入记录，不能重复导入：XXX在【XX模式】"`
**新错误信息**: `"电站编码XXX已在【XX模式】模式下存在收入记录，不能重复导入"` — 更明确指向具体电站和模式。

### 9.3 电站状态校验精简

- 移除了独立的 `REPURCHASE` 状态检查（由 `findActiveRepurchaseStationCodes` 替代）
- 保留了 `DISABLE`（无效电站）检查
- 保留了 `SUSPENDING`（暂停状态，仅基金模式跳过）检查

### 9.4 新增 DAO 方法

```java
// LightStationRepurchaseDao.java
public Set<String> findActiveRepurchaseStationCodes(Collection<String> stationCodes) {
    return new HashSet<>(this.getSqlSession()
        .selectList(getNamespacePrefix() + "findActiveRepurchaseStationCodes", stationCodes));
}
```

