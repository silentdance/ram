# Cross-account resource authorization and access {#concept_es5_cgk_xdb .concept}

This topic describes how to use RAM roles to perform cross-account resource authorization and access.

## Scenario {#section_01 .section}

Account A and Account B represent two different enterprises \(Enterprise A and Enterprise B, respectively\). Enterprise A has bought various cloud resources \(such as ECS instances, RDS instances, SLB instances, and OSS buckets\) to support its business.

## Requirement analysis {#section_02 .section}

-   Account A is the resource owner and wants to grant Account B the relevant permissions to perform operations on resources of Account A.
-   Account B wants to further grant the permissions to its RAM users \(employees or applications\). If an employee of Account B joins or leaves Enterprise B, Account A cannot make any changes to the permissions.
-   If Enterprise A or Enterprise B ends the agreement, Account A can remove the permissions of Account B at any time.

## Solution {#section_03 .section}

Use RAM roles to perform cross-account authorization and resource access.

-   Account A creates a role in RAM, grants relevant permissions to the RAM role, and allows Account B to use this role.

    For more information, see [Cross-account authorization](#).

-   If an employee \(that is, a RAM user\) under Account B needs to use this role, Account B can grant permissions to this RAM user to perform operations on the resources of Account A.

    For more information, see [Cross-account resource access](#).

-   If Enterprise A or Enterprise B ends the agreement, Account A can revoke the permissions of Account B. In this case, all RAM users of Account B lose the permissions associated with this role.

    For more information, see [Removing cross-account authorization](#).


## Cross-account authorization {#section_04 .section}

The following figure shows how to use a RAM role to achieve cross-account authorization. In this example, Enterprise A \(whose account ID is 11223344 and account alias is company-a\) needs to grant ECS operation permissions to the employees of Enterprise B \(whose account ID is 12345678 and account alias is company-b\).

![Use a RAM role to achieve cross-account authorization](images/14408_en-US.png "Use a RAM role to achieve cross-account authorization")

1.  Account A creates a RAM role \(here, the role is named ecs-admin\) and selects **Other Alibaba Cloud Account** \(here, the account ID is 12345678\) as a trusted entity.

    For more information, see [Manage RAM roles](reseller.en-US/User Guide/Identity management/RAM roles and identities/Manage RAM roles.md#).

    After creating the role, Account A can view the role information on the **Basic Information** page.

    -   In this example, the Alibaba Cloud Resource Name \(ARN\) of the role is as follows:

        ```
        acs:ram::11223344:role/ecs-admin
        ```

    -   The trust policy in the role \(in which only RAM users under Account B can assume\) is as follows:

        ```
        {
        "Statement": [
        {
         "Action": "sts:AssumeRole",
         "Effect": "Allow",
         "Principal": {
           "RAM": [
             "acs:ram::12345678:root"
           ]
         }
        }
        ],
        "Version": "1"
        }
        ```

2.  Account A attaches the `AliyunECSFullAccess` policy to the role ecs-admin.

    For more information, see [Permission granting in RAM](reseller.en-US/User Guide/Permission management/Permission granting/Permission granting in RAM.md#).

3.  Account B creates a RAM user \(here, the RAM user is named Alice\) for its employee, sets a logon password for the RAM user, and attaches the `AliyunSTSAssumeRoleAccess` system policy for the RAM user to call the STS AssumeRole API.

## Cross-account resource access {#section_05 .section}

To allow RAM user Alice under Account B to access the ECS resources of Account A \(through the Alibaba Cloud console\), follow these steps:

1.  Log on to the **RAM console**.

    During logon, enter the **account alias** company-b, **RAM user name** Alice, and **password** 123456.

2.  Move the pointer over the account icon and click **Switch Role**.

    On the displayed page, enter company-a for **Enterprise Alias/Default Domain Name** and ecs-admin for **Role Name**.


**Note:** After completing the preceding operations, the RAM user Alice can perform operations on the ECS resources of Account A.

## Removing cross-account authorization {#section_06 .section}

If Account A wants to remove the permission of using the role ecs-admin from Account B, the procedure is as follows:

1.  Log on to the **RAM console**, click **RAM Roles**, and click the role name of ecs-admin.
2.  Click the **Trust Policy Management** tab and delete `acs:ram::12345678:root`.

    **Note:** Account A can also remove the permission of using the role ecs-admin from Account B by deleting the ecs-admin role on the **RAM Roles** page. However, the role cannot have any policies attached to it before being deleted.


