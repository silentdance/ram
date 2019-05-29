# SetDefaultPolicyVersion {#doc_api_977678 .reference}

Sets the default version of a policy.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Ram&api=CreateUser) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|SetDefaultPolicyVersion| The name of this action.

 Value: SetDefaultPolicyVersion

 |
|PolicyName|String|Yes|OSS-Administrator|The policy name.|
|VersionId|String|Yes|v2|The ID of the default policy version.|

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|9B34724D-54B0-4A51-B34D-4512372FE1BE|The request ID.|

## Example {#demo .section}

Request example

``` {#request_demo}
https://ram.aliyuncs.com/?Action=SetDefaultPolicyVersion
&PolicyName=OSS-Administrator
&VersionId=v2
&<Common parameters>
```

Response example

`XML` format

``` {#xml_return_success_demo}
<SetDefaultPolicyVersionResponse>
  <RequestId>9B34724D-54B0-4A51-B34D-4512372FE1BE</RequestId>
</SetDefaultPolicyVersionResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
    "RequestId":"9B34724D-54B0-4A51-B34D-4512372FE1BE"
}
```

## Errors { .section}

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ram?spm=5176.10421674.0.0.29c5cav7cav7Io).

