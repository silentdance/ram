# ECS授权样例 {#concept_phs_2sx_ydb .concept}

如果您的租户账号购买了10个ECS实例。而作为RAM管理员，您希望仅仅授权其中的2个ECS实例给某个RAM用户。那么您可以创建如下的授权策略：

**说明：** 授予该策略的RAM用户是可以列出所有的ECS实例，但只能操作（比如StopInstance操作）其中的两台。目前，不支持RAM用户仅仅查看自己有访问权限的ECS实例。

```
{
  "Statement": [
    {
      "Action": "ecs:*",
      "Effect": "Allow",
      "Resource": [
                  "acs:ecs:*:*:instance/i-001",
                  "acs:ecs:*:*:instance/i-002"
                  ]
    },
    {
      "Action": "ecs:Describe*",
      "Effect": "Allow",
      "Resource": "*"
    }
  ],
  "Version": "1"
}
```

