# AddUserToGroup {#doc_api_977723 .reference}

将子用户添加到指定的用户组。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=AddUserToGroup)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddUserToGroup|系统规定参数。取值：AddUserToGroup

 |
|GroupName|String|是|Dev-Team|组名称。

 |
|UserName|String|是|zhangqiang|用户名称。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|1B968853-B423-63A6-FE1F-45E81BC2AD61|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=AddUserToGroup
&UserName=zhangqiang
&GroupName=Dev-Team
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AddUserToGroupResponse>
  <RequestId>1B968853-B423-63A6-FE1F-45E81BC2AD61</RequestId>
</AddUserToGroupResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"1B968853-B423-63A6-FE1F-45E81BC2AD61"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ram)

