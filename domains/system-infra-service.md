# rrsjk-system-service — 基础系统服务

> 日日顺光伏体系的**基础公共服务**，提供银行、地区、OCR识别、日历工作日、字典、消息发送、定时任务管理等基础设施能力。被 rrsjk-light-service、rrsjk-trade-service 等多个业务服务通过 Dubbo 引用。

**仓库**: `rrsjk-system-service` → `/data/pvcode/rrsjk-system-service`
**分支**: master | HEAD: 6542e243ef88
**证据等级**: 代码明确证明 (2026-06-03 全量通读)

---

## 项目结构

- **模块**: `rrsjk-system-api` (接口/实体) + `rrsjk-system-impl` (实现)
- **包路径**: `com.rrsjk.system`
- **依赖**: rrs-framework-core, Aliyun OCR SDK, 阿里云短信 SDK, WeChat SDK

---

## 1. 银行服务 (BankService)

**来源**: `basic/service/BankService.java`, `basic/service/impl/BankServiceImpl.java`

### 主银行信息
- `getMainBankInfoList()` — 查询所有主银行名称
- `getProvinceInfoList()` — 获取省份列表
- `getAreaInfoByParentCode(parentCode)` — 根据省代码查询市县
- `getBankInfoByAreaAndBank(bankCode, areaCode)` — 根据银行编码+地区查询支付联行全称
- `getBankAreaByName(bankName)` — 根据银行名称查询支付联行

### 越秀模式银行服务
- `getByCityIdAndHeadBankName(cityId, headBankName)` — 根据城市ID+主银行名查询联行号 (有 Guava LoadingCache 10小时缓存)
- `getAllHeadBank()` — 获取所有主银行列表 (去重排序，10小时缓存)

### 华融租赁 (Hrflc) 银行
- `getHrflcMainBankInfoList()` — 获取华融主银行信息
- `getHrflcBankInfoByBankNumber(bankNumber)` — 根据联行号查询华融银行信息

### 联行号服务 (BankNumberService)
- 越秀方使用，`BankNumberService` 独立接口
- 特殊城市处理 (注释掉): 湖北直辖/海南直辖 cityId 映射

### 支行管理 (BankAreaService)
- `findBy(pageRequest, params)` — 分页查询支行
- `addBankArea(bankArea, userId)` — 新增支行 (校验12位联行号格式)
- `updateBankArea(bankArea, userId)` — 更新支行 (记录变更历史到 `bank_area_history`)
- `deleteBankArea(id, userId)` — 删除支行 (记录历史)

**联行号校验**: `^\\d{12}$` — 必须是12位纯数字

---

## 2. 地区服务 (RegionService)

**来源**: `basic/service/RegionService.java`, `basic/service/impl/RegionServiceImpl.java`

### 基础查询
- `getAllProvinceList()` — 获取所有省 (LoadingCache 180分钟)
- `getAllCityList()` — 获取所有市
- `getAllRegionList()` — 获取所有区
- `getByParentId(parentId)` — 根据上级ID查询子地区
- `get(id)` — 根据ID查询

### 腾讯地图同步
- `initTXRegion()` — 从腾讯地图 API 同步省市区数据
  - API: `https://apis.map.qq.com/ws/district/v1/list`
  - 同步 Level 2(市) + Level 3(区/县)
  - 事务保护: 先备份旧数据 (`fullCopyToOld`)，再删除旧数据 (`fullDeleteOld`)，再批量插入
- `initTXTownship()` — 同步乡镇/街道数据 (Level 4)
  - API: `https://apis.map.qq.com/ws/district/v1/getchildren`
  - 遍历所有 Level 3 区域，逐个获取子级
  - 每次请求间隔 200ms (限流)

### 广发/大华区域匹配
- `GfMatchRegionService` — 广发区域匹配
- `DhMatchRegionService` — 大华区域匹配

---

## 3. OCR 识别服务 (OcrAnalyseRecordService)

**来源**: `basic/service/OcrAnalyseRecordService.java`, `basic/service/impl/OcrAnalyseRecordServiceImpl.java`

- **引擎**: 阿里云 OCR API (`ocr_api20210707`)
- `create(url, type, createdBy)` — 创建 OCR 分析记录
- `analyseUrl(url, type, createdBy)` — 执行 OCR 识别
  - 识别身份证正反面
  - 身份证反面 → 提取有效期限 → 校验是否过期
  - 日期格式: `yyy-MM-dd` (注意: 代码中年份格式为3位 `yyy`)
