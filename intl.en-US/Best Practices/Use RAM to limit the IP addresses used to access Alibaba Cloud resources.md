# Use RAM to limit the IP addresses used to access Alibaba Cloud resources {#task_1614402 .task}

This topic describes how to use RAM to limit the IP addresses that are used to access Alibaba Cloud resources. This feature of RAM enables a higher level of security.

-   An Alibaba Cloud account is created. If not, create one before proceeding. To create an Alibaba Cloud account, click [Create a new Alibaba Cloud account](https://account.alibabacloud.com/register/intl_register.htm).
-   The RAM service is activated, and you can log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram). If the RAM service is not activated, activate the service before proceeding. For more information, see [Activation methods](../../../../reseller.en-US/Pricing/Activation methods.md#).
-   You have a basic knowledge of the policy elements, structure, and syntax before creating a custom policy. For more information, see [Policy elements](../../../../reseller.en-US/User Guide/Policies/Policy language/Policy elements.md#) and [Policy structure and grammar](../../../../reseller.en-US/User Guide/Policies/Policy language/Policy structure and grammar.md#).

Enterprise A has purchased more than one type of Alibaba Cloud resources, such as ECS instances, RDS instances, SLB instances, and OSS buckets. To ensure business and data security, this enterprise wants to only allow RAM users to access Alibaba Cloud resources from its IP addresses of the corporate intranet.

## Solution {#section_7fb_2lv_k12 .section}

To only allow RAM users to access Alibaba Cloud resources from the specified IP addresses, create and attach a custom policy for the RAM users.

1.  [Create a RAM user](../../../../reseller.en-US/User Guide/RAM users/Create a RAM user.md#).
2.  [Create a custom policy](#section_9ti_0x8_228).
3.  [Grant permission to a RAM user](../../../../reseller.en-US/User Guide/RAM users/Grant permission to a RAM user.md#).

## Create a custom policy {#section_9ti_0x8_228 .section}

1.  In the left-side navigation pane, click **Policies** under **Permissions**.
2.  On the Policies page, click **Create Policy**.
3.  On the page that appears, specify the **Policy Name** and **Note** parameters.
4.  Under **Configuration Mode**, select **Script**. Copy and paste the following sample script to the **Policy Document** area, and edit the script based on your business needs. 

    ![Limit the IP addresses used for accessing Alibaba Cloud resources](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1280070/156689737954965_en-US.png)

    If the following policy is attached to a RAM user, the RAM user can only access ECS instances from the IP addresses in the CIDR block range of 192.168.0.0/16. In this case, the `acs:SourceIp` parameter in `Condition` is set to `192.168.0.0/16`.

    ``` {#codeblock_3ci_blk_288 .lanuage-xml}
    {
      "Statement": [
        {
          "Action": "ecs:*",
          "Effect": "Allow",
          "Resource": "*",
          "Condition": {
            "IpAddress": {
              "acs:SourceIp": "192.168.0.0/16"
            }
          }
        }
      ],
      "Version": "1"
    }
    ```

    **Note:** The `Condition` setting only applies to the actions that are specified for the current policy. You can change the `192.168.0.0/16` CIDR block to the IP address of your corporate intranet.

5.  Click **OK**.

