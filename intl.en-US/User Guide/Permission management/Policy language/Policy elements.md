# Policy elements {#concept_xg5_51g_xdb .concept}

This topic describes the elements of policies that are used in Alibaba Cloud RAM to define a permission.

## Elements {#section_t2q_412_qgb .section}

The following table describes the policy elements.

|Element|Description|
|:------|:----------|
|Effect|Effect can be either Allow or Deny.|
|Action|Actions are operations performed on specific resources.|
|Resource|Resources are the objects being authorized.|
|Condition|Conditions are the circumstances under which a permission takes effect.|

## How to use a policy element {#section_tgv_vc2_qgb .section}

-   **Effect**

    The value can be either 'Allow' or 'Deny', for example, `"Effect": "Allow"`.

-   **Action**

    Action can have multiple values. The values are API operations defined by the target cloud services.

    **Note:** Actions are operations performed on specific resources. In most cases, an action corresponds to an Alibaba Cloud API. For more information about the actions supported by different Alibaba Cloud products, see [Alibaba Cloud services that work with RAM](../../../../../reseller.en-US/Product Introduction/Alibaba Cloud services that work with RAM.md#).

    Format:

    `<service-name>:<action-name>`

    -   `service-name`: name of an Alibaba Cloud product, such as ecs, rds, slb, oss, and ots.
    -   `action-name: service`: name of a relevant API.
    Example:

    `"Action": ["oss:ListBuckets", "ecs:Describe*", "rds:Describe*"]`

-   **Resource**

    Resource generally specifies the object of operations.

    Format:

    `acs:<service-name>:<region>:<account-id>:<relative-id>`

    -   `acs`: abbreviation of Alibaba Cloud Service, indicating the Alibaba Cloud public cloud platform.
    -   `service-name`: name of a service provided by Alibaba Cloud, such as ecs, rds, slb, oss, and ots.
    -   `region`: region information. If this option is not supported by the service, use an asterisk \(`*`\).
    -   `account-id`: account ID, such as `1234567890123456`. If no ID is required or available, it can be replaced with an asterisk \(`*`\).
    -   `relative-id`: service-related resource description. Its meaning is specified by a specific service. `relative-id` is similar to a file path. For example, `relative-id = "mybucket/dir1/object1.jpg"` indicates an OSS object.
    Example:

    `"Resource": ["acs:ecs:*:*:instance/inst-001", "acs:ecs:*:*:instance/inst-002", "acs:oss:*:*:mybucket", "acs:oss:*:*:mybucket/*"]`

-   **Condition**

    A condition block consists of one or more condition clauses. A condition clause consists of an operation type, a keyword, and a condition value.

    ![Logic for determining whether a condition is satisfied](images/38714_en-US.png "Logic for determining whether a condition is satisfied")

    The details are as follows:

    -   For each condition keyword, one or more condition values can be specified. When conditions are evaluated, if the runtime value of the condition keyword matches any of the corresponding values, the condition is satisfied.
    -   A condition clause is satisfied only if multiple conditions of the same condition operation type are all satisfied.
    -   A condition block is satisfied only if all of its condition clauses are satisfied.
    **Condition operation type**

    The following types of condition operations are supported: string, numeric, date and time, Boolean, and IP address.

    |Operation type|Supported type|
    |:-------------|:-------------|
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

    **Condition keyword**

    The common condition keywords reserved by Alibaba Cloud services use the following naming format:

    ```
    acs:<condition-key>
    ```

    The product-related condition keywords reserved by Alibaba Cloud services use the following naming format:

    ```
    <service-name>:<condition-key>
    ```

    |Common condition keyword|Type|Description|
    |:-----------------------|:---|:----------|
    |`acs:CurrentTime`|Date and time|Time when the Web server receives a request. This keyword is defined in ISO 8601 format, for example, `2012-11-11T23:59:59Z`.|
    |`acs:SecureTransport`|Boolean|Indicates whether a secure channel, such as HTTPS, is used to send a request.|
    |`acs:SourceIp`|IP address|IP address of the client that sends a request.|
    |`acs:MFAPresent`|Boolean|Indicates whether multi-factor authentication is used during user logon.|

    |Product|Condition keyword|Type|Description|
    |:------|:----------------|:---|:----------|
    |ECS|`ecs:tag/<tag-key>`|String|Tag keyword for ECS resources. This keyword can be customized by users.|
    |RDS|`rds:ResourceTag/<tag-key>`|String|Tag keyword for RDS resources. This keyword can be customized by users.|
    |OSS|`oss:Delimiter`|String|Separator used by OSS to group the object names.|
    |OSS|`oss:Prefix`|String|Prefix of an OSS object name.|


## Policy example {#section_mnm_v1g_xdb .section}

In the following policy example, read-only permissions for the OSS resource SampleBucket are allowed on condition that the source IP address of the requester is 42.160.1.0.

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

