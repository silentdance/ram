# AssumeRoleWithSAML {#reference_qrl_qcb_1hb .reference}

Uses an SAML assertion to obtain a temporary identity for assuming a role.

## Request parameters {#section_it1_ksv_xdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|:------------|:----------|
|Action|String|Yes|AssumeRoleWithSAML| The name of this action.

 Value: AssumeRoleWithSAML

 |
|SAMLProviderArn|String|Yes|acs:ram::123456789012\*\*\*\*:saml-provider/company1| The Alibaba Cloud Resource Name \(ARN\) of the identity provider \(IdP\) created in RAM.

 Pattern: `acs:ram::$account_ID:saml-provider/$saml_provider_ID`

 |
|RoleArn|String|Yes|acs:ram::123456789012\*\*\*\*:role/adminrole| The ARN of the role to be assumed.

 Pattern: `acs:ram::$accountID:role/$roleName`

 |
|SAMLAssertion|String|Yes|<base64\_encoded\_saml\_assertion\>|The SAML assertion that is encoded by using Base64. The value must be 4 to 100000 bytes in length.|
|Policy|String|No|<url\_encoded\_policy\>|The policy that specifies the permission of the STS token. If this parameter is left unspecified, the STS token has all permissions of a specific role. This parameter must be 1 to 1024 bytes in length.|
|DurationSeconds|String|No|3,600| The expiration time.

 Unit: second

 Value range: 900 to 3,600

 Default value: 3,600

 |

## Response parameters {#section_tqj_lsv_xdb .section}

|Parameter|Type|Example value|Description|
|:--------|:---|:------------|:----------|
|RequestId|String|6894B13B-6D71-4EF5-88FA-F32781734A7F|The request ID.|
|Credentials|N/A|N/A|The access credential.|
|└AccessKeyId|String|STS.L4aBSCSJVMuKg5U1\*\*\*\*|The acces key ID.|
|└AccessKeySecret|String|wyLTSmsyPGP1ohvvw8xYgB29dlGI8KMiH2pK\*\*\*\*|The access key secret.|
|└SecurityToken|String|\*\*\*\*\*\*\*\*|The security token.|
|└Expiration|String|2015-04-09T11:52:19Z|The expiration time.|
|AssumedRoleUser|N/A|N/A|The temporary identity to assume the role.|
|└Arn|String|acs:sts::123456789012\*\*\*\*:assumed-role/AdminRole/alice| The ARN of the temporary identity to assume the role.

 Pattern: `acs:ram::$accountID:assumed-role/$roleName/$roleSessionName`

 |
|└AssumedRoleUserId|String|34458433936495\*\*\*\*:alice|The ID of the temporary identity to assume the role.|
|SAMLAssertionInfo|N/A|N/A|The information in the SAML assertion.|
|└SubjectType|String|persistent|The format of the `NameID` field in the SAML assertion. If the `NameID` contains the `urn:oasis:names:tc:SAML:2.0:nameid-format:` prefix, the prefix will be removed. For example, if the prefix is `urn:oasis:names:tc:SAML:2.0:nameid-format:persistant/transient`, only `persistant/transient` is displayed.|
|└Subject|String|alice@example.com|The value of the `Subject - NameID` field in the SAML assertion.|
|└Recipient|String|https://signin.aliyun.com/saml-role/SSO|The `Recipient` attribute of the `Subject - SubjectConfirmation - SubjectConfirmationData` field in the SAML assertion.|
|└Issuer|String|http://example.com/adfs/services/trust|The value of the `Issuer` field in the SAML assertion.|

## Example {#section_tdy_lsv_xdb .section}

**Note:** The SAMLAssertion parameter may have a large amount of body text. Therefore, we recommend that you use POST rather than GET when sending a request.

Response example

`XML` format

``` {#codeblock_c3r_m4i_fh0}
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

`JSON` format

``` {#codeblock_xqh_oe6_8se}
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

## Errors {#section_rf1_vrv_kn4 .section}

|Error code|Error message|HTTP status code|Meaning|
|----------|-------------|----------------|-------|
|MissingParameter.SAMLAssertion|Parameter SAMLAssertion is required.|400|The SAMLAssertion parameter is required.|
|MissingParameter.SAMLProviderArn|Parameter SAMLProviderArn is required.|400|The SAMLProviderArn parameter is required.|
|MissingParameter.RoleArn|Parameter RoleArn is required.|400|The RoleArn parameter is required.|
|InvalidParameter.PolicyGrammar|Invalid Policy.|400|The policy is invalid.|
|InvalidParameter.PolicySize|The max size of policy string is 1024.|400|The policy cannot exceed 1024 bytes.|
|InvalidParameter.RoleSessionName|The RoleSessionName is invalid.|400|The role session name is invalid.|
|InvalidParameter.DurationSeconds|The DurationSeconds is invalid.|400|The DurationSeconds parameter is invalid.|
|EntityNotExist.SAMLProvider|Can not find SAML provider.|404|The SAML IdP does not exist.|
|EntityNotExist.RoleArn|The specified Role does not exists.|404|The specified role does not exist.|
|AuthenticationFail.IDPMetadata.Invalid|The IdP Metadata of your SAML Provider is invalid.|401|The metadata of your SAML IdP is invalid.|
|AuthenticationFail.SAMLAssertion.Expired|The SAML Assertion is expired.|401|The SAML assertion has expired.|
|AuthenticationFail.SAMLAssertion.Invalid|The SAML Assertion is invalid.|401|The SAML assertion is invalid.|

