# 通过ActionTrail查看RAM的操作记录 {#task_cbf_khk_xdb .task}

ActionTrail可以记录主账号或RAM用户进行的操作，通过ActionTrail可以查看所有用户对资源实例进行操作的记录。

进行操作前，请确保您已经注册了阿里云账号。如还未注册，请先完成[账号注册](https://account.aliyun.com/register/register.htm)。

## 通过ActionTrail控制台查看事件 {#section_hyp_ll4_tgb .section}

1.  登录[操作审计控制台](https://actiontrail.console.aliyun.com)。
2.  在**历史事件查询**页签下，使用**过滤器**进行搜索。
3.  输入相关的用户名，选择**事件类型**和**时间**后，单击**搜索**。 

    **说明：** 您也可以通过**事件名称**、**资源类型**、**资源名称**以及**AccessKeyId**等进行搜索。

4.  找到目标事件，单击**+**。
5.  单击**查看事件**。

## ActionTrail记录的操作 {#section_qkm_4f4_tgb .section}

ActionTrail可以记录RAM的以下操作信息，关于操作记录的详细信息，请参见[操作事件结构定义](../../../../cn.zh-CN/历史事件管理/操作事件结构定义.md#)。

-   主账号或RAM用户的登录信息，详情请参见[ConsoleSignin](../../../../cn.zh-CN/历史事件管理/操作事件示例/ConsoleSignin.md#)。
-   RAM控制台的操作，例如：

    ``` {#codeblock_sm6_6f2_rci .language-json}
    {
        "apiVersion":"2015-05-01",
        "eventId":"2cc52dee-d8d2-40c2-8de0-3a2cf1df****",
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
        "sourceIpAddress":"42.120.XX.XX",
        "userAgent":"AliyunConsole",
        "userIdentity":{
            "type":"ram-user",
            "principalId":"27418064654829****",
            "accountId":"123456789012****",
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

-   RAM/STS的所有创建、变更、删除类API调用信息，例如：

    ``` {#codeblock_ptd_6m4_yow .language-json}
    {
        "apiVersion": "2015-05-01",
        "eventId": "234ef3c7-8938-4bd7-bb80-11754b7b****",
        "eventName": "CreateGroup",
        "eventSource": "ram.aliyuncs.com",
        "eventTime": "2016-01-04T08:58:50Z",
        "eventType": "ApiCall",
        "eventVersion": "1",
        "recipientAccountId": "4****",
        "requestId": "1485748C-DB62-4693-AB7E-4BA3F3A970E1",
        "requestParameters": {
            "Comments": "this is a test group",
            "GroupName": "grp1"
        },
        "serviceName": "Ram",
        "sourceIpAddress": "42.120.XX.XX",
        "userAgent": "aliyuncli/2.0.6",
        "userIdentity": {
            "type": "ram-user",
            "principalId": "27418064654829****",
            "accountId": "4****",
            "accessKeyId": "f6Iz********EI4d",
            "userName": "Alice"
        }
    }                        
    ```


