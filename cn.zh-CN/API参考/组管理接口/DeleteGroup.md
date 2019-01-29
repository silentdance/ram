# DeleteGroup {#doc_api_977713 .reference}

删除指定的组。

-   删除组前，需要保证组不拥有任何授权策略（Policy）。
-   删除组前，需要保证组不拥有任何用户（User）。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=DeleteGroup)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteGroup|系统规定参数。取值：DeleteGroup

 |
|GroupName|String|是|Dev-Team|指定组名，例：dev。

 格式：`^[a-zA-Z0-9\-]+$`。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|FCF40AB5-881C-A0F9-334C-B0AD423AA69D|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=DeleteGroup
&GroupName=Dev-Team
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteGroupResponse>
  <RequestId>FCF40AB5-881C-A0F9-334C-B0AD423AA69D</RequestId>
</DeleteGroupResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"FCF40AB5-881C-A0F9-334C-B0AD423AA69D"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ram)

