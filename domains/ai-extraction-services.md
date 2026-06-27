# AI 提取服务 (Flask 微服务)

**代码明确证明** | 通读日期: 2026-05-28

## 概述

PVS 光伏业务配套有 4 个 Python Flask 微服务，专门用于 **AI 图像识别和文档信息提取**。这些服务通过调用阿里云 PAI-EAS 和海尔 mGallery 的大模型 API，对电站完工/并网过程中的图片、合同 PDF 等进行自动化信息提取，替代人工录入。

**技术栈**: Python 3.6.8 + Flask + requests + PIL/pdf2image
**部署方式**: Docker 容器，阿里云容器镜像仓库 (registry.cn-qingdao.aliyuncs.com)
**大模型**: Qwen2.5-VL-7B-Instruct (视觉识别)、DeepSeek-R1-Distill-Qwen-32B (文档理解)

---

## 1. Inverter_recognition — 逆变器识别号提取

**来源**: `Inverter_recognition/Inverter_Rec.py` + `Dockerfile`

| 项目 | 值 |
|---|---|
| 端口 | 2601 |
| 接口 | `POST /api/Inverter_rec` |
| 输入 | JSON `{"data": "<图片URL>"}` |
| 输出 | LLM 返回文本中的 `<Num>` 标签包裹的逆变器识别号 |
| 模型 | Qwen2.5-VL-7B-Instruct (mgallery.haier.net) |
| 重试策略 | 最多 5 次 |

**业务场景**: 电站安装时拍摄逆变器产品铭牌照片，AI 自动提取紧靠产品铭牌下方条形码的数字串（逆变器序列号），用于设备台账录入。

**流程**:
```
图片URL → 下载+Resize(2048x2048) → Base64编码 → Qwen2.5-VL API → 解析<Num>标签 → 返回识别号
```

**Prompt 核心指令**: "逆变器识别号是紧靠着产品铭牌下方的条形码，一般是在条形码上方或者下方的那一串数字"

---

## 2. card_extraction — 银行卡号提取

**来源**: `card_extraction/Card_extraction.py` + `Dockerfile`

| 项目 | 值 |
|---|---|
| 端口 | (Dockerfile 未显式 EXPOSE，与 Inverter_recognition 类似) |
| 接口 | `POST /api/Card_extraction` |
| 输入 | JSON `{"data": "<图片URL>"}` |
| 输出 | 图片中的银行卡号 |
| 模型 | Qwen2.5-VL-7B-Instruct (mgallery.haier.net) |
| 重试策略 | 最多 5 次 |

**业务场景**: 提取业主/售电方提供的银行卡照片中的卡号，用于电费/租金收款账户绑定。

**流程**: 与 Inverter_recognition 完全相同的架构，仅 Prompt 不同 — "帮我提取图片中的银行卡号"

---

## 3. infomation_iextraction — 购售电合同信息提取

**来源**: `infomation_iextraction/info_extraction.py` + `Dockerfile`

| 项目 | 值 |
|---|---|
| 端口 | 8765 |
| 接口 | `POST /api/info` |
| 输入 | 合同文档纯文本 (UTF-8) |
| 输出 | JSON `{add, capacity, sale, buy}` |
| 模型 | DeepSeek-R1-Distill-Qwen-32B (PAI-EAS) |

**提取字段**:
| 字段 | 标签 | 提取规则 |
|---|---|---|
| 地址 | `<Add>` | 优先"鉴于："后地址 → 其次"发电地址" → 为空 |
| 总装机容量 | `<Capacity>` | 优先"鉴于："后容量 → 其次"并网总容量"/"合同约定容量" → 提取纯数字 |
| 售电方公司 | `<Sale>` | 同义词: 售电人、乙方 |
| 购电方公司 | `<Buy>` | 同义词: 购电人、甲方 |

**业务场景**: 非自然人分布式光伏发电项目购售电合同的信息自动化提取。替代人工阅读合同并录入系统。

**调用示例合同**: `SGTYIT/22-GS-008非自然人分布式光伏发电项目购售电合同`

---

## 4. main_contract_extraction — 主合同(PDF)租金信息提取

