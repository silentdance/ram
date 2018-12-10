# User groups {#concept_hb3_nsf_xdb .concept}

If you have created multiple RAM users under your account, you can create user groups to classify and organize these RAM users for easier user and permission management.

Adding RAM users to user groups means that:

-   When the responsibilities of a user change, you only need to move this user to a group that has the appropriate permissions. Other RAM users are not affected.
-   When the responsibilities of a user group change, you only need to modify the policy attached to the group, and all changes to the policy apply to all RAM users in the group.

## Create a user group {#section_01 .section}

1.  In the [RAM console](https://partners-intl.console.aliyun.com/#/ram), click **Identities** \> **Groups** \> **Create Group**.
2.  Enter a group name, a display name, and a note for the group and click **OK**.

## Manage group members {#section_02 .section}

1.  In the **RAM console**, click **Groups**. Then, locate the target group and click the group name.

    **Note:** Fuzzy search is supported for user group names.

2.  Click the **Group Members** tab to manage group members.
    -   Add group members: Click **Add Group Members**. On the displayed **Add Group Members** page, select the users you want to add to the group \(or enter keywords to search\) from the left column, and then click **OK**.

        **Note:** You can click "×" to clear your selection.

    -   Remove group members: To remove a member from a group, find the user that you want to remove and click **Remove from Group**.

## Rename a user group {#section_03 .section}

1.  In the **RAM console**, click **Groups**. Then, locate the group that you want to rename and click the group name.

    **Note:** Fuzzy search is supported for user group names.

2.  Click **Modify Basic Information**.
3.  Enter a display name and click **OK**.

## Delete a user group {#section_04 .section}

1.  In the **RAM console**, click **Groups** and locate the group that you want to delete.

    **Note:** Fuzzy search is supported for user group names.

2.  Click **Delete**.
3.  In the displayed **Delete Group** dialog box, click **OK**.

    **Note:** If the group contains any members or is attached to any policies, these members and policies will be removed from the group.


## Grant permissions to a user group {#section_05 .section}

For more information about how to grant permissions to a group, see [Permission granting in RAM](reseller.en-US/User Guide/Permission management/Permission granting/Permission granting in RAM.md#).

