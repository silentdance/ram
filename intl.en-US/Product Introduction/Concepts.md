# Concepts {#concept_ant_mt2_xdb .concept}

This document explains the relevant concepts of RAM for your better understanding of the service.

## Identity management related concepts {#section_r4g_qt2_xdb .section}

## Alibaba Cloud account {#section_kjz_nt2_xdb .section}

An Alibaba Cloud account \(primary account\) is the basic entity for judging the ownership of Alibaba Cloud resources and billing for resource consumption. Before you start using Alibaba Cloud services, you must register an Alibaba Cloud account. An Alibaba Cloud account is billed for all the resources under the account and has full permissions for these resources.

By default, a resource can be accessed only by the resource owner. Other users must have explicit authorization from the owner to access the resource. Therefore, from the perspective of permissions management, the Alibaba Cloud account is similar to the root or admin account of an operating system, which is often called root account or primary account.

## Alibaba Cloud account alias {#section_ljz_nt2_xdb .section}

In RAM, a globally unique alias can be set for each Alibaba Cloud account. Aliases are mainly used for RAM user logon and are displayed after a successful logon.

For example, if the alias abc.com is set for the Alibaba Cloud account admin@abc.com, after a RAM user Alice successfully logs on to the Alibaba Cloud console, the displayed name is alice@abc.com.

## Identity credentials {#section_mjz_nt2_xdb .section}

An identity credential is used to verify the real identity of a user. It usually refers to a user’s logon password or AccessKey. Identity credentials are confidential, so users must keep their credentials secure and private.

-   **Logon name/password** You can use the logon name and password to access the Alibaba Cloud console to view orders or bills, buy resources, or perform resource operations.
-   **AccessKey** You can use the AccessKey to construct an API request \(or use cloud service SDKs\) to perform resource operations.
-   **Multi-factor authentication** Multi-Factor Authentication \(MFA\) is a simple but effective best practice that can provide additional security protection apart from usernames and passwords. After MFA is enabled, when a user logs on to Alibaba Cloud website, the system requires the user to enter the username and password \(first security factor\), and then requires the user to enter a variable verification code \(second security factor\) provided by the MFA device. All these factors work together to offer higher security protection for your account.

## RAM-User {#section_ojz_nt2_xdb .section}

The account owner can create multiple RAM users \(corresponding to employees, systems, or applications of an enterprise\) under an Alibaba Cloud account. RAM users have no resources and are not billed independently. The Alibaba Cloud account has all the resources and unified payments of all bills. RAM users belong to an Alibaba Cloud account and are visible only under this account. They are not independent Alibaba Cloud accounts. RAM users can log on to the console or use APIs to perform operations on resources under an Alibaba Cloud account only after being authorized by the Alibaba Cloud account.

RAM supports two types of identities, which are RAM-User and RAM-Role.

-   A RAM-User is a real identity, with a fixed ID and identity credentials. Generally they correspond to specific persons or applications.
-   A RAM-Role is a virtual identity, with no fixed identity credentials. A RAM-Role must be associated with a real identity so that it becomes available.

## RAM-Role {#section_qjz_nt2_xdb .section}

RAM role The traditional role \(textbook-style role\) is a set of permissions, which are similar to policies in RAM. If a user is assigned a role, it means that the user is given a set of permissions, and the user can access authorized resources.

The RAM role is different from the textbook role. The RAM role is a virtual user \(or shadow account\), which is a type of RAM user. This type of virtual user has a fixed ID and can also be assigned a set of permissions \(policy\), but the user does not have a fixed identity authentication key \(logon password or AccessKey\). The difference between the RAM role and the ordinary RAM user mainly lies in the usage method. The RAM role needs to be played by an authorized entity user. After the successful play, the entity user will obtain the temporary security token of the RAM role. The temporary security token can be used to access authorized resources as the role identity.

The differences between RAM-Role and Textbook-Role are as follows:

