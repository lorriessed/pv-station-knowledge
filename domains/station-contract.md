# 电站签合同业务

更新时间: 2026-05-18 (代码扫描)

## 业务概述

新建电站确认时，系统自动创建合同记录，通过 DCC 电子签章系统生成合同内容，发送短信通知业主签署。商户通 (rrsjk-merchant-h5) 提供合同管理页面。

## 核心数据表

| 表名 | 说明 | 数据库 | 关键引用 |
|---|---|---|---|
| `light_station_contract_record` | 电站合同记录主表 | rrsjk_light | `LightStationContractRecordDao` |
| `light_station_contract_record_log` | 合同记录操作日志 | rrsjk_light | `LightStationContractRecordLogDao` |
| `light_station_contract_info` | 合同信息详情 | rrsjk_light | `LightStationContractInfoDao` |
| `light_elec_contract` | 电费合同表 | rrsjk_light | `LightElecContractDao` |
| `light_elec_seal_use` | 用印记录表 | rrsjk_light | `LightElecSealUseDao` |

## 完整业务流程

```
1. 商户提交电站信息 (rrsjk-merchant-web / rrsjk-merchant-h5)
   ↓
2. 业务员确认电站 (LightStationServiceImpl.confirmStation)
   ├─ 创建合同记录: light_station_contract_record
   ├─ 状态: WAIT_USER_SIGN (待用户签署)
   └─ 异步触发: notifyLightStationDccContract
       ↓
3. DCC 合同监听器 (LightStationDccContractListener)
   ├─ 查询合伙人信息 (LightProjectPartner)
   ├─ 查询项目公司信息 (LightCompanyInfo)
   ├─ 生成合同号: FS + yyyyMMddHHmmssSSS
   ├─ 填充合同模板参数 (业主信息、电站信息、政策信息)
   ├─ 调用 DCC 用印接口 (addContract)
   ├─ 调用 DCC 快捷签接口 (getSignUrlByTaskNoKjq)
   └─ 获取签署链接 PDF URL
       ↓
4. 发送短信 (StationSignSendSmsModel)
   ├─ 主合同: 短信模板 1133
   ├─ 结算协议: 短信模板 1135
   ├─ 装机协议: 短信模板 1134
   ├─ 权属证明: 短信模板 1146
   └─ 短信内容: "尊敬的{user}，请点击链接签署合同: {signUrl}"
       ↓
5. 业主收到短信，点击链接签署
   ├─ 商户通 H5 展示合同预览
   ├─ 业主签署 (userSignAt 记录时间)
   └─ 状态变更: WAIT_USER_SIGN → SIGNED
       ↓
6. 合伙人/公司用印 (如需要)
   └─ 状态: WAIT_PARTNER_SIGN → SIGNED
```

## 合同类型枚举

| 枚举值 | 说明 | 短信模板 | 合同号前缀 | 签署方式 |
|---|---|---|---|---|
| `MASTER` | 主合同 (整村分布式) | 1133 | FS | 线上/线下 |
| `ZH_MASTER` | 中核主合同 | 1133 | FS | 线上 |
| `CHD_MASTER` | 华电主合同 | 1133 | FS | 线上 |
| `INSTALL` | 装机补充协议 | 1134 | FSI | 线上 |
| `FINANCE` | 结算补充协议 | 1135 | FSF | 线上 |
| `STOP` | 终止协议 | - | FSS | 线上 |
| `OWNERSHIP_PROVE` | 权属证明 (华润) | 1146 | FSO | 线上 |
| `DH_MASTER` | 顶好主合同 | - | - | - |
| `GF_MASTER` | 广发主合同 | - | - | - |
| `TP_PAYMENT_AGENCY` | 共建合同 | - | - | - |
| `PF_INFO_AUTH` | 浦银信息授权协议 | - | - | - |
| `CREDIT_AUTH` | 信用授权协议 | - | - | - |
| `GF_INFO_AUTH` | 广发展信息授权协议 | - | - | - |
| `HRFLC_INFO_AUTH` | 华融信息授权协议 | - | - | - |
| `HRFLC_EPC_MASTER` | 华融EPC业主主合同 | - | - | - |

## 合同状态

| 状态值 | 说明 | 可操作 |
|---|---|---|
| `INIT` | 初始 | - |
| `WAIT_SIGN` | 待签合同 | 发送短信 |
| `WAIT_USER_SIGN` | 待用户签合同 | 重发短信 |
| `WAIT_PARTNER_SIGN` | 待合伙人签合同 | - |
| `SIGNED` | 已签署 | 下载合同 |
| `DISABLE` | 已作废 | - |

## 签署方式

| 方式 | 说明 |
|---|---|
| `ONLINE` | 线上签署，通过 DCC 电子签章系统 |
| `OFFLINE` | 线下签署，手动录入合同编号 |

## 关键字段

| 字段 | 类型 | 说明 |
|---|---|---|
| `station_id` | Long | 电站 ID |
| `station_code` | String | 电站编码 |
| `station_name` | String | 业主姓名 |
| `mobile` | String | 业主手机号 |
| `contract_type` | String | 合同类型 (枚举见上) |
| `status` | String | 合同状态 (枚举见上) |
| `send_sms_at` | LocalDateTime | 发送短信时间 |
| `send_sms_sum` | Integer | 发送短信次数 |
| `guarantor_send_sms_at` | LocalDateTime | 共签人发送短信时间 |
| `guarantor_send_sms_sum` | Integer | 共签人发送短信次数 |
| `user_sign_url` | String | 用户签署链接 |
| `user_sign_at` | LocalDateTime | 用户签署时间 |
| `guarantor_sign_at` | LocalDateTime | 共签人签署时间 |
| `sign_at` | LocalDateTime | 最终签署时间 |
| `contract_no` | String | 合同编号 (线下签署时录入) |
| `dh_contract_path` | String | 顶好合同下载地址 |
| `dh_contract_view_path` | String | 顶好合同预览地址 |
| `dh_contract_owner_path` | String | 共签人签署链接 |
| `dh_contract_from_type` | Integer | 顶好合同来源: 10-纸质, 20-电子 |
| `sign_type` | String | 签署方式 (ONLINE/OFFLINE) |
| `station_type` | String | 电站类型 |
| `sp_id` | Long | 服务商 ID |
| `sp_name` | String | 服务商名称 |
| `partner_id` | Long | 合伙人 ID |
| `partner_name` | String | 合伙人名称 |
| `seal_user` | String | 用印人 |
| `type` | Integer | 类型: 0-电站, 1-登记信息 |

