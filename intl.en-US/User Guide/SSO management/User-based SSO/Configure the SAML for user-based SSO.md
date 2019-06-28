# Configure the SAML for user-based SSO {#task_fzb_hjc_mfb .task}

This topic describes how to configure the metadata for user-based Single Sign On \(SSO\) according to SAML 2.0 to establish trust between your identity provider \(IdP\) and Alibaba Cloud.

A default domain name, a domain alias, or an auxiliary domain name is set for your Alibaba Cloud account to simplify SAML SSO. For more information, see [Manage the default domain name of an Alibaba Cloud account](intl.en-US/User Guide/Security settings/Advanced settings/Manage the default domain name of an Alibaba Cloud account.md#) and [Create a domain alias for an Alibaba Cloud account](intl.en-US/User Guide/Security settings/Advanced settings/Create a domain alias for an Alibaba Cloud account.md#).

1.  Log on to the [RAM console](https://ram.console.aliyun.com/).
2.  In the left-side navigation pane, click **SSO**.
3.  Click the **User-based SSO** tab.
4.  In the **SSO Settings** section, click **Modify** to modify the SSO settings as needed. 
    -   **SSO Status**: You can enable or disable the SSO function as needed.

        **Note:** This setting applies to all RAM users under your Alibaba Cloud account.

        -   The SSO function is disabled by default. If the SSO function is disabled, RAM users can use their passwords for logon, and all SSO settings do not take effect.
        -   If you enable the SSO function, RAM users cannot use their passwords for logon. They must log on to an IdP for identity authentication. If the SSO function is disabled later, the page for logon by using passwords is automatically displayed.
    -   **Metadata File**: You can click **Upload** to upload the metadata file provided by your IdP.

        **Note:** The metadata file, usually in XML format, is provided by an IdP. It contains the IdP's logon service address and X.509 public key certificate that is used to verify the validity of the SAML assertion issued by the IdP.

    -   **Auxiliary Domain**: \(Optional\) You can click **Edit** to set an auxiliary domain name.

        -   If you set an auxiliary domain name, you can use it as the suffix of the `NameID` element in the SAML assertion.
        -   If you do not set an auxiliary domain name, you must use the default domain name or domain alias of your Alibaba Cloud account as the suffix of the `NameID` element in the SAML assertion.
        For more information about values of the `NameID` element, see [Configure the SAML of an IdP during user-based SSO](intl.en-US/User Guide/SSO management/User-based SSO/Configure the SAML of an IdP during user-based SSO.md#).

        **Note:** If you set a domain alias and an auxiliary domain name at the same time, only the domain alias or the default domain name can be used as the suffix of the `NameID` element.


You can migrate or synchronize data from your IdP to Alibaba Cloud or Alibaba Cloud RAM by using either of the following methods:

-   Log on to the [RAM console](https://ram.console.aliyun.com/) and create RAM users that match the users in your IdP.
-   Use a RAM SDK to write a program or use Alibaba Cloud command line interface \(CLI\) to customize a solution.

