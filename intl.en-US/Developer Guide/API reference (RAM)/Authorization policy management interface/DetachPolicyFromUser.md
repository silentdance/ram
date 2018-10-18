# DetachPolicyFromUser {#reference_fqb_k44_xdb .reference}

## Interface description {#section_erh_xh4_xdb .section}

Detaches a specified authorization policy from a user.

## Request parameters {#section_nps_yh4_xdb .section}

**Action**

-   Type: String
-   Required: Yes
-   Description: Required. The parameter value is “DetachPolicyFromUser”.

**PolicyType**

-   Type: String
-   Required: Yes
-   Description: Authorization policy type. Value: “System” or “Custom”.

**PolicyName**

-   Type: String
-   Required: Yes
-   Description: Authorization policy name.

**UserName**

-   Type: String
-   Required: Yes
-   Description: User name. Example: zhangqiang

## Return parameters {#section_ldp_zh4_xdb .section}

Only public parameters are returned. For details, see[Public parameters](reseller.en-US/Developer Guide/API reference (RAM)/Method of calling/Public parameters.md)

## Required permissions {#section_twc_134_xdb .section}

**Action**

```
ram:DetachPolicyFromUser
```

**Resource**

```
acs:ram:*:${AccountId}:user/${UserName}

acs:ram:*:${AccountId} or system:policy/${PolicyName}
```

## Error messages {#section_unp_qm4_xdb .section}

**InvalidParameter.PolicyType**

-   HTTP Status: 400
-   Error Message: The parameter - "PolicyType" is incorrect.

**InvalidParameter.UserName.InvalidChars**

-   HTTP Status: 400
-   Error Message: The parameter - "UserName" contains invalid chars.

**InvalidParameter.UserName.Length**

-   HTTP Status: 400
-   Error Message: The parameter - "UserName" beyond the length limit.

**EntityNotExist.User**

-   HTTP Status: 404
-   Error Message: The user does not exist.

**InvalidParameter.PolicyName.InvalidChars**

-   HTTP Status: 400
-   Error Message: The parameter - "PolicyNam" contains invalid chars.

**InvalidParameter.PolicyName.Length**

-   HTTP Status: 400
-   Error Message: The parameter - "PolicyName" beyond the length limit.

**EntityNotExist.Policy**

-   HTTP Status: 404
-   Error Message: The policy does not exist.

**EntityNotExist.User.Policy**

-   HTTP Status: 404
-   Error Message: The indicate policy of the user does not exist.

## Operation examples {#section_hbw_1n4_xdb .section}

## Request example {#section_knn_d34_xdb .section}

```
https://ram.aliyuncs.com/?Action=DetachPolicyFromUser
&PolicyType=Custom
&PolicyName=OSS-Administrator
&UserName=zhangqiang
&<Public request parameters>
```

## Return example {#section_jy3_f34_xdb .section}

-   XML format

    ```
    <DetachPolicyFromUserResponse>
        <RequestId>697852FB-50D7-44D9-9774-530C31EAC572</RequestId>
    </DetachPolicyFromUserResponse>
    ```

-   JSON format

    ```
    
        "RequestId": "697852FB-50D7-44D9-9774-530C31EAC572"
    
    ```


