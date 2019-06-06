# Installation {#reference_hts_dzy_xdb .reference}

## Use JAR package in Eclipse {#section_ctd_qyy_xdb .section}

Steps:

-   Download [STS Java SDK](https://develop.aliyun.com/tools/sdk#/java) from Alibaba Cloud website
-   Decompress the file
-   Copy aliyun-java-sdk-core-<versionId\>.jar and aliyun-java-sdk-sts-<versionId\>.jar from the decompressed folderto your project folder
-   In Eclipse, right-click**and choose Project** \> **Properties** \> **Java Build Path** \> **Add JARs**.
-   Select all the JAR files you copied
-   After completing the steps above, you can use STS Java SDK in the project

The STS Java SDK in other IDEs is configured in a similar way.

## Use SDK in Maven projects {#section_nny_qyy_xdb .section}

Add relevant aliyun-java-sdk dependency. Take version 3.0.0 as an example. `<dependencies>`Type the following content in the

```
<dependency> tab:
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