- **记录表**: `ocr_analyse_record` — 记录 URL、请求ID、响应、状态码

**⚠️ Bug**: 日期格式 `yyy-MM-dd` 应为 `yyyy-MM-dd`，但代码中写的是 `yyy` (少一位y)

---

## 4. 日历工作日服务 (CalendarDayService)

**来源**: `basic/service/CalendarDayService.java`, `basic/service/impl/CalendarDayServiceImpl.java`

- `findByCalDate(calDate)` — 根据日期查询 (LoadingCache 24小时)
- `findByYearMonthDay(year, month, day)` — 根据年月日查询 (三级缓存)
- `findByYearMonth(year, month)` — 根据年月查询 (List 缓存)
- `change(model)` — 修改日历 (工作日/节假日标记)
- `add(model)` — 新增日历条目

**缓存设计**: 3个 LoadingCache (日期/年月日/年月)，最大容量 1000/1000/500

---

## 5. 字典服务 (CodeService / DictTypeService / DictValueService)

### CodeService (旧版字典)
- `getAll()` — 获取所有字典数据
- `getCode(codeDiv, codeCd)` — 根据分类+编码查询单个字典

### DictTypeService / DictValueService (新版字典)
- `selectDictValueByCode(code)` — 根据字典编码查询字典值列表
- `insert/update` — 字典类型/值的增删改

---

## 6. 消息服务 (MessageService)

**来源**: `message/service/MessageService.java`

- `sendSms(request)` — 发送短信 (默认使用【日日顺乐农】签名)
- `sendSms(request, smsSign)` — 发送短信 (指定签名)
- `sendEmail(request)` — 发送邮件
- `aliyunSendSms(request, smsSign)` — 直接调用阿里云短信 SDK

**DTO**:
- `SendSmsRequest` — 短信模板请求 (mobile + templateId + parameters)
- `SendEmailRequest` — 邮件请求 (to/cc/bcc + templateId + parameters)

---

## 7. 定时任务管理 (JobService)

**来源**: `task/service/JobService.java`

### Dubbo 定时任务
- `addJob(AddDubboJobRequest)` — 新建 Dubbo 定时任务
  - `interfaceName` — Dubbo 接口全限定名
  - `method` — 方法名
  - `group/version/timeout` — Dubbo 调用参数
- `find(pageable, criteria)` — 分页查询任务
- `get(id)` — 获取任务详情

### Job 实体
- `JobStatusEnum`: `ENABLED` / `DISABLED` / `DELETED`
- `JobStateEnum`: `RUNNING` / `PAUSED`
- `JobTypeEnum`: `DUBBO` / `JDBC`

### 事件驱动
- `AddJobEvent` / `DeleteJobEvent` / `EditJobEvent` / `PauseJobEvent` / `ResumeJobEvent`
- 通过 Guava EventBus 发布任务变更事件

---

## 8. 支付账号服务 (Account*)

**来源**: `account/service/`

| Service | 说明 |
|---|---|
| `AccountWechatService` | 微信支付账号 (按公司码+客户端查询) |
| `AccountAlipayService` | 支付宝账号 |
| `AccountBaiduService` | 百度支付账号 |
| `AccountCcbService` | 建行支付账号 |
| `AccountKjtService` | 科技通账号 |
| `AccountTransferService` | 转账汇款账号 |

- 通用接口: `AccountService<T>` — `get(primaryKey)`, `findByCompanyCode()`, `findByMerchantId()`, `findAll()`

---

## 9. 其他基础服务

| Service | 说明 |
|---|---|
| `ExpressService` | 快递服务 (按编码查询/按类型查询) |
| `XiaoweiService` | 小微部门 (海尔组织架构) |
| `ChainGroupService` | 链群管理 (parent/level 层级) |
| `SubCenterInfoService` | 分中心信息查询 |
| `PageHtmlService` | 商城页头页脚 HTML (LoadingCache 1小时) |
| `Oauth2ClientService` | OAuth2 客户端查询 (LoadingCache 6小时 + Proxy 代理) |
| `Oauth2ClientServiceProxy` | 带缓存的 OAuth2 客户端代理 (5分钟过期) |
| `SensitiveWordService` | 敏感词过滤 (DFA 算法，启动时加载到内存) |
| `AccessTokenService` | Access Token 管理 |
| `AccessTokenRefreshService` | Token 定时刷新 |
| `BizRoleService` | 业务角色管理 |
| `CalendarDayService` | 日历/工作日节假日 |

