# ChangePassword {#reference_w4g_sfn_xdb .reference}

## Interface description {#section_whn_4tk_xdb .section}

Changes RAM user password.

## Request parameters {#section_k2y_ptk_xdb .section}

**Action**

-   Type: String
-   Required: Yes
-   Description: Operation interface. System required parameter. Value: ChangePassword.

**OldPassword**

-   Type: String
-   Required: Yes
-   Description: Old password

**NewPassword**

-   Type: String
-   Required: Yes
-   Description: Specify the password, which must meet the complexity requirements. For details about the interface for setting password complexity, see [SetPasswordPolicy](reseller.en-US/API reference/API Reference (RAM)/Security setting interface/SetPasswordPolicy.md).

## Return parameters { .section}

Only public parameters are returned. For details, see [Public parameters](reseller.en-US/API reference/API Reference (RAM)/Method of calling/Public parameters.md)

## Required permissions {#section_g22_rtk_xdb .section}

**Action**

```
ram:ChangePassword
```

**Resource**

```
acs:ram:*:${AccountId}:user/${UserName}
```

## Error messages {#section_erf_h2n_xdb .section}

**NotSupport.Account**

-   HTTP Status: 400
-   Error Message: This method can be only invoked by sub user.

**InvalidParameter.OldPassword.Incorrect**

-   HTTP Status: 400
-   Error Message: The parameter - "OldPassword" is incorrect.

**InvalidParameter.NewPassword.TooWeak**

-   HTTP Status: 400
-   Error Message: The parameter - "NewPassword" is not compliant with the password policy.

**InvalidParameter.NewPassword.ReusePrevention**

-   HTTP Status: 400
-   Error Message: The parameter - "NewPassword" is not compliant with the reuse prevention password policy.

## Operation examples {#section_pwp_vtk_xdb .section}

**Request example**

```
https://ram.aliyuncs.com/?Action=ChangePassword
&OldPassword=123456
&NewPassword=aw$2ad)d
&<Public request parameters>
```

**Return example**

-   XML format

    ```
    <ChangePassword>
        <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
    </ChangePassword>
    ```

-   JSON format

    ```
    
        "RequestId": "04F0F334-1335-436C-A1D7-6C044FE73368"
    
    ```


