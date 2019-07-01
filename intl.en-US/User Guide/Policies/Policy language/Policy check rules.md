# Policy check rules {#concept_xgf_ldk_xdb .concept}

This topic describes the policy check rules to help you better understand RAM policies.

## Check rules {#section_vgn_mdk_xdb .section}

You can access Alibaba Cloud resources in RAM by using an Alibaba Cloud account, or as an authorized RAM user or RAM role.

RAM determines whether to allow access according to the rules described in the following table.

|Access type|Rules|
|:----------|:----|
|Alibaba Cloud account|The Alibaba Cloud account is the resource owner and can access all Alibaba Cloud resources under the account. **Note:** Some Alibaba Cloud services, such as Log Service, support cross-account ACL authorization. If ACL authorization is successful, access is allowed even the Alibaba Cloud account is not the resource owner.

 |
|RAM user| -   The Alibaba Cloud account has attached a policy with explicit allow effect to the RAM user.
-   The Alibaba Cloud account to which the RAM user belongs has permission to access specific Alibaba Cloud resources.

 **Note:** By default, a RAM user does not have any permissions to access Alibaba Cloud resources. The user can access Alibaba Cloud resources only when both of the preceding rules are met.

 For information about how to check the permissions of a RAM user, see [Policy check rules for RAM users](#section_ahn_mdk_xdb).

 |
|RAM role| -   The STS token of the RAM role has the required permissions.

For more information about RAM role STS tokens, see [What is STS?](../../../../reseller.en-US/API Reference (STS)/What is STS?.md#)

-   The Alibaba Cloud account has attached a policy with explicit allow effect to the RAM role.
-   The Alibaba Cloud account to which the RAM role belongs has permission to access specific Alibaba Cloud resources.

 **Note:** By default, a RAM role does not have any permissions to access Alibaba Cloud resources. The role can access Alibaba Cloud resources only when all the preceding rules are met.

 For information about how to check the permissions of a RAM role, see [Policy check rules for RAM roles](#section_ghn_mdk_xdb).

 |

## Policy check rules for RAM users {#section_ahn_mdk_xdb .section}

By default, RAM users do not have resource access permissions unless they have been granted explicit permission by the Alibaba Cloud account.

**Note:** A policy can contain `Allow` and `Deny` statements. If policies that apply to a request include an `Allow` statement and a `Deny` statement, the `Deny` statement trumps the `Allow` statement.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23771/156195222414405_en-US.png)

When you access Alibaba Cloud resources as a RAM user, the system checks the policies as follows:

1.  Whether the policy attached to the RAM user has a `Deny` statement:
    -   If yes, access is denied.
    -   If no, go to the next step.
2.  Whether the policy attached to the Alibaba Cloud account of the RAM user has an `Allow` statement:
    -   If yes, access is allowed.
    -   If no, go to the next step.
3.  Whether the Alibaba Cloud account of the RAM user has cross-account ACL authorization:
    -   If yes, access is allowed.
    -   If no, access is denied.

## Policy check rules for RAM roles {#section_ghn_mdk_xdb .section}

You can access Alibaba Cloud resources as a RAM role by using an STS token and calling the [AssumeRole](../../../../reseller.en-US/API Reference (STS)/Operation interfaces/AssumeRole.md#) action. The Policy parameter specifies the resource access permission or permissions.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23771/156195222448452_en-US.png)

When you access Alibaba Cloud resources as a RAM role, the system checks the policies as follows:

1.  Whether a policy is attached to the STS token:
    -   If a policy is attached to the STS token, the system checks whether the policy has a `Deny` statement.
        -   If yes, access is denied.
        -   If no, the system checks the policy attached to the RAM role.
    -   If no policy is attached to the STS token, the system checks the policy attached to the RAM role.
2.  Whether the policy attached to the RAM role has a `Deny` statement:
    -   If yes, access is denied.
    -   If no, go to the next step.
3.  Whether the policy attached to the Alibaba Cloud account of the RAM role has an `Allow` statement:
    -   If yes, access is allowed.
    -   If no, go to the next step.
4.  Whether the Alibaba Cloud account of the RAM role has cross-account ACL authorization:
    -   If yes, access is allowed.
    -   If no, access is denied.

