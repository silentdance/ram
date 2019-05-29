# API 概览 {#concept_vdd_rmk_xdb .concept}

本文列出了访问控制（RAM）所有可调用的 API 接口及相关描述。

更多 API 资源，详情请参考 [API Explorer](https://api.aliyun.com/)。

## 用户管理相关接口 {#section_uyr_dmj_3gb .section}

|API|描述|
|:--|:-|
|[CreateUser](intl.zh-CN/API参考（RAM）/用户管理接口/CreateUser.md)|创建 RAM 用户。|
|[GetUser](intl.zh-CN/API参考（RAM）/用户管理接口/GetUser.md)|获取用户的详细信息。|
|[UpdateUser](intl.zh-CN/API参考（RAM）/用户管理接口/UpdateUser.md)|更新用户的基本信息。|
|[DeleteUser](intl.zh-CN/API参考（RAM）/用户管理接口/DeleteUser.md)|删除一个 RAM 用户。|
|[ListUsers](intl.zh-CN/API参考（RAM）/用户管理接口/ListUsers.md#)|列出所有 RAM 用户。|
|[CreateLoginProfile](intl.zh-CN/API参考（RAM）/用户管理接口/CreateLoginProfile.md)|为一个 RAM 用户启用 Web 控制台登录。|
|[GetLoginProfile](intl.zh-CN/API参考（RAM）/用户管理接口/GetLoginProfile.md)|查看一个 RAM 用户的登录配置。|
|[DeleteLoginProfile](intl.zh-CN/API参考（RAM）/用户管理接口/DeleteLoginProfile.md)|关闭指定 RAM 用户登录 Web 控制台的功能。|
|[UpdateLoginProfile](intl.zh-CN/API参考（RAM）/用户管理接口/UpdateLoginProfile.md#)|修改用户的登录配置。|
|[CreateAccessKey](intl.zh-CN/API参考（RAM）/用户管理接口/CreateAccessKey.md)|为 RAM 用户创建 AccessKey。|
|[UpdateAccessKey](intl.zh-CN/API参考（RAM）/用户管理接口/UpdateAccessKey.md)|变更 RAM 用户 AccessKey 的状态。|
|[DeleteAccessKey](intl.zh-CN/API参考（RAM）/用户管理接口/DeleteAccessKey.md)|删除 RAM 用户的 AccessKey。|
|[ListAccessKeys](intl.zh-CN/API参考（RAM）/用户管理接口/ListAccessKeys.md)|列出指定用户的 AccessKeys。|
|[CreateVirtualMFADevice](intl.zh-CN/API参考（RAM）/用户管理接口/CreateVirtualMFADevice.md)|创建虚拟多因素认证设备。|
|[ListVirtualMFADevices](intl.zh-CN/API参考（RAM）/用户管理接口/ListVirtualMFADevices.md)|列出虚拟多因素认证设备。|
|[DeleteVirtualMFADevice](intl.zh-CN/API参考（RAM）/用户管理接口/DeleteVirtualMFADevice.md)|删除虚拟多因素认证设备。|
|[BindMFADevice](intl.zh-CN/API参考（RAM）/用户管理接口/BindMFADevice.md)|绑定多因素认证设备。|
|[UnbindMFADevice](intl.zh-CN/API参考（RAM）/用户管理接口/UnbindMFADevice.md)|解绑多因素认证设备。|
|[GetUserMFAInfo](intl.zh-CN/API参考（RAM）/用户管理接口/GetUserMFAInfo.md)|获取指定 RAM 用户的多因素认证设备信息。|
|[ChangePassword](intl.zh-CN/API参考（RAM）/用户管理接口/ChangePassword.md)|修改 RAM 用户密码。|

## 组管理相关接口 {#section_i54_gmj_3gb .section}

|API|描述|
|:--|:-|
|[CreateGroup](intl.zh-CN/API参考（RAM）/组管理接口/CreateGroup.md)|创建用户组。|
|[GetGroup](intl.zh-CN/API参考（RAM）/组管理接口/GetGroup.md)|获取用户组信息。|
|[UpdateGroup](intl.zh-CN/API参考（RAM）/组管理接口/UpdateGroup.md)|更新用户组信息。|
|[ListGroups](intl.zh-CN/API参考（RAM）/组管理接口/ListGroups.md)|列出所有的用户组。|
|[DeleteGroup](intl.zh-CN/API参考（RAM）/组管理接口/DeleteGroup.md)|删除指定的组。|
|[AddUserToGroup](intl.zh-CN/API参考（RAM）/组管理接口/AddUserToGroup.md)|将 RAM 用户添加到指定的用户组。|
|[RemoveUserFromGroup](intl.zh-CN/API参考（RAM）/组管理接口/RemoveUserFromGroup.md)|将 RAM 用户从用户组中移除。|
|[ListGroupsForUser](intl.zh-CN/API参考（RAM）/组管理接口/ListGroupsForUser.md)|列出指定 RAM 用户所加入的组信息。|
|[ListUsersForGroup](intl.zh-CN/API参考（RAM）/组管理接口/ListUsersForGroup.md)|列出指定用户组所包含的 RAM 用户。|

## 角色管理相关接口 {#section_bmq_3mj_3gb .section}

|API|描述|
|:--|:-|
|[CreateRole](intl.zh-CN/API参考（RAM）/角色管理接口/CreateRole.md)|创建角色。|
|[GetRole](intl.zh-CN/API参考（RAM）/角色管理接口/GetRole.md)|获取角色信息。|
|[UpdateRole](intl.zh-CN/API参考（RAM）/角色管理接口/UpdateRole.md)|更新角色信息。|
|[ListRoles](intl.zh-CN/API参考（RAM）/角色管理接口/ListRoles.md)|列出角色。|
|[DeleteRole](intl.zh-CN/API参考（RAM）/角色管理接口/DeleteRole.md)|删除指定的角色。|

## 权限策略管理接口 {#section_dcl_lmj_3gb .section}

|API|描述|
|:--|:-|
|[CreatePolicy](intl.zh-CN/API参考（RAM）/权限策略管理接口/CreatePolicy.md)|创建一个权限策略。|
|[GetPolicy](intl.zh-CN/API参考（RAM）/权限策略管理接口/GetPolicy.md)|获取指定的权限策略信息。|
|[DeletePolicy](intl.zh-CN/API参考（RAM）/权限策略管理接口/DeletePolicy.md)|删除指定的权限策略。|
|[ListPolicies](intl.zh-CN/API参考（RAM）/权限策略管理接口/ListPolicies.md)|列出权限策略。|
|[CreatePolicyVersion](intl.zh-CN/API参考（RAM）/权限策略管理接口/CreatePolicyVersion.md)|为权限策略创建新的版本。|
|[GetPolicyVersion](intl.zh-CN/API参考（RAM）/权限策略管理接口/GetPolicyVersion.md)|获取某个权限策略的版本。|
|[DeletePolicyVersion](intl.zh-CN/API参考（RAM）/权限策略管理接口/DeletePolicyVersion.md)|删除指定的权限策略的某个版本。|
|[ListPolicyVersions](intl.zh-CN/API参考（RAM）/权限策略管理接口/ListPolicyVersions.md)|列出权限策略版本。|
|[SetDefaultPolicyVersion](intl.zh-CN/API参考（RAM）/权限策略管理接口/SetDefaultPolicyVersion.md)|设置权限策略默认版本。|
|[AttachPolicyToUser](intl.zh-CN/API参考（RAM）/权限策略管理接口/AttachPolicyToUser.md)|为指定用户附加权限。|
|[DetachPolicyFromUser](intl.zh-CN/API参考（RAM）/权限策略管理接口/DetachPolicyFromUser.md)|为用户撤销指定的权限。|
|[AttachPolicyToGroup](intl.zh-CN/API参考（RAM）/权限策略管理接口/AttachPolicyToGroup.md)|为指定组附加权限。|
|[DetachPolicyFromGroup](intl.zh-CN/API参考（RAM）/权限策略管理接口/DetachPolicyFromGroup.md)|为组撤销指定的权限。|
|[AttachPolicyToRole](intl.zh-CN/API参考（RAM）/权限策略管理接口/AttachPolicyToRole.md)|为指定角色附加权限。|
|[DetachPolicyFromRole](intl.zh-CN/API参考（RAM）/权限策略管理接口/DetachPolicyFromRole.md)|为角色撤销指定的权限。|
|[ListEntitiesForPolicy](intl.zh-CN/API参考（RAM）/权限策略管理接口/ListEntitiesForPolicy.md)|列出引用权限策略的实体。|
|[ListPoliciesForUser](intl.zh-CN/API参考（RAM）/权限策略管理接口/ListPoliciesForUser.md)|列出指定用户被授予的权限策略。|
|[ListPoliciesForGroup](intl.zh-CN/API参考（RAM）/权限策略管理接口/ListPoliciesForGroup.md)|列出组被授予的权限策略。|
|[ListPoliciesForRole](intl.zh-CN/API参考（RAM）/权限策略管理接口/ListPoliciesForRole.md)|列出角色被授予的权限策略。|

## 安全设置相关接口 {#section_hb4_mmj_3gb .section}

|API|描述|
|:--|:-|
|[SetAccountAlias](intl.zh-CN/API参考（RAM）/安全设置接口/SetAccountAlias.md)|设置云账号别名。|
|[GetAccountAlias](intl.zh-CN/API参考（RAM）/安全设置接口/GetAccountAlias.md)|查看云账号别名。|
|[ClearAccountAlias](intl.zh-CN/API参考（RAM）/安全设置接口/ClearAccountAlias.md)|清除云账号别名。|
|[SetPasswordPolicy](intl.zh-CN/API参考（RAM）/安全设置接口/SetPasswordPolicy.md)|设置 RAM 用户密码强度等策略。|
|[GetPasswordPolicy](intl.zh-CN/API参考（RAM）/安全设置接口/GetPasswordPolicy.md)|获取 RAM 用户密码强度等策略。|
|[SetSecurityPreference](intl.zh-CN/API参考（RAM）/安全设置接口/SetSecurityPreference.md)|设置全局安全首选项。|

