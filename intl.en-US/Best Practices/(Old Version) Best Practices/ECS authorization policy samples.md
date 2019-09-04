# ECS authorization policy samples {#concept_phs_2sx_ydb .concept}

If your tenant account has 10 ECS instances, but as a RAM administrator, you would like to grant only two instances to a RAM user. You can create a policy as follows:

**Note:** The authorized RAM user can view all the ECS instances but can perform operations \(such as the StopInstance operation\) on only two of them. Currently, RAM does not support viewing only the authorized ECS instances.

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

