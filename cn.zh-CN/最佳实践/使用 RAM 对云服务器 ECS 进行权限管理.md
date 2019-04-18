# 使用 RAM 对云服务器 ECS 进行权限管理 {#concept_k1k_r4x_ydb .concept}

本文介绍了通过 RAM 的权限管理功能，创建相应的权限策略，从而对云服务器 ECS 进行权限管理，以满足 RAM 用户操作 ECS 的多种需求。

## 基本信息 {#section_x3f_rzk_5gb .section}

使用 RAM 对 ECS 进行权限管理前，需先了解几个常用的权限策略。

|权限策略|描述|
|:---|:-|
|AliyunECSFullAccess|为 RAM 用户授予 ECS 的完全管理权限。|
|AliyunECSReadOnlyAccess|为 RAM 用户授予 ECS 的只读访问权限。|

**说明：** 查看 ECS 的权限定义，请参考 ECS 产品文档中的[鉴权规则](../../../../intl.zh-CN/API参考/鉴权规则.md)。

## 将自定义策略授权给 RAM 用户的操作步骤 {#section_03 .section}

1.  根据下述[ECS 授权样例](#section_01)创建相应的自定义策略。

    详情请参考：[权限策略管理](../../../../intl.zh-CN/用户指南/权限管理/权限策略管理.md#)。

2.  找到创建好的权限策略，单击其**权限策略名称**。
3.  单击**引用记录** \> **新增授权**。
4.  **被授权主体**处输入需要授权的用户名称或 ID。
5.  单击**确定**。

    **说明：** 您也可以直接对**用户**或**用户组**授予创建好的权限策略，详情请参考：[RAM 授权](../../../../intl.zh-CN/用户指南/权限管理/授权管理/RAM 授权.md#)。


## ECS 授权样例 {#section_01 .section}

-   示例 1：授权 RAM 用户管理 2 台指定的 ECS 实例。

    假设您的账号购买了多个实例，而作为 RAM 管理员，您希望仅授权其中的 2 个实例给某个 RAM 用户。实例 ID 分别为：i-001，i-002。

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

    **说明：** 

    -   授予该权限策略的 RAM 用户可以查看所有的实例及资源，但只能操作其中 2 个实例。
    -   `Describe*`在权限策略中是必须的，否则用户在控制台将无法看到任何实例，使用 API、CLI 或 SDK 直接对两个实例进行操作是可以的。
-   示例 2：仅授权 RAM 用户查看青岛的 ECS 实例，但不允许查看磁盘及快照信息。

    查看 ECS 资源列表的授权粒度可以到 Region + 资源类型的级别。

    ```
    {
      "Statement": [
        {
          "Effect": "Allow",
          "Action": "ecs:Describe*",
          "Resource": "acs:ecs:cn-qingdao:*:instance/*"
        }
      ],
      "Version": "1"
    }
    ```

-   示例 3：授权 RAM 用户创建快照权限。

    若 RAM 用户已拥有 ECS 实例管理员权限， 但仍不能创建磁盘快照，再次授予 RAM 用户指定磁盘的权限即可正常使用。ECS 实例 ID：inst-01，磁盘 ID：dist-01。

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


