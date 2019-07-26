# ListRoles {#doc_api_Ram_ListRoles .reference}

调用ListRoles接口列出角色。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ram&api=ListRoles&type=RPC&version=2015-05-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListRoles|系统规定参数。取值：ListRoles

 |
|Marker|String|否|EXAMPLE|当请求的返回结果被截断时，可以使用`Marker`获取从当前截断位置之后的内容。

 |
|MaxItems|Integer|否|100|指定返回结果的条数。当返回结果达到`MaxItems`限制被截断时，返回参数`IsTruncated`将等于`true`。

 取值范围：1 ~ 1000，默认值：100。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|IsTruncated|Boolean|true|请求返回结果是否被截断。

 |
|Marker|String|EXAMPLE|当`IsTruncated`为`true`时才有此字段。当返回`true`时，需要继续调用此接口，并且使用`Marker`获取截断后的内容。

 |
|RequestId|String|7B8A4E7D-6CFF-471D-84DF-195A7A241ECB|请求ID。

 |
|Roles| | |角色信息。

 |
|Arn|String|acs:ram::123456789012\*\*\*\*:role/ECSAdmin|角色的资源描述符。

 |
|CreateDate|String|2015-01-23T12:33:18Z|创建时间。

 |
|Description|String|ECS管理角色|角色的备注。

 |
|RoleId|String|901234567890\*\*\*\*|角色ID。

 |
|RoleName|String|ECSAdmin|角色名称。

 |
|UpdateDate|String|2015-01-23T12:33:18Z|更新时间。

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
                  <RoleId>901234567890****</RoleId>
                  <RoleName>ECSAdmin</RoleName>
                  <Arn>acs:ram::123456789012****:role/ECSAdmin</Arn>
                  <Description>ECS管理角色</Description>
                  <CreateDate>2015-01-23T12:33:18Z</CreateDate>
                  <UpdateDate>2015-01-23T12:33:18Z</UpdateDate>
            </Role>
            <Role>
                  <RoleId>901234567890****</RoleId>
                  <RoleName>OSSReadonlyAccess</RoleName>
                  <Arn>acs:ram::123456789012****:role/OSSReadonlyAccess</Arn>
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
				"Arn":"acs:ram::123456789012****:role/ECSAdmin",
				"CreateDate":"2015-01-23T12:33:18Z",
				"RoleId":"901234567890****"
			},
			{
				"RoleName":"OSSReadonlyAccess",
				"Description":"OSS只读访问角色",
				"UpdateDate":"2015-01-23T12:33:18Z",
				"Arn":"acs:ram::123456789012****:role/OSSReadonlyAccess",
				"CreateDate":"2015-01-23T12:33:18Z",
				"RoleId":"901234567890****"
			}
		]
	},
	"Marker":"EXAMPLE"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/Ram)查看更多错误码。

