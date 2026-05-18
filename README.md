# PVS 业务知识库

该目录服务于 219 服务器上的 Hermes 业务知识机器人。

## 目录

- `daily/`：每日扫描原始结论和摘要。
- `modules/`：模块职责、代码入口、关键 Service。
- `domains/`：业务域稳定知识。
- `data/`：表、字段、枚举、数据库实例。
- `source-map/`：页面、接口、Controller、Service、Mapper、Job 对照。
- `decisions/`：重要结论和历史决策。
- `runbooks/`：排查手册和运维说明。

## 使用原则

- 短期变化写入 `daily/`。
- 可复用结论沉淀到长期目录。
- 所有结论尽量带来源，避免只保留模型推断。
- 涉及生产排查只记录只读证据和结论。
