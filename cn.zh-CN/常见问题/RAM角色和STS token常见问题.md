# RAM角色和STS token常见问题 {#concept_wsg_bsx_ydb .concept}

本文介绍了一些RAM角色和STS token的常见问题，为您提供说明和指导。

## RAM角色有几种类型？ {#section_l3e_s8m_3fb .section}

根据RAM可信实体的不同，RAM支持以下三种类型的角色：

-   **阿里云账号**
-   **阿里云服务**
-   **身份提供商**

## 三种类型的RAM角色分别可以被谁扮演？ {#section_ykd_yux_fjf .section}

-   **阿里云账号**：允许RAM用户所扮演的角色。扮演角色的RAM用户可以属于自己的云账号，也可以属于其他云账号。此类角色主要用来解决跨账号访问和临时授权问题。
-   **阿里云服务**：允许云服务所扮演的角色。特别的是，ECS实例RAM角色也属于这个类型，其可信实体为ECS服务，详情请参见[借助于实例RAM角色访问其他云产品](../../../../cn.zh-CN/最佳实践/借助于实例RAM角色访问其他云产品.md#)。此类角色主要用于授权云服务代理您进行资源操作。
-   **身份提供商**：允许受信身份提供商下的用户所扮演的角色。此类角色主要用于实现与阿里云的SSO。

## 能否指定RAM用户具体可以扮演哪个RAM角色？ {#section_c5c_e3t_at9 .section}

您也可以通过创建自定义策略指定RAM用户具体可以扮演的RAM角色。策略示例如下所示：

``` {#codeblock_6kn_jyr_j18}
{
    "Statement": [
        {
            "Action": "sts:AssumeRole",
            "Effect": "Allow",
            "Resource": "acs:ram:*:$accountId:role/$roleName"
        }
    ],
    "Version": "1"
}
```

**说明：** 

-   上述自定义策略中的`Resource`为角色ARN，如何查看角色ARN请参见[\#section\_3di\_0zn\_p7y](#section_3di_0zn_p7y)其中，`$accountId`为云账号ID，`$roleName`为RAM角色名称。
-   将上述自定义策略授权给RAM用户，便可以指定具体可以扮演的RAM角色。关于如何为RAM用户授权，请参见[为RAM用户授权](../../../../cn.zh-CN/用户管理/为RAM用户授权.md#)。

## 如何查看RAM角色的ARN？ {#section_qbw_mhy_173 .section}

您可以登录[RAM控制台](https://signin.aliyun.com/login.htm)，在**RAM角色管理**页签下，单击目标RAM角色名称，在**基本信息**区域下查看角色ARN。

![ RAM角色ARN](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1769808/156887212460601_zh-CN.png)

## 为什么使用STS时会报错？ {#section_lj3_0pc_8ep .section}

STS使用Java SDK生成临时账号密码报错的信息如下所示：

``` {#screen_4u6_gtm_n0h .screen}
Error message: You are not authorized to do this action. You should be authorized by RAM.
```

出现上述现象是因为进行授权的RAM用户没有相应的权限，因此使用时系统会报错。

请为RAM用户添加系统策略（AliyunSTSAssumeRoleAccess）或自定义策略，详情请参见[\#section\_5el\_qdq\_959](#section_5el_qdq_959)

## STS服务调用次数是否有上限？ {#section_oyc_f04_h99 .section}

STS服务有流控限制：100QPS。超过流控会被限制。

## STS token的权限限制是什么？ {#section_nnn_h2l_qfb .section}

STS token的权限：指定角色的权限与调用[AssumeRole](../../../../cn.zh-CN/API 参考（STS）/操作接口/AssumeRole.md#)接口时所设置的`Policy`的交集。

**说明：** 若在调用AssumeRole接口时不设置Policy参数，则返回的STS token将拥有指定角色的所有权限。

## STS token的有效期是多久？ {#section_gqr_tbl_qfb .section}

STS token的有效期为900秒~3600秒，默认值为3600秒。

**说明：** 您可以在调用[AssumeRole](../../../../cn.zh-CN/API 参考（STS）/操作接口/AssumeRole.md#)接口时设置DurationSeconds参数来限制STS token的有效时间。

## STS获取的多个token是否同时有效？ {#section_hgb_lcl_qfb .section}

STS token在过期之前都是有效的，无论是否创建了新的STS token。

