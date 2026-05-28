# PVS 全量代码通读报告 — 2026-05-28

## 概况

| 指标 | 值 |
|---|---|
| 通读轮次 | 第 15 轮 |
| 本次通读仓库 | 5 个 |
| 已通读总数 | 105/122 (86%) |
| 待通读 | 17 个 |
| 新增 domain 文件 | 1 个 |

## 本次通读仓库清单

| # | 仓库 | 类型 | 业务文件数 | 核心职责 |
|---|---|---|---|---|
| 1 | DB_TOOL | SQL 脚本集 | 0 | 生产问题排查 SQL 集合(服务费/浦银账单/对赌等) |
| 2 | Inverter_recognition | Flask AI 服务 | 0 | 逆变器识别号 OCR 识别(Qwen2.5-VL) |
| 3 | card_extraction | Flask AI 服务 | 0 | 银行卡号 OCR 识别(Qwen2.5-VL) |
| 4 | infomation_iextraction | Flask AI 服务 | 0 | 购售电合同信息提取(DeepSeek-R1) |
| 5 | main_contract_extraction | Flask AI 服务 | 0 | 主合同 PDF 信息提取(Qwen2.5-VL OCR + DeepSeek-R1 两阶段) |

## 核心发现

### AI 提取服务架构 (4 个 Flask 微服务)

本次通读首次完整发现了 PVS 业务配套的 AI 信息提取服务体系：

1. **逆变器识别号提取** (`Inverter_recognition:2601`) — 电站安装时拍摄逆变器铭牌照片，AI 自动提取序列号
2. **银行卡号提取** (`card_extraction`) — 业主/售电方银行卡照片自动识别
3. **购售电合同信息提取** (`infomation_iextraction:8765`) — 文本合同提取地址、装机容量、售电方、购电方
4. **主合同 PDF 提取** (`main_contract_extraction`) — 两阶段流程：Qwen2.5-VL OCR → DeepSeek-R1 文档理解

**技术栈**: Python 3.6.8 + Flask + Qwen2.5-VL-7B-Instruct (视觉) + DeepSeek-R1-Distill-Qwen-32B (理解)
**部署**: Docker 容器，阿里云 PAI-EAS + 海尔 mGallery

### DB_TOOL — 生产排查工具

包含 8+ 个 SQL 脚本，覆盖服务费生成、浦银账单导出、对赌、并网时效等生产问题排查场景。SQL 注释中明确引用了 Java 代码位置 `LightUseModel.java:543`。

## 知识库更新

| 操作 | 文件 | 说明 |
|---|---|---|
| **新增** | `domains/ai-extraction-services.md` | AI 提取服务完整文档(架构/接口/模型/关联) |
| **更新** | `modules/repositories.md` | 5 个仓库标记为已通读，计数 100→105 |
| **更新** | `state/full_sweep.json` | completed_repos 新增 5 个，轮次 14→15 |
| **更新** | `index.md` | 进度更新为 105/122 |

## 待通读仓库 (17 个)

剩余仓库主要为: Flutter 打包壳、iOS/Android 原生项目、H5 模板等低业务价值仓库。