-   \(Similarities\) RAM-Roles and Textbook-Roles can both be bound to a permissions set.
-   \(Differences\) A RAM-Role is a virtual identity or shadow account. It has an independent ID. Permissions need to be bound to a RAM-Role and a list of users with this role \(Roleplayers\). It is mainly used to solve problems related to  Identity Federation. A Textbook-Role generally only indicates a permissions set. It is not an identity and is mainly used to simplify authorization management.

    **RAM-Role role assumption and switching**

-   Switch from a logon identity to a role identity \(SwitchRole\): After an actual user \(such as a RAM-User\) logs on to the console, the user can choose to **Switch to a role** if the entity user is already associated with the role. A user can only switch to one role at a time. When the user switches from a **logon identity** to a **role identity**, the user can only use the permissions granted to this role identity. He can no longer use the permissions granted to the logon identity. If the user needs to use logon identity permissions, he must switch from the role identity back to the logon identity.
-   Call a program to assume a role \(AssumeRole\): If an actual user \(such as a RAM-User\) is associated with a RAM-Role, this user can use an AccessKey to call the AssumeRole interface of the STS service to obtain a temporary AccessKey for this RAM-Role. The temporary AccessKey has a validity period and restricted access permissions \(not beyond the permission set bound to the role\). Generally temporary access keys are used to resolve temporary authorization problems.

**RAM related concepts**

## Resources {#section_sjz_nt2_xdb .section}

Resources are abstractions of the objects that are presented by a cloud service to users and used for interaction with users, such as OSS buckets, OSS objects and ECS instances.

We have defined a global Alibaba Cloud Resource Name \(ARN\) for each resource. The format is as follows:

```
acs:<service-name>:<region>:<account-id>:<resource-relative-id>
```

**Format description:**

-   acs: This is the abbreviation of Alibaba Cloud Service, indicating an Alibaba Cloud public cloud platform.
-   service-name: This indicates the name of an open service provided by Alibaba Cloud, such as ECS \(ecs\), OSS \(oss\), or ODPS \(odps\).
-   region: This indicates region information. If this option is not supported, use the wildcard “\*” instead.
-   account-id: This is an account ID, such as `1234567890123456`.
-   resource-relative-id: This indicates the service-related resource. Its meaning varies with specific services of types.  Using OSS as an example, `acs:oss::1234567890123456:sample_bucket/file1.txt` indicates an OSS resource of the public cloud platform, where `sample_bucket/file1.txt` indicates the OSS object name, and `1234567890123456` indicates the object owner.

## Permissions {#section_vjz_nt2_xdb .section}

A permission is used to allow or deny a user to perform a certain operation on a particular cloud resource.

Operations can be divided into two main categories: **resource control operations**  and **resource use operations**.

-   Resource control operations indicate cloud resource lifecycle management and O&M management operations, such as ECS instance creation, stopping, and restart and OSS bucket creation, modification, and deletion. Resource control operations are generally oriented to resource buyers or O&M employees in your organization.
-   Resource use operations indicate the use of resources’ core functions, such as user operations in an ECS instance operating system and  OSS bucket data upload/download. Resource use operations are oriented to R&D employees or application systems in your organization.

    **Note:** For elastic computing and database products, resource control operations can be managed using RAM, while resource use operations can be managed in each product instance. For example, ECS instance OS permission control or MySQL database permission control. For storage-type products, such as OSS and Table Store, resource control operations and resource use operations can both be managed through RAM.


## Policies {#section_xjz_nt2_xdb .section}

A policy is a type of simple language specification that describes a permission set. For the language specifications supported by RAM, see [Policy syntax structure](../../../../intl.en-US/User Guide/Policy Language/Policy syntax structure.md). RAM supports two types of authorization policies: **system access policies** and **custom access policies**.

-   You can use but cannot modify the system access policies managed by Alibaba Cloud. Alibaba Cloud automatically updates the system access policy version.
-   You can create or delete the custom access policies. In addition, you must maintain the policy version by yourself.

