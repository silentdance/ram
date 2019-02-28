# Use tags to authorize ECS instances by group {#concept_acb_stx_ydb .concept}

This topic describes how to use tags to authorize resources \(such as ECS instances\) by group so that RAM users can only view and operate on the tagged resources.

## Scenario {#section_plg_byz_qfb .section}

You have 10 ECS instances. You want your dev team to manage 5 of them, and your ops team to manage the other 5. However, you want each team to see only their authorized resources \(not the authorized resources of the other team\).

## Preparations {#section_02 .section}

Make sure that you can log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram) by using your RAM account.

## Solution {#section_lty_lg5_qgb .section}

Create two RAM user groups, tag these two groups, and grant permissions to the groups.

-   Tag five of them with the key as team and the value as dev.
-   Tag the other five with the key as team and the value as ops.

## Procedure {#section_ohn_tyz_qfb .section}

1.  Log on to the **ECS console**, click **Instances**, and select the target instance. In the **Actions** column, choose **More** \> **Instance Settings** \> **Edit Tag**.
2.  Click **Create**, enter the key and value, and click **Confirm**.
3.  Log on to the **RAM console**, create two RAM user groups, and name the groups as dev and ops.

    For more information, see [\(Optional\) Create a RAM user group](../../../../../reseller.en-US/Quick Start/(Optional) Create a RAM user group.md#).

4.  Create RAM users and add the users to different user groups.

    For more information, see [Create a RAM user](../../../../../reseller.en-US/Quick Start/Create a RAM user.md#).

5.  Create two custom policies and attach them to different user groups.

    For more information, see [Permission granting in RAM](../../../../../reseller.en-US/User Guide/Permission management/Permission granting/Permission granting in RAM.md#).

    **Note:** After you attach a policy to a user group, the RAM users in this group inherit the relevant permissions.

    In this example, the policy name of the dev user group is policyForDevTeam. The policy content is as follows:

    ```
    {
        "Statement": [
        {
            "Action": "ecs:*",
            "Effect": "Allow",
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "ecs:tag/team": "dev"
                }
            }
        },
        {
            "Action": "ecs:DescribeTag*",
            "Effect": "Allow",
            "Resource": "*"
        }
        ],
        "Version": "1"
    }
    ```

    In the preceding policy,

    -   The `"Action": "ecs:*"` element with "Condition" is used to filter the instances tagged as `"team": "dev"`.
    -   The `"Action": "ecs:DescribeTag*"` element is used to display all tags. When a user performs operations in the **ECS console**, the system displays all the tags for the user to select, and then filters the instances according to the tag key and value selected by the user.
    **Note:** You can create the policy policyForOpsTeam according to the example and grant this policy to the ops user group.


## Display authorized instances {#section_hwz_j25_qgb .section}

1.  Log on to the **ECS console** as a RAM user.

    **Note:** After a user logs on to the ECS console, the system navigates to the ECS overview page by default. In this case, the number of the ECS instances displayed on the page is 0. To view relevant instances, click **Instances**.

2.  Click **Instances** and click **Tags** next to the search box.

    **Note:** You need make sure that the region displayed in the console is the region to which the instances belong.

3.  Move the pointer over **Tag Key**. The **Tag Value** list is displayed. Select a value, and the system then filters the corresponding instances.

## What to do next {#section_i14_kkm_qfb .section}

You can use the procedures described in this topic to tag and authorize security groups, disks, snapshots, and images by group.

**Note:** Only custom images can be tagged.

