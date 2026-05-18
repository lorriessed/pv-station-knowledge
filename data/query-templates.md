# PVS 生产库查询模板

> 适用 MCP: `pv_mysql_prod` (`rrsjk_light`) 与 `electric_pv_mysql_prod` (`rrsjk_light_data`)。所有查询必须只读。

## 使用规则

1. 先确认用户给出的检索条件：电站编码、手机号、服务商编码、订单号、月份、需求编号。
2. 查询前先 `LIMIT`，避免大表全扫。
3. 不直接输出身份证、手机号全量等敏感信息；必要时脱敏。
4. 只查询必要字段，不使用 `SELECT *`。
5. 所有 SQL 只允许 `SELECT` 或 `SHOW`。

## 电站基础信息

按电站编码：

```sql
SELECT id, station_code, name, status, business_status, contract_status,
       sp_id, sp_code, mode, special_flag, project_company_code,
       province_name, city_name, region_name, created_at, updated_at
FROM light_station
WHERE station_code = ?
LIMIT 5;
```

按业主手机号后四位辅助定位：

```sql
SELECT id, station_code, name, status, phone, sp_code, created_at
FROM light_station
WHERE phone LIKE ?
ORDER BY id DESC
LIMIT 20;
```

## 电站审核与操作日志

```sql
SELECT id, station_id, station_code, audit_status, audit_type,
       audit_result, audit_remark, created_by, created_at
FROM light_station_audit
WHERE station_code = ?
ORDER BY id DESC
LIMIT 50;
```

```sql
SELECT id, station_id, station_code, operate_type, operate_content,
       created_by, created_at
FROM light_station_operate_log
WHERE station_code = ?
ORDER BY id DESC
LIMIT 80;
```

## 服务商

```sql
SELECT id, sp_code, sp_name, status, sub_center_code, server_all,
       created_at, updated_at
FROM light_service_provider
WHERE sp_code = ? OR sp_name LIKE ?
LIMIT 20;
```

## 订单与辅材额度

```sql
SELECT id, order_no, sp_code, order_status, pay_status,
       total_amount, created_at, updated_at
FROM light_sp_order
WHERE order_no = ? OR sp_code = ?
ORDER BY id DESC
LIMIT 50;
```

```sql
SELECT id, sp_code, flow_type, amount, before_amount, after_amount,
       business_no, remark, created_at
FROM light_auxiliary_material_quota_flow
WHERE sp_code = ?
ORDER BY id DESC
LIMIT 100;
```

## SAP 记录

```sql
SELECT id, ywms, source_no, belnr, flag, msg, created_at, updated_at
FROM sap_record
WHERE source_no = ? OR belnr = ?
ORDER BY id DESC
LIMIT 50;
```

## 租金与结算

```sql
SELECT id, station_code, rent_month, rent_amount, status,
       pay_status, created_at, updated_at
FROM light_rent
WHERE station_code = ?
ORDER BY rent_month DESC
LIMIT 60;
```

```sql
SELECT id, station_code, settle_month, settle_status, total_amount,
       created_at, updated_at
FROM light_station_settle_sum
WHERE station_code = ?
ORDER BY settle_month DESC
LIMIT 60;
```

## 逆变器数据

在 `electric_pv_mysql_prod` 上查询：

```sql
SELECT id, station_code, inveter_sn, record_time, today_power_generation,
       total_power_generation, created_at
FROM light_inveter_record
WHERE station_code = ?
ORDER BY record_time DESC
LIMIT 100;
```

```sql
SELECT id, inveter_sn, station_code, status, fault_code, alarm_code,
       record_time, created_at
FROM light_inveter_data
WHERE inveter_sn = ?
ORDER BY record_time DESC
LIMIT 100;
```

## 报表/大屏排查

先定位报表表名，再按业务主键和月份查询。若不确定表名，先查 `data/sql-table-refs.md` 和 Mapper。

```sql
SHOW TABLES LIKE '%report%';
```

```sql
SHOW COLUMNS FROM table_name;
```
