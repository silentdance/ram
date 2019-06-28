# Policy example {#concept_jxs_x2h_tgb .concept}

This topic describes how to create a policy and details the basic elements, policy structure, and policy syntax involved.

The following is a policy example, which contains two statements:

-   The first statement grants the permission \(`ecs:Describe*`\) to view all ECS resources in China East 1 \(Hangzhou\) Region.
-   The second statement grants two read-only permissions \(`oss:ListObjects` and `oss:GetObject`\) to access objects in the OSS bucket mybucket, and allows access to resources only from users with the source IP address of `192.168.0.0/16` or `172.12.0.0/16`.

``` {#codeblock_d7j_yhn_k85}
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
                    "acs:SourceIp": ["192.168.0.0/16", "172.12.0.0/16"]
                }
            }
        }
    ]
}
```

