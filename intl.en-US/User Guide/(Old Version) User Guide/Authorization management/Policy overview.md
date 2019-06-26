# Policy overview {#concept_tfz_4wf_xdb .concept}

You can manage access in Alibaba Cloud by creating policies and attaching them to RAM identities \(RAM users, RAM user groups, or RAM roles\) or Alibaba Cloud resources. A policy, when attached to an identity or resource, defines their permissions. Permissions in a policy determine whether the request of a RAM user or RAM role is allowed or denied.

## Permission {#section_ysq_rwf_xdb .section}

-   An Alibaba Cloud account \(the resource owner\) controls all permissions.
    -   Each resource has only one owner. The owner must be an Alibaba Cloud account and has full resource control permissions.
    -   The resource owner is not necessarily the resource creator. For example, if a RAM user has permission to create resources, the resources created by this RAM user belong to the Alibaba Cloud account of the RAM user. The RAM user is the resource creator, but is not the resource owner.
-   By default, a RAM user has no permissions.
    -   A RAM user is an operator and must be granted explicit permission before performing any operations.
    -   A new RAM user has no operation permissions by default, and cannot perform operations on resources through the console or APIs until being granted permission.
-   A resource creator \(RAM user\) is not automatically granted permissions for the created resources.
    -   A RAM user can create resources if the user is granted the resource creation permission.
    -   However, the RAM user is not automatically granted any permissions for the created resources, unless the resource owner explicitly grants permission to the user.

## Policy {#section_egs_pwf_xdb .section}

A policy is a set of permissions described in [Policy structure and grammar](reseller.en-US/User Guide/(Old Version) User Guide/Policy Language/Policy structure and grammar.md#). It can accurately describe the authorized resource sets, operation sets, and authorization conditions a user can be granted with. If a policy that applies to a request include an `Allow` statement and a `Deny` statement, the `Deny` statement trumps the `Allow` statement.

In RAM, a policy is an object that can be created, updated, deleted, and viewed by RAM users. RAM supports the following two types of policies:

-   System policy: A system policy is a group of common permissions provided by Alibaba Cloud. The permissions include read-only permissions and full permissions for different Alibaba Cloud services that are commonly used. System policies cannot be modified by users. The policies are automatically upgraded by Alibaba Cloud.
-   Custom policy: If no system policy meets your requirements, you can create a custom policy as needed. For example, if you want to control the operation permissions for a certain ECS instance or want the resource operation requests to come from specified IP addresses, you must use a custom policy.

## Grant permission to RAM identities {#section_ggs_pwf_xdb .section}

Granting permission to RAM identities is to attach one or more policies to RAM users, RAM user groups, or RAM roles.

-   The attached policy can be either a system policy or a custom policy.
-   If the attached policy is updated, the updates to the policy automatically take effect, and you do not need to attach the policy again.

