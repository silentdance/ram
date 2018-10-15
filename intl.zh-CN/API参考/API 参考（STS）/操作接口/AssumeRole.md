# AssumeRole {#reference_clc_3sv_xdb .reference}

## 接口描述 {#section_lgj_jsv_xdb .section}

通过该接口，获取一个扮演该角色的临时身份。

## 请求参数 {#section_it1_ksv_xdb .section}

**Action**

-   类型：String
-   必须：是
-   描述：系统规定参数，取值：AssumeRole

**RoleArn**

-   类型：String
-   必须：是
-   描述：指定角色的全局资源描述符\(Aliyun Resource Name，简称Arn\)。每个角色都有一个唯一的全局资源描述符，规定格式为 acs:ram::$accountID:role/$roleName ，一个样例：acs:ram::1234567890123456:role/samplerole 。您可以在RAM控制台的角色管理页面RAM控制台的角色管理列表中，进入角色详情页可以查看一个角色的RoleArn。

**RoleSessionName**

-   类型：String
-   必须：是
-   描述：用户自定义参数。此参数用来区分不同的Token，可用于用户级别的访问审计。
-   格式：

    ```
    ^[a-zA-Z0-9\.@\-_]+$
    ```

    **说明：** 支持输入 2-32 个字符，请输入至少 2 个字符，如果只有 1 个字符，会出现错误。


**Policy**

-   名称：Policy
-   类型：String
-   必须：否
-   描述：授权策略[Policy 语法结构](../../../../intl.zh-CN/用户指南/授权策略语言/Policy 语法结构.md)，Policy长度限制为1024字节；您可以通过此参数限制生成的Token的权限，不指定则返回的Token将拥有指定角色的所有权限。

**DurationSeconds**

-   名称：DurationSeconds
-   类型：Integer
-   必须：否
-   描述：指定的过期时间，单位为秒。过期时间范围：900 ~ 3600，默认值为3600。

## 返回参数 {#section_tqj_lsv_xdb .section}

**Credentials**

-   类型：[Credentials](intl.zh-CN/API参考/API 参考（STS）/数据类型/Credentials.md)
-   描述：访问凭证

**AssumedRoleUser**

-   描述：角色扮演临时身份

## 操作示例 {#section_tdy_lsv_xdb .section}

**HTTP Request**

```
https://sts.aliyuncs.com?Action=AssumeRole
&RoleArn=acs:ram::1234567890123456:role/adminrole
&RoleSessionName=alice
&DurationSeconds=3600
&Policy=<url_encoded_policy>
&<公共请求参数>
```

**HTTP Response**

-   **XML格式**

    ```
    <AssumeRoleResponse>
        <RequestId>6894B13B-6D71-4EF5-88FA-F32781734A7F</RequestId>
        <AssumedRoleUser>
            <arn>acs:sts::1234567890123456:assumed-role/AdminRole/alice</arn>
            <AssumedRoleUserId>344584339364951186:alice<AssumedRoleUserId>
        </AssumedRoleUser>
        <Credentials>
            <AccessKeyId>STS.L4aBSCSJVMuKg5U1vFDw</AccessKeyId>
            <AccessKeySecret>wyLTSmsyPGP1ohvvw8xYgB29dlGI8KMiH2pKCNZ9</AccessKeySecret>
            <SecurityToken>CAESrAIIARKAAShQquMnLIlbvEcIxO6wCoqJufs8sWwieUxu45hS9AvKNEte8KRUWiJWJ6Y+YHAPgNwi7yfRecMFydL2uPOgBI7LDio0RkbYLmJfIxHM2nGBPdml7kYEOXmJp2aDhbvvwVYIyt/8iES/R6N208wQh0Pk2bu+/9dvalp6wOHF4gkFGhhTVFMuTDRhQlNDU0pWTXVLZzVVMXZGRHciBTQzMjc0KgVhbGljZTCpnJjwySk6BlJzYU1ENUJuCgExGmkKBUFsbG93Eh8KDEFjdGlvbkVxdWFscxIGQWN0aW9uGgcKBW9zczoqEj8KDlJlc291cmNlRXF1YWxzEghSZXNvdXJjZRojCiFhY3M6b3NzOio6NDMyNzQ6c2FtcGxlYm94L2FsaWNlLyo=</SecurityToken>
            <Expiration>2015-04-09T11:52:19Z</Expiration>
        </Credentials>
    </AssumeRoleResponse>
    ```

-   **JSON格式**

    ```
    {
        "Credentials": {
            "AccessKeyId": "STS.L4aBSCSJVMuKg5U1vFDw",
            "AccessKeySecret": "wyLTSmsyPGP1ohvvw8xYgB29dlGI8KMiH2pKCNZ9",
            "Expiration": "2015-04-09T11:52:19Z",
            "SecurityToken": "CAESrAIIARKAAShQquMnLIlbvEcIxO6wCoqJufs8sWwieUxu45hS9AvKNEte8KRUWiJWJ6Y+YHAPgNwi7yfRecMFydL2uPOgBI7LDio0RkbYLmJfIxHM2nGBPdml7kYEOXmJp2aDhbvvwVYIyt/8iES/R6N208wQh0Pk2bu+/9dvalp6wOHF4gkFGhhTVFMuTDRhQlNDU0pWTXVLZzVVMXZGRHciBTQzMjc0KgVhbGljZTCpnJjwySk6BlJzYU1ENUJuCgExGmkKBUFsbG93Eh8KDEFjdGlvbkVxdWFscxIGQWN0aW9uGgcKBW9zczoqEj8KDlJlc291cmNlRXF1YWxzEghSZXNvdXJjZRojCiFhY3M6b3NzOio6NDMyNzQ6c2FtcGxlYm94L2FsaWNlLyo="
        },
        "AssumedRoleUser": {
            "arn": "acs:sts::1234567890123456:assumed-role/AdminRole/alice",
            "AssumedRoleUserId":"344584339364951186:alice"
            },
        "RequestId": "6894B13B-6D71-4EF5-88FA-F32781734A7F"
    }
    ```


