# 设置 MFA（可选） {#concept_u2b_ww2_xdb .concept}

本文介绍了在 RAM 控制台开启 MFA（Multi-factor authentication，多因素认证）以及使用 MFA 进行登录的方法，帮助您使用 MFA 提高账号安全性。

## 为主账号开启多因素认证 {#section_gw3_xw2_xdb .section}

主账号对其名下的资源拥有完全控制权限，一旦主账号登录密码泄露，账号下的资产将面临极大的威胁。为了降低风险，我们强烈建议您给主账号绑定多因素认证。

## 前提条件 {#section_szw_wsb_rfb .section}

请确保您已在智能手机终端上安装了虚拟 MFA 应用程序。

## 操作步骤 {#section_dgc_3pq_kgb .section}

常用的虚拟 MFA 应用程序有 Google Authenticator，您可以自主选择安装并使用。

-   iOS：在 App Store 中安装 Google Authenticator。
    1.  打开 Google Authenticator，单击**开始设置**。
    2.  单击**扫描条形码**，扫描 MFA 绑定页上生成的二维码。

        **说明：** 扫描成功后，界面上会出现账户名和 MFA 密钥。

    3.  在 MFA 绑定页输入连续的两组 MFA Code，单击**确定启用**，完成绑定。
-   Android：在 Google 应用市场中安装 Google Authenticator。

    **说明：** 因为安卓版 Google Authenticator 还依赖外部二维码扫描组件，所以您还需要在应用市场中搜索安装条码扫描器。

    1.  打开 Google Authenticator 后，单击右上角的菜单，选择**设置帐户**。
    2.  选择**扫描条形码**，扫描 MFA 绑定页上生成的二维码。

        **说明：** 扫描成功后，界面上会出现账户名和 MFA 密钥。

    3.  在 MFA 绑定页输入连续的两组 MFA Code，单击**确定启用**，完成绑定。

