# Role {#concept_xvr_ftf_xdb .concept}

Like a RAM-User, a RAM-Role is also a type of RAM identity. Compared with a RAM-User, a RAM-Role is a virtual user, that is, a RAM-Role has no identity credentials and has to be assumed by a trusted Alibaba Cloud account.

With this document, you can gain a better understanding of the RAM-Role, and know how to create and use a RAM-Role.

**Note:** Unless otherwise stated, the **role** in this document represents a **RAM-Role**.

## Understanding RAM-Role {#section_fmj_gtf_xdb .section}

A RAM-Role is a virtual user \(or shadow account\). It is a type of RAM identity.

-   A RAM-Role differs from a Textbook-Role. A Textbook-Role \(or a role as traditionally defined\) indicates a set of permissions. It is similar to a policy in RAM. If a role is granted to a user, this means that the corresponding permissions are granted to the user. Then, this user can access the authorized resources.
-   As a type of virtual user, a RAM-Role has a fixed identity and can be granted policies. However, it does not have a fixed security credential \(such as a logon password or an AccessKey\).

    **Virtual users vs. Real users**: The difference between a virtual user and a real user is that a real user identity can be directly authenticated.

    -   A real user has a logon password or an AccessKey. For example, Alibaba Cloud accounts, RAM-User accounts, and cloud service accounts are real users.
    -   However, a virtual user, such as a RAM-Role, does not have a fixed security credential.
-   RAM-Roles must be assumed by an authorized real user. After assuming a role, the real user receives a temporary security token for this RAM-Role. Then, the user can use this temporary security token to access the resources authorized for the role.


## Notes {#section_jmj_gtf_xdb .section}

A RAM-Role must be **associated** with a real user identity so that it becomes available.

-   If a real user wants to use a RAM-Role that has been granted to the user, the real user must first log on using his identity and then perform the **SwitchRole** operation to switch from **a real identity** to **a role identity**.

    **Note:** The user can then perform all operations authorized for this role identity, but the access permissions of the user’s real identity will not be available.

-   To switch from **the role identity** back to **the real identity**, the user must perform the **Switch Back to Logon Identity** operation.

    **Note:** Then, the user can have the access permissions granted to his real identity, but not those of the role.


## Concepts {#section_mmj_gtf_xdb .section}

The following table lists several basic concepts related to RAM-Roles:

|Concept|Meaning|
|:------|:------|
|RoleARN|A RoleARN is the global resource description of a role. It is used to specify a role.-   RoleARNs follow Alibaba Cloud ARN naming rules. For example, the RoleARN for the devops role under an Alibaba Cloud account is: `acs:ram::1234567890123456:role/samplerole`.
-   After a RAM-Role is created, the role’s ARN is displayed on the Role Details page.

|
|Trusted Actors|A role’s trusted actors are the real user identities \(the current Alibaba Cloud account or another Alibaba Cloud account\) that can assume this role.-   When creating a role, you must specify the trusted actors. A role can only be assumed by trusted actors.
-   A trusted actor can be a trusted cloud account or a trusted service.

|
|Policy|A role can be attached with a set of permissions, that is, a policy. Roles not attached with policies can exist, but cannot be used.|
|Assume Role|By performing the assume role operation, a real user can obtain a security token for a role. By calling the AssumeRole API, a real user obtains the role’s security token and can use this token to access cloud service APIs.|
|Switch Role|By performing the switch role operation on the console, a real user can switch from the current logon identity to a role identity.-   After a real user logs on to the console, the user can switch to a role for which he is a trusted actor. Then, the user can use the role identity to perform operations on cloud resources. After switching to a role identity, the user's real identity access permissions are no longer available.
-   When the user no longer needs to use a role, he can switch from the role back to the original logon identity.

|
|Role Token|A role token is a temporary AccessKey for the role identity. Role identities do not have fixed AccessKeys. Therefore, when a real user wants to use a role, he or she must assume the role to obtain the corresponding role token. Then, the user can use this role token to call Alibaba Cloud service APIs.|

## Application scenarios {#section_smj_gtf_xdb .section}

RAM-Role is mainly used to entrust other cloud accounts and their RAM users as well as cloud services to operate on your cloud resources.

## Cross-account resource operation and authorization management {#section_tmj_gtf_xdb .section}

Scenario description: Enterprise A and Enterprise B represent two different companies. Enterprise A has purchased a variety of cloud resources \(for example, ECS instances, RDS instances, SLB instances, OSS buckets, etc.\) to conduct business.

