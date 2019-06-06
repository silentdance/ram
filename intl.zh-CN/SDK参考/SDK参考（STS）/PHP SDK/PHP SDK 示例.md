# PHP SDK 示例 {#reference_j4k_jzy_xdb .concept}

本文简要介绍如何构建一个 PHP SDK 的示例。

``` {#codeblock_jdg_pzy_20s}
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

-   关于角色相关信息，请参考：[管理 RAM 角色](../../../../cn.zh-CN/用户指南/身份管理/RAM 角色身份/管理 RAM 角色.md#)。
-   STS 各区域的 endpoint 请参考：[服务地址](../../../../cn.zh-CN/API 参考（STS）/调用方式/服务地址.md#)。
-   AssumeRole 接口相关信息，请参考：[AssumeRole](../../../../cn.zh-CN/API 参考（STS）/操作接口/AssumeRole.md#)。

