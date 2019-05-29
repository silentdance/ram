# CreateRole {#doc_api_Ram_CreateRole .reference}

创建角色。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=CreateRole)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|RoleName|String|是|ECSAdmin|指定角色名，最多包含64个字符。

 格式：`^[a-zA-Z0-9\.@\-]+$`。

 |
|AssumeRolePolicyDocument|String|是|\{"Statement":\[\{"Action":"sts:AssumeRole","Effect":"Allow","Principal":\{"RAM":"acs:ram::123456789012\*\*\*\*:root"\}\}\],"Version":"1"\}|一个策略文本，指定受信任的允许扮演该角色的一个或多个主体，这个主体可以是阿里云账号、阿里云服务或身份提供商。

 |
|Action|String|是|CreateRole|系统规定参数。取值：CreateRole。

 |
|Description|String|否|ECS管理角色|角色描述，最大长度1024字符。

 |

AssumeRolePolicyDocument样例说明：

-   如下策略表示允许扮演该角色的受信主体为云账号\(AccountID=123456789012\*\*\*\*\)下被授权的RAM用户：

```

{
"Statement": [
{
  "Action": "sts:AssumeRole",
  "Effect": "Allow",
  "Principal": {
    "RAM": [
      "acs:ram::123456789012****:root"
    ]
  }
}
],
"Version": "1"
}

```

-   如下策略表示允许扮演该角色的受信主体为云账号\(AccountID=123456789012\*\*\*\*\)下被授权的RAM用户\(testuser\)：

    ```
    
    {
    "Statement": [
    {
      "Action": "sts:AssumeRole",
      "Effect": "Allow",
      "Principal": {
        "RAM": [
          "acs:ram::123456789012****:user/testuser"
        ]
      }
    }
    ],
    "Version": "1"
    }
    
    ```

-   如下策略表示允许扮演该角色的受信主体为当前云账号下的ECS服务（用户创建ECS实例时可以指定使用该RAM角色，实例启动后将能获得该RAM角色的STS Token）：

```

{
"Statement": [
{
  "Action": "sts:AssumeRole",
  "Effect": "Allow",
  "Principal": {
    "Service": [
      "ecs.aliyuncs.com"
    ]
  }
}
],
"Version": "1"
}


```

-   如下策略表示允许扮演该角色的受信主体为当前云账号（AccountID=123456789012****）中的身份提供商（testprovider）下的用户：

```

{

    "Statement": [

        {
            "Action": "sts:AssumeRole",
            "Effect": "Allow",
            "Principal": {
                "Federated": [
                    "acs:ram::123456789012****:saml-provider/testprovider"
                ]
            },
            "Condition":{
                "StringEquals":{
                    "saml:recipient":"https://signin.aliyun.com/saml-role/sso"
                }
            }
        }
    ],
    "Version": "1"
}

```

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|请求ID。

 |
|Role| | |角色信息。

 |
|└Arn|String|acs:ram::123456789012\*\*\*\*:role/ECSAdmin|角色的资源描述符。

 |
|└AssumeRolePolicyDocument|String|\{ "Statement": \[ \{ "Action": "sts:AssumeRole", "Effect": "Allow", "Principal": \{ "RAM": "acs:ram::123456789012\*\*\*\*:root" \} \} \], "Version": "1" \}|扮演角色的信任策略。

 |
|└CreateDate|String|2015-01-23T12:33:18Z|创建时间。

 |
|└Description|String|ECS管理角色|角色的文字描述。

 |
|└RoleId|String|901234567890\*\*\*\*|角色ID。

 |
|└RoleName|String|ECSAdmin|角色名称。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=CreateRole
&RoleName=ECSAdmin
&AssumeRolePolicyDocument={"Statement":[{"Action":"sts:AssumeRole","Effect":"Allow","Principal":{"RAM":"acs:ram::123456789012****:root"}}],"Version":"1"}
&Description=ECS管理角色
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateRoleResponse>
  <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
  <Role>
    <RoleId>901234567890****</RoleId>
    <RoleName>ECSAdmin</RoleName>
    <Arn>acs:ram::123456789012****:role/ECSAdmin</Arn>
    <Description>ECS管理角色</Description>
    <AssumeRolePolicyDocument>{ "Statement": [ { "Action": "sts:AssumeRole", "Effect": "Allow", "Principal": { "RAM": "acs:ram::123456789012****:root" } } ], "Version": "1" }</AssumeRolePolicyDocument>
    <CreateDate>2015-01-23T12:33:18Z</CreateDate>
  </Role>
</CreateRoleResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368",
	"Role":{
		"RoleName":"ECSAdmin",
		"Description":"ECS管理角色",
		"AssumeRolePolicyDocument":"{ \"Statement\": [ { \"Action\": \"sts:AssumeRole\", \"Effect\": \"Allow\", \"Principal\": { \"RAM\": \"acs:ram::123456789012****:root\" } } ], \"Version\": \"1\" }",
		"Arn":"acs:ram::123456789012****:role/ECSAdmin",
		"CreateDate":"2015-01-23T12:33:18Z",
		"RoleId":"901234567890****"
	}
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ram)

