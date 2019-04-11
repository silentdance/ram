# RemoveUserFromGroup {#doc_api_Ram_RemoveUserFromGroup .reference}

将RAM用户从用户组中移除。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=RemoveUserFromGroup)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|RemoveUserFromGroup|系统规定参数。取值：RemoveUserFromGroup

 |
|GroupName|String|是|Dev-Team|组名称。

 |
|UserName|String|是|zhangq\*\*\*\*|子用户名称。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|A07EF215-B9B3-8CB2-2899-3F9575C6E320|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=RemoveUserFromGroup
&UserName=zhangq****
&GroupName=Dev-Team
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<RemoveUserFromGroupResponse>
  <RequestId>A07EF215-B9B3-8CB2-2899-3F9575C6E320</RequestId>
</RemoveUserFromGroupResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"A07EF215-B9B3-8CB2-2899-3F9575C6E320"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ram)

