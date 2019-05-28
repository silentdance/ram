# CreateRole {#doc_api_Ram_CreateRole .reference}

Creates a RAM role.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Ram&api=CreateRole) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|:------------|:----------|
|Action|String|Yes|CreateRole| The name of this action.

 Value: CreateRole

 |
|RoleName|String|Yes|ECSAdmin| The RAM role name. It must be 1 to 64 characters in length.

 Patter: `^[a-zA-Z0-9\.@\-]+$`

 |
|AssumeRolePolicyDocument|String|Yes|\{"Statement":\[\{"Action":"sts:AssumeRole","Effect":"Allow","Principal":\{"RAM":"acs:ram::123456789012\*\*\*\*:root"\}\}\],"Version":"1"\}|The policy text that specifies one or more entities entrusted to assume the RAM role. The entrusted entity can be an Alibaba Cloud account, an Alibaba Cloud service, or an identity provider \(IdP\).|
|Description|String|Yes|ECS administrator|The RAM role description. It must be 1 to 1,024 characters in length.|

## Example of AssumeRolePolicyDocument {#requestParamsSupplement .section}

-   The following policy allows the RAM role to be assumed by RAM users under the entrusted Alibaba Cloud account \(ID: 123456789012\*\*\*\*\):

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

-   The following policy allows the RAM role to be assumed by the RAM user \(testuser\) under the entrusted Alibaba Cloud account \(ID: 123456789012\*\*\*\*\):

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

-   The following policy allows the RAM role to be assumed by ECS under the current Alibaba Cloud account:

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

    **Note:** After the RAM role is assumed by ECS, you can specify to use this role when you create an instance. The STS token of role to be assumed is then obtained when you start the instance.

-   The following policy allows the RAM role to be assumed by users under the IdP \(testprovider\) in the current Alibaba Cloud account \(ID: 123456789012\*\*\*\*\):

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


## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|:--------|:---|:------------|:----------|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|The request ID.|
|Role|N/A|N/A|The information about the RAM role.|
|└Arn|String|acs:ram::123456789012\*\*\*\*:role/ECSAdmin|The Alibaba Cloud Resource Name \(ARN\) of the RAM role.|
|└AssumeRolePolicyDocument|String|\{ "Statement": \[ \{ "Action": "sts:AssumeRole", "Effect": "Allow", "Principal": \{ "RAM": "acs:ram::123456789012\*\*\*\*:root" \} \} \], "Version": "1" \}|The policy that specifies the entity entrusted to assume the RAM role.|
|└CreateDate|String|2015-01-23T12:33:18Z|The date and time when the RAM role was created.|
|└Description|String|ECS administrator|The description of the RAM role.|
|└RoleId|String|901234567890\*\*\*\*|The ID of the RAM role.|
|└RoleName|String|ECSAdmin|The name of the RAM role.|

## Examples {#demo .section}

Request example

``` {#request_demo}
https://ram.aliyuncs.com/?Action=CreateRole
&RoleName=ECSAdmin
&AssumeRolePolicyDocument={"Statement":[{"Action":"sts:AssumeRole","Effect":"Allow","Principal":{"RAM":"acs:ram::123456789012****:root"}}],"Version":"1"}
&Description=ECS administrator
&<Common parameters>
```

Response example

`XML` format

``` {#xml_return_success_demo}
<CreateRoleResponse>
  <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
  <Role>
    <RoleId>901234567890****</RoleId>
    <RoleName>ECSAdmin</RoleName>
    <Arn>acs:ram::123456789012****:role/ECSAdmin</Arn>
    <Description>ECS administrator</Description>
    <AssumeRolePolicyDocument>{ "Statement": [ { "Action": "sts:AssumeRole", "Effect": "Allow", "Principal": { "RAM": "acs:ram::123456789012****:root" } } ], "Version": "1" }</AssumeRolePolicyDocument>
    <CreateDate>2015-01-23T12:33:18Z</CreateDate>
  </Role>
</CreateRoleResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
    "RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368",
    "Role":{
        "RoleName":"ECSAdmin",
        "Description":"ECS administrator",
        "AssumeRolePolicyDocument":"{ \"Statement\": [ { \"Action\": \"sts:AssumeRole\", \"Effect\": \"Allow\", \"Principal\": { \"RAM\": \"acs:ram::123456789012****:root\" } } ], \"Version\": \"1\" }",
        "Arn":"acs:ram::123456789012****:role/ECSAdmin",
        "CreateDate":"2015-01-23T12:33:18Z",
        "RoleId":"901234567890****"
    }
}
```

## Errors { .section}

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ram?spm=5176.10421674.0.0.29c5cav7cav7Io).

