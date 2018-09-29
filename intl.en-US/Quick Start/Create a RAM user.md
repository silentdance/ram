# Create a RAM user {#concept_gpm_ccf_xdb .concept}

Before creating a RAM user, ensure that you have finished [Ram initial setup](reseller.en-US/Quick Start/Ram initial setup.md) and have configured your enterprise alias, RAM user's logon password policy, and security policy.

This document describes how to create a RAM user and how to configure the logon password \(if the user needs to log on to the console\) or the AccessKey \(if the user needs to call the cloud service API through a program\).

## Create a RAM user {#section_qt4_dcf_xdb .section}

To create a RAM user, follow these steps.

1.  From the left navigation pane of the [RAM控制台](https://partners-intl.console.aliyun.com/#/ram), click **Users**.
2.  Click **Create User** in the upper right corner to open the Create User dialog box.
3.  After entering user information, click **OK**.

    ![](images/3520_en-US.png "Create a user")


Now, you have created a RAM user.

## Create a logon password {#section_tt4_dcf_xdb .section}

To allow a RAM user's access to the management console, create a logon password for the user.

## Procedure {#section_ut4_dcf_xdb .section}

1.  From the left navigation pane of the RAM console, click **Users**.
2.  On the User Management page, select the target user \(which can be searched by **User Name**\) and click the user name or the corresponding **Manage** in the Actions column to open the User Details page.
3.  In the **Web Console Logon Management** area, click **Enable Console Logon**.

    ![](images/6206_en-US.png "Enable console logon")

4.  In the displayed dialog box, set an initial password for the user. You can also specify that the user must change this password at next logon.

     ![](images/3522_en-US.png "Set a logon password") 


Now, you have set the logon password for the RAM user.

-   To log on for testing as a RAM user, see [Log on with a RAM user account](reseller.en-US/Quick Start/Log on with a RAM user account.md).
-   To manage the RAM user logon password, perform steps 1 through 3. In the **Web Console Logon Management** area, click **Reset Password** or **Disable Console Logon**.

## Create an AccessKey {#section_zt4_dcf_xdb .section}

To allow a RAM user to call the cloud service API through a program, create an AccessKey for the user.

## Procedure {#section_a54_dcf_xdb .section}

1.  From the left navigation pane of the RAM console, click **Users**.
2.  Select the target user \(which can be queried by **User Name**\). Click the user name or **Manage** to open the User Details page.
3.  In the **User Access Key** area, click **Create Access Key**.

     ![](images/3523_en-US.png "Create AccessKey") 

4.  After an AccessKey is created, click **Save Access Key Information** to save the AccessKey.

    **Note:** 

    -   An AccessKeySecret can only be viewed or downloaded during the AccessKey creation process. For security reasons, you cannot view or download it once the AccessKey has been created.

    -   If an AccessKey is lost, you must create a new one. The newly created AccessKey represents the same user identity as the old one. Different AccessKeys for the same RAM user are equivalent.

    -   We recommend that you regularly change application AccessKeys to avoid any risk of AccessKey disclosure.


Now, you have created an AccessKey for the RAM user. To manage the user's AccessKey, perform steps 1 through 3. In the User Access Key area, **Disable** or **Delete** an existing AccessKey.

## Follow-up operations {#section_e54_dcf_xdb .section}

For a RAM user that has been created,  assign the user an appropriate permission for accessing resources based on the user's responsibilities, before performing operations.

-   For details about how to attach policies to a RAM user, see [Attach policies to a RAM user](reseller.en-US/Quick Start/Attach policies to a RAM user.md).

-   To create a fine-grained custom authorization policy, see [Create a custom policy \(optional\)](reseller.en-US/Quick Start/Create a custom policy (optional).md)create a custom policy.


