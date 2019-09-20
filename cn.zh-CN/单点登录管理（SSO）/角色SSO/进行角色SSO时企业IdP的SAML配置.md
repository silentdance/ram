# 进行角色SSO时企业IdP的SAML配置 {#task_o3t_54r_bhb .task}

本文主要介绍企业在使用角色SSO时，如何在企业身份提供商（IdP）中配置阿里云为可信SAML服务提供商（SP）。

1.  企业IdP的SAML SP配置需要使用阿里云的SAML服务提供商元数据URL：`https://signin.aliyun.com/saml-role/sp-metadata.xml`。 
    1.  云账号登录 [RAM控制台](https://ram.console.aliyun.com/)。
    2.  在左侧导航栏，单击**SSO管理**。
    3.  在**角色SSO** 页签下查看**SAML服务提供商元数据URL**。
2.  在企业IdP中创建一个SAML SP，并根据实际情况选择下面任意一种方式配置阿里云为信赖方： 
    -   直接使用上述阿里云的元数据URL进行配置。
    -   如果您的IdP不支持URL配置，您可以根据上述URL下载元数据文件并上传至您的IdP。
    -   如果您的IdP不支持元数据文件上传，则需要手动配置以下参数：
        -   `Entity ID`：`urn:alibaba:cloudcomputing`
        -   `ACS URL`：`https://signin.aliyun.com/saml-role/sso`
        -   `RelayState`（可选）：如果您的IdP支持设置`RelayState`参数，您可以将其配置成SSO登录成功后希望跳转到的页面URL。如果不进行配置，SSO登录成功后，将会跳转到阿里云控制台首页。

            **说明：** 您只能填写`*.console.aliyun.com`域名下的URL作为`RelayState`的值。


在企业IdP中配置阿里云为可信SAML SP后，需要在企业IdP中配置SAML断言属性。

阿里云要求企业IdP生成的SAML断言里包含一些必要的信息以确定企业用户的登录身份，因此企业IdP必须进行属性配置来匹配RAM角色，从而实现企业用户与阿里云的SSO。

具体需要配置的SAML断言属性请参见[支持角色 SSO 的 SAML 断言](ZH-CN_TP_136748_V1.dita)。

