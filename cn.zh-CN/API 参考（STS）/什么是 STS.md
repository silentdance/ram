# 什么是 STS {#concept_ong_5nv_xdb .concept}

阿里云临时安全令牌（Security Token Service，STS）是阿里云提供的一种临时访问权限管理服务。

## STS 功能特性 {#section_xsr_q4v_xdb .section}

通过 STS 服务，您所授权的身份主体（RAM 用户、RAM 用户组或 RAM 角色）可以获取一个自定义时效和访问权限的临时访问令牌。STS 令牌持有者可以通过以下方式访问阿里云资源：

-   通过编程方式访问被授权的阿里云服务 API。
-   登录阿里云控制台操作被授权的云资源。

## STS 接入地址 {#section_ijw_rfh_vgb .section}

用于 API 访问的 STS 接入地址：`https://sts.aliyuncs.com`。

## STS 基本概念 {#section_kzx_rfh_vgb .section}

 RAM 角色（RAM role）
 :   一种虚拟的 RAM 用户。

  RAM 角色的全局资源描述符（Role ARN）
 :   Role ARN 是角色的全局资源描述符（Aliyun Resource Name， 简称 ARN），用来指定具体角色。每个角色都有一个唯一的全局资源描述符。格式：`acs:ram::$accountID:role/$roleName`。

  可信实体（Trusted entity）
 :   角色的可信实体是指可以扮演角色的实体用户身份。创建角色时必须指定可信实体，角色只能被受信的主体扮演。可信实体可以是受信的阿里云账号、受信的阿里云服务或身份提供商。

  扮演角色（Assume role）
 :   扮演角色是实体用户获取角色身份的安全令牌的方法。一个实体用户调用 STS API [AssumeRole](intl.zh-CN/API 参考（STS）/操作接口/AssumeRole.md#) 可以获得角色的安全令牌，使用安全令牌可以访问云服务 API。

 
