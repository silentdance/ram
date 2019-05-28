# CreatePolicy {#doc_api_977717 .reference}

Creates a policy.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Ram&api=CreateUser) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|CreatePolicy| The name of this action.

 Value: CreatePolicy

 |
|PolicyDocument|String|Yes|\{"Statement":\[\{"Action":\["oss:\*"\],"Effect":"Allow","Resource":\["acs:oss:\*:\*:\*"\]\}\],"Version":"1"\}|The policy text. It can be up to 2048 bytes.|
|PolicyName|String|Yes|OSS-Administrator| The policy name. It must be 1 to 128 characters in length.

 Pattern: `^[a-zA-Z0-9\-]+$`

 |
|Description|String|No|OSS administrator|The policy description. It must be 1 to 1,024 characters in length.|

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|Policy|N/A|N/A|The information about the policy.|
|└CreateDate|String|2015-01-23T12:33:18Z|The date and time when the policy was created.|
|└DefaultVersion|String|v1|The default version.|
|└Description|String|OSS administrator|The policy description.|
|└PolicyName|String|OSS-Administrator|The policy name.|
|└PolicyType|String|Custom|The policy type.|
|RequestId|String|9B34724D-54B0-4A51-B34D-4512372FE1BE|The request ID.|

## Example {#demo .section}

Request example

``` {#request_demo}
https://ram.aliyuncs.com/?Action=CreatePolicy
&PolicyName=OSS-Administrator
&PolicyDocument={"Statement":[{"Action":["oss:*"],"Effect":"Allow","Resource":["acs:oss:*:*:*"]}],"Version":"1"}
&Description=OSS administrator
&<Common parameters>
```

Response example

`XML` format

``` {#xml_return_success_demo}
<CreatePolicyResponse>
  <RequestId>9B34724D-54B0-4A51-B34D-4512372FE1BE</RequestId>
  <Policy>
    <PolicyName>OSS-Administrator</PolicyName>
    <PolicyType>Custom</PolicyType>
    <Description>OSS administrator</Description>
    <DefaultVersion>v1</DefaultVersion>
    <CreateDate>2015-01-23T12:33:18Z</CreateDate>
  </Policy>
</CreatePolicyResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
    "Policy":{
        "Description":"OSS administrator",
        "PolicyName":"OSS-Administrator",
        "CreateDate":"2015-01-23T12:33:18Z",
        "DefaultVersion":"v1",
        "PolicyType":"Custom"
    },
    "RequestId":"9B34724D-54B0-4A51-B34D-4512372FE1BE"
}
```

## Errors { .section}

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ram?spm=5176.10421674.0.0.29c5cav7cav7Io).

