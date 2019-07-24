# Overview of a RAM role {#concept_fgc_wjc_mfb .concept}

A RAM role is a RAM identity that you can create in your Alibaba Cloud account. A role does not have standard long-term credentials such as a password or an access key. You must first specify a trusted entity that can assume a RAM role before you use the role.

## Related concepts {#section_f2y_k4d_nfb .section}

![Related concepts](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23744/156394991914225_en-US.png)

 RAM role
 :   A virtual identity that you can create in your Alibaba Cloud account. The differences among RAM roles, entity users \(Alibaba Cloud account, RAM users, or Alibaba Cloud services\), and textbook roles are as follows:

    -   Entity users have specific logon passwords or access keys.
    -   A textbook role \(or a traditionally defined role\) indicates a permission set, similar to a policy in RAM. If such a role is granted to a user, the user has a set of permissions and can access the authorized resources.
    -   As virtual users, RAM roles have specific identities and can be granted a set of policies. However, RAM roles do not have standard long-term credentials \(passwords or access keys\). When an entity user wants to use a role, the user must assume the role to obtain the role token. Then, the user can use the role token to call Alibaba Cloud API actions.

  ARN
 :   The Alibaba Cloud Resource Name \(ARN\) of a RAM role. Each role has a unique ARN. For example, the ARN of the RAM role `devops` under an Alibaba Cloud account is `acs:ram::123456789012****:role/samplerole`. After you create a RAM role, you can click the role name and find its ARN on the Basic Information page.

  Trusted entity
 :   The trusted entity that can assume a RAM role. You must specify a trusted entity when you create a RAM role. Only trusted entities can assume RAM roles. The trusted entity can be an Alibaba Cloud account, Alibaba Cloud service, or identity provider \(IdP\).

  Policy
 :   A set of permissions that are described by using policy structure and grammar. Roles that are not attached to any policy can exist, but cannot access resources.

  Role assuming
 :   The method for entity users to obtain security tokens of RAM roles. By calling the AssumeRole action of STS, an entity user can obtain the security token of a role and use the token to access Alibaba Cloud service APIs.

  Identity switching
 :   The method by which entity users can switch from the logon identity to role identity in the RAM console. After logging on to the RAM console, an entity user can switch to a RAM role that the user can assume. The user can then use the role identity to operate Alibaba Cloud resources. When the user no longer needs the role identity, the user can switch back to its logon identity.

  Role token
 :   A temporary access key to a role identity. RAM roles do not have standard long-term credentials \(passwords or access keys\). When an entity user wants to use a role, the user must assume the role to obtain the role token. Then, the user can use the role token to call Alibaba Cloud API actions.

 ## Access to Alibaba Cloud resources by using a RAM role {#section_87u_bb6_s05 .section}

![Access to Alibaba Cloud resources by using a RAM role](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23744/156394991914219_en-US.png)

1.  The Alibaba Cloud account specifies a trusted entity that can assume the RAM role.
2.  The trusted entity logs on to the console or calls an API action to assume the role and obtains a role token.

    -   The trusted entity can assume the role by switching its identity in the console. For more information, see [Assume a RAM role](reseller.en-US/User Guide/RAM roles/Assume a RAM role.md#).
    -   The trusted entity can assume the role by calling the AssumeRole action.
    **Note:** An entity user can obtain a role token by assuming a RAM role and then use the token to access Alibaba Cloud resources.

3.  The Alibaba Cloud account attaches a policy to the RAM role. For more information, see [Grant permission to a RAM role](reseller.en-US/User Guide/RAM roles/Grant permission to a RAM role.md#).

    **Note:** A RAM role can have one or more polices attached. A RAM role without a policy cannot access Alibaba Cloud resources.

4.  The trusted entity assumes the RAM role and uses a temporary STS token to access Alibaba Cloud resources.

## RAM role types {#section_01 .section}

RAM roles are divided into the following types according to different trusted entities:

-   Alibaba Cloud account: roles that RAM users can assume. The RAM users may belong to their own Alibaba Cloud accounts or other Alibaba Cloud accounts. Such roles provide solutions to cross-account access and temporary authorization.
-   Alibaba Cloud service: roles that Alibaba Cloud services can assume. Such roles are used to authorize Alibaba Cloud services to operate resources as stand-alone applications.
-   IdP: roles that users in an entrusted IdP can assume. Such roles are used to implement Single Sign On \(SSO\) to Alibaba Cloud.

## Application scenarios {#section_yhg_nzp_4fb .section}

-   [Grant temporary permissions to mobile apps](../../../../reseller.en-US/Best Practices/Grant temporary permissions to mobile apps.md#)
-   [Cross-account resource authorization and access](../../../../reseller.en-US/Best Practices/Cross-account resource authorization and access.md#)
-   [../../../../dita-oss-bucket/SP\_65/DNRAM11894803/EN-US\_TP\_23777.md\#](../../../../reseller.en-US/Best Practices/Dynamic identity and permission management of cloud applications.md#)

