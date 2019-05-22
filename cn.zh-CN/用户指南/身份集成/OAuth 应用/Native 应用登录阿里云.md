# Native 应用登录阿里云 {#concept_dzq_mkc_mfb .concept}

本文介绍桌面和移动端的 Native 应用如何通过 OAuth 2.0 扮演登录用户访问阿里云 API。

## 前提条件 {#section_01 .section}

Native 应用扮演登录用户访问阿里云首先需要创建应用，为应用提供恰当的名称、OAuth 范围、回调地址等关键信息。详情请参考：[创建应用](cn.zh-CN/用户指南/身份集成/OAuth 应用/管理 OAuth 应用/创建应用.md#)。由于 Native 应用运行在非可信环境，无法有效保护应用密钥，因此 Native 应用不使用应用密钥。

**说明：** 应用创建成功之后，可以在云账号内直接扮演用户。

## 基本流程 {#section_02 .section}

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23751/155852797814376_zh-CN.png)

1.  用户通过浏览器登录 Native 应用。
2.  Native 应用重定向到阿里云 OAuth 2.0 服务并将 URL 返回给浏览器。

    **说明：** 如果用户还未登录，则会进一步重定向到阿里云登录服务。

3.  用户通过浏览器登录阿里云 OAuth 2.0 服务并申请授权码。
4.  阿里云 OAuth 2.0 服务重定向到 Native 应用并返回授权码。
5.  Native 应用使用授权码向阿里云 OAuth 2.0 服务申请代表用户身份的令牌。
    -   如何获取访问令牌，请参考：[获取访问令牌](#section_03)。
    -   如何获取新的访问令牌，请参考：[获取新的访问令牌](#section_04)。
    -   如何撤销刷新令牌，请参考：[撤销刷新令牌](#section_05)。
6.  阿里云 OAuth 2.0 服务向 Native 应用返回令牌。
7.  Native 应用通过获取的令牌向阿里云发起访问 API 的请求。

    **说明：** 由于令牌可以代表用户身份，因此应用可以访问当前用户的资源。


## Proof Key 机制的原理 {#section_5xd_yii_rz1 .section}

Native 应用支持 [Proof Key 机制](https://tools.ietf.org/html/rfc7636)，用于每次获取授权码以及用授权码换取访问令牌。

**说明：** 这一机制可以减轻针对授权码截获的攻击。

1.  Native 应用应用生成：`Code_Verifier`，并保存好这个随机字符串。

    **说明：** `code_verifier`是一个高熵值的随机字符串，其取值为：\[A-Z\] / \[a-z\] / \[0-9\] / "-" / "." / "\_" / "~"，长度限制为：43 ~ 128 个字符。

2.  应用根据`transform`的方式选择生成`code_challenge`。应用在申请授权码的同时提交：`code_challenge`以及生成`code_challenge`的方式。

    ``` {#codeblock_zvk_se9_xu6}
    code_challenge = transform(code_verifier, [Plain|S256])
    ```

    |方式|取值|
    |:-|:-|
    |`plain`|如果`transform`的方式选择为：`plain`，那么`code_challenge`与`code_verifier`的值相同。|
    |`S256`|如果`transform`的方式选择为：`S256`，那么`code_challenge`等于`code verifier`的 SHA256 哈希值。     ``` {#codeblock_3fw_o9c_mfl}
code_challenge=BASE64URL-Encode(SHA256(ASCII(code_verifier)))
    ```

 **说明：** 哈希算法的输入为：`code_verifier` 的 ASCII 编码串，哈希算法的输出字符串需要进行 BASE64-URL 编码。

 |

    `code_challenge`选择方式计算示例：

    如果应用采用方式为 S256，生成`code_verifier`的值为：dBjftJeZ4CVP-mB92K27uhbUJU1p1r\_wW1gFWFOEjXk，那么`code_challenge`为：E9Melhoa2OwvFrEMTJguCHaoeK1t8URWbuGJSstw-cM。

3.  应用获取授权码后，在使用授权码换取访问令牌时，服务端通过计算判断是否颁发令牌。

    授权码需包括`code_verifier`，服务端按照应用选择的`transform`方式对`code_verifier`进行计算，将结果与`code_challenge`进行对比，如果一致则颁发访问令牌。


## 获取访问令牌 {#section_03 .section}

1.  Native 应用通过浏览器将用户重定向到阿里云 OAuth 2.0 服务从而获取授权码。

    授权码的请求地址：`https://signin.aliyun.com/oauth2/v1/auth`。

    |参数名称|是否必选|描述|
    |:---|:---|:-|
    |client\_id|是|应用的身份 ID。|
    |redirect\_uri|是|创建应用的重定向 URI 之一。|
    |response\_type|是|返回类型。根据 OAuth 2.0 协议，目前支持设置此参数的取值为：code。|
    |scope|否|空格分隔的 OAuth 范围列表。如不指定此参数取值，则默认为应用的全部 OAuth 范围。|
    |state|否|应用通过 state 参数实现多种目的，例如：状态保持、作为 nonce 使用从而减少 CSRF 威胁等。state 如果设置为任意字符串，阿里云 OAuth 2.0 服务会将请求中的 state 参数以及取值原样放到返回参数中以供后续使用。|
    |code\_challenge\_method|否|如果不指定此参数，则默认取值为：plain。|
    |code\_challenge|否|根据客户端指定的 code\_challenge\_method，对随机生成的 code\_verifier 进行转换和编码，转换的结果作为 code\_challenge 参数的值在授权码请求中使用。 **说明：** 如果不指定此参数，则无法使用 Proof Key 机制，在使用授权码换取令牌时也不需要指定相应的 code\_verifier，若授权码被截获可以直接被用于换取访问令牌。

 |

    请求示例

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

    返回示例

    ``` {#codeblock_9m5_37d_1kl}
    GET HTTP/1.1 302 Found
    Location: meeting://authorize/?code=ABAFDGDFXYZW888&state=123456****                     
    ```

2.  Native 应用使用授权码向阿里云 OAuth 2.0 服务申请代表用户身份的令牌。

    换取访问令牌的请求地址：`https://oauth.aliyun.com/v1/token`。

    |参数名称|是否必选|描述|
    |:---|:---|:-|
    |code|是|初始请求中获取的授权码。|
    |client\_id|是|应用的身份 ID。|
    |redirect\_uri|是|初始请求中设置的参数。|
    |grant\_type|是|根据 OAuth 2.0 协议， 取值为：authorization\_code。|
    |code\_verifier|否|初始请求中生成的 code verifier，对应于授权码请求中的 code\_challenge 参数。|

    请求示例

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

    |参数名称|描述|
    |:---|:-|
    |access\_token|访问令牌。访问令牌可以代表用户身份，应用使用此访问令牌来访问阿里云 API。应用不需要理解访问令牌的含义，直接使用即可。|
    |expires\_in|访问令牌的剩余有效时间，单位为秒。|
    |token\_type|访问令牌的类型。取值为：Bearer。|
    |id\_token|身份令牌。id\_token 为 OAuth 签名的 JWT（JSON Web Token）。如果初始请求的 scope 参数包含了 openid，则返回身份令牌。|
    |refresh\_token|刷新令牌。此参数可以直接使用，Native 应用不需要指定访问令牌的值，可以直接获得刷新令牌。|

    返回示例

    ``` {#codeblock_lnv_839_46l}
    {
      "access_token": "eyJraWQiOiJrMTIzNCIsImVuYyI6****",
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

请求示例

``` {#codeblock_2vb_nfc_ern}
POST /v1/token HTTP/1.1 
Host: oauth.aliyun.com 
Content-Type: application/x-www-form-urlencoded
refresh_token=Ccx63VVeTn2dxV7ovXXfLtAqLLERAH****
client_id=98989****
grant_type=refresh_token
```

|参数名称|描述|
|:---|:-|
|access\_token|新的访问令牌。应用使用新的访问令牌来访问阿里云 API。|
|expires\_in|访问令牌的剩余有效时间，单位为秒。|
|token\_type|访问令牌的类型。取值为：Bearer。|

返回示例

``` {#codeblock_shj_6zc_siw}
{
  "access_token": "eyJraWQiOiJrMTIzNCIsImVuYyI6****",
  "token_type": "Bearer",
  "expires_in": 3600,
}                      
```

**说明：** 本次请求的返回值与用授权码换取访问令牌的返回值一致，但不包含 refresh\_token 和 id\_token。

## 撤销刷新令牌 {#section_05 .section}

Native 应用获取了刷新令牌后，在用户退出登录应用时或用户将自己的账号从应用中移除时，必须撤销刷新令牌。

撤销刷新令牌的请求地址：`https://oauth.aliyun.com/v1/revoke`。

|参数名称|是否必选|描述|
|:---|:---|:-|
|token|是|需要撤销的刷新令牌。|
|client\_id|是|应用的身份 ID。|

