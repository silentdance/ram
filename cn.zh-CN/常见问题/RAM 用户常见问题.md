# RAM 用户常见问题 {#concept_dwg_5rx_ydb .concept}

本文介绍了在使用 RAM 用户过程中的常见问题，包括登录、费用和权限等问题，为您提供说明和指导。

## RAM 用户登录地址在哪里？ {#section_x1f_w4x_ydb .section}

RAM 用户登录地址如下： [RAM 用户登录页](https://signin-intl.aliyun.com/login.htm)。

**说明：** 通过登录 [RAM 控制台](https://ram.console.aliyun.com/)，在概览页可以快速查询登录 RAM 用户登录地址。当您使用此地址登录时，系统会为您自动填写默认域名，您只需补齐 RAM 用户名称即可。

RAM 用户的登录有以下几种方式：

-   方式一：<$username\>@<$AccountAlias\>.onaliyun.com 。例如：username@company-alias.onaliyun.com。

    **说明：** RAM 用户登录账号为 UPN（User Principal Name）格式，即 RAM 控制台用户列表中所见的用户登录名称。<$username\>为 RAM 用户名称，<$AccountAlias\>.onaliyun.com 为默认域名。

-   方式二：<$username\>@<$AccountAlias\>。例如：username@company-alias。

    **说明：** <$username\>为 RAM 用户名称，<$AccountAlias\> 为账号别名。

-   方式三：如果创建了域别名，也可以使用域别名登录，格式为：<$username\>@<$DomainAlias\>。

    **说明：** <$username\>为 RAM 用户名称，<$DomainAlias\> 为域别名。


关于 RAM 用户的登录地址和登录方式，请参考：[RAM 用户登录控制台](../../../../intl.zh-CN/用户指南/用户/RAM 用户登录控制台.md#)。

## 什么是默认域名、账号别名、域别名？ {#section_bb5_2sm_qfb .section}

关于**默认域名**、**账号别名**、**域别名**的概念，请参考[基本概念](../../../../intl.zh-CN/产品简介/基本概念.md#)。

-   使用云账号或具有 RAM 管理权限的 RAM 用户登录 [RAM 控制台](https://ram.console.aliyun.com/)。
-   在左侧导航栏的**人员管理**菜单下，单击**设置**。
-   在**高级设置**页签下，可以查看并管理**默认域名**、**账号别名**和**域别名**。

## RAM 用户采购云产品需要什么权限？ {#section_ic3_fms_qfb .section}

-   如需采购按量付费的云产品，一般只需给 RAM 用户分配该产品的创建实例或类似权限即可。
-   如需采购包年包月的云产品，还需要额外授予支付订单的权限，即授予用户 `AliyunBSSOrderAccess` 的权限策略。
-   有些产品在购买时需要连带使用或创建多种资源，这种情况下需要 RAM 用户具备相应资源的读取或创建权限。

    以下以创建 ECS 实例为例，说明具体需要的权限。

    如下权限策略表示 RAM 用户具有从控制台、使用 API 或从实例启动模板创建 ECS 实例的能力：

    ``` {#codeblock_hzt_yy2_83z}
    {
      "Version": "1",
      "Statement": [
        {
          "Action": [
            "ecs:DescribeLaunchTemplates",
            "ecs:CreateInstance",
            "ecs:RunInstances",
            "ecs:DescribeInstances",
            "ecs:DescribeImages",
            "ecs:DescribeSecurityGroups"
          ],
          "Resource": "*",
          "Effect": "Allow"
        },
        {
          "Action": [
            "vpc:DescribeVpcs",
            "vpc:DescribeVSwitches"
          ],
          "Resource": "*",
          "Effect": "Allow"
        }
      ]
    }
    ```

    如果需要 RAM 用户在创建 ECS 实例过程中使用或创建其他资源，根据资源类型不同，还需要授予以下各类权限。

    **说明：** 

    -   关于如何创建自定义策略，请参考：[创建自定义策略](../../../../intl.zh-CN/用户指南/权限策略/自定义策略/创建自定义策略.md#)。
    -   关于如何为 RAM 用户授权，请参考：[为 RAM 用户授权](../../../../intl.zh-CN/用户指南/用户/为 RAM 用户授权.md#)。
    |操作|权限策略|
    |:-|:---|
    |使用快照创建 ECS 实例|`ecs:DescribeSnapshots`|
    |同时创建并使用新的 VPC|     -   `vpc:CreateVpc`
    -   `vpc:CreateVSwitch`
 |
    |同时创建并使用新的安全组|     -   `ecs:CreateSecurityGroup`
    -   `ecs:AuthorizeSecurityGroup`
 |
    |指定实例角色|     -   `ecs:DescribeInstanceRamRole`
    -   `ram:ListRoles`
    -   `ram:PassRole`
 |
    |使用 Keypair|     -   `ecs:CreateKeyPair`
    -   `ecs:DescribeKeyPairs`
 |
    |在专有宿主机上创建 ECS 实例|`ecs:AllocateDedicatedHosts`|


## 授权给 RAM 用户后，为什么访问时系统依然提示无权限？ {#section_kjs_vjs_qfb .section}

-   请确认 RAM 用户的权限策略是否正确。
-   请检查 RAM 用户的自定义策略（个人权限策略、加入用户组的权限策略）是否对相关资源或操作设置了`"Effect": "Deny"`。

    例如：RAM 用户拥有只读访问云服务器 ECS 的权限：`AliyunECSReadOnlyAccess`，但如果同时也拥有如下权限策略：

    ``` {#codeblock_4v3_8cq_hgb}
    {
      "Statement": [
        {
          "Action": "ecs:*",
          "Effect": "Deny",
          "Resource": "*"
        }
      ],
      "Version": "1"
    }
    					
    ```

    **说明：** 根据 RAM 的 Deny 优先原则，该 RAM 用户不可以查看 ECS 资源。


## 没有授权 RAM 用户某个权限，为什么 RAM 用户仍可以操作？ {#section_cv1_qsm_qfb .section}

例如：RAM 用户没有 ECS 的 `FullAccess`或者 `ReadOnly`系统策略，也没有添加任何自定义策略，但可以查看实例列表。

-   请检查 RAM 用户所在的用户组权限策略中是否存在允许 RAM 用户操作的相应权限。
-   请确认当前已经被授权给 RAM 用户的其他权限策略中是否包含了相关权限。

    例如：云监控的系统权限策略为 `AliyunCloudMonitorFullAccess`，此权限包括查看 ECS 实例列表的权限：`"ecs:DescribeInstances"`，查看 RDS 实例列表的权限：`"rds:DescribeDBInstances"`和查看 SLB 实例列表的权限`"slb:DescribeLoadBalancer"` 等。当 `AliyunCloudMonitorFullAccess`被授权给 RAM 用户后，该 RAM 用户便有权限查看 ECS、RDS 和 SLB 等产品的实例信息。


## 怎样授权 RAM 用户单独管理续费？ {#section_ikw_mms_qfb .section}

目前续费管理没有统一的权限策略，需要根据具体产品自定义权限策略。一般需要授权给 RAM 用户购买该产品所需要的权限以及支付订单的权限。

例如：RAM 用户进行 ECS 的续费管理所需权限，请参考：[RAM 用户采购云产品需要什么权限？](#section_ic3_fms_qfb)给 RAM 用户授权，同时需要授予 `AliyunBSSOrderAccess`权限策略。

## RAM 用户使用资源所产生的费用怎么计算？ {#section_qqy_n1h_chb .section}

-   RAM 用户使用资源所产生的费用由其所属的云账号承担。
-   RAM 用户可以自动享有云账号享有的折扣，无需特殊设置。
-   消费额度、信用额度、独立付款方式等财务相关属性均为云账号内的全局设置，影响所有 RAM 用户。不支持为某个 RAM 用户单独设置。
-   RAM 用户可以被授权进行充值操作，充值后的金额归属于云账号。
-   RAM 用户或 RAM 用户集合不能作为独立的财务单元出账单。 若有云账号内的分账需求，请提交工单由售后人员提供解决方案。

