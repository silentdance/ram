# Python SDK {#concept_smb_tzy_xdb .concept}

本文简要介绍了 Python SDK 的安装并提供一个简单的操作示例。

## Python SDK 的安装 {#section_egk_sbz_xdb .section}

安装包下载地址：

-   [Python SDK](https://develop.aliyun.com/tools/sdk?#/python)
-   [GitHub](https://github.com/aliyun/aliyun-openapi-python-sdk/tree/master/aliyun-python-sdk-sts)

## Python SDK 示例 {#section_1jp_c02_8a3 .section}

``` {#codeblock_oa9_1pu_2rv}
#!/usr/bin/env python
#coding=utf-8
from aliyunsdkcore import client
from aliyunsdkcore.profile import region_provider
from aliyunsdksts.request.v20150401 import AssumeRoleRequest
# 构建一个阿里云 Client, 用于发起请求
# 构建阿里云 Client 时需要设置 access key ID 和 access key secret
REGIONID = 'cn-shanghai'
ENDPOINT = 'sts.cn-shanghai.aliyuncs.com'
# 配置要访问的 STS endpoint
region_provider.add_endpoint('Sts', REGIONID, ENDPOINT)
# 初始化 Client
clt = client.AcsClient('<access-key-id>','<access-key-secret>', REGIONID)
# 构建 AssumeRole 请求
request = AssumeRoleRequest.AssumeRoleRequest()
# 指定角色 ARN
request.set_RoleArn('<role-arn>')
# 设置会话名称，审计服务使用此名称区分调用者
request.set_RoleSessionName('<role-session-name>')
# 发起请求，并得到 response
response = clt.do_action_with_exception(request)
print response
```

**说明：** 

-   STS 各区域的 endpoint，请参考：[接入地址](../../../../intl.zh-CN/API 参考（STS）/调用方式/接入地址.md#)。
-   AssumeRole 接口相关信息，请参考：[AssumeRole](../../../../intl.zh-CN/API 参考（STS）/操作接口/AssumeRole.md#)。

