# GetGroup {#doc_api_Ram_GetGroup .reference}

获取用户组信息。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=GetGroup)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetGroup|系统规定参数。取值：GetGroup

 |
|GroupName|String|是|Dev-Team|组名。

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
|└GroupName|String|Dev-Team|组名称。

 |
|└UpdateDate|String|2015-02-11T03:15:21Z|更新时间。

 |
|RequestId|String|D4065824-E422-3ED6-68B1-1AF7D5C7804C|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=GetGroup
&GroupName=Dev-Team
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<GetGroupResponse>
  <RequestId>D4065824-E422-3ED6-68B1-1AF7D5C7804C</RequestId>
  <Group>
    <GroupName>Dev-Team</GroupName>
    <Comments>开发团队</Comments>
    <CreateDate>2015-01-23T12:33:18Z</CreateDate>
    <UpdateDate>2015-02-11T03:15:21Z</UpdateDate>
  </Group>
</GetGroupResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"D4065824-E422-3ED6-68B1-1AF7D5C7804C",
	"Group":{
		"Comments":"开发团队",
		"GroupName":"Dev-Team",
		"UpdateDate":"2015-02-11T03:15:21Z",
		"CreateDate":"2015-01-23T12:33:18Z"
	}
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ram)

