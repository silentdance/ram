# Manage ECS permissions by using RAM {#concept_k1k_r4x_ydb .concept}

This topic describes how to manage ECS permissions of RAM users by creating policies in RAM.

## Common policies {#section_x3f_rzk_5gb .section}

The following table lists some common policies that can be created in RAM to manage ECS permissions.

|Policy|Description|
|:-----|:----------|
|AliyunECSFullAccess|Grants a RAM user full management permissions for ECS instances.|
|AliyunECSReadOnlyAccess|Grants a RAM user read-only permission for ECS instances.|

**Note:** For more information about ECS permissions, see [Authorization rules](../../../../reseller.en-US/API Reference/Authorization rules.md).

## Attach custom policies to RAM users {#section_03 .section}

1.  Create custom policies according to the subsequent ECS authorization examples.

    For more information, see [Policy management](../../../../reseller.en-US/User Guide/Permission management/Policy management.md#).

2.  Locate the target policy and click the policy name.
3.  On the **References** tab, click **Grant Permission**.
4.  In the **Principal** field, enter the ID or name of the target RAM user.
5.  Click **OK**.

    **Note:** You can also attach policies to a RAM user or a RAM user group as needed. For more information, see [Permission granting in RAM](../../../../reseller.en-US/User Guide/Permission management/Permission granting/Permission granting in RAM.md#).


## ECS authorization examples {#section_jb5_p1l_5gb .section}

-   Example 1: As a RAM administrator with multiple instances, authorize a user to operate on only two of your instances.

    The IDs of these two ECS instances are i-001 and i-002.

    ```
    {
      "Statement": [
        {
          "Action": "ecs:*",
          "Effect": "Allow",
          "Resource": [
                      "acs:ecs:*:*:instance/i-001",
                      "acs:ecs:*:*:instance/i-002"
                      ]
        },
        {
          "Action": "ecs:Describe*",
          "Effect": "Allow",
          "Resource": "*"
        }
      ],
      "Version": "1"
    }
    ```

    **Note:** 

    -   The authorized RAM user can view all the ECS instances but can only operate on two of them.
    -   The `Describe*` element is required in a policy. If a policy does not contain the `Describe*` element, the authorized RAM user cannot view any instance in the console. However, the RAM user can operate on the two specified ECS instances by calling API actions, by using the CLI, or by using ECS SDKs.
-   Example 2: As a RAM administrator, authorize a RAM user to view ECS instances in the Qingdao region, but do not allow them to view information about disks and snapshots.

    You can grant ECS permissions to the user by region and resource type.

    ```
    {
      "Statement": [
        {
          "Effect": "Allow",
          "Action": "ecs:Describe*",
          "Resource": "acs:ecs:cn-qingdao:*:instance/*"
        }
      ],
      "Version": "1"
    }
    ```

-   Example 3: As a RAM administrator, authorize a RAM user to create snapshots.

    If a RAM user cannot create disk snapshots after being granted the ECS instance administrator permission, you must grant disk permissions to the user again. In this example, the ECS instance ID is inst-01 and the disk ID is dist-01.

    ```
    {
      "Statement": [
        {
          "Action": "ecs:*",
          "Effect": "Allow",
          "Resource": [
            "acs:ecs:*:*:instance/inst-01"
          ]
        },
        {
          "Action": "ecs:CreateSnapshot",
          "Effect": "Allow",
          "Resource": [
            "acs:ecs:*:*:disk/dist-01",
            "acs:ecs:*:*:snapshot/*"
          ]
        },
        {
          "Action": [
            "ecs:Describe*"
          ],
          "Effect": "Allow",
          "Resource": "*"
        }
      ],
      "Version": "1"
    }
    ```


