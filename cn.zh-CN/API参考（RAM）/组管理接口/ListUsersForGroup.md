# ListUsersForGroup {#doc_api_Ram_ListUsersForGroup .reference}

调用ListUsersForGroup接口列出指定用户组所包含的RAM用户。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=ListUsersForGroup)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListUsersForGroup|系统规定参数。取值：ListUsersForGroup

 |
|GroupName|String|是|Dev-Team|用户组名称。

 |
|Marker|String|否|EXAMPLE|当请求的返回结果被截断时，可以使用`Marker`获取从当前截断位置之后的内容。

 |
|MaxItems|Integer|否|100|指定返回结果的条数。当返回结果达到`MaxItems`限制被截断时，返回参数`IsTruncated`将等于`true`。

 取值范围：1 ~ 1000，默认值：100。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|IsTruncated|Boolean|true|请求返回结果是否被截断。

 |
|Marker|String|EXAMPLE|当`IsTruncated`为`true`时才有此字段。当返回`true`时，需要继续调用此接口，并且使用`Marker`获取截断后的内容。

 |
|RequestId|String|4B450CA1-36E8-4AA2-8461-86B42BF4CC4E|请求ID。

 |
|Users| | |用户信息。

 |
|DisplayName|String|张强|显示名称。

 |
|JoinDate|String|2015-01-23T12:33:18Z|加入日期。

 |
|UserName|String|zhangqiang|用户名称。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=ListUsersForGroup
&GroupName=dev
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ListUsersForGroupResponse>
  <RequestId>5756784B-79C4-E82E-24C2-FC3E171E5AB3</RequestId>
  <Users>
    <User>
      <UserName>zhangqiang</UserName>
      <DisplayName>张强</DisplayName>
      <JoinDate>2015-01-23T12:33:18Z</JoinDate>
    </User>
    <User>
      <UserName>lili</UserName>
      <DisplayName>李丽</DisplayName>
      <JoinDate>2015-02-18T17:22:08Z</JoinDate>
    </User>
  </Users>
</ListUsersForGroupResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Users":{
		"User":[
			{
				"JoinDate":"2015-01-23T12:33:18Z",
				"UserName":"zhangqiang",
				"DisplayName":"张强"
			},
			{
				"JoinDate":"2015-02-18T17:22:08Z",
				"UserName":"lili",
				"DisplayName":"李丽"
			}
		]
	},
	"RequestId":"4B450CA1-36E8-4AA2-8461-86B42BF4CC4E"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ram)查看更多错误码。

