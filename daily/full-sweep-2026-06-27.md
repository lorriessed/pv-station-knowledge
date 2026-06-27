# PVS 全量代码通读报告 — 2026-06-27 (第42轮)

## 概要

| 项目 | 值 |
|---|---|
| 通读日期 | 2026-06-27 |
| 本轮次 | 第42轮 (re-sweep, sweep_round 保持 42) |
| 通读仓库数 | 5 |
| 有新增提交 | 0 |
| 知识库更新 | 无 |
| 策略 | 零提交跳过优化 + KB 已全覆盖快速收敛 |

## 通读仓库详情

### 1. main_contract_whole_extraction
- **类型**: Python Flask AI 微服务 — 主合同(PDF)完整信息提取(丙方版)
- **最后提交**: 2025-12-16 (更新 main_contract_whole_extraction.py)
- **自上次通读以来新增提交**: 0
- **KB 覆盖**: `domains/ai-extraction-services.md` §5 (通读日期 2026-05-29) 已完整覆盖
- **处理**: ⏭️ 跳过（零提交，KB 已全覆盖）

### 2. poc_extraction_without_pdf
- **类型**: Python Flask AI 微服务 — 房产证/产权证明图片识别
- **最后提交**: 2026-05-26 (更新 poc_extraction_without_pdf.py)
- **自上次通读以来新增提交**: 0 (最后提交早于 KB 文档化日期 2026-05-29)
- **KB 覆盖**: `domains/ai-extraction-services.md` §6 已完整覆盖
- **处理**: ⏭️ 跳过（零提交，KB 已全覆盖）

### 3. purchase_electricity_contract
- **类型**: Python Flask AI 微服务 — 购售电合同信息提取(PDF增强版，三模型协作)
- **最后提交**: 2025-12-29 (更新 purchase_electricity_contract.py)
- **自上次通读以来新增提交**: 0
- **KB 覆盖**: `domains/ai-extraction-services.md` §7 已完整覆盖
- **处理**: ⏭️ 跳过（零提交，KB 已全覆盖）

### 4. rent_extraction
- **类型**: Python Flask AI 微服务 — 租赁协议文本信息提取(轻量版)
- **最后提交**: 2025-07-15 (更新 rent_extraction.py)
- **自上次通读以来新增提交**: 0
- **KB 覆盖**: `domains/ai-extraction-services.md` §8 已完整覆盖
- **处理**: ⏭️ 跳过（零提交，KB 已全覆盖）

### 5. rent_extraction_guding
- **类型**: Python Flask AI 微服务 — 固定租赁协议信息提取(丙方版)
- **最后提交**: 2025-07-15 (更新 rent_extraction_guding.py)
- **自上次通读以来新增提交**: 0
- **KB 覆盖**: `domains/ai-extraction-services.md` §9 已完整覆盖
- **处理**: ⏭️ 跳过（零提交，KB 已全覆盖）

## 知识库变更

**本轮无知识库更新。**

所有 5 个仓库自上次通读以来均无新增提交，且已有完整 KB 覆盖（`domains/ai-extraction-services.md` 430行，§5-§9 详细记录了每个服务的接口/模型/输入输出/业务流程）。按照"零提交跳过优化"策略，直接更新时间戳，不读取源文件，不写入 KB。

## sweep_round 修正

脚本自动递增 sweep_round 到 44（经 42→43→44），但第42轮(6/26)和第43轮(6/27)均为零知识产出，按规范 sweep_round 不应递增。已手动修正回 42（最后一次有知识产出的轮次为第41轮，2026-06-25）。

## 全量通读进度

- 仓库总数: 138
- 已通读: 138/138 (100%)
- 当前轮次: 第42轮 (re-sweep)
- 所有仓库均已覆盖，后续均为重扫（delta discovery）
- 连续零提交轮次: 2 (6/26, 6/27)
