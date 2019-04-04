# Permission granting in RAM {#concept_vyr_mzf_xdb .concept}

This topic describes how to attach one or more policies to RAM identities \(that is, RAM users, RAM user groups, or RAM roles\) under an Alibaba Cloud account.

## Scenarios {#section_drn_djl_pgb .section}

-   Granting permission to RAM users mainly refers to granting permission to users under your account, so that the users can access the necessary resources.
-   Granting permission to RAM user groups mainly refers to granting permission to groups under your account. After you grant permission to a RAM user group, all users in the group share the same permissions.
-   Granting permission to RAM roles mainly refers to granting permission to standalone operations and applications, for example, temporary authorization for mobile device applications, cross-account resource authorization, dynamic identity and authorization management for cloud applications, and authorization for operations between cloud services.

## Before granting permission in RAM {#section_ikw_lvg_qgb .section}

Log on to the [RAM console](https://ram.console.aliyun.com/).

## Grant permission to a RAM user {#section_01 .section}

1.  Log on to the **RAM console** and choose **Identities** \> **Users**.
2.  In the **User Logon Name/Display Name** column, select the target user and click **Add Permissions**.
3.  In the **Policy Name** column on the left, select the target policies and click **OK**.

    **Note:** To remove a policy, select the policy from the area on the right, and then click ×.


## Grant permission to a RAM user group {#section_02 .section}

1.  Log on to the **RAM console** and choose **Identities** \> **Groups**.
2.  In the **Group Name/Display Name** column, select the target group and click **Add Permissions**.
3.  In the **Policy Name** column on the left, select the target policies and click **OK**.

    **Note:** To remove a policy, select the policy from the area on the right, and then click ×.


## Grant permission to a RAM role {#section_03 .section}

When you create a RAM role, you can select the trusted entity as **Alibaba Cloud Account** \(the current Alibaba Cloud account or other Alibaba Cloud accounts\), **Alibaba Cloud Service**, or **IdP**. You must enter the corresponding trusted account ID, select the trusted service, or select the trusted identity provider \(IdP\) as needed.

-   If you select **Alibaba Cloud Account** and **Current Alibaba Cloud Account**, the RAM users under the current account can assume the RAM role \(that is, be authorized to access the required cloud resources\).
-   If you select **Alibaba Cloud Account** and **Other Alibaba Cloud Account**, the RAM users under other specified accounts can assume the RAM role \(that is, be authorized to access the required cloud resources\).
-   If you select **Alibaba Cloud Service**, the trusted cloud services can assume the RAM role \(that is, be authorized to access the required cloud resources\).
-   If you select **IdP**, the users in the trusted IdP can assume the RAM role \(that is, be authorized to access the required cloud resources\).

1.  Log on to the **RAM console** and click **RAM Roles**.
2.  In the **Role Name** column, select the target RAM role and click **Add Permissions**.
3.  In the **Policy Name** column on the left, select the target policies and click **OK**.

    **Note:** To remove a policy, select the policy from the area on the right, and then click ×.


