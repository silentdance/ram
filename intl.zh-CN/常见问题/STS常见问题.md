# STS常见问题 {#concept_wsg_bsx_ydb .concept}

本文介绍了一些STS使用过程中的常见问题，为您提供说明和指导。

## 为什么使用STS会报错？ {#section_zb1_ydl_qfb .section}

进行授权的RAM用户没有`AliyunSTSAssumeRoleAccess`权限策略，因此使用STS时会报错无权限。

STS使用Java SDK生成临时账号密码报错。报错信息如下：

``` {#screen_yxl_pfc_hh0 .screen}
Error message: You are not authorized to do this action. You should be authorized by RAM
```

## STS token的权限限制是什么？ {#section_nnn_h2l_qfb .section}

STS token的权限：指定角色的权限与调用[AssumeRole](../../../../intl.zh-CN/API 参考（STS）/操作接口/AssumeRole.md#)接口时所设置的`Policy`的交集。

**说明：** 若在调用AssumeRole接口时不设置`Policy`参数，则返回的STS token将拥有指定角色的所有权限。

## STS token的有效期是多久？ {#section_gqr_tbl_qfb .section}

STS token的有效期为900秒~3600秒，默认值3600秒。

**说明：** 您可以在调用AssumeRole接口时设置DurationSeconds参数来限制STS token的有效时间。

## STS服务调用次数是否有上限？ {#section_a1m_ycl_qfb .section}

STS服务有流控限制：100QPS。超过流控会被限制。

## STS获取的多个token是否同时有效？ {#section_hgb_lcl_qfb .section}

STS token在过期之前都是有效的，无论是否创建了新的STS token。

