# 使用 ActionTrail 记录 RAM 操作 {#concept_cbf_khk_xdb .concept}

ActionTrail 可以记录主账号或 RAM 用户进行的操作，通过 ActionTrail 可以查看所有用户对资源实例进行操作的记录。

## 前提条件 {#section_a5m_mf4_tgb .section}

RAM 已经与 ActionTrail 服务进行了集成，可以联合使用。

## 使用 ActionTrail 查看 RAM 操作记录的步骤 {#section_hyp_ll4_tgb .section}

1.  登录 [ActionTrail 控制台](https://actiontrail.console.aliyun.com)。
2.  在**历史事件查询**页签下，使用**过滤器**进行搜索。
3.  输入相关的用户名，选择**事件类型**和**时间**后，单击**搜索**。

    **说明：** 您也可以通过**事件名称**、**资源类型**、**资源名称**、**AccessKeyId**等进行搜索。

4.  单击需要查看的事件，单击**查看事件**。

## ActionTrail 记录的操作 {#section_qkm_4f4_tgb .section}

ActionTrail 可以记录 RAM 的如下操作信息：

-   主账号或 RAM 用户的登录信息，详情请参考 [ConsoleSignin](../../../../../intl.zh-CN/用户指南/操作事件(Event)样例/ConsoleSignin.md#)。
-   RAM 控制台的操作，例如：

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

-   RAM/STS 的所有创建、变更、删除类 API 调用信息，例如：

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


## 更多信息 {#section_qqw_pf4_tgb .section}

关于操作记录的详细信息，请参考[操作事件\(Event\)结构定义](../../../../../intl.zh-CN/用户指南/操作事件(Event)结构定义.md#)。

