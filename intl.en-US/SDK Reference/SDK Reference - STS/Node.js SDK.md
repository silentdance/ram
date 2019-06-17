# Node.js SDK {#concept_fvb_xzy_xdb .concept}

This topic describes how to install Node.js SDK and provides an operation example.

## Installation {#section_egk_sbz_xdb .section}

You can use npm to install Node.js SDK.

``` {#codeblock_rfl_xaf_zql}
npm install aliyun-sdk
```

## Example {#section_c4w_0ax_p6c .section}

``` {#codeblock_vxy_igi_mt4}
/*
  Usage: npm install -S @alicloud/pop-core
  powered by alinode (http://alinode.aliyun.com/)
*/

const Core = require('@alicloud/pop-core');
// Construct an Alibaba Cloud client to initiate a request.
// Set the access key ID and access key secret.
var client = new Core({
  accessKeyId: '<accessKeyId>',
  AccessKeysecret: '<accessSecret>',
  endpoint: 'https://sts.aliyuncs.com',
  apiVersion: '2015-04-01'
});

// Specify the Alibaba Cloud Resource Name (ARN) of the role.
var params = {
  'RoleArn': '<role-arn>',
  'RoleSessionName': 'session-name'
};

// Construct the "AssumeRole" request.
client.request('AssumeRole', params).then((result) => {
  console.log(result);
}, (ex) => {
  console.log(ex);
})
```

**Note:** 

-   For information about STS endpoints, see [Service address](../../../../reseller.en-US/API Reference (STS)/Calling method/Service address.md#).
-   For information about the AssumeRole action, see [AssumeRole](../../../../reseller.en-US/API Reference (STS)/Operation interfaces/AssumeRole.md#).

