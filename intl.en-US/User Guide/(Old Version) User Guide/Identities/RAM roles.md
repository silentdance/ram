# RAM roles {#concept_kwz_hrk_bhb .concept}

A RAM role is a RAM identity that represents a virtual user. A RAM role does not have a long-term password or AccessKey and is assumable by trusted entities through the console or API.

**Note:** In this topic, the term "role" refers to a RAM role unless otherwise specified.

## Related concepts {#section_f2y_k4d_nfb .section}

The following figure illustrates the relationships between the concepts related to RAM roles.

![](images/14219_en-US.png "Concepts related to RAM roles")

|Concept|Description|
|:------|:----------|
|ARN|An Alibaba Cloud Resource Name \(ARN\) is the global resource identifier of a role. It is used to specify a role. -   ARNs conform to Alibaba Cloud ARN naming conventions. For example, the ARN of the role devops under an Alibaba Cloud account is `acs:ram::1234567890123456:role/samplerole`.
-   After you create a role, you can click the role name and view its ARN in the **Basic Information** area.

 |
|Trusted entity|A trusted entity is the identity of a trusted entity user who can assume a role. -   You must specify a trusted entity when you create a role. Only trusted entities can assume roles.
-   A trusted entity can be a trusted Alibaba Cloud account or an Alibaba Cloud service.

 |
|Policy|A role can be attached to a set of policies. Roles that are not attached to any policy can exist, but cannot access resources.|
|Role assuming|Role assuming is the method for entity users to obtain security tokens of roles. By calling the AssumeRole API action, an entity user can obtain the security token of a role and use the token to access Alibaba Cloud service APIs.|
|Identity switching|Identity switching is the method by which entity users can switch from the logon identity to role identity in the RAM console. -   After an entity user logs on to the RAM console, the entity user can switch to a role that the user can assume. The user can then use the role identity to operate on Alibaba Cloud resources.
-   When the user no longer needs the role identity, the user can switch back to its logon identity.

 |
|Role token|A role token is a temporary AccessKey of a role identity. RAM roles do not have specific identity authentication keys. When an entity user wants to use a role, the user must assume the role to obtain the role token. Then, the user can use the role token to call Alibaba Cloud service APIs.|

## Instructions {#section_b2y_k4d_nfb .section}

RAM roles can be used only after they are assumed by trusted entity users.

![](images/14225_en-US.png "Use RAM roles")

The difference between RAM roles and textbook roles is as follows:

-   As virtual users, RAM roles have specific identities and can be granted a set of policies. However, RAM roles do not have specific identity authentication keys \(logon passwords or AccessKeys\).
-   A textbook role \(or a traditionally defined role\) indicates a permission set, similar to a policy in RAM. If such a role is granted to a user, the user has a set of permissions and can access the authorized resources.

The difference between entity users and virtual users is as follows:

-   Entity users have specific logon passwords or AccessKeys. Accounts, RAM user accounts, and Alibaba Cloud service accounts are examples of entity users.
-   Virtual users do not have specific authentication keys. RAM roles are an example of entity users.

## RAM role types {#section_01 .section}

RAM roles are divided into the following types according to different trusted entities:

-    **User Role**: roles that RAM users can assume. The RAM users may belong to their own Alibaba Cloud accounts or other accounts. Such roles provide solutions to cross-account access and temporary authorization.
-    **Service Role**: roles that Alibaba Cloud services can assume. Such roles are used to authorize Alibaba Cloud services to operate on resources.

## Create a RAM role {#section_n10_ukv_vo1 .section}

To create a RAM role in the RAM console, follow these steps:

1.  Select a role type.
2.  Select a trusted entity.
3.  Enter the role name.
4.  Attach a policy to the role.

## Create a RAM role for a user {#section_eu0_086_fm8 .section}

1.  Log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram).
2.  In the left-side navigation pane, click **Roles**.
3.  On the displayed page, click **Create Role**.
4.  Click **User Role**.
5.  Select a trusted Alibaba Cloud account and click **Next**.
    -   To create a role for RAM users under your Alibaba Cloud account, select **Current Alibaba Cloud Account**.
    -   To create a role for RAM users under another Alibaba Cloud account, select **Other Alibaba Cloud Account** and enter the account ID.
