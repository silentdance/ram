# 进行用户SSO时企业IdP的SAML配置 {#task_gsy_gw3_sfb .task}

本文主要介绍企业在使用用户SSO时，如何在企业身份提供商（IdP）中配置阿里云为可信SAML服务提供商（SP）。

1.  从阿里云获取SAML服务提供商元数据URL。 
    1.  云账号登录[RAM控制台](https://ram.console.aliyun.com/)。
    2.  在左侧导航栏，单击**SSO管理**。
    3.  单击**用户SSO**。
    4.  在**SSO登录设置**区域，可以查看当前云账号的**SAML服务提供商元数据URL**。
2.  在企业IdP中创建一个SAML SP，并根据实际情况选择下面任意一种方式配置阿里云为信赖方： 
    -   直接使用上述阿里云的元数据URL进行配置。
    -   如果您的IdP不支持URL配置，您可以根据上述URL下载元数据文件并上传至您的IdP。
    -   如果您的IdP不支持元数据文件上传，则需要手动配置以下参数：
        -   `Entity ID`：下载的元数据XML中，`md:EntityDescriptor`元素的`entityID`属性值。
        -   `ACS URL`：下载的元数据XML中，`md:AssertionConsumerService`元素的`Location`属性值。
        -   `RelayState`（可选）：如果您的IdP支持设置`RelayState`参数，您可以将其配置成SSO登录成功后希望跳转到的页面URL。如果不进行配置，SSO登录成功后，将会跳转到阿里云控制台首页。

            **说明：** 您只能填写`*.console.aliyun.com`或`*.console.alibabacloud.com`域名下的URL作为`RelayState`的值。


在企业IdP中配置阿里云为可信SAML SP后，需要在企业IdP中配置SAML断言属性。

阿里云需要通过UPN （User Principal Name）来定位一个RAM用户，所以要求企业IdP生成的SAML断言包含用户的UPN。阿里云通过解析SAML断言中的`NameID`元素，来匹配RAM用户的UPN从而实现用户SSO。

因此，在配置IdP颁发的SAML断言时，需要将对应于RAM用户UPN的字段映射为SAML断言中的`NameID`元素。`NameID`元素必须是以下几种：

-   使用**域别名**作为`NameID`元素的后缀，即`<username>@<domain_alias>`。其中**<username\>**为RAM用户的用户名，`<domain_alias>`为域别名。关于如何设置域别名，请参见[创建域别名](intl.zh-CN/用户指南/安全设置/高级设置/创建域别名.md#)。
-   使用**辅助域名**作为`NameID`元素的后缀，即`<username>@<auxiliary_domain>`。其中**<username\>**为RAM用户的用户名，`<auxiliary_alias>` 为辅助域名。关于如何设置辅助域名，请参见[设置辅助域名](intl.zh-CN/用户指南/单点登录管理（SSO）/用户 SSO/阿里云用户 SSO 的 SAML 配置.md#)。

    **说明：** 如果您同时设置了域别名和辅助域名，辅助域名将不会生效。此时，`NameID`元素只能使用域别名作为后缀。

-   使用**默认域名**作为`NameID`元素的后缀，即`<username>@<default_domain>`。其中**<username\>**为RAM用户的用户名，`<default_domain>`为默认域名。关于如何设置默认域名，请参见[管理默认域名](intl.zh-CN/用户指南/安全设置/高级设置/管理默认域名.md#)。

    **说明：** 即使设置了域别名或辅助域名，仍可以使用默认域名作为`NameID`的后缀。


示例：RAM用户名为：`Alice`，默认域名为：`example.onaliyun.com`。

-   如果设置了域别名为：`example.com`，SAML断言中的`NameID`取值为：`Alice@example.onaliyun.com`或`Alice@example.com`。
-   如果没有设置域别名，设置了辅助域名为：`example2.com`，SAML断言中的`NameID`取值为：`Alice@example.onaliyun.com`或`Alice@example2.com`。
-   如果设置了域别名为：`example.com`后，又设置了辅助域名为：`example2.com`，SAML断言中的`NameID`取值为：`Alice@example.onaliyun.com`或`Alice@example.com`。

