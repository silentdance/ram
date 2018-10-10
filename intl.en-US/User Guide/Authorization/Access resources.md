# Access resources {#concept_wbc_21g_xdb .concept}

After authorization, RAM users can access the relevant resources through the console or the API. RAM users can also switch identities after logging on to the console, or call AssumeRole to obtain the role token \(STS\) to act as a relevant role and manipulate related resources as the role.

## Access resources on the console {#section_qpw_21g_xdb .section}

The RAM user logon requires an independent logon URL \(which can be viewed on the RAM console\). Use the **primary account enterprise alias**, **username**, and **password** to log on to the console. After successfully logging on, the user can perform operations on the authorized resources. If the user attempts to perform an operation that they do not have permission for, the error message “No operation permissions” is displayed.

If a RAM user is allowed to assume a role:

-   After logon, the user can use the **Switch Role** operation to switch from the current logon identity to a role identity. In this way, the user can use the permissions of the newly selected role to perform operations on resources.

-   If the user wants to switch back to the logon identity, the user can use the **Return to Logon Identity** operation.


For more information about roles, see [Role](intl.en-US/User Guide/Identities/Role.md).

## Access resources from calling APIs {#section_spw_21g_xdb .section}

For the application that calls cloud service APIs to perform resource operations, you create a RAM user account for this application and grant it relevant permissions. Then, create an AccessKey for this RAM user, which is used by the application to call cloud service SDKs and APIs.

## Access resources by using a client tool {#section_tpw_21g_xdb .section}

Some cloud services provide easy-to-use client tools, for example, aliyuncli. These tools allow the usage of RAM user AccessKeys to perform cloud resource operations.

The following is an example of the OSS service. Assuming that the RAM user is authorized to access a bucket, you can then use the OSS client tool [ossbrowser](http://oss.aliyuncs.com/ossbrowserupdate/ossbrowser.jar) to access the specified bucket.

The operation procedure is as follows:

1.  Open ossbrowser and set the account and password to AccessKeyId and AccessKeySecret, respectively.
2.  After logging on, enter the ossbrowser interface. Select the **Authorized Bucket** tab and click **Add** to add an authorized bucket. Then, you can manipulate the content of the authorized bucket.

