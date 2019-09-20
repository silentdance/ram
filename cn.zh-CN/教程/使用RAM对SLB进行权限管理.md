# 使用RAM对SLB进行权限管理 {#task_qhc_xqx_ydb .task}

本文介绍了通过RAM的权限管理功能，创建相应的权限策略，从而对负载均衡（SLB）进行权限管理，以满足RAM用户操作SLB的多种需求。

-   进行操作前，请确保您已经注册了阿里云账号。如还未注册，请先完成[账号注册](https://account.aliyun.com/register/register.htm)。
-   使用RAM对SLB进行权限管理前，请先了解几个常用的权限策略：
    -   AliyunSLBFullAccess：为RAM用户授予SLB的完全管理权限。
    -   AliyunSLBReadOnlyAccess：为RAM用户授予SLB的只读访问权限。
-   使用RAM对SLB进行权限管理前，请先了解SLB的权限定义。详情请参见[RAM鉴权](../../../../cn.zh-CN/API参考/RAM鉴权.md)。

## 将自定义策略授权给RAM用户 {#section_03 .section}

1.  根据下述[SLB授权样例](#section_hwy_ypl_5gb)创建相应的自定义策略。 

    关于如何创建自定义策略，请参见[创建自定义策略](../../../../cn.zh-CN/权限策略管理/自定义策略/创建自定义策略.md#)。

2.  找到创建好的权限策略，单击其权限策略名称。
3.  在**引用记录**页签下，单击**新增授权**。
4.  在**被授权主体**区域下，输入RAM用户名称后，单击需要授权的RAM用户。
5.  单击**确定**。 

    **说明：** 更多为RAM用户或用户组授权的方式，请参见[为RAM用户授权](../../../../cn.zh-CN/用户管理/为RAM用户授权.md#)和[为用户组授权](../../../../cn.zh-CN/用户组管理/为用户组授权.md#)。


## SLB授权样例 {#section_hwy_ypl_5gb .section}

-   示例1：授权RAM用户管理2台指定的SLB实例。

    假设您的账号购买了多个实例，而作为RAM管理员，您希望仅授权其中的2个实例给某个RAM用户。实例ID分别为：i-001，i-002。

    ``` {#codeblock_u95_o19_5tu .language-json}
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

    -   授予该权限策略的RAM用户可以查看所有的实例及资源，但只能操作其中2个实例。
    -   `Describe*`在权限策略中是必须的，否则用户在控制台将无法看到任何实例，使用API、CLI或 SDK直接对两个实例进行操作是可以的。
-   示例2：将ECS实例加入SLB-001负载均衡器。实例ID：i-001。

    ``` {#codeblock_jx0_9zh_nof .language-json}
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

    **说明：** 即使RAM用户按照示例1被授予管理某个SLB的权限，该用户在SLB实例中添加/移除ECS服务器或设置权重时仍然提示没有权限，原因是在负载均衡器中关于ECS服务器操作时没有授予以下两个权限：

    -   SLB的资源权限。
    -   ECS服务器的权限。
-   示例3：允许在特定SLB实例上执行任意ECS相关的操作。

    ``` {#codeblock_as8_8xz_kna .language-json}
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

    **说明：** 上述授权策略，允许RAM用户在i-001和i-002这两个负载均衡器实例上执行所有管理操作，并允许在这两个实例上执行与ECS资源相关的所有操作，例如向实例中添加ECS服务器，以及设置ECS服务器的权重等。


