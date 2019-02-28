# Federated SSO overview {#concept_etn_fjc_mfb .concept}

This topic describes the Alibaba Cloud RAM federated Single Sign On \(SSO\) solution that allows users to configure and enable federated SSO using their own identity systems.

## Federated SSO prerequisites {#section_khp_n4p_pgb .section}

Alibaba Cloud supports the [SAML 2.0 \(Security Assertion Markup Language 2.0\)](https://wiki.oasis-open.org/security) identity federation open standards that are widely used by enterprise identity providers \(IdPs\). By enabling federated SSO, users can use the account authentication mechanism of their organization to log on to the Alibaba Cloud console.

|Term|Description|
|:---|:----------|
| Identity Provider \(IdP\)

 |Provides identity management services, for example:-   Locally deployed IdPs, such as Microsoft Active Directory Federation Service \(AD FS\) and Shibboleth.
-   Cloud-based IdPs, such as Azure AD, Google G Suite, Okta, and OneLogin.

|
| Service Provider \(SP\)

 |Uses the identity management function of an IdP to provide users with specific service applications. An SP uses the user information provided by an IdP. In some identity systems \(such as OpenID Connect\) that do not comply with the SAML protocol, Service Provider is known as Relying Party, which means the relying party of an IdP.|
| Security Assertion Markup Language \(SAML\)

 |A standard protocol for enterprise-level user identity authentication. It can be used to achieve communication between an SP and an IdP. SAML 2.0 is a de facto standard that enterprises can use to implement identity federation.|
| SAML Assertion

 |A core element in the SAML protocol to describe the authentication request and response. For example, specific properties of a user are contained in the authentication response assertion.|
| Trust

 |A Mutual Trust mechanism between an SP and an IdP. It is usually implemented by using public and private keys. An SP obtains the identity federation metadata of an IdP through a circle of trust establishment. The metadata includes the public key for verifying the SAML Assertion issued by the IdP. The SP can use the public key to verify the assertion integrity.|

## SAML federated SSO process {#section_02 .section}

In the following scenario, Alibaba Cloud services are integrated with an enterprise identity system, Alibaba Cloud is the SP, and the enterprise identity system is the IdP. The following figure shows the methods by which enterprise employees can log on to the Alibaba Cloud console through their enterprise identity services.

![Process](images/14250_en-US.png "Process")

As shown in the figure, after the administrator configures the SAML federated SSO, employees can log on to the Alibaba Cloud console by performing the following steps:

1.  The enterprise employee Alice logs on to Alibaba Cloud through a browser, and Alibaba Cloud returns an SAML authentication request to the browser.
2.  The browser forwards the SAML authentication request to the enterprise IdP.
3.  The enterprise IdP prompts the RAM user to log on and returns an SAML response to the browser.
4.  The browser forwards the SAML response to Alibaba Cloud.
5.  With the SAML Mutual Trust configuration, Alibaba Cloud verifies the digital signature of the SAML response and the authenticity of the SAML Assertion, and then matches the identity of the RAM user according to the user name configured in SAML Assertion.
6.  After the logon service is verified, Alibaba Cloud returns the logon session and the URL of the Alibaba Cloud console to the browser.
7.  The browser redirects to the Alibaba Cloud console.

    **Note:** In step 1, the employee is not required to log on to Alibaba Cloud. Instead, the employee can click the link on the enterprise IdP portal to send an SAML authentication request to the enterprise IdP and access the console.


## SAML federated SSO configuration {#section_03 .section}

Before configuring SAML federated SSO, you must establish a mutual trust relationship between your Alibaba Cloud account and your enterprise IdP.

1.  Configure the SAML of an external IdP. For more information, see [Configure the SAML of an external IdP](reseller.en-US/User Guide/Identity management/Identity federation management/Configure the SAML of an external IdP.md#).

    To make sure your Alibaba Cloud account is trusted by the enterprise IdP, you must configure your Alibaba Cloud account as a trusted SAML SP in an external IdP.

2.  Configure the SAML of an account. For more information, see [Configure the SAML of an account](reseller.en-US/User Guide/Identity management/Identity federation management/Configure the SAML of an account.md#).

    To make sure the enterprise IdP trusts your Alibaba Cloud account, you must configure the enterprise IdP to Alibaba Cloud.

    **Note:** During the configuration, the SAML metadata provided by the enterprise IdP is required. The metadata includes the IdP service address, the public key for verifying the SAML assertion, and the assertion format. Common IdP services provide the specific URLs for downloading the SAML metadata.

3.  Configure RAM users. For more information, see [Configure RAM users](reseller.en-US/User Guide/Identity management/Identity federation management/Configure RAM users.md#).

    After establishing a mutual trust relationship between the SP and the IdP, you must create one or more RAM users that correspond to users in the enterprise IdP. Only RAM users can use SSO authentication.


## Result {#section_a32_4wp_pgb .section}

After the preceding configurations are completed, federated SSO can be implemented between RAM users and an enterprise IdP. Then, when a RAM user logs on to Alibaba Cloud, Alibaba Cloud redirects the user to the URL of your enterprise IdP for the user to use to log on. After the logon succeeds, the Alibaba Cloud console is automatically displayed.

