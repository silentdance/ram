# AssumeRole {#reference_clc_3sv_xdb .reference}

You can call this operation to obtain a temporary identity for assuming a role. In this topic, RAM users can only assume the RAM roles of the trusted Alibaba Cloud account.

## Request parameters {#section_it1_ksv_xdb .section}

|Parameter|Type|Required|Example|Description|
|:--------|:---|:-------|:------|:----------|
|Action|String|Yes|AssumeRole|The operation that you want to perform. Set this parameter to AssumeRole.|
|RoleArn|String|Yes|acs:ram::123456789012\*\*\*\*:role/adminrole|The Alibaba Cloud Resource Name \(ARN\) of the specified RAM role. Format: `acs:ram::$accountID:role/$roleName`. **Note:** 

-   `$accountID`: specifies the Alibaba Cloud account ID. To view the account ID, log on to the Alibaba Cloud console, move your pointer over your profile picture in the upper-right corner, and then click **Security Settings**.
-   `$roleName`: specifies the name of the RAM role. To view the role name, log on to the RAM console, and click **RAM Roles** in the left-side navigation pane. In the **RAM Role Name** column, you can view the name of the target RAM role.

 |
|RoleSessionName|String|Yes|alice|The role session name that is specified by the user. This parameter can be used to identify the RAM user who assumes the role. Format: `^[a-zA-Z0-9\. @\-_]+$`. **Note:** The value must be 2 to 32 characters in length. If you enter only one character, an error occurs.

 |
|Policy|String|No|\{"Statement": \[\{"Action": \["\*"\],"Effect": "Allow","Resource": \["\*"\]\}\],"Version":"1"\}|The policy that specifies the permissions of the generated STS token. The value can be up to 1,024 bytes in length. If you do not specify this parameter, the STS token has all permissions of the specified RAM role.|
|DurationSeconds|Long|No|3600|The validity period of the STS token. Unit: seconds. Valid values: 900 to 3600. Default value: 3600.|

## Response parameters {#section_tqj_lsv_xdb .section}

|Parameter|Type|Example|Description|
|:--------|:---|:------|:----------|
|RequestId|String|6894B13B-6D71-4EF5-88FA-F32781734A7F|The ID of the request.|
|Credentials| | |The access credential.|
|└AccessKeyId|String|STS.L4aBSCSJVMuKg5U1\*\*\*\*|The AccessKey ID provided to you by Alibaba Cloud.|
|└AccessKeySecret|String|wyLTSmsyPGP1ohvvw8xYgB29dlGI8KMiH2pK\*\*\*\*|The AccessKey secret provided to you by Alibaba Cloud.|
|└SecurityToken|String|\*\*\*\*\*\*\*\*|The STS token.|
|└Expiration|String|2015-04-09T11:52:19Z|The time when the STS token expires.|
|AssumedRoleUser| | |The temporary identity that you use to assume the role.|
|└Arn|String|acs:sts::123456789012\*\*\*\*:assumed-role/AdminRole/alice|The ARN of the specified RAM role. Format: `acs:ram::$accountID:role/$roleName`. **Note:** 

-   `$accountID`: specifies the Alibaba Cloud account ID. To view the account ID, log on to the Alibaba Cloud console, move your pointer over your profile picture in the upper-right corner, and then click **Security Settings**.
-   `$roleName`: specifies the name of the RAM role. To view the role name, log on to the RAM console, and click **RAM Roles** in the left-side navigation pane. In the **RAM Role Name** column, you can view the name of the target RAM role.

 |
|└AssumedRoleUserId|String|34458433936495\*\*\*\*:alice|The ID of the temporary identity that you use to assume the role.|

## Examples {#section_tdy_lsv_xdb .section}

Sample requests

``` {#codeblock_br3_y78_b45}
https://sts.aliyuncs.com?Action=AssumeRole
&RoleArn=acs:ram::123456789012****:role/adminrole
&RoleSessionName=alice
&DurationSeconds=3600
&Policy=<url_encoded_policy>
&<Common request parameters>
```

Sample responses

`XML` format

``` {#codeblock_tu8_teg_g3b .lanuage-xml}
<AssumeRoleResponse>
    <RequestId>6894B13B-6D71-4EF5-88FA-F32781734A7F</RequestId>
    <AssumedRoleUser>
        <arn>acs:sts::123456789012****:assumed-role/AdminRole/alice</arn>
        <AssumedRoleUserId>34458433936495****:alice</AssumedRoleUserId>
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

``` {#codeblock_zru_lnb_ld8 .language-json}
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

## Error codes {#section_dij_6fr_eae .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|InvalidParameter|The parameter RoleArn is wrongly formed.|The error message returned because the ARN format of the RAM role is invalid.|
|400|InvalidParameter.RoleArn|The parameter RoleArn is wrongly formed.|The error message returned because the ARN format of the RAM role is invalid.|
|400|InvalidParameter.RoleSessionName|The parameter RoleSessionName is wrongly formed.|The error message returned because the format of the RoleSessionName parameter is invalid. The value must be 2 to 32 characters in length. Enter a value in the format of `^[a-zA-Z0-9\. @\-_]+$`, and try again.|
|400|InvalidParameter.DurationSeconds|The Min/Max value of DurationSeconds is 15min/1hr.|The error message returned because the value of the DurationSeconds parameter is invalid. The value range is from 900 to 3600.|
|400|InvalidParameter.PolicyGrammar|The parameter Policy has not passed grammar check.|The error message returned because the policy syntax is incorrect.|
|400|InvalidParameter.PolicySize|The size of Policy must be smaller than 1024 bytes.|The error message returned because the length of the specified policy string has reached the upper limit. The policy string can be up to 1,024 bytes in length.|
|403|NoPermission|You are not authorized to do this action. You should be authorized by RAM.|The error message returned because the STS token does not have the required permission.|
|500|InternalError|STS Server Internal Error happened.|The error message returned because an internal server error has occurred.|

