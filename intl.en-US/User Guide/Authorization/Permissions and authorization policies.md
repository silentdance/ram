# Permissions and authorization policies {#concept_tfz_4wf_xdb .concept}

Alibaba Cloud uses permissions to describe the ability of internal identities \(such as users, user groups, roles\) to access specific resources. Permission refers to **allowing** or **denying** to perform certain operations on certain resources under certain conditions. An authorization policy is a collection of access permissions.

This document describes the relationships between Alibaba Cloud permissions and authorization policies, to help you understand and use them correctly.

## Permissions {#section_ysq_rwf_xdb .section}

-   The primary account \(resource owner\) controls all permissions.

    -   Each resource has one and only one owner \(resource owner\). The owner must be an Alibaba Cloud account. This account pays for and has full control over the resource.
    -   The resource owner is not necessarily the resource creator. For example, a RAM user is granted permission to create a resource. The resource belongs to the primary account. This user is the resource creator but not the resource owner.
-   A RAM user \(operator\) does not have any permissions by default.

    -   A RAM user represents an operator and must be explicitly authorized to perform any operation.
    -   A new RAM user has no operation permission by default, and cannot operate on resources in the console or by using APIs until the authorization is granted.
-   Resource creators \(RAM users\) are not automatically granted permissions for the resources they have created.

    -   If a RAM user is granted permission to create a resource, the user will be allowed to create the resource.
    -   However, the RAM user does not automatically have any permissions for the created resource, unless the resource owner has an explicit authorization on him.

## Authorization policies {#section_egs_pwf_xdb .section}

An authorization policy is a set of permissions described by [Policy syntax structure](intl.en-US/User Guide/Policy Language/Policy syntax structure.md) that accurately describes the set of authorized resources, the set of operations, and the authorization conditions. The **deny first** principle is followed when there are both allow and deny authorization statements in an authorization policy.

In RAM, an authorization policy is a type of resource entity. Users can create, update, delete, and view authorization policies. RAM supports the following two authorization policies:

-   **System authorization policies** are a group of general permissions created and managed by Alibaba Cloud, such as read-only permission for ECS or full permissions for ECS. You can use these policies, but cannot modify them.
-   **Custom authorization policies** are a group of permissions created and managed by users. They can be used to expand and supplement system authorization policies.

System authorization policies describe coarse-grained permissions. If you require finer-grained authorization policies, such as policies that precisely control permissions for a certain ECS instance or that have additional authorization conditions, you must create custom authorization policies.

## Authorization to a RAM user {#section_ggs_pwf_xdb .section}

Authorization to a RAM user refers to binding one or more authorization policies to a user, user group, or role.

-   The bound authorization policy can be either a system authorization policy or a custom authorization policy.
-   If a bound authorization policy is updated, the updated policy automatically takes effect, and you do not have to rebind it.

