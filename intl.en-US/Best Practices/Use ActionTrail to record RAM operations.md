# Use ActionTrail to record RAM operations {#concept_cbf_khk_xdb .concept}

This topic describes how to use ActionTrail to record the operations of an Alibaba Cloud account or a RAM user on resources.

## Prerequisite {#section_a5m_mf4_tgb .section}

RAM and ActionTrail have been integrated.

## Use ActionTrail to view RAM operations {#section_hyp_ll4_tgb .section}

1.  Log on to the [ActionTrail console](https://partners-intl.console.aliyun.com/#/actiontrail).
2.  On the **History Search** page, select **Username** from the **Filter** drop-down list.
3.  Enter the target user name, select an event type and time, and click **Search**.

    **Note:** You can also select **Event Name**, **Resource Type**, **Resource Name**, or **AccessKeyId** from the **Filter** drop-down list to search for relevant operations.

4.  Click the target event and click **View event**.

## Operations recorded by ActionTrail {#section_qkm_4f4_tgb .section}

ActionTrail can record the following RAM operations:

-   Logon information of an Alibaba Cloud account or a RAM user. For more information, see [ConsoleSignin event log examples](../../../../../reseller.en-US/User Guide/ActionTrail Event Examples/ConsoleSignin event log examples.md#).
-   Operations on the RAM console. The following is an example:

    ```language-json
    
    
    {
        "apiVersion":"2015-05-01",
        "eventId":"2cc52dee-d8d2-40c2-8de0-3a2cf1df07a0",
        "eventName":"DeleteGroup",
        "eventSource":"ram.aliyuncs.com",
        "eventTime":"2015-11-03T13:41:49Z",
        "eventType":"ApiCall",
        "eventVersion":"1",
        "requestId":"9AE24F49-C52C-4F0F-BCF9-9A4B8C22B147",
        "requestParameters":{
            "GroupName":"grp1",
        },
        "serviceName":"Ram",
        "sourceIpAddress":"42.120.74.90",
        "userAgent":"AliyunConsole",
        "userIdentity":{
            "type":"ram-user",
            "principalId":"274180646548292385",
            "accountId":"43274",
            "userName":"Alice",
            "sessionContext":{
                "sessionAttributes":{
                    "creationDate":"2015-11-03T13:41:48Z",
                    "mfaAuthenticated":"true"
                }
            }
        }
    }
    
    ```

-   RAM and STS API calls for resource creation, change, and deletion. The following is an example:

    ```language-json
    
    
    {
        "apiVersion": "2015-05-01",
        "eventId": "234ef3c7-8938-4bd7-bb80-11754b7bdd4c",
        "eventName": "CreateGroup",
        "eventSource": "ram.aliyuncs.com",
        "eventTime": "2016-01-04T08:58:50Z",
        "eventType": "ApiCall",
        "eventVersion": "1",
        "recipientAccountId": "43274",
        "requestId": "1485748C-DB62-4693-AB7E-4BA3F3A970E1",
        "requestParameters": {
            "Comments": "this is a test group",
            "GroupName": "grp1"
        },
        "serviceName": "Ram",
        "sourceIpAddress": "42.120.74.96",
        "userAgent": "aliyuncli/2.0.6",
        "userIdentity": {
            "type": "ram-user",
            "principalId": "274180646548292385",
            "accountId": "43274",
            "accessKeyId": "f6IzzFZMmzNwEI4d",
            "userName": "Alice"
        }
    }
    
    ```


## What to do next {#section_qqw_pf4_tgb .section}

For more information about operation records, see [ActionTrail event log syntax](../../../../../reseller.en-US/User Guide/ActionTrail event log syntax.md#).

