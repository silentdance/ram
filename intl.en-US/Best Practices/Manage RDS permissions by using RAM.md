# Manage RDS permissions by using RAM {#concept_zqh_gqx_ydb .concept}

This topic describes how to manage RDS permissions of RAM users by creating policies in RAM.

## Common policies {#section_rth_xua_nes .section}

The following table lists some common policies that can be created in RAM to manage RDS permissions.

|Policy|Description|
|:-----|:----------|
|AliyunRDSFullAccess|Grants a RAM user full management permissions for RDS instances.|
|AliyunRDSReadOnlyAccess|Grants a RAM user read-only permission for RDS instances.|

**Note:** For more information about RDS permissions, see [RAM authorization](../../../../reseller.en-US/API Reference/RAM authorization.md#).

## Attach custom policies to RAM users {#section_hcn_ich_5qp .section}

1.  Create custom policies according to the subsequent RDS authorization examples.

    For more information, see [Policy management](../../../../reseller.en-US/User Guide/Permission management/Policy management.md#).

2.  Locate the target policy and click the policy name.
3.  On the **References** tab, click **Grant Permission**.
4.  In the **Principal** field, enter the ID or name of the target RAM user.
5.  Click **OK**.

    **Note:** You can also attach policies to a RAM user or a RAM user group as needed. For more information, see [Permission granting in RAM](../../../../reseller.en-US/User Guide/Permission management/Permission granting/Permission granting in RAM.md#).


## RDS authorization examples {#section_en0_f0b_60y .section}

-   Example 1: As a RAM administrator with multiple instances, authorize a user to operate on only two of your instances.

    The IDs of these two RDS instances are i-001 and i-002.

    ```
    {
      "Statement": [
        {
          "Action": "rds:*",
          "Effect": "Allow",
          "Resource": [
                      "acs:rds:*:*:dbinstance/i-001",
                      "acs:rds:*:*:dbinstance/i-002"
                      ]
        },
        {
          "Action": "rds:Describe*",
          "Effect": "Allow",
          "Resource": "*"
        }
      ],
      "Version": "1"
    }
    ```

    **Note:** 

    -   The authorized RAM user can view all the RDS instances but can only operate on two of them.
    -   The `Describe*` element is required in a policy. If a policy does not contain the `Describe*` element, the authorized RAM user cannot view any instance in the console. However, the RAM user can operate on the two specified RDS instances by calling API actions, by using the CLI, or by using RDS SDKs.
-   Example 2: As a RAM administrator, authorize a user to access data in the Alibaba Cloud Data Management System \(DMS\).
    -   Authorize a RAM user to access a specified RDS instance.

        ```
        {
          "Statement": [
            {
              "Action": "dms:LoginDatabase",
              "Effect": "Allow",
              "Resource": "acs:rds:*:*:dbinstance/rds783a0639ks5k7****"
            }
          ],
          "Version": "1"
        }
        ```

        **Note:** You need to replace `rds783a0639ks5k7****` with the ID of the RDS instance to be accessed.

    -   Authorize a RAM user to access all RDS instances.

        ```
        {
          "Statement": [
            {
              "Action": "dms:LoginDatabase",
              "Effect": "Allow",
              "Resource": "acs:rds:*:*:*"
            }
          ],
          "Version": "1"
        }
        ```


