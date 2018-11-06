# AssumeRole {#reference_clc_3sv_xdb .reference}

## Interface description {#section_lgj_jsv_xdb .section}

You can use this interface to obtain a temporary identity to assume a role.

## Request prameters {#section_it1_ksv_xdb .section}

**Action **

-   Type: String
-   Required: Yes
-   Description: A required system parameter. The parameter value is “AssumeRole”.

**RoleArn**

-   Type: String
-   Required: Yes
-   Description: Role resource descriptor. Each role has a unique Aliyun Resource Name \(ARN\). The format is: acs:ram::$accountID:role/$roleName Example: acs:ram::1234567890123456:role/samplerole . You can view the ARN of a role in RAM role management.

**RoleSessionName**

-   Type: String
-   Required: Yes
-   Description: You can use this parameter to identify different tokens in order to indicate who is using a specific token, which facilitates audit.
-   Format: 

    ```
    ^[a-zA-Z0-9\. @\-_]+$
    ```

    **Note:** An input of 2-32 characters is supported. Please enter at least 2 characters. If only 1 character is entered, an error occurs.


**Policy**

-   Name: Policy
-   Type: String
-   Required: No
-   Description: Authorization policy [Policy syntax structure](../../../../reseller.en-US/User Guide/Policy Language/Policy syntax structure.md). The policy length is restricted to 1024 bytes. You can use this parameter to restrict permissions of the generated tokens. If this parameter is not set, the returned token will have all permissions of a specific role.

**DurationSeconds**

-   Name: DurationSeconds
-   Type: Integer
-   Required: No
-   Description: Specified expiration duration, in seconds. The expiration duration ranges from 900 seconds to 3600 seconds, and the default value is “3600”.

## Return parameters {#section_tqj_lsv_xdb .section}

**Credentials**

-   Type:[Credentials](reseller.en-US/API reference/API reference (STS)/Data types/Credentials.md)
-   Description: Access credential.

**AssumedRoleUser**

-   Description: Temporary role assume identity.

## Operation example {#section_tdy_lsv_xdb .section}

**HTTP Request**

```
https://sts.aliyuncs.com?Action=AssumeRole
&RoleArn=acs:ram::1234567890123456:role/adminrole
&RoleSessionName=alice
&DurationSeconds=3600
&Policy=<url_encoded_policy>
&<Public request parameters>
```

**HTTP Response**

-   **XML format**

    ```
    <AssumeRoleResponse>
        <RequestId>6894B13B-6D71-4EF5-88FA-F32781734A7F</RequestId>
        <AssumedRoleUser>
            <arn>acs:sts::1234567890123456:assumed-role/AdminRole/alice</arn>
            <AssumedRoleUserId>344584339364951186:alice<AssumedRoleUserId>
        </AssumedRoleUser>
        <Credentials>
            <AccessKeyId>STS.L4aBSCSJVMuKg5U1vFDw</AccessKeyId>
            <AccessKeySecret>wyLTSmsyPGP1ohvvw8xYgB29dlGI8KMiH2pKCNZ9</AccessKeySecret>
            <SecurityToken>CAESrAIIARKAAShQquMnLIlbvEcIxO6wCoqJufs8sWwieUxu45hS9AvKNEte8KRUWiJWJ6Y+YHAPgNwi7yfRecMFydL2uPOgBI7LDio0RkbYLmJfIxHM2nGBPdml7kYEOXmJp2aDhbvvwVYIyt/8iES/R6N208wQh0Pk2bu+/9dvalp6wOHF4gkFGhhTVFMuTDRhQlNDU0pWTXVLZzVVMXZGRHciBTQzMjc0KgVhbGljZTCpnJjwySk6BlJzYU1ENUJuCgExGmkKBUFsbG93Eh8KDEFjdGlvbkVxdWFscxIGQWN0aW9uGgcKBW9zczoqEj8KDlJlc291cmNlRXF1YWxzEghSZXNvdXJjZRojCiFhY3M6b3NzOio6NDMyNzQ6c2FtcGxlYm94L2FsaWNlLyo=</SecurityToken>
            <Expiration>2015-04-09T11:52:19Z</Expiration>
        </Credentials>
    </AssumeRoleResponse>
    ```

-   **JSON format**

    ```
    {
        "Credentials": {
            "AccessKeyId": "STS.L4aBSCSJVMuKg5U1vFDw",
            "AccessKeySecret": "wyLTSmsyPGP1ohvvw8xYgB29dlGI8KMiH2pKCNZ9",
            "Expiration": "2015-04-09T11:52:19Z",
            "SecurityToken": "CAESrAIIARKAAShQquMnLIlbvEcIxO6wCoqJufs8sWwieUxu45hS9AvKNEte8KRUWiJWJ6Y+YHAPgNwi7yfRecMFydL2uPOgBI7LDio0RkbYLmJfIxHM2nGBPdml7kYEOXmJp2aDhbvvwVYIyt/8iES/R6N208wQh0Pk2bu+/9dvalp6wOHF4gkFGhhTVFMuTDRhQlNDU0pWTXVLZzVVMXZGRHciBTQzMjc0KgVhbGljZTCpnJjwySk6BlJzYU1ENUJuCgExGmkKBUFsbG93Eh8KDEFjdGlvbkVxdWFscxIGQWN0aW9uGgcKBW9zczoqEj8KDlJlc291cmNlRXF1YWxzEghSZXNvdXJjZRojCiFhY3M6b3NzOio6NDMyNzQ6c2FtcGxlYm94L2FsaWNlLyo="
        },
        "AssumedRoleUser": {
            "arn": "acs:sts::1234567890123456:assumed-role/AdminRole/alice",
            "AssumedRoleUserId":"344584339364951186:alice"
            },
        "RequestId": "6894B13B-6D71-4EF5-88FA-F32781734A7F"
    }
    ```


