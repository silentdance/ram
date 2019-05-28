# ListPoliciesForUser {#doc_api_Ram_ListPoliciesForUser .reference}

Lists the policies attached to a RAM user.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Ram&api=CreateUser) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|ListPoliciesForUser| The name of this action.

 Value: ListPoliciesForUser

 |
|UserName|String|Yes|Alice|The username of the RAM user to which the policies are attached.|

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|Policies|N/A|N/A|The policy list.|
|└AttachDate|String|2015-01-23T12:33:18Z|The date and time when a policy was attached to the RAM user.|
|└DefaultVersion|String|v1|The default policy version.|
|└Description|String|OSS administrator|The policy description.|
|└PolicyName|String|OSS-Administrator|The policy name.|
|└PolicyType|String|Custom|The policy type.|
|RequestId|String|7B8A4E7D-6CFF-471D-84DF-195A7A241ECB|The request ID.|

## Example {#demo .section}

Request example

``` {#request_demo}
https://ram.aliyuncs.com/?Action=ListPoliciesForUser
&UserName=Alice
&<Common parameters>
```

Response example

`XML` format

``` {#xml_return_success_demo}
<ListPoliciesForUserResponse>
    <RequestId>7B8A4E7D-6CFF-471D-84DF-195A7A241ECB</RequestId>
    <Policies>
        <Policy>
            <PolicyName>OSS-Administrator</PolicyPolicyName>
            <PolicyType>Custom</PolicyType>
            <Description>OSS administrator</Description>
            <DefaultVersion>v1</DefaultVersion>
            <AttachDate>2015-01-23T12:33:18Z</AttachDate>
        </Policy>
        <Policy>
            <PolicyName>ReadOnlyAccess</PolicyPolicyName>
            <PolicyType>System</PolicyType>
            <Description>Read-only permission</Description>
            <DefaultVersion>v1</DefaultVersion>
            <AttachDate>2015-02-18T17:22:08Z</AttachDate>
        </Policy>
    </Policies>
</ListPoliciesForUserResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
    "Policies":{
        "Policy":[
            {
                "Description":"OSS administrator",
                "PolicyName":"OSS-Administrator",
                "AttachDate":"2015-01-23T12:33:18Z",
                "DefaultVersion":"v1",
                "PolicyType":"Custom"
            },
            {
                "Description":"Read-only permission",
                "PolicyName":"ReadOnlyAccess",
                "AttachDate":"2015-02-18T17:22:08Z",
                "DefaultVersion":"v1",
                "PolicyType":"System"
            }
        ]
    },
    "RequestId":"7B8A4E7D-6CFF-471D-84DF-195A7A241ECB"
}
```

## Errors { .section}

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ram?spm=5176.10421674.0.0.29c5cav7cav7Io).

