# Python SDK {#concept_zhn_1wv_xdb .concept}

This topic describes how to install Python SDK and provides an operation example.

## Installation {#section_d2h_2wv_xdb .section}

You can use PIP to install Python SDK or download the Python SDK package and add the package to the target project.

-   Use PIP to install Python SDK:

    ``` {#codeblock_7a1_bkg_dxr}
    pip install aliyun-python-sdk-ram
    ```

-   Download the Python SDK package:
    -   [Python SDK](https://pypi.python.org/pypi/aliyun-python-sdk-core)
    -   [RAM SDK](https://pypi.python.org/pypi/aliyun-python-sdk-ram)

## Example {#section_7la_s6f_vkz .section}

The following is an example of how to create a RAM user by using Python SDK:

``` {#codeblock_x1u_8d8_lwf}
#!/usr/bin/env python
#coding=utf-8

from aliyunsdkcore import client
from aliyunsdkram.request.v20150501 import CreateUserRequest


# Construct an Alibaba Cloud client to initiate a request.
# Set the access key ID and access key secret.
# Alibaba Cloud Resource Access Management (RAM) is a global service. Its API endpoint is China (Hangzhou). Here, set "Region" to "cn-hangzhou".
clt = client.AcsClient('<access-key-id>','<access-key-secret>','cn-hangzhou')

# Construct the "CreateUser" request.
request = CreateUserRequest.CreateUserRequest()
# Set the "UserName" parameter.
request.set_UserName('alice')

# Initiate a request and obtain a response.
response = clt.do_action(request)

print response
```