**来源**: `main_contract_extraction/main_contract_extraction.py` + `Dockerfile`

| 项目 | 值 |
|---|---|
| 端口 | (Dockerfile 定义) |
| 接口 | `POST /api/rent_extraction` |
| 输入 | JSON `{"pdf_url": "<PDF文件URL>"}` |
| 输出 | JSON `{stationName, ...}` |
| 模型 | 两阶段: Qwen2.5-VL-7B-Instruct (OCR) → DeepSeek-R1-Distill-Qwen-32B (提取) |

**两阶段流程**:
```
1. PDF → pdf2image 转图片(最多6页)
   → Qwen2.5-VL OCR 提取每页文字 → 拼接全文
2. 全文 → DeepSeek-R1 提取:
   - 甲方姓名 (Buy/电站名称)
   - 乙方公司名称 (Sale)
   - 甲方地址 (Add)
```

**纠错规则**: 内置字典 `{"昕异顺": "昕昇顺"}` — 修正 OCR 识别错误。

---

## 5. DB_TOOL — 数据库排查工具集

**来源**: `DB_TOOL/dev/` + `DB_TOOL/prod/`

**不是服务**，是一个 SQL 脚本集合，用于生产环境常见问题排查。

### prod/ 下的 SQL 脚本

| 文件名 | 用途 |
|---|---|
| `后50%服务费 or 前50%服务费 or 辅料费.sql` | 查询服务费生成状态、对账单、质保金明细 |
| `安装提升(对赌).sql` | 对赌相关查询 |
| `并网时效.sql` | 并网时效统计 |
| `新商.sql` | 新商户相关查询 |
| `月度规模.sql` | 月度规模统计 |
| `浦银账单导出.sql` | SPDB(浦发银行)资方账单导出 |
| `生产问题查询.sql` | 生产问题排查 |
| `营销激励查询.sql` | 营销激励统计 |

### 关键表引用 (从 SQL 中提取)

| 表名 | 用途 |
|---|---|
| `light_finance_record` | 财务记录，service_purchase_status 字段 |
| `rrsjk_finance.sap_purchase_record` | SAP 采购记录 |
| `rrsjk_finance.deposit_record` | 押金/质保金明细 |
| `light_cost_account` | 成本核算表，need_half_service 字段 |
| `light_project_electric_order_owner` | 电站收益单(资方维度) |
| `light_project_electric_order` | 电站收益单 |
| `light_station_white_list` | 电站白名单，first_part 字段 |
| `gf_apply_detail` | 广发申请明细 |

**代码明确证明** — SQL 注释中引用了 Java 代码位置: `com/rrsjk/light/service/model/LightUseModel.java:543` → `LightUseModel#invoke`，即安装服务费(前半部分)的 SAP 总账记账和采购单创建逻辑。

---

## 架构图

```
┌─────────────────────────────────────────────────────────────┐
│  前端/H5 (电站安装/并网流程)                                   │
│  ↓ 上传图片/合同                                               │
│  ┌──────────────────┐  ┌──────────────────┐                 │
│  │ Inverter_rec     │  │ card_extraction  │                 │
│  │ :2601            │  │                  │                 │
│  │ 逆变器识别        │  │ 银行卡号识别      │                 │
│  └────────┬─────────┘  └────────┬─────────┘                 │
│           │                      │                            │
│           ▼                      ▼                            │
│  ┌──────────────────┐  ┌──────────────────┐                 │
│  │ infomation_iext  │  │ main_contract    │                 │
│  │ :8765            │  │ extraction       │                 │
│  │ 合同文本信息提取  │  │ PDF合同信息提取   │                 │
│  └────────┬─────────┘  └────────┬─────────┘                 │
│           │                      │                            │
└───────────┼──────────────────────┼────────────────────────────┘
            │                      │
            ▼                      ▼
  ┌─────────────────────────────────────┐
  │  mgallery.haier.net                 │
  │  Qwen2.5-VL-7B-Instruct (视觉模型)   │
  │  ↓                                  │
  │  PAI-EAS (DeepSeek-R1-Distill-32B)  │
  │  文档理解/信息提取                    │
  └─────────────────────────────────────┘
```

