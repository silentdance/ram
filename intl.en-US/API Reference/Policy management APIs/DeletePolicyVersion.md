# DeletePolicyVersion {#doc_api_977672 .reference}

Deletes a version of a specified policy.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Ram&api=CreateUser) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DeletePolicyVersion| The name of this action.

 Value: DeletePolicyVersion

 |
|PolicyName|String|Yes|OSS-Administrator|The policy name.|
|VersionId|String|Yes|v3|The ID of the target policy version.|

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|9B34724D-54B0-4A51-B34D-4512372FE1BE|The request ID.|

## Example {#demo .section}

Request example

``` {#request_demo}
https://ram.aliyuncs.com/?Action=DeletePolicyVersion
&PolicyName=OSS-Administrator
&VersionId=v3
&<Common parameters>
```

Response example

`XML` format

``` {#xml_return_success_demo}
<DeletePolicyVersionResponse>
  <RequestId>9B34724D-54B0-4A51-B34D-4512372FE1BE</RequestId>
</DeletePolicyVersionResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
    "RequestId":"9B34724D-54B0-4A51-B34D-4512372FE1BE"
}
```

## Errors { .section}

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ram?spm=5176.10421674.0.0.29c5cav7cav7Io).

