# Policy 基本元素 {#concept_xg5_51g_xdb .concept}

Policy 基本元素是权限策略的基本组成部分，RAM 中使用权限策略来描述授权的具体内容，掌握 Policy 基本元素的基本知识可以更合理的使用权限策略。

## Policy 基本元素 {#section_t2q_412_qgb .section}

使用权限策略之前需要了解 Policy 基本元素。

|元素名称|描述|
|:---|:-|
|效力（Effect）|授权效力包括两种：允许（Allow）和拒绝（Deny）。|
|操作（Action）|操作是指对具体资源的操作。|
|资源（Resource）|资源是指被授权的具体对象。|
|限制条件（Condition）|限制条件是指授权生效的限制条件。|

## Policy 元素使用规则 {#section_tgv_vc2_qgb .section}

-   **效力（Effect）**：

    取值 为 Allow 或 Deny，例如：`"Effect": "Allow"`。

-   **操作（Action）**：

    Action 支持多值，取值为云服务所定义的 API 操作名称。

    **说明：** 操作是指对具体资源的操作，多数情况下 Action 与云产品的 API 一一对应，但也有例外。各产品支持的 Action 列表请参阅各产品关于 RAM 授权的文档，您可以在[支持 RAM 的云服务](../../../../../intl.zh-CN/产品简介/支持 RAM 的云服务.md#)中查询相关文档的链接。

    格式：

    `<service-name>:<action-name>`。

    -   `service-name`: 阿里云产品名称。例如：ecs，rds，slb，oss，ots 等。
    -   `action-name: service`：相关的 API 操作接口名称。
    描述样例：

    `"Action": ["oss:ListBuckets", "ecs:Describe*", "rds:Describe*"]`

-   **资源（Resource）**

    Resource 通常指资源，即操作对象。

    格式：

    `acs:<service-name>:<region>:<account-id>:<relative-id>`。

    -   `acs`: Alibaba Cloud Service 的首字母缩写，表示阿里云的公有云平台。
    -   `service-name`: 阿里云产品名称。例如：ecs，rds，slb，oss，ots 等。
    -   `region`: 地域信息。如果不支持该项，可以使用通配符`*`来代替。
    -   `account-id`: 账号 ID。例如：`1234567890123456`，可以用`*`代替。
    -   `relative-id`: 与服务相关的资源描述部分，其语义由具体服务指定。这部分的格式支持树状结构（类似文件路径）。以 oss 为例，表示一个 OSS 对象的格式为：`relative-id = “mybucket/dir1/object1.jpg”` 。
    描述样例：

    `"Resource": ["acs:ecs:*:*:instance/inst-001", "acs:ecs:*:*:instance/inst-002", "acs:oss:*:*:mybucket", "acs:oss:*:*:mybucket/*"]`

-   **限制条件（Condition）**：

    条件块（Condition Block）由一个或多个条件子句构成。一个条件子句由条件操作类型、条件关键字和条件值组成。

    ![条件块判断逻辑](images/38714_zh-CN.png "条件块判断逻辑")

    逻辑说明：

    -   条件满足：一个条件关键字可以指定一个或多个值，在条件检查时，如果条件关键字的值与指定值中的某一个相同，即可判定条件满足。
    -   条件子句满足：同一条件操作类型的条件子句下，若有多个条件关键字，所有条件关键字必须同时满足，才能判定该条件子句满足。
    -   条件块满足：条件块下的所有条件子句同时满足的情况下，才能判定该条件块满足。
    **条件操作类型**

    条件操作类型包括：字符串类型（String）、数字类型（Numeric）、日期类型（Date and time）、布尔类型（Boolean）和 IP 地址类型（IP address）。

    |条件操作类型|支持类型|
    |:-----|:---|
    |字符串类型（String）|     -   StringEquals
    -   StringNotEquals
    -   StringEqualsIgnoreCase
    -   StringNotEqualsIgnoreCase
    -   StringLike
    -   StringNotLike
 |
    |数字类型（Numeric）|     -   NumericEquals
    -   NumericNotEquals
    -   NumericLessThan
    -   NumericLessThanEquals
    -   NumericGreaterThan
    -   NumericGreaterThanEquals
 |
    |日期类型（Date and time）|     -   DateEquals
    -   DateNotEquals
    -   DateLessThan
    -   DateLessThanEquals
    -   DateGreaterThan
    -   DateGreaterThanEquals
 |
    |布尔类型（Boolean）|Bool|
    |IP 地址类型（IP address）|     -   IpAddress
    -   NotIpAddress
 |

    **条件关键字**

    阿里云通用条件关键字命名格式：

    ```
    acs:<condition-key>
    ```

    阿里云产品级别条件关键字命名格式：

    ```
    <service-name>:<condition-key>
    ```

    |通用条件关键字|类型|说明|
    |:------|:-|:-|
    |`acs:CurrentTime`|Date and time|Web Server 接收到请求的时间。以 ISO 8601 格式表示，例如：`2012-11-11T23:59:59Z`。|
    |`acs:SecureTransport`|Boolean|发送请求是否使用了安全信道。例如：HTTPS。|
    |`acs:SourceIp`|IP address|发送请求时的客户端 IP 地址。|
    |`acs:MFAPresent`|Boolean|用户登录时是否使用了多因素认证。|

    |产品名称|条件关键字|类型|说明|
    |:---|:----|:-|:-|
    |ECS|`ecs:tag/<tag-key>`|String|ECS 资源的标签关键字，可自定义。|
    |RDS|`rds:ResourceTag/<tag-key>`|String|RDS 资源的标签关键字，可自定义。|
    |OSS|`oss:Delimiter`|String|OSS 对 Object 名字进行分组的分隔符。|
    |OSS|`oss:Prefix`|String|OSS Object 名称的前缀。|


## 权限策略样例 {#section_mnm_v1g_xdb .section}

以下权限策略的含义：允许对 OSS 的 samplebucket 进行只读操作，限制条件：请求者的 IP 来源为 42.160.1.0。

```

{
      "Version": "1",
      "Statement":
        [{
          "Effect": "Allow",
            "Action": ["oss:List*", "oss:Get*"],
            "Resource": ["acs:oss:*:*:samplebucket", "acs:oss:*:*:samplebucket/*"],
            "Condition":
             {
                "IpAddress":
                 {
                    "acs:SourceIp": "42.160.1.0"
                  }
              }
         }]
}
```

