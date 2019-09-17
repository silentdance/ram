# 支持RAM的云服务 {#concept_ofk_yt2_xdb .concept}

许多阿里云服务都与RAM/STS相集成，本文按服务类别罗列了这些服务，并提供每个服务支持的RAM授权粒度、系统策略，以及相关文档的链接，方便您使用及查询。

RAM（Resource Access Management）是阿里云为客户提供的用户身份管理与资源访问控制服务。

STS（Security Token Service）是阿里云提供的一种临时访问权限管理服务。

在集成RAM功能时，各产品针对RAM用户定义了不同级别的授权粒度，具体有：

-   服务级别：将云产品作为一个整体进行授权。一个RAM用户只能处于对这个产品拥有所有权限和没有任何权限两种状态。
-   操作级别：在API级别进行授权。一个RAM用户可以对指定云产品的某类资源执行某几个指定的操作。
-   资源级别：对执行资源的指定操作进行授权，这是最细的授权粒度。例如：授权一个RAM用户仅可对某一台云服务器进行重启操作。

## 支持RAM/STS的云服务列表 {#section_00 .section}

以下表格分别罗列了阿里云各个模块下支持 RAM/STS 的云服务：[弹性计算](#section_01)、[云数据库](#section_02)、[存储与CDN](#section_03)、[网络](#section_04)、[分析](#section_05)、[云通信](#section_06)、[监控与管理](#section_07)、[应用服务](#section_08)、[互联网中间件](#section_09)、[消息队列MQ](#section_10)、[视频服务](#section_12)、[大数据（数加）](#section_13)、[安全（云盾）](#section_14)、[云市场](#section_15)、[域名与网站](#section_16)、[会员服务](#section_17)、[费用中心](#section_18)、[工单](#section_19)、[消息](#section_20)。

每个表格具体包含如下信息：

-   服务名：支持RAM/STS的云服务的名称。
-   控制台：当前服务是否支持在控制台进行访问控制，“√”表示支持，“×”表示不支持，“○”表示不提供。
-   API（RAM/STS）：当前服务是否支持通过 API 进行访问控制，“√”表示支持，“×”表示不支持，“○”表示不提供。
-   授权粒度：当前服务提供的最小授权粒度，“-”表示暂无。
-   系统策略：当前服务支持的系统策略，“-”表示暂无。
-   相关文档：当前服务应用RAM/STS相关的文档链接，“-”表示暂无。

## 弹性计算 {#section_01 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|云服务器ECS|√|√|√|√|资源级别| -   AliyunECSFullAccess
-   AliyunECSReadOnlyAccess
-   AliyunECSNetworkInterfaceManagementAccess

 |[ECS鉴权规则](../../../../intl.zh-CN/API参考/鉴权规则.md#)|
|弹性伸缩 AutoScaling|√|√|√|√|服务级别| -   AliyunESSFullAccess
-   AliyunESSReadOnlyAccess

 |[API使用须知](../../../../intl.zh-CN/API参考/API使用须知.md#)|
|容器服务|√|√|×|√|服务级别| -   AliyunCSFullAccess
-   AliyunCSReadOnlyAccess

 |[使用子账号](../../../../intl.zh-CN/用户指南/授权管理/使用子账号.md#)|
|容器镜像服务|√|√|×|×|资源级别| -   AliyunContainerRegistryFullAccess
-   AliyunContainerRegistryReadOnlyAccess

 |[仓库访问控制](https://www.alibabacloud.com/help/zh/doc-detail/67992.htm)|
|资源编排ROS|√|√|√|√|服务级别| -   AliyunROSFullAccess
-   AliyunROSReadOnlyAccess

 |[使用 RAM 控制资源访问](../../../../intl.zh-CN/快速入门/使用 RAM 控制资源访问.md#)|
|批量计算BatchCompute|√|√|√|√|服务级别| -

 |-|
|函数计算|√|√|√|√|资源级别| -   AliyunFCFullAccess
-   AliyunFCInvocationAccess
-   AliyunFCReadOnlyAccess

 |[子账号控制台快速指导](https://www.alibabacloud.com/help/zh/doc-detail/55617.html)|
|弹性高性能计算|√|√|√|√|服务级别| -   AliyunEHPCFullAccess
-   AliyunEHPCReadOnlyAccess

 |-|
|轻量应用服务器|√|○|×|○|服务级别|AliyunSWASFullAccess|-|
|弹性容器实例ECI|√|√|√|√|资源级别| -   AliyunECIFullAccess
-   AliyunECIReadOnlyAccess

 |[如何为子账号授权](https://www.alibabacloud.com/help/zh/doc-detail/92790.htm)|

## 云数据库 {#section_02 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|云数据库RDS 版|√|√|√|√|资源级别| -   AliyunRDSFullAccess
-   AliyunRDSReadOnlyAccess

 |[RAM资源授权](../../../../intl.zh-CN/API参考/RAM资源授权.md#)|
|云数据库MongoDB版|√|√|√|√|资源级别| -   AliyunMongoDBFullAccess
-   AliyunMongoDBReadOnlyAccess

 |[MongoDB API的鉴权规则](../../../../intl.zh-CN/API参考/如何使用RAM授权/MongoDB API的鉴权规则.md#)|
|云数据库Redis版|√|√|√|√|资源级别| -   AliyunKvstoreFullAccess
-   AliyunKvstoreReadOnlyAccess

 |[RAM鉴权](../../../../intl.zh-CN/API参考/RAM鉴权.md#)|
|云数据库Memcache版|√|√|√|√|服务级别| -   AliyunOCSFullAccess
-   AliyunOCSReadOnlyAccess

 |-|
|时序时空数据库TSDB|√|√|√|√|操作级别| -

 |-|
|云数据库HybridDB for PostgreSQL|√|√|√|√|资源级别| -   AliyunGPDBFullAccess
-   AliyunGPDBReadOnlyAccess

 |[API的鉴权规则](../../../../intl.zh-CN/API参考/如何使用RAM授权/API的鉴权规则.md#)|
|数据传输服务DTS|√|√|√|√|服务级别| -   AliyunDTSFullAccess
-   AliyunDTSReadOnlyAccess

 |[授权子账号使用DTS](../../../../intl.zh-CN/用户指南/RAM授权管理/授权子账号使用DTS.md#)|
|数据库备份DBS|√|√|√|√|服务级别| -   AliyunDBSFullAccess
-   AliyunDBSReadOnlyAccess

 |-|
|分布式关系型数据库DRDS|√|√|√|√|资源级别| -   AliyunDRDSReadOnlyAccessyAccess
-   AliyunDRDSFullAccess

 | -

 |

## 存储与CDN {#section_03 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|对象存储OSS|√|√|√|√|资源级别| -   AliyunOSSFullAccess
-   AliyunOSSReadOnlyAccess

 |[如何构建RAM Policy](../../../../intl.zh-CN/开发指南/权限控制/基于RAM Policy的权限控制/如何构建RAM Policy.md#)|
|文件存储NAS|√|○|×|○|操作级别| -   AliyunNASFullAccess
-   AliyunNASReadOnlyAccess

 |[../../../../dita-oss-bucket/SP\_111/DNnas1882233/ZH-CN\_TP\_18697.md\#](../../../../intl.zh-CN/控制台用户指南/管理权限/管理权限组.md#)|
|表格存储|√|√|√|√|资源级别| -   AliyunOTSFullAccess
-   AliyunOTSReadOnlyAccess
-   AliyunOTSWriteOnlyAccess

 |[../../../../dita-oss-bucket/SP\_28/DNots1887058/ZH-CN\_TP\_20298.md\#](../../../../intl.zh-CN/开发指南/授权管理/自定义权限.md#)|
|CDN|√|√|√|√|资源级别| -   AliyunCDNFullAccess
-   AliyunCDNReadOnlyAccess

 |[CDN API鉴权规则](../../../../intl.zh-CN/旧版API参考/RAM资源授权/CDN API鉴权规则.md#)|
|全站加速|√|√|√|√|资源级别| -   AliyunDCDNFullAccess
-   AliyunDCDNReadOnlyAccess

 |-|
|云存储网关|√|○|×|○|服务级别|AliyunHCSSGWFullAccess|-|
|混合云备份|√|○|×|○|资源级别| -   AliyunHBRFullAccess
-   AliyunHBRReadOnlyAccess

 |-|
|闪电立方|√|○|×|○|服务级别|AliyunMGWFullAccess|-|

## 网络 {#section_04 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|专有网络VPC|√|√|√|√|资源级别| -   AliyunVPCFullAccess
-   AliyunVPCReadOnlyAccess

 |[RAM鉴权](../../../../intl.zh-CN/API参考/RAM鉴权.md#)|
|负载均衡|√|√|√|√|资源级别| -   AliyunSLBReadOnlyAccess
-   AliyunSLBFullAccess

 |[RAM鉴权](../../../../intl.zh-CN/API参考/RAM鉴权.md#)|
|弹性公网IP|√|√|√|√|资源级别| -   AliyunEIPFullAccess
-   AliyunEIPReadOnlyAccess

 |[RAM鉴权](../../../../intl.zh-CN/API参考/RAM鉴权.md#)|
|高速通道ExpressConnect|√|√|√|√|资源级别| -   AliyunExpressConnectFullAccess
-   AliyunExpressConnectReadOnlyAccess

 |[RAM鉴权](../../../../intl.zh-CN/API参考/RAM鉴权.md#)|
|NAT网关|√|√|√|√|资源级别| -   AliyunNATGatewayReadOnlyAccess
-   AliyunNATGatewayFullAccess

 |[RAM鉴权](../../../../intl.zh-CN/API参考/RAM鉴权.md#)|
|VPN网关|√|√|√|√|资源级别| -   AliyunVPNGatewayFullAccess
-   AliyunVPNGatewayReadOnlyAccess

 |[RAM鉴权](../../../../intl.zh-CN/API参考/RAM鉴权.md#)|
|全球加速|√|√|√|√|资源级别| -   AliyunGlobalAccelerationReadOnlyAccess
-   AliyunGlobalAccelerationFullAccess

 |[RAM鉴权](../../../../intl.zh-CN/API参考/RAM鉴权.md#)|
|智能接入网关|√|√|×|×|资源级别| -

 |[RAM鉴权](../../../../intl.zh-CN/API参考/RAM鉴权.md#)|
|云企业网|√|√|×|×|资源级别| -   AliyunCENReadOnlyAccess
-   AliyunCENFullAccess

 |[RAM鉴权](../../../../intl.zh-CN/API参考/RAM鉴权.md#)|

## 分析 {#section_05 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|E-MapReduce|√|√|×|×|服务级别| -   AliyunEMRFullAccess
-   AliyunEMRDevelopAccess
-   AliyunEMRFlowAdmin

 |-|
|Data Lake Analytics|√|√|×|×|操作级别| -   AliyunDLAFullAccess
-   AliyunDLAReadOnlyAccess

 |-|

## 云通信 {#section_06 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|消息服务|√|√|√|√|资源级别| -   AliyunMNSFullAccess
-   AliyunMNSReadOnlyAccess

 |-|
|短信服务|√|√|√|√|服务级别| -

 | -

 |

## 监控与管理 {#section_07 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|云监控|√|√|√|√|服务级别| -   AliyunCloudMonitorFullAccess
-   AliyunCloudMonitorReadOnlyAccess

 |[访问控制](../../../../intl.zh-CN/用户指南/访问控制.md#)|
|操作审计|√|√|√|√|资源级别| -

 |[RAM鉴权](../../../../intl.zh-CN/API参考/RAM鉴权.md#)|
|访问控制|√|√|√|√|资源级别| -   AliyunRAMFullAccess
-   AliyunRAMReadOnlyAccess

 |[RAM鉴权](../../../../intl.zh-CN/API参考（RAM）/RAM鉴权.md#)|
|密钥管理服务|√|√|√|√|资源级别| -   AliyunKMSFullAccess
-   AliyunKMSReadOnlyAccess
-   AliyunKMSCryptoAccess

 |[使用RAM实现KMS资源授权](../../../../intl.zh-CN/用户指南/使用RAM实现访问控制.md#)|
|智能顾问|-|-|-|-|操作级别|-|-|

## 应用服务 {#section_08 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|日志服务|√|√|√|√|资源级别| -   AliyunLogFullAccess
-   AliyunLogReadOnlyAccess

 |[鉴权规则](../../../../intl.zh-CN/API 参考/RAM__STS/鉴权规则.md#)|
|邮件推送|√|√|√|√|服务级别| -   AliyunDirectMailFullAccess
-   AliyunDirectMailReadOnlyAccess

 |-|
|API网关|√|√|√|√|服务级别| -   AliyunApiGatewayFullAccess
-   AliyunApiGatewayReadOnlyAccess

 | [使用RAM管理 API](https://www.alibabacloud.com/help/zh/doc-detail/48108.htm)|
|物联网平台|√|√|√|√|资源级别| -   AliyunIOTFullAccess
-   AliyunIOTReadOnlyAccess

 | [子账号访问](https://www.alibabacloud.com/help/zh/doc-detail/47496.htm)|
|区块链服务|√|√|√|√|资源级别|-| -

 |

## 互联网中间件 {#section_09 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|企业级分布式应用服务EDAS|√|√|×|×|服务级别|AliyunEDASFullAccess|[子账号管理](https://www.alibabacloud.com/help/zh/doc-detail/44023.htm)|
|分布式关系型数据库服务DRDS|√|√|×|√|资源级别| -   AliyunDRDSFullAccess
-   AliyunDRDSReadOnlyAccess

 | -

 |
|业务实时监控服务ARMS|√|√|×|×|服务级别|AliyunARMSFullAccess|[创建 RAM 子账号并授权](../../../../intl.zh-CN/访问控制/借助 RAM 用户实现分权.md#)|
|应用配置管理|√|√|√|√|资源级别|AliyunACMFullAccess|[访问权限控制](../../../../intl.zh-CN/访问控制/访问权限控制.md#)|

## 消息队列MQ {#section_10 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|消息队列RocketMQ|√|√|×|√|资源级别| -   AliyunMQFullAccess
-   AliyunMQPubOnlyAccess
-   AliyunMQSubOnlyAccess

 | [RAM子账号授权](https://www.alibabacloud.com/help/zh/doc-detail/61382.htm)

 |
|消息服务MNS|√|√|√|√|资源级别| -   AliyunMNSFullAccess
-   AliyunMNSReadOnlyAccess

 | -

 |

## 视频服务 {#section_12 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|媒体处理|√|√|×|√|服务级别| -   AliyunMTSFullAccess
-   AliyunMTSPlayerAuth

 |[子帐号使用控制台说明](../../../../intl.zh-CN/用户指南/子帐号使用控制台说明.md#)|
|视频点播|√|√|√|√|服务级别|AliyunVODFullAccess|-|
|视频直播|√|√|×|√|资源级别|AliyunLiveFullAccess|[API鉴权规则](../../../../intl.zh-CN/API参考/API鉴权规则.md#)|
|音视频通信RTC|√|√|×|×|资源级别| -

 | -

 |

## 大数据（数加） {#section_13 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|DataWorks|√|√|×|×|服务级别|AliyunDataWorksFullAccess|[用户使用子账号](../../../../intl.zh-CN/准备工作/用户使用子账号.md#)|
|Quick BI|√|√|×|×|服务级别|-|-|
|机器学习|√|√|×|×|服务级别|-|-|
|公众趋势分析|√|√|×|×|服务级别|-|-|
|DataV数据可视化|√|√|×|×|服务级别|-|-|
|MaxCompute|√|√|×|×|服务级别|-|-|
|阿里云 Elasticsearch|√|√|√|√|资源级别| -   AliyunElasticsearchReadOnlyAccess
-   AliyunElasticsearchFullAccess

 |[授权资源类型](../../../../intl.zh-CN/用户指南/访问控制/授权资源类型.md#)|
|机器翻译|-|-|-|-|服务级别|-|-|
|图像搜索|√|√|√|√|资源级别| -   AliyunImagesearchReadOnlyAccess
-   AliyunImagesearchFullAccess

 | [授权访问鉴权规则](https://www.alibabacloud.com/help/zh/doc-detail/66586.htm)

 |

## 安全（云盾） {#section_14 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|云安全中心（态势感知）|√|○|√|○|服务级别| -   AliyunYundunSASFullAccess
-   AliyunYundunSASReadOnlyAccess

 |-|
|安骑士（服务器安全）|√|○|√|○|服务级别| -   AliyunYundunAegisFullAccess
-   AliyunYundunAegisReadOnlyAccess

 |-|
|DDoS基础防护|√|○|√|○|服务级别| -   AliyunYundunDDosFullAccess
-   AliyunYundunDDosReadOnlyAccess

 |-|
|DDoS高防IP（国际）|√|○|√|○|服务级别| -   AliyunYundunAntiDDoSPremiumFullAccess
-   AliyunYundunAntiDDoSPremiumReadOnlyAccess

 |-|
|游戏盾|√|○|√|○|服务级别| AliyunYundunGameShieldReadOnlyAccess

 |-|
|Web应用防火墙（网络安全）|√|○|√|○|服务级别| -   AliyunYundunWAFFullAccess
-   AliyunYundunWAFReadOnlyAccess

 |-|
|SSL证书（应用安全）|√|○|√|○|服务级别| -   AliyunYundunCertFullAccess
-   AliyunYundunCertReadOnlyAccess

 |-|
|网站威胁扫描（应用安全）|√|○|√|○|服务级别|-|-|
|内容安全（业务安全）|√|○|√|○|服务级别|AliyunYundunGreenWebFullAccess|-|
|爬虫风险管理|√|○|√|○|服务级别| -   AliyunYundunAntibotFullAccess
-   AliyunYundunAntibotReadOnlyAccess

 |-|

## 云市场 {#section_15 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|云市场|√|○|√|○|服务级别|AliyunMarketplaceFullAccess|-|

## 域名与网站 {#section_16 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|云解析DNS|√|○|√|○|资源级别| -   AliyunDNSFullAccess
-   AliyunDNSReadOnlyAccess

 |-|
|域名|√|√|√|√|资源级别|AliyunDomainFullAccess|[Domain API 鉴权规则](../../../../intl.zh-CN/域名管理/RAM资源授权-域名/Domain API 鉴权规则.md#)|
|云虚拟主机|×|×|×|×|-|-|-|
|企业邮箱|×|×|×|×|-|-|-|

## 会员服务 {#section_17 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|备案|√|○|√|○|服务级别|-|-|

## 费用中心 {#section_18 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|费用中心|√|×|×|×|服务级别| -   AliyunBSSFullAccess
-   liyunBSSReadOnlyAccess
-   AliyunBSSOrderAccess

 |-|

## 工单 {#section_19 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|工单|√|○|×|○|服务级别|AliyunSupportFullAccess|-|

## 消息 {#section_20 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|消息中心|√|○|×|○|服务级别|AliyunNotificationsFullAccess|-|

