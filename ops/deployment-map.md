# 生产部署拓扑与 /deployment 发版脚本地图

更新时间：2026-05-10

来源：通过 SSH 只读检查各生产服务器 `/deployment` 目录及脚本内容。`10.2.160.221`、`10.2.160.222` 已在 2026-05-10 补充读取，nginx 详细域名、upstream、H5 静态目录和发版脚本见 `ops/nginx-route-map.md`。

## 服务器角色

| IP | 主机名/角色 | 部署定位 |
|---|---|---|
| 10.2.160.221 | rrsjk-prod-nginx1-10-2-160-221 | 生产 nginx1，静态 H5 和反向代理；详见 `ops/nginx-route-map.md` |
| 10.2.160.222 | rrsjk-prod-nginx2-10-2-160-222 | 生产 nginx2，静态 H5 和反向代理；详见 `ops/nginx-route-map.md` |
| 10.2.160.228 | rrsjk-prod-api1-10-2-160-228 | API Web 层，和 229 镜像部署 |
| 10.2.160.229 | rrsjk-prod-api2-10-2-160-229 | API Web 层，和 228 镜像部署 |
| 10.2.160.230 | rrsjk-prod-web1-10-2-160-230 | 传统 Web/Tomcat 层，和 231 大体镜像部署 |
| 10.2.160.231 | rrsjk-prod-web2-10-2-160-231 | 传统 Web/Tomcat 层，含 finance jetty |
| 10.2.160.232 | rrsjk-prod-dubbo1-10-2-160-232 | Dubbo/业务服务层，和 233 大体镜像部署 |
| 10.2.160.233 | rrsjk-prod-dubbo2-10-2-160-233 | Dubbo/业务服务层，和 232 大体镜像部署 |
| 10.2.160.234 | rrsjk-prod-dispenser1-10-2-160-234 | dispenser/light-data 专用服务层 |
| 10.2.160.235 | rrsjk-prod-dispenser2-10-2-160-235 | dispenser/light-data 专用服务层 |
| 10.2.160.236 | rrsjk-prod-dubbo3-10-2-160-236 | dubbo3/light 服务节点 |

## 10.2.160.228 / 10.2.160.229 API Web 层

这些机器上的 `/deployment` 脚本主要发布 API 类 Web 服务。多数服务部署在 `/data/tomcat/apache-tomcat-9.0.12-*`，打包格式多为 `*.tar.gz` 或 `api.war`，启动方式是服务自己的 `bin/<service>` 或 Tomcat `startup.sh`。

| 脚本 | 服务/包 | 目标路径 | 启动入口 |
|---|---|---|---|
| deploy_api_web.sh | api.war | /data/tomcat/apache-tomcat-9.0.12-api/webapps/ | Tomcat startup.sh |
| deploy_payapi_web.sh | rrsjk-pay-web.tar.gz | /data/tomcat/apache-tomcat-9.0.12-payapi | rrsjk-pay-web/bin/rrsjk-pay-web |
| deploy_rrsjk_appapi_web.sh | rrsjk-appapi-web.tar.gz | /data/tomcat/apache-tomcat-9.0.12-rrsjk-appapi-web | rrsjk-appapi-web/bin/rrsjk-appapi-web |
| deploy_rrsjk_hdsapi_web.sh | rrsjk-hds-web.tar.gz | /data/tomcat/apache-tomcat-9.0.12-hds | rrsjk-hds-web/bin/rrsjk-hds-web |
| deploy_rrsjk_merchant_web.sh | rrsjk-merchant-web.tar.gz | /data/tomcat/apache-tomcat-9.0.12-merchant | rrsjk-merchant-web/bin/rrsjk-merchant-web |
| deploy_rrsjk_mobile_web.sh | rrsjk-mobile-web.tar.gz | /var/tomcat/apache-tomcat-9.0.12-rrsjk-mobile-web | rrsjk-mobile-web/bin/rrsjk-mobile-web |
| deploy_rrsjk_oauth2_web.sh | rrsjk-oauth2-web.tar.gz | /data/tomcat/apache-tomcat-9.0.12-oauth2 | rrsjk-oauth2-web/bin/rrsjk-oauth2-web |
| deploy_rrsjk_openapi-web.sh | rrsjk-openapi-web.tar.gz | /data/tomcat/apache-tomcat-9.0.12-openapi-web | rrsjk-openapi-web/bin/rrsjk-openapi-web |
| deploy_rrsjk_report_web.sh | rrsjk-report-web.tar.gz | /data/tomcat/apache-tomcat-9.0.12-report | rrsjk-report-web/bin/rrsjk-report-web |
| kkFileView.sh | kkFileView-4.4.0-beta.tar.gz | /data/deploy/kkFileView | kkFileView bin start/stop |

