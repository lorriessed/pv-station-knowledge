# 金蝶/SAP 双系统记账架构

> 来源: TAEI-3005 【股转】金蝶总账接口开发，马斌(mabin)，2026-04-15 ~ 05-16，30+ commits

## 核心结论

**不是"SAP切换金蝶"，而是"双系统并行"**。根据项目公司的 `stockTransfer` 字段路由：
- `stockTransfer == 1`（股转公司）→ **金蝶**
- `stockTransfer != 1`（乐道/统众等其他公司）→ **原SAP**

## 路由逻辑

**入口**: `LightProjectElectricOrderServiceImpl.java` (rrsjk-light-service)

```java
Integer stockTransfer = lightCompanyInfo.getStockTransfer();
if (!Objects.equals(stockTransfer, 1)) {
    // 走 SAP 原逻辑
    SapRecord sapRecord = sapRecordService.getSapRecordByBidAndYWS(ywms, orderNo);
    syncFinanceToSapService.reverseFinanceToSap(...);
} else {
    // 股转公司 → 金蝶逻辑
    KingDieSapRecord sapRecord = jinDieSapRecordService.getSapRecordByBidAndYwms(orderNo, ywms);
    jinDieSapRecordService.reverseFinanceToSap(...);
}
```

## 金蝶模块结构（rrsjk-finance-service）

| 文件路径 | 职责 |
|---|---|
| `rrsjk-finance-api/.../entity/KingDieSapRecord.java` | 金蝶记账主记录实体 |
| `rrsjk-finance-api/.../entity/KingDieSapItemRecord.java` | 金蝶记账明细实体 |
| `rrsjk-finance-api/.../service/JinDieSapRecordService.java` | **Dubbo接口**：记账/冲销/查询 |
| `rrsjk-finance-impl/.../service/impl/JinDieSapRecordServiceImpl.java` | Dubbo实现 |
| `rrsjk-finance-impl/.../component/collection/JinDieSapClient.java` | 记账逻辑封装（按H01/H05/H06业务模式） |
| `rrsjk-finance-impl/.../model/JinDieSyncFinanceModel.java` | 同步核心：生成rowId、调HTTP、落库 |
| `rrsjk-finance-impl/.../model/JinSapClientModel.java` | HTTP调用层：`${kingdie.saveVoucherUrl}` |
| `rrsjk-finance-impl/.../model/XJinDieModel.java` | 获取token + 调用金蝶API |
| `rrsjk-finance-impl/.../dao/KingDieSapRecordDao.java` | DAO |
| `rrsjk-finance-impl/resources/mybatis/mapper/sap/KingDieSapRecordMapper.xml` | MyBatis映射 |

## 业务模式（YWMS）覆盖

| 代码 | 含义 | 税率 | 场景 |
|---|---|---|---|
| **H01** | 股转公司电费收益收入记账 | 收入÷1.13 | 非乐道/非统众 |
| **H05** | 股转公司电费收益成本记账 | 收入÷1.13, 成本÷1.06 | rentAmount场景 |
| **H06** | 盈利模式电费收益成本记账 | 收入÷1.13, 成本×1.058÷1.06 | rentAmount×1.058 |
| **A02** | 股转公司电费月汇总收款 | - | 确认收款场景 |

**对比SAP**: SAP支持10+种模式（A40/A41/A42/A43/A44/A50/A51/A55/W25等），金蝶目前仅覆盖股转公司的4种。

## 完整业务链

```
CBS/admin-web 前端
  └─ lightProjectElectricOrderList.ftl → 显示"金蝶记账失败"状态

rrsjk-light-service（业务层，Dubbo消费方）
  ├─ LightProjectElectricOrderServiceImpl → 收款/红冲/历史重传调用金蝶Dubbo
  ├─ ProjectElectricOrderSapModel → stockTransElectricIncomeToJinDie()
  ├─ LightProjectElectricInvoiceReverseRecordServiceImpl → 发票冲销
  └─ service.xml → <dubbo:reference id="JinDieSapRecordService" .../>

rrsjk-finance-service（财务层，Dubbo提供方）
  ├─ JinDieSapRecordServiceImpl → Dubbo接口实现
  ├─ JinDieSapClient → stockTransferElectricOrderIncome() 按YWMS封装
  ├─ JinDieSyncFinanceModel → syncFinance(): 生成rowId → HTTP → 落库
  ├─ JinSapClientModel → HTTP POST ${kingdie.saveVoucherUrl}
  └─ KingDieSapRecordDao/Mapper → 持久化

rrsjk-light-report-service（报表层）
  └─ EstimateToSapModel → 暂估记账调用金蝶（股转公司场景，3处）
```

## 数据库表结构

### king_die_sap_record（主表）
| 字段 | 类型/说明 |
|---|---|
| sid | 主键ID |
| row_id | 业务单据号，格式: `R` + ywms + 左补零18位bid |
| bid | 业务主键（与ywms联合主键） |
| ywms | 业务模式（H01/H05/H06/A02） |
| jylx | 交易类型 |
| bukrs | 公司代码，默认"4110" |
| budat | 过账日期 |
| bktxt | 凭证抬头文本 |
| xblnr | 参考凭证编号 |
| waers | 货币码，默认"CNY" |
| gjahr | 会计年度 |
| belnr | 凭证号（金蝶返回） |
| vouched_at | 凭证日期 |
| flag | S成功/E错误/W警告/I信息/A中断 |
| message | 消息文本 |
| request_json | 请求报文 |
| response_json | 响应报文 |
| created_at/updated_at | 时间戳 |

