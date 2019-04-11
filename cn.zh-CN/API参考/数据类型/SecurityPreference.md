# SecurityPreference {#reference_alh_5mv_xdb .reference}

安全首选项。

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|AccessKeyPreference| | |访问密钥首选项。|
|└AllowUserToManageAccessKeys|Boolean|false|是否允许用户管理自己的访问密钥。|
|LoginProfilePreference| | |登录首选项。|
|└AllowUserToChangePassword|Boolean|true|是否允许用户修改自己的密码。|
|└EnableSaveMFATicket|Boolean|true|是否允许在用户在登录时保存MFA验证票据。|
|└LoginNetworkMasks|String|10.0.0.0/8|登录掩码，默认空字符串，不限制登录IP。|
|└LoginSessionDuration|Integer|6|用户登录有效期，单位：小时。|
|MFAPreference| | |多因素认证首选项。|
|└AllowUserToManageMFADevices|Boolean|true|是否允许用户管理自己绑定或解绑多因素认证设备。|
|PublicKeyPreference| | |公钥首选项。|
|└AllowUserToManagePublicKeys|Boolean|false|是否允许用户管理自己的公钥。|

