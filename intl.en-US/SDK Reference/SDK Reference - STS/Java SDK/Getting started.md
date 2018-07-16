# Getting started {#reference_g22_fzy_xdb .reference}

## Create and manage roles {#section_ctd_qyy_xdb .section}

To use STS’s AssumeRole interface, you need to create and manage roles in RAM. For details, see [Role](../../../../intl.en-US/User Guide/Identities/Role.md#).

## Use Maven to create a project {#section_nny_qyy_xdb .section}

```
mvn archetype:generate -DgroupId=com.aliyun.sts.sample \
-DartifactId=sts-sdk-sample \
-Dpackage=com.aliyun.sts.sample \
-Dversion=1.0-SNAPSHOT
```

Modify the generated pom.xml, and add relevant aliyun-java-sdk dependency. Take version 3.0.0 as an example. Type the following content in the “dependencies” tab:

```
<dependency>
    <groupId>com.aliyun</groupId>
    <artifactId>aliyun-java-sdk-sts</artifactId>
    <version>3.0.0</version>
 
</dependency>
<dependency>
    <groupId>com.aliyun</groupId>
    <artifactId>aliyun-java-sdk-core</artifactId>
    <version>3.5.0</version>
 
</dependency>
```

aliyun-java-sdk has been added to [https://maven-repository.com/artifact/com.aliyun](https://maven-repository.com/artifact/com.aliyun)

You do not need to set the file settings.xml for maven.

## Sample code used in aliyun-java-sdk-sts {#section_omd_n1z_xdb .section}

In the com/aliyun/sts/sample/ directory, create the Java’s source code StsServiceSample.java and type the following content:

**Note:** 

-   Change the values of accessKeyID and accessKeySecret to valid ones.
-   For the region endpoints of STS, see [Service address](../../../../intl.en-US//Appendix/Service address.md#)
-   For a detailed description of the parameters of the AssumeRole interface in the sample, see [Service address](../../../../intl.en-US//Appendix/Service address.md#)

```
package com.aliyun.sts.sample;
import com.aliyuncs.DefaultAcsClient;
import com.aliyuncs.exceptions.ClientException;
import com.aliyuncs.http.MethodType;
import com.aliyuncs.profile.DefaultProfile;
import com.aliyuncs.profile.IClientProfile;
import com.aliyuncs.sts.model.v20150401. AssumeRoleRequest;
import com.aliyuncs.sts.model.v20150401. AssumeRoleResponse;
public class StsServiceSample {
    public static void main(String[] args) {
        String endpoint = "sts.aliyuncs.com";
        String accessKeyId = "<access-key-id>";
        String accessKeySecret = "<access-key-secret>";
        String roleArn = "<role-arn>";
        String roleSessionName = "session-name";
        String policy = "{\n" +
                "    \"Version\": \"1\", \n" +
                " \"Statement\": [\n" +
                " {\n" +
                " \"Action\": [\n" +
                " \"oss:*\"\n" +
                " ], \n" +
                "\" Resource \ ": [\ n" +
                " \"acs:oss:*:*:*\" \n" +
                " ], \n" +
                " \"Effect\": \"Allow\"\n" +
                " }\n" +
                " ]\n" +
                "}";
        try {
            // Add endpoint
            DefaultProfile.addEndpoint("", "", "Sts", endpoint);
            // Construct default profile
            IClientProfile profile = DefaultProfile.getProfile("", accessKeyId, accessKeySecret);
            // Construct client with profile
            DefaultAcsClient client = new DefaultAcsClient(profile);
            final AssumeRoleRequest request = new AssumeRoleRequest();
            request.setMethod(MethodType.POST);
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
            System.out.println("Failed:");
            System.out.println("Error code: " + e.getErrCode());
            System.out.println("Error message: " + e.getErrMsg());
            System.out.println("RequestId: " + e.getRequestId());
        }
    }
}
```

## Compile and run the sample code {#section_yqj_q1z_xdb .section}

**Compile the sample code**

```
mvn install
```

**Run the sample code**

```
mvn -q exec:java -Dexec.mainClass=com.aliyun.sts.sample.StsServiceSample
```

