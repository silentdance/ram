# Security setting overview {#concept_662738 .concept}

This topic describes some commonly used concepts that are relevant to security settings in the RAM console.

## Password {#section_zv5_aqh_xn8 .section}

Your password is an identity credential that is used to verify your real identity.

**Note:** We recommend that you change your password periodically and keep your password private.

For information about how to set a password, see [Change the password for a RAM user](reseller.en-US/User Guide/Security settings/Passwords/Change the password for a RAM user.md#).

## Default domain name {#section_por_wog_qlj .section}

A default domain name is a unique identifier of an Alibaba Cloud account that is used in scenarios such as RAM user logon and Single Sign On \(SSO\) management. Alibaba Cloud assigns a default domain name for each Alibaba Cloud account in the format of `<AccountAlias>.onaliyun.com`.

For information about how to set a default domain name, see [Manage the default domain name of an Alibaba Cloud account](reseller.en-US/User Guide/Security settings/Advanced settings/Manage the default domain name of an Alibaba Cloud account.md#).

## Domain alias {#section_me3_fct_ps0 .section}

A domain alias is a custom domain name that can be used to replace the default domain name provided by the system.

**Note:** A domain alias can be used only after domain ownership verification.

For information about how to change you domain alias, see [Create a domain alias for an Alibaba Cloud account](reseller.en-US/User Guide/Security settings/Advanced settings/Create a domain alias for an Alibaba Cloud account.md#).

## Access key {#section_han_75i_9to .section}

Access keys are long-term credentials for a RAM user or the Alibaba Cloud account. An access key consists of an access key ID and an access key secret. You can use access keys or Alibaba Cloud SDKs to initiate API requests. Alibaba Cloud RAM uses access key IDs and access key secrets to authenticate your requests. You can access Alibaba Cloud resources after you are authenticated.

Like a username and password, you must use both the access key ID and access key secret together to authenticate your requests. Access key IDs are used to identify the identity of a user, and access key secrets are used to encrypt and authenticate signature strings.

**Note:** The access key secret is displayed only once when you first create it. We recommend that you save the access key secret for subsequent use.

For information about how to create an access key, see [Create an access key for a RAM user](reseller.en-US/User Guide/Security settings/Access keys/Create an access key for a RAM user.md#).

## Multi-factor authentication {#section_3a0_r17_zmk .section}

Multi-factor authentication \(MFA\) is a simple but effective means for achieving a higher level security protection. When you log on to Alibaba Cloud with MFA enabled, the system requires the following two security factors:

-   Your username and password
-   The verification code provided by your target virtual MFA device

For information about how to set MFA, see [Enable an MFA device for an Alibaba Cloud account](reseller.en-US/User Guide/Security settings/Multi-factor authentication/Enable an MFA device for an Alibaba Cloud account.md#) and [Enable an MFA device for a RAM user](reseller.en-US/User Guide/Security settings/Multi-factor authentication/Enable an MFA device for a RAM user.md#).

