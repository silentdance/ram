# ListPolicyVersions {#doc_api_Ram_ListPolicyVersions .reference}

调用ListPolicyVersions接口列出权限策略版本。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=ListPolicyVersions)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListPolicyVersions|系统规定参数。取值：ListPolicyVersions

 |
|PolicyName|String|是|OSS-Administrator|权限策略名称。

 |
|PolicyType|String|是|Custom|指定权限策略的类型, 取值为：`System`或`Custom`。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|PolicyVersions| | |权限策略版本信息。

 |
|└CreateDate|String|2015-02-26T01:25:52Z|创建时间。

 |
|└IsDefaultVersion|Boolean|false|是否默认版本。

 |
|└PolicyDocument|String|\{ "Statement": \[\{ "Action": \["oss:\*"\], "Effect": "Allow", "Resource": \["acs:oss:\*:\*:\*"\]\}\], "Version": "1"\}|权限策略内容。

 |
|└VersionId|String|v3|权限策略标识。

 |
|RequestId|String|7B8A4E7D-6CFF-471D-84DF-195A7A241ECB|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=ListPolicyVersions
&PolicyName=OSS-Administrator
&PolicyType=Custom
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ListPolicyVersionsResponse>
  <RequestId>7B8A4E7D-6CFF-471D-84DF-195A7A241ECB</RequestId>
  <PolicyVersions>
    <PolicyVersion>
      <VersionId>v3</VersionId>
      <IsDefaultVersion>false</IsDefaultVersion>
      <CreateDate>2015-01-23T12:33:18Z</CreateDate>
      <PolicyDocument>{ "Statement": [{ "Action": ["oss:*"], "Effect": "Allow", "Resource": ["acs:oss:*:*:*"]}], "Version": "1"}</PolicyDocument>
    </PolicyVersion>
    <PolicyVersion>
      <VersionId>v5</VersionId>
      <IsDefaultVersion>true</IsDefaultVersion>
      <CreateDate>2015-02-26T01:25:52Z</CreateDate>
      <PolicyDocument>{ "Statement": [{ "Action": ["oss:*"], "Effect": "Allow", "Resource": ["acs:oss:*:*:*"]}], "Version": "1"}</PolicyDocument>
    </PolicyVersion>
  </PolicyVersions>
</ListPolicyVersionsResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"7B8A4E7D-6CFF-471D-84DF-195A7A241ECB",
	"PolicyVersions":{
		"PolicyVersion":[
			{
				"IsDefaultVersion":false,
				"VersionId":"v3",
				"PolicyDocument":"{ \"Statement\": [{ \"Action\": [\"oss:*\"], \"Effect\": \"Allow\", \"Resource\": [\"acs:oss:*:*:*\"]}], \"Version\": \"1\"}",
				"CreateDate":"2015-01-23T12:33:18Z"
			},
			{
				"IsDefaultVersion":true,
				"VersionId":"v5",
				"PolicyDocument":"{ \"Statement\": [{ \"Action\": [\"oss:*\"], \"Effect\": \"Allow\", \"Resource\": [\"acs:oss:*:*:*\"]}], \"Version\": \"1\"}",
				"CreateDate":"2015-02-26T01:25:52Z"
			}
		]
	}
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ram)

