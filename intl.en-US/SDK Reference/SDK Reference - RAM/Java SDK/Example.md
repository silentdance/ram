# Example {#concept_473271 .concept}

This topic describes how to create a RAM user by using Java SDK.

``` {#codeblock_dx7_3pm_6c5}
package com.aliyun.ram.sample;

import com.aliyuncs.DefaultAcsClient;
import com.aliyuncs.exceptions.ClientException;
import com.aliyuncs.profile.DefaultProfile;
import com.aliyuncs.profile.IClientProfile;

//The version of the RAM API used in this example was the version released on May 1, 2015.
import com.aliyuncs.ram.model.v20150501.*;

/**
 * Created by JasonGao on 15/11/4.
 */

public class RamServiceSample {

    public static void main(String[] args) {
        //Create an Alibaba Cloud client to initiate a request.
        //Set the access key ID and access key secret.
        //Alibaba Cloud Resource Access Management (RAM) is a global service. The endpoint of RAM API is China (Hangzhou). Here, set "Region" to "cn-hangzhou".
        IClientProfile profile = DefaultProfile.getProfile("cn-hangzhou",
                                                           "<AccessKeyId>",
                                                           "<AccessKeySecret>");
        DefaultAcsClient client = new DefaultAcsClient(profile);

        //Construct the "CreateUser" request.
        final CreateUserRequest request = new CreateUserRequest();

        //Set the "UserName" parameter.
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

