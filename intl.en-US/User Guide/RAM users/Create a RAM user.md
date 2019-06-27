# Create a RAM user {#task_187540 .task}

A RAM user is an entity that you create in Alibaba Cloud to represent the person or application to interact with Alibaba Cloud. You can create a RAM user and grant it the relevant permissions to access the necessary Alibaba Cloud resources.

1.  Log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram).
2.  Choose **Identities** \> **Users**.
3.  Click **Create User**, and enter the logon name and display name. 

    **Note:** You can click **Add User** to create multiple RAM users at a time.

4.  Select an access mode. The available access modes are **Console Password Logon** and **Programmatic Access**. 

    -   **Console Password Logon**: If you select this check box, you must also complete the basic security settings for logon, including deciding whether to automatically generate a password or customize the logon password, setting whether the user must reset the password upon the next logon, and setting whether to enable multi-factor authentication \(MFA\).
    -   **Programmatic Access**: If you select this check box, an access key is automatically created for the RAM user. The user can access Alibaba Cloud resources by calling an API action or by using a development tool.
    **Note:** We recommend that you set only one access mode for the user to maintain the security of your Alibaba Cloud account.

5.  Click **OK**.

-   You can add the RAM user to one or more RAM user groups and grant permission to the user as needed. For more information, see [Add RAM users to a group](reseller.en-US/User Guide/RAM user groups/Add RAM users to a group.md#).
-   You can also attach one or more policies to the RAM user to grant the user access permission. For more information, see [Grant permission to a RAM user](reseller.en-US/User Guide/RAM users/Grant permission to a RAM user.md#).

