# Overview of security settings {#concept_662738 .concept}

This topic describes some commonly used concepts that are relevant to security settings in the RAM console.

## Password {#section_zv5_aqh_xn8 .section}

An identity credential that is used by a user to log on to Alibaba Cloud.

**Note:** We recommend that you change your password periodically and keep your password private.

For information about how to set a password, see [Change the password for an Alibaba Cloud account](reseller.en-US/User Guide/Security settings/Passwords/Change the password for an Alibaba Cloud account.md#) and [Change the password for a RAM user](reseller.en-US/User Guide/Security settings/Passwords/Change the password for a RAM user.md#).

## Default domain name {#section_por_wog_qlj .section}

A unique identifier of an Alibaba Cloud account that is used in scenarios such as RAM user logon and Single Sign On \(SSO\) management. Alibaba Cloud assigns a default domain name for each Alibaba Cloud account in the `<AccountAlias>.onaliyun.com` format.

For information about how to set a default domain name, see [Manage the default domain name of an Alibaba Cloud account](reseller.en-US/User Guide/Security settings/Advanced settings/Manage the default domain name of an Alibaba Cloud account.md#).

## Domain alias {#section_me3_fct_ps0 .section}

A custom domain name that can be used to replace the default domain name provided by the system.

**Note:** A domain alias can be used only after domain ownership verification.

For information about how to set a domain alias, see [Create a domain alias for an Alibaba Cloud account](reseller.en-US/User Guide/Security settings/Advanced settings/Create a domain alias for an Alibaba Cloud account.md#).

## Access key {#section_han_75i_9to .section}

The combination of an access key ID and an access key secret. You can use your access key or Alibaba Cloud SDK to sign API requests that you make to Alibaba Cloud.

The access key ID and access key secret are used together to sign programmatic Alibaba Cloud requests cryptographically. The access key ID is used to identify a user, whereas the access key secret is used to encrypt and verify a signature.

**Note:** The access key secret is displayed only once when you first create it. We recommend that you save the access key secret for subsequent use.

For information about how to create an access key, see [Create an access key for a RAM user](reseller.en-US/User Guide/Security settings/Access keys/Create an access key for a RAM user.md#).

## Multi-factor authentication \(MFA\) {#section_3a0_r17_zmk .section}

A simple best practice that adds an extra layer of protection on top of your username and password. When you log on to Alibaba Cloud with MFA enabled, the system requires the following two security factors:

1.  Your username and password
2.  Verification code provided by the MFA device

For information about how to set MFA, see [Enable an MFA device for an Alibaba Cloud account](reseller.en-US/User Guide/Security settings/Multi-factor authentication/Enable an MFA device for an Alibaba Cloud account.md#) and [Enable an MFA device for a RAM user](reseller.en-US/User Guide/Security settings/Multi-factor authentication/Enable an MFA device for a RAM user.md#).

