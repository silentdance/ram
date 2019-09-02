# 修改RAM角色的可信实体 {#concept_221552 .concept}

通过修改RAM角色的策略内容，可以修改RAM角色的可信实体。本文通过示例为您介绍如何修改RAM角色的可信实体为阿里云账号、阿里云服务或身份提供商。

## 修改RAM角色的可信实体为阿里云账号 {#section_2gb_zs1_4g9 .section}

若`Principal`中有`RAM`字段，表示该RAM角色的可信实体为**阿里云账号**，即可以被受信云账号下授权的RAM用户扮演。

以下述策略为例：该RAM角色可以被阿里云账号（AccountID=123456789012\*\*\*\*）下授权的任何RAM用户扮演。

``` {#codeblock_dtf_u2w_ycg .language-json}
{

    "Statement": [

        {
            "Action": "sts:AssumeRole",
            "Effect": "Allow",
            "Principal": {
                "RAM": [
                    "acs:ram::123456789012****:root"
                ]
            }
        }
    ],
    "Version": "1"
}
```

若您将`Principal`中的内容更改如下，则表示该RAM角色可以被阿里云账号（AccountID=123456789012\*\*\*\*）下的RAM用户`testuser`扮演。

``` {#codeblock_ldt_de5_bjr .language-json}
            "Principal": {
                "RAM": [
                    "acs:ram::123456789012****:user/testuser"                        
```

**说明：** 创建此角色时，请确保已创建好RAM用户`testuser`（其UPN为：testuser@123456789012\*\*\*\*.onaliyun.com）。

## 修改RAM角色的可信实体为阿里云服务 {#section_b5k_b6k_aut .section}

若`Principal`中有`Service`字段，表示该RAM角色的可信实体为**阿里云服务**，即可以被受信云服务扮演。

以下述策略为例：该RAM角色可以被当前云账号下的ECS服务扮演。

``` {#codeblock_q2q_69l_wg8 .language-json}
{

    "Statement": [

        {
            "Action": "sts:AssumeRole",
            "Effect": "Allow",
            "Principal": {
                "Service": [
                    "ecs.aliyuncs.com"
                ]
            }
        }
    ],
    "Version": "1"
}
```

## 修改RAM角色的可信实体为身份提供商 {#section_63s_tna_q1e .section}

若`Principal`中有`Federated`字段，表示该RAM角色的可信实体为**身份提供商**，即可以被受信身份提供商下的用户扮演。

以下述策略为例：该RAM角色可以被当前云账号（AccountID=123456789012\*\*\*\*）中的身份提供商`testprovider`下的用户扮演。

``` {#codeblock_ife_eyb_qvo .language-json}
{

    "Statement": [

        {
            "Action": "sts:AssumeRole",
            "Effect": "Allow",
            "Principal": {
                "Federated": [
                    "acs:ram::123456789012****:saml-provider/testprovider"
                ]
            },
            "Condition":{
                "StringEquals":{
                    "saml:recipient":"https://signin.alibabacloud.com/saml-role/sso"
                }
            }
        }
    ],
    "Version": "1"
}
```

