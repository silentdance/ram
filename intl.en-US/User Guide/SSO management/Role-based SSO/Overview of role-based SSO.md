# Overview of role-based SSO {#concept_zrv_2ny_zgb .concept}

This topic describes the scenario, process, and configuration of role-based Single Sign On \(SSO\).

## Scenario {#section_t5k_rhp_chb .section}

In scenarios where Alibaba Cloud and the identity management system of an enterprise work together to perform role-based SSO, Alibaba Cloud is the service provider \(SP\) and the enterprise system is the identity provider \(IdP\). Through role-based SSO, the enterprise can manage users in the local IdP without synchronizing users from your IdP to Alibaba Cloud, and the enterprise employee can log on to Alibaba Cloud by using a specific RAM role.

## Role-based SSO process {#section_wcm_shp_chb .section}

Through role-based SSO, you can access Alibaba Cloud either by logging on to the Alibaba Cloud console or by using a program.

## Access Alibaba Cloud through the console {#section_xr3_3y4_chb .section}

![](images/40723_en-US.png "Process")

As shown in the figure, after the administrator configures role-based SSO, the employee \(Alice\) can log on to Alibaba Cloud after the following steps are completed:

1.  Alice uses the browser to select Alibaba Cloud as the target service on the logon page of the IdP.

    For example, if the IdP is Microsoft Active Directory Federation Service \(AD FS\), the log on URL will be `https://ADFSServiceName/adfs/ls/IdpInitiatedSignOn.aspx`.

    **Note:** Some IdPs require users to log on first and then select an SSO application that represents Alibaba Cloud.

2.  The IdP generates an SAML response to the browser.
3.  The browser redirects to the page of the SSO service, and forwards the SAML response.
4.  The SSO service uses the SAML response to request an STS token from the Alibaba Cloud STS service, and generates a URL that can log on to the Alibaba Cloud console with the STS token.

    **Note:** If the SAML response contains attributes that map to multiple RAM roles, the user is prompted to select a role firstly.

5.  The SSO service returns the URL to the browser.
6.  The browser redirects to the URL, and logs on to the Alibaba Cloud console with the specific RAM role.

## Access Alibaba Cloud through a program {#section_xfl_sdp_chb .section}

![](images/40724_en-US.png "Process")

As shown in the figure, the employee \(Alice\) can log on to Alibaba Cloud after the following steps are completed:

1.  Alice initiates an authentication request to the IdP through a program.
2.  The IdP generates an SAML response that contains the user's SAML assertion, and returns the SAML response to the program.
3.  The program calls the [AssumeRoleWithSAML](../../../../intl.en-US/API Reference (STS)/Operation interfaces/AssumeRoleWithSAML.md#) API action of the Alibaba Cloud STS service, and forwards the information including the ARN of an Alibaba Cloud IdP, the ARN of the role to be assumed, and the SAML assertion obtained from the IdP.
4.  The STS service verifies the SAML assertion and returns an STS token to the program.
5.  The program calls an Alibaba Cloud API action with the STS token.

## Configure role-based SSO {#section_kq5_wwr_bhb .section}

Before you use role-based SSO, you must set configurations to establish trust between Alibaba Cloud and your IdP.

1.  To make sure your IdP is trusted by Alibaba Cloud, you must configure the IdP in the Alibaba Cloud console.

    For more information, see [EN-US\_TP\_135641.md\#](intl.en-US/User Guide/SSO management/Role-based SSO/Configure the SAML for role-based SSO.md#).

2.  You must use a program or log on to the RAM console to create RAM roles and grant permissions to them.

    For more information, see [Create a RAM role for a trusted IdP](intl.en-US/User Guide/RAM roles/Create a RAM role/Create a RAM role for a trusted IdP.md#).

3.  To make sure Alibaba Cloud is trusted by the IdP, you must configure Alibaba Cloud as a trusted SAML SP and configure SAML assertions in your IdP.

    For more information, see [EN-US\_TP\_136785.md\#](intl.en-US/User Guide/SSO management/Role-based SSO/Configure the SAML of an IdP during role-based SSO.md#).


The processes of configuring SAML assertions and an SAML SP vary according to the IdP system. For more information about how to implement role-based SSO from AD FS to Alibaba Cloud, see [Implement role-based SSO by using AD FS](intl.en-US/User Guide/SSO management/Role-based SSO/Implement role-based SSO by using AD FS.md#).

