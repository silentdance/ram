# PHP SDK {#concept_cph_rwv_xdb .concept}

This topic describes how to install PHP SDK and provides an operation example.

## Installation {#section_z6y_39e_6kr .section}

To download PHP SDK, click [PHP SDK](https://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/cn/ram/0.0.71/assets/ram-sdk/aliyun_ram_php_sdk_2.0.7.zip).

## Example {#section_kvg_i91_pbh .section}

The following is an example of how to create a RAM user by using PHP SDK:

``` {#codeblock_5v5_vyy_5dl}
<?php
include_once 'aliyun-php-sdk-core/Config.php';
use Ram\Request\V20150501 as Ram;

// Construct an Alibaba Cloud client to initiate a request.
// Set the access key ID and access key secret.
// Alibaba Cloud Resource Access Management (RAM) is a global service. Its API endpoint is China (Hangzhou). Here, set "Region" to "cn-hangzhou".
$iClientProfile = DefaultProfile::getProfile("cn-hangzhou", "<acccess-key-id>", "<access-key-secret>");
$client = new DefaultAcsClient($iClientProfile);

// Construct the "CreateUser" request.
$request = new Ram\CreateUserRequest();
// Set the "UserName" parameter.
$request->setUserName("alice");

// Initiate a request and obtain a response.
$response = $client->doAction($request);

print_r("\r\n");
print_r($response);
?>
```

