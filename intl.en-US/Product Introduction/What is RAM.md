# What is RAM {#concept_oyr_zzv_tdb .concept}

Resource Access Management \(RAM\) is a cloud service that helps you **manage user identities** and **control resources access**. Using RAM, you can create and manage user accounts, and control the operation permissions that these user accounts possess for resources under your account, for example, employees, systems, and applications. If multiple users in your enterprise collaboratively work with resources, using RAM allows you to avoid sharing your Alibaba Cloud account AccessKey with other users. Instead, you can grant users the minimum permissions needed to complete their work, reducing security risks of your enterprise.

## Identity management and access control {#section_rwm_q1w_tdb .section}

RAM allows you to create and manage multiple user identities under an account, and attach different authorization policies to different identities or identity groups. This grants different resource access permissions to different users.

## Identity {#section_swm_q1w_tdb .section}

Identity refers to any person, system, or application that uses resources from the console or by using Open APIs. To enable identity management in different application scenarios, RAM supports two types of identities, which are RAM-User and RAM-Role.

-   A RAM-User is a real identity of a fixed ID and an identity authentication AccessKey. Generally, a RAM-User refers to a person or an application.

-   A RAM-Role is a virtual identity of a fixed ID, but no identity authentication AccessKey.


A RAM-Role must be associated with a real identity before it becomes available. A RAM-Role can be associated with multiple real identities, such as RAM-Users under the current Alibaba Cloud account, RAM-Users under another Alibaba Cloud account, Alibaba Cloud services \(such as EMR or MTS\), and External real identities \(such as a local enterprise account\).

## Authorization {#section_uwm_q1w_tdb .section}

RAM allows you to create and manage multiple authorization policies under your Alibaba Cloud account. In essence, each authorization policy is a collection of permissions. Administrators can attach one or more authorization policies to a RAM identity \(including RAM-Users and  RAM-Roles\).

The RAM authorization policy language expresses the meaning of the authorization policy in detail. A policy can grant permissions to an API-Action and Resource-ID, and specify multiple restrictions \(such as source IP address, access time, and MFA\).

## RAM user vs. Alibaba Cloud account {#section_rfk_hs2_xdb .section}

-   From an **ownership** point of view, the relationship between your Alibaba Cloud account and its RAM users is like parent-child.
    -   An Alibaba Cloud account is the basic entity for judging the ownership of Alibaba Cloud resources and billing for resource consumption.
    -   RAM users exist only in the RAM instances of a certain Alibaba Cloud account. RAM users do not possess resources, and the resources they create under authorization belong to the parent account. RAM users do not possess bills, and all expenses incurred by their authorized operations are debited to the parent account.
-   In terms of **permissions**, the relationship between your Alibaba Cloud account and its RAM users is like root–user \(such as the relationship in Linux\).
    -   The root user has all operation and control permissions for resources.
    -   A RAM user has only some permissions that are granted by the root user. In addition, the root user can revoke the permissions granted to a RAM user at any time.

## Perform enterprise-level cloud resource management using RAM {#section_ywm_q1w_tdb .section}

RAM is applicable to the following enterprise scenarios:

-   An enterprise needs to easily manage the account and permissions of each operator \(or application\).
-   An enterprise does not want to calculate the costs and fees for each operator \(or application\) separately.

The specific requirements are shown as follows:

![](images/3479_en-US.png "Enterprise scenario")

-   Company A only needs one Alibaba Cloud account \(in the figure, this is companyA@aliyun.com\).
-   All resources belong to this Alibaba Cloud account. As the resource owner, this account has full control of all resources. This account is also responsible for paying all bills.
-   A can use RAM to create independent user accounts for operators under the account \(the employees who perform operation and maintenance on resources\) and perform authorization management.
-   User accounts do not possess resources. By default they do not have access permissions for the resources they create and can only perform operations on resources after their permissions are authorized. 
-   The charges incurred due to operations of user accounts are billed to the primary account. Separate billing for user accounts is not supported.

## Learning path {#section_mkm_gkx_42b .section}

Visit the [RAM Learning Path](https://help.aliyun.com/learn/learningpath/ram.html) for the knowledge you need to become a RAM expert!

