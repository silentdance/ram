# SetSecurityPreference {#doc_api_Ram_SetSecurityPreference .reference}

调用SetSecurityPreference接口设置全局安全首选项。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=SetSecurityPreference)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetSecurityPreference|系统规定参数。取值：SetSecurityPreference

 |
|AllowUserToChangePassword|Boolean|否|true|是否允许用户修改自己的密码。

 |
|AllowUserToManageAccessKeys|Boolean|否|false|是否允许用户管理自己的访问密钥。

 |
|AllowUserToManageMFADevices|Boolean|否|true|是否允许用户管理自己绑定或解绑多因素认证设备。

 |
|AllowUserToManagePublicKeys|Boolean|否|false|是否允许用户管理自己的公钥。

 |
|EnableSaveMFATicket|Boolean|否|true|是否允许在用户在登录时保存多因素认证设备验证票据，目前票据有效期是七天。

 |
|LoginNetworkMasks|String|否|10.0.0.0/8|登录掩码，默认空字符串，不限制登录IP。

 |
|LoginSessionDuration|Integer|否|6|用户登录有效期，单位：小时。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|请求ID。

 |
|SecurityPreference| | |安全首选项。

 |
|└AccessKeyPreference| | |访问密钥首选项。

 |
|└AllowUserToManageAccessKeys|Boolean|false|是否允许用户管理自己的访问密钥。

 |
|└LoginProfilePreference| | |登录首选项。

 |
|└AllowUserToChangePassword|Boolean|true|是否允许用户修改自己的密码。

 |
|└EnableSaveMFATicket|Boolean|true|是否允许在用户在登录时保存多因素认证设备验证票据。

 |
|└LoginNetworkMasks|String|10.0.0.0/8|登录掩码，默认空字符串，不限制登录IP。

 |
|└LoginSessionDuration|Integer|6|用户登录有效期，单位：小时。

 |
|└MFAPreference| | |多因素认证首选项。

 |
|└AllowUserToManageMFADevices|Boolean|true|是否允许用户管理自己绑定或解绑多因素认证设备。

 |
|└PublicKeyPreference| | |公钥首选项。

 |
|└AllowUserToManagePublicKeys|Boolean|false|是否允许用户管理自己的公钥。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=SetSecurityPreference
&EnableSaveMFATicket=true
&AllowUserToChangePassword=true
&AllowUserToManageAccessKeys=false
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<SetSecurityPreferenceResponse>
  <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
  <SecurityPreference>
    <LoginProfilePreference>
      <EnableSaveMFATicket>true</EnableSaveMFATicket>
      <AllowUserToChangePassword>true</AllowUserToChangePassword>
      <LoginNetworkMasks>10.0.0.0/8</LoginNetworkMasks>
      <LoginSessionDuration>6</LoginSessionDuration>
    </LoginProfilePreference>LoginProfilePreference&gt;
        <AccessKeyPreference>
      <AllowUserToManageAccessKeys>false</AllowUserToManageAccessKeys>
    </AccessKeyPreference>
    <MFAPreference>
      <AllowUserToManageMFADevices>false</AllowUserToManageMFADevices>
    </MFAPreference>
    <PublicKeyPreference>
      <AllowUserToManagePublicKeys>false</AllowUserToManagePublicKeys>
    </PublicKeyPreference>
  </SecurityPreference>
</SetSecurityPreferenceResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368",
	"SecurityPreference":{
		"LoginProfilePreference":{
			"LoginSessionDuration":6,
			"LoginNetworkMasks":"10.0.0.0/8",
			"EnableSaveMFATicket":true,
			"AllowUserToChangePassword":true
		},
		"AccessKeyPreference":{
			"AllowUserToManageAccessKeys":false
		},
		"PublicKeyPreference":{
			"AllowUserToManagePublicKeys":false
		},
		"MFAPreference":{
			"AllowUserToManageMFADevices":true
		}
	}
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ram)

