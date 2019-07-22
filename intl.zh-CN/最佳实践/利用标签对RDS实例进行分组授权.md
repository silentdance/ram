# 利用标签对RDS实例进行分组授权 {#concept_msq_pmm_qfb .concept}

本文介绍了如何利用标签对RDS实例进行分组并授权，以满足RAM用户只能查看和操作被授权资源的需求。

## 前提条件 {#section_73h_tsp_9t8 .section}

请确保您已经注册了阿里云账号。如还未注册，请先完成账号注册。详情请参见[账号注册](https://account.alibabacloud.com/register/intl_register.htm)。

## 背景信息 {#section_lsl_wq5_qgb .section}

假设您的账号购买了10个RDS实例，其中5个想要授权给dev团队，另外5个授权给ops团队。企业希望每个团队只能查看被授权的实例，未被授权的不允许查看。

## 利用标签对RDS分组授权的操作步骤 {#section_jqp_tmm_qfb .section}

具体操作步骤请参见[利用标签对ECS实例进行分组授权](intl.zh-CN/最佳实践/利用标签对ECS实例进行分组授权.md#)。

RDS相关自定义策略：

``` {#codeblock_7py_5qt_3kd .language-json}
{
  "Statement": [
    {
      "Action": "rds:*",
      "Effect": "Allow",
      "Resource": "*",
      "Condition": {
        "StringEquals": {
          "rds:ResourceTag/team": "dev"
         }
       }
     },
    {
       "Action": "rds:DescribeTag*",
       "Effect": "Allow",
       "Resource": "*"
     }
  ],
  "Version": "1"
}
```

权限策略内容分为两部分：

-   其中带有`Condition`的`"Action": "rds:*"`部分用于过滤标签为`"team": "dev"`的资源。`Condition`部分的关键字为`rds:ResourceTag`。
-   `"Action": "rds:DescribeTag*"`用于展示所有标签。当RAM用户在操作**RDS控制台**时，系统展示出所有标签供RAM用户选择，只有当RAM用户选择了标签值后，系统才能根据选中的标签值过滤相应资源。

## 更多信息 {#section_csr_3hn_tgb .section}

利用标签对RDS实例分组授权后，如果遇到RAM用户登录控制台报无权限的问题，请参见[利用标签对RDS实例分组授权的常见问题](../../../../intl.zh-CN/常见问题/利用标签对RDS实例分组授权的常见问题.md#)。

