# CreateUser {#doc_api_Ram_CreateUser .reference}

Creates a RAM user.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Ram&api=CreateUser) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|CreateUser| The name of this action.

 Value: CreateUser

 |
|UserName|String|Yes|Alice| The username. It must be 1 to 64 characters in length.

 Pattern: `^[a-zA-Z0-9\.@\-_]+$`

 |
|Comments|String|No|This is a cloud computing engineer.|The comment. It must be 1 to 128 characters in length.|
|DisplayName|String|No|Alice| The display name. It must be 1 to 128 characters in length.

 Pattern: `^[a-zA-Z0-9\.@\-\u4e00-\u9fa5]+$`

 |
|Email|String|No|alice@example.com|The email address of the RAM user.|
|MobilePhone|String|No|86-1868888\*\*\*\*| The mobile phone number of the RAM user.

 Format: International area code-mobile phone number

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|The request ID.|
|User|N/A|N/A|The RAM user information.|
|└Comments|String|This is a cloud computing engineer.|The comment.|
|└CreateDate|String|2015-01-23T12:33:18Z|The date and time when the RAM user was created.|
|└DisplayName|String|Alice|The display name.|
|└Email|String|alice@example.com|The email address of the RAM user.|
|└MobilePhone|String|86-1860000\*\*\*\*|The mobile phone number of the RAM user.|
|└UserId|String|122748924538\*\*\*\*|The ID of the RAM user.|
|└UserName|String|Alice|The username.|

## Example {#demo .section}

Request example

``` {#request_demo}
https://ram.aliyuncs.com/?Action=CreateUser
&UserName=Alice
&DisplayName=Alice
&MobilePhone=86-1868888****
&Email=alice@example.com
&Comments=This is a cloud computing engineer.
&<Common parameters>
```

Response example

`XML` format

``` {#xml_return_success_demo}
<CreateUserResponse>
  <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
  <User>
    <UserId>122748924538****</UserId>
    <UserName>Alice</UserName>
    <DisplayName>Alice</DisplayName>
    <MobilePhone>86-1860000****</MobilePhone>
    <Email>alice@example.com</Email>
    <Comments>This is a cloud computing engineer.</Comments>
    <CreateDate>2015-01-23T12:33:18Z</CreateDate>
  </User>
</CreateUserResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
    "User":{
        "Comments":"This is a cloud computing engineer.",
        "Email":"alice@example.com",
        "UserName":"Alice",
        "UserId":"122748924538****",
        "MobilePhone":"86-1860000****",
        "DisplayName":"Alice",
        "CreateDate":"2015-01-23T12:33:18Z"
    },
    "RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368"
}
```

## Errors { .section}

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ram?spm=5176.10421674.0.0.29c5cav7cav7Io).

