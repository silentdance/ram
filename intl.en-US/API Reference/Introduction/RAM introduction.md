# RAM introduction {#reference_jz1_cmk_xdb .reference}

## What is RAM? {#section_ynd_dmk_xdb .section}

Resource Access Management \(RAM\) is a resource access control service provided by Alibaba Cloud that enables you to centrally manage your users, systems, and applications, and control access to your resources.

## Issues that are resolved by RAM {#section_znd_dmk_xdb .section}

If you have purchased some cloud resources and several users in your organization need to use them, the users require access to your Alibaba Cloud account. In this case, the following issues may occur:

1.  Sharing the AccessKey \(AK\) of your Alibaba Cloud account may mistakenly expose all of your cloud resources.
2.  You cannot grant resource-specific access permissions to users.

## Handling methods {#section_a4d_dmk_xdb .section}

-   RAM allows you to create multiple RAM users under your Alibaba Cloud account and grant each RAM user the necessary resource operation permissions.
-   RAM users cannot possess resources. They are centrally controlled and billed under your Alibaba Cloud account.
-   You can create an independent password or AK for each RAM user, but RAM users do not have any operation permissions by default. RAM allows you to use access policies to control the authorization and access of your resources.

## Functions {#section_b4d_dmk_xdb .section}

RAM provides the following functions:

-   Centralized control of RAM users and their AKs: You can manage RAM users and their AKs, and attach and detach MFA devices to and from RAM users as needed.
-   Centralized control of access permissions of RAM users: You can grant operation permissions for specific cloud resources to a RAM user.
-   Centralized control of the resource access mode of RAM users: Through RAM, RAM users use secure channels \(for example, SSL\) to request access to specific cloud services at a specified time point in a specific network environment.
-   Centralized control over cloud resources: You can centrally control the instances or data created by RAM users. When a user is removed from your organization, these instances or data will be retained.
-   Centralized billing of charges: You need to pay for all charges incurred by resource operations of both your Alibaba Cloud account and RAM users.

## Endpoint {#section_d4d_dmk_xdb .section}

The endpoint for API access is `https://ram.aliyuncs.com`.

## Alibaba Cloud products supporting RAM {#section_e4d_dmk_xdb .section}

RAM can be integrated with a wide range of Alibaba Cloud products. For more information, see [Alibaba Cloud services that work with RAM](../../../../reseller.en-US/Product Introduction/Alibaba Cloud services that work with RAM.md).

## Pricing {#section_f4d_dmk_xdb .section}

Alibaba Cloud RAM is provided free of charge. You only incur fees from RAM users using other services under your Alibaba Cloud account.

