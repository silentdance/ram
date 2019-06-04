# Java SDK 示例 {#reference_g22_fzy_xdb .concept}

本文简要介绍了 aliyun-java-sdk-sts 使用的示例代码以及后续如何编译和运行。

## 示例代码 {#section_omd_n1z_xdb .section}

在 com/aliyun/sts/sample/ 目录下创建 Java 源代码`StsServiceSample.java`。

**说明：** 以下示例 core 以 4.4.2 版本为例，仅供参考。

``` {#codeblock_erm_wwa_1gt}
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
            // 用 profile 构造client
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
-   STS 各 region endpoint 请参考：[服务地址](../../../../intl.zh-CN/API 参考（STS）/附录/服务地址.md#)。
-   AssumeRole 接口相关信息，请参考：[AssumeRole](../../../../intl.zh-CN/API 参考（STS）/操作接口/AssumeRole.md#)。

## 编译示例代码 {#section_yqj_q1z_xdb .section}

``` {#codeblock_6vq_trh_bnz}
mvn install
```

## 运行示例代码 {#section_p4z_90n_2sn .section}

``` {#codeblock_ege_tre_sn5}
mvn -q exec:java -Dexec.mainClass=com.aliyun.sts.sample.StsServiceSample
```

