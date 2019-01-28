# CreateUser {#doc_api_936640 .reference}

创建RAM子用户。

## 调试 {#apiExplorer .section}

单击[这里](https://api.aliyun.com/#product=Ram&api=CreateUser)在OpenAPI Explorer中进行可视化调试，并生成SDK代码示例。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|UserName|String|是|zhangqiang|指定用户名，最多包含64个字符。

 格式：`^[a-zA-Z0-9\.@\-_]+$`。

 |
|Comments|String|否|Thisisacloudcomputingengineer|备注，最大长度128个字符。

 |
|DisplayName|String|否|zhangqiang|显示名称，最多包含128个字符或汉字。

 格式：`^[a-zA-Z0-9\.@\-\u4e00-\u9fa5]+$`。

 |
|Email|String|否|zhangqiang@example.com|RAM用户的邮箱。

 |
|MobilePhone|String|否|86-18688888888|RAM用户手机号。

 格式：国际区号-号码，例如：86-18600008888。

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
|└Email|String|zhangqiang@example.com|RAM用户的邮箱。

 |
|└MobilePhone|String|86-18600008888|RAM用户手机号。

 |
|└UserId|String|1227489245380721|用户唯一标识。

 |
|└UserName|String|zhangqiang|用户名称。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=CreateUser
&UserName=zhangqiang
&DisplayName=zhangqiang.
&MobilePhone=86-18688888888
&Email=zhangqiang@example.com
&Comments=This is a cloud computing engineer.
&<公共请求参数>


```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateUserResponse>
  <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
  <User>
    <UserId>1227489245380721</UserId>
    <UserName>zhangqiang</UserName>
    <DisplayName>zhangqiang</DisplayName>
    <MobilePhone>86-18600008888</MobilePhone>
    <Email>zhangqiang@example.com</Email>
    <Comments>This is a cloud computing engineer.</Comments>
    <CreateDate>2015-01-23T12:33:18Z</CreateDate>
  </User>
</CreateUserResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"User":{
		"Comments":"这是一位云计算工程师",
		"Email":"zhangqiang@example.com",
		"UserName":"zhangqiang",
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