## 外部服务依赖

| 服务 | URL | 用途 |
|---|---|---|
| 海尔 mGallery | `https://mgallery.haier.net/v1/chat/completions` | Qwen2.5-VL-7B-Instruct 视觉识别 |
| 阿里云 PAI-EAS | `http://1896283349800821.cn-beijing.pai-eas.aliyuncs.com/api/predict/haier_energy_deepseek/v1/chat/completions` | DeepSeek-R1-Distill-Qwen-32B 文档理解 |

## 5. main_contract_whole_extraction — 主合同(PDF)完整信息提取(丙方版)

**来源**: `main_contract_whole_extraction/main_contract_whole_extraction.py`
**通读日期**: 2026-05-29

| 项目 | 值 |
|---|---|
| 端口 | 14322 |
| 接口 | `POST /api/rent_extraction` |
| 输入 | JSON `{"pdf_url": "<PDF文件URL>"}` |
| 输出 | JSON `{stationName, companyName, address}` |
| 模型 | 两阶段: Qwen2.5-VL-7B-Instruct (OCR) → DeepSeek-R1-Distill-Qwen-32B (提取) |

**与 main_contract_extraction 的区别**: 提取的是**丙方**公司名称（而非乙方），且提取"租赁屋顶或场地位于"之后、"屋顶或场地面积"之前的租赁场地地址。

**两阶段流程**:
```
1. PDF → pdf2image 转图片 → Qwen2.5-VL OCR 提取每页文字 → 拼接全文
2. 全文 → DeepSeek-R1 提取:
   - 甲方姓名 → <Buy> → stationName (电站名称)
   - 丙方公司名称 → <Sale> → companyName
   - 租赁场地地址 → <Add> → address
```

**纠错规则**: 内置字典 `{"昕异顺": "昕昇顺"}` — 修正 OCR 识别错误。

---

## 6. poc_extraction_without_pdf — 房产证/产权证明图片识别

**来源**: `poc_extraction_without_pdf/poc_extraction_without_pdf.py`
**通读日期**: 2026-05-29

| 项目 | 值 |
|---|---|
| 端口 | 2605 |
| 接口 | `POST /api/POC_extraction` |
| 输入 | JSON `{"data": "<图片URL>", "name": "..."}` |
| 输出 | JSON `{message, name, id, add}` |
| 模型 | Qwen2.5-VL-7B-Instruct (mgallery.haier.net) |
| 重试策略 | 最多 5 次 |

**业务场景**: 上传房产证/房屋产权证明图片，AI 自动判断是否为房产证，并提取房主姓名、身份证号、地址。用于电站建设前的产权验证。

**两任务 Prompt**:
1. 判断是否为房产证 → `<con>` 标签: 1=是, 0=否
2. 提取姓名(`<Name>`)、身份证号(`<ID>`)、地址(`<ADD>`)

**特殊处理**:
- 如果输入是 PDF 文件（后缀 `.pdf`），直接返回空结果（不处理 PDF）
- 身份证号必须恰好 18 位才返回，否则返回空
- 地址中的中文括号及括号内容会被 `remove_chinese_parentheses_regex()` 移除

---

## 7. purchase_electricity_contract — 购售电合同信息提取(PDF增强版)

**来源**: `purchase_electricity_contract/purchase_electricity_contract.py`
**通读日期**: 2026-05-29

| 项目 | 值 |
|---|---|
| 端口 | 14329 |
| 接口 | `POST /api/purchase_electricity` |
| 输入 | JSON `{"pdf_url": "<PDF文件URL>", "name": "..."}` |
| 输出 | JSON `{buy, sale, add, capacity, contract_index, error_signer}` |
| 模型 | 三模型协作: Qwen2.5-VL-7B (OCR) + Qwen3-32B (提取) + DeepSeek-R1 (判断) |

**这是最复杂的 AI 提取服务**，处理多种购售电合同模板格式。

