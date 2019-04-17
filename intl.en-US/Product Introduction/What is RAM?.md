# What is RAM? {#concept_oyr_zzv_tdb .concept}

Alibaba Cloud Resource Access Management \(RAM\) is an identity and access management service that helps you manage user identities and control access to your cloud resources. You can use RAM to create and manage RAM users and control their level of access permissions to resources under your Alibaba Cloud account. RAM allows you to give users the minimum level of necessary permissions to reduce security risks.

## Identity {#section_swm_q1w_tdb .section}

An identity refers to any person, system, or application that uses resources in the RAM console or through APIs. To manage identities in different application scenarios, RAM supports two types of identities: RAM users and RAM roles.

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

-   An account and its RAM users have a parent-child relationship.
    -   An account is the basic entity for judging the ownership of Alibaba Cloud resources and billing for resource consumption.
    -   Resources a RAM user creates belong to the parent \(root\) account to which the RAM user belongs. Similarly, resources created by RAM users are billed against the parent \(root\) account rather than against the RAM account.
-   From the permission perspective, an Alibaba Cloud account could be considered to be a "root" account and RAM accounts are "users" \(similar to the security model used in Linux\).
    -   The root user has all operation and control permissions for resources.
    -   RAM users only have permissions that are granted by the root user. The root user can revoke the permissions of a RAM user at any time.

## Use RAM to manage cloud resources for enterprises {#section_ywm_q1w_tdb .section}

RAM can be used to help enterprises with the following requirements:

-   An enterprise needs to manage the account and permissions of each operator \(or application\) in a simplified manner.
-   An enterprise does not want to calculate the costs and fees for each operator \(or application\) separately.

The following figure is a simplified illustration of how RAM works.

![](images/3479_en-US.png "Enterprise scenario")

-   Company A only needs one account \(for example, companyA@alibabacloud.com\).
-   All resources belong to the account. As the resource owner, the account has full control over all resources. It also pays for all bills.
-   Company A can use RAM to create independent RAM users for operators \(the employees who perform operation and maintenance on resources\) and grant permissions to the RAM users.
-   RAM users do not possess resources. By default, they do not have access permissions for the resources they create and can only operate on the resources after they are authorized.
-   The fees incurred by RAM users are billed to accounts that they belong to. RAM users do not receive individual bills and cannot make payments.

