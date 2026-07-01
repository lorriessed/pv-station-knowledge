# 前端项目与杂项服务分析

> 基于 /data/pvcode/ 下的代码通读分析
> 更新日期: 2026-05-17

---

## 前端项目

### 1. nahui-pv.mobile-h5 - 移动端H5门户

#### 技术栈
- **框架**: React 18 + Vite 4
- **UI库**: antd-mobile 5 + antd 5 (桌面)
- **状态管理**: valtio (轻量响应式)
- **路由**: react-router-dom 6
- **组件缓存**: react-activation (KeepAlive)
- **构建**: Vite + TailwindCSS + Less
- **图表**: echarts 5.3.3
- **其他**: pdfjs-dist, jsqr (二维码), axios

#### 页面/路由
主路由 (src/router/index.jsx) + 模块化路由 (router/modules/*.jsx):

| 路由路径 | 页面 | 说明 |
|---------|------|------|
| `/` | Welcome页 | 入口页 |
| `/home` | 首页 | 主Tab |
| `/shop` | 商城 | 主Tab |
| `/user` | 我的 | 主Tab |
| `/login` | 登录页 | 普通登录 |
| `/vlogin` | VPP登录页 | VPP专用登录 |
| `/enrolment` | 电站登记 | APV-服务商 |
| `/stationDetails` | 电站详情 | YX/ZH/HR等 |
| `/dhStationDetails` | 顶好电站详情 | DH_EPC专用 |
| `/completeAffirm` | 完工确认 | 影像上传 |
| `/accept` | 上传并网资料 | |
| `/inverter/*` | 逆变器管理 | 列表/详情 |
| `/dataBase/index` | 绿能学院资料库 | |
| `/areaManage/*` | 服务区域管理 | |
| `/contract/*` | 合同管理 | 详情/确认 |
| `/pepc/*` | PEPC电站管理 | 统计/电站/发电 |
| `/vpp/*` | VPP虚拟电厂 | 光储/电站详情 |
| `/offline` | 整改影像 | |
| `/policy/*` | 政策管理 | |
| `/store/*` | 库存管理 | 入库/调拨 |
| `/message/*` | 消息管理 | |

#### API 调用
- **Base URL**: `//console.rrsjk.com` (dev) / `//api.rrsjk.com` (prod)
- **Auth**: Basic Auth + OAuth2 token
- **主要 API 文件**: `src/api/index.js`, `src/api/apv.js`, `src/api/vpp.js`, `src/api/pepc.js`
- **API 前缀**: `/merchant/light/`, `/merchant/oss/`, `/merchant/bank/`, `/merchant/app/`, `/oauth2/`

核心 API 端点:
- `/merchant/light/sp/stationListByLnApp.do` - 电站列表
- `/merchant/light/owner/stationOwnerDetail.do` - 业主详情
- `/merchant/light/inveter/lightInveterList.do` - 逆变器列表
- `/merchant/light/station/registHoseholdStation.do` - 户用电站登记
- `/merchant/light/sp/confirmStation.do` - 电站确认
- `/merchant/light/workOrder/workOrderList.do` - 工单列表
- `/merchant/light/databaseManagement/list.do` - 资料库
- `/merchant/light/stopStation/applyStop.do` - 终止申请

#### 业务功能
- **电站登记**: 多品牌（YX越秀/ZH中核/HR华融/DH顶好/GF广发等）的户用/公共建筑/整村电站登记流程
- **完工确认**: 上传完工影像资料（四件套：组件/逆变器/支架/线缆）
- **并网验收**: 上传并网资料，发起并网申请
- **逆变器管理**: 逆变器列表查询与详情
- **服务区域**: 服务商申请/管理区域、签合同
- **工单管理**: 派工/改派工单
- **合同管理**: 电子合同签署、短信触发
- **商城**: 商品浏览与下单
- **VPP**: 虚拟电厂光储管理
- **PEPC**: 特殊品牌电站管理

#### 后端服务映射
- **主服务**: `rrsjk-light-web` (light-service) - `/merchant/light/*`
- **认证服务**: `rrsjk-auth` - `/oauth2/*`
- **OSS服务**: 文件上传 `/merchant/oss/*`
- **银行服务**: `/merchant/bank/*`
- **字典服务**: `nahui-dicts-serve` - `/dictapi`

---

### 2. nahuipv_greenergy_flutter - 绿能Flutter APP

#### 技术栈
- **框架**: Flutter (Dart SDK >=3.3.4 <4.0.0)
- **版本**: 2.2.2+202****1901 (2026-05-20 更新，上次为 2.2.1+202****1401)
- **状态管理**: Riverpod
- **网络**: Dio + retrofit
- **路由**: fluro
- **UI组件**: 自研组件库 + nhpv_common 公共库
- **依赖**: nhpv_common (公共模块)、flutter_screenutil、freezed

#### ⚠️ 新发现: DJI 无人机 SDK 集成 (2026-05-20 通读)

**海尔绿能 APP 集成了 DJI Mobile SDK 用于无人机飞控**：
- **USB 配件**: T600、AG410 (农业无人机)、WM160 (遥控器)、com.dji.logiclink
- **AndroidManifest.xml**: `android.hardware.usb.accessory` 权限 + `com.dji.sdk.API_KEY` meta-data
- **飞控入口**: `activity_aplsh.xml` 包含"点击调用飞控"和"切换App"按钮
- **UXSDK 组件**: 电池状态、飞行模式、避障、RTK 卫星状态、雷达距离等大量 DJI UX 样式
- **DJI API Key**: `d38d5408aa93389e40d53b11` (key.properties)
- **Mapbox**: MAPBOX_DOWNLOADS_TOKEN (gradle.properties)
- **高德地图**: AMap API Key (key.properties)

**⚠️ 安全警告**: DJI API Key、高德 API Key、签名密码明文存储在仓库中。

#### 近期活跃开发 (2026-05-14 ~ 2026-05-19)
- 更换水印相机 Android SDK (修复二维码白边、logo 问题)
- 地图 Key 更新 (chore-map-key)
- 电站列表项优化 (opt-station-list-item)
- 广发业务 (feat_gf) — 与 domains/guangfa-business.md 相关

#### 页面/路由
主要页面模块 (lib/pages/):

| 模块 | 页面 |
|------|------|
| order | 待下单管理（列表/详情/服务区域） |
| station_register | 电站登记（多品牌） |
| audit_station | 审核电站列表与详情 |
| work_order | 派工单管理（列表/搜索/详情） |
| inverter | 逆变器管理 |
| contract | 合同签署管理 |
| message | 消息中心（审批/政策/紧急/文档） |
| college | 绿能学院 |
| store | 库存管理（入库/调拨/商内调拨） |
| stop_station | 电站终止管理 |
| offline_acceptance | 线下验收 |
| basic_info | 基本信息变更 |
| owner_register | 用户登记 |
| search | 搜索功能 |
| policy | 政策查看 |
| personal | 个人中心 |

主页面: `main_page.dart` - 底部Tab导航（首页/消息/我的）

#### API 调用
- **Base URL**: 通过 nhpv_common 的 BaseApi 配置
- **业务 API 前缀**: `/merchant/` (必须以/merchant开头才能通过token校验)
- **H5 嵌入 URL**: BaseApi.baseUrlH5 (跳转到 mobile-h5 页面)
- **主要 API 文件**: `lib/http/nh_api.dart`, `lib/http/rrs_api.dart`

核心 API 端点 (与 mobile-h5 高度一致):
- `/merchant/light/sp/getSpInfo.do` - 服务商信息
- `/merchant/light/sp/stationListByLnApp.do` - 电站列表(APP版)
- `/merchant/light/sp/waitAuditStationList.do` - 审核列表
- `/merchant/light/workOrder/workOrderList.do` - 派工单列表
- `/merchant/light/sp/getYxStationById.do` - 电站详情
- `/merchant/light/constructionTeam/teamList.do` - 施工队列表
- `/merchant/light/inveter/lightInveterList.do` - 逆变器列表
- `/merchant/light/databaseManagement/list.do` - 资料库
- `/merchant/search/history/querySearchHistory` - 搜索历史

#### 业务功能
- **移动端完整业务**: 与 mobile-h5 功能高度重叠，但为原生APP体验
- **电站登记**: 多品牌电站登记、编辑、查看
- **审核管理**: 待审核电站列表，审核操作
- **派工管理**: 派工/改派施工队
- **库存管理**: 仓库入库、调拨、库存查询
- **消息中心**: 审批消息、政策消息、紧急消息、文档消息
- **合同签署**: 在线电子合同签署
- **绿能学院**: 培训资料浏览
- **H5 嵌入**: 部分复杂页面（如电站登记详情页）嵌入 mobile-h5 页面
- **AI助手**: 集成海尔AI聊天页面

#### 后端服务映射
- **主服务**: `rrsjk-light-web` (light-service)
- **认证服务**: `rrsjk-auth`
- **字典服务**: `nahui-dicts-serve`
- **H5嵌入**: `nahui-pv.mobile-h5`

---

### 3. nahui-pv.merchant-micro.osp - OSP服务商管理后台

#### 技术栈
- **框架**: Vue 2.7 + vue-cli
- **UI库**: view-design (iView) 4.7
- **路由**: vue-router 3
- **状态管理**: Vuex 3
- **微前端**: qiankun 2.10 (作为子应用嵌入)
- **构建**: Webpack (vue-cli-service)
- **其他**: echarts, xlsx, perfect-scrollbar

#### 页面/路由
模块化路由 (src/router/modules/):

**osp.js** - OSP主模块:
- 在线签约 (ospReg)
- 保证金管理 (depositList)
- 服务商认证 (ospAuth)
- 电站管理 (station)
- 逆变器管理
- 合同管理
- 工单管理
- 收益管理
- 培训管理 (college)
- 备件管理 (spare)

**commercial.js** - 商业模块:
- 工作台 (workbench)
- 商机列表 (registration)
- 中标公告 (announcement)
- 我的商机
- 响应管理

**ospSpare.js** - 备件子模块
**ospSupplier.js** - 供应商子模块

#### API 调用
- **Base URL**: 通过环境变量配置
- **API 前缀**: `/merchant/`, `/hdsapi/`, `/reportapi/`
- **主要 API 文件**: `src/api/index.js`, `src/api/maintainance.js`
- **微前端**: 通过 qiankun 作为子应用加载，base 路径为 `/mch/${subName}` 或 `/sub/${subName}`

#### 业务功能
- **OSP服务商门户**: 服务商在线签约、资质认证
- **电站运维**: 电站列表、逆变器监控、工单处理
- **商业运营**: 商机管理、中标公告、投标响应
- **备件管理**: 备件库存、备件申请
- **收益管理**: 电站收益查询、对账
- **培训管理**: 在线培训与考核

#### 后端服务映射
- **主服务**: `rrsjk-light-web` (light-service)
- **HDS服务**: `rrsjk-hds-web` (焓图设计)
- **报表服务**: `rrsjk-report-web`
- **认证服务**: `rrsjk-auth`

---

### 4. nahui-dashboad-h5 - 数据大屏看板

#### 技术栈
- **框架**: Vue 3.2 + Vite + TypeScript
- **UI库**: Element Plus
- **状态管理**: Pinia
- **路由**: vue-router 4
- **可视化**: @antv/g2, @antv/l7, @antv/l7plot (地图+图表)
- **国际化**: vue-i18n
- **构建**: Vite

#### 页面/路由
- 数据大屏首页 (Dashboard)
- 覆盖区域地图
- 节能减排统计
- 并网信息
- 安装信息统计
- 月发电量
- 获单信息
- 建站排行榜
- 运维工单统计

#### API 调用
- **Base URL**: `//console.rrsjk.com`
- **API 前缀**: `/reportapi/light/screen/`
- **主要 API 文件**: `src/api/index.ts`

核心 API 端点:
- `/reportapi/light/screen/getCoverageArea.do` - 覆盖区域
- `/reportapi/light/screen/getEnergy.do` - 节能减排
- `/reportapi/light/screen/getGrid.do` - 并网信息
- `/reportapi/light/screen/getInstallt.do` - 安装信息
- `/reportapi/light/screen/getMap.do` - 地图信息
- `/reportapi/light/screen/getMonthElectricity.do` - 月发电量
- `/reportapi/light/screen/getOrder.do` - 获单信息
- `/reportapi/light/screen/getStationRank.do` - 建站排行榜
- `/reportapi/light/screen/getWorkOrderCount.do` - 工单统计

#### 业务功能
- **运营数据大屏**: 可视化展示光伏电站整体运营数据
- **地图展示**: L7 地图展示电站分布、覆盖区域
- **数据图表**: G2 图表展示发电量、安装量、工单等趋势
- **排行榜**: 建站排行榜、公司排行
- **实时监控**: 并网状态、运维工单状态

#### 后端服务映射
- **报表服务**: `rrsjk-report-web` - `/reportapi/*`
- **数据源**: `rrsjk-light-web` (light-service) 的 Dubbo 服务

#### 2026-06-01 变更
- **globalCapital 组件大规模删除**: `src/components/globalCapital/` 整个目录删除（约 2,500+ 行），包括 Complete/Core/Coverage/CutEmissions/SellData/Statistics/assetCoverage/assetSituation/electricityTrading 等 8+ 个全局资本组件。同时删除了大量全局样式文件（globalCapital.less、globalAssetCalc.less 等）。
- **资方数据运算修复**: `src/components/capital/sellDataScroll.vue` 修复资方数据计算逻辑。
- **推断**: globalCapital（全球资本/全球收入）模块可能被迁移到独立大屏或新架构中。

---

### 5. nahui-dicts-serve - 字典服务

#### 技术栈
- **框架**: Node.js + Koa 2
- **路由**: koa-router
- **文档**: koa2-swagger-ui (Swagger API文档)
- **跨域**: koa2-cors
- **静态文件**: koa-static
- **服务端口**: 3088
- **模块类型**: ESM (type: module)

#### 页面/路由
这不是前端项目，而是轻量级 Node.js 后端服务：
- `/dictapi` - 字典查询接口
- `/swagger` - Swagger API文档页面
- `/src/static/` - 静态资源

#### API 调用
- **端口**: 3088
- **接口**: GET only (methods: ['GET'])
- **CORS**: 白名单模式，精确匹配 origin
- **Swagger**: 提供 `/swagger.json` 和 UI

#### 业务功能
- **数据字典服务**: 提供全局数据字典查询
- **静态资源托管**: 托管 Swagger 文档和静态文件
- **跨域支持**: 白名单模式 CORS

#### 后端服务映射
- **独立服务**: 自身即为后端服务，被前端项目调用
- **被调用方**: mobile-h5, Flutter APP 等前端项目

---

### 6. nahui-pv.merchant-micro.zch - 零碳适家管理后台

#### 技术栈
- **框架**: Vue 2.7 + vue-cli
- **UI库**: view-design 4.7 + vxe-table 3.12 + vxe-pc-ui 3.3
- **路由**: vue-router 3
- **状态管理**: Vuex 3
- **微前端**: qiankun (作为子应用嵌入)
- **PDF**: vue-pdf
- **表格**: vxe-table (高性能表格)
- **其他**: xlsx, js-base64

#### 页面/路由
模块化路由 (src/router/):

**zeroCarbon.js** - 零碳模块:
- 首页/工作台
- 项目管理
- 电站管理
- 合同管理

**zchStore.js** - 零碳适家商城模块:
- 商品管理
- 订单管理
- 用户管理

#### API 调用
- **微前端**: base 路径 `/mch/${subName}` 或 `/sub/${subName}`
- **主要 API**: `src/api/index.js`
- **API 前缀**: `/merchant/`, `/oauth2/`

核心 API 端点:
- `/oauth2/oauth/token` - 登录/刷新token
- `/merchant/member/reg/do_regist.do` - 用户注册
- `/merchant/item/category/children.do` - 商品分类
- `/merchant/item/spu/find_by_category.do` - 商品列表
- `/merchant/item/item/releaseItem.do` - 发布商品

#### 业务功能
- **零碳适家商城**: 商品管理（分类/SPU/SKU）、商品发布
- **订单管理**: 订单处理、保本价查询
- **项目管理**: 零碳项目管理
- **电站管理**: 电站数据查看
- **用户管理**: 用户注册、信息维护
- **与OSP版本对比**: zch 版本增加了商城/商品功能，使用 vxe-table 替代纯 view-design

#### 后端服务映射
- **主服务**: `rrsjk-light-web` (light-service)
- **认证服务**: `rrsjk-auth`
- **商品服务**: `rrsjk-item-service` (item-service)

---

### 7. nahui-pv.construction-mini - 施工队微信小程序

#### 技术栈
- **框架**: 微信原生小程序 (TypeScript)
- **UI组件**: @vant/weapp 1.10
- **监控**: @arms/rum-miniapp (阿里云监控)
- **部署**: miniprogram-ci (自动上传)
- **语言**: TypeScript

#### 页面/路由
小程序页面 (miniprogram/pages/):

| 页面 | 路径 | 说明 |
|------|------|------|
| 首页 | pages/home/index | 底部Tab: 首页 |
| 准备中 | pages/preparation/index | 待准备电站列表 |
| 准备详情 | pages/preparation/detail | 电站准备详情 |
| 签到 | pages/preparation/sign | 现场签到 |
| 发现 | pages/discover/index | 底部Tab: 发现 |
| 我的 | pages/user/index | 底部Tab: 我的 |
| 工单 | pages/order/index | 工单列表 |
| 加入工单 | pages/order/join | 加入工单 |
| 屋顶信息 | pages/order/roof | 屋顶数据录入 |
| 工程管理 | pages/engin/index | 底部Tab: 工程 |
| 工程信息 | pages/engin/information | 工程信息录入 |
| 分包管理 | pages/engin/subManagement | 分包商管理 |
| 逆变器信息 | pages/engin/inverterInfo | 逆变器信息 |
| 组件计数 | pages/engin/componentCount | 组件清点 |
| 拍照 | pages/camera | 拍照上传 |
| 评价 | pages/evaluate | 工程评价 |
| 客服 | pages/customerService | 在线客服 |

#### API 调用
- **API 文件**: `miniprogram/wxapi/`
- **请求方式**: wx.request 封装

#### 业务功能
- **施工全流程**: 签到→准备→施工→验收→评价
- **工单管理**: 工单列表、加入工单、执行工单
- **现场作业**: 屋顶信息采集、组件清点、逆变器安装信息
- **分包管理**: 分包商管理、施工记录
- **签到打卡**: GPS定位签到
- **拍照上传**: 现场照片拍摄与上传
- **工程评价**: 完工评价

#### 后端服务映射
- **主服务**: `rrsjk-light-web` (light-service)
- **认证服务**: `rrsjk-auth`

---

### 8. nahui-pv.hds-h5 - HDS焓图设计管理后台

#### 技术栈
- **框架**: Vue 3.2 + Vite
- **UI库**: Element Plus
- **状态管理**: Pinia
- **路由**: vue-router 4
- **BPMN**: bpmn-js 7.5 (流程设计器)
- **富文本**: Quill 2.0
- **表单设计**: vform3-builds 3.0
- **图表**: echarts 5.4
- **打印**: print-js

#### 页面/路由
模块化路由 (src/router/*.js):

| 模块文件 | 功能域 |
|---------|--------|
| index.js | 首页/登录 |
| baseData.js | 基础数据管理 |
| processManage.js | 流程管理 (BPMN) |
| bidding.js | 招投标管理 |
| epc.js | EPC项目管理 |
| epp.js | EPP管理 |
| rent.js | 租赁管理 |
| maintainance.js | 运维管理 |
| workManage.js | 工作管理 |
| dataBoard.js | 数据看板 |
| automaticDrawing.js | 自动设计 (焓图) |
| sparePartsManage.js | 备件管理 |
| sparePartsSettlement.js | 备件结算 |
| sparePartMonitor.js | 备件监控 |
| osp.js | OSP管理 |
| pvEnergy.js | 光伏能源 |
| socialization.js | 社交化 |
| sys.js | 系统管理 |

#### API 调用
- **Base URL**: `//console.rrsjk.com` (dev) / `//api.rrsjk.com` (prod)
- **Auth**: Basic Auth (hds:9859fd...)
- **API 前缀**: `/hdsapi/`, `/oauth2/`
- **IDM集成**: 海尔IDM单点登录 (iama.haier.net)
- **焓图服务**: `https://itest.ytusmart.com` (测试) / `https://api.ytusmart.com` (生产)

核心 API 端点:
- `/oauth2/oauth/token` - 登录
- `/hdsapi/system/menu/menus.do` - 菜单树
- `/hdsapi/yantuData/findPage.do` - 焓图数据管理
- `/hdsapi/yantuData/doExport.do` - 焓图数据导出
- `/oauth2/oauth/hds_idmlogin` - 海尔IDM登录

#### 业务功能
- **焓图设计**: 光伏电站自动设计、CAD图管理
- **流程设计**: BPMN流程设计器，可视化配置审批流程
- **招投标**: 招标发布、投标响应、中标管理
- **EPC/EPP管理**: 工程总承包/工程采购项目管理
- **租赁管理**: 设备租赁业务
- **运维管理**: 运维工单、巡检管理
- **备件管理**: 备件库存、采购、结算
- **数据看板**: 运营数据统计
- **基础数据**: 主数据管理（商品、供应商、客户等）
- **表单设计**: 可视化表单设计器

#### 后端服务映射
- **HDS服务**: `rrsjk-hds-web` - `/hdsapi/*`
- **认证服务**: `rrsjk-auth`
- **焓图服务**: ytusmart.com (外部服务)
- **IDM**: 海尔统一身份认证

---

## 后端服务

### 9. rrsjk-light-message-service - 消息服务

#### 服务定位
光伏电站业务消息中心，提供审批消息、文档消息、政策消息、紧急消息等类型的消息管理，以及用户消息关系管理和消息搜索功能。

#### 项目结构
- **模块**: `rrsjk-light-message-api` (接口定义) + `rrsjk-light-message-impl` (实现)
- **Java文件**: 84个

#### 所有 API/Service (Dubbo 暴露)
通过 `spring-config/service.xml` 配置:

**Dubbo 暴露 (dubbo:service)**:
| Service | 说明 |
|---------|------|
| `ApprovalMessageService` | 审批消息服务 |
| `DocumentMessageService` | 文档消息服务 |
| `PolicyMessageService` | 政策消息服务 |
| `UrgentMessageService` | 紧急消息服务 |
| `UserMessageRelationService` | 用户消息关系服务 |
| `MessageSearchHistoryService` | 消息搜索历史服务 |
| `UrgentMessageScopeService` | 紧急消息范围服务 |
| `OverdueStationNotifyJobService` | 超期电站通知定时任务 |

**Dubbo 引用 (dubbo:reference)**:
| Service | 说明 |
|---------|------|
| `LightStationService` | 电站服务 (来自 light-service) |
| `LightServiceProviderService` | 服务商服务 (来自 light-service) |
| `LightSubSpService` | 子服务商服务 (来自 light-service) |

#### 核心业务逻辑
- **消息分类管理**: 审批/文档/政策/紧急四种消息类型，各自独立CRUD
- **用户消息关联**: user_message_relations 表记录用户与消息的关联关系（已读/未读状态）
- **紧急消息范围**: 紧急消息可指定接收范围（按角色/部门/用户）
- **消息搜索**: 支持搜索历史记录
- **RocketMQ集成**: 通过 MQ 消费消息推送事件
- **定时任务**: OverdueStationNotifyJob 定期通知超期未处理电站
- **短信集成**: 阿里云短信 (AcsClientConfig)
- **OSS存储**: 消息附件存储

#### 数据库表
通过 MyBatis Mapper XML 推断:
| 表名 | 说明 |
|------|------|
| `approval_message` | 审批消息表 |
| `document_message` | 文档消息表 |
| `policy_message` | 政策消息表 |
| `urgent_message` | 紧急消息表 |
| `user_message_relations` | 用户消息关联表 |
| `message_search_history` | 消息搜索历史表 |
| `urgent_message_scope` | 紧急消息范围表 |

#### Dubbo 配置
- **注册中心**: Zookeeper
- **超时**: 10000ms
- **配置中心**: Zookeeper ConfigCenter

---

### 10. rrsjk-pvbusiness-job-service - 光伏业务定时任务服务

#### 服务定位
光伏电站业务定时任务调度中心，负责仓库库龄分析、资产数据同步、逾期库存控制等后台批处理任务。

#### 项目结构
- **模块**: `rrsjk-pvbusiness-job-api` (接口定义) + `rrsjk-pvbusiness-job-impl` (实现)
- **Java文件**: 70个

#### 所有 API/Service (Dubbo 暴露)
**Dubbo 暴露 (dubbo:service)**:
| Service | 说明 |
|---------|------|
| `SampleJobService` | 示例定时任务 (async=true) |
| `LightOwnAssetService` | 自有资产服务 (已注释) |

**Dubbo 引用**:
| Service | 说明 |
|---------|------|
| `ProductPriceService` | 商品价格服务 (已注释) |

#### 核心业务逻辑
- **定时任务框架**: 自研 `@SingleJob` 注解 + AOP 切面，分布式锁防并发 (详见下方 SingleJob 机制)
- **仓库库龄分析**: GvsWarehouseAgeAnalysis - 从 GVS 系统同步仓库库龄数据 (库龄分段: 1-30天→3年以上)
- **逾期库存控制**: EnergyOverdueInventoryControl - 多维度逾期库存管控（总表/中心/SKU/基础数据）
- **资产数据同步**: LightOwnAsset - 光伏电站自有资产数据同步 (导入→推送HSCC→状态回查)
- **SAP集成**: SapSpCenterRelation - SAP SP 中心关系数据同步
- **数据源**: 7个数据源 — light (主库), report (报表库), local (本地库), elec, operation, shop, finance

#### SingleJob 分布式锁机制 (代码明确证明, 2026-06-03)
**来源**: `SingleJob.java`, `SingleJobAspect.java`

```java
@SingleJob(jobName = "sampleJob", maxLockTimeMilliSeconds = 90000, skipOnLockFail = true)
```

- **Redis 分布式锁**: Key 格式 `single_job_lock_{className}.{methodName}`
- **锁续期 (Watchdog)**: 每 maxLockTime/3 自动续期，确保长任务不丢锁
- **skipOnLockFail 策略**:
  - `true`(默认): 获取锁失败 → 跳过执行，60秒内最多打印一次跳过日志
  - `false`: 获取锁失败 → 降级模式继续执行 (无锁保护)
- **全局开关**: `${single-job.enabled:true}` 配置控制是否启用
- **线程池隔离**: `jobExecutor` (8~40线程, CallerRunsPolicy) 执行任务体
- **异常清理**: 无论任务成功/失败，finally 块中取消续期 + 释放锁

#### LightOwnAsset 资产推送流程 (代码明确证明, 2026-06-03)
**来源**: `LightOwnAssetServiceImpl.java`, `LightAssetInterfaceServiceImpl.java`

1. **资产导入**: Excel批量导入 → 校验(合同号/租赁类型/税种/发票选项/付款类型/付款周期) → 生成CBS单号(LOA+yyyyMMdd+6位序列) → 插入 `light_own_asset`
2. **异步推送**: 导入成功后通过 `pushAssetExecutor` 线程池异步调用 HSCC 资产系统
   - 签名: `Application-Key + X-Yx-Nonce + X-Yx-Timestamp` → HMAC
   - 推送成功 → 状态更新为 `TRANSFERRED`
3. **状态回查**: `queryAssetStatusJob()` 定时拉取 `TRANSFERRED`/`WAIT_AUDIT` 状态
   - 调用 HSCC 查询接口 → 解析审批节点/审批人/驳回原因 → 写入 `light_own_asset_status`

**资产状态**: `IMPORTED` → `TRANSFERRED` → `WAIT_AUDIT` / `ERROR`

**HSCC 接口**:
- 申请: `http://hscapi.haier.net/Product/CBS-RightOfUseAsset/ApplicationInterface`
- 查询: `http://hscapi.haier.net/Product/CBS-RightOfUseAsset/QueryInterface`

#### 数据库表
| 表名 | 说明 |
|------|------|
| `gvs_warehouse_age_analysis` | GVS仓库库龄分析表 |
| `energy_overdue_inventory_control_summary` | 逾期库存控制汇总表 |
| `energy_overdue_inventory_control_center` | 逾期库存控制中心表 |
| `energy_overdue_inventory_control_sku` | 逾期库存控制SKU表 |
| `energy_overdue_inventory_control_data_base` | 逾期库存控制数据库表 |
| `sap_sp_center_relation` | SAP SP中心关系表 |
| `light_own_asset` | 自有资产表 |
| `light_own_asset_status` | 自有资产状态表 |
| `light_asset_application_log` | 资产申请日志表 |

#### Dubbo 配置
- **注册中心**: Zookeeper
- **任务调度**: 自研 JobConfig + XXL-JOB 集成

---

### 11. rrsjk-light-openapi-service - 光伏业务开放接口服务

#### 服务定位
光伏电站业务对外开放 API 服务，为第三方系统（如招银租赁、GVS等）提供数据对接接口。

#### 项目结构
- **模块**: `rrsjk-light-openapi-api` (接口定义) + `rrsjk-light-openapi-impl` (实现)
- **Java文件**: 76个

#### 所有 API/Service (Dubbo 暴露)
**Dubbo 暴露 (dubbo:service)**:
| Service | 说明 |
|---------|------|
| `LightOwnAssetService` | 自有资产服务 (timeout=60000) |
| `ZhaoYinLeaseService` | 招银租赁服务 (timeout=60000) |

#### 核心业务逻辑
- **招银租赁对接**: ZhaoYinLeaseService - 向招商银行提供光伏电站数据
  - 电站电费数据: `ZhaoYinElectricityBillDto`
  - 电站发电量: `ZhaoYinStationElecDto`
  - 逆变器功率: `ZhaoYinInverterPowerDto`
  - 电站状态: `ZhaoYinStationStatusDto`
- **GVS对接**: GvsWarehouseAgeAnalysis - 仓库库龄数据导出
- **资产管理**: LightOwnAsset - 自有资产管理
- **资产接口服务**: LightAssetInterfaceService - 资产申请/推送/查询
- **多数据源**: light (主库), report (报表库), local (本地库), ods (ODS库)
- **RSA加密**: NhoisRSAUtil - 接口数据安全传输
- **签名校验**: SignatureUtil - 接口请求签名验证

#### 数据库表
| 表名 | 说明 |
|------|------|
| `gvs_warehouse_age_analysis` | GVS仓库库龄分析表 |
| `energy_overdue_inventory_control_*` | 逾期库存控制系列表 |
| `energy_leased_station_asset_management` | 租赁电站资产管理表 |
| `sap_sp_center_relation` | SAP SP中心关系表 |
| `light_own_asset` | 自有资产表 |
| `light_own_asset_status` | 自有资产状态表 |
| `light_asset_application_log` | 资产申请日志表 |
| `light_project_electric_order` | 项目电费订单表 |
| `ods_light_station_elec` | ODS电站电费表 |

#### Dubbo 配置
- **注册中心**: Zookeeper
- **超时**: 默认 + 特定服务60s超时

---

### 12. rrsjk-report-web - 报表大屏服务

#### 服务定位
光伏电站报表数据大屏 Web 服务，提供运营看板、资产大屏、各金融方（招行/普银/中核/越秀/华融等）专属看板的数据接口。

#### 项目结构
- **单模块**: 标准 Spring Boot Web 项目
- **Java文件**: 75个
- **技术**: Spring Boot + Dubbo + MyBatis

#### 所有 API/Controller
**HTTP Controller**:
| Controller | 说明 |
|-----------|------|
| `ReportScreenController` | 数据大屏主接口 |
| `ReportAssetScreenController` | 资产大屏接口 |
| `HuarongDashboardController` | 华融看板 |
| `PuyinDashboardController` | 普银看板 |
| `CnncDashboardController` | 中核看板 |
| `CmbDashboardController` | 招行看板 |
| `YueXiuDashboardController` | 越秀看板 |
| `BocDashboardController` | 中行看板 |

**大屏鉴权模式 (代码明确证明, 2026-06-03)**:
- **SF_TOKEN**: 各资方大屏 (`/light/screen/{boc|cmb|cnnc|huarong|yuexiu|*`) 使用 `SF_TOKEN` 硬编码校验
- **ASF_TOKEN**: 资产大屏 (`/light/screen/asset/*`) 使用 `ASF_TOKEN` 硬编码校验
- **Fallback 机制**: 当指定日期无数据时，自动回退到前一天数据 (`LocalDate.now().minusDays(1)`)

**新增: 工商业并网维度 (2026-03-10)**:
- `ReportAssetScreenCmGridService` — 工商业电站月/年/累计并网数量及装机容量
- 接口: `getCmGrid.do` → `/light/screen/asset/getCmGrid.do`

**新增: 工单数量统计接口 (2026-04-28)**:
- `ReportAssetScreenWorkOrderService` — 获取工单数量统计
- 接口: `getWorkOrderCount.do` → `/light/screen/asset/getWorkOrderCount.do`
- 开发者: laowang, commit 0b157ce4

**Adapter 模式**: 通过 Adapter 层聚合多个数据源
| Adapter | 说明 |
|---------|------|
| `CoverageAreaAdapter` | 覆盖区域数据 |
| `EnergyAdapter` | 节能减排数据 |
| `GridAdapter` | 并网数据 |
| `InstallAdapter` | 安装数据 |
| `MapAdapter` | 地图数据 |
| `OrderAdapter` | 获单数据 |
| `StationRankAdapter` | 建站排行 |
| `ElectricityAdapter` | 发电量数据 |
| 各种 Asset*Adapter | 资产大屏各维度数据 |

#### Dubbo 引用
该服务**不暴露 Dubbo 服务**，仅作为 Dubbo 消费者调用其他服务:

| 引用服务 | 说明 | 超时 |
|---------|------|------|
| `MemberRoleService` | 成员角色服务 | - |
| `ReportScreenCountyService` | 县域大屏数据 | 1000s |
| `ReportScreenEnergyService` | 节能减排数据 | 1000s |
| `ReportScreenGridService` | 并网数据 | 1000s |
| `ReportScreenInstallService` | 安装数据 | - |
| `ReportScreenInstallShaftService` | 安装横轴数据 | 1000s |
| `ReportScreenMapService` | 地图数据 | 1000s |
| `ReportScreenMonthElecService` | 月发电量数据 | 1000s |
| `ReportScreenOrderService` | 获单数据 | - |
| `ReportScreenStationRankService` | 建站排行 | 1000s |
| `LightWorkOrderService` | 工单服务 | 1000s |
| `WorkOrderCountService` | 工单统计 | 1000s |
| `CmbDashboard` | 招行看板 | 1000s |
| `BocDashboard` | 中行看板 | 1000s |
| `CnncDashboard` | 中核看板 | 1000s |
| `YueXiuDashboard` | 越秀看板 | 1000s |
| `PuyinDashboard` | 普银看板 | 1000s |
| `HuaRongDashboard` | 华融看板 | 1000s |
| `RegionService` | 区域服务 | - |
| `ReportAssetScreenRentService` | 资产租金数据 | 1000s |
| `ReportAssetScreenInvestorDataService` | 投资人数据 | 1000s |
| `ReportAssetScreenElectricRevenueService` | 电费收入数据 | 1000s |
| `ReportAssetScreenCompanyRevenueService` | 公司收入数据 | 1000s |
| `ReportAssetScreenWorkOrderService` | 资产工单数据 | 1000s |
| `ReportAssetScreenProvinceGridService` | 省份并网数据 | 1000s |
| `ReportAssertStationInfo` | 电站信息 | - |
| `ReportAssetScreenCmGridService` | CM并网数据 | - |
| `LightOperationDashboardService` | 运营看板 | - |

#### 核心业务逻辑
- **数据大屏**: 聚合多维度数据，提供大屏展示接口
- **多金融方看板**: 为不同金融机构提供定制化数据看板
- **Adapter 模式**: 每个数据维度通过 Adapter 接口聚合，支持多数据源切换
- **报表数据**: 从报表库/ODS库读取统计数据
- **安全过滤**: XssFilter + AccessToken 校验
- **OAuth2**: Oauth2Config 接口权限控制

#### 数据库表
- 主要使用报表数据库 (report DB)
- 通过 Dubbo 引用从其他服务获取实时数据
- 不直接管理业务表

#### Dubbo 配置
- **注册中心**: Zookeeper
- **仅消费者**: 该服务只消费 Dubbo 服务，不暴露

---

## 前后端映射总结

| 前端项目 | 主要后端服务 | API 前缀 |
|---------|------------|---------|
| mobile-h5 | light-service, auth-service | `/merchant/light/*`, `/oauth2/*` |
| greenergy_flutter | light-service, auth-service | `/merchant/*` |
| merchant-micro.osp | light-service, hds-web, report-web | `/merchant/*`, `/hdsapi/*` |
| dashboad-h5 | report-web | `/reportapi/*` |
| dicts-serve | 自身为后端服务 | `/dictapi` |
| merchant-micro.zch | light-service, item-service | `/merchant/*` |
| construction-mini | light-service | wx.request 封装 |
| hds-h5 | hds-web, auth-service | `/hdsapi/*` |

| 后端服务 | 角色 | Dubbo |
|---------|------|-------|
| light-message-service | 消息中心 | 暴露 8 个 Service, 引用 3 个 Service |
| pvbusiness-job-service | 定时任务 | 暴露 1 个 Service |
| light-openapi-service | 开放接口 | 暴露 2 个 Service |
| report-web | 报表大屏 | 仅消费者, 引用 28 个 Service |

---

## 技术层面整体提高体验（2026年6月规划）

> 来源：用户提供的技术规划幻灯片（2026-06-07，水印：杨铭）
> ⚠️ **重要：这是海尔新能源整体平台的架构升级，与海外系统无关。**

### 四大关键任务

| 任务 | 状态 | 负责人 | 说明 |
|---|---|---|---|
| **发电数据迁移** | 持续推进中 | — | 新旧系统发电数据对齐，全面排查发电服务相关业务逻辑 |
| **CBS系统重构** | 进展顺利 | 于淼 | 结合 Codex 持续优化迭代，暂无需外部技术支持 |
| **系统整体架构升级** | 计划阶段 | — | JDK→17, Dubbo→3.9+, 注册中心→Nacos, 全面容器化部署 |
| **定时任务服务升级** | 计划阶段 | — | XXL-JOB 统一替换为 SnailJob，提升调度稳定性与效率 |

### 架构升级详情
- **JDK**: 当前版本 → **17**
- **Dubbo**: 当前 2.7.4 → **3.9+**
- **注册中心**: Zookeeper → **Nacos**
- **部署方式**: 传统部署 → **全面容器化**
- **定时任务**: XXL-JOB → **SnailJob**

### ⚠️ 与海外二期的关系
- 四项技术升级是**海尔新能源整体平台**的基础设施层升级
- 与海外系统（海外二期）**无直接关系**
- 海外二期作为新建业务，应**基于**新架构栈开发（受益方而非升级对象）

