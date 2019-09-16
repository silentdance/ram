# CreateRole {#doc_api_Ram_CreateRole .reference}

You can call this operation to create a RAM role.

## Debugging {#api_explorer .section}

[OpenAPI Explorer](https://api.aliyun.com/#product=Ram&api=CreateRole&type=RPC&version=2015-05-01) automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.

## Request parameters {#parameters .section}

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateRole| The operation that you want to perform. Set this parameter to CreateRole.

 |
|RoleName|String|Yes|ECSAdmin| The name of the RAM role. The specified name can be up to 64 characters in length.

 Format: `^[a-zA-Z0-9\. @\-]+$`.

 |
|AssumeRolePolicyDocument|String|Yes|\{"Statement":\[\{"Action":"sts:AssumeRole","Effect":"Allow","Principal":\{"RAM":"acs:ram::123456789012\*\*\*\*:root"\}\}\],"Version":"1"\}| The policy text that specifies one or more entities entrusted to assume the RAM role. The trusted entity can be an Alibaba Cloud account, Alibaba Cloud service, or identity provider \(IdP\).

 **Note:** RAM users cannot assume the RAM roles of the trusted Alibaba Cloud service.

 |
|Description|String|No|The RAM role is used to manage ECS instances.| The description of the RAM role. The description can be up to 1,024 characters in length.

 |

Example value of the AssumeRolePolicyDocument parameter

-   The following policy allows the RAM role to be assumed by RAM users under the trusted Alibaba Cloud account whose ID is 123456789012\*\*\*\*.

    ``` {#codeblock_7a5_bww_3z8}
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

-   The following policy allows the RAM role to be assumed by the RAM user named testuser under the trusted Alibaba Cloud account whose ID is 123456789012\*\*\*\*.

    **Note:** To create the RAM role, you must ensure that you have created the RAM user testuser whose UPN is testuser@123456789012\*\*\*\*.onaliyun.com.

    ``` {#codeblock_nyz_hg6_75j}
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

-   The following policy allows the RAM role to be assumed by the ECS service under the current Alibaba Cloud account.

    ``` {#codeblock_e1t_34j_p65}
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

-   The following policy allows the RAM role to be assumed by users under the IdP named testprovider for the current Alibaba Cloud account whose ID is 123456789012\*\*\*\*.

    ``` {#codeblock_abw_5g1_go4}
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

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368| The ID of the request.

 |
|Role|N/A|N/A| The information about the RAM role.

 |
|Arn|String|acs:ram::123456789012\*\*\*\*:role/ECSAdmin| The Alibaba Cloud Resource Name \(ARN\) of the RAM role.

 |
|AssumeRolePolicyDocument|String|\{ "Statement": \[ \{ "Action": "sts:AssumeRole", "Effect": "Allow", "Principal": \{ "RAM": "acs:ram::123456789012\*\*\*\*:root" \} \} \], "Version": "1" \}| The policy that specifies the trusted entity to assume the RAM role.

 |
|CreateDate|String|2015-01-23T12:33:18Z| The time when the RAM role was created.

 |
|Description|String|The RAM role is used to manage ECS instances.| The description of the RAM role.

 |
|RoleId|String|901234567890\*\*\*\*| The ID of the RAM role.

 |
|RoleName|String|ECSAdmin| The name of the RAM role.

 |

## Examples {#demo .section}

Sample requests

``` {#request_demo}
https://ram.aliyuncs.com/?Action=CreateRole
&RoleName=ECSAdmin
&AssumeRolePolicyDocument={"Statement":[{"Action":"sts:AssumeRole","Effect":"Allow","Principal":{"RAM":"acs:ram::123456789012****:root"}}],"Version":"1"}
&Description=The RAM role is used to manage ECS instances.
&<Common request parameters>
```

Sample success responses

`XML` format

``` {#xml_return_success_demo}
<CreateRoleResponse>
      <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
      <Role>
            <RoleId>901234567890****</RoleId>
            <RoleName>ECSAdmin</RoleName>
            <Arn>acs:ram::123456789012****:role/ECSAdmin</Arn>
            <Description>The RAM role is used to manage ECS instances.</Description>
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
        "Description":"The RAM role is used to manage ECS instances.",
        "AssumeRolePolicyDocument":"{ \"Statement\": [ { \"Action\": \"sts:AssumeRole\", \"Effect\": \"Allow\", \"Principal\": { \"RAM\": \"acs:ram::123456789012****:root\" } } ], \"Version\": \"1\" }",
        "Arn":"acs:ram::123456789012****:role/ECSAdmin",
        "CreateDate":"2015-01-23T12:33:18Z",
        "RoleId":"901234567890****"
    }
}
```

## Error codes {#section_5z7_3so_m53 .section}

