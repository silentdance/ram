# GetPolicyVersion {#doc_api_977689 .reference}

获取某个权限策略的版本。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=GetPolicyVersion)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetPolicyVersion|系统规定参数。取值：GetPolicyVersion

 |
|PolicyName|String|是|OSS-Administrator|权限策略名称。

 |
|PolicyType|String|是|Custom|指定权限的类型, 取值`System`或`Custom`。

 |
|VersionId|String|是|v3|指定目标版本的ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|PolicyVersion| | |权限策略版本信息。

 |
|└CreateDate|String|2015-01-23T12:33:18Z|创建时间。

 |
|└IsDefaultVersion|Boolean|false|是否默认版本。

 |
|└PolicyDocument|String|\{ "Statement": \[\{ "Action": \["oss:\*"\], "Effect": "Allow", "Resource": \["acs:oss:\*:\*:\*"\]\}\], "Version": "1"\}|权限策略内容。

 |
|└VersionId|String|v3|权限策略标识。

 |
|RequestId|String|9B34724D-54B0-4A51-B34D-4512372FE1BE|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=GetPolicyVersion
&PolicyName=OSS-Administrator
&PolicyType=Custom
&VersionId=v3
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<GetPolicyVersionResponse>
  <RequestId>9B34724D-54B0-4A51-B34D-4512372FE1BE</RequestId>
  <PolicyVersion>
    <VersionId>v3</VersionId>
    <IsDefaultVersion>false</IsDefaultVersion>
    <CreateDate>2015-01-23T12:33:18Z</CreateDate>
    <PolicyDocument>
            { "Statement": [{ "Action": ["oss:*"], "Effect": "Allow", "Resource": ["acs:oss:*:*:*"]}], "Version": "1"}
        </PolicyDocument>
  </PolicyVersion>
</GetPolicyVersionResponse>

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

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ram)

