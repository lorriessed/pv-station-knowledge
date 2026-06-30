# PVS 全量代码通读报告 — 2026-06-30

## 本轮概要

- **轮次**: 第 44 轮（重扫）
- **通读仓库**: usher-rpc, usher-stream, rrsjk-mobile-h5, rrsjk-mobile-web, rrsjk-oauth2-web
- **策略**: Delta discovery — 对比已有 KB 覆盖，仅补充遗漏

## 仓库分析

### 1. usher-rpc — 外围框架（跳过）
- **最后提交**: 2026-01-25（仅版本号更新）
- **KB 覆盖**: `domains/usher-rpc-framework.md` 18 处引用，`source-map/java-symbols.md` 202 条
- **结论**: 开源 RPC 框架（Netty + Nacos），无 PVS 业务逻辑。KB 已完整覆盖。**零提交跳过**。

### 2. usher-stream — 外围工具库（跳过）
- **最后提交**: 2026-01-25（仅版本号更新）
- **KB 覆盖**: 仅 `source-map/java-symbols.md` 10 条
- **结论**: Java 8 Stream 扩展工具库（takeWhile 等），无 PVS 业务逻辑。**零提交跳过**。

### 3. rrsjk-mobile-h5 — 乐农商城 H5 前端（新增分类）
- **最后提交**: 2024-10-09（停滞 8+ 个月）
- **技术栈**: Vue.js（137 个 Vue 文件），包名 `RRSJK-MOBILE-H5`
- **KB 覆盖**: 此前零覆盖
- **发现**: 这是乐农商城的移动端 H5 配套前端，与 `rrsjk-mobile-web` 后端配合。注意与 PVS 光伏的 `nahui-pv.mobile-h5`（React 18）是**完全不同的项目**。
- **动作**: 在 `domains/web-and-additional-services.md` 的 rrsjk-mobile-web 章节新增关联前端仓库说明。

### 4. rrsjk-mobile-web — 移动端 Web/商城（已全覆盖）
- **最后提交**: 2026-06-11（bug fix: 图片上传创建者信息 getName→getUsername）
- **KB 覆盖**: `source-map/controllers.md` 92 条路由，`domains/web-and-additional-services.md` 完整章节
- **结论**: 近期仅有 bug 修复，无新业务逻辑。KB 已完整覆盖。**快速收敛**。

### 5. rrsjk-oauth2-web — OAuth2 统一认证（补充遗漏）
- **最后提交**: 2026-05-25（SM2 国密 + 中银租赁登录）
- **KB 覆盖**: `domains/remaining-services-and-frontends.md` 已有完整章节（~80 行）
- **发现遗漏**:
  1. `/oauth/assertLease/login` 端点未在 Controller 表格中列出
  2. SM2 国密解密流程（从 oauth2_client 表取公私钥 → 解密密码 → client_credentials 授权）未记录
- **动作**: 
  - 在 Controller 表格新增 `/oauth/assertLease/login` 行
  - 在核心业务逻辑新增"中银租赁 SM2 登录"段落，详述 SM2 解密 + client_credentials 流程

## 知识库更新汇总

| 文件 | 更新类型 | 内容 |
|------|----------|------|
| `domains/remaining-services-and-frontends.md` | patch | +1 行 Controller 表格（assertLease 端点）；+1 段核心业务逻辑（SM2 中银租赁登录流程） |
| `domains/web-and-additional-services.md` | patch | +1 段关联前端仓库说明（rrsjk-mobile-h5 分类） |
| `state/full_sweep.json` | update | 5 个仓库 repo_last_sweep 时间戳更新 |

## 统计

- 通读仓库: 5/138
- 零提交跳过: 2 (usher-rpc, usher-stream)
- 已全覆盖快速收敛: 1 (rrsjk-mobile-web)
- 新增分类: 1 (rrsjk-mobile-h5)
- 补充遗漏: 1 (rrsjk-oauth2-web SM2/中银登录细节)
- KB 文件更新: 2 个 domain 文件
- sweep_round: 44（未递增，本轮为增量补充）
