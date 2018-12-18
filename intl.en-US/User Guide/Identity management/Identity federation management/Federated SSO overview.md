# Federated SSO overview {#concept_etn_fjc_mfb .concept}

Many enterprises want to leverage their own identity systems, including those from other providers, to enable federated Single Sign On \(SSO\) to better manage their resources and applications deployed locally and in the cloud. This topic describes Alibaba Cloud RAM federated SSO solution to help users quickly understand and configure federated SSO.

Alibaba Cloud supports the [SAML 2.0 \(Security Assertion Markup Language 2.0\)](https://wiki.oasis-open.org/security) Identity Federation open standards that are widely used by enterprise identity providers \(IdPs\). By enabling federated SSO, users can use the account authentication mechanism of their organization to log on to the Alibaba Cloud console.

The following table details some basic terms related to SAML federated SSO.

## Terms {#section_01 .section}

|Term|Description|
|:---|:----------|
|Identity Provider \(IdP\)|Provides identity management services, for example:-   Locally deployed IdPs, such as Microsoft Active Directory Federation Service \(AD FS\) and Shibboleth.
-   Cloud-based IdPs, such as Azure AD, Google G Suite, Okta, and OneLogin.

|
|Service Provider \(SP\)|Uses the identity management function of an IdP to provide users with specific service applications. An SP uses the user information provided by an IdP. In some identity systems \(such as OpenID Connect\) that do not comply with the SAML protocol, Service Provider is known as Relying Party, which means the relying party of an IdP.|
|Security Assertion Markup Language \(SAML\)|A standard protocol for enterprise-level user identity authentication. It can be used to achieve communication between an SP and an IdP. SAML 2.0 is a de facto standard that enterprises can use to implement Identity Federation.|
|SAML Assertion|A core element in the SAML protocol to describe the authentication request and response. For example, specific properties of a user are contained in the authentication response assertion.|
|Trust|A Mutual Trust mechanism between an SP and an IdP. It is usually implemented by using public and private keys. An SP obtains the Identity Federation metadata of an IdP through a circle of trust establishment. The metadata includes the public key for verifying the SAML Assertion issued by the IdP. The SP can use the public key to verify the assertion integrity.|

## SAML federated SSO process {#section_02 .section}

In the scenario where Alibaba Cloud services are integrated with an enterprise identity system, Alibaba Cloud is the SP, and the enterprise identity system is the IdP. The following figure shows the ways enterprise employees can log on to the Alibaba Cloud console through their enterprise identity services.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23739/154514280614250_en-US.png)

As shown in the figure, after the administrator configures the services provided by an enterprise IdP, the enterprise's employees can log on to the Alibaba Cloud console by performing the following steps:

1.  An enterprise employee logs on to Alibaba Cloud through a browser, and Alibaba Cloud returns an SAML authentication request to the browser.
2.  The browser forwards the request to the enterprise IdP.
3.  The enterprise IdP prompts the RAM user to log on and returns an SAML response to the browser.
4.  The browser forwards the SAML response to Alibaba Cloud.
5.  With the SAML Mutual Trust configuration, Alibaba Cloud verifies the digital signature of the SAML response and the authenticity of the SAML Assertion, and then matches the RAM user's identity according to the user name configured in SAML Assertion.
6.  After the logon service is verified, Alibaba Cloud returns the logon session and the URL of the Alibaba Cloud console to the browser.
7.  The browser redirects to the Alibaba Cloud console.

    **Note:** In step 1, the employee is not required to log on to Alibaba Cloud. Instead, the employee can click the link on the enterprise IdP portal to send an SAML authentication request to the enterprise IdP and access the console.


## SAML federated SSO configuration {#section_03 .section}

Before configuring SAML federated SSO, you must establish the mutual trust between your Alibaba Cloud account and your enterprise IdP.

For example, your enterprise is using some IdPs that are compatible with SAML 2.0, such as AD FS, Google G Suite, and Shibboleth. The following describes how to perform the general configuration:

1.  **Configure the Alibaba Cloud account as a trusted SAML SP in an external IdP.**
    1.  Obtain the SAML Service Provider Metadata URL of your account from Alibaba Cloud. For details, see [Configure the SAML of an external IdP](reseller.en-US/User Guide/Identity management/Identity federation management/Configure the SAML of an external IdP.md#).
    2.  On the IdP side, use the metadata to register your account as a SP and establish the mutual trust between your enterprise IdP and Alibaba Cloud account.
    3.  Customize an SAML assertion in the external IdP.

        The IdP and SP must achieve common understanding of the SAML assertion to better understand the description of a user identity. Alibaba Cloud uses a User Principal Name \(UPN\) to locate a RAM user. Therefore, the SAML response generated by an external IdP must contain the UPN of the RAM user. Alibaba Cloud resolves the NameID node in the SAML assertion and matches the UPN of the RAM user, so that the federated SSO can be implemented.

        That means, when you customize the SAML assertion issued by an IdP, you need to map the UPN of a RAM user to the NameID in the SAML assertion.

2.  **Configure a trusted external SAML IdP in the Alibaba Cloud account.**

    To establish the mutual trust between Alibaba Cloud and your enterprise IdP, you must configure your IdP to Alibaba Cloud using the SAML metadata provided by the enterprise IdP. The metadata includes the IdP service address, the public key for verifying the SAML assertion, and the assertion format. Common IdP services provide the specific URLs for downloading the SAML metadata. For details, see [Configure the SAML of an account](reseller.en-US/User Guide/Identity management/Identity federation management/Configure the SAML of an account.md#).

3.  **Provision users.**

    After establishing the mutual trust between the SP and the IdP, you must create one or more RAM users that correspond to users in the enterprise IdP. Only RAM users can use SSO authentication. You cannot use SSO for your account.

    You can provision the users using either of the following methods:

    -   Log on to the RAM console and manually create the RAM users that match the enterprise IdP.
    -   Use a RAM SDK to write a program or use aliyuncli to customize a solution.
    -   Use the Alibaba Cloud RAM user synchronization tool to synchronize users from the enterprise IdP to Alibaba Cloud RAM.

        **Note:** To use the RAM user synchronization tool for a trial, contact your account manager.

    For details about how to provision users, see [Provision users](reseller.en-US/User Guide/Identity management/Identity federation management/Provision users.md#).


After the preceding configurations are complete, the federated SSO can be implemented between RAM users and an enterprise IdP. When a RAM user in a account logs on to Alibaba Cloud, Alibaba Cloud automatically directs to the URL of your enterprise IdP for the user to log on. After the logon succeeds, the Alibaba Cloud console is automatically displayed.

