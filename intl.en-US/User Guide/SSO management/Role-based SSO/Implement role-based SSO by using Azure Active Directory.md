# Implement role-based SSO by using Azure Active Directory {#concept_cnw_3lg_jhb .concept}

This topic provides an example of how to implement role-based Single Sign On \(SSO\) to Alibaba Cloud from Azure Active Directory \(Azure AD\), detailing the end-to-end identity SSO process from a cloud identity provider \(IdP\) to Alibaba Cloud. After implementing role-based SSO, you can better manage your Azure AD users who have access to Alibaba Cloud, enable your users to automatically log on to Alibaba Cloud with their Azure AD accounts, and manage your accounts in the Azure portal.

## Scenario {#section_i32_zdd_mfb .section}

You use Azure AD to manage your users and configure enterprise applications such as Alibaba Cloud. In this example, you have an Alibaba Cloud account \(Account1\) and a user named u2. You want u2 to implement SSO from Azure AD to Account1.

The following figure shows the basic SSO process.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156404951144059_en-US.png)

## Configurations {#section_mjz_zwm_jhb .section}

To implement role-based SSO, you must configure Azure AD and Alibaba Cloud by following these steps:

-   Add Alibaba Cloud role-based SSO from Azure AD gallery:
    1.  Log on to the [Azure portal](https://login.microsoftonline.com/common/oauth2/authorize?resource=https%3a%2f%2fmanagement.core.windows.net%2f&response_mode=form_post&response_type=code+id_token&scope=user_impersonation+openid&state=OpenIdConnect.AuthenticationProperties%3d5FT_-vA-86sjnHvdYgae3xIrfEYWocMbFm6b-6ZkjvyDN7oGP-eWsavs5bEJ7Ui4QLqrvKnbzv4y2jHrhRevyBj_wkvale5omi5UmyapSuopu9DVqOUDOr_4NHTF8vx-8mFviu87A4pkroboR4O1UvvnTsM5_j52lxGUHiqwduqJTfjv5RI19crtYGbT0AYA3wnOUj0CgbDRsoNqfWB1l4oG3A381I9d94MvXPcuK3g&nonce=636903212631060810.OGU3ZjE3ZDQtNGU0ZS00NTY1LWEzZjItZDEzOGU4OGZkMTFjMThiZWE5YWItMGEwOC00ZTBlLTkzYmMtYTkxNTc4ZTdmZTM2&client_id=c44b4083-3bb0-49c1-b47d-974e53cbdf3c&redirect_uri=https%3a%2f%2fportal.azure.com%2fsignin%2findex%2f&site_id=501430&client-request-id=f7c9e806-ffd9-4d71-a38a-e28c89ff7ba3&x-client-SKU=ID_NET&x-client-ver=1.0.40306.1554).
    2.  In the left-side navigation pane, choose **Azure Active Directory** \> **Enterprise applications** \> **All applications**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156404951143719_en-US.png)

    3.  Click **New application**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156404951143721_en-US.png)

    4.  On the displayed page, enter Alibaba Cloud Service \(Role-based SSO\) in the search box, press **Enter**, and select **Alibaba Cloud Service \(Role-based SSO\)**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156404951143722_en-US.png)

    5.  On the displayed page, click **Add**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156404951143723_en-US.png)

    6.  On the **Alibaba Cloud Service \(Role-based SSO\)** page, click **Properties** in the left-side navigation pane, and copy and save the object ID for subsequent use.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156404951243726_en-US.png)

-   Enable Azure AD SSO in Azure AD:
    1.  In the Azure portal, choose **Azure Active Directory** \> **Enterprise applications** \> **All applications**.
    2.  In the **NAME** column, click **Alibaba Cloud Service \(Role-based SSO\)**.
    3.  On the displayed page, select **Single sign-on** from the left-side navigation pane.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156404951243729_en-US.png)

    4.  In the **Select a single sign-on method** section, click **SAML**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156404951243727_en-US.png)

    5.  On the **Set up Single Sign-On with SAML** page, follow these steps:
        1.  In the upper-left corner, click **Upload metadata file** to integrate Azure AD with Alibaba Cloud role-based SSO, and click **Save**.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156404951243731_en-US.png)

            **Note:** You can obtain the metadata file from the URL `https://signin.alibabacloud.com/saml-role/sp-metadata.xml`.

        2.  In the **User Attributes & Claims** section, click the **Edit** icon.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156404951244052_en-US.png)

        3.  Click **Add new claim**. In the **Name** field, enter `Role`. In the **Namespace** field, enter `https://www.aliyun.com/SAML-Role/Attributes`. Set **Source** to **Attribute**, select `user.assignedroles` from the **Source attribute** drop-down list, and click **Save**.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156404951244053_en-US.png)

        4.  Repeat the preceding step to add a new claim with **Name** set to `RoleSessionName` and **Source attribute** set to `user.userprincipalname`, and click **Save**.

            **Note:** You can also enter `https://www.aliyun.com/SAML-Role/Attributes` in the **Namespace** field.

        5.  In the **SAML Signing Certificate** section, click **Download** to download the federation metadata XML for subsequent use.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156404951244054_en-US.png)

        6.  In the **Set up Alibaba Cloud Service \(Role-based SSO\)** section, copy the URLs as needed.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156404951244055_en-US.png)

