# What is RAM? {#concept_oyr_zzv_tdb .concept}

Alibaba Cloud Resource Access Management \(RAM\) is an identity and access management service that helps you manage user identities and access to your cloud resources. You can use RAM to create and manage RAM users and control their level of access permissions to resources under your Alibaba Cloud account. RAM allows you to give users the minimum level of necessary permissions to reduce security risks.

## Identity {#section_swm_q1w_tdb .section}

An identity refers to any person, system, or application that uses resources in the RAM console or through APIs. To manage identities in different application scenarios, RAM supports two types of identities: RAM users and RAM roles. For more information, see [Terms](reseller.en-US/Product Introduction/Terms.md#).

## Features of RAM {#section_79b_qmz_1va .section}

RAM allows you to create and manage multiple identities under an Alibaba Cloud account and to attach different policies to different identities or identity groups. That is, RAM grants different resource access permissions to different RAM users. The features of RAM are as follows:

-   Manage RAM users and their keys: You can create and manage RAM users and their keys under your Alibaba Cloud account and attach Multi-Factor Authentication \(MFA\) devices for them.
-   Mange access permissions of RAM users: You can manage a RAM user's permission for operating on resources.
-   Manage resource access methods of RAM users: You can specify that RAM users must use security channels to operate on specified cloud resources at a specified time or from specified source IP addresses.
-   Manage cloud resources: You can manage the instances and data created by RAM users. Therefore, when a user leaves your organization, you can still fully control the user's instances and data.
-   Manage Single Sign On \(SSO\): You can perform user-based SSO or role-based SSO to Alibaba Cloud by using your identity provider \(IdP\).

## Policy {#section_uwm_q1w_tdb .section}

RAM allows you to create and manage multiple policies under your Alibaba Cloud account. Each policy is a collection of permissions. Administrators can attach one or more policies to a RAM user, a RAM user group, or a RAM role.

The RAM policy language expresses fine-grained authorization semantics. A policy can grant permissions to a specific action or resource and specify multiple restrictions \(such as the source IP address, access time, and MFA\). For more information, see [Policy management](../../../../reseller.en-US/User Guide/Permission management/Policy management.md#).

## Accessing RAM {#section_84q_m6p_rlf .section}

The endpoint for API access is `https://ram.aliyuncs.com`.

## Free to use {#section_sh7_jy8_vsp .section}

You can use RAM for free after creating an Alibaba Cloud account.

You can go to the RAM logon page to create an Alibaba Cloud account.

## Alibaba Cloud services that work with RAM {#section_b13_vex_zdm .section}

See [Alibaba Cloud services that work with RAM](reseller.en-US/Product Introduction/Alibaba Cloud services that work with RAM.md#).

