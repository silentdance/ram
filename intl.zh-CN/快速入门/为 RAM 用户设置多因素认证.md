# 为 RAM 用户设置多因素认证 {#task_268585 .concept}

为了提高账号安全性，您可以为 RAM 用户开启多因素认证（MFA, Multi-factor authentication）。

## 操作步骤 {#section_x22_ddn_o0l .section}

下文以 Google Authenticator 应用为例来介绍具体的操作步骤。

1.  RAM 用户登录[RAM 控制台](https://signin-intl.aliyun.com/login.htm)。
2.  鼠标悬浮在右上角头像处，单击**安全信息管理**。
3.  在用户信息管理页面，单击 **MFA 设备管理**。
4.  单击**启用 MFA 设备**。
5.  在手机端，下载并安装 Google Authenticator 应用。
    -   iOS：在 App Store 中搜索 Google Authenticator。
    -   Android：在应用市场中搜索 Google Authenticator。

        **说明：** 因为安卓版 Google Authenticator 还依赖外部二维码扫描组件，所以您还需要在应用市场中搜索安装条行码扫描器。

6.  在手机端，登录 Google Authenticator 应用。
7.  选择合适的方式添加虚拟 MFA。
    -   单击**开始设置** \> **扫描条形码**，扫描以下二维码。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/221961/155857913947637_zh-CN.png)

    -   单击**开始设置** \> **手动输入验证码**，填写用户名和密钥，单击”√“。

        **说明：** 密钥可以控制台获取，在启用虚拟MFA设备页面，单击**手输信息获取** ，可以查看用户名和密钥。

8.  在控制台**扫码获取**页签下，输入手机端显示的两组连续的动态验证码，单击**确定启用**，完成绑定。

    **说明：** 阿里云会显示您当前账号的动态验证码，每 30 秒更新一次。


## 设置 MFA 后的登录过程 {#section_s1o_au8_izs .section}

设置 MFA 后，用户再次登录阿里云时，需要提供密码和 MFA 应用生成的验证码才能登录到阿里云。

**说明：** 卸载 MFA 应用或删除绑定好的 MFA 前，请先前往阿里云停用 MFA，否则可能无法正常登录阿里云。

1.  RAM 用户登录 [RAM 控制台](https://signin-intl.aliyun.com/login.htm)。
2.  输入账号和密码。
3.  在手机端，登录 Google Authenticator 应用。
4.  将页面的动态验证码输入到控制台页面，完成登录。

