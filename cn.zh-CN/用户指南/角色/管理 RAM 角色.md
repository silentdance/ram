# 管理 RAM 角色 {#concept_xvr_ftf_xdb .concept}

使用控制台或 API 都可以扮演 RAM 角色。创建 RAM 角色后，通过对角色进行授权可以访问相应的资源。

**说明：** 如果没有特别说明，文中出现的**角色**都是指 **RAM 角色**。

## 创建 RAM 角色的前提条件 {#section_xy3_vhk_pgb .section}

使用云账号（或拥有 RAM 操作权限的 RAM 用户）登录到 [RAM 控制台](https://ram.console.aliyun.com/)。

## 创建 RAM 角色 {#section_02 .section}

-   创建可信实体为**阿里云账号**的角色。
    1.  单击 **RAM 角色管理** \> **新建 RAM 角色** 。
    2.  选择可信实体类型为**阿里云账号**，单击**下一步**。
    3.  输入角色名称，填写备注（可选），并选择云账号后，单击**完成**。
        -   若创建的角色是给自己名下的 RAM 用户使用（例如授权移动 app 客户端直接操作 OSS 资源），请选择**当前云账号**为受信云账号。
        -   若创建的角色是给其他云账号名下的 RAM 用户使用（例如跨账号的资源授权），请选择**其他云账号**，并填写其他云账号的 ID。
-   创建可信实体为**阿里云服务**的角色。
    1.  单击 **RAM 角色管理** \> **新建 RAM 角色** 。
    2.  选择可信实体类型为**阿里云服务**，单击**下一步**。
    3.  输入角色名称，填写备注（可选），并选择受信服务后，单击**完成**。可用的服务角色举例如下：

        -   多媒体转码服务：用于将 OSS Bucket 设置为 MTS 任务的数据源时，创建以 MTS 为受信服务的角色，并使用 MTS 服务扮演该角色访问 OSS 中的数据。
        -   归档存储服务：用于将 OSS Bucket 设置为归档存储服务的数据源时，创建以归档存储为受信服务的角色，并使用归档存储服务扮演该角色访问 OSS 中的数据。
        -   日志服务：用于将日志服务收集的日志导入 OSS 时，创建以日志服务为受信服务的角色，并使用日志服务扮演该角色将数据写入 OSS。
        -   API 网关服务：用于将函数服务设置为 API 网关的后端服务时，创建以 API 网关服务为受信服务的角色，并使用 API 网关扮演该角色调用函数服务。
        -   云服务器：用于授权 ECS 服务访问您在其他云服务中的云资源。
        **说明：** 更多受信服务请以实际界面为准。

-   创建可信实体为**身份提供商**的角色。
    1.  单击 **RAM 角色管理** \> **新建 RAM 角色**。
    2.  选择可信实体类型为**身份提供商**，单击**下一步**。
    3.  输入角色名称，填写备注（可选），并选择身份提供商。
    4.  查看限制条件，单击**完成**。

        **说明：** 目前只支持一个条件关键字`saml:recipient`（必选且不能修改），对应 SAML 断言中的 Subject - SubjectConfirmation - SubjectConfirmationData 元素的`Recipient`属性值。限定条件的取值必须为`https://signin.alibabacloud.com/saml-role/sso`。


## 编辑 RAM 角色 {#section_kng_xxg_chb .section}

在 **RAM 角色管理**页面找到新创建的角色，单击其角色名称可以查看该角色的基本信息。在基本信息页面，单击**信任策略管理** \> **修改信任策略** ，即可通过修改 Principal 的内容来改变允许扮演该角色的可信实体。策略中的 Principal 部分决定了允许扮演该角色的可信实体：

1.  若 Principal 中有 RAM 字段，表示该角色的可信实体类型为阿里云账号，可以被受信云账号下被授权的 RAM 用户扮演。举例如下：

    ``` {#codeblock_lex_06t_q5e}
    
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

    上述策略表示，该角色可以被阿里云账号（AccountID=123456789012\*\*\*\*）下被授权的任何 RAM 用户扮演。若您将 Principal 中的内容更改如下，则表示该角色可以被阿里云账号（AccountID=123456789012\*\*\*\*）下的用户 testuser 扮演。

    ``` {#codeblock_i7v_bk6_20d}
    
                "Principal": {
                    "RAM": [
                        "acs:ram::123456789012****:user/testuser"
    						
    ```

2.  若 Principal 中有 Service 字段，表示该角色的可信实体类型为阿里云服务，可以被受信云服务扮演。举例如下：

    ``` {#codeblock_ulr_uxk_ykk}
    
    {
    
        "Statement": [
    
            {
                "Action": "sts:AssumeRole",
                "Effect": "Allow",
                "Principal": {
                    "Service": [
                        "ecs.aliyuncs.com"
                    ]
                }
            }
        ],
        "Version": "1"
    }
    ```

    上述策略表示，该角色可以被当前云账号下的 ECS 服务扮演。

3.  若 Principal 中有 Federated 字段，表示该角色的可信实体类型为身份提供商，可以被受信身份提供商下的用户扮演。举例如下：

    ``` {#codeblock_myr_922_m7u}
    
    {
    
        "Statement": [
    
            {
                "Action": "sts:AssumeRole",
                "Effect": "Allow",
                "Principal": {
                    "Federated": [
                        "acs:ram::123456789012****:saml-provider/testprovider"
                    ]
                },
                "Condition":{
                    "StringEquals":{
                        "saml:recipient":"https://signin.alibabacloud.com/saml-role/sso"
                    }
                }
            }
        ],
        "Version": "1"
    }
    ```

    上述策略表示，该角色可以被当前云账号（AccountID=123456789012\*\*\*\*）中的身份提供商 testprovider 下的用户扮演。


## 使用 RAM 角色 {#section_05 .section}

**阿里云服务**的角色只能被受信云服务扮演，**阿里云账号**的角色可以通过 RAM 用户身份来扮演，**身份提供商**的角色可以被可信身份提供商下的用户来扮演。本章节所介绍的 RAM 角色使用方式，均只针对受信实体类型为阿里云账号的 RAM 角色。

1.  创建一个 RAM 用户，并为该用户创建 AccessKey 或设置登录密码。
2.  给该 RAM 用户授权，授权时添加系统权限策略：AliyunSTSAssumeRoleAccess（或使用 STS 的自定义策略）。

**说明：** 为了安全起见，阿里云不允许受信云账号以自己的身份扮演角色。必须使用 RAM 用户进行角色扮演。

根据使用方式的不同，RAM 用户可以使用控制台或 API 扮演 RAM 角色：

-   使用控制台扮演 RAM 角色

    如果一个实体用户想使用被赋予的某个 RAM 角色，该实体用户必须先以自己身份登录，然后执行**切换身份**操作将自己从实体身份切换到角色身份。

    1.  RAM 用户登录 **RAM 控制台**。
    2.  将鼠标悬停在右上角头像的位置，单击**切换身份**。
    3.  进入**角色切换**的页面，填写相应账号别名和角色名，单击**切换**。

        **说明：** 

        -   切换成功后，用户将以角色身份访问控制台。此时控制台右上角将显示角色身份（即当前身份）和登录身份。
        -   切换成功后，用户将只能执行该角色身份被授权的所有操作，而登录时实体身份所对应的访问权限被隐藏。
    4.  在扮演角色身份时，选择**返回登录身份**可以切换回登录身份。

        **说明：** 此时将拥有实体身份所对应的访问权限，而不再拥有角色身份所拥有的权限。

-   使用 API 扮演 RAM 角色

    当 RAM 用户被授予 AssumeRole 权限之后，可以使用其 AccessKey 调用安全令牌服务（STS）的 AssumeRole 接口，以获取某个角色的临时安全令牌，然后使用临时安全令牌访问云资源的 API 接口。

    关于 AssumeRole API 的调用方法，请参考 [AssumeRole](../../../../intl.zh-CN/API 参考（STS）/操作接口/AssumeRole.md)。


## 后续操作 {#section_qgj_y1k_pgb .section}

成功创建角色后，角色没有任何权限，单击**为角色授权**可直接为该角色授权。详情请参考 [RAM 授权](intl.zh-CN/用户指南/权限策略/RAM 授权.md#)。

