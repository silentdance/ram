# Policy structure and syntax {#concept_srq_fbk_xdb .concept}

This topic describes the structure, syntax, and rules of policies used in Alibaba Cloud RAM.

## Policy structure {#section_xvl_gbk_xdb .section}

The policy structure includes the version number and a list of statements.

Each statement contains the following elements: effect, action, resource, and condition. The condition element is optional.

![Policy structure](images/14403_en-US.png "Policy structure")

## Before using a policy syntax {#section_qmk_mb4_tgb .section}

Before using the syntax of a policy, you need to understand its characters and rules.

-   Policy characters:
    -   The JSON characters in a policy include `{ } [ ] " , :`.
    -   The special characters used to describe the syntax of a policy include `= < > ( ) |`.
-   Rules for using the policy characters:
    -   If an element requires multiple values, a comma \(,\) is used as the delimiter to separate each value, and an ellipses \(...\) is used to describe the remaining values. For example, `[ <action_string>, <action_string>, ...]`.

        **Note:** Elements that support multiple values also support single values. This means that the two descriptions `"Action": [<action_string>]` and `"Action": <action_string>` are equivalent.

    -   An element with a question mark \(?\) in the syntax indicates that it is an optional element, for example, `<condition_block?>`.
    -   If multiple values are separated by vertical bars \(`|`\) in the syntax, only one of the values can be selected, for example, `("Allow" | "Deny")`.
    -   An element enclosed with double quotation marks \(""\) is a text string, for example, `<version_block> = "Version" : ("1")`.

## Policy syntax {#section_cwl_gbk_xdb .section}

An example of the syntax of a policy is as follows:

```
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

-   Version: The current policy version is 1.
-   Statement: A policy can have multiple statements.
    -   Each statement can be either `Allow` or `Deny`.

        **Note:** In a statement, both the action and resource elements can have multiple values.

    -   Each statement supports its own conditions.

        **Note:** A condition block can contain multiple conditions with different operation types and logical combinations of these conditions.

-   Deny takes effect: You can grant multiple polices to a user. If these polices contain both `Allow` and `Deny` statements, `Deny` takes priority \(that is, the `Deny` statements overwrite the `Allow` statements\).
-   Element value:
    -   If an element value is a number or Boolean, it must be enclosed using double quotation marks \(""\) such as strings.
    -   If an element value is a string, characters such as the asterisk \(`*`\) and question mark \(`?`\) can be used for fuzzy matching.
        -   The asterisk \(`*`\) indicates any number \(including zero\) of allowed characters.

            **Note:** For example, `ecs:Describe*` indicates all ECS actions starting with 'Describe'.

        -   The question mark \(`?`\) indicates one allowed character.

## Policy format check {#section_awl_gbk_xdb .section}

RAM policies must be expressed in JSON format. When you create or update a policy, RAM first checks whether the JSON format is correct.

-   For more information about the JSON syntax standards, see [RFC 7159](http://tools.ietf.org/html/rfc7159).
-   We recommend that you use tools such as JSON validators and editors to verify your policies to meet JSON syntax standards.

