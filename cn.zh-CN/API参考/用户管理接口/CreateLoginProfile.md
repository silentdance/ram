# CreateLoginProfile {#doc_api_977699 .reference}

为一个RAM子用户启用Web控制台登录。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=CreateLoginProfile)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|UserName|String|是|zhangqiang|指定用户名。

 |
|Password|String|是|mypassword|指定密码，密码必须符合密码强度要求。关于密码强度设置接口，请参考[GetPasswordPolicy](~~28740~~)。

 |
|Action|String|是|CreateLoginProfile|系统规定参数。取值：CreateLoginProfile

 |
|PasswordResetRequired|Boolean|否|false|指定用户在登录时是否需要修改密码。默认为false。

 |
|MFABindRequired|Boolean|否|false|指定用户在下次登录时是否必须绑定多因素认证器。默认为false。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|LoginProfile| | |登录配置信息。

 |
|└CreateDate|String|2015-01-23T12:33:18Z|创建时间。

 |
|└MFABindRequired|Boolean|false|要求必须绑定多因素认证设备。

 |
|└PasswordResetRequired|Boolean|false|要求下次登录时重设密码。

 |
|└UserName|String|zhangqiang|用户名。

 |
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=CreateLoginProfile
&UserName=zhangqiang
&Password=mypassword
&PasswordResetRequired=false
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateLoginProfile>
  <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
  <LoginProfile>
    <UserName>zhangqiang</UserName>
    <PasswordResetRequired>true</PasswordResetRequired>
    <MFABindRequired>true</MFABindRequired>
    <CreateDate>2015-01-23T12:33:18Z</CreateDate>
  </LoginProfile>
</CreateLoginProfile>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368",
	"LoginProfile":{
		"PasswordResetRequired":true,
		"MFABindRequired":true,
		"UserName":"zhangqiang",
		"CreateDate":"2015-01-23T12:33:18Z"
	}
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ram)

