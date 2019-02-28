# RAM user groups {#concept_hb3_nsf_xdb .concept}

If you have created multiple RAM users under your account, you can create user groups to classify and organize these RAM users for easier user and permission management.

## Advantages {#section_cf2_r2k_pgb .section}

Adding RAM users to user groups will bring the following benefits:

-   If the responsibilities of a user change, you only need to move the user to a RAM user group with the appropriate permissions. This action does not affect other RAM users.
-   If the responsibilities of a user group change, you only need to modify the policy attached to the RAM user group. Changes to the policy apply to all RAM users in the group.

## Before creating a RAM user group {#section_gpb_j43_pgb .section}

Log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram).

## Create a RAM user group {#section_01 .section}

1.  In the **RAM console**, click **Identities** and choose **Groups** \> **Create Group**.
2.  Enter the **Group Name**, **Display Name**, and **Note**, and click **OK**.

## Manage group members {#section_02 .section}

1.  In the **RAM console**, click **Groups**. Then, locate the target group and click the group name.

    **Note:** Fuzzy search is supported for user group names.

2.  Click the **Group Members** tab to manage group members.
    -   To add a group member, click **Add Group Members**, select the target user \(or enter keywords to search for a specific user\), and click **Ok**.

        **Note:** You can click "X" to clear your selection.

    -   To remove a member from a group, select the target user, and click **Remove from Group**.

## Rename a user group {#section_03 .section}

1.  In the **RAM console**, click **Groups**. Then, locate the target group and click the group name.

    **Note:** Fuzzy search is supported for user group names.

2.  Click **Modify Basic Information**.
3.  Enter the **Display Name** and click **OK**.

## Delete a user group {#section_04 .section}

1.  In the **RAM console**, click **Groups** and locate the target group.

    **Note:** Fuzzy search is supported for user group names.

2.  Click **Delete**.
3.  In the displayed **Delete Group** dialog box, click **OK**.

    **Note:** If the group contains any members or is attached to any policies, these members and policies will be removed from the group.


## What to do next {#section_05 .section}

For more information about how to grant permissions to a group, see [Permission granting in RAM](reseller.en-US/User Guide/Permission management/Permission granting/Permission granting in RAM.md#).

