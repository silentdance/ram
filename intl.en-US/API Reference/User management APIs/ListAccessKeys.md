# ListAccessKeys {#doc_api_Ram_ListAccessKeys .reference}

Lists the AccessKeys of a RAM user.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Ram&api=CreateUser) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|ListAccessKeys| The name of this action.

 Value: ListAccessKeys

 |
|UserName|String|No|Alice| The username of the RAM user. If this parameter is not set when the user logs on to the console, the AccessKeys of this user are displayed.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|AccessKeys|N/A|N/A|The information about the RAM user.|
|└AccessKeyId|String|0wNEpMMlzy7s\*\*\*\*|The AccessKeyId.|
|└CreateDate|String|2015-01-23T12:33:18Z|The date and time when an AccessKey was created.|
|└Status|String|Active| The status of an AccessKey.

 Valid values: Active | Inactive

 |
|RequestId|String|4B450CA1-36E8-4AA2-8461-86B42BF4CC4E|The request ID.|

## Example {#demo .section}

Request example

``` {#request_demo}
https://ram.aliyuncs.com/?Action=ListAccessKeys
&<Common parameters>
```

Response example

`XML` format

``` {#xml_return_success_demo}
<ListAccessKeysResponse>
  <RequestId>4B450CA1-36E8-4AA2-8461-86B42BF4CC4E</RequestId>
  <AccessKeys>
    <AccessKey>
      <AccessKeyId>0wNEpMMlzy7s****</AccessKeyId>
      <Status>Active</Status>
      <CreateDate>2015-01-23T12:33:18Z</CreateDate>
    </AccessKey>
    <AccessKey>
      <AccessKeyId>WnIWUruvfaDT****</AccessKeyId>
      <Status>Inactive</Status>
      <CreateDate>2015-03-24T21:12:21Z</CreateDate>
    </AccessKey>
  </AccessKeys>
</ListAccessKeysResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
    "RequestId":"4B450CA1-36E8-4AA2-8461-86B42BF4CC4E",
    "AccessKeys":{
        "AccessKey":[
            {
                "Status":"Active",
                "AccessKeyId":"0wNEpMMlzy7s****",
                "CreateDate":"2015-01-23T12:33:18Z"
            },
            {
                "Status":"Inactive",
                "AccessKeyId":"WnIWUruvfaDT****",
                "CreateDate":"2015-03-24T21:12:21Z"
            }
        ]
    }
}
```

## Errors { .section}

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ram?spm=5176.10421674.0.0.29c5cav7cav7Io).

