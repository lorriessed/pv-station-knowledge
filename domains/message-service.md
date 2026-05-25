# 消息服务 (rrsjk-light-message-service)

更新时间: 2026-05-25

## 服务概述

**来源**: `rrsjk-light-message-service` 全量通读 (2026-05-25)

`rrsjk-light-message-service` 是光伏业务统一消息中心，负责审批消息、资料消息、政策消息、紧急消息的 CRUD、已读状态追踪、范围推送和定时通知。

### 技术栈
- Spring Boot 2.2.4 + Dubbo 2.7.4.1
- MyBatis (单数据源: `light_message_center` 库)
- Redis (消息去重/缓存)
- RocketMQ 5.0.7 (Usher MQ 框架)
- 阿里云短信 SDK (AcsClient)
- 阿里云 OSS (文件存储)
- iText PDF 生成
- EasyExcel 导出

### 数据库
- **库名**: `light_message_center` (dev 使用阿里云 RDS 加密连接 `encdb://`, prod 使用 `db003.rrsjk.internal`)
- **核心表**: `approval_message`, `document_message`, `policy_message`, `urgent_message`, `urgent_message_scope`, `user_message_relations`, `message_search_history`

---

## 消息类型体系

### 5 种消息类型

| 类型 | 枚举值 | 用途 |
|---|---|---|
| 审批消息 | `APPROVAL_MESSAGE` | 电站审核审批通知（方案审核、技术审核等） |
| 资料消息 | `DOCUMENT_MESSAGE` | 并网资料上传/补交通知 |
| 政策消息 | `POLICY_MESSAGE` | 政策变更/新政策发布通知 |
| 紧急消息 | `URGENT_MESSAGE` | 预警/紧急通知（含超期未完工预警） |
| 搜索历史 | - | 用户消息搜索记录 |

---

## 用户-消息关系模型

### user_message_relations 表

**来源**: `rrsjk-light-message-service` → `userMessageRelationServiceImpl.java`, `userMessageRelation.xml` (代码明确证明)

每条记录关联一个用户和一条消息，追踪：
- `is_read`: `Y`/`N` (已读/未读)
- `is_agree`: `Y`/`N` (是否同意/确认)
- `read_time`: 阅读时间

**查询逻辑**: 每次查询消息列表时 LEFT JOIN `user_message_relations` 获取 `isRead` 状态，未找到记录则默认 `N`。

**批量操作**: 支持 `batchMarkMessageAsRead()` — 一次性批量插入多条已读关系。

---

## 紧急消息 (UrgentMessage)

### 审核流程

**来源**: `rrsjk-light-message-service` → `UrgentMessageServiceImpl.java` (代码明确证明)

紧急消息发布需审核，状态流转：
1. `WAIT_AUDIT` — 待审核（默认状态，外部未指定 status 时）
2. `ENABLE` — 已生效（审核通过或免审核直接设置）

审核方法: `audit(Long urgentAuditId, String status, String remark, String passBy)`

### 消息接收范围 (UrgentMessageScope)

**来源**: `rrsjk-light-message-service` → `UrgentMessageScopeServiceImpl.java` (代码明确证明)

紧急消息支持按范围推送，范围表 `urgent_message_scope`:
- `scope_type`: `SP` (按服务商) / `SUB_CENTER` (按分中心)
- `sp_code`: 服务商编码（一级商用 spCode，二级商用 mobile）
- `sp_type`: `LEVEL_1` (一级商) / `LEVEL_2` (二级商) / `ALL`
- `center_id` / `center_name`: 分中心标识

**范围匹配逻辑** (`isInMessageScope`):
1. 如果消息没有配置接收范围 → 所有人都可以接收
2. 按 `scope_type` 匹配：
   - `SUB_CENTER`: 匹配分中心 ID 或服务商类型
   - `SP`: 匹配服务商 ID 或服务商编码，同时检查类型

### 弹窗消息

**来源**: `rrsjk-light-message-service` → `urgentMessageServiceDao.java`, `UrgentMessageServiceImpl.java` (代码明确证明)

