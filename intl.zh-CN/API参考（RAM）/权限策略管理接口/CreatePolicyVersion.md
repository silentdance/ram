# CreatePolicyVersion {#doc_api_Ram_CreatePolicyVersion .reference}

调用CreatePolicyVersion接口为权限策略创建新的版本。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=CreatePolicyVersion)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreatePolicyVersion|系统规定参数。取值：CreatePolicyVersion

 |
|PolicyDocument|String|是|\{"Statement":\[\{"Action":\["oss:\*"\],"Effect":"Allow","Resource":\["acs:oss:\*:\*:\*"\]\}\],"Version":"1"\}|权限策略内容，最大长度2048字节。

 |
|PolicyName|String|是|OSS-Administrator|权限策略名称。

 |
|RotateStrategy|String|否|None|权限策略版本自动化轮转机制，可以删除历史权限策略版本。

 目前包含：

 -   `None`: 关闭轮转机制。
-   `DeleteOldestNonDefaultVersionWhenLimitExceeded`：当权限策略版本数量超限时，删除最早且非活跃的版本。

 默认值：`None`

 |
|SetAsDefault|Boolean|否|false|是否设置为默认权限策略，默认值为`false`。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|PolicyVersion| | |新建的权限策略版本的信息。

 |
|CreateDate|String|2015-01-23T12:33:18Z|创建时间。

 |
|IsDefaultVersion|Boolean|false|是否默认版本。

 |
|PolicyDocument|String|\{ "Statement": \[\{ "Action": \["oss:\*"\], "Effect": "Allow", "Resource": \["acs:oss:\*:\*:\*"\]\}\], "Version": "1"\}|权限策略内容。

 |
|VersionId|String|v3|权限策略标识。

 |
|RequestId|String|9B34724D-54B0-4A51-B34D-4512372FE1BE|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=CreatePolicyVersion
&PolicyName=OSS-Administrator
&PolicyDocument={"Statement":[{"Action":["oss:*"],"Effect":"Allow","Resource":["acs:oss:*:*:*"]}],"Version":"1"}
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreatePolicyVersionResponse>
  <RequestId>9B34724D-54B0-4A51-B34D-4512372FE1BE</RequestId>
  <PolicyVersion>
    <VersionId>v3</VersionId>
    <IsDefaultVersion>false</IsDefaultVersion>
    <CreateDate>2015-01-23T12:33:18Z</CreateDate>
    <PolicyDocument>{ "Statement": [{ "Action": ["oss:*"], "Effect": "Allow", "Resource": ["acs:oss:*:*:*"]}], "Version": "1"}</PolicyDocument>
  </PolicyVersion>
</CreatePolicyVersionResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"9B34724D-54B0-4A51-B34D-4512372FE1BE",
	"PolicyVersion":{
		"IsDefaultVersion":false,
		"VersionId":"v3",
		"PolicyDocument":"{ \"Statement\": [{ \"Action\": [\"oss:*\"], \"Effect\": \"Allow\", \"Resource\": [\"acs:oss:*:*:*\"]}], \"Version\": \"1\"}",
		"CreateDate":"2015-01-23T12:33:18Z"
	}
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ram)查看更多错误码。

