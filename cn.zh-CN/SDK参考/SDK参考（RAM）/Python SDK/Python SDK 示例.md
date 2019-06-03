# Python SDK 示例 {#reference_egf_vvv_xdb .reference}

本文以 Python SDK 为例，说明如何创建 RAM 用户。

``` {#codeblock_5vd_lfi_xts}
#!/usr/bin/env python
#coding=utf-8

from aliyunsdkcore import client
from aliyunsdkram.request.v20150501 import CreateUserRequest


# 构建一个 Aliyun Client, 用于发起请求
# 构建 Aliyun Client 时需要设置 access key ID 和 access key secret
# RAM 是 Global Service, API 入口位于华东 1 (杭州) , 这里 Region 填写“cn-hangzhou”
clt = client.AcsClient('<access-key-id>','<access-key-secret>','cn-hangzhou')

# 构造“CreateUser”请求
request = CreateUserRequest.CreateUserRequest()
# 设置参数：UserName
request.set_UserName('alice')

# 发起请求，并得到 response
response = clt.do_action(request)

print response
```

