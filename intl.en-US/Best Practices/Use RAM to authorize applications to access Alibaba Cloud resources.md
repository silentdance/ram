# Use RAM to authorize applications to access Alibaba Cloud resources {#concept_xdg_1vc_mfb .concept}

This topic describes how to use RAM to authorize applications to access Alibaba Cloud resources by obtaining the temporary STS token of a RAM role.

## Scenario {#section_01 .section}

An enterprise has bought ECS instances and wants to deploy its applications in ECS. To allow the applications to access other Alibaba Cloud APIs by using access keys, the enterprise can use one of the following methods:

-   Embed the access keys into the code.
-   Save the access keys in the configuration files of the applications.

However, if the preceding methods are used, the following issues occur:

-   Access key disclosure: If the access keys are embedded in the ECS instances in plaintext, they can be mistakenly disclosed to another user due to the sharing of a snapshot, or an image to create a shared image instance.
-   O&M complexity: If the access keys are changed \(due to access key rotation or changes to user identities\), all instances and images need to be updated and redeployed because the access keys exist in the ECS instances. As a result, the management of instances and images is highly complex.

## Solution {#section_02 .section}

To resolve the preceding issues, the enterprise can combine ECS with the access control feature of RAM. Specifically, the administrator creates a RAM role for each ECS instance \(that is, the operating environment of the applications\) and grants each RAM role appropriate permissions. The applications can use the temporary STS token of the corresponding RAM role to call other Alibaba Cloud APIs.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23777/156586485514410_en-US.png)

1.  The enterprise uses its Alibaba Cloud account to create a RAM role \(`MyApplicationRole`\).

    **Note:** The preceding role is an Alibaba Cloud service in which ECS is selected as the trusted service.

    For information about how to create a RAM role, see [Create a RAM role for a trusted Alibaba Cloud service](../../../../reseller.en-US/User Guide/RAM roles/Create a RAM role/Create a RAM role for a trusted Alibaba Cloud service.md#).

2.  The enterprise uses its Alibaba Cloud account to grant relevant permissions to the RAM role.

    For information about how to grant permission to a RAM role, see [Grant permission to a RAM role](../../../../reseller.en-US/User Guide/RAM roles/Grant permission to a RAM role.md#).

    **Note:** If the temporary STS token does not have corresponding permissions, the enterprise needs to attach related policies to the RAM role. After the policies attached to the RAM role are updated, the permissions associated with the temporary STS token take effect immediately and the user does not need to restart the ECS instance.

3.  The enterprise uses its Alibaba Cloud account to create a RAM user.

    For information about how to create a RAM user, see [Create a RAM user](../../../../reseller.en-US/User Guide/RAM users/Create a RAM user.md#).

4.  The enterprise uses its Alibaba Cloud account to grant relevant permissions to the RAM user.

    -   If the administrator and the RAM user have the same responsibilities, the `AdministratorAccess` permission should be granted to the user.
    -   If the administrator and the RAM user have different responsibilities, the `PassRole` permission should be granted to the user.

        The enterprise uses its Alibaba Cloud account to create a custom policy in the RAM console and attach the policy to the RAM user. The policy content is as follows:

        ``` {#codeblock_srz_5i6_mpu}
        {
           "Statement": [
            {
              "Effect": "Allow",
              "Action": "ram:PassRole",
              "Resource": "acs:ram:*:*:role/MyApplicationRole"//Replace MyApplicationRole with the name of your RAM role.
            }
          ],
          "Version": "1"
        }                
        ```

        **Note:** 

        -   Only authorized RAM users can configure RAM roles for ECS instances. In this way, the use of RAM roles is strictly controlled, which helps to prevent any abuse of permission usage.
        -   Before a RAM user \(for example, a RAM user that only has access to ECS and is not a RAM permission administrator\) creates an ECS instance and configures a RAM role, ECS checks whether the RAM user has the `ram:PassRole` permission of the RAM role. If no permission is found, the RAM user cannot create an ECS instance.
    For information about how to create a custom policy, see [Create a custom policy](../../../../reseller.en-US/User Guide/Policies/Custom policies/Create a custom policy.md#).

    For information about how to grant permission to a RAM user, see [Grant permission to a RAM user](../../../../reseller.en-US/User Guide/RAM users/Grant permission to a RAM user.md#).

5.  The RAM user starts the ECS instance and then configures the RAM role.
6.  ECS calls the AssumeRole action of the STS API to obtain the temporary STS token of the RAM role.

    **Note:** STS verifies the identity of ECS and the policies attached to the RAM role. If the verification succeeds, a temporary STS token is issued. If the verification fails, the request is denied.

    For information about how to use a RAM role by calling an STS API action, see [Use the instance RAM role by calling APIs](../../../../reseller.en-US/Security/Instance RAM roles/Use the instance RAM role by calling APIs.md#).

7.  STS returns the temporary STS token to ECS.
8.  ECS sends the temporary STS token to applications in the ECS instance by using the instance metadata.

    -   In Linux, the temporary STS token and its validity period can be obtained by using the instance metadata. For more information, see [Access other Alibaba Cloud APIs by using instance RAM roles](../../../../reseller.en-US/Best Practices/Access other Cloud Product APIs by the Instance RAM Role.md#).

        Request example:

        ``` {#codeblock_f3j_2uh_9xw}
        $ curl http://100.100.100.200/latest/meta-data/ram/security-credentials/MyApplicationRole
        ```

        Response example

        ``` {#codeblock_7ai_75w_sg6}
        [root@local ~]# curl http://100.100.100.200/latest/meta-data/ram/security-credentials/MyApplicationRole
        {
        "AccessKeyId" : "STS.J8XXXXXXXXXX4",
        "AccessKeySecret" : "9PjfXXXXXXXXXBf2XAW",
        "Expiration" : "2017-06-09T09:17:19Z",
        "SecurityToken" : "CAIXXXXXXXXXXXwmBkleCTkyI+",
        "LastUpdated" : "2017-06-09T03:17:18Z",
        "Code" : "Success"
        }cess"
        }
        ```

    -   If the applications use an Alibaba Cloud SDK, the Alibaba Cloud SDK can obtain the STS token of the RAM role from the ECS instance metadata, and you do not need to configure any access key-related information in the SDK.
    **Note:** The applications can access Alibaba Cloud APIs when the temporary STS token is within the validity period. The STS token usually expires after one hour. ECS automatically refreshes the STS token before it expires.

9.  The applications use the STS token to access Alibaba Cloud APIs.

## What to do next {#section_n3k_rgx_pgb .section}

If Alibaba Cloud RAM does not meet all of your permission application requirements, you can use other Alibaba Cloud services, such as Function Compute and MaxCompute, that provide the access control features to authorize applications to access your Alibaba Cloud resources.

