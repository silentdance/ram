# DeleteAccessKey {#doc_api_Ram_DeleteAccessKey .reference}

删除RAM用户的AccessKey。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=DeleteAccessKey)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteAccessKey|系统规定参数。取值：DeleteAccessKey

 |
|UserAccessKeyId|String|是|0wNEpMMlzy7s\*\*\*\*|指定要删除的AccessKeyId。

 |
|UserName|String|否|zhangq\*\*\*\*|指定用户名。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=DeleteAccessKey
&UserName=zhangq****
&UserAccessKeyId=0wNEpMMlzy7s****
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteAccessKeyResponse>
  <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
</DeleteAccessKeyResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ram)

