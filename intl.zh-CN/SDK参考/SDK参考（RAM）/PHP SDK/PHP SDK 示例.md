# PHP SDK 示例 {#reference_lng_lwv_xdb .concept}

本文以 PHP SDK 为例，说明如何创建 RAM 用户。

``` {#codeblock_hg8_mj4_ig8}
<?php
include_once 'aliyun-php-sdk-core/Config.php';
use Ram\Request\V20150501 as Ram;

// 构建一个阿里云 Client, 用于发起请求
// 构建阿里云 Client 时需要设置 access key ID 和 access key secret
// RAM 是 Global Service, API 入口位于华东 1 (杭州) , 这里 Region 填写:cn-hangzhou
$iClientProfile = DefaultProfile::getProfile("cn-hangzhou", "<acccess-key-id>", "<access-key-secret>");
$client = new DefaultAcsClient($iClientProfile);

// 构造 CreateUser 请求
$request = new Ram\CreateUserRequest();
//设置参数：UserName
$request->setUserName("alice");

//发起请求，并得到 response
$response = $client->doAction($request);

print_r("\r\n");
print_r($response);
?>
```

