# Policy syntax structure {#concept_srq_fbk_xdb .concept}

This article describes the syntax structure and rules of Authorization Policy in Ram, helps you understand and use it correctly. In everyday applications, you can quickly check out the following:, and in this article.

## Policy Structure {#section_xvl_gbk_xdb .section}

Authorization Policy \(policy\) structure includes policy The version number and the list of authorized statements. Each authorization statement includes the following elements: Effect \(authorization type\), Action \(action name list\), resource \(Action object list\), and Condition, where condition is optional.

Basic policy structure:

![](images/3625_en-US.png "Policy Structure")

## Format check \(JSON\) {#section_awl_gbk_xdb .section}

Ram only supports descriptions in JSON format. When creating or updating a policy, RAM will first check that the JSON format is correct.

-   For information on JSON syntax standards, refer to \[RFC 7159\].
-   You can also use some online JSON format validators and editors to verify the validity of the JSON text.

## Policy syntax {#section_cwl_gbk_xdb .section}

Understanding the characters and rules used in policy, and Policy The syntax description.

**Characters and rules**

The JSON characters contained in policy are: \{\} \[\] ", :; The special characters used in the description syntax are: = <\> \(\) |.

Instructions for use:

-   When an element allows multiple values, it is expressed using a comma and ellipsis, such: \[<action\_string\>, <action\_string\>, ...\]. All syntaxes that support multiple values, also allow single values. And the two expressions are equivalent: "action ": \[<Action\_string\>\] and "action ": <Action\_string\>
-   An element with a question mark indicates that this is an optional element, such as: <condition \_block? \>
-   When multiple values are separated by a vertical bar \(|\), this indicates that only one of the values can be selected. For example: \("allow" | "deny "\)
-   An element enclosed with double quotes indicate a text string. For example: <version \_block\> = "version ": \("1 "\)

**Grammar description and description**

Policy The syntax is described below:

```
Policy = {
                    <Version _block>,
                    <Wollongong _block>
}
<Version _block> = "version": ("1 ")
<Direct_block> = "statement": [<Statement>, <Statement>,...]
<Statement> = { 
<Glast_block>,
<Action_block>,
<Think_block>,
<Condition _block? >
}
<Glast_block> = "effect": ("allow" | "deny ")  
<Action_block> = ("action" | "notaction "): 
("*" | [<Action_string>, <action_string>,...])
<Think_block> = ("resource" | "notresource "): 
("*" | [<Think_string>, <think_string>,...])
<Condition _block> = "condition": <condition _map>
<Condition _map> = {
<Maid> :{ 
<Condition_key_string>: <condition_value_list>,
<Condition_key_string>: <condition_value_list>,
...
},
<Maid> :{
<Condition_key_string>: <condition_value_list>,
<Condition_key_string>: <condition_value_list>,
...
}, ...
}  
<Condition_value_list> = [<condition _value>, <condition _value>,...]
<Condition _value> = ("string" | "Number" | "Boolean ")
```

The syntax is described below:

-   Version: The currently supported version of policy is 1.
-   Authorization statement: A policy can have multiple authorization statements.
    -   \* Each authorization statement can be either Deny or Allow. In an authorization statement, action is a list that supports multiple operations, Resource It is also a list that supports multiple objects.
    -   Each authorization Statement supports separate conditions \). A condition block supports multiple condition operation types and logical combinations of these conditions.
-   Deny priority: a user can be granted multiple policies, follow these policies when there are multiple authorization statements that contain both allow and deny Deny first \(only deny does not recognize allow\) principle.
-   Element value:
    -   When the value is a number or Boolean, it is similar to a string, need to be caused by double quotation marks.
    -   Supports \(\*\) and \(?\) When element values are string values \(?\) Fuzzy Matching.

        -   \(\*\) Represents 0 or more arbitrary English letters.
        -   \(?\) Represents 1 arbitrary Letter of English.
        For example, "ecs:Describe\*" indicates all ECS API operation names starting with 'Describe'. Operation name.


## The policy element uses {#section_uwl_gbk_xdb .section}

Understand the rules for the use of each element in the policy syntax.

**\#\#\# Effect \(authorization type\)**

The Effect value is either Allow or Deny. For example, "effect": "allow"

**\#\#\# Action \(operation name list\)**

Action supports multiple values, which is defined by the API operation name defined by the cloud service, and is defined in the following format:

```
<Service-Name>: <action-Name>
```

Description:

-   \* service-name: This indicates the name of an Alibaba Cloud product, such as ECS, RDS, Server Load Balancer, OSS, and Table Store.
-   action-name: name of service-related action interfaces.

Description example:

```
"Action": ["Oss: listshoes", "ECs: Describe *", "RDS: Describe *"]
```

## \#\#\# Resource \(list of operation objects\) {#section_axl_gbk_xdb .section}

Resource usually refers to an operational object, such as ECS. Virtual Machine instance, OSS Store objects. Alibaba Cloud service resource names are formatted as follow:

