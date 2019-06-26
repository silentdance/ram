# RAM user groups {#concept_hb3_nsf_xdb .concept}

If you have created multiple RAM users under your Alibaba Cloud account, you can create RAM user groups to classify and organize these RAM users for easier user and permission management.

## Advantages {#section_cf2_r2k_pgb .section}

Adding RAM users to user groups will bring the following benefits:

-   If the responsibilities of a RAM user change, you only need to move the user to a RAM user group with the appropriate permissions. This action does not affect other RAM users.
-   If the responsibilities of a RAM user group change, you only need to modify the policy attached to the user group. Changes to the policy apply to all RAM users in the group.

## Create a RAM user group {#section_d2c_4sf_xdb .section}

1.  Log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram).
2.  In the left-side navigation pane, click **Groups**.
3.  In the upper-right corner of the displayed page, click **Create Group**.
4.  Enter the group name and description.
5.  Click **OK**.

## Manage group members {#section_f2c_4sf_xdb .section}

1.  In the left-side navigation pane of the RAM console, click **Groups**.
2.  In the **Group Name** column, locate the target RAM user group.

    **Note:** You can also enter keywords to search for a specific RAM user group.

3.  In the **Actions** column, click **Management** to manage group members.
    -   To add a group member, click **Edit Group Member**, select the target RAM user \(or enter keywords to search for a specific RAM user\), click the rightwards arrow, and then click **OK**.

        **Note:** You can click the leftwards arrow in the right-side area to remove a RAM user.

    -   To delete a group member, select the target RAM user from the **Member Name** column, click **Remove from Group**, and then click **OK**.

## Rename a RAM user group {#section_k2c_4sf_xdb .section}

1.  In the left-side navigation pane of the RAM console, click **Groups**.
2.  In the **Group Name** column, click the name of the target RAM user group.
3.  In the **Basic Information** section, click **Edit Basic Info**.
4.  In the displayed dialog box, enter the group name and description.
5.  Click **OK**.

## Delete a RAM user group {#section_n2c_4sf_xdb .section}

1.  In the left-side navigation pane of the RAM console, click **Groups**.
2.  In the **Actions** column, click **Delete** on the right of the target RAM user group.
3.  In the displayed dialog box, click **OK**.

    **Note:** If the RAM user group to be deleted contain any members or has any policies, you must select **Unlink Dependent Objects** before you click **OK**.


## Grant permission to a RAM user group {#section_p2c_4sf_xdb .section}

For information about how to grant permission to a RAM user group, see [Permission granting in RAM](reseller.en-US/User Guide/(Old Version) User Guide/Authorization management/Permission granting in RAM.md#).