### king_die_sap_record_item（明细表）
| 字段 | 说明 |
|---|---|
| row_id | 关联主表 |
| zhc | 账号 |
| kunnr/lifnr | 客户编码/供应商编码 |
| name/city | 名称/城市 |
| prctr | 利润中心 |
| kostl | 成本中心 |
| dmbtr | 含税收入 |
| dmbtr1 | 金额2 |
| dmbtr2 | 税金 |
| dmbtr3 | 成本金额 |
| dmbtr4 | 收款金额 |
| xref3 | 参考字段3 |
| sgtxt | 项目文本 |
| zuonr | 分配编号 |
| kunnr1/lifnr1 | 客户/供应商编码2 |
| zpl/zpp/zwlh/zxw/zxwzsx | 扩展字段 |
| yhzh | 银行账号 |

## 金蝶与SAP对比

| 维度 | SAP | 金蝶 |
|---|---|---|
| 支持模式数 | 10+ 种 | 4 种（H01/H05/H06/A02） |
| 覆盖公司 | 乐道/统众等 | 仅股转公司（stockTransfer=1） |
| 税率 | 各科目不同（1.13/1.09/1.06） | 统一 1.13 / 1.06 |
| 冲销前缀 | rowId 本身 | `C_` + rowId |
| 公司代码 | 动态获取 | 默认 4110 |

## Git 提交时间线（马斌，2026-04-15 ~ 05-16，30+ commits）

```
04-15  集成金蝶SAP系统（初始版本）
04-16  多次重构：移除冗余字段、接口定型、修复重复数据
04-17  添加测试用例
04-21  实现股转公司金蝶集成（核心功能）
04-22  修复配置引用、日志记录
04-23  修复401错误+token缓存线程安全
04-27~30  优化交易类型、添加A02收款记账
05-08  实现发票红冲金蝶集成（1次revert后重新提交）
05-09  配置金蝶生产参数
05-12  ❌ 误删金蝶SAP服务 → 05-13 Revert
05-13~16  修复历史记录处理、前端状态显示、放开限制
```

## 风险经验

1. **误删回滚**：05-12 commit `refactor(project): 移除金蝶SAP服务相关功能`，05-13 Revert
2. **线程安全**：token获取需双重检查，04-23专门修复（commit `ab06aa7b`）
3. **rowId 生成**: `R` + ywms + 左补零18位bid，冲销前缀 `C_`
4. **幂等**: `syncFinance` 先查已有记录（bid+ywms），有belnr直接返回
5. **历史数据重传**：05-14有专门commit处理5月份历史已收款收入重传金蝶
6. **并发控制**（2026-05-19新增）：`syncFinance()` 使用 Redis 分布式锁 `jinDie:sync:finance:{bid}:{ywms}`（1分钟超时），防止同一业务单据并发同步。锁冲突时标记 flag=E 直接返回

## 金蝶凭证过账功能 (TAEI-3157, 代码明确证明, 2026-05-27)
**来源**: `rrsjk-finance-service` → `JinDieSyncFinanceModel.java`, `JinSapClientModel.java`, `application-dev/prod.yml` (commits: f4bf864/9b888ae/beadf50/c233685/e7e2c37, mabin, branch: origin/20250525-jindieRepeatFix + origin/20260527-jindieFix)
**关联需求**: TAEI-3157 金蝶冲销接口优化
- **核心变更**: 冲销前先调用金蝶凭证过账接口，过账成功才执行冲销
  - `JinSapClientModel.postingVoucherForReverse(rowId, sapRecord)`: 新增方法，调用 `/xfd6/gl/gl_voucher/PostingVoucher`
  - `JinDieSyncFinanceModel`: 修改冲销逻辑，`postResult = postingVoucherForReverse()` → true 才调 `syncFinanceToSap()`
  - **配置**: `kingdie.postVoucherUrl` 新增（dev: `https://jintai.test.kdgalaxy.com/kapi/v2/xfd6/gl/gl_voucher/PostingVoucher`）
- **错误处理增强**:
  - 限制金蝶SAP同步消息长度防止数据库字段溢出（9b888ae4）
  - 解决金蝶SAP同步中的重复校验和错误处理问题（beadf501）
  - 优化金蝶sap同步财务记账接口异常处理（c233685b, e7e2c376）
  - 解决金蝶SAP客户端BUKRS字段映射问题（e44ebe80，7CQ0→9002）
- **关联变更**:
  - `rrsjk-light-service` → `LightProjectElectricOrderServiceImpl`: 放开发票金蝶冲销（4ee999f3, mabin）
  - `rrsjk-light-service` → `CmChangeServiceImpl`: 修复冲销逻辑中的状态判断错误（587197f8, sunzn）
