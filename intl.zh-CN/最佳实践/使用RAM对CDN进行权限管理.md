# 使用RAM对CDN进行权限管理 {#task_g2m_jrx_ydb .task}

本文介绍了通过RAM的权限管理功能，创建相应的权限策略，从而对内容分发（CDN）进行权限管理，以满足RAM用户操作CDN的多种需求。

-   请确保您已经注册了阿里云账号。如还未注册，请先完成账号注册。详情请参见[账号注册](https://account.alibabacloud.com/register/intl_register.htm)。
-   使用RAM对CDN进行权限管理前，请先了解以下常用的权限策略：
    -   AliyunCDNFullAccess：为RAM用户授予CDN的完全管理权限。
    -   AliyunCDNReadOnlyAccess：为RAM用户授予CDN的只读访问权限。
-   使用RAM对CDN进行权限管理前，请先了解CDN的权限定义。详情请参见[CDN API鉴权规则](../../../../intl.zh-CN/旧版API参考/RAM资源授权/CDN API鉴权规则.md#)。

1.  [创建自定义策略](../../../../intl.zh-CN/用户指南/权限策略/自定义策略/创建自定义策略.md#)。 

    ``` {#codeblock_6jg_tqy_dgh .language-json}
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

    **说明：** 上述自定义策略表示授权RAM用户执行CDN只读、刷新缓存及预热的操作。您可以根据需要修改自定义策略内容，从而授权RAM用户不同的权限。关于`Action`或`Resource`的使用规则，请参见[权限策略基本元素](../../../../intl.zh-CN/用户指南/权限策略/权限策略语言/权限策略基本元素.md#)。

2.  找到创建好的权限策略，单击其权限策略名称。
3.  在**引用记录**页签下，单击**新增授权**。
4.  在**被授权主体**区域下，输入RAM用户名称后，单击需要授权的RAM用户。
5.  单击**确定**。 

    **说明：** 更多为RAM用户或用户组授权的方式，请参见[为RAM用户授权](../../../../intl.zh-CN/用户指南/用户/为 RAM 用户授权.md#)和[为用户组授权](../../../../intl.zh-CN/用户指南/用户组/为用户组授权.md#)。