## 服务调用链

```
rrsjk-merchant-web / rrsjk-merchant-h5 (前端)
    ↓
LightStationServiceImpl.confirmStation()
    ├─ 创建/更新合同记录 (addRecord/updateRecord)
    └─ 异步: executorService.execute(() -> notifyLightStationDccContract)
        ↓
LightStationDccContractEvent (事件总线)
    ↓
LightStationDccContractListener.dccSignContract()
    ├─ 查询合伙人 (LightProjectPartnerService)
    ├─ 查询项目公司 (LightCompanyService)
    ├─ 构建用印参数 (buildSealUseOnline, buildPartner, buildPdfParams)
    ├─ DccContractModel.addContract() → DCC 用印申请
    ├─ DccContractModel.getSignUrlByTaskNoKjq() → 获取快捷签链接
    └─ StationSignSendSmsModel.notifyUserSign() → 发送短信
        ↓
MessageService.sendSms() → 阿里云短信服务
```

## DCC 签章系统配置

DCC 是第三方电子签章服务，通过 HTTP API 调用：

| 配置项 | 说明 |
|---|---|
| `dcc.sourceSystem` | 来源系统标识 |
| `dcc.password` | DCC 系统密码 |
| `dcc.addContract` | 添加合同/用印申请接口 |
| `dcc.singUrlByTaskNoKjq` | 获取快捷签签署链接 |
| `dcc.signedNotifyUrl` | 签署完成回调地址 |
| `dcc.signedNotifyUrlToOp` | 签署完成回调地址 (运维) |
| `dcc.companyCheck` | 企业认证接口 |
| `dcc.personalRegister` | 个人注册接口 |
| `dcc.retreatTaskUrl` | 撤回任务接口 |

## 短信模板

| 模板 ID | 用途 | 参数 |
|---|---|---|
| 1133 | 主合同签署 | user(姓名), signUrl(签署链接) |
| 1134 | 装机协议签署 | user(姓名), signUrl(签署链接) |
| 1135 | 结算协议签署 | user(姓名), signUrl(签署链接) |
| 1146 | 权属证明签署 | user(姓名), signUrl(签署链接) |

## 前端页面

| 页面 | 路径 | 说明 |
|---|---|---|
| 商户通合同列表 | `rrsjk-merchant-h5/src/views/apv/pro/contractList.vue` | 合同管理主页面 |
| 商户通合同详情 | `rrsjk-merchant-h5/src/views/apv/base/spContracts.vue` | 服务商合同管理 |
| 零碳合同列表 | `rrsjk-merchant-h5/src/views/zeroCarbon/base/contractList.vue` | 零碳项目合同 |
| 供应商合同列表 | `rrsjk-merchant-h5/src/views/supplier/contractList.vue` | 供应商合同 |
| 服务商合同管理 | `nahui-pv.hds-h5/src/views/osp/provider/contractManagement.vue` | 运维商合同 |

## 核心代码文件

| 文件 | 说明 |
|---|---|
| `LightStationContractRecord.java` | 合同记录实体 |
| `LightStationContractRecordServiceImpl.java` | 合同记录服务实现 |
| `LightStationContractRecordDao.java` | 合同记录 DAO |
| `LightStationDccContractEvent.java` | 合同事件定义 |
| `LightStationDccContractListener.java` | 合同事件监听器 |
| `DccContractModel.java` | DCC 签章接口封装 |
| `StationSignSendSmsModel.java` | 短信发送模型 |
| `LightStationServiceImpl.java` | 电站创建服务 (confirmStation) |
| `LightStationContractInfoController.java` | 商户通合同信息接口 |

## 排查要点

1. **短信未发送**: 检查 `send_sms_at` 和 `send_sms_sum` 字段，查看 `LightStationDccContractListener` 日志
2. **合同状态卡住**: 检查 DCC 接口调用是否成功，查看 `light_elec_seal_use` 表状态
3. **业主未收到短信**: 检查 `station.phone` 是否正确，短信模板是否配置
4. **签署链接失效**: DCC 签署链接有有效期，需重新发起
5. **线下合同**: 需在确认电站时手动录入合同编号 (`contract_no`)

## 相关定时任务

- 合同时效提醒: 定期发送短信催促未签署的业主
- 合同状态同步: 监听 DCC 回调更新合同状态

## 来源

- 代码扫描: 2026-05-18
- `LightStationContractRecord.java`: rrsjk-light-service/rrsjk-light-api
- `LightStationContractRecordServiceImpl.java`: rrsjk-light-service/rrsjk-light-impl
- `LightStationDccContractListener.java`: rrsjk-light-service/rrsjk-light-impl
- `StationSignSendSmsModel.java`: rrsjk-light-service/rrsjk-light-impl
- `DccContractModel.java`: rrsjk-light-service/rrsjk-light-impl
- `LightStationServiceImpl.java`: rrsjk-light-service/rrsjk-light-impl
- `contractList.vue`: rrsjk-merchant-h5
