# 进行角色 SSO 时企业 IdP 的 SAML 配置 {#task_o3t_54r_bhb .task}

本文主要介绍企业在使用角色 SSO 时，如何在企业身份提供商（IdP）中配置阿里云为可信 SAML 服务提供商（SP）。

1.  企业 IdP 的 SAML SP 配置需要使用阿里云的 SAML 服务提供商元数据 URL：`https://signin.alibabacloud.com/saml-role/sp-metadata.xml`。 
    1.  登录 [RAM 控制台](https://ram.console.aliyun.com/)。
    2.  在左侧导航栏，单击 **SSO 管理**。
    3.  在**角色 SSO** 页签下查看 **SAML 服务提供商元数据 URL**。
2.  在企业 IdP 中创建一个 SAML SP，并根据实际情况选择下面任意一种方式配置阿里云为信赖方： 
    -   直接使用上述阿里云的元数据 URL 进行配置。
    -   如果您的 IdP 不支持 URL 配置，您可以根据上述 URL 下载元数据文件并上传至您的 IdP。
    -   如果您的 IdP 不支持元数据文件上传，则需要手动配置以下参数：
        -   `Entity ID`：`urn:alibaba:cloudcomputing:international`
        -   `ACS URL`：`https://signin.alibabacloud.com/saml-role/sso`
        -   `RelayState`（可选）：如果您的 IdP 支持设置`RelayState`参数，您可以将其配置成 SSO 登录成功后希望跳转到的页面 URL。如果不进行配置，SSO 登录成功后，将会跳转到阿里云控制台首页。

            **说明：** 您只能填写 `*.console.aliyun.com` 或 `*.console.alibabacloud.com` 域名下的 URL 作为 `RelayState` 的值。


在企业 IdP 中配置阿里云为可信 SAML SP 后，需要在企业 IdP 中配置 SAML 断言属性。

阿里云要求企业 IdP 生成的 SAML 断言里包含一些必要的信息以确定企业用户的登录身份，因此企业 IdP 必须进行属性配置来匹配 RAM 角色，从而实现企业用户与阿里云的 SSO。

具体需要配置的 SAML 断言属性请参考：[支持角色 SSO 的 SAML 断言](ZH-CN_TP_136748_V1.dita)。

