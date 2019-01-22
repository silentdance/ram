# RAM 对多运维人员的权限管控 {#concept_fz1_np1_kgb .concept}

当您的企业涉及多种运维需求时，通过 RAM 进行运维划分，对不同的运维人员授予不同的权限，方便管理和控制。

## 背景信息 {#section_mfv_k2b_kgb .section}

某公司购买了大量的阿里云产品，并将应用系统部署在云上，因此涉及多种运维需求：

-   不同的运维负责人需要运维不同的阿里云产品。
-   不同的运维人员需要不同的访问、操作、管理云资源的权限。

## 运维划分解决方案 {#section_jyj_z2b_kgb .section}

根据云产品进行运维划分，设置如下[运维负责人](#)并授予特定的[权限策略](#)。

![运维负责人](images/37801_zh-CN.png "运维负责人")

|运维负责人|权限策略名称|权限策略说明|
|:----|:-----|:-----|
|云运维负责人|AdministratorAccess|管理所有阿里云资源的权限|
|虚拟机运维负责人|AliyunECSFullAccess|管理云服务器服务（ECS）的权限|
|AliyunESSFullAccess|管理弹性伸缩服务（ESS）的权限|
|AliyunSLBFullAccess|管理负载均衡服务（SLB）的权限|
|AliyunNASFullAccess|管理文件存储服务（NAS）的权限|
|AliyunOSSFullAccess|管理对象存储服务（OSS）权限|
|AliyunOTSFullAccess|管理表格存储服务（OTS）的权限|
|网络运维负责人|AliyunCDNFullAccess|管理CDN的权限|
|AliyunCENFullAccess|管理云企业网（CEN）的权限|
|AliyunCommonBandwidthPackageFullAccess|管理共享带宽的权限|
|AliyunEIPFullAccess|管理弹性公网IP（EIP）的权限|
|AliyunExpressConnectFullAccess|管理高速通道（ExpressConnect）的权限|
|AliyunNATGatewayFullAccess|管理NAT网关（NATGateway）的权限|
|AliyunSCDNFullAccess|管理安全加速（SCDN）的权限|
|AliyunSmartAccessGatewayFullAccess|管理智能接入网关（SmartAccessGateway）的权限|
|AliyunVPCFullAccess|管理专有网络（VPC）的权限|
|AliyunVPNGatewayFullAccess|管理VPN网关（VPNGateway）的权限|
|数据库运维负责人|AliyunRDSFullAccess|管理云数据库服务（RDS）的权限|
|AliyunDTSFullAccess|管理数据传输服务（DTS）的权限|
|安全运维负责人|AliyunYundunFullAccess|管理云盾所有产品（Yundun）的权限|
|监控运维负责人|AliyunActionTrailFullAccess|管理操作审计（ActionTrail）的权限|
|AliyunARMSFullAccess|管理业务实时监控服务（ARMS）的权限|
|AliyunCloudMonitorFullAccess|管理云监控（CloudMonitor）的权限|
|ReadOnlyAccess（可选）|只读访问所有阿里云资源的权限（可选）|
|AliyunSupportFullAccess|管理工单系统的权限|

## 示例：将用户配置为数据库运维负责人 {#section_uc1_cfl_ngb .section}

此示例将 RAM 用户`alice@secloud.onaliyun.com`配置为数据库运维负责人，从而允许该用户管理云数据库服务（RDS）和数据传输服务（DTS）。

1.  登录 [RAM 控制台](https://ram.console.aliyun.com/)。
2.  [创建 RAM 用户](../../../../../intl.zh-CN/快速入门/创建 RAM 用户.md#)为`alice@secloud.onaliyun.com`。
3.  找到创建好的 RAM 用户，单击**添加权限** 。
4.  从左侧**权限策略名称**列中勾选`AliyunRDSFullAccess`和`AliyunDTSFullAccess`，单击**确定**。

**说明：** 如需将用户配置为其他运维负责人，请参考[权限策略](#)表格，为相关负责人授予相应的权限。

