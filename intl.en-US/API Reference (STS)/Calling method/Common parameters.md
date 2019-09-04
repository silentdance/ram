# Common parameters {#reference_rzc_v4v_xdb .reference}

This topic describes the common parameters, including the common request parameters and common response parameters.

## Common request parameters {#section_ilz_1ry_3hb .section}

|Parameter|Type|Required|Description|
|:--------|:---|:-------|:----------|
|Action|String|Yes|The operation that you want to perform.|
|Format|String|No|The format to return the response values in. Valid values: `JSON` and `XML`. Default value: `XML`.|
|Version|String|Yes|The version number of the API. Specify the version in the YYYY-MM-DD format. Set this parameter to 2015-04-01.|
|Signature|String|Yes|The signature string of the current request.|
|SignatureMethod|String|Yes|The encryption method of the signature string. Set this parameter to HMAC-SHA1.|
|SignatureNonce|String|Yes|A unique, random number used to prevent replay attacks. You must use different numbers for different requests.|
|SignatureVersion|String|Yes|The version of the signature encryption algorithm. Set this parameter to 1.0.|
|AccessKeyId|String|Yes|The AccessKey ID provided to you by Alibaba Cloud.|
|Timestamp|String|Yes|The timestamp of the request. Specify the time in the ISO 8601 standard in the YYYY-MM-DDThh:mm:ssZ format. The time must be in UTC.|

## Common response parameters {#section_dsh_ydz_ngb .section}

|Parameter|Type|Description|
|:--------|:---|:----------|
|RequestId|String|The ID of the request. The system returns a unique request ID for each API request. This request ID is used to identify each API request.|

## Sample requests {#section_azp_mqk_xdb .section}

``` {#codeblock_3kc_jgf_n6g .lanuage-xml}
https://sts.aliyuncs.com/?Action=XXXXXX
? Format=xml
&Version=2015-04-01
&Signature=Pc5WB8gokVn0xfeu%2FZV%2BiNM1dg****
&SignatureMethod=HMAC-SHA1
&SignatureNonce=1521552885****
&SignatureVersion=1.0
&AccessKeyId=key-test
&Timestamp=2012-06-01T12:00:00Z
…
```

## Sample responses {#section_rkn_nqk_xdb .section}

-   XML format

    ``` {#codeblock_jro_u3w_4ee .lanuage-xml}
    <? xml version="1.0" encoding="utf-8"? >
    <!—Response root node-->
    <API operation name+response>
      <!—Request ID-->
      <RequestId>4C467B38-3910-447D-87BC-AC049166F216</RequestId>
      <!—Result data-->
    </API operation name+response>
    ```

-   JSON format

    ``` {#codeblock_wzv_hgv_y7e .language-json}
    {
      "RequestId": "4C467B38-3910-447D-87BC-AC049166F216"
      /* Result data */
    }
    ```


