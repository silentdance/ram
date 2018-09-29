# Users {#concept_hnj_mjf_xdb .concept}

RAM user is an identity used in RAM to relate with a true identity, such as a user or an application. To allow a new user or a new application to access your cloud resources, you can create and grant permissions to a RAM user. The general procedure is as follows:

1.  Use the primary account \(or a RAM user with RAM operation permissions\) to log on to the [RAM console](https://partners-ram.console.aliyun.com/).
2.  Create a RAM user and add the user to one or more groups.
3.  Attach one or more authorization policies to the user \(or the group to which the user belongs\).
4.  Create a credential for the user. If the user performs operations through the console, set a logon password for the user. If the user performs operations by calling APIs, create an API AccessKey for the user.
5.  If the user needs to use special permissions \(for example, to stop ECS instances\), you can set MFA for the user and require that the user use an MFA password to log on to the Alibaba Cloud console.
6.  Provide the user with the logon URL, username, and password.

## RAM settings {#section_h3q_sjf_xdb .section}

-   [Set the enterprise alias](#section_dbn_plf_xdb)
-   [Configure the password policy](#section_x1n_plf_xdb)
-   [Configure the security policy](#section_gvd_1rf_xdb)

## Set the enterprise alias {#section_dbn_plf_xdb .section}

1.  In the **RAM console**, choose**Settings** \> **Enterprise Alias Settings** \> **Edit Enterprise Alias**.
2.  Enter an **enterprise alias** and click **OK**.

## Configure the password policy {#section_x1n_plf_xdb .section}

To configure the password policy, follow these steps:

1.  In the **RAM console**, choose**Settings** \> **Password Strength Settings**.
2.  Follow the page prompts to configure rules such as password length, character format, expiration date, and retry constraint policy, and then click **Save Changes** to make the rules take effect.

    **Note:** Once the password policy takes effect, all RAM users created hereafter must comply with the password strength settings.


## Configure the security policy {#section_gvd_1rf_xdb .section}

1.  In the **RAM console**, choose**Settings** \> **User Security Settings**.
2.  On the User Security Settings page, configure your security policy.
3.  Click **Save Changes**.

## Create a RAM user {#section_rtb_njf_xdb .section}

To create a RAM user, follow these steps:

1.  In the **RAM console**, choose **Users** \> **New User**.
2.  Enter user information in the displayed dialog box and click **OK**.

After creating a RAM user, you can do the following as needed:

-   [Set a logon password](#section_utb_njf_xdb)
-   [Create an AccessKey](#section_ytb_njf_xdb)
-   [Enable virtual MFA devices](#section_b5b_njf_xdb)

## Set a logon password {#section_utb_njf_xdb .section}

To allow a RAM user to access the **RAM console**, you can set a logon password for the user. The procedure is as follows:

1.  Click Users in the left navigation bar of the **RAM console**. Select the target user \(which can be queried by user name\). Click the user name or **Manage**.
2.  On the User Details page, click **Enable Console Logon**.

    ![](images/3576_en-US.png "Set a logon password")

3.  In the displayed dialog box, set an initial password for the user. You can specify a rule that the user must change the password upon logon.

## Create an AccessKey {#section_ytb_njf_xdb .section}

To create an AccessKey for the user who needs to call the API, follow these steps:

1.  Click Users in the left navigation bar of the RAM console. Select the target user \(which can be queried by user name\). Click the user name or **Manage**.
2.  On the User Details page, click **Create Access Key**.
3.  In the displayed dialog box, view the new AccessKey information and click **Save Access Key Information**.

**Note:** 

-   New AccessKeys are displayed only during creation. For security reasons, RAM does not provide an AccessKey query interface. Therefore, please keep the AccessKey safe.
-   If your AccessKey is disclosed or lost, you must create a new one.

## Enable virtual MFA devices {#section_b5b_njf_xdb .section}

Multi-Factor Authentication \(MFA\) is a simple but effective best practice that can provide additional security protection. After MFA is enabled, when a user logs on to Alibaba Cloud, the system requires the user to enter the user name and password \(first security factor\), and then enter a variable verification code \(second security factor\) provided by the user’s VMFA \(virtual MFA\) device. All these factors work together to offer higher security protection for your account.

The virtual MFA \(VMFA\) device is an application that generates a 6-digit verification code. It complies with the time-based one-time password algorithm \(TOTP\) standard \([RFC 6238](http://tools.ietf.org/html/rfc6238)\). This application can run on mobile hardware devices including smartphones, making it easily accessible.

To enable virtual MFA devices for a RAM user, follow these steps:

1.  Click **Users** in the left navigation bar of the **RAM console**. Select the target user \(which can be queried by user name\). Click the user name or **Manage**.
2.  On the User Details page, click **Enable VMFA Device** to start the [Set up MFA \(optional\)](../../../../reseller.en-US/Quick Start/Set up MFA (optional).md) procedure.

    ![](images/3577_en-US.png "Set MFA")


## RAM user logon {#section_c5s_bkf_xdb .section}

**Logon entry**

RAM user and cloud account logon entries are different. RAM users cannot log on through the cloud account logon page.

Please log on to the [RAM console](https://partners-ram.console.aliyun.com/) to query the logon link on the Dashboard page\).

**Login information**

RAM User logon requires an enterprise alias, a sub-user name, and a password.

The enterprise alias is the one you have set in the initial RAM setup. If you have not set an enterprise alias, the default enterprise alias is your cloud account ID \(which can be queried through**Account Management** \> **Security Settings**.

**Note:** By default, RAM users do not have any access permissions. A RAM user without permissions can log on to the console, but cannot perform any operations. For details about how to attach a policy to a RAM user, see [Authorization](reseller.en-US/User Guide/Authorization/Authorization.md).

## Delete a RAM user {#section_h5b_njf_xdb .section}

**Note:** Think it over before deleting a RAM user. If a user is running a certain service, deleting this user may cause a service failure.

To delete a RAM user, follow these steps:

1.  Click **Users** in the left navigation bar of the RAM console to open the User Management page.
2.  Find the RAM user you want to delete and click **Delete** in the **Actions** area.

    ![](images/3578_en-US.png "Delete a RAM user")

3.  In the displayed **Delete User** dialog box, select the **Unlink Dependent Objects** check box, and then click **OK**.

    ![](images/3579_en-US.png "Confirm the deletion")


