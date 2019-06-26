# Policy structure and grammar {#concept_srq_fbk_xdb .concept}

This topic describes the structure and grammar used to create or update policies in Alibaba Cloud Resource Access Management \(RAM\).

## Conventions used in a policy grammar {#section_wev_5eu_i9a .section}

The conventions used in a policy grammar are as follows:

-   Characters in a policy:
    -   The following characters are JSON tokens and are included in policies:

         `{ } [ ] " , :` 

    -   The following characters are special characters in the grammar and are not included in policies:

         `= < > ( ) |` 

-   Use of characters:
    -   If an element allows multiple values, you can:
        -   Use a comma \(,\) as the delimiter to separate each value, and an ellipses \(...\) to describe the remaining values. For example, `[ <action_string>, <action_string>, ...]`.
        -   Include only one value, for example, `"Action": [<action_string>]` and `"Action": <action_string>`.
    -   A question mark \(?\) following an element indicates that the element is optional, for example, `<condition_block?>`.
    -   A vertical bar \(|\) between elements indicates alternatives, for example, `("Allow" | "Deny")`.
    -   Elements that must be text strings are enclosed in double quotation marks \(""\), for example, `<version_block> = "Version" : ("1")`.

## Policy structure {#section_xvl_gbk_xdb .section}

The policy structure includes the version number and a list of statements.

Each statement contains the following elements: effect, action, resource, and condition. The condition element is optional.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23770/156152314514403_en-US.png)

## Policy grammar {#section_cwl_gbk_xdb .section}

``` {#codeblock_w9r_1s5_hpj}
policy  = {
     <version_block>,
     <statement_block>
}
<version_block> = "Version" : ("1")
<statement_block> = "Statement" : [ <statement>, <statement>, ... ]
<statement> = { 
    <effect_block>,
    <action_block>,
    <resource_block>,
    <condition_block?>
}
<effect_block> = "Effect" : ("Allow" | "Deny")  
<action_block> = ("Action" | "NotAction") : 
    ("*" | [<action_string>, <action_string>, ...])
<resource_block> = ("Resource" | "NotResource") : 
    ("*" | [<resource_string>, <resource_string>, ...])
<condition_block> = "Condition" : <condition_map>
<condition_map> = {
  <condition_type_string> : { 
      <condition_key_string> : <condition_value_list>,
      <condition_key_string> : <condition_value_list>,
      ...
  },
  <condition_type_string> : {
      <condition_key_string> : <condition_value_list>,
      <condition_key_string> : <condition_value_list>,
      ...
  }, ...
}  
<condition_value_list> = [<condition_value>, <condition_value>, ...]
<condition_value> = ("String" | "Number" | "Boolean")
```

Description:

-   The current policy version is 1.
-   The policy can have multiple statements.
    -   Each statement can be either `Allow` or `Deny`.

        **Note:** In a statement, both the action and resource elements can have multiple values.

    -   Each statement supports its own conditions.

        **Note:** A condition block can contain multiple conditions with different action types and logical combinations of these conditions.

-   You can attach multiple policies to a RAM user. If policies that apply to a request include an `Allow` statement and a `Deny` statement, the `Deny` statement trumps the `Allow` statement.
-   Element value:
    -   If an element value is a number or Boolean, it must be enclosed by using double quotation marks \(""\) such as strings.
    -   If an element value is a string, characters such as the asterisk \(`*`\) and question mark \(`?`\) can be used for fuzzy matching.
        -   The asterisk \(`*`\) indicates any number \(including zero\) of allowed characters. For example, `ecs:Describe*` indicates all ECS actions starting with `Describe`.
        -   The question mark \(`?`\) indicates one allowed character.

## Policy format check {#section_awl_gbk_xdb .section}

Policies are stored in RAM as JSON documents. When you create or update a policy, RAM first checks whether the JSON format is correct

-   For more information about the JSON grammar standards, see [RFC 7159](http://tools.ietf.org/html/rfc7159).
-   We recommend that you use tools such as JSON validators and editors to verify your policies to meet JSON grammar standards.

