# 使用 AD FS 进行用户 SSO 的示例 {#concept_bpk_3jc_mfb .concept}

本文提供一个以 AD FS 与阿里云进行 SSO 的示例，帮助您理解企业 IdP 与阿里云进行 SSO 的端到端配置流程。

## 注意事项 {#section_cvz_jdp_1wn .section}

本文以 Windows Server 2012 R2 为例，介绍如何配置 AD FS 与阿里云，从而实现 SSO。

**注意：** 本文中涉及到 Microsoft Active Directory 配置的部分属于建议，仅用于帮助理解阿里云 SSO 的端到端配置，阿里云不提供 Microsoft Active Directory 配置官方咨询服务。

## 前提条件 {#section_i32_zdd_mfb .section}

用户对 Microsoft Active Directory \(AD\) 需进行合理正确的配置，在 Windows Server 2012 R2 上配置以下服务器角色：

-   DNS 服务器：将身份认证请求解析到正确的 Federation Service 上。
-   Active Directory 域服务 （AD DS）：提供对域用户和域设备等对象的创建、查询和修改等功能。
-   Active Directory Federation Service （AD FS）：提供配置 SSO 信赖方的功能，并对配置好的信赖方提供 SSO 认证。

## 示例配置 {#section_k32_zdd_mfb .section}

示例中用到的相关配置如下：

-   云账号的默认域名为：`secloud.onaliyun.com`。
-   云账号下包含 RAM 用户：`alice`，其完整的 UPN（User Principal Name）为：`alice@secloud.onaliyun.com`。
-   创建的 Microsoft AD 中的 AD FS 服务名称为：`adfs.secloud.club`。
-   创建的 Microsoft AD 的域名为： `secloud.club`，NETBIOS 名为：`secloud`。
-   RAM 用户 `alice` 在 AD 中的 UPN 为：`alice@secloud.club`，域内登录也可以使用：`secloud\alice`。

## 在 RAM 中将 AD FS 配置为可信 SAML IdP {#section_m32_zdd_mfb .section}

1.  在浏览器中输入如下地址：

    ``` {#codeblock_hpu_vmj_ocs}
    https://adfs.secloud.club/FederationMetadata/2007-06/FederationMetadata.xml
    ```

2.  将元数据 XML 文件下载到本地。
3.  在 RAM 控制台的 SSO 配置时使用下载好的元数据文件。

具体配置请参考：[阿里云用户 SSO 的 SAML 配置](intl.zh-CN/用户指南/单点登录管理（SSO）/用户 SSO/阿里云用户 SSO 的 SAML 配置.md#)。

## 在 AD FS 中将阿里云配置为可信 SAML SP {#section_q32_zdd_mfb .section}

在 AD FS 中，SAML SP 被称作 **信赖方**。

1.  在**服务器管理器**的**工具**菜单中选择**AD FS 管理** 。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23741/156171505514260_zh-CN.png)

2.  在 **AD FS** 管理工具中**添加信赖方信任**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23741/156171505614261_zh-CN.png)

3.  为新创建的信赖方设置阿里云的 SAML 元数据。

    阿里云账号的 SAML 服务提供商元数据 URL 可以登录 [RAM 控制台](https://ram.console.aliyun.com/)，在左侧菜单栏，单击 **SSO 管理**，在 **用户 SSO**页签下的 **SSO 登录设置**区域下查看。AD FS 信赖方可以直接配置元数据的 URL。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23741/156171505614262_zh-CN.png)

    完成配置信赖方之后，阿里云和 AD FS 就产生了互信，阿里云会将默认域名为`secloud.onaliyun.com`的云账号下所有 RAM 用户的认证请求转发到 AD FS：`adfs.secloud.club`，AD FS 也会接受来自于阿里云的认证请求并向阿里云转发认证响应。


## 为阿里云 SP 配置 SAML 断言属性 {#section_u32_zdd_mfb .section}

为了让阿里云能使用 SAML 响应定位到正确的 RAM 用户，SAML 断言中的 `NameID` 字段取值应为 RAM 用户的 UPN。

我们需要配置 AD 中的 UPN 为 SAML 断言中的 `NameID`。

1.  为信赖方**编辑声明规则**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23741/156171505614263_zh-CN.png)

2.  添加**颁发转换规则**。

    **说明：** 颁发转换规则（Issuance Transform Rules）：指如何将一个已知的用户属性，经过转换后颁发为 SAML 断言中的属性。由于我们要将用户在 AD 中的 UPN 颁发为`NameID`，因此需要添加一个新的规则。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23741/156171505614264_zh-CN.png)

3.  **声明规则模版**选择**转换传入声明**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23741/156171505614265_zh-CN.png)

4.  **编辑规则**。

    **说明：** 由于示例中的云账号里的 UPN 域名为`secloud.onaliyun.com`，而 AD 中的 UPN 域名为`secloud.club`，如果直接将 AD 中的 UPN 映射为`NameID`，阿里云将无法匹配到正确的 RAM 用户。

    下面提供几种设置 RAM 用户的 UPN 与 AD 用户的 UPN 保持一致的方法：

    1.  方法一：将 AD 域名设置为 RAM 的**域别名**。

        如果 AD 域名`secloud.club`是一个在公网 DNS 中注册的域名。用户可以将`secloud.club`设置为 RAM 的**域别名**。关于如何设置域别名，请参考：[创建域别名](intl.zh-CN/用户指南/安全设置/高级设置/创建域别名.md#)。

        完成设置后，在编辑规则窗口，将 UPN 映射为名称 ID（`NameID`）。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23741/156171505714266_zh-CN.png)

    2.  方法二：在 AD FS 中设置域名转换。

        如果域名`secloud.club`是企业的内网域名，那么阿里云将无法验证企业对域名的所有权。RAM 就只能使用默认域名`secloud.onaliyun.com`。

        在 AD FS 给阿里云颁发的 SAML 断言中必须将 UPN 的域名后缀从 `secloud.club` 替换为：`secloud.onaliyun.com`。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23741/156171505714267_zh-CN.png)

    3.  方法三：将 AD 域名设置为用户 SSO 的辅助域名。

        如果域名`secloud.club`是企业的内网域名，那么阿里云将无法验证企业对域名的所有权。您可以将 `secloud.club` 设置为用户 SSO 的辅助域名，无需进行域名转换。关于如何设置辅助域名，请参考：[设置辅助域名](intl.zh-CN/用户指南/单点登录管理（SSO）/用户 SSO/阿里云用户 SSO 的 SAML 配置.md#)。

    完成设置后，在编辑规则窗口，将 UPN 映射为名称 ID（`NameID`）。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23741/156171505714266_zh-CN.png)


