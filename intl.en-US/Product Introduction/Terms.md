# Terms {#concept_ant_mt2_xdb .concept}

This topic defines commonly used terms in the Alibaba Cloud RAM service.

## Terms related to identity management {#section_r4g_qt2_xdb .section}

## Account {#section_kjz_nt2_xdb .section}

The basic entity for identifying the ownership of Alibaba Cloud resources and measuring and billing the corresponding resources. Before using Alibaba Cloud services, you must register an account. An account owner has full control over all of its resources, and manages payment for all resources under its account \(including fees incurred by RAM users under the account\)

By default, a resource can be accessed only by its owner \(ResourceOwner\). Other users can access the resource only after they obtain the corresponding authorization from the owner. Therefore, from the perspective of permission management, an account plays a role similar to the root user or administrator of an operating system \(OS\). Such an account is also called the root account or primary account.

## Account alias {#section_ljz_nt2_xdb .section}

A parameter that, in RAM, each account can set as a globally unique account identifier. The alias is mainly used for RAM user logon, and is presented as a display name after logon.

For example, a company named company1 sets company1 as its account alias. The RAM user alice can then use alice@company1 to log on to the RAM console. The displayed name of RAM user alice is then alice@company1.

## Default domain name and domain alias of an account {#section_mjz_nt2_xdb .section}

**Default domain name**

A unique identifier of an account that is used in scenarios such as RAM user logon and identity federation management. Alibaba Cloud assigns a **default domain name** for each account in the format `<AccountAlias>.onaliyun.com`.

With a default domain name, you can name a RAM user in the standard format, for example, alice@company1.onaliyun.com.

**Domain alias**

If you have a domain name that can be parsed on the Internet, you can replace the default domain name with your custom domain name. Such a domain name is called **domain alias**.

**Note:** A domain alias can be used only after it passes domain ownership verification. After the verification, you can use the domain alias in all scenarios where the default domain name is required.

A RAM user with a suffix of the account alias, default domain name, or domain alias after their user name can log on to the RAM console.

## Identity credential {#section_mjz_nt2_xdc .section}

A credential component that is used to verify the real identity of a user. Generally, identity credential refers to a user's logon password or AccessKey \(AK\). Identity credentials are necessary for account security, so users are strongly recommended to keep their credentials secure and private. The following components are typically involved in an identity credential:

-   **Logon name/password \(Password\)**: You can use your logon name and password to access the Alibaba Cloud console to view orders or bills, and purchase or operate resources.
-   **AK \(AccessKey\)**: You can use your AK to construct an API request \(or use a cloud service SDK\) to operate resources.
-   **Multi-Factor Authentication \(MFA\)**: MFA is a simple but effective best practice that can provide additional security protection compared with traditional user name and password methods. When you log on to Alibaba Cloud with MFA enabled, the system requires two security factors:

    -   The first security factor is your user name and password.
    -   The second security factor is the variable verification code provided by your target virtual MFA device.
    When combined, these authentication factors greatly increase the security of your account.


## RAM user {#section_ojz_nt2_xdb .section}

A type of sub-user under the account \(account owner\). An account owner can create multiple RAM users \(corresponding to employees, systems, or applications of an enterprise\) under their account. RAM users do not own resources, cannot function independently from the corresponding account, and have no measurement or billing permissions. Instead, the account has full control over its corresponding RAM users and pays the fees associated to them. Additionally, the RAM users are visible only to the corresponding account. RAM users can log on to the RAM console or use APIs to operate the resources under the account only after being authorized by the account.

RAM user identities are divided into:

-   **RAM user**, which includes entity identities with fixed IDs and identity credentials. Generally, a RAM user is associated with a specific person or application \(a physical identity\).
-   **RAM role**, which is a virtual identity without fixed identity credentials. A RAM role must be associated with an entity identity for it to become valid.

## RAM role {#section_qjz_nt2_xdb .section}