Codeup 子目录里有 `deploy_rrsjk_hds_web.sh`、`merchant_web.sh`、`report_web.sh` 等脚本，目标路径与上表同类服务一致，只是包文件由脚本入参 `$1` 传入。

## 10.2.160.230 / 10.2.160.231 Web/Tomcat 层

这两台主要承载传统 Web 应用，多数脚本将 WAR 发布为对应 Tomcat 的 `webapps/ROOT.war`，然后重启对应 Tomcat。

| 服务 | 目标路径 |
|---|---|
| admin | /data/tomcat/apache-tomcat-9.0.12-admin/webapps/ROOT.war |
| cart | /data/tomcat/apache-tomcat-9.0.12-cart/webapps/ROOT.war |
| cbs-web | /data/tomcat/apache-tomcat-9.0.12-cbs-web/webapps/ROOT.war |
| console | /data/tomcat/apache-tomcat-9.0.12-console/webapps/ROOT.war |
| dispenser-web | /data/tomcat/apache-tomcat-9.0.12-dispenser/webapps/ROOT.war |
| image | /data/tomcat/apache-tomcat-9.0.12-image/webapps/ROOT.war |
| item | /data/tomcat/apache-tomcat-9.0.12-item/webapps/ROOT.war |
| mall/shopmall | /data/tomcat/apache-tomcat-9.0.12-shopmall/webapps/ROOT.war |
| member | /data/tomcat/apache-tomcat-9.0.12-member/webapps/ROOT.war |
| mobile-web | /data/tomcat/apache-tomcat-9.0.12-mobile-web/webapps/ROOT.war |
| pay | /data/tomcat/apache-tomcat-9.0.12-pay/webapps/ROOT.war |
| search | /data/tomcat/apache-tomcat-9.0.12-search/webapps/ROOT.war |
| seller | /data/tomcat/apache-tomcat-9.0.12-seller/webapps/ROOT.war |

其他独立包服务：

| 脚本 | 服务/包 | 目标路径 | 启动入口 |
|---|---|---|---|
| deploy_portal_web.sh | portal-web.tar.gz | /data/tomcat/apache-tomcat-9.0.12-portal | portal-web/bin/portal-web |
| deploy_rrsjk_admin_web.sh | rrsjk-admin-web.tar.gz | /data/tomcat/apache-tomcat-9.0.12-rrsjk_admin | rrsjk-admin-web/bin/rrsjk-admin-web |
| deploy_rrsjk_app_web.sh | rrsjk-app-web.tar.gz | /data/tomcat/apache-tomcat-9.0.12-rrsjk-app-web | rrsjk-app-web/bin/rrsjk-app-web |
| deploy_finance_web.sh | finance web WAR | /data/tomcat/jetty-distribution-9.4.15.v20190215/webapps/ | jetty.sh |

`deploy_finance_web.sh` 只在 10.2.160.231 上看到。Codeup 子目录有 `deploy_cbs_web.sh` 等，属于同一类 Tomcat ROOT 发布方式。

## 10.2.160.232 / 10.2.160.233 Dubbo/业务服务层

这两台是核心 Dubbo/业务服务节点，脚本大多把 `*-impl.tar.gz` 发布到 `/data/deploy/job-deploy-*`，再执行 `bin/<service>` 的 stop/start。

| 脚本/服务 | 包 | 目标路径 | 启动入口/应用标识 |
|---|---|---|---|
| deploy_rrsjk_light_service.sh | rrsjk-light-impl.tar.gz | /data/deploy/job-deploy-rrsjk-light | rrsjk-light-impl/bin/rrsjk-light-impl，light.Application |
| deploy_rrsjk_light_report_service.sh | rrsjk-light-report-impl.tar.gz | /data/deploy/job-deploy-rrsjk-light-report | rrsjk-light-report-impl/bin/rrsjk-light-report-impl，report.Application |
| deploy_rrsjk_light_operation_service.sh | rrsjk-light-operation-impl.tar.gz | /data/deploy/job-deploy-rrsjk-light-operation | rrsjk-light-operation-impl/bin/rrsjk-light-operation-impl，operation.Application |
| deploy_rrsjk_light_data_service.sh | rrsjk-light-data-impl.tar.gz | /data/deploy/job-deploy-rrsjk-light-data | rrsjk-light-data-impl/bin/rrsjk-light-data-impl |
| deploy_rrsjk_finance_service.sh | rrsjk-finance-impl.tar.gz | /data/deploy/job-deploy-rrsjk-finance | rrsjk-finance-impl/bin/rrsjk-finance-impl，finance.Application |
| deploy_rrsjk_trade_service.sh | rrsjk-trade-impl.tar.gz | /data/deploy/job-deploy-rrsjk-trade | rrsjk-trade-impl/bin/rrsjk-trade-impl，trade.Application |
| deploy_rrsjk_system_service.sh | rrsjk-system-impl.tar.gz | /data/deploy/job-deploy-rrsjk-system | rrsjk-system-impl/bin/rrsjk-system-impl，system.Application |
| deploy_rrsjk_openapi_service.sh | rrsjk-light-openapi-impl.tar.gz | /data/deploy/job-deploy-rrsjk-light-openapi | rrsjk-light-openapi-impl/bin/rrsjk-light-openapi-impl |
| deploy_rrsjk_item_service.sh | rrsjk-item-impl.tar.gz | /data/deploy/job-deploy-rrsjk-item | rrsjk-item-impl/bin/rrsjk-item-impl |
| deploy_rrsjk_light_message_service.sh | rrsjk-light-message-impl.tar.gz | /data/deploy/job-deploy-rrsjk-light-message | rrsjk-light-message-impl/bin/rrsjk-light-message-impl |
| deploy_pvs_repairs_service.sh | repairs-impl.tar.gz | /data/deploy/job-deploy-pvs-repairs | repairs-impl/bin/repairs-impl |

