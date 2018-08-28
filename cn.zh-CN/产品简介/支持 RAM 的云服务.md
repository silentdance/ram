# 支持 RAM 的云服务 {#concept_ofk_yt2_xdb .concept}

许多阿里云服务都与 RAM 相集成，本文按服务类别罗列了这些服务，并提供每个服务支持的 RAM 授权粒度、系统策略，以及相关 RAM 文档的链接，方便您使用及查询。

在集成 RAM 功能时，各产品针对子用户定义了不同级别的授权粒度，具体有：

-   服务级别：将云产品作为一个整体进行授权；一个子用户只能处于对这个产品“拥有所有权限”和“没有任何权限”两种状态。
-   操作级别：在 API 级别进行授权；一个子用户可以对指定云产品的某类资源执行某几个指定的操作。
-   资源级别：对执行资源的指定操作进行授权，这是最细的授权粒度；例如：授权一个子用户仅可对某一台云服务器进行重启操作。

## 支持 RAM 的云服务列表 {#section_asb_zt2_xdb .section}

以下表格分别罗列了 [弹性计算](#section_b53_g52_xdb)、[云数据库](#section_ep3_h52_xdb)、[存储与 CDN](#section_ihm_352_xdb)、[网络](#section_az3_j52_xdb)、[分析](#section_psg_k52_xdb)、[云通信](#section_xlt_l52_xdb)、[监控与管理](#section_ypn_m52_xdb)、[应用服务](#section_mfn_n52_xdb)、[互联网中间件](#section_wck_452_xdb)、[移动服务](#section_qqf_p52_xdb)、[视频服务](#section_slb_q52_xdb)、[大数据（数加）](#section_qbt_q52_xdb)、[安全（云盾）](#section_tsn_r52_xdb)、[云市场](#section_ejg_s52_xdb)、[域名与网站](#section_spw_s52_xdb)下，已支持 RAM 的云服务。每个表格具体包含如下信息：

-   服务名：支持 RAM 的云服务的名称。
-   控制台：当前服务是否支持在控制台进行访问控制，“∨”表示支持，“×”表示不支持，“○”表示不提供。
-   API：当前服务是否支持通过 API 进行访问控制，“∨”表示支持，“×”表示不支持，“○”表示不提供。
-   授权粒度：当前服务提供的最小授权粒度。
-   系统策略：当前服务支持的系统策略。
-   相关文档：当前服务应用 RAM 相关的文档链接。

## 弹性计算 {#section_b53_g52_xdb .section}

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|云服务器 ECS|√|√|资源级别| -   AliyunECSFullAccess
-   AliyunECSReadOnlyAccess

 |[ECS鉴权规则](../../../../cn.zh-CN/API 参考/鉴权规则.md)|
|负载均衡 SLB|√|√|资源级别| -   AliyunSLBFullAccess
-   AliyunSLBReadOnlyAccess

 |[SLB鉴权规则](../../../../cn.zh-CN/API参考/RAM鉴权.md)|
|弹性伸缩 AutoScaling|√|√|服务级别| -   AliyunESSFullAccess
-   AliyunESSReadOnlyAccess

 |[弹性伸缩API使用须知](https://help.aliyun.com/document_detail/25925.html)|
|容器服务|√|√|服务级别|-|[使用子账号](https://help.aliyun.com/document_detail/63578.html)|
|资源编排 ROS|√|√|服务级别|-|[使用 RAM 控制资源访问](https://help.aliyun.com/document_detail/48754.html)|
|批量计算 BatchCompute|√|√|服务级别|AliyunBatchComputeFullAccess|-|

## 云数据库 {#section_ep3_h52_xdb .section}

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|云数据库 RDS 版|√|√|资源级别| -   AliyunRDSFullAccess
-   AliyunRDSReadOnlyAccess

 |[RDS鉴权规则](https://help.aliyun.com/document_detail/26307.html)|
|云数据库 MongoDB 版|√|√|资源级别| -   AliyunMongoDBFullAccess
-   AliyunMongoDBReadOnlyAccess

 |[MongoDB鉴权规则](https://help.aliyun.com/document_detail/61757.html)|
|云数据库 Redis 版|√|√|资源级别| -   AliyunKvstoreFullAccess
-   AliyunKvstoreReadOnlyAccess

 |[Redis鉴权规则](https://help.aliyun.com/document_detail/61122.html)|
|云数据库 Memcache 版|√|√|服务级别| -   AliyunOCSFullAccess
-   AliyunOCSReadOnlyAccess

 |-|
|云数据库 HybridDB for MySQL|√|√|资源级别| -   AliyunPetaDataFullAccess
-   AliyunPetaDataReadOnlyAccess

 |-|
|云数据库 Hbase 版|√|√|资源级别|-|-|
|数据传输服务 DTS|√|√|服务级别| -   AliyunDTSFullAccess
-   AliyunDTSReadOnlyAccess

 |[DTS授权和子账号管理DTS实例](https://help.aliyun.com/document_detail/52589.html)|

## 存储与 CDN {#section_ihm_352_xdb .section}

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|对象存储 OSS|√|√|资源级别| -   AliyunOSSFullAccess
-   AliyunOSSReadOnlyAccess

 | -   [OSS权限控制](https://help.aliyun.com/document_detail/56283.html)
-   [OSS授权策略配置](https://help.aliyun.com/document_detail/56288.html)
-   [OSS权限管理最佳实践](https://help.aliyun.com/document_detail/31929.html)

 |
|文件存储 NAS|√|○|服务级别| -   AliyunNASFullAccess
-   AliyunNASReadOnlyAccess

 |[使用权限组进行访问控制](https://help.aliyun.com/document_detail/27534.html)|
|表格存储|√|√|资源级别| -   AliyunOTSFullAccess
-   AliyunOTSReadOnlyAccess
-   AliyunOTSWriteOnlyAccess

 |[自定义权限](https://help.aliyun.com/document_detail/27362.html)|
|CDN|√|√|资源级别| -   AliyunCDNFullAccess
-   AliyunCDNReadOnlyAccess

 |[CDN鉴权规则](https://help.aliyun.com/document_detail/27154.html)|
|云存储网关|√|○|服务级别|AliyunHCSSGWFullAccess|-|
|混合云备份|√|○|资源级别| -   AliyunHBRFullAccess
-   AliyunHBRReadOnlyAccess

 |-|

## 网络 {#section_az3_j52_xdb .section}

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|专有网络 VPC|√|√|资源级别| -   AliyunVPCFullAccess
-   AliyunVPCReadOnlyAccess

 |[VPC鉴权规则](https://help.aliyun.com/document_detail/27777.html)|
|弹性公网 IP|√|√|资源级别| -   AliyunEIPFullAccess
-   AliyunEIPReadOnlyAccess

 |[弹性公网IP鉴权规则](https://help.aliyun.com/document_detail/27777.html)|
|高速通道 ExpressConnect|√|√|资源级别| -   AliyunExpressConnectFullAccess
-   AliyunExpressConnectReadOnlyAccess

 |[高速通道鉴权规则](https://help.aliyun.com/document_detail/31813.html)|
|NAT网关|√|√|资源级别| -   AliyunNATGatewayReadOnlyAccess
-   AliyunNATGatewayFullAccess

 |-|

## 分析 {#section_psg_k52_xdb .section}

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|---|---|---|----|----|----|
|E-MapReduce|√|√|服务级别|AliyunEMRFullAccess|[E-MapReduce角色授权](https://help.aliyun.com/document_detail/28072.html)|
|开放搜索|√|√|服务级别| -   AliyunOpenSearchFullAccess
-   AliyunOpenSearchReadOnlyAccess

 |[开放搜索 鉴权规则](https://help.aliyun.com/document_detail/53744.html)|

## 云通信 {#section_xlt_l52_xdb .section}

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|消息服务|√|√|资源级别| -   AliyunMNSFullAccess
-   AliyunMNSReadOnlyAccess

 |[消息服务鉴权规则](https://help.aliyun.com/document_detail/27448.html)|
|移动推送|√|√|服务级别| -   AliyunMPushFullAccess
-   AliyunMPushReadOnlyAccess

 |-|
|邮件推送|√|√|服务级别| -   AliyunDirectMailFullAccess
-   AliyunDirectMailReadOnlyAccess

 |-|
|语音服务|√|√|服务级别| -   AliyunDyvmsFullAccess
-   AliyunDyvmsReadOnlyAccess

 |[语音权限访问控制](https://help.aliyun.com/document_detail/55766.html)|
|流量服务|√|√|服务级别| -   AliyunDycdpFullAccess
-   AliyunDycdpReadOnlyAccess

 |[流量权限访问控制](https://help.aliyun.com/document_detail/55767.html)|
|短信服务|√|√|服务级别| -   AliyunSMSFullAccess
-   AliyunSMSReadOnlyAccess

 |[短信权限访问控制](https://help.aliyun.com/document_detail/55764.html)|

## 监控与管理 {#section_ypn_m52_xdb .section}

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|云监控|√|√|服务级别| -   AliyunCloudMonitorFullAccess
-   AliyunCloudMonitorReadOnlyAccess

 |[云监控访问控制](https://help.aliyun.com/document_detail/43170.html)|
|访问控制|√|√|资源级别| -   AliyunRAMFullAccess
-   AliyunRAMReadOnlyAccess
-   AliyunSTSAssumeRoleAccess

 |[RAM API参考](https://help.aliyun.com/document_detail/28672.html)|
|操作审计|√|√|资源级别| -   AliyunActionTrailFullAccess
-   AliyunActionTrailReadOnlyAccess

 |[RAM支持的ActionTrail操作和资源](https://help.aliyun.com/document_detail/28817.html)|
|密钥管理|√|√|资源级别|-|[KMS鉴权规则](https://help.aliyun.com/document_detail/28953.html)|

## 应用服务 {#section_mfn_n52_xdb .section}

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|日志服务|√|√|资源级别| -   AliyunLogFullAccess
-   AliyunLogReadOnlyAccess

 | -   [RAM用户](https://help.aliyun.com/document_detail/47664.html)
-   [日志服务 鉴权规则](https://help.aliyun.com/document_detail/29052.html)

 |
|性能测试服务|√|√|服务级别|AliyunPTSFullAccess|[性能测试RAM](https://help.aliyun.com/document_detail/29315.html)|
|API 网关|√|√|服务级别| -   AliyunApiGatewayFullAccess
-   AliyunApiGatewayReadOnlyAccess

 |-|
|物联网套件|√|√|资源级别| -   AliyunIOTFullAccess
-   AliyunIOTReadOnlyAccess

 |[物联网套件鉴权规则](https://help.aliyun.com/document_detail/47495.html)|
|智能对话分析服务|√|√|资源级别|-|-|

## 互联网中间件 {#section_wck_452_xdb .section}

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|企业级分布式应用服务 EDAS|√|×|服务级别|AliyunEDASFullAccess|[子账号管理](https://help.aliyun.com/document_detail/44023.html)|
|分布式关系型数据库服务 DRDS|√|×|资源级别| -   AliyunDRDSFullAccess
-   AliyunDRDSReadOnlyAccess

 |[DRDS支持的资源授权](https://help.aliyun.com/document_detail/51480.html)|
|业务实时监控服务 ARMS|√|×|服务级别|AliyunARMSFullAccess|-|

## 移动服务 {#section_qqf_p52_xdb .section}

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|移动用户反馈|√|√|服务级别| -   AliyunFeedbackFullAccess
-   AliyunFeedbackReadOnlyAccess

 |[移动用户反馈鉴权规则](https://help.aliyun.com/document_detail/55906.html?spm=a2c4g.11186623.6.550.yApBCI)|
|移动热修复|√|√|服务级别| -   AliyunHotfixFullAccess
-   AliyunHotfixReadOnlyAccess

 |[移动热修复鉴权规则](https://help.aliyun.com/document_detail/55889.html)|
|移动安全（应用安全）|√|√|服务级别|AliyunYundunJaqFullAccess|-|

## 视频服务 {#section_slb_q52_xdb .section}

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|媒体处理|√|√|服务级别| -   AliyunMTSFullAccess
-   AliyunMTSPlayerAuth

 |[子账号使用控制台说明](https://help.aliyun.com/document_detail/42841.html)|
|视频点播|√|√|服务级别|AliyunMTSFullAccess|-|
|视频直播|√|√|服务级别|AliyunLiveFullAccess|-|

## 大数据（数加） {#section_qbt_q52_xdb .section}

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|大数据开发套件|√|√|服务级别|-|[用户使用子账号](https://help.aliyun.com/document_detail/55316.html)|
|Quick BI|√|√|服务级别|-|-|
|机器学习|√|√|服务级别|-|-|
|推荐引擎|√|√|服务级别|-|-|
|公众趋势分析|√|√|服务级别|-|-|
|DataV 数据可视化|√|√|服务级别|-|-|
|智能语音交互|√|√|服务级别| -   AliyunSCAFullAccess
-   AliyunSCAReadOnlyAccess

 |-|
|流计算|√|√|服务级别|-|[流计算角色授权](https://help.aliyun.com/document_detail/62460.html?spm=a2c4g.11186623.6.568.PHcqK9)|
|画像分析|√|√|服务级别|-|-|
|企业图谱|√|√|服务级别|-|-|

## 安全（云盾） {#section_tsn_r52_xdb .section}

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|态势感知|√|○|服务级别| -   AliyunYundunSASFullAccess
-   AliyunYundunSASReadOnlyAccess

 |-|
|安骑士（服务器安全）|√|○|服务级别| -   AliyunYundunAegisFullAccess
-   AliyunYundunAegisReadOnlyAccess

 |-|
|DDoS 基础防护|√|○|服务级别|AliyunYundunDDosFullAccess|-|
|DDoS 高防 IP|√|○|服务级别| -   AliyunYundunHighFullAccess
-   AliyunYundunHighReadOnlyAccess

 |-|
|Web应用防火墙（网络安全）|√|○|服务级别| -   AliyunYundunWAFFullAccess
-   AliyunYundunWAFReadOnlyAccess

 |-|
|先知\(安全情报\)|√|○|服务级别|AliyunYundunXianzhiFullAccess|-|
|安全管家|√|○|服务级别| |-|
|加密服务|√|○|服务级别|AliyunYundunHSMFullAccess|-|
|内容安全（业务安全）|√|○|服务级别|AliyunYundunGreenWebFullAccess|-|
|数据风控|√|○|服务级别|AliyunYundunAFSFullAccess|-|
|证书服务|√|○|服务级别|AliyunYundunCertFullAccess|-|
|移动安全|√|○|服务级别|AliyunYundunJaqFullAccess|-|
|合作伙伴中心|√|○|服务级别|AliyunYundunPartnerFullAccess|-|
|数据库审计|√|○|服务级别|AliyunYundunDbAuditFullAccess|-|
|堡垒机|√|○|服务级别|AliyunYundunBastionHostFullAccess|-|

## 云市场 {#section_ejg_s52_xdb .section}

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|云市场|√|○|服务级别|AliyunMarketplaceFullAccess|-|

## 域名与网站 {#section_spw_s52_xdb .section}

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|云解析DNS|√|○|服务级别| -   AliyunDNSFullAccess
-   AliyunDNSReadOnlyAccess

 |-|
|HTTPDNS|√|○|服务级别| -   AliyunHTTPDNSFullAccess
-   AliyunHTTPDNSReadOnlyAccess

 |-|

## 支持 STS 的云服务列表 {#section_cwb_zt2_xdb .section}

下表列出了支持 STS 的云服务。

表格定义同 [支持 RAM 的云服务列表](#section_asb_zt2_xdb)。

|服务|控制台|API|
|:-|:--|:--|
|云服务器 ECS|√|√|
|云数据库 RDS|√|√|
|负载均衡 SLB|√|√|
|对象存储 OSS|√|√|
|专有网络 VPC|√|√|
|物联网套件 IoT|×|√|
|函数计算 FC|×|√|

