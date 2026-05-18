# Hermes Gateway 运维手册

## 常用只读检查

```bash
systemctl status hermes-gateway --no-pager -l
/root/.hermes/scripts/hermes_health_check.py
tail -120 /root/.hermes/logs/errors.log
tail -120 /root/.hermes/logs/gateway.log
```

## 进程原则

- gateway 只允许由 `hermes-gateway.service` 常驻管理。
- 不长期保留手工执行的 `hermes gateway run`。
- MCP 子进程应挂在当前 gateway 进程下。
- 如果出现 PPID=1 的 MCP 进程，说明旧 gateway 没有完整回收，可执行清理脚本。

## 清理 MCP 孤儿进程

```bash
/root/.hermes/scripts/cleanup_orphan_mcp.sh
```

## 重启 gateway

重启属于写操作，执行前需要确认。

```bash
systemctl restart hermes-gateway
sleep 8
systemctl status hermes-gateway --no-pager -l
/root/.hermes/scripts/hermes_health_check.py
```
