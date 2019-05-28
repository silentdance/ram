# UpdateRole {#doc_api_977718 .reference}

Updates information about a RAM role.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Ram&api=CreateUser) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|UpdateRole| The name of this action.

 Value: UpdateRole

 |
|RoleName|String|Yes|ECSAdmin| The RAM role name. It must be 1 to 64 characters in length.

 Pattern: `^[a-zA-Z0-9\.@\-]+$`

 |
|NewAssumeRolePolicyDocument|String|No|\{ "Statement": \[ \{ "Action": "sts:AssumeRole", "Effect": "Allow", "Principal": \{ "RAM": "acs:ram::123456789012\*\*\*\*:root" \} \} \], "Version": "1" \}|The policy text that specifies one or more entities entrusted to assume the RAM role.|

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|The request ID.|
|Role|N/A|N/A|The information about the RAM role.|
|└Arn|String|acs:ram::123456789012\*\*\*\*:role/ECSAdmin|The Alibaba Cloud Resource Name \(ARN\) of the RAM role.|
|└AssumeRolePolicyDocument|String|\{ "Statement": \[ \{ "Action": "sts:AssumeRole", "Effect": "Allow", "Principal": \{ "RAM": "acs:ram::123456789012\*\*\*\*:root" \} \} \], "Version": "1" \}|The policy that specifies the entity entrusted to assume the RAM role.|
|└CreateDate|String|2015-01-23T12:33:18Z|The date and time when the RAM role was created.|
|└Description|String|ECS administrator|The description of the RAM role.|
|└RoleId|String|901234567890\*\*\*\*|The ID of the RAM role.|
|└RoleName|String|ECSAdmin|The name of the RAM role.|
|└UpdateDate|String|2015-01-23T12:33:18Z|The date and time when the RAM role was modified.|

## Example {#demo .section}

Request example

``` {#request_demo}
https://ram.aliyuncs.com/?Action=UpdateRole
&RoleName=ECSAdmin
&NewAssumeRolePolicyDocument={ "Statement": [ { "Action": "sts:AssumeRole", "Effect": "Allow", "Principal": { "RAM": "acs:ram::123456789012****:root" } } ], "Version": "1" }
&<Common parameters>
```

Response example

`XML` format

``` {#xml_return_success_demo}
<UpdateRoleResponse>
  <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
  <Role>
    <RoleId>901234567890****</RoleId>
    <RoleName>ECSAdmin</RoleName>
    <Arn>acs:ram::123456789012****:role/ECSAdmin</Arn>
    <Description>ECS administrator</Description>
    <AssumeRolePolicyDocument>{ "Statement": [ { "Action": "sts:AssumeRole", "Effect": "Allow", "Principal": { "RAM": "acs:ram::123456789012****:root" } } ], "Version": "1" }</AssumeRolePolicyDocument>
    <CreateDate>2015-01-23T12:33:18Z</CreateDate>
    <UpdateDate>2015-01-23T12:33:18Z</UpdateDate>
  </Role>
</UpdateRoleResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
    "RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368",
    "Role":{
        "RoleName":"ECSAdmin",
        "Description":"ECS administrator",
        "AssumeRolePolicyDocument":"{ \"Statement\": [ { \"Action\": \"sts:AssumeRole\", \"Effect\": \"Allow\", \"Principal\": { \"RAM\": \"acs:ram::123456789012****:root\" } } ], \"Version\": \"1\" }",
        "UpdateDate":"2015-01-23T12:33:18Z",
        "Arn":"acs:ram::123456789012****:role/ECSAdmin",
        "CreateDate":"2015-01-23T12:33:18Z",
        "RoleId":"901234567890****"
    }
}
```

## Errors { .section}

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ram?spm=5176.10421674.0.0.29c5cav7cav7Io).

