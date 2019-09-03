# Responses {#concept_slh_1rk_xdb .concept}

After RAM API operations are called, data is returned in a unified format. The returned data is in either the XML or JSON format, and the XML format is the default choice. Sample responses in our API documents are formatted in a way that is easier for you to read. The actual responses are not formatted with line breaks or indentation.

## Sample success responses {#section_wmm_crk_xdb .section}

The HTTP status code `2xx` indicates that the API operation is successful.

-   XML format

    ``` {#codeblock_qty_af8_lo9 .lanuage-xml}
    <? xml version="1.0" encoding="utf-8"? >
    <!—Response root node-->
    <API operation name+response>
        <!—Request ID-->
        <RequestId>4C467B38-3910-447D-87BC-AC049166F216</RequestId>
        <!—Result data-->
    </API operation name+response>
    ```

-   JSON format

    ``` {#codeblock_je9_zdn_m7j .language-json}
    {
        "RequestId": "4C467B38-3910-447D-87BC-AC049166F216",
        /* Result data */
    }
    ```


## Sample error responses {#section_psj_lrk_xdb .section}

The HTTP status code `4xx` or `5xx` indicates that the API operation failed, and no result data is returned. The returned message body contains the specific error code, error message, the value of the `RequestId` parameter, and the value of the `HostId` parameter. The RequestId parameter indicates the globally unique ID of the API request, and the HostId parameter indicates the ID of the host to which your API request is sent. You can locate the errors by using the error codes. You can locate the errors by using the error codes. For more information, see [Error codes](https://error-center.aliyun.com/status/product/Ram).

-   XML format

    ``` {#codeblock_tw4_sae_rsz .lanuage-xml}
    <? xml version="1.0" encoding="UTF-8"? >
    <Error>
       <RequestId>8906582E-6722-409A-A6C4-0E7863B733A5</RequestId>
       <HostId>ram.aliyuncs.com</HostId>
       <Code>InvalidParameter</Code>
       <Message>The specified parameter "Action or Version" is not valid. </Message>
    </Error>
    ```

-   JSON format

    ``` {#codeblock_af1_rw2_ic8 .language-json}
    {
        "RequestId": "7463B73D-35CC-4D19-A010-6B8D65D242EF",
        "HostId": "ram.aliyuncs.com",
        "Code": "InvalidParameter",
        "Message": "The specified parameter \"Action or Version\" is not valid."
    }
    ```


