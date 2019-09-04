# AssumeRoleWithSAML {#reference_qrl_qcb_1hb .reference}

You can call this operation to obtain a temporary identity for assuming a role during the role-based single sign-on \(SSO\).

## Request parameters {#section_it1_ksv_xdb .section}

|Parameter|Type|Required|Example|Description|
|:--------|:---|:-------|:------|:----------|
|Action|String|Yes|AssumeRoleWithSAML|The operation that you want to perform. Set this parameter to AssumeRoleWithSAML.|
|SAMLProviderArn|String|Yes|acs:ram::123456789012\*\*\*\*:saml-provider/company1|The Alibaba Cloud Resource Name \(ARN\) of the identity provider \(IdP\) that is created in the RAM console. Format: `acs:ram::$account_ID:saml-provider/$saml_provider_ID`.|
|RoleArn|String|Yes|acs:ram::123456789012\*\*\*\*:role/adminrole|The ARN of the role to be assumed. Format: `acs:ram::$accountID:role/$roleName`.|
|SAMLAssertion|String|Yes|<base64\_encoded\_saml\_assertion\>|The SAML assertion that is encoded by using Base64 encoding. The value must be 4 to 100,000 bytes in length.|
|Policy|String|No|<url\_encoded\_policy\>|The policy that specifies the permissions of the generated STS token. The value can be up to 1,024 bytes in length. If you do not specify this parameter, the STS token has all permissions of the specified RAM role.|
|DurationSeconds|Long|No|3600|The validity period of the STS token. Unit: seconds. Valid values: 900 to 3600. Default value: 3600.|

## Response parameters {#section_tqj_lsv_xdb .section}

|Parameter|Type|Example|Description|
|:--------|:---|:------|:----------|
|RequestId|String|6894B13B-6D71-4EF5-88FA-F32781734A7F|The ID of the request.|
|Credentials| | |The access credential.|
|└AccessKeyId|String|STS.L4aBSCSJVMuKg5U1\*\*\*\*|The AccessKey ID.|
|└AccessKeySecret|String|wyLTSmsyPGP1ohvvw8xYgB29dlGI8KMiH2pK\*\*\*\*|The AccessKey Secret.|
|└SecurityToken|String|\*\*\*\*\*\*\*\*|The STS token.|
|└Expiration|String|2015-04-09T11:52:19Z|The time when the STS token expires.|
|AssumedRoleUser| | |The temporary identity that you use to assume the role.|
|└Arn|String|acs:sts::123456789012\*\*\*\*:assumed-role/AdminRole/alice|The ARN of the temporary identity that you use to assume the role. Format: `acs:ram::$accountID:assumed-role/$roleName/$roleSessionName`.|
|└AssumedRoleUserId|String|34458433936495\*\*\*\*:alice|The ID of the temporary identity to assume the role.|
|SAMLAssertionInfo| | |The information in the SAML assertion.|
|└SubjectType|String|persistent|The format of the `NameID` value in the SAML assertion. If a name ID contains the `urn:oasis:names:tc:SAML:2.0:nameid-format:` prefix, the prefix is removed from the ID. For example, if the ID is urn:oasis:names:tc:SAML:2.0:nameid-format:persistant/transient, only `persistant/transient` is displayed.|
|└Subject|String|alice@example.com|The value of the `Subject - NameID` field in the SAML assertion.|
|└Recipient|String|https://signin.aliyun.com/saml-role/SSO|The `Recipient` attribute of the `Subject - SubjectConfirmation - SubjectConfirmationData` field in the SAML assertion.|
|└Issuer|String|http://example.com/adfs/services/trust|The value of the `Issuer` field in the SAML assertion.|

## Examples {#section_tdy_lsv_xdb .section}

**Note:** If the SAMLAssertion parameter has a large amount of body text and you use the GET method to send the API request, an error may occur. Therefore, we recommend that you use the POST method to send the API request.

Sample responses

`XML` format

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

`JSON` format

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

## Error codes {#section_rf1_vrv_kn4 .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|MissingParameter.SAMLAssertion|Parameter SAMLAssertion is required.|The error message returned because the SAMLAssertion parameter is not specified.|
|400|MissingParameter.SAMLProviderArn|Parameter SAMLProviderArn is required.|The error message returned because the SAMLProviderArn parameter is not specified.|
|400|MissingParameter.RoleArn|Parameter RoleArn is required.|The error message returned because the RoleArn parameter is not specified.|
|400|InvalidParameter.PolicyGrammar|Invalid Policy.|The error message returned because the specified permission policy is invalid.|
|400|InvalidParameter.PolicySize|The max size of policy string is 1024.|The error message returned because the length of the specified policy string has reached the upper limit. The policy string can be up to 1,024 bytes in length.|
|400|InvalidParameter.RoleSessionName|The RoleSessionName is invalid.|The error message returned because the specified role session name is invalid.|
|400|InvalidParameter.DurationSeconds|The DurationSeconds is invalid.|The error message returned because the specified value for the DurationSeconds parameter is invalid.|
|404|EntityNotExist.SAMLProvider|Can not find SAML provider.|The error message returned because the specified SAML IdP does not exist.|
|404|EntityNotExist.RoleArn|The specified Role does not exists.|The error message returned because the specified RAM role name does not exist.|
|401|AuthenticationFail.IDPMetadata.Invalid|The IdP Metadata of your SAML Provider is invalid.|The error message returned because the metadata of the SAML IdP is invalid.|
|401|AuthenticationFail.SAMLAssertion.Expired|The SAML Assertion is expired.|The error message returned because the SAML assertion has expired.|
|401|AuthenticationFail.SAMLAssertion.Invalid|The SAML Assertion is invalid.|The error message returned because the SAML assertion is invalid.|

