# 使用Azure AD进行角色SSO的示例 {#task_cnw_3lg_jhb .task}

本文提供一个以Azure AD（Azure Active Directory，以下简称 AAD）与阿里云进行角色SSO的示例，帮助用户理解企业IdP与阿里云进行SSO的端到端配置流程。

在本示例中，企业拥有一个阿里云账号（Account1）和一个企业员工用户（u2）。企业可以使用AAD进行员工管理，并通过AAD配置包括阿里云在内的企业应用。配置完成后，您可以更好的管理企业员工，企业员工也可以实现从AAD到阿里云的角色SSO。

![场景](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156618765544059_zh-CN.png)

## 在AAD库中添加应用程序 {#section_mjz_zwm_jhb .section}

1.  管理员登录[Azure门户](https://portal.azure.com/#home)。
2.  在左侧导航栏，单击**Azure Active Directory** \> **企业应用程序** \> **所有应用程序**。 

    ![Azure Active Directory](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156618765543719_zh-CN.png)

3.  单击**新建应用程序**。 

    ![新建应用程序](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156618765543721_zh-CN.png)

4.  在添加应用程序页面下的**从库中添加**搜索区域，输入**Alibaba Cloud Service（Role-based SSO）**并单击选择。 

    ![Alibaba Cloud Service (Role-based SSO）](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156618765543722_zh-CN.png)

5.  单击**添加**。 

    ![添加](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156618765543723_zh-CN.png)

6.  在Alibaba Cloud Service（Role-based SSO）页面下，单击左侧导航栏下的**属性**，复制并保存**对象ID**。 

    ![对象ID](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156618765643726_zh-CN.png)


## 配置AAD SSO {#section_hcw_ey6_57b .section}

1.  管理员登录**Azure门户**。
2.  在左侧导航栏，单击**Azure Active Directory** \> **企业应用程序** \> **所有应用程序**。
3.  在**名称**列表下，单击**Alibaba Cloud Service（Role-based SSO）**。
4.  在左侧导航栏，选择**单一登录**。 

    ![单一登录](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156618765643729_zh-CN.png)

5.  在更改单一登录模式页面下，单击**SAML**。 

    ![SAML](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156618765643727_zh-CN.png)

6.  在设置SAML单一登录页面进行配置。 
    1.  在页面左上角，单击**上传元数据文件**，选择文件后，单击**添加**。 

        ![上传元数据文件](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156618765643731_zh-CN.png)

        **Note:** 您可以通过以下URL获取元数据文件： `https://signin.aliyun.com/saml-role/sp-metadata.xml`。

    2.  在**用户属性和声明**区域，单击编辑图标。 

        ![用户属性和声明](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156618765644052_zh-CN.png)

    3.  单击**添加新的声明**，设置以下配置后，单击**保存**。 

        -   在**名称**区域下，输入`Role`。
        -   在**命名空间**区域下，输入`https://www.aliyun.com/SAML-Role/Attributes`。
        -   在**源**区域下，选择**属性**。
        -   在**源属性**区域下，从下拉列表中选择`user.assignedroles`。
        ![管理用户声明](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156618765644053_zh-CN.png)

    4.  重复上述步骤，添加一个新的声明。 
        -   在**名称**区域下，输入`RoleSessionName`。
        -   在**命名空间**区域下，输入`https://www.aliyun.com/SAML-Role/Attributes`。
        -   在**源**区域下，选择**属性**。
        -   在**源属性**区域下，从下拉列表中选择`user.userprincipalname`。
    5.  在**SAML签名证书**区域下的**联合元数据XML**，单击**下载**。 

        ![下载联合元数据XML](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156618765744054_zh-CN.png)

    6.  在**安装Alibaba Cloud Service（Role-based SSO）**区域下，复制**登录URL**、**Azure AD标识符**和**注销URL**。 

        ![安装 Alibaba Cloud Service (Role-based SSO)](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156618765744055_zh-CN.png)


## 在阿里云配置角色SSO {#section_pc7_e43_i5z .section}

1.  云账号（Account1）登录[RAM控制台](https://ram.console.aliyun.com/)。
2.  在左侧导航栏，单击**SSO管理**。
3.  在**角色SSO**页签下，单击**新建身份提供商**。
4.  输入**提供商名称**`AAD`和**备注**。
5.  在**元数据文档**处，单击**上传文件**。 

    **Note:** 上传上述步骤中在**SAML 签名证书**区域下载的**联合元数据XML**。

6.  单击**确定**。
7.  创建身份提供商后，单击**前往新建RAM角色**。
8.  输入**角色名称**`AADrole`和**备注**。
9.  在下拉列表中选择身份提供商`AAD`，单击**完成**。 

    **Note:** 

    -   您可以根据需要为RAM角色添加权限。关于如何为RAM角色添加权限，请参见[为RAM角色授权](cn.zh-CN/用户指南/角色/为RAM角色授权.md#)。
    -   当身份提供商和对应的RAM角色后，请保存好对应的ARN。关于如何查看ARN，请参见[查看RAM角色基本信息](cn.zh-CN/用户指南/角色/查看 RAM 角色基本信息.md#)。

## 将阿里云RAM角色与AAD用户进行关联 {#section_1p2_4hh_yah .section}

1.  在AAD中创建角色。 
    1.  用户（u2）登录[AAD Graph浏览器](https://developer.microsoft.com/zh-cn/graph/graph-explorer)。
    2.  单击**修改权限**。 

        ![Graph浏览器](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156618765744132_zh-CN.png)

    3.  从下拉列表中选择以下权限并单击**修改权限**。 

        ![修改权限](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156618765744135_zh-CN.png)

        **Note:** 修改权限后，系统会重定向到Graph浏览器。

    4.  在Graph浏览器页面，第一个下拉列表中选择**GET**，第二个下拉列表中选择**beta**。在搜索框中输入`https://graph.microsoft.com/beta/servicePrincipals`并单击**运行查询**。 

        ![运行查询](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156618765744150_zh-CN.png)

        **Note:** 如果您有多个目录，您可以在查询区域输入`https://graph.microsoft.com/beta/contoso.com/servicePrincipals`。

    5.  在**响应预览**页签下，从`Service Principal`中提取出`appRoles`属性并保存。 

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

        **Note:** 您可以在查询字段中输入`https://graph.microsoft.com/beta/servicePrincipals/<objectID>`来定位`appRoles`属性，其中`objectID`是您在AAD属性页面保存的。

    6.  返回**Graph浏览器**，将第一个下拉列表改为**PATCH**，第二个下拉列表中选择**beta**。在搜索框中输入`https://graph.microsoft.com/beta/servicePrincipals/<objectID>`，将以下内容复制到**请求正文**中并选择**运行查询**。 

        ``` {#codeblock_xcc_6ab_ucb .language-json}
        { 
          "appRoles": [
            { 
              "allowedMemberTypes":[
                "User"
              ],
              "description": "msiam_access",
              "displayName": "msiam_access",
              "id": "41be2db8-48d9-4277-8e86-f6d22d35****",//appRoles的ID
              "isEnabled": true,
              "origin": "Application",
              "value": null
            },
            { "allowedMemberTypes": [
                "User"
            ],
            "description": "Admin,AzureADProd",
            "displayName": "Admin,AzureADProd",
            "id": "68adae10-8b6b-47e6-9142-6476078c****",//ID生成器（例如：GUID生成器）实时生成的ID
            "isEnabled": true,
            "origin": "ServicePrincipal",
            "value": "acs:ram::187125022722****:role/aadrole,acs:ram::187125022722****:saml-provider/AAD"//身份提供商和RAM角色的ARN
            }
          ]
        }
        ```

        **Note:** 您可以根据需要创建多个RAM角色，AAD将在SAML中将这些角色作为声明值进行传送，但是您只能在`msiam_access`后添加新的角色。

2.  将RAM角色添加到用户（u2）中。 
    1.  用户（u2）登录**Azure门户**。
    2.  在左侧导航栏，单击**Azure Active Directory** \> **企业应用程序** \> **所有应用程序**。
    3.  在**名称**列表下，单击**Alibaba Cloud Service（Role-based SSO）**。
    4.  在左侧导航栏，单击**用户和组**。
    5.  单击左上角的**添加用户**。 

        ![添加用户](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156618765844178_zh-CN.png)

    6.  在左侧导航栏，单击**用户和组**，从用户列表中选择用户（u2），单击**选择**。 

        ![选择用户](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156618765844179_zh-CN.png)

    7.  单击**分配**。
    8.  查看分配的角色。 

        ![查看分配的角色](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156618765844185_zh-CN.png)

        **Note:** 如果您分配了用户（u2），创建好的RAM角色会自动附加给用户。如果您创建了多个角色，您需要根据需要合理分配角色。如果您需要完成AAD与多个阿里云账号的角色SSO，请重复上述配置步骤。


## 测试角色SSO {#section_yj4_slh_jhb .section}

1.  登录**Azure门户**。
2.  在左侧导航栏，单击**Azure Active Directory** \> **企业应用程序** \> **所有应用程序**。
3.  在**名称**列表下，单击**Alibaba Cloud Service（Role-based SSO）**。
4.  在左侧导航栏，选择**单一登录**。
5.  在**使用Alibaba Cloud Service（Role-based SSO）的Validate单一登录**区域下，单击**Validate**。 

    ![Validate](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156618765844188_zh-CN.png)

6.  选择**作为当前用户登录**。 

    ![作为当前用户登录](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156618765844191_zh-CN.png)

7.  在选择账户页面下，选择用户（u2）。 

    ![选择账户](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156618765944192_zh-CN.png)


以下界面出现，表示角色SSO成功。

![角色SSO成功](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/155432/156618765944194_zh-CN.png)

