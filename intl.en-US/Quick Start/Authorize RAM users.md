# Authorize RAM users {#concept_t13_3gf_xdb .concept}

You can apply policies to authorize individual RAM users directly or authorize entire RAM user groups as needed. Both methods can grant RAM users the resource access permission.

## Policy types {#section_ndn_kgf_xdb .section}

System policies are a group of common policies that meet coarse-grained authorization requirements. For example, you can use system policies to authorize a RAM user to manage orders \(through the AliyunBSSFullAccess policy\), ECS resources \(through the AliyunECSFullAccess policy\), or all users and their permissions \(through the AliyunRAMFullAccess policy\).

You can view all system policies supported by RAM in [Policy overview](../../../../../reseller.en-US/User Guide/Permission management/Policy overview.md#).

If you require finer-grained authorization, you can create a custom policy as needed. For more information, see [\(Optional\) Create a custom policy](reseller.en-US/Quick Start/(Optional) Create a custom policy.md).

## Authorize RAM users directly {#section_odn_kgf_xdb .section}

Call the `AttachPolicyToUser` API to authorize RAM users directly.

1.  Log on to the [RAM Console](https://partners-intl.console.aliyun.com/#/ram).
2.  Choose **Identities** \> **Users**.
3.  In the **User Logon Name/Display Name** column, select the target user and click **Add Permissions**.
4.  In the **Policy Name** column on the left, select the target policies and click **OK**.

    **Note:** To remove a policy, select the policy from the area on the right, and then click ×.


## Authorize RAM users by authorizing their user groups {#section_tdn_kgf_xdb .section}

Call the `AttachPolicyToGroup` API to authorize a user group.

**Note:** The user to be authorized must be included in the target user group.

1.  Log on to the [RAM Console](https://partners-intl.console.aliyun.com/#/ram).
2.  Choose **Identities** \> **Groups**.
3.  In the **Group Name/Display Name** column, select the target group and click **Add Permissions**.
4.  In the **Policy Name** column on the left, select the target policies and click **OK**.

    **Note:** To remove a policy, select the policy from the area on the right, and then click ×.


## What to do next {#section_c3y_vnj_pfb .section}

-   In the **User Logon Name/Display Name** column, click a user logon name. On the displayed **Permissions** tab page, you can navigate to the **Individual** tab page to view or revoke a permission granted directly to the user.
-   In the **Group Name/Display Name** column, click a group name. On the displayed **Permissions** tab page, you can view or revoke a permission granted to the group.