A type of RAM user but of a virtual identity. RAM roles can be granted a set of policies. However, RAM roles do not have fixed identity credentials \(logon passwords or AKs\).

RAM roles and RAM users are different in usage. RAM roles can be used only after being assumed by a trusted entity. The entity obtains temporary security tokens of the RAM role, and then use the token to access the authorized resources as role identities.

-   **Role assuming and switching**

-   A trusted entity can switch from the logon identity to a role identity \(SwitchRole\): After a trusted entity \(for example, a RAM user\) logs on to the RAM console, the RAM user can click **Switch Role** if the trusted entity has been associated with a role. The RAM user can only switch to one role at a time. When the RAM user switches from the logon identity to a role identity, the RAM user can only use the permissions granted to the role identity, and the permissions bound to the logon identity are temporarily unavailable. If the RAM user needs to use permissions of the logon identity, the RAM user must switch from the role identity back to the logon identity.
-   A trusted entity can assume a role by calling an application \(AssumeRole\): If the trusted entity \(for example, a RAM user\) is associated with a RAM role, the RAM user can use an AK to call the AssumeRole API of Security Token Service \(STS\) to obtain a temporary AK of the RAM role. The temporary AK has a validity period and restricted access permissions \(within the permission set bound to the role\). The temporary AK is used to resolve temporary authorization problems.

**Terms related to access control**

## Resource {#section_sjz_nt2_xdb .section}

An abstraction of the objects that are presented by a cloud service to users and are used for interaction with users. OSS buckets, OSS objects, and ECS instances are examples of resources.

Alibaba Cloud has defined a global Aliyun Resource Name \(ARN\) for each resource. The format is as follows:

```
acs:<service-name>:<region>:<account-id>:<resource-relative-id>
```

**where:**

-   `acs` is the abbreviation of Alibaba Cloud Service, indicating the public cloud platform of Alibaba Cloud.
-   `service-name` indicates the name of a cloud service provided by Alibaba Cloud, such as `ecs` \(ECS\) and `oss` \(OSS\).
-   `region` indicates region information. If this option is not supported, the wildcard "\*" is used instead.
-   `account-id` indicates an account ID, for example, `1234567890123456`.
-   `resource-relative-id` indicates resources related services. Its meaning changes based on the specific service type. For example, `acs:oss::1234567890123456:sample_bucket/file1.txt` indicates an OSS resource on the public cloud platform, where `sample_bucket/file1.txt` indicates the OSS object name and `1234567890123456` indicates the object owner.

## Permission {#section_vjz_nt2_xdb .section}

An action by which you can allow or deny a user to perform certain operations on a particular cloud resource.

Permission operations can be divided into:

-   **Resource management and control operations**, which indicate managing the cloud resource life cycle and operating and maintaining resources, for example, creating, stopping, and restarting ECS instances, or creating, modifying, and deleting OSS buckets. Such operations are intended for resource purchasers or O&M employees in your organization.
-   **Resource use operations**, which indicate using core functions of resources, for example, operating an ECS instance OS and uploading/downloading OSS bucket data. Such operations are intended for R&D employees or application systems in your organization.

    **Note:** For ECS and database products, resource management and control operations can be managed through RAM, while resource use operations can be managed by instances of each product \(for example, permission control on ECS instance OSs or provided by MySQL database\). For storage products, such as OSS and Table Store, both types of operations can be managed through RAM.


## Policy {#section_xjz_nt2_xdb .section}

A type of simple language specifications that describe a permission. For the language specifications supported by RAM, see [Policy syntax structure](../../../../../reseller.en-US//Policy Language/Policy syntax structure.md).

RAM supports two types of policies:

-   **System access policies**, which are managed by Alibaba Cloud. You can use but cannot modify such policies. Alibaba Cloud automatically updates system policy versions.
-   **Custom access policies**, which are managed by accounts. You can create or delete the custom access policies at anytime. Additionally, you must maintain custom policy versions by yourself.

