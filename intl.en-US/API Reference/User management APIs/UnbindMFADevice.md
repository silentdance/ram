# UnbindMFADevice {#doc_api_Ram_UnbindMFADevice .reference}

Removes a Multi-Factor Authentication \(MFA\) device from a RAM user.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Ram&api=CreateUser) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|UnbindMFADevice| The name of this action.

 Value: UnbindMFADevice

 |
|UserName|String|Yes|Alice|The username of the RAM user from which the MFA device is removed.|

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|MFADevice|N/A|N/A|The information about the MFA device.|
|└SerialNumber|String|acs:ram::123456789012\*\*\*\*:mfa/device002|The ID of the MFA device.|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|The request ID.|

## Example {#demo .section}

Request example

``` {#request_demo}
https://ram.aliyuncs.com/?Action=UnbindMFADevice
&UserName=Alice
&<Common parameters>
```

Response example

`XML` format

``` {#xml_return_success_demo}
<UnbindMFADeviceResponse>
  <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
  <MFADevice>
    <SerialNumber>acs:ram::123456789012****:mfa/device002</SerialNumber>
  </MFADevice>
</UnbindMFADeviceResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
    "RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368",
    "MFADevice":{
        "SerialNumber":"acs:ram::123456789012****:mfa/device002"
    }
}
```

## Errors { .section}

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ram?spm=5176.10421674.0.0.29c5cav7cav7Io).

