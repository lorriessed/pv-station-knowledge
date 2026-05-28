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

## 与核心 Java 微服务的关联

这些 Flask 服务是**被调用方**，核心 Java 微服务 (rrsjk-light-service 等) 通过 HTTP 调用这些 AI 接口完成信息提取后，将结果写入业务数据库。

**关联 Java 代码位置**: `com.rrsjk.light.service.model.LightUseModel#invoke` (LightUseModel.java:543) — 安装服务费 SAP 记账逻辑，DB_TOOL SQL 中明确引用。
