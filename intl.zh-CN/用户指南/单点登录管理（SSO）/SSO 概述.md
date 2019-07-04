# SSO 概述 {#concept_etn_fjc_mfb .concept}

阿里云支持基于 SAML 2.0 的 SSO（Single Sign On，单点登录），也称为身份联合登录。本文为您介绍企业如何使用自有的身份系统实现与阿里云的 SSO。

## SSO 基本概念 {#section_gjk_3tl_bhb .section}

阿里云提供基于 SAML 2.0 协议的 SSO。为了更好的理解 SSO，下面简要介绍与 SAML / SSO 相关的一些基本概念：

 身份提供商（IdP）
 :   一个包含有关外部身份提供商元数据的 RAM 实体，身份提供商可以提供身份管理服务。例如：

-   企业本地 IdP ：Microsoft Active Directory Federation Service （AD FS）、Shibboleth 等。
-   Cloud IdP ：Azure AD、Google G Suite、Okta、OneLogin 等。

  服务提供商（SP）
 :   利用 IdP 的身份管理功能，为用户提供具体服务的应用，SP 会使用 IdP 提供的用户信息。一些非 SAML 协议的身份系统（例如：OpenID Connect），也把服务提供商称作 IdP 的信赖方。

  安全断言标记语言（SAML 2.0）
 :   实现企业级用户身份认证的标准协议，它是 SP 和 IdP 之间实现沟通的技术实现方式之一。SAML 2.0 已经是目前实现企业级 SSO 的一种事实标准。

  SAML 断言（SAML assertion）
 :   SAML 协议中用来描述认证请求和认证响应的核心元素。例如：用户的具体属性就包含在认证响应的断言里。

  信赖（Trust）
 :   建立在 SP 和 IdP 之间的互信机制，通常由公钥和私钥来实现。SP 通过可信的方式获取 IdP 的 SAML 元数据，元数据中包含 IdP 签发 SAML 断言的签名验证公钥，SP 则使用公钥来验证断言的完整性。

 ## SSO 的方式 {#section_wzw_k5l_bhb .section}

企业根据自身需要，使用支持 SAML 2.0 的企业 IdP（例如：AD FS）与阿里云进行 SSO。阿里云提供以下两种基于 SAML 2.0 协议的 SSO 方式：

-   用户 SSO：阿里云通过 IdP 颁发的 SAML 断言确定企业用户与阿里云 RAM 用户的对应关系 。企业用户登录后，使用该 RAM 用户访问阿里云。详情请参考：[用户 SSO 概述](../intl.zh-CN/用户指南/单点登录管理（SSO）/用户 SSO/用户 SSO 概述.md#)。
-   角色 SSO：阿里云通过 IdP 颁发的 SAML 断言确定企业用户在阿里云上可以使用的 RAM 角色。企业用户登录后，使用 SAML 断言中指定的 RAM 角色访问阿里云。详情请参考：[角色 SSO 概述](../intl.zh-CN/用户指南/单点登录管理（SSO）/角色 SSO/角色 SSO 概述.md#)。

## SSO 方式的比较 {#section_kyq_l1m_bhb .section}

|SSO 方式|SP 发起的 SSO|IdP 发起的 SSO|使用 RAM 用户账号和密码登录|一个 IdP 关联多个阿里云账号|多个 IdP|
|:-----|:---------|:----------|:---------------|:---------------|:-----|
|用户 SSO|√|√|×|×|×|
|角色 SSO|×|√|√|√|√|

**说明：** 

-   “√”支持，“×”表示不支持。
-   关于用户 SSO 与角色 SSO 的更多比较，请参考：[联合登录方式的适用场景](intl.zh-CN/用户指南/单点登录管理（SSO）/SSO 方式的适用场景.md#)。

