# ListPoliciesForUser {#doc_api_Ram_ListPoliciesForUser .reference}

调用ListPoliciesForUser接口列出指定用户的权限策略。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ram&api=ListPoliciesForUser&type=RPC&version=2015-05-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListPoliciesForUser|系统规定参数。取值：ListPoliciesForUser

 |
|UserName|String|是|zhangq\*\*\*\*|指定用户名。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Policies| | |权限策略信息。

 |
|AttachDate|String|2015-01-23T12:33:18Z|授权时间。

 |
|DefaultVersion|String|v1|默认版本。

 |
|Description|String|OSS管理员权限|权限策略描述。

 |
|PolicyName|String|OSS-Administrator|权限策略名称。

 |
|PolicyType|String|Custom|权限策略类型。

 |
|RequestId|String|7B8A4E7D-6CFF-471D-84DF-195A7A241ECB|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=ListPoliciesForUser
&UserName=zhangq****
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ListPoliciesForUserResponse>
    <RequestId>7B8A4E7D-6CFF-471D-84DF-195A7A241ECB</RequestId>
    <Policies>
        <Policy>
            <PolicyName>OSS-Administrator</PolicyPolicyName>
            <PolicyType>Custom</PolicyType>
            <Description>OSS管理员权限</Description>
            <DefaultVersion>v1</DefaultVersion>
            <AttachDate>2015-01-23T12:33:18Z</AttachDate>
        </Policy>
        <Policy>
            <PolicyName>ReadOnlyAccess</PolicyPolicyName>
            <PolicyType>System</PolicyType>
            <Description>只读权限</Description>
            <DefaultVersion>v1</DefaultVersion>
            <AttachDate>2015-02-18T17:22:08Z</AttachDate>
        </Policy>
    </Policies>
</ListPoliciesForUserResponse>
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

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ram)查看更多错误码。

