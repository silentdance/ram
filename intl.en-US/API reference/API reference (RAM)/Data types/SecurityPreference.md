# SecurityPreference {#reference_alh_5mv_xdb .reference}

## Description {#section_erh_xh4_xdb .section}

Security preference

## Node name {#section_nps_yh4_xdb .section}

SecurityPreference

## Subnode**\[LoginProfilePreference\]** {#section_ldp_zh4_xdb .section}

**EnableSaveMFATicket**

-   Type: Boolean
-   Required: No
-   Description: Whether to allow users to save the MFA authentication ticket at logon. The ticket validity period is currently 7 days.

**AllowUserToChangePassword**

-   Type: Boolean
-   Required: false
-   Description: Whether to allow users to modify their own passwords.

**Subnode \[AccessKeyPreference\]****AllowUserToManageAccessKeys**

-   Type: Boolean
-   Required: false
-   Description: Whether to allow users to manage their own AccessKeys.

## Subnode \[MFAPreference\] {#section_ivn_wmv_xdb .section}

**AllowUserToManageMFADevices**

-   Type: Boolean
-   Required: false
-   Description: Whether to allow users to bind or unbind their own MFA devices.

