# 用户 SSO 概述 {#concept_kwz_hrk_bhb .concept}

本文为您介绍用户 SSO 的背景、基本流程以及配置步骤。

## 背景信息 {#section_khp_n4p_pgb .section}

阿里云与企业进行用户 SSO 时，阿里云是服务提供商（SP），而企业自有的身份管理系统则是身份提供商（IdP）。通过用户 SSO，企业员工在登录后，将以 RAM 用户身份访问阿里云。

## 用户 SSO 基本流程 {#section_02 .section}

![](images/40784_zh-CN.png "基本流程")

当管理员在完成用户 SSO 的相关配置后，企业员工 Alice 可以通过如图所示的方法登录到阿里云：

1.  Alice 使用浏览器登录阿里云，阿里云将 SAML 认证请求返回给浏览器。
2.  浏览器向 IdP 转发 SAML 认证请求。
3.  IdP 提示 Alice 登录，并在 Alice 登录成功后生成 SAML 响应返回给浏览器。
4.  浏览器将 SAML 响应转发给 SSO 服务。
5.  SSO 服务通过 SAML 互信配置，验证 SAML 响应的数字签名来判断 SAML 断言的真伪，并通过 SAML 断言的`NameID`元素值，匹配到对应阿里云账号中的 RAM 用户身份。
6.  SSO 服务向浏览器返回控制台的 URL。
7.  浏览器重定向到阿里云控制台。

    **说明：** 在第 1 步中，企业员工从阿里云发起登录并不是必须的。企业员工也可以在企业自有 IdP 的登录页直接点击登录到阿里云的链接，向企业 IdP 发出登录到阿里云的 SAML 认证请求。


## 用户 SSO 的配置步骤 {#section_03 .section}

为了建立阿里云与企业 IdP 之间的互信关系，需要进行阿里云作为 SP 的 SAML 配置和企业 IdP 的 SAML 配置，配置完成后才能进行用户 SSO。

1.  为了建立阿里云对企业 IdP 的信任，需要将企业 IdP 配置到阿里云。

    详情请参考：[云账号的 SAML配置](intl.zh-CN/用户指南/单点登录管理（SSO）/用户 SSO/阿里云用户 SSO 的 SAML 配置.md#)。

2.  为了建立企业 IdP 对阿里云的信任，需要在企业 IdP 中配置阿里云为可信 SAML SP 并进行 SAML 断言属性的配置。

    详情请参考：[外部 IdP 的 SAML 配置](intl.zh-CN/用户指南/单点登录管理（SSO）/用户 SSO/进行用户 SSO 时企业 IdP 的 SAML 配置.md#)。

3.  企业 IdP 和阿里云均配置完成后，企业需要使用 SDK、CLI 或登录到 RAM 控制台创建与企业 IdP 匹配的 RAM 用户。

    详情请参考：[创建 RAM 用户](intl.zh-CN/用户指南/用户/创建 RAM 用户.md#)。


## 用户 SSO 示例 {#section_zfr_vss_bhb .section}

由于不同 IdP 的系统差异，关于 SAML SP 配置和断言属性配置的操作流程都有些差异。我们会提供一个以 AD FS（Microsoft Active Directory Federation Service）与阿里云进行用户 SSO 的示例，用于帮助理解企业 IdP 与阿里云的端到端配置流程。

详情请参考：[使用 AD FS 进行用户 SSO 的示例](intl.zh-CN/用户指南/单点登录管理（SSO）/用户 SSO/使用 AD FS 进行用户 SSO 的示例.md#)。

