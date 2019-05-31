# Enable MFA for a RAM user {#task_268585 .task}

This topic describes how to enable Multi-Factor Authentication \(MFA\) for a RAM user.

1.  Log on to the [Alibaba Cloud console](https://signin-intl.aliyun.com/login.htm) as a RAM user.
2.  In the upper-left corner, click **Security**.
3.  In the left-side navigation pane, click **MFA Device Management**.
4.  In the **Operation** column, click **Enable MFA Device**.
5.  Install Google Authenticator \(an MFA device\) on you mobile phone. 
    -   For iOS: Install Google Authenticator from the App Store.
    -   For Android: Install Google Authenticator from the Google Play Store.

        **Note:** You need to install a QR code scanner from the Google Play Store for Google Authenticator to identify QR codes.

6.  Open Google Authenticator and tap **BEGIN SETUP**. 
    -   Tap **Scan barcode** and scan the following QR code.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/221961/155928376447637_en-US.png)

    -   Tap **Manual entry**, enter the account name and key, and then tap the check mark \(**√**\) icon.

        **Note:** You can obtain the account name and key from the **Manual information retrieval** tab of the Enable virtual MFA device page in the Alibaba Cloud console.

7.  On the Enable virtual MFA device page of the Alibaba Cloud console, click **Scan to retrieve**.
8.  Enter the two consecutive security codes obtained from Google Authenticator and click **Enable**. 

    **Note:** The security code is refreshed at an interval of 30 seconds.


After you enable MFA, enter your password and the security code obtained from Google Authenticator when you log on to Alibaba Cloud next time.

**Note:** Before you uninstall or remove an MFA device, you must first log on to the Alibaba Cloud console to disable the MFA device.

