# Perform RAM operations {#concept_ckb_5kk_xdb .concept}

This topic provides RAM operation suggestions from the following aspects: logon verification, account authorization, and permission granting. These suggestions help you effectively use RAM to manage user identities and control resource access.

## Logon verification {#section_xj3_sjk_xdb .section}

**Enable MFA for accounts and RAM user accounts**

-   We recommend that you enable multi-factor authentication \(MFA\) for your account so that MFA is performed each time the account is used.
-   If you have created a RAM user and granted high-risk permissions to the user \(such as stopping instances and deleting buckets\), we recommend that you enable MFA for the user.

**Configure strong password policies for user logon**

-   If you allow a RAM user to change its logon password, the user must create a strong logon password and change the password on a regular basis.
-   You can create password policies from the perspectives of the minimum length, mandatory elements, and validation period, for RAM users in the RAM console.

**Periodically change logon passwords and AccessKeys for users**

-   We recommend that you or RAM users periodically change logon passwords or AccessKeys \(AKs\). If a credential is disclosed without your knowledge, the validity of the credential will be restricted.
-   You can set a password policy to force RAM users to periodically change their logon passwords or AKs.

## Account authorization {#section_g2x_5jk_xdb .section}

**Follow the minimum authorization principle**

The minimum authorization principle is the primary principle for security design. When you need to [authorize RAM users](../../../../reseller.en-US/Quick Start/(Old Version) Quick Start/Authorize RAM users.md), grant the user only the permissions that are required for work.

For example, in your organization, if a developer group \(or an application system\) only requires reading data from OSS buckets, you only need to grant the group \(or the application system\) the read-only permission. All permissions for OSS resources, or the permission to access resources of all products cannot be granted to the group \(or the application system\).

**Enhance security with policy restrictions**

To enhance security, we recommend that you set policy restrictions when you grant permissions to a user.

For example, you grant a user the permission to stop ECS instances with the restriction that the user stops instances at a specified time through the company network.

**Revoke permissions that are no longer needed**

When a user's responsibility changes and the granted permissions are no longer necessary, you need to revoke the permissions. This helps minimize any security risk caused by possible disclosure of the user access credential.

For details about how to revoke permissions, see [Authorize RAM users](../../../../reseller.en-US/Quick Start/(Old Version) Quick Start/Authorize RAM users.md).

## Permission granting {#section_eyl_3kk_xdb .section}

**Avoid creating an AK for your account**

Your account has full permissions for all resources under it. To prevent loss caused by possible AK disclosure, we recommend that you do not create an AK for your account but use a private key during daily work.

**Grant permissions to RAM users by granting the users' group**

To authorize a RAM user, you can directly authorize the user. Alternatively, it is more convenient for you to create a group \(such as admin, developer, and accounting groups\) related to the role and responsibilities of the user, grant appropriate permissions to the group, and then add the user to the group. All users in the group share the same permissions.

-   You can modify the permissions of all users in the group with one operation.
-   When a user is transferred in your organization, you only need to change the group to which the user belongs.

**Manage users, permissions, and resources separately**

When using RAM, you need to create different RAM users responsible for managing RAM users, permissions, and resource operations on various products. A secure authority-based management system supports checks and balances to minimize security risks.

**Separate console users from API users**

We recommend that you do not create a logon password for console operations and an AK for API operations for a RAM user at the same time. We recommend that you create only logon passwords for employees and create only AKs for systems and applications.

