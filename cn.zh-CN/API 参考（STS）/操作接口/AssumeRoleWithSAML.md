# AssumeRoleWithSAML {#reference_qrl_qcb_1hb .reference}

调用 AssumeRoleWithSAML 接口，使用 SAML 断言获取一个扮演该角色的临时身份。

## 请求参数 {#section_it1_ksv_xdb .section}

|名称|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|AssumeRoleWithSAML|系统规定参数，取值：AssumeRoleWithSAML|
|SAMLProviderArn|String|是|acs:ram::123456789012\*\*\*\*:saml-provider/company1|RAM 中创建的身份提供商的 ARN。格式：`acs:ram::$account_ID:saml-provider/$saml_provider_ID`。|
|RoleArn|String|是|acs:ram::123456789012\*\*\*\*:role/adminrole|要扮演的角色的 ARN。格式：`acs:ram::$accountID:role/$roleName`。|
|SAMLAssertion|String|是|<base64\_encoded\_saml\_assertion\>|Base64 编码后的 SAML 断言。长度限制：4 ~ 100000字节。|
|Policy|String|否|<url\_encoded\_policy\>|长度限制为 1024 字节。此参数可以限制生成 STS Token 的权限，若不指定则返回的 Token 拥有指定角色的所有权限。|
|DurationSeconds|String|否|3600|指定的过期时间，单位为秒。过期时间范围：900 ~ 3600，默认值为：3600。|

## 返回参数 {#section_tqj_lsv_xdb .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|RequestId|String|6894B13B-6D71-4EF5-88FA-F32781734A7F|请求 ID。|
|Credentials| | |访问凭证。|
|└AccessKeyId|String|STS.L4aBSCSJVMuKg5U1\*\*\*\*|访问密钥标识。|
|└AccessKeySecret|String|wyLTSmsyPGP1ohvvw8xYgB29dlGI8KMiH2pK\*\*\*\*|访问密钥。|
|└SecurityToken|String|\*\*\*\*\*\*\*\*|安全令牌。|
|└Expiration|String|2015-04-09T11:52:19Z|失效时间。|
|AssumedRoleUser| | |角色扮演临时身份。|
|└Arn|String|acs:sts::123456789012\*\*\*\*:assumed-role/AdminRole/alice|扮演的临时身份的 ARN。格式：`acs:ram::$accountID:assumed-role/$roleName/$roleSessionName`。|
|└AssumedRoleUserId|String|34458433936495\*\*\*\*:alice|该角色临时身份的用户 ID。|
|SAMLAssertionInfo| | |SAML 断言中的部分信息。|
|└SubjectType|String|persistent|SAML 断言中`NameID`的格式。当前缀为`urn:oasis:names:tc:SAML:2.0:nameid-format:`时，前缀会被移除。例如：`persistant/transient`。|
|└Subject|String|alice@example.com|SAML 断言中`Subject - NameID`字段的值。|
|└Recipient|String|https://signin.aliyun.com/saml-role/SSO|SAML 断言中`Subject - SubjectConfirmation - SubjectConfirmationData`字段中`Recipient`属性的值。|
|└Issuer|String|http://example.com/adfs/services/trust|SAML 断言中`Issuer`字段的值。|

## 操作示例 {#section_tdy_lsv_xdb .section}

**说明：** 由于 SAMLAssertion 参数较长，可能会导致 GET 请求失败，请您使用 POST 方法发送此请求。

返回示例

`XML`格式

``` {#codeblock_yzq_nfq_xji}
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
    <SAMLAssertionInfo>
        <SubjectType>persistent</SubjectType>
        <Subject>alice@example.com</Subject>
        <Recipient>https://signin.aliyun.com/saml-role/SSO</Recipient>
        <Issuer>http://example.com/adfs/services/trust</Issuer>
    </SAMLAssertionInfo>
</AssumeRoleResponse>         
```

`JSON`格式

``` {#codeblock_uv1_wz5_v7j}
{
    "Credentials": {
        "AccessKeyId": "STS.L4aBSCSJVMuKg5U1****",
        "AccessKeySecret": "wyLTSmsyPGP1ohvvw8xYgB29dlGI8KMiH2pK****",
        "Expiration": "2015-04-09T11:52:19Z",
        "SecurityToken": "********"
    },
    "AssumedRoleUser": {
        "arn": "acs:sts::1234567890123456:assumed-role/AdminRole/alice",
        "AssumedRoleUserId":"34458433936495****:alice"
        },
    "SAMLAssertionInfo": {
        "SubjectType": "persistent",
        "Subject": "alice@example.com",
        "Recipient": "https://signin.aliyun.com/saml-role/SSO",
        "Issuer": "http://example.com/adfs/services/trust"
    },
    "RequestId": "6894B13B-6D71-4EF5-88FA-F32781734A7F"
}         
```

## 错误码 {#section_rf1_vrv_kn4 .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|MissingParameter.SAMLAssertion|Parameter SAMLAssertion is required.|缺少 SAMLAssertion 参数。|
|400|MissingParameter.SAMLProviderArn|Parameter SAMLProviderArn is required.|缺少 SAMLProviderArn 参数。|
|400|MissingParameter.RoleArn|Parameter RoleArn is required.|缺少 RoleArn 参数。|
|400|InvalidParameter.PolicyGrammar|Invalid Policy.|无效的权限策略。|
|400|InvalidParameter.PolicySize|The max size of policy string is 1024.|权限策略字符串长度超限，最大不超过 1024 字节。|
|400|InvalidParameter.RoleSessionName|The RoleSessionName is invalid.|角色会话名称无效。|
|400|InvalidParameter.DurationSeconds|The DurationSeconds is invalid.|DurationSeconds 无效。|
|404|EntityNotExist.SAMLProvider|Can not find SAML provider.|找不到 SAML 身份提供商。|
|404|EntityNotExist.RoleArn|The specified Role does not exists.|指定的角色不存在。|
|401|AuthenticationFail.IDPMetadata.Invalid|The IdP Metadata of your SAML Provider is invalid.|SAML 身份提供商的 IdP 元数据无效。|
|401|AuthenticationFail.SAMLAssertion.Expired|The SAML Assertion is expired.|SAML 断言已过期。|
|401|AuthenticationFail.SAMLAssertion.Invalid|The SAML Assertion is invalid.|SAML 断言无效。|

