# RAM role management {#concept_xvr_ftf_xdb .concept}

This topic describes how to manage RAM roles. RAM roles can be assumed either in the RAM console or through APIs. After creating a RAM role, you can grant permissions to the role so that the role can access specified resources.

**Note:** In this topic, **roles** refer to **RAM roles** unless otherwise specified.

## Create a RAM role {#section_02 .section}

-   Create a RAM role for a trusted **Alibaba Cloud Account**.
    1.  Log on to the [RAM console](https://ram.console.aliyun.com/).
    2.  In the left-side navigation pane, choose **RAM Roles**.
    3.  On the displayed page, click **Create RAM Role**.
    4.  Select **Alibaba Cloud Account** and click **Next**.
    5.  Enter a role name in the **RAM Role Name** field. You can also enter a description in the **Note** field. Then, select a trusted Alibaba Cloud account and click **OK**.
        -   To create a role for RAM users under your account \(for example, authorizing mobile app clients to directly operate on OSS resources\), select **Current Alibaba Cloud Account** as the trusted account.
        -   To create a role for RAM users under another account \(for example, cross-account resource authorization\), select **Other Alibaba Cloud Account** as the trusted account and enter the account ID.
-   Create a RAM role for a trusted **Alibaba Cloud Service**.
    1.  Log on to the [RAM console](https://ram.console.aliyun.com/).
    2.  In the left-side navigation pane, choose **RAM Roles**.
    3.  On the displayed page, click **Create RAM Role**.
    4.  Select **Alibaba Cloud Service** and click **Next**.
    5.  Enter a role name in the **RAM Role Name** field. You can also enter a description in the **Note** field. Then, select a trusted service and click **OK**. Available services include:

        -   Media Transcoding Service: You can create a role, configure MTS as its trusted service, and use MTS to assume the role and access OSS data when you set OSS Bucket as the data source for MTS tasks.
        -   Archive Storage Service: You can create a role, configure OAS as its trusted service, and use OAS to assume the role and access OSS data when you set OSS Bucket as the data source for OAS.
        -   Log Service: You can create a role, configure Log Service as its trusted service, and use Log Service to assume the role and write data into OSS when you import Log Service-collected logs into OSS.
        -   API Gateway: You can create a role, configure API Gateway as its trusted service, and use API Gateway to assume the role and call the function service when you set the function service as the backend service of API Gateway.
        -   Elastic Compute Service: You can create a role and use this role to authorize ECS to access your cloud resources in other cloud services.
        **Note:** For more information about the trusted services, see the RAM console.

-   Create a RAM role for a trusted **IdP**.
    1.  Log on to the [RAM console](https://ram.console.aliyun.com/).
    2.  In the left-side navigation pane, choose **RAM Roles**.
    3.  On the displayed page, click **Create RAM Role**.
    4.  Select **IdP** and click **Next**.
    5.  Enter a role name in the **RAM Role Name** field. You can also enter a description in the **Note** field. Then, select a trusted IdP.
    6.  View the conditions and click **OK**.

        **Note:** In the conditions, only the keyword `saml:recipient` \(which is required and cannot be modified\) is currently allowed. This keyword corresponds to the value of the `Recipient` attribute in the Subject - SubjectConfirmation - SubjectConfirmationData element of the SAML assertion. The value of the condition must be set to `https://signin.alibabacloud.com/saml-role/sso`.


## Edit a RAM role {#section_kng_xxg_chb .section}

On the **RAM Roles** page, click the name of the role you created to view the basic information. On the **Trust Policy Management** tab, click **Edit Trust Policy**. Then, you can change the trusted entity that assumes the role by modifying the 'Principal' element in the policy. The 'Principal' element determines the entrusted entity of the role.

1.  If the 'Principal' element contains a 'RAM' field, the entrusted entity is an Alibaba Cloud account, and the role can be assumed by RAM users under the entrusted account. The following is an example:

    ```
    
    {
    
        "Statement": [
    
            {
                "Action": "sts:AssumeRole",
                "Effect": "Allow",
                "Principal": {
                    "RAM": [
                        "acs:ram::123456789012****:root"
                    ]
                }
            }
        ],
        "Version": "1"
    }
    ```

    The preceding policy indicates that the role can be assumed by any RAM user under the Alibaba Cloud account \(123456789012\*\*\*\*\). If you modify the 'Principal' element as follows, the role can be assumed by the RAM user \(testuser\) under the Alibaba Cloud account \(123456789012\*\*\*\*\):

    ```
    
                "Principal": {
                    "RAM": [
                        "acs:ram::123456789012****:user/testuser"
    
    ```

2.  If the 'Principal' element contains a 'Service' field, the entrusted entity is an Alibaba Cloud service, and the role can be assumed by entrusted Alibaba Cloud services under the current Alibaba Cloud account. The following is an example:

    ```
    
    {
    
        "Statement": [
    
            {
                "Action": "sts:AssumeRole",
                "Effect": "Allow",
                "Principal": {
                    "Service": [
                        "ecs.aliyuncs.com"
                    ]
                }
            }
        ],
        "Version": "1"
    }
    ```

    The preceding policy indicates that the role can be assumed by ECS under the current Alibaba Cloud account.

3.  If the 'Principal' element contains a 'Federated' field, the entrusted entity is an identity provider \(IdP\), and the role can be assumed by users under the entrusted IdP. The following is an example:

    ```
    
    {
    
        "Statement": [
    
            {
                "Action": "sts:AssumeRole",
                "Effect": "Allow",
                "Principal": {
                    "Federated": [
                        "acs:ram::123456789012****:saml-provider/testprovider"
                    ]
                },
                "Condition":{
                    "StringEquals":{
                        "saml:recipient":"https://signin.alibabacloud.com/saml-role/sso"
                    }
                }
            }
        ],
        "Version": "1"
    }
    ```

    The preceding policy indicates that the role can be assumed by users under the IdP \(testprovider\) in the current Alibaba Cloud account \(123456789012\*\*\*\*\).


## Use a RAM role {#section_05 .section}

Roles that are created for an **Alibaba Cloud Service** can be assumed only by trusted cloud services, roles that are created for an **Alibaba Cloud Account** can be assumed by RAM users, and roles that are created for an **IdP** can be assumed by users under the entrusted IdP.

1.  Create a RAM user and create an AccessKey or set a password for the user.
2.  Attach the system policy AliyunSTSAssumeRoleAccess or an STS custom policy to authorize the RAM user.

**Note:** To maintain account security, a trusted Alibaba Cloud account is not allowed to assume roles itself. Roles must instead be assumed by RAM users of the Alibaba Cloud account.

RAM users can assume roles either in the RAM console or through APIs.

-   Assume RAM roles in the RAM console.

    If an entity user wants to assume a RAM role, the entity user must log on to the RAM console and switch their role.

    1.  Log on to the **RAM console** as a RAM user.
    2.  Move the pointer over your account icon in the upper-right corner and click **Switch Role**.
    3.  In the displayed **Switch Role** dialog box, enter the account alias and role name, and then click **Switch**.

        **Note:** 

        -   After switching the role, you can log on to the console as a RAM user with the new RAM role. After you log on, both the current role and identity and the logon identity are displayed in the upper-right corner of the console.
        -   After switching the role, you can only perform operations that are authorized to this role. The access permission of your original identity is hidden when you log on to the console.
    4.  Click **Switch Back to Logon User** to switch back to your logon identity.

        **Note:** After switching to the logon identity, you will obtain the original permissions and lose the permissions associated with the role.

-   Assume RAM roles through APIs.

    After being granted the AssumeRole permission, a RAM user can use its AccessKey to call the AssumeRole API action of Security Token Service \(STS\) to obtain the temporary security token of a role. Then, the user uses the token to access cloud resource APIs.

    For more information about how to call the AssumeRole API action, see [AssumeRole](../../../../../intl.en-US/API Reference (STS)/Operation interfaces/AssumeRole.md).


## What to do next {#section_qgj_y1k_pgb .section}

After creating a role, you can click **Add Permissions to RAM role** to grant permissions to this role. For more information, see [Permission granting in RAM](intl.en-US/User Guide/Permission management/Permission granting/Permission granting in RAM.md#).

