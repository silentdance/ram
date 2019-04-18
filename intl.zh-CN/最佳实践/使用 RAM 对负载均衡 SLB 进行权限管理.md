# 使用 RAM 对负载均衡 SLB 进行权限管理 {#concept_qhc_xqx_ydb .concept}

本文介绍了通过 RAM 的权限管理功能，创建相应的权限策略，从而对负载均衡 SLB 进行权限管理，以满足 RAM 用户操作 SLB 的多种需求。

## 基本信息 {#section_x3f_rzk_5gb .section}

使用 RAM 对 SLB 进行权限管理前，需先了解几个常用的权限策略。

|权限策略|描述|
|:---|:-|
|AliyunSLBFullAccess|为 RAM 用户授予 SLB 的完全管理权限。|
|AliyunSLBReadOnlyAccess|为 RAM 用户授予 SLB 的只读访问权限。|

**说明：** 查看 SLB 的权限定义，请参考 SLB 产品文档中的 [RAM鉴权](../../../../intl.zh-CN/API参考/RAM鉴权.md)。

## 将自定义策略授权给 RAM 用户的操作步骤 {#section_03 .section}

1.  根据下述 [SLB 授权样例](#section_hwy_ypl_5gb)创建相应的自定义策略。

    详情请参考：[权限策略管理](../../../../intl.zh-CN/用户指南/权限管理/权限策略管理.md#)。

2.  找到创建好的权限策略，单击其**权限策略名称**。
3.  单击**引用记录** \> **新增授权**。
4.  **被授权主体**处输入需要授权的用户名称或 ID。
5.  单击**确定**。

    **说明：** 您也可以直接对**用户**或**用户组**授予创建好的权限策略，详情请参考：[RAM 授权](../../../../intl.zh-CN/用户指南/权限管理/授权管理/RAM 授权.md#)。


## SLB 授权样例 {#section_hwy_ypl_5gb .section}

-   示例 1：授权 RAM 用户管理 2 台指定的 SLB 实例。

    假设您的账号购买了多个实例，而作为 RAM 管理员，您希望仅授权其中的 2 个实例给某个 RAM 用户。实例 ID 分别为：i-001，i-002。

    ```
    {
      "Statement": [
        {
          "Effect": "Allow",
          "Action": "slb:*",
          "Resource": [
                      "acs:slb:*:*:loadbalancer/i-001",
                      "acs:slb:*:*:loadbalancer/i-002"
                      ]
        },
        {
          "Effect": "Allow",
          "Action": "slb:Describe*",
          "Resource": "*"
        }
      ],
      "Version": "1"
    }
    ```

    **说明：** 

    -   授予该权限策略的 RAM 用户可以查看所有的实例及资源，但只能操作其中 2 个实例。
    -   `Describe*`在权限策略中是必须的，否则用户在控制台将无法看到任何实例，使用 API、CLI 或 SDK 直接对两个实例进行操作是可以的。
-   示例 2：将 ECS 实例加入 SLB-001 负载均衡器。实例 ID：i-001。

    ```
    {
      "Statement": [
        {
          "Effect": "Allow",
          "Action": "slb:AddBackendServers",
          "Resource": ["acs:slb:*:*:loadbalancer/slb-001"]
        },
        {
          "Effect": "Allow",
          "Action": "slb:AddBackendServers",
          "Resource": ["acs:ecs:*:*:instance/i-001"]
        },
        {
            "Effect": "Allow",
            "Action": "slb:DescribeLoadBalancers",
            "Resource": "acs:slb:*:*:loadbalancer/*"
        }
      ],
      "Version": "1"
    }
    ```

    **说明：** 即使 RAM 用户按照示例 1 被授予管理某个 SLB 的权限，该用户在 SLB 实例中添加/移除 ECS 服务器或设置权重时仍然提示没有权限，原因是在负载均衡器中关于 ECS 服务器操作时没有授予以下两个权限：

    -   SLB 的资源权限。
    -   ECS 服务器的权限。
-   示例 3：允许在特定 SLB 实例上执行任意 ECS 相关的操作。

    ```
    {
      "Statement": [
        {
          "Effect": "Allow",
          "Action": "slb:*",
          "Resource": [
                      "acs:slb:*:*:loadbalancer/i-001",
                      "acs:slb:*:*:loadbalancer/i-002"
                      ]
        },
        {
          "Effect": "Allow",
          "Action": "slb:Describe*",
          "Resource": "*"
        },
        {
          "Effect": "Allow",
          "Action": "slb:*",
          "Resource": "acs:ecs:*:*:*"
        }
      ],
      "Version": "1"
    }
    ```

    **说明：** 上述授权策略，允许 RAM 用户在 i-001、i-002 这两个负载均衡器实例上执行所有管理操作，并允许在这两个实例上执行与 ECS 资源相关的所有操作，例如向实例中添加 ECS 服务器，以及设置 ECS 服务器的权重等。


