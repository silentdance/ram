# Use RAM to limit the methods of accessing Alibaba Cloud resources {#task_1614775 .task}

This topic describes how to use RAM to limit the methods of accessing Alibaba Cloud resources to enable a higher level of security.

-   An Alibaba Cloud account is created. If not, create one before proceeding. To create an Alibaba Cloud account, click [Create a new Alibaba Cloud account](https://account.alibabacloud.com/register/intl_register.htm).
-   The RAM service is activated, and you can log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram). If the RAM service is not activated, activate the service before proceeding. For more information, see [Activation methods](../../../../reseller.en-US/Pricing/Activation methods.md#).
-   You have a basic knowledge of the policy elements, structure, and syntax before creating a custom policy. For more information, see [Policy elements](../../../../reseller.en-US/User Guide/Policies/Policy language/Policy elements.md#) and [Policy structure and grammar](../../../../reseller.en-US/User Guide/Policies/Policy language/Policy structure and grammar.md#).

Enterprise A has purchased more than one type of Alibaba Cloud resources, such as ECS instances, RDS instances, SLB instances, and OSS buckets. To ensure business and data security, this enterprise wants to only allow RAM users to access Alibaba Cloud resources by using the HTTPS method.

## Solution {#section_7fb_2lv_k12 .section}

To only allow RAM users to access Alibaba Cloud resources by using the HTTPS method, create and attach a custom policy for the RAM users.

1.  [Create a RAM user](../../../../reseller.en-US/User Guide/RAM users/Create a RAM user.md#).
2.  [Create a custom policy](#section_9ti_0x8_228).
3.  [Grant permission to a RAM user](../../../../reseller.en-US/User Guide/RAM users/Grant permission to a RAM user.md#).

## Create a custom policy {#section_9ti_0x8_228 .section}

1.  In the left-side navigation pane, click **Policies** under **Permissions**.
2.  On the Policies page, click **Create Policy**.
3.  On the page that appears, specify the **Policy Name** and **Note** parameters.
4.  Under **Configuration Mode**, select **Script**. Copy and paste the following sample script to the **Policy Document** area, and edit the script based on your business needs. 

    ![Limit the methods of accessing Alibaba Cloud resources](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1280575/156689773055110_en-US.png)

    If the following policy is attached to a RAM user, the RAM user can only access ECS instances by using the HTTPS method. In this case, the `acs:SecureTransport` parameter in `Condition` is set to `true`.

    ``` {#codeblock_ms7_zv1_mae .lanuage-xml}
    {
      "Statement": [
        {
          "Action": "ecs:*",
          "Effect": "Allow",
          "Resource": "*",
          "Condition": {        
            "Bool": {
              "acs:SecureTransport": "true"
            }
          }
        }
      ],
      "Version": "1"
    }
    ```

    **Note:** The `Condition` setting only applies to the actions that are specified for the current policy. The valid values for the `acs:SecureTransport` parameter include `true` and `false`.

5.  Click **OK**.

