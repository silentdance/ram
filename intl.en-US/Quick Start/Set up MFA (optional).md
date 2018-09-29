# Set up MFA \(optional\) {#concept_u2b_ww2_xdb .concept}

This document describes how to activate and use multi-factor authentication \(MFA\) to log on to the RAM console. With MFA, your account security will be improved.

## Activate MFA for your primary account {#section_gw3_xw2_xdb .section}

Your primary account has full control over the resources under it. Once the logon password or access key of the primary account is disclosed, the assets under the account will face great security threats. To reduce the security threats, we strongly recommend that you bind MFA to your primary account.

**Prerequisites**

Make sure you have installed on your smartphone a virtual MFA application, preferably the Alibaba Cloud app.

You can also install Google Authenticator, which is also a common MFA application.

-   iOS: Install Google Authenticator in App Store. The installation method can be found in [iOS-based Google Authenticator installation and use guide](https://help.aliyun.com/document_detail/28668.html).
-   Android: Install Google Authenticator in Google Play. The installation method can be found in [Android-based Google Authenticator installation and use guide](https://help.aliyun.com/document_detail/28669.html).

The following takes the Alibaba Cloud app as an example to describe the operation procedure.

**Procedure**

1.  Log on to the Alibaba Cloud Console with your primary account. Choose Account Management \> Security Settings to open the [Security Settings](https://partners-intl.console.aliyun.com/#/ram) page.
2.  Under the Virtual MFA menu, click **Set** to enter the virtual MFA device binding procedure.
3.  Complete the authentication through mailbox authentication, smartphone authentication, or security authentication. Then, go to the Enable the Virtual MFA Device page, as shown in the following figure.

     ![](images/3500_en-US.png "Identity verification") 

4.  Open the **Alibaba Cloud app** in your smartphone and select**+** \> **Sweep Code add**Sweep code. The user is automatically added upon completion of the sweep code, and the Alibaba Cloud app displays the dynamic password for your current account, update every 30 seconds.

     ![](images/3501_en-US.png "Dynamic Password") 

    **Note:** If your smart device does not support code sweep, then you can also select hand-to-hand information acquisition and manually enter it in the MFA application. How the MFA key is configured.

5.  Enter mfa on the enable virtual MFA appliance page Apply the two consecutive sets of dynamic passwords displayed in, and then click OK to enable. as shown in the following figure.

     ![](images/3503_en-US.png "Enable virtual MFA Devices") 


So far, you have successfully enabled the MFA device.

## Login process after opening MFA {#section_nw3_xw2_xdb .section}

After opening MFA, you can only log in to Ali cloud after completing two-step verification. The operation is as follows:

1.  Enter your login user name and password first when you log on to the console.
2.  After the password is verified, you also need to provide the dynamic verification code from the VMFA device, as shown in the figure below:

    ![](images/3503_en-US.png "Verify dynamic security verification code")


In your mobile Alibaba Cloud app, get and enter the dynamic verification code for your login account, you can log in to Ali cloud.

