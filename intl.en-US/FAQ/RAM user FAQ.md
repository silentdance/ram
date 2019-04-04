# RAM user FAQ {#concept_dwg_5rx_ydb .concept}

## How do I log on to the Alibaba Cloud console as a RAM user? {#section_x1f_w4x_ydb .section}

You can visit the RAM user logon URL on the right of the **Overview** page in the [RAM console](https://partners-intl.console.aliyun.com/#/ram).

The user name for logon can be in either of the following formats: <$username\>@<$AccountAlias\> and <$username\>@<$AccountAlias\>.onaliyun.com. If you have created a domain alias, you can also use the domain alias in <$username\>@<$DomainAlias\> format for logon.

**Note:** If you log on to the Alibaba Cloud console by visiting the RAM user logon URL on the right of the **Overview** page in the RAM console, the system automatically provides a default domain name. You only need to enter the user name.

## What are the default domain name, account alias, and domain alias? How do I use and manage them? {#section_bb5_2sm_qfb .section}

For details about the **default domain name**, **account alias**, and **domain alias**, see [Terms](../../../../../reseller.en-US/Product Introduction/Terms.md#).

To view and manage the default domain name, account alias, and domain alias of your account, log on to the **RAM console** by using your account or as a RAM user with the RAM permission, choose **Identities** \> **Settings**, and click **Advanced**.

## What permissions are required for a RAM user to purchase Alibaba Cloud services? {#section_ic3_fms_qfb .section}

-   For Pay-As-You-Go services, permission to create service instances, or similar permissions are required.
-   For Subscription services, permission to create service instances and permission to make payments \(the AliyunBSSOrderAccess policy\) are required.
-   For services that must be purchased with the use or creation of some other resources, the permission for reading or creating the corresponding resources is required. The following example describes the permissions required for creating an ECS instance.

    The following policy allows a RAM user to create an ECS instance through the console, the ECS API, or the instance launch template:

    ```
    
    {
      "Version": "1",
      "Statement": [
        {
          "Action": [
            "ecs:DescribeLaunchTemplates",
            "ecs:CreateInstance",
            "ecs:RunInstances",
            "ecs:DescribeInstances",
            "ecs:DescribeImages",
            "ecs:DescribeSecurityGroups"
          ],
          "Resource": "*",
          "Effect": "Allow"
        },
        {
          "Action": [
            "vpc:DescribeVpcs",
            "vpc:DescribeVSwitches"
          ],
          "Resource": "*",
          "Effect": "Allow"
        }
      ]
    }
    ```

    To allow a user to use or create resources other than ECS instances, log on to the **RAM console** and click **Policies**. On the displayed page, create a custom policy and grant permissions to the user according to the following table.

    |Operation|Policy action|
    |:--------|:------------|
    |Use a snapshot to create an ECS instance.|`ecs:DescribeSnapshots`|
    |Create and use a VPC.| `vpc:CreateVpc`

 `vpc:CreateVSwitch`

 |
    |Create and use a security group.| `ecs:CreateSecurityGroup`

 `ecs:AuthorizeSecurityGroup`

 |
    |Specify the instance RAM role.| `ecs:DescribeInstanceRamRole`

 `ram:ListRoles`

 `ram:PassRole`

 |
    |Use a key pair.| `ecs:CreateKeyPair`

 `ecs:DescribeKeyPairs`

 |
    |Create an ECS instance on a Dedicated Host \(DDH\).|`ecs:AllocateDedicatedHosts`|


## After I grant permission to a user, why is a message displayed when the user accesses the system, indicating that the user does not have the permission? {#section_kjs_vjs_qfb .section}

-   Check whether the policy attached to the user is correct.
-   Check whether `"Effect": "Deny"` has been set in the custom policy \(including policies of the user and policies of the user's groups\) attached to the user for the corresponding resources or operations.

    For example, a user has both the AliyunECSReadOnlyAccess policy \(which contains the read-only permission for accessing ECS\) and the following policy:

    ```
    
    {
      "Statement": [
        {
          "Action": "ecs:*",
          "Effect": "Deny",
          "Resource": "*"
        }
      ],
      "Version": "1"
    }
    
    ```

    According to the "Deny takes priority" principle in RAM, the user is not allowed to view the ECS resources.


## Why can a user perform operations without the corresponding permission? {#section_cv1_qsm_qfb .section}

If a user does not have the required custom policy or the FullAccess or ReadOnly system policy of ECS and can view the created ECS instances in the console, perform the following operations:

1.  Check whether the group policy of the user contains the permission that allows the user to perform the corresponding operations.
2.  Check whether other polices attached to the user contain the corresponding permissions.

For example, the system policy of CloudMonitor is AliyunCloudMonitorFullAccess, which contains the following permissions: `"ecs:DescribeInstances"` \(view ECS instances\), `"rds:DescribeDBInstances"` \(view RDS instances\), and `"slb:DescribeLoadBalancer"` \(view SLB instances\). If you attach the AliyunCloudMonitorFullAccess policy to a user, the user has permission to view the information of ECS, RDS, and SLB instances.

## How do I grant permission to a user for renewal management only? {#section_ikw_mms_qfb .section}

A unified renewal management policy is not currently available. You must customize a policy according to the specific services. You can grant the user the permission for purchasing the service and the payment permission.

For example, if you want a user to perform ECS renewal management, see [What permissions are required for a RAM user to purchase Alibaba Cloud services?](#) to grant required permissions and the AliyunBSSOrderAccess policy to the user.

## Who will be charged for the resources used by a RAM user? {#section_qqy_n1h_chb .section}

-   Fees incurred by a user when using Alibaba Cloud resources are paid by the account to which the user belongs.
-   Users under an account enjoy the discounts of the account by default.
-   Users under an account share the same financial attributes such as consumption, credit limit, and payment method. You cannot set a financial attribute for a single user.
-   A user under an account can be authorized to add money to the account balance. However, the balance belongs to the account, not the user.
-   Users in a group are not billed separately. To obtain bills that detail the charges incurred by each user under an account, [open a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex).

