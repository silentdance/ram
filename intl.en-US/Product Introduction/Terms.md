# Terms {#concept_ant_mt2_xdb .concept}

This topic explains terms that are commonly used in Alibaba Cloud RAM.

## Alibaba Cloud account {#section_ken_41b_lrk .section}

An Alibaba Cloud account, also known as the root account or primary account, is the account type used to own Alibaba Cloud resources and manage the billing of these resources. You must register an Alibaba Cloud account before using Alibaba Cloud services. An Alibaba Cloud account owner has full operational control over all associated resources. Furthermore, the account owner can manage the payment for all resources under the Alibaba Cloud account \(including fees incurred by RAM users under this account\).

By default, a resource can be accessed only by the owner of an Alibaba Cloud account. Other users must be granted the corresponding authorization from the owner to access and operate on the resource. As a result, the Alibaba Cloud account functions similar to that of the root user or administrator of an operating system.

## Terms related to identity management {#section_d7u_3t7_vtx .section}

## Identity {#section_d13_ajj_5qs .section}

Identities can be created in RAM to allow or deny access to resources in your Alibaba Cloud account. RAM users, RAM user groups, and RAM roles are identities that you can create in RAM. RAM users and RAM user groups are entity identities, whereas RAM roles are virtual identities.

## Default domain name {#section_okb_3dj_e1w .section}

A unique identifier of an Alibaba Cloud account that is used in scenarios such as RAM user logon. Alibaba Cloud assigns a default domain name for each Alibaba Cloud account in the `<AccountAlias>.onaliyun.com` format.

