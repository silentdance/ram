# DeletePolicy {#doc_api_977695 .reference}

Deletes a policy.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Ram&api=CreateUser) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DeletePolicy| The name of this action.

 Value: DeletePolicy

 |
|PolicyName|String|Yes|OSS-Administrator|The policy name.|

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|898FAB24-7509-43EE-A287-086FE4C44394|The request ID.|

## Example {#demo .section}

Request example

``` {#request_demo}
https://ram.aliyuncs.com/?Action=DeletePolicy
&PolicyName=OSS-Administrator
&<Common parameters>
```

Response example

`XML` format

``` {#xml_return_success_demo}
<DeletePolicyResponse>
  <RequestId>898FAB24-7509-43EE-A287-086FE4C44394</RequestId>
</DeletePolicyResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
    "RequestId":"898FAB24-7509-43EE-A287-086FE4C44394"
}
```

## Errors { .section}

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ram?spm=5176.10421674.0.0.29c5cav7cav7Io).

