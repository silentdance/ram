# Java SDK {#reference_q3x_v5v_xdb .reference}

## Introduction {#section_cyw_n5v_xdb .section}

RAM SDK consists of two parts. The public part of Alibaba Cloud Java SDK depends on `aliyun-java-sdk-core`, and the RAM part depends on `aliyun-java-sdk-ram`.

For details about each API interface, see RAM API documentation.

## Installation {#section_nvs_p5v_xdb .section}

You can use Maven Repo to introduce RAM SDK or manually download RAM SDK.jar and then add it to the project.

**Maven Dependencies**

```
<dependency>
    <groupId>com.aliyun</groupId>
    <artifactId>aliyun-java-sdk-ram</artifactId>
    <version>2.0.7</version>
</dependency>
<dependency>
    <groupId>com.aliyun</groupId>
    <artifactId>aliyun-java-sdk-core</artifactId>
    <version>2.2.3</version>
</dependency>
```

**Download the JAR package**

[aliyun-java-sdk-core-2.2.3.jar](http://search.maven.org/remotecontent?filepath=com/aliyun/aliyun-java-sdk-core/2.2.3/aliyun-java-sdk-core-2.2.3.jar)

[aliyun-java-sdk-ram-2.0.7.jar](http://search.maven.org/remotecontent?filepath=com/aliyun/aliyun-java-sdk-ram/2.0.7/aliyun-java-sdk-ram-2.0.7.jar)

## Examples {#section_btk_r5v_xdb .section}

Creation of a sub-account named “alice” in RAM is used as an example:

```
package com.aliyun.ram.sample;

import com.aliyuncs.DefaultAcsClient;
import com.aliyuncs.exceptions.ClientException;
import com.aliyuncs.profile.DefaultProfile;
import com.aliyuncs.profile.IClientProfile;

// The RAM API version is 2015-05-01
import com.aliyuncs.ram.model.v20150501. *;

/**
 * Created by JasonGao on 15/11/4.
 */

public class RamServiceSample {

    public static void main(String[] args) {
        // Construct an Aliyun Client for initiating a request
        // Set AccessKeyID and AccessKeySevcret when constructing the Aliyun Client
        // RAM is a Global Service, and its API ingress is located in the East China 1 (Hangzhou) region. Enter "cn-hangzhou" in "Region"
        IClientProfile profile = DefaultProfile.getProfile("cn-hangzhou",
                                                           "<AccessKeyId>",
                                                           "<AccessKeySecret>");
        DefaultAcsClient client = new DefaultAcsClient(profile);

        // Construct a "CreateUser" request
        final CreateUserRequest request = new CreateUserRequest();

        // Set the parameter - User
        request.setUserName("alice");

        // Initiate a request and obtain the response
        try {
            final CreateUserResponse response = client.getAcsResponse(request);

            System.out.println("UserName: " + response.getUser().getUserName());
            System.out.println("CreateTime: " + response.getUser().getCreateDate());
        } catch (ClientException e) {
            System.out.println("Failed.") ;
            System.out.println("Error code: " + e.getErrCode());
            System.out.println("Error message: " + e.getErrMsg());
        }

    }
}
```

## Release Notes {#section_mpj_s5v_xdb .section}

**Version: 2.0.7**

The first version of RAM Java SDK was released on November 7, 2015, which contains all APIs of RAM.

