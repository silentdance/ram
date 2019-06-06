# Node.js SDK 示例 {#reference_gzd_wzy_xdb .concept}

本文简要介绍如何构建一个 Node.js SDK 的示例。

``` {#codeblock_vdq_8mk_qb5}
/*
  Usage: npm install -S @alicloud/pop-core
  powered by alinode (http://alinode.aliyun.com/)
*/

const Core = require('@alicloud/pop-core');
// 构建一个阿里云 Client, 用于发起请求
// 构建阿里云 Client 时需要设置 access key ID 和 access key secret
var client = new Core({
  accessKeyId: '<accessKeyId>',
  secretAccessKey: '<accessSecret>',
  endpoint: 'https://sts.aliyuncs.com',
  apiVersion: '2015-04-01'
});

//设置参数，指定角色 ARN
var params = {
  'RoleArn': '<role-arn>',
  'RoleSessionName': 'session-name'
};

//构建 AssumeRole 请求
client.request('AssumeRole', params).then((result) => {
  console.log(result);
}, (ex) => {
  console.log(ex);
})
```

