# Java SDK 示例 {#concept_473271 .concept}

本文以 Java SDK 为例，说明如何创建 RAM 用户。

``` {#codeblock_dx7_3pm_6c5}
package com.aliyun.ram.sample;

import com.aliyuncs.DefaultAcsClient;
import com.aliyuncs.exceptions.ClientException;
import com.aliyuncs.profile.DefaultProfile;
import com.aliyuncs.profile.IClientProfile;

// 当前 RAM API 版本为：2015-05-01
import com.aliyuncs.ram.model.v20150501.*;

/**
 * Created by JasonGao on 15/11/4.
 */

public class RamServiceSample {

    public static void main(String[] args) {
        // 构建一个阿里云 Client, 用于发起请求
        // 构建阿里云 Client 时需要设置 access key ID 和 access key secret
        // RAM 是 Global Service, API 入口位于华东 1 (杭州) , 这里 Region 填写:cn-hangzhou
        IClientProfile profile = DefaultProfile.getProfile("cn-hangzhou",
                                                           "<AccessKeyId>",
                                                           "<AccessKeySecret>");
        DefaultAcsClient client = new DefaultAcsClient(profile);

        // 构建 CreateUser 请求
        final CreateUserRequest request = new CreateUserRequest();

        //设置参数：UserName
        request.setUserName("alice");

        // 发起请求，并得到 response
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

