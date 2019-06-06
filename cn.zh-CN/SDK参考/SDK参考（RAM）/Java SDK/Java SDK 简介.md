# Java SDK 简介 {#reference_q3x_v5v_xdb .reference}

本文简要介绍了 Java SDK 的安装以及版本发布通知。

## Java SDK 的安装 {#section_nvs_p5v_xdb .section}

RAM SDK 包含阿里云 Java SDK 公共部分和 RAM 部分：

-   阿里云 Java SDK 公共部分依赖`aliyun-java-sdk-core`。关于 SDK 示例代码的自动生成和在线 API 调试，请参考：[OpenAPI Explorer](https://api.aliyun.com/)。
-   RAM 部分依赖`aliyun-java-sdk-ram`。关于 RAM API 接口相关信息，请参考：[API 概览](../../../../cn.zh-CN/API参考（RAM）/API 概览.md#)。

您可以通过 Maven 管理项目依赖或手动下载 RAM SDK 的 jar 包后手动添加到项目中。

-   通过 Maven 管理项目依赖（推荐）。
    1.  使用 Maven 创建项目。

        ``` {#codeblock_wy5_9yh_uya}
        mvn archetype:generate -DgroupId=com.aliyun.ram.sample \
        -DartifactId=ram-sdk-sample \
        -Dpackage=com.aliyun.ram.sample \
        -Dversion=1.0-SNAPSHOT
        ```

    2.  在项目的 pom.xml文件中加入相应依赖项。

        添加`aliyun-java-sdk`的相关依赖，以 2.0.7 版本为例，在标签内添加如下内容：

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

        **说明：** `aliyun-java-sdk`已经加入到 [Maven 仓库](https://maven-repository.com/artifact/com.aliyun)中，无需设置settings.xml。

-   手动下载 RAM SDK 的 jar 包后手动添加到项目中。

    下载地址：

    -   [Java SDK](http://search.maven.org/remotecontent?filepath=com/aliyun/aliyun-java-sdk-core/2.2.3/aliyun-java-sdk-core-2.2.3.jar)
    -   [RAM SDK](http://search.maven.org/remotecontent?filepath=com/aliyun/aliyun-java-sdk-ram/2.0.7/aliyun-java-sdk-ram-2.0.7.jar)

## Java SDK 的版本发布通知 {#section_mpj_s5v_xdb .section}

|时间|版本|说明|
|--|--|--|
|2015 年 11 月 07 日|2.0.7|发布 RAM Java SDK 第一个版本，覆盖 RAM 所有 API。|

