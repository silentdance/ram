# Domain name management {#concept_f15_z3c_mfb .concept}

Each account has a default domain. You can also set a domain alias for your account. Specifically, you can customize the logon name suffix through the domain name management function. Then, a RAM user can log on to the console using the default domain name or the domain alias.

## Before a RAM user logs on to the console {#section_mfs_lj3_pgb .section}

The logon account of a RAM user must be in the User Principal Name \(UPN\) format, such as the logon user names on the **Users** page of the RAM console.

On the RAM user logon page, a RAM user can select either of the following logon methods:

-   <$username\>@<$AccountAlias\>.onaliyun.com
-   <$username\>@<$AccountAlias\>

## RAM user logon entry {#section_wtz_3j3_pgb .section}

The logon entries for RAM users and Alibaba Cloud accounts are different.

You can find the logon link on the **Overview** page after you log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram).

## Domain name management {#section_qk5_5j3_pgb .section}

**Default domain name**

1.  Log on to the **RAM console**.
2.  Click **Identities** and choose **Settings** \> **Advanced** to view or modify the default domain name.
    -   The format of the **Default Domain** is <$AccountAlias\>.onaliyun.com.
    -   If you have not set an enterprise alias, your account ID is used by default. In this case, the format of the **Domain Alias** is <$AccountID\>.onaliyun.com.

**Domain alias**

In addition to the default domain name, you can also set a domain alias for your account.

1.  Log on to the **RAM console**.
2.  Click **Identities** and choose **Settings** \> **Advanced** to view the domain alias.
3.  Click **Create Domain Alias**.
4.  Enter a domain name.
5.  Click **OK**.
6.  Click **Domain Ownership Verification**.

    **Note:** After the domain alias is created, copy the verification code and paste the DNS TXT record on the domain purchase platform. After the setting is completed, verify the domain ownership.


