# Request structure {#concept_stv_fnk_xdb .concept}

This topic describes the details about the request structure, including the endpoint of Resource Access Management \(RAM\), communications protocol, HTTP request methods, and request parameters.

## Endpoint {#section_m4p_wpk_xdb .section}

The RAM endpoint is `https://ram.aliyuncs.com`.

## Communications protocol {#section_n4p_wpk_xdb .section}

To ensure communication security, RAM only allows you to send requests over HTTPS.

## HTTP request methods {#section_o4p_wpk_xdb .section}

RAM allows you to send HTTP GET and POST requests.

**Note:** The size of each HTTP GET request cannot exceed 4 KB, and the size of each HTTP POST request cannot exceed 10 MB.

## Request parameters {#section_p4p_wpk_xdb .section}

You must specify the following parameters for each API request:

-   The Action parameter. It specifies the operation you want to perform.
-   The common request parameters.
-   The request parameters that are specific to the specified API operation.

## Character encoding {#section_q4p_wpk_xdb .section}

Requests and responses are encoded by using the UTF-8 character set.

