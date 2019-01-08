# Maintain account security {#concept_wzh_wkk_xdb .concept}

An account is equivalent to a root account that controls all of your cloud resources. If the account password or API AccessKey \(AK\) is lost or disclosed, immeasurable loss may be caused to your enterprise.

To maintain account security, follow these account security practice principles:

## Principle 1: Enable MFA for your account {#section_a52_ykk_xdb .section}

-   Enable Multi-Factor Authorization \(MFA\) for your account and do not share your MFA device with others.
-   Enable MFA for RAM users with special operation permissions. Special operation permissions include user management, authorization, instance stopping/release, instance configuration modification, and data deletion.

## Principle 2: Create different RAM accounts for routine O&M operations {#section_urz_ykk_xdb .section}

-   Create independent RAM user accounts for RAM administrators.
-   Create RAM user accounts for employees for routine O&M.
-   Create independent RAM user accounts for financial staffs.

## Principle 3: Do not create an AK for your account {#section_q5n_xkk_xdb .section}

AKs have the same permissions as logon passwords. However, AKs are used for program access while logon passwords are used to log on to the console. Because AKs are stored in cleartext in configuration files, there is a higher disclosure risk.

Configure RAM user identities for all application systems and follow the minimum authorization principle in the case of [attaching policies to a RAM user](../../../../../reseller.en-US/Quick Start/Authorize RAM users.md#).

## Principle 4: Use policies with IP restrictions {#section_r5n_xkk_xdb .section}

All users that are granted special operation permissions must be configured with IP restrictions \(acs:SourceIp\).

Therefore, even if a RAM user's logon password or AK is disclosed, attackers will be unable to obtain account information as long as they have not penetrated your trusted network.

## Principle 5: Use policies with MFA restrictions {#section_s5n_xkk_xdb .section}

All users that are granted special operation permissions must be configured with MFA restrictions \(acs:MFAPresent\).

Therefore, even if a RAM user's logon password or AK is disclosed, attackers will be unable to obtain account information as long as the MFA device is not lost.

For more restrictions, see [Policy language syntax](../../../../../reseller.en-US/User Guide/Permission management/Policy language/Policy language syntax.md#).

There is no such thing as absolute security, but only best practices. In combination with these protection mechanisms, adherence to the best security practice principles will significantly secure your account assets.

