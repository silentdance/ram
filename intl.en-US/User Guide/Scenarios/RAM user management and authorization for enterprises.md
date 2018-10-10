# RAM user management and authorization for enterprises {#concept_d2j_wdk_xdb .concept}

## Scenario description {#section_w1b_xdk_xdb .section}

Assume that enterprise A buys several types of cloud resources, such as ECS instances, RDS instances, SLB instances, and OSS buckets. Employees at enterprise A need to perform operations on these resources, such as procurement, O&amp;M, or online application. Because different employees have different responsibilities, they require different permissions.

-   For security reasons, the Alibaba Cloud account owner of enterprise A does not want to disclose its account AccessKey to its employees. Rather, the account owner prefers to create different RAM user accounts for their employees and associate each RAM user account with different permissions.
-   Then, the employees can perform resource operations only under their permissions with their RAM user accounts and charges are not billed to these accounts. All expenses are charged to the account owner.
-   The account owner can also revoke the permissions of a RAM user account at any time, and delete the user.

## Requirement analysis {#section_y1b_xdk_xdb .section}

Different scenarios have different requirements:

-   Employees do not share the primary account to avoid uncontrollable risks caused by the disclosure of the account’s password or AccessKey.
-   Different employees are allocated independent user accounts \(or operator accounts\) with independent permissions, so that their responsibilities are consistent with their permissions.
-   All the operations of all user accounts can be audited.
-   Charges are not calculated for each operator; the primary account is billed for all fees incurred.

## Solution {#section_abb_xdk_xdb .section}

Use RAM-user accounts and the authorization management function, as shown in the following figure:

![](images/3629_en-US.png "Solution for the enterprise scenario")

The operation procedure is as follows:

1.  [Set up MFA](../../../../intl.en-US/Quick Start/Set up MFA (optional).md) to prevent risks caused by disclosure of the password of the primary account.
2.  Activate RAM.
3.  [Create RAM users](../../../../intl.en-US/Quick Start/Create a RAM user.md) for different employees \(or application systems\) and set logon passwords or create AccessKeys for them as needed.
4.  [Create a RAM user group](../../../../intl.en-US/Quick Start/Create a RAM user group (optional).md). If multiple employees share the same responsibility, we recommend that you create a group for them and add the users to the group.
5.  [Grant permissions](https://www.alibabacloud.com/help/doc-detail/28653.htm). Attach one or more authorization policies to groups or users. For finer-grained authorization, you can create [custom authorization policies](intl.en-US/User Guide/Authorization/Authorization Policy Management.md) and then attach them to groups or users.

