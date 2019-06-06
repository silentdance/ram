# ChangePassword {#doc_api_Ram_ChangePassword .reference}

调用ChangePassword接口修改RAM用户密码。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=ChangePassword)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ChangePassword|系统规定参数。取值：ChangePassword

 |
|NewPassword|String|是|aw$2\*\*\*\*|指定密码，密码必须符合密码强度要求。

 关于密码强度设置接口，请参考 [SetPasswordPolicy](~~28739~~)。

 |
|OldPassword|String|是|12\*\*\*\*|旧密码。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=ChangePassword
&NewPassword=aw$2****
&OldPassword=12****
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ChangePassword>
  <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
</ChangePassword>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ram)

