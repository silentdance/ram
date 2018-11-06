# Authorization for OSS instances {#concept_ohn_ypx_ydb .concept}

## Questions {#section_x1f_w4x_ydb .section}

-   [View OSS permission definitions](#)
-   [Assign the OSS read-only permission to a RAM user](#)
-   [Assign the full OSS management permission to a RAM user](#)
-   [Authorize a RAM user to list and read resources in a bucket](#)
-   [Apply IP address-specific access control in OSS](#)
-   [Authorization by OSS directory](#)
-   [Authorize a RAM user complete management of a bucket](#)
-   [RAM user authorized to manage a bucket notified of having no operation permissions when logging on to the OSS console](#)

## View OSS permission definitions {#section_mzy_x4x_ydb .section}

See [Access control](../../../../reseller.en-US/Developer Guide/Access and control/Access control.md#) in the OSS product document.

## Assign the OSS read-only permission to a RAM user {#section_jft_y4x_ydb .section}

Create a RAM user in the RAM console and add the system authorization policy AliyunOSSReadOnlyAccess to the user.  For more information about how to add an authorization policy, see [Authorization](../../../../reseller.en-US/User Guide/Authorization/Authorization.md).

## Assign the full OSS management permission to a RAM user {#section_fnn_z4x_ydb .section}

Add the system authorization policy AliyunOSSFullAccess to the RAM user in the RAM console. 

## Authorize a RAM user to list and read resources in a bucket {#section_jpq_1px_ydb .section}

If you need to authorize a RAM user \(such as an application that represents you\) to list and read the resources in a bucket using the OSS SDK or OSS CMD, you must create an authorization policy.Resource in, then you need to create a custom Authorization Policy to complete.

Assume that your bucket is named “myphotos”. Create the authorization policy as follows:

```
{
    "Version": "1",
    "Statement ":[
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

If you want the authorized RAM-user to perform operations on the OSS console, add the GetBucketAcl and GetObjectAcl permissions to the authorization policy. \(The console needs to call additional OSS APIs to optimize the operation experience.\) The following provides an example of the authorization policy definition that allows the RAM-user to perform operations on the OSS console:

```
{
    "Version": "1",
    "Statement ":[
        {
            "Effect": "Allow",
            "Action": "oss:ListBuckets",
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

## Apply IP address-specific access control in OSS {#section_plf_hkg_c2b .section}

Example 1: Apply IP address-specific access control using the `Allow` command

The IP address segments `42.120.88.0/24` and `42.120.66.0/24` are allowed to read the information in the myphotos directory.

```
{
    "Version": "1",
    "Statement ":[
        {
            "Sid": "To allow listing all buckets",
            "Effect": "Allow",
            "Action": [
                "oss:ListBuckets"
            ],
            "Resource": [
                "acs:oss:*:*:*"
            ]
        },
        {
            "Sid": "To allow only the users in the specified IP address segment to obtain the information in the myphotos directory",
            "Effect": "Allow",
            "Action": [
                "oss:ListObjects",
                "oss:GetObject"
            ],
            "Resource": [
                "acs:oss:*:*:myphotos",
                "acs:oss:*:*:myphotos/*"
            ],
            "Condition ":{
                "IpAddress": {
                    "acs:SourceIp": "42.120.88.0/24", "42.120.66.0/24"
                }
            }
        }
    ]
}
```

Example 2: Apply IP address-specific access control using the `Deny` command

If the IP address of a user is not within the `42.120.88.0/24` segment, the user cannot perform any OSS operations. Create an authorization policy as follows:

```
{
    "Version": "1",
    "Statement ":[
        {
            "Sid": "To allow listing all buckets",
            "Effect": "Allow",
            "Action": [
                "oss:ListBuckets"
            ],
            "Resource": [
                "acs:oss:*:*:*"
            ]
        },
        {
            "Sid": "To allow obtaining the information in the myphotos directory",
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
            "Sid": "To disallow IP addresses not in the 42.120.88.0/24 segment to access OSS",
            "Effect": "Deny",
            "Action": "oss:*",
            "Resource": [
                "acs:oss:*:*:*"
            ],
            "Condition ":{
                "NotIpAddress": {
                    "acs:SourceIp": ["42.120.88.0/24"]
                }
            }
        }
    ]
}
```

NOTE: A policy with the Deny command has a higher priority than the policy with the Allow command. \(If the accessing operation of a user meets any policy with the Deny command, the user is disallowed to access the content.\) Therefore, when a user whose IP address is not in the 42.120.88.0/24 segment attempts to access the information in the “myphotos” directory, the OSS service notifies the user of having no operation permissions.

## Authorization by OSS directory {#section_dk4_42k_c2b .section}

Authorization by directory is an advanced authorization function.

**Background**

Assume that you have a photo bucket named “myphotos”. The bucket contains directories that indicate the places where the photos were taken. Each directory contains subdirectories that indicate the years when the photos were taken.

*The directory tree is as follows:*

```
myphotos[Bucket]
  ├── beijing
  │   ├── 2014
  │   └── 2015
  ├── hangzhou
  │ ├── 2013
  │   ├── 2014
  │ └── 2015 //The read-only permission on this directory must be assigned.
  └── qingdao
      ├── 2014
      └── 2015
```

Assume that you need to assign the read-only permission on the `myphotos/hangzhou/2015/` directory to a RAM user. The required authorization policy depends on the application scenario. The following describes the authorization policies for three scenarios by policy complexity, from simplest to more complex.

**Scenario 1: The RAM user knows all file paths, requires only the permission to read file content, and does not require the permission to list files.**

In this scenario, the RAM user knows the complete paths of all files and can directly read the files using the complete paths. A software system requires such permission assignment, because the file paths in the software system comply with a certain rule \(for example, files are named after employee IDs\) or the file paths have persisted in the database of the software system.

```
{
    "Version": "1",
    "Statement ":[
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

**Scenario 2: A RAM user uses the OSS CMD to access the `myphotos/hangzhou/2015/` directory, but does not know what files are available in the directory. Therefore, the files must be listed.**

Generally, software developers require such permission assignment. The developers do not know what files are available in a directory and use the OSS CMD or API to directly obtain the directory information.

In this scenario, the ListObjects permission that is not required in `scenario 1` must be added. Because only the files in the `myphotos/hangzhou/2015/` directory are to be listed, the oss:Prefix condition must be added to the ListObjects permission.

```
{
    "Version": "1",
    "Statement ":[
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
                    "oss:Prefix":"hangzhou/2015/"
                }
            }
        }
    ]
}
```

**Scenario 3: A RAM user uses the OSS console to access the `myphotos/hangzhou/2015/` directory.**

This is the most easy-to-use scenario. When the RAM user uses the visual OSS client to access the `myphotos/hangzhou/2015/` directory, like Windows File Explorer, the visual OSS client allows the RAM user to access the target directory from the root directory through levels of sub-directories.

Therefore, you need to add the following permissions to implement this type of directory navigation:

1.  Permission to list all buckets
2.  Permission to list the subdirectories of the “myphotos” directory \(In this example, the subdirectories include beijing, hangzhou, and qingdao.\)
3.  Permission to list the subdirectories under “myphotos/hangzhou” \(The subdirectories include 2013, 2014, and 2015.\)

```
{
    "Version": "1",
    "Statement ":[
        {
            "Effect": "Allow",
            "Action": [
                "oss:ListBuckets",
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

## Authorize a RAM user complete management of a bucket {#section_a1c_cpx_ydb .section}

You need to create an authorization policy first. Assume that your bucket is named “myphotos”. Create the authorization policy as follows:

```
{
    "Version": "1",
    "Statement ":[
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

Then, add the authorization policy for this user.

## RAM user authorized to manage a bucket notified of having no operation permissions when logging on to the OSS console {#section_t51_sfk_c2b .section}

Assume that you create an authorization policy as follows to authorize a RAM user to read data objects from a bucket \(such as “myphotos”\):

```
{
  "Version": "1",
  "Statement ":[
    {
      "Effect": "Allow",
      "Action": [
        "oss:ListObjects"
      ],
      "Resource": "acs:oss:*:*:myphotos"
    },
    {
      "Effect": "Allow",
      "Action": [
        "oss:GetObject"
      ],
      "Resource": "acs:oss:*:*:myphotos/*"
    }
  ]
}
```

However, the RAM user was notified of having no operation permissions when logging on to the OSS console.

The reason is that when the RAM user logs on to the OSS console, the OSS console makes the RAM user access the OSS service as authorized. For a better user interaction experience, the OSS console also calls the ListBuckets, GetBucketAcl, and GetObjectAcl operations. \(GetBucketAcl specifies whether a bucket is private or public. GetObjectAcl specifies an object is private or public.\)

Therefore, to enable the RAM user to manage a bucket on the OSS console, you need to create the authorization policy as follows:

```
{
  "Version": "1",
  "Statement ":[
    {
      "Effect": "Allow",
      "Action": "oss:ListBuckets",
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

