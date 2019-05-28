# Signature mechanism {#reference_ax4_3sk_xdb .reference}

RAM authenticates the identity of each access request. Therefore, no matter whether submitted through HTTP or HTTPS, a request must contain signature information. RAM uses **AccessKeyId** and **AccessKeySecret** for symmetric encryption to verify the identities of request senders. **AccessKeyId** and **AccessKeySecret** are officially issued to visitors by Alibaba Cloud \(visitors can apply for and manage them on the official website of Alibaba Cloud\). **AccessKeyId** indicates the identity of the visitor, and **AccessKeySecret** is the secret key used to encrypt the signature string and to verify the signature string on the server. It must be kept strictly confidential and should only be known only by Alibaba Cloud and the authenticated visitor.

## Procedure {#section_p4v_lsk_xdb .section}

1.  Use request parameters to construct a canonicalized query string.
    1.  Sort all request parameters \(including public request parameters and user-defined parameters with given request APIs described in this topic and excluding the Signature parameter\) alphabetically by parameter name.

        **Note:** If you use the GET method to submit requests, these parameters will be included in the request URI, namely, the part after the question mark \(?\) following the ampersand \(&\) in the URI.

    2.  Encode the name and value of each request parameter. URL encoding using the UTF-8 character set is required. URL encoding rules are as follows:

        -   Upper case letters from A to Z, lowercase letters from a to z, digits from 0 to 9, and other characters including en dashes \(-\), underscores \(\_\), periods \(.\), and tildes \(~\) are not encoded.
        -   Other characters are encoded in %XY format, with XY representing the characters' ASCII code in hexadecimal notation. For example, double quotation marks \(""\) are encoded as %22.
        -   It must be noted that spaces are encoded as %20 instead of plus signs \(+\).
        **Note:** Generally, URL-encoded libraries \(such as java.net.URLEncoder in Java\) are encoded based on rules of the MIME type in application/x-www-form-urlencoded format. You can directly use this encoding method by replacing the plus sign \(+\) in the encoded string with %20 and the asterisk \(\*\) with %2A. Also, you must change %7E back to the tilde \(~\) to conform to the encoding rules described above.

    3.  Connect the encoded parameter names and values with equal signs \(=\).
    4.  Connect the parameter name and value pairs connected by equal signs \(=\) alphabetically by parameter name with ampersands \(&\) to produce a canonicalized query string.
2.  Use the canonicalized query string to construct the string for signature calculation according to the rule:

    ```
    StringToSign= HTTPMethod + "&" + percentEncode("/") + "&" + percentEncode(CanonicalizedQueryString)
    ```

    In this rule, HTTPMethod is the HTTP method \(for example, GET\) used for request submission. percentEncode\("/"\) is the encoded value \(namely, %2F\) for the character "/" according to the URL encoding rules described in 1.b.

    percentEncode\(CanonicalizedQueryString\) is the canonicalized query string encoded by following the URL encoding rules described in 1.b.

3.  Use the string for signature calculation to calculate the HMAC value of the signature based on [RFC2104](http://www.ietf.org/rfc/rfc2104.txt). Note that the key used for signature calculation is your AccessKeySecret with an ampersand \(&\) \(ASCII code: 38\) and it is based on the hash algorithm SHA1.
4.  Encode the HMAC value as a string according to the base64 encoding rules to obtain the signature.
5.  Add the signature to the parameters of a request as a signature parameter. Note that the obtained signature value requires URL encoding based on RFC3986 rules like other parameters before it is submitted to the RAM server as the final request parameter value.

## Example {#section_zpc_ysk_xdb .section}

Use CreateUser as an example. The request URL before signature is:

```
https://ram.aliyuncs.com/?UserName=test&SignatureVersion=1.0&Format=JSON&Timestamp=2015-08-18T03%3A15%3A45Z&AccessKeyId=testid&SignatureMethod=HMAC-SHA1&Version=2015-05-01&Action=CreateUser&SignatureNonce=6a6e0ca6-4557-11e5-86a2-b8e8563dc8d2
```

The corresponding StringToSign is:

```
GET&%2F&AccessKeyId%3Dtestid%26Action%3DCreateUser%26Format%3DJSON%26SignatureMethod%3DHMAC-SHA1%26SignatureNonce%3D6a6e0ca6-4557-11e5-86a2-b8e8563dc8d2%26SignatureVersion%3D1.0%26Timestamp%3D2015-08-18T03%253A15%253A45Z%26UserName%3Dtest%26Version%3D2015-05-01
```

Assume that the value of the AccessKeyId parameter is testid and that of the AccessKeySecret parameter is testsecret, and the key used for HMAC calculation is testsecret&. The calculated signature value is:

```
kRA2cnpJVacIhDMzXnoNZG9tDCI%3D
```

The signed request URL is \(with the Signature parameter added\):

```
https://ram.aliyuncs.com/?UserName=test&SignatureVersion=1.0&Format=JSON&Timestamp=2015-08-18T03%3A15%3A45Z&AccessKeyId=testid&SignatureMethod=HMAC-SHA1&Version=2015-05-01&Signature=kRA2cnpJVacIhDMzXnoNZG9tDCI%3D&Action=CreateUser&SignatureNonce=6a6e0ca6-4557-11e5-86a2-b8e8563dc8d2
```

