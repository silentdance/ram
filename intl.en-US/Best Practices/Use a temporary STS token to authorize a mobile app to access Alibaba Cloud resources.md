# Use a temporary STS token to authorize a mobile app to access Alibaba Cloud resources {#concept_tdn_n2k_xdb .concept}

This topic describes how to use a temporary STS token of a RAM role to authorize a mobile app to access Alibaba Cloud resources.

## Scenario {#section_01 .section}

Enterprise A has developed a mobile app, which runs on users' own devices. Therefore, Enterprise A cannot manage these devices directly and wants to use Alibaba Cloud OSS so that the mobile app can upload data to or download data from OSS.

The requirements of Enterprise A are as follows:

-   The app does not need to use an application server to transmit data. Instead, it can directly upload data to or download data from OSS.
-   To maintain account security, Enterprise A will not save the access key to the mobile app because mobile devices that run the app are not managed by Enterprise A directly.
-   Security risks are minimized by granting the app temporary access credentials \(by means of an STS token\) that the app can then use to connect to OSS. The app can access OSS only for a specified duration.

## Solution {#section_03 .section}

Before you upload data to or download data from OSS, the mobile app must first apply for an access credential from the application server. The application server assumes a RAM role as a RAM user, calls the AssumeRole action of the STS API to obtain a temporary STS token, and then sends the STS token to the mobile app. After the STS token is sent, the mobile app uses the STS token to access OSS.

![Use a temporary STS token to authorize a mobile app to access Alibaba Cloud resources](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23775/156680415614407_en-US.png)

