# RAM best practices {#concept_ckb_5kk_xdb .concept}

This document introduces some best practices of using RAM from the following aspects: **logon verification**, **account authorization**, and **permission assignment**. These suggestions help you make full use of RAM to deploy a secure and controllable environment.

## Logon verification {#section_xj3_sjk_xdb .section}

**Enable account protection for the root account and RAM users**

-   We recommend that you enable multi-factor authentication \(MFA\) for your root account so that MFA is performed each time the root account is used.
-   If you have created a RAM user and granted high-risk permissions to the user \(such as stopping instances and deleting buckets\), you are advised to enable MFA for the RAM user.

**Configure strong password policies for user logon**

-   If you allow a RAM user to change his or her logon password, you should require the user to create a strong logon password and encourage frequent password rotation.
-   You can create password policies, such as the minimum length, whether non-letter characters are required, and the rotation cycle, for RAM users on the RAM console.

**Rotate logon passwords and AccessKeys of users**

-   We recommend that you or the RAM users regularly rotate logon passwords or AccessKeys. If a credential is disclosed without your knowledge, the validity of the credential is restricted.
-   You can set a password policy to force the RAM users to rotate their logon passwords or AccessKeys in a regular cycle.

## Account authorization {#section_g2x_5jk_xdb .section}

**Adhere to the minimum authorization rule**

The minimum authorization rule is a primary rule for security design. When you need to [Attach policies to a RAM user](../../../../reseller.en-US/Quick Start/Attach policies to a RAM user.md), grant the user only the permissions that are required for his work.

For example, in your organization, if the responsibilities of the developers group \(or an application system\) only require reading data stored in the OSS buckets, grant the group \(or the application system\) read-only permission. All permissions for OSS resources, or the permission to access resources of all products are not required.

**Enhance security with policy conditions**

We recommend that you set policy conditions when you grant permissions to a user to enhance the security.

For example, you grant a user the permission to stop ECS instances with the condition that the user enacts the stop at a specified time on the company network.

**Revoke permissions that are no longer needed**

When a user’s role changes and the assigned permission is no longer necessary, you need to revoke the permission. See [Attach policies to a RAM user](../../../../reseller.en-US/Quick Start/Attach policies to a RAM user.md) for the **subsequent operation**.

This can help minimize any security risk caused by disclosure of the access credential of the user without your knowledge.

## Permission assignment {#section_eyl_3kk_xdb .section}

**Avoid creating an AccessKey for the root account**

We recommend that you do not create an AccessKey for the root account, as the root account has full permissions for all resources under it.

**Grant permissions to RAM users through groups**

Normally, you do not need to [Attach policies to a RAM user](../../../../reseller.en-US/Quick Start/Attach policies to a RAM user.md). It is more convenient to create a group \(such as admin, developer, and accounting groups\) related to the role and responsibilities of the user. Attach an appropriate authorization policy to the group, and then add users to the group. All users in a group share the same permissions.

Therefore, you can modify the permissions of all users in the group with one operation. When a user is transferred in your organization, you only need to change the group to which the user belongs.

**Separate user management, permission management and resource management**

When using RAM, create separate RAM users responsible for RAM user management, RAM permission management, and the management of resource operations under various products. A secure authority-based management system supports checks and balances to minimize security risks.

**Separate console users from API users**

It is not recommended that you create both a logon password for console operations and an AccessKey for API operations for one RAM user. We recommend that you create only logon passwords for employees and create only AccessKeys for systems and applications.

