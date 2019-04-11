# GetCallerIdentity {#reference_yyw_ssv_xdb .reference}

通过该接口，可以获取当前调用者的身份信息。

## 请求参数 {#section_it1_ksv_xdb .section}

|名称|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|GetCallerIdentity|系统规定参数。取值：GetCallerIdentity|

## 返回参数 {#section_tqj_lsv_xdb .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|RequestId|String|2C9BE469-4A35-44D5-9529-CAA280B11603|请求 ID。|
|Arn|String|acs:ram::196813200012\*\*\*\*:user/admin|当前调用者的 ARN。|
|AccountId|String|196813200012\*\*\*\*|当前调用者所属主帐号的数字 ID。|
|UserId|String|216959339000\*\*\*\*|当前调用者的用户 ID。如果当前调用者是主帐号，则返回值与`AccountId`相同。|

## 操作示例 {#section_tdy_lsv_xdb .section}

请求示例

```

https://sts.aliyuncs.com?Action=GetCallerIdentity
&<公共请求参数>

```

返回示例

`XML`格式

```
<GetCallerIdentityResponse>
    <RequestId>2C9BE469-4A35-44D5-9529-CAA280B11603</RequestId>
    <AccountId>196813200012****</AccountId>
    <UserId>216959339000****</UserId>
    <Arn>acs:ram::196813200012****:user/admin</Arn>
</GetCallerIdentityResponse>
```

`JSON`格式

```
{
    "RequestId": "2C9BE469-4A35-44D5-9529-CAA280B11603",
    "AccountId": "196813200012****",
    "UserId": "216959339000****",
    "Arn": "acs:ram::196813200012****:user/admin"
}
```

