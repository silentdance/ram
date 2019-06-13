# Java SDK {#concept_q3x_v5v_xdb .concept}

This topic describes how to install Java SDK and provides an operation example.

## Introduction {#section_1rf_7jm_v0z .section}

RAM SDKs consist of Alibaba Cloud Java SDKs and RAM SDKs.

-   To install an Alibaba Cloud Java SDK, you must firstly install `aliyun-java-sdk-core`. For information about how to generate code examples and perform debug operations, see [OpenAPI Explorer](https://api.aliyun.com/).
-   To install a RAM SDK, you must firstly install `aliyun-java-sdk-ram`. For information about RAM API actions, see [API overview](../../../../reseller.en-US/API Reference/API overview.md#).

## Installation {#section_nvs_p5v_xdb .section}

Yo can use Maven to manage project dependencies or download the RAM SDK JAR package and add the package to the target project.

-   Recommended. Use Maven to manage project dependencies.
    1.  Use Maven to create a project.

        ``` {#codeblock_wy5_9yh_uya}
        mvn archetype:generate -DgroupId=com.aliyun.ram.sample \
        -DartifactId=ram-sdk-sample \
        -Dpackage=com.aliyun.ram.sample \
        -Dversion=1.0-SNAPSHOT
        ```

    2.  Add dependencies to the pom.xml file of the project.

        Add `aliyun-java-sdk` dependencies. The following is an example of Java SDK 2.0.7:

        ``` {#codeblock_g4n_czg_fid}
        <dependency>
            <groupId>com.aliyun</groupId>
            <artifactId>aliyun-java-sdk-ram</artifactId>
            <version>2.0.7</version>
        </dependency>
        <dependency>
            <groupId>com.aliyun</groupId>
            <artifactId>aliyun-java-sdk-core</artifactId>
            <version>[4.4.2,5.0.0)</version>
        </dependency>
        ```

        **Note:** The `aliyun-java-sdk` artifact is added to the [Maven repository](https://maven-repository.com/artifact/com.aliyun). Therefore, you do not need to configure the settings.xml file.

-   Download the target JAR package and add the package to the project.
    -   [Java SDK](http://search.maven.org/remotecontent?filepath=com/aliyun/aliyun-java-sdk-core/2.2.3/aliyun-java-sdk-core-2.2.3.jar)
    -   [RAM SDK](http://search.maven.org/remotecontent?filepath=com/aliyun/aliyun-java-sdk-ram/2.0.7/aliyun-java-sdk-ram-2.0.7.jar)

## Example {#section_2qp_w3e_8fs .section}

The following is an example of how to create a RAM user by using Java SDK:

``` {#codeblock_cyf_zv1_s62}
package com.aliyun.ram.sample;

import com.aliyuncs.DefaultAcsClient;
import com.aliyuncs.exceptions.ClientException;
import com.aliyuncs.profile.DefaultProfile;
import com.aliyuncs.profile.IClientProfile;

// The version of the RAM API used in this example was the version released on May 1, 2015.
import com.aliyuncs.ram.model.v20150501.*;

/**
 * Created by JasonGao on 15/11/4.
 */

public class RamServiceSample {

    public static void main(String[] args) {
        // Construct an Alibaba Cloud client to initiate a request.
        // Set the access key ID and access key secret.
        // Alibaba Cloud Resource Access Management (RAM) is a global service. Its API endpoint is China (Hangzhou). Here, set "Region" to "cn-hangzhou".
        IClientProfile profile = DefaultProfile.getProfile("cn-hangzhou",
                                                           "<AccessKeyId>",
                                                           "<AccessKeySecret>");
        DefaultAcsClient client = new DefaultAcsClient(profile);

        // Construct the "CreateUser" request.
        final CreateUserRequest request = new CreateUserRequest();

        // Set the "UserName" parameter.
        request.setUserName("alice");

        //Initiate a request and obtain a response.
        try {
            final CreateUserResponse response = client.getAcsResponse(request);

            System.out.println("UserName: " + response.getUser().getUserName());
            System.out.println("CreateTime: " + response.getUser().getCreateDate());
        } catch (ClientException e) {
            System.out.println("Failed.");
            System.out.println("Error code: " + e.getErrCode());
            System.out.println("Error message: " + e.getErrMsg());
        }

    }
}
```

