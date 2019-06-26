# Change the trusted entity of a RAM role {#concept_221552 .concept}

This topic describes how to change the trusted entity of a RAM role by modifying the policy attached to the role. The trusted entity of a RAM role can be an Alibaba Cloud account, an Alibaba Cloud service, or an identity provider \(IdP\).

## Change the trusted entity to an Alibaba Cloud account {#section_2gb_zs1_4g9 .section}

If the `Principal` element contains a "RAM" field, the trusted entity is an Alibaba Cloud account, and the role can be assumed by RAM users under the trusted account.

The following policy indicates that the role can be assumed by any RAM user under the Alibaba Cloud account \(123456789012\*\*\*\*\):

``` {#codeblock_dtf_u2w_ycg}
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

If you modify the `Principal` element as follows, the role can be assumed by the RAM user `testuser` under the Alibaba Cloud account \(123456789012\*\*\*\*\):

``` {#codeblock_ldt_de5_bjr}
            "Principal": {
                "RAM": [
                    "acs:ram::123456789012****:user/testuser"                        
```

## Change the trusted entity to an Alibaba Cloud service {#section_b5k_b6k_aut .section}

If the `Principal` element contains a "Service" field, the trusted entity is an Alibaba Cloud service, and the role can be assumed by trusted Alibaba Cloud services under the current Alibaba Cloud account.

The following policy indicates that the role can be assumed by ECS under the current Alibaba Cloud account:

``` {#codeblock_q2q_69l_wg8}
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

## Change the trusted entity to an IdP {#section_63s_tna_q1e .section}

If the `Principal` element contains a "Federated" field, the trusted entity is an IdP, and the role can be assumed by users under the trusted IdP.

The following policy indicates that the role can be assumed by users under the IdP \(`testprovider`\) in the current Alibaba Cloud account \(123456789012\*\*\*\*\):

``` {#codeblock_ife_eyb_qvo}
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

