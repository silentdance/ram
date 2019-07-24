# Configure the SAML for role-based SSO {#task_ntr_jkt_zgb .task}

This topic describes how to configure the metadata for role-based Single Sign On \(SSO\) according to SAML 2.0, to establish trust between your identity provider \(IdP\) and Alibaba Cloud.

1.  Log on to the [RAM console](https://ram.console.aliyun.com/).
2.  In the left-side navigation pane, click **SSO**.
3.  On the **Role-based SSO** tab, click **Create IdP**.
4.  Enter an IdP name and description.
5.  In the **Metadata File** section, click **Upload** to upload a metadata file. 

    **Note:** The metadata file, usually in XML format, is provided by an IdP. It contains the logon service address of the IdP, the public key for verifying the SAML assertion, and the assertion format.

6.  Click **OK**.

After you create an IdP in RAM, you must create one or more RAM roles with the trusted entity type set to IdP, to establish an association between the IdP and Alibaba Cloud.

Click **Create RAM Role** to navigate to the page for creating RAM roles. For more information about how to create a RAM role, see [Create a RAM role for a trusted IdP](intl.en-US/User Guide/RAM roles/Create a RAM role/Create a RAM role for a trusted IdP.md#).

