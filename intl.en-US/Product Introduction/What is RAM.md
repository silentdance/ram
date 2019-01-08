# What is RAM {#concept_oyr_zzv_tdb .concept}

Resource Access Management \(RAM\) is a cloud service that helps you manage identities and control resource access. You can use RAM to create and manage user \(such as employees, systems, and applications.\) and control the users' operation permissions on resources. When multiple users in your enterprise collaboratively operate on resources, RAM keeps the users' keys confidential and grant users the minimum permissions to reduce information security risks.

## Identity management and access control {#section_rwm_q1w_tdb .section}

RAM allows you to create and manage multiple identities under an account and to attach different policies to different identities or identity groups. That is, RAM grants different resource access permissions to different users.

## Identity {#section_swm_q1w_tdb .section}

An identity refers to any person, system, or application that uses resources in the RAM console or through open APIs. To manage identities in different application scenarios, RAM supports two types of identities, RAM users and RAM roles.

-   A RAM user is an entity identity with a fixed ID and an identity authentication key. Generally, a RAM user corresponds to a person or an application.
-   A RAM role is a virtual identity with a fixed ID but without an identity authentication key.

A RAM role must be associated with an entity identity before it can be used. A RAM role can be associated with multiple entity identities, such as:

-   RAM users under the current account
-   RAM users under another account
-   Alibaba Cloud services \(such as EMR or MTS\)
-   External real identities \(such as a local enterprise account\)

## Policy {#section_uwm_q1w_tdb .section}

RAM allows you to create and manage multiple policies under your account. In essence, each policy is a collection of permissions. Administrators can attach one or more policies to a RAM identity \(a RAM user or RAM role\).

The RAM policy language expresses fine-grained authorization semantics. A policy can grant permissions to a specific API action or resource ID and specify multiple restrictions \(such as source IP address, access time, and MFA\).

## Relationship between accounts and RAM users {#section_rfk_hs2_xdb .section}

-   From the ownership perspective, an account and its RAM users are in parent-child relationship.
    -   An account is the basic entity for judging the ownership of Alibaba Cloud resources and billing for resource consumption.
    -   RAM users exist only in RAM instances of a certain account. RAM users do not possess resources, and the resources they create under authorization belong to their accounts. RAM users do not possess bills, and all fees incurred by their authorized operations are debited to their accounts.
-   From the permission perspective, an account and its RAM users are in root–user relationship \(similar to the relationship in Linux\).
    -   The root user has all operation and control permissions on resources.
    -   RAM users only have permissions that are granted by the root user. The root user can revoke the permissions at any time.

## Use RAM to manage cloud resources for enterprises {#section_ywm_q1w_tdb .section}

RAM is applicable to the following enterprise scenarios:

-   An enterprise needs to manage the account and permissions of each operator \(or application\) in a simplified manner.
-   An enterprise does not want to calculate the costs and fees for each operator \(or application\) separately.

The specific requirements are shown in the following figure.

![](images/3479_en-US.png "Enterprise scenario")

-   Company A only needs one account \(for example, companyA@aliyun.com\).
-   All resources belong to the account. As the resource owner, the account has full control over all resources. It also pays for all bills.
-   Company A can use RAM to create independent users for operators \(the employees who perform operation and maintenance on resources\) and grant permissions to the users.
-   Users do not possess resources. By default, they do not have access permissions on the resources they create and can only operate on the resources after they are authorized.
-   The fees incurred due to operations of user accounts are billed by their accounts. Users have no permission to pay for themselves.

