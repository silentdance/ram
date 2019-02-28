# Use an externally authorized account to log on to Alibaba Cloud {#concept_d2j_wdk_xdb .concept}

This topic describes how to authenticate the identity of an internal enterprise account before the internal account is used to access Alibaba Cloud resources.

## Scenario {#section_w1b_xdk_xdb .section}

Enterprise A has two departments that use Alibaba Cloud resources. Each department has its own Alibaba Cloud account \(named as A1 and A2\). Enterprise A also has its own domain account system, namely Microsoft Active Directory \(AD\) and Active Directory Federation Services \(AD FS\).

Enterprise A has strict requirements on identity access management:

-   All operations on Alibaba Cloud must pass identity authentication through the domain account system of Enterprise A. All employees are prohibited from using independent accounts and passwords to access the cloud resources.
-   Enterprise A wants to integrate its Alibaba Cloud RAM users with its local domain account system, so that all employees must use their local domain accounts to log on to Alibaba Cloud before they can access the authorized cloud resources.

## Solution {#section_y1b_xdk_xdb .section}

**Relevant concepts**

The following table describes the concepts relevant to this solution.

|Concept|Description|
|:------|:----------|
|Workload Account|Purchases Alibaba Cloud resources, such as ECS instances, RDS, and OSS.|
|Identity Account|Creates only RAM uses under an Alibaba Cloud account.|
|Service Provider|Uses the identity management function of an IdP to provide users with specific service applications. An SP uses the user information provided by an Identity Provider \(IdP\).|

If an enterprise has two Workload Accounts, follow these steps:

1.  Create an independent Identity Account.
2.  Use the Identity Account as a service provider and integrate it with the local IdP to implement Single Sign On \(SSO\).
3.  Use the cross-account access function provided by Alibaba Cloud through RAM roles to authorize its RAM users \(employees\) to access the resources under other Alibaba Cloud accounts.

![Process](images/14411_en-US.png "Process")

## Procedure {#section_bgh_m5j_pfb .section}

1.  Register a new Alibaba Cloud account and use it as an Identity Account \(A0\).

    **Note:** A0 is used to resolve issues concerning user synchronization and SSO.

2.  Use the account A0 to log on to the **RAM console** and configure SSO.
3.  In the AD FS of the enterprise, add A0 as a service provider.
4.  Synchronize local domain users who need to access the cloud resources to RAM.
5.  Use the Workload Account A1 to log on to the RAM console, create a RAM role \(RAM role 1\) in Workload Account A1 that can be used for cross-account authorization, grant required permissions to RAM role 1, and set A0 as the trusted Alibaba Cloud account.
6.  Use the Workload Account A2 to log on to the RAM console, create a RAM role \(RAM role 2\) in Workload Account A2 that can be used for cross-account authorization, grant required permissions to RAM role 2, and set A0 as the trusted Alibaba Cloud account.
7.  Grant the RAM users under the Identity Account A0 the permission to assume RAM role 1 or RAM role 2.