还存在较多历史/商城/基础服务脚本，例如 base-service、item-service、member-service、portal-service、rank-service、cbs order/system、shoppingmall basic/cart/item/order、rrsjk-cms、echannel、merchant、member、pay、activity、flowable、energystorage、migration、rrsln、shop 等。总体规律是：232/233 承载后端业务服务，服务目录集中在 `/data/deploy/job-deploy-*`。

差异点：

- 10.2.160.233 看到 `deploy_job_service.sh`、`deploy_rrs_dispenser.sh`、`deploy_rrs_dispenser_server.sh`、`deploy_rrsjk_migration_member.sh` 等脚本。
- 10.2.160.232 看到部分 stop/bak 变体、`deploy_rrsjk_migration_mix.sh`、`deploy_rrs_dispenser_report.sh` 等脚本。

## 10.2.160.234 / 10.2.160.235 Dispenser/Light-Data 层

这两台是 dispenser 和 light-data 专用节点。

| 脚本 | 包 | 目标路径 | 启动入口 |
|---|---|---|---|
| deploy_rrs_dispenser.sh | rrs-dispenser.tar.gz | /data/deploy/job-deploy-dispenser | dispenser-service/bin/dispenser-service |
| deploy_rrs_dispenser_report.sh | rrs-dispenser-report.tar.gz | /data/deploy/rrs-dispenser-report | dispenser-report-service/bin/dispenser-report-service |
| deploy_rrs_dispenser_server.sh | dispenser-server.tar.gz | /data/deploy/job-deploy-dispenser-server | dispenser-server/bin/dispenser-server |
| deploy_rrsjk_light_data_service.sh | rrsjk-light-data-impl.tar.gz | /data/deploy/job-deploy-rrsjk-light-data | rrsjk-light-data-impl/bin/rrsjk-light-data-impl |

Codeup 子目录中的 light-data 脚本会按 `light.Application` 或 `light.data.Application` 识别进程。

## 10.2.160.236 Dubbo3/Light 节点

10.2.160.236 目前 `/deployment` 内容很少，主要是 light 服务：

| 脚本 | 包 | 目标路径 | 启动入口/应用标识 |
|---|---|---|---|
| deploy_rrsjk_light_service.sh | rrsjk-light-impl.tar.gz | /data/deploy/job-deploy-rrsjk-light | rrsjk-light-impl/bin/rrsjk-light-impl，light.Application |
| codeup/deploy_rrsjk_light_service.sh | 入参包 | /data/deploy/job-deploy-rrsjk-light | rrsjk-light-impl/bin/rrsjk-light-impl，light.Application |

## JVM 内存配置

- **rrsjk-admin-web**: 2026-05-07 生产环境 (jk-prod profile) 最大堆内存从 2048M 提升到 **4096M** (commit 2771790, yumiao)
- 开发环境 (jk-dev) 保持 512M 不变

## 发版脚本共性

- 传统 Jenkins 类脚本通常读取 `/deployment/jenkins.conf`，下载包，按时间戳备份旧版本，停止服务，清理旧目录，解压新包，启动服务。
- Codeup 子目录脚本通常从 `$1` 接收包路径，复制为目标 `*.tar.gz` 或 `ROOT.tar.gz` 后解压并启动。
- Web 层通常是 Tomcat/Jetty；业务服务层通常是 `/data/deploy/job-deploy-*` 下的自启动脚本。
- 对 Hermes 回答问题时，应优先按 IP 和服务分层回答：221/222 nginx，228/229 API，230/231 Web，232/233 Dubbo 服务，234/235 dispenser/light-data，236 dubbo3/light。
