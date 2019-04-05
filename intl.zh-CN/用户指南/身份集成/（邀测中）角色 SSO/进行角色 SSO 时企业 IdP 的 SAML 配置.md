# 进行角色 SSO 时企业 IdP 的 SAML 配置 {#concept_o3t_54r_bhb .concept}

本文主要介绍在使用角色 SSO 时，如何进行企业 IdP 的 SAML 配置，包括在企业 IdP 中配置阿里云为可信 SAML 服务提供商（SP） 以及在企业 IdP 中配置 SAML 断言属性。

## 在企业 IdP 中配置阿里云为可信 SAML SP {#section_ehv_hrj_sfb .section}

企业 IdP 的 SAML SP 配置需要用到阿里云的 SAML 服务提供商元数据 URL：`https://signin.alibabacloud.com/saml-role/sp-metadata.xml`。

**说明：** 您也可以登录 **RAM 控制台**，单击 **SSO 管理**，在**角色 SSO** 下查看元数据 URL。

您需要在企业 IdP 中创建一个 SAML SP，并根据实际情况选择下面任意一种方式配置阿里云为依赖方。

-   直接使用上述阿里云的元数据 URL 进行配置。
-   如果您的 IdP 不支持 URL 配置，您可以根据上述 URL 下载元数据文件并上传至您的 IdP。
-   如果您的 IdP 不支持元数据文件上传，则需要手动配置以下参数：
    -   Entity ID：`urn:alibaba:cloudcomputing:international`
    -   ACS URL：`https://signin.alibabacloud.com/saml-role/sso`

## 在企业 IdP 中配置 SAML 断言属性 {#section_wyp_hrj_sfb .section}

阿里云要求企业 IdP 生成的 SAML 断言里包含一些必要的信息以确定企业用户的登录身份，因此企业 IdP 必须进行属性配置来匹配 RAM 角色，从而实现企业用户与阿里云的 SSO。

具体需要配置的 SAML 断言属性请参考：[支持角色 SSO 的 SAML 断言](ZH-CN_TP_136748_V1.dita)。

