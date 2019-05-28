# ListUsers {#doc_api_Ram_ListUsers .reference}

Lists all RAM users.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Ram&api=CreateUser) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|ListUsers| The name of this action.

 Value: ListUsers

 |
|Marker|String|No|EXAMPLE|The marker. If part of a response is intercepted, you can use this parameter to obtain the intercepted content.|
|MaxItems|Integer|No|100| The number of response items. If a response is intercepted when it reaches the maximum value of this parameter, the value of IsTruncated is true.

 Value range: 1 to 100

 Default value: 100

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|IsTruncated|Boolean|true|Indicates whether a response is intercepted.|
|Marker|String|EXAMPLE|This parameter is available only when the value of IsTruncated is true. In this case, you need to call this API action and use Marker to obtain the intercepted content.|
|RequestId|String|4B450CA1-36E8-4AA2-8461-86B42BF4CC4E|The request ID.|
|Users|N/A|N/A|The information about the RAM users.|
|└Comments|String|This is a cloud computing engineer.|The comment.|
|└CreateDate|String|2015-01-23T12:33:18Z|The date and time when the RAM user was created.|
|└DisplayName|String|Alice|The display name.|
|└Email|String|alice@example.com|The email address of the RAM user.|
|└MobilePhone|String|86-1860000\*\*\*\*|The mobile phone number of the RAM user.|
|└UpdateDate|String|2015-01-23T12:33:18Z|The date and time when the user information was modified.|
|└UserId|String|122748924538\*\*\*\*|The ID of the RAM user.|
|└UserName|String|Alice|The username.|

## Example {#demo .section}

Request example

``` {#request_demo}
https://ram.aliyuncs.com/?Action=ListUsers
&<Common parameters>
```

Response example

`XML` format

``` {#xml_return_success_demo}
<ListUsersResponse>
  <RequestId>4B450CA1-36E8-4AA2-8461-86B42BF4CC4E</RequestId>
  <Users>
    <User>
      <UserId>122748924538****</UserId>
      <UserName>Alice</UserName>
      <DisplayName>Alice</DisplayName>
      <MobilePhone>86-1860000****</MobilePhone>
      <Email>alice@example.com</Email>
      <Comments>This is a cloud computing engineer.</Comments>
      <CreateDate>2015-01-23T12:33:18Z</CreateDate>
      <UpdateDate>2015-01-23T12:33:18Z</UpdateDate>
    </User>
    <User>
      <UserId>140649822472****</UserId>
      <UserName>Bob</UserName>
      <DisplayName>Bob</DisplayName>
      <MobilePhone>86-1860000****</MobilePhone>
      <Email>bob@example.com</Email>
      <Comments>The administrator.</Comments>
      <CreateDate>2015-02-18T17:22:08Z</CreateDate>
      <UpdateDate>2015-02-18T17:22:08Z</UpdateDate>
    </User>
  </Users>
  <IsTruncated>true</IsTruncated>
  <Marker>EXAMPLE</Marker>
</ListUsersResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
    "Users":{
        "User":[
            {
                "Comments":"This is a cloud computing engineer.",
                "Email":"alice@example.com",
                "UserName":"Alice",
                "UpdateDate":"2015-01-23T12:33:18Z",
                "UserId":"122748924538****",
                "MobilePhone":"86-1860000****",
                "DisplayName":"Alice",
                "CreateDate":"2015-01-23T12:33:18Z"
            },
            {
                "Comments":"The administrator.",
                "Email":"bob@example.com",
                "UserName":"Bob",
                "UpdateDate":"2015-02-18T17:22:08Z",
                "UserId":"140649822472****",
                "MobilePhone":"86-1860000****",
                "DisplayName":"Bob",
                "CreateDate":"2015-02-18T17:22:08Z"
            }
        ]
    },
    "IsTruncated":true,
    "RequestId":"4B450CA1-36E8-4AA2-8461-86B42BF4CC4E",
    "Marker":"EXAMPLE"
}
```

## Error codes { .section}

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ram?spm=5176.10421674.0.0.29c5cav7cav7Io).

