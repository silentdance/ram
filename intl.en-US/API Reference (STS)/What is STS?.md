# What is STS? {#reference_ong_5nv_xdb .reference}

Alibaba Cloud Security Token Service \(STS\) provides short-term access management for Alibaba Cloud accounts or RAM users.

## Features {#section_xsr_q4v_xdb .section}

STS grants temporary access tokens to authorized RAM entities \(RAM users, RAM user groups, or RAM roles\). The validity period and access permissions of these temporary access tokens can be customized as needed. Authorized RAM entities with temporary STS tokens can access Alibaba Cloud resources by using either of the following methods:

-   Call Alibaba Cloud API actions.
-   Log on to the Alibaba Cloud console.

## Endpoint {#section_et2_on2_zqb .section}

The endpoint of STS that is used to call API actions is `https://sts.aliyuncs.com`.

## Commonly used terms {#section_f7s_vhy_40q .section}

 RAM role
 :   A virtual RAM user.

  ARN
 :   The Alibaba Cloud Resource Name \(ARN\) of a RAM role. Each role has a unique ARN.

    Format: `acs:ram::$accountID:role/$roleName`

  Trusted entity
 :   The trusted entity that can assume a RAM role. You must specify a trusted entity when you create a RAM role. Only trusted entities can assume roles. The trusted entity can be an Alibaba Cloud account, Alibaba Cloud service, or identity provider \(IdP\).

  Role assuming
 :   The method for entity users to obtain security tokens of RAM roles. By calling the [AssumeRole](reseller.en-US/API Reference (STS)/Operation interfaces/AssumeRole.md#) action, an entity user can obtain the security token of a role and use the token to access Alibaba Cloud service APIs.

 
