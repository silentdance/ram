# Node.js SDK 示例 {#concept_njz_bxv_xdb .concept}

本文以 Node.js SDK 为例，说明如何创建 RAM 用户。

``` {#codeblock_nqz_gzg_u2x}
ALY = require("aliyun-sdk")

// 构建一个 Aliyun Client, 用于发起请求
// 构建 Aliyun Client 时需要设置 access key ID 和 access key secret
// RAM 是 Global Service, API 入口位于华东 1 (杭州) , 这里使用 RAM API 的主地址
var ram = new ALY.RAM({
        accessKeyId: "<access-key-id>",
        secretAccessKey: "<access-key-secret>",
        endpoint: 'https://ram.aliyuncs.com',
        apiVersion: '2015-05-01'
});

// 构造“CreateUser”请求
ram.createUser({
        Action: 'CreateUser',
        UserName: "alice"
}, function (err, res) {
        console.log(err, res);
});
```

