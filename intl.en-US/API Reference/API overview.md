# API overview {#concept_vdd_rmk_xdb .concept}

This topic lists all RAM API actions.

## Debug {#section_ia8_53n_ako .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Ram&api=CreateUser) to perform debug operations and generate SDK code examples.

## User management API actions {#section_fhn_1nj_3gb .section}

|Action|Description|
|:-----|:----------|
|[CreateUser](reseller.en-US/API Reference/User management APIs/CreateUser.md#)|Creates a RAM user.|
|[GetUser](reseller.en-US/API Reference/User management APIs/GetUser.md#)|Obtains the detailed information about a RAM user.|
|[UpdateUser](reseller.en-US/API Reference/User management APIs/UpdateUser.md#)|Updates the basic information about a RAM user.|
|[DeleteUser](reseller.en-US/API Reference/User management APIs/DeleteUser.md#)|Deletes a RAM user.|
|[ListUsers](reseller.en-US/API Reference/User management APIs/ListUsers.md#)|Lists all RAM users.|
|[CreateLoginProfile](reseller.en-US/API Reference/User management APIs/CreateLoginProfile.md#)|Enables console logon for a RAM user.|
|[GetLoginProfile](reseller.en-US/API Reference/User management APIs/GetLoginProfile.md#)|Views the logon configurations of a RAM user.|
|[DeleteLoginProfile](reseller.en-US/API Reference/User management APIs/DeleteLoginProfile.md#)|Disables console logon for a RAM user.|
|[DeleteLoginProfile](reseller.en-US/API Reference/User management APIs/DeleteLoginProfile.md#)|Modifies the logon configurations of a RAM user.|
|[CreateAccessKey](reseller.en-US/API Reference/User management APIs/CreateAccessKey.md#)|Creates an AccessKey for a RAM user.|
|[UpdateAccessKey](reseller.en-US/API Reference/User management APIs/UpdateAccessKey.md#)|Changes the AccessKey status of a RAM user.|
|[DeleteAccessKey](reseller.en-US/API Reference/User management APIs/DeleteAccessKey.md#)|Deletes the AccessKey of a RAM user.|
|[ListAccessKeys](reseller.en-US/API Reference/User management APIs/ListAccessKeys.md#)|Lists the AccessKey of a RAM user.|
|[CreateVirtualMFADevice](reseller.en-US/API Reference/User management APIs/CreateVirtualMFADevice.md#)|Creates a virtual Multi-Factor Authentication \(MFA\) device.|
|[ListVirtualMFADevices](reseller.en-US/API Reference/User management APIs/ListVirtualMFADevices.md#)|Lists virtual MFA devices.|
|[DeleteVirtualMFADevice](reseller.en-US/API Reference/User management APIs/DeleteVirtualMFADevice.md#)|Deletes a virtual MFA device.|
|[BindMFADevice](reseller.en-US/API Reference/User management APIs/BindMFADevice.md#)|Attaches an MFA device to a RAM user.|
|[UnbindMFADevice](reseller.en-US/API Reference/User management APIs/UnbindMFADevice.md#)|Removes an MFA device from a RAM user.|
|[GetUserMFAInfo](reseller.en-US/API Reference/User management APIs/GetUserMFAInfo.md#)|Obtains the MFA device information of a RAM user.|
|[ChangePassword](reseller.en-US/API Reference/User management APIs/ChangePassword.md#)|Changes the password for a RAM user.|

## Group management API actions {#section_ot3_dnj_3gb .section}

|Action|Description|
|:-----|:----------|
|[CreateGroup](reseller.en-US/API Reference/Group management APIs/CreateGroup.md#)|Creates a RAM user group.|
|[GetGroup](reseller.en-US/API Reference/Group management APIs/GetGroup.md#)|Obtains RAM user group information.|
|[UpdateGroup](reseller.en-US/API Reference/Group management APIs/UpdateGroup.md#)|Updates RAM user group information.|
|[ListGroups](reseller.en-US/API Reference/Group management APIs/ListGroups.md#)|Lists all RAM user groups.|
|[DeleteGroup](reseller.en-US/API Reference/Group management APIs/DeleteGroup.md#)|Deletes a RAM user group.|
|[AddUserToGroup](reseller.en-US/API Reference/Group management APIs/AddUserToGroup.md#)|Adds a RAM user to a RAM user group.|
|[RemoveUserFromGroup](reseller.en-US/API Reference/Group management APIs/RemoveUserFromGroup.md#)|Removes a RAM user from a RAM user group.|
|[ListGroupsForUser](reseller.en-US/API Reference/Group management APIs/ListGroupsForUser.md#)|Lists information about the RAM user groups to which a specified RAM user is added.|
|[ListUsersForGroup](reseller.en-US/API Reference/Group management APIs/ListUsersForGroup.md#)|Lists the RAM users in a RAM user group.|

## Role management API actions {#section_b3r_dnj_3gb .section}

|Action|Description|
|:-----|:----------|
|[CreateRole](reseller.en-US/API Reference/Role management APIs/CreateRole.md#)|Creates a RAM role.|
|[GetRole](reseller.en-US/API Reference/Role management APIs/GetRole.md#)|Obtains information about a RAM role.|
|[UpdateRole](reseller.en-US/API Reference/Role management APIs/UpdateRole.md#)|Updates information about a RAM role.|
|[ListRoles](reseller.en-US/API Reference/Role management APIs/ListRoles.md#)|Lists RAM roles.|
|[DeleteRole](reseller.en-US/API Reference/Role management APIs/DeleteRole.md#)|Deletes a RAM role.|

## Policy management API actions {#section_pds_dnj_3gb .section}

|Action|Description|
|:-----|:----------|
|[CreatePolicy](reseller.en-US/API Reference/Policy management APIs/CreatePolicy.md#)|Creates a policy.|
|[GetPolicy](reseller.en-US/API Reference/Policy management APIs/GetPolicy.md#)|Obtains information about a policy.|
|[DeletePolicy](reseller.en-US/API Reference/Policy management APIs/DeletePolicy.md#)|Deletes a policy.|
|[ListPolicies](reseller.en-US/API Reference/Policy management APIs/ListPolicies.md#)|Lists policies.|
|[CreatePolicyVersion](reseller.en-US/API Reference/Policy management APIs/CreatePolicyVersion.md#)|Creates a version for a policy.|
|[GetPolicyVersion](reseller.en-US/API Reference/Policy management APIs/GetPolicyVersion.md#)|Obtains information about the version of a policy.|
|[DeletePolicyVersion](reseller.en-US/API Reference/Policy management APIs/DeletePolicyVersion.md#)|Deletes a version of a policy.|
|[ListPolicyVersions](reseller.en-US/API Reference/Policy management APIs/ListPolicyVersions.md#)|Lists all versions of a policy.|
|[SetDefaultPolicyVersion](reseller.en-US/API Reference/Policy management APIs/SetDefaultPolicyVersion.md#)|Sets the default version of a policy.|
|[AttachPolicyToUser](reseller.en-US/API Reference/Policy management APIs/AttachPolicyToUser.md#)|Attaches a policy to a RAM user.|
|[DetachPolicyFromUser](reseller.en-US/API Reference/Policy management APIs/DetachPolicyFromUser.md#)|Removes a policy from a RAM user.|
|[AttachPolicyToGroup](reseller.en-US/API Reference/Policy management APIs/AttachPolicyToGroup.md#)|Attaches a policy to a RAM user group.|
|[DetachPolicyFromGroup](reseller.en-US/API Reference/Policy management APIs/DetachPolicyFromGroup.md#)|Removes a policy from a RAM user group.|
|[AttachPolicyToRole](reseller.en-US/API Reference/Policy management APIs/AttachPolicyToRole.md#)|Attaches a policy to a RAM role.|
|[DetachPolicyFromRole](reseller.en-US/API Reference/Policy management APIs/DetachPolicyFromRole.md#)|Removes a policy from a RAM role.|
|[ListEntitiesForPolicy](reseller.en-US/API Reference/Policy management APIs/ListEntitiesForPolicy.md#)|Lists the entities that use a policy.|
|[ListPoliciesForUser](reseller.en-US/API Reference/Policy management APIs/ListPoliciesForUser.md#)|Lists the policies attached to a RAM user.|
|[ListPoliciesForGroup](reseller.en-US/API Reference/Policy management APIs/ListPoliciesForGroup.md#)|Lists the policies attached to a RAM user group.|
|[ListPoliciesForRole](reseller.en-US/API Reference/Policy management APIs/ListPoliciesForRole.md#)|Lists the policies attached to a RAM role.|

## Security management API actions {#section_zbt_dnj_3gb .section}

|Action|Description|
|:-----|:----------|
|[SetAccountAlias](reseller.en-US/API Reference/Security management APIs/SetAccountAlias.md#)|Sets an alias for an Alibaba Cloud account.|
|[GetAccountAlias](reseller.en-US/API Reference/Security management APIs/GetAccountAlias.md#)|Views the alias of an Alibaba Cloud account.|
|[ClearAccountAlias](reseller.en-US/API Reference/Security management APIs/ClearAccountAlias.md#)|Deletes the alias of an Alibaba Cloud account.|
|[SetPasswordPolicy](reseller.en-US/API Reference/Security management APIs/SetPasswordPolicy.md#)|Sets the password policy, including the password strength, for a RAM user.|
|[GetPasswordPolicy](reseller.en-US/API Reference/Security management APIs/GetPasswordPolicy.md#)|Obtains the password policy, including the password strength, of a RAM user.|
|[SetSecurityPreference](reseller.en-US/API Reference/Security management APIs/SetSecurityPreference.md#)|Sets the security preferences.|

