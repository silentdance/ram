# Access to Alibaba Cloud APIs by using a web application {#concept_amf_lkc_mfb .concept}

This topic describes how Alibaba Cloud APIs can be accessed by using a web application through OAuth 2.0.

## Prerequisites {#section_01 .section}

-   A web application is created. For more information, see [Create an application](reseller.en-US/User Guide/OAuth management/Manage an OAuth application/Create an application.md#).
-   The name, callback URL, and OAuth scopes are specified for the web application.
-   An application secret is created for the web application.

**Note:** After you create a web application, the application can access Alibaba Cloud resources under your Alibaba Cloud account. The application must obtain corresponding authorization before accessing Alibaba Cloud resources on behalf of other Alibaba Cloud accounts.

## Overall process {#section_02 .section}

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23750/155920075514349_en-US.png)

1.  A user logs on to a web application through a browser.
2.  The web application redirects to the Alibaba Cloud OAuth 2.0 service and sends the preceding URL to the user.

    **Note:** If the user is not logged on to Alibaba Cloud, the web application redirects to the Alibaba Cloud logon page first.

3.  The user logs on to the Alibaba Cloud OAuth 2.0 service through the browser and requests an authorization code.
4.  The Alibaba Cloud OAuth 2.0 service returns an authorization code to the web application.
5.  The web application requests the tokens that are granted to the user from the Alibaba Cloud OAuth 2.0 service. For more information, see the sections [Obtain an access token](#section_03), [Obtain a new access token](#section_04), and [Revoke a refresh token](#section_05).
6.  The Alibaba Cloud OAuth 2.0 service sends the requested tokens to the web application.
7.  The web application uses the tokens to send an API access request to Alibaba Cloud.

    **Note:** The tokens contain the identity information about the user. Therefore, the web application can use these tokens to access the user resources on behalf of the user.


## Obtain an access token {#section_03 .section}

1.  The web application redirects the user to the Alibaba Cloud OAuth 2.0 service to obtain an authorization code.

    The authorization code endpoint is `https://signin.aliyun.com/oauth2/v1/auth`.

    |Parameter|Required?|Description|
    |:--------|:--------|:----------|
    |client\_id|Yes|The web application ID.|
    |redirect\_uri|Yes|The Uniform Resource Identifier \(URI\) of the web application.|
    |response\_type|Yes|The response type. Value: code

 |
    |scope|No|The space-separated list of OAuth scopes. If this parameter is left unspecified, all scopes are authorized to the web application by default.|
    |access\_type|No|The access method of the web application. Valid values:     -   online: The web application does not need to refresh the access token offline.
    -   offline: The web application can obtain a refresh token and refresh its access token for many times as needed.
 Default value: online

 |
    |state|No|A value that is used as a nonce to prevent cross-site request forgery \(CSRF\) attacks. If you set this parameter to a string of any content, the Alibaba Cloud OAuth 2.0 service returns the value of state in the token response for subsequent use.|

    Request example

    ``` {#codeblock_m80_i3h_ztc}
    https://signin.aliyun.com/oauth2/v1/auth?
    client_id=123****
    redirect_uri=https%3A%2F%2Fyourwebapp.com%2Fauthcallback%2F&
    response_type=code&
    scope=openid%20%2Facs%2Fccc&
    access_type=offline&
    state=123456****
    ```

    Response example

    ``` {#codeblock_3s5_4ex_hb9}
    GET HTTP/1.1 302 Found
    Location: https://yourwebapp.com/authcallback/?code=ABAFDGDFXYZW888&state=123456****
    ```

2.  The web application uses the authorization code to request an access token of the user from the Alibaba Cloud OAuth 2.0 service.

    The access token endpoint is `https://oauth.aliyun.com/v1/token`.

    |Parameter|Required?|Description|
    |:--------|:--------|:----------|
    |code|Yes|The authorization code requested by the web application.|
    |client\_id|Yes|The web application ID.|
    |redirect\_uri|Yes|The URI of the web application.|
    |grant\_type|Yes|The value of this parameter must be set to authorization\_code.|
    |client\_secret|No|The application secret that is used to authenticate the web application when the web application requests an access token.|

    Request example

    ``` {#codeblock_m24_flw_jni}
    POST /v1/token HTTP/1.1
    Host: oauth.aliyun.com
    Content-Type: application/x-www-form-urlencoded
    code=ABAFDGDFXYZW888&
    client_id=123****
    client_secret=`your_client_secret`&
    redirect_uri=https://yourwebapp.com/authcallback/&
    grant_type=authorization_code
    ```

    |Parameter|Description|
    |:--------|:----------|
    |access\_token|The requested access token. The web application can use this token to access Alibaba Cloud APIs.|
    |expires\_in|The validity period of the access token. Unit: second

 |
    |token\_type|The access token type. Value: Bearer

 |
    |id\_token|The ID token. It is a JSON Web Token \(JWT\). This parameter is returned if the openid scope was requested.|
    |refresh\_token|The refresh token. This parameter is returned if the offline access method was requested.|

    Response example

    ``` {#codeblock_bzj_675_t4m}
    {
      "access_token": "eyJraWQiOiJrMTIzNCIsImVu****",
      "token_type": "Bearer",
      "expires_in": 3600,
      "refresh_token": "Ccx63VVeTn2dxV7ovXXfLtAqLLERA****",
      "id_token": "eyJhbGciOiJIUzI1****"
    }
    ```


## Obtain a new access token {#section_04 .section}

The access token endpoint is `https://oauth.aliyun.com/v1/token`.

|Parameter|Required?|Description|
|:--------|:--------|:----------|
|refresh\_token|Yes|The refresh token that is obtained by using the authorization code.|
|client\_id|Yes|The web application ID.|
|grant\_type|Yes|The value of this parameter must be set to refresh\_token.|
|client\_secret|No|The application secret that is used to authenticate the web application when the web application requests an access token.|

Request example

``` {#codeblock_iwx_85n_p9t}
POST /v1/token HTTP/1.1
Host: oauth.aliyun.com
Content-Type: application/x-www-form-urlencoded
refresh_token=Ccx63VVeTn2dxV7ovXXfLtAqLLERAH1Bc&
client_id=123****
client_secret=`your_client_secret`&
grant_type=refresh_token
```

|Parameter|Description|
|:--------|:----------|
|access\_token|The new access token. The web application can use this token to access Alibaba Cloud APIs.|
|expires\_in|The validity period of the access token. Unit: second

 |
|token\_type|The type of the access token. Value: Bearer

 |

Response example

``` {#codeblock_kx6_pzi_pm9}
{
  "access_token": "eyJraWQiOiJrMTIzNCIsImVu****",
  "token_type": "Bearer",
  "expires_in": 3600,
}
```

**Note:** The values in this response are the same as those in the preceding response example. This response does not contain the refresh\_token and id\_token parameters.

## Revoke a refresh token {#section_05 .section}

When a user logs out of an application or removes its account from an application, you must revoke the refresh token of the application.

The endpoint for revoking a refresh token is `https://oauth.aliyun.com/v1/revoke`.

|Parameter|Required?|Description|
|:--------|:--------|:----------|
|token|Yes|The refresh token to be revoked.|
|client\_id|Yes|The web application ID.|
|client\_secret|No|The web application secret.|

