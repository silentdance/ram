# Operations on resources {#concept_wbc_21g_xdb .concept}

After being authorized, RAM users can access the relevant Alibaba Cloud resources through the console or APIs. RAM users can also switch identities after logging on to the console, or call the AssumeRole API action to obtain the STS token to act as a relevant RAM role and operate related resources as the role.

## RAM users operate resources in the console {#section_qpw_21g_xdb .section}

RAM users log on to the console through an independent logon URL \(which can be obtained from the **Dashboard** page of the RAM console\). Then, RAM users can operate authorized Alibaba Cloud resources. If RAM users attempt to operate an unauthorized Alibaba Cloud resource, an error message indicating no operation permissions will be displayed.

If a RAM user is allowed to assume a RAM role, the user can:

-   Click **Switch Role** to switch from the current logon identity to the role identity. Then, the user can use the role permissions to operate Alibaba Cloud resources.
-   Click **Return to Logon Identity** to switch back to its logon identity. Then, the user can operate Alibaba Cloud resources as its logon identity.

For more information about RAM roles, see [RAM roles](reseller.en-US/User Guide/(Old Version) User Guide/Identities/RAM roles.md#).

## Applications operate resources by calling APIs {#section_spw_21g_xdb .section}

If your application needs to call Alibaba Cloud API actions, you need to create a RAM user for the application and grant it relevant permissions. Then, create an AccessKey \(AK\), which can be used by the application to call Alibaba Cloud SDK or API actions.

## RAM users operate resources by using a client tool {#section_tpw_21g_xdb .section}

Some Alibaba Cloud services provide easy-to-use client tools for RAM users to use AKs to operate Alibaba Cloud resources.

The following uses OSS as an example. Assume that a RAM user is authorized to access a bucket. Then, you can use the OSS client tool [ossbrowser](http://oss.aliyuncs.com/ossbrowserupdate/ossbrowser.jar) to access the bucket.

The procedure is as follows:

1.  Open ossbrowser and set the account and password to the RAM user's AccessKeyId and AccessKeySecret, respectively.
2.  Click **Authorized Bucket** and click **Add** to add an authorized bucket. Then, you can operate the bucket.

