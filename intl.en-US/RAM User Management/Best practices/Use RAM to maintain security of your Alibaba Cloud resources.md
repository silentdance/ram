# Use RAM to maintain security of your Alibaba Cloud resources {#concept_ezq_5bp_kgb .concept}

This topic describes how to use RAM to apply access and security settings to your Alibaba Cloud resources so that you can better manage access permissions with fine-grained access control.

## Prerequisites {#section_ug8_z0q_5pv .section}

An Alibaba Cloud account is created. If not, create one before proceeding.

## Scenario {#section_pqk_vdp_kgb .section}

When you migrate your business resources to the cloud, the traditional organizational structures and previous management methods of your resources may no longer meet your requirements. As a result, the migration of your resources may create higher security management issues as follows:

-   The responsibilities of the RAM users are not clear.
-   The Alibaba Cloud account owner does not want to share the access key with RAM users due to security risks involved.
-   RAM users can access resources by using different methods, which is not unified and may mistakenly cause security risks.
-   The resource access permissions of RAM users need to be frequently recalled when the users no longer require these permissions.

## Solution {#section_n4z_klp_kgb .section}

To resolve the preceding issues, you can use RAM to create RAM users and grant resource access permissions to RAM users. Specifically, you can use RAM to separate the access key of your Alibaba Cloud account from RAM users and grant minimum permissions to users as needed to maintain the security of your resources.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/97386/156870340237013_en-US.png)

## Security management solution {#section_gyq_2ny_pgb .section}

-   Create independent RAM users.

    An enterprise needs only one Alibaba Cloud account. As a best practice, the Alibaba Cloud account is not used for daily tasks. However, multiple RAM users can be created under the account, and granted the necessary access permissions to resources as needed.

    For more information, see [Create a RAM user](../../../../reseller.en-US/RAM User Management/Create a RAM user.md#).

-   Separate console users from API users.

    We recommend that you do not create a logon password for console operations and an access key for API operations for a RAM user at the same time.

    -   To allow an application to access cloud resources only through APIs, you only need to create an access key for the application.
    -   To allow an employee to operate on cloud resources only through the console, you only need to set a logon password for the employee.
    For more information, see [Create a RAM user](../../../../reseller.en-US/RAM User Management/Create a RAM user.md#).

-   Create RAM users and group them.

    If your Alibaba Cloud account has multiple RAM users, you can group RAM users with same responsibilities and grant permissions to the group as needed.

    For more information, see [Create a RAM user group](../../../../reseller.en-US/RAM User Group Management/Create a RAM user group.md#).

-   Grant the minimum permissions to different RAM user groups.

    You can attach proper system policies to RAM users or user groups as needed. You can also create custom policies for fine-grained permission management. In this way, by granting the minimum permissions to different RAM users and user groups, you can better manage the RAM users' operations on the cloud resources.

    For more information, see [Create a custom policy](../../../../reseller.en-US/Policy Management/Custom policies/Create a custom policy.md#).

-   Configure strong password policies.

    You can configure password policies with custom conventions regarding the minimum length, mandatory characters, and validation period, for RAM users in the RAM console. If a RAM user is allowed to change their logon password, the user must create a strong logon password and rotate the password or access key on a regular basis.

    For more information, see [Set a security policy for RAM users](../../../../reseller.en-US/Security Settings/Basic security settings/Set a security policy for RAM users.md#).

-   Enable an MFA device for your Alibaba Cloud account.

    You can enable a multi-factor authentication \(MFA\) device for your Alibaba Cloud account to enhance the account security. When you log on to Alibaba Cloud with MFA enabled, the system requires the following two security factors:

    1.  Your username and password
    2.  Verification code provided by the MFA device
    For more information, see [Enable an MFA device for an Alibaba Cloud account](../../../../reseller.en-US/Security Settings/Multi-factor authentication/Enable an MFA device for an Alibaba Cloud account.md#).

-   Do not share the access key of your Alibaba Cloud account.

    Your Alibaba Cloud account has full control permissions over resources under it, and its access keys have the same permissions as logon passwords. However, access keys are used for programmatic access whereas logon passwords are used to log on to the console. Therefore, to avoid information leaks due to misuse of an access key, we recommend that you do not share or use the access key of your Alibaba Cloud account.

    Instead, create a RAM user and grant this user the relevant permissions.

    For more information, see [Create an access key for a RAM user](../../../../reseller.en-US/Security Settings/Access keys/Create an access key for a RAM user.md#).

-   Specify operation conditions to enhance security.

    You can specify the operational conditions that a RAM user must meet before they can use your cloud resources. For example, you can specify that the RAM user must use a secure channel \(such as SSL\), use a specified source IP address, or operate within a specified period of time.

    For more information, see [Policy elements](../../../../reseller.en-US/Policy Management/Policy language/Policy elements.md#).

-   Manage permissions of your cloud resources.

    By default, all your resources are under your Alibaba Cloud account. A RAM user can use the resources but do not own the resources. This allows you to easily manage the instances or data created by RAM users.

    -   For an existing RAM user that you no long require, you can remove all of its corresponding permissions by simply removing the RAM user account.
    -   For a RAM user that requires a permission, you need to first create the RAM user, set the logon password or access key for it, and then grant the RAM user the relevant permissions as needed.
    For more information, see [Grant permission to a RAM user](../../../../reseller.en-US/RAM User Management/Grant permission to a RAM user.md#).

-   Use STS to grant temporary permissions to RAM users.

    The Security Token Service \(STS\) is an extended authorization service of RAM. You can use STS to grant temporary permissions to RAM users and specify the permission and automatic expiration time of the tokens as needed.

    For more information, see [What is STS?](../../../../reseller.en-US/API Reference (STS)/What is STS?.md#)


## Result {#section_ybx_ssy_pgb .section}

After migrating your services to the cloud, you can use the preceding solutions to ensure you manage your cloud-based resources effectively and keep your Alibaba Cloud account and all business assets secure.

## What to do next {#section_v52_q2f_qgb .section}

You can use RAM to categorize your O&M requirements and assign tasks to different engineers as needed. For more information, see [Use RAM to manage permissions of O&M engineers](reseller.en-US/Tutorials/Use RAM to manage permissions of O&M engineers.md#).

