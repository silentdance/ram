# ListAccessKeys {#doc_api_977668 .reference}

列出指定用户的AccessKeys。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=ListAccessKeys)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListAccessKeys|系统规定参数。取值：ListAccessKeys

 |
|UserName|String|否|zhangqiang|指定用户，子帐号访问时不提供此参数则表示列出自己的AccessKeys。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|AccessKeys| | |用户信息集合。

 |
|└AccessKeyId|String|0wNEpMMlzy7szvai|访问密钥标识。

 |
|└CreateDate|String|2015-01-23T12:33:18Z|创建时间。

 |
|└Status|String|Active|状态，激活或禁用。

 |
|RequestId|String|4B450CA1-36E8-4AA2-8461-86B42BF4CC4E|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=ListAccessKeys
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ListAccessKeysResponse>
  <RequestId>4B450CA1-36E8-4AA2-8461-86B42BF4CC4E</RequestId>
  <AccessKeys>
    <AccessKey>
      <AccessKeyId>0wNEpMMlzy7szvai</AccessKeyId>
      <Status>Active</Status>
      <CreateDate>2015-01-23T12:33:18Z</CreateDate>
    </AccessKey>
    <AccessKey>
      <AccessKeyId>WnIWUruvfaDT37vQ</AccessKeyId>
      <Status>Inactive</Status>
      <CreateDate>2015-03-24T21:12:21Z</CreateDate>
    </AccessKey>
  </AccessKeys>
</ListAccessKeysResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"4B450CA1-36E8-4AA2-8461-86B42BF4CC4E",
	"AccessKeys":{
		"AccessKey":[
			{
				"Status":"Active",
				"AccessKeyId":"0wNEpMMlzy7szvai",
				"CreateDate":"2015-01-23T12:33:18Z"
			},
			{
				"Status":"Inactive",
				"AccessKeyId":"WnIWUruvfaDT37vQ",
				"CreateDate":"2015-03-24T21:12:21Z"
			}
		]
	}
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ram)

