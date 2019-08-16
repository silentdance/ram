# Create a domain alias {#task_221525 .task}

This topic describes how to create a domain alias for an Alibaba Cloud account. A domain alias is an additional domain name that points to your default domain name. RAM users under your Alibaba Cloud account can use your domain alias that can be resolved on the Internet to log on to the RAM console.

1.  Log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram) by using your Alibaba Cloud account.
2.  In the left-side navigation pane, click **Identities**, and click **Settings**.
3.  Click the **Advanced** tab, and click **Create Domain Alias**.
4.  Enter a domain alias.
5.  Click **OK**.
6.  Click **Domain Ownership Verification** to verify the domain ownership. 

    **Note:** Before you perform domain ownership verification, make sure that you have added a TXT record for the domain alias in the system of your domain service provider. After you add a domain alias, a random code is generated for domain ownership verification. Copy the verification code, and then click **Domain Ownership Verification** to verify the domain ownership.


After the domain alias is created, the RAM users under your Alibaba Cloud account can use the domain alias to log on to the RAM console.

To log on to the RAM console as a RAM user by using the domain alias, enter the logon name in the format of `<$username>@<$DomainAlias>`. For more information, see [Log on to the console as a RAM user](reseller.en-US/User Guide/RAM users/Log on to the console as a RAM user.md#).

