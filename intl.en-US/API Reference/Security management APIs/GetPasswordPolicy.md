# GetPasswordPolicy {#doc_api_977673 .reference}

Obtains the password policy, including the password strength, of a RAM user.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Ram&api=CreateUser) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|GetPasswordPolicy| The name of this action.

 Value: GetPasswordPolicy

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|PasswordPolicy|N/A|N/A|The password policy.|
|└HardExpiry|Boolean|false| Indicates whether the password has expired.

 Valid values: true | false

 Default value: false

 **Note:** 

-   If the value of this parameter is true, the RAM user cannot log on until the administrator resets the password.
-   If the value of this parameter is false, the RAM user can change the password after the password expires and continues to log on as the user.

 |
|└MaxLoginAttemps|Integer|5|The maximum number of permitted logon attempts within one hour. **Note:** The number of logon attempts is reset to zero after you change the password.

 |
|└MaxPasswordAge|Integer|0| The number of days that the password is valid.

 Unit: day

 Default value: 0

 **Note:** The valid period will be changed if you reset the password. If the value of this parameter is 0, the password never expires.

 |
|└MinimumPasswordLength|Integer|12|The minimum number of allowed characters in the password.|
|└PasswordReusePrevention|Integer|0| The number of previous passwords that the RAM user is prevented from reusing.

 Default value: 0

 **Note:** If the value of this parameter is 0, the RAM user is not prevented from reusing previous passwords.

 |
|└RequireLowercaseCharacters|Boolean|true|Indicates that one or more lowercase letters are required.|
|└RequireNumbers|Boolean|true|Indicates that one or more numbers are required.|
|└RequireSymbols|Boolean|true|Indicates that one or more special characters are required.|
|└RequireUppercaseCharacters|Boolean|true|Indicates that one or more uppercase letters are required.|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|The request ID.|

## Example {#demo .section}

Request example

``` {#request_demo}
https://ram.aliyuncs.com/?Action=GetPasswordPolicy
&AcccountAlias=myalias
&<Common parameters>
```

Response example

`XML` format

``` {#xml_return_success_demo}
<GetPasswordPolicyResponse>
  <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
  <PasswordPolicy>
    <HardExpiry>false</HardExpiry>
    <MaxLoginAttemps>5</MaxLoginAttemps>
    <MaxPasswordAge>0</MaxPasswordAge>
    <PasswordReusePrevention>0</PasswordReusePrevention>
    <MinimumPasswordLength>12</MinimumPasswordLength>
    <RequireLowercaseCharacters>true</RequireLowercaseCharacters>
    <RequireUppercaseCharacters>true</RequireUppercaseCharacters>
    <RequireNumbers>true</RequireNumbers>
    <RequireSymbols>true</RequireSymbols>
  </PasswordPolicy>
</GetPasswordPolicyResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
    "RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368",
    "PasswordPolicy":{
        "RequireUppercaseCharacters":true,
        "MaxPasswordAge":0,
        "HardExpiry":false,
        "RequireNumbers":true,
        "RequireSymbols":true,
        "MaxLoginAttemps":5,
        "PasswordReusePrevention":0,
        "RequireLowercaseCharacters":true,
        "MinimumPasswordLength":12
    }
}
```

## Errors { .section}

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ram?spm=5176.10421674.0.0.29c5cav7cav7Io).

