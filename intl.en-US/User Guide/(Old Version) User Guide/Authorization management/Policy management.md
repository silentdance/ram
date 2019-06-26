# Policy management {#concept_glf_vwf_xdb .concept}

This topic describes how to manage different types of policies. Types of policies include system policies and custom policies. System policies can be viewed but cannot be modified, whereas custom policies can be created to meet your needs as required.

## Create a custom policy {#section_03 .section}

Before you create a custom policy, you can view the [Policy structure and grammar](intl.en-US/User Guide/(Old Version) User Guide/Policy Language/Policy structure and grammar.md#) to obtain detailed information about the basic structure and grammar of the policy language.

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) .
2.  In the left-side navigation pane, click **Policies**.
3.  Click **Custom Policy** and then click **Create Authorization Policy**.

    ![](images/3598_en-US.png "Create a custom policy")

4.  Select a template, for example, the AliyunOSSReadOnlyAccess template.
5.  Edit the policy based on the template, as shown in the following figure.

    ![](images/3599_en-US.png "Edit the policy")

    **Note:** You can modify the name, remarks, and content of the custom policy. You can also add fine-grained policy content as needed.

    The following is a policy example.

    ``` {#codeblock_y1e_obt_3f5}
    
    {
        "Version": "1",
        "Statement": [
          {
            "Action": [
              "oss:Get*",
              "oss:List*"
            ],
            "Effect": "Allow",
            "Resource": "acs:oss:*:*:samplebucket/bob/*",
            "Condition": {
              "IpAddress": {
                "acs:SourceIp": "127.0.27.1"
               }
            }
          }
        ]
    }
    ```

6.  Click **Create Authorization Policy**.

## Modify a custom policy {#section_nuh_jno_8vj .section}

Scenario

If the permissions of a RAM user are changed \(added or removed\), you must modify the corresponding policy attached to the user. However, you may have the following requirements when you modify a policy:

-   You still want to use the old policy after a period of time.
-   You want to restore a previous policy version if the current version has incorrect modifications.

To address these issues, a version management function is provided.

-   You can retain multiple versions for a policy. If you reach the maximum number of policy versions allowed, we recommend that you delete versions you no longer need to save space.
-   Even if a policy has multiple versions, only one version is active. The active version is known as the default version.

Procedure

1.  In the left-side navigation pane of the RAM console, click **Policies**.
2.  Click **Custom Policy**.
3.  In the **Authorization Policy Name** column, click the target policy name.

    **Note:** You can enter keywords to search for a specific policy.

4.  In the left-side navigation pane, click **Versions**. Then you can:
    -   Click **View** to view the policy content of all historical versions.
    -   Click **Set to Current** to set the target version policy to the default version.
    -   Click **Delete** to delete a target version.

## Delete a custom policy {#section_6s4_z6v_np1 .section}

You can create multiple policies and maintain multiple versions for each policy. For custom policies that are no longer needed, we recommend that you delete them.

Before you delete a policy, ensure that:

-   The policy has only one version, that is, the default version. If multiple versions exist, you can delete all of the versions except the default one.
-   The policy is not referenced \(that is, attached to a RAM user, RAM user group, or RAM role\). If the policy is currently being referenced, click the policy name, click **References**, and then click **Revoke Authorization**.

Procedure

1.  In the left-side navigation pane of the RAM console, click **Policies**.
2.  Click **Custom Policy**.
3.  In the **Authorization Policy Name** column, select the target policy and click **Delete**.

    **Note:** You can enter keywords to search for a specific policy.

4.  In the displayed dialog box, click **OK**.

    **Note:** If the policy is referenced, select **Unlink Dependent Objects**.


