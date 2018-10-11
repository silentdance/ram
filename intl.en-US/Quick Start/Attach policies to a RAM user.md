# Attach policies to a RAM user {#concept_t13_3gf_xdb .concept}

There are two methods for authorizing a RAM user:

-   \#[Attach policies to a RAM user directly](#section_odn_kgf_xdb)
-   \#[Attach policies to a RAM user group](#section_tdn_kgf_xdb)

Both of these methods can achieve the purpose of granting a RAM user the permission for accessing related resources.

## Background {#section_ndn_kgf_xdb .section}

System authorization policies are a group of general authorization policies that meet coarse-granularity authorization requirements. For example, you can use them to authorize a RAM user to manage orders \(AliyunBSSFullAccess\), ECS resources \(AliyunECSFullAccess\), or all sub-users and their permissions \(AliyunRAMFullAccess\).

You can view all the system authorization policies that are supported by RAM in [Authorization Policy Management](../../../../intl.en-US/User Guide/Authorization/Authorization Policy Management.md).

If none of these authorization policies meet your needs, you can customize a finer-granularity authorization policy. For details, see [Create a custom policy \(optional\)](intl.en-US/Quick Start/Create a custom policy (optional).md).

## Attach policies to a RAM user directly {#section_odn_kgf_xdb .section}

Use AttachPolicyToUser to attach policies to a RAM user directly.

**Operation procedure:**

1.  Click **Users** in the left navigation pane of the RAM console.
2.  On the **User Management** page, click **Authorize** next to the user \(which can be searched by user name\) to whom you want to grant permissions.
3.  In the **Edit User-Level Authorization** dialog box, add an authorization policy \(which can be searched by keyword\) and click **OK**.
    -   Select the policy you want from the **Available Authorization Policy Names** list on the left, and click the right arrow to add it to the **Selected Authorization Policy Name** list.
    -   To deselect an authorization policy, select the policy, and click the left arrow to remove it from the **Selected Authorization Policy Name** list.

## Attach policies to a RAM user group {#section_tdn_kgf_xdb .section}

Use AttachPolicyToGroup to attach policies to a RAM user group.

Before using this method, make sure that the authorized user is already in the user group that you want to authorize.

**Operation procedure:**

1.  Click **Groups** in the left navigation pane of the RAM console.
2.  On the **Group Management** page, click **Authorize** next to the group to whom you want to grant permissions.
3.  In the **Edit Group Authorization Policy** dialog box, add an authorization policy \(which can be searched by keyword\) and click **OK**.

**Subsequent operation**

-   If policies are attached to a RAM user directly, you can go to the **User-Level Authorization** sub-page of the **User Authorization Polices** page to **View Permissions** or **Revoke Authorization**.
-   If policies are attached to a RAM user group, you can go to **Group Authorization Polices** page to **View Permissions** or **Revoke Authorization**.

