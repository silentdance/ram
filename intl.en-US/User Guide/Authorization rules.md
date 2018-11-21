# Authorization rules {#concept_xgf_ldk_xdb .concept}

To help you better understand the authorization policy, this document describes the authorization model and rules.

## Basic model {#section_vgn_mdk_xdb .section}

When a user attempts to access a resource by using different identities, RAM evaluates the access with corresponding logic.

|Access From|The Access is Permitted Only When|
|:----------|:--------------------------------|
|A primary account|The user is the resource owner. **Exception**: A few cloud products, such as SLS, directly support cross-account ACL authorization. If the ACL authorization check is passed, access is permitted.|
|A RAM user identity| -   The primary account to which the RAM user belongs has the access permission for the resource.
-   The primary account has attached an explicit Allow authorization policy to the RAM user.

 |
|A RAM role identity| -   The primary account to which the RAM role belongs has the access permission for the resource.
-   The primary account has attached an explicit Allow authorization policy to the RAM role.
-   The role’s STS-Token is explicitly authorized.

 |

## Authorization policy check logic for a RAM user identity {#section_ahn_mdk_xdb .section}

By default, RAM users do not have resource access permissions unless they have been explicitly authorized by the primary account \(that is, they have been attached with an authorization policy\). Authorization policy statements support two types of authorization: Allow and Deny. When multiple authorization policy statements grant Allow and Deny permissions for the same resource, **Deny** takes priority.

The following figure details the authorization policy check logic.

![](images/3628_en-US.png "Authorization policy check logic")

When a RAM user accesses resources, the authorization policy check logic is as follows:

1.  The system checks whether a RAM user identity is authorized according to the authorization policy attached with the RAM user identity.
    -   If the result is Deny, access is denied.
    -   Otherwise, the system proceeds with the next stage.
2.  The system checks whether the primary account of the RAM user has access permission for the resource.
    -   If the account is the resource owner, access is permitted.
    -   If the account is not the resource owner, the system checks whether the resource supports cross-account ACL authorization.
        -   If yes, access is permitted.
        -   Otherwise, access is denied.

## Authorization policy check logic for a RAM role identity {#section_ghn_mdk_xdb .section}

If a user attempts to access a resource by using a RAM role \(that is, using an STS-Token\), the authorization policy check logic is as follows:

1.  If the current STS-Token specifies an authorization policy \(the authorization policy parameters entered when the AssumeRole API is called\), the authorization policy check logic described in the preceding section is implemented.

    -   If the result is Deny, access is denied.
    -   Otherwise, the system proceeds with the next stage.
    If the STS-Token does not specify an authorization policy, the system automatically goes to the next stage.

2.  The system checks whether the RAM role identity is authorized according to the authorization policy attached with the RAM role identity.
    -   If the result is Deny, access is denied.
    -   Otherwise, the system proceeds with the next stage.
3.  The system checks whether the primary account of the RAM user has access permission for the resource.
    -   If the account is the resource owner, access is permitted.
    -   If the account is not the resource owner, the system checks whether the resource supports cross-account ACL authorization.
        -   If yes, access is permitted.
        -   Otherwise, access is denied.

