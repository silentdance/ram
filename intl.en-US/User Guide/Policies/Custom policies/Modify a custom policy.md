# Modify a custom policy {#task_221534 .task}

This topic describes how to modify a custom policy. If the permissions of a RAM user are changed \(added or removed\), you must modify the corresponding policy attached to the user.

You may have the following requirements when modifying a policy:

-   You still want to use the old policy after a period of time.
-   You want to restore a previous policy version if the current version has incorrect modifications.

1.   Log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram). 
2.   Choose **Permissions** \> **Policies**. 
3.   From the **Policy Type** drop-down list, select **Custom Policy**. 
4.   In the **Policy Name** column, click the name of the target custom policy. 

    **Note:** System policies and custom policies are available for use in Alibaba Cloud Resource Access Management \(RAM\). System policies can be viewed but cannot be modified, whereas custom policies can be created and modified.

5.   On the **Policy Document** tab, click **Modify Policy Document**. 

    **Note:** For information about how to modify a policy document, see [Policy structure and grammar](reseller.en-US/User Guide/Policies/Policy language/Policy structure and grammar.md#).

6.   Click **OK**. 

    **Note:** After the modifications are completed, a new custom policy is automatically generated and used as a default policy.