```
ACS: <service-Name>: <region>: <account-ID>: <relative-ID>
```

Description:

-   \* acs: This is the abbreviation of Aliyun Cloud Service, indicating an Alibaba Cloud public cloud platform.
-   \* service-name: This indicates the name of an open service provided by Alibaba Cloud, such as ECS, OSS, or Table Store.
-   \* region: This indicates region information. If this option is not supported, use the wildcard "\*" instead.
-   Account-ID: account ID, such 1234567890123456 can also be replaced.
-   \* relative-id: This indicates the service-related resource. Its meaning is specified by the specific service. Specifies. This part of the format description supports a tree structure similar to the file path. In the case of OSS, relative-id = "Mybucket/dir1/object1.jpg" represents an OSS object.

Description example:

```
"Resource": ["ACS: ECs: *: instance/inst-001 ", "ACS: ECs: *: instance/inst-002", "ACS: OSS: *: mybucket "," ACS: OSS :*:*: mybucket/* "]
```

**\#\#\# Condition \(condition restrictions\)**

Condition block \(Condition Block\) consists of one or more conditional clauses. A condition clause consists of an action type, keyword, and condition value. The action type and keyword are to be elaborated in the following sections.

**Conditional block judgment Logic**

The following figure shows the criteria for determining whether a condition is met.

![](images/3626_en-US.png "Are the judgment principles that meet the conditions?")

The specific rules are as follows:

-   One condition keyword corresponds to one or more values. When conditions are checked, if the condition keyword value is equal to one of the corresponding values, the condition is considered satisfied.
-   A condition clause is considered satisfied only if multiple condition keywords of the condition clause of the same condition action type are all satisfied.
-   A condition block is satisfied only if all its condition clauses are satisfied.

**Condition action type**

Supports the following conditions: string type, numeric type\), date type \(data and Time, Boolean, and IP address type \(IP address \).

These condition action types support the following methods, respectively:

|String|Numeric|Date and time|Boolean|IP address|
|:-----|:------|:------------|:------|:---------|
|Stringequals|Numericequals|Dateequals|bool|IPaddress|
|Stringnotes|Numericnotequals|Datenotequals|-|Notipaddress|
|Stringequalsignorecase|Numericlessthan|Datelessthan|-|-|
|Stringnotequalsignorecase|Numericlessthanequals|Datelessthanequals|-|-|
|Stringlike|Numericgreaterthan|Dategreaterthan|-|-|
|Stringnotlike|Numericgreaterthanequals|Dategreaterthanequals|-|-|

**Conditions keyword \(Condition-key\)**

The condition keywords reserved by Alibaba Cloud adopt the following naming format:

```
ACS: <condition-key>
```

The common condition keywords reserved by the Ali Cloud Service are as follows:

|General Condition keyword|Type|Description|
|:------------------------|:---|:----------|
|`acs: CurrentTime`|Date and time|The time that the Web server received the request in ISO 8601 format, such `2012-11-11T23: 59: 59Z`|
|`acs: SecureTransport`|Boolean|Whether the request is sent over a secure channel, such as via HTTPS.|
|`acs: SourceIp`|IP address|The IP address of the console sending the request.|
|`ACS: mfapresent`|Boolean|Whether multi-factor authentication is used during user login \(two-step authentication\)|

Some products define product-level condition keywords, in the following format:

```
<Service-Name>: <condition-key>
```

Some cloud products define conditional keywords as follows:

|Product Name|Conditional keyword|Type|Description:|
|:-----------|:------------------|:---|:-----------|
|ECS|`ECS: tag/<tag-key>`|String|Tag keywords for ECs resources that can be customized by the user|
|RDS|`RDS: thinktag/<tag-key>`|String|Tag keyword for the RDS resource that can be customized by the user|
|OSS|`OSS: impressioniter`|String|The separator that the OSS groups object names|
| |`OSS: prefix`|String|Prefix of the OSS Object Name|

## Policy sample {#section_wxl_gbk_xdb .section}

The policy below contains two authorization statements.

-   1st authorization statements are allowed on Region East 1 \(Hangzhou\) All ECs Resources have permission to view \(ECS: Describe \*\);
-   2nd authorization statement is to allow read access to objects in the mybucket bucket of OSS \(OSS: listObjects, OSS: GetObject\), and limits the IP of the requestor Source must be 42.120.88.10 or 42.120.66.0/24.

```
{
    Version: "1 ",
    "Statement ":[
        {
            "Effect": "allow ",
            "Action": "ECs: Describe *",
            "Resource": "ACS: ECs: CN-Hangzhou :*:*"
        },
        {
            "Effect": "allow ",
            "Action ":[
                "Oss: maid ",
                "Oss: GetObject"
            ],
            "Resource ":[
                "ACS: OSS: *: mybucket ",
                "ACS: OSS: *: mybucket /*"
            ],
            "Condition ":{
                "IPaddress ":{
                    "ACS: sourceip": ["maid", "maid/24"]
                }
            }
        }
    ]
}
```

