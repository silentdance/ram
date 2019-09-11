# What is RAM? {#concept_oyr_zzv_tdb .concept}

Resource Access Management \(RAM\) is a service provided by Alibaba Cloud to manage user identities and resource access permissions.

## Features {#section_pc7_qy7_6cj .section}

RAM allows you to create and manage multiple identities under an Alibaba Cloud account, and grant diverse permissions to a single identity or a group of identities. In this way, different RAM users are authorized to access different Alibaba Cloud resources. The following section lists the features of RAM:

-   You can manage RAM users and their AccessKey pairs. You can also enable multi-factor authentication \(MFA\) devices for RAM users.
-   You can manage the permissions of RAM users to access Alibaba Cloud resources.
-   You can manage resource access channels. This ensures that RAM users access specific Alibaba Cloud resources by using secure channels at the specified time from the specified IP address.
-   You can manage the instances or data created by RAM users. For enterprises, RAM ensures that the instances or data created by RAM users are still available even if the users leave the enterprises.
-   You can use single sign-on \(SSO\) services. Alibaba Cloud provides two types of SSO services for enterprise ID providers \(IdPs\): user-based SSO and role-based SSO.

## Scenarios {#section_e9w_v3i_71m .section}

|Scenario|Description|
|--------|-----------|
|[Use RAM to manage user permissions and resources](../../../../reseller.en-US/Best Practices/Use RAM to manage user permissions and resources.md#)|Enterprise A has purchased several types of Alibaba Cloud resources, such as ECS instances, ApsaraDB for RDS instances, SLB instances, and OSS buckets, for the migration of a project. Certain employees need to perform operations on these cloud resources. Different employees require different permissions to fulfill the corresponding duties.|
|[Use a temporary STS token to authorize a mobile app to access Alibaba Cloud resources](../../../../reseller.en-US/Tutorials/Use a temporary STS token to authorize a mobile app to access Alibaba Cloud resources.md#)|Enterprise A has developed a mobile app and purchased the OSS service. The app running on the users' own mobile devices are not controlled by Enterprise A. Permissions must be granted to the app to access OSS to upload or download data.|
|[Use a RAM role to grant permission across Alibaba Cloud accounts](../../../../reseller.en-US/Tutorials/Use a RAM role to grant permission across Alibaba Cloud accounts.md#)|Enterprise A has purchased various Alibaba Cloud resources, such as ECS instances, ApsaraDB for RDS instances, SLB instances, and OSS buckets. Enterprise A wants to delegate certain businesses to Enterprise B.|
|[Use RAM to authorize applications to access Alibaba Cloud resources](../../../../reseller.en-US/Tutorials/Use RAM to authorize applications to access Alibaba Cloud resources.md#)|Enterprise A has purchased ECS instances and wants to deploy apps in the ECS instances. The apps need to use AccessKey pairs to call API operations of other Alibaba Cloud services.|

## Benefits {#section_wx4_3pf_ti5 .section}

RAM allows you to create and manage RAM users, such as employees, systems, and apps. You can manage the permissions of RAM users to access Alibaba Cloud resources. RAM is also applicable in the scenario where multiple users in an enterprise need to collaboratively manage cloud resources. RAM allows you to grant the corresponding users the minimum required permissions, alleviating the need to share your Alibaba Cloud account and password. In this way, security risks for your enterprise are minimized.

## Endpoint {#section_nkc_r5s_gpw .section}

The endpoint for accessing RAM by calling API operations is `https://RAM.aliyuncs.com`.

