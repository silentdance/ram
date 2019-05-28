# AttachPolicyToGroup {#doc_api_Ram_AttachPolicyToGroup .reference}

Attaches a policy to a RAM user group.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Ram&api=CreateUser) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|AttachPolicyToGroup| The name of this action.

 Value: AttachPolicyToGroup

 |
|GroupName|String|Yes|dev|The name of the RAM user group to which the policy is attached.|
|PolicyName|String|Yes|OSS-Administrator|The policy name.|
|PolicyType|String|Yes|Custom| The policy type.

 Valid values: System | Custom

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|697852FB-50D7-44D9-9774-530C31EAC572|The request ID.|

## Example {#demo .section}

Request example

``` {#request_demo}
https://ram.aliyuncs.com/?Action=AttachPolicyToGroup
&PolicyType=Custom
&PolicyName=OSS-Administrator
&GroupName=dev
&<Common parameters>
```

Response example

`XML` format

``` {#xml_return_success_demo}
<AttachPolicyToGroupResponse>
  <RequestId>697852FB-50D7-44D9-9774-530C31EAC572</RequestId>
</AttachPolicyToGroupResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
    "RequestId":"697852FB-50D7-44D9-9774-530C31EAC572"
}
```

## Errors { .section}

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ram?spm=5176.10421674.0.0.29c5cav7cav7Io).

