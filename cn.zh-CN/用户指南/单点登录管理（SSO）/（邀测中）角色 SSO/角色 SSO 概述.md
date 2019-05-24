# 角色 SSO 概述 {#concept_zrv_2ny_zgb .concept}

本文为您介绍角色 SSO 的背景、基本流程以及配置步骤。

## 背景信息 {#section_ar3_r4d_bhb .section}

阿里云与企业进行角色 SSO 时，阿里云是服务提供商（SP），而企业自有的身份管理系统则是身份提供商（IdP）。通过角色 SSO，企业可以在本地 IdP 中管理员工信息，无需进行阿里云和企业 IdP 间的用户同步，企业员工将使用指定的 RAM 角色来登录阿里云。

## 角色 SSO 流程 {#section_j2c_twr_bhb .section}

通过角色 SSO，企业员工既可以通过控制台也可以使用程序访问阿里云。

## 通过控制台访问阿里云 {#section_hv1_3yr_bhb .section}

![](images/40723_zh-CN.png "基本流程")

当管理员在完成角色 SSO 的相关配置后，企业员工 Alice 可以通过如图所示的方法登录到阿里云：

1.  Alice 使用浏览器在 IdP 的登录页面中选择阿里云作为目标服务。

    例如：如果企业 IdP 使用 AD FS \(Microsoft Active Directory Federation Service\)，则登录 URL 为：`https://ADFSServiceName/adfs/ls/IdpInitiatedSignOn.aspx`。

    **说明：** 有些 IdP 会要求用户先登录，再选择代表阿里云的 SSO 应用。

2.  IdP 生成一个 SAML 响应并返回给浏览器。
3.  浏览器重定向到 SSO 服务页面，并转发 SAML 响应给 SSO 服务。
4.  SSO 服务使用 SAML 响应向阿里云 STS 服务请求临时安全凭证，并生成一个可以使用临时安全凭证登录阿里云控制台的 URL。

    **说明：** 如果 SAML 响应中包含映射到多个 RAM 角色的属性，系统将会首先提示用户选择一个用于访问阿里云的角色。

5.  SSO 服务将 URL 返回给浏览器。
6.  浏览器重定向到该 URL，以指定角色身份登录到阿里云控制台。

## 使用程序访问阿里云 {#section_rxk_lyr_bhb .section}

![](images/40724_zh-CN.png "基本流程")

企业员工 Alice 可以通过编写程序来访问阿里云，基本流程如图所示：

1.  Alice 使用程序向企业 IdP 发起登录请求。
2.  IdP 生成一个 SAML 响应，其中包含关于登录用户的 SAML 断言，并将此响应返回给程序。
3.  程序调用阿里云 STS 服务提供的 API AssumeRoleWithSAM，并传递以下信息：阿里云中身份提供商的 ARN、要扮演的角色的 ARN 以及来自企业 IdP 的 SAML 断言。
4.  STS 服务将校验 SAML 断言并返回临时安全凭证给程序。
5.  程序可以开始使用临时安全凭证来调用阿里云 API。

## 角色 SSO 的配置步骤 {#section_hvw_zbp_chb .section}

为了建立阿里云与企业 IdP 之间的互信关系，需要进行阿里云作为 SP 的 SAML 配置和企业 IdP 的 SAML 配置，配置完成后才能进行角色 SSO。

1.  为了建立阿里云对企业 IdP 的信任，需要将企业 IdP 配置到阿里云。

    详情请参考：[阿里云角色 SSO 的 SAML 配置](intl.zh-CN/用户指南/单点登录管理（SSO）/（邀测中）角色 SSO/阿里云角色 SSO 的 SAML 配置.md#)。

2.  企业需要使用程序或登录 RAM 控制台创建用于 SSO 的角色，并授予相关权限。

    详情请参考：[管理 RAM 角色](intl.zh-CN/用户指南/身份管理/RAM 角色身份/管理 RAM 角色.md#)。

3.  为了建立企业 IdP 对阿里云的信任，需要在企业 IdP 中配置阿里云为可信 SAML SP 并进行 SAML 断言属性的配置。

    详情请参考：[进行角色 SSO 时企业 IdP 的 SAML 配置](intl.zh-CN/用户指南/单点登录管理（SSO）/（邀测中）角色 SSO/进行角色 SSO 时企业 IdP 的 SAML 配置.md#)。


## 角色 SSO 配置示例 {#section_ahn_wss_bhb .section}

由于不同 IdP 的系统差异，关于 SAML SP 配置和断言属性配置的操作流程都有些差异。我们会提供一个以 AD FS 与阿里云进行角色 SSO 的示例，用于帮助理解企业 IdP 与阿里云的端到端配置流程。

详情请参考：[使用 AD FS 进行角色 SSO](intl.zh-CN/用户指南/单点登录管理（SSO）/（邀测中）角色 SSO/使用 AD FS 进行角色 SSO 示例.md#)。

