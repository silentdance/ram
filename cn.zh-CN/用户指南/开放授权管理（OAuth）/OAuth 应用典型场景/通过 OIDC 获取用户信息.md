# 通过 OIDC 获取用户信息 {#concept_dr1_4kc_mfb .concept}

OIDC（OpenID Connect）是建立在 OAuth 2.0 基础上的一个认证协议，本文为您介绍应用如何使用 OIDC 获取阿里云登录用户的信息。

## 前提条件 {#section_xho_ig1_o4a .section}

应用获取用户登录信息首先需要创建应用，为应用提供恰当的名称、OAuth 范围、回调地址等关键信息，并为应用生成应用密钥。详情请参考：[创建应用](cn.zh-CN/用户指南/开放授权管理（OAuth）/管理 OAuth 应用/创建应用.md#)。

## OIDC 基本概念 {#section_ob9_yh9_ibw .section}

 身份令牌
 :   OIDC 可以给应用下发代表登录用户的身份令牌。身份令牌用于获取姓名，登录名等用户信息，不能用于访问阿里云服务。

  OIDC discovery endpoint
 :   OIDC 协议包含了不同的 endpoint 用于不同的目的，discovery endpoint 中包含 OIDC 协议所需要的所有配置信息，方便开发者使用。

 **说明：** Discovery endpoint 是通过 JSON 文档来提供一系列键值，其中包含主要的提供者信息，例如：协议支持的响应类型，令牌颁发者的取值，身份令牌签名密钥的地址，签名算法等。

阿里云作为 OIDC 服务提供者，提供了一个 discovery endpoint：`https://oauth.aliyun.com/.well-known/openid-configuration`来简化配置流程。

Discovery endpoint 包含的内容示例如下：

``` {#codeblock_trw_h2j_56k}
{
  "code_challenge_methods_supported": [
    "plain",
    "S256"
  ],
  "subject_types_supported": [
    "public"
  ],
  "response_types_supported": [
    "code"
  ],
  "issuer": "https://oauth.aliyun.com",
  "jwks_uri": "https://oauth.aliyun.com/v1/keys",
  "revocation_endpoint": "https://oauth.aliyun.com/v1/revoke",
  "token_endpoint": "https://oauth.aliyun.com/v1/token",
  "id_token_signing_alg_values_supported": [
    "RS256"
  ],
  "scopes_supported": [
    "openid",
    "aliuid",
    "profile"
  ],
  "authorization_endpoint": "https://signin.aliyun.com/oauth2/v1/auth"
}
```

## 基本流程 {#section_gb1_zq4_law .section}

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23752/155970212947437_zh-CN.png)

1.  用户通过浏览器登录应用。
2.  应用重定向到阿里云 OIDC 服务并将 URL 返回给浏览器。

    **说明：** 如果用户还未登录，则会进一步重定向到阿里云登录服务。

