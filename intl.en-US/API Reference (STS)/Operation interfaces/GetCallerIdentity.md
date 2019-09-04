# GetCallerIdentity {#reference_yyw_ssv_xdb .reference}

You can call this operation to query the identity of the user who is making the API request.

## Request parameters {#section_it1_ksv_xdb .section}

|Parameter|Type|Required|Example|Description|
|:--------|:---|:-------|:------|:----------|
|Action|String|Yes|GetCallerIdentity|The operation that you want to perform. Set this parameter to GetCallerIdentity.|

## Response parameters {#section_tqj_lsv_xdb .section}

|Parameter|Type|Example|Description|
|:--------|:---|:------|:----------|
|RequestId|String|2C9BE469-4A35-44D5-9529-CAA280B11603|The ID of the request.|
|Arn|String|acs:ram::196813200012\*\*\*\*:user/admin|The Alibaba Cloud Resource Name \(ARN\) of the user who is calling the API operation.|
|AccountId|String|196813200012\*\*\*\*|The ID of the Alibaba Cloud account to which the user who is calling the API operation belongs. The ID only consists of digits.|
|UserId|String|216959339000\*\*\*\*| -   The ID of the user who is calling the API operation. If the user is a RAM user under an Alibaba Cloud account, this parameter and the AccountId parameter are returned.
-   If the user is the owner of an Alibaba Cloud account, the AccountId parameter is returned. The UserId parameter is not returned.

 |
|RoleId|String|33537620082992\*\*\*\*|The ID of the RAM role that is assumed by the user who is calling the API operation. If the user uses a RAM role to call the API operation, this parameter and the AccountId parameter are returned.|
|PrincipalId|String|28877424437521\*\*\*\*|The ID of the principle.|
|IdentityType|String|RAMUser|The type of the identity.|

## Examples {#section_tdy_lsv_xdb .section}

Sample requests

``` {#codeblock_39p_4iy_qco}
https://sts.aliyuncs.com?Action=GetCallerIdentity
&<Common request parameters>        
```

Sample responses

`XML` format

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

`JSON` format

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

## Error codes {#section_epa_14v_4if .section}

None.

