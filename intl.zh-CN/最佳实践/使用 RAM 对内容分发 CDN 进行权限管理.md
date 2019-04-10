# 使用 RAM 对内容分发 CDN 进行权限管理 {#concept_g2m_jrx_ydb .concept}

本文介绍了通过 RAM 的权限管理功能，创建相应的权限策略，从而对内容分发 CDN 进行权限管理，以满足 RAM 用户操作 CDN 的多种需求。

## 基本信息 {#section_x3f_rzk_5gb .section}

使用 RAM 对 CDN 进行权限管理前，需先了解几个常用的权限策略。

|操作|描述|
|:-|:-|
|查看 CDN 的权限定义|请参考 CDN open API 文档中的 [CDN API鉴权规则](../../../../../intl.zh-CN/旧版API参考/RAM资源授权/CDN API鉴权规则.md#)。|
|为 RAM 用户授予 CDN 的完全管理权限|为 RAM 用户添加系统策略：`AliyunCDNFullAccess`。|
|为 RAM 用户授予 CDN 的只读访问权限|为 RAM 用户添加系统策略：`AliyunCDNReadOnlyAccess`。|

## 授权 RAM 用户执行 CDN 只读、刷新缓存及预热的操作步骤 {#section_03 .section}

1.  创建自定义策略。

    ```
    {
      "Version": "1",
      "Statement": [
        {
          "Action": [
            "cdn:Describe*",
            "cdn:PushObjectCache",
            "cdn:RefreshObjectCaches"
          ],
          "Resource": "acs:cdn:*:*:*",
          "Effect": "Allow"
        }
      ]
    }
    ```

    详情请参考：[权限策略管理](../../../../../intl.zh-CN/用户指南/权限管理/权限策略管理.md#)。

2.  找到创建好的权限策略，单击其**权限策略名称**。
3.  单击**引用记录** \> **新增授权**。
4.  **被授权主体**处输入需要授权的用户名称或 ID。
5.  单击**确定**

    **说明：** 您也可以在**人员管理**界面，对**用户**或**用户组**授予创建好的权限策略，详情请参考：[RAM 授权](../../../../../intl.zh-CN/用户指南/权限管理/授权管理/RAM 授权.md#)。

    。


