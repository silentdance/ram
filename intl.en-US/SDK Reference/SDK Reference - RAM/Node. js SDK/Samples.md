# Samples {#reference_njz_bxv_xdb .reference}

``` {#codeblock_p3y_do8_udw}
ALY = require("aliyun-sdk")

// Construct an Aliyun Client for initiating a request
// Set AccessKeyID and AccessKeySecret when constructing the Aliyun Client
// RAM is a Global Service, and its API ingress is located in the East China 1 (Hangzhou) region. The master IP address of RAM API is used
var ram = new ALY.RAM({
        accessKeyId: "<access-key-id>",
        secretAccessKey: "<access-key-secret>",
        endpoint: 'https://ram.aliyuncs.com',
        apiVersion: '2015-05-01'


// Construct a "CreateUser" request
ram.createUser({
        Action: 'CreateUser',
        UserName: "alice"
}, function (err, res) {
        console.log(err, res);
			
```