---

## 10. Dubbo 服务暴露

**来源**: `rrsjk-system-api` 下的 Service 接口

| Service | 说明 |
|---|---|
| `BankService` | 银行信息/联行号/支行管理 |
| `BankAreaService` | 支行增删改 |
| `BankNumberService` | 联行号查询 (越秀) |
| `RegionService` | 地区查询/腾讯地图同步 |
| `GfMatchRegionService` | 广发区域匹配 |
| `DhMatchRegionService` | 大华区域匹配 |
| `OcrAnalyseRecordService` | OCR 识别 |
| `CalendarDayService` | 日历工作日 |
| `CodeService` | 字典查询 |
| `DictTypeService` | 新字典类型 |
| `DictValueService` | 新字典值 |
| `MessageService` | 短信/邮件发送 |
| `JobService` | 定时任务管理 |
| `AccountWechatService` | 微信账号 |
| `AccountAlipayService` | 支付宝账号 |
| `AccountCcbService` | 建行账号 |
| `AccountBaiduService` | 百度账号 |
| `AccountKjtService` | 科技通账号 |
| `AccountTransferService` | 转账账号 |
| `ExpressService` | 快递查询 |
| `XiaoweiService` | 小微部门 |
| `ChainGroupService` | 链群管理 |
| `SubCenterInfoService` | 分中心 |
| `PageHtmlService` | 页面HTML |
| `Oauth2ClientService` | OAuth2客户端 |
| `SensitiveWordService` | 敏感词 |
| `AccessTokenService` | Token管理 |
| `BizRoleService` | 业务角色 |

---

## 11. 数据库表

| 表名 | 说明 | Mapper |
|---|---|---|
| `bank_info` | 主银行信息 | BankInfoMapper.xml |
| `bank_area` | 支行/联行信息 | BankAreaMapper.xml |
| `bank_area_history` | 支行变更历史 | BankAreaHistoryMapper.xml |
| `bank_number` | 联行号 (越秀) | BankNumberMapper.xml |
| `hrflc_bank_info` | 华融租赁银行信息 | HrflcBankInfoMapper.xml |
| `area_info` | 地区信息 | AreaInfoMapper.xml |
| `Regions` | 地区表 (腾讯同步) | RegionsMapper.xml |
| `gf_match_region` | 广发区域匹配 | GfMatchRegionMapper.xml |
| `dh_match_region` | 大华区域匹配 | DhMatchRegionMapper.xml |
| `calendar_day` | 日历工作日节假日 | CalendarDayMapper.xml |
| `code` | 字典数据 | CodeMapper.xml |
| `dict_type` | 字典类型 | DictTypeMapper.xml |
| `dict_value` | 字典值 | DictValueMapper.xml |
| `ocr_analyse_record` | OCR分析记录 | OcrAnalyseRecordMapper.xml |
| `sensitive_word` | 敏感词 | SensitiveWordMapper.xml |
| `account_wechat` | 微信账号 | AccountWechatMapper.xml |
| `account_alipay` | 支付宝账号 | AccountAlipayMapper.xml |
| `account_ccb` | 建行账号 | AccountCcbMapper.xml |
| `account_baidu` | 百度账号 | AccountBaiduMapper.xml |
| `account_kjt` | 科技通账号 | AccountKjtMapper.xml |
| `account_transfer` | 转账账号 | AccountTransferMapper.xml |
| `express` | 快递公司 | ExpressMapper.xml |
| `xiaowei` | 小微部门 | XiaoweiMapper.xml |
| `chain_group` | 链群 | ChainGroupMapper.xml |
| `oauth2_client` | OAuth2客户端 | Oauth2ClientMapper.xml |
| `access_token` | 访问令牌 | AccessTokenMapper.xml |
| `job` | 定时任务 | JobMapper.xml |
| `biz_role` | 业务角色 | BizRoleMapper.xml |
| `page_html` | 页面HTML | PageHtmlMapper.xml |
| `sub_center_info` | 分中心信息 | SubCenterInfoMapper.xml |

---

## 12. 已知问题

### OCR 日期格式 Bug
**来源**: `OcrAnalyseRecordServiceImpl.java`
```java
DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyy-MM-dd");
```
年份格式 `yyy` (3位) 应为 `yyyy` (4位)，但 `LocalDate.parse()` 在 4 位年份输入时仍能正常工作 (宽松解析)。建议修复为标准格式。
