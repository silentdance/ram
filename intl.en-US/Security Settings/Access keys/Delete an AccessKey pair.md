# Delete an AccessKey pair {#task_221540 .task}

If you no longer need to access Alibaba Cloud resources by calling API operations or using other development tools, you can delete AccessKey pairs.

Before deleting an AccessKey pair, you can query the time when the pair was last used to check whether the pair is being used. For more information about how to query the time when an AccessKey pair was last used, see [View basic information about an access key](../../../../reseller.en-US/Security Settings/Access keys/View basic information about an access key.md#).

**Note:** Use caution when you delete an AccessKey pair. If you delete an AccessKey pair that is being used by an app, system errors may occur on the app.

1.  Log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram) by using an Alibaba Cloud account.
2.  In the left-side navigation pane, click **Users** under **Identities**.
3.  In the **User Logon Name/Display Name** column, click the name of the target RAM user.
4.  In the **User AccessKeys** section, click **Delete**.
5.  In the check box that appears, select **I am aware of the risk and confirm the deletion**.
6.  Click **OK**.

**More information**  


[DeleteAccessKey](../../../../reseller.en-US/API Reference/User management APIs/DeleteAccessKey.md#)

