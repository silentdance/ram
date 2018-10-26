# Java SDK {#reference_q3x_v5v_xdb .reference}

## 简介 {#section_cyw_n5v_xdb .section}

RAM SDK 包含阿里云 Java SDK 公共部分和 RAM 部分，公共部分依赖`aliyun-java-sdk-core`, RAM 部分依赖`aliyun-java-sdk-ram`。

每个接口的详细使用方法请参考 RAM API 文档。

关于 SDK Demo 代码的自动生成和在线 API 调试，请参考[OpenAPI Explorer](https://api.aliyun.com/)。

## 安装 {#section_nvs_p5v_xdb .section}

您可以使用 Maven 仓库引入 RAM SDK 或手动下载 RAM SDK jar 后手动添加到项目中。

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

**下载 jar 包**

[aliyun-java-sdk-core-2.2.3.jar](http://search.maven.org/remotecontent?filepath=com/aliyun/aliyun-java-sdk-core/2.2.3/aliyun-java-sdk-core-2.2.3.jar)

[aliyun-java-sdk-ram-2.0.7.jar](http://search.maven.org/remotecontent?filepath=com/aliyun/aliyun-java-sdk-ram/2.0.7/aliyun-java-sdk-ram-2.0.7.jar)

## 示例 {#section_btk_r5v_xdb .section}

这里以在 RAM 中创建一个名为 alice 的子用户为例：

```
package com.aliyun.ram.sample;

import com.aliyuncs.DefaultAcsClient;
import com.aliyuncs.exceptions.ClientException;
import com.aliyuncs.profile.DefaultProfile;
import com.aliyuncs.profile.IClientProfile;

// 当前RAM API版本为2015-05-01
import com.aliyuncs.ram.model.v20150501.*;

/**
 * Created by JasonGao on 15/11/4.
 */

public class RamServiceSample {

    public static void main(String[] args) {
        // 构建一个 Aliyun Client, 用于发起请求
        // 构建Aliyun Client时需要设置AccessKeyId和AccessKeySevcret
        // RAM是Global Service, API入口位于华东 1 (杭州) , 这里Region填写"cn-hangzhou"
        IClientProfile profile = DefaultProfile.getProfile("cn-hangzhou",
                                                           "<AccessKeyId>",
                                                           "<AccessKeySecret>");
        DefaultAcsClient client = new DefaultAcsClient(profile);

        // 构造"CreateUser"请求
        final CreateUserRequest request = new CreateUserRequest();

        //设置参数 - UserName
        request.setUserName("alice");

        // 发起请求，并得到response
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

## Release Notes {#section_mpj_s5v_xdb .section}

**Version: 2.0.7**

2015 年 11 月 07 日发布 RAM Java SDK 第一个版本，覆盖 RAM 所有 API

