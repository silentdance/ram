# Enable an MFA device for an Alibaba Cloud account {#task_268585 .task}

This topic describes how to enable a multi-factor authentication \(MFA\) device for your Alibaba Cloud account with the Google Authenticator app. After an MFA device is enabled, it provides additional security protection for your Alibaba Cloud account.

1.  Log on to the [Alibaba Cloud console](https://partners-intl.console.aliyun.com/#/ram).
2.  Move the pointer over the account icon and click **Security Settings**.
3.  In the **Account Protection** section, click **Edit**. 

    **Note:** Virtual MFA is now renamed TOTP.

4.  On the displayed page, select a scenario and select **TOTP**.
5.  Click **Submit**.
6.  On the displayed page, click **Verify now**.
7.  Enter the verification code and click **Submit**.
8.  Download and install Google Authenticator on you mobile phone. 

    **Note:** If you already installed Google Authenticator, click **Next**.

    -   For iOS: Install Google Authenticator from the App Store.
    -   For Android: Install Google Authenticator from the Google Play Store.

        **Note:** You need to install a QR code scanner from the Google Play Store for Google Authenticator to identify QR codes.

9.  After you install Google Authenticator, go back to the Identity Verification page and click **Next**.
10. Open Google Authenticator and tap **BEGIN SETUP**. 
    -   Tap **Scan barcode** and scan the QR code on the Identity Verification page.
    -   Tap **Manual entry**, enter the username and key, and then tap the check mark \(**√**\) icon.

        **Note:** You can obtain the username and key by moving the pointer over **Scan failed** on the Identity Verification page.

11. On the Identity Verification page, enter the 6-digit verification code obtained from Google Authenticator and click **Next**. 

    **Note:** The verification code is refreshed at an interval of 30 seconds.


When you log on to Alibaba Cloud with MFA enabled, the system requires the following two security factors:

1.  Your username and password
2.  Verification code provided by the MFA device

**Note:** 

-   The MFA settings for your Alibaba Cloud account does not affect the logon of users under the account.
-   Before you uninstall or remove an MFA device, you must first log on to the Alibaba Cloud console to disable the MFA device.

