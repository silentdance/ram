# Python SDK {#concept_smb_tzy_xdb .concept}

This topic describes how to install Python SDK and provides an operation example.

## Installation {#section_egk_sbz_xdb .section}

To download Python SDK, click either of the following links:

-   [Python SDK](https://develop.aliyun.com/tools/sdk?#/python)
-   [GitHub](https://github.com/aliyun/aliyun-openapi-python-sdk/tree/master/aliyun-python-sdk-sts)

## Example {#section_1jp_c02_8a3 .section}

``` {#codeblock_oa9_1pu_2rv}
#!/usr/bin/env python
#coding=utf-8
from aliyunsdkcore import client
from aliyunsdkcore.profile import region_provider
from aliyunsdksts.request.v20150401 import AssumeRoleRequest
# Construct an Alibaba Cloud client to initiate a request.
# Set the access key ID and access key secret.
REGIONID = 'cn-shanghai'
ENDPOINT = 'sts.cn-shanghai.aliyuncs.com'
# Configure the STS endpoint to be accessed.
region_provider.add_endpoint('Sts', REGIONID, ENDPOINT)
# Initialize the client.
clt = client.AcsClient('<access-key-id>','<access-key-secret>', REGIONID)
# Construct the "AssumeRole" request.
request = AssumeRoleRequest.AssumeRoleRequest()
# Specify the Alibaba Cloud Resource Name (ARN) of the role.
request.set_RoleArn('<role-arn>')
# Set the session name. The session name is used to identify the user who is calling this API action.
request.set_RoleSessionName('<role-session-name>')
# Initiate a request and obtain a response.
response = clt.do_action_with_exception(request)
print response
```

**Note:** 

-   For information about STS endpoints, see [Service address](../../../../reseller.en-US/API Reference (STS)/Calling method/Service address.md#).
-   For information about the AssumeRole action, see [AssumeRole](../../../../reseller.en-US/API Reference (STS)/Operation interfaces/AssumeRole.md#).

