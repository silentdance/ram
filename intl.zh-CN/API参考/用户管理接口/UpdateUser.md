# UpdateUser {#doc_api_936647 .reference}

更新用户的基本信息。

## 调试 {#apiExplorer .section}

单击[这里](https://api.aliyun.com/#product=Ram&api=UpdateUser)在OpenAPI Explorer中进行可视化调试，并生成SDK代码示例。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|UserName|String|是|zhangqiang|指定用户名。

 |
|NewComments|String|否|这是一位云计算工程师|指定新备注, 最大长度128个字符。

 |
|NewDisplayName|String|否|xiaoqiang|指定新显示名称。

 |
|NewEmail|String|否|zhangqiang@example.com|指定RAM用户的新邮箱。

 |
|NewMobilePhone|String|否|86-18600008888|指定RAM用户新手机号。

 格式：国际区号-号码，例如：86-18600008888。

 |
|NewUserName|String|否|xiaoqiang|指定新用户名。

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
|└Email|String|zhangqiang@example.com|RAM用户邮箱。

 |
|└MobilePhone|String|86-18600008888|RAM用户手机号。

 |
|└UpdateDate|String|2015-02-11T03:15:21Z|更新时间。

 |
|└UserId|String|1227489245380721|用户唯一标识。

 |
|└UserName|String|xiaoqiang|用户名称。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=UpdateUser
&UserName=zhangqiang
&NewUserName=xiaoqiang
&NewMobilePhone=86-18600008888
&NewEmail=zhangqiang@example.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateUserResponse>
  <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
  <User>
    <UserId>1227489245380721</UserId>
    <UserName>xiaoqiang</UserName>
    <DisplayName>张强</DisplayName>
    <MobilePhone>86-18600008888</MobilePhone>
    <Email>zhangqiang@example.com</Email>
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
		"Email":"zhangqiang@example.com",
		"UserName":"xiaoqiang",
		"UpdateDate":"2015-02-11T03:15:21Z",
		"UserId":"1227489245380721",
		"MobilePhone":"86-18600008888",
		"DisplayName":"张强",
		"CreateDate":"2015-01-23T12:33:18Z"
	},
	"RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ram)