1.  The mobile app applies for an access credential from the application server.
2.  Enterprise A uses its Alibaba Cloud account to create a RAM role and grant relevant permissions to the role.

    For more information, see [Create a RAM role and grant relevant permissions](#section_04).

3.  Enterprise A uses its Alibaba Cloud account to create a RAM user for the application server to assume the RAM role.

    For more information, see [Create a RAM user and allow the user to assume a RAM role](#section_ngg_4ea_gpn).

4.  The application server calls the [AssumeRole](../../../../reseller.en-US/API Reference (STS)/Operation interfaces/AssumeRole.md#) action of the STS API to obtain a temporary STS token of the RAM role.

    For more information, see [Obtain the STS token of the RAM role](#section_05).

5.  The application server further limits the resource operation permissions of the temporary STS token when it assumes the role, to better manage the permissions of each app.

    For more information, see [Restrict STS token permissions](#section_06).

6.  The mobile app uses the temporary STS token to upload data to or download data from OSS.

    For more information, see [Use the STS token to access OSS](#section_14v_k3h_jad).


## Create a RAM role and grant relevant permissions {#section_04 .section}

Assume that the Alibaba Cloud account ID of Enterprise A is `123456789012****`.

1.  Enterprise A uses its Alibaba Cloud account to create a RAM role `oss-readonly` and selects **Current Alibaba Cloud Account** as the trusted account so that only RAM users under the Alibaba Cloud account can assume this role.

    For information about how to create a RAM role, see [Create a RAM role for a trusted Alibaba Cloud account](../../../../reseller.en-US/User Guide/RAM roles/Create a RAM role/Create a RAM role for a trusted Alibaba Cloud account.md#).

    After creating the role, Enterprise A can view the role information on the basic information page.

    -   In this example, the Alibaba Cloud Resource Name \(ARN\) of the role is `acs:ram::123456789012****:role/oss-readonly`.
    -   The trust policy of the role \(in which only RAM users under the current Alibaba Cloud account of Enterprise A can assume\) is as follows:

        ``` {#codeblock_qnb_kcv_izv}
        {
        "Statement": [
        {
         "Action": "sts:AssumeRole",
         "Effect": "Allow",
         "Principal": {
           "RAM": [
             "acs:ram::123456789012****:root"
           ]
         }
        }
        ],
        "Version": "1"
        }
        ```

2.  Enterprise A uses its Alibaba Cloud account to attach the `AliyunOSSReadOnlyAccess` policy \(OSS read-only permission\) to the role `oss-readonly`.

    For information about how to grant permission to a RAM role, see [Grant permission to a RAM role](../../../../reseller.en-US/User Guide/RAM roles/Grant permission to a RAM role.md#).


## Create a RAM user and allow the user to assume a RAM role {#section_ngg_4ea_gpn .section}

1.  Enterprise A uses its Alibaba Cloud account to create a RAM user `appserver`.

    For information about how to create a RAM user, see [Create a RAM user](../../../../reseller.en-US/User Guide/RAM users/Create a RAM user.md#).

2.  Enterprise A uses its Alibaba Cloud account to attach the `AliyunSTSAssumeRoleAccess` policy to the user `appserver` so that the user can assume a RAM role.

    For information about how to grant permission to a RAM user, see [Grant permission to a RAM user](../../../../reseller.en-US/User Guide/RAM users/Grant permission to a RAM user.md#).


## Obtain the STS token of the RAM role {#section_05 .section}

1.  The application server uses the access key of the RAM user to call the AssumeRole action of the STS API.

    **Note:** The access key for the application server must be configured.

    The following is an example of how to use Alibaba Cloud CLI to call the AssumeRole action:

    ``` {#codeblock_ago_nku_ae6}
    $ aliyuncli sts AssumeRole --RoleArn acs:ram::123456789012****:role/oss-readonly --RoleSessionName client-001
     {
         "AssumedRoleUser": {
             "AssumedRoleId": "391578752573****:client-001", 
             "Arn": "acs:ram::123456789012****:role/oss-readonly/client-001"
         }, 
         "Credentials": {
             "AccessKeySecret": "93ci2umK1QKNEja6WGqi1Ba7Q2Fv9PwxZqtVF2Vy****", 
             "SecurityToken": "********", 
             "Expiration": "2016-01-13T15:02:37Z", 
             "AccessKeyId": "STS.F13GjskXTjk38dBY6YxJt****"
         }, 
         "RequestId": "E1779AAB-E7AF-47D6-A9A4-53128708B6CE"
     }
    ```

    **Note:** If the `Policy` parameter is left unspecified, the returned STS token has all the permissions of the RAM role `oss-readonly`.

2.  The STS service sends the STS token to the application server. The STS token contains the following elements: `AccessKeyId`, `AccessKeySecret`, and `SecurityToken`.

    **Note:** The validity period of the security token \(`SecurityToken`\) is determined. If the application requires a longer validity period, the application server must re-issue a new STS token, for example, issue one STS token every 1800 seconds.


## Restrict STS token permissions {#section_06 .section}

Enterprise A configures the `Policy` parameter to further restrict the permissions of the STS token.

For example, Enterprise A allows the STS token to access only `sample-bucket/2015/01/01/*.jpg`.

``` {#codeblock_x17_jfh_j1z}
$ aliyuncli sts AssumeRole --RoleArn acs:ram::123456789012****:role/oss-readonly --RoleSessionName client-002 --Policy "{\"Version\":\"1\", \"Statement\": [{\"Effect\":\"Allow\", \"Action\":\"oss:GetObject\", \"Resource\":\"acs:oss:*:*:sample-bucket/2015/01/01/*.jpg\"}]}"
{
   "AssumedRoleUser": {
       "AssumedRoleId": "391578752573****:client-002", 
       "Arn": "acs:ram::123456789012****:role/oss-readonly/client-002"
   }, 
   "Credentials": {
       "AccessKeySecret": "28Co5Vyx2XhtTqj3RJgdud4ntyzrSNdUvNygAj7x****", 
       "SecurityToken": "********", 
       "Expiration": "2016-01-13T15:03:39Z", 
       "AccessKeyId": "STS.FJ6EMcS1JLZgAcBJSTDG1****"
   }, 
   "RequestId": "98835D9B-86E5-4BB5-A6DF-9D3156ABA567"
}
```

**Note:** The default validity period of the STS token is 3600 seconds \(maximum limit\). You can specify the `DurationSeconds` parameter to limit the STS token expiration time.

## Use the STS token to access OSS {#section_14v_k3h_jad .section}

1.  The application server sends the STS token to the mobile app.
2.  The mobile app uses the STS token to access OSS.

    The following is an example of how to use Alibaba Cloud CLI and the STS token to access an OSS object:

    ``` {#codeblock_yzc_4zg_m1a}
    Configure the STS token syntax: aliyuncli oss Config --host  --accessid  --accesskey  --sts_token 
    $ aliyuncli oss Config --host oss.aliyuncs.com --accessid STS.FJ6EMcS1JLZgAcBJSTDG1**** --accesskey 28Co5Vyx2XhtTqj3RJgdud4ntyzrSNdUvNygAj7x**** --sts_token CAESnQMIARKAASJgnzMzlXVyJn4KI+FsysaIpTGm8ns8Y74HVEj0pOevO8ZWXrnnkz4a4rBEPBAdFkh3197GUsprujsiU78FkszxhnQPKkQKcyvPihoXqKvuukrQ/Uoudk31KAJEz5o2EjlNUREcxWjRDRSISMzkxNTc4NzUyNTczOTcyODU0KgpjbGllbnQtMDAxMKmZxIHBKjoGUnNhTUQ1Qn8KATEaegoFQWxsb3cSJwoMQWN0aW9uRXF1YWxzEgZBY3Rpb24aDwoNb3NzOkdldE9iamVjdBJICg5SZXNvdXJjZUVxdWFscxIIUmVzb3VyY2UaLAoqYWNzOm9zczoqOio6c2FtcGxlLWJ1Y2tldC8yMDE1LzAxLzAxLyouanBnSgU0MzI3NFIFMjY4NDJaD0Fzc3VtZWRSb2xlVXNlcmAAahIzOTE1Nzg3NTI1NzM5NzI4NTRyCWVjcy1hZG1pbnjgxt7Cj/bo****
    Access OSS
    $ aliyuncli oss Get oss://sample-bucket/2015/01/01/grass.jpg grass.jpg
    ```


## What to do next {#section_07 .section}

For more information, see:

-   [Set up direct data transfer for mobile apps](../../../../reseller.en-US/Best Practices/Application server/Set up direct data transfer for mobile apps.md#)
-   [Permission control](../../../../reseller.en-US/Best Practices/Application server/Permission control.md#)
-   [Set up data callback for mobile apps](../../../../reseller.en-US/Best Practices/Application server/Set up data callback for mobile apps.md#)
-   [STS temporary access authorization](../../../../reseller.en-US/Developer Guide/Hide/Access control/STS temporary access authorization.md#)

