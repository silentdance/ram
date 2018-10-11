# Set up MFA \(optional\) {#concept_u2b_ww2_xdb .concept}

This document describes how to activate and use multi-factor authentication \(MFA\) to log on to the RAM console. With MFA, your account security will be improved.

## Activate MFA for your primary account {#section_gw3_xw2_xdb .section}

Your primary account has full control over the resources under it. Once the logon password or access key of the primary account is disclosed, the assets under the account will face great security threats. To reduce the security threats, we strongly recommend that you bind MFA to your primary account.

**Prerequisites**

Make sure you have installed on your smartphone a virtual MFA application, preferably the Alibaba Cloud app.

You can also install Google Authenticator, which is also a common MFA application.

-   iOS: Install Google Authenticator in App Store. The installation method can be found in [iOS-based Google Authenticator installation and use guide](https://alibabacloud.com/help/doc-detail/28668.html).
-   Android: Install Google Authenticator in Google Play. The installation method can be found in [Android-based Google Authenticator installation and use guide](https://alibabacloud.com/help/doc-detail/28669.html).

The following takes the Alibaba Cloud app as an example to describe the operation procedure.

**Procedure**

1.  Log on to the Alibaba Cloud Console with your primary account. Choose Account Management \> Security Settings to open the [Security Settings](https://account.console.aliyun.com/#/secure) page.
2.  Under the Virtual MFA menu, click **Set** to start the virtual MFA device binding procedure.
3.  Complete the authentication through mailbox authentication, smartphone authentication, or security authentication. Then, the Bind MFA Device page is displayed, as shown in the following figure.

     ![](images/3500_en-US.png "Identity verification") 

4.  Open the **Alibaba Cloud app** in your smartphone and scan the QR code. The user is then automatically added. The Alibaba Cloud app will display the dynamic password of your current account, which will be updated every 30 seconds.

     ![](images/3501_en-US.png "Dynamic password") 

    **Note:** If your smartphone does not support scanning QR code, you can also manually enter the MFA key in the MFA application.

5.  On the **Enable Virtual MFA Device** page, enter the two consecutive sets of dynamic passwords displayed in the MFA app and click **OK**.

Now you have successfully enabled the MFA device.

## Log on to Alibaba Cloud after enabling MFA {#section_nw3_xw2_xdb .section}

If you have enabled MFA, you can log on to Alibaba Cloud only after completing 2-step verification. The operation procedure is as follows:

1.  Enter your logon user name and password when logging on to the console.
2.  After the user name and password are verified, enter the dynamic verification code from the MFA device.

Now, you can log on to Alibaba Cloud.

