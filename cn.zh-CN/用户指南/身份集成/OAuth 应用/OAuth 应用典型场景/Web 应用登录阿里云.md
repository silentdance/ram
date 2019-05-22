# Web 应用登录阿里云 {#concept_amf_lkc_mfb .concept}

本文介绍 Web 应用如何通过 OAuth 2.0 扮演登录用户访问阿里云 API。

## 前提条件 {#section_01 .section}

Web 应用扮演登录用户访问阿里云首先需要创建应用，为应用提供恰当的名称、OAuth 范围、回调地址等关键信息，并为应用生成应用密钥。详情请参考：[创建应用](cn.zh-CN/用户指南/身份集成/OAuth 应用/管理 OAuth 应用/创建应用.md#)。

**说明：** 应用创建成功之后，可以在云账号内直接扮演用户。如果要扮演其他云账号的用户，需要获得其他云账号的授权。

## 基本流程 {#section_02 .section}

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23750/155852701114349_zh-CN.png)

1.  用户通过浏览器登录 Web 应用。
2.  Web 应用重定向到阿里云 OAuth 2.0 服务并将 URL 返回给浏览器。

    **说明：** 如果用户还未登录，则会进一步重定向到阿里云登录服务。

3.  用户通过浏览器登录阿里云 OAuth 2.0 服务并申请授权码。
4.  阿里云 OAuth 2.0 服务重定向到 Web 应用并返回授权码。
5.  Web 应用使用授权码向阿里云 OAuth 2.0 服务申请代表用户身份的令牌。
    -   如何获取访问令牌，请参考：[获取访问令牌](#section_03)。
    -   如何获取新的访问令牌，请参考：[获取新的访问令牌](#section_04)。
    -   如何撤销刷新令牌，请参考：[撤销刷新令牌](#section_05)。
6.  阿里云 OAuth 2.0 服务向 Web 应用返回令牌。
7.  Web 应用通过获取的令牌向阿里云发起访问 API 的请求。

    **说明：** 由于令牌可以代表用户身份，因此应用可以访问当前用户的资源。


## 获取访问令牌 {#section_03 .section}

1.  Web 应用通过浏览器将用户重定向到阿里云 OAuth 2.0 服务从而获取授权码。

    授权码的请求地址：`https://signin.aliyun.com/oauth2/v1/auth`。

    |参数名称|是否必选|描述|
    |:---|:---|:-|
    |client\_id|是|应用的身份 ID。|
    |redirect\_uri|是|创建应用的重定向 URI 之一。|
    |response\_type|是|返回类型。根据 OAuth 2.0 协议，目前支持设置此参数的取值为：code。|
    |scope|否|空格分隔的 OAuth 范围列表。如不指定此参数取值，则默认为应用的全部 OAuth 范围。|
    |access\_type|否|应用的访问类型。取值分为两种类型：     -   online：应用不需要离线刷新访问令牌。
    -   offline：针对离线访问类型的请求，会发放刷新令牌，应用可以根据需求持续刷新访问令牌。
 默认取值为：online。

 |
    |state|否|应用通过 state 参数实现多种目的，例如：状态保持、作为 nonce 使用从而减少 CSRF 威胁等。state 如果设置为任意字符串，阿里云 OAuth2.0 服务会将请求中的 state 参数及取值原样放到返回参数中以供后续使用。|

    请求示例

    ``` {#codeblock_m80_i3h_ztc}
    https://signin.aliyun.com/oauth2/v1/auth?
    client_id=123****
    redirect_uri=https%3A%2F%2Fyourwebapp.com%2Fauthcallback%2F&
    response_type=code&
    scope=openid%20%2Facs%2Fccc&
    access_type=offline&
    state=123456****
    ```

    返回示例

    ``` {#codeblock_3s5_4ex_hb9}
    GET HTTP/1.1 302 Found
    Location: https://yourwebapp.com/authcallback/?code=ABAFDGDFXYZW888&state=123456****
    ```

2.  Web 应用使用授权码向阿里云 OAuth 2.0 服务申请代表用户身份的令牌。

    换取访问令牌的请求地址：`https://oauth.aliyun.com/v1/token`。

    |参数名称|是否必选|描述|
    |:---|:---|:-|
    |code|是|初始请求中获取的授权码。|
    |client\_id|是|应用的身份 ID。|
    |redirect\_uri|是|初始请求中设置的参数。|
    |grant\_type|是|根据 OAuth 2.0 协议， 取值为：authorization\_code。|
    |client\_secret|否|应用的密钥，用作换取访问令牌时鉴定应用身份的密码。|

    请求示例

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

    |参数名称|描述|
    |:---|:-|
    |access\_token|访问令牌。访问令牌可以代表用户身份，应用使用此访问令牌来访问阿里云 API。应用不需要理解访问令牌的含义，直接使用即可。|
    |expires\_in|访问令牌的剩余有效时间，单位为秒。|
    |token\_type|访问令牌的类型。取值为：Bearer。|
    |id\_token|身份令牌。身份令牌为 OAuth 签名的 JWT（JSON Web Token）。如果初始请求的 scope 参数包含了 openid，则返回身份令牌。|
    |refresh\_token|刷新令牌。如果初始请求时应用的访问类型为：offline，则返回刷新令牌。|

    返回示例

    ``` {#codeblock_bzj_675_t4m}
    {
      "access_token": "eyJraWQiOiJrMTIzNCIsImVu****",
      "token_type": "Bearer",
      "expires_in": 3600,
      "refresh_token": "Ccx63VVeTn2dxV7ovXXfLtAqLLERA****",
      "id_token": "eyJhbGciOiJIUzI1****"
    }
    ```


## 获取新的访问令牌 {#section_04 .section}

换取访问令牌的请求地址：`https://oauth.aliyun.com/v1/token`。

|参数名称|是否必选|描述|
|:---|:---|:-|
|refresh\_token|是|用授权码换取访问令牌时获得的刷新令牌。|
|client\_id|是|应用的身份 ID。|
|grant\_type|是|根据 OAuth 2.0 协议， 取值为：refresh\_token。|
|client\_secret|否|应用的密钥，用作换取访问令牌时鉴定应用身份的密码。|

请求示例

``` {#codeblock_iwx_85n_p9t}
POST /v1/token HTTP/1.1
Host: oauth.aliyun.com
Content-Type: application/x-www-form-urlencoded
refresh_token=Ccx63VVeTn2dxV7ovXXfLtAqLLERAH1Bc&
client_id=123****
client_secret=`your_client_secret`&
grant_type=refresh_token
```

|参数名称|描述|
|:---|:-|
|access\_token|新的访问令牌。应用可以使用新的访问令牌来访问阿里云 API。|
|expires\_in|访问令牌的剩余有效时间，单位为秒。|
|token\_type|访问令牌的类型。取值为：Bearer。|

返回示例

``` {#codeblock_kx6_pzi_pm9}
{
  "access_token": "eyJraWQiOiJrMTIzNCIsImVu****",
  "token_type": "Bearer",
  "expires_in": 3600,
}
```

**说明：** 本次请求的返回值与用授权码换取访问令牌的返回值一致，但不包含 refresh\_token 和 id\_token。

## 撤销刷新令牌 {#section_05 .section}

如果应用获取了刷新令牌，在特定的场景下也需要撤销刷新令牌，例如：用户退出登录应用或用户将自己的账号从应用中移除等。

撤销刷新令牌的请求地址：`https://oauth.aliyun.com/v1/revoke`。

|参数名称|是否必选|描述|
|:---|:---|:-|
|token|是|需要撤销的刷新令牌。|
|client\_id|是|应用的身份 ID。|
|client\_secret|否|应用的密钥。|

