# ListPolicies {#doc_api_Ram_ListPolicies .reference}

调用ListPolicies接口列出权限策略。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=ListPolicies)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListPolicies|系统规定参数。取值：ListPolicies。

 |
|Marker|String|否|EXAMPLE|当请求的返回结果被截断时，可以使用`Marker`获取从当前截断位置之后的内容。

 |
|MaxItems|Integer|否|100|指定返回结果的条数，当返回结果达到`MaxItems`限制被截断时，返回参数`IsTruncated`将等于`true`。

 取值范围：1 ~ 1000，默认值：100。

 |
|PolicyType|String|否|System|指定`Policy`的类型, 取值`System`或`Custom`，如果没有指定则列出所有权限策略。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|IsTruncated|Boolean|true|请求返回结果是否被截断。

 |
|Marker|String|EXAMPLE|当`IsTruncated`为`true`时才有此字段，当返回`true`时，需要继续调用此接口，并且使用`Marker`获取截断后的内容 。

 |
|Policies| | |权限策略信息。

 |
|AttachmentCount|Integer|3|引用次数。

 |
|CreateDate|String|2015-01-23T12:33:18Z|创建时间。

 |
|DefaultVersion|String|v1|默认版本。

 |
|Description|String|OSS管理员权限|权限策略描述。

 |
|PolicyName|String|OSS-Administrator|权限策略名称。

 |
|PolicyType|String|System|权限策略类型。

 |
|UpdateDate|String|2015-01-23T12:33:18Z|修改时间。

 |
|RequestId|String|7B8A4E7D-6CFF-471D-84DF-195A7A241ECB|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=ListPolicies
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ListPoliciesResponse>
  <RequestId>7B8A4E7D-6CFF-471D-84DF-195A7A241ECB</RequestId>
  <IsTruncated>true</IsTruncated>
  <Marker>EXAMPLE</Marker>
  <Policies>
    <Policy>
      <PolicyName>OSS-Administrator</PolicyName>
      <PolicyType>Custom</PolicyType>
      <Description>OSS管理员权限</Description>
      <DefaultVersion>v1</DefaultVersion>
      <CreateDate>2015-01-23T12:33:18Z</CreateDate>
      <UpdateDate>2015-01-23T12:33:18Z</UpdateDate>
      <AttachmentCount>0</AttachmentCount>
    </Policy>
    <Policy>
      <PolicyName>ReadOnlyAccess</PolicyName>
      <PolicyType>System</PolicyType>
      <Description>只读权限</Description>
      <DefaultVersion>v1</DefaultVersion>
      <CreateDate>2015-02-11T18:39:12Z</CreateDate>
      <UpdateDate>2015-02-19T09:43:16Z</UpdateDate>
      <AttachmentCount>0</AttachmentCount>
    </Policy>
  </Policies>
</ListPoliciesResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Policies":{
		"Policy":[
			{
				"AttachmentCount":3,
				"Description":"OSS管理员权限",
				"PolicyName":"OSS-Administrator",
				"UpdateDate":"2015-01-23T12:33:18Z",
				"CreateDate":"2015-01-23T12:33:18Z",
				"DefaultVersion":"v1",
				"PolicyType":"Custom"
			},
			{
				"AttachmentCount":1,
				"Description":"只读权限",
				"PolicyName":"ReadOnlyAccess",
				"UpdateDate":"2015-02-19T09:43:16Z",
				"CreateDate":"2015-02-11T18:39:12Z",
				"DefaultVersion":"v1",
				"PolicyType":"System"
			}
		]
	},
	"IsTruncated":true,
	"RequestId":"7B8A4E7D-6CFF-471D-84DF-195A7A241ECB",
	"Marker":"EXAMPLE"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ram)查看更多错误码。

