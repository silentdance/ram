# Assume a RAM role {#task_221553 .task}

This topic describes how to assume a RAM role by using a RAM user under a trusted Alibaba Cloud account.

**Note:** To maintain account security, a trusted Alibaba Cloud account is not allowed to assume RAM roles itself. RAM roles must instead be assumed by RAM users of the Alibaba Cloud account.

1.  A RAM user is created. For information about how to create a RAM user, see [Create a RAM user](reseller.en-US/User Guide/RAM users/Create a RAM user.md#).
2.  An access key or a password is set for the RAM user.
    -   For information about how to create an access key, see [Create an access key for a RAM user](reseller.en-US/User Guide/Security settings/Access keys/Create an access key for a RAM user.md#).
    -   For information about how to set a password, see [Change the password for an Alibaba Cloud account](reseller.en-US/User Guide/Security settings/Passwords/Change the password for an Alibaba Cloud account.md#).
3.  The system policy `AliyunSTSAssumeRoleAccess` is attached to the RAM user. For information about how to grant permission to a RAM role, see [Grant permission to a RAM role](reseller.en-US/User Guide/RAM roles/Grant permission to a RAM role.md#).

1.  Log on to the as a RAM user.
2.  Move the pointer over the account icon in the upper-right corner and click **Switch Role**.
3.  On the displayed Switch Role page, enter the enterprise alias or the default domain name in the **Enterprise Alias/Default Domain Name** filed and the RAM role name in the **Role Name** field. Then, click **Switch**.
4.  Click **Switch Back to Logon User** to switch back to your logon identity. 

    **Note:** After you switch to the logon identity, you will obtain the original permissions and lose the permissions associated with the RAM role.


A RAM user can also assume a RAM role by calling an API action. After being granted the `AliyunSTSAssumeRoleAccess` policy, a RAM user can use its access key to call the [AssumeRole](../../../../reseller.en-US/API Reference (STS)/Operation interfaces/AssumeRole.md#) action of the Security Token Service \(STS\) to obtain the temporary security token of a role. Then, the user uses the token to access Alibaba Cloud APIs.

