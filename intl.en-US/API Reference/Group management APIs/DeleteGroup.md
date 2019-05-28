# DeleteGroup {#doc_api_977713 .reference}

Deletes a RAM user group.

**Note:** Before you delete a RAM user group, make sure that no policy is attached to the group and no RAM user belongs to this group.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Ram&api=CreateUser) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DeleteGroup| The name of this action.

 Value: DeleteGroup

 |
|GroupName|String|Yes|Dev-Team| The RAM user group name. It must be 1 to 64 characters in length.

 Pattern: `^[a-zA-Z0-9\-]+$`.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|FCF40AB5-881C-A0F9-334C-B0AD423AA69D|The request ID.|

## Example {#demo .section}

Request example

``` {#request_demo}
https://ram.aliyuncs.com/?Action=DeleteGroup
&GroupName=Dev-Team
&<Common parameters>
```

Response example

`XML` format

``` {#xml_return_success_demo}
<DeleteGroupResponse>
  <RequestId>FCF40AB5-881C-A0F9-334C-B0AD423AA69D</RequestId>
</DeleteGroupResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
    "RequestId":"FCF40AB5-881C-A0F9-334C-B0AD423AA69D"
}
```

## Errors { .section}

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ram?spm=5176.10421674.0.0.29c5cav7cav7Io).

