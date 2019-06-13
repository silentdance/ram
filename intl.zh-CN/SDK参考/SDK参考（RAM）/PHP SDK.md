# PHP SDK {#concept_cph_rwv_xdb .concept}

本文简要介绍了 PHP SDK 的安装并提供一个简单的操作示例。

## PHP SDK 的安装 {#section_z6y_39e_6kr .section}

安装包下载地址 ：[PHP SDK](https://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/cn/ram/0.0.71/assets/ram-sdk/aliyun_ram_php_sdk_2.0.7.zip)。

## PHP SDK 示例 {#section_kvg_i91_pbh .section}

以下示例以 PHP SDK 为例，说明如何创建 RAM 用户。

``` {#codeblock_5v5_vyy_5dl}
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

