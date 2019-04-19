# Terms {#concept_ant_mt2_xdb .concept}

This topic explains terms that are commonly used in Alibaba Cloud RAM.

## Alibaba Cloud account {#section_kjz_nt2_xdb .section}

An Alibaba Cloud account, also known as the root account or primary account, is the account type used to own Alibaba Cloud resources and manage the billing of these resources. You must register an Alibaba Cloud account before using Alibaba Cloud services. An Alibaba Cloud account owner has full operational control over all associated resources. Furthermore, the account owner can manage the payment for all resources under the Alibaba Cloud account \(including fees incurred by RAM users under this account\).

By default, a resource can be accessed only by the owner of Alibaba Cloud account. Other users must be granted the corresponding authorization from the owner to access and operate on the resource. As a result, the Alibaba Cloud account functions similar to that of the root user or administrator of an operating system.

## RAM user {#section_nfd_yoe_31v .section}

A RAM user is an identity with a fixed ID and credential information. Generally, a RAM user directly corresponds to a specific identity, which can be either a person or an application.

-   An Alibaba Cloud account owner can create multiple RAM users \(which correspond to employees, systems, or applications of their enterprise\) under their account.
-   RAM users do not own resources. Rather, the fees incurred by RAM users are billed to the Alibaba Cloud accounts to which they belong. RAM users do not receive individual bills and cannot make payments.
-   RAM users are visible only to the corresponding Alibaba Cloud account to which they belong.
-   RAM users have permissions for only the resources under the Alibaba Cloud account to which they belong after they are authorized to operate on these resources.

## RAM role {#section_qs4_dla_hic .section}

A RAM role is a virtual identity with a fixed ID but without an identity authentication key. A RAM role must be associated with the identity of a target entity before it can be used for a valid role.

More specifically, RAM roles can be used only after they are assumed by a user or service of a trusted entity. The user or service obtains the temporary security tokens of RAM roles, and then uses these tokens to access the authorized resources.

RAM roles can be associated with the following trusted entities:

-   **Alibaba Cloud account:** a type of role that RAM users can assume. The RAM users may belong to their own Alibaba Cloud account or another Alibaba Cloud account. Such type of role can be assumed to achieve cross-account access through temporary authorization.
-   **Alibaba Cloud service:** a type of role that cloud services can assume. Such type of role can be used to authorize cloud services to operate resources as stand-alone applications.
-   **Identity provider \(IdP\):** a type of role that users in a trusted identity provider \(IdP\) can assume. Such type of role can be used to implement Single Sign On \(SSO\) to Alibaba Cloud.

## Identity credential {#section_gqr_ce5_uxl .section}

An identity credential is used to verify the real identity of a user. Generally, an identity credential refers to the logon password or AccessKey \(AK\) of a RAM user.

**Note:** Identity credentials are necessary for account security, so we recommend that you keep your credentials secure and private.

An identity credential usually contains the following:

-   **Logon name and password:** You can use your logon name and password to access the Alibaba Cloud console to view order or billing information, or to purchase or operate on resources.
-   **AccessKey \(AK\):** You can use your AK to create an API request, or to use a cloud service SDK to operate on resources.
-   **Multi-Factor Authentication \(MFA\):** MFA is a simple but effective means for achieving a higher level security protection. When you log on to Alibaba Cloud with MFA enabled, the system requires the following two security factors:
    -   Your username and password
    -   The verification code provided by your target virtual MFA device

## Account alias {#section_ljz_nt2_xdb .section}

To log on to the RAM console, a RAM user must have a username that contains the account alias, default domain name, or domain alias as a suffix.

The alias is a unique account identifier that appears at the end of the RAM user's username and forms part of the RAM user's display name after logon.

For example, a company named company1 sets company1 as its account alias. The RAM user Alice can then use alice@company1 to log on to the RAM console. The display name of RAM user Alice is then alice@company1.

## Default domain name {#section_mjz_nt2_xdb .section}

A unique identifier of an Alibaba Cloud account that is used in scenarios such as RAM user logon and SSO management. Alibaba Cloud assigns a **default domain name** for each account in the format `<AccountAlias>.onaliyun.com`.

## Domain alias {#section_6ay_t5p_or5 .section}

A custom domain name that can be used to replace the default domain name provided by the system.

**Note:** A domain alias can be used only after domain ownership verification.

## Single Sign On \(SSO\) {#section_kvm_4vj_w71 .section}

Enterprises can implement SSO to Alibaba Cloud through an SAML 2.0-based IdP. Alibaba Cloud offers the following two SAML 2.0-based SSO methods:

-   User-based SSO: After logging on, an Enterprise employee can use the RAM user to access Alibaba Cloud.
-   Role-based SSO: Enterprises can manage their employees with their IdP with no need of synchronizing user information to Alibaba Cloud. In addition, an Enterprise employee can use a specified role to access Alibaba Cloud.

## Permission {#section_jcr_ggc_f8c .section}

The means by which you can allow or deny a user to be authorized to perform certain operations on a particular cloud resource.

Permission can be used to authorize the following operations:

-   Resource management and control operations: Used to allow managing the cloud resources, such as creating, stopping, and restarting ECS instances, or creating, modifying, and deleting OSS buckets. Such operations are intended for resource purchasers or O&M engineers in your organization.
-   Resource-use operations: Used to allow core operations related to resources, such as operating an ECS instance operating system, and uploading or downloading OSS bucket data. Such operations are intended for R&D engineers or application systems in your organization.

    **Note:** 

    -   For ECS and database services, resource management and control operations can be managed through RAM, whereas resource-use operations can be managed through the instances of each product \(for example, by using the permission control function provided by the ECS instance operating system or by the MySQL database running on the instance\).
    -   For storage services, such as OSS and Table Store, both types of operations can be managed by using RAM.

## Policy {#section_luj_a8f_ren .section}

A specification that defines a permission for an identity or resource on Alibaba Cloud. For more information about the policies supported by RAM, see [Policy syntax structure](../../../../reseller.en-US//Policy Language/Policy syntax structure.md).

RAM supports two types of policies:

-   System policies: Policies managed by Alibaba Cloud. You can use but cannot modify these policies. Alibaba Cloud automatically updates system policy versions.
-   Custom policies: Policies managed by Alibaba Cloud account owners or RAM users. You can create or delete the custom access policies at any time. However, you must maintain custom policy versions by yourself.

## Resource {#section_sjz_nt2_xdb .section}

An object that serves as a service package provided by Alibaba Cloud. OSS buckets, OSS objects, and ECS instances are examples of resources.

A global Alibaba Cloud Resource Name \(ARN\) is defined for each resource on Alibaba Cloud. The format of an ARN is as follows:

 `acs:<service-name>:<region>:<account-id>:<resource-relative-id>` 

For more information, see [Policy elements](../../../../reseller.en-US/User Guide/Permission management/Policy language/Policy elements.md#).

