# 支持 RAM 的云服务 {#concept_ofk_yt2_xdb .concept}

RAM \(Resource Access Management\) 是阿里云为客户提供的用户身份管理与资源访问控制服务。

STS \(Security Token Service\) 是阿里云提供的一种临时访问权限管理服务。

许多阿里云服务都与 RAM/STS 相集成，本文按服务类别罗列了这些服务，并提供每个服务支持的 RAM 授权粒度、系统策略，以及相关文档的链接，方便您使用及查询。

在集成 RAM 功能时，各产品针对 RAM 用户定义了不同级别的授权粒度，具体有：

-   服务级别：将云产品作为一个整体进行授权；一个 RAM 用户只能处于对这个产品拥有所有权限和没有任何权限两种状态。
-   操作级别：在 API 级别进行授权；一个 RAM 用户可以对指定云产品的某类资源执行某几个指定的操作。
-   资源级别：对执行资源的指定操作进行授权，这是最细的授权粒度；例如：授权一个 RAM 用户仅可对某一台云服务器进行重启操作。

## 支持 RAM/STS 的云服务列表 {#section_00 .section}

以下表格分别罗列了弹性计算、云数据库、存储与 CDN、网络、分析、云通信、监控与管理、应用服务、互联网中间件、移动服务、视频服务、大数据（数加）、安全（云盾）、云市场、域名与网站下，已支持 RAM/STS 的云服务。每个表格具体包含如下信息：

-   服务名：支持 RAM/STS 的云服务的名称。
-   控制台：当前服务是否支持在控制台进行访问控制，“∨”表示支持，“×”表示不支持，“○”表示不提供。
-   API \(RAM/STS\)：当前服务是否支持通过 API 进行访问控制，“∨”表示支持，“×”表示不支持，“○”表示不提供。
-   授权粒度：当前服务提供的最小授权粒度。
-   系统策略：当前服务支持的系统策略。
-   相关文档：当前服务应用 RAM/STS 相关的文档链接。

## 弹性计算 {#section_01 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API （STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:--------|:---|:---|:---|
|云服务器 ECS|√|√|√|√|资源级别| -   AliyunECSFullAccess
-   AliyunECSReadOnlyAccess

 |[ECS鉴权规则](../../../../../intl.zh-CN/API参考/鉴权规则.md)|
|负载均衡 SLB|√|√|√|√|资源级别| -   AliyunSLBFullAccess
-   AliyunSLBReadOnlyAccess

 |[SLB鉴权规则](../../../../../intl.zh-CN/API参考/RAM鉴权.md)|
