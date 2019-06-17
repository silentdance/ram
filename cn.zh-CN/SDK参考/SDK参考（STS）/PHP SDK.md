# PHP SDK {#concept_esm_kzy_xdb .concept}

本文简要介绍了 PHP SDK 的安装并提供一个简单的操作示例。

## PHP SDK 的安装 {#section_egk_sbz_xdb .section}

安装包下载地址：

-   [PHP SDK](https://develop.aliyun.com/tools/sdk?#/php)
-   [GitHub](https://github.com/aliyun/aliyun-openapi-php-sdk/tree/master/aliyun-php-sdk-sts)

## PHP SDK 示例 {#section_v2h_tik_es1 .section}

``` {#codeblock_0re_eqi_0xo}
<?php
include_once 'aliyun-php-sdk-core/Config.php';
use Sts\Request\V20150401 as Sts;
define("REGION_ID", "cn-shanghai");
define("ENDPOINT", "sts.cn-shanghai.aliyuncs.com");
// 只允许 RAM 用户使用角色
DefaultProfile::addEndpoint(REGION_ID, REGION_ID, "Sts", ENDPOINT);
$iClientProfile = DefaultProfile::getProfile(REGION_ID, "<acccess-key-id>", "<access-key-secret>");
$client = new DefaultAcsClient($iClientProfile);
// 指定角色 ARN
$roleArn = "<role-arn>";
// 在扮演角色时，添加一个权限策略，进一步限制角色的权限
// 以下权限策略表示拥有可以读取所有 OSS 的只读权限
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
// RoleSessionName 即临时身份的会话名称，用于区分不同的临时身份
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

**说明：** 

-   STS 各区域的 endpoint，请参考：[接入地址](../../../../intl.zh-CN/API 参考（STS）/调用方式/接入地址.md#)。
-   AssumeRole 接口相关信息，请参考：[AssumeRole](../../../../intl.zh-CN/API 参考（STS）/操作接口/AssumeRole.md#)。

