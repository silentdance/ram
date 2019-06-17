# Node.js SDK {#concept_mnq_2xv_xdb .concept}

本文简要介绍了 Node.js SDK 的安装并提供一个简单的操作示例。

## Node.js SDK 的安装 {#section_hnm_fxv_xdb .section}

您可以通过 npm 安装 Node.js SDK：

``` {#codeblock_0zu_1wz_x99}
npm install aliyun-sdk
```

## Node.js SDK 示例 {#section_8qp_yie_4yo .section}

以下示例以 Node.js SDK 为例，说明如何创建 RAM 用户。

``` {#codeblock_hiv_pqh_ukg}
ALY = require("aliyun-sdk")

// 构建一个阿里云 Client, 用于发起请求
// 构建阿里云 Client 时需要设置 access key ID 和 access key secret
// RAM 是 Global Service, API 入口位于华东 1 (杭州) , 这里使用 RAM API 的主地址
var ram = new ALY.RAM({
        accessKeyId: "<access-key-id>",
        AccessKeysecret: "<access-key-secret>",
        endpoint: 'https://ram.aliyuncs.com',
        apiVersion: '2015-05-01'
});

// 构造 CreateUser 请求
ram.createUser({
        Action: 'CreateUser',
        UserName: "alice"
}, function (err, res) {
        console.log(err, res);
});
```

