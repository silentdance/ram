# User management and access control {#concept_d2j_wdk_xdb .concept}

This topic provides an example scenario that describes how to use Alibaba Cloud RAM to manage user permissions and resources.

## Scenario {#section_w1b_xdk_xdb .section}

Assume that Enterprise A has bought several types of Alibaba Cloud resources, such as ECS instances, RDS instances, SLB instances, and OSS buckets, for Project-X. In this project, multiple employees need to perform operations on these cloud resources. Specifically, different employees require different permissions to complete different operations.

## Requirement analysis {#section_y1b_xdk_xdb .section}

-   Employees do not share the Alibaba Cloud account to avoid mistaken disclosure of the account password or AccessKey.
-   Independent RAM users are created for different employees and the RAM users are granted independent permissions.
-   All operations of all RAM users can be audited.
-   Fees are not charged to each RAM user, but are instead charged to the corresponding Alibaba Cloud account to which the RAM users belong.

## Solution {#section_abb_xdk_xdb .section}

![Solution](images/14406_en-US.png "Solution")

1.  Set multi-factor authentication \(MFA\) to avoid risks associated with mistaken disclosure of the Alibaba Cloud account password. For more information, see [\(Optional\) Set MFA](../../../../../reseller.en-US/Quick Start/(Optional) Set MFA.md#).
2.  Create RAM users for different employees \(or applications\) and set logon passwords or create AccessKeys. For more information, see [Create a RAM user](../../../../../reseller.en-US/Quick Start/Create a RAM user.md#).
3.  If multiple RAM users require the same permissions, we recommend that you create a user group and add the corresponding users to this user group. For more information, see [\(Optional\) Create a RAM user group](../../../../../reseller.en-US/Quick Start/(Optional) Create a RAM user group.md#).
4.  Attach one or more system policies to the groups or users. For more information, see [Permission granting in RAM](reseller.en-US/User Guide/Permission management/Permission granting/Permission granting in RAM.md#). For finer-grained permission management, you can create one or more custom policies and attach them to individual users or to a user group. For more information, see [Create a custom policy](reseller.en-US/User Guide/Permission management/Policy management.md#section_qpw_vwf_xdb).

