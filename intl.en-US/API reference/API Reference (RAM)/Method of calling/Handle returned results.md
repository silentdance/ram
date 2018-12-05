# Handle returned results {#reference_slh_1rk_xdb .reference}

After the API service is called, data is returned in a unified format. The returned HTTP status code 2xx indicates that the call is successful. The returned HTTP status code 4xx or 5xx indicates that the call fails. For successful calls, the returned data are mainly in two formats: XML and JSON. When a request is sent, an external system can input a parameter to define the format of returned data, which is XML by default. In this document, examples of returned results are formatted in a way that is easier for you to view. The actual results returned are not formatted with line breaks, indentation, and so on.

## Successful results {#section_wmm_crk_xdb .section}

-   **XML example**

    XML returned results include a message stating if the request is successful and the specific service data. Example:

    ```
    <? xml version="1.0" encoding="utf-8"? >
    <!—Result root node-->
    <Interface name+response>
        <!—Return request tag-->
        <RequestId>4C467B38-3910-447D-87BC-AC049166F216</RequestId>
        <!—Return result data-->
    </Interface name+response>
    ```

-   **JSON example**

    ```
    
        "RequestId": "4C467B38-3910-447D-87BC-AC049166F216",
        /* Return result data */
    
    ```


## Incorrect results {#section_psj_lrk_xdb .section}

If there is an interface call error, no result data is returned. You can locate error causes according to [Error code](reseller.en-US/API reference/API Reference (STS)/Appendix/Error code.md).

When an error occurs in a call, an HTTP status code 4xx or 5xx will be returned for an HTTP request. The returned message body contains the specific error code and error message. The message body also contains the globally unique “RequestId” and the requested “HostId”. If you cannot find the error cause, you can contact Alibaba Cloud customer service and provide “HostId” and “RequestId” to help us solve the problem as quickly as possible.

-   **XML example**

    ```
    <? xml version="1.0" encoding="UTF-8"? >
    <Error>
       <RequestId>8906582E-6722-409A-A6C4-0E7863B733A5</RequestId>
       <HostId>ram.aliyuncs.com</HostId>
       <Code>InvalidParameter</Code>
       <Message>The specified parameter "Action or Version" is not valid.</Message>
    </Error>
    ```

-   **JSON example**

    ```
    
        "RequestId": "7463B73D-35CC-4D19-A010-6B8D65D242EF",
        "HostId": "ram.aliyuncs.com",
        "Code": "InvalidParameter",
        "Message": "The specified parameter \"Action or Version\" is not valid."
    
    ```