- `getLatestUrgentMessageForPopup()` — 获取最新紧急消息用于弹窗展示
- `getPopupForId()` — 获取指定弹窗消息
- 查询条件包括 `spCode`, `centerName`, `spType` 等

---

## 超期未完工提醒通知

### 定时任务规则

**来源**: `rrsjk-light-message-service` → `OverdueStationNotifyJob.java` (代码明确证明)

**Dubbo 暴露**: 通过 `service.xml` 中 `<dubbo:service>` 注册，外部调度系统（XXL-Job）通过 Dubbo 调用 `OverdueStationNotifyJobService.execute()`。

**查询条件**: 查询 `[40, 60]` 天内 `complete_at IS NULL` 的电站。

**分阶段通知规则**:

| 阶段 | 天数范围 | 通知频率 | 去重方式 |
|---|---|---|---|
| 首次提醒 | 40 ≤ days < 50 | 仅通知一次 | Redis Key: `overdue_notify_40:spId:{spId}`, TTL=5天 |
| 每日提醒 | 50 ≤ days ≤ 60 | 每天通知一次 | 无需去重 |
| 停止 | days > 60 | 不通知 | - |

**权限隔离**:
- **一级商**: 收到名下所有超期电站（含二级商建的站）
- **二级商**: 只收到 `sub_sp_member_id = 该二级商 memberId` 的站

**消息内容格式**:
```
您的电站
「编码：xxx/业主：xxx」
「编码：xxx/业主：xxx」
距离首次签约时间已超过N天还未完工，为了不影响您的激励政策结算，请及时跟进施工进度！
```

**发送渠道**: APP 和 MER（商户通）各写一条 `urgent_message`。

**发送方标识**: `sendBy="SYSTEM"`, `sendByName="系统自动"`。

### Redis 去重

```java
private static final String NOTIFY_40_KEY_PREFIX = "overdue_notify_40:spId:";
private static final long   NOTIFY_40_TTL_DAYS   = 5L;
```

40 天阶段使用 Redis 去重，Key 格式 `overdue_notify_40:spId:{spId}`，TTL 5 天，保证在该阶段只发一次。

---

## 审批消息 (ApprovalMessage)

**来源**: `rrsjk-light-message-service` → `ApprovalMessageServiceImpl.java` (代码明确证明)

### 查询条件

支持按以下条件筛选:
- `stationCode`, `stationStatus`, `name`, `idCardNumber`, `houseType`
- `spId`, `spName`, `auditStatus`
- `mode` (业务模式), `createdBy`
- `isRead` (已读/未读，通过 `user_message_relations` 关联查询)

### 已读/同意操作

- `markMessageAsRead(messageId, memberId)` — 标记已读，无记录则新建
- `markMessageAsAgree(messageId, memberId)` — 标记同意（事务性操作，消息不存在抛异常）

---

## 资料消息 (DocumentMessage)

**来源**: `rrsjk-light-message-service` → `DocumentMessageServiceImpl.java` (代码明确证明)

### 创建去重

创建时先按 `documentId` 查询，如果存在则更新而非新建：
```java
List<documentMessage> documentId = documentMessageDao.findBy(ImmutableMap.of("documentId", message.getDocumentId()));
if (documentId.isEmpty()) {
    return documentMessageDao.create(message);
} else {
    message.setId(documentId.get(0).getId());
    return (long) documentMessageDao.update(message);
}
```

### 逻辑删除

- `logicalDeleteMessage(id)` — 设置 `isDeleted=1`
- `batchLogicalDeleteMessages(ids)` — 批量逻辑删除

---

## 政策消息 (PolicyMessage)

**来源**: `rrsjk-light-message-service` → `PolicyMessageServiceImpl.java` (代码明确证明)

### 创建去重

按 `policyId` + `policyMessageType` 查询，如果存在则更新。但 `BASIC_POLICY` 类型每次都创建新记录：
```java
if (!"BASIC_POLICY".equals(message.getPolicyMessageType())){
    byPolicyId = policyMessageDao.getByPolicyId(params);
}
if (null == byPolicyId || "BASIC_POLICY".equals(message.getPolicyMessageType())) {
    return policyMessageDao.create(message);
} else {
    return (long) policyMessageDao.update(message);
}
```

