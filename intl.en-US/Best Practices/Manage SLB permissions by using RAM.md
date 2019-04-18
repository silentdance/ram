# Manage SLB permissions by using RAM {#concept_qhc_xqx_ydb .concept}

This topic describes how to manage SLB permissions of RAM users by creating policies in RAM.

## Common policies {#section_ida_4ln_8lj .section}

The following table lists some common policies that can be created in RAM to manage SLB permissions.

|Policy|Description|
|:-----|:----------|
|AliyunSLBFullAccess|Grants a RAM user full management permissions for SLB instances.|
|AliyunSLBReadOnlyAccess|Grants a RAM user read-only permission for SLB instances.|

**Note:** For more information about SLB permissions, see [RAM authentication](../../../../reseller.en-US/Developer Guide/RAM authentication.md).

## Attach custom policies to RAM users {#section_z9a_zmd_ey3 .section}

1.  Create custom policies by referring to [SLB authorization examples](#section_hwy_ypl_5gb).

    For more information, see [Policy management](../../../../reseller.en-US/User Guide/Permission management/Policy management.md#).

2.  Locate the target policy and click the policy name.
3.  On the **References** tab, click **Grant Permission**.
4.  In the **Principal** field, enter the ID or name of the target RAM user.
5.  Click **OK**.

    **Note:** You can also attach policies to a RAM user or a RAM user group as needed. For more information, see [Permission granting in RAM](../../../../reseller.en-US/User Guide/Permission management/Permission granting/Permission granting in RAM.md#).


## SLB authorization examples {#section_fox_sam_p1n .section}

-   Example 1: As a RAM administrator with multiple instances, authorize a user to operate on only two of your instances.

    The IDs of these two SLB instances are i-001 and i-002.

    ```
    {
      "Statement": [
        {
          "Effect": "Allow",
          "Action": "slb:*",
          "Resource": [
                      "acs:slb:*:*:loadbalancer/i-001",
                      "acs:slb:*:*:loadbalancer/i-002"
                      ]
        },
        {
          "Effect": "Allow",
          "Action": "slb:Describe*",
          "Resource": "*"
        }
      ],
      "Version": "1"
    }
    ```

    **Note:** 

    -   The authorized RAM user can view all the SLB instances but can only operate on two of them.
    -   The `Describe*` element is required in a policy. If a policy does not contain the `Describe*` element, the authorized RAM user cannot view any instance in the console. However, the RAM user can operate on the two specified SLB instances by calling API actions, by using the CLI, or by using SLB SDKs.
-   Example 2: As a RAM administrator, authorize a user to add ECS instances to an SLB instance. The ID the SLB instance is i-001.

    ```
    {
      "Statement": [
        {
          "Effect": "Allow",
          "Action": "slb:AddBackendServers",
          "Resource": ["acs:slb:*:*:loadbalancer/slb-001"]
        },
        {
          "Effect": "Allow",
          "Action": "slb:AddBackendServers",
          "Resource": ["acs:ecs:*:*:instance/i-001"]
        },
        {
            "Effect": "Allow",
            "Action": "slb:DescribeLoadBalancers",
            "Resource": "acs:slb:*:*:loadbalancer/*"
        }
      ],
      "Version": "1"
    }
    ```

    **Note:** After you have granted the SLB management permission to a RAM user according to the policy described in example 1, you also need to grant the following permissions to the user so that the user can add or remove ECS instances, or set the weight of ECS instances as needed:

    -   The permission for SLB resources
    -   The permission for ECS resources
-   Example 3: As a RAM administrator, authorize a user to perform any ECS-related operations on a specified SLB instance.

    ```
    {
      "Statement": [
        {
          "Effect": "Allow",
          "Action": "slb:*",
          "Resource": [
                      "acs:slb:*:*:loadbalancer/i-001",
                      "acs:slb:*:*:loadbalancer/i-002"
                      ]
        },
        {
          "Effect": "Allow",
          "Action": "slb:Describe*",
          "Resource": "*"
        },
        {
          "Effect": "Allow",
          "Action": "slb:*",
          "Resource": "acs:ecs:*:*:*"
        }
      ],
      "Version": "1"
    }
    ```

    **Note:** The preceding policy allows a RAM user to manage two specified SLB instances \(IDs: i-001 and i-002\) and perform all ECS-related operations on these two SLB instances, for example, add ECS instances to these two SLB instances and set the weight of ECS.


