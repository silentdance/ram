# Group {#concept_hb3_nsf_xdb .concept}

If you have created multiple RAM users with your Alibaba Cloud account, we recommend that you manage those users by group to simplify the management process. Classify RAM users with the same responsibility by group and [Authorization](reseller.en-US/User Guide/Authorization/Authorization.md) upon authorization. The benefits of doing so are as follows:

-   When the responsibility of a specific user changes, you can simply move them to an appropriate group, which does not have an impact on other users.
-   When the permissions of a group change, you only need to modify the authorization policy for the group, which can be applied to all users.

This document describes the following tasks:

-   [Create a group](#section_d2c_4sf_xdb)
-   [Manage group members](#section_f2c_4sf_xdb)
-   [Rename a group](#section_k2c_4sf_xdb)
-   [Delete a group](#section_n2c_4sf_xdb)
-   [Grant permissions to a group](#section_p2c_4sf_xdb)

## Create a group {#section_d2c_4sf_xdb .section}

The operation procedure is as follows:

1.  On the [homepage](https://partners-intl.console.aliyun.com/#/ram) of the [RAM console](https://partners-ram.console.aliyun.com/), click**Groups** \> **Create Group**.
2.  Enter a Group Name and click **OK**.

## Manage group members {#section_f2c_4sf_xdb .section}

The operation procedure is as follows:

1.  On the **homepage** of the **RAM console**, click Groups.
2.  On the Group Management page, click **Management** in the **Actions** area to manage group members.

-   Add group members:
    1.  Locate the group you want to manage in the group list \(you can use the group name for a fuzzy query \), and click **Edit Group Member** in the Actions area.
    2.  Select the target user from the left box \(you can query using the keyword \), and click the right arrow to add the user to the right box; select the user in the right box, and click the left arrow to undo the selection.
    3.  Click **OK** when the selection is complete.
-   Delete group members:
    1.  Locate the group you want to manage in the group list \(you can use the group name for a fuzzy query \), and click the group name.
    2.  In the **Group Member Management** area, click **Remove from Group** to delete the target user from the group.

## Rename a group {#section_k2c_4sf_xdb .section}

The operation procedure is as follows:

1.  On the homepage of the **RAM console**, click **Groups**.
2.  Locate the group you want to rename in the group list \(you can use the group name for a fuzzy query \), and click the group name or **Management** to enter the **Group Details** page.
3.  Click **Edit Basic Info**.
4.  Enter **Group Name** and click **OK**.

## Delete a group {#section_n2c_4sf_xdb .section}

The operation procedure is as follows:

1.  On the homepage of the **RAM console**, click **Groups**.
2.  Locate the group you want to delete in the group list \(you can use the group name for a fuzzy query \), and click **Delete** in the Actions area.

    **Note:** If the group contains group members or a bound authorization policy, you can delete a group only after selecting **Unlink Dependent Objects**.


## Grant permissions to a group {#section_p2c_4sf_xdb .section}

For details about how to grant permissions to a group, see [Authorization](reseller.en-US/User Guide/Authorization/Authorization.md).

