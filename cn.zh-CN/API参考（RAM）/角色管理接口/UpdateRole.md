# UpdateRole {#doc_api_Ram_UpdateRole .reference}

调用UpdateRole接口更新角色信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ram&api=UpdateRole&type=RPC&version=2015-05-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateRole|系统规定参数。取值：UpdateRole

 |
|NewAssumeRolePolicyDocument|String|否|\{ "Statement": \[ \{ "Action": "sts:AssumeRole", "Effect": "Allow", "Principal": \{ "RAM": "acs:ram::123456789012345678:root" \} \} \], "Version": "1" \}|指定可以扮演此角色的身份。

 |
|RoleName|String|否|ECSAdmin|指定角色名，最多包含64个字符。

 格式：`^[a-zA-Z0-9\.@\-]+$`。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|请求ID。

 |
|Role| | |角色信息。

 |
|Arn|String|acs:ram::123456789012\*\*\*\*:role/ECSAdmin|角色的资源描述符。

 |
|AssumeRolePolicyDocument|String|\{ "Statement": \[ \{ "Action": "sts:AssumeRole", "Effect": "Allow", "Principal": \{ "RAM": "acs:ram::123456789012\*\*\*\*:root" \} \} \], "Version": "1" \}|扮演角色的权限策略。

 |
|CreateDate|String|2015-01-23T12:33:18Z|创建时间。

 |
|Description|String|ECS管理角色|角色的文字描述。

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

https://ram.aliyuncs.com/?Action=UpdateRole
&RoleName=ECSAdmin
&NewAssumeRolePolicyDocument={ "Statement": [ { "Action": "sts:AssumeRole", "Effect": "Allow", "Principal": { "RAM": "acs:ram::123456789012****:root" } } ], "Version": "1" }
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<UpdateRoleResponse>
      <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
      <Role>
            <RoleId>901234567890****</RoleId>
            <RoleName>ECSAdmin</RoleName>
            <Arn>acs:ram::123456789012****:role/ECSAdmin</Arn>
            <Description>ECS管理角色</Description>
            <AssumeRolePolicyDocument>{ "Statement": [ { "Action": "sts:AssumeRole", "Effect": "Allow", "Principal": { "RAM": "acs:ram::123456789012****:root" } } ], "Version": "1" }</AssumeRolePolicyDocument>
            <CreateDate>2015-01-23T12:33:18Z</CreateDate>
            <UpdateDate>2015-01-23T12:33:18Z</UpdateDate>
      </Role>
</UpdateRoleResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368",
	"Role":{
		"RoleName":"ECSAdmin",
		"Description":"ECS管理角色",
		"AssumeRolePolicyDocument":"{ \"Statement\": [ { \"Action\": \"sts:AssumeRole\", \"Effect\": \"Allow\", \"Principal\": { \"RAM\": \"acs:ram::123456789012****:root\" } } ], \"Version\": \"1\" }",
		"UpdateDate":"2015-01-23T12:33:18Z",
		"Arn":"acs:ram::123456789012****:role/ECSAdmin",
		"CreateDate":"2015-01-23T12:33:18Z",
		"RoleId":"901234567890****"
	}
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/Ram)查看更多错误码。

