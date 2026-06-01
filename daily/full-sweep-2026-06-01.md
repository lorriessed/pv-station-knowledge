# 全量通读报告 2026-06-01

## 统计
- **通读日期**: 2026-06-01 22:00
- **本轮第 17 轮**
- **本次通读 2 个仓库**: usher-rpc, usher-stream
- **总进度**: 107/122 (87.7%)
- **从未通读仓库**: 15 个

## 仓库分析

### usher-rpc — 自定义轻量级 RPC 框架（非 Dubbo）
- **业务价值**: ⭐ 基础设施层 — 无 PVS 业务逻辑
- **技术栈**: Java 8 + Netty 4.1.54 + Nacos 2.4.3
- **核心功能**: 
  - 自定义二进制 RPC 协议（非 HTTP/gRPC/Dubbo）
  - Nacos 服务注册/发现
  - 6 种负载均衡策略（IP_HASH/MANUAL/RANDOM/POLLING/LEAST_ACTIVE/FASTEST）
  - SPI 扩展机制（11 个扩展点）
  - 超时/重试/熔断支持
  - Spring Boot 自动配置集成
- **关键发现**: PVS 系统同时使用 Dubbo 和 usher-rpc 两套 RPC 框架
- **产出**: 新建 `domains/usher-rpc-framework.md`

### usher-stream — Java 8 Stream 扩展工具库
- **业务价值**: ⭐ 极低 — 仅 pom.xml，添加 takeWhile 等 Java 8 缺失的 Stream 能力
- **无业务逻辑**

## 知识库更新
| 文件 | 操作 | 说明 |
|------|------|------|
| `domains/usher-rpc-framework.md` | **新建** | usher-rpc 框架完整文档（协议、枚举、配置、调用链、SPI） |
| `modules/repositories.md` | 更新 | 从 full_sweep.json 重新生成，107/122 标记 ✅ |
| `state/full_sweep.json` | 更新 | completed_repos 新增 usher-rpc, usher-stream |

## 剩余 15 个未通读仓库
- 5 个 Python AI 提取服务: main_contract_whole_extraction, poc_extraction_without_pdf, purchase_electricity_contract, rent_extraction, rent_extraction_guding
- 1 个父 POM: rrs-parent
- 4 个 CBS 认证/管理: rrsjk-admin-auth-server, rrsjk-admin-authz-service, rrsjk-admin-bff, rrsjk-admin-biff
- 1 个前端: rrsjk-admin-web-next
- 4 个 usher 框架: usher-common, usher-dependencies, usher-groovy-flex, usher-protofuse
