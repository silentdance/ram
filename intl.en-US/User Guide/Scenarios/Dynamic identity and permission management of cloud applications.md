# Dynamic identity and permission management of cloud applications {#concept_xdg_1vc_mfb .concept}

This topic describes how to use Alibaba Cloud RAM to allow applications to access Alibaba Cloud APIs by obtaining the dynamic STS token of a RAM role.

## Scenario {#section_01 .section}

An enterprise has bought ECS instances and wants to deploy its applications in ECS. To allow the applications to access other Alibaba Cloud APIs by using AccessKeys, the enterprise can use one of the following methods:

-   Embed the AccessKeys into the code.
-   Save the AccessKeys in the configuration files of the applications.

However, if the preceding methods are used, the following issues occur:

-   AccessKey disclosure: If the AccessKeys are embedded in the ECS instances in plaintext, they can be mistakenly disclosed to another user due to the sharing of a snapshot, or an image to create a shared image instance.
-   O&M complexity: If the AccessKeys are changed \(due to AccessKey rotation or changes to user identities\), all instances and images need to be updated and redeployed because the AccessKeys exist in the ECS instances. As a result, the management of instances and images is highly complex.

## Solution {#section_02 .section}

To resolve the preceding issues, you can combine ECS with the access control feature of RAM. Specifically, the administrator creates a RAM role for each ECS instance \(that is, the operating environment of the application\) and grants each RAM role appropriate permissions. The applications can use the dynamic STS token of the corresponding RAM role to call other Alibaba Cloud APIs.

![Process](images/14409_en-US.png "Process")

## Configure a RAM role for an ECS instance {#section_03 .section}

1.  The administrator uses the Alibaba Cloud account to create an ECS instance RAM role and attach appropriate policies to the RAM role.

    **Note:** An ECS instance RAM role is a type of RAM service role that is created by a user and used by the ECS instance of the user after authorization.

2.  The administrator starts the ECS instance and configures the RAM role.

    -   \(i\) ECS calls the AssumeRole API according to the configured RAM role to access STS and sends a request to obtain the STS token of the RAM role.
    -   \(ii\) STS verifies the identity of ECS and the policies attached to the RAM role. If the verification succeeds, a STS token is issued. If the verification fails, the request is denied.
    For more information, see [Use the instance RAM role in the console](../../../../../reseller.en-US/Security/Instance RAM roles/Use the instance RAM role in the console.md#) or [Use the instance RAM role by calling APIs](../../../../../reseller.en-US/Security/Instance RAM roles/Use the instance RAM role by calling APIs.md#).

3.  Upon obtaining the STS token, the ECS instance provides the STS token to its applications through the Metadata service.

    For example, the following command can be used in Linux to obtain metadata information such as the STS token and its validity period:

    ```
    $ curl http://100.100.100.200/latest/meta-data/ram/security-credentials/<roleName>
    ```

    **Note:** 

    -   The applications can call Alibaba Cloud APIs when the STS token is within the validity period. The STS token usually expires after one hour. ECS automatically refreshes the STS token before it expires.
    -   If the STS token does not have corresponding permissions, the administrator needs to attach related policies to the RAM role.
    -   After the policies attached to the RAM role are updated, the permissions associated with the STS token take effect immediately and the user does not need to restart the ECS instance.
4.  The applications use the STS token to call Alibaba Cloud APIs.

    **Note:** If the applications use Alibaba Cloud SDK, the Alibaba Cloud SDK can obtain the STS token of the RAM role from the ECS Metadata service, and the developers do not need to configure any sensitive AccessKey-related information in the SDK.

    For more information, see [Configure RamRole to achieve non-AccesKey access to ECS instances](../../../../../reseller.en-US/Java SDK/Use SDK/Configure RamRole to achieve non-AK access to ECS instances.md#).


## Separate permissions of administrators and general users {#section_04 .section}

In most scenarios, the permissions of the administrator and a typical ECS instance user are configured as different RAM users. The following figure shows how to separate the permissions of the administrator and a general user.

![Process](images/14410_en-US.png "Process")

**Notice:** 

-   Before a RAM user \(for example, a RAM user that only has access to ECS and is not a RAM permission administrator\) creates an ECS instance and configures a RAM role, ECS checks whether the RAM user has the `ram:PassRole` permission of the RAM role. If no permission is found, the RAM user cannot create an ECS instance.
-   Only authorized users can configure RAM roles for ECS instances. In this way, the use of RAM roles is strictly controlled, which helps to prevent any abuse of permission usage.

To separate the permissions of the administrator and the general user, you need to [configure a RAM role for an ECS instance](#) and grant the `PassRole` permission to the general user, as shown in Step 1.5 in the preceding figure.

The administrator can also create a custom policy and attach the policy to the general user. The following is an example:

**Notice:** The `rolename` must be replaced with the RAM name.

```


{
   "Statement": [
    {
      "Effect": "Allow",
      "Action": "ram:PassRole",
      "Resource": "acs:ram:*:*:role/<rolename>"
    }
  ],
  "Version": "1"
}

```

## What to do next {#section_n3k_rgx_pgb .section}

If Alibaba Cloud RAM does not meet all of your permission application requirements, you can use other Alibaba Cloud services, such as Function Compute and MaxCompute, that provide the access control features to help manage the identities and AccessKeys of your users and applications on the cloud.

