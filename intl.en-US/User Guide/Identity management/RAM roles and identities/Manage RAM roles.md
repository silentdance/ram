# Manage RAM roles {#concept_xvr_ftf_xdb .concept}

This topic describes how to manage RAM roles.

**Note:** In this topic, **roles** refer to **RAM roles** unless otherwise specified.

## Create a RAM role {#section_02 .section}

1.  Create an **Alibaba Cloud Account**.
    1.  Log on to the [RAM Console](https://partners-intl.console.aliyun.com/#/ram).
    2.  Choose **RAM Roles** \> **Create RAM Role**.
    3.  In the displayed dialog box, select **Alibaba Cloud Account** for **Select type of trusted entity**.
    4.  Select an account type.
        -   If you create a role for RAM users under your account \(for example, authorizing mobile app clients to directly operate OSS resources\), select **Current Alibaba Cloud Account** as the trusted account.
        -   If you create a role for RAM users under another account \(for example, cross-account resource authorization\), select **Other Alibaba Cloud Account** and enter the account ID.
    5.  Enter **RAM Role Name**. You can also choose to enter **Note**. Then, click **OK**.
2.  Create an **Alibaba Cloud Service**.

    1.  Log on to the [RAM Console](https://partners-intl.console.aliyun.com/#/ram).
    2.  Choose **RAM Roles** \> **Create RAM Role**.
    3.  In the displayed dialog box, select **Alibaba Cloud Service** for **Select type of trusted entity**.
    4.  **Select Trusted Service** as needed. Available service roles include:

        -   Media Transcoding Service \(MTS\): You can create such a role, configure MTS as its trusted service, and use MTS to assume the role and access OSS data when you set OSS Bucket as the data source for MTS tasks.
        -   Archive Storage Service \(OAS\): You can create such a role, configure OAS as its trusted service, and use OAS to assume the role and access OSS data when you set OSS Bucket as the data source for OAS.
        -   Log Service \(LOG\): You can create such a role, configure LOG as its trusted service, and use LOG to assume the role and write data into OSS when you import LOG-collected logs into OSS.
        -   API Gateway \(ApiGateway\): You can create such a role, configure API Gateway as its trusted service, and use API Gateway to assume the role and call the function service when you set the function service as the backend service of API Gateway.
        -   Elastic Compute Service \(ECS\): You can use such a role to authorize ECS to access your cloud resources in other cloud services.
        **Note:** For more trusted services, see the RAM console.

    5.  Enter **RAM Role Name**. You can also choose to enter **Note**. Then, click **OK**.
    The created role has no permission. You can click **Add Permissions** to directly grant permissions to the role. For the authorization method, see [Permission granting in RAM](reseller.en-US/User Guide/Permission management/Permission granting/Permission granting in RAM.md#).

    Return to the **RAM Console** home page. In the **RAM Roles** pane, locate the created role and click **RAM Name** to view the role details.


## Use a RAM role {#section_05 .section}

**Alibaba Cloud Service** can be assumed only by trusted cloud services, while **Alibaba Cloud Account** can be assumed by RAM users.

1.  Create a RAM user and create an AccessKey \(AK\) or set a password for the user.
2.  Add the system policy AliyunSTSAssumeRoleAccess to authorize the RAM user.

**Note:** For maintain account security, trusted accounts are not allowed to assume roles by their own identities. Roles must be assumed by RAM users.

RAM users can assume roles either in the RAM console or through APIs:

-   **Assume RAM roles in the RAM console**
    1.  Log on to the **RAM Console** as a RAM user.
    2.  In the upper-right corner, hover your mouse over your account icon and click **Switch Role**.
    3.  In the displayed **Switch Role** dialog box, enter the account alias and role name, and then click **Switch**.

        The RAM user logs on to the RAM console as the role identity. In this case, both the current role identity and the user's logon identity are displayed in the upper-right corner.

    4.  Click **Switched Login Role** to switch back to the user's logon identity.
-   **Assume RAM roles through APIs**

    After being granted the AssumeRole permission, a RAM user can use its AK to call the AssumeRole API of Security Token Service \(STS\) to obtain the temporary security token of a role. Then, the user uses the token to access cloud resource APIs. For details about how to call the AssumeRole API, see [AssumeRole](../../../../reseller.en-US/API reference/API Reference (STS)/Operation interface/AssumeRole.md).


