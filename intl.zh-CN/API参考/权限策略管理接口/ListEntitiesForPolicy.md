# ListEntitiesForPolicy {#doc_api_Ram_ListEntitiesForPolicy .reference}

列出引用权限策略的实体。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=ListEntitiesForPolicy)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListEntitiesForPolicy|系统规定参数。取值：ListEntitiesForPolicy

 |
|PolicyName|String|是|OSS-Administrator|权限策略名称。

 |
|PolicyType|String|是|Custom|指定权限的类型, 取值`System`或`Custom`。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Users| | |用户信息集合。

 |
|└AttachDate|String|2015-01-23T12:33:18Z|授权时间。

 |
|└DisplayName|String|张\*|显示名称。

 |
|└UserId|String|122748924538\*\*\*\*|用户唯一标识。

 |
|└UserName|String|zhangq\*\*\*\*|用户名称。

 |
|Groups| | |组信息集合。

 |
|└AttachDate|String|2015-02-18T17:22:08Z|授权时间。

 |
|└Comments|String|测试团队|备注信息。

 |
|└GroupName|String|QA-Team|组名称。

 |
|Roles| | |角色信息结合。

 |
|└Arn|String|acs:ram::123456789012\*\*\*\*:role/ECSAdmin|角色的资源描述符。

 |
|└AttachDate|String|2015-01-23T12:33:18Z|授权时间。

 |
|└Description|String|ECS管理角色|角色的文字描述。

 |
|└RoleId|String|122748924538\*\*\*\*|角色ID。

 |
|└RoleName|String|ECSAdmin|角色名称。

 |
|RequestId|String|7B8A4E7D-6CFF-471D-84DF-195A7A241ECB|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=ListEntitiesForPolicy
&PolicyName=OSS-Administrator
&PolicyType=Custom
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ListEntitiesForPolicyResponse>
  <RequestId>7B8A4E7D-6CFF-471D-84DF-195A7A241ECB</RequestId>
  <Groups>
    <Group>
      <GroupName>QA-Team</GroupName>
      <Comments>测试团队</Comments>
      <AttachDate>2015-01-23T12:33:18Z</AttachDate>
    </Group>
    <Group>
      <GroupName>Dev-Team</GroupName>
      <Comments>开发团队</Comments>
      <AttachDate>2015-02-18T17:22:08Z</AttachDate>
    </Group>
  </Groups>
  <Users>
    <User>
      <UserId>122748924538****</UserId>
      <UserName>zhangq****</UserName>
      <DisplayName>张*</DisplayName>
      <AttachDate>2015-01-23T12:33:18Z</AttachDate>
    </User>
    <User>
      <UserId>140649822472****</UserId>
      <UserName>li****</UserName>
      <DisplayName>李*</DisplayName>
      <AttachDate>2015-02-18T17:22:08Z</AttachDate>
    </User>
  </Users>
  <Roles>
    <Role>
      <RoleId>122748924538****</RoleId>
      <RoleName>ECSAdmin</RoleName>
      <Arn>acs:ram::123456789012****:role/ECSAdmin</Arn>
      <Description>ECS管理角色</Description>
      <AttachDate>2015-01-23T12:33:18Z</AttachDate>
    </Role>
    <Role>
      <RoleId>140649822472****</RoleId>
      <RoleName>OSSReadonlyAccess</RoleName>
      <Description>OSS只读访问角色</Description>
      <Arn>acs:ram::123456789012****:role/OSSReadonlyAccess</Arn>
      <AttachDate>2015-01-23T12:33:18Z</AttachDate>
    </Role>
  </Roles>
</ListEntitiesForPolicyResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Groups":{
		"Group":[
			{
				"Comments":"测试团队",
				"GroupName":"QA-Team",
				"AttachDate":"2015-01-23T12:33:18Z"
			},
			{
				"Comments":"开发团队",
				"GroupName":"Dev-Team",
				"AttachDate":"2015-02-18T17:22:08Z"
			}
		]
	},
	"Users":{
		"User":[
			{
				"UserName":"zhangq****",
				"UserId":"122748924538****",
				"DisplayName":"张*",
				"AttachDate":"2015-01-23T12:33:18Z"
			},
			{
				"UserName":"li****",
				"UserId":"140649822472****",
				"DisplayName":"李*",
				"AttachDate":"2015-02-18T17:22:08Z"
			}
		]
	},
	"RequestId":"7B8A4E7D-6CFF-471D-84DF-195A7A241ECB",
	"Roles":{
		"Role":[
			{
				"RoleName":"ECSAdmin",
				"Description":"ECS管理角色",
				"Arn":"acs:ram::123456789012****:role/ECSAdmin",
				"AttachDate":"2015-01-23T12:33:18Z",
				"RoleId":"122748924538****"
			},
			{
				"RoleName":"OSSReadonlyAccess",
				"Description":"OSS只读访问角色",
				"Arn":"acs:ram::123456789012****:role/OSSReadonlyAccess",
				"AttachDate":"2015-02-18T17:22:08Z",
				"RoleId":"140649822472****"
			}
		]
	}
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ram)

