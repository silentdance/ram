# Change the trusted entity of a RAM role {#concept_221552 .concept}

This topic describes how to change the trusted entity of a RAM role to a specific Alibaba Cloud account, Alibaba Cloud service, or identity provider \(IdP\). You can change the trusted entity of a RAM role by modifying the policy attached to the RAM role.

**Note:** When creating a RAM role, you can specify an Alibaba Cloud account, Alibaba Cloud service, or identity provider \(IdP\) for the trusted entity of the RAM role. In most cases, you do not need to change the trusted entity after creating a RAM role. If you have to change the trusted entity, you can use either of the following methods. After you change the trusted entity, we recommend that you test whether the RAM role works properly.

## Change the trusted entity of a RAM role to a specific Alibaba Cloud account {#section_2gb_zs1_4g9 .section}

You can check the trusted entity of a RAM role by viewing the policy. If the `Principal` element contains the `RAM` field, the trusted entity is an **Alibaba Cloud account**. The role can be assumed by RAM users under the trusted account.

For example, the following policy indicates that the RAM role can be assumed by any RAM user under the Alibaba Cloud account whose ID is 123456789012\*\*\*\*.

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

If you modify the `Principal` element as follows, the RAM role can be assumed by the RAM user named `testuser` under the Alibaba Cloud account whose ID is 123456789012\*\*\*\*.

``` {#codeblock_ldt_de5_bjr .language-json}
            "Principal": {
                "RAM": [
                    "acs:ram::123456789012****:user/testuser"                        
```

**Note:** Before modifying the policy, you must ensure that you have created a RAM user named `testuser` whose UPN is testuser@123456789012\*\*\*\*.onaliyun.com.

## Change the trusted entity of a RAM role to a specific Alibaba Cloud service {#section_b5k_b6k_aut .section}

If the `Principal` element contains the `Service` field, the trusted entity is an **Alibaba Cloud service**. The role can be assumed by the trusted Alibaba Cloud service under the current Alibaba Cloud account.

For example, the following policy indicates that the RAM role can be assumed by ECS.

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

## Change the trusted entity of a RAM role to a specific IdP {#section_63s_tna_q1e .section}

If the `Principal` element contains the `Federated` field, the trusted entity is an **IdP**. The RAM role can be assumed by any user in the IdP.

For example, the following policy indicates that the RAM role can be assumed by any user in the IdP named `testprovider`. testprovider is the IdP for the current Alibaba Cloud account whose ID is 123456789012\*\*\*\*.

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
                "StringEquals": {
                    "saml:recipient":"https://signin.alibabacloud.com/saml-role/sso"
                }
            }
        }
    ],
    "Version": "1"
}
```