6.  Enter a role name in the **Role Name** field. You can also enter a description in the **Description** field. Then, click **Create**.

    **Note:** 

    -   After you create a RAM role, you can click **Authorize** to grant permission to the role. For more information, see [Permission granting in RAM](reseller.en-US/User Guide/(Old Version) User Guide/Authorization management/Permission granting in RAM.md#).
    -   After you create a RAM role, you can click the role name in the **Role Name** column, or click **Manage** in the **Actions** column to view the role details.

## Create a RAM role for an Alibaba Cloud service {#section_h2y_zdd_g07 .section}

1.  Log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram).
2.  In the left-side navigation pane, click **Roles**.
3.  On the displayed page, click **Create Role**.
4.  Click **Service Role** and select a trusted Alibaba Cloud service. Available services include:

    -    **Media Transcoding Service \(MTS\):** You can create a role, configure MTS as its trusted service, and use MTS to assume the role and access Object Storage Service \(OSS\) data when you set OSS Bucket as the data source for MTS tasks.
    -    **Archive Storage:** You can create a role, configure Archive Storage as its trusted service, and use Archive Storage to assume the role and access OSS data when you set OSS Bucket as the data source for Archive Storage.
    -    **Log Service:** You can create a role, configure Log Service as its trusted service, and use Log Service to assume the role and write data into OSS when you import Log Service-collected logs into OSS.
    -    **API Gateway:** You can create a role, configure API Gateway as its trusted service, and use API Gateway to assume the role and call the function service when you set the function service as the backend service of API Gateway.
    -    **Elastic Compute Service \(ECS\):** You can create a role and use this role to authorize ECS to access your resources in other Alibaba Cloud services.
    **Note:** For more information about the trusted services, see the RAM console.

5.  Enter a role name in the **Role Name** field. You can also enter a description in the **Description** field. Then, click **Create**.

    **Note:** 

    -   After you create a RAM role, you can click **Authorize** to grant permission to the role. For more information, see [Permission granting in RAM](reseller.en-US/User Guide/(Old Version) User Guide/Authorization management/Permission granting in RAM.md#).
    -   After you create a RAM role, you can click the role name in the **Role Name** column, or click **Manage** in the **Actions** column to view the role details.

## Use a RAM role {#section_npw_0du_0r6 .section}

Roles that are created for an Alibaba Cloud service can be assumed only by trusted Alibaba Cloud services, and roles that are created for a user can be assumed by RAM users.

1.  Create a RAM user and create an AccessKey or set a password for the user.
2.  Attach the system policy AliyunSTSAssumeRoleAccess to authorize the RAM user.

**Note:** To maintain account security, a trusted Alibaba Cloud account is not allowed to assume roles itself. Roles must instead be assumed by RAM users of the Alibaba Cloud account.

RAM users can assume roles either in the RAM console or by calling an API action.

-   Assume RAM roles in the RAM console.

    If an entity user wants to assume a RAM role, the entity user must log on to the RAM console and switch their role.

    1.  Log on to the **RAM console** as a RAM user.
    2.  Move the pointer over your account icon in the upper-right corner and click **Switch Role**.
    3.  In the displayed **Switch Role** dialog box, enter the account alias and role name, and then click **Switch**.

        **Note:** 

        -   After you switch the role, you can log on to the console as a RAM user with the new RAM role. After you log on, both the current role and identity and the logon identity are displayed in the upper-right corner of the console.
        -   After you switch the role, you can only perform operations that are authorized to this role. The access permission of your original identity is hidden when you log on to the console.
    4.  Click **Switch Back to Logon User** to switch back to your logon identity.

        **Note:** After you switch to the logon identity, you will obtain the original permissions and lose the permissions associated with the role.

-   Assume RAM roles by calling an API action.

    After a RAM user is granted the AssumeRole permission, the user can use its AccessKey to call the AssumeRole API action of Security Token Service \(STS\) to obtain the temporary security token of a role. Then, the user uses the token to access Alibaba Cloud resource APIs.

    For more information about how to call the AssumeRole API action, see [AssumeRole](../../../../reseller.en-US/API Reference (STS)/Operation interfaces/AssumeRole.md#).


## Application scenarios of RAM roles {#section_yhg_nzp_4fb .section}

-    [Temporary authorization management for mobile apps](reseller.en-US/User Guide/(Old Version) User Guide/Scenarios/Temporary authorization management for mobile apps.md#) 
-    [Cross-account resource operation and authorization management](reseller.en-US/User Guide/(Old Version) User Guide/Scenarios/Cross-account resource operation and authorization management.md#) 

