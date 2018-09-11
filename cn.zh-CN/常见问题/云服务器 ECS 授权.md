# 云服务器 ECS 授权 {#concept_k1k_r4x_ydb .concept}

## 问题 {#section_x1f_w4x_ydb .section}

-   [查看 ECS 的权限定义](#section_mzy_x4x_ydb)
-   [为一个子用户授予 ECS 服务的完全管理权限](#section_jft_y4x_ydb)
-   [为一个子用户授予只读访问 ECS 的权限](#section_fnn_z4x_ydb)
-   [仅允许子用户查看青岛的 ECS 实例，但是不允许查看磁盘信息及快照信息](#section_jpq_1px_ydb)
-   [授权一个子用户管理两台指定的 ECS 实例](#section_a1c_cpx_ydb)
-   [授权子用户创建快照权限](#section_ecc_2px_ydb)

## 查看 ECS 的权限定义 {#section_mzy_x4x_ydb .section}

请参考 ECS OpenAPI 文档中的[鉴权规则](../../../../intl.zh-CN/API 参考/鉴权规则.md)。

## 为一个子用户授予 ECS 服务的完全管理权限 {#section_jft_y4x_ydb .section}

在 RAM 控制台上，为此子用户（或该用户所在群组）附加系统授权策略 “AliyunECSFullAccess”。

## 为一个子用户授予只读访问 ECS 的权限 {#section_fnn_z4x_ydb .section}

在 RAM 控制台中创建一个子用户，并为此子用户附加系统授权策略 “AliyunECSReadOnlyAccess”。

添加授权策略的方式请参考[授权](../../../../intl.zh-CN/用户指南/授权管理/授权.md)。

## 仅允许子用户查看青岛的 ECS 实例，但是不允许查看磁盘信息及快照信息 {#section_jpq_1px_ydb .section}

查看 ECS 资源列表的授权粒度可以到 “Region + 资源类型” 的级别。

下面的样例仅授权查看青岛的 ECS 实例信息。

```
{
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "ecs:DescribeRegions",
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": "ecs:Describe*",
      "Resource": "acs:ecs:cn-qingdao:*:instance/*"
    }
  ],
  "Version": "1"
}
```

## 授权一个子用户管理两台指定的 ECS 实例 {#section_a1c_cpx_ydb .section}

假设您的租户账号购买了 10 个 ECS 实例。而作为 RAM 管理员，您希望仅仅授权其中的 2 个 ECS 实例给某个 RAM 用户。那么您可以创建如下的自定义授权策略：

**说明：** 授予该策略的 RAM 用户是可以列出所有的 ECS 实例，但只能操作（比如 StopInstance 操作）其中的两台。目前，不支持 RAM 用户仅仅查看自己有访问权限的 ECS 实例。

这里假设您的两台实例 ID 分别是 i-001 和 i-002；首先您需要创建一条自定义授权策略，包含管理 i-001,i-002 的权限以及查看 ECS 所有资源的权限：

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

然后为子用户附加该自定义授权策略即可。

## 授权子用户创建快照权限 {#section_ecc_2px_ydb .section}

如果已经授权给子账户指定 ECS 的管理员权限后，依然不能创建磁盘快照，因为快照是基于磁盘基础上，需要授予子用户指定磁盘的权限。

假设您需要指定子账户管理实例 ID 为 inst-01 的 ecs，并且具备给 ID 为：dist-01 的磁盘创建快照的权限。您可以创建如下的自定义授权策略：

```
{
  "Statement": [
    {
      "Action": "ecs:*",
      "Effect": "Allow",
      "Resource": [
        "acs:ecs:*:*:instance/inst-01"
      ]
    },
    {
      "Action": "ecs:CreateSnapshot",
      "Effect": "Allow",
      "Resource": [
        "acs:ecs:*:*:disk/dist-01",
        "acs:ecs:*:*:snapshot/*"
      ]
    },
    {
      "Action": [
        "ecs:Describe*"
      ],
      "Effect": "Allow",
      "Resource": "*"
    }
  ],
  "Version": "1"
}
```

然后为子用户附加该自定义授权策略即可。

