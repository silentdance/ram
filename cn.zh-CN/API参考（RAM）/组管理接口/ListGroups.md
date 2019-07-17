# ListGroups {#doc_api_Ram_ListGroups .reference}

调用ListGroups接口列出所有的用户组。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=ListGroups)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListGroups|系统规定参数。取值：ListGroups。

 |
|Marker|String|否|EXAMPLE|当请求的返回结果被截断时，可以使用`Marker`获取从当前截断位置之后的内容。

 |
|MaxItems|Integer|否|100|指定返回结果的条数，当返回结果达到`MaxItems`限制被截断时，返回参数`IsTruncated`将等于`true`。

 取值范围：1 ~ 1000，默认值：100。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Groups| | |用户组信息。

 |
|Comments|String|开发团队|备注信息。

 |
|CreateDate|String|2015-01-23T12:33:18Z|创建时间。

 |
|GroupName|String|Dev-Team|用户组名称。

 |
|UpdateDate|String|2015-01-23T12:33:18Z|更新时间。

 |
|IsTruncated|Boolean|true|请求返回结果是否被截断。

 |
|Marker|String|EXAMPLE|当`IsTruncated`为`true`时才有此字段，当返回`true`时，需要继续调用此接口，并且使用`Marker`获取截断后的内容。

 |
|RequestId|String|065527AA-2F2E-AD7C-7484-F2626CFE4934|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=ListGroups
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ListGroupsResponse>
  <RequestId>065527AA-2F2E-AD7C-7484-F2626CFE4934</RequestId>
  <IsTruncated>true</IsTruncated>
  <Marker>EXAMPLE</Marker>
  <Groups>
    <Group>
      <GroupName>Dev-Team</GroupName>
      <Comments>开发团队</Comments>
      <CreateDate>2015-01-23T12:33:18Z</CreateDate>
      <UpdateDate>2015-01-23T12:33:18Z</UpdateDate>
    </Group>
    <Group>
      <GroupName>QA-Team</GroupName>
      <Comments>测试团队</Comments>
      <CreateDate>2015-02-18T17:22:08Z</CreateDate>
      <UpdateDate>2015-02-18T17:22:08Z</UpdateDate>
    </Group>
  </Groups>
</ListGroupsResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Groups":{
		"Group":[
			{
				"Comments":"开发团队",
				"GroupName":"Dev-Team",
				"UpdateDate":"2015-01-23T12:33:18Z",
				"CreateDate":"2015-01-23T12:33:18Z"
			},
			{
				"Comments":"测试团队",
				"GroupName":"QA-Team",
				"UpdateDate":"2015-02-18T17:22:08Z",
				"CreateDate":"2015-02-18T17:22:08Z"
			}
		]
	},
	"IsTruncated":true,
	"RequestId":"065527AA-2F2E-AD7C-7484-F2626CFE4934",
	"Marker":"EXAMPLE"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ram)查看更多错误码。

