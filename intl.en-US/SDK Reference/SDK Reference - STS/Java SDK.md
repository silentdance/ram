# Java SDK {#concept_rxg_yxv_xdb .concept}

This topic describes how to install Java SDK and provides an operation example.

## Introduction {#section_mtl_8e9_scy .section}

STS SDKs consist of Alibaba Cloud Java SDKs and STS SDKs.

-   To install an Alibaba Cloud Java SDK, you must firstly install `aliyun-java-sdk-core`. For information about how to generate code examples and perform debug operations, see [OpenAPI Explorer](https://api.aliyun.com/).
-   To install an STS SDK, you must firstly install `aliyun-java-sdk-sts`. For information about STS API actions, see [Introduction](../../../../reseller.en-US/API Reference (STS)/Introduction.md#).

## Installation {#section_tsg_gxv_xdb .section}

Yo can use Maven to manage project dependencies or download the STS SDK JAR package and add the package to the target project.

-   Recommended. Use Maven to manage project dependencies.
    1.  Use Maven to create a project.

        ``` {#codeblock_xaz_tmq_ab5}
        mvn archetype:generate -DgroupId=com.aliyun.sts.sample \
        -DartifactId=sts-sdk-sample \
        -Dpackage=com.aliyun.sts.sample \
        -Dversion=1.0-SNAPSHOT
        ```

    2.  Add dependencies to the pom.xml file of the project.

        Add `aliyun-java-sdk` dependencies. The following is an example of STS SDK 3.0.0:

        ``` {#codeblock_4g0_b7w_131}
        <dependency>
            <groupId>com.aliyun</groupId>
            <artifactId>aliyun-java-sdk-sts</artifactId>
            <version>3.0.0</version>
        </dependency>
        <dependency>
            <groupId>com.aliyun</groupId>
            <artifactId>aliyun-java-sdk-core</artifactId>
            <version>[4.4.2,5.0.0)</version>
        </dependency>
        ```

        **Note:** The `aliyun-java-sdk` artifact is added to the [Maven repository](https://maven-repository.com/artifact/com.aliyun). Therefore, you do not need to configure the settings.xml file.

-   Download the target JAR package and add the package to the project.
    -   [Java SDK](https://develop.aliyun.com/tools/sdk#/java)
    -   [GitHub](https://github.com/aliyun/aliyun-openapi-java-sdk/tree/master/aliyun-java-sdk-sts)

## Example {#section_be7_hph_1z9 .section}

Create the source code `StsServiceSample.java` in the com/aliyun/sts/sample/ directory.

**Note:** The following is an example of core 4.4.2.

``` {#codeblock_t4p_zzo_lzd}
package com.aliyun.sts.sample;
import com.aliyuncs.DefaultAcsClient;
import com.aliyuncs.exceptions.ClientException;
import com.aliyuncs.http.MethodType;
import com.aliyuncs.profile.DefaultProfile;
import com.aliyuncs.profile.IClientProfile;
import com.aliyuncs.sts.model.v20150401.AssumeRoleRequest;
import com.aliyuncs.sts.model.v20150401.AssumeRoleResponse;
public class StsServiceSample {
    public static void main(String[] args) {
        String endpoint = "sts.aliyuncs.com";
        String accessKeyId = "<access-key-id>";
        String accessKeySecret = "<access-key-secret>";
        String roleArn = "<role-arn>";
        String roleSessionName = "session-name";
        String policy = "{\n" +
                "    \"Version\": \"1\", \n" +
                "    \"Statement\": [\n" +
                "        {\n" +
                "            \"Action\": [\n" +
                "                \"oss:*\"\n" +
                "            ], \n" +
                "            \"Resource\": [\n" +
                "                \"acs:oss:*:*:*\" \n" +
                "            ], \n" +
                "            \"Effect\": \"Allow\"\n" +
                "        }\n" +
                "    ]\n" +
                "}";
        try {
            // Construct the default profile. (You do not need to add the region ID.)
            IClientProfile profile = DefaultProfile.getProfile("", accessKeyId, accessKeySecret);
            // Use the profile to construct a client.
            DefaultAcsClient client = new DefaultAcsClient(profile);
            final AssumeRoleRequest request = new AssumeRoleRequest();
            request.setSysEndpoint(endpoint);
            request.setSysMethod(MethodType.POST);
            request.setRoleArn(roleArn);
            request.setRoleSessionName(roleSessionName);
            request.setPolicy(policy); // Optional
            final AssumeRoleResponse response = client.getAcsResponse(request);
            System.out.println("Expiration: " + response.getCredentials().getExpiration());
            System.out.println("Access Key Id: " + response.getCredentials().getAccessKeyId());
            System.out.println("Access Key Secret: " + response.getCredentials().getAccessKeySecret());
            System.out.println("Security Token: " + response.getCredentials().getSecurityToken());
            System.out.println("RequestId: " + response.getRequestId());
        } catch (ClientException e) {
            System.out.println("Failed：");
            System.out.println("Error code: " + e.getErrCode());
            System.out.println("Error message: " + e.getErrMsg());
            System.out.println("RequestId: " + e.getRequestId());
        }
    }
}
```

**Note:** 

-   Make sure that the access key ID and access key secret are valid.
-   For information about STS endpoints, see [Service address](../../../../reseller.en-US/API Reference (STS)/Calling method/Service address.md#).
-   For information about the AssumeRole API action, see [AssumeRole](../../../../reseller.en-US/API Reference (STS)/Operation interfaces/AssumeRole.md#).

