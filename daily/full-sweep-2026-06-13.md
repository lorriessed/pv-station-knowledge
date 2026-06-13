# PVS 全量代码通读报告 — 2026-06-13 (第29轮)

## 概览
- **通读仓库**: 5 个 (nahui-pv.merchant-micro.zch, nahui-pv.merchant-monorepo-h5, nahui-pv.mobile-h5, nahui-pv.osp-mini, nahuipv-greenergy-management-flutter)
- **本轮性质**: 重扫 (122/122 仓库已于 2026-06-11 完成首扫，此后全部为重扫)
- **策略**: Delta Discovery — 聚焦自上次通读以来的新增业务逻辑
- **有实质业务变更**: 2 个仓库 (nahui-pv.mobile-h5, nahui-pv.merchant-micro.zch)
- **无变更/空壳**: 3 个仓库 (nahui-pv.merchant-monorepo-h5, nahui-pv.osp-mini, nahuipv-greenergy-management-flutter)

---

## 仓库分析

### 1. nahui-pv.mobile-h5 ⭐ 重点 (dev, HEAD: a5d4302a)

**最近活跃**: 2026-06-11 (2天前)，开发者: yanghui/杨辉

#### 业务变更 1: TAEI-3127 完工/技术驳回暂存增强
- **techRejectFlag 字段**: 当 `lightStation.status === 'TECH_CHECK_REJECT'` 时设置 `techRejectFlag: 1`
- **cacheEnable 缓存策略变更**: 编辑模式从"不读缓存"改为"强制读缓存"，确保驳回后编辑时加载草稿数据
- **存草稿按钮权限变更**: 从 `edit != '1'` 条件显示改为始终显示，orderTeamId 模式下编辑时也支持暂存
- **影响页面**: `completeAffirm/index.jsx` (户用完工确认) + `completeAffirmGf/index.jsx` (工商业完工确认)

#### 业务变更 2: 逆变器水印相机拍摄
- Upload 组件新增 `isNeedCamera` 属性，与 `scanQrCode` 解耦
- 逆变器铭牌照片拍摄 (`inverterMaintenance/index.jsx` + `inverterMaintenanceGf/index.jsx`) 启用 `isNeedCamera=true`
- 通过 Flutter inappwebview bridge 的 `openCamera` handler 调用原生水印相机

#### 业务变更 3: Upload 组件"只拍摄不验真"逻辑
- 当 `isNeedCamera=true` 但 `scanQrCode=false` 时，调用水印相机但不进行二维码验真
- 验真结果处理修复: 成功时硬编码 `"1"`，失败时传 `"0"`

#### 业务变更 4: 审批单张图片驳回开放修改限制
- `RoofImages.jsx`: rejectFlag 从 `0` 改为 `""` (空字符串)，适配二态驳回逻辑
- 放开驳回图片的修改限制

---

### 2. nahui-pv.merchant-micro.zch (dev, HEAD: 5844f7eb)

**最近活跃**: 2026-05-25，开发者: yuanruilin/袁睿林, lining/李宁

#### 业务变更: 零碳结算管理角色扩展
- 路由角色新增 `ZERO_CARBON_E_STATION`，影响 6 个零碳结算管理页面路由
- 结算管理菜单 type 从 `"ZERO_CARBON_USER"` 改为 `"ZERO_CARBON_USER,ZERO_CARBON_E_STATION"`
- 影响子菜单: 对账单 (`/zch/sapPurchase`)、请款申请 (`/zch/paymentRequest`)、发票校验 (`/zch/invoiceVerification`)
- **业务含义**: 零碳适家电站的独立角色 (ZERO_CARBON_E_STATION) 获得结算管理页面访问权限

#### 其他: 请款申请数据字典过滤调整
- `addPaymentRequest.vue`: 调整零碳适家请款申请页面数据字典过滤逻辑 (3行删除)

---

### 3. nahui-pv.merchant-monorepo-h5 (master, HEAD: 32107693)

**状态**: 空壳仓库。最后提交 2024-07-06 (近2年前)，仅有 `.yarnrc.yml` 配置文件。初始化 monorepo 后被 revert。**无业务价值，跳过。**

---

### 4. nahui-pv.osp-mini (dev, HEAD: 6ed9d40e)

**状态**: 低活跃。最后提交 2024-08-27 (近2年前)。运维服务微信小程序，功能包括过程记录和故障字典。**自上次通读以来无新提交，跳过。**

---

### 5. nahuipv-greenergy-management-flutter (master, HEAD: 5dcb0b21)

**状态**: 骨架项目。唯一提交 `init project` (2026-04-07)，仅包含 Flutter 项目骨架配置 (AndroidManifest.xml, pubspec.yaml 等)。应用名 `app_sub_center` (分中心app)。**无实际 Dart 业务代码，跳过。**

---

## 知识库更新

| 文件 | 更新类型 | 内容 |
|---|---|---|
| `domains/station-lifecycle.md` | 追加 | TAEI-3127 前端实现细节: techRejectFlag 字段、cacheEnable 缓存策略变更、存草稿按钮权限变更 |
| `domains/mobile-app-architecture.md` | 追加 | Upload 公共组件架构演进: isNeedCamera 属性、与 scanQrCode 解耦、"只拍摄不验真"逻辑 |
| `domains/inverter-data.md` | 增强 | 逆变器水印相机拍摄: 补充 isNeedCamera 属性细节和架构变更说明 |

## 统计
- 通读仓库: 5/122
- 有业务变更: 2 个
- 知识库更新: 3 个文件
- 新发现业务规则: 5 条 (techRejectFlag, cacheEnable策略, 存草稿权限, isNeedCamera解耦, 零碳角色扩展)
- 全部为代码明确证明 (前端配置证明)
