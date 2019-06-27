# 什么是 RAM {#concept_oyr_zzv_tdb .concept}

RAM \(Resource Access Management\) 是阿里云为客户提供的用户身份管理与资源访问控制服务。

## RAM 的优势 {#section_udo_h7b_dkt .section}

使用 RAM，您可以创建、管理 RAM 用户（比如员工、系统或应用程序），并可以控制这些 RAM 用户对资源的操作权限。当您的企业存在多用户协同操作资源时，使用 RAM 可以让您避免与其他用户共享云账号密钥，按需为用户分配最小权限，从而降低企业信息安全风险。

## RAM 功能特性 {#section_pc7_qy7_6cj .section}

RAM 允许在一个云账号下创建并管理多个身份，并允许给单个身份或一组身份分配不同的权限，从而实现不同用户拥有不同的云资源访问权限。

-   集中控制 RAM 用户及其密钥：管理每个 RAM 用户及其访问密钥，可以为用户绑定多因素认证设备。
-   集中控制 RAM 用户的访问权限：控制每个 RAM 用户访问资源的操作权限。
-   集中控制 RAM 用户的资源访问方式：确保 RAM 用户在指定的时间和网络环境下，通过安全信道访问特定阿里云资源。
-   集中控制云资源：对 RAM 用户创建的实例或数据进行集中控制。当用户离开组织时，实例或数据不会丢失。
-   SSO 管理：支持与企业 IdP 进行用户 SSO 或角色 SSO。

## RAM 应用场景 {#section_e9w_v3i_71m .section}

|应用场景|描述|
|----|--|
| [用户管理与分权](../intl.zh-CN/最佳实践/用户管理与分权.md#) | 企业 A 的某个项目（Project-X）上云，购买了多种阿里云资源，例如：ECS 实例、RDS 实例、SLB 实例、OSS 存储空间等。项目里有多个员工需要操作这些云资源，由于每个员工的工作职责不同，需要的权限也不一样。

 |
| [移动设备应用使用临时安全令牌访问阿里云](../intl.zh-CN/最佳实践/移动设备应用使用临时安全令牌访问阿里云.md#) | 企业 A 开发了一款移动应用（App），并购买了对象存储（OSS）服务。App 需要直连 OSS 上传或下载数据，但是 App 运行在用户自己的移动设备上，这些设备不受企业 A 的控制。

 |
| [跨云账号的资源授权](../intl.zh-CN/最佳实践/跨云账号的资源授权.md#) | 企业 A 购买了多种阿里云资源来开展业务，例如：ECS 实例、RDS 实例、SLB 实例、OSS 存储空间等。企业 A 希望将部分业务授权给企业 B。

 |
| [云上应用的动态身份与授权管理](../intl.zh-CN/最佳实践/云上应用的动态身份与授权管理.md#) | 企业购买了 ECS 实例，并且打算在 ECS 中部署企业的应用程序。这些应用程序需要使用访问密钥（AccessKey）访问其它云服务 API。

 |

## RAM 接入地址 {#section_nkc_r5s_gpw .section}

用于 API 访问的 RAM 接入地址为：`https://ram.aliyuncs.com`。

## RAM 计费 {#section_hgx_l57_3s6 .section}

RAM 不收取服务费用，开通后即可使用该服务。

请访问 [RAM 开通页面](https://buy-intl.aliyun.com/ram)开通 RAM。

## 支持 RAM 的云服务 {#section_o3g_i0s_tg3 .section}

支持 RAM 的云服务列表，请参考：[支持 RAM 的云服务](intl.zh-CN/产品简介/支持 RAM 的云服务.md)。

## 学习路径图 {#section_mkm_gkx_42b .section}

您可以通过 [RAM 学习路径图](https://www.alibabacloud.com/getting-started/learningpath/ram)快速了解 RAM，学习相关的基础操作，并利用丰富的 API、SDK 包和便捷工具进行二次开发。

