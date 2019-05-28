# GetLoginProfile {#doc_api_Ram_GetLoginProfile .reference}

Views the logon configurations of a RAM user.

## Debug {#apiExplorer .section}

Use [API Explorer](https://api.aliyun.com/#product=Ram&api=GetUser) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|GetLoginProfile| The name of this action.

 Value: GetLoginProfile

 |
|UserName|String|Yes|Alice|The username.|

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|LoginProfile|N/A|N/A|The logon configurations.|
|└CreateDate|String|2015-01-23T12:33:18Z|The creation time.|
|└MFABindRequired|Boolean|true|Indicates that you must attach an MFA device.|
|└PasswordResetRequired|Boolean|true|Indicates that you must change your password upon next logon.|
|└UserName|String|Alice|The username.|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|The request ID.|

## Example {#demo .section}

Request example

``` {#request_demo}
https://ram.aliyuncs.com/?Action=GetLoginProfile
&UserName=Alice
&<Common parameters>
```

Response example

`XML` format

``` {#xml_return_success_demo}
<GetLoginProfile>
  <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
  <LoginProfile>
    <UserName>Alice</UserName>
    <PasswordResetRequired>true</PasswordResetRequired>
    <MFABindRequired>true</MFABindRequired>
    <CreateDate>2015-01-23T12:33:18Z</CreateDate>
  </LoginProfile>
</GetLoginProfile>
```

`JSON` format

``` {#json_return_success_demo}
{
    "RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368",
    "LoginProfile":{
        "PasswordResetRequired":true,
        "MFABindRequired":true,
        "UserName":"Alice",
        "CreateDate":"2015-01-23T12:33:18Z"
    }
}
```

## Errors { .section}

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ram?spm=5176.10421674.0.0.29c5cav7cav7Io).

