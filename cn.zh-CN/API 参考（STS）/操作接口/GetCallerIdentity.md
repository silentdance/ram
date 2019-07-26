# GetCallerIdentity {#reference_yyw_ssv_xdb .reference}

调用GetCallerIdentity接口获取当前调用者的身份信息。

## 请求参数 {#section_it1_ksv_xdb .section}

|名称|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|GetCallerIdentity|系统规定参数。取值：GetCallerIdentity|

## 返回数据 {#section_tqj_lsv_xdb .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|RequestId|String|2C9BE469-4A35-44D5-9529-CAA280B11603|请求ID。|
|Arn|String|acs:ram::196813200012\*\*\*\*:user/admin|当前调用者的ARN。|
|AccountId|String|196813200012\*\*\*\*|当前调用者所属云帐号的数字ID。|
|UserId|String|216959339000\*\*\*\*| -   如果当前调用者是RAM用户，则返回当前调用者的UID。
-   如果当前调用者是云帐号，则返回当前调用者云账号ID。

 |
|RoleId|String|33537620082992\*\*\*\*|如果当前调用者是RAM角色，则返回当前调用者的角色ID。|
|PrincipalId|String|28877424437521\*\*\*\*|身份标识。|
|IdentityType|String|RAMUser|身份类型。|

## 示例 {#section_tdy_lsv_xdb .section}

请求示例

``` {#codeblock_39p_4iy_qco}
https://sts.aliyuncs.com?Action=GetCallerIdentity
&<公共请求参数>        
```

返回示例

`XML`格式

``` {#codeblock_ryq_sc1_6e9 .lanuage-xml}
<GetCallerIdentityResponse>
    <RequestId>2C9BE469-4A35-44D5-9529-CAA280B11603</RequestId>
    <AccountId>196813200012****</AccountId>
    <UserId>216959339000****</UserId>
    <IdentityType>RAMUser</IdentityType>
    <PrincipalId>28877424437521****</PrincipalId>
    <Arn>acs:ram::196813200012****:user/admin</Arn>
</GetCallerIdentityResponse>
```

`JSON`格式

``` {#codeblock_15s_mzn_twx .language-json}
{
    "RequestId": "2C9BE469-4A35-44D5-9529-CAA280B11603",
    "AccountId": "196813200012****",
    "UserId": "216959339000****",
    "IdentityType": "RAMUser",
    "PrincipalId": "28877424437521****",
    "Arn": "acs:ram::196813200012****:user/admin"
}
```

## 错误码 {#section_epa_14v_4if .section}

无。

