# CreatePolicyVersion {#doc_api_977704 .reference}

Creates a version for a policy.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Ram&api=CreateUser) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|CreatePolicyVersion| The name of this action.

 Value: CreatePolicyVersion

 |
|PolicyDocument|String|Yes|\{"Statement":\[\{"Action":\["oss:\*"\],"Effect":"Allow","Resource":\["acs:oss:\*:\*:\*"\]\}\],"Version":"1"\}|The policy content. It can be up to 2048 bytes.|
|PolicyName|String|Yes|OSS-Administrator|The policy name.|
|RotateStrategy|String|No|None| The rotation stategy of a policy. You can set this parameter to delete an existing policy.

 Vaild values:

 -   `None`: indicates no rotation strategy is set
-   `DeleteOldestNonDefaultVersionWhenLimitExceeded`: indicates the earliest and non-active version can be deleted when the number of versions exceeds the limit

 Default value: `None`

 |
|SetAsDefault|Boolean|No|false| Indicates whether to set the version as the default version of the policy.

 Default value: false

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|PolicyVersion|N/A|N/A|The information about the policy version.|
|└CreateDate|String|2015-01-23T12:33:18Z|The date and time when the policy version was created.|
|└IsDefaultVersion|Boolean|false|Indicates whether the version is the default version of the policy.|
|└PolicyDocument|String|\{ "Statement": \[\{ "Action": \["oss:\*"\], "Effect": "Allow", "Resource": \["acs:oss:\*:\*:\*"\]\}\], "Version": "1"\}|The policy content.|
|└VersionId|String|v3|The ID of the policy version.|
|RequestId|String|9B34724D-54B0-4A51-B34D-4512372FE1BE|The request ID.|

## Example {#demo .section}

Request example

``` {#request_demo}
https://ram.aliyuncs.com/?Action=CreatePolicyVersion
&PolicyName=OSS-Administrator
&PolicyDocument={"Statement":[{"Action":["oss:*"],"Effect":"Allow","Resource":["acs:oss:*:*:*"]}],"Version":"1"}
&<Common parameters>
```

Response example

`XML` format

``` {#codeblock_le7_gpr_zdy}
<CreatePolicyVersionResponse>
  <RequestId>9B34724D-54B0-4A51-B34D-4512372FE1BE</RequestId>
  <PolicyVersion>
    <VersionId>v3</VersionId>
    <IsDefaultVersion>false</IsDefaultVersion>
    <CreateDate>2015-01-23T12:33:18Z</CreateDate>
    <PolicyDocument>{ "Statement": [{ "Action": ["oss:*"], "Effect": "Allow", "Resource": ["acs:oss:*:*:*"]}], "Version": "1"}</PolicyDocument>
  </PolicyVersion>
</CreatePolicyVersionResponse>
```

`JSON` format

``` {#codeblock_xv1_umf_oh7}
{
    "RequestId":"9B34724D-54B0-4A51-B34D-4512372FE1BE",
    "PolicyVersion":{
        "IsDefaultVersion":false,
        "VersionId":"v3",
        "PolicyDocument":"{ \"Statement\": [{ \"Action\": [\"oss:*\"], \"Effect\": \"Allow\", \"Resource\": [\"acs:oss:*:*:*\"]}], \"Version\": \"1\"}",
        "CreateDate":"2015-01-23T12:33:18Z"
    }
}
```

## Errors {#section_kfp_r4h_2rb .section}

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ram?spm=5176.10421674.0.0.29c5cav7cav7Io).

