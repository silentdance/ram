# RAM 安全实践 {#concept_wzh_wkk_xdb .concept}

阿里云主账号是您所有云资源管控的根账号。一旦主账号的登录密码或 API 访问密钥丢失或泄露，将会对您的企业造成不可估量的损失。

使用阿里云服务时，为了保障主账号的安全，请参考本文提供的主账号和RAM 用户安全实践原则：

## 原则 1：为主账号开启多因素认证 {#section_a52_ykk_xdb .section}

-   为主账号开启多因素认证（MFA），不要与他人共享 MFA 设备。
-   为授予特权的 RAM 用户也开启多因素认证。特权操作通常指管理用户、授权、停止/释放实例、修改实例配置、删除数据等。

## 原则 2：不要使用主账号进行日常运维管理操作 {#section_urz_ykk_xdb .section}

-   创建独立的 RAM 用户账号，作为 RAM 管理员。
-   为员工创建 RAM 用户账号，进行日常的运维管理操作。
-   为财务人员创建独立的 RAM 用户账号。

## 原则 3：不要为主账号创建 AccessKey {#section_q5n_xkk_xdb .section}

AccessKey 与登录密码具有同样的特权，AccessKey 用于程序访问，登录密码用于控制台登录。由于 AccessKey 通常以明文形式保存在配置文件中，泄露的风险更高。

为所有的应用系统配置 RAM 用户身份，并在[为 RAM 用户授权](../../../../intl.zh-CN/快速入门/为 RAM 用户授权.md#) 时遵循最小授权原则。

## 原则 4：使用带 IP 限制条件的权限策略进行授权 {#section_r5n_xkk_xdb .section}

授予所有的特权操作必须受 IP 条件限制（acs:SourceIp）。

即使 RAM 用户的登录密码或 AccessKey 泄露，只要攻击者没有渗透进入您的可信网络，就无法进行攻击。

## 原则 5：使用带 MFA 限制条件的权限策略进行授权 {#section_s5n_xkk_xdb .section}

授予所有的特权操作必须受 MFA 条件限制（acs:MFAPresent）。

即使 RAM 用户的登录密码或 AccessKey 泄露，只要 MFA 设备没有丢失，就无法进行攻击。

更多限制条件，请参考 [Policy 结构和语法](../../../../intl.zh-CN/用户指南/权限管理/Policy 语言/Policy 结构和语法.md#)。

遵循最佳安全实践原则，综合利用这些保护机制，可以有效的保护账号资产的安全。

