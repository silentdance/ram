# 进行用户 SSO 时企业 IdP 的 SAML 配置 {#task_gsy_gw3_sfb .task}

本文主要介绍企业在使用用户 SSO 时，如何在企业身份提供商（IdP）中配置阿里云为可信 SAML 服务提供商（SP）。

1.  从阿里云获取 SAML 服务提供商元数据 URL。 
    1.  登录 [RAM 控制台](https://ram.console.aliyun.com/)。
    2.  在左侧导航栏，单击 **SSO 管理**。
    3.  在**用户 SSO** 页签下的 **SSO 登录设置**区域，可以查看当前云账号的 **SAML 服务提供商元数据 URL**。
2.  在企业 IdP 中创建一个 SAML SP，并配置阿里云的 SAML 服务提供商元数据 URL。 

    **说明：** 如果您的 IdP 不支持 URL 配置，那么您可以从 **SAML 服务提供商元数据 URL** 下载 XML 文件，并在创建 SAML SP 的相应流程中上传此 XML文件。


在企业 IdP 中配置阿里云为可信 SAML SP 后，需要在企业 IdP 中配置 SAML 断言属性。

阿里云需要通过 UPN （User Principal Name）来定位一个 RAM 用户，所以要求企业 IdP 生成的 SAML 断言包含用户的 UPN。阿里云通过解析 SAML 断言中的`NameID`元素，来匹配 RAM 用户的 UPN 从而实现用户 SSO。

因此，在配置 IdP 颁发的 SAML 断言时，需要将对应于 RAM 用户 UPN 的字段映射为 SAML 断言中的 `NameID` 元素。`NameID` 元素必须是以下几种：

-   使用**域别名**作为 `NameID` 元素的后缀，即 `<username>@<domain_alias>`。其中 **<username\>** 为 RAM 用户的用户名，`<domain_alias>` 为域别名。关于如何设置域别名，请参考：[创建域别名](intl.zh-CN/用户指南/安全设置/高级设置/创建域别名.md#)。
-   使用**辅助域名**作为 `NameID` 元素的后缀，即 `<username>@<auxiliary_domain>`。其中 **<username\>** 为 RAM 用户的用户名，`<auxiliary_alias>` 为辅助域名。关于如何设置辅助域名，请参考：[设置辅助域名](intl.zh-CN/用户指南/单点登录管理（SSO）/用户 SSO/阿里云用户 SSO 的 SAML 配置.md#)。

    **说明：** 如果您同时设置了域别名和辅助域名，辅助域名将不会生效。此时，`NameID` 元素只能使用域别名作为后缀。

-   使用**默认域名**作为 `NameID` 元素的后缀，即 `<username>@<default_domain>`。其中 **<username\>** 为 RAM 用户的用户名，`<default_domain>` 为默认域名。关于如何设置默认域名，请参考：[管理默认域名](intl.zh-CN/用户指南/安全设置/高级设置/管理默认域名.md#)。

    **说明：** 即使设置了域别名或辅助域名，仍可以使用默认域名作为 `NameID` 的后缀。


示例：RAM 用户名为：`Alice`，默认域名为：`example.onaliyun.com`。

-   如果设置了域别名为：`example.com`，SAML 断言中的 `NameID` 取值为：`Alice@example.onaliyun.com` 或 `Alice@example.com`。
-   如果没有设置域别名，设置了辅助域名为：`example2.com`，SAML 断言中的 `NameID` 取值为：`Alice@example.onaliyun.com` 或 `Alice@example2.com`。
-   如果设置了域别名为：`example.com`后，又设置了辅助域名为：`example2.com`，SAML 断言中的 `NameID` 取值为：`Alice@example.onaliyun.com` 或 `Alice@example.com`。

