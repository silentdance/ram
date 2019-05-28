# CreateAccessKey {#doc_api_Ram_CreateAccessKey .reference}

Creates an AccessKey for a RAM user.

## Debug {#apiExplorer .section}

Use [API Explorer](https://api.aliyun.com/#product=Ram&api=GetUser) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|CreateAccessKey| The name of this action.

 Value: CreateAccessKey

 |
|UserName|String|No|Alice|The username of the RAM user that can call this API action to create an AccessKey.|

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|AccessKey|N/A|N/A|The AccessKey.|
|└AccessKeyId|String|0wNEpMMlzy7s\*\*\*\*|The AccessKeyId.|
|└AccessKeySecret|String|PupkTg8jdmau1cXxYacgE736PJ\*\*\*\*|The AccessKeySecret.|
|└CreateDate|String|2015-01-23T12:33:18Z|The date and time when the AccessKey was created.|
|└Status|String|Active| The status of the AccessKey.

 Valid values: Active | Inactive

 |
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|The request ID.|

## Example {#demo .section}

Request example

``` {#request_demo}
https://ram.aliyuncs.com/?Action=CreateAccessKey
&UserName=Alice
&<Common parameters>
```

Response example

`XML` format

``` {#xml_return_success_demo}
<CreateAccessKeyResponse>
  <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
  <AccessKey>
    <AccessKeyId>0wNEpMMlzy7s****</AccessKeyId>
    <AccessKeySecret>PupkTg8jdmau1cXxYacgE736PJ****</AccessKeySecret>
    <Status>Active</Status>
    <CreateDate>2015-01-23T12:33:18Z</CreateDate>
  </AccessKey>
</CreateAccessKeyResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
    "AccessKey":{
        "Status":"Active",
        "AccessKeySecret":"PupkTg8jdmau1cXxYacgE736PJ****",
        "AccessKeyId":"0wNEpMMlzy7s****",
        "CreateDate":"2015-01-23T12:33:18Z"
    },
    "RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368"
}
```

## Errors { .section}

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ram?spm=5176.10421674.0.0.29c5cav7cav7Io).