|Requirement|Solution|
|:----------|:-------|
|Enterprise A wants to focus on its business systems, so it authorizes Enterprise B to perform the tasks of maintaining, monitoring, and managing cloud resources.|Alibaba Cloud account A creates a role in RAM and grants this role the necessary permissions. Then, it allows Alibaba Cloud account B to use this role.|
|Enterprise B assigns the entrusted maintenance tasks to its employees. B needs to precisely control the permissions assigned to its employees who operate on A's resources.|If account B has employees \(RAM-Users\) who need to use this role, it can independently control their permissions. When performing O&M operations on behalf of A, account B’s RAM-users can use the role identity to perform operations on A’s resources.|
|If A and B terminate this O&M entrustment contract, enterprise A is able to revoke the permissions of the enterprise B as needed.|If accounts A and B terminate their contract, A just needs to revoke B’s permission to use this role. Once account B’s permission to use this role is revoked, all RAM-Users of account B will automatically lose their permission to use this role.|

## Temporary authorization access {#section_vmj_gtf_xdb .section}

Scenario description: Assume that Enterprise A has developed a mobile app and has bought OSS. The mobile app must upload and download data to and from OSS, but A does not want to allow all apps to use the AppServer to transmit data. Because the mobile app runs on user devices, these devices are out of A’s control. For security reasons, A cannot save the AccessKey in the app.

|Requirement|Solution|
|:----------|:-------|
|Enterprise A does not want all apps to transmit data through the AppServer. Instead, A wants to allow the apps to directly upload and download data to and from OSS.| -   Alibaba Cloud account A creates a role in RAM and grants this role the necessary permissions. Then, it allows the AppServer \(giving it a RAM user identity\) to use this role.
-   When the app needs to directly connect to OSS to upload and download data, the AppServer can use this role to obtain the role’s temporary security token and send it to the app. The app can then use the temporary security token to directly access OSS APIs.

 |
|Enterprise A wants to minimize its security risks by, for example, giving each app an access token with only the minimum permissions it needs when directly connected to OSS and restricting the access duration to a short period of time \(such as 30 minutes\).| -   If more precise control over the permissions of each app is required, when using the role, the AppServer can further restrict the resource operation permissions of the temporary security token.
-   For example, when assuming the role, the AppServer can restrict that different app users can perform operations only on a few subdirectories.

 |

## Entrust cloud services to operate on your cloud resources {#section_ymj_gtf_xdb .section}

Scenario description: Enterprise A has purchased the ECS server and has deployed an application in it. The application needs to access A's OSS bucket. In most cases:

-   Cloud account A saves its AccessKey \(AK\) in the application's configuration file, and modifies the file when periodically replacing the AK.

-   In the case of multi-region consistency deployment, the AK is spread out with the images and the instances created with the images. If this happens, when A needs to replace the AK, it is necessary to update and redeploy the instances and images one by one.


|Requirement|Solution|
|:----------|:-------|
| -   For security reasons, A does not want its application to get full access to its API operations through the AK. Instead, A expects the application to access the APIs of other products with the STS.
-   For operational considerations, A does not want to update the AK on the application, and does not want to maintain the AK in multiple regions.

 |With the RAM service role:-   Cloud account A creates an ECS service role \(assumed by ECS instances only\) in RAM, grants appropriate permissions to the role \(such as read-only access to OSS\), and associates the service role with its ECS instance.
-   After the ECS instance is connected, the STS of the service role is obtained by accessing the metadata of the ECS instance. The application in the ECS server uses the STS to access the OSS.

|

**Note:** The RAM service role can be used for authorization operations in cross-product scenarios, such as authorizing the EMR to operate on the customer's ECS, the FC to operate on the customer's OSS, and the MTS to operate on the customer's OSS data. For all service role types and scenarios provided by RAM, see [Create a service role](#).

**About the PassRole permission for RAM**

In order to limit what a service can do on your behalf, you need to configure a RAM role for the service. The service will perform the relevant operations as the corresponding RAM role and is limited by the administrator's authorization for the RAM role. For example, you can configure a RAM role for an ECS instance, and the application in the ECS instance can obtain the STS of the corresponding RAM role to access Alibaba Cloud APIs.

When a RAM user configures a RAM role for a cloud service, the RAM user must have the PassRole permission for the RAM role. Once the cloud service receives a request for RAM role configuration, a mandatory check will be performed to see if the RAM user has the ram:PassRole permission for the specified RoleArn. This ensures that only authorized users can configure RAM roles for cloud services, without causing abuse of RAM role permissions.

## RAM role types {#section_dnj_gtf_xdb .section}

RAM supports two types of roles:

-   **User role**: role that can be assumed by RAM users. RAM users permitted to assume roles can belong to your Alibaba Cloud account or another Alibaba Cloud account. User roles are used to solve problems such as cross-account access and temporary authorization access.
-   **Service role**: role that can be assumed by cloud services. Service roles are used to authorize cloud services to perform operations on resources on your behalf.

## Create a RAM role {#section_fnj_gtf_xdb .section}

To create a RAM role in the RAM console, perform the following steps:

