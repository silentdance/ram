# Set a security policy for RAM users {#task_188786 .task}

This topic describes how to set a security policy for RAM users under your Alibaba Cloud account to better manage RAM user permissions.

1.  Log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram).
2.  Choose **Identities** \> **Settings**.
3.  On the **Security Settings** tab, click **Update RAM user security settings** and set the relevant parameters. 
    -   **Save MFA Logon Status for 7 Days**: Specifies whether to save the multi-factor authentication \(MFA\) logon status for your RAM users. The default value is **Not Allowed**. If you select **Allow**, the MFA logon status is saved for seven days.
    -   **Manage Passwords**: Specifies whether RAM users are allowed to change their own passwords.
    -   **Manage AccessKey**: Specifies whether RAM users are allowed to manage their access keys.
    -   **Manage MFA Devices**: Specifies whether RAM users are allowed to enable or disable an MFA device.
    -   **Logon Session Valid For**: The validity period of the logon sessions. The unit is hours.
    -   **Logon Address Mask**: Specifies which IP addresses cannot be used for logon. This parameter is left unspecified by default. That is, all IP addresses can be used for logon. If you specify this parameter, you cannot log on to the console by using a password or through Single Sign On \(SSO\). However, you can call API actions by using an access key. For information about how to set a logon mask, see [Set a logon mask for an Alibaba Cloud account](reseller.en-US/User Guide/Security settings/Basic security settings/Set a logon mask for an Alibaba Cloud account.md#).
4.  Click **OK**. 

    **Note:** The settings of the security policy apply to all RAM users under your Alibaba Cloud account.


