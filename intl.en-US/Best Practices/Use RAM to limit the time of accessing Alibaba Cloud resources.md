# Use RAM to limit the time of accessing Alibaba Cloud resources {#task_1614774 .task}

This topic describes how to use RAM to limit the time of accessing Alibaba Cloud resources to enable a higher level of security.

-   An Alibaba Cloud account is created. If not, create one before proceeding. To create an Alibaba Cloud account, click [Create a new Alibaba Cloud account](https://account.alibabacloud.com/register/intl_register.htm).
-   The RAM service is activated, and you can log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram). If the RAM service is not activated, activate the service before proceeding. For more information, see [Activation methods](../../../../reseller.en-US/Pricing/Activation methods.md#).
-   You have a basic knowledge of the policy elements, structure, and syntax before creating a custom policy. For more information, see [Policy elements](../../../../reseller.en-US/User Guide/Policies/Policy language/Policy elements.md#) and [Policy structure and grammar](../../../../reseller.en-US/User Guide/Policies/Policy language/Policy structure and grammar.md#).

Enterprise A has purchased more than one type of Alibaba Cloud resources, such as ECS instances, RDS instances, SLB instances, and OSS buckets. To ensure business and data security, this enterprise wants RAM users to only access Alibaba Cloud resources during the working hours.

## Solution {#section_7fb_2lv_k12 .section}

To only allow RAM users to access Alibaba Cloud resources during the specified period, create and attach a custom policy for the RAM users.

1.  [Create a RAM user](../../../../reseller.en-US/User Guide/RAM users/Create a RAM user.md#).
2.  [Create a custom policy](#section_9ti_0x8_228).
3.  [Grant permission to a RAM user](../../../../reseller.en-US/User Guide/RAM users/Grant permission to a RAM user.md#).

## Create a custom policy {#section_9ti_0x8_228 .section}

1.  In the left-side navigation pane, click **Policies** under **Permissions**.
2.  On the Policies page, click **Create Policy**.
3.  On the page that appears, specify the **Policy Name** and **Note** parameters.
4.  Under **Configuration Mode**, select **Script**. Copy and paste the following sample script to the **Policy Document** area, and edit the script based on your business needs. 

    ![Limit the time of accessing Alibaba Cloud resources](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1280574/156689756055096_en-US.png)

    If the following policy is attached to a RAM user, the RAM user can only access ECS instances before 17:00 on August 12, 2019 \(UTC+8\). In this case, the `acs:CurrentTime` parameter in `Condition` is set to `2019-08-12T17:00:00+08:00`.

    ``` {#codeblock_6v5_m94_cvb .lanuage-xml}
    {
      "Statement": [
        {
          "Action": "ecs:*",
          "Effect": "Allow",
          "Resource": "*",
          "Condition": {
              "DateLessThan": {
                  "acs:CurrentTime": "2019-08-12T17:00:00+08:00"
              }
          }
        }
      ],
      "Version": "1"
    }
    ```

    **Note:** The `Condition` setting only applies to the actions that are specified for the current policy. You can change the `2019-08-12T17:00:00+08:00` value if necessary.

5.  Click **OK**.

