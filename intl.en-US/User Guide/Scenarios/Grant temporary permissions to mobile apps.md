# Grant temporary permissions to mobile apps {#concept_tdn_n2k_xdb .concept}

This topic describes how to use the RAM role STS token to grant temporary permissions to mobile apps.

## Scenario {#section_01 .section}

Enterprise A has developed a mobile app, which runs on users' own devices. Therefore, Enterprise A cannot manage these devices directly and wants to use Alibaba Cloud OSS so that the mobile app can upload data to and download data from OSS.

The requirements of Enterprise A are as follows:

-   Enterprise A does not want the app to use the appServer to transmit data. Instead, it wants the app to directly upload data to and download data from OSS.
-   To maintain account security, Enterprise A will not save the AccessKey to the mobile app because mobile devices that run the app are not managed by Enterprise A directly.
-   Enterprise A wants to minimize its security risks by granting the app temporary access credentials \(by means of an STS token\) that the app can then use to connect to OSS, thereby restricting the access duration to a specified period of time.

## Solution {#section_03 .section}

-   Use the Alibaba Cloud account of Enterprise A \(Account A\) to create a role in RAM, grant relevant permissions to the role, and allow the appServer \(which is logged on as a RAM user\) to use this role.

    For more information, see [Create a RAM role and user, and grant permissions](#).

-   When an app needs to connect directly to OSS to upload or download data, the appServer can assume a role \(by calling the STS AssumeRole API\) to get a temporary STS token and transfer it to the app. Then, the app can use the temporary STS token to access the OSS API directly.

    For more information, see [Obtain and transfer the role STS token and access OSS](#).

-   The appServer can further limit the resource operation permissions of the temporary STS token when it assumes the role, to better manage the permissions of each app.

    For more information, see [Restrict STS token permissions](#).


## Create a RAM role and user, and grant permissions {#section_04 .section}

Assume that the account ID of Account A is 11223344.

1.  Account A creates a RAM role `oss-readonly` and selects **Current Alibaba Cloud Account** as the trusted account so that only RAM users under Account A can assume this role.

    For more information, see [Manage RAM roles](reseller.en-US/User Guide/Identity management/RAM roles and identities/Manage RAM roles.md#).

    After creating the role, Enterprise A can view the role information on the basic information page.

    -   In this example, the Alibaba Cloud Resource Name \(ARN\) of the role is as follows:

        ```
        acs:ram::11223344:role/oss-readonly
        ```

    -   The trust policy in the role \(in which only RAM users under Account A can assume\) is as follows:

        ```
        {
        "Statement": [
        {
         "Action": "sts:AssumeRole",
         "Effect": "Allow",
         "Principal": {
           "RAM": [
             "acs:ram::11223344:root"// If the trusted entity type of the role is Alibaba Cloud account, 'root' is used by default.
           ]
         }
        }
        ],
        "Version": "1"
        }
        ```

2.  Account A attaches the policy `AliyunOSSReadOnlyAccess` \(OSS read-only permission\) to the role oss-readonly.

    For more information, see [Permission granting in RAM](reseller.en-US/User Guide/Permission management/Permission granting/Permission granting in RAM.md#).

3.  Account A creates a RAM user \(here, the RAM user is named Appserver\) for the appServer, creates an AccessKey for the RAM user, and attaches the `AliyunSTSAssumeRoleAccess` system policy to the user so that the user can call the STS AssumeRole API.

## Obtain and transfer the role STS token and access OSS {#section_05 .section}

The procedure for an app to obtain a role STS token and use it to call the OSS API is illustrated in the following figure.

![Procedure](images/14407_en-US.png "Procedure")

The appServer uses the AccessKey of the RAM user Appserver to call the STS API [AssumeRole](../../../../../reseller.en-US/API Reference (STS)/Operation interfaces/AssumeRole.md).

**Note:** The AccessKey for the appServer must be configured.

The following is an example of how to use aliyuncli to call the AssumeRole API:

```
$ aliyuncli sts AssumeRole --RoleArn acs:ram::11223344:role/oss-readonly --RoleSessionName client-001
 {
     "AssumedRoleUser": {
         "AssumedRoleId": "391578752573972854:client-001", 
         "Arn": "acs:ram::11223344:role/oss-readonly/client-001"
     }, 
     "Credentials": {
         "AccessKeySecret": "93ci2umK1QKNEja6WGqi1Ba7Q2Fv9PwxZqtVF2VynUvz", 
         "SecurityToken": "CAES6AIIARKAAUiwSHpkD3GXRMQk9stDr3YSVbyGqanqkS+fPlEEkjZ+dlgFnGdCI2PV93jksole8ijH8dHJrHRA5JA1YCGsfX5hrzcNM37Vr4eVdWFVQhoCw0DXBpHv//ZcITp+ELRr4MHsnyGiErnDsXLkI7q/sbuWg6PACZ/jzQfEWQb/f7Y1Gh1TVFMuRjEzR2pza1hUamszOGRCWTZZeEp0WEFaayISMzkxNTc4NzUyNTczOTcyODU0KgpjbGllbnQtMDAxMKT+lIHBKjoGUnNhTUQ1QkoKATEaRQoFQWxsb3cSGwoMQWN0aW9uRXF1YWxzEgZBY3Rpb24aAwoBKhIfCg5SZXNvdXJjZUVxdWFscxIIUmVzb3VyY2UaAwoBKkoFNDMyNzRSBTI2ODQyWg9Bc3N1bWVkUm9sZVVzZXJgAGoSMzkxNTc4NzUyNTczOTcyODU0cgllY3MtYWRtaW544Mbewo/26AE=", 
         "Expiration": "2016-01-13T15:02:37Z", 
         "AccessKeyId": "STS.F13GjskXTjk38dBY6YxJtXAZk"
     }, 
     "RequestId": "E1779AAB-E7AF-47D6-A9A4-53128708B6CE"
 }
```

## Restrict STS token permissions {#section_06 .section}

1.  After calling the AssumeRole API, you can grant fine-grained permissions to the STS token.

    Specifically, if you do not specify a policy when calling the AssumeRole API, the STS token has all permissions of `oss-readonly`. To solve this issue, you can specify a policy to further restrict the permissions of the STS token, for example, only allow the STS token to access `sample-bucket/2015/01/01/*.jpg`. The following is an example:

    ```
    $ aliyuncli sts AssumeRole --RoleArn acs:ram::11223344:role/oss-readonly --RoleSessionName client-002 --Policy "{\"Version\":\"1\", \"Statement\": [{\"Effect\":\"Allow\", \"Action\":\"oss:GetObject\", \"Resource\":\"acs:oss:*:*:sample-bucket/2015/01/01/*.jpg\"}]}"
    {
       "AssumedRoleUser": {
           "AssumedRoleId": "391578752573972854:client-002", 
           "Arn": "acs:ram::11223344:role/oss-readonly/client-002"
       }, 
       "Credentials": {
           "AccessKeySecret": "28Co5Vyx2XhtTqj3RJgdud4ntyzrSNdUvNygAj7xEMow", 
           "SecurityToken": "CAESnQMIARKAASJgnzMzlXVyJn4KI+FsysaIpTGm8ns8Y74HVEj0pOevO8ZWXrnnkz4a4rBEPBAdFkh3197GUsprujsiU78FkszxhnQPKkQKcyvPihoXqKvuukrQ/Uoudk31KAJEz5o2EjlNUREcxWjRDRSISMzkxNTc4NzUyNTczOTcyODU0KgpjbGllbnQtMDAxMKmZxIHBKjoGUnNhTUQ1Qn8KATEaegoFQWxsb3cSJwoMQWN0aW9uRXF1YWxzEgZBY3Rpb24aDwoNb3NzOkdldE9iamVjdBJICg5SZXNvdXJjZUVxdWFscxIIUmVzb3VyY2UaLAoqYWNzOm9zczoqOio6c2FtcGxlLWJ1Y2tldC8yMDE1LzAxLzAxLyouanBnSgU0MzI3NFIFMjY4NDJaD0Fzc3VtZWRSb2xlVXNlcmAAahIzOTE1Nzg3NTI1NzM5NzI4NTRyCWVjcy1hZG1pbnjgxt7Cj/boAQ==", 
           "Expiration": "2016-01-13T15:03:39Z", 
           "AccessKeyId": "STS.FJ6EMcS1JLZgAcBJSTDG1Z4CE"
       }, 
       "RequestId": "98835D9B-86E5-4BB5-A6DF-9D3156ABA567"
    }
    ```

    **Note:** The default validity period of the STS token is 3600 seconds \(maximum limit\). You can use the DurationSeconds parameter to limit the STS token expiration time.

2.  The appServer obtains and parses the credentials.
    -   The appServer obtains the AccessKeyId, AccessKeySecret, and STS token from the credentials returned by the AssumeRole API.
    -   The STS token validity period is determined. If the application requires a longer validity period, the appServer must re-issue a new STS token, for example, issue one STS token every 1800 seconds.
3.  The appServer securely transfers the STS token to the app.
4.  The app uses the STS token to directly access APIs of Alibaba Cloud services \(such as OSS\).

    The following is an example of how to use aliyuncli and an STS token to access an OSS object \(here, the STS token is issued to client-002\):

    ```
    
    Configure the STS token syntax: aliyuncli oss Config --host  --accessid  --accesskey  --sts_token 
    $ aliyuncli oss Config --host oss.aliyuncs.com --accessid STS.FJ6EMcS1JLZgAcBJSTDG1Z4CE --accesskey 28Co5Vyx2XhtTqj3RJgdud4ntyzrSNdUvNygAj7xEMow --sts_token CAESnQMIARKAASJgnzMzlXVyJn4KI+FsysaIpTGm8ns8Y74HVEj0pOevO8ZWXrnnkz4a4rBEPBAdFkh3197GUsprujsiU78FkszxhnQPKkQKcyvPihoXqKvuukrQ/Uoudk31KAJEz5o2EjlNUREcxWjRDRSISMzkxNTc4NzUyNTczOTcyODU0KgpjbGllbnQtMDAxMKmZxIHBKjoGUnNhTUQ1Qn8KATEaegoFQWxsb3cSJwoMQWN0aW9uRXF1YWxzEgZBY3Rpb24aDwoNb3NzOkdldE9iamVjdBJICg5SZXNvdXJjZUVxdWFscxIIUmVzb3VyY2UaLAoqYWNzOm9zczoqOio6c2FtcGxlLWJ1Y2tldC8yMDE1LzAxLzAxLyouanBnSgU0MzI3NFIFMjY4NDJaD0Fzc3VtZWRSb2xlVXNlcmAAahIzOTE1Nzg3NTI1NzM5NzI4NTRyCWVjcy1hZG1pbnjgxt7Cj/boAQ==
    access OSS objects
    $ aliyuncli oss Get oss://sample-bucket/2015/01/01/grass.jpg grass.jpg
    ```


## What to do next {#section_07 .section}

For more information, see:

-   [Set up direct data transfer for mobile apps](../../../../../reseller.en-US/Best Practices/Application server/Set up direct data transfer for mobile apps.md)
-   [Permission control](../../../../../reseller.en-US/Best Practices/Application server/Permission control.md)
-   [Set up data callback for mobile apps](../../../../../reseller.en-US/Best Practices/Application server/Set up data callback for mobile apps.md)
-   [STS temporary access authorization](../../../../../reseller.en-US/Developer Guide/Hide/Access control/STS temporary access authorization.md)

