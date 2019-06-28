# Permission granting in RAM {#concept_vyr_mzf_xdb .concept}

This topic describes how to attach one or more policies to RAM identities \(that is, RAM users, RAM user groups, or RAM roles\) under an Alibaba Cloud account.

## Scenarios {#section_drn_djl_pgb .section}

-   Granting permission to RAM users mainly refers to granting permission to users under your Alibaba Cloud account, so that the users can access the necessary Alibaba Cloud resources.
-   Granting permission to RAM user groups mainly refers to granting permission to groups under your Alibaba Cloud account. After you grant permission to a RAM user group, all users in the group share the same permissions.
-   Granting permission to RAM roles mainly refers to granting permission to standalone operations and applications, for example, temporary authorization for mobile device applications, cross-account resource authorization, dynamic identity and authorization management for cloud applications, and authorization for operations between Alibaba Cloud services.

## Grant permission to a RAM user {#section_r3j_nzf_xdb .section}

1.  Log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram).
2.  In the left-side navigation pane, click **Users**.
3.  In the **User Name/Display Name** column, locate the target RAM user and click **Authorize**.
4.  In the displayed dialog box, select the target policy from the **Available Authorization Policy Names** column.
5.  Click the rightwards arrow and then click **OK**.

    **Note:** To remove a policy, you can select the target policy from the **Selected Authorization Policy Name** column, and click the leftwards arrow.


## Grant permission to a RAM user group {#section_v3j_nzf_xdb .section}

1.  Log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram).
2.  In the left-side navigation pane, click **Groups**.
3.  In the **Group Name** column, locate the target RAM user group and click **Authorize**.
4.  In the displayed dialog box, select the target policy from the **Available Authorization Policy Names** column.
5.  Click the rightwards arrow and then click **OK**.

    **Note:** To remove a policy, you can select the target policy from the **Selected Authorization Policy Name** column, and click the leftwards arrow.


## Grant permission to a RAM role {#section_cx1_4wv_hfd .section}

When you create a RAM role, you can select **User Role** or **Service Role**

-   If you select **User Role** and **Current Alibaba Cloud Account**, the RAM users under the current Alibaba Cloud account can assume the RAM role \(that is, be authorized to access the required Alibaba Cloud resources\).
-   If you select **User Role** and **Other Alibaba Cloud Account**, the RAM users under other specified Alibaba Cloud accounts can assume the RAM role \(that is, be authorized to access the required Alibaba Cloud resources\).
-   If you select **Service Role**, the trusted Alibaba Cloud services can assume the RAM role \(that is, be authorized to access the required Alibaba Cloud resources\).

1.  Log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram).
2.  In the left-side navigation pane, click **Roles**.
3.  In the **Role Name** column, locate the target RAM role and click **Authorize**.
4.  In the displayed dialog box, select the target policy from the **Available Authorization Policy Names** column.
5.  Click the rightwards arrow and then click **OK**.

    **Note:** To remove a policy, you can select the target policy from the **Selected Authorization Policy Name** column, and click the leftwards arrow.


