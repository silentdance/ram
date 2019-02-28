# Manage RAM roles {#concept_xvr_ftf_xdb .concept}

This topic describes how to manage RAM roles. RAM users can assume RAM roles either in the RAM console or through APIs. After creating a RAM role, you can grant permissions to the role so that the role can access specified resources.

**Note:** In this topic, **roles** refer to **RAM roles** unless otherwise specified.

## Before creating a RAM role {#section_xy3_vhk_pgb .section}

Log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram).

## Create a RAM role {#section_02 .section}

1.  Create a RAM role of a trusted **Alibaba Cloud Account**.
    1.  Choose **RAM Roles** \> **Create RAM Role**.
    2.  Set **Select type of trusted entity** to **Alibaba Cloud Account**.
    3.  Select a trusted Alibaba Cloud account ID.
        -   To create a role for RAM users under your account \(for example, authorizing mobile app clients to directly operate OSS resources\), select **Current Alibaba Cloud Account** as the trusted account.
        -   To create a role for RAM users under another account \(for example, cross-account resource authorization\), select **Other Alibaba Cloud Account** and enter the account ID.
    4.  Enter a name for **RAM Role Name**. You can also enter a description in **Note**. Then, click **OK**.
2.  Create a RAM role of a trusted **Alibaba Cloud Service**.
    1.  Choose **RAM Roles** \> **Create RAM Role**.
    2.  Set **Select type of trusted entity** to **Alibaba Cloud Service**.
    3.  Select a trusted service as needed. Available service roles include:

        -   Media Transcoding Service \(MTS\): You can create such a role, configure MTS as its trusted service, and use MTS to assume the role and access OSS data when you set OSS Bucket as the data source for MTS tasks.
        -   Archive Storage Service \(OAS\): You can create such a role, configure OAS as its trusted service, and use OAS to assume the role and access OSS data when you set OSS Bucket as the data source for OAS.
        -   Log Service \(LOG\): You can create such a role, configure LOG as its trusted service, and use LOG to assume the role and write data into OSS when you import LOG-collected logs into OSS.
        -   API Gateway \(ApiGateway\): You can create such a role, configure ApiGateway as its trusted service, and use API Gateway to assume the role and call the function service when you set the function service as the backend service of API Gateway.
        -   Elastic Compute Service \(ECS\): You can use such a role to authorize ECS to access your cloud resources in other cloud services.
        **Note:** For more trusted services, see the RAM console.

    4.  Enter a name for **RAM Role Name**. You can also enter a description in **Note**. Then, click **OK**.

**Note:** To view the role details, you can locate the target role on the **RAM Roles** page and click the role name.

## Use a RAM role {#section_05 .section}

**Alibaba Cloud Service** can be assumed only by trusted cloud services, while **Alibaba Cloud Account** can be assumed by RAM users.

1.  Create a RAM user and create an AccessKey or set a password for the user.
2.  Attach the system policy AliyunSTSAssumeRoleAccess to authorize the RAM user.

**Note:** To maintain account security, trusted accounts are not allowed to assume roles by their own identities. Roles must be assumed by RAM users.

RAM users can assume roles either in the RAM console or through APIs:

-   **Assume RAM roles in the RAM console.**

    If an entity user wants to assume a RAM role, the entity user must log on to the RAM console and switch its role.

    1.  Log on to the **RAM console** as a RAM user.
    2.  In the upper-right corner, move your pointer over your account icon and click **Switch Role**.
    3.  In the displayed **Switch Role** dialog box, enter the account alias and role name, and then click **Switch**.

        **Note:** 

        -   After switching the role, you can log on to the console as a RAM role. In this case, both the current role and identity and the logon identity are displayed in the upper-right corner of the console.
        -   After switching the role, you can only perform operations that are authorized to this role. The access permission of your original identity is hidden when you log on to the console.
    4.  Click **Switched Login Role** to switch back to your logon identity.

        **Note:** After switching to the logon identity, you will obtain the original permissions and lose the permissions associated with the role.

-   **Assume RAM roles through APIs.**

    After being granted the AssumeRole permission, a RAM user can use its AccessKey to call the AssumeRole API of Security Token Service \(STS\) to obtain the temporary security token of a role. Then, the user uses the token to access cloud resource APIs.

    For more information about how to call the AssumeRole API, see [AssumeRole](../../../../../reseller.en-US/API Reference (STS)/Operation interfaces/AssumeRole.md).


## What to do next {#section_qgj_y1k_pgb .section}

After creating a role, you can click **Add permissions** to grant permissions to this role. For more information, see [Permission granting in RAM](reseller.en-US/User Guide/Permission management/Permission granting/Permission granting in RAM.md#).