### 确认状态

政策消息查询时同时设置 `confirmStatus`:
- `isRead`: 已读状态
- `confirmStatus`: `"1"` 已确认 / `"0"` 未确认（从 `user_message_relations.isAgree` 映射）

### 复杂查询条件

支持政策级别筛选:
- `policyMessageType`, `policyCode`, `policyName`
- `beginAt`, `endAt` (生效时间范围)
- `deliveryType`, `mode`, `houseType`
- `type`, `rewardNode`, `newMerchantStandard`
- 省市区筛选: `provinceId`, `cityId`, `regionId`
- `policyIds`, `basicPolicyIds`, `lightGridAwardPolicyIds` (批量 ID 查询)

---

## 消息搜索历史

**来源**: `rrsjk-light-message-service` → `MessageSearchHistoryServiceImpl.java` (代码明确证明)

- 记录用户搜索关键词和消息类型
- 支持分页查询、单条删除、批量删除、清空历史
- 可指定 `messageType` 过滤

---

## 技术架构

### EventBus

**来源**: `rrsjk-light-message-service` → `EventBusConfig.java` (代码明确证明)

```java
@Bean
public EventBus lightEventBus() {
    ThreadPoolExecutor executorService = new ThreadPoolExecutor(800, 1300, 20L, TimeUnit.SECONDS, 
        new ArrayBlockingQueue<Runnable>(10000));
    AsyncEventBus bus = new AsyncEventBus("光伏事件总线", executorService);
    return bus;
}
```

线程池配置: 核心 800，最大 1300，队列 10000。

### RocketMQ (Usher)

**来源**: `rrsjk-light-message-service` → `MqConfig.java`, `RocketMqConfigInfo.java` (代码明确证明)

- 使用 Usher MQ 框架封装 RocketMQ 5.x
- Producer 配置: `producerName=light_service`
- Dev: `rmq-cn-bcd3zqxsi02` / Prod: `rmq-cn-lyi3zqxtl01`

### Dubbo 依赖

**来源**: `rrsjk-light-message-service` → `service.xml` (代码明确证明)

调用的外部服务:
- `messageService` (系统服务)
- `regionService`, `subCenterInfoService` (系统基础服务)
- `memberService`, `memberRoleService` (会员服务)
- `merchantService` (商户服务)
- `lightStationService`, `lightServiceProviderService` (光伏基础)
- `lightStationInverterService`, `lightStationPlanConfigService`
- `zeroCarbonServiceProviderService`, `lightZeroCarbonStationService` (零碳)
- `lightOpAuthorityZoneService`, `lightSpAuthorityZoneService` (运维区域)
- `repairs-api` (运维工单)

---

## 外部集成

### 阿里云短信

**来源**: `rrsjk-light-message-service` → `AcsClientConfig.java`, `application-prod.yml` (代码明确证明)

- `acs-client`: 杭州 Region
- 模板: `sms_master_template=SMS_249905426`, `sms_master_signed_template=SMS_249805413`

### 好签合同服务

**来源**: `rrsjk-light-message-service` → `application-dev.yml` (配置明确证明)

- `hxq.newcompany.url` — 新公司认证
- `hxq.uploadpdf.url` — PDF 上传
- `hxq.sign.url` — 合同签署

### 物流查询 (RRS)

**来源**: `rrsjk-light-message-service` → `application-dev.yml` (配置明确证明)

- `transit.url` — 物流查询接口
- Dev: `https://omstest.rrswl.com` / Prod: `https://oms.rrswl.com`

---

## 数据库表结构概要

| 表名 | 用途 |
|---|---|
| `approval_message` | 审批消息（电站编码、状态、审核状态等） |
| `document_message` | 资料消息（文档名称、类型、URL、业务类型等） |
| `policy_message` | 政策消息（政策编码、名称、生效时间、奖励节点等） |
| `urgent_message` | 紧急消息（标题、内容、渠道、审核状态等） |
| `urgent_message_scope` | 紧急消息接收范围（服务商/分中心维度） |
| `user_message_relations` | 用户-消息关系（已读/同意状态） |
| `message_search_history` | 消息搜索历史 |
