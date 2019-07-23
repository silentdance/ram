# 支持RAM的云服务 {#concept_ofk_yt2_xdb .concept}

许多阿里云服务都与RAM/STS相集成，本文按服务类别罗列了这些服务，并提供每个服务支持的RAM授权粒度、系统策略，以及相关文档的链接，方便您使用及查询。

RAM（Resource Access Management）是阿里云为客户提供的用户身份管理与资源访问控制服务。

STS（Security Token Service）是阿里云提供的一种临时访问权限管理服务。

在集成RAM功能时，各产品针对RAM用户定义了不同级别的授权粒度，具体有：

-   服务级别：将云产品作为一个整体进行授权。一个RAM用户只能处于对这个产品拥有所有权限和没有任何权限两种状态。
-   操作级别：在API级别进行授权。一个RAM用户可以对指定云产品的某类资源执行某几个指定的操作。
-   资源级别：对执行资源的指定操作进行授权，这是最细的授权粒度。例如：授权一个RAM用户仅可对某一台云服务器进行重启操作。

## 支持RAM/STS的云服务列表 {#section_00 .section}

以下表格分别罗列了阿里云各个模块下支持 RAM/STS 的云服务：[弹性计算](#section_01)、[云数据库](#section_02)、[存储与CDN](#section_03)、[网络](#section_04)、[分析](#section_05)、[云通信](#section_06)、[监控与管理](#section_07)、[应用服务](#section_08)、[互联网中间件](#section_09)、[消息队列MQ](#section_10)、[移动云](#section_11)、[视频服务](#section_12)、[大数据（数加）](#section_13)、[安全（云盾）](#section_14)、[云市场](#section_15)、[域名与网站](#section_16)、[备案](#section_17)、[费用中心](#section_18)、[工单](#section_19)、[消息](#section_20)、[企业控制台](#section_21)。

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

 |[ECS鉴权规则](../../../../cn.zh-CN/API参考/鉴权规则.md#)|
|弹性伸缩 AutoScaling|√|√|√|√|服务级别| -   AliyunESSFullAccess
-   AliyunESSReadOnlyAccess

 |[API使用须知](../../../../cn.zh-CN/API参考/API使用须知.md#)|
|容器服务|√|√|×|√|服务级别| -   AliyunCSFullAccess
-   AliyunCSReadOnlyAccess

 |[使用子账号](../../../../cn.zh-CN/用户指南/授权管理/使用子账号.md#)|
|容器镜像服务|√|√|×|×|资源级别| -   AliyunContainerRegistryFullAccess
-   AliyunContainerRegistryReadOnlyAccess

 |[仓库访问控制](https:/alibabacloud.com/help/doc-detail/67992.html)|
|资源编排ROS|√|√|√|√|服务级别| -   AliyunROSFullAccess
-   AliyunROSReadOnlyAccess

 |[使用 RAM 控制资源访问](../../../../cn.zh-CN/快速入门/使用 RAM 控制资源访问.md#)|
|批量计算BatchCompute|√|√|√|√|服务级别| AliyunBatchComputeFullAccess

 |-|
|函数计算|√|√|√|√|资源级别| -   AliyunFCFullAccess
-   AliyunFCInvocationAccess
-   AliyunFCReadOnlyAccess

 |[子账号控制台快速指导](https://help.aliyun.com/document_detail/55617.html)|
|弹性高性能计算|√|√|√|√|服务级别| -   AliyunEHPCFullAccess
-   AliyunEHPCReadOnlyAccess

 |-|
|轻量应用服务器|√|○|×|○|服务级别|AliyunSWASFullAccess|-|
|图形工作站|√|○|×|○|服务级别|-|-|
|弹性容器实例ECI|√|√|√|√|资源级别| -   AliyunECIFullAccess
-   AliyunECIReadOnlyAccess

 |[如何为子账号授权](https://help.aliyun.com/document_detail/92790.html)|

## 云数据库 {#section_02 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|云数据库POLARDB|√|√|√|√|操作级别| -   AliyunPolardbReadOnlyAccess
-   AliyunPolardbFullAccess

 |[创建和使用子账号](../../../../cn.zh-CN/POLARDB for MySQL用户指南/账号管理/创建和使用子账号.md#)|
|云数据库RDS 版|√|√|√|√|资源级别| -   AliyunRDSFullAccess
-   AliyunRDSReadOnlyAccess

 |[RAM资源授权](../../../../cn.zh-CN/API参考/RAM资源授权.md#)|
|云数据库MongoDB版|√|√|√|√|资源级别| -   AliyunMongoDBFullAccess
-   AliyunMongoDBReadOnlyAccess

 |[MongoDB API的鉴权规则](../../../../cn.zh-CN/API参考/如何使用RAM授权/MongoDB API的鉴权规则.md#)|
|云数据库Redis版|√|√|√|√|资源级别| -   AliyunKvstoreFullAccess
-   AliyunKvstoreReadOnlyAccess

 |[RAM鉴权](../../../../cn.zh-CN/API参考/RAM鉴权.md#)|
|云数据库Memcache版|√|√|√|√|服务级别| -   AliyunOCSFullAccess
-   AliyunOCSReadOnlyAccess

 |-|
|云数据库HybridDB for MySQL|√|√|√|√|资源级别| -   AliyunPetaDataFullAccess
-   AliyunPetaDataReadOnlyAccess

 |[API鉴权规则](../../../../cn.zh-CN/API参考/如何使用RAM授权/API鉴权规则.md#)|
|云数据库Hbase版|√|√|√|√|资源级别|-|-|
|时序时空数据库TSDB|√|√|√|√|操作级别| -   AliyunHiTSDBReadOnlyAccess
-   AliyunHiTSDBFullAccess

 |-|
|云数据库HybridDB for PostgreSQL|√|√|√|√|资源级别| -   AliyunGPDBFullAccess
-   AliyunGPDBReadOnlyAccess

 |[API的鉴权规则](../../../../cn.zh-CN/API参考/如何使用RAM授权/API的鉴权规则.md#)|
|云数据库OceanBase|×|×|×|×|-|-|-|
|分析型数据库|√|×|×|×|服务级别|-|[使用阿里云访问控制（RAM）进行权限管理](https://help.aliyun.com/document_detail/95521.html)|
|数据传输服务DTS|√|√|√|√|服务级别| -   AliyunDTSFullAccess
-   AliyunDTSReadOnlyAccess

 |[DTS授权和子账号管理DTS实例](https://help.aliyun.com/document_detail/52589.html)|
|数据管理DMS|√|○|√|○|资源级别|-|[云资源授权](https://help.aliyun.com/document_detail/47571.html)|
|数据库备份DBS|√|√|√|√|服务级别| -   AliyunDBSFullAccess
-   AliyunDBSReadOnlyAccess

 |-|
|混合云数据库管理HDM|√|○|√|○|服务级别| -   AliyunHDMReadOnlyAccess
-   AliyunHDMFullAccess

 |[子账号如何使用HDM](https://help.aliyun.com/knowledge_detail/66674.html)|
|分布式关系型数据库DRDS|√|√|√|√|资源级别| -   AliyunDRDSReadOnlyAccessyAccess
-   AliyunDRDSFullAccess

 |[DRDS支持的资源授权](https://help.aliyun.com/document_detail/51480.html) |
|图数据库GDB|√|√|×|×|资源级别|-|-|
|数据库和应用迁移|√|○|×|○|服务级别| -   AliyunADAMReadOnlyAccess
-   AliyunADAMFullAccess

 |-|

## 存储与CDN {#section_03 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|对象存储OSS|√|√|√|√|资源级别| -   AliyunOSSFullAccess
-   AliyunOSSReadOnlyAccess

 |[如何构建RAM Policy](../../../../cn.zh-CN/开发指南/权限控制/基于RAM Policy的权限控制/如何构建RAM Policy.md#)|
|文件存储NAS|√|○|×|○|操作级别| -   AliyunNASFullAccess
-   AliyunNASReadOnlyAccess

 |[../../../../dita-oss-bucket/SP\_111/DNnas1882233/ZH-CN\_TP\_18697.md\#](../../../../cn.zh-CN/控制台用户指南/管理权限/管理权限组.md#)|
|表格存储|√|√|√|√|资源级别| -   AliyunOTSFullAccess
-   AliyunOTSReadOnlyAccess
-   AliyunOTSWriteOnlyAccess

 |[../../../../dita-oss-bucket/SP\_28/DNots1887058/ZH-CN\_TP\_20298.md\#](../../../../cn.zh-CN/开发指南/授权管理/自定义权限.md#)|
|CDN|√|√|√|√|资源级别| -   AliyunCDNFullAccess
-   AliyunCDNReadOnlyAccess

 |[CDN API鉴权规则](../../../../cn.zh-CN/旧版API参考/RAM资源授权/CDN API鉴权规则.md#)|
|PCDN|√|√|√|√|资源级别| -   AliyunPCDNFullAccess
-   AliyunPCDNReadOnlyAccess

 |[PCDN API鉴权规则](https://help.aliyun.com/document_detail/58028.html)|
|全站加速|√|√|√|√|资源级别| -   AliyunDCDNFullAccess
-   AliyunDCDNReadOnlyAccess

 |-|
|云存储网关|√|○|×|○|服务级别|AliyunHCSSGWFullAccess|-|
|智能云相册|√|√|×|√|资源级别| -   AliyunCloudPhotoFullAccess
-   AliyunCloudPhotoReadOnlyAccess

 |[授权映射表](https://help.aliyun.com/document_detail/56485.html)|
|混合云备份|√|○|×|○|资源级别| -   AliyunHBRFullAccess
-   AliyunHBRReadOnlyAccess

 |-|
|混合云容灾|√|○|×|○|服务级别|AliyunHDRFullAccess|-|
|安全加速SCDN|√|√|×|×|资源级别| -   AliyunSCDNReadOnlyAccess
-   AliyunSCDNFullAccess

 |-|
|智能媒体管理|√|√|×|×|服务级别| -   AliyunIMMReadOnlyAccess
-   AliyunIMMFullAccess

 |[子账户使用指南](https://help.aliyun.com/document_detail/73265.html)|
|闪电立方|√|○|×|○|服务级别|AliyunMGWFullAccess|-|
|边缘节点服务ENS|√|√|√|√|资源级别| -   AliyunENSReadOnlyAccess
-   AliyunENSFullAccess

 |-|
|文件存储HDFS|√|√|×|×|资源级别|-|[使用RAM授权访问](../../../../cn.zh-CN/用户指南/使用RAM授权访问.md#)|

## 网络 {#section_04 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|专有网络VPC|√|√|√|√|资源级别| -   AliyunVPCFullAccess
-   AliyunVPCReadOnlyAccess

 |[RAM鉴权](../../../../cn.zh-CN/API参考/RAM鉴权.md#)|
|负载均衡|√|√|√|√|资源级别| -   AliyunSLBReadOnlyAccess
-   AliyunSLBFullAccess

 |[RAM鉴权](../../../../cn.zh-CN/API参考/RAM鉴权.md#)|
|共享流量包|√|○|√|○|服务级别|-|-|
|弹性公网IP|√|√|√|√|资源级别| -   AliyunEIPFullAccess
-   AliyunEIPReadOnlyAccess

 |[RAM鉴权](../../../../cn.zh-CN/API参考/RAM鉴权.md#)|
|高速通道ExpressConnect|√|√|√|√|资源级别| -   AliyunExpressConnectFullAccess
-   AliyunExpressConnectReadOnlyAccess

 |[RAM鉴权](../../../../cn.zh-CN/API参考/RAM鉴权.md#)|
|NAT网关|√|√|√|√|资源级别| -   AliyunNATGatewayReadOnlyAccess
-   AliyunNATGatewayFullAccess

 |[RAM鉴权](../../../../cn.zh-CN/API参考/RAM鉴权.md#)|
|VPN网关|√|√|√|√|资源级别| -   AliyunVPNGatewayFullAccess
-   AliyunVPNGatewayReadOnlyAccess

 |[RAM鉴权](../../../../cn.zh-CN/API参考/RAM鉴权.md#)|
|共享带宽|√|√|√|√|资源级别| -   AliyunCommonBandwidthPackageReadOnlyAccess
-   AliyunCommonBandwidthPackageFullAccess

 |-|
|全球加速|√|√|√|√|资源级别| -   AliyunGlobalAccelerationReadOnlyAccess
-   AliyunGlobalAccelerationFullAccess

 |[RAM鉴权](../../../../cn.zh-CN/API参考/RAM鉴权.md#)|
|智能接入网关|√|√|×|×|资源级别| -   AliyunSmartAccessGatewayFullAccess
-   AliyunSmartAccessGatewayReadOnlyAccess

 |[RAM鉴权](../../../../cn.zh-CN/API参考/RAM鉴权.md#)|
|IPv6转换服务|√|√|×|×|资源级别| -   AliyunIPv6TranslationFullAccess
-   AliyunIPv6TranslationReadOnlyAccess

 |[RAM鉴权](../../../../cn.zh-CN/API参考/RAM鉴权.md#)|
|云企业网|√|√|×|×|资源级别| -   AliyunCENReadOnlyAccess
-   AliyunCENFullAccess

 |[RAM鉴权](../../../../cn.zh-CN/API参考/RAM鉴权.md#)|

## 分析 {#section_05 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|E-MapReduce|√|√|×|×|服务级别| AliyunEMRFullAccess

 |-|
|数据集成（旧版）|×|×|×|×|-|-|-|
|Data Lake Analytics|√|√|×|×|操作级别| -   AliyunDLAFullAccess
-   AliyunDLAReadOnlyAccess

 |-|

## 云通信 {#section_06 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|消息服务|√|√|√|√|资源级别| -   AliyunMNSFullAccess
-   AliyunMNSReadOnlyAccess

 |-|
|语音服务|√|√|√|√|服务级别| -   AliyunDyvmsFullAccess
-   AliyunDyvmsReadOnlyAccess

 |[语音权限访问控制](https://help.aliyun.com/document_detail/55766.html)|
|流量服务|√|√|√|√|服务级别| -   AliyunDycdpFullAccess
-   AliyunDycdpReadOnlyAccess

 |[流量权限访问控制](https://help.aliyun.com/document_detail/55767.html)|
|短信服务|√|√|√|√|服务级别| -   AliyunSMSFullAccess
-   AliyunSMSReadOnlyAccess

 |[短信权限访问控制](https://help.aliyun.com/document_detail/55764.html) |
|物联网无线连接服务|√|√|√|√|服务级别| -   AliyunDyiotFullAccess
-   AliyunDyiotReadOnly

 |[访问权限控制](https://help.aliyun.com/document_detail/59434.html)|
|号码隐私保护|√|√|√|√|服务级别| -   AliyunDyplsFullAccess
-   AliyunDyplsReadOnlyAccess
-   AliyunCloudCommunicationFullAccess
-   AliyunCloudCommunicationReadOnlyAccess

 |[号码权限访问控制](https://help.aliyun.com/document_detail/59872.html)|
|号码认证服务|√|√|×|×|服务级别| -   AliyunDypnsFullAccess
-   AliyunDypnsReadOnlyAccess

 |[关于访问控制RAM](https://help.aliyun.com/document_detail/88440.html)|
|云通信网络加速|√|√|×|×|操作级别| -   AliyunSNSUFullAccess
-   AliyunSNSUReadOnlyAccess

 |-|

## 监控与管理 {#section_07 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|云监控|√|√|√|√|服务级别| -   AliyunCloudMonitorFullAccess
-   AliyunCloudMonitorReadOnlyAccess

 |[访问控制](../../../../cn.zh-CN/用户指南/访问控制.md#)|
|操作审计|√|√|√|√|资源级别| -   AliyunActionTrailFullAccess
-   AliyunActionTrailReadOnlyAccess

 |[RAM鉴权](../../../../cn.zh-CN/API参考/RAM鉴权.md#)|
|访问控制|√|√|√|√|资源级别| -   AliyunRAMFullAccess
-   AliyunRAMReadOnlyAccess

 |[RAM鉴权](../../../../cn.zh-CN/API参考（RAM）/RAM鉴权.md#)|
|密钥管理服务|√|√|√|√|资源级别| -   AliyunKMSFullAccess
-   AliyunKMSReadOnlyAccess
-   AliyunKMSCryptoAccess

 |[使用RAM实现KMS资源授权](../../../../cn.zh-CN/用户指南/使用 RAM 实现 KMS 资源授权.md#)|
|智能顾问|√|√|√|√|操作级别| -   AliyunAdvisorFullAccess
-   AliyunAdvisorReadOnlyAccess

 |-|

## 应用服务 {#section_08 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS\)|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:--------|:-------|:---|:---|:---|
|日志服务|√|√|√|√|资源级别| -   AliyunLogFullAccess
-   AliyunLogReadOnlyAccess

 |[鉴权规则](../../../../cn.zh-CN/API 参考/RAM__STS/鉴权规则.md#)|
|开放搜索|√|√|×|×|资源级别|AliyunOpenSearchFullAccess|[访问鉴权规则](https://help.aliyun.com/document_detail/53744.html)|
|性能测试PTS|√|√|√|√|服务级别|AliyunPTSFullAccess|-|
|邮件推送|√|√|√|√|服务级别| -   AliyunDirectMailFullAccess
-   AliyunDirectMailReadOnlyAccess

 |-|
|API网关|√|√|√|√|服务级别| -   AliyunApiGatewayFullAccess
-   AliyunApiGatewayReadOnlyAccess

 | -

 |
|物联网平台|√|√|√|√|资源级别| -   AliyunIOTFullAccess
-   AliyunIOTReadOnlyAccess

 | -

 |
|智能对话分析服务|√|√|√|√|资源级别| -   AliyunSCAFullAccess
-   AliyunSCAReadOnlyAccess

 |[如何使用阿里云子账号登录](https://help.aliyun.com/document_detail/99311.html)|
|云效|√|√|×|×|资源级别| -   AliyunRDCFullAccess
-   AliyunRDCReadOnlyAccess

 |-|
|云AP|×|×|×|×|-|-|-|
|云桌面|√|○|√|○|服务级别|-|-|
|CodePipeline|√|√|×|√|资源级别|AliyunCodePipelineFullAccess|[授权策略示例](https://help.aliyun.com/document_detail/63799.html)|
|云客服|×|○|×|○|-|-|-|
|云小蜜|√|√|×|×|服务级别|AliyunChatbotFullAccess|-|
|云呼叫中心|√|√|×|×|服务级别|AliyunCCCFullAccess|-|
|Node.js性能平台|√|○|√|○|服务级别|AliyunNPPFullAccess|[子账号授权](https://help.aliyun.com/document_detail/65672.html)|
|API控制台|×|○|×|○|-|-|-|
|智联车管理云平台|√|√|×|×|服务级别| -   AliyunIoVCCFullAccess
-   AliyunIoVCCConfigAccess
-   AliyunIoVCCReadOnlyAccess

 |-|
|区块链服务|√|√|√|√|资源级别|-|[鉴权规则](https://help.aliyun.com/document_detail/99202.html) |
|智能推荐|√|√|×|×|资源级别| -   AliyunAIRecFullAccess
-   AliyunAIRecReadOnlyAccess

 |-|
|物联网络管理平台|√|√|×|×|资源级别| -   AliyunLinkWANFullAccess
-   AliyunLinkWANReadOnlyAccess

 |[自定义权限](https://help.aliyun.com/document_detail/112452.html)|
|IoT设备身份认证|√|√|√|√|资源级别| -   AliyunIOTIDFullAccess
-   AliyunIOTIDReadOnlyAccess
-   AliyunIOTIDVerifyAccess

 |-|
|宜搭|√|○|×|○|服务级别|-|-|

## 互联网中间件 {#section_09 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|企业级分布式应用服务EDAS|√|√|×|×|服务级别|AliyunEDASFullAccess|[子账号管理](https://help.aliyun.com/document_detail/44023.html)|
|分布式关系型数据库服务DRDS|√|√|×|√|资源级别| -   AliyunDRDSFullAccess
-   AliyunDRDSReadOnlyAccess

 |[DRDS支持的资源授权](https://help.aliyun.com/document_detail/51480.html) |
|业务实时监控服务ARMS|√|√|×|×|服务级别|AliyunARMSFullAccess|[创建 RAM 子账号并授权](../../../../cn.zh-CN/访问控制/借助 RAM 用户实现分权.md#)|
|云服务总线|√|√|√|√|资源级别|AliyunCSBFullAccess|[子账号支持](https://help.aliyun.com/document_detail/66522.html)|
|全局事务服务|×|×|×|×|-|-|-|
|应用配置管理|√|√|√|√|资源级别|AliyunACMFullAccess|[访问权限控制](../../../../cn.zh-CN/访问控制/访问权限控制.md#)|
|链路追踪|√|○|×|○|服务级别|AliyunTracingAnalysisFullAccess|-|
|应用高可用服务|√|○|×|○|服务级别| -   AliyunAHASFullAccess
-   AliyunAHASReadOnlyAccess

 |-|

## 消息队列MQ {#section_10 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|消息队列RocketMQ|√|√|×|√|资源级别| -   AliyunMQFullAccess
-   AliyunMQPubOnlyAccess
-   AliyunMQSubOnlyAccess

 |[RAM子账号授权](https://help.aliyun.com/document_detail/61382.html) |
|消息队列Kafka|√|√|×|×|服务级别| -   AliyunKafkaFullAccess
-   AliyunKafkaPubOnlyAccess
-   AliyunKafkaSubOnlyAccess

 |[RAM访问控制](https://help.aliyun.com/document_detail/68338.html)|
|消息队列AMQP|√|√|×|×|资源级别| -   AliyunAMQPFullAccess
-   AliyunAMQPReadOnlyAccess

 |[RAM子账户授权](https://help.aliyun.com/document_detail/110522.html)|
|微消息队列for IoT|√|√|×|×|服务级别|-|-|
|消息服务MNS|√|√|√|√|资源级别| -   AliyunMNSFullAccess
-   AliyunMNSReadOnlyAccess

 |[授权子账号访问MNS](https://help.aliyun.com/document_detail/27446.html) |

## 移动云 {#section_11 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|移动用户反馈|√|√|×|×|服务级别| -   AliyunFeedbackFullAccess
-   AliyunFeedbackReadOnlyAccess

 |[鉴权Action与鉴权规则](https://help.aliyun.com/document_detail/55906.html)|
|移动热修复|√|√|×|×|服务级别| -   AliyunHotfixFullAccess
-   AliyunHotfixReadOnlyAccess

 |[鉴权规则](https://help.aliyun.com/document_detail/55889.html)|
|移动推送|√|√|√|√|服务级别| -   AliyunMPushFullAccess
-   AliyunMPushReadOnlyAccess

 |[鉴权规则](https://help.aliyun.com/document_detail/48059.html)|
|移动测试|√|○|√|○|资源级别| -   AliyunMobileTestingReadOnlyAccess
-   AliyunMobileTestingFullAccess

 |[授权管理](https://help.aliyun.com/document_detail/93670.html)|
|移动数据分析|√|○|×|○|服务级别|-|[RAM子账号访问](https://help.aliyun.com/document_detail/56608.html)|

## 视频服务 {#section_12 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|媒体处理|√|√|×|√|服务级别| -   AliyunMTSFullAccess
-   AliyunMTSPlayerAuth

 |[子帐号使用控制台说明](../../../../cn.zh-CN/用户指南/子帐号使用控制台说明.md#)|
|视频点播|√|√|√|√|服务级别|AliyunVODFullAccess|-|
|视频直播|√|√|×|√|资源级别|AliyunLiveFullAccess|[API鉴权规则](../../../../cn.zh-CN/API参考/API鉴权规则.md#)|
|音视频通信RTC|√|√|×|×|资源级别| -   AliyunRTCFullAccess
-   AliyunRTCReadOnlyAccess

 |[RAM资源授权](https://help.aliyun.com/document_detail/74559.html) |
|智能视觉|×|×|×|×|-|-|-|
|视频监控|×|×|×|×|-|-|-|

## 大数据（数加） {#section_13 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|DataWorks|√|√|×|×|服务级别|AliyunDataWorksFullAccess|[用户使用子账号](https://help.aliyun.com/document_detail/55316.html) |
|Quick BI|√|√|×|×|服务级别|-|-|
|机器学习|√|√|×|×|服务级别|-|-|
|推荐引擎|√|√|×|×|服务级别|-|-|
|公众趋势分析|√|√|×|×|服务级别|-|-|
|DataV数据可视化|√|√|×|×|服务级别|-|-|
|MaxCompute|√|√|×|×|服务级别|-|-|
|智能语音交互|√|√|×|×|服务级别| -   AliyunSCAFullAccess
-   AliyunSCAReadOnlyAccess

 |-|
|实时计算|√|√|×|×|服务级别|-|-|
|画像分析|√|√|×|×|服务级别|-|-|
|企业图谱|√|√|×|×|服务级别|-|-|
|数据集成|√|√|×|×|服务级别|-|-|
|人脸识别|√|√|×|×|服务级别|-|-|
|图像识别|√|×|×|×|服务级别|-|-|
|阿里云 Elasticsearch|√|√|√|√|资源级别| -   AliyunElasticsearchReadOnlyAccess
-   AliyunElasticsearchFullAccess

 |[授权资源类型](../../../../cn.zh-CN/用户指南/访问控制/授权资源类型.md#)|
|自然语言处理|×|√|×|×|服务级别|-|-|
|机器翻译|×|√|×|×|服务级别|-|-|
|I+关系网络分析|√|√|×|×|服务级别|-|-|
|图像搜索|√|√|√|√|资源级别| -   AliyunImagesearchReadOnlyAccess
-   AliyunImagesearchFullAccess

 |[授权访问鉴权规则](https://help.aliyun.com/document_detail/66586.html) |

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
|DDoS高防IP|√|○|√|○|服务级别| -   AliyunYundunHighFullAccess
-   AliyunYundunHighReadOnlyAccess

 |-|
|游戏盾|√|○|√|○|服务级别| -   AliyunYundunGameShieldReadOnlyAccess
-   AliyunYundunGameShieldFullAccess

 |-|
|Web应用防火墙（网络安全）|√|○|√|○|服务级别| -   AliyunYundunWAFFullAccess
-   AliyunYundunWAFReadOnlyAccess

 |-|
|SSL证书（应用安全）|√|○|√|○|服务级别| -   AliyunYundunCertFullAccess
-   AliyunYundunCertReadOnlyAccess

 |-|
|风险识别（业务安全）|√|○|√|○|服务级别|AliyunYundunSAFFullAccess|-|
|先知（安全服务）|√|○|√|○|服务级别|AliyunYundunXianzhiFullAccess|-|
|云防火墙|√|○|√|○|服务级别| -   AliyunYundunCloudFirewallReadOnlyAccess
-   AliyunYundunCloudFirewallFullAccess

 |-|
|实人认证|√|○|√|○|服务级别| -   AliyunYundunCloudAuthReadOnlyAccess
-   AliyunYundunCloudAuthFullAccess

 |-|
|网站威胁扫描（应用安全）|√|○|√|○|服务级别|-|-|
|安全管家 （安全服务）|√|○|√|○|服务级别|-|-|
|加密服务 （数据安全）|√|○|√|○|服务级别|AliyunYundunHSMFullAccess|-|
|内容安全（业务安全）|√|○|√|○|服务级别|AliyunYundunGreenWebFullAccess|-|
|数据风控（业务安全）|√|○|√|○|服务级别|AliyunYundunAFSFullAccess|-|
|移动安全|√|○|×|○|服务级别|AliyunYundunJaqFullAccess|-|
|合作伙伴中心|√|○|×|○|服务级别|AliyunYundunPartnerFullAccess|-|
|数据库审计|√|○|√|○|服务级别|AliyunYundunDbAuditFullAccess|-|
|堡垒机|√|○|√|○|服务级别|AliyunYundunBastionHostFullAccess|-|
|爬虫风险管理|√|○|√|○|服务级别| -   AliyunYundunAntibotFullAccess
-   AliyunYundunAntibotReadOnlyAccess

 |-|
|敏感数据保护（数据安全）|√|○|√|○|服务级别| -   AliyunYundunSDDPFullAccess
-   AliyunYundunSDDPReadOnlyAccess

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
|域名|√|√|√|√|资源级别|AliyunDomainFullAccess|[Domain API 鉴权规则](../../../../cn.zh-CN/域名管理/RAM资源授权-域名/Domain API 鉴权规则.md#)|
|HTTPDNS|√|√|√|√|资源级别| -   AliyunHTTPDNSFullAccess
-   AliyunHTTPDNSReadOnlyAccess

 |[鉴权Action与鉴权规则](https://help.aliyun.com/document_detail/56803.html)|
|云虚拟主机|×|×|×|×|-|-|-|
|企业邮箱|×|×|×|×|-|-|-|
|标准建站|×|×|×|×|-|-|-|
|弹性Web托管|×|×|×|×|-|-|-|
|商标服务|×|×|×|×|-|-|-|

## 备案 {#section_17 .section}

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

## 企业控制台 {#section_21 .section}

|服务名|控制台（RAM）|API（RAM）|控制台（STS）|API（STS）|授权粒度|系统策略|相关文档|
|:--|:-------|:-------|:-------|:-------|:---|:---|:---|
|财务管理|√|○|×|○|服务级别| -   AliyunFinanceConsoleReadOnlyAccess
-   AliyunFinanceConsoleFullAccess

 |-|

