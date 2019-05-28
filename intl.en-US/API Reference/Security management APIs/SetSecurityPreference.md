# SetSecurityPreference {#doc_api_977692 .reference}

Sets the security preferences.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Ram&api=CreateUser) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|SetSecurityPreference| The name of this action.

 Value: SetSecurityPreference

 |
|AllowUserToChangePassword|Boolean|No|true|Indicates whether RAM users can change their passwords.|
|AllowUserToManageAccessKeys|Boolean|No|false|Indicates whether RAM users can manage their AccessKeys.|
|AllowUserToManageMFADevices|Boolean|No|true|Indicates whether RAM users can attach or remove Multi-Factor Authentication \(MFA\) devices.|
|AllowUserToManagePublicKeys|Boolean|No|false|Indicates whether RAM users can manage their public keys.|
|EnableSaveMFATicket|Boolean|No|true|Indicates whether RAM users can save MFA tickets during logon. The ticket is currently valid for seven days.|
|LoginNetworkMasks|String|No|10.0.0.0/8|The logon mask. This parameter is left unspecified by default. That is, all IP addresses on the network can be used for logon.|
|LoginSessionDuration|Integer|No|6| The number of hours that the logon session is valid.

 Unit: hour

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|The request ID.|
|SecurityPreference|N/A|N/A|The security preference.|
|└AccessKeyPreference|N/A|N/A|The AccessKey preference.|
|└AllowUserToManageAccessKeys|Boolean|false|Indicates whether RAM users can manage their AccessKeys.|
|└LoginProfilePreference|N/A|N/A|The Logon preference.|
|└AllowUserToChangePassword|Boolean|true|Indicates whether RAM users can change their passwords.|
|└EnableSaveMFATicket|Boolean|true|Indicates whether RAM users can save MFA tickets during logon.|
|└LoginNetworkMasks|String|10.0.0.0/8|The logon mask. This parameter is left unspecified by default. That is, all IP addresses on the network can be used for logon.|
|└LoginSessionDuration|Integer|6| The number of hours that the logon session is valid.

 Unit: hour

 |
|└MFAPreference|N/A|N/A|The MFA preference.|
|└AllowUserToManageMFADevices|Boolean|true|Indicates whether RAM users can attach or remove MFA devices.|
|└PublicKeyPreference|N/A|N/A|The public key preference.|
|└AllowUserToManagePublicKeys|Boolean|false|Indicates whether RAM users can manage their public keys.|

## Example {#demo .section}

Request example

``` {#request_demo}
https://ram.aliyuncs.com/?Action=SetSecurityPreference
&EnableSaveMFATicket=true
&AllowUserToChangePassword=true
&AllowUserToManageAccessKeys=false
&<Common parameters>
```

Response example

`XML` format

``` {#xml_return_success_demo}
<SetSecurityPreferenceResponse>
  <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
  <SecurityPreference>
    <LoginProfilePreference>
      <EnableSaveMFATicket>true</EnableSaveMFATicket>
      <AllowUserToChangePassword>true</AllowUserToChangePassword>
      <LoginNetworkMasks>10.0.0.0/8</LoginNetworkMasks>
      <LoginSessionDuration>6</LoginSessionDuration>
    </LoginProfilePreference>LoginProfilePreference&gt;
        <AccessKeyPreference>
      <AllowUserToManageAccessKeys>false</AllowUserToManageAccessKeys>
    </AccessKeyPreference>
    <MFAPreference>
      <AllowUserToManageMFADevices>false</AllowUserToManageMFADevices>
    </MFAPreference>
    <PublicKeyPreference>
      <AllowUserToManagePublicKeys>false</AllowUserToManagePublicKeys>
    </PublicKeyPreference>
  </SecurityPreference>
</SetSecurityPreferenceResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
    "RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368",
    "SecurityPreference":{
        "LoginProfilePreference":{
            "LoginSessionDuration":6,
            "LoginNetworkMasks":"10.0.0.0/8",
            "EnableSaveMFATicket":true,
            "AllowUserToChangePassword":true
        },
        "AccessKeyPreference":{
            "AllowUserToManageAccessKeys":false
        },
        "PublicKeyPreference":{
            "AllowUserToManagePublicKeys":false
        },
        "MFAPreference":{
            "AllowUserToManageMFADevices":true
        }
    }
}
```

## Errors { .section}

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ram?spm=5176.10421674.0.0.29c5cav7cav7Io).

