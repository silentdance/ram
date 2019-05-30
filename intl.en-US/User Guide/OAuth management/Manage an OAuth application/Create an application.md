# Create an application {#task_183262 .task}

This topic describes how to create an application. You can create a web application or a native application based on OAuth to obtain user information and access Alibaba Cloud APIs.

1.  Log on to the [RAM console](https://ram.console.aliyun.com/).
2.  In the left-side navigation pane, click **OAuth Applications**.
3.  Click **Create Application**, and enter the application name and the display name.
4.  Select an application type. 
    -   **WebApp**: This type interacts with a web browser.
    -   **NativeApp**: This type runs on an operating system, such as a desktop or mobile operating system.
5.  In the **Access Token Validity Period** field, enter a value for the validity period. 

    **Note:** The validity period of an access token must be within the range of 900 seconds \(15 minutes\) to 10,800 seconds \(3 hours\). The unit is seconds. The default value is 3,600 seconds \(60 minutes\).

6.  In the **Refresh Token Validity Period** field, enter a value for the validity period. 

    **Note:** The validity period of a refresh token must be within the range of 7,200 seconds \(2 hours\) to 31,556,952 seconds \(1 year\). The unit is seconds. The default value is 2,592,000 seconds \(30 days\).

7.  In the **Callback URL** field, enter the callback URL.
8.  Click **OK**.

