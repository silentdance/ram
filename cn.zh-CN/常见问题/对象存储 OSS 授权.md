# 对象存储 OSS 授权 {#concept_ohn_ypx_ydb .concept}

## 问题 {#section_x1f_w4x_ydb .section}

-   [查看 OSS 的权限定义](#section_mzy_x4x_ydb)
-   [为一个子用户授予只读访问 OSS 的权限](#section_jft_y4x_ydb)
-   [为一个子用户授予完全管理 OSS 的权限](#section_fnn_z4x_ydb)
-   [授权一个子用户列出并读取一个 Bucket 中的资源](#section_jpq_1px_ydb)
-   [在OSS中使用带IP限制的访问控制](#section_jpq_1px_ydb)
-   [OSS目录级别的授权](#section_a1c_cpx_ydb)
-   [授权子用户完全管理某个 Bucket 的权限](#section_a1c_cpx_ydb)
-   [子用户已经被授予了某Bucket权限，为什么登录OSS控制台访问时提示没有操作权限](#section_a1c_cpx_ydb)

## 查看 OSS 的权限定义 {#section_mzy_x4x_ydb .section}

请参考 OSS 产品文档中的[访问控制](../../../../intl.zh-CN/开发指南/访问与控制/访问控制.md#)部分。

## 为一个子用户授予只读访问 OSS 的权限 {#section_jft_y4x_ydb .section}

在 RAM 控制台中创建一个子用户，并为此子用户附加系统授权策略”AliyunOSSReadOnlyAccess”。附加授权策略的方式请参考[授权](../../../../intl.zh-CN/用户指南/授权管理/授权.md)。

## 为一个子用户授予完全管理 OSS 的权限 {#section_fnn_z4x_ydb .section}

在 RAM 控制台中为此子用户附加系统授权策略 “AliyunOSSFullAccess”。

## 授权一个子用户列出并读取一个 Bucket 中的资源 {#section_jpq_1px_ydb .section}

如果您需要授权一个子用户（例如，代表您的某个应用程序）通过 OSS SDK 或 OSS CMD 列出并读取一个 Bucket 中的资源，那么您需要创建一条自定义授权策略来完成。

假设您的 Bucket 名称为 “myphotos”，那么创建的授权策略样例如下：

```
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

如果您希望被授权的子用户能够通过 OSS 控制台进行操作，那么授权策略中还需要添加 GetBucketAcl 以及 GetObjectAcl 权限（控制台为了操作体验的优化需要额外调用 OSS 的部分 API）。允许子用户通过 OSS 控制台操作的授权策略样例如下：

```
{
    "Version": "1",
    "Statement": [
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

## 在OSS中使用带IP限制的访问控制 {#section_plf_hkg_c2b .section}

示例1: 在`Allow`授权中增加IP限制

允许通过`42.120.88.0/24`, `42.120.66.0/24`两个IP段读取myphotos中的信息;

```
{
    "Version": "1",
    "Statement": [
        {
            "Sid": "允许列出所有Bucket",
            "Effect": "Allow",
            "Action": [
                "oss:ListBuckets"
            ],
            "Resource": [
                "acs:oss:*:*:*"
            ]
        },
        {
            "Sid": "允许获取myphotos中的信息, 访问源必须在允许的IP段中",
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
                    "acs:SourceIp": ["42.120.88.0/24", "42.120.66.0/24"]
                }
            }
        }
    ]
}
```

示例2: 在`Deny`授权中增加IP限制

如果源IP不在`42.120.88.0/24`中，则禁止对OSS执行任何操作；

```
{
    "Version": "1",
    "Statement": [
        {
            "Sid": "允许列出所有Bucket",
            "Effect": "Allow",
            "Action": [
                "oss:ListBuckets"
            ],
            "Resource": [
                "acs:oss:*:*:*"
            ]
        },
        {
            "Sid": "允许获取myphotos中的信息",
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
            "Sid": "禁止从42.120.88.0/24以外访问OSS",
            "Effect": "Deny",
            "Action": "oss:*",
            "Resource": [
                "acs:oss:*:*:*"
            ],
            "Condition":{
                "NotIpAddress": {
                    "acs:SourceIp": ["42.120.88.0/24"]
                }
            }
        }
    ]
}
```

注意：因为Policy的鉴权规则是Deny优先\(即如果用户的访问操作命中任意一条Deny规则，则禁止访问\)，所以访问者从42.120.88.0/24以外的IP地址访问myphotos中的内容时，OSS服务会报没有权限。

## OSS目录级别的授权 {#section_dk4_42k_c2b .section}

目录级别的授权属于授权的高级功能，如果您有此类需求，请您认真阅读并理解此部分。

**背景**

假设有一个用于存放照片的Bucket，叫myphotos。这个bucket下有一些目录，代表照片的拍摄地；每个拍摄地目录下又有年份子目录。

*目录树结构如下*

```
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

假设我们需要授权一个子用户只读访问`myphotos/hangzhou/2015/`目录的只读权限。根据使用场景不同，授权策略也有很大的区别。下面我们根据授权策略的复杂程度，由简入繁的为大家介绍三种场景。

**场景一：子用户知道所在文件的路径，只需要读取文件内容的权限，不需要列出文件的权限**

这个场景的特点是子用户知道文件的完整路径，可以使用完整的文件路径直接去读取文件内容。通常我们会将这样的权限授予一个软件系统，系统中文件路径符合某种规则\(比如文件名是员工工号\)，或者文件路径持久化在软件系统的数据库中。

```
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

**场景二：子用户使用OSS CMD访问目录`myphotos/hangzhou/2015/`，但是不知道目录中有哪些文件，需要列出目录中文件的权限**

通常会将这样的权限授予软件开发者。开发者不清楚目录中究竟有哪些文件，然后使用OSS CMD或API直接获取目录信息。

与`场景一`相比，这里需要新增ListObjects的权限。因为我们仅允许列出`myphotos/hangzhou/2015/`目录中的文件，所以在新增的ListObjects权限中，增加”oss:Prefix”的条件限定。

```
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

**场景三：子用户使用OSS控制台访问目录`myphotos/hangzhou/2015/`**

最易用的场景，当子用户使用可视化的OSS客户端访问目录`myphotos/hangzhou/2015/`，可视化的客户端像Windows文件管理器一样，让子用户可以从根目录开始，一层一层的进入所要访问的目录。

与场景二相比，使用OSS可视化客户端时需要从从根目录一层一层导航进入`myphotos/hangzhou/2015/`，所以需要新增以下权限：

1.  列出所有Bucket的权限
2.  列出myphotos下目录的权限，在这个例子中，即可以看到beijing/hangzhou/qingdao三个目录
3.  列出myphotos/hangzhou下的目录的权限，即可以看到2013/2014/2015三个目录

```
{
    "Version": "1",
    "Statement": [
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

## 授权子用户完全管理某个 Bucket 的权限 {#section_a1c_cpx_ydb .section}

首先，创建一条自定义授权策略。假设您的 Bucket 名称为 “myphotos”。

```
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

然后，为此用户添加此条自定义授权策略。

## 子用户已经被授权了某Bucket权限，为什么登录OSS控制台访问时提示没有操作权限 {#section_t51_sfk_c2b .section}

假设您已经授权某个子用户对某个Bucket（比如myphotos）拥有读取数据对象的操作权限：

```
{
  "Version": "1",
  "Statement": [
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

但是子用户登录OSS控制台仍然报错“没有相应操作权限”，这是为何呢？

因为当用户登录OSS控制台时，OSS控制台为以当前登录用户的授权身份去访问OSS服务。为了获得更好的交互体验，OSS控制台会额外调用ListBuckets操作，以及GetBucketAcl和GetObjectAcl操作（因为要确定bucket属性是公开或私有）。

所以，为了支持通过OSS控制台操作某个Bucket，相应的授权Policy如下所示：

```
{
  "Version": "1",
  "Statement": [
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

