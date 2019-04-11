# ListUsers {#doc_api_Ram_ListUsers .reference}

列出所有RAM用户。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=ListUsers)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListUsers|系统规定参数。取值：ListUsers

 |
|Marker|String|否|EXAMPLE|当请求的返回结果被截断时，可以使用Marker获取从当前截断位置之后的内容。

 |
|MaxItems|Integer|否|100|指定返回结果的条数，当返回结果达到MaxItems限制被截断时，返回参数`IsTruncated`将等于`true`。

 取值范围：1

 -   100，默认值：100。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|IsTruncated|Boolean|true|请求返回结果是否被截断。

 |
|Marker|String|EXAMPLE|当`IsTruncated`为`true`时才有此字段，当返回`true`时，需要继续调用此接口，并且使用`Marker`获取截断后的内容 。

 |
|RequestId|String|4B450CA1-36E8-4AA2-8461-86B42BF4CC4E|请求ID。

 |
|Users| | |用户信息集合。

 |
|└Comments|String|这是一位云计算工程师|备注。

 |
|└CreateDate|String|2015-01-23T12:33:18Z|创建时间。

 |
|└DisplayName|String|张\*|显示名称。

 |
|└Email|String|zhangq\*\*\*\*@example.com|RAM用户邮箱。

 |
|└MobilePhone|String|86-1860000\*\*\*\*|RAM用户手机号。

 |
|└UpdateDate|String|2015-01-23T12:33:18Z|更新时间。

 |
|└UserId|String|122748924538\*\*\*\*|用户唯一标识。

 |
|└UserName|String|zhangq\*\*\*\*|用户名称。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=ListUsers
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ListUsersResponse>
  <RequestId>4B450CA1-36E8-4AA2-8461-86B42BF4CC4E</RequestId>
  <Users>
    <User>
      <UserId>122748924538****</UserId>
      <UserName>zhangq****</UserName>
      <DisplayName>张*</DisplayName>
      <MobilePhone>86-1860000****</MobilePhone>
      <Email>zhangq****@example.com</Email>
      <Comments>这是一位云计算工程师</Comments>
      <CreateDate>2015-01-23T12:33:18Z</CreateDate>
      <UpdateDate>2015-01-23T12:33:18Z</UpdateDate>
    </User>
    <User>
      <UserId>140649822472****</UserId>
      <UserName>li****</UserName>
      <DisplayName>李*</DisplayName>
      <MobilePhone>86-1860000****</MobilePhone>
      <Email>li****@example.com</Email>
      <Comments>权限管理员</Comments>
      <CreateDate>2015-02-18T17:22:08Z</CreateDate>
      <UpdateDate>2015-02-18T17:22:08Z</UpdateDate>
    </User>
  </Users>
  <IsTruncated>true</IsTruncated>
  <Marker>EXAMPLE</Marker>
</ListUsersResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Users":{
		"User":[
			{
				"Comments":"这是一位云计算工程师",
				"Email":"zhangq****@example.com",
				"UserName":"zhangq****",
				"UpdateDate":"2015-01-23T12:33:18Z",
				"UserId":"122748924538****",
				"MobilePhone":"86-1860000****",
				"DisplayName":"张*",
				"CreateDate":"2015-01-23T12:33:18Z"
			},
			{
				"Comments":"权限管理员",
				"Email":"li****@example.com",
				"UserName":"li****",
				"UpdateDate":"2015-02-18T17:22:08Z",
				"UserId":"140649822472****",
				"MobilePhone":"86-1860000****",
				"DisplayName":"李*",
				"CreateDate":"2015-02-18T17:22:08Z"
			}
		]
	},
	"IsTruncated":true,
	"RequestId":"4B450CA1-36E8-4AA2-8461-86B42BF4CC4E",
	"Marker":"EXAMPLE"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ram)

