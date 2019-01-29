# ListRoles {#doc_api_977676 .reference}

列出角色。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=ListRoles)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListRoles|系统规定参数。取值：ListRoles

 |
|Marker|String|否|EXAMPLE|当请求的返回结果被截断时，可以使用`Marker`获取从当前截断位置之后的内容。

 |
|MaxItems|Integer|否|100|指定返回结果的条数。当返回结果达到`MaxItems`限制被截断时，返回参数`IsTruncated`将等于`true`。

 取值范围：1

 -   1000，默认值：100。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|IsTruncated|Boolean|true|请求返回结果是否被截断。

 |
|Marker|String|EXAMPLE|当IsTruncated为true时才有此字段。当返回true时，需要继续调用此接口，并且使用Marker获取截断后的内容。

 |
|RequestId|String|7B8A4E7D-6CFF-471D-84DF-195A7A241ECB|请求ID。

 |
|Roles| | |角色名称列表。

 |
|└Arn|String|acs:ram::1234567890123456:role/ECSAdmin|角色的资源描述符。

 |
|└CreateDate|String|2015-01-23T12:33:18Z|创建时间。

 |
|└Description|String|ECS管理角色|角色的文字描述。

 |
|└RoleId|String|901234567890123|角色ID。

 |
|└RoleName|String|ECSAdmin|角色名称。

 |
|└UpdateDate|String|2015-01-23T12:33:18Z|更新时间。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=ListRoles
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ListRolesResponse>
  <RequestId>7B8A4E7D-6CFF-471D-84DF-195A7A241ECB</RequestId>
  <IsTruncated>true</IsTruncated>
  <Marker>EXAMPLE</Marker>
  <Roles>
    <Role>
      <RoleId>901234567890123</RoleId>
      <RoleName>ECSAdmin</RoleName>
      <Arn>acs:ram::1234567890123456:role/ECSAdmin</Arn>
      <Description>ECS管理角色</Description>
      <CreateDate>2015-01-23T12:33:18Z</CreateDate>
      <UpdateDate>2015-01-23T12:33:18Z</UpdateDate>
    </Role>
    <Role>
      <RoleId>901234567890456</RoleId>
      <RoleName>OSSReadonlyAccess</RoleName>
      <Arn>acs:ram::1234567890123456:role/OSSReadonlyAccess</Arn>
      <Description>OSS只读访问角色</Description>
      <CreateDate>2015-01-23T12:33:18Z</CreateDate>
      <UpdateDate>2015-01-23T12:33:18Z</UpdateDate>
    </Role>
  </Roles>
</ListRolesResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"IsTruncated":true,
	"RequestId":"7B8A4E7D-6CFF-471D-84DF-195A7A241ECB",
	"Roles":{
		"Role":[
			{
				"RoleName":"ECSAdmin",
				"Description":"ECS管理角色",
				"UpdateDate":"2015-01-23T12:33:18Z",
				"Arn":"acs:ram::1234567890123456:role/ECSAdmin",
				"CreateDate":"2015-01-23T12:33:18Z",
				"RoleId":"901234567890123"
			},
			{
				"RoleName":"OSSReadonlyAccess",
				"Description":"OSS只读访问角色",
				"UpdateDate":"2015-01-23T12:33:18Z",
				"Arn":"acs:ram::1234567890123456:role/OSSReadonlyAccess",
				"CreateDate":"2015-01-23T12:33:18Z",
				"RoleId":"901234567890456"
			}
		]
	},
	"Marker":"EXAMPLE"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ram)

