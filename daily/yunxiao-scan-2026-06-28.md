# 云效驱动代码学习报告 — 2026-06-28

## 扫描范围
- 扫描窗口: 2026-06-27 03:00 ~ 2026-06-28 03:00
- 云效需求: 15 个（近期活跃）
- Git 提交: 19 个（5 个仓库）
- 涉及人员: mabin(王斌), 龙龙(王斌), yumiao(于淼), 解钦

## Step -1 增量检查
- HEAD 比较: TOTAL_NEW=0（last_scan.json 已由 23:00 daily scan 更新）
- 但 --since 日期扫描发现 19 个新提交（23:00 daily scan 窗口与 yunxiao-scan 窗口不同）
- 云效状态变更: 15 个需求有状态变化（3个已发版、2个已完成、5个待测试、1个测试中、3个开发中、2个新创建）

## 云效需求状态变更

### 已发版（3个）
| 需求号 | 标题 | 研发负责人 | AI编码占比 |
|---|---|---|---|
| TAEI-3282 | 大屏-浦银大屏 | 马金虎 | 50% |
| TAEI-3290 | 同步部分逆变器数据到VPP kafka | 马金虎 | 60% |
| TAEI-3044 | 华融上收入多1个账(B43质量保证金) | 于淼 | 70% |

### 已完成（2个）
| 需求号 | 标题 | 研发负责人 | AI编码占比 |
|---|---|---|---|
| TAEI-3228 | 中核传数据逻辑优化 | 王斌 | 20% |
| TAEI-3264 | 派单人员管理添加删除功能 | 包鑫 | 50% |

### 待测试（5个）
| 需求号 | 标题 | 研发负责人 | AI编码占比 |
|---|---|---|---|
| TAEI-3324 | 越秀授权协议替换新模板 | 于淼 | 80% |
| TAEI-3266 | 统众导入发票号及连接 | 代继宁 | 93% |
| TAEI-3221 | 仓储调拨入库 | 姜传德 | 50% |
| TAEI-3193 | 零碳适家优化施工页面 | 姜传德 | 20% |
| TAEI-3234 | 商户通业主租赁合同管理 | 孙志男 | 85% |

### 开发中（3个）
| 需求号 | 标题 | 研发负责人 |
|---|---|---|
| TAEI-3246 | 零碳适家退安装质保金 | 代继宁 |
| TAEI-3317 | 大屏-资产大屏 | 马金虎 |
| TAEI-3304 | 商户通&CBS新增低效电站 | 姜传德 |

### 新创建（2个）
| 需求号 | 标题 | 研发负责人 |
|---|---|---|
| TAEI-3323 | 供应商风险模型对接 | 于淼 |
| TAEI-3322 | BT下项目公司基本信息及变更信息 | 于淼 |

## 代码变更分析

### 1. 并网容量计算数据源回退 (yumiao, rrsjk-light-report-service)
- **架构回退**: ReportMGridServiceImpl 从 DwsLightInveterDataService → LightInveterDataService
- **影响**: 手机报表大屏的并网电站数统计全部改回 MySQL 主库
- **提交**: 0fcf50092, ae9a9d216
- **风险**: 与之前 ADS/DWS 迁移方向相反，需确认 DWS 数据源问题根因

### 2. 收入成本报表导出功能 (解钦, rrsjk-admin-web)
- **新增**: /doSummaryExport.do 接口 + IncomeCostSummaryExcel VO
- **功能**: EasyExcel 导出，树形缩进，权限 report:incomeCost:export
- **改进**: 默认日期从"当天"改为"前一天"（数据打标时效性）
- **提交**: 6cdd55b8f0
- **数据来源**: ADS 层 ads_sap_revenue_cost_summary

### 3. 智能体Token统计 (mabin/王斌, rrsjk-light-service + rrsjk-merchant-web)
- **新增**: AgentTokenView 实体 + AgentTokenViewMapper + AgentTokenModel
- **功能**: AI 智能体 Token 消耗统计与日志记录
- **商户通**: OCR 识别服务 Token 统计 + AI 统计 Token 验收
- **提交**: c655469974, eec5fef9ea, 72240df891, 29aee48d34, b117ef0db1, b3d86b5586
- **业务意义**: 追踪 AI 智能体 Token 消耗，支撑成本核算

### 4. 报表配置优化 (龙龙/王斌, rrsjk-light-service + rrsjk-admin-web)
- **增强**: Excel 下拉选择、年月格式校验、房型/模式数据验证
- **重构**: 下载模板方法支持下拉选项，ReportHouseTypeEnum 迁移
- **提交**: 1a9abeb8dc, 53ebed324f, 06b43520f3, d757687f79, 23b5c2e280

### 5. 其他
- autotest: 于淼添加 AI 自动 MR 测试标记 (f64dece)

## AI编码占比观察
| 需求号 | AI编码占比 | 负责人 |
|---|---|---|
| TAEI-3266 | 93% | 代继宁 |
| TAEI-3234 | 85% | 孙志男 |
| TAEI-3324 | 80% | 于淼 |
| TAEI-3044 | 70% | 于淼 |
| TAEI-3290 | 60% | 马金虎 |

## 风险预警
1. **DWS→MySQL 回退**: yumiao 将 ReportMGridServiceImpl 从 DWS 回退到 MySQL，需确认 DWS 数据源问题
2. **收入成本报表默认日期变更**: 从"当天"改为"前一天"，需确认用户习惯影响

## 知识库更新
- 新增: daily/yunxiao-scan-2026-06-28.md
- 待更新: domains/settlement.md (收入成本报表导出)
- 待更新: domains/inverter-data.md (DWS→MySQL 回退)
- 待更新: domains/cbs-management.md (智能体Token统计)

## HTML 报表
https://cdn01.rrsjk.com/reports/7a1616e1-4003-4591-aa1b-075633be0472.html
