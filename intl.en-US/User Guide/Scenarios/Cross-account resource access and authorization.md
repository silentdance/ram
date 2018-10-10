# Cross-account resource access and authorization {#concept_es5_cgk_xdb .concept}

This document describes how to use RAM roles to perform cross-account resource access and authorization in specific scenarios.

## Scenario description {#section_rgm_dgk_xdb .section}

Account A and account B represent different enterprises \(teams or projects\). Assume that enterprise A has bought a lot of cloud resources, such as ECS instances, RDS instances, SLB instances, and OSS buckets for its business requirements.

-   Enterprise A wants to focus on its business systems, so it grants cloud resource O&M, monitoring management, and other tasks to the enterprise B.
-   Enterprise B can then further delegate O&M tasks to its employees. Enterprise B needs to precisely control the delegate operations that its employees can perform on the cloud resources of the enterprise A.
-   If A and B terminate this O&M entrustment contract, enterprise A is able to revoke the permissions of the enterprise B as needed.

## Requirement analysis {#section_tgm_dgk_xdb .section}

The analysis of the preceding scenarios is as follows:

-   Authorization between two Alibaba Cloud accounts, A and B. Account A is the resource owner and wants to grant B permissions to perform operations on its resources.
-   Account B needs to further allocate permissions to its sub-users \(employees or applications\). If an employee of B joins or leaves the company, A does not have to make any changes to the permissions.
-   If A and B terminate their cooperation, A is able to revoke B’s permissions as needed.

## Solution {#section_vgm_dgk_xdb .section}

For the requirements above, **use the RAM role for cross-account authorization and resource access**.

-   Account A creates a role in RAM and assigns appropriate permissions to the role, and allows account B to use this role. For the operation procedure, see the section "Cross-account authorization".
-   If an employee \(RAM user\) under account B needs to use this role, account B can perform authorization control independently. Under the O&M entrustment contract, the RAM user under account B can use the granted role identity to manipulate the resources of account A. For the operation procedure, see the section "Cross-account resource access".
-   If A and B terminate this O&M entrustment contract, account A only needs to revoke the enterprise B's use of this role. Once account B's use of this role is revoked, all RAM users under account B cannot use this role. For the operation procedure, see the section "Revocation of cross-account authorization".

## Cross-account authorization {#section_xgm_dgk_xdb .section}

The following figure shows how to use the RAM role for cross-account authorization. Assume that enterprise A \(AccountID=11223344, alias: company-a\) needs to grant ECS operation permissions to the employees of enterprise B \(AccountID=12345678, alias: company-b\).

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/12363/15391782423632_en-US.png)

The operation procedure is as follows:

1.  Account A creates a user role \(assuming the role is named ecs-admin\) and selects **Other Alibaba Cloud Account** \(account B: 12345678\). As a trusted account, the RAM users under account B are allowed to assume this role. For the detailed operation, see [Role](intl.en-US/User Guide/Identities/Role.md).

    After creating the role, enterprise A can get the role information on the details page. 

    -   In this example, the role’s global name ARN is:

        ```
        acs:ram::11223344:role/ecs-admin
        ```

    -   The role’s policy \(only enterprise B can assume this role\)  is as follows:

        ```
        
        "Statement": [
        
         "Action": "sts:AssumeRole",
         "Effect": "Allow",
         "Principal": {
           "RAM": [
             "acs:ram::12345678:root"
           
         }
        
        
        "Version": "1"
        
        ```

2.  Account A [adds the authorization policy](intl.en-US/User Guide/Authorization/Authorization.md) \(AliyunECSFullAccess\) to the role ecs-admin.
3.  Account B creates a RAM user for its employee \(assuming the user name is Alice\) and
    -   [sets the logon password](intl.en-US/User Guide/Identities/User.md) \(assuming the logon password is 123456\). That is, the RAM user is allowed to log on to the console.
    -   [calls the permission for the STS interface AssumeRole](intl.en-US/User Guide/Authorization/Authorization.md) \(AliyunSTSAssumeRoleAccess\). That is, the RAM user Alice is allowed to assume or switch the role.

## Cross-account resource access {#section_fhm_dgk_xdb .section}

The RAM user Alice under account B accesses account A's ECS resources through the console. The operation procedure is as follows:

1.  The RAM user \(Alice\) under account B [logs on to the console](intl.en-US/User Guide/Identities/User.md).

    When a sub-user logs on, the sub-user must enter **enterprise alias** \(company-b\), **sub-user username** \(Alice\), and **sub-user password** \(123456\) correctly.

2.  The RAM user \(Alice\) under account B [switches the role](intl.en-US/User Guide/Identities/Role.md).

    In the upper right corner of the console, move the mouse pointer to the logon user name and click **Switch Role** to go to the identity switching page. Enter **enterprise alias** \(company-a\) and **role name** \(ecs-admin\) correctly to **switch** the role.

3.  The RAM user \(Alice\) under account B manipulates the ECS resources under account A.

## Revocation of cross-account authorization {#section_ihm_dgk_xdb .section}

Account A revokes account B's use of the role ecs-admin. The operation procedure is as follows:

1.  Account A logs on to the RAM console, finds the role ecs-admin on the Role Management page, and clicks the name of its role or the **Manage** button to go to the Role Details page.
2.  Click **Edit Basic Information** in the upper right corner. In the displayed dialog box, remove `acs:ram::12345678:root` from **Policy Content**. \(That is, account B will be removed from the trusted cloud accounts of the role.\)

    **Note:** Alternatively, account A can **Delete** the role ecs-admin from the Role Management page. Before the deletion, ensure that the role does not have any authorization policies.


