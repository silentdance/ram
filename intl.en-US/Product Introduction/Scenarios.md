# Scenarios {#concept_xrp_jt2_xdb .concept}

RAM is applicable to user account management and authorization in an enterprise, resource management and authorization between enterprises, and temporary authorization and management for apps running on untrusted user equipment \(UE\).

## Account management and authorization in an enterprise {#section_rvv_kt2_xdb .section}

Assume that Enterprise A purchases several types of Alibaba Cloud resources \(such as ECS instances, RDS instances, SLB instances, and OSS buckets\), and its employees need to operate on these resources \(such as purchase new resources and perform O&M\). Different employees require different permissions because the employees have different responsibilities.

Requirements:

-   For security and reliability, Enterprise A does not want to disclose its account key to its employees. Enterprise A prefers to create different RAM user accounts for their employees.
-   The employees can operate on resources only after they are authorized. All the fees incurred by the employees will not be charged independently but be paid by Enterprise A.
-   Enterprise A can revoke the permissions of a RAM user account or delete a RAM user account at any time.

## Resource management and authorization between enterprises {#section_tvv_kt2_xdb .section}

Assume that there are Enterprises A and B, and Enterprise A has purchased many Alibaba Cloud resources \(such as ECS instances, RDS instances, SLB instances, and OSS buckets\) for its business requirements.

Requirements:

-   Enterprise A wants to focus on its business systems, so it entrusts O&M, monitoring, and management for its cloud resources to Enterprise B, and grants Enterprise B permissions for RAM.
-   Enterprise B can assign O&M tasks to its employees. In this way, Enterprise B can precisely control the employees' permissions on the cloud resources of Enterprise A.
-   If Enterprises A and B terminate their O&M entrustment contract, Enterprise A can revoke the permissions of Enterprise B at any time.

## Temporary authorization and management for apps running on untrusted UE {#section_vvv_kt2_xdb .section}

Assume that Enterprise A has developed a mobile app and has purchased OSS for it. Enterprise A can then upload data to and download data from their OSS bucket for app data.

Requirements:

-   Enterprise A does not want to use their application server to transmit data to and from OSS. Instead, they want their application to have direct permission to send data to OSS.
-   Because the mobile application runs on untrusted UE that is not controlled by Enterprise A, the enterprise does not want to store their security key in the application.
-   Enterprise A wants to minimize security risks by, for example, giving the app a temporary access token with the minimum permissions that the app needs to connect to OSS and restricting the access duration to a 30 minute window.

