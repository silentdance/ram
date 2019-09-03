# Enable an MFA device for a RAM user {#task_268585 .task}

This topic describes how to enable a multi-factor authentication \(MFA\) device for a RAM user with the Google Authenticator app. After an MFA device is enabled, it provides additional security protection for your Alibaba Cloud account.

1.  Log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram) by using your Alibaba Cloud account. 

    **Note:** 

    -   If you selected **Required** for **Enable MFA** when you modify the logon settings of a RAM user, the user can go to step 5 when the user logs on to the RAM console.
    -   If you allow a RAM user under your Alibaba Cloud account to manage its own MFA device, the user can also enable an MFA device in the RAM console.
2.  Choose **Identities** \> **Users**.
3.  In the **User Logon Name/Display Name** column, click the username of the target RAM user.
4.  In the **MFA Device** section, click **Enable the device**.
5.  Download and install Google Authenticator on your mobile phone. 
    -   For iOS: Install Google Authenticator from the App Store.
    -   For Android: Install Google Authenticator from the Google Play Store.

        **Note:** You need to install a QR code scanner from the Google Play Store for Google Authenticator to identify QR codes.

6.  Open Google Authenticator and tap **BEGIN SETUP**. 
    -   Tap **Scan barcode** and scan the QR code displayed on the **Scan the code** tab in the console.
    -   Tap **Manual entry**, enter the username and key, and then tap the check mark \(**√**\) icon.

        **Note:** You can obtain the username and key from the **Retrieve manually enter information** tab in the console.

7.  On the **Scan the code** tab, enter the two consecutive verification codes obtained from Google Authenticator and click **Enable**. 

    **Note:** The verification code is refreshed at an interval of 30 seconds.


When a RAM user logs on to the RAM console with MFA enabled, the system requires the following two security factors:

1.  Username and password of the RAM user
2.  Two consecutive verification codes provided by the MFA device

**Note:** Before you uninstall or remove an MFA device from a RAM user, you must first log on to the Alibaba Cloud console to disable the MFA device.

