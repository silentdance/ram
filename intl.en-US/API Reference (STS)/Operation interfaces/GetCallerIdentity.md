# GetCallerIdentity {#reference_yyw_ssv_xdb .reference}

Obtains the identity of the user who is calling the API action.

## Request parameters {#section_it1_ksv_xdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|:------------|:----------|
|Action|String|Yes|GetCallerIdentity| The name of this action.

 Value: GetCallerIdentity

 |

## Response parameters {#section_tqj_lsv_xdb .section}

|Parameter|Type|Example value|Description|
|:--------|:---|:------------|:----------|
|RequestId|String|2C9BE469-4A35-44D5-9529-CAA280B11603|The request ID.|
|Arn|String|acs:ram::196813200012\*\*\*\*:user/admin|The Alibaba Cloud Resource Name \(ARN\) of the user who is calling the API action.|
|AccountId|String|196813200012\*\*\*\*|The ID of the Alibaba Cloud account to which the user who is calling the API action belongs.|
|UserId|String|216959339000\*\*\*\*|The ID of the user who is calling the API action. If the user is the owner of an Alibaba Cloud account, the AccountId parameter is returned.|

## Example {#section_tdy_lsv_xdb .section}

Request example

``` {#codeblock_39p_4iy_qco}
https://sts.aliyuncs.com?Action=GetCallerIdentity
&<Common parameters>        
```

Response example

`XML` format

``` {#codeblock_h73_mvs_xhy}
<GetCallerIdentityResponse>
    <RequestId>2C9BE469-4A35-44D5-9529-CAA280B11603</RequestId>
    <AccountId>196813200012****</AccountId>
    <UserId>216959339000****</UserId>
    <Arn>acs:ram::196813200012****:user/admin</Arn>
</GetCallerIdentityResponse>
```

`JSON` format

``` {#codeblock_k0r_0t3_gqw}
{
    "RequestId": "2C9BE469-4A35-44D5-9529-CAA280B11603",
    "AccountId": "196813200012****",
    "UserId": "216959339000****",
    "Arn": "acs:ram::196813200012****:user/admin"
}
```

## Errors {#section_epa_14v_4if .section}

None.

