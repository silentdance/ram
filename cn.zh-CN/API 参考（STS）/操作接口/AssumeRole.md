# AssumeRole {#reference_clc_3sv_xdb .reference}

调用AssumeRole接口获取一个扮演该角色的临时身份。

## 请求参数 {#section_it1_ksv_xdb .section}

|名称|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|AssumeRole|系统规定参数。取值：AssumeRole|
|RoleArn|String|是|acs:ram::123456789012\*\*\*\*:role/adminrole|指定角色的ARN。格式：`acs:ram::$accountID:role/$roleName` 。 **说明：** 

-   `$accountID`：云账号ID。您可以通过登录阿里云控制台，将鼠标悬停在右上角头像的位置，单击**安全设置**进行查看。
-   `$roleName`：RAM角色名称。您可以通过登录RAM控制台，单击左侧导航栏的**RAM角色管理**，在**RAM角色名称**列表下进行查看。

 |
|RoleSessionName|String|是|alice|用户自定义参数。此参数用来区分不同的令牌，可用于用户级别的访问审计。格式：`^[a-zA-Z0-9\.@\-_]+$`。 **说明：** 支持输入2~32个字符，请输入至少2个字符，如果只有1个字符，会出现错误。

 |
|Policy|String|否|\{"Statement": \[\{"Action": \["\*"\],"Effect": "Allow","Resource": \["\*"\]\}\],"Version":"1"\}|长度限制为1024字节。此参数可以限制生成的STS token的权限，若不指定则返回的token拥有指定角色的所有权限。|
|DurationSeconds|Long|否|3600|指定的过期时间，单位为秒。过期时间范围：900~3600秒，默认值为3600秒。|

## 返回数据 {#section_tqj_lsv_xdb .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|RequestId|String|6894B13B-6D71-4EF5-88FA-F32781734A7F|请求ID。|
|Credentials| | |访问凭证。|
|└AccessKeyId|String|STS.L4aBSCSJVMuKg5U1\*\*\*\*|访问密钥标识。|
|└AccessKeySecret|String|wyLTSmsyPGP1ohvvw8xYgB29dlGI8KMiH2pK\*\*\*\*|访问密钥。|
|└SecurityToken|String|\*\*\*\*\*\*\*\*|安全令牌。|
|└Expiration|String|2015-04-09T11:52:19Z|失效时间。|
|AssumedRoleUser| | |角色扮演临时身份。|
|└Arn|String|acs:sts::123456789012\*\*\*\*:assumed-role/AdminRole/alice|指定角色的ARN。格式：`acs:ram::$accountID:role/$roleName` 。 **说明：** 

-   `$accountID`：云账号ID。您可以通过登录阿里云控制台，将鼠标悬停在右上角头像的位置，单击**安全设置**进行查看。
-   `$roleName`：RAM角色名称。您可以通过登录RAM控制台，单击左侧导航栏的**RAM角色管理**，在**RAM角色名称**列表下进行查看。

 |
|└AssumedRoleUserId|String|34458433936495\*\*\*\*:alice|该角色临时身份的用户ID。|

## 示例 {#section_tdy_lsv_xdb .section}

请求示例

``` {#codeblock_br3_y78_b45}
https://sts.aliyuncs.com?Action=AssumeRole
&RoleArn=acs:ram::123456789012****:role/adminrole
&RoleSessionName=alice
&DurationSeconds=3600
&Policy=<url_encoded_policy>
&<公共请求参数>
```

返回示例

`XML`格式

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

`JSON`格式

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

## 错误码 {#section_dij_6fr_eae .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidParameter|The parameter RoleArn is wrongly formed.|角色ARN格式错误。|
|400|InvalidParameter.RoleArn|The parameter RoleArn is wrongly formed.|角色ARN格式错误。|
|400|InvalidParameter.RoleSessionName|The parameter RoleSessionName is wrongly formed.|RoleSessionName格式错误，支持输入2~32个字符，请输入至少2个字符；允许输入`^[a-zA-Z0-9\.@\-_]+$`。|
|400|InvalidParameter.DurationSeconds|The Min/Max value of DurationSeconds is 15min/1hr.|DurationSeconds参数设置错误，取值范围：900~3600秒。|
|400|InvalidParameter.PolicyGrammar|The parameter Policy has not passed grammar check.|权限策略语法错误。|
|400|InvalidParameter.PolicySize|The size of Policy must be smaller than 1024 bytes.|权限策略长度超限，最大不超过1024字节。|
|403|NoPermission|You are not authorized to do this action. You should be authorized by RAM.|STS token没有权限。|
|500|InternalError|STS Server Internal Error happened.|服务器内部错误。|

