# CreatePolicy {#doc_api_Ram_CreatePolicy .reference}

调用CreatePolicy接口创建一个权限策略。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=CreatePolicy)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreatePolicy|系统规定参数。取值：CreatePolicy

 |
|Description|String|否|OSS管理员权限|描述，最大长度1024字字符。

 |
|PolicyDocument|String|否|\{"Statement":\[\{"Action":\["oss:\*"\],"Effect":"Allow","Resource":\["acs:oss:\*:\*:\*"\]\}\],"Version":"1"\}|权限策略内容，最大长度2048字节。

 |
|PolicyName|String|否|OSS-Administrator|权限策略名称, 最多包含128个字符。

 格式：`^[a-zA-Z0-9\-]+$`。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Policy| | |权限策略信息。

 |
|└CreateDate|String|2015-01-23T12:33:18Z|创建时间。

 |
|└DefaultVersion|String|v1|默认版本。

 |
|└Description|String|OSS管理员权限|描述。

 |
|└PolicyName|String|OSS-Administrator|权限策略名称。

 |
|└PolicyType|String|Custom|权限策略类型。

 |
|RequestId|String|9B34724D-54B0-4A51-B34D-4512372FE1BE|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=CreatePolicy
&PolicyName=OSS-Administrator
&PolicyDocument={"Statement":[{"Action":["oss:*"],"Effect":"Allow","Resource":["acs:oss:*:*:*"]}],"Version":"1"}
&Description=OSS管理员权限
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreatePolicyResponse>
  <RequestId>9B34724D-54B0-4A51-B34D-4512372FE1BE</RequestId>
  <Policy>
    <PolicyName>OSS-Administrator</PolicyName>
    <PolicyType>Custom</PolicyType>
    <Description>OSS管理员权限</Description>
    <DefaultVersion>v1</DefaultVersion>
    <CreateDate>2015-01-23T12:33:18Z</CreateDate>
  </Policy>
</CreatePolicyResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Policy":{
		"Description":"OSS管理员权限",
		"PolicyName":"OSS-Administrator",
		"CreateDate":"2015-01-23T12:33:18Z",
		"DefaultVersion":"v1",
		"PolicyType":"Custom"
	},
	"RequestId":"9B34724D-54B0-4A51-B34D-4512372FE1BE"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ram)

