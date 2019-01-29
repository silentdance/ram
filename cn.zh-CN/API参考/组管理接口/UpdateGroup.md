# UpdateGroup {#doc_api_977714 .reference}

更新用户组信息。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=UpdateGroup)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateGroup|系统规定参数。取值：UpdateGroup

 |
|GroupName|String|是|Dev-Team|指定组名称。

 格式：`^[a-zA-Z0-9\-]+$`。

 |
|NewComments|String|否|开发团队|新的备注信息，最大长度128个字符。

 |
|NewGroupName|String|否|NewDev-Team|新的组名。

 格式：`^[a-zA-Z0-9\-]+$`。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Group| | |组信息。

 |
|└Comments|String|开发团队|备注信息。

 |
|└CreateDate|String|2015-01-23T12:33:18Z|创建时间。

 |
|└GroupName|String|NewDev-Team|组名称。

 |
|└UpdateDate|String|2015-01-23T12:33:18Z|更新时间。

 |
|RequestId|String|EC6647CC-0A36-EC7A-BA72-CC81BF3DE182|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=UpdateGroup
&GroupName=Dev-Team
&NewGroupName=NewDev-Team
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<UpdateGroupResponse>
  <RequestId>EC6647CC-0A36-EC7A-BA72-CC81BF3DE182</RequestId>
  <Group>
    <GroupName>NewDev-Team</GroupName>
    <Comments>开发团队</Comments>
    <CreateDate>2015-01-23T12:33:18Z</CreateDate>
    <UpdateDate>2015-01-23T12:33:18Z</UpdateDate>
  </Group>
</UpdateGroupResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"EC6647CC-0A36-EC7A-BA72-CC81BF3DE182",
	"Group":{
		"Comments":"开发团队",
		"GroupName":"NewDev-Team",
		"UpdateDate":"2015-01-23T12:33:18Z",
		"CreateDate":"2015-01-23T12:33:18Z"
	}
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ram)

