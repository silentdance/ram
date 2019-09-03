# Samples {#reference_gzd_wzy_xdb .concept}

This topic provides an operation example.

``` {#codeblock_vq4_7kw_xt6}
/*
  Usage: npm install -S @alicloud/pop-core
  powered by alinode (http://alinode.aliyun.com/)
*/

const Core = require('@alicloud/pop-core');

//Initialization
var client = new Core({
  accessKeyId: '<accessKeyId>',
  secretAccessKey: '<accessSecret>',
  endpoint: 'https://ram.aliyuncs.com',
  apiVersion: '2015-05-01'
});

//Set parameters
var params = {}

//Initiate a request
client.request('ListUsers', params).then((result) => {
  console.log(result)
}, (ex) => {
  console.log(ex)
})
```

**Note:** 

-   For information about STS endpoints, see [Endpoints](../../../../reseller.en-US/API Reference (STS)/Calling method/Endpoints.md#).
-   For information about the AssumeRole action, see [AssumeRole](../../../../reseller.en-US/API Reference (STS)/Operation interfaces/AssumeRole.md#).

