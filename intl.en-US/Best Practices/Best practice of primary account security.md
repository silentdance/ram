# Best practice of primary account security {#concept_wzh_wkk_xdb .concept}

A primary account is equivalent to a root account that controls all of your cloud resources. As such, if the primary account password or API AccessKey is lost or disclosed, this may cause immeasurable loss to your enterprise.

So how to protect the security of your primary account? This document makes a reference for you.

## Principle 1: Enable account protection for the root account {#section_a52_ykk_xdb .section}

-   Enable account protection for your root account and do not share the MFA device with others.
-   Enable MFA for RAM users with special operation permissions. Special operation permissions include user management, authorization, instance stopping/release, instance configuration modification, and data deletion.

## Principle 2: Create different RAM accounts for routine O&M management operations {#section_urz_ykk_xdb .section}

-   Create RAM user accounts for employees and use them to perform routine O&M management operations.
-   Create independent RAM user accounts for financial employees.
-   Create independent RAM user accounts for RAM administrators.

## Principle 3: Prohibit creation of an AccessKey for the root account {#section_q5n_xkk_xdb .section}

AccessKeys have the same permissions as logon passwords. However, AccessKeys are used for program access while logon passwords are used to log on to the console. Because AccessKeys are generally stored in configuration files in cleartext format, there is a high leakage risk.

Configure RAM user identities for all application systems and follow the minimum authorization rule in the case of [Attach policies to a RAM user](../../../../reseller.en-US/Quick Start/Attach policies to a RAM user.md#).

## Principle 4: Use authorization policies with IP restrictions {#section_r5n_xkk_xdb .section}

All users that are granted special operation permissions must be [configured with IP restrictions \(acs:SourceIp\)](../../../../reseller.en-US/Quick Start/Create a custom policy (optional).md).

Therefore, even if a RAM user’s logon password or AccessKey is disclosed, attackers will be unable to obtain account information as long as they have not penetrated your trusted network.

## Principle 5: Use authorization policies with MFA restrictions {#section_s5n_xkk_xdb .section}

All users that are granted special operation permissions must be [configured with MFA restrictions \(acs:MFAPresent\)](../../../../reseller.en-US/Quick Start/Set up MFA (optional).md#).

Therefore, even if a RAM user’s logon password or AccessKey is disclosed, attackers will be unable to obtain account information as long as the MFA device is not lost.

For more restrictions, see [Syntax](../../../../reseller.en-US/User Guide/Policy Language/Policy syntax structure.md#).

There is no such thing as absolute security, but only best practices. In combination with these protection mechanisms, adherence to the best security practice principles will significantly secure your account assets.

