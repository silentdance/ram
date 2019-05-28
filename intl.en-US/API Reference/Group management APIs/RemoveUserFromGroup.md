# RemoveUserFromGroup {#doc_api_Ram_RemoveUserFromGroup .reference}

Removes a RAM user from a RAM user group.

## Debug {#apiExplorer .section}

Use [API Explorer](https://api.aliyun.com/#product=Ram&api=GetUser) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|RemoveUserFromGroup| The name of this action.

 Value: RemoveUserFromGroup

 |
|GroupName|String|Yes|Dev-Team|The RAM user group name.|
|UserName|String|Yes|Alice|The username of the RAM user to be removed.|

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|A07EF215-B9B3-8CB2-2899-3F9575C6E320|The request ID.|

## Example {#demo .section}

Request example

``` {#request_demo}
https://ram.aliyuncs.com/?Action=RemoveUserFromGroup
&UserName=Alice
&GroupName=Dev-Team
&<Common parameters>
```

Response example

`XML` format

``` {#xml_return_success_demo}
<RemoveUserFromGroupResponse>
  <RequestId>A07EF215-B9B3-8CB2-2899-3F9575C6E320</RequestId>
</RemoveUserFromGroupResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
    "RequestId":"A07EF215-B9B3-8CB2-2899-3F9575C6E320"
}
```

## Errors { .section}

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ram?spm=5176.10421674.0.0.29c5cav7cav7Io).

