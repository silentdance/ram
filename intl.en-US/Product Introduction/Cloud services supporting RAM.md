# Cloud services supporting RAM {#concept_ofk_yt2_xdb .concept}

A large number of Alibaba Cloud services have been integrated with RAM. This document lists these services and provides relevant links for your quick reference.

When each product is being integrated with RAM functions, different levels of authorization granularity have been defined for RAM users:

-   Service level: Authorization is performed at the cloud product level. A RAM user either has all permissions or has no permission for the product.
-   Operation level: Authorization is performed at the API level. A RAM user can perform specified operations on a certain type of resource for a specified product.
-   Resource level: Authorization is performed at the operation level, which is the finest authorization granularity level. For example, authorizing a RAM user to restart only a specified cloud server.

## List of cloud services supporting RAM {#section_x2b_krs_q2b .section}

The following tables list the cloud services that support RAM in the following categories: [Elastic Computing](#section_b53_g52_xdb), [Database Services](#section_ep3_h52_xdb), [Storage & CDN](#section_ihm_352_xdb), [Networking](#section_az3_j52_xdb), [Analytics](#section_psg_k52_xdb), [Cloud Communication](#section_xlt_l52_xdb), [Monitoring and Management](#section_ypn_m52_xdb), [Application Service](#section_mfn_n52_xdb), [Middleware](#section_wck_452_xdb), [Mobile Service](#section_qqf_p52_xdb), [Media Services](#section_slb_q52_xdb), [Big Data \(data plus\)](#section_qbt_q52_xdb), [Security \(Alibaba Cloud Security\)](#section_tsn_r52_xdb), [Cloud Marketplace](#section_ejg_s52_xdb), and [Domain and Hosting](#section_spw_s52_xdb).

Each table contains the following information:

-   Service: name of the cloud service that supports RAM
-   Console: whether the current service supports RAM through the console; “∨” indicates "supported", “×” indicates "not supported", and “○” indicates "not available".
-   API: whether the current service supports RAM through the API; “∨” indicates "supported", “×” indicates "not supported", and “○” indicates "not available".
-   Authorization granularity: minimum authorization granularity provided by the current service
-   System policy: system policy supported by the current service
-   Reference: document link

## Elastic Computing {#section_b53_g52_xdb .section}

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Elastic Compute Service|√|√|Resource level| -   AliyunECSFullAccess
-   AliyunECSReadOnlyAccess

 |[ECS authorization rules](../../../../intl.en-US/API Reference/Authorization rules.md)|
|Server Load Balancer|√|√|Resource level| -   AliyunSLBFullAccess
-   AliyunSLBReadOnlyAccess

 |[SLB authorization rules](../../../../intl.en-US/Developer Guide/RAM authentication.md)|
|Auto Scaling|√|√|Service level| -   AliyunESSFullAccess
-   AliyunESSReadOnlyAccess

 |[Auto Scaling API usage instructions](https://help.aliyun.com/document_detail/25925.html)|
|Container Service|√|√|Service level|AliyunCSFullAccess|[Use sub-accounts](https://help.aliyun.com/document_detail/63578.html)|
|Container Registry|√|√|Resource level| -   AliyunContainerRegistryFullAccess
-   AliyunContainerRegistryReadOnlyAccess

 |[Repository access control](https://www.alibabacloud.com/help/zh/doc-detail/67992.htm?spm=a2796.11159934.1160638.1.19ae409aoYRHYp)|
|Resource Orchestration Service|√|√|Service level| -   AliyunROSFullAccess
-   AliyunROSReadOnlyAccess

 |[Use RAM to control resource access](https://www.alibabacloud.com/help/zh/doc-detail/48754.htm?spm=a2c63.p38356.b99.10.42d02cb78VbyLL)|
|BatchCompute|√|√|Service level|-|-|
|Function Compute|√|√|Resource level| -   AliyunFCFullAccess
-   AliyunFCInvocationAccess
-   AliyunFCReadOnlyAccess

 |-|
|Elastic HPC|√|√|Operation level| -   AliyunEHPCFullAccess
-   AliyunEHPCReadOnlyAccess

 |-|
|Simple Application Server|√|○|Operation level|AliyunSWASFullAccess|-|

## Database Services {#section_ep3_h52_xdb .section}

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|ApsaraDB for RDS|√|√|Resource level| -   AliyunRDSFullAccess
-   AliyunRDSReadOnlyAccess

 |[RDS authorization rules](https://help.aliyun.com/document_detail/26307.html)|
|ApsaraDB for MongoDB|√|√|Resource level| -   AliyunMongoDBFullAccess
-   AliyunMongoDBReadOnlyAccess

 |[MongoDB authorization rules](https://help.aliyun.com/document_detail/61757.html)|
|ApsaraDB for Redis|√|√|Resource level| -   AliyunKvstoreFullAccess
-   AliyunKvstoreReadOnlyAccess

 |[Redis authorization rules](https://help.aliyun.com/document_detail/61122.html)|
|ApsaraDB for Memcache|√|√|Service level| -   AliyunOCSFullAccess
-   AliyunOCSReadOnlyAccess

 |-|
|HiTSDB|√|√|Operation level|-|-|
|HybridDB for PostgreSQL|√|○|Resource level| -   AliyunGPDBFullAccess
-   AliyunGPDBReadOnlyAccess

 |-|
|Data Transmission Service|√|√|Service level| -   AliyunDTSFullAccess
-   AliyunDTSReadOnlyAccess

 |-|
|Distributed Relational Database Service|√|○|Resource level| -   AliyunDRDSFullAccess
-   AliyunDRDSReadOnlyAccess

 |-|

## Storage & CDN {#section_ihm_352_xdb .section}

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Object Storage Service|√|√|Resource level| -   AliyunOSSFullAccess
-   AliyunOSSReadOnlyAccess

 | -   [OSS rights control](https://help.aliyun.com/document_detail/56283.html)
-   [OSS authorization policy configuration](https://help.aliyun.com/document_detail/56288.html)
-   [OSS rights management best practices](https://help.aliyun.com/document_detail/31929.html)

 |
|Network Attached Storage|√|○|Service level| -   AliyunNASFullAccess
-   AliyunNASReadOnlyAccess

 |[Use permission groups](https://help.aliyun.com/document_detail/27534.html)|
|Table Store|√|√|Resource level| -   AliyunOTSFullAccess
-   AliyunOTSReadOnlyAccess
-   AliyunOTSWriteOnlyAccess

 |[Customize permissions](https://help.aliyun.com/document_detail/27362.html)|
|CDN|√|√|Resource level| -   AliyunCDNFullAccess
-   AliyunCDNReadOnlyAccess

 |[CDN authorization rules](https://help.aliyun.com/document_detail/27154.html)|
|Cloud Storage Gateway|√|○|Service level|AliyunHCSSGWFullAccess|-|
|Hybrid Backup|√|○|Resource level| -   AliyunHBRFullAccess
-   AliyunHBRReadOnlyAccess

 |-|

## Networking {#section_az3_j52_xdb .section}

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Virtual Private Cloud|√|√|Resource level| -   AliyunVPCFullAccess
-   AliyunVPCReadOnlyAccess

 |[VPC authorization rules](https://www.alibabacloud.com/help/zh/doc-detail/27777.htm)|
|Elastic IP Address|√|√|Resource level| -   AliyunEIPFullAccess
-   AliyunEIPReadOnlyAccess

 |[EIP authorization rules](https://www.alibabacloud.com/help/zh/doc-detail/27777.htm)|
|Express Connect|√|√|Resource level| -   AliyunExpressConnectFullAccess
-   AliyunExpressConnectReadOnlyAccess

 |[Express Connect authorization rules](https://www.alibabacloud.com/help/zh/doc-detail/31813.htm)|
|NAT Gateway|√|√|Resource level| -   AliyunNATGatewayReadOnlyAccess
-   AliyunNATGatewayFullAccess

 |-|

## Analytics {#section_psg_k52_xdb .section}

|Service|Console|API|Authorization granularity|System policy|Reference|
|-------|-------|---|-------------------------|-------------|---------|
|E-MapReduce|√|√|Service level|AliyunEMRFullAccess|[E-MapReduce role authorization](https://www.alibabacloud.com/help/zh/doc-detail/28072.htm)|
|HybridDB for PostgreSQL|√|√|Resource level| -   AliyunGPDBFullAccess
-   AliyunGPDBReadOnlyAccess

 |-|

## Cloud Communication {#section_xlt_l52_xdb .section}

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Message Service|√|√|Resource level| -   AliyunMNSFullAccess
-   AliyunMNSReadOnlyAccess

 |[Message Service authorization rules](https://help.aliyun.com/document_detail/27448.html)|
|DirectMail|√|√|Service level| -   AliyunDirectMailFullAccess
-   AliyunDirectMailReadOnlyAccess

 |-|
|Short Message Service|√|√|Service level|-|-|

## Monitoring and Management {#section_ypn_m52_xdb .section}

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|CloudMonitor|√|√|Service level| -   AliyunCloudMonitorFullAccess
-   AliyunCloudMonitorReadOnlyAccess

 |[RAM for CloudMonitor](https://help.aliyun.com/document_detail/43170.html)|
|Resource Access Management|√|√|Resource level| -   AliyunRAMFullAccess
-   AliyunRAMReadOnlyAccess

 |[RAM API reference](https://www.alibabacloud.com/help/zh/doc-detail/28672.htm)|
|ActionTrail|√|√|Resource level|-|-|
|Key Management Service|√|√|Resource level| -   AliyunKMSFullAccess
-   AliyunKMSReadOnlyAccess
-   AliyunKMSCryptoAccess

 |[KMS authorization rules](https://www.alibabacloud.com/help/zh/doc-detail/28953.htm)|

## Application Service {#section_mfn_n52_xdb .section}

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Log Service|√|√|Resource level| -   AliyunLogFullAccess
-   AliyunLogReadOnlyAccess

 | -   [Grant RAM sub-accounts permissions to access Log Service](https://www.alibabacloud.com/help/zh/doc-detail/47664.htm)
-   [Authorization rules](https://www.alibabacloud.com/help/zh/doc-detail/29052.htm)

 |
|API Gateway|√|√|Service level| -   Aliyunapigatewayfullaccess
-   AliyunApiGatewayReadOnlyAccess

 |-|
|DirectMail|√|√|Operation level| -   AliyunDirectMailFullAccess
-   AliyunDirectMailReadOnlyAccess

 |-|
|Message Service|√|√|Resource level| -   AliyunMNSFullAccess
-   AliyunMNSReadOnlyAccess

 |-|

## Middleware {#section_wck_452_xdb .section}

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Enterprise Distributed Application Service|√|×|Service level|AliyunEDASFullAccess|[Sub-accounts](https://help.aliyun.com/document_detail/44023.html)|
|Message Queue|√|√|Resource level| -   AliyunMQFullAccess
-   AliyunMQPubOnlyAccess
-   AliyunMQSubOnlyAccess

 |-|
|Application Real-Time Monitoring Service|√|×|Service level|-|-|
|Application configuration management|√|√|Resource level|-|-|

## Mobile Service {#section_qqf_p52_xdb .section}

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Mobile Security \(Application Security\)|√|√|Service level|AliyunYundunJaqFullAccess|-|

## Media Services {#section_slb_q52_xdb .section}

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Media Processing|√|√|Service level| -   AliyunMTSFullAccess
-   AliyunMTSPlayerAuth

 |[Sub-account console operating instructions](https://www.alibabacloud.com/help/zh/doc-detail/42841.htm)|
|ApsaraVideo for Live|√|√|Service level|AliyunLiveFullAccess|-|

## Big Data \(data plus\) {#section_qbt_q52_xdb .section}

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Quick BI|√|√|Service level|-|-|
|Machine Learning|√|√|Service level|-|-|
|DataV|√|√|Service level|-|-|
|Elasticsearch|√|√|Resource level|-|-|

## Security \(Alibaba Cloud Security\) {#section_tsn_r52_xdb .section}

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Server Guard \(Server Security\)|√|○|Service level|AliyunYundunAegisFullAccess|-|
|Anti-DDoS Basic|√|○|Service level| -   AliyunYundunDDosFullAccess
-   AliyunYundunDDosReadOnlyAccess

 |-|
|Anti-DDoS Pro|√|○|Service level| -   AliyunYundunHighFullAccess
-   AliyunYundunHighReadOnlyAccess

 |-|
|Web Application Firewall \(Network Security\)|√|○|Service level| -   AliyunYundunWAFFullAccess
-   AliyunYundunWAFReadOnlyAccess

 |-|
|Alibaba Content Security Service \(Business Security\)|√|○|Service level|-|-|
|Certificate Service|√|○|Service level|AliyunYundunCertFullAccess|-|
|Mobile Security|√|○|Service level|AliyunYundunJaqFullAccess|-|
|SSL Certificate \(Application Security\)|√|○|Service level| -   AliyunYundunCertFullAccess
-   AliyunYundunCertReadOnlyAccess

 |-|

## Cloud Marketplace {#section_ejg_s52_xdb .section}

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Cloud Marketplace|√|○|Service level|AliyunMarketplaceFullAccess|-|

## Domain and Hosting {#section_spw_s52_xdb .section}

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Alibaba Cloud DNS|√|○|Service level| -   AliyunDNSFullAccess
-   AliyunDNSReadOnlyAccess

 |-|

## List of cloud services supporting STS {#section_cwb_zt2_xdb .section}

The following table lists the cloud services that support STS.

The table conventions in this table are the same as those in [List of cloud services supporting RAM](intl.en-US/Product Introduction/Cloud services supporting RAM.md#ul_yx3_gtx_g2b).

|Service|Console|API|
|:------|:------|:--|
|Elastic Compute Service|√|√|
|ApsaraDB for RDS|√|√|
|Server Load Balancer|√|√|
|Object Storage Service|√|√|
|Virtual Private Cloud|√|√|

