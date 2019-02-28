# Understand RAM roles {#concept_fgc_wjc_mfb .concept}

RAM roles are a type of identity defined in RAM that represent virtual users, and as such do not have specific identity authentication keys. RAM roles can be assumed by any entity through the target console or by using a specific API and can be used only when the roles are assumed by trusted entity users.

**Note:** In this topic, **roles** refer to **RAM roles** unless otherwise specified.

## Related concepts {#section_f2y_k4d_nfb .section}

The following figure illustrates the relationships between the concepts related to RAM roles.

![Concepts related to RAM](images/14219_en-US.png "Concepts related to RAM roles")

|Concept|Description|
|:------|:----------|
|RoleARN|A RoleARN is the global resource identifier of a role. It is used to specify a role.-   RoleARNs conform to Alibaba Cloud ARN naming conventions. For example, the ARN of the role devops under an account is `acs:ram::1234567890123456:role/samplerole`.
-   After creating a role, you can click the role name and find its ARN in the Basic Information area.

|
|Trusted entity|A trusted entity is the identity of a trusted entity user who can assume a role.-   You must specify a trusted entity when creating a role. Only trusted entities can assume roles.
-   A trusted entity can be a trusted account or service.

|
|Policy|A role can be attached to a set of policies. Roles that are not attached to any policy can exist, but cannot access resources.|
|Role assuming|Role assuming \(Assume Role\) is the method for entity users to obtain security tokens of roles. By calling the AssumeRole API, an entity user can obtain the security token of a role and use the token to access cloud service APIs.|
|Identity switching|Identity switching \(Switch Role\) is the method by which entity users can switch from the logon identity to role identity in the RAM console.-   After logging on to the RAM console, an entity user can switch to a role that the user can assume. The user can then use the role identity to operate cloud resources.
-   When the user no longer needs the role identity, the user can switch back to its logon identity.

|
|Role token|A role token is a temporary AccessKey to a role identity. RAM roles do not have specific identity authentication keys. When an entity user wants to use a role, the user must assume the role to obtain the role token. Then, the user can use the role token to call Alibaba Cloud service APIs.|

## RAM role types {#section_01 .section}

RAM roles are divided into the following types according to different trusted players:

-   **Alibaba Cloud Account:** roles that RAM users can assume. The RAM users may belong to their own accounts or other accounts. Such roles provide solutions to cross-account access and temporary authorization.
-   **Alibaba Cloud Service:** roles that cloud services can assume. Such roles are used to authorize cloud services to operate resources as stand-alone applications.

## Applicable scenarios of RAM roles {#section_yhg_nzp_4fb .section}

-   [Grant temporary permissions to mobile apps](reseller.en-US/User Guide/Scenarios/Grant temporary permissions to mobile apps.md#)
-   [Cross-account resource authorization and access](reseller.en-US/User Guide/Scenarios/Cross-account resource authorization and access.md#)
-   [Dynamic identity and permission management of cloud applications](reseller.en-US/User Guide/Scenarios/Dynamic identity and permission management of cloud applications.md#)

