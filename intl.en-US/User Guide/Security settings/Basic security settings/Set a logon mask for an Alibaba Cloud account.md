# Set a logon mask for an Alibaba Cloud account {#task_221531 .task}

This topic describes how to set a logon mask for an Alibaba Cloud account to specify the IP addresses that can be used for logon.

1.  Log on to the [Alibaba Cloud console](https://partners-intl.console.aliyun.com/#/ram).
2.  Move the pointer over the account icon and click **Security Settings**.
3.  In the **Login Mask** section of the Security Settings page, click **Set**.
4.  On the Login Mask page, enter a correct mask. 

    **Note:** If you need to configure multiple masks, separate the masks by using a semicolon \(;\), for example, 192.168.0.0/16;10.0.0.0/8.

5.  Click **Save**. 

    **Note:** After you set a logon mask for your Alibaba Cloud account, you cannot log on to the console by using a password or through Single Sign On \(SSO\). However, you can call API actions by using an access key.


