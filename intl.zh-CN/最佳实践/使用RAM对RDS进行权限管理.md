# 使用 RAM 对云数据库 RDS 进行权限管理 {#concept_zqh_gqx_ydb .concept}

本文介绍了通过 RAM 的权限管理功能，创建相应的权限策略，从而对云数据库 RDS 进行权限管理，以满足 RAM 用户操作 RDS 的多种需求。

## 基本信息 {#section_x3f_rzk_5gb .section}

使用 RAM 对 RDS 进行权限管理前，需先了解几个常用的权限策略。

|权限策略|描述|
|:---|:-|
|AliyunRDSFullAccess|为 RAM 用户授予 RDS 的完全管理权限。|
|AliyunRDSReadOnlyAccess|为 RAM 用户授予 RDS 的只读访问权限。|

**说明：** 查看 RDS 的权限定义，请参考 RDS 产品文档中的[RAM资源授权](../../../../intl.zh-CN/API参考/RAM资源授权.md#)。

## 将自定义策略授权给 RAM 用户的操作步骤 {#section_03 .section}

1.  根据下述 [RDS 授权样例](#section_rhd_4ll_5gb)创建相应的自定义策略。

    详情请参考：[../../../../dita-oss-bucket/SP\_65/DNRAM11885314/ZH-CN\_TP\_23764.md\#](../../../../intl.zh-CN/用户指南/权限策略/自定义策略/创建自定义策略.md#)。

2.  找到创建好的权限策略，单击其**权限策略名称**。
3.  单击**引用记录** \> **新增授权**。
4.  **被授权主体**处输入需要授权的用户名称或 ID。
5.  单击**确定**。

    **说明：** 您也可以直接对**用户**或**用户组**授予创建好的权限策略，详情请参考：[RAM 授权](../../../../intl.zh-CN/用户指南/（隐藏）旧版用户指南/授权管理/RAM 授权.md#)。


## RDS 授权样例 {#section_rhd_4ll_5gb .section}

-   示例 1：授权 RAM 用户管理 2 台指定的 RDS 实例。

    假设您的账号购买了多个实例，而作为 RAM 管理员，您希望仅授权其中的 2 个实例给某个 RAM 用户。实例 ID 分别为：i-001，i-002。

    ```
    {
      "Statement": [
        {
          "Action": "rds:*",
          "Effect": "Allow",
          "Resource": [
                      "acs:rds:*:*:dbinstance/i-001",
                      "acs:rds:*:*:dbinstance/i-002"
                      ]
        },
        {
          "Action": "rds:Describe*",
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
-   示例 2：授权 RAM 用户访问 DMS 管理数据库内容。
    -   授权 RAM 用户登录指定 RDS：

        ```
        {
          "Statement": [
            {
              "Action": "dms:LoginDatabase",
              "Effect": "Allow",
              "Resource": "acs:rds:*:*:dbinstance/rds783a0639ks5k7****"
            }
          ],
          "Version": "1"
        }
        ```

        **说明：** 请将 `rds783a0639ks5k7****` 替换为您要授权的 RDS 实例 ID。

    -   授权 RAM 用户登录所有 RDS：

        ```
        {
          "Statement": [
            {
              "Action": "dms:LoginDatabase",
              "Effect": "Allow",
              "Resource": "acs:rds:*:*:*"
            }
          ],
          "Version": "1"
        }
        ```


