# Access to Alibaba Cloud APIs by using a native application {#concept_dzq_mkc_mfb .concept}

This topic describes how Alibaba Cloud APIs can be accessed by using a native application, such as a desktop application or a mobile application, through OAuth 2.0.

## Prerequisites {#section_01 .section}

-   A native application is created. For more information, see [Create an application](intl.en-US/User Guide/OAuth management/Manage an OAuth application/Create an application.md#).
-   The name, callback URL, and OAuth scopes are specified for the native application.

**Note:** Native applications run on insecure hosts and therefore do not use application secrets. After you create a native application, the application can access Alibaba Cloud resources under your Alibaba Cloud account.

## Overall process {#section_02 .section}

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23751/155920093014376_en-US.png)

1.  A user logs on to a native application through a browser.
2.  The native application redirects to the Alibaba Cloud OAuth 2.0 service and sends the preceding URL to the user.

    **Note:** If the user is not logged on to Alibaba Cloud, the web application redirects to the Alibaba Cloud logon page first.

3.  The user logs on to the Alibaba Cloud OAuth 2.0 service through the browser and requests an authorization code.
4.  The Alibaba Cloud OAuth 2.0 service returns an authorization code to the native application.
5.  The native application requests the tokens that are granted to the user from the Alibaba Cloud OAuth 2.0 service. For more information, see the sections [Obtain an access token](#section_03), [Obtain a new access token](#section_04), and [Revoke a refresh token](#section_05).
6.  The Alibaba Cloud OAuth 2.0 service sends the requested tokens to the native application.
7.  The native application uses the tokens to send an API access request to Alibaba Cloud.

    **Note:** The tokens contain the identity information about the user. Therefore, the native application can use these tokens to access the user resources on behalf of the user.


## The PKCE specification {#section_5xd_yii_rz1 .section}

Native applications can use the [Proof Key for Code Exchange \(PKCE\)](https://tools.ietf.org/html/rfc7636) specification to obtain an authorization code and an access token.

**Note:** The PKCE specification can mitigate against the authorization code interception.

1.  A native application creates and records a string named `code_verifier`.

    **Note:** The `code_verifier` is a high-entropy cryptographic string. It must be 43 to 128 characters in length, and can contain letters, numbers, hyphens \(-\), periods \(.\), underscores \(\_\), and tildes \(~\).

2.  The native application uses `transform` to create `code_challenge`, which is a transformed version of `code_verifier`. The `code_challenge` and the transformation method are sent in the OAuth 2.0 authorization request.

    ``` {#codeblock_zvk_se9_xu6}
    code_challenge = transform(code_verifier, [Plain|S256])
    ```

    |Transformation method|Value|
    |:--------------------|:----|
    |`plain`|If the transformation method is `plain`, the value of `code_challenge` equals to the value of `code_verifier`.|
    |`S256`|If the transformation method is `S256`, the value of `code_challenge` equals to the SHA-256 hash value of `code verifier`.     ``` {#codeblock_3fw_o9c_mfl}
code_challenge=BASE64URL-Encode(SHA256(ASCII(code_verifier)))
    ```

 **Note:** The input of the hash algorithm is an ASCII-encoded string of `code_verifier`. The output of the hash algorithm must be encoded by using base64url.

 |

    The following is a calculation example of `code_challenge`:

    If the `S256` transformation method is used, the value of `code_verifier` is dBjftJeZ4CVP-mB92K27uhbUJU1p1r\_wW1gFWFOEjXk, and the value of `code_challenge` is `E9Melhoa2OwvFrEMTJguCHaoeK1t8URWbuGJSstw-cM`.

3.  When the application uses the authorization code to request an access token, the server determines whether to issue a token by calculating `code_challenge` transformed from `code_verifier`.

    The authorization code must contain `code_verifier`. The server compares `code_challenge` with the previously associated `code_verifier`. If the values of `code_verifier` and `code_challenge` are equal, the server issues the requested token.


## Obtain an access token {#section_03 .section}

1.  The native application redirects the user to the Alibaba Cloud OAuth 2.0 service to obtain an authorization code.

    The authorization code endpoint is `https://signin.aliyun.com/oauth2/v1/auth`.

    |Parameter|Required?|Description|
    |:--------|:--------|:----------|
    |client\_id|Yes|The native application ID.|
    |redirect\_uri|Yes|The Uniform Resource Identifier \(URI\) of the native application.|
    |response\_type|Yes|The response type. Value: code

 |
    |scope|No|The space-separated list of OAuth scopes. If this parameter is left unspecified, all scopes are authorized to the native application by default.|
    |state|No|A value that is used as a nonce to prevent cross-site request forgery \(CSRF\) attacks. If you set this parameter to a string of any content, the Alibaba Cloud OAuth 2.0 service returns the value of state in the token response for subsequent use.|
    |code\_challenge\_method|No|The transformation method. If this parameter is left unspecified, the default method plain is used.|
    |code\_challenge|No|This parameter is used to secure authorization code grants through PKCE from the native application. This parameter is generated by transcoding and encoding the code\_verifier parameter according to the value of code\_challenge\_method. **Note:** If this parameter is left unspecified, the PKCE specification cannot be used, and you do not need to specify the code\_verifier parameter when a native application uses an authorization code to request an access token. If another application intercepts the authorization code, they can use this code to exchange for an access token.

 |

    Request example

    ``` {#codeblock_f5x_f4r_nwh}
    https://signin.aliyun.com/oauth2/v1/authorize?
    client_id=98989****
    redirect_uri=meeting%3A%2F%2Fauthorize%2F
    &response_type=code
    &scope=openid%20%2Fworksuite%2Fuseraccess
    &state=123456****
    &code_challenge=E9Melhoa2OwvFrEMTJguCHaoeK1t8URWbuGJSst****
    &code_challenge_method=S256
    ```

    Response example

    ``` {#codeblock_9m5_37d_1kl}
    GET HTTP/1.1 302 Found
    Location: meeting://authorize/?code=ABAFDGDFXYZW888&state=123456****                     
    ```

2.  The native application uses the authorization code to request an access token of the user from the Alibaba Cloud OAuth 2.0 service.

    The access token endpoint is `https://oauth.aliyun.com/v1/token`.

    |Parameter|Required?|Description|
    |:--------|:--------|:----------|
    |code|Yes|The authorization code requested by the native application.|
    |client\_id|Yes|The native application ID.|
    |redirect\_uri|Yes|The URI of the native application.|
    |grant\_type|Yes|The value of this parameter must be set to authorization\_code.|
    |code\_verifier|No|The parameter that is created in the initial request. This parameter corresponds to the code\_challenge parameter in the authorization code request.|

    Request example

    ``` {#codeblock_50d_zd0_tqx}
    POST /v1/token HTTP/1.1 
    Host: oauth.aliyun.com 
    Content-Type: application/x-www-form-urlencoded
    code=ABAFDGDFXYZW888&
    client_id=98989****
    redirect_uri=meeting://authorize/&
    grant_type=authorization_code&
    code_verifier=dBjftJeZ4CVP-mB92K27uhbUJU1p1r_wW1gFWFOEjXk                    
    ```

    |Parameter|Description|
    |:--------|:----------|
    |access\_token|The requested access token. The native application can use this token to access Alibaba Cloud APIs.|
    |expires\_in|The validity period of the access token. Unit: second

 |
    |token\_type|The access token type. Value: Bearer

 |
    |id\_token|The ID token. It is a JSON Web Token \(JWT\). This parameter is returned if the openid scope was requested.|
    |refresh\_token|The refresh token. You do not need to specify this parameter for the native application. The native application can obtain a refresh token directly.|

    Response example

    ``` {#codeblock_lnv_839_46l}
    {
      "access_token": "eyJraWQiOiJrMTIzNCIsImVuYyI6****",
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
|client\_id|Yes|The native application ID.|
|grant\_type|Yes|The value of this parameter must be set to refresh\_token.|

Request example

``` {#codeblock_2vb_nfc_ern}
POST /v1/token HTTP/1.1 
Host: oauth.aliyun.com 
Content-Type: application/x-www-form-urlencoded
refresh_token=Ccx63VVeTn2dxV7ovXXfLtAqLLERAH****
client_id=98989****
grant_type=refresh_token
```

|Parameter|Description|
|:--------|:----------|
|access\_token|The new access token. The native application can use this token to access Alibaba Cloud APIs.|
|expires\_in|The validity period of the access token. Unit: second

 |
|token\_type|The type of the access token. Value: Bearer

 |

Response example

``` {#codeblock_shj_6zc_siw}
{
  "access_token": "eyJraWQiOiJrMTIzNCIsImVuYyI6****",
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
|client\_id|Yes|The native application ID.|

