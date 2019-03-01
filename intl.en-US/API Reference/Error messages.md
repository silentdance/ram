# Error messages {#reference_j1t_zmv_xdb .reference}

## HTTP status 400 {#section_ogq_dnv_xdb .section}

**InvalidParameter**

**InvalidParameter.UserName.InvalidChars**

-   HTTP status: 400
-   Error message: The parameter - "UserName" contains invalid chars.
-   Solution: Modify the value of UserName. The value can contain letters, numbers, periods \(.\), underscores \(\_\), and hyphens \(-\).

**InvalidParameter.UserName.Length**

-   HTTP status: 400
-   Error message: The parameter - "UserName" beyond the length limit.
-   Solution: Modify the length of UserName. The value must be 1 to 64 characters in length.

**InvalidParameter.NewUserName.InvalidChars**

-   HTTP status: 400
-   Error message: The parameter - "NewUserName" contains invalid chars.
-   Solution: Modify the value of NewUserName. The value can contain letters, numbers, periods \(.\), underscores \(\_\), and hyphens \(-\).

**InvalidParameter.NewUserName.Length**

-   HTTP status: 400
-   Error message: The parameter - "NewUserName" beyond the length limit.
-   Solution: Modify the length of NewUserName. The value must be 1 to 64 characters in length.

**InvalidParameter.DisplayName.InvalidChars**

-   HTTP status: 400
-   Error message: The parameter - "DisplayName" contains invalid chars.
-   Solution: Modify the value of DisplayName. The value can contain letters, numbers, at signs \(@\), periods \(.\), underscores \(\_\), and hyphens \(-\).

**InvalidParameter.DisplayName.Length**

-   HTTP status: 400
-   Error message: The parameter - "DisplayName" beyond the length limit.
-   Solution: Modify the length of DisplayName. The value must be 1 to 128 characters in length.

**InvalidParameter.NewDisplayName.InvalidChars**

-   HTTP status: 400
-   Error message: The parameter - "NewDisplayName" contains invalid chars.
-   Solution: Modify the value of NewDisplayName. The value can contain letters, numbers, at signs \(@\), periods \(.\), underscores \(\_\), and hyphens \(-\).

**InvalidParameter.NewDisplayName.Length**

-   HTTP status: 400
-   Error message: The parameter - "NewDisplayName" beyond the length limit.
-   Solution: Modify the length of NewDisplayName. The value must be 1 to 128 characters in length.

**InvalidParameter.MobilePhone.Format**

-   HTTP status: 400
-   Error message: The format of the parameter - "MobilePhone" is incorrect.
-   Solution: Modify the value of MobilePhone to a correct mobile phone number.

**InvalidParameter.NewMobilePhone.Format**

-   HTTP status: 400
-   Error message: The format of the parameter - "NewMobilePhone" is incorrect.
-   Solution: Modify the value of NewMobilePhone to a correct mobile phone number.

**InvalidParameter.Email.Format**

-   HTTP status: 400
-   Error message: The format of the parameter - "Email" is incorrect.
-   Solution: Modify the value of Email to a correct email address.

**InvalidParameter.NewEmail.Format**

-   HTTP status: 400
-   Error message: The format of the parameter - "NewEmail" is incorrect.
-   Solution: Modify the value of NewEmail to a correct email address.

**InvalidParameter.Comments.Length**

-   HTTP status: 400
-   Error message: The parameter - "Comments" beyond the length limit.
-   Solution: Modify the length of Comments. The length cannot exceed 128 characters.

**InvalidParameter.NewComments.Length**

-   HTTP status: 400
-   Error message: The parameter - "NewComments" beyond the length limit.
-   Solution: Modify the length of NewComments. The length cannot exceed 128 characters.

**InvalidParameter.Password.TooWeak**

-   HTTP status: 400
-   Error message: The parameter - "Password" is not compliant with the password policy.
-   Solution: Set a new password that meets password strength requirements.

**InvalidParameter.VirtualMFADeviceName.InvalidChars**

-   HTTP status: 400
-   Error message: The parameter - "VirtualMFADeviceName" contains invalid chars.
-   Solution: Enter the correct name of the virtual MFA device.

**InvalidParameter.VirtualMFADeviceName.Length**

-   HTTP status: 400
-   Error message: The parameter - "VirtualMFADeviceName" beyond the length limit.
-   Solution: Modify the length of VirtualMFADeviceName. The length cannot exceed 64 characters.

**InvalidParameter.GroupName.InvalidChars**

-   HTTP status: 400
-   Error message: The parameter - "GroupName" contains invalid chars.
-   Solution: Modify the value of GroupName. The value can contain letters, numbers, and hyphens \(-\).

