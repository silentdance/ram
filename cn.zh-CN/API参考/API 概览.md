# API 概览 {#concept_vdd_rmk_xdb .concept}

本页面列出了 RAM 所有 API 接口。更多 OpenAPI 资源，请关注 [API Explorer](https://api.aliyun.com/)。

## 用户管理相关接口 {#section_uyr_dmj_3gb .section}

|API|描述|
|:--|:-|
|[CreateUser](intl.zh-CN/API参考/用户管理接口/CreateUser.md)|创建 RAM 子用户|
|[GetUser](intl.zh-CN/API参考/用户管理接口/GetUser.md)|获取用户的详细信息|
|[UpdateUser](intl.zh-CN/API参考/用户管理接口/UpdateUser.md)|更新用户的基本信息|
|[DeleteUser](intl.zh-CN/API参考/用户管理接口/DeleteUser.md)|删除一个 RAM 用户|
|[ListUsers](intl.zh-CN/API参考/用户管理接口/ListUsers.md#)|列出所有 RAM 用户|
|[CreateLoginProfile](intl.zh-CN/API参考/用户管理接口/CreateLoginProfile.md)|为一个 RAM 子用户启用 Web 控制台登录|
|[GetLoginProfile](intl.zh-CN/API参考/用户管理接口/GetLoginProfile.md)|查看一个 RAM 用户的登录配置|
|[DeleteLoginProfile](intl.zh-CN/API参考/用户管理接口/DeleteLoginProfile.md)|关闭指定子用户登录 Web 控制台的功能|
|[UpdateLoginProfile](intl.zh-CN/API参考/用户管理接口/UpdateLoginProfile.md#)|修改用户的登录配置|
|[CreateAccessKey](intl.zh-CN/API参考/用户管理接口/CreateAccessKey.md)|为 RAM 子用户创建 AccessKey|
|[UpdateAccessKey](intl.zh-CN/API参考/用户管理接口/UpdateAccessKey.md)|变更 RAM 子用户 AccessKey 的状态|
|[DeleteAccessKey](intl.zh-CN/API参考/用户管理接口/DeleteAccessKey.md)|删除 RAM 子用户的 AccessKey|
|[ListAccessKeys](intl.zh-CN/API参考/用户管理接口/ListAccessKeys.md)|列出指定用户的 AccessKeys|
|[CreateVirtualMFADevice](intl.zh-CN/API参考/用户管理接口/CreateVirtualMFADevice.md)|创建虚拟多因素认证设备|
|[ListVirtualMFADevices](intl.zh-CN/API参考/用户管理接口/ListVirtualMFADevices.md)|列出虚拟多因素认证设备|
|[DeleteVirtualMFADevice](intl.zh-CN/API参考/用户管理接口/DeleteVirtualMFADevice.md)|删除虚拟多因素认证设备|
|[BindMFADevice](intl.zh-CN/API参考/用户管理接口/BindMFADevice.md)|绑定多因素认证设备|
|[UnbindMFADevice](intl.zh-CN/API参考/用户管理接口/UnbindMFADevice.md)|解绑多因素认证设备|
|[GetUserMFAInfo](intl.zh-CN/API参考/用户管理接口/GetUserMFAInfo.md)|获取指定子用户的多因素认证设备信息|
|[ChangePassword](intl.zh-CN/API参考/用户管理接口/ChangePassword.md)|修改子用户密码|

## 组管理相关接口 {#section_i54_gmj_3gb .section}

|API|描述|
|:--|:-|
|[CreateGroup](intl.zh-CN/API参考/组管理接口/CreateGroup.md)|创建用户组|
|[GetGroup](intl.zh-CN/API参考/组管理接口/GetGroup.md)|获取用户组信息|
|[UpdateGroup](intl.zh-CN/API参考/组管理接口/UpdateGroup.md)|更新用户组信息|
|[ListGroups](intl.zh-CN/API参考/组管理接口/ListGroups.md)|列出所有的用户组|
|[DeleteGroup](intl.zh-CN/API参考/组管理接口/DeleteGroup.md)|删除指定的组|
|[AddUserToGroup](intl.zh-CN/API参考/组管理接口/AddUserToGroup.md)|将子用户添加到指定的用户组|
|[RemoveUserFromGroup](intl.zh-CN/API参考/组管理接口/RemoveUserFromGroup.md)|将子用户从用户组中移除|
|[ListGroupsForUser](intl.zh-CN/API参考/组管理接口/ListGroupsForUser.md)|列出指定子用户所加入的组信息|
|[ListUsersForGroup](intl.zh-CN/API参考/组管理接口/ListUsersForGroup.md)|列出指定用户组所包含的子用户|

## 角色管理相关接口 {#section_bmq_3mj_3gb .section}

|API|描述|
|:--|:-|
|[CreateRole](intl.zh-CN/API参考/角色管理接口/CreateRole.md)|创建角色|
|[GetRole](intl.zh-CN/API参考/角色管理接口/GetRole.md)|获取角色信息|
|[UpdateRole](intl.zh-CN/API参考/角色管理接口/UpdateRole.md)|更新角色信息|
|[ListRoles](intl.zh-CN/API参考/角色管理接口/ListRoles.md)|列出角色|
|[DeleteRole](intl.zh-CN/API参考/角色管理接口/DeleteRole.md)|删除指定的角色|

## 权限策略管理接口 {#section_dcl_lmj_3gb .section}

|API|描述|
|:--|:-|
|[CreatePolicy](intl.zh-CN/API参考/权限策略管理接口/CreatePolicy.md)|创建一个授权策略|
|[GetPolicy](intl.zh-CN/API参考/权限策略管理接口/GetPolicy.md)|获取指定的授权策略信息|
|[DeletePolicy](intl.zh-CN/API参考/权限策略管理接口/DeletePolicy.md)|删除指定的授权策略|
|[ListPolicies](intl.zh-CN/API参考/权限策略管理接口/ListPolicies.md)|列出授权策略|
|[CreatePolicyVersion](intl.zh-CN/API参考/权限策略管理接口/CreatePolicyVersion.md)|为授权策略创建新的版本|
|[GetPolicyVersion](intl.zh-CN/API参考/权限策略管理接口/GetPolicyVersion.md)|获取某个授权策略的版本|
|[DeletePolicyVersion](intl.zh-CN/API参考/权限策略管理接口/DeletePolicyVersion.md)|删除指定的授权策略的某个版本|
|[ListPolicyVersions](intl.zh-CN/API参考/权限策略管理接口/ListPolicyVersions.md)|列出授权策略版本|
|[SetDefaultPolicyVersion](intl.zh-CN/API参考/权限策略管理接口/SetDefaultPolicyVersion.md)|设置授权策略默认版本|
|[AttachPolicyToUser](intl.zh-CN/API参考/权限策略管理接口/AttachPolicyToUser.md)|为指定用户附加授权|
|[DetachPolicyFromUser](intl.zh-CN/API参考/权限策略管理接口/DetachPolicyFromUser.md)|为用户撤销指定的授权|
|[AttachPolicyToGroup](intl.zh-CN/API参考/权限策略管理接口/AttachPolicyToGroup.md)|为指定组附加授权|
|[DetachPolicyFromGroup](intl.zh-CN/API参考/权限策略管理接口/DetachPolicyFromGroup.md)|为组撤销指定的授权|
|[AttachPolicyToRole](intl.zh-CN/API参考/权限策略管理接口/AttachPolicyToRole.md)|为指定角色附加授权|
|[DetachPolicyFromRole](intl.zh-CN/API参考/权限策略管理接口/DetachPolicyFromRole.md)|为角色撤销指定的授权|
|[ListEntitiesForPolicy](intl.zh-CN/API参考/权限策略管理接口/ListEntitiesForPolicy.md)|列出引用授权策略的实体|
|[ListPoliciesForUser](intl.zh-CN/API参考/权限策略管理接口/ListPoliciesForUser.md)|列出指定用户被授予的授权策略|
|[ListPoliciesForGroup](intl.zh-CN/API参考/权限策略管理接口/ListPoliciesForGroup.md)|列出组被授予的授权策略|
|[ListPoliciesForRole](intl.zh-CN/API参考/权限策略管理接口/ListPoliciesForRole.md)|列出角色被授予的授权策略|

## 安全设置相关接口 {#section_hb4_mmj_3gb .section}

|API|描述|
|:--|:-|
|[SetAccountAlias](intl.zh-CN/API参考/安全设置接口/SetAccountAlias.md)|设置云账号别名|
|[GetAccountAlias](intl.zh-CN/API参考/安全设置接口/GetAccountAlias.md)|查看云账号别名|
|[ClearAccountAlias](intl.zh-CN/API参考/安全设置接口/ClearAccountAlias.md)|清除云账号别名|
|[SetPasswordPolicy](intl.zh-CN/API参考/安全设置接口/SetPasswordPolicy.md)|设置子用户密码强度等策略|
|[GetPasswordPolicy](intl.zh-CN/API参考/安全设置接口/GetPasswordPolicy.md)|获取子用户密码强度等策略|
|[SetSecurityPreference](intl.zh-CN/API参考/安全设置接口/SetSecurityPreference.md)|设置全局安全首选项|

## 数据类型 {#section_cfy_nmj_3gb .section}

|类型|描述|
|:-|:-|
|[User](intl.zh-CN/API参考/数据类型/User.md)|用户信息|
|[LoginProfile](intl.zh-CN/API参考/数据类型/LoginProfile.md)|用户登录配置|
|[MFADevice](intl.zh-CN/API参考/数据类型/MFADevice.md)|多因素认证设备|
|[VirtualMFADevice](intl.zh-CN/API参考/数据类型/VirtualMFADevice.md)|虚拟多因素认证设备|
|[AccessKey](intl.zh-CN/API参考/数据类型/AccessKey.md)|访问密钥|
|[Group](intl.zh-CN/API参考/数据类型/Group.md)|组信息类型|
|[Role](intl.zh-CN/API参考/数据类型/Role.md)|角色|
|[Policy](intl.zh-CN/API参考/数据类型/Policy.md)|授权策略|
|[PolicyVersion](intl.zh-CN/API参考/数据类型/PolicyVersion.md)|授权策略版本|
|[PasswordPolicy](intl.zh-CN/API参考/数据类型/PasswordPolicy.md)|密码策略|
|[SecurityPreference](intl.zh-CN/API参考/数据类型/SecurityPreference.md)|安全首选项|

