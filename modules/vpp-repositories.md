# VPP 项目仓库索引

更新时间: 2026-05-15

## API 后端

| 仓库 | 路径 | 状态 | 备注 |
|---|---|---|---|
| vpp-api-common | /data/pvcode/vpp-api-common | 2026-05-13 全量通读 ✅ | VPP API基础框架, JDK 17, 实体/DTO/枚举/i18n |
| vpp-api-elecbusiness | /data/pvcode/vpp-api-elecbusiness | 2026-05-13 全量通读 ✅ | 电力交易/Drcloud对接/纳光宝大屏/XXL-JOB定时任务 |
| vpp-api-ems | /data/pvcode/vpp-api-ems | 2026-05-13 全量通读 ✅ | 能控系统/代理商管理/用户管理/登录鉴权 |
| vpp-api-gateway | /data/pvcode/vpp-api-gateway | 2026-05-13 全量通读 ✅ | Spring Cloud Gateway/JWT鉴权/跨域/异常处理 |
| vpp-api-gect | /data/pvcode/vpp-api-gect | 2026-05-13 全量通读 ✅ | 绿证交易(客户/订单/采购/发票/SAP), JDK 17 |
| vpp-api-auth | /data/pvcode/vpp-api-auth | 已通读 ✅ (2026-07-02) | 认证授权服务 |
| vpp-api-gpower | /data/pvcode/vpp-api-gpower | 2026-06-06 重扫 ✅ (2026-05-14 首扫) | 绿电收益管理/电网公司/MDM主数据/SAP记账/电价数据报表(新增) |
| vpp-api-km | /data/pvcode/vpp-api-km | 2026-06-06 重扫 ✅ (2026-05-14 首扫) | 知识库目录/文件管理/标签/权限控制 (JDK 17升级) |
| vpp-api-meta | /data/pvcode/vpp-api-meta | 2026-06-06 重扫 ✅ (2026-05-14 首扫) | 产品管理/出货日志/Excel导入 |
| vpp-api-system | /data/pvcode/vpp-api-system | 2026-06-06 重扫 ✅ (2026-05-14 首扫) | 用户/部门/角色/菜单/租户/字典/i18n/SSO, JDK 17 |
| vpp-api-template | /data/pvcode/vpp-api-template | 2026-06-06 重扫 ✅ (2026-05-14 首扫) | 模板项目(无业务逻辑, JDK 8) |
| vpp-openapi | /data/pvcode/vpp-openapi | 2026-05-15 全量通读 ✅ | 开放API网关/AK-SK管理/Drcloud数据推送, JDK 17 |
| vpp-pv-oversea | /data/pvcode/vpp-pv-oversea | 2026-05-15 全量通读 ✅ | 海外光伏/电站管理/采购销售/付款计划/SAP/云报账, JDK 17 |

## 数据平台

| 仓库 | 路径 | 状态 |
|---|---|---|
| vpp-data-platform | /data/pvcode/vpp-data-platform | 2026-05-15 全量通读 ✅ |
| vpp-crawler | /data/pvcode/vpp-crawler | 2026-05-15 全量通读 ✅ |

## 前端/H5

| 仓库 | 路径 | 状态 |
|---|---|---|
| he-vpp.admin-h5 | /data/pvcode/he-vpp.admin-h5 | 待通读 |
| he-vpp.hnzl-h5 | /data/pvcode/he-vpp.hnzl-h5 | 待通读 |
| vpp-thai-dashboard | /data/pvcode/vpp-thai-dashboard | 2026-05-16 全量通读 ✅ (泰国大屏/华为FusionSolar集成) |
| vpp-template-ui | /data/pvcode/vpp-template-ui | 2026-05-16 全量通读 ✅ (仅pnpm-workspace.yaml,无业务代码) |

## 移动端

| 仓库 | 路径 | 技术 | 状态 |
|---|---|---|---|
| nahuipv-vpp-hnzl-rn | /data/pvcode/nahuipv-vpp-hnzl-rn | React Native | 待通读 |
| nahuipv-greenergy-management-flutter | /data/pvcode/nahuipv-greenergy-management-flutter | Flutter | 2026-05-19 全量通读 ✅ (分中心app骨架/无Dart业务代码) |
| nahuipv_greenergy_flutter | /data/pvcode/nahuipv_greenergy_flutter | Flutter | 待通读 |
| nahuipv-hnzc-app-android | /data/pvcode/nahuipv-hnzc-app-android | 原生 Android | 待通读 |
| nahuipv-hnzc-app-ios | /data/pvcode/nahuipv-hnzc-app-ios | 原生 iOS | 待通读 |
| nahuipv_business_flutter | /data/pvcode/nahuipv_business_flutter | Flutter | 2026-05-15 全量通读 ✅ (纳光宝APP) |
| nhpv_common_business | /data/pvcode/nhpv_common_business | Flutter | 2026-05-15 全量通读 ✅ (通用组件库) |

## Cordova H5 桥接应用

| 仓库 | 路径 | 技术 | 状态 |
|---|---|---|---|
| esp-mag-haier-android-main | /data/pvcode/esp-mag-haier-android-main | Android+Cordova | 2026-05-15 全量通读 ✅ (海尔H5桥接) |
| esp-mag-haier-ios-main | /data/pvcode/esp-mag-haier-ios-main | iOS+Cordova | 2026-05-15 全量通读 ✅ (海尔H5桥接) |
| esp-mag-haier-h5-portal | /data/pvcode/esp-mag-haier-h5-portal | H5 | 2026-05-15 全量通读 ✅ (空壳) |

## 统计

- **总仓库数**: 29 (含移动端和H5桥接)
- **已通读**: 23 (15个后端 + 2个数据平台 + 2个Flutter移动应用 + 1个Flutter骨架 + 3个Cordova桥接)
- **待通读**: 6
