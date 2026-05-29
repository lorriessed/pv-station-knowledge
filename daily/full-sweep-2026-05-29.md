# PVS 全量代码通读报告 — 2026-05-29

## 通读概况

| 指标 | 值 |
|---|---|
| 通读轮次 | 第 15 轮 |
| 通读日期 | 2026-05-29 |
| 本次通读仓库 | 5 个 |
| 仓库类型 | Python Flask AI 提取服务 |
| 总仓库数 | 122 |
| 已通读 | 105/122 (86%) |
| 待通读 | 17 个 |

## 本次通读仓库清单

| 仓库 | HEAD | 最后提交 | 业务文件数 | 类型 |
|---|---|---|---|---|
| main_contract_whole_extraction | 85303dd | 2025-12-16 (张青山) | 1 | Flask AI |
| poc_extraction_without_pdf | dac5949 | 2026-05-26 (maverick100) | 1 | Flask AI |
| purchase_electricity_contract | 9f61e84 | 2025-12-29 (张青山) | 1 | Flask AI |
| rent_extraction | 9b9dcf8 | 2025-07-15 (maverick100) | 1 | Flask AI |
| rent_extraction_guding | da3e6c6 | 2025-07-15 (maverick100) | 1 | Flask AI |

## 仓库分析

### 1. main_contract_whole_extraction — 主合同(PDF)完整信息提取(丙方版)
- **端口**: 14322
- **接口**: `POST /api/rent_extraction`
- **输入**: PDF URL
- **流程**: PDF → pdf2image → Qwen2.5-VL OCR → DeepSeek-R1 提取 → 返回 {stationName, companyName, address}
- **特点**: 提取丙方(非乙方)，提取"租赁屋顶或场地位于"后的地址
- **纠错**: {"昕异顺": "昕昇顺"}
- **与 main_contract_extraction 关系**: 功能高度相似，但 party 角色不同（丙方 vs 乙方），可能用于三方合同场景

### 2. poc_extraction_without_pdf — 房产证/产权证明图片识别
- **端口**: 2605
- **接口**: `POST /api/POC_extraction`
- **输入**: 图片 URL
- **流程**: 图片下载 → resize 2048x2048 → Base64 → Qwen2.5-VL 识别 → 返回 {message, name, id, add}
- **两任务**: 判断是否为房产证(con标签 1/0) + 提取姓名/身份证号/地址
- **特殊**: 拒绝 PDF 输入；身份证号必须 18 位；地址中文括号被移除
- **业务场景**: 电站建设前产权验证

### 3. purchase_electricity_contract — 购售电合同信息提取(PDF增强版)
- **端口**: 14329
- **接口**: `POST /api/purchase_electricity`
- **输入**: PDF URL
- **这是最复杂的 AI 提取服务**: 三模型协作(Qwen2.5-VL + Qwen3-32B + DeepSeek-R1)，处理 5+ 种合同模板格式
- **流程**: PDF OCR → 提取买卖方 → 判断合同类型(contract_index=0~5) → 分支提取地址和容量
- **容量处理**: 直流侧优先；兆瓦→kW换算
- **纠错字典**: 3条(昕异顺→昕昇顺, 海翔顺→海耀顺, 武店镇前郭村→武店镇前郢村)
- **使用两个 mGallery API Key**: Qwen2.5-VL 和 Qwen3-32B 使用不同 key

### 4. rent_extraction — 租赁协议文本信息提取(轻量版)
- **端口**: 4321
- **接口**: `POST /api/rent_extraction`
- **输入**: 纯文本(UTF-8)
- **模型**: DeepSeek-R1-Distill-Qwen-32B (PAI-EAS)
- **提取**: 甲方→stationName, 乙方→companyName, 甲方地址→address
- **特点**: 不处理 PDF，直接接收纯文本

### 5. rent_extraction_guding — 固定租赁协议信息提取(丙方版)
- **端口**: 4322
- **接口**: `POST /api/rent_extraction_firm`
- **输入**: 纯文本(UTF-8)
- **模型**: DeepSeek-R1-Distill-Qwen-32B (PAI-EAS)
- **提取**: 甲方→stationName, 丙方→companyName, 租赁场地地址→address
- **特点**: 提取丙方(非乙方)，三方合同场景

## AI 提取服务全景(9个服务)

本次通读后，已完整记录 9 个 AI 提取微服务：

| # | 服务名 | 端口 | 接口 | 输入 | 输出 | 模型 |
|---|---|---|---|---|---|---|
| 1 | Inverter_recognition | 2601 | /api/Inverter_rec | 图片URL | 逆变器序列号 | Qwen2.5-VL |
| 2 | card_extraction | ? | /api/Card_extraction | 图片URL | 银行卡号 | Qwen2.5-VL |
| 3 | infomation_iextraction | 8765 | /api/info | 合同文本 | add/capacity/sale/buy | DeepSeek-R1 |
| 4 | main_contract_extraction | ? | /api/rent_extraction | PDF URL | stationName+... | Qwen2.5-VL+DeepSeek |
| 5 | main_contract_whole_extraction | 14322 | /api/rent_extraction | PDF URL | stationName/companyName/address | Qwen2.5-VL+DeepSeek |
| 6 | poc_extraction_without_pdf | 2605 | /api/POC_extraction | 图片URL | name/id/add | Qwen2.5-VL |
| 7 | purchase_electricity_contract | 14329 | /api/purchase_electricity | PDF URL | buy/sale/add/capacity | 三模型 |
| 8 | rent_extraction | 4321 | /api/rent_extraction | 纯文本 | stationName/companyName/address | DeepSeek-R1 |
| 9 | rent_extraction_guding | 4322 | /api/rent_extraction_firm | 纯文本 | stationName/companyName/address | DeepSeek-R1 |

## 知识库更新

| 操作 | 文件 | 变更摘要 |
|---|---|---|
| 更新 | domains/ai-extraction-services.md | 新增 5 个 AI 提取服务完整文档 + 端口汇总表(9个服务) |
| 更新 | modules/repositories.md | 从 full_sweep.json 重新生成(122 仓库, 105 已通读) |
| 更新 | state/full_sweep.json | 更新 last_sweep_at 时间戳 |
| 更新 | index.md | 更新通读日期和本轮通读仓库列表 |

## 待通读仓库(17个)

- rrsjk-admin-auth-server, rrsjk-admin-authz-service, rrsjk-admin-bff, rrsjk-admin-biff
- rrsjk-admin-web-next, rrs-parent
- usher-common, usher-dependencies, usher-groovy-flex, usher-protofuse, usher-rpc, usher-stream
- （以及部分已标记为"变更"但尚未通读的仓库）
