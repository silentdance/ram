# DeletePolicyVersion {#doc_api_Ram_DeletePolicyVersion .reference}

调用DeletePolicyVersion接口删除指定的权限策略的某个版本。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=DeletePolicyVersion)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeletePolicyVersion|系统规定参数。取值：DeletePolicyVersion

 |
|PolicyName|String|是|OSS-Administrator|权限策略名称。

 |
|VersionId|String|是|v3|指定目标版本的ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|9B34724D-54B0-4A51-B34D-4512372FE1BE|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=DeletePolicyVersion
&PolicyName=OSS-Administrator
&VersionId=v3
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeletePolicyVersionResponse>
  <RequestId>9B34724D-54B0-4A51-B34D-4512372FE1BE</RequestId>
</DeletePolicyVersionResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"9B34724D-54B0-4A51-B34D-4512372FE1BE"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ram)

