# Policy management {#concept_glf_vwf_xdb .concept}

This topic describes how to manage different types of policies. Types of policies include system policies and custom policies. System policies can be viewed but cannot be modified, whereas custom policies can be created to meet your needs as required.

## Before creating a custom policy {#section_rkt_ptk_pgb .section}

Before you create a custom policy, we recommend that you read about the basic structure and syntax of a policy. For more information, see [Policy structure and syntax](reseller.en-US/User Guide/Permission management/Policy language/Policy structure and syntax.md#).

## Create a custom policy {#section_qpw_vwf_xdb .section}

1.  Log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram).
2.  Choose **Permissions** \> **Policies**.
3.  Click **Create Policy**.
4.  Enter a name for the **Policy Name**. You can also enter a description in **Note**.
5.  Set **Configuration Mode** to **Visualized** or **Script**.
    -   If you set the configuration mode to **Visualized**, click **Add Statement** and configure the permission effect, actions, and resources as prompted.
    -   If you set the configuration mode to **Script**, edit the policy according to [Policy structure and syntax](reseller.en-US/User Guide/Permission management/Policy language/Policy structure and syntax.md#).

## Modify a custom policy {#section_aqw_vwf_xdb .section}

**Scenario**

If the permissions of a user are changed \(added or removed\), you must modify the corresponding policy associated to the user. However, you may have the following requirements when modifying a policy:

-   You still want to use the old policy after a period of time.
-   You want to restore a previous policy version if the current version has incorrect modifications.

To address these issues, a version management function is provided.

-   You can retain multiple versions for a policy. If you reach the maximum number of policy versions allowed, we recommend that you delete versions you no longer need to save space.
-   Even if a policy has multiple versions, only one version is active. The active version is known as the default version.

**Procedure**

1.  In the **RAM console**, choose **Permissions** \> **Policies**.
2.  In the **Policy Name** column, click the target policy name.

    **Note:** You can enter keywords to search for a specific policy.

3.  Click **Versions**, then you can:
    -   Click **View** to view the policy content of all historical versions.
    -   Click **Use This Version** to set the target version policy to the default version.
    -   Click **Delete** to delete a target version.

## Delete a custom policy {#section_iqw_vwf_xdb .section}

You can create multiple policies and maintain multiple versions for each policy. For custom policies that are no longer needed, we recommend that you delete them.

**Prerequisites**

Before deleting a policy, ensure that:

-   The policy has only one version, that is, the default version. If multiple versions exist, you can delete all of the versions except the default one.
-   The policy is not referenced \(that is, attached to a user, user group, or role\). If the policy is currently being referenced, click **Revoke Permission** on the **References** page.

**Procedure**

1.  In the **RAM console**, click **Permissions**.
2.  In the **Policy Name** column, select the target policy and click **Delete** on the right.

    **Note:** You can enter keywords to search for a specific policy.

3.  In the **Delete Custom Policy** dialog box, click **OK**.

