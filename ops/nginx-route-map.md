# Nginx 路由与 H5 发版地图

更新时间：2026-05-10

来源：只读检查 `10.2.160.221`、`10.2.160.222` 的 `/etc/nginx/conf.d/*.conf`、`/deployment/*.sh` 和 `nginx -T`。两台 nginx 配置基本镜像，差异点是 `dict_server` 分别指向本机 `3088`。

## 服务器定位

| IP | 主机名 | 角色 |
|---|---|---|
| 10.2.160.221 | rrsjk-prod-nginx1-10-2-160-221 | 生产 nginx1，静态 H5 和反向代理 |
| 10.2.160.222 | rrsjk-prod-nginx2-10-2-160-222 | 生产 nginx2，静态 H5 和反向代理 |

## H5/静态站点发版脚本

221/222 的 `/deployment` 主要是前端 H5 发版脚本。脚本逻辑基本是：进入目标目录，备份旧 zip 或旧目录，删除旧目录，解压新 zip，把 `dist` 改名为目标目录。

| 脚本 | 目标目录 | 发布目录 |
|---|---|---|
| deploy_pv.mobile_h5.sh | /home/www/pv.mh5.com | h5 |
| deploy_dashboard_h5.sh | /home/www/www.rrsjk.com | dashboard |
| deploy_merchant_h5.sh | /home/www/www.rrsjk.com | mch |
| deploy_merchant_pre_h5.sh | /home/www/www.rrsjk.com | mchpre |
| deploy_hds_h5.sh | /home/www/hds.rrsjk.com | h5 |
| deploy_mobile_h5.sh | /home/www/ln.rrsjk.com | 脚本变量 DIR 指定 |
| deploy_lj_h5.sh | /home/www/ln.rrsjk.com | ljh5 |
| deploy_jk-rrsjk-water-dashboard-h5-prod.sh | /home/www/ln.rrsjk.com | swh5 |

## 光伏/PVS 相关域名

| 域名 | 配置文件 | 入口 | 静态目录/后端 |
|---|---|---|---|
| h5.nahuipv.com | h5.nahuipv.com.conf | `/` | `/home/www/pv.mh5.com/h5/`，SPA fallback 到 `/index.html` |
| nahuipv.com | h5.nahuipv.com.conf | `/` | 同 h5.nahuipv.com |
| www.nahuipv.com | h5.nahuipv.com.conf | `/` | 同 h5.nahuipv.com |
| pvsapph5.nahui-newenergy.com | pvsapph5.nahui-newenergy.com.conf | `/` | `/home/www/pv.mh5.com/h5/`，SPA fallback 到 `/index.html` |
| api.nahuipv.com | api.rrsjk.com.conf | `/appapi`、`/merchant`、`/payapi`、`/reportapi`、`/hdsapi`、`/mobileapi`、`/openapi` 等 | 反向代理到 228/229 API 层 |
| hds.rrsjk.com | hds.rrsjk.com.conf | `/hdsapi`、`/h5`、`/ospboard` | hdsapi 到 228/229:8096；H5 到 `/home/www/hds.rrsjk.com`；ospboard 到 `/home/www/ospboard.hds.rrsjk.com/dist/` |

## API 路由到 228/229

配置文件：`/etc/nginx/conf.d/api.rrsjk.com.conf`

| upstream | 后端 | 入口 location |
|---|---|---|
| v3api_server | 10.2.160.228:8191, 10.2.160.229:8191 | `/api/api/open/*` 以及默认 `/` |
| rrsjk_appapi_host | 10.2.160.228:9097, 10.2.160.229:9097 | `/appapi/*` |
| oauth2_host | 10.2.160.228:8086, 10.2.160.229:8086 | oauth2 相关配置 |
| rrsjk_merchant_host | 10.2.160.228:8087, 10.2.160.229:8087 | `/merchant/*` |
| rrsjk_mobileapi_host_prod | 10.2.160.228:8092, 10.2.160.229:8092 | `/mobileapi/*` |
| rrsjk_payapi_host | 10.2.160.228:8093, 10.2.160.229:8093 | `/payapi/*` |
| rrsjk_reportapi_host | 10.2.160.228:8095, 10.2.160.229:8095 | `/reportapi/*` |
| rrsjk_hdsapi_host | 10.2.160.228:8096, 10.2.160.229:8096 | `/hdsapi/*` |
| openapi_server_host_dev | 10.2.160.228:8083, 10.2.160.229:8083 | `/openapi/*` |
| dict_server | 10.2.160.221:3088 或 10.2.160.222:3088 | `/dictapi` |

