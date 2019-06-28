# Policy 样例 {#concept_jxs_x2h_tgb .concept}

本文介绍了解 Policy 基本元素、结构及语法后，如何创建 Policy 样例。

如下所示的 Policy 样例中，包含两条授权语句（Statement）：

-   第 1 条授权语句：允许对华东 1（杭州）地域的所有 ecs 资源授予查看权限`ecs:Describe*`。
-   第 2 条授权语句：允许对 oss 的 mybucket 存储桶中的对象授予只读访问权限`oss:ListObjects`和`oss:GetObject`，并限制请求者的 IP 来源必须是`192.168.0.0/16`或`172.12.0.0/16`。

``` {#codeblock_emt_lv4_dpq}
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
                    "acs:SourceIp": ["172.12.0.0/16", "172.12.0.0/16"]
                }
            }
        }
    ]
}
```

