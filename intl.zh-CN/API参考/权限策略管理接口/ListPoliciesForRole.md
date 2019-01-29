# ListPoliciesForRole {#doc_api_977687 .reference}

列出角色被授予的权限策略。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=ListPoliciesForRole)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListPoliciesForRole|系统规定参数。取值：ListPoliciesForRole

 |
|RoleName|String|是|AdminRole|指定角色名，例如：AdminRole。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Policies| | |权限策略名称列表。

 |
|└AttachDate|String|2015-01-23T12:33:18Z|授权时间。

 |
|└DefaultVersion|String|v1|默认版本。

 |
|└Description|String|OSS管理员权限|权限策略描述。

 |
|└PolicyName|String|OSS-Administrator|权限策略名称。

 |
|└PolicyType|String|Custom|权限策略类型。

 |
|RequestId|String|7B8A4E7D-6CFF-471D-84DF-195A7A241ECB|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=ListPoliciesForRole
&RoleName=AdminRole
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ListPoliciesForRoleResponse>
  <RequestId>7B8A4E7D-6CFF-471D-84DF-195A7A241ECB</RequestId>
  <Policies>
    <Policy>
      <PolicyName>OSS-Administrator</PolicyName>
      <PolicyType>Custom</PolicyType>
      <Description>OSS管理员权限</Description>
      <DefaultVersion>v1</DefaultVersion>
      <AttachDate>2015-01-23T12:33:18Z</AttachDate>
    </Policy>
    <Policy>
      <PolicyName>ReadOnlyAccess</PolicyName>
      <PolicyType>System</PolicyType>
      <Description>只读权限</Description>
      <DefaultVersion>v1</DefaultVersion>
      <AttachDate>2015-02-18T17:22:08Z</AttachDate>
    </Policy>
  </Policies>
</ListPoliciesForRoleResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Policies":{
		"Policy":[
			{
				"Description":"OSS管理员权限",
				"PolicyName":"OSS-Administrator",
				"AttachDate":"2015-01-23T12:33:18Z",
				"DefaultVersion":"v1",
				"PolicyType":"Custom"
			},
			{
				"Description":"只读权限",
				"PolicyName":"ReadOnlyAccess",
				"AttachDate":"2015-02-18T17:22:08Z",
				"DefaultVersion":"v1",
				"PolicyType":"System"
			}
		]
	},
	"RequestId":"7B8A4E7D-6CFF-471D-84DF-195A7A241ECB"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ram)

