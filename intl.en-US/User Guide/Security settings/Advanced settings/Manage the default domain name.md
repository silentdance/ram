# Manage the default domain name {#task_221524 .task}

This topic describes how to view or change the default domain name of an Alibaba Cloud account. Each Alibaba Cloud account has a default domain name, and the domain name can be used by its RAM users to log on to the RAM console. You can customize the logon name suffix by changing the default domain name.

1.  Log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram) by using your Alibaba Cloud account.
2.  In the left-side navigation pane, click **Identities**, and click **Settings**.
3.  Click the **Advanced** tab. In the **Default Domain**section, you can: 
    -   View the default domain name of your Alibaba Cloud account. The format of the default domain name is `<$AccountAlias>.onaliyun.com`. By default, the AccountAlias is your Alibaba Cloud account ID. If you have not specified an account alias, the format of the default domain name is `<$AccountID>.onaliyun.com`.
    -   Update the domain name. Click **Update**, enter an account alias, and then click **OK**.

RAM users then can use the updated domain name to log on to the RAM console.

To log on to the RAM console as a RAM user by using the updated domain name, enter the logon name in the format of `<$username>@<$AccountAlias>.onaliyun.com`. For more information, see [Log on to the console as a RAM user](reseller.en-US/User Guide/RAM users/Log on to the console as a RAM user.md#).