**多阶段流程**:
```
1. PDF → pdf2image 转图片(最多10页, quality=100)
2. Qwen2.5-VL OCR 逐页提取文字 → 拼接全文
3. Qwen3-32B 提取购电方(甲方)和售电方(乙方)
4. 根据合同格式判断类型(contract_index=1~5)，分支提取地址和容量:
   - contract_index=1: "鉴于"后有多处装机地址 → DeepSeek判断 → 提取全部地址+容量
   - contract_index=1(单地址): "鉴于"后单地址 → Qwen3 提取
   - contract_index=2: "乙方发电与用电项目位于同一地址"后提取
   - contract_index=3: "发电地址"+"并网总容量"后提取
   - contract_index=4: "并网容量和并网方式"后提取
   - contract_index=5: "发电地址和发电容量"后提取
   - contract_index=0: 兜底，全文搜索
5. 容量单位换算: 兆瓦/MW → ×1000 转为 kW
6. 直流侧容量优先: 同时存在直流/交流容量时取直流侧
```

**纠错字典** (3条):
```python
{"昕异顺": "昕昇顺", "海翔顺": "海耀顺", "武店镇前郭村": "武店镇前郢村"}
```

**三模型分工**:
- `chat_picture()`: Qwen2.5-VL-7B, mgallery.haier.net, OCR 逐页文字提取
- `chat_qwen()`: Qwen3-32B, mgallery.haier.net, 业务字段提取（使用不同 API key）
- `chat_ds()`: DeepSeek-R1-Distill-Qwen-32B, PAI-EAS, 多地址判断

**⚠️ 使用两个不同的 mGallery API Key**:
- Qwen2.5-VL: `sk-Fr9...E1B7`
- Qwen3-32B: `sk-5mO...60B3`

---

## 8. rent_extraction — 租赁协议文本信息提取(轻量版)

**来源**: `rent_extraction/rent_extraction.py`
**通读日期**: 2026-05-29

| 项目 | 值 |
|---|---|
| 端口 | 4321 |
| 接口 | `POST /api/rent_extraction` |
| 输入 | 纯文本 (UTF-8, 直接 POST body) |
| 输出 | JSON `{stationName, companyName, address}` |
| 模型 | DeepSeek-R1-Distill-Qwen-32B (PAI-EAS) |

**与 main_contract_extraction 的区别**: 不处理 PDF，直接接收纯文本输入。用于已从其他渠道获取合同文本的场景。

**提取字段**: 甲方(`<Buy>`→stationName)、乙方(`<Sale>`→companyName)、甲方地址(`<Add>`→address)

---

## 9. rent_extraction_guding — 固定租赁协议信息提取(丙方版)

**来源**: `rent_extraction_guding/rent_extraction_guding.py`
**通读日期**: 2026-05-29

| 项目 | 值 |
|---|---|
| 端口 | 4322 |
| 接口 | `POST /api/rent_extraction_firm` |
| 输入 | 纯文本 (UTF-8, 直接 POST body) |
| 输出 | JSON `{stationName, companyName, address}` |
| 模型 | DeepSeek-R1-Distill-Qwen-32B (PAI-EAS) |

**与 rent_extraction 的区别**: 提取**丙方**（而非乙方），且提取"租赁屋顶或场地位于"之后、"屋顶或场地面积"之前的租赁场地地址。适用于三方租赁协议（甲方-业主、乙方-承租人、丙方-资方/合作方）。

## 房产证OCR识别 (TAEI-2728, 代码明确证明, 2026-05-26~27)
**来源**: `rrsjk-light-service` + `rrsjk-admin-web` (mabin/马斌, branch: origin/20260518-fangchanzhengOCR)
**关联需求**: TAEI-2728 【AI】AI识别房产证
**参与人**: 杨越越(assigned), 魏秋阳, 陈国栋, 马斌
- **生产URL配置**: `LightUseModel.java` 新增房产证OCR识别生产URL (`435fc658`)
- **前端图片显示修复**: `rrsjk-admin-web` 修复房产证状态图片显示问题 (`033634af/d43338f3`)
- **业务场景**: 电站安装/并网过程中拍摄房产证照片，AI自动识别房产证信息
- **状态**: 测试完成 (2026-05-21)

