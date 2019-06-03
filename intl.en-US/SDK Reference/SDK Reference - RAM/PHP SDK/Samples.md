# Samples {#reference_lng_lwv_xdb .reference}

``` {#codeblock_pab_btu_wgm}
<? php
include_once 'aliyun-php-sdk-core/Config.php';
use Ram\Request\V20150501 as Ram;

// Construct an Aliyun Client for initiating a request
// Set AccessKeyID and AccessKeySecret when constructing the Aliyun Client
// RAM is a Global Service, and its API ingress is located in the East China 1 (Hangzhou) region. Enter "cn-hangzhou" in "Region"
$iClientProfile = DefaultProfile::getProfile("cn-hangzhou", "<acccess-key-id>", "<access-key-secret>");
$client = new DefaultAcsClient($iClientProfile);

// Construct a "CreateUser" request
$request = new Ram\CreateUserRequest();
// Set the parameter - UserName
$request->setUserName("alice");

// Initiate a request and obtain the response
$response = $client->doAction($request);

print_r("\r\n");
print_r($response);
			
```

