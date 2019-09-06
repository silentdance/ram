# Use RAM to manage permissions of O&M engineers {#concept_fz1_np1_kgb .task}

This topic describes how to use RAM to grant and then manage permissions of O&M engineers.

An Alibaba Cloud account is created. If not, create one before proceeding.

Your company purchases several Alibaba Cloud products and deploys a number of application systems on the cloud, which brings greater O&M requirements.

-   Different O&M owners are responsible for different Alibaba Cloud products.
-   Different O&M engineers require different permissions to access, operate, and manage Alibaba Cloud resources.

## Solution {#section_jyj_z2b_kgb .section}

You can categorize the O&M requirements by product to make them easier to manage. More specifically, you can set an O&M owner and assign different O&M engineers to different categories of requirements and attach your specified policies to these engineers, as shown in the following figure.

![O&M owner](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/92369/156777844937801_en-US.png)

## Example {#section_uc1_cfl_ngb .section}

This example describes how to set the RAM user `alice@secloud.onaliyun.com` as the database O&M owner, so that the user can manage RDS and DTS.

1.  Log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram).
2.  [Create a RAM user](../../../../reseller.en-US/User Guide/RAM users/Create a RAM user.md#).
3.  In the **User Logon Name/Display Name** column, find the target RAM user.
4.  Click **Add Permissions**.
5.  In the **Policy Name** column, click `AliyunRDSFullAccess` and `AliyunDTSFullAccess`.
6.  Click **OK**.
7.  Click **Finished**.

**Note:** To grant other O&M permissions to the RAM user, see the policies described in the following table.

|O&M owner|Policy|Description|
|:--------|:-----|:----------|
|O&M owner|AdministratorAccess|Grants the O&M owner the permission to manage all Alibaba Cloud resources.|
|VM O&M engineer|AliyunECSFullAccess|Grants the VM O&M engineer the permission to manage Elastic Compute Service \(ECS\).|
|AliyunESSFullAccess|Grants the VM O&M engineer the permission to manage Elastic Scaling Service \(ESS\).|
|AliyunSLBFullAccess|Grants the VM O&M engineer the permission to manage Server Load Balancer \(SLB\).|
|AliyunNASFullAccess|Grants the VM O&M engineer the permission to manage Network Attached Storage \(NAS\).|
|AliyunOSSFullAccess|Grants the VM O&M engineer the permission to manage Object Storage Service \(OSS\).|
|AliyunOTSFullAccess|Grants the VM O&M engineer the permission to manage Table Store \(OTS\).|
|Network O&M engineer|AliyunCDNFullAccess|Grants the network O&M engineer the permission to manage Content Delivery Network \(CDN\).|
|AliyunCENFullAccess|Grants the network O&M engineer the permission to manage Cloud Enterprise Network \(CEN\).|
|AliyunCommonBandwidthPackageFullAccess|Grants the network O&M engineer the permission to manage Internet Shared Bandwidth.|
|AliyunEIPFullAccess|Grants the network O&M engineer the permission to manage Elastic IP \(EIP\).|
|AliyunExpressConnectFullAccess|Grants the network O&M engineer the permission to manage ExpressConnect.|
|AliyunNATGatewayFullAccess|Grants the network O&M engineer the permission to manage NAT Gateway.|
|AliyunSCDNFullAccess|Grants the network O&M engineer the permission to manage Secure Content Delivery Network \(SCDN\).|
|AliyunSmartAccessGatewayFullAccess|Grants the network O&M engineer the permission to manage Smart Access Gateway.|
|AliyunVPCFullAccess|Grants the network O&M engineer the permission to manage Virtual Private Cloud \(VPC\).|
|AliyunVPNGatewayFullAccess|Grants the network O&M engineer the permission to manage VPN Gateway.|
|Database O&M engineer|AliyunRDSFullAccess|Grants the database O&M engineer the permission to manage Relational Database Service \(RDS\).|
|AliyunDTSFullAccess|Grants the database O&M engineer the permission to manage Data Transmission Service \(DTS\).|
|Security O&M engineer|AliyunYundunFullAccess|Grants the security O&M engineer the permission to manage Alibaba Cloud Security.|
|Monitoring O&M engineer|AliyunActionTrailFullAccess|Grants the monitoring O&M engineer the permission to manage ActionTrail.|
|AliyunARMSFullAccess|Grants the monitoring O&M engineer the permission to manage Application Real-Time Monitoring Service ARMS\).|
|AliyunCloudMonitorFullAccess|Grants the monitoring O&M engineer the permission to manage CloudMonitor.|
|\(Optional\) ReadOnlyAccess|Optional. Grants the monitoring O&M engineer the read-only permission to all Alibaba Cloud resources.|
|AliyunSupportFullAccess|Grants the monitoring O&M engineer the permission to manage Alibaba Cloud support systems.|