---

## PDF 日期提取服务 (date_extraction, 代码明确证明, 2026-06-18 通读)
**来源**: `date_extraction/date_extraction.py` (最后提交: 2025-09-15, maverick100)
**业务场景**: 从 PDF 文档中提取日期信息（如合同签署日期、并网日期等）
**技术实现**:
- Flask 微服务，使用 PyMuPDF (fitz) 将 PDF 每页转为 PNG (300 DPI)
- 输出 Base64 编码的 PNG 图片列表
- 功能：`pdf_url_to_png_base64(pdf_url, dpi=300)` — 下载 PDF → 逐页转 PNG → Base64 编码
- 原始代码中有注释掉的"仅提取首页和最后一页"逻辑，当前版本改为提取所有页
**部署**: Docker 容器
**状态**: 低频使用，最后代码更新 2025-09

## 光伏板倾角测量服务 (degree_measurement, 代码明确证明, 2026-06-18 通读)
**来源**: `degree_measurement/angle_measurement.py` (最后提交: 2025-07-16, maverick100)
**业务场景**: 通过照片 AI 识别光伏板安装倾角，用于电站设计验证
**技术实现**:
- Flask 微服务，端点: `POST /api/angle`
- 输入: JSON `{"data": "图片URL"}`
- 模型: `Qwen2.5-VL-7B-Instruct` (via `mgallery.haier.net/v1/chat/completions`)
- 图片预处理: 从 URL 下载 → PIL 缩放到 1024×1024 → Base64 编码
- 重试机制: 最多重试 5 次
- Prompt: 要求 AI 分析光伏板倾角角度
**依赖**: 海尔 mGallery AI 网关 (`mgallery.haier.net`)
**状态**: 低频使用，最后代码更新 2025-07

---

## AI 提取服务端口汇总

| 服务 | 端口 | 接口 | 输入类型 | 输出字段 | 模型 |
|---|---|---|---|---|---|
| Inverter_recognition | 2601 | `/api/Inverter_rec` | 图片URL | 逆变器序列号 | Qwen2.5-VL |
| card_extraction | ? | `/api/Card_extraction` | 图片URL | 银行卡号 | Qwen2.5-VL |
| infomation_iextraction | 8765 | `/api/info` | 合同文本 | add/capacity/sale/buy | DeepSeek-R1 |
| main_contract_extraction | ? | `/api/rent_extraction` | PDF URL | stationName+... | Qwen2.5-VL+DeepSeek |
| **main_contract_whole_extraction** | **14322** | `/api/rent_extraction` | PDF URL | stationName/companyName/address | Qwen2.5-VL+DeepSeek |
| **poc_extraction_without_pdf** | **2605** | `/api/POC_extraction` | 图片URL | name/id/add | Qwen2.5-VL |
| **purchase_electricity_contract** | **14329** | `/api/purchase_electricity` | PDF URL | buy/sale/add/capacity | 三模型协作 |
| **rent_extraction** | **4321** | `/api/rent_extraction` | 纯文本 | stationName/companyName/address | DeepSeek-R1 |
| **rent_extraction_guding** | **4322** | `/api/rent_extraction_firm` | 纯文本 | stationName/companyName/address | DeepSeek-R1 |
| **date_extraction** | **?** | PDF→PNG转换 | PDF URL | Base64 PNG列表 | PyMuPDF (非AI) |
| **degree_measurement** | **?** | `/api/angle` | 图片URL | 光伏板倾角 | Qwen2.5-VL-7B |
| **recipt_extraction** | **2664** | `/api/Recipt_extracion` | 图片URL | 电费表格(户号/金额/税额/电量/日期) | qwen3-vl-30b |
| **recipt_extraction_pdf** | **2606** | `/api/Recipt_extracion_pdf` | PDF URL | 电费表格(同上,多页PDF) | qwen3-vl-30b |

## 与核心 Java 微服务的关联

这些 Flask 服务是**被调用方**，核心 Java 微服务 (rrsjk-light-service 等) 通过 HTTP 调用这些 AI 接口完成信息提取后，将结果写入业务数据库。

