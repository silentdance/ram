# Samples {#reference_egf_vvv_xdb .reference}

``` {#codeblock_8qe_d7t_njt}
/usr/bin/env python
#coding=utf-8

from aliyunsdkcore import client
from aliyunsdkram.request.v20150501 import CreateUserRequest


# Construct an Aliyun Client for initiating a request
# Set AccessKeyID and AccessKeySecret when constructing the Aliyun Client
# RAM is a Global Service, and its API ingress is located in the East China 1 (Hangzhou) region. Enter "cn-hangzhou" in "Region"
clt = client.AcsClient('<access-key-id>','<access-key-secret>','cn-hangzhou')

# Construct a "CreateUser" request
request = CreateUserRequest.CreateUserRequest()
# Set the UserName parameter
request.set_UserName('alice')

# Initiate a request and obtain the response
response = clt.do_action(request)

print response
```

