# OAuth application overview {#concept_ypk_fkc_mfb .concept}

This topic describes commonly used concepts of OAuth 2.0. You can use the OAuth 2.0 protocol with Alibaba Cloud Resource Access Management \(RAM\) to authenticate users so that they can access specific Alibaba Cloud resources. You can also authorize applications to access these resources on behalf of users.

## Commonly used concepts {#section_gpx_3nq_nfb .section}

The following table describes the commonly used concepts of OAuth 2.0.

|Concept|Description|
|:------|:----------|
|User|The user is an Alibaba Cloud account owner or a RAM user. The user must log on to Alibaba Cloud before authorizing an application to access specific Alibaba Cloud resources.|
|Alibaba Cloud OAuth 2.0 service|The Alibaba Cloud OAuth 2.0 service is used to authenticate users and generate tokens for applications to access specific Alibaba Cloud resources on behalf of users.|
|Application|The application that can access Alibaba Cloud resources after it is authorized by a user and obtains tokens of the user.|
|Application type|The type of applications supported by the OAuth 2.0 service. Currently, the following types are supported: -   **WebApp**: This type interacts with a web browser.
-   **NativeApp**: This type runs locally on an operating system, such as a desktop operating system or a mobile operating system.

 |
|Token|The token that is issued by OAuth 2.0 to an application. The following types of tokens are used: -   ID token: This type only contains user identity information, and therefore cannot be used to access Alibaba Cloud resources.
-   Access token: This type contains both user identity information and the OAuth scopes of an application. It can be used to access Alibaba Cloud resources within specified OAuth scopes.
-   Refresh token: This type can be used to obtain new access tokens.

 |
|OAuth scopes|The scopes within which an application is allowed to access Alibaba Cloud resources on behalf of a user. The supported scopes are: -   openid: Obtains basic user information.

**Note:** The openid scope is automatically added by the OpenID Connect \(OIDC\) protocol to applications. This scope cannot be deleted.

-   aliuid: Indicates the user ID issued by Alibaba Cloud.
-   profile: Indicates the personal information about a user, such as the username.
-   /acs/ccc: Indicates the Alibaba Cloud Call Center API.
-   /acs/alidns: Indicates the Alibaba Cloud DNS API.

 **Note:** The openid, aliuid, and profile scopes are related to ID tokens, and the other scopes are related to access tokens.

 |
|Alibaba Cloud APIs|The API action that an application can call to access Alibaba Cloud resources.|

