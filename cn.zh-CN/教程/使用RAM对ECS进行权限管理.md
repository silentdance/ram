# 使用RAM对ECS进行权限管理 {#task_k1k_r4x_ydb .task}

本文介绍了通过RAM的权限管理功能，创建相应的权限策略，从而对云服务器（ECS）进行权限管理，以满足RAM用户操作ECS的多种需求。

-   进行操作前，请确保您已经注册了阿里云账号。如还未注册，请先完成[账号注册](https://account.aliyun.com/register/register.htm)。
-   使用RAM对ECS进行权限管理前，请先了解以下常用的权限策略：
    -   AliyunECSFullAccess：为RAM用户授予ECS的完全管理权限。
    -   AliyunECSReadOnlyAccess：为RAM用户授予ECS的只读访问权限。
-   使用RAM对ECS进行权限管理前，请先了解ECS的权限定义。详情请参见[鉴权规则](../../../../cn.zh-CN/API参考/鉴权规则.md)。

## 将自定义策略授权给RAM用户 {#section_03 .section}

1.  根据下述[ECS授权样例](#section_01)创建相应的自定义策略。 

    关于如何创建自定义策略，请参见[创建自定义策略](../../../../cn.zh-CN/权限策略管理/自定义策略/创建自定义策略.md#)。

2.  找到创建好的权限策略，单击其权限策略名称。
3.  在**引用记录**页签下，单击**新增授权**。
4.  在**被授权主体**区域下，输入RAM用户名称后，单击需要授权的RAM用户。
5.  单击**确定**。 

    **说明：** 更多为RAM用户或用户组授权的方式，请参见[为RAM用户授权](../../../../cn.zh-CN/用户管理/为RAM用户授权.md#)和[为用户组授权](../../../../cn.zh-CN/用户组管理/为用户组授权.md#)。


## ECS授权样例 {#section_01 .section}

-   示例1：授权RAM用户管理2台指定的ECS实例。

    假设您的账号购买了多个实例，而作为RAM管理员，您希望仅授权其中的2个实例给某个RAM用户。实例ID分别为：i-001，i-002。

    ``` {#codeblock_dh2_4lh_eab .language-json}
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

    -   授予该权限策略的RAM用户可以查看所有的实例及资源，但只能操作其中2个实例。
    -   `Describe*`在权限策略中是必须的，否则用户在控制台将无法看到任何实例，使用API、CLI或SDK直接对两个实例进行操作是可以的。
-   示例2：仅授权RAM用户查看青岛的ECS实例，但不允许查看磁盘及快照信息。

    查看ECS资源列表的授权粒度可以到Region+资源类型的级别。

    ``` {#codeblock_ymj_ywx_ytm .language-json}
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

-   示例3：授权RAM用户创建快照权限。

    若RAM用户已拥有ECS实例管理员权限， 但仍不能创建磁盘快照，再次授予RAM用户指定磁盘的权限即可正常使用。ECS实例ID：inst-01，磁盘ID：dist-01。

    ``` {#codeblock_nhs_n78_zq5 .language-json}
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