**InvalidParameter.GroupName.Length**

-   HTTP status: 400
-   Error message: The parameter - "GroupName" beyond the length limit.
-   Solution: Modify the length of GroupName. The value must be 1 to 64 characters in length.

**InvalidParameter.NewGroupName.InvalidChars**

-   HTTP status: 400
-   Error message: The parameter - "NewGroupName" contains invalid chars.
-   Solution: Modify the value of NewGroupName. The value can contain letters, numbers, and hyphens \(-\).

**InvalidParameter.NewGroupName.Length**

-   HTTP status: 400
-   Error message: The parameter - "NewGroupName" beyond the length limit.
-   Solution: Modify the length of NewGroupName. The value must be 1 to 64 characters in length.

**InvalidParameter.PolicyType**

-   HTTP status: 400
-   Error message: The parameter - "PolicyType" is incorrect.
-   Solution: Modify the value of PolicyType. The value can be System or Custom.

**InvalidParameter.PolicyName.InvalidChars**

-   HTTP status: 400
-   Error message: The parameter - "PolicyName" contains invalid chars.
-   Solution: Modify the value of PolicyName. The value can contain letters, numbers, and hyphens \(-\).

**InvalidParameter.PolicyName.Length**

-   HTTP status: 400
-   Error message: The parameter - "PolicyName" beyond the length limit.
-   Solution: Modify the length of PolicyName. The value must be 1 to 128 characters in length.

**InvalidParameter.PolicyDocument.Length**

-   HTTP status: 400
-   Error message: The parameter - "PolicyDocument" beyond the length limit.
-   Solution: Modify the value of PolicyDocument. The value cannot exceed 2,048 bytes.

**InvalidParameter.Description.Length**

-   HTTP status: 400
-   Error message: The parameter - "Description" beyond the length limit.
-   Solution: Modify the value of Description. The value cannot exceed 1,024 bytes.

**InvalidParameter.VersionId.Format**

-   HTTP status: 400
-   Error message: The format of the parameter - "VersionId" is incorrect.
-   Solution: Modify the value of VersionId. The value must be consistent with the VersionId of the existing policy in the system.

**InvalidParameter.AccountAlias.Format**

-   HTTP status: 400
-   Error message: The format of parameter - "AccountAlias" is incorrect.
-   Solution: Modify the value of AccountAlias. The value can contain lowercase letters, numbers, and hyphens \(-\). It cannot start or end with hyphens \(-\) or contain consecutive hyphens \(such as --\).

## InvalidParameter.AccountAlias.Length {#section_rxt_3rc_nfb .section}

-   HTTP status: 400
-   Error message: The parameter - "AccountAlias" MUST be in the range of 3 and 63.
-   Solution: Modify the length of AccountAlias. The value must be 3 to 63 characters in length.

**InvalidParameter.MinimumPasswordLength.Range**

-   HTTP status: 400
-   Error message: The parameter - "MinimumPasswordLength" MUST be in the range of 8 and 32.
-   Solution: Modify the length of MinimumPasswordLength. The value must be 8 to 32 characters in length.

**InvalidParameter.AuthenticationCode.Format**

-   HTTP status: 400
-   Error message: The parameter - "AuthenticationCode" MUST be 6 numbers.
-   Solution: Modify the value of AuthenticationCode. The value must contain 6 numbers.

**MalformedPolicyDocument**

-   HTTP status: 400
-   Error message: \{The error details\}
-   Solution: Modify the policy content.

## HTTP status 403 {#section_eqv_gnv_xdb .section}

**NoPermission**

-   HTTP status: 403
-   Error message: You are not authorized to do this action.
-   Solution: Grant related permissions to the RAM user.

**Inactive**

-   HTTP status: 403
-   Error message: Your ram service is inactive, please activate it.
-   Solution: Activate the Alibaba Cloud RAM service.

**CheckAuthenticationCodeFail**

-   HTTP status: 403
-   Error message: The parameter - "AuthenticationCode" is inccorrect.
-   Solution: Enter the correct MFA authentication code.

## HTTP status 404 {#section_axq_hnv_xdb .section}

**EntityNotExist****EntityNotExist.User**

-   HTTP status: 404
-   Error message: The user does not exist.
-   Solution: Verify that the current RAM user exists in the system.

**EntityNotExist.User.AccessKey**

-   HTTP status: 404
-   Error message: The user access key does not exist.
-   Solution: Verify that the current AccessKey \(AK\) exists in the system.

## EntityNotExist.User.LoginProfile {#section_obn_vrc_nfb .section}

-   HTTP status: 404
-   Error message: The user login profile does not exist.
-   Solution: Allow the RAM user to log on to the console.

