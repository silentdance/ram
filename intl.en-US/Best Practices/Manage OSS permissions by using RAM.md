# Manage OSS permissions by using RAM {#concept_ohn_ypx_ydb .concept}

This topic describes how to manage OSS permissions of RAM users by creating policies in RAM.

## Common policies {#section_u3g_83i_suj .section}

The following table lists some common policies that can be created in RAM to manage OSS permissions.

|Policy|Description|
|:-----|:----------|
|AliyunOSSFullAccess|Grants a RAM user full management permissions for OSS instances.|
|AliyunOSSReadOnlyAccess|Grants a RAM user read-only permission for OSS instances.|

**Note:** For more information about OSS permissions, see [Overview](../../../../reseller.en-US/Developer Guide/Access and control/Overview.md#).

## Attach custom policies to RAM users {#section_fk8_5wm_q9b .section}

1.  Create custom policies according to the subsequent OSS authorization examples.

    For more information, see [Create a custom policy](../../../../reseller.en-US/User Guide/Policies/Custom policies/Create a custom policy.md#).

2.  Locate the target policy and click the policy name.
3.  On the **References** tab, click **Grant Permission**.
4.  In the **Principal** field, enter the ID or name of the target RAM user.
5.  Click **OK**.

    **Note:** You can also attach policies to a RAM user or a RAM user group as needed. For more information, see [Grant permission to a RAM user](../../../../reseller.en-US/User Guide/RAM users/Grant permission to a RAM user.md#)and [Grant permission to a RAM user group](../../../../reseller.en-US/User Guide/RAM user groups/Grant permission to a RAM user group.md#).


## OSS authorization examples {#section_rnr_j0s_mu9 .section}

-   Example 1: As a RAM administrator, authorize a user to fully manage an OSS bucket.

    ``` {#codeblock_nvf_d4s_3zx}
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

-   Example 2: As a RAM administrator, authorize a user to list and read resources in an OSS bucket.
    -   Authorize a RAM to list and read resources in an OSS bucket by using the OSS CLI or by using OSS SDKs. The name of the OSS bucket is `myphotos`.

        ``` {#codeblock_ktc_8k3_wkj}
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

    -   Authorize a RAM user to operate on resources in the OSS console.

        **Note:** When a RAM user logs on to the OSS console, the console calls the `ListBuckets`, `GetBucketAcl`, and `GetObjectAcl` actions to check whether the bucket is public.

        ``` {#codeblock_b6h_fwa_wyx}
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

-   Example 3: As a RAM administrator, authorize a RAM user to access OSS instances by using a specified IP address.
    -   Add the following condition in the `Allow` element. This allows the IP address segments `192.168.0.0/16` and `172.12.0.0/16` to read data in `myphotos`.

        ``` {#codeblock_opj_2qy_6ch}
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

    -   Add the following condition in the `Deny` element. If the IP address of a RAM user is not within the `192.168.0.0/16` segment, the user cannot perform any operations on OSS instances.

        ``` {#codeblock_fz1_n1q_e7f}
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

        **Note:** A policy with the Deny command has a higher priority than the policy with the Allow command. Therefore, when a RAM user whose IP address is not within the `192.168.0.0/16` segment attempts to access data in `myphotos`, OSS notifies the user of having no permissions.

-   Example 4: Authorize a RAM user by OSS directory.

    You have a photo bucket named myphotos. The bucket contains directories that indicate the places where the photos were taken. Each directory contains sub-directories that indicate the years when the photos were taken.

    ``` {#codeblock_8rw_15w_4ba}
    myphotos[Bucket]
      ├── beijing
      │   ├── 2014
      │   └── 2015
      ├── hangzhou
      │   ├── 2013
      │   ├── 2014
      │   └── 2015 //Grant read-only permission on this directory to users.
      └── qingdao
          ├── 2014
          └── 2015
    ```

    You can grant read-only permission on the `myphotos/hangzhou/2015/` directory to a RAM user according to application scenarios and policy complexity. The following are examples of the application scenarios:

    -   Scenario 1: Authorize a RAM user to read files in the directory without them having to list the files.

        In this scenario, the RAM user knows the complete paths of all files and can directly read the files by using the complete paths. Generally, a software system requires permission assignment for this.

        ``` {#codeblock_u3d_z5o_uod}
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

    -   Scenario 2: Authorize a RAM user to access the `myphotos/hangzhou/2015/` directory and list files in the directory by using the OSS CLI.

        Generally, software developers require such permission assignment. The developers do not know what files are available in a directory and can use the OSS CLI or API to directly obtain the directory information.

        In this scenario, the `ListObjects` permission is required.

        ``` {#codeblock_12v_qyk_dce}
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

    -   Scenario 3: Authorize a RAM user to access the `myphotos/hangzhou/2015/` directory by using the OSS console.

        In this scenario, the RAM user uses a visual OSS client, such as Windows File Explorer, to access the `myphotos/hangzhou/2015/` directory from the root directory through levels of sub-directories.

        The following permissions are required:

        -   Permission to list all buckets
        -   Permission to list directories under `myphotos`
        -   Permission to list directories under `myphotos/hangzhou`
        ``` {#codeblock_1lz_o16_x5v}
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


