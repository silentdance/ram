# GetPolicy {#doc_api_Ram_GetPolicy .reference}

调用GetPolicy接口获取指定的权限策略信息。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=GetPolicy)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetPolicy|系统规定参数。取值：GetPolicy

 |
|PolicyName|String|是|OSS-Administrator|指定权限策略名称。

 |
|PolicyType|String|是|Custom|指定Policy的类型, 取值`System`或`Custom`。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|DefaultPolicyVersion| | |权限策略的默认版本。

 |
|CreateDate|String|2015-01-23T12:33:18Z|创建时间。

 |
|IsDefaultVersion|Boolean|true|`DefaultPolicyVersion`返回的数据结构固定为默认版本，因此`isDefault`的取值固定为`ture`。

 |
|PolicyDocument|String|\{ "Statement": \[\{ "Action": \["oss:\*"\], "Effect": "Allow", "Resource": \["acs:oss:\*:\*:\*"\]\}\], "Version": "1"\}|权限策略内容。

 |
|VersionId|String|v1|权限策略标识。

 |
|Policy| | |权限策略的基本信息。

 |
|AttachmentCount|Integer|0|引用次数。

 |
|CreateDate|String|2015-01-23T12:33:18Z|创建时间。

 |
|DefaultVersion|String|v1|默认版本。

 |
|Description|String|OSS管理员权限|权限策略描述。

 |
|PolicyDocument|String|N/A|已废弃。

 |
|PolicyName|String|OSS-Administrator|权限策略名称。

 |
|PolicyType|String|Custom|权限策略类型。

 |
|UpdateDate|String|2015-01-23T12:33:18Z|修改时间。

 |
|RequestId|String|697852FB-50D7-44D9-9774-530C31EAC572|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=GetPolicy
&PolicyName=OSS-Administrator
&PolicyType=Custom
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<GetPolicyResponse>
  <RequestId>697852FB-50D7-44D9-9774-530C31EAC572</RequestId>
  <Policy>
    <PolicyName>OSS-Administrator</PolicyName>
    <PolicyType>Custom</PolicyType>
    <Description>OSS管理员权限</Description>
    <DefaultVersion>v1</DefaultVersion>
    <CreateDate>2015-01-23T12:33:18Z</CreateDate>
    <UpdateDate>2015-01-23T12:33:18Z</UpdateDate>
    <AttachmentCount>0</AttachmentCount>
  </Policy>
  <DefaultPolicyVersion>
    <VersionId>v1</VersionId>
    <IsDefaultVersion>true</IsDefaultVersion>
    <CreateDate>2015-01-23T12:33:18Z</CreateDate>
    <PolicyDocument>{ "Statement": [{ "Action": ["oss:*"], "Effect": "Allow", "Resource": ["acs:oss:*:*:*"]}], "Version": "1"}</PolicyDocument>
  </DefaultPolicyVersion>
</GetPolicyResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Policy":{
		"AttachmentCount":0,
		"Description":"OSS管理员权限",
		"PolicyName":"OSS-Administrator",
		"UpdateDate":"2015-01-23T12:33:18Z",
		"CreateDate":"2015-01-23T12:33:18Z",
		"DefaultVersion":"v1",
		"PolicyType":"Custom"
	},
	"DefaultPolicyVersion":{
		"IsDefaultVersion":true,
		"VersionId":"v1",
		"PolicyDocument":"{ \"Statement\": [{ \"Action\": [\"oss:*\"], \"Effect\": \"Allow\", \"Resource\": [\"acs:oss:*:*:*\"]}], \"Version\": \"1\"}",
		"CreateDate":"2015-01-23T12:33:18Z"
	},
	"RequestId":"697852FB-50D7-44D9-9774-530C31EAC572"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ram)查看更多错误码。

