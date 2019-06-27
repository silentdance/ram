# Set a password policy for RAM users {#task_188785 .task}

You can set a password policy on your Alibaba Cloud account to specify the complexity requirements and expiration period for passwords of your RAM users.

1.  Log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram).
2.  Choose **Identities** \> **Settings**.
3.  On the **Security Settings** tab, click **Edit Password Rule** and set the relevant parameters. 
    -   **Password Length**: The password must be 8 to 32 characters in length.
    -   **Required Elements in Password**: The required elements include lowercase letters, uppercase letters, numbers, and special characters.

        **Note:** To protect your Alibaba Cloud account, we recommend that you select a minimum of two of the preceding elements.

    -   **Password Validity Period**: The value range is from 0 to 1,095, in days. The default value is 0, indicating that the password never expires.

        **Note:** The password validity period changes if you reset the password.

    -   **Action After Password Expires**: Specifies whether to allow your RAM users to log on to the console after their passwords expire. The options are **Deny Logon** and **Allow Logon**.
        -   If you select **Deny Logon**, your RAM users can log on to the console only after you reset the password by using your Alibaba Cloud account.
        -   If you select **Allow Logon**, your RAM users can change their passwords after their passwords expire and log on to the console properly.
    -   **Password History Check Policy**: You can prevent RAM users from reusing a specified number of previous passwords. The value range is from 0 to 24. The default value is 0, indicating that RAM users are not prevented from reusing previous passwords.
    -   **Password Retry Constraint Policy**: The maximum number of permitted logon attempts in an hour. The value range is from 0 to 32. The default value is 0, indicating that the logon attempts are not limited.

        **Note:** The number of logon attempts is reset to zero after you change the password.

4.  Click **OK**. 

    **Note:** The settings of the password policy apply to all RAM users under your Alibaba Cloud account.


