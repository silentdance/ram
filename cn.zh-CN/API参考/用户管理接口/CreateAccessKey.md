# CreateAccessKey {#doc_api_977683 .reference}

为RAM子用户创建AccessKey。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=CreateAccessKey)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateAccessKey|系统规定参数。取值：CreateAccessKey

 |
|UserName|String|否|zhangqiang|指定用户名，子账号调用此接口时，默认为自己创建AccessKey。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|AccessKey| | |访问密钥。

 |
|└AccessKeyId|String|0wNEpMMlzy7szvai|访问密钥标识。

 |
|└AccessKeySecret|String|PupkTg8jdmau1cXxYacgE736PJj4cA|访问密钥。

 |
|└CreateDate|String|2015-01-23T12:33:18Z|创建时间。

 |
|└Status|String|Active|状态，激活或禁用。

 |
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=CreateAccessKey
&UserName=zhangqiang
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateAccessKeyResponse>
  <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
  <AccessKey>
    <AccessKeyId>0wNEpMMlzy7szvai</AccessKeyId>
    <AccessKeySecret>PupkTg8jdmau1cXxYacgE736PJj4cA</AccessKeySecret>
    <Status>Active</Status>
    <CreateDate>2015-01-23T12:33:18Z</CreateDate>
  </AccessKey>
</CreateAccessKeyResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"AccessKey":{
		"Status":"Active",
		"AccessKeySecret":"PupkTg8jdmau1cXxYacgE736PJj4cA",
		"AccessKeyId":"0wNEpMMlzy7szvai",
		"CreateDate":"2015-01-23T12:33:18Z"
	},
	"RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ram)

