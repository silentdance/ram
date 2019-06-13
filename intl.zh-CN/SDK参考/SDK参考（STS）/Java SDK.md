# Java SDK {#concept_rxg_yxv_xdb .concept}

本文简要介绍了 Java SDK 的安装并提供一个简单的操作示例。

## 背景信息 {#section_mtl_8e9_scy .section}

STS SDK 包含阿里云 Java SDK 公共部分和 STS 部分：

-   阿里云 Java SDK 公共部分依赖`aliyun-java-sdk-core`。关于 SDK 示例代码的自动生成和在线 API 调试，请参考：[OpenAPI Explorer](https://api.aliyun.com/)。
-   STS 部分依赖`aliyun-java-sdk-sts`。关于 STS API 接口相关信息，请参考：[简介](../../../../intl.zh-CN/API 参考（STS）/什么是 STS.md#)。

## STS Java SDK 的安装 {#section_tsg_gxv_xdb .section}

您可以通过 Maven 管理项目依赖或手动下载 STS SDK 的 jar 包后添加到项目中。

-   通过 Maven 管理项目依赖（推荐）。
    1.  使用 Maven 创建项目。

        ``` {#codeblock_xaz_tmq_ab5}
        mvn archetype:generate -DgroupId=com.aliyun.sts.sample \
        -DartifactId=sts-sdk-sample \
        -Dpackage=com.aliyun.sts.sample \
        -Dversion=1.0-SNAPSHOT
        ```

    2.  在项目的 pom.xml文件中加入相应依赖项。

        添加`aliyun-java-sdk`的相关依赖，以 3.0.0 版本为例，在标签内添加如下内容：

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

        **说明：** `aliyun-java-sdk`已经加入到 [Maven 仓库](https://maven-repository.com/artifact/com.aliyun)中，无需设置 settings.xml。

-   手动下载 STS SDK 的 jar 包后手动添加到项目中。

    下载地址：

    -   [Java SDK](https://develop.aliyun.com/tools/sdk#/java)
    -   [GitHub](https://github.com/aliyun/aliyun-openapi-java-sdk/tree/master/aliyun-java-sdk-sts)

## Java SDK 示例 {#section_be7_hph_1z9 .section}

在 com/aliyun/sts/sample/ 目录下创建 Java 源代码`StsServiceSample.java`。

**说明：** 以下示例 core 以 4.4.2 版本为例，仅供参考。

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
            // 构造 default profile（参数留空，无需添加 region ID）
            IClientProfile profile = DefaultProfile.getProfile("", accessKeyId, accessKeySecret);
            // 用 profile 构造 client
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

**说明：** 

-   请修改 access key ID 和 access key secret 为有效值。
-   STS 各区域的 endpoint 请参考：[接入地址](../../../../intl.zh-CN/API 参考（STS）/调用方式/接入地址.md#)。
-   AssumeRole 接口相关信息，请参考：[AssumeRole](../../../../intl.zh-CN/API 参考（STS）/操作接口/AssumeRole.md#)。

