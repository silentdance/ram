# 什么是 RAM {#concept_oyr_zzv_tdb .concept}

RAM \(Resource Access Management\) 是阿里云为客户提供的用户身份管理与资源访问控制服务。

## RAM 的优势 {#section_udo_h7b_dkt .section}

使用 RAM，您可以创建、管理 RAM 用户（比如员工、系统或应用程序），并可以控制这些 RAM 用户对资源的操作权限。当您的企业存在多用户协同操作资源时，使用 RAM 可以让您避免与其他用户共享云账号密钥，按需为用户分配最小权限，从而降低企业信息安全风险。

## RAM 用户身份 {#section_psv_r9l_0mm .section}

RAM 用户身份是指任意通过控制台或 API 操作阿里云资源的人、系统或应用程序。为了支持多种应用场景的身份管理，RAM 支持两种不同的用户身份类型：RAM 用户和 RAM 角色，详情请参考：[相关术语](intl.zh-CN/产品简介/相关术语.md#)。

## RAM 功能 {#section_pc7_qy7_6cj .section}

RAM 允许在一个云账号下创建并管理多个用户身份，并允许给单个身份或一组身份分配不同的权限，从而实现不同用户拥有不同的云资源访问权限。

-   集中控制 RAM 用户及其密钥：管理每个 RAM 用户及其访问密钥，可以为用户绑定多因素认证设备。
-   集中控制 RAM 用户的访问权限：控制每个 RAM 用户访问资源的操作权限。
-   集中控制 RAM 用户的资源访问方式：确保 RAM 用户必须使用安全信道、在指定时间、以及在指定的网络环境下请求访问特定的阿里云资源。
-   集中控制云资源：对 RAM 用户创建的实例或数据进行集中控制。当用户离开组织时，实例或数据不会丢失。
-   SSO 管理：支持与企业 IdP 进行用户 SSO 或角色 SSO。

## 权限策略 {#section_4gh_0xr_9pp .section}

RAM 允许在云账号下创建并管理多个权限策略，每个权限策略本质上是一组权限的集合。管理员可以将一个或多个权限策略分配给 RAM 用户、RAM 用户组或 RAM 角色。

RAM 权限策略语言可以表达精细的授权语义，可以指定对某个操作和资源授权，也可以支持多种限制条件（源 IP、访问时间、多因素认证等）。详情请参考：[权限策略管理](../../../../intl.zh-CN/用户指南/权限管理/权限策略管理.md#)。

## RAM 访问点 {#section_nkc_r5s_gpw .section}

用于 API 访问的 RAM 接入点为：`https://ram.aliyuncs.com`。

## RAM 如何计费 {#section_hgx_l57_3s6 .section}

RAM 不收取服务费用，开通后即可使用该服务。

请访问 [RAM 开通页面](https://buy-intl.aliyun.com/ram) 开通 RAM。

## 支持 RAM 的云服务 {#section_o3g_i0s_tg3 .section}

阿里云服务与 RAM 集成的信息，请参考 [支持 RAM 的云服务](intl.zh-CN/产品简介/支持 RAM 的云服务.md)。

## 学习路径图 {#section_mkm_gkx_42b .section}

您可以通过 [RAM 学习路径图](https://www.alibabacloud.com/getting-started/learningpath/ram)快速了解 RAM，学习相关的基础操作，并利用丰富的 API、SDK 包和便捷工具进行二次开发。

