# Use the RAM role token to control temporary authorization access for mobile apps {#concept_tdn_n2k_xdb .concept}

This document describes how to use the RAM role token to control temporary authorization access for mobile apps in specific scenarios.

## Scenario description {#section_dqp_42k_xdb .section}

Assume that an enterprise A has developed a mobile app and has bought OSS for it. The mobile app must upload and download data to and from OSS. Because the mobile app runs on user devices, these devices are out of A’s control.

-   Enterprise A does not want to allow all apps to use the AppServer to transmit data. Instead, enterprise A wants the apps to directly upload and download data to and from OSS.
-   For security reasons, enterprise A cannot save the AccessKey in the app.
-   Enterprise A also wants to minimize its security risks by, for example, giving each app an access token with the minimum permissions that the app needs to connect to OSS and restricting the access duration to a specified period of time \(such as 30 minutes\).

## Requirement analysis {#section_fqp_42k_xdb .section}

The analysis of the preceding scenarios is as follows:

-   The mobile app needs to directly transmit data to OSS, without using a data proxy.
-   Enterprise A cannot give an AccessKey to the mobile app because the mobile devices are under the control of A’s users.
-   The access permissions of each mobile app must be restricted to OSS object granularity.

## Solution {#section_hqp_42k_xdb .section}

In response to the above requirements, the RAM role token is used to authorize temporary access to the OSS.