**EntityNotExist.User.MFADevice**

-   HTTP status: 404
-   Error message: The user has not bound any MFA device.
-   Solution: Attach an MFA device to the RAM user.

## EntityNotExist.User.Policy {#section_usc_yrc_nfb .section}

-   HTTP status: 404
-   Error message: The indicate policy of the user does not exist.
-   Solution: Verify that the policy name and RAM user name are correct.

**EntityNotExist.User.Group**

-   HTTP status: 404
-   Error message: The user has not joined the group.
-   Solution: Verify that the group name and RAM user name are correct.

**EntityNotExist.VirtualMFADevice**

-   HTTP status: 404
-   Error message: The virtual mfa device does not exist.
-   Solution: Verify that the virtual MFA device name is correct.

## EntityNotExist.Group {#section_rsx_1sc_nfb .section}

-   HTTP status: 404
-   Error message: The group does not exist.
-   Solution: Verify that the group exists.

**EntityNotExist.Group.Policy**

-   HTTP status: 404
-   Error message: The indicate policy attached to the group does not exist.
-   Solution: Verify that the group is attached to the policy and that the group name and policy name are correct.

**EntityNotExist.Policy**

-   HTTP status: 404
-   Error message: The policy does not exist.
-   Solution: Verify that the policy exists.

**EntityNotExist.Policy.Version**

-   HTTP status: 404
-   Error message: The policy version does not exist.
-   Solution: Verify that the policy version exists or has been deleted.

## HTTP status 409 {#section_vpq_3nv_xdb .section}

**EntityAlreadyExists****EntityAlreadyExists.User**

-   HTTP status: 409
-   Error message: The user does already EXIST.
-   Solution: Edit the RAM user name. Each RAM user name must be unique.

**EntityAlreadyExists.User.LoginProfile**

-   HTTP status: 409
-   Error message: The user login profile does already EXIST.
-   Solution: Do not attempt to enable console logon for RAM users repeatedly.

**EntityAlreadyExists.User.MFADevice**

-   HTTP status: 409
-   Error message: The user has already bound a MFA device.
-   Solution: Do not attempt to attach the MFA device to the RAM user repeatedly.

**EntityAlreadyExists.User.Group**

-   HTTP status: 409
-   Error message: The user has already joined the group.
-   Solution: Do not attempt to add the RAM user to the group repeatedly.

**EntityAlreadyExists.User.Policy**

-   HTTP status: 409
-   Error message: The user has already been attached this policy.
-   Solution: Do not attempt to attach the policy to the RAM user repeatedly.

**EntityAlreadyExists.VirtualMFADevice**

-   HTTP status: 409
-   Error message: The virtual mfa device does already EXIST.
-   Solution: Do not attempt to create the virtual MFA device repeatedly.

**EntityAlreadyExists.VirtualMFADevice.User**

-   HTTP status: 409
-   Error message: The virtual mfa device does already been bound to a user.
-   Solution: Do not attempt to attach the virtual MFA device to the RAM user repeatedly.

**EntityAlreadyExists.Group**

-   HTTP status: 409
-   Error message: The group does already EXIST.
-   Solution: Do not attempt to create a group repeatedly.

**EntityAlreadyExists.Group.Policy**

-   HTTP status: 409
-   Error message: The group has already been attached this policy.
-   Solution: Do not attempt to attach the policy to the group repeatedly.

**EntityAlreadyExists.Policy**

-   HTTP status: 409
-   Error message: The group does already EXIST.
-   Solution: Do not attempt to create a policy repeatedly.

**EntityAlreadyExists.AccountAlias**

-   HTTP status: 409
-   Error message: The account alias does already exist.
-   Solution: Set a new account alias after deleting existing account aliases by using ClearAccountAlias.

**DeleteConflict****DeleteConflict.User.Group**

-   HTTP status: 409
-   Error message: The user CAN NOT be in any group while deleting the user.
-   Solution: Remove the RAM user from the group before deleting it.

**DeleteConflict.User.AccessKey**

-   HTTP status: 409
-   Error message: The user CAN NOT has any access key while deleting the user.
-   Solution: Delete the AK of the RAM user before deleting the user.

**DeleteConflict.User.LoginProfile**

-   HTTP status: 409
-   Error message: The user CAN NOT has any login profile while deleting the user.
-   Solution: Delete the logon profile of the RAM user before deleting the user.

**DeleteConflict.User.MFADevice**

-   HTTP status: 409
-   Error message: The user CAN NOT has any mfa device while deleting the user.
-   Solution: Detach the MFA device from the RAM user before deleting the user.

**DeleteConflict.User.Policy**

