# Configure the SAML for role-based SSO {#concept_ntr_jkt_zgb .concept}

This topic describes how to configure the metadata for role-based SSO according to SAML 2.0 to establish trust between your identity provider \(IdP\) and Alibaba Cloud.

## Create an IdP in RAM {#section_rvy_lkt_zgb .section}

1.  Log on to the [RAM console](https://ram.console.aliyun.com/).
2.  In the left-side navigation pane, choose **SSO**.
3.  On the **Role-based SSO** tab, click **Create IdP**.
4.  Enter the **IdP Name** and **Note**.
5.  In the **Metadata File** area, click **Upload**.

    **Note:** The metadata file, usually in XML format, is provided by an IdP. It contains the IdP's logon service address, the public key for verifying the SAML assertion, and the assertion format.

6.  Click **OK**. After creating an IdP, you can view and modify basic information of the IdP:

    -   Click the target IdP name to view the basic information of the IdP, including the IdP name, ARN, and the metadata file.
    -   On the **IdP Information** page, click **Modify** to modify the basic information of the IdP, including the IdP name and the metadata file.
    **Note:** If you want to delete the IdP, click **Delete**.


## What to do next {#section_kfd_11z_zgb .section}

After creating an IdP in RAM, you must create one or more RAM roles with the trusted entity type set to IdP, to establish an association between the IdP and Alibaba Cloud.

Click **Create RAM Role** to navigate to the page for creating RAM roles. For more information about how to create a RAM role, see [RAM role management](intl.en-US/User Guide/Identity management/RAM roles and identities/RAM role management.md#).