For information about how to set a default domain name, see [Manage the default domain name of an Alibaba Cloud account](../../../../reseller.en-US/User Guide/Security settings/Advanced settings/Manage the default domain name of an Alibaba Cloud account.md#).

## Enterprise alias {#section_g2p_rh1_95e .section}

To log on to the RAM console, a RAM user must have a username that contains the enterprise alias, default domain name, or domain alias as a suffix.

The enterprise alias is a unique account identifier that appears at the end of the RAM user's username and forms part of the RAM user's display name after logon.

For example, a company named company1 sets company1 as its enterprise alias. The RAM user Alice can then use alice@company1 to log on to the RAM console. The display name of RAM user Alice is then alice@company1.

## Domain alias {#section_c87_ajg_wsm .section}

A custom domain name that can be used to replace the default domain name provided by the system.

**Note:** A domain alias can be used only after domain ownership verification.

For information about how to set a domain alias, see [Create a domain alias for an Alibaba Cloud account](../../../../reseller.en-US/User Guide/Security settings/Advanced settings/Create a domain alias for an Alibaba Cloud account.md#).

## RAM user {#section_ty7_tyy_31d .section}

An identity with a fixed ID and credential information. Specifically, a RAM user directly corresponds to a specific identity, which can be either a person or an application.

-   An Alibaba Cloud account owner can create multiple RAM users \(which correspond to employees, systems, or applications of their enterprise\) under their account.
-   RAM users do not own resources. Rather, the fees incurred by RAM users are billed to the Alibaba Cloud accounts to which they belong. RAM users do not receive individual bills and cannot make payments.
-   RAM users are visible only to the corresponding Alibaba Cloud account to which they belong.
-   RAM users have permissions for only the Alibaba Cloud resources under the Alibaba Cloud account to which they belong after they are authorized to operate on these resources.

For information about how to create a RAM user, see [Create a RAM user](../../../../reseller.en-US/User Guide/RAM users/Create a RAM user.md#).

## Password {#section_5sl_484_xbj .section}

An identity credential that is used by a user to log on to Alibaba Cloud.

**Note:** We recommend that you change your password periodically and keep your password private.

For information about how to set a password, see [Change the password for an Alibaba Cloud account](../../../../reseller.en-US/User Guide/Security settings/Passwords/Change the password for an Alibaba Cloud account.md#) and [Change the password for a RAM user](../../../../reseller.en-US/User Guide/Security settings/Passwords/Change the password for a RAM user.md#).

## Access key {#section_41b_bdb_14h .section}

The combination of an access key ID and an access key secret. You can use your access key or Alibaba Cloud SDK to sign API requests that you make to Alibaba Cloud.

The access key ID and access key secret are used together to sign programmatic Alibaba Cloud requests cryptographically. The access key ID is used to identify a user, whereas the access key secret is used to encrypt and verify a signature.

**Note:** The access key secret is displayed only once when you first create it. We recommend that you save the access key secret for subsequent use.

For information about how to create an access key, see [Create an access key for a RAM user](../../../../reseller.en-US/User Guide/Security settings/Access keys/Create an access key for a RAM user.md#).

## Multi-factor authentication \(MFA\) {#section_rto_w6u_64w .section}

A simple best practice that adds an extra layer of protection on top of your username and password. When you log on to Alibaba Cloud with MFA enabled, the system requires the following two security factors:

1.  Your username and password
2.  Verification code provided by the MFA device

For information about how to set MFA, see [Enable an MFA device for an Alibaba Cloud account](../../../../reseller.en-US/User Guide/Security settings/Multi-factor authentication/Enable an MFA device for an Alibaba Cloud account.md#) and [Enable an MFA device for a RAM user](../../../../reseller.en-US/User Guide/Security settings/Multi-factor authentication/Enable an MFA device for a RAM user.md#).

## RAM user group {#section_rwm_6ht_krb .section}

A type of entity identity in RAM. You can create RAM user groups to classify and organize RAM users under your Alibaba Cloud account. By classifying and organizing your RAM users, you can effectively manage permissions in the RAM console.

-   If the responsibilities of a RAM user change, you only need to move the user to a RAM user group with the appropriate permissions. This action does not affect other RAM users.

    For information about how to create a RAM user group, see [Create a RAM user group](../../../../reseller.en-US/User Guide/RAM user groups/Create a RAM user group.md#).

-   If the responsibilities of a RAM user group change, you only need to modify the policy attached to the user group. Changes to the policy apply to all RAM users in the group.

    For information about how to grant permission to a RAM user group, see [Grant permission to a RAM user group](../../../../reseller.en-US/User Guide/RAM user groups/Grant permission to a RAM user group.md#).


## RAM role {#section_j4a_qpf_28a .section}

A virtual identity that you can create in your Alibaba Cloud account. The differences among RAM roles, entity users \(Alibaba Cloud account, RAM users, or Alibaba Cloud services\), and textbook roles are as follows:

-   Entity users have specific logon passwords or access keys.
-   A textbook role \(or a traditionally defined role\) indicates a permission set, similar to a policy in RAM. If such a role is granted to a user, the user has a set of permissions and can access the authorized resources.
-   As virtual users, RAM roles have specific identities and can be granted a set of policies. However, RAM roles do not have standard long-term credentials \(passwords or access keys\). When an entity user wants to use a role, the user must assume the role to obtain the role token. Then, the user can use the role token to call Alibaba Cloud API actions.

RAM roles are divided into the following types according to different trusted entities:

-   Alibaba Cloud account: roles that RAM users can assume. The RAM users may belong to their own Alibaba Cloud accounts or other Alibaba Cloud accounts. Such roles provide solutions to cross-account access and temporary authorization.
-   Alibaba Cloud service: roles that Alibaba Cloud services can assume. Such roles are used to authorize Alibaba Cloud services to operate resources as stand-alone applications.

For information about how to create a RAM role, see

-   [Create a RAM role for a trusted Alibaba Cloud account](../../../../reseller.en-US/User Guide/RAM roles/Create a RAM role/Create a RAM role for a trusted Alibaba Cloud account.md#)
-   [Create a RAM role for a trusted Alibaba Cloud service](../../../../reseller.en-US/User Guide/RAM roles/Create a RAM role/Create a RAM role for a trusted Alibaba Cloud service.md#)

## Terms related to access control {#section_op3_gvn_tdt .section}

## Permission {#section_1xu_e22_yts .section}

A statement within a policy that allows or denies access to a particular Alibaba Cloud resource.

Permission can be used to authorize the following operations:

-   Resource management and control operations: Used to allow managing the cloud resources, such as creating, stopping, and restarting ECS instances, or creating, modifying, and deleting OSS buckets. Such operations are intended for resource purchasers or O&M engineers in your organization.
-   Resource-use operations: Used to allow core operations related to resources, such as operating an ECS instance operating system, and uploading or downloading OSS bucket data. Such operations are intended for R&D engineers or application systems in your organization.

    **Note:** 

    -   For ECS and database services, resource management and control operations can be managed through RAM, whereas resource-use operations can be managed through the instances of each product \(for example, by using the permission control function provided by the ECS instance operating system or by the MySQL database running on the instance\).
    -   For storage services, such as OSS and Table Store, both types of operations can be managed by using RAM.

## Policy {#section_bcp_6w6_8j6 .section}

A set of permissions that are described by using policy structure and grammar. It can accurately describe the authorized resource sets, operation sets, and authorization conditions a user can be granted with. For information about structures and grammars supported by RAM, see [Policy structure and grammar](../../../../reseller.en-US/User Guide/Policies/Policy language/Policy structure and grammar.md#).

In RAM, a policy is a resource entity that can be created, updated, deleted, and viewed by RAM users. RAM supports the following two types of policies:

-   System policy: System policies are created by Alibaba Cloud and cannot be modified by users. The policies are automatically upgraded by Alibaba Cloud.
-   Custom policy: If no system policy meets your requirements, you can create a custom policy as needed. You can also modify and delete a custom policy as needed.

You can attach one or more policies to RAM users, RAM user groups, or RAM roles. For more information, see [Grant permission to a RAM user](../../../../reseller.en-US/User Guide/RAM users/Grant permission to a RAM user.md#), [Grant permission to a RAM user group](../../../../reseller.en-US/User Guide/RAM user groups/Grant permission to a RAM user group.md#), and [Grant permission to a RAM role](../../../../reseller.en-US/User Guide/RAM roles/Grant permission to a RAM role.md#).

## Principal {#section_30z_nfh_hnz .section}

The RAM user, group, or role that receives permissions that are defined in a policy.

## Effect {#section_9bt_0ph_wf4 .section}

A policy element that specifies whether the statement results in an allow or an explicit deny. The valid values are `Allow` and `Deny`.

## Action {#section_ln8_om7_37u .section}

A policy element that describes the specific API action or actions that will be allowed or denied.

## Condition {#section_o17_y91_kwv .section}

A policy element that specifies when a policy takes effect.

## Resource {#section_53h_ei7_653 .section}

An entity that users can work with in Alibaba Cloud, such as an OSS bucket and an ECS instance.

