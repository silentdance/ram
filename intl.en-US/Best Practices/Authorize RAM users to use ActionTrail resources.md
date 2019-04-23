# Authorize RAM users to use ActionTrail resources {#concept_kkr_klm_xgb .concept}

This topic describes how to authorize RAM users to use ActionTrail resources by using system policies or custom policies.

## Before you begin {#section_c3m_csm_xgb .section}

1.  View the ActionTrail API actions and their descriptions. For more information, see [RAM account authentication](../../../../reseller.en-US/API Reference/RAM account authentication.md#).
2.  View the RAM policy structure and syntax. For more information, see [Policy structure and syntax](../../../../reseller.en-US/User Guide/Permission management/Policy language/Policy structure and syntax.md#).

## Procedure {#section_03 .section}

1.  Create a RAM user.

    For more information, see [RAM users](../../../../reseller.en-US/User Guide/Identity management/User management/RAM users.md#).

2.  Grant permission to the RAM user.
    -   You can grant required permissions to the RAM user by attaching one or more system policies according to the subsequent ActionTrail-related system policies.

        For more information, see [Permission granting in RAM](../../../../reseller.en-US/User Guide/Permission management/Permission granting/Permission granting in RAM.md#).

    -   You can grant fine-grained permissions to the RAM user by creating custom policies according to the subsequent authorization examples.

        For more information, see [Policy management](../../../../reseller.en-US/User Guide/Permission management/Policy management.md#).


## ActionTrail-related system policies {#section_yty_gmm_xgb .section}

The following table lists the system policies that are commonly used in ActionTrail.

|System policy|Description|
|:------------|:----------|
|AliyunActionTrailFullAccess|Grants a RAM user full management permissions for ActionTrail resources.|
|AliyunActionTrailReadOnlyAccess|Grants a RAM user read-only permission for ActionTrail resources.|

## Authorization examples {#section_xqm_lnm_xgb .section}

-   Example 1: As a RAM administrator, grant a user read-only permission.

    ```language-json
    {
        "Version": "1",
        "Statement": [{
            "Effect": "Allow",
            "Action": [
                "actiontrail:LookupEvents", 
                "actiontrail:Describe*", 
                "actiontrail:Get*"
            ],
            "Resource": "*"
        }]
    }
    ```

-   Example 2: As a RAM administrator, grant a user read-only permission when they log on from a specified IP address.

    ```language-json
    {
        "Version": "1",
        "Statement": [{
            "Effect": "Allow",
            "Action": [
                "actiontrail:LookupEvents", 
                "actiontrail:Describe*", 
                "actiontrail:Get*"
            ],
            "Resource": "*",
            "Condition":{
                "IpAddress": {
                    "acs:SourceIp": "42.120.XX.X/24"
                }
            }
        }]
    }
    ```


