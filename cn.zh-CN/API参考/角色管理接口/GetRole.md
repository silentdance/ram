# GetRole {#doc_api_977719 .reference}

获取角色信息。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=GetRole)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetRole|系统规定参数。取值：GetRole

 |
|RoleName|String|是|ECSAdmin|指定角色名，最多包含64个字符。

 格式：`^[a-zA-Z0-9\.@\-]+$`。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|请求ID。

 |
|Role| | |角色信息。

 |
|└Arn|String|acs:ram::1234567890123456:role/ECSAdmin|角色的资源描述符。

 |
|└AssumeRolePolicyDocument|String|\{ "Statement": \[ \{ "Action": "sts:AssumeRole", "Effect": "Allow", "Principal": \{ "RAM": "acs:ram::123456789012345678:root" \} \} \], "Version": "1" \}|角色扮演授权策略。

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

https://ram.aliyuncs.com/?Action=GetRole
&RoleName=ECSAdmin
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<GetRoleResponse>
  <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
  <Role>
    <RoleId>901234567890123</RoleId>
    <RoleName>ECSAdmin</RoleName>
    <Arn>acs:ram::1234567890123456:role/ECSAdmin</Arn>
    <Description>ECS管理角色</Description>
    <AssumeRolePolicyDocument>{ "Statement": [ { "Action": "sts:AssumeRole", "Effect": "Allow", "Principal": { "RAM": "acs:ram::123456789012345678:root" } } ], "Version": "1" }</AssumeRolePolicyDocument>
    <CreateDate>2015-01-23T12:33:18Z</CreateDate>
    <UpdateDate>2015-01-23T12:33:18Z</UpdateDate>
  </Role>
</GetRoleResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368",
	"Role":{
		"RoleName":"ECSAdmin",
		"Description":"ECS管理角色",
		"AssumeRolePolicyDocument":"{ \"Statement\": [ { \"Action\": \"sts:AssumeRole\", \"Effect\": \"Allow\", \"Principal\": { \"RAM\": \"acs:ram::123456789012345678:root\" } } ], \"Version\": \"1\" }",
		"UpdateDate":"2015-01-23T12:33:18Z",
		"Arn":"acs:ram::1234567890123456:role/ECSAdmin",
		"CreateDate":"2015-01-23T12:33:18Z",
		"RoleId":"901234567890123"
	}
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ram)

