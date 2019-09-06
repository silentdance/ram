# 使用 RAM 对对象存储 OSS 进行权限管理 {#concept_ohn_ypx_ydb .concept}

本文介绍了通过 RAM 的权限管理功能，创建相应的权限策略，从而对对象存储 OSS 进行权限管理，以满足 RAM 用户操作 OSS 的多种需求。

## 基本信息 {#section_x3f_rzk_5gb .section}

使用 RAM 对 OSS 进行权限管理前，需先了解几个常用的权限策略。

|权限策略|描述|
|:---|:-|
|AliyunOSSFullAccess|为 RAM 用户授予 OSS 的完全管理权限。|
|AliyunOSSReadOnlyAccess|为 RAM 用户授予 OSS 的只读访问权限。|

**说明：** 查看 OSS 的权限定义，请参考 OSS 产品文档中的[权限控制概述](../../../../intl.zh-CN/开发指南/权限控制/权限控制概述.md#)。

## 将自定义策略授权给 RAM 用户的操作步骤 {#section_03 .section}

1.  根据下述 [OSS 授权样例](#section_mlc_ww2_vgb)创建相应的自定义策略。

    详情请参考：[创建自定义策略](../../../../intl.zh-CN/用户指南/权限策略/自定义策略/创建自定义策略.md#)。

2.  找到创建好的权限策略，单击其**权限策略名称**。
3.  单击**引用记录** \> **新增授权**。
4.  **被授权主体**处输入需要授权的用户名称或 ID。
5.  单击**确定**。

    **说明：** 您也可以直接对**用户**或**用户组**授予创建好的权限策略，详情请参考：[为 RAM 用户授权](../../../../intl.zh-CN/用户指南/用户/为RAM用户授权.md#)和[为用户组授权](../../../../intl.zh-CN/用户指南/用户组/为用户组授权.md#)。


## OSS 授权样例 {#section_mlc_ww2_vgb .section}

-   示例 1：授权 RAM 用户完全管理某个 Bucket 的权限。

    ``` {#codeblock_qgu_4s5_kig}
    {
        "Version": "1",
        "Statement": [
            {
                "Effect": "Allow",
                "Action": "oss:*",
                "Resource": [
                    "acs:oss:*:*:myphotos",
                    "acs:oss:*:*:myphotos/*"
                ]
            }
        ]
    }
    ```

-   示例 2：授权 RAM 用户列出并读取一个 Bucket 中的资源。
    -   授权 RAM 用户通过 OSS SDK 或 OSS 命令行工具列出并读取一个 Bucket 中的资源。Bucket 名称为：`myphotos`。

        ``` {#codeblock_zy7_sg0_ft0}
        {
            "Version": "1",
            "Statement": [
                {
                    "Effect": "Allow",
                    "Action": "oss:ListObjects",
                    "Resource": "acs:oss:*:*:myphotos"
                },
                {
                    "Effect": "Allow",
                    "Action": "oss:GetObject",
                    "Resource": "acs:oss:*:*:myphotos/*"
                }
            ]
        }
        ```

    -   授权 RAM 用户能够通过 OSS 控制台进行操作。

        **说明：** 用户登录 OSS 控制台时，为了操作体验的优化，OSS控制台会额外调用`ListBuckets`操作，以及`GetBucketAcl`和`GetObjectAcl`，以确定 bucket 属性是公开还是私有。

        ``` {#codeblock_1gm_yz1_gg8}
        {
            "Version": "1",
            "Statement": [
                {
                    "Effect": "Allow",
                    "Action": [
                              "oss:ListBuckets",
                              "oss:GetBucketStat",
                              "oss:GetBucketInfo",
                              "oss:GetBucketAcl" 
                              ],    
                    "Resource": "acs:oss:*:*:*"
                },
                {
                    "Effect": "Allow",
                    "Action": [
                        "oss:ListObjects",
                        "oss:GetBucketAcl"
                    ],
                    "Resource": "acs:oss:*:*:myphotos"
                },
                {
                    "Effect": "Allow",
                    "Action": [
                        "oss:GetObject",
                        "oss:GetObjectAcl"
                    ],
                    "Resource": "acs:oss:*:*:myphotos/*"
                }
            ]
        }
        ```

-   示例 3：授权 RAM 用户通过特定的 IP 地址访问 OSS。
    -   在`Allow`授权中增加 IP 限制：允许通过`192.168.0.0/16`, `172.12.0.0/16`两个 IP 段读取`myphotos`中的信息。

        ``` {#codeblock_zty_vu1_dmt}
        {
            "Version": "1",
            "Statement": [
                {
                    "Effect": "Allow",
                    "Action": [
                              "oss:ListBuckets",
                              "oss:GetBucketStat",
                              "oss:GetBucketInfo",
                              "oss:GetBucketAcl" 
                              ], 
                    "Resource": [
                        "acs:oss:*:*:*"
                    ]
                },
                {
                    "Effect": "Allow",
                    "Action": [
                        "oss:ListObjects",
                        "oss:GetObject"
                    ],
                    "Resource": [
                        "acs:oss:*:*:myphotos",
                        "acs:oss:*:*:myphotos/*"
                    ],
                    "Condition":{
                        "IpAddress": {
                            "acs:SourceIp": ["192.168.0.0/16", "172.12.0.0/16"]
                        }
                    }
                }
            ]
        }
        ```

    -   在`Deny`授权中增加 IP 限制：如果源 IP 不在`192.168.0.0/16`中，则禁止对 OSS 执行任何操作。

        ``` {#codeblock_kem_12e_9a3}
        {
            "Version": "1",
            "Statement": [
                {
                    "Effect": "Allow",
                    "Action": [
                              "oss:ListBuckets",
                              "oss:GetBucketStat",
                              "oss:GetBucketInfo",
                              "oss:GetBucketAcl" 
                              ], 
                    "Resource": [
                        "acs:oss:*:*:*"
                    ]
                },
                {
                    "Effect": "Allow",
                    "Action": [
                        "oss:ListObjects",
                        "oss:GetObject"
                    ],
                    "Resource": [
                        "acs:oss:*:*:myphotos",
                        "acs:oss:*:*:myphotos/*"
                    ]
                },
                {
                    "Effect": "Deny",
                    "Action": "oss:*",
                    "Resource": [
                        "acs:oss:*:*:*"
                    ],
                    "Condition":{
                        "NotIpAddress": {
                            "acs:SourceIp": ["192.168.0.0/16"]
                        }
                    }
                }
            ]
        }
        ```

        **说明：** 因为 Policy 的鉴权规则是 Deny 优先，所以访问者从`192.168.0.0/16`以外的 IP 地址访问`myphotos`中的内容时，OSS 服务会提示没有权限。

-   示例 4：OSS 目录级别的授权。

    假设用于存放照片的 Bucket：myphotos。这个 Bucket 下有一些目录，代表照片的拍摄地，每个拍摄地目录下又有年份子目录。

    ``` {#codeblock_a2h_agq_ltn}
    myphotos[Bucket]
      ├── beijing
      │   ├── 2014
      │   └── 2015
      ├── hangzhou
      │   ├── 2013
      │   ├── 2014
      │   └── 2015 //授予此目录只读权限
      └── qingdao
          ├── 2014
          └── 2015
    ```

    若要授权 RAM 用户访问`myphotos/hangzhou/2015/`目录的只读权限。目录级别的授权属于授权的高级功能，根据使用场景不同，授权策略的复杂程度也不同，以下几种场景可供参考。

    -   场景 1：授予 RAM 用户读取文件内容的权限，不需要列出文件的权限。

        RAM 用户知道文件的完整路径，可以使用完整的文件路径直接去读取文件内容，通常会将这样的权限授予应用程序。

        ``` {#codeblock_ryw_93w_j8u}
        {
            "Version": "1",
            "Statement": [
                {
                    "Effect": "Allow",
                    "Action": [
                        "oss:GetObject"
                    ],
                    "Resource": [
                        "acs:oss:*:*:myphotos/hangzhou/2015/*"
                    ]
                }
            ]
        }
        ```

    -   场景 2：授权 RAM 用户使用 OSS 命令行工具访问目录`myphotos/hangzhou/2015/`并列出目录中文件的权限。

        RAM 用户不清楚目录中有哪些文件，可以使用 OSS 命令行工具或 API 直接获取目录信息，通常会将这样的权限授予软件开发者。

        此场景需要新增`ListObjects`的权限。

        ``` {#codeblock_807_onv_q70}
        {
            "Version": "1",
            "Statement": [
                {
                    "Effect": "Allow",
                    "Action": [
                        "oss:GetObject"
                    ],
                    "Resource": [
                        "acs:oss:*:*:myphotos/hangzhou/2015/*"
                    ]
                },
                {
                    "Effect": "Allow",
                    "Action": [
                        "oss:ListObjects"
                    ],
                    "Resource": [
                        "acs:oss:*:*:myphotos"
                    ],
                    "Condition":{
                        "StringLike":{
                            "oss:Prefix":"hangzhou/2015/*"
                        }
                    }
                }
            ]
        }
        ```

    -   场景 3： 授予 RAM 用户使用 OSS 控制台访问目录。

        RAM 用户使用可视化的 OSS 客户端访问目录`myphotos/hangzhou/2015/`，可视化的客户端类似Windows文件管理器，RAM 用户可以从根目录开始，一层一层的进入要访问的目录，此场景是最易用的场景。

        此场景需要新增以下权限：

        -   列出所有`Bucket`的权限
        -   列出`myphotos`下目录的权限。
        -   列出`myphotos/hangzhou`下的目录的权限。
        ``` {#codeblock_pyy_it4_vi1}
        {
            "Version": "1",
            "Statement": [
                {
                    "Effect": "Allow",
                    "Action": [
                              "oss:ListBuckets",
                              "oss:GetBucketStat",
                              "oss:GetBucketInfo",
                              "oss:GetBucketAcl" 
                              ], 
                    "Resource": [
                        "acs:oss:*:*:*"
                    ]
                },
                {
                    "Effect": "Allow",
                    "Action": [
                        "oss:GetObject",
                        "oss:GetObjectAcl"
                    ],
                    "Resource": [
                        "acs:oss:*:*:myphotos/hangzhou/2015/*"
                    ]
                },
                {
                    "Effect": "Allow",
                    "Action": [
                        "oss:ListObjects"
                    ],
                    "Resource": [
                        "acs:oss:*:*:myphotos"
                    ],
                    "Condition": {
                        "StringLike": {
                            "oss:Delimiter": "/",
                            "oss:Prefix": [
                                "",
                                "hangzhou/",
                                "hangzhou/2015/*"
                            ]
                        }
                    }
                }
            ]
        }
        ```


