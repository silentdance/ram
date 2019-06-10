# AssumeRole {#reference_clc_3sv_xdb .reference}

Obtains a temporary identity for assuming a role.

## Request parameters {#section_it1_ksv_xdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|:------------|:----------|
|Action|String|Yes|AssumeRole| The name of this action.

 Value: AssumeRole

 |
|RoleArn|String|Yes|acs:ram::123456789012\*\*\*\*:role/adminrole| The Alibaba Cloud Resource Name \(ARN\) of a RAM role.

 Pattern: `acs:ram::$accountID:role/$roleName`

 |
|RoleSessionName|String|Yes|alice| The role session name. This parameter can be customized to identify the user who assumes a role.

 Pattern: `^[a-zA-Z0-9\.@\-_]+$`

 **Note:** This parameter must be 2 to 32 characters in length.

 |
|Policy|String|No|\{"Statement": \[\{"Action": \["\*"\],"Effect": "Allow","Resource": \["\*"\]\}\],"Version":"1"\}| The policy. It must be 1 to 1024 bytes in length.

 This parameter can be used to specify the permission of an STS token. If this parameter is left unspecified, the returned STS token has all permissions of a specific role.

 |
|DurationSeconds|Integer|No|3,600| The expiration duration.

 Unit: second

 Value range: 900 to 3,600

 Default value: 3,600

 |

## Response parameters {#section_tqj_lsv_xdb .section}

|Parameter|Type|Example value|Description|
|:--------|:---|:------------|:----------|
|RequestId|String|6894B13B-6D71-4EF5-88FA-F32781734A7F|The request ID.|
|Credentials|N/A|N/A|The access credential.|
|└AccessKeyId|String|STS.L4aBSCSJVMuKg5U1\*\*\*\*|The access key ID.|
|└AccessKeySecret|String|wyLTSmsyPGP1ohvvw8xYgB29dlGI8KMiH2pK\*\*\*\*|The access key secret.|
|└SecurityToken|String|\*\*\*\*\*\*\*\*|The security token.|
|└Expiration|String|2015-04-09T11:52:19Z|The date and time when the identity expires.|
|AssumedRoleUser|N/A|N/A|The temporary identity for assuming a role.|
|└Arn|String|acs:sts::123456789012\*\*\*\*:assumed-role/AdminRole/alice| The ARN of a specific role.

 Pattern: `acs:ram::$accountID:role/$roleName`

 |
|└AssumedRoleUserId|String|34458433936495\*\*\*\*:alice|The ID of the temporary identity for assuming a role.|

## Example {#section_tdy_lsv_xdb .section}

Request example

``` {#codeblock_br3_y78_b45}
https://sts.aliyuncs.com?Action=AssumeRole
&RoleArn=acs:ram::123456789012****:role/adminrole
&RoleSessionName=alice
&DurationSeconds=3600
&Policy=<url_encoded_policy>
&<Common parameters>
```

Response example

`XML` format

``` {#codeblock_tu8_teg_g3b}
<AssumeRoleResponse>
    <RequestId>6894B13B-6D71-4EF5-88FA-F32781734A7F</RequestId>
    <AssumedRoleUser>
        <arn>acs:sts::123456789012****:assumed-role/AdminRole/alice</arn>
        <AssumedRoleUserId>34458433936495****:alice<AssumedRoleUserId>
    </AssumedRoleUser>
    <Credentials>
        <AccessKeyId>STS.L4aBSCSJVMuKg5U1****</AccessKeyId>
        <AccessKeySecret>wyLTSmsyPGP1ohvvw8xYgB29dlGI8KMiH2pK****</AccessKeySecret>
        <SecurityToken>********</SecurityToken>
        <Expiration>2015-04-09T11:52:19Z</Expiration>
    </Credentials>
</AssumeRoleResponse>
```

`JSON` format

``` {#codeblock_zru_lnb_ld8}
{
    "Credentials": {
        "AccessKeyId": "STS.L4aBSCSJVMuKg5U1****",
        "AccessKeySecret": "wyLTSmsyPGP1ohvvw8xYgB29dlGI8KMiH2pK****",
        "Expiration": "2015-04-09T11:52:19Z",
        "SecurityToken": "********"
    },
    "AssumedRoleUser": {
        "arn": "acs:sts::123456789012****:assumed-role/AdminRole/alice",
        "AssumedRoleUserId":"34458433936495****:alice"
        },
    "RequestId": "6894B13B-6D71-4EF5-88FA-F32781734A7F"
}
```

## Errors {#section_dij_6fr_eae .section}

|Error code|Error message|HTTP status code|Meaning|
|----------|-------------|----------------|-------|
|InvalidParameter|The parameter RoleArn is wrongly formed.|400|The ARN format of the role is incorrect.|
|InvalidParameter.RoleArn|The parameter RoleArn is wrongly formed.|400|The ARN format of the role is incorrect.|
|InvalidParameter.RoleSessionName|The parameter RoleSessionName is wrongly formed.|400| The value of the RoleSessionName parameter is incorrect. This parameter must be 2 to 32 characters in length.

 The allowed pattern is `^[a-zA-Z0-9\.@\-_]+$`.

 |
|InvalidParameter.DurationSeconds|The Min/Max value of DurationSeconds is 15min/1hr.|400|The value of the DurationSeconds parameter is incorrect. The value ranges from 900 to 3,600, in seconds.|
|InvalidParameter.PolicyGrammar|The parameter Policy has not passed grammar check.|400|The policy grammar is incorrect.|
|InvalidParameter.PolicySize|The size of Policy must be smaller than 1024 bytes.|400|The policy cannot exceed 1024 bytes.|
|NoPermission|You are not authorized to do this action. You should be authorized by RAM.|403|The STS token does not have the required permission.|
|InternalError|STS Server Internal Error happened.|500|An internal server error occurs.|