1.  Select the role type.
2.  Select the trusted actor.
3.  Enter the role name.
4.  Bind an authorization policy to the role.

## Create a user role {#section_hnj_gtf_xdb .section}

The procedure is as follows:

1.  Log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram).
2.  In the left navigation pane, click **Roles**.
3.  On the **Role Management** page, click **Create Role**.
4.  On the **Select Role Type** page, click **User Role**.
5.  On the **Enter Type Information** page, do one of the following and click **Next**.
    -   If the role is to be used by the RAM-Users under your own account \(such as authorizing a mobile app client to directly perform operations on OSS resources\), select your **Current Alibaba Cloud Account** as the trusted Alibaba Cloud account.
    -   If the role is to be used by the RAM-Users under another Alibaba Cloud account \(such as for cross-account resource authorization access\), select **Other Alibaba Cloud Account** and enter its ID in the **Trusted Alibaba Cloud Account ID** field.
6.  On the **Configure Basic Role Information** page, enter a **Role Name** \(the description is optional\) and click **Create**.
7.  After you have successfully created a role, you can click **Authorize** to grant permissions to the role or click **Close**. For details, see [Authorization](reseller.en-US/User Guide/Authorization/Authorization.md).

Now you have created the user role.

Go back to the [Role Management](https://partners-intl.console.aliyun.com/#/ram/role/list) page and you can find the newly created role in the role list. Click the **Role Name** or the corresponding **Manage** in the **Actions** column to enter the **Role Details** page, where you can find the role’s ARN and can **Edit Basic Information**.

## Create a service role {#section_nnj_gtf_xdb .section}

The procedure is as follows:

1.  In the RAM console, click **Roles** in the left navigation pane.
2.  On the **Role Management** page, click **Create Role**.
3.  On the **Select Role Type** page, click **Service Role**. Available service roles include the following:
    -   MTS Media Transcoding. When setting the OSS Bucket to the data source for the MTS service, create a role with MTS as the trusted service and use the MTS service to assume this service role to access data in the OSS.
    -   OAS Archive Storage. When setting the OSS Bucket to the data source for the archive storage service, create a role with archive storage as the trusted service and use the archive storage service to assume this service role to access data in the OSS.

    -   LOG Log Service. When importing logs collected by the log service into the OSS, create a role with log service as the trusted service and use the log service to assume this service role to write data into the OSS. 

    -   ApiGateway Service. When setting the function service to a backend service for an API gateway, create a role with API gateway as the trusted service and use the API gateway service to assume this service role to call the function service.

    -   ECS Elastic Compute Service, which is used to authorize the ECS service to access your cloud resources in other cloud services.

4.  On the **Enter Type Information** page, select a service as the trusted service.
5.  On the **Configure Basic Role Information** page, enter a **Role Name** \(the description is optional\) and click **Create**.
6.  After you have successfully created a role, you can click **Authorize** to grant permissions to the role or click **Close**. For details, see [Authorization](reseller.en-US/User Guide/Authorization/Authorization.md).

Now you have created the service role.

Go back to the [Role Management](https://partners-intl.console.aliyun.com/#/ram/role/list) page and you can find the newly created role in the role list. Click the **Role Name** or the corresponding **Manage** in the **Actions** column to enter the **Role Details** page, where you can find the role’s ARN and can **Edit Basic Information**.

## Use a RAM role {#section_snj_gtf_xdb .section}

**A RAM role can only be assumed by RAM users in the trusted Alibaba Cloud account.** For security reasons, the trusted Alibaba Cloud accounts are not allowed to perform AssumeRole.

Therefore, you must use a trusted account to create a RAM-User account, and grant the AssumeRole permission to the RAM-User account. Then, you can assume the role by using this RAM-User identity.

The procedure is as follows:

1.  Create a RAM-User and create an AccessKey or set a logon password for this user.
2.  Grant the following system authorization policy to this RAM-User: `AliyunSTSAssumeRoleAccess`

## Use a RAM role to perform console operations {#section_unj_gtf_xdb .section}

If a RAM-User needs to use the role identity to perform console operations, the RAM-User must first log on to the console with the logon identity, and then use the **SwitchRole** method. After that, the user can use the role identity to perform console operations.

For example, the RAM-User Alice under company2 \(enterprise alias\) logs on to the console, the user can move the mouse pointer to the account name on the upper-right corner and click **Switch Role**.

-   Alice needs to select the corresponding company alias and role name. For example, we assume that the user has been granted permission to assume the **ecs-admin** role of company1 \(enterprise alias\).

-   After switching to the role, Alice can use the role identity to access the console.


## Use a RAM role to access APIs {#section_znj_gtf_xdb .section}

After a RAM-User is granted the AssumeRole permission, the user can use the AccessKey to call the STS AssumeRole API to obtain a temporary security token for this role. For details about how to call the AssumeRole API, see API documentation.