-   Configure role-based SSO in Alibaba Cloud:

    1.  Log on to the Alibaba Cloud [RAM console](https://ram.console.aliyun.com/) by using Account1.
    2.  In the left-side navigation pane, select **SSO**.
    3.  On the **Role-based SSO** tab, click **Create IdP**.
    4.  On the displayed page, enter `AAD` in the **IdP Name** field, enter a description in the **Note** field, click **Upload** to upload the federation metadata file you downloaded before, and click **OK**.
    5.  After the IdP is successfully created, click **Create RAM Role**.
    6.  In the **RAM Role Name** filed, enter `AADrole`, select `AAD` from the **Select IdP** drop-down list, and click **OK**.
    **Note:** You can grant permission to the role as needed. After creating the IdP and the corresponding role, we recommend that you save the ARNs of the IdP and the role for subsequent use. You can obtain the ARNs on the IdP information page and the role information page.

-   Associate the Alibaba Cloud RAM role \(AADrole\) with the Azure AD user \(u2\):

    To associate the RAM role with the Azure AD user, you must create a role in Azure AD by following these steps:

    1.  Log on to the [Azure AD Graph Explorer](https://developer.microsoft.com/en-us/graph/graph-explorer).
    2.  Click **modify permissions** to obtain required permissions for creating a role.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156404951344132_en-US.png)

    3.  Select the following permissions from the list and click **Modify Permissions**, as shown in the following figure.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156404951344135_en-US.png)

        **Note:** After permissions are granted, log on to the Graph Explorer again.

    4.  On the **Graph Explorer** page, select **GET** from the first drop-down list and **beta** from the second drop-down list. Then enter `https://graph.microsoft.com/beta/servicePrincipals` in the field next to the drop-down lists, and click **Run Query**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156404951344150_en-US.png)

        **Note:** If you are using multiple directories, you can enter `https://graph.microsoft.com/beta/contoso.com/servicePrincipals` in the field of the query.

    5.  In the **Response Preview** section, extract the appRoles property from the 'Service Principal' for subsequent use.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156404951344166_en-US.png)

        **Note:** You can locate the appRoles property by entering `https://graph.microsoft.com/beta/servicePrincipals/<objectID>` in the field of the query. Note that the `objectID` is the object ID you have copied from the Azure AD **Properties** page.

    6.  Go back to the Graph Explorer, change the method from **GET** to **PATCH**, paste the following content into the **Request Body** section, and click **Run Query**:

        ``` {#codeblock_y9g_mkr_57x}
        
        { 
          "appRoles": [
            { 
              "allowedMemberTypes":[
                "User"
              ],
              "description": "msiam_access",
              "displayName": "msiam_access",
              "id": "41be2db8-48d9-4277-8e86-f6d22d35****",
              "isEnabled": true,
              "origin": "Application",
              "value": null
            },
            { "allowedMemberTypes": [
                "User"
            ],
            "description": "Admin,AzureADProd",
            "displayName": "Admin,AzureADProd",
            "id": "68adae10-8b6b-47e6-9142-6476078cdbce",
            "isEnabled": true,
            "origin": "ServicePrincipal",
            "value": "acs:ram::187125022722****:role/aadrole,acs:ram::187125022722****:saml-provider/AAD"
            }
          ]
        }
        ```

        **Note:** The `value` is the ARNs of the IdP and the role you created in the RAM console. Here, you can add multiple roles as needed. Azure AD will send the value of these roles as the claim value in SAML response. However, you can only add new roles after the `msiam_access` part for the patch operation. To smooth the creation process, we recommend that you use an ID generator, such as GUID Generator, to generate IDs in real time.

    7.  After the 'Service Principal' is patched with the required role, attach the role with the Azure AD user \(u2\) by following these steps:
        1.  In the Azure portal, choose **Azure Active Directory** \> **Enterprise applications** \> **All applications**.
        2.  In the **NAME** column, click **Alibaba Cloud Service \(Role-based SSO\)**.
        3.  On the displayed page, select **Users and groups** from the left-side navigation pane.
        4.  In the upper-left corner, click **Add user**.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156404951344178_en-US.png)

        5.  On the **Users and groups** tab, select u2 from the user list, and click **Select**. Then, click **Assign**.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156404951444179_en-US.png)

        6.  View the assigned role and test role-based SSO.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156404951444185_en-US.png)

    **Note:** After you assign the user \(u2\), the created role is automatically attached to the user. If you have created multiple roles, you need to attach the appropriate role to the user as needed. If you want to implement role-based SSO from Azure AD to multiple Alibaba Cloud accounts, repeat the preceding steps.


## Test role-based SSO {#section_yj4_slh_jhb .section}

After the preceding configurations are completed, test role-based SSO by following these steps:

1.  In the Azure portal, go to the **Alibaba Cloud Service \(Role-based SSO\)** page, select **Single sign-on**, and click **Test**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156404951444188_en-US.png)

2.  Click **Sign in as current user**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156404951444191_en-US.png)

3.  On the account selection page, select u2.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156404951444192_en-US.png)


The following page is displayed, indicating that role-based SSO is successful.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156404951444194_en-US.png)