3.  用户通过浏览器登录阿里云 OIDC 服务并申请授权码。
4.  阿里云 OIDC 服务重定向到应用并返回授权码。
5.  应用使用授权码向阿里云 OIDC 服务申请身份令牌。

    如何获取身份令牌的签名密钥，请参考：[应用获取身份令牌签名密钥](#section_31e_m2z_uzf)。

6.  阿里云 OIDC 服务向应用返回身份令牌，应用通过身份令牌便可以获取用户信息。
    -   在身份令牌用于获取用户信息的场景下，由于身份令牌是由应用直接从 OIDC 服务获取的，因此应用不需要验证令牌的签名。

        用户信息返回示例请参考：[用户信息返回示例](#section_at9_88y_ynv)。

    -   在身份令牌用于应用的各个不同模块之间通信的场景下，为保证信息安全，建议应用接受对身份令牌进行验证。

        如何验证身份令牌，请参考：[验证身份令牌的 JWT \(JSON Web Token\) 签名](#section_bzg_o4n_qul)。


## 应用获取身份令牌签名密钥 {#section_31e_m2z_uzf .section}

请求示例

``` {#codeblock_n6e_xyj_kmc}
private List getSignPublicKey() {
  HttpResponse response = HttpClientUtils.doGet("https://oauth.aliyun.com/v1/keys");
  List rsaKeyList = new ArrayList();
  if (response.getCode() == 200 && response.isSuccess()) {
    String keys = JSON.parseObject(response.getData()).getString("keys");
    try {
      JSONArray publicKeyList = JSON.parseArray(keys);
      for (Object object : publicKeyList) {
        RSAKey rsaKey = RSAKey.parse(JSONObject.toJSONString(object));
        rsaKeyList.add(rsaKey);
      }
      return rsaKeyList;
    } catch (Exception e) {
      LOG.info(e.getMessage());
    }
  }
  LOG.info("GetSignPublicKey failed:{}", response.getData());
  throw new AuthenticationException(response.getData());
}                    
```

## 验证身份令牌的 JWT \(JSON Web Token\) 签名 {#section_bzg_o4n_qul .section}

阿里云颁发的身份令牌是带有签名的 JWT，签名算法为 JWS 标准 RS256。当应用请求获取用户信息时，阿里云需要对身份令牌进行验证，包含以下几个方面：

-   签名验证：通过 OAuth 服务公布的签名公钥，验证身份令牌的真实性和完整性。
-   有效期验证：检查令牌颁发时间和令牌过期时间的有效性。
-   检查令牌接收者：防止颁发给其他应用的身份令牌被传递给本应用。

请求示例

``` {#codeblock_rvh_2nv_35z}
public boolean verifySign(SignedJWT signedJWT) {
  List publicKeyList = getSignPublicKey();
  RSAKey rsaKey = null;
  for (RSAKey key : publicKeyList) {
    if (signedJWT.getHeader().getKeyID().equals(key.getKeyID())) {
      rsaKey = key;
    }
  }
  if (rsaKey != null) {
    try {
      RSASSAVerifier verifier = new RSASSAVerifier(rsaKey.toRSAPublicKey());
      if (signedJWT.verify(verifier)) {
        return true;
      }
    } catch (Exception e) {
      LOG.info("Verify exception:{}", e.getMessage());
    }
  }
  throw new AuthenticationException("Can't verify signature for id token");
}
```

## 用户信息返回示例 {#section_at9_88y_ynv .section}

|参数名称|描述|需要的 OAuth 范围|
|:---|:-|------------|
|alg|签名算法。|openid|
|kid|验证身份令牌签名使用的公钥，用户需要使用此公钥验证签名，防止身份令牌被篡改。|openid|

|参数名称|描述|需要的 OAuth 范围|
|:---|:-|------------|
|exp|令牌过期时间。|openid|
|sub|令牌主体，登录用户的 UID。|openid|
|aud|令牌接收者，OAuth 应用 ID。|openid|
|iss|令牌颁发者。取值为：https://oauth.aliyun.com。|openid|
|iat|令牌颁发时间。|openid|
|name|登录用户的显示名称。|profile|
|upn|登录用户的 UPN（User Principal Name）。|profile|
|login\_name|主账号的登录名。|profile|
|aid|登录用户所属的阿里云账号 ID。|aliuid|
|uid|登录用户的阿里云账号 ID。|aliuid|

返回示例

返回 Header

``` {#codeblock_wyi_s6z_8ph}
{
  "alg": "RS256",
  "kid": "JC9wxzrhqJ0gtaCEt2QLUfevEUIwltFhui4O1bh****"
}
```

返回 Body

为了阅读方便，这里展示的是未加密的身份令牌的返回。实际返回为加密的身份令牌，详情请参考：[验证身份令牌的 JWT \(JSON Web Token\) 签名](#section_bzg_o4n_qul)。

-   主账号请求时的返回 Body

    ``` {#codeblock_3ya_tmq_obu}
    {
      "exp": 1517539523,
      "sub": "123456789012****",
      "aud": "4567890123456****",
      "iss": "https:\/\/oauth.aliyun.com",//中国站
      "iat": 1517535923,
      "name": "alice", //登录用户的显示名称
      "login_name":"alice@example.com", // 主账号的登录名
      "aid": "123456789012****", //对应的阿里云主账号 ID
      "uid": "123456789012****", //登录用户的阿里云账号 ID
    }
    ```

-   RAM 用户请求时的返回 Body

    ``` {#codeblock_vsm_fnv_xdg}
    {
      "exp": 1517539523,
      "sub": "123456789012****",
      "aud": "4567890123456****",
      "iss": "https:\/\/oauth.aliyun.com",
      "iat": 1517535923,
      "name": "alice", //登录用户的显示名称
      "upn": "alice@example.com",// RAM 用户的登录名
      "aid": "123456789012****", //对应的阿里云主账号 ID
      "uid": "234567890123****", //登录用户的阿里云账号 ID
    }
    ```


## 更多信息 {#section_l5o_ito_xf6 .section}

除了直接获取身份令牌，您也可以在获取访问令牌后通过调用 UserInfo 接口获取用户信息，该接口必须使用访问令牌才能访问，返回信息不加密。

**说明：** OIDC 场景下，即只有 openid，aliuid 和 profile 这几个范围的时候，也会返回访问令牌，此时的访问令牌只能用于调用UserInfo接口。

获取用户信息的请求地址：`https://oauth.aliyun.com/v1/userinfo`。

请求示例

``` {#codeblock_oii_yin_0ty}
GET v1/userinfo HTTP/1.1
Host: oauth.aliyun.com
Authorization: Bearer SlAV32hkKG 
```

返回 Body

-   主账号请求时的返回 Body

    ``` {#codeblock_r5a_r36_g3w}
    HTTP/1.1 200 OK
    Content-Type: application/json
    {
      "sub": "123456789012****", 
      "name": "alice", //登录用户的显示名称
      "login_name":"alice@example.com", // 主账号的登录名
      "aid": "123456789012****", //对应的阿里云主账号 ID
      "uid": "123456789012****", //登录用户的阿里云账号 ID
    }
    ```

-   RAM 用户请求时的返回 Body

    ``` {#codeblock_b6b_4ab_o67}
    HTTP/1.1 200 OK
    Content-Type: application/json
    {
      "sub": "123456789012****", 
      "name": "alice", //登录用户的显示名称
      "upn": "alice@example.com",// RAM 用户的登录名
      "aid": "123456789012****", //对应的阿里云主账号 ID
      "uid": "234567890123****", //登录用户的阿里云账号 ID
    }
    ```


