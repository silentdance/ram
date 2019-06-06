# Samples {#reference_lt5_rzy_xdb .reference}

-   For the region endpoints of STS, see[Service address](../../../../reseller.en-US/API Reference (STS)/Calling method/Service address.md)
-   For a detailed description of the parameters of the AssumeRole interface in the code sample, see[AssumeRole](../../../../reseller.en-US/API Reference (STS)/Operation interfaces/AssumeRole.md)

```
/usr/bin/env python
#coding=utf-8
from aliyunsdkcore import client
from aliyunsdkcore.profile import region_provider
from aliyunsdksts.request.v20150401 import AssumeRoleRequest
# Construct an Aliyun Client for initiating a request
# Set AccessKeyID and AccessKeySevcret when constructing the Aliyun Client
REGIONID = 'cn-shanghai'
ENDPOINT = 'sts.cn-shanghai.aliyuncs.com'
# Configure the STS Endpoint to be accessed
region_provider.add_endpoint('Sts', REGIONID, ENDPOINT)
# Initialize the client
clt = client.AcsClient('<access-key-id>','<access-key-secret>', REGIONID)
# Construct a "AssumeRole" request
request = AssumeRoleRequest.AssumeRoleRequest()
# Specify a role
request.set_RoleArn('<role-arn>')
# Set the session name, which the Audit Service uses to distinguish the caller
request.set_RoleSessionName('<role-session-name>')
# Initiate a request and obtain the response
response = clt.do_action_with_exception(request)
print response
```

