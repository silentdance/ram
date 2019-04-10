# AssumeRole {#reference_clc_3sv_xdb .reference}

通过该接口，获取一个扮演该角色的临时身份。

## 请求参数 {#section_it1_ksv_xdb .section}

|名称|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|AssumeRole|系统规定参数。取值：AssumeRole|
|RoleArn|String|是|acs:ram::123456789012\*\*\*\*:role/adminrole|指定角色的 ARN。格式：`acs:ram::$accountID:role/$roleName` 。|
|RoleSessionName|String|是|alice|用户自定义参数。此参数用来区分不同的 token，可用于用户级别的访问审计。格式：`^[a-zA-Z0-9\.@\-_]+$`。**说明：** 支持输入 2 ~ 32 个字符，请输入至少 2 个字符，如果只有 1 个字符，会出现错误。

|
|Policy|String|否|\{"Statement": \[\{"Action": \["\*"\],"Effect": "Allow","Resource": \["\*"\]\}\],"Version":"1"\}|长度限制为 1024 字节。此参数可以限制生成的 STS token 的权限，若不指定则返回的 token 拥有指定角色的所有权限。|
|DurationSeconds|Integer|否|3600|指定的过期时间，单位为秒。过期时间范围：900 ~ 3600，默认值为 3600。|

## 返回参数 {#section_tqj_lsv_xdb .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|RequestId|String|6894B13B-6D71-4EF5-88FA-F32781734A7F|请求ID。|
|Credentials| | |访问凭证。|
|└AccessKeyId|String|STS.L4aBSCSJVMuKg5U1\*\*\*\*|访问密钥标识。|
|└AccessKeySecret|String|wyLTSmsyPGP1ohvvw8xYgB29dlGI8KMiH2pK\*\*\*\*|访问密钥。|
|└SecurityToken|String|\*\*\*\*\*\*\*\*|安全令牌。|
|└Expiration|String|2015-04-09T11:52:19Z|失效时间。|
|AssumedRoleUser| | |角色扮演临时身份。|
|└Arn|String|acs:sts::123456789012\*\*\*\*:assumed-role/AdminRole/alice|指定角色的 ARN。格式：`acs:ram::$accountID:role/$roleName` 。|
|└AssumedRoleUserId|String|34458433936495\*\*\*\*:alice|该角色临时身份的用户 ID。|

## 操作示例 {#section_tdy_lsv_xdb .section}

请求示例

```
https://sts.aliyuncs.com?Action=AssumeRole
&RoleArn=acs:ram::123456789012****:role/adminrole
&RoleSessionName=alice
&DurationSeconds=3600
&Policy=<url_encoded_policy>
&<公共请求参数>
```

返回示例

`XML`格式

```
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

`JSON`格式

```
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

