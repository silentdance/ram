# Permission and Authorization Policy {#concept_tfz_4wf_xdb .concept}

Alibaba Cloud uses permission to describe the ability of an operation subject \(such as user, user group, and RAM role\) to access a specific resource. Permission refers to allow or deny under certain conditions\) Perform certain actions on certain resources. The carrier of authority is Authorization Policy, and authorization policy is a collection of access rights.

This article provides an overview of the attributes associated with Alibaba Cloud permissions and authorization policies to help you understand and use them correctly.

## Permission {#section_ysq_rwf_xdb .section}

-   Master account \(resource owner\) controls all Permissions

    -   Each resource has only one owner \(resource owner\). The owner must be an Alibaba Cloud account. This account pays for and has full control permissions to this resource.
    -   The resource owner is not necessarily the resource creator. For example, a ram The user is granted permission to create a resource that belongs to the master account, the user is the creator of the resource, but not the resource owner.
-   Ram user \(operator\) does not have any permissions by default

    -   A RAM user represents an operator and must be explicitly authorized to perform any operation.
    -   A new RAM user has no operation permission by default, and cannot operate on resources in the console or by using APIs until the authorization is granted.
-   \#\#\#\# Resource creators \(RAM users\) are not automatically granted permissions for the resources they create

    -   If the ram user is granted permission to create a resource, the user can create a resource.
    -   However, the RAM user does not automatically have any permissions on the created resource, unless the resource owner has an explicit authorization on him.

## Authorization Policy {#section_egs_pwf_xdb .section}

Authorization Policy \(policy\) is used [Policy syntax structure](reseller.en-US/User Guide/Policy Language/Policy syntax structure.md) The set of permissions described, it can accurately describe authorized resource sets, Action sets, and authorization conditions. Follow deny first when there are both allow and deny authorization statements in the Authorization Policy The principle.

In RAM, an authorization policy is a type of resource entity. Users can create, update, delete, and view authorization policies. Ram supports the following two authorization policies:

-   System authorization policies are a group of general permission sets created and managed by Alibaba Cloud, such as read-only permission for ECS or full permissions for ECS. You can use these policies, but cannot modify them.
-   Custom authorization policies are policies created and managed by users. They can be used to expand and supplement system authorization policies.

System authorization policies describe coarse-grained permissions. If you require finer-grained authorization policies, such as policies that precisely control permissions for a certain ECS instance or that have additional authorization conditions, you must create custom authorization policies.

## Give Ram user authorization {#section_ggs_pwf_xdb .section}

Give the ram user authorization to bind one or more authorization policies to a user, user group, or role.

-   You can bind both system authorization policies and custom authorization policies.
-   If a bound authorization policy is updated, the updated policy automatically takes effect, and you do not have to rebind it.

