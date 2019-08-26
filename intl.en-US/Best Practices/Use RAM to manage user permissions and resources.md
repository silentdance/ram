# Use RAM to manage user permissions and resources {#concept_d2j_wdk_xdb .concept}

This topic describes how to use RAM to manage user permissions and resources.

## Scenario {#section_w1b_xdk_xdb .section}

Enterprise A has bought several types of Alibaba Cloud resources, such as ECS instances, RDS instances, SLB instances, and OSS buckets for a project. During this project, many employees need to perform operations on these cloud resources, but different employees require different permissions to complete different operations.

The requirements of Enterprise A are as follows:

-   Employees do not share the Alibaba Cloud account to avoid mistaken disclosure of the account password or AccessKey pair.
-   Independent RAM users are created for different employees and the RAM users are granted independent permissions.
-   All operations of all RAM users can be audited by Enterprise A.
-   The permissions of RAM users can be removed at any time, and users under an Alibaba Cloud account can be deleted by Enterprise A.
-   Fees are not charged to each RAM user, but are instead charged to the corresponding Alibaba Cloud account to which the RAM users belong.

## Solution {#section_abb_xdk_xdb .section}

![Solution](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23773/156680510514406_en-US.png)

-   Set multi-factor authentication \(MFA\) for you Alibaba Cloud account to avoid risks associated with mistaken disclosure of the password. For more information, see [Enable an MFA device for an Alibaba Cloud account](../../../../reseller.en-US/User Guide/Security settings/Multi-factor authentication/Enable an MFA device for an Alibaba Cloud account.md#).
-   Create RAM users for different employees \(or applications\) and set logon passwords or create AccessKey pairs. For more information, see [Create a RAM user](../../../../reseller.en-US/User Guide/RAM users/Create a RAM user.md#).
-   If multiple RAM users require the same permissions, we recommend that you create a user group and add the corresponding users to this group. For more information, see [Create a RAM user group](../../../../reseller.en-US/User Guide/RAM user groups/Create a RAM user group.md#).
-   Attach one or more system policies to the groups or users. For more information, see [Grant permission to a RAM user](../../../../reseller.en-US/User Guide/RAM users/Grant permission to a RAM user.md#) or [Grant permission to a RAM user group](../../../../reseller.en-US/User Guide/RAM user groups/Grant permission to a RAM user group.md#). For finer-grained permission management, you can create one or more custom policies and attach them to individual users or to a user group. For more information, see [Create a custom policy](../../../../reseller.en-US/User Guide/Policies/Custom policies/Create a custom policy.md#).
-   Remove permissions from groups or RAM users when they no longer need the permissions. For more information, see [Remove permission from a RAM user](../../../../reseller.en-US/User Guide/RAM users/Remove permission from a RAM user.md#) or [Remove permission from a RAM user group](../../../../reseller.en-US/User Guide/RAM user groups/Remove permission from a RAM user group.md#).

