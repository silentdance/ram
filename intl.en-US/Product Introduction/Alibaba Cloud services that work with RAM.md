# Alibaba Cloud services that work with RAM {#concept_ofk_yt2_xdb .concept}

This topic describes the Alibaba Cloud services that integrate with Alibaba Cloud RAM and Alibaba Cloud STS, the authorization granularity and policies supported by each service, and links to these services.

When a product is integrated with RAM, relevant permissions are granted to RAM users according to the following authorization granularities:

-   Service: RAM users are authorized by cloud product. A RAM user either has all permissions or has no permission on a cloud product.
-   Operation: RAM users are authorized by API. A RAM user can perform specified operations on specified resources of a specified cloud product.
-   Resource: RAM users are authorized by resource operation. For example, you can grant the permission of restarting a cloud server to a RAM user. Resource is the finest granularity of authorization in Alibaba Cloud RAM.

## Supported services {#section_00 .section}

The following tables detail the cloud services that support RAM and STS, and relevant content for your reference. Note that a circle \(○\) indicates the corresponding function is not applicable to the corresponding service.

## Elastic Computing {#section_01 .section}

|Service|Supports RAM console access?|Supports RAM API access?|Supports STS console access?|Supports STS API access?|Authorization granularity \(minimum\)|System policy|Reference|
|:------|:---------------------------|:-----------------------|:---------------------------|:-----------------------|:------------------------------------|:------------|:--------|
|Elastic Compute Service|√|√|√|√|Resource| -   AliyunECSFullAccess
-   AliyunECSReadOnlyAccess

 |[ECS authorization rules](../../../../../reseller.en-US/API Reference/Authorization rules.md#)|
|Server Load Balancer|√|√|√|√|Resource| -   AliyunSLBFullAccess
-   AliyunSLBReadOnlyAccess

 |[SLB authorization rules](../../../../../reseller.en-US/Developer Guide/RAM authentication.md)|
|Auto Scaling|√|√|×|×|Resource| -   AliyunESSFullAccess
-   AliyunESSReadOnlyAccess

 |[API usage instructions](../../../../../reseller.en-US/API-Reference/API usage instructions.md#)|
|Container Service for Kubernetes|√|√|×|×|Resource|AliyunCSFullAccess|[Use sub-accounts](../../../../../reseller.en-US/User Guide/Authorizations/Use sub-accounts.md#)|
|Container Registry|√|√|×|×|Resource| -   AliyunContainerRegistryFullAccess
-   AliyunContainerRegistryReadOnlyAccess

 |[Repository access control](https:/alibabacloud.com/help/doc-detail/67992.html)|
|Resource Orchestration Service|√|√|×|×|Resource| -   AliyunROSFullAccess
-   AliyunROSReadOnlyAccess

 |[Use RAM to control resource access](../../../../../reseller.en-US/Quick Start/Use RAM to control resource access.md#)|
|BatchCompute|√|√|×|×|Resource|-|-|
|Function Compute|√|√|×|√|Resource| -   AliyunFCFullAccess
-   AliyunFCInvocationAccess
-   AliyunFCReadOnlyAccess

 |-|
|E-HPC|√|√|×|×|Operation| -   AliyunEHPCFullAccess
-   AliyunEHPCReadOnlyAccess

 |-|
|Simple Application Server|√|○|×|×|Operation|AliyunSWASFullAccess|-|

## ApsaraDB {#section_02 .section}

|Service|Supports RAM console access?|Supports RAM API access?|Supports STS console access?|Supports STS API access?|Authorization granularity \(minimum\)|System policy|Reference|
|:------|:---------------------------|:-----------------------|:---------------------------|:-----------------------|:------------------------------------|:------------|:--------|
|ApsaraDB for RDS|√|√|√|√|Resource| -   AliyunRDSFullAccess
-   AliyunRDSReadOnlyAccess

 | |
|ApsaraDB for MongoDB|√|√|×|×|Resource| -   AliyunMongoDBFullAccess
-   AliyunMongoDBReadOnlyAccess

 |-|
|ApsaraDB for Redis|√|√|×|×|Resource| -   AliyunKvstoreFullAccess
-   AliyunKvstoreReadOnlyAccess

 |-|
|ApsaraDB for Memcache|√|√|×|×|Service| -   AliyunOCSFullAccess
-   AliyunOCSReadOnlyAccess

 |-|
|\(High-Performance Time Series Database\) HiTSDB|√|√|×|×|Operation|-|-|
|HybridDB for PostgreSQL|√|○|×|×|Resource| -   AliyunGPDBFullAccess
-   AliyunGPDBReadOnlyAccess

 |[Authentication rules for APIs](../../../../../reseller.en-US/API Reference/Use RAM for resource authorization/Authentication rules for APIs.md#)|
|Data Transmission Service|√|√|×|×|Service| -   AliyunDTSFullAccess
-   AliyunDTSReadOnlyAccess

 |-|
|Distributed Relational Database Service|√|○|×|×|Resource| -   AliyunDRDSFullAccess
-   AliyunDRDSReadOnlyAccess

 |-|

## Storage & CDN {#section_03 .section}

|Service|Supports RAM console access?|Supports RAM API access?|Supports STS console access?|Supports STS API access?|Authorization granularity \(minimum\)|System policy|Reference|
|:------|:---------------------------|:-----------------------|:---------------------------|:-----------------------|:------------------------------------|:------------|:--------|
|Object Storage Service|√|√|√|√|Resource| -   AliyunOSSFullAccess
-   AliyunOSSReadOnlyAccess

 |--

|
|NAS|√|○|×|×|Service| -   AliyunNASFullAccess
-   AliyunNASReadOnlyAccess

 | |
|Table Store|√|√|×|×|Resource| -   AliyunOTSFullAccess
-   AliyunOTSReadOnlyAccess
-   AliyunOTSWriteOnlyAccess

 | |
|Alibaba Cloud CDN|√|√|×|×|Resource| -   AliyunCDNFullAccess
-   AliyunCDNReadOnlyAccess

 | |
|Cloud Storage Gateway|√|○|×|×|Service|AliyunHCSSGWFullAccess|-|
|Hybrid Backup Recovery|√|○|×|×|Resource| -   AliyunHBRFullAccess
-   AliyunHBRReadOnlyAccess

 |-|

## Networking {#section_04 .section}

|Service|Supports RAM console access?|Supports RAM API access?|Supports STS console access?|Supports STS API access?|Authorization granularity \(minimum\)|System policy|Reference|
|:------|:---------------------------|:-----------------------|:---------------------------|:-----------------------|:------------------------------------|:------------|:--------|
|Virtual Private Cloud|√|√|√|√|Resource| -   AliyunVPCFullAccess
-   AliyunVPCReadOnlyAccess

 |[RAM authentication](../../../../../reseller.en-US/API reference/RAM authentication.md#)|
|Elastic IP Address|√|√|×|×|Resource| -   AliyunEIPFullAccess
-   AliyunEIPReadOnlyAccess

 |-|
|Express Connect|√|√|×|×|Resource| -   AliyunExpressConnectFullAccess
-   AliyunExpressConnectReadOnlyAccess

 |-|
|NAT Gateway|√|√|×|×|Resource| -   AliyunNATGatewayReadOnlyAccess
-   AliyunNATGatewayFullAccess

 |-|

## Analysis {#section_05 .section}

|Service|Supports console access?|Supports API access?|Authorization granularity \(minimum\)|System policy|Reference|
|:------|:-----------------------|:-------------------|:------------------------------------|:------------|:--------|
|E-MapReduce|√|√|Service|AliyunEMRFullAccess|-|
|HybridDB for PostgreSQL|√|√|Resource| -   AliyunGPDBFullAccess
-   AliyunGPDBReadOnlyAccess

 |[Authentication rules for APIs](../../../../../reseller.en-US/API Reference/Use RAM for resource authorization/Authentication rules for APIs.md#)|

## Cloud Communication {#section_06 .section}

|Service|Supports console access?|Supports API access?|Authorization granularity \(minimum\)|System policy|Reference|
|:------|:-----------------------|:-------------------|:------------------------------------|:------------|:--------|
|Message Service|√|√|Resource| -   AliyunMNSFullAccess
-   AliyunMNSReadOnlyAccess

 |-|
|Direct Mail|√|√|Service| -   AliyunDirectMailFullAccess
-   AliyunDirectMailReadOnlyAccess

 |-|
|Short Message Service|√|√|Service|-|-|

## Monitoring and Management {#section_07 .section}

|Service|Supports console access?|Supports API access?|Authorization granularity \(minimum\)|System policy|Reference|
|:------|:-----------------------|:-------------------|:------------------------------------|:------------|:--------|
|CloudMonitor|√|√|Service| -   AliyunCloudMonitorFullAccess
-   AliyunCloudMonitorReadOnlyAccess

 | |
|ActionTrail|√|√|Resource|-|[RAM account authentication](../../../../../reseller.en-US/.md#)|
|Key Management Service|√|√|Resource| -   AliyunKMSFullAccess
-   AliyunKMSReadOnlyAccess
-   AliyunKMSCryptoAccess

 |[Use RAM for KMS resource authorization](../../../../../reseller.en-US/User Guide/Use RAM for KMS resource authorization.md#)|

## Application Services {#section_08 .section}

|Service|Supports RAM console access?|Supports RAM API access?|Supports STS console access?|Supports STS API access?|Authorization granularity \(minimum\)|System policy|Reference|
|:------|:---------------------------|:-----------------------|:---------------------------|:-----------------------|:------------------------------------|:------------|:--------|
|Log Service|√|√|×|×|Resource| -   AliyunLogFullAccess
-   AliyunLogReadOnlyAccess

 |[Authentication rules](../../../../../reseller.en-US/API Reference/RAM__STS/Authentication rules.md#)|
|API Gateway|√|√|×|×|Service| -   AliyunApiGatewayFullAccess
-   AliyunApiGatewayReadOnlyAccess

 |-|
|Direct Mail|√|√|×|×|Operation| -   AliyunDirectMailFullAccess
-   AliyunDirectMailReadOnlyAccess

 |-|
|Message Service|√|√|×|×|Resource| -   AliyunMNSFullAccess
-   AliyunMNSReadOnlyAccess

 |-|

## Middleware {#section_09 .section}

|Service|Supports console access?|Supports API access?|Authorization granularity \(minimum\)|System policy|Reference|
|:------|:-----------------------|:-------------------|:------------------------------------|:------------|:--------|
|Enterprise Distributed Application Service|√|×|Service|AliyunEDASFullAccess|[Sub-accounts](https://www.alibabacloud.com/help/en/doc-detail/44023.htm)|
|Message Queue|√|√|Resource| -   AliyunMQFullAccess
-   AliyunMQPubOnlyAccess
-   AliyunMQSubOnlyAccess

 |-|
|Application Real Time Monitoring Service|√|×|Service|-|-|
|Application Configuration Management|√|√|Resource|-|-|

## Alibaba Cloud Mobile Services {#section_10 .section}

|Service|Supports console access?|Supports API access?|Authorization granularity \(minimum\)|System policy|Reference|
|:------|:-----------------------|:-------------------|:------------------------------------|:------------|:--------|

## Media Services {#section_11 .section}

|Service|Supports console access?|Supports API access?|Authorization granularity \(minimum\)|System policy|Reference|
|:------|:-----------------------|:-------------------|:------------------------------------|:------------|:--------|
|Media Processing Service|√|√|Service| -   AliyunMTSFullAccess
-   AliyunMTSPlayerAuth

 |[Sub-account console operating instructions](../../../../../reseller.en-US/User Guide/Sub-account console operating instructions.md#)|
|ApsaraVideo VoD|√|√|Service|AliyunVODFullAccess|-|
|ApsaraVideo Live|√|√|Service|AliyunLiveFullAccess|[API authentication rules](../../../../../reseller.en-US/API Reference/API authentication rules.md#)|

## DTplus {#section_12 .section}

|Service|Supports console access?|Supports API access?|Authorization granularity \(minimum\)|System policy|Reference|
|:------|:-----------------------|:-------------------|:------------------------------------|:------------|:--------|
|Quick BI|√|√|Service|-|-|
|Machine Learning|√|√|Service|-|-|
|DataV|√|√|Service|-|-|
|Alibaba Cloud Elasticsearch|√|√|Resource|-|-|

## Security {#section_13 .section}

|Service|Supports console access?|Supports API access?|Authorization granularity \(minimum\)|System policy|Reference|
|:------|:-----------------------|:-------------------|:------------------------------------|:------------|:--------|
|Server Guard|√|○|Service|AliyunYundunAegisFullAccess|-|
|Anti-DDoS Basic|√|○|Service| -   AliyunYundunDDosFullAccess
-   AliyunYundunDDosReadOnlyAccess

 |-|
|Anti-DDoS Pro|√|○|Service| -   AliyunYundunHighFullAccess
-   AliyunYundunHighReadOnlyAccess

 |-|
|Web Application Firewall|√|○|Service| -   AliyunYundunWAFFullAccess
-   AliyunYundunWAFReadOnlyAccess

 |-|
|Content Moderation|√|○|Service|-|-|
|Mobile Security|√|○|Service|AliyunYundunJaqFullAccess|-|
|SSL Certificates|√|○|Service| -   AliyunYundunCertFullAccess
-   AliyunYundunCertReadOnlyAccess

 |-|

## Marketplace {#section_14 .section}

|Service|Supports console access?|Supports API access?|Authorization granularity \(minimum\)|System policy|Reference|
|:------|:-----------------------|:-------------------|:------------------------------------|:------------|:--------|
|Marketplace|√|○|Service|AliyunMarketplaceFullAccess|-|

## Domains & Websites {#section_15 .section}

|Service|Supports console access?|Supports API access?|Authorization granularity \(minimum\)|System policy|Reference|
|:------|:-----------------------|:-------------------|:------------------------------------|:------------|:--------|
|Alibaba Cloud DNS|√|○|Service| -   AliyunDNSFullAccess
-   AliyunDNSReadOnlyAccess

 |-|
|Domains|√|√|Resource|AliyunDomainFullAccess|[Domain API Authentication Rules](../../../../../reseller.en-US/Domain name management/Use RAM in Domain Name/Domain API Authentication Rules.md#)|

