# Implement user-based SSO by using AD FS {#concept_bpk_3jc_mfb .concept}

This topic provides an example of how to implement user-based Single Sign On \(SSO\) from AD FS to Alibaba Cloud, detailing the end-to-end SSO process from an enterprise identity provider \(IdP\) to Alibaba Cloud.

## Notes {#section_shi_bb2_bxr .section}

This topic uses Windows Server 2012 R2 as an example to describe how to implement user-based SSO from AD FS to Alibaba Cloud.

## Prerequisites {#section_i32_zdd_mfb .section}

Microsoft AD is properly configured and the following server roles are configured on Windows Server 2012 R2:

-   DNS server: resolves and sends identity authentication requests to the correct Federation Service.
-   Active Directory Domain Service \(AD DS\): creates, queries, and modifies objects such as domain users and domain devices.
-   Active Directory Federation Service \(AD FS\): configures the identity federation relying party and performs SSO authentication for the configured relying party.

## Example configuration {#section_k32_zdd_mfb .section}

The configuration details used in the example are as follows:

-   The default domain name of the Alibaba Cloud account: `secloud.onaliyun.com`.
-   The RAM user under the Alibaba Cloud account: `alice`. The User Principal Name \(UPN\) of the RAM user is `alice@secloud.onaliyun.com`.
-   The AD FS of the on-premises Microsoft AD: `adfs.secloud.club`.
-   The domain name of the on-premises Microsoft AD: `secloud.club`. The NETBIOS is `secloud`.
-   The UPN of the RAM user \(Alice\) in Microsoft AD: `alice@secloud.club`. The RAM user can also use `secloud\alice` for intra-domain logon.

## Configure AD FS as a trusted SAML IdP in RAM {#section_m32_zdd_mfb .section}

1.  Enter the following URL in your browser:

    ``` {#codeblock_no3_8nt_ocd}
    https://adfs.secloud.club/FederationMetadata/2007-06/FederationMetadata.xml
    ```

2.  Download the metadata file in XML format.
3.  In the RAM console, use the metadata file for SSO configuration.

For more information, see [Configure the SAML for user-based SSO](reseller.en-US/User Guide/SSO management/User-based SSO/Configure the SAML for user-based SSO.md#).

## Configure Alibaba Cloud as a trusted SAML SP in AD FS {#section_q32_zdd_mfb .section}

In AD FS, SAML SP is called relying party. To configure Alibaba Cloud as a trusted SP, follow these steps:

1.  On the Server Manager page, choose **Tools** \> **AD FS Management**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23741/156171507114260_en-US.png)

2.  Select **Add Relying Party Trust**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23741/156171507214261_en-US.png)

3.  Set the SAML metadata of Alibaba Cloud for the relying party.

    To view the SAML metadata URL, log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram), click **SSO** in the left-side navigation pane, and click **User-based SSO**. You can enter the metadata URL when configuring the AD FS relying party.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23741/156171507214262_en-US.png)

    After the relying party is configured, Alibaba Cloud sends a request to authenticate RAM users under the Alibaba Cloud account whose default domain name is `secloud.onaliyun.com` to AD FS `adfs.secloud.club`. AD FS receives the request from Alibaba Cloud, authenticates the user, and sends a response to Alibaba Cloud.


## Configure the SAML assertion attributes for the Alibaba Cloud SP {#section_u32_zdd_mfb .section}

We recommend that you set the value of the `NameID` field in the SAML assertion to the UPN of the RAM user, so that Alibaba Cloud can locate the correct RAM user according to the SAML response.

You must set the UPN in the AD to the `NameID` in the SAML assertion. The procedure is as follows:

1.  Right-click the display name of the relying party and select **Edit Claim Rules**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23741/156171507314263_en-US.png)

2.  Click **Issuance Transform Rules** to add a rule.

    **Note:** **Issuance Transform Rules** indicates how to transform a known user attribute and issue it as an attribute in the SAML assertion. You must issue the UPN of a user in Microsoft AD as a `NameID`. This means that a new rule is required.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23741/156171507314264_en-US.png)

3.  From the **Claim rule template** drop-down list, select **Transform an Incoming Claim**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23741/156171507314265_en-US.png)

4.  Select **Edit Rule**.

    **Note:** In this example, the domain name of the UPN in the Alibaba Cloud account is `secloud.onaliyun.com`, and the domain name of the UPN in Microsoft AD is `secloud.club`. If you directly map the UPN in Microsoft AD to the `NameID`, Alibaba Cloud cannot match the correct user.

    To solve this problem, use one of the following methods:

    1.  Method 1: Set the domain name of Microsoft AD to the domain alias of your Alibaba Cloud account.

        If the domain name `secloud.club` of Microsoft AD is registered in a DNS on the Internet, you can set `secloud.club` to the domain alias of RAM. For information about how to set a domain alias, see [Create a domain alias for an Alibaba Cloud account](reseller.en-US/User Guide/Security settings/Advanced settings/Create a domain alias for an Alibaba Cloud account.md#).

        After the settings are completed, map the UPN to the `NameID` on the Edit Rule page.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23741/156171507414266_en-US.png)

    2.  Method 2: Transform the domain names in AD FS.

        If the domain name `secloud.club` is an intranet domain name of an enterprise, Alibaba Cloud cannot verify the domain ownership of the enterprise. RAM can only use the default domain name `secloud.onaliyun.com`.

        In this case, in the SAML assertion issued by AD FS to Alibaba Cloud, you must replace the domain name suffix `secloud.club` of the UPN with `secloud.onaliyun.com`.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23741/156171507414267_en-US.png)

    3.  Method 3: Set the domain name of Microsoft AD to an auxiliary domain name.

        **Note:** You can configure auxiliary domain by modifying SSO settings on the **User-based SSO** tab.

        If the domain name `secloud.club` is an intranet domain name of an enterprise, Alibaba Cloud cannot verify the domain ownership of the enterprise. In this case, you can set `secloud.onaliyun.com` to the auxiliary domain name. For information about how to set an auxiliary domain name, see [Set an auxiliary domain name](reseller.en-US/User Guide/SSO management/User-based SSO/Configure the SAML for user-based SSO.md#).

    After the settings are completed, map the UPN to the `NameID` on the Edit Rule page.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23741/156171507414266_en-US.png)


