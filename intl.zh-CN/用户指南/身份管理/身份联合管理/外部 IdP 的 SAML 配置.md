# 外部 IdP 的 SAML 配置 {#concept_gsy_gw3_sfb .concept}

阿里云 SAML 联合登录涉及的配置操作包括外部 IdP 的 SAML 配置和阿里云账号作为 SP 的SAML配置，以建立外部 IdP 与阿里云账号之间的信任关系。本文主要介绍外部 IdP 的 SAML 配置流程。

## 一、配置阿里云账号为可信 SAML SP {#section_ehv_hrj_sfb .section}

1.  从阿里云获取您的云账号的 SAML 服务提供方元数据 URL。
    1.  登录 [RAM 控制台](https://ram.console.aliyun.com/)。
    2.  单击**人员管理** \> **设置** \> **高级设置**，在**SSO 登录设置**下可以查看当前云账号的**SAML 服务提供方元数据 URL**。
2.  在外部 IdP 中创建一个 SAML SP，并配置阿里云的 SAML 服务提供方元数据 URL。

    **说明：** 如果您的 IdP 不支持 URL 配置，那么您可以从**SAML 服务提供方元数据 URL**下载 XML 文件，并在创建 SAML SP 的相应流程中上传此 XML文件。


## 二、在 IdP 中定制 SAML 断言 {#section_wyp_hrj_sfb .section}

阿里云需要通过 User Principal Name \(UPN\)来定位一个 RAM 用户，所以要求外部 IdP 生成的 SAML 回应里包含用户的 UPN。阿里云通过解析 SAML 断言中的 NameID 节点，来匹配 RAM 用户的 UPN 从而实现用户的联合登录。

所以，在定制 IdP 颁发的 SAML 断言时，需要将对应于 RAM 用户 UPN 的字段映射为 SAML 断言中的 NameID。

## 示例 {#section_obf_2pm_sfb .section}

由于不同 IdP 的系统差异，关于 SAML SP 配置和断言定制的操作流程都有些差异。在本章内容中，我们会提供一个以 Microsoft Active Directory 与阿里云进行联合 SSO 集成的[示例](intl.zh-CN/用户指南/身份管理/身份联合管理/示例.md#)，用于帮助客户理解企业 IdP 与阿里云身份联合的端到端配置流程。

