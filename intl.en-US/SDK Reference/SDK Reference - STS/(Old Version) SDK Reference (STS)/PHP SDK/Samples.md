# Samples {#reference_j4k_jzy_xdb .concept}

This topic provides an operation example.

``` {#codeblock_9hq_srb_axq}
<? php

 * Before using STS SDK, read description on role management in the RAM Manual, and read the STS API Documentation


include_once 'aliyun-php-sdk-core/Config.php';
use Sts\Request\V20150401 as Sts;
define("REGION_ID", "cn-shanghai");
define("ENDPOINT", "sts.cn-shanghai.aliyuncs.com");
// Only sub-account can use the role
DefaultProfile::addEndpoint(REGION_ID, REGION_ID, "Sts", ENDPOINT);
$iClientProfile = DefaultProfile::getProfile(REGION_ID, "<acccess-key-id>", "<access-key-secret>");
$client = new DefaultAcsClient($iClientProfile);
// You can obtain the role resource descriptor from the resource details page on RAM console
$roleArn = "<role-arn>";
// When assuming a role (AssumeRole), you can assign an authorization policy to further limit the role permission.
// For details, see the "RAM Use Guide"
// The authorization policy indicates the read-only permission on all OSS resources
$policy=<<<POLICY

  "Statement": [

      "Action": [
        "oss:Get*",
        "oss:List*"

      "Effect": "Allow",
      "Resource": "*"


  "Version": "1"

POLICY;
$request = new Sts\AssumeRoleRequest();
// RoleSessionName indicates the session name of a temporary ID which is used to distinguish different temporary temporary IDs
// You can use your customer's ID as the session name
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

		
```

**Note:** 

-   For information about STS endpoints, see [Endpoints](../../../../reseller.en-US/API Reference (STS)/Calling method/Endpoints.md#).
-   For information about the AssumeRole action, see [AssumeRole](../../../../reseller.en-US/API Reference (STS)/Operation interfaces/AssumeRole.md#).

