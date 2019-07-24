# SSO overview {#concept_etn_fjc_mfb .concept}

This topic describes the concepts and methods of Single Sign On \(SSO\), also known as identity federation. Enterprises can implement SSO to their Alibaba Cloud accounts by using SAML 2.0.

## Concepts {#section_khp_n4p_pgb .section}

 Identity provider \(IdP\)
 :   A RAM entity that provides identity management services. IdPs are generally classified into the following types:

    -   Locally deployed IdPs, such as Microsoft Active Directory Federation Service \(AD FS\) and Shibboleth
    -   Cloud-based IdPs, such as Azure AD, Google G Suite, Okta, and OneLogin

  Service provider \(SP\)
 :   An application that uses the identity management function of an IdP to provide users with specific services. An SP uses the user information provided by an IdP. In some identity systems \(such as OpenID Connect\) that do not comply with the SAML protocol, SP is known as relying party, which means the relying party of an IdP.

  Security Assertion Markup Language 2.0 \(SAML 2.0\)
 :   A protocol for enterprise-level user identity authentication. It can be used to achieve communication between an SP and an IdP. SAML 2.0 is a standard that enterprises can use to implement enterprise-level SSO.

  SAML assertion
 :   A core element in the SAML protocol to describe the authentication request and response. For example, specific properties of a user are contained in the authentication response assertion.

  Trust
 :   A mutual trust mechanism between an SP and an IdP. It is usually implemented by using public and private keys. An SP obtains SAML metadata of an IdP in a trusted way. The metadata includes the public key for verifying the SAML Assertion issued by the IdP. The SP can use the public key to verify the assertion integrity.

 ## Methods of SSO {#section_a32_4wp_pgb .section}

Enterprises can implement SSO with Alibaba Cloud through SAML 2.0-based IdPs \(for example, AD FS\). Alibaba Cloud offers the following two SAML 2.0-based SSO methods:

-   User-based SSO: The RAM user that you can use to log on to Alibaba Cloud can be determined through a SAML assertion. After logon, you can use the RAM user to access Alibaba Cloud. For more information, see [Overview of user-based SSO](intl.en-US/User Guide/SSO management/User-based SSO/Overview of user-based SSO.md#).
-   Role-based SSO: The RAM role that you can use to log on to Alibaba Cloud can be determined through SAML assertions. After logon, you can use the role specified in the SAML assertion to access Alibaba Cloud. For more information, see [Overview of role-based SSO](intl.en-US/User Guide/SSO management/Role-based SSO/Overview of role-based SSO.md#).

## Comparison between role-based SSO and user-based SSO {#section_kyq_l1m_bhb .section}

|SSO method|Supports SSO initiated by SP?|Supports SSO initiated by IdP?|Supports logon with your RAM account and password?|Supports association of one IdP and multiple Alibaba Cloud accounts?|Supports multiple IdPs?|
|:---------|:----------------------------|:-----------------------------|:-------------------------------------------------|:-------------------------------------------------------------------|:----------------------|
|User- based SSO|Yes|Yes|No|No|No|
|Role-based SSO|No|Yes|Yes|Yes|Yes|

**Note:** For more information, see [Application scenarios of SSO](intl.en-US/User Guide/SSO management/Application scenarios of SSO.md#).

