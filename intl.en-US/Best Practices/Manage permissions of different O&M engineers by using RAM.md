# Manage permissions of different O&M engineers by using RAM {#concept_fz1_np1_kgb .concept}

You can grant and manage the permissions of different O&M engineers by using RAM to meet various O&M requirements while also facilitating better management and control.

## Scenario {#section_mfv_k2b_kgb .section}

Your company purchases several Alibaba Cloud products and deploys a number of application systems on the cloud, which brings greater O&M requirements.

-   Different O&M owners are responsible for different Alibaba Cloud products.
-   Different O&M engineers require different permissions to access, operate, and manage cloud resources.

## Solution {#section_jyj_z2b_kgb .section}

You can categorize the O&M requirements by product to make them easier to manage. More specifically, you can assign different [O&M owners](#) to different categories of requirements and attach your specified [policies](#) to these owners, as shown in the following example.

![O&M owner](images/37801_en-US.png "O&M owner")

|O&M owner|Policy|Description|
|:--------|:-----|:----------|
|O&M owner|AdministratorAccess|This policy grants the O&M owner the permission to manage all Alibaba Cloud resources.|
|VM O&M engineer|AliyunECSFullAccess|This policy grants the VM O&M engineer the permission to manage Elastic Compute Service \(ECS\).|
|AliyunESSFullAccess|This policy grants the VM O&M engineer the permission to manage Elastic Scaling Service \(ESS\).|
|AliyunSLBFullAccess|This policy grants the VM O&M engineer the permission to manage Server Load Balancer \(SLB\).|
|AliyunNASFullAccess|This policy grants the VM O&M engineer the permission to manage Network Attached Storage \(NAS\).|
|AliyunOSSFullAccess|This policy grants the VM O&M engineer the permission to manage Object Storage Service \(OSS\).|
|AliyunOTSFullAccess|This policy grants the VM O&M engineer the permission to manage Table Store \(OTS\).|
|Network O&M engineer|AliyunCDNFullAccess|This policy grants the network O&M engineer the permission to manage Content Delivery Network \(CDN\).|
|AliyunCENFullAccess|This policy grants the network O&M engineer the permission to manage Cloud Enterprise Network \(CEN\).|
|AliyunCommonBandwidthPackageFullAccess|This policy grants the network O&M engineer the permission to manage Internet Shared Bandwidth.|
|AliyunEIPFullAccess|This policy grants the network O&M engineer the permission to manage Elastic IP \(EIP\).|
|AliyunExpressConnectFullAccess|This policy grants the network O&M engineer the permission to manage ExpressConnect.|
|AliyunNATGatewayFullAccess|This policy grants the network O&M engineer the permission to manage NAT Gateway.|
|AliyunSCDNFullAccess|This policy grants the network O&M engineer the permission to manage Secure Content Delivery Network \(SCDN\).|
|AliyunSmartAccessGatewayFullAccess|This policy grants the network O&M engineer the permission to manage Smart Access Gateway.|
|AliyunVPCFullAccess|This policy grants the network O&M engineer the permission to manage Virtual Private Cloud \(VPC\).|
|AliyunVPNGatewayFullAccess|This policy grants the network O&M engineer the permission to manage VPN Gateway.|
|Database O&M engineer|AliyunRDSFullAccess|This policy grants the database O&M engineer the permission to manage Relational Database Service \(RDS\).|
|AliyunDTSFullAccess|This policy grants the database O&M engineer the permission to manage Data Transmission Service \(DTS\).|
|Security O&M engineer|AliyunYundunFullAccess|This policy grants the security O&M engineer the permission to manage Alibaba Cloud Security.|
|Monitoring O&M engineer|AliyunActionTrailFullAccess|This policy grants the monitoring O&M engineer the permission to manage ActionTrail.|
|AliyunARMSFullAccess|This policy grants the monitoring O&M engineer the permission to manage Application Real-Time Monitoring Service ARMS\).|
|AliyunCloudMonitorFullAccess|This policy grants the monitoring O&M engineer the permission to manage CloudMonitor.|
|\(Optional\) ReadOnlyAccess|\(Optional\) This policy grants the monitoring O&M engineer the read-only permission to all Alibaba Cloud resources.|
|AliyunSupportFullAccess|This policy grants the monitoring O&M engineer the permission to manage Alibaba Cloud support systems.|

## Example {#section_uc1_cfl_ngb .section}

This example describes how to set the RAM user `alice@secloud.onaliyun.com` as the database O&M owner, so that the user can manage RDS and DTS.

1.  Log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram).
2.  [Create a RAM user](../../../../../reseller.en-US/Quick Start/Create a RAM user.md#) and name the user `alice@secloud.onaliyun.com`.
3.  Find the created RAM user and click **Add Permissions**.
4.  In the **Policy Name** column, select `AliyunRDSFullAccess` and `AliyunDTSFullAccess`, and click **Ok**.

**Note:** To grant other O&M permissions to the RAM user, see [Policies](#).

