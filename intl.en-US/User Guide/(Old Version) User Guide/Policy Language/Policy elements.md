# Policy elements {#concept_xg5_51g_xdb .concept}

This topic describes the elements of policies that are used in Alibaba Cloud Resource Access Management \(RAM\) to define a permission.

## Elements {#section_t2q_412_qgb .section}

|Element|Description|
|:------|:----------|
|Effect| Specifies whether the statement results in an allow or an explicit deny.

 Valid values: `Allow` | `Deny`

 |
|Action|Describes the specific API action or actions that will be allowed or denied.|
|Resource|Specifies the object or objects that the statement covers.|
|Condition|Specifies when a policy takes effect.|

## How to use a policy element {#section_tgv_vc2_qgb .section}

-   Effect

    Example: `"Effect": "Allow"`

-   Action

    **Note:** In most cases, each Alibaba Cloud service has its own set of API actions. For more information, see [Alibaba Cloud services that work with RAM](../../../../reseller.en-US/Product Introduction/Alibaba Cloud services that work with RAM.md#).

    Format: `<service-name>:<action-name>`

    -   `service-name`: the name of an Alibaba Cloud service, such as ecs, rds, slb, oss, and ots
    -   `action-name: service`: the name of a relevant API action
    Example: `"Action": ["oss:ListBuckets", "ecs:Describe*", "rds:Describe*"]`

-   Resource

    Format: `acs:<service-name>:<region>:<account-id>:<relative-id>`

    -   `acs`: the abbreviation of Alibaba Cloud Service
    -   `service-name`: the name of an Alibaba Cloud service, such as ecs, rds, slb, oss, and ots
    -   `region`: the region information. If this element is not supported, use an asterisk \(`*`\).
    -   `account-id`: the Alibaba Cloud account ID, such as `123456789012****`. If no ID is required or available, it can be replaced with an asterisk \(`*`\).
    -   `relative-id`: service-related resource description. Its meaning is specified by a specific Alibaba Cloud service. The `relative-id` element is similar to a file path. For example, `relative-id = "mybucket/dir1/object1.jpg"` indicates an OSS object.
    Example: `"Resource": ["acs:ecs:*:*:instance/inst-001", "acs:ecs:*:*:instance/inst-002", "acs:oss:*:*:mybucket", "acs:oss:*:*:mybucket/*"]`

-   Condition

    A condition block can contain multiple conditions, and each condition can contain multiple key-value pairs.

    ![](images/38714_en-US.png "Condition block")

    -   Unless otherwise specified, all keys can have multiple values. When conditions are evaluated, if the condition value matches any of the corresponding values, the condition is satisfied.
    -   A condition is satisfied only if multiple conditions of the same action type are all satisfied.
    -   A condition block is satisfied only if all of its conditions are satisfied.
    Action type

    The following types of actions are supported: string, numeric, date and time, Boolean, and IP address.

    |Action type|Supported type|
    |:----------|:-------------|
    |String|     -   StringEquals
    -   StringNotEquals
    -   StringEqualsIgnoreCase
    -   StringNotEqualsIgnoreCase
    -   StringLike
    -   StringNotLike
 |
    |Numeric|     -   NumericEquals
    -   NumericNotEquals
    -   NumericLessThan
    -   NumericLessThanEquals
    -   NumericGreaterThan
    -   NumericGreaterThanEquals
 |
    |Date and time|     -   DateEquals
    -   DateNotEquals
    -   DateLessThan
    -   DateLessThanEquals
    -   DateGreaterThan
    -   DateGreaterThanEquals
 |
    |Boolean|Bool|
    |IP address|     -   IpAddress
    -   NotIpAddress
 |

    Condition key

    -   The format of common condition keys is as follows:

        ``` {#codeblock_fvr_7e3_rf5}
        acs:<condition-key>
        ```

        |Condition key|Type|Description|
        |:------------|:---|:----------|
        |`acs:CurrentTime`|Date and time|The date and time when the web server receives a request. This key is defined in ISO 8601 format, for example, `2012-11-11T23:59:59Z`.|
        |`acs:SecureTransport`|Boolean|Indicates whether a secure channel, such as HTTPS, is used to send a request.|
        |`acs:SourceIp`|IP address|The IP address of the client that sends a request.|
        |`acs:MFAPresent`|Boolean|Indicates whether multi-factor authentication \(MFA\) is used during user logon.|

    -   The format of Alibaba Cloud service-related condition keys is as follows:

        ``` {#codeblock_htp_y2s_g4h}
        <service-name>:<condition-key>
        ```

        |Condition key|Alibaba Cloud service|Type|Description|
        |:------------|---------------------|:---|:----------|
        |`ecs:tag/<tag-key>`|ECS|String|The tag-key pair for ECS. This key can be customized.|
        |`rds:ResourceTag/<tag-key>`|RDS|String|The tag-key pair for RDS. This key can be customized.|
        |`oss:Delimiter`|OSS|String|The separator used by OSS to group object names.|
        |`oss:Prefix`|OSS|String|The prefix of an OSS object name.|


## Policy example {#section_0pf_q9t_4vg .section}

The following policy specifies that read-only operations on the OSS bucket samplebucket are allowed on the condition that the source IP address of the requester is 10.0.0.0/8.

``` {#codeblock_vg4_shc_zbt}






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
                    "acs:SourceIp": "10.0.0.0/8"
                  }
              }
         }]
}
```

