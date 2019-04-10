# Policy 语法结构 {#concept_srq_fbk_xdb .concept}

本文介绍 RAM 中授权策略的语法结构和规则，帮助您正确理解 Policy 语法，以完成创建或更新授权策略。

## Policy 结构 {#section_xvl_gbk_xdb .section}

Policy 结构包括：版本号及授权语句（Statement）列表。

每条授权语句包括：Effect（授权效力）、Action（操作列表）、Resource（资源列表）以及 Condition（限制条件），其中限制条件是可选项。

![Policy 结构](images/14403_zh-CN.png "Policy 结构")

## 运用 Policy 语法的前提条件 {#section_qmk_mb4_tgb .section}

运用 Policy 语法前，首先应了解 Policy 字符及其使用规则。

-   Policy 字符：
    -   Policy 中所包含的 JSON 字符：`{ } [ ] " , :`。
    -   描述语法使用的特殊字符：`= < > ( ) |`。
-   Policy 字符使用规则：
    -   当一个元素允许多值时，使用逗号和省略号来表达。例如：`[ <action_string>, <action_string>, ...]`。

        **说明：** 在所有支持多值的元素中，使用单值进行表达也是有效的，且两种表达方式效果相同。例如：`"Action": [<action_string>]` 和 `"Action": <action_string>`

    -   元素带有问号表示此元素是一个可选元素。例如：`<condition_block?>`。
    -   多值之间用竖线 `|`隔开，表示取值只能选取这些值中的某一个。例如：`("Allow" | "Deny")`。
    -   使用双引号的元素，表示此元素是文本串。例如： `<version_block> = "Version" : ("1")`。

## Policy 语法 {#section_cwl_gbk_xdb .section}

Policy 语法描述如下：

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

Policy 语法说明：

-   版本：当前支持的 Policy 版本为 1。
-   授权语句：一个 Policy 可以有多条授权语句。
    -   每条授权语句的效力是`Allow`或`Deny` 。

        **说明：** 一条授权语句中，Action（操作）和 Resource（资源）都支持多值。

    -   每条授权语句都支持独立的限制条件（Condition）。

        **说明：** 一个条件块可以支持多种条件操作类型，以及多种条件的逻辑组合。

-   Deny 优先原则： 一个用户可以被授予多个授权策略，当这些授权策略同时包含`Allow`和 `Deny`时，遵循 Deny 优先原则。
-   元素取值：
    -   当取值为数字（Number）或布尔值（Boolean）时，与字符串类似，需要使用双引号。
    -   当元素取值为字符串值（String）时，支持使用`*`和`?`进行模糊匹配。
        -   `*`代表 0 个或多个任意的英文字母。

            **说明：** 例如：`ecs:Describe*` 表示 ecs 的所有以 Describe 开头的 action。

        -   `?`代表 1 个任意的英文字母。

## Policy 格式检查 {#section_awl_gbk_xdb .section}

RAM 仅支持 JSON 格式。当创建或更新授权策略时，RAM 会首先检查 JSON 格式的正确性。

-   关于 JSON 的语法标准请参考 [RFC 7159](http://tools.ietf.org/html/rfc7159)。
-   您也可以使用一些在线的 JSON 格式验证器和编辑器来校验 JSON 文本的有效性。

## Policy 样例 {#section_okd_31f_xgb .section}

如下所示的 Policy 样例中，包含两条授权语句（Statement）：

-   第 1 条授权语句：允许对华东 1（杭州）地域的所有 ecs 资源授予查看权限`ecs:Describe*`。
-   第 2 条授权语句：允许对 oss 的 mybucket 存储桶中的对象授予只读访问权限`oss:ListObjects`和`oss:GetObject`，并限制请求者的 IP 来源必须是`42.120.88.10`或`42.120.66.0/24`。

```
{
    "Version": "1",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "ecs:Describe*",
            "Resource": "acs:ecs:cn-hangzhou:*:*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "oss:ListObjects",
                "oss:GetObject"
            ],
            "Resource": [
                "acs:oss:*:*:mybucket",
                "acs:oss:*:*:mybucket/*"
            ],
            "Condition":{
                "IpAddress": {
                    "acs:SourceIp": ["42.120.88.10", "42.120.66.0/24"]
                }
            }
        }
    ]
}
```

