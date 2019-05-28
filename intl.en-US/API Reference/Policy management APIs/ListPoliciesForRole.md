# ListPoliciesForRole {#doc_api_Ram_ListPoliciesForRole .reference}

Lists the policies attached to a RAM role.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Ram&api=CreateUser) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|ListPoliciesForRole| The name of this action.

 Value: ListPoliciesForRole

 |
|RoleName|String|Yes|AdminRole|The RAM role name.|

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|Policies|N/A|N/A|The list of policies attached to the RAM role.|
|└AttachDate|String|2015-01-23T12:33:18Z|The date and time when a policy was attached to the RAM role.|
|└DefaultVersion|String|v1|The default policy version.|
|└Description|String|OSS administrator|The policy description.|
|└|String|OSS-Administrator|The policy name.|
|└PolicyType|String|Custom|The policy type.|
|RequestId|String|7B8A4E7D-6CFF-471D-84DF-195A7A241ECB|The request ID.|

## Example {#demo .section}

Request example

``` {#request_demo}
https://ram.aliyuncs.com/?Action=ListPoliciesForRole
&RoleName=AdminRole
&<Common parameters>
```

Response example

`XML` format

``` {#xml_return_success_demo}
<ListPoliciesForRoleResponse>
  <RequestId>7B8A4E7D-6CFF-471D-84DF-195A7A241ECB</RequestId>
  <Policies>
    <Policy>
      <PolicyName>OSS-Administrator</PolicyName>
      <PolicyType>Custom</PolicyType>
      <Description>OSS administrator</Description>
      <DefaultVersion>v1</DefaultVersion>
      <AttachDate>2015-01-23T12:33:18Z</AttachDate>
    </Policy>
    <Policy>
      <PolicyName>ReadOnlyAccess</PolicyName>
      <PolicyType>System</PolicyType>
      <Description>Read-only access</Description>
      <DefaultVersion>v1</DefaultVersion>
      <AttachDate>2015-02-18T17:22:08Z</AttachDate>
    </Policy>
  </Policies>
</ListPoliciesForRoleResponse>
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
                "Description":"Read-only access",
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