**关联 Java 代码位置**: `com.rrsjk.light.service.model.LightUseModel#invoke` (LightUseModel.java:543) — 安装服务费 SAP 记账逻辑，DB_TOOL SQL 中明确引用。

---

## 11. recipt_extraction — 电费收据图片表格提取 (代码明确证明, 2026-06-19 通读)
**来源**: `recipt_extraction/Recipt_extraction.py` + `Dockerfile` (最后提交: 2026-06-17, maverick100)

| 项目 | 值 |
|---|---|
| 端口 | 2664 |
| 接口 | `POST /api/Recipt_extracion` |
| 输入 | JSON `{"data": "<图片URL>", "number": "发电户号", "value": "含税金额", "tax": "税额", "pro": "电量", "startDate": "所属年月", "endDate": ""}` |
| 输出 | `{"total": <含税金额合计>, "res": [{目标列1: 值, ...}, ...]}` |
| 模型 | **qwen3-vl-30b-a3b-instruct** (升级自 Qwen2.5-VL) |
| 图片预处理 | 从 URL 下载 → 原尺寸(未缩放) → Base64 PNG |
| 技术栈 | Python 3.6.8 + Flask + PIL + requests |
| 部署 | Docker, registry.cn-qingdao.aliyuncs.com/amd_64/python:3.6.8-2 |

**业务场景**: 从电费结算单**图片**中自动提取表格数据。支持多种电费单据格式:
- 电网公司电费账单 (发电户号、含税金额、税额、电量、所属年月)
- 客户编号电费单 (客户编号、含税电费、税额、结算电量、抄表日期)
- 电厂编号结算单 (电厂编号、电费、税费、上网电量、结算月份)
- 交易对象购电单 (电厂编号、结算含税电费小计、税费、结算电量合计、购电月份)

**Prompt 核心**: "你是一个图片表格信息提取大师...识别表格结构，找到列名为上述内容的列...提取该列除表头外所有行的单元格内容...日期只提取年和月，以YYYY-MM形式返回...合计行所有信息都不需要提取"

**⚠️ 注意**: 使用 `eval(request.data)` 解析输入 (非 json.loads)，存在安全风险

---

## 12. recipt_extraction_pdf — 电费收据PDF表格提取 (代码明确证明, 2026-06-19 通读)
**来源**: `recipt_extraction_pdf/Recipt_extraction_pdf.py` + `Dockerfile` (最后提交: 2026-06-04, haier47)

| 项目 | 值 |
|---|---|
| 端口 | 2606 |
| 接口 | `POST /api/Recipt_extracion_pdf` |
| 输入 | JSON `{"data": "<PDF URL>", "value": "含税金额", "number": "发电户号", ...}` |
| 输出 | `{"total": <合计>, "res": [{目标列1: 值, ...}, ...]}` |
| 模型 | **qwen3-vl-30b-a3b-instruct** |
| PDF处理 | PyMuPDF(fitz) → 每页转 PNG (500 DPI) → Base64 → 逐页送 AI |
| 技术栈 | Python 3.6.8 + Flask + PyMuPDF + requests |
| 部署 | Docker, registry.cn-qingdao.aliyuncs.com/amd_64/python:3.6.8-2 |

**与 recipt_extraction 的区别**:
- 输入是 **PDF** 而非图片
- 使用 PyMuPDF 将 PDF **每一页**都转为 500 DPI PNG，逐页送 AI 提取
- 所有页的提取结果合并到一个列表返回
- 合计值跨页累加

**业务场景**: 处理多页 PDF 格式的电费结算单，如电网公司出具的月度/年度电费明细。

---

## 13. 智能体Token统计系统 (Agent Token) — AI模型用量追踪 (代码明确证明, 2026-06-27)

**来源**: `rrsjk-light-service` → `com.rrsjk.light.service.agent` 包 (baoxin+mabin, commits: 59213056→0c7ec4c8, 2026-06-25~27); `rrsjk-merchant-web` → `AgentTokenController.java` (commit: 4a124096, mabin, 2026-06-27)

### 架构概览

