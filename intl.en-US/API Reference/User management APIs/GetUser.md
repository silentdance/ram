# GetUser {#doc_api_Ram_GetUser .reference}

Obtains the detailed information about a RAM user.

## Debug {#apiExplorer .section}

Use [API Explorer](https://api.aliyun.com/#product=Ram&api=GetUser) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|GetUser| The name of this action.

 Value: GetUser

 |
|UserName|String|Yes|Alice| The username. It must be 1 to 64 characters in length.

 Pattern: `^[a-zA-Z0-9\.@\-_]+$`

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|2D69A58F-345C-4FDE-88E4-BF5189484043|The request ID.|
|User|N/A|N/A|The RAM user information.|
|└Comments|String|This is a cloud computing engineer.|The comment.|
|└CreateDate|String|2015-01-23T12:33:18Z|The date and time when the RAM user was created.|
|└DisplayName|String|Alice|The display name.|
|└Email|String|alice@example.com|The email address of the RAM user.|
|└LastLoginDate|String|2015-01-23T12:33:18Z|The date and time when the user last logged on to the RAM console by using the password.|
|└MobilePhone|String|86-1860000\*\*\*\*|The mobile phone number of the RAM user.|
|└UpdateDate|String|2015-02-11T03:15:21Z|The date and time when the user information was modified.|
|└UserId|String|122748924538\*\*\*\*|The ID of the RAM user.|
|└UserName|String|Alice|The username.|

## Example {#demo .section}

Request example

``` {#request_demo}
https://ram.aliyuncs.com/?Action=GetUser
&UserName=Alice
&<Common parameters>
```

Response example

`XML` format

``` {#xml_return_success_demo}
<GetUserResponse>
  <RequestId>2D69A58F-345C-4FDE-88E4-BF5189484043</RequestId>
  <User>
    <UserId>122748924538****</UserId>
    <UserName>Alice</UserName>
    <DisplayName>Alice</DisplayName>
    <MobilePhone>86-1860000****</MobilePhone>
    <Email>alice@example.com</Email>
    <Comments>This is a cloud computing engineer.</Comments>
    <CreateDate>2015-01-23T12:33:18Z</CreateDate>
    <UpdateDate>2015-02-11T03:15:21Z</UpdateDate>
    <LastLoginDate>2015-01-23T12:33:18Z</LastLoginDate>
  </User>
</GetUserResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
    "User":{
        "LastLoginDate":"2015-01-23T12:33:18Z",
        "Comments":"This is a cloud computing engineer.",
        "Email":"alice@example.com",
        "UserName":"Alice",
        "UpdateDate":"2015-02-11T03:15:21Z",
        "UserId":"122748924538****",
        "MobilePhone":"86-1860000****",
        "DisplayName":"Alice",
        "CreateDate":"2015-01-23T12:33:18Z"
    },
    "RequestId":"2D69A58F-345C-4FDE-88E4-BF5189484043"
}
```

## Errors { .section}

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ram?spm=5176.10421674.0.0.29c5cav7cav7Io).

