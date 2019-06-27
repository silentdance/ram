# 进行用户 SSO 时企业 IdP 的 SAML 配置 {#concept_gsy_gw3_sfb .concept}

本文主要介绍在使用用户 SSO 时，如何进行企业 IdP 的 SAML 配置，包括在企业 IdP 中配置阿里云为可信 SAML 服务提供商（SP）以及在企业 IdP 中配置 SAML 断言属性。

## 在企业 IdP 中配置阿里云为可信 SAML SP {#section_ehv_hrj_sfb .section}

1.  从阿里云获取 SAML 服务提供商元数据 URL。

    登录 [RAM 控制台](https://ram.console.aliyun.com/)，单击 **SSO 管理** \> **用户 SSO** ，在 **SSO 登录设置**下可以查看当前云账号的 **SAML 服务提供商元数据 URL**。

2.  在企业 IdP 中创建一个 SAML SP，并配置阿里云的 SAML 服务提供商元数据 URL。

    **说明：** 如果您的 IdP 不支持 URL 配置，那么您可以从 **SAML 服务提供商元数据 URL** 下载 XML 文件，并在创建 SAML SP 的相应流程中上传此 XML文件。


## 在企业 IdP 中配置 SAML 断言属性 {#section_wyp_hrj_sfb .section}

阿里云需要通过 User Principal Name （UPN）来定位一个 RAM 用户，所以要求企业 IdP 生成的 SAML 断言包含用户的 UPN。阿里云通过解析 SAML 断言中的`NameID`元素，来匹配 RAM 用户的 UPN 从而实现用户 SSO。

所以，在配置 IdP 颁发的 SAML 断言时，需要将对应于 RAM 用户 UPN 的字段映射为 SAML 断言中的`NameID`。

