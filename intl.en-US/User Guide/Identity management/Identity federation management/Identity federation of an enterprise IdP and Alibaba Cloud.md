# Identity federation of an enterprise IdP and Alibaba Cloud {#concept_bpk_3jc_mfb .concept}

This topic provides an example of how to implement Single Sign On \(SSO\) from Microsoft Active Directory \(AD\) to Alibaba Cloud, detailing the end-to-end identity federation configuration process from an enterprise identity provider \(IdP\) to Alibaba Cloud.

## Prerequisites {#section_i32_zdd_mfb .section}

Microsoft AD has been properly configured and the following server roles have been configured on Windows Server 2012 R2:

-   DNS server: resolves and sends identity authentication requests to the correct Federation Service.
-   Active Directory Domain Service \(AD DS\): creates, queries, and modifies objects such as domain users and domain devices.
-   Active Directory Federation Service \(AD FS\): configures the identity federation relying party and performs SSO authentication for the configured relying party.

## Notes {#section_a14_jgg_4fb .section}

This topic uses Windows Server 2012 R2 as an example to describe how to configure Microsoft AD as the SSO IdP of Alibaba Cloud.

## Example configuration {#section_k32_zdd_mfb .section}

The configuration details used in the example are as follows:

-   Default domain name of the account: `secloud.onaliyun.com`.
-   RAM user under the account: `alice`. The User Principal Name \(UPN\) is `alice@secloud.onaliyun.com`.
-   AD FS of the self-built Microsoft AD: `adfs.secloud.club`.
-   Domain name of the self-built Microsoft AD: `secloud.club`. The NETBIOS is `secloud`.
-   UPN of the user \(alice\) in Microsoft AD: `alice@secloud.club`. The user can also use `secloud\alice` for intra-domain logon.

## Configure AD FS as a trusted SAML IdP in RAM {#section_m32_zdd_mfb .section}

1.  Enter the following URL in your browser:

    ```
    https://adfs.secloud.club/FederationMetadata/2007-06/FederationMetadata.xml
    ```

2.  Download the metadata file in XML format.
3.  In the RAM console, use the metadata file for SSO configuration.

## Configure Alibaba Cloud as a trusted SAML SP in AD FS {#section_q32_zdd_mfb .section}

In AD FS, SAML SP is called **Relying Party**. To configure Alibaba Cloud as a trusted SP, follow these steps:

1.  On the **Server Manager** page, click **Tools** and select **AD FS Management**.

    ![Server manager](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23741/155134580014260_en-US.png)

2.  Select **Add Relying Party Trust**.

    ![AD FS management](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23741/155134580014261_en-US.png)

3.  Set the SAML metadata of Alibaba Cloud for the relying party.

    To view the SAML metadata URL, log on to the **RAM console** and choose **Identities** \> **Settings** \> **Advanced**. You can enter the metadata URL when configuring the AD FS relying party.

    ![Add relying party trust wizard](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23741/155134580014262_en-US.png)

    After the relying party is configured, Alibaba Cloud sends a request to authenticate the RAM user whose domain name is `secloud.onaliyun.com` to AD FS `adfs.secloud.club`. AD FS receives the request from Alibaba Cloud, authenticates the user, and sends a response to Alibaba Cloud.


## Configure the SAML assertion attributes for the Alibaba Cloud SP {#section_u32_zdd_mfb .section}

We recommend that you set the value of the NameID field in the SAML assertion to the UPN of the RAM user, so that Alibaba Cloud can locate the correct RAM user according to the SAML response.

You must set the UPN in the AD to the NameID in the SAML assertion. The procedure is as follows:

1.  Select **Edit Claim Rules**.

    ![Edit claim rules](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23741/155134580014263_en-US.png)

2.  Click **Issuance Transform Rules** to add a rule.

    **Note:** **Issuance Transform Rules** indicates how to transform a known user attribute and issue it as an attribute in the SAML assertion. You must issue the UPN of a user in Microsoft AD as a NameID. This means that a new rule is required.

    ![Issuance transform rules](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23741/155134580014264_en-US.png)

3.  Set **Claim rule template** to **Transform an Incoming Claim**.

    ![Transform an incoming claim](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23741/155134580114265_en-US.png)

4.  Select **Edit Rule**.

    **Note:** In this example, the domain name of the UPN in the account is `secloud.onaliyun.com`, and the domain name of the UPN in Microsoft AD is `secloud.club`. If you directly map the UPN in Microsoft AD to the NameID, Alibaba Cloud cannot match the correct user.

    To solve this problem, use either of the following methods:

    1.  **Method 1:** Set the domain name of Microsoft AD to the **domain alias** of RAM.

        If the domain name `secloud.club` of Microsoft AD is registered in a DNS on the Internet, you can set `secloud.club` to the **domain alias** of RAM. For more information, see [Configure the SAML of an account](reseller.en-US/User Guide/Identity management/Identity federation management/Configure the SAML of an account.md#).

        After the settings are completed, map the UPN to the NameID in the **Edit Rule** window.

        ![Edit rules](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23741/155134580114266_en-US.png)

    2.  **Method 2:** Transform the domain names in AD FS.

        If the domain name `secloud.club` is an intranet domain name of an enterprise, Alibaba Cloud cannot verify the domain ownership of the enterprise. RAM can only use the default domain name `secloud.onaliyun.com`. In this case, in the SAML assertion issued by AD FS to Alibaba Cloud, you must replace the domain name suffix `secloud.club` of the UPN with `secloud.onaliyun.com`.

        ![Edit rules](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23741/155134580114267_en-US.png)


