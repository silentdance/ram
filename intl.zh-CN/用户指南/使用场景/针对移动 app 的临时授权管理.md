# 针对移动 app 的临时授权管理 {#concept_tdn_n2k_xdb .concept}

本文介绍了具体场景下，使用 RAM 角色令牌对移动 app 客户端进行临时授权的解决方案与操作步骤。

## 场景描述 {#section_dqp_42k_xdb .section}

企业 A 开发了一款移动 app，并购买了 OSS 服务。移动 app 需要上传数据到 OSS（或从 OSS 下载数据）；移动 app 运行在用户自己的终端设备上，这些设备并不受 A 的控制。

-   A 不希望所有 app 都通过 appServer 来进行数据中转，而希望让 app 能直连 OSS 上传/下载数据。
-   出于安全考虑，A 不能将访问密钥保存到移动 app 中。
-   A 希望将安全风险控制到最小，比如，每个移动 app 直连 OSS 时都必须使用最小权限的访问令牌，而且访问时效也要很短（比如 30 分钟）。

## 需求分析 {#section_fqp_42k_xdb .section}

对以上场景的需求分析如下：

-   移动 app 需要直传数据到 OSS，不需要经过数据 proxy。
-   不能将 AK 交给移动 app，因为移动设备归属于您的用户来控制（并不可信），最佳实践是使用带过期时间的访问令牌。
-   每个移动 app 的访问权限都可以限制，支持到 OSS 对象的粒度。

## 解决方案 {#section_hqp_42k_xdb .section}

针对以上需求，**使用 RAM 角色令牌对 OSS 做临时访问授权**。

