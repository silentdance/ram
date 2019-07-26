# AssumeRoleWithSAML {#reference_qrl_qcb_1hb .reference}

进行角色SSO时，通过调用AssumeRoleWithSAML接口，可以获取一个扮演该角色的临时身份。

## 请求参数 {#section_it1_ksv_xdb .section}

|名称|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|AssumeRoleWithSAML|系统规定参数，取值：AssumeRoleWithSAML|
|SAMLProviderArn|String|是|acs:ram::123456789012\*\*\*\*:saml-provider/company1|RAM中创建的身份提供商的ARN。格式：`acs:ram::$account_ID:saml-provider/$saml_provider_ID`。|
|RoleArn|String|是|acs:ram::123456789012\*\*\*\*:role/adminrole|要扮演的角色的ARN。格式：`acs:ram::$accountID:role/$roleName`。|
|SAMLAssertion|String|是|<base64\_encoded\_saml\_assertion\>|Base64编码后的SAML断言。长度限制：4~100000字节。|
|Policy|String|否|<url\_encoded\_policy\>|长度限制为1024字节。此参数可以限制生成STS token的权限，若不指定则返回的token拥有指定角色的所有权限。|
|DurationSeconds|Long|否|3600|指定的过期时间，单位为秒。过期时间范围：900~3600秒，默认值为：3600秒。|

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
|└Arn|String|acs:sts::123456789012\*\*\*\*:assumed-role/AdminRole/alice|扮演的临时身份的ARN。格式：`acs:ram::$accountID:assumed-role/$roleName/$roleSessionName`。|
|└AssumedRoleUserId|String|34458433936495\*\*\*\*:alice|该角色临时身份的用户ID。|
|SAMLAssertionInfo| | |SAML断言中的部分信息。|
|└SubjectType|String|persistent|SAML断言中`NameID`的格式。当前缀为`urn:oasis:names:tc:SAML:2.0:nameid-format:`时，前缀会被移除。例如：`persistant/transient`。|
|└Subject|String|alice@example.com|SAML断言中`Subject - NameID`字段的值。|
|└Recipient|String|https://signin.aliyun.com/saml-role/SSO|SAML断言中`Subject - SubjectConfirmation - SubjectConfirmationData`字段中`Recipient`属性的值。|
|└Issuer|String|http://example.com/adfs/services/trust|SAML断言中`Issuer`字段的值。|

## 示例 {#section_tdy_lsv_xdb .section}

**说明：** 由于SAMLAssertion参数较长，可能会导致GET请求失败，请您使用POST方法发送此请求。

返回示例

`XML`格式

``` {#codeblock_yzq_nfq_xji .lanuage-xml}
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
    <SAMLAssertionInfo>
        <SubjectType>persistent</SubjectType>
        <Subject>alice@example.com</Subject>
        <Recipient>https://signin.aliyun.com/saml-role/SSO</Recipient>
        <Issuer>http://example.com/adfs/services/trust</Issuer>
    </SAMLAssertionInfo>
</AssumeRoleResponse>         
```

`JSON`格式

``` {#codeblock_uv1_wz5_v7j .language-json}
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
|400|MissingParameter.SAMLAssertion|Parameter SAMLAssertion is required.|缺少SAMLAssertion参数。|
|400|MissingParameter.SAMLProviderArn|Parameter SAMLProviderArn is required.|缺少SAMLProviderArn参数。|
|400|MissingParameter.RoleArn|Parameter RoleArn is required.|缺少RoleArn参数。|
|400|InvalidParameter.PolicyGrammar|Invalid Policy.|无效的权限策略。|
|400|InvalidParameter.PolicySize|The max size of policy string is 1024.|权限策略字符串长度超限，最大不超过1024字节。|
|400|InvalidParameter.RoleSessionName|The RoleSessionName is invalid.|角色会话名称无效。|
|400|InvalidParameter.DurationSeconds|The DurationSeconds is invalid.|DurationSeconds无效。|
|404|EntityNotExist.SAMLProvider|Can not find SAML provider.|找不到SAML身份提供商。|
|404|EntityNotExist.RoleArn|The specified Role does not exists.|指定的角色不存在。|
|401|AuthenticationFail.IDPMetadata.Invalid|The IdP Metadata of your SAML Provider is invalid.|SAML身份提供商的IdP元数据无效。|
|401|AuthenticationFail.SAMLAssertion.Expired|The SAML Assertion is expired.|SAML断言已过期。|
|401|AuthenticationFail.SAMLAssertion.Invalid|The SAML Assertion is invalid.|SAML断言无效。|

