# Implement role-based SSO by using Azure Active Directory {#task_cnw_3lg_jhb .task}

This topic provides an example of how to implement role-based single sign-on \(SSO\) to Alibaba Cloud from Azure Active Directory \(Azure AD\). It also helps you to learn about the end-to-end identity SSO process from a cloud identity provider \(IdP\) to Alibaba Cloud.

In this example, you have an Alibaba Cloud account \(Account1\) and an Azure AD user \(u2\). You use Azure AD to manage your users and configure enterprise applications such as Alibaba Cloud. After implementing role-based SSO, you can better manage your Azure AD users who have access to Alibaba Cloud. You can also enable your users to log on to the Alibaba Cloud console with their Azure AD accounts, and manage your accounts in the Azure portal.

![Scenario](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156697594744059_en-US.png)

## Add Alibaba Cloud role-based SSO from the Azure AD gallery {#section_mjz_zwm_jhb .section}

1.  Log on to the [Azure portal](https://portal.azure.com/?l=en.en-us#home) as an administrator.
2.  In the left-side navigation pane, choose **Azure Active Directory** \> **Enterprise applications** \> **All applications**. 

    ![Azure Active Directory](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156697594743719_en-US.png)

3.  Click **New application**. 

    ![New application](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156697594743721_en-US.png)

4.  In the **Add from the gallery** section of the Add an application page, enter **Alibaba Cloud Service \(Role-based SSO\)** into the textbox and press Enter. Then, select Alibaba Cloud Service \(Role-based SSO\). 

    ![Alibaba Cloud Service (Role-based SSO)](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156697594743722_en-US.png)

5.  On the page that appears, click **Add**. 

    ![Add](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156697594843723_en-US.png)

6.  On the Alibaba Cloud Service \(Role-based SSO\) page, click **Properties** in the left-side navigation pane, and copy and save the object ID for subsequent use. 

    ![Object ID](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156697594843726_en-US.png)


## Configure Azure AD SSO {#section_hcw_ey6_57b .section}

1.  Log on to the **Azure portal** as an administrator.
2.  In the left-side navigation pane, choose **Azure Active Directory** \> **Enterprise applications** \> **All applications**.
3.  In the **NAME** column, click **Alibaba Cloud Service \(Role-based SSO\)**.
4.  In the left-side navigation pane of the page that appears, click **Single sign-on**. 

    ![Single sign-on](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156697594843729_en-US.png)

5.  In the Select a single sign-on method section, click **SAML**. 

    ![SAML](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156697594843727_en-US.png)

6.  On the Set up Single Sign-On with SAML page, follow these steps: 
    1.  In the upper-left corner, click **Upload metadata file**, select a file, and then click **Add**. 

        ![Upload a metadata file](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156697594843731_en-US.png)

        **Note:** You can obtain the metadata file from the URL: `https://signin.alibabacloud.com/saml-role/sp-metadata.xml`.

    2.  In the **User Attributes & Claims** section, click the edit icon. 

        ![User attributes and claims](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156697594844052_en-US.png)

    3.  Click **Add new claim**, specify the following parameters, and then click **Save**. 

        -   Specify the **Name** parameter as `Role`.
        -   Specify the **Namespace** parameter as `https://www.aliyun.com/SAML-Role/Attributes`.
        -   Select **Attribute** for the **Source** parameter.
        -   Select `user.assignedroles` from the **Source attribute** drop-down list.
        ![Manage user claims](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156697594844053_en-US.png)

    4.  Repeat the preceding step to add another claim. 
        -   Specify the **Name** parameter as `RoleSessionName`.
        -   Specify the **Namespace** parameter as `https://www.aliyun.com/SAML-Role/Attributes`.
        -   Select **Attribute** for the **Source** parameter.
        -   Select `user.userprincipalname` from the **Source attribute** drop-down list.
    5.  In the upper-right corner of the User Attributes & Claims page, click the close icon. On the page that appears, in the **SAML Signing Certificate** section, click **Download** next to **Federation Metadata XML** to download the federation metadata XML for subsequent use. 

        ![Download the federation metadata XML](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156697594844054_en-US.png)

    6.  In the **Set up Alibaba Cloud Service \(Role-based SSO\)** section, copy and save the **Login URL**, **Azure AD Identifier**, and **Logout URL** for subsequent use. 

        ![Set up Alibaba Cloud Service (Role-based SSO)](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156697594844055_en-US.png)


## Configure role-based SSO in Alibaba Cloud {#section_pc7_e43_i5z .section}

1.  Log on to the Alibaba Cloud [RAM console](https://ram.console.aliyun.com/) by using Account1.
2.  In the left-side navigation pane, click **SSO**.
3.  On the **Role-based SSO** page, click **Create IdP**.
4.  On the page that appears, specify the **IdP Name** parameter as `AAD`, and specify the **Note** parameter.
5.  Click **Upload** under **Metadata File** to upload the federation metadata file you downloaded before. 

    **Note:** You need to upload the **federation metadata file** that you have downloaded from the **SAML Signing Certificate** section in Step 6-e.

6.  Click **OK**.
7.  After the IdP is created, click **Create RAM Role**.
8.  Specify the **RAM Role Name** parameter as `AADrole`, and specify the **Note** parameter.
9.  Select `AAD` from the drop-down list of Select IdP, and click **OK**. 

    **Note:** 

    -   You can grant permission to the role based on your business needs. For more information, see [Grant permission to a RAM role](intl.en-US/User Guide/RAM roles/Grant permission to a RAM role.md#).
    -   After creating the IdP and the corresponding role, we recommend that you save the ARNs of the IdP and the RAM role for subsequent use. For more information about how to obtain the ARN of the RAM role, see [View basic information about a RAM role](intl.en-US/User Guide/RAM roles/View basic information about a RAM role.md#).

## Associate the Alibaba Cloud RAM role \(AADrole\) with the Azure AD user \(u2\) {#section_1p2_4hh_yah .section}

1.  To associate the RAM role with the Azure AD user, you must first create a role in Azure AD by following these steps: 
    1.  Log on to the [Azure AD Graph Explorer](https://developer.microsoft.com/en-us/graph/graph-explorer) by using u2.
    2.  Click **modify permissions** to obtain the required permissions. 

        ![Azure AD Graph Explorer](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156697594844132_en-US.png)

    3.  Select the following permissions from the list, and click **Modify Permissions**. 

        ![Modify permissions](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156697594944135_en-US.png)

        **Note:** After the permissions are granted, log on to the Graph Explorer again.

    4.  On the Graph Explorer page, select **GET** from the first drop-down list, and select **beta** from the second drop-down list. Then, enter `https://graph.microsoft.com/beta/servicePrincipals` into the textbox next to the drop-down lists, and click **Run Query**. 

        ![Run Query](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156697594944150_en-US.png)

        **Note:** If you are using multiple directories, enter `https://graph.microsoft.com/beta/contoso.com/servicePrincipals` into the textbox next to the drop-down lists.

    5.  On the **Response Preview** tab, extract the `appRoles` property from the `Service Principal` object for subsequent use. 

        ``` {#codeblock_fxv_xkg_gv1 .language-json}
         "appRoles": [
                        {
                            "allowedMemberTypes": [
                                "User"
                            ],
                            "description": "msiam_access",
                            "displayName": "msiam_access",
                            "id": "7dfd756e-8c27-4472-b2b7-38c17fc5****",
                            "isEnabled": true,
                            "origin": "Application",
                            "value": null
                        }
                    ],
        ```

        **Note:** You can find the `appRoles` property by entering `https://graph.microsoft.com/beta/servicePrincipals/<objectID>` into the textbox next to the drop-down lists. Note that the value of the `objectID` parameter is the object ID you have copied from the Azure AD Properties page.

    6.  Go back to the **Graph Explorer**, select **PATCH** from the first drop-down list, and select **beta** from the second drop-down list. Enter `https://graph.microsoft.com/beta/servicePrincipals/<objectID>` into the textbox next to the drop-down lists. Copy and paste the following sample script into the **Request Body** section, edit the script based on your business needs, and click **Run Query**. 

        ``` {#codeblock_xcc_6ab_ucb .language-json}
        { 
          "appRoles": [
            { 
              "allowedMemberTypes":[
                "User"
              ],
              "description": "msiam_access",
              "displayName": "msiam_access",
              "id": "41be2db8-48d9-4277-8e86-f6d22d35****",// The ID of the RAM role.
              "isEnabled": true,
              "origin": "Application",
              "value": null
            },
            { "allowedMemberTypes": [
                "User"
            ],
            "description": "Admin,AzureADProd",
            "displayName": "Admin,AzureADProd",
            "id": "68adae10-8b6b-47e6-9142-6476078c****",// The ID that is produced by an ID generator in real time, such as GUID Generator.
            "isEnabled": true,
            "origin": "ServicePrincipal",
            "value": "acs:ram::187125022722****:role/aadrole,acs:ram::187125022722****:saml-provider/AAD"// The ARNs of the IdP and the RAM role that you created in the RAM console.
            }
          ]
        }
        ```

        **Note:** You can add multiple roles based on your business needs. Azure AD will send the ARNs of these roles and their corresponding IdPs as the claim value in SAML response. However, you can only add new roles after the `msiam_access` part for the patch operation.

2.  Associate the RAM role with the Azure AD user \(u2\) by following these steps: 
    1.  Log on to the **Azure portal** as an administrator.
    2.  In the left-side navigation pane, choose **Azure Active Directory** \> **Enterprise applications** \> **All applications**.
    3.  In the **NAME** column, click **Alibaba Cloud Service \(Role-based SSO\)**.
    4.  In the left-side navigation pane, click **Users and groups**.
    5.  In the upper-left corner, click **Add user**. 

        ![Add a user](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156697594944178_en-US.png)

    6.  On the page that appears, click **Users**, select u2 from the user list, and then click **Select**. 

        ![Select a user](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156697594944179_en-US.png)

    7.  Click **Assign**.
    8.  View the assigned role and test role-based SSO. 

        ![View the assigned role and test role-based SSO](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156697594944185_en-US.png)

        **Note:** After you assign the user \(u2\), the created RAM role is automatically attached to the user. If you have created multiple RAM roles, you need to attach an appropriate role to the user. If you want to implement role-based SSO from Azure AD to multiple Alibaba Cloud accounts, repeat the preceding steps.


## Test role-based SSO {#section_yj4_slh_jhb .section}

1.  Log on to the **Azure portal** as an administrator.
2.  In the left-side navigation pane, choose **Azure Active Directory** \> **Enterprise applications** \> **All applications**.
3.  In the **NAME** column, click **Alibaba Cloud Service \(Role-based SSO\)**.
4.  In the left-side navigation pane of the page that appears, click **Single sign-on**.
5.  On the page that appears, in the **Validate single sign-on with Alibaba Cloud Service \(Role-based SSO\)** section, click **Validate**. 

    ![Validate](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156697594944188_en-US.png)

6.  Click **Sign in as current user**. 

    ![Sign in as the current user](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156697594944191_en-US.png)

7.  On the page for selecting a logon account, select u2. 

    ![Select an account](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156697594944192_en-US.png)


If the following page appears, it indicates that role-based SSO is successful.

![Successful role-based SSO](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156697594944194_en-US.png)

