# PHP SDK {#concept_esm_kzy_xdb .concept}

This topic describes how to install PHP SDK and provides an operation example.

## Installation {#section_egk_sbz_xdb .section}

To download PHP SDK, click either of the following links:

-   [PHP SDK](https://develop.aliyun.com/tools/sdk?#/php)
-   [GitHub](https://github.com/aliyun/aliyun-openapi-php-sdk/tree/master/aliyun-php-sdk-sts)

## Example {#section_v2h_tik_es1 .section}

``` {#codeblock_0re_eqi_0xo}
<?php
include_once 'aliyun-php-sdk-core/Config.php';
use Sts\Request\V20150401 as Sts;
define("REGION_ID", "cn-shanghai");
define("ENDPOINT", "sts.cn-shanghai.aliyuncs.com");
// Only RAM users can assume the role.
DefaultProfile::addEndpoint(REGION_ID, REGION_ID, "Sts", ENDPOINT);
$iClientProfile = DefaultProfile::getProfile(REGION_ID, "<acccess-key-id>", "<access-key-secret>");
$client = new DefaultAcsClient($iClientProfile);
// Specify the Alibaba Cloud Resource Name (ARN) of the role.
$roleArn = "<role-arn>";
// Specify the permission of the role by attaching a policy to the role.
// The following policy indicates that the role has all the read-only permission for OSS.
$policy=<<<POLICY
{
  "Statement": [
    {
      "Action": [
        "oss:Get*",
        "oss:List*"
      ],
      "Effect": "Allow",
      "Resource": "*"
    }
  ],
  "Version": "1"
}
POLICY;
$request = new Sts\AssumeRoleRequest();
// RoleSessionName: The session name of the temporary identity for assuming the role.
$request->setRoleSessionName("client_name");
$request->setRoleArn($roleArn);
$request->setPolicy($policy);
$request->setDurationSeconds(3600);
try {
    $response = $client->getAcsResponse($request);
    print_r($response);
} catch(ServerException $e) {
    print "Error: " . $e->getErrorCode() . " Message: " . $e->getMessage() . "\n";
} catch(ClientException $e) {
    print "Error: " . $e->getErrorCode() . " Message: " . $e->getMessage() . "\n";
}
?>
```

**Note:** 

-   For information about RAM roles, see [RAM role management](../../../../reseller.en-US/User Guide/Roles/RAM role management.md#).
-   For information about STS endpoints, see [Service address](../../../../reseller.en-US/API Reference (STS)/Calling method/Service address.md#).
-   For information about the AssumeRole action, see [AssumeRole](../../../../reseller.en-US/API Reference (STS)/Operation interfaces/AssumeRole.md#).

