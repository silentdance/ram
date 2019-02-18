# Use RAM to maintain security of your cloud-based services {#concept_ezq_5bp_kgb .concept}

This topic describes how to use RAM to apply access and security settings to your cloud-based resources so that you can better manage access permissions with fine-grained access controls.

## Scenario {#section_pqk_vdp_kgb .section}

When you migrate your business resources to the cloud, the traditional organizational structures and previous management methods of your resources may no longer meet your requirements. As a result, the migration of your services may create higher security management issues as follows:

-   The responsibilities of the RAM users are not clear.
-   The account owner does not want to share the account AccessKey with RAM users due to security risks involved.
-   RAM users can access resources using different methods, which is not unified and may mistakenly cause security risks.
-   The resource access permissions of RAM users need to be frequently recalled when the users no longer require these permissions.

## Solution {#section_n4z_klp_kgb .section}

To resolve the preceding issues, you can use RAM to create RAM users and apply resource access permissions to them. Specifically, you can use RAM to separate the account AccessKey from RAM users and grant minimum permissions to users as needed to ensure that the security of your resources is maintained.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/97386/155048009337013_en-US.png)

## Security management solution {#section_gyq_2ny_pgb .section}

-   **Create independent RAM users.**

    An enterprise needs only one account \(that is, an Alibaba Cloud account\). As a best practice, the account should not be used for daily tasks. However, multiple RAM users can be created for different users under the account, and they can be granted the necessary access permissions to resources as needed.

    For more information, see [Create a RAM user](../../../../../reseller.en-US/Quick Start/Create a RAM user.md#).

-   **Separate console users from API users.**

    We recommend that you do not create a logon password for console operations and an AccessKey for API operations for a RAM user at the same time.

    -   To allow an application to access cloud resources only through open APIs, you only need to create an AccessKey for the application.
    -   To allow an employee to operate on cloud resources only through the console, you only need to set a logon password for the employee.
    For more information, see [Create a RAM user](../../../../../reseller.en-US/Quick Start/Create a RAM user.md#).

-   **Create RAM users and group them.**

    If your account has multiple RAM users, you can group RAM users with same responsibilities and grant permissions to the group as needed.

    For more information, see [\(Optional\) Create a RAM user group](../../../../../reseller.en-US/Quick Start/(Optional) Create a RAM user group.md#).

-   **Grant the minimum permissions to different RAM user groups.**

    You can attach proper system policies to RAM users or user groups as needed. You can also create custom policies for fine-grained permission management. In this way, by granting the minimum permissions to different RAM users and user groups, you can better manage the RAM users' operations on the cloud resources.

    For more information, see [Policy management](../../../../../reseller.en-US/User Guide/Permission management/Policy management.md#).

-   **Configure strong password policies.**

    You can configure password policies with custom conventions regarding the minimum length, mandatory characters, and validation period, for RAM users in the RAM console. If a RAM user is allowed to change their logon password, the user must create a strong logon password and rotate the password or AccessKey on a regular basis.

    For more information, see [Set up initial RAM configurations](../../../../../reseller.en-US/Quick Start/Set up initial RAM configurations.md#).

-   **Enable MFA for your account.**

    You can enable multi-factor authentication \(MFA\) for your account to enhance the account security. After MFA is enabled, the system asks the RAM user logging on to Alibaba Cloud to enter the following two security factors:

    -   First security factor: account name and password
    -   Second security factor: a variable verification code from the virtual MFA device
    For more information, see [\(Optional\) Set MFA](../../../../../reseller.en-US/Quick Start/(Optional) Set MFA.md#).

-   **Enable SSO for RAM users.**

    After Single Sign-On \(SSO\) is enabled, all the internal accounts of your enterprise will be authenticated. Then, users can log on to Alibaba Cloud to access corresponding resources only by using an internal account.

    For more information, see [Configure the SAML of an account](../../../../../reseller.en-US/User Guide/Identity management/Identity federation management/Configure the SAML of an account.md#).

-   **Do not share the AccessKey of your account.**

    Your account has full control permissions over resources under it, and its AccessKeys have the same permissions as logon passwords. However, AccessKeys are used for programmatic access whereas logon passwords are used to log on to the console. Therefore, to avoid information leaks due to misuse of an AccessKey, we recommend that you do not share or use the AccessKey of your account. Instead, create a RAM user and grant this user the relevant permissions.

    For more information, see [Manage AccessKeys](../../../../../reseller.en-US/User Guide/Identity management/User management/Users.md#ol_ik1_pzh_4fb).

-   **Specify operation conditions to enhance security.**

    You can specify the operational conditions that a RAM user must meet before they can use your cloud resources. For example, you can specify that the RAM user must use a secure channel \(such as SSL\), use a specified source IP address, or operate within a specified period of time.

    For more information, see [Elements](../../../../../reseller.en-US/User Guide/Permission management/Policy language/Elements.md#).

-   **Manage permissions of your cloud resources.**

    By default, all your resources are under your account. A RAM user can use the resources but do not own the resources. This allows you to easily manage the instances or data created by RAM users.

    -   For an existing RAM user that you no long require, you can remove all of its corresponding permissions by simply removing the RAM user account.
    -   For a RAM user that requires a permission, you need to first create the RAM user, set the logon password or AccessKey for it, and then grant the RAM user the relevant permissions as needed.
    For more information, see [Authorize RAM users](../../../../../reseller.en-US/Quick Start/Authorize RAM users.md#).

-   **Use STS to grant temporary permissions to RAM users.**

    The Security Token Service \(STS\) is an extended authorization service of RAM. You can use STS to grant temporary permissions to RAM users and specify the permission and automatic expiration time of the tokens as needed.

    For more information, see [../../../../../dita-oss-bucket/SP\_65/DNRAM19100116/EN-US\_TP\_12547.md\#](../../../../../reseller.en-US/FAQ/STS FAQ.md#).


## Result {#section_ybx_ssy_pgb .section}

After migrating your services to the cloud, you can use the preceding solutions to ensure you manage your cloud-based resources effectively and keep your account and all business assets secure.

## What to do next {#section_v52_q2f_qgb .section}

You can use RAM to categorize your O&M requirements and assign tasks to different engineers as needed. For more information, see [Manage permissions of different O&M engineers by using RAM](reseller.en-US/Best Practices/Manage permissions of different O&M engineers by using RAM.md#).

