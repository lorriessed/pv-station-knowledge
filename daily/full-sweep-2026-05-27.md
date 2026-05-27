# 全量通读报告 2026-05-27 (第14轮)

## 统计

- **通读仓库**: 5 个 (rrsjk-merchant-h5, rrsjk-merchant-service, rrsjk-merchant-web, rrsjk-migration-member, rrsjk-migration-mix)
- **从未通读**: 0 个 (全部已在历史轮次通读过，本轮为重扫)
- **业务文件总数**: 834 (3 + 182 + 413 + 43 + 196)
- **新增知识库文件**: 1 个
- **更新知识库文件**: 2 个

## 仓库分析

### 1. rrsjk-merchant-h5 (3 文件, 无业务代码)
- 仅包含 openspec 配置变更提案(token-expiry-form-recovery, token401-modal-login)
- 无光伏业务逻辑，前端 H5 应用
- **业务价值**: 低

### 2. rrsjk-merchant-service (182 文件, ⭐核心)
**核心业务域**:
- **企业客户管理**: 注册(MDM校验)→审核→启用，零碳适家企业客户押金管理→SAP记账
- **牛人(专业)客户**: 额度/账期/合同管理
- **工商业客户**: 安装商/设计院/甲方客户管理
- **驿站(自提点)**: 申请/审核/分组/经纬度/门头照片
- **配送线路**: 线路管理+驿站关联
- **店铺体系**: 普通店铺 + 云智妆(YZZ)店铺/导购员
- **供应商管理**: 注册/审核/MDM同步
- **园区评价**: 三版评价模型(非光伏核心)
- **MDM集成**: 客户/供应商主数据校验(Dubbo)
- **外部调用**: SAP记账(Dubbo)、顺丰BKind(HTTP)、短信(Dubbo)、快递100(HTTP)

### 3. rrsjk-merchant-web (413 文件, ⭐核心)
**核心功能**:
- **OAuth2网关**: Token校验 + 跨域 + IP白名单 + 店铺状态检查
- **会员注册**: 手机号+短信验证码+密码，Redis限流
- **AI助手集成**: Dify API 聊天消息接收 + 用户问题管理(三级分类)
- **领用单管理**: 完工前领用列表/导出/手动出库(关联 rrsjk-light-service)
- **领用异常**: 异常列表/导出
- **垂杨对接**: 电站信息/出图数据/踏勘数据
- **百度AI**: 太阳板数量识别
- **保外记账**: repairs 模块结算数据
- **商户用户信息**: AES加密 + 分中心分组
- **QPS限流**: 自定义 @RequestLimiter 注解 + Redis 实现

### 4. rrsjk-migration-member (43 文件, 历史迁移, @Deprecated)
- Canal 监听 Shop 库 binlog → 迁移到 rrscom
- 迁移表: Members, MemberAddresses, LoginInfo
- 最后活跃: 2025-04-07 (版本升级)

### 5. rrsjk-migration-mix (196 文件, 历史迁移, @Deprecated)
- Canal 监听多库(Shop, ln_shoptv, ehaier_system)
- 迁移域: 产品主数据/价格/保本价/外仓直发/供应商/乐农商品/评价/地址
- 多数据源: item/shop/merchant/ln/mdm/system/member/portal/rrs
- 最后活跃: 2025-04-07 (版本升级)

## 知识库更新

| 文件 | 操作 | 新增内容 |
|---|---|---|
| `domains/merchant-service.md` | **新增** | 商户服务域完整文档(企业客户/押金/牛人客户/驿站/店铺/供应商/AI集成/外部调用) |
| `domains/settlement.md` | 追加 | 零碳适家企业客户押金结算流程 |
| `domains/approval.md` | 追加 | 企业客户审核流程 + 工商业客户审核流程 |

## 关键业务发现

1. **企业客户注册必须通过 MDM 建户校验** — 税号+公司名称与MDM一致才可注册
2. **零碳适家企业客户押金确认后自动累加保证金** — 同一事务内更新押金状态 + corporate_client.deposit
3. **押金确认后触发 SAP 记账** — FinanceIncomeModel.corporateClientDepositToSap() (Dubbo)，失败不影响收款确认
4. **企业客户与商户是一对一关系** — 同一 memberId 不能对应多个启用商户
5. **商户-web 集成 Dify AI 助手** — 聊天消息接收 + 问题管理三级分类
6. **商户-web 有领用单管理接口** — 通过 Dubbo 调用 light-service 的 LightUseOrderService