-   云账号 A 在 RAM 中创建一个角色，给角色授予合适的权限，并允许 appServer（以 RAM 用户身份运行）使用该角色。操作流程见[创建角色、用户及授权](#section_jqp_42k_xdb)。

-   当 app 需要直连 OSS 上传/下载数据时，appServer 可以扮演角色（调用 STS AssumeRole），获取角色的一个临时安全令牌（STS-Token）并传送给 app，app 就可以使用临时安全令牌直接访问 OSS API。操作流程见[获取、传递角色令牌及访问](#section_sqp_42k_xdb)。

-   appServer 可以在使用角色时进一步限制临时安全令牌的资源操作权限，以更精细地控制每个 app 的权限。操作方法见 [限制 STS-Token 权限](#ul_zqp_42k_xdb)。


## 创建角色、用户及授权 {#section_jqp_42k_xdb .section}

假设云账号 A 的 AccountID 为：11223344。为 appServer 创建角色、用户，并配置权限的操作流程如下：

1.  云账号 A 创建用户角色（假设角色名为 oss-readonly），并选择**当前云账号**作为受信云账号，即只允许云账号 A 下的 RAM 用户来扮演该角色。具体操作请参考[角色](intl.zh-CN/用户指南/身份管理/角色.md)。

    角色创建成功后，在角色详情中可以查看到该角色的基本信息：

    -   角色的全局名称 Arn 如下：

        ```
        acs:ram::11223344:role/oss-readonly
        ```

    -   角色的信任策略（只允许 云账号 A 下的 RAM 角色来扮演角色）如下：

        ```
        {
        "Statement": [
        {
         "Action": "sts:AssumeRole",
         "Effect": "Allow",
         "Principal": {
           "RAM": [
             "acs:ram::11223344:root"// 当角色为用户角色时，此处固定是root
           ]
         }
        }
        ],
        "Version": "1"
        }
        ```

2.  云账号 A 给角色授权，向用户角色（oss-readonly）[附加只读访问 OSS 的权限](intl.zh-CN/用户指南/授权管理/授权.md)（AliyunOSSReadOnlyAccess）。
3.  云账号 A 为 appServer 创建 RAM 用户身份（假设用户名为 appserver），并为该 RAM 用户
    -   [创建 AccessKey](intl.zh-CN/用户指南/身份管理/用户.md)，即许可 RAM 用户（appserver）调用 API。
    -   [附加调用 STS AssumeRole 接口的权限](intl.zh-CN/用户指南/授权管理/授权.md)（AliyunSTSAssumeRoleAccess），即许可 RAM 用户（appserver）去扮演角色。

## 获取、传递角色令牌及访问 {#section_sqp_42k_xdb .section}

appClient 获取并使用角色令牌调用 OSS API 的操作示意图如下：

![](images/3631_zh-CN.png "操作流程")

操作流程如下：

1.  appServer 使用 RAM 用户（appserver）的 AccessKey调用STS[AssumeRole](../../../../intl.zh-CN/API参考/API 参考（STS）/操作接口/AssumeRole.md)。 使用 aliyuncli 来调用 AssumeRole 的命令示例如下：

    **说明：** 必须配置 appServer 的 AccessKey，而不允许是主账号 A 的 AccessKey。

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

    **限制 STS-Token 权限**

    -   上述 AssumeRole 调用时没有指定 Policy 参数，意味着该 STS-Token 拥有 oss-readonly 的所有权限。
    -   如果需要对 STS-Token 的权限进一步限制，比如只允许访问 `sample-bucket/2015/01/01/*.jpg`，那么可以通过 Policy 参数对 STS-Token 的权限进一步限制。例如：

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

    此外：

    -   上述 STS-Token 的默认过期时间为 3600 秒，用户还可以通过 DurationSeconds 参数来限制 STS-Token 的过期时间（最长不超过 3600 秒）。
2.  appServer 获取并解析 Credentials。
    -   appServer 从 AssumeRole 返回的 Credentials 中获取 AccessKeyId、AccessKeySecret 和 SecurityToken。
    -   考虑到 STS-Token 过期时间较短，如果应用业务需要一个较长的过期时间，需要 appServer 重新颁发新的 STS-Token（比如每隔 1800 秒颁发一次 STS-Token）。
3.  appServer 将 STS-Token 安全传递给 appClient。
4.  appClient 使用 STS-Token 直接访问云服务的 API（比如 OSS）。下面是 aliyuncli 使用 STS-Token 访问 OSS 对象的操作命令（颁发给 client-002 的 STS-Token）：

    ```
    
    配置STS-Token语法：aliyuncli oss Config --host  --accessid  --accesskey  --sts_token 
    $ aliyuncli oss Config --host oss.aliyuncs.com --accessid STS.FJ6EMcS1JLZgAcBJSTDG1Z4CE --accesskey 28Co5Vyx2XhtTqj3RJgdud4ntyzrSNdUvNygAj7xEMow --sts_token CAESnQMIARKAASJgnzMzlXVyJn4KI+FsysaIpTGm8ns8Y74HVEj0pOevO8ZWXrnnkz4a4rBEPBAdFkh3197GUsprujsiU78FkszxhnQPKkQKcyvPihoXqKvuukrQ/Uoudk31KAJEz5o2EjlNUREcxWjRDRSISMzkxNTc4NzUyNTczOTcyODU0KgpjbGllbnQtMDAxMKmZxIHBKjoGUnNhTUQ1Qn8KATEaegoFQWxsb3cSJwoMQWN0aW9uRXF1YWxzEgZBY3Rpb24aDwoNb3NzOkdldE9iamVjdBJICg5SZXNvdXJjZUVxdWFscxIIUmVzb3VyY2UaLAoqYWNzOm9zczoqOio6c2FtcGxlLWJ1Y2tldC8yMDE1LzAxLzAxLyouanBnSgU0MzI3NFIFMjY4NDJaD0Fzc3VtZWRSb2xlVXNlcmAAahIzOTE1Nzg3NTI1NzM5NzI4NTRyCWVjcy1hZG1pbnjgxt7Cj/boAQ==
    访问OSS对象
    $ aliyuncli oss Get oss://sample-bucket/2015/01/01/grass.jpg grass.jpg
    ```


## 更多参考 {#section_lfc_nfk_xdb .section}

关于移动应用直传场景，可参考以下文档：

-   [快速搭建移动应用直传服务](../../../../intl.zh-CN/最佳实践/移动应用端直传实践/快速搭建移动应用直传服务.md)
-   [搭建应用服务器之STS Policy](../../../../intl.zh-CN/最佳实践/移动应用端直传实践/权限控制.md)
-   [快速搭建移动应用上传回调服务](../../../../intl.zh-CN/最佳实践/移动应用端直传实践/快速搭建移动应用上传回调服务.md)
-   [STS临时授权访问](../../../../intl.zh-CN/最佳实践/权限管理/STS临时授权访问.md)