-   HTTP status: 409
-   Error message: The user CAN NOT has any attached policy while deleting the user.
-   Solution: Revoke the policies of the RAM user before deleting the user.

**DeleteConflict.VirtualMFADevice.User**

-   HTTP status: 409
-   Error message: The virtual mfa device CAN NOT been bound to any user while deleting it.
-   Solution: Detach the virtual MFA device from the RAM user before deleting the device.

**DeleteConflict.Group.User**

-   HTTP status: 409
-   Error message: The group CAN NOT has any user member while deleting the group.
-   Solution: Remove the RAM user from the group before deleting the group.

**DeleteConflict.Group.Policy**

-   HTTP status: 409
-   Error message: The entity CAN NOT has any attached policy while deleting the group.
-   Solution: Revoke the policies of the group before deleting the group.

**DeleteConflict.Policy.User**

-   HTTP status: 409
-   Error message: The policy CAN NOT been attached to any user while deleting the policy.
-   Solution: Revoke the policies of the RAM user before deleting the policy.

**DeleteConflict.Policy.Group**

-   HTTP status: 409
-   Error message: The policy CAN NOT been attached to any group while deleting the policy.
-   Solution: Revoke the policies of the group before deleting the policy.

**DeleteConflict.Policy.Version**

-   HTTP status: 409
-   Error message: The policy CAN NOT has any version except the default version.
-   Solution: Retain only the default policy version before deleting the policy.

**DeleteConflict.Policy.Version.Default**

-   HTTP status: 409
-   Error message: The default policy version CAN NOT been deleted directly.
-   Solution: Verify the policy version you want to delete.

**DeleteConflict.Role.Policy**

-   HTTP status: 409
-   Error message: The role CAN NOT has any attached policy while deleting the role.
-   Solution: Revoke the policies of the role before deleting the role.

**LimitExceeded****LimitExceeded.User**

-   HTTP status: 409
-   Error message: The count of users beyond the current limits.
-   Solution: Remove one or more RAM users that you no longer require. The maximum number of RAM users allowed is 100.

**LimitExceeded.User.AccessKey**

-   HTTP status: 409
-   Error message: The access key count of the user access keys beyond the current limits.
-   Solution: Remove one or more AKs you no longer require. The maximum number of AKs allowed is 2.

**LimitExceeded.User.Group**

-   HTTP status: 409
-   Error message: The count of groups the target user joined beyond the current limits.
-   Solution: Remove the target RAM user from one or more user groups. The maximum number of groups a RAM user can join is 5.

**LimitExceeded.User.Policy**

-   HTTP status: 409
-   Error message: The policy count of the user attached policies beyond the current limits.
-   Solution: Remove one or more of the target policy type \(system or custom\) from the target RAM user. Each RAM user can be granted up to 20 system policies and up to 5 custom policies.

**LimitExceeded.VirtualMFADevice**

-   HTTP status: 409
-   Error message: The count of virtual mfa devices beyond the current limits.
-   Solution: Remove one or more virtual MFA devices you no longer require. The maximum number of virtual MFA devices allowed is 100.

**LimitExceeded.Group**

-   HTTP status: 409
-   Error message: The count of groups beyond the current limits.
-   Solution: Remove one or more groups you no longer require. The maximum number of groups allowed is 50.

**LimitExceeded.Group.Policy**

-   HTTP status: 409
-   Error message: The policy count of the group beyond the current limits.
-   Solution: Remove one or more policies you no longer require from the group. The maximum numbers of system policies and custom policies allowed are 20 and 5, respectively.

**LimitExceeded.Policy**

-   HTTP status: 409
-   Error message: The count of policy beyond the current limits.
-   Solution: Remove one or more custom policies you no longer require. The maximum number of custom policies allowed is 200.

**LimitExceeded.Policy.Version**

-   HTTP status: 409
-   Error message: The count of policy version beyond the current limits.
-   Solution: Remove one or more versions of the custom policy you no longer require. The maximum number of versions allowed is 5.

**LimitExceeded.Role**

-   HTTP status: 409
-   Error message: The count of roles beyond the current limits.
-   Solution: Remove one or more roles you no longer require. The maximum number of roles allowed is 100.

**LimitExceeded.Role.Policy**

-   HTTP status: 409
-   Error message: The count of policies attached to the role beyond the current limits.
-   Solution: Remove one or more policies attached to the role. The maximum numbers of system policies and custom policies that can be granted to a role is 20 and 5, respectively.

## HTTP status 500 {#section_ykv_jnv_xdb .section}

**InternalError**

-   HTTP status: 500
-   Error message: An internal error occurred.
-   Solution: Open a ticket.

