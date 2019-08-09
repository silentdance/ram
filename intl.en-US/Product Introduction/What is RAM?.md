# What is RAM? {#concept_oyr_zzv_tdb .concept}

Alibaba Cloud Resource Access Management \(RAM\) is an identity and access management service that helps you manage user identities and access to your Alibaba Cloud resources. You can use RAM to create and manage RAM users and control their level of access permissions to resources under your Alibaba Cloud account. RAM allows you to give users the minimum level of necessary permissions to reduce security risks.

## Features of RAM {#section_dzq_6ri_ebx .section}

RAM allows you to create and manage multiple identities under an Alibaba Cloud account and to attach different policies to different identities or identity groups. That is, RAM grants different resource access permissions to different RAM users. The features of RAM are as follows:

-   You can create and manage RAM users and their access keys under your Alibaba Cloud account and attach or deactivate MFA devices for them.
-   You can attach one or more policies to a RAM user or a RAM user group to restrict users' operation permissions for Alibaba Cloud resources.
-   You can specify that RAM users use security channels \(for example, SSL\) to operate on the specified Alibaba Cloud resources at a specified time or from specified source IP addresses.
-   You can centrally control the instances and data created by RAM users. Therefore, when a user leaves your organization, you can still fully control the user's instances and data.
-   You can implement Single Sign On \(SSO\), such as user-based SSO or role-based SSO, between your enterprise IdPs and Alibaba Cloud.

## Application scenarios of RAM {#section_2o8_law_8rj .section}

|Application scenario|Description|
|--------------------|-----------|
|[../../../../dita-oss-bucket/SP\_65/DNRAM11894803/EN-US\_TP\_23773.md\#](../../../../reseller.en-US/Best Practices/User management and access control.md#)|Enterprise A has bought several types of Alibaba Cloud resources, such as ECS instances, RDS instances, SLB instances, and OSS buckets for a project. During this project, many employees need to perform operations on these cloud resources, but different employees require different permissions to complete different operations.|
|[Grant temporary permissions to mobile apps](../../../../reseller.en-US/Best Practices/Grant temporary permissions to mobile apps.md#)|Enterprise A has developed a mobile app, which runs on users' own devices. Therefore, Enterprise A cannot manage these devices directly and wants to use Alibaba Cloud OSS so that the mobile app can upload data to or download data from OSS.|
|[Cross-account resource authorization and access](../../../../reseller.en-US/Best Practices/Cross-account resource authorization and access.md#)|Enterprise A has bought various Alibaba Cloud resources \(such as ECS instances, RDS instances, SLB instances, and OSS buckets\) to support its business. Account A is the resource owner and wants to grant Account B the relevant permissions to perform operations on resources of Account A.|
|[Use RAM to authorize applications to access Alibaba Cloud resources](../../../../reseller.en-US/Best Practices/Use RAM to authorize applications to access Alibaba Cloud resources.md#)|An enterprise has bought ECS instances and wants to deploy its applications in ECS. To allow the applications to access other Alibaba Cloud APIs by using access keys.|

## Accessing RAM {#section_84q_m6p_rlf .section}

The endpoint for accessing RAM by calling API actions is `https://ram.aliyuncs.com`.

## Free to use {#section_sh7_jy8_vsp .section}

You can use RAM for free after you create an Alibaba Cloud account.

To activate the RAM service, go to the RAM activation page.

**Note:** The RAM service cannot be deactivated after you activate it.

## Alibaba Cloud services that work with RAM {#section_b13_vex_zdm .section}

See [Alibaba Cloud services that work with RAM](reseller.en-US/Product Introduction/Alibaba Cloud services that work with RAM.md#).

