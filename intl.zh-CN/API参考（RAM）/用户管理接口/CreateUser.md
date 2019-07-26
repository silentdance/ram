# CreateUser {#doc_api_Ram_CreateUser .reference}

调用CreateUser接口创建RAM用户。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=CreateUser)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateUser|系统规定参数。取值：CreateUser。

 |
|Comments|String|否|This is a cloud computing engineer.|备注，最大长度128个字符。

 |
|DisplayName|String|否|zhangq\*\*\*\*|显示名称，最多包含128个字符或汉字。

 格式：`^[a-zA-Z0-9\.@\-\u4e00-\u9fa5]+$`。

 |
|Email|String|否|zhangq\*\*\*\*@example.com|RAM用户的邮箱。

 |
|MobilePhone|String|否|86-1868888\*\*\*\*|RAM用户手机号。

 格式：国际区号-号码。

 |
|UserName|String|否|zhangq\*\*\*\*|指定用户名，最多包含64个字符。

 格式：`^[a-zA-Z0-9\.@\-_]+$`。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|请求ID。

 |
|User| | |用户信息。

 |
|└Comments|String|这是一位云计算工程师|备注。

 |
|└CreateDate|String|2015-01-23T12:33:18Z|创建时间。

 |
|└DisplayName|String|张强|显示名称。

 |
|└Email|String|zhangq\*\*\*\*@example.com|RAM用户的邮箱。

 |
|└MobilePhone|String|86-1860000\*\*\*\*|RAM用户手机号。

 |
|└UserId|String|122748924538\*\*\*\*|用户唯一标识。

 |
|└UserName|String|zhangq\*\*\*\*|用户名称。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=CreateUser
&UserName=zhangq****
&DisplayName=zhangq****
&MobilePhone=86-1868888****
&Email=zhangq****@example.com
&Comments=This is a cloud computing engineer.
&<公共请求参数>


```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateUserResponse>
  <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
  <User>
    <UserId>122748924538****</UserId>
    <UserName>zhangq****</UserName>
    <DisplayName>zhangq****</DisplayName>
    <MobilePhone>86-1860000****</MobilePhone>
    <Email>zhangq****@example.com</Email>
    <Comments>这是一位云计算工程师</Comments>
    <CreateDate>2015-01-23T12:33:18Z</CreateDate>
  </User>
</CreateUserResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"User":{
		"Comments":"这是一位云计算工程师",
		"Email":"zhangq****@example.com",
		"UserName":"zhangq****",
		"UserId":"122748924538****",
		"MobilePhone":"86-1860000****",
		"DisplayName":"zhangq****",
		"CreateDate":"2015-01-23T12:33:18Z"
	},
	"RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ram)