## 传统 RRSJK Web 路由

这些域名主要代理到 `10.2.160.230`、`10.2.160.231` 的 Web/Tomcat 服务。

| 域名/配置 | upstream | 后端 |
|---|---|---|
| c.rrsjk.com | c_host | 10.2.160.230:8090, 10.2.160.231:8090 |
| cart.rrsjk.com | cart_host | 10.2.160.230:8082, 10.2.160.231:8082 |
| cbs.rrsjk.com | cbs_host | 10.2.160.230:7780, 10.2.160.231:7780 |
| cbs.rrsjk.com `/console` | seller_console_host | 10.2.160.230:6124, 10.2.160.231:6124 |
| cbs.rrsjk.com `/admin` | rrsjk_admin_host | 10.2.160.230:8089, 10.2.160.231:8089 |
| cbs.rrsjk.com `/preview` | kkfileview_host | 10.2.160.232:8012, 10.2.160.233:8012 |
| finance.rrsjk.com | finance_server | 10.2.160.231:8094 |
| img002.rrsjk.com | img002_host | 10.2.160.230:8088, 10.2.160.231:8088 |
| item.rrsjk.com | item_host | 10.2.160.230:8080, 10.2.160.231:8080 |
| m.rrsjk.com | mobile-web-host | 10.2.160.230:8085, 10.2.160.231:8085 |
| m.rrsjk.com `/mapp` | app_web_host | 10.2.160.230:9095, 10.2.160.231:9095 |
| member.rrsjk.com | member_host | 10.2.160.230:8081, 10.2.160.231:8081 |
| pay.rrsjk.com | pay_host_java | 10.2.160.230:9900, 10.2.160.231:9900 |
| portal.rrsjk.com | portal_host | 10.2.160.230:5566, 10.2.160.231:5566 |
| rrscdn.com/img.rrscdn.com/img04.rrsjk.com | image_host | 10.2.160.230:8088, 10.2.160.231:8088 |
| search.rrsjk.com | search_host | 10.2.160.230:8183, 10.2.160.231:8183 |
| www.rrsjk.com | console_host | 10.2.160.230:8091, 10.2.160.231:8091 |
| www.rrsjk.com `/seller` | seller_host | 10.2.160.230:6123, 10.2.160.231:6123 |
| www.rrsjk.com `/dispenser` | dispenser_host | 10.2.160.230:6128, 10.2.160.231:6128 |

## 其他路由

| 域名 | 后端/目录 | 说明 |
|---|---|---|
| ln.rrsjk.com | 10.2.160.227 多端口 + `/home/www/ln.rrsjk.com` | 辽宁相关 H5/API/admin/image 路由 |
| www3.rrsjk.com | 10.2.160.227:81 | report_server |
| slapi.rrsjk.com | slapi_server | 当前配置文件定义，需按源码/完整配置继续核对后端 |
| slvideo.rrsjk.com | slvideo_server | 当前配置文件定义，需按源码/完整配置继续核对后端 |

## 回答建议

- 问“域名/路径打到哪里”：先查本文件的域名表和 upstream 表。
- 问“H5 发版脚本发到哪里”：查“ H5/静态站点发版脚本”表。
- 问“后端服务部署在哪台机器”：结合 `ops/deployment-map.md`，通常 228/229 是 API，230/231 是 Web，232/233 是 Dubbo 服务，234/235 是 dispenser/light-data，236 是 dubbo3/light。
- 如果涉及 221/222 差异，重点说明 `dict_server` 指向本机 `3088`。

