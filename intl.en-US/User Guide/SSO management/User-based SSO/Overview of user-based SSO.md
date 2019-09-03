# Overview of user-based SSO {#concept_kwz_hrk_bhb .concept}

This topic describes the scenario, process, and configuration of user-based Single Sign On \(SSO\).

## Scenario {#section_ovg_sr3_dhb .section}

In scenarios where Alibaba Cloud and the identity management system of an enterprise work together to perform user-based SSO, Alibaba Cloud is the service provider \(SP\) and the enterprise system is the identity provider \(IdP\). User-based SSO allows an employee in the enterprise to access Alibaba Cloud as a RAM user.

## User-based SSO process {#section_byh_tsn_2hb .section}

![](images/40784_en-US.png "Process")

As shown in the preceding figure, after the administrator configures user-based SSO, the employee \(Alice\) can log on to Alibaba Cloud after the following steps are completed:

1.  Alice logs on to the Alibaba Cloud console through a browser, and Alibaba Cloud returns an SAML authentication request to the browser.
2.  The browser forwards the SAML authentication request to the IdP.
3.  The IdP prompts Alice to log on and returns an SAML response to the browser.
4.  The browser forwards the SAML response to the SSO service.
5.  Through the SAML mutual trust configuration, the SSO service verifies the digital signature in the SAML response to check the authenticity of the SAML assertion, and then matches the identity of the RAM user according to the value of `NameID` in the SAML assertion.
6.  The SSO service returns the URL of the Alibaba Cloud console to the browser.
7.  The browser redirects to the Alibaba Cloud console.

    **Note:** In step 1, the employee does not necessarily have to log on to Alibaba Cloud. Instead, the employee can click the link on the IdP portal to send an SAML authentication request to the IdP and access the Alibaba Cloud console.


## User-based SSO configuration {#section_lhr_rsx_bhb .section}

Before you use user-based SSO, you must set configurations to establish trust between Alibaba Cloud and your IdP.

1.  To make sure your IdP is trusted by Alibaba Cloud, you must configure the IdP in the Alibaba Cloud console.

    For more information, see [Configure the SAML for user-based SSO](intl.en-US/User Guide/SSO management/User-based SSO/Configure the SAML for user-based SSO.md#).

2.  To make sure Alibaba Cloud is trusted by the IdP, you must configure Alibaba Cloud as a trusted SAML SP and configure an SAML assertion in your IdP.

    For more information, see [Configure the SAML of an IdP during user-based SSO](intl.en-US/User Guide/SSO management/User-based SSO/Configure the SAML of an IdP during user-based SSO.md#).

3.  After the IdP and Alibaba Cloud are configured, you must create RAM users to match your IdP through SDK, CLI, or logging on to the RAM console.

    For more information, see [Create a RAM user](intl.en-US/User Guide/RAM users/Create a RAM user.md#).


The processes of configuring an SAML assertion and an SAML SP vary according to the IdP system. For more information about how to implement user-based SSO from Microsoft Active Directory Federation Service \(AD FS\) to Alibaba Cloud, see [Implement user-based SSO by using AD FS](intl.en-US/User Guide/SSO management/User-based SSO/Implement user-based SSO by using AD FS.md#).

