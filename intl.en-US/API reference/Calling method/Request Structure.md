# Request Structure {#reference_ntw_s4v_xdb .reference}

## Endpoint {#section_eys_z4v_xdb .section}

For the STS service address, see [Service address](reseller.en-US/API reference/Appendix/Service address.md).

## Communication protocol {#section_tqr_1pv_xdb .section}

To ensure communication security, the STS service uses only the HTTPS secure channel to send requests.

## HTTP request methods {#section_rkw_bpv_xdb .section}

The system allows you to send HTTP GET/POST requests. In this method, the request parameters must be included in the request URL. \(The size of a GET request cannot exceed 4 KB, and the size of a POST requests cannot exceed 10 MB.\)

## Request parameters {#section_zlt_cpv_xdb .section}

You must use an “Action” parameter \(such as “AddUser”\) in each request to specify the operation to perform, and meanwhile you must add public request parameters and interface-specified request parameters that each operation interface requires.

## Character encoding {#section_ov3_dpv_xdb .section}

Requests and responses are encoded using UTF-8.

