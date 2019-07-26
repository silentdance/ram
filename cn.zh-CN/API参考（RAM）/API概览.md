# API概览 {#reference_vdd_rmk_xdb .reference}

本文列出了访问控制（RAM）所有可调用的API接口及相关描述。

## 调试 {#section_4jj_n5q_zgy .section}

前往[API Explorer](https://api.aliyun.com/#product=Ram&api=CreateUser)在线调试，API Explorer提供在线调用API、动态生成SDK Example代码和快速检索接口等能力，能显著降低使用云API的难度，强烈推荐使用。

## 用户管理相关接口 {#section_uyr_dmj_3gb .section}

|API|描述|
|:--|:-|
|[CreateUser](cn.zh-CN/API参考（RAM）/用户管理接口/CreateUser.md)|创建RAM用户。|
|[GetUser](cn.zh-CN/API参考（RAM）/用户管理接口/GetUser.md)|获取用户的详细信息。|
|[UpdateUser](cn.zh-CN/API参考（RAM）/用户管理接口/UpdateUser.md)|更新用户的基本信息。|
|[DeleteUser](cn.zh-CN/API参考（RAM）/用户管理接口/DeleteUser.md)|删除一个RAM用户。|
|[ListUsers](cn.zh-CN/API参考（RAM）/用户管理接口/ListUsers.md#)|列出所有RAM用户。|
|[CreateLoginProfile](cn.zh-CN/API参考（RAM）/用户管理接口/CreateLoginProfile.md)|为一个RAM用户启用Web控制台登录。|
|[GetLoginProfile](cn.zh-CN/API参考（RAM）/用户管理接口/GetLoginProfile.md)|查看一个RAM用户的登录配置。|
|[DeleteLoginProfile](cn.zh-CN/API参考（RAM）/用户管理接口/DeleteLoginProfile.md)|关闭指定RAM用户登录Web控制台的功能。|
|[UpdateLoginProfile](cn.zh-CN/API参考（RAM）/用户管理接口/UpdateLoginProfile.md#)|修改用户的登录配置。|
|[CreateAccessKey](cn.zh-CN/API参考（RAM）/用户管理接口/CreateAccessKey.md)|为RAM用户创建AccessKey。|
|[UpdateAccessKey](cn.zh-CN/API参考（RAM）/用户管理接口/UpdateAccessKey.md)|变更RAM用户AccessKey的状态。|
|[DeleteAccessKey](cn.zh-CN/API参考（RAM）/用户管理接口/DeleteAccessKey.md)|删除RAM用户的AccessKey。|
|[ListAccessKeys](cn.zh-CN/API参考（RAM）/用户管理接口/ListAccessKeys.md)|列出指定用户的AccessKeys。|
|[CreateVirtualMFADevice](cn.zh-CN/API参考（RAM）/用户管理接口/CreateVirtualMFADevice.md)|创建虚拟多因素认证设备。|
|[ListVirtualMFADevices](cn.zh-CN/API参考（RAM）/用户管理接口/ListVirtualMFADevices.md)|列出虚拟多因素认证设备。|
|[DeleteVirtualMFADevice](cn.zh-CN/API参考（RAM）/用户管理接口/DeleteVirtualMFADevice.md)|删除虚拟多因素认证设备。|
|[BindMFADevice](cn.zh-CN/API参考（RAM）/用户管理接口/BindMFADevice.md)|绑定多因素认证设备。|
|[UnbindMFADevice](cn.zh-CN/API参考（RAM）/用户管理接口/UnbindMFADevice.md)|解绑多因素认证设备。|
|[GetUserMFAInfo](cn.zh-CN/API参考（RAM）/用户管理接口/GetUserMFAInfo.md)|获取指定RAM用户的多因素认证设备信息。|
|[ChangePassword](cn.zh-CN/API参考（RAM）/用户管理接口/ChangePassword.md)|修改RAM用户密码。|

## 组管理相关接口 {#section_i54_gmj_3gb .section}

|API|描述|
|:--|:-|
|[CreateGroup](cn.zh-CN/API参考（RAM）/组管理接口/CreateGroup.md)|创建用户组。|
|[GetGroup](cn.zh-CN/API参考（RAM）/组管理接口/GetGroup.md)|获取用户组信息。|
|[UpdateGroup](cn.zh-CN/API参考（RAM）/组管理接口/UpdateGroup.md)|更新用户组信息。|
|[ListGroups](cn.zh-CN/API参考（RAM）/组管理接口/ListGroups.md)|列出所有的用户组。|
|[DeleteGroup](cn.zh-CN/API参考（RAM）/组管理接口/DeleteGroup.md)|删除指定的组。|
|[AddUserToGroup](cn.zh-CN/API参考（RAM）/组管理接口/AddUserToGroup.md)|将RAM用户添加到指定的用户组。|
|[RemoveUserFromGroup](cn.zh-CN/API参考（RAM）/组管理接口/RemoveUserFromGroup.md)|将RAM用户从用户组中移除。|
|[ListGroupsForUser](cn.zh-CN/API参考（RAM）/组管理接口/ListGroupsForUser.md)|列出指定RAM用户所加入的组信息。|
|[ListUsersForGroup](cn.zh-CN/API参考（RAM）/组管理接口/ListUsersForGroup.md)|列出指定用户组所包含的RAM用户。|

## 角色管理相关接口 {#section_bmq_3mj_3gb .section}

|API|描述|
|:--|:-|
|[CreateRole](cn.zh-CN/API参考（RAM）/角色管理接口/CreateRole.md)|创建角色。|
|[GetRole](cn.zh-CN/API参考（RAM）/角色管理接口/GetRole.md)|获取角色信息。|
|[UpdateRole](cn.zh-CN/API参考（RAM）/角色管理接口/UpdateRole.md)|更新角色信息。|
|[ListRoles](cn.zh-CN/API参考（RAM）/角色管理接口/ListRoles.md)|列出角色。|
|[DeleteRole](cn.zh-CN/API参考（RAM）/角色管理接口/DeleteRole.md)|删除指定的角色。|

## 权限策略管理接口 {#section_dcl_lmj_3gb .section}

|API|描述|
|:--|:-|
|[CreatePolicy](cn.zh-CN/API参考（RAM）/权限策略管理接口/CreatePolicy.md)|创建一个权限策略。|
|[GetPolicy](cn.zh-CN/API参考（RAM）/权限策略管理接口/GetPolicy.md)|获取指定的权限策略信息。|
|[DeletePolicy](cn.zh-CN/API参考（RAM）/权限策略管理接口/DeletePolicy.md)|删除指定的权限策略。|
|[ListPolicies](cn.zh-CN/API参考（RAM）/权限策略管理接口/ListPolicies.md)|列出权限策略。|
|[CreatePolicyVersion](cn.zh-CN/API参考（RAM）/权限策略管理接口/CreatePolicyVersion.md)|为权限策略创建新的版本。|
|[GetPolicyVersion](cn.zh-CN/API参考（RAM）/权限策略管理接口/GetPolicyVersion.md)|获取某个权限策略的版本。|
|[DeletePolicyVersion](cn.zh-CN/API参考（RAM）/权限策略管理接口/DeletePolicyVersion.md)|删除指定的权限策略的某个版本。|
|[ListPolicyVersions](cn.zh-CN/API参考（RAM）/权限策略管理接口/ListPolicyVersions.md)|列出权限策略版本。|
|[SetDefaultPolicyVersion](cn.zh-CN/API参考（RAM）/权限策略管理接口/SetDefaultPolicyVersion.md)|设置权限策略默认版本。|
|[AttachPolicyToUser](cn.zh-CN/API参考（RAM）/权限策略管理接口/AttachPolicyToUser.md)|为指定用户附加权限。|
|[DetachPolicyFromUser](cn.zh-CN/API参考（RAM）/权限策略管理接口/DetachPolicyFromUser.md)|为用户撤销指定的权限。|
|[AttachPolicyToGroup](cn.zh-CN/API参考（RAM）/权限策略管理接口/AttachPolicyToGroup.md)|为指定组附加权限。|
|[DetachPolicyFromGroup](cn.zh-CN/API参考（RAM）/权限策略管理接口/DetachPolicyFromGroup.md)|为组撤销指定的权限。|
|[AttachPolicyToRole](cn.zh-CN/API参考（RAM）/权限策略管理接口/AttachPolicyToRole.md)|为指定角色附加权限。|
|[DetachPolicyFromRole](cn.zh-CN/API参考（RAM）/权限策略管理接口/DetachPolicyFromRole.md)|为角色撤销指定的权限。|
|[ListEntitiesForPolicy](cn.zh-CN/API参考（RAM）/权限策略管理接口/ListEntitiesForPolicy.md)|列出引用权限策略的实体。|
|[ListPoliciesForUser](cn.zh-CN/API参考（RAM）/权限策略管理接口/ListPoliciesForUser.md)|列出指定用户被授予的权限策略。|
|[ListPoliciesForGroup](cn.zh-CN/API参考（RAM）/权限策略管理接口/ListPoliciesForGroup.md)|列出组被授予的权限策略。|
|[ListPoliciesForRole](cn.zh-CN/API参考（RAM）/权限策略管理接口/ListPoliciesForRole.md)|列出角色被授予的权限策略。|

## 安全设置相关接口 {#section_hb4_mmj_3gb .section}

|API|描述|
|:--|:-|
|[SetAccountAlias](cn.zh-CN/API参考（RAM）/安全设置接口/SetAccountAlias.md)|设置云账号别名。|
|[GetAccountAlias](cn.zh-CN/API参考（RAM）/安全设置接口/GetAccountAlias.md)|查看云账号别名。|
|[ClearAccountAlias](cn.zh-CN/API参考（RAM）/安全设置接口/ClearAccountAlias.md)|清除云账号别名。|
|[SetPasswordPolicy](cn.zh-CN/API参考（RAM）/安全设置接口/SetPasswordPolicy.md)|设置RAM用户密码强度等策略。|
|[GetPasswordPolicy](cn.zh-CN/API参考（RAM）/安全设置接口/GetPasswordPolicy.md)|获取RAM用户密码强度等策略。|
|[SetSecurityPreference](cn.zh-CN/API参考（RAM）/安全设置接口/SetSecurityPreference.md)|设置全局安全首选项。|

