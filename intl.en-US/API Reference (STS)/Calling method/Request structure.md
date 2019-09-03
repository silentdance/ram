# Request structure {#concept_ntw_s4v_xdb .concept}

This topic describes the details about the request structure, including the endpoints of Security Token Service \(STS\), communications protocol, HTTP request methods, and request parameters.

## Endpoints {#section_eys_z4v_xdb .section}

For more information about the STS endpoints, see [Endpoints](reseller.en-US/API Reference (STS)/Calling method/Endpoints.md).

## Communications protocol {#section_tqr_1pv_xdb .section}

To ensure communication security, STS only allows you to send requests over HTTPS.

## HTTP request methods {#section_rkw_bpv_xdb .section}

STS allows you to send HTTP GET and POST requests.

**Note:** The size of each HTTP GET request cannot exceed 4 KB, and the size of each HTTP POST request cannot exceed 10 MB.

## Request parameters {#section_zlt_cpv_xdb .section}

You must specify the following parameters for each API request:

-   The Action parameter. It specifies the operation you want to perform.
-   The common request parameters.
-   The request parameters that are specific to the specified API operation.

## Character encoding {#section_ov3_dpv_xdb .section}

Requests and responses are encoded by using the UTF-8 character set.

