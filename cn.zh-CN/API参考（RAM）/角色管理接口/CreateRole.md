# CreateRole {#doc_api_Ram_CreateRole .reference}

调用CreateRole接口创建角色。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ram&api=CreateRole&type=RPC&version=2015-05-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateRole|系统规定参数。取值：CreateRole

 |
|RoleName|String|否|ECSAdmin|指定角色名，最多包含64个字符。

 格式：`^[a-zA-Z0-9\.@\-]+$`。

 |
|AssumeRolePolicyDocument|String|否|\{"Statement":\[\{"Action":"sts:AssumeRole","Effect":"Allow","Principal":\{"RAM":"acs:ram::123456789012\*\*\*\*:root"\}\}\],"Version":"1"\}|一个策略文本。指定受信任的允许扮演该角色的一个或多个主体，这个主体可以是阿里云账号、阿里云服务或身份提供商。

 **说明：** RAM用户不能扮演受信实体为阿里云服务的RAM角色。

 |
|Description|String|否|ECS管理角色|角色描述，最大长度为1024个字符。

 |

 **AssumeRolePolicyDocument样例说明** 

-   以下策略表示：允许扮演该角色的受信实体为云账号\(AccountID=123456789012\*\*\*\*\)下被授权的RAM用户。

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

-   以下策略表示：允许扮演该角色的受信实体为云账号\(AccountID=123456789012\*\*\*\*\)下被授权的RAM用户（testuser）。

**说明：** 创建此角色时，请确保已创建好RAM用户`testuser`\(其UPN为：testuser@123456789012\*\*\*\*.onaliyun.com\)。

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

-   以下策略表示：允许扮演该角色的受信实体为当前云账号下的ECS服务（用户创建ECS实例时可以指定使用该RAM角色，实例启动后将能获得该RAM角色的STS Token）。

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

-   以下策略表示：允许扮演该角色的受信实体为当前云账号\(AccountID=123456789012\*\*\*\*\)中的身份提供商（testprovider）下的用户。

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

访问[错误中心](https://error-center.aliyun.com/status/product/Ram)查看更多错误码。

