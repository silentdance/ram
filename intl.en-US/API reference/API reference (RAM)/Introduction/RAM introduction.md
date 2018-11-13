# RAM introduction {#reference_jz1_cmk_xdb .reference}

## What is RAM {#section_ynd_dmk_xdb .section}

Resource Access Management \(RAM\) is a resource access control service provided by Alibaba Cloud. RAM enables you to centrally manage your users \(such as employees, systems, or applications\) and control users' access to your resources.

## Issues to be resolved by RAM {#section_znd_dmk_xdb .section}

If you have bought cloud resources and several users in your organization need to use them, the users have to share your Alibaba Cloud account key. The following two issues need to be resolved: \(1\) Your Alibaba Cloud account key is shared by many people, causing a high risk of leakage; \(2\) You cannot control access to resources by specific users.

## How RAM resolves the issues {#section_a4d_dmk_xdb .section}

RAM allows you to create multiple RAM users under your Alibaba Cloud account and allocate them resource operation permissions. RAM users cannot possess resources or are not billed separately. These users are centrally controlled and billed under your Alibaba Cloud account. You can create separate passwords or keys for each RAM user, but by default these users don’t have any operation permissions. RAM provides an access-policy-based authorization mechanism to help you grant fine-grained authority to RAM users.

## RAM functions {#section_b4d_dmk_xdb .section}

**RAM has the following functions:**

-   Centralized control of RAM users and their keys - You can manage all users and their access keys, bind MFA devices to users and unbind MFA devices from users.
-   Centralized control of access permissions for RAM users - You can grant each user access to the resources you specify.
-   Centralized control of resource access mode of RAM users - You can ensure that users must use secure channels \(such as SSL\) to request access to specific cloud services at designated time in designated network environment.
-   Centralized control over cloud resources - You can centrally control the instances or data created by RAM users. When a user leaves your organization, these instances or data will not be lost.
-   Uniform bill - Your account will receive one bill for all expenses incurred by resource operations done by all users.

## RAM access point {#section_d4d_dmk_xdb .section}

The default RAM access point is `https://ram.aliyuncs.com` . You must connect to the access point through HTTPS.

## Alibaba Cloud products supporting RAM {#section_e4d_dmk_xdb .section}

Almost all Alibaba Cloud products are integrated with RAM. For details about services integrated with RAM, refer to  [Cloud services supporting RAM](../../../../intl.en-US/Product Introduction/Cloud services supporting RAM.md).

## RAM service charges {#section_f4d_dmk_xdb .section}

The RAM service is a function of your Alibaba Cloud account and does not produce any extra charges. You only need to pay for the other services used by your RAM users.

