# Node.js SDK {#concept_mnq_2xv_xdb .concept}

This topic describes how to install Node.js SDK and provides an operation example.

## Installation {#section_hnm_fxv_xdb .section}

You can use npm to install Node.js SDK.

``` {#codeblock_0zu_1wz_x99}
npm install aliyun-sdk
```

## Example {#section_8qp_yie_4yo .section}

The following is an example of how to create a RAM user by using Node.js SDK:

``` {#codeblock_hiv_pqh_ukg}
ALY = require("aliyun-sdk")

// Construct an Alibaba Cloud client to initiate a request.
// Set the access key ID and access key secret.
// Alibaba Cloud Resource Access Management (RAM) is a global service. Its API endpoint is China (Hangzhou). Here, set "Region" to "cn-hangzhou".
var ram = new ALY.RAM({
        accessKeyId: "<access-key-id>",
        AccessKeysecret: "<access-key-secret>",
        endpoint: 'https://ram.aliyuncs.com',
        apiVersion: '2015-05-01'
});

// Construct the "CreateUser" request.
ram.createUser({
        Action: 'CreateUser',
        UserName: "alice"
}, function (err, res) {
        console.log(err, res);
});
```