-   Account A creates a role in RAM and assigns appropriate permissions to the role, and allows the appServer \(logs on as the RAM user\) to use this role. For the operation procedure, see [Create roles, users, and authorizations](#section_jqp_42k_xdb).

-   When the app needs to upload or download data to OSS through direct connection, the appServer can assume a role \(calling STS AssumeRole\) to get a temporary security token \(STS-Token\) for the role and transfer it to the app. Then, the app can use the temporary security token to access the OSS API directly. For the operation procedure, see [Get and pass the role token](#section_sqp_42k_xdb).

-   The appServer can further limit the resource operation permissions of the temporary security token while using the role, to control the permissions of each app in greater detail. For the operation procedure, see [Restrict the STS-Token permissions](#ul_zqp_42k_xdb).


## Create roles, users, and authorizations {#section_jqp_42k_xdb .section}

Assume that account A's account D is: 11223344. The process for creating roles, users, and configuring permissions for the appServer is as follows:

1.  Account A creates a user role \(assuming the role is named oss-readonly\) and selects the **Current Alibaba Cloud Account** as the trusted account. That is, only the RAM users under account A are allowed to assume this role. For the operation procedure, see [Roles](https://www.alibabacloud.com/help/doc-detail/28649.htm).

    After creating the role, enterprise A can get the role information on the details page. 

    -   In this example, the role’s global name ARN  is:

        ```
        acs:ram::11223344:role/oss-readonly
        ```

    -   The role’s policy \(only the RAM users under account A can assume this role\) is as follows:

        ```
        
        "Statement": [
        
         "Action": "sts:AssumeRole",
         "Effect": "Allow",
         "Principal": {
           "RAM": [
             "acs:ram::11223344:root"
           
         }
        
        
        "Version": "1"
        
        ```

2.  Account A adds the policy AliyunOSSReadOnlyAccess to the role oss-readonly.
3.  Account A creates a RAM user role for the  appServer \(assuming the user name is  appServer\)
    -   [and creates AccessKey](intl.en-US/User Guide/Identities/Users.md) for the RAM user. That is, the RAM user \(appserver\) is allowed to call the API.
    -   [Additionally, the permission](intl.en-US/User Guide/Authorization/Authorization.md) \(AliyunSTSAssumeRoleAccess\) of the STS AssumeRole interface is called. That is, the RAM user appserver is allowed to assume the role.

## Get and pass the role token {#section_sqp_42k_xdb .section}

The procedure for the appClient to get and use the role token to call the OSS API is as follows:

![](images/3631_en-US.png "Operation procedure")

The operation procedure is as follows:

1.  The appServer uses the AccessKey[AssumeRole](../../../../intl.en-US//Operation interface/AssumeRole.md) of the RAM user \(appserver\). The command example of using aliyuncli to call AssumeRole is as follows:

    **Note:** The AccessKey for the appServer must be configured, and the AccessKey for master account A is not allowed.

    ```
    $ aliyuncli sts AssumeRole --RoleArn acs:ram::11223344:role/oss-readonly --RoleSessionName client-001
     
         "AssumedRoleUser": {
             "AssumedRoleId": "391578752573972854:client-001", 
             "Arn": "acs:ram::11223344:role/oss-readonly/client-001"
          
         "Credentials": {
             "AccessKeySecret": "93ci2umK1QKNEja6WGqi1Ba7Q2Fv9PwxZqtVF2VynUvz", 
             "SecurityToken": "CAES6AIIARKAAUiwSHpkD3GXRMQk9stDr3YSVbyGqanqkS+fPlEEkjZ+dlgFnGdCI2PV93jksole8ijH8dHJrHRA5JA1YCGsfX5hrzcNM37Vr4eVdWFVQhoCw0DXBpHv//ZcITp+ELRr4MHsnyGiErnDsXLkI7q/sbuWg6PACZ/jzQfEWQb/f7Y1Gh1TVFMuRjEzR2pza1hUamszOGRCWTZZeEp0WEFaayISMzkxNTc4NzUyNTczOTcyODU0KgpjbGllbnQtMDAxMKT+lIHBKjoGUnNhTUQ1QkoKATEaRQoFQWxsb3cSGwoMQWN0aW9uRXF1YWxzEgZBY3Rpb24aAwoBKhIfCg5SZXNvdXJjZUVxdWFscxIIUmVzb3VyY2UaAwoBKkoFNDMyNzRSBTI2ODQyWg9Bc3N1bWVkUm9sZVVzZXJgAGoSMzkxNTc4NzUyNTczOTcyODU0cgllY3MtYWRtaW544Mbewo/26AE=", 
             "Expiration": "2016-01-13T15:02:37Z", 
             "AccessKeyId": "STS.F13GjskXTjk38dBY6YxJtXAZk"
          
         "RequestId": "E1779AAB-E7AF-47D6-A9A4-53128708B6CE"
     
    ```

    -   The Policy parameter is not specified when the AssumeRole above is called, indicating that the STS-Token has all permissions of oss-readonly.
    -   If you need to further restrict the permission of STS-Token, for example, only access to `sample-bucket/2015/01/01/*.jpg` is allowed, you can restrict the permission of STS-Token in greater detail through the Policy parameter. For example:

        ```
        $ aliyuncli sts AssumeRole --RoleArn acs:ram::11223344:role/oss-readonly --RoleSessionName client-002 --Policy "{\"Version\":\"1\", \"Statement\": [{\"Effect\":\"Allow\", \"Action\":\"oss:GetObject\", \"Resource\":\"acs:oss:*:*:sample-bucket/2015/01/01/*.jpg\"}]}"
        
           "AssumedRoleUser": {
               "AssumedRoleId": "391578752573972854:client-002", 
               "Arn": "acs:ram::11223344:role/oss-readonly/client-002"
            
           "Credentials": {
               "AccessKeySecret": "28Co5Vyx2XhtTqj3RJgdud4ntyzrSNdUvNygAj7xEMow", 
               "SecurityToken": "CAESnQMIARKAASJgnzMzlXVyJn4KI+FsysaIpTGm8ns8Y74HVEj0pOevO8ZWXrnnkz4a4rBEPBAdFkh3197GUsprujsiU78FkszxhnQPKkQKcyvPihoXqKvuukrQ/Uoudk31KAJEz5o2EjlNUREcxWjRDRSISMzkxNTc4NzUyNTczOTcyODU0KgpjbGllbnQtMDAxMKmZxIHBKjoGUnNhTUQ1Qn8KATEaegoFQWxsb3cSJwoMQWN0aW9uRXF1YWxzEgZBY3Rpb24aDwoNb3NzOkdldE9iamVjdBJICg5SZXNvdXJjZUVxdWFscxIIUmVzb3VyY2UaLAoqYWNzOm9zczoqOio6c2FtcGxlLWJ1Y2tldC8yMDE1LzAxLzAxLyouanBnSgU0MzI3NFIFMjY4NDJaD0Fzc3VtZWRSb2xlVXNlcmAAahIzOTE1Nzg3NTI1NzM5NzI4NTRyCWVjcy1hZG1pbnjgxt7Cj/boAQ==", 
               "Expiration": "2016-01-13T15:03:39Z", 
               "AccessKeyId": "STS.FJ6EMcS1JLZgAcBJSTDG1Z4CE"
            
           "RequestId": "98835D9B-86E5-4BB5-A6DF-9D3156ABA567"
        
        ```

    Additionally,

    -   the default validity period of the preceding STS-Token is 3600 seconds. You can use the DurationSeconds parameter to limit the STS-Token expiration time \(the expiration time cannot exceed 3600 seconds\).
2.  The appServer retrieves and parses the credentials.
    -   The appServer retrieves the AccessKeyId, AccessKeySecret and SecurityToken from the credentials returned by AssumeRole.
    -   Because the STS-Token validity period is relatively short, if the application requires a longer validity period, the appServer must re-issue a new STS-Token \(for example, issue one STS-Token every other 1800 seconds\).
3.  The appServer securely transmits an STS-Token to the appClient.
4.  The appClient uses the STS-Token to directly access a cloud service API \(such as OSS\). The operation commands for aliyuncli to use an STS-Token to access an OSS object are as follows \(a STS-Token is issued to client-002\):

    ```
    
    Configure STS-Token syntax: aliyuncli oss Config --host --accessid --accesskey --sts_token 
    $ aliyuncli oss Config --host oss.aliyuncs.com --accessid STS.FJ6EMcS1JLZgAcBJSTDG1Z4CE --accesskey 28Co5Vyx2XhtTqj3RJgdud4ntyzrSNdUvNygAj7xEMow --sts_token CAESnQMIARKAASJgnzMzlXVyJn4KI+FsysaIpTGm8ns8Y74HVEj0pOevO8ZWXrnnkz4a4rBEPBAdFkh3197GUsprujsiU78FkszxhnQPKkQKcyvPihoXqKvuukrQ/Uoudk31KAJEz5o2EjlNUREcxWjRDRSISMzkxNTc4NzUyNTczOTcyODU0KgpjbGllbnQtMDAxMKmZxIHBKjoGUnNhTUQ1Qn8KATEaegoFQWxsb3cSJwoMQWN0aW9uRXF1YWxzEgZBY3Rpb24aDwoNb3NzOkdldE9iamVjdBJICg5SZXNvdXJjZUVxdWFscxIIUmVzb3VyY2UaLAoqYWNzOm9zczoqOio6c2FtcGxlLWJ1Y2tldC8yMDE1LzAxLzAxLyouanBnSgU0MzI3NFIFMjY4NDJaD0Fzc3VtZWRSb2xlVXNlcmAAahIzOTE1Nzg3NTI1NzM5NzI4NTRyCWVjcy1hZG1pbnjgxt7Cj/boAQ==
    Access OSS objects
    $ aliyuncli oss Get oss://sample-bucket/2015/01/01/grass.jpg grass.jpg
    ```


## More references {#section_lfc_nfk_xdb .section}

More references to mobile app access include:

-   [Set up direct data transfer for mobile apps](https://www.alibabacloud.com/help/doc-detail/31920.htm)
-   [Construct an STS policy for an app server](https://www.alibabacloud.com/help/doc-detail/31921.htm)
-   [Set up data callback for mobile apps](https://www.alibabacloud.com/help/doc-detail/31922.htm)
-   [Authorize STS temporary access](https://www.alibabacloud.com/help/doc-detail/31935.htm)