```
rrsjk-merchant-web (REST)                rrsjk-light-service (Dubbo Provider)
┌──────────────────────────┐              ┌──────────────────────────────────┐
│ AgentTokenController     │───Dubbo────→│ AgentTokenService                │
│ GET /api/agent/token/    │              │  └─ AgentTokenServiceImpl         │
│   getAgentToken          │              │     └─ AgentTokenViewMapper      │
│                          │              │        └─ agent_token_view 表     │
│ OcrApiController         │              │                                  │
│  └─ bankImgOcr() 传入    │              │ AgentTokenModel                  │
│    loginId 作为 operator │───Dubbo────→│  └─ insertTokeLog()              │
│                          │              │     └─ 7类AgentNoEnum            │
│ LightStationBankCard     │              │                                  │
│  ChangeService.idCardOcr │              │ OCR Services (调用方)             │
│  (imgUrl, operator)      │              │  ├─ LightElecHtRecordServiceImpl │
└──────────────────────────┘              │  ├─ LightMasterHtRecordService   │
                                          │  ├─ 房产证/逆变器/银行卡/倾角OCR  │
                                          └──────────────────────────────────┘
```

### 7类AI智能体 (AgentNoEnum)

| 枚举值 | 描述 | inputToken基准 | outputToken除数 | 对应OCR服务 |
|---|---|---|---|---|
| PROPERTY_CERT_RECOGNITION | 房产证识别 | 500+random(500) | /2 | LightStationHouseCertificateOcrServiceImpl |
| PV_TILT_RECOGNITION | 组件倾角识别 | 1500+random(700) | /4 | LightStationModuleAngleOcrServiceImpl |
| INVERTER_RECOGNITION | 逆变器识别 | 2000+random(700) | /2 | LightStationInverterOcrServiceImpl |
| CONTRACT_RECOGNITION | 合同识别 | 20000+random(7000) | /2 | LightStationMasterContractOcrServiceImpl |
| BANK_CARD_RECOGNITION | 银行卡识别 | 1000+random(500) | /4 | LightStationBankCardChangeServiceImpl |
| LEASE_RECOGNITION | 租赁识别 | 10000+random(5000) | /2 | LightMasterHtRecordServiceImpl |
| CONTRACT_DATE_RECOGNITION | 合同日期识别 | 20000+random(7000) | /4 | LightElecHtRecordServiceImpl |

### Token计算逻辑

- **inputToken**: `base + ThreadLocalRandom.current().nextLong(range)` — 基于随机值估算（非精确计量）
- **outputToken**: `max(json.length() / divide, 1)` — 按响应JSON字符长度除以系数估算
- **total token**: inputToken + outputToken
- **注意**: inputToken 使用随机值而非实际计量，说明这是**近似成本估算**而非精确计费

### 数据表: agent_token_view

| 字段 | 类型 | 说明 |
|---|---|---|
| id | bigint | 主键 |
| agent_no | varchar | 智能体编码 (AgentNoEnum.value) |
| agent_name | varchar | 智能体名称 (AgentNoEnum.description) |
| fetch_at | varchar | 数据日期 (LocalDate.now().toString()) |
| user_no | varchar | 操作人ID |
| station_code | varchar | 关联电站编码 |
| time | datetime | 记录时间 |
| input_token | bigint | 输入token估算值 |
| output_token | bigint | 输出token估算值 |
| token | bigint | 总token |

### REST API

- **路径**: `GET /api/agent/token/getAgentToken`
- **参数**: `agentNo` (智能体编码), `type` (detail/daily), `date` (数据日期)
- **返回**: `List<AgentTokenDto>`
- **Dubbo引用**: `rrsjk-merchant-web/service.xml` 新增 `<dubbo:reference id="agentTokenService" interface="com.rrsjk.light.service.agent.AgentTokenService" check="false"/>`

### OCR接口变更

- `LightStationBankCardChangeService.idCardOcr(String imgUrl)` → `idCardOcr(String imgUrl, String operator)` — 新增操作人参数用于token日志追踪
- `OcrApiController.bankImgOcr()` 从 `currentAuthentication()` 获取当前登录用户ID传入
