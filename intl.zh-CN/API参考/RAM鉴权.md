# RAM鉴权 {#concept_az3_vrl_lgb .concept}

本文列举了RAM中可授权的API及其描述方式。

当其他账号通过 API 访问主账号的资源时，RAM 需进行权限检查，以确保资源拥有者的确将相关资源的权限授予了调用者。不同的 API 会根据涉及的资源以及 API 语义确定需要检查哪些资源的权限。

API 的鉴权规则如下表所示：

|API|资源描述|
|:--|:---|
|ram:CreateUser|`acs:ram:*:${AccountId}:user/*`|
|ram:GetUser|`acs:ram:*:${AccountId}:user/${UserName}`|
|ram:UpdateUser|`acs:ram:*:${AccountId}:user/${UserName}`|
|ram:DeleteUser|`acs:ram:*:${AccountId}:user/${UserName}`|
|ram:ListUsers|`acs:ram:*:${AccountId}:user/*`|
|ram:CreateLoginProfile|`acs:ram:*:${AccountId}:user/${UserName}`|
|ram:GetLoginProfile|`acs:ram:*:${AccountId}:user/${UserName}`|
|ram:DeleteLoginProfile|`acs:ram:*:${AccountId}:user/${UserName}`|
|ram:UpdateLoginProfile|`acs:ram:*:${AccountId}:user/${UserName}`|
|ram:CreateAccessKey|`acs:ram:*:${AccountId}:user/${UserName}`|
|ram:UpdateAccessKey|`acs:ram:*:${AccountId}:user/${UserName}`|
|ram:DeleteAccessKey|`acs:ram:*:${AccountId}:user/${UserName}`|
|ram:ListAccessKeys|`acs:ram:*:${AccountId}:user/${UserName}`|
|ram:CreateVirtualMFADevice|`acs:ram:*:${AccountId}:mfa/*`|
|ram:ListVirtualMFADevices|`acs:ram:*:${AccountId}:mfa/*`|
|ram:DeleteVirtualMFADevice|`${SerialNumber}`|
|ram:BindMFADevice|`acs:ram:*:${AccountId}:user/${UserName}`|
|ram:UnbindMFADevice|`acs:ram:*:${AccountId}:user/${UserName}`|
|ram:GetUserMFAInfo|`acs:ram:*:${AccountId}:user/${UserName}`|
|ram:ChangePassword|`acs:ram:*:${AccountId}:user/${UserName}`|
|ram:CreateGroup|`acs:ram:*:${AccountId}:group/*`|
|ram:GetGroup|`acs:ram:*:${AccountId}:group/${GroupName}`|
|ram:UpdateGroup|`acs:ram:*:${AccountId}:group/${GroupName}`|
|ram:ListGroups|`acs:ram:*:${AccountId}:group/*`|
|ram:DeleteGroup|`acs:ram:*:${AccountId}:group/${GroupName}`|
|ram:AddUserToGroup|`acs:ram:*:${AccountId}:user/${UserName}`|
|`acs:ram:*:${AccountId}:group/${GroupName}`|
|ram:RemoveUserFromGroup|`acs:ram:*:${AccountId}:user/${UserName}`|
|`acs:ram:*:${AccountId}:group/${GroupName}`|
|ram:ListGroupsForUser|`acs:ram:*:${AccountId}:user/${UserName}`|
|ram:ListUsersForGroup|`acs:ram:*:${AccountId}:group/${GroupName}`|
|ram:CreateRole|`acs:ram:*:${AccountId}:role/*`|
|ram:GetRole|`acs:ram:*:${AccountId}:role/${RoleName}`|
|ram:UpdateRole|`acs:ram:*:${AccountId}:role/${RoleName}`|
|ram:ListRoles|`acs:ram:*:${AccountId}:role/*`|
|ram:DeleteRole|`acs:ram:*:${AccountId}:role/${RoleName}`|
|ram:CreatePolicy|`acs:ram:*:${AccountId}:policy/*`|
|ram:GetPolicy|`acs:ram:*:${AccountId} or system:policy/${PolicyName}`|
|ram:DeletePolicy|`acs:ram:*:${AccountId}:policy/${PolicyName}`|
|ram:ListPolicies|`acs:ram:*:${AccountId}:policy/*`|
|ram:CreatePolicyVersion|`acs:ram:*:${AccountId}:policy/${PolicyName}`|
|ram:GetPolicyVersion|`acs:ram:*:${AccountId} or system:group/${PolicyName}`|
|ram:DeletePolicyVersion|`acs:ram:*:${AccountId}:policy/${PolicyName}`|
|ram:ListPolicyVersions|`acs:ram:*:${AccountId} or system:policy/${PolicyName}`|
|ram:SetDefaultPolicyVersion|`acs:ram:*:${AccountId}:policy/${PolicyName}`|
|ram:AttachPolicyToUser|`acs:ram:*:${AccountId}:user/${UserName}`|
|`acs:ram:*:${AccountId} or system:policy/${PolicyName}`|
|ram:DetachPolicyFromUser|`acs:ram:*:${AccountId}:user/${UserName}`|
|`acs:ram:*:${AccountId} or system:policy/${PolicyName}`|
|ram:AttachPolicyToGroup|`acs:ram:*:${AccountId}:group/${GroupName}`|
|`acs:ram:*:${AccountId} or system:policy/${PolicyName}`|
|ram:DetachPolicyFromGroup|`acs:ram:*:${AccountId}:group/${GroupName}`|
|`acs:ram:*:${AccountId} or system:policy/${PolicyName}`|
|ram:AttachPolicyToRole|`acs:ram:*:${AccountId}:role/${RoleName}`|
|`acs:ram:*:${AccountId} or system:policy/${PolicyName}`|
|ram:DetachPolicyFromRole|`acs:ram:*:${AccountId}:role/${RoleName}`|
|`acs:ram:*:${AccountId} or system:policy/${PolicyName}`|
|ram:ListEntitiesForPolicy|`acs:ram:*:${AccountId} or system:policy/${PolicyName}`|
|ram:SetAccountAlias|`acs:ram:*:${AccountId}:*`|
|ram:GetAccountAlias|`acs:ram:*:${AccountId}:*`|
|ram:ClearAccountAlias|`acs:ram:*:${AccountId}:*`|
|ram:SetPasswordPolicy|`acs:ram:*:${AccountId}:*`|
|ram:GetPasswordPolicy|`acs:ram:*:${AccountId}:*`|
|ram:SetSecurityPreference|`acs:ram:*:${AccountId}:*`|

