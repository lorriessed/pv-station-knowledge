# PVS 全量代码通读报告 — 2026-06-18 (第35轮)

## 通读概况

| 指标 | 数值 |
|---|---|
| 仓库总数 | 138 |
| 本轮通读 | 5 个 |
| 累计已通读 | 127/138 |
| 从未通读 | 11 个 |

## 本轮通读仓库分析

### 1. app_aiwork_flutter (原 greenergy-management)
- **业务职责**: 海尔绿能通 — 分中心管理端 Flutter APP
- **最后提交**: 2026-06-05 (褚福贺: iconfont 动态图标系统)
- **核心发现**:
  - 仓库已从 `greenergy-management` 重命名为 `app_aiwork_flutter`
  - 后端 API: `apitest.nahuipv.com` (测试) / `api.nahuipv.com` (生产)
  - OAuth2 登录: `POST /oauth2/oauth/login` (clientId=nh_app)
  - 版本检查: `GET /merchant/light/lightVersionInformation/list.do` → 调用 rrsjk-merchant-web
  - 路由: privacy → login → home/workspace/profile (3-tab BottomNav)
  - 预留路由: analytics, check-in, warning, project-funnel, acceptance, station, watermark-camera, webview
  - 已集成: ARMS 监控 (release模式)、GoRouter、Riverpod 状态管理、Retrofit API、iconfont 动态图标系统、应用自更新
  - 人脸登录页: `face_login_page.dart` (已创建但未接入主路由)
  - **与已有 KB 关系**: 2026-06-05 已通读为 `greenergy-management`，本次为仓库重命名后的重扫，无新增业务逻辑
- **业务价值**: 高 — 分中心管理人员移动端入口

### 2. autotest
- **业务职责**: 自动化测试配置
- **最后提交**: 2026-06-18 (haier47: Dockerfile + .dockerignore)
- **核心发现**: 仅含 `config.yaml` — 测试环境 API 地址 (`cbstest.rrsjk.com`) + 本地 MySQL/PostgreSQL 占位配置
- **业务价值**: **极低** — 测试基础设施，无业务逻辑

### 3. date_extraction
- **业务职责**: PDF 文档日期提取 AI 服务
- **最后提交**: 2025-09-15 (maverick100)
- **核心发现**:
  - Flask 微服务，使用 PyMuPDF 将 PDF 逐页转 PNG (300 DPI) → Base64
  - 功能: `pdf_url_to_png_base64()` — 下载 PDF → 转图片 → 供下游 AI 模型识别
  - 非直接 AI 推理服务，是 AI 提取 pipeline 的预处理环节
- **业务价值**: 低 — 辅助工具，最后更新 2025-09

### 4. degree_measurement
- **业务职责**: 光伏板倾角 AI 测量服务
- **最后提交**: 2025-07-16 (maverick100)
- **核心发现**:
  - Flask 微服务，端点: `POST /api/angle`
  - 模型: Qwen2.5-VL-7B-Instruct (via mgallery.haier.net)
  - 输入: 照片 URL → 预处理 (缩放到 1024×1024 → Base64) → AI 分析倾角
  - 重试 5 次机制
- **业务价值**: 低 — 电站设计验证辅助工具，最后更新 2025-07

### 5. haier-energy-job-admin
- **业务职责**: 分布式任务调度管理台 (Snail Job 品牌定制版)
- **最后提交**: 2026-06-09 (解钦: 登录页 CSS 优化)
- **核心发现**:
  - 开源 Snail Job 前端 → 替换品牌为 "HaierEnergy"
  - Vue 3.5 + Naive UI + Vite 7 + pnpm monorepo
  - 功能: 工作流管理、批量任务、通知配置 (邮件/企微/钉钉/飞书/Webhook)
  - 2026-06 活跃: 解钦做品牌定制 (登录页重设计、Snail Job→HaierEnergy)
- **业务价值**: 中 — PVS 定时任务运维入口，不含光伏业务逻辑

## 知识库更新

| 文件 | 操作 | 内容 |
|---|---|---|
| `domains/ai-extraction-services.md` | 追加 | 新增 date_extraction + degree_measurement 服务文档 + 端口汇总表 |
| `domains/mobile-app-architecture.md` | 修改 | 标注 app_aiwork_flutter 为 greenergy-management 的重命名 |
| `domains/system-infra-service.md` | 追加 | 新增 HaierEnergy Job Admin (Snail Job 定制版) 文档 |
| `state/full_sweep.json` | 更新 | 127/138 完成，第35轮 |

## 关键发现

1. **app_aiwork_flutter = greenergy-management 重命名**: 同一仓库换了名字，KB 已有完整文档，本次无新增业务逻辑
2. **AI 辅助工具矩阵扩充**: date_extraction (PDF预处理) + degree_measurement (倾角测量) 加入已有的 AI 提取服务家族，总计 11 个 Python Flask AI 服务
3. **Snail Job 品牌定制**: PVS 团队正在将开源 Snail Job 定制为内部 "HaierEnergy Job Admin"，2026-06 活跃开发中
4. **autotest 仓库**: 今日有提交 (Dockerfile)，但仅含测试配置，无业务价值