|弹性伸缩 AutoScaling|√|√|×|×|服务级别| -   AliyunESSFullAccess
-   AliyunESSReadOnlyAccess

 |[API使用须知](../../../../../intl.zh-CN/API 参考/API使用须知.md#)|
|容器服务|√|√|×|×|服务级别|AliyunCSFullAccess|[使用子账号](../../../../../intl.zh-CN/用户指南/授权管理/使用子账号.md#)|
|容器镜像服务|√|√|×|×|资源级别| -   AliyunContainerRegistryFullAccess
-   AliyunContainerRegistryReadOnlyAccess

 |[仓库访问控制](https:/alibabacloud.com/help/doc-detail/67992.html)|
|资源编排 ROS|√|√|×|×|服务级别| -   AliyunROSFullAccess
-   AliyunROSReadOnlyAccess

 |[使用 RAM 控制资源访问](../../../../../intl.zh-CN/快速入门/使用 RAM 控制资源访问.md#)|
|批量计算 BatchCompute|√|√|×|×|服务级别|-|-|
|函数计算|√|√|×|√|资源级别| -   AliyunFCFullAccess
-   AliyunFCInvocationAccess
-   AliyunFCReadOnlyAccess

 |-|
|弹性高性能计算|√|√|×|×|操作级别| -   AliyunEHPCFullAccess
-   AliyunEHPCReadOnlyAccess

 |-|
|轻量应用服务器|√|○|×|×|操作级别|AliyunSWASFullAccess|-|

## 云数据库 {#section_02 .section}

|服务名|控制台\(RAM\)|API \(RAM\)|控制台\(STS\)|API \(STS\)|授权粒度|系统策略|相关文档|
|:--|:---------|:----------|:---------|:----------|:---|:---|:---|
|云数据库 RDS 版|√|√|√|√|资源级别| -   AliyunRDSFullAccess
-   AliyunRDSReadOnlyAccess

 | |
|云数据库 MongoDB 版|√|√|×|×|资源级别| -   AliyunMongoDBFullAccess
-   AliyunMongoDBReadOnlyAccess

 | |
|云数据库 Redis 版|√|√|×|×|资源级别| -   AliyunKvstoreFullAccess
-   AliyunKvstoreReadOnlyAccess

 | |
|云数据库 Memcache 版|√|√|×|×|服务级别| -   AliyunOCSFullAccess
-   AliyunOCSReadOnlyAccess

 |-|
|高性能时间序列数据库HiTSDB|√|√|×|×|操作级别|-|-|
|云数据库 HybridDB for PostgreSQL|√|○|×|×|资源级别| -   AliyunGPDBFullAccess
-   AliyunGPDBReadOnlyAccess

 |-|
|数据传输服务DTS|√|√|×|×|服务级别| -   AliyunDTSFullAccess
-   AliyunDTSReadOnlyAccess

 |-|
|分布式关系型数据库 DRDS|√|○|×|×|资源级别| -   AliyunDRDSFullAccess
-   AliyunDRDSReadOnlyAccess

 |-|

## 存储与 CDN {#section_03 .section}

|服务名|控制台（RAM）|API \(RAM\)|控制台（STS）|API （STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:----------|:-------|:--------|:---|:---|:---|
|对象存储 OSS|√|√|√|√|资源级别| -   AliyunOSSFullAccess
-   AliyunOSSReadOnlyAccess

 |-

|
|文件存储 NAS|√|○|×|×|服务级别| -   AliyunNASFullAccess
-   AliyunNASReadOnlyAccess

 | |
|表格存储|√|√|×|×|资源级别| -   AliyunOTSFullAccess
-   AliyunOTSReadOnlyAccess
-   AliyunOTSWriteOnlyAccess

 | |
|CDN|√|√|×|×|资源级别| -   AliyunCDNFullAccess
-   AliyunCDNReadOnlyAccess

 | |
|云存储网关|√|○|×|×|服务级别|AliyunHCSSGWFullAccess|-|
|混合云备份|√|○|×|×|资源级别| -   AliyunHBRFullAccess
-   AliyunHBRReadOnlyAccess

 |-|

## 网络 {#section_04 .section}

|服务名|控制台（RAM）|API \(RAM\)|控制台（STS）|API \(STS\)|授权粒度|系统策略|相关文档|
|:--|:-------|:----------|:-------|:----------|:---|:---|:---|
|专有网络 VPC|√|√|√|√|资源级别| -   AliyunVPCFullAccess
-   AliyunVPCReadOnlyAccess

 |[VPC鉴权规则](https://alibabacloud.com/help/doc-detail/27777.htm)|
|弹性公网 IP|√|√|×|×|资源级别| -   AliyunEIPFullAccess
-   AliyunEIPReadOnlyAccess

 |[弹性公网IP鉴权规则](https://www.alibabacloud.com/help/en/doc-detail/27777.htm)|
|高速通道 ExpressConnect|√|√|×|×|资源级别| -   AliyunExpressConnectFullAccess
-   AliyunExpressConnectReadOnlyAccess

 |[高速通道鉴权规则](https://www.alibabacloud.com/help/en/doc-detail/31813.html)|
|NAT网关|√|√|×|×|资源级别| -   AliyunNATGatewayReadOnlyAccess
-   AliyunNATGatewayFullAccess

 |-|

## 分析 {#section_05 .section}

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|E-MapReduce|√|√|服务级别|AliyunEMRFullAccess|[角色授权](../../../../../intl.zh-CN/用户指南/角色授权.md#)|
|云数据库 HybridDB for PostgreSQL|√|√|资源级别| -   AliyunGPDBFullAccess
-   AliyunGPDBReadOnlyAccess

 |-|

## 云通信 {#section_06 .section}

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|消息服务|√|√|资源级别| -   AliyunMNSFullAccess
-   AliyunMNSReadOnlyAccess

 |-|
|邮件推送|√|√|服务级别| -   AliyunDirectMailFullAccess
-   AliyunDirectMailReadOnlyAccess

 |-|
|短信服务|√|√|服务级别|-|-|

## 监控与管理 {#section_07 .section}

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|云监控|√|√|服务级别| -   AliyunCloudMonitorFullAccess
-   AliyunCloudMonitorReadOnlyAccess

 | |
|操作审计|√|√|资源级别|-|-|
|密钥管理|√|√|资源级别| -   AliyunKMSFullAccess
-   AliyunKMSReadOnlyAccess
-   AliyunKMSCryptoAccess

 |[使用RAM实现KMS资源授权](../../../../../intl.zh-CN/用户指南/使用RAM实现KMS资源授权.md#)|

## 应用服务 {#section_08 .section}

|服务名|控制台（RAM）|API \(RAM\)|控制台 \(STS\)|API \(STS\)|授权粒度|系统策略|相关文档|
|:--|:-------|:----------|:----------|:----------|:---|:---|:---|
|日志服务|√|√|×|×|资源级别| -   AliyunLogFullAccess
-   AliyunLogReadOnlyAccess

 | -   [授权RAM 用户](../../../../../intl.zh-CN/用户指南/         访问控制 RAM/授权RAM 用户.md#)
-   [鉴权规则](../../../../../intl.zh-CN/API 参考/RAM子用户访问/鉴权规则.md#)

 |
|API 网关|√|√|×|×|服务级别| -   AliyunApiGatewayFullAccess
-   AliyunApiGatewayReadOnlyAccess

 |-|
|邮件推送|√|√|×|×|操作级别| -   AliyunDirectMailFullAccess
-   AliyunDirectMailReadOnlyAccess

 |-|
|消息服务|√|√|×|×|资源级别| -   AliyunMNSFullAccess
-   AliyunMNSReadOnlyAccess

 |-|

## 互联网中间件 {#section_09 .section}

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|企业级分布式应用服务 EDAS|√|×|服务级别|AliyunEDASFullAccess|[子账号管理](https://www.alibabacloud.com/help/en/doc-detail/44023.htm)|
|消息队列|√|√|资源级别| -   AliyunMQFullAccess
-   AliyunMQPubOnlyAccess
-   AliyunMQSubOnlyAccess

 |-|
|业务实时监控服务|√|×|服务级别|-|-|
|应用配置管理|√|√|资源级别|-|-|

## 移动服务 {#section_10 .section}

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|移动安全（应用安全）|√|√|服务级别|AliyunYundunJaqFullAccess|-|

## 视频服务 {#section_11 .section}

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|媒体处理|√|√|服务级别| -   AliyunMTSFullAccess
-   AliyunMTSPlayerAuth

 |[子帐号使用控制台说明](../../../../../intl.zh-CN/用户指南/子帐号使用控制台说明.md#)|
|视频直播|√|√|服务级别|AliyunLiveFullAccess|-|

## 大数据（数加） {#section_12 .section}

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|Quick BI|√|√|服务级别|-|-|
|机器学习|√|√|服务级别|-|-|
|DataV 数据可视化|√|√|服务级别|-|-|
|阿里云Elasticsearch|√|√|资源级别|-|-|

## 安全（云盾） {#section_13 .section}

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|安骑士（服务器安全）|√|○|服务级别|AliyunYundunAegisFullAccess|-|
|DDoS基础防护|√|○|服务级别| -   AliyunYundunDDosFullAccess
-   AliyunYundunDDosReadOnlyAccess

 |-|
|DDoS 高防 IP|√|○|服务级别| -   AliyunYundunHighFullAccess
-   AliyunYundunHighReadOnlyAccess

 |-|
|Web应用防火墙（网络安全）|√|○|服务级别| -   AliyunYundunWAFFullAccess
-   AliyunYundunWAFReadOnlyAccess

 |-|
|内容安全（业务安全）|√|○|服务级别|-|-|
|证书服务|√|○|服务级别|AliyunYundunCertFullAccess|-|
|移动安全|√|○|服务级别|AliyunYundunJaqFullAccess|-|
|SSL证书（应用安全）|√|○|服务级别| -   AliyunYundunCertFullAccess
-   AliyunYundunCertReadOnlyAccess

 |-|

## 云市场 {#section_14 .section}

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|云市场|√|○|服务级别|AliyunMarketplaceFullAccess|-|

## 域名与网站 {#section_15 .section}

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|云解析DNS|√|○|服务级别| -   AliyunDNSFullAccess
-   AliyunDNSReadOnlyAccess

 |-|
|域名|√|有|资源级别|AliyunDomainFullAccess|[概述](../../../../../intl.zh-CN/域名管理/RAM资源授权-域名/概述.md#)|

