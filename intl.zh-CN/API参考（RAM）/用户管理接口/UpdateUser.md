# UpdateUser {#doc_api_Ram_UpdateUser .reference}

调用UpdateUser接口更新用户的基本信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ram&api=UpdateUser&type=RPC&version=2015-05-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateUser|系统规定参数。取值：UpdateUser

 |
|UserName|String|否|zhangq\*\*\*\*|指定用户名。

 |
|NewUserName|String|否|xiaoq\*\*\*\*|指定新用户名。

 格式：`^[a-zA-Z0-9\.@\-_]+$`。

 |
|NewMobilePhone|String|否|86-1860000\*\*\*\*|指定RAM用户新手机号。

 格式：国际区号-号码。

 |
|NewDisplayName|String|否|xiaoq\*\*\*\*|指定新显示名称。

 |
|NewEmail|String|否|xiaoq\*\*\*\*@example.com|指定RAM用户的新邮箱。

 |
|NewComments|String|否|这是一位云计算工程师|指定新备注, 最大长度128个字符。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|请求ID。

 |
|User| | |用户信息。

 |
|Comments|String|这是一位云计算工程师|备注。

 |
|CreateDate|String|2015-01-23T12:33:18Z|创建时间。

 |
|DisplayName|String|xiaoq\*\*\*\*|显示名称。

 |
|Email|String|xiaoq\*\*\*\*@example.com|RAM用户邮箱。

 |
|MobilePhone|String|86-1860000\*\*\*\*|RAM用户手机号。

 |
|UpdateDate|String|2015-02-11T03:15:21Z|更新时间。

 |
|UserId|String|122748924538\*\*\*\*|用户唯一标识。

 |
|UserName|String|xiaoq\*\*\*\*|用户名称。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=UpdateUser
&UserName=zhangq****
&NewUserName=xiaoq****
&NewMobilePhone=86-1860000****
&NewEmail=xiaoq****@example.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateUserResponse>
      <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
      <User>
            <UserId>122748924538****</UserId>
            <UserName>xiaoq****</UserName>
            <DisplayName>xiaoq****</DisplayName>
            <MobilePhone>86-1860000****</MobilePhone>
            <Email>xiaoq****@example.com</Email>
            <Comments>这是一位云计算工程师</Comments>
            <CreateDate>2015-01-23T12:33:18Z</CreateDate>
            <UpdateDate>2015-02-11T03:15:21Z</UpdateDate>
      </User>
</CreateUserResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"User":{
		"Comments":"这是一位云计算工程师",
		"Email":"xiaoq****@example.com",
		"UserName":"xiaoq****",
		"UpdateDate":"2015-02-11T03:15:21Z",
		"UserId":"122748924538****",
		"MobilePhone":"86-1860000****",
		"DisplayName":"xiaoq*****",
		"CreateDate":"2015-01-23T12:33:18Z"
	},
	"RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ram)查看更多错误码。

