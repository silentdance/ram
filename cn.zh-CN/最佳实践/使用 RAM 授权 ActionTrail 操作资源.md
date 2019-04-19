# 使用 RAM 授权 ActionTrail 操作资源 {#concept_kkr_klm_xgb .concept}

本文介绍了通过 RAM 的权限管理能力，通过创建用户并授予相应的权限，以满足 RAM 用户操作 ActionTrail 的资源。

## 前提条件 {#section_c3m_csm_xgb .section}

使用 RAM 对 ActionTrail 进行授权前，需掌握以下两方面内容：

-   了解 ActionTrail 相关 API 接口及其描述方式，详情请参考：[RAM鉴权](../../../../intl.zh-CN/API参考/RAM鉴权.md#)。
-   了解[Policy 结构和语法](../../../../intl.zh-CN/用户指南/权限管理/Policy 语言/Policy 结构和语法.md#)。

## 使用 RAM 授权 ActionTrail 操作资源的操作步骤 {#section_03 .section}

1.  创建 RAM 用户。

    详情请参考：[用户](../../../../intl.zh-CN/用户指南/身份管理/用户管理/用户.md#)。

2.  为 RAM 用户授权。
    -   若要为 RAM 用户添加一条或多条系统策略，可根据下述 ActionTrail 相关系统策略授予 RAM 用户相应权限。

        详情请参考：[RAM 授权](../../../../intl.zh-CN/用户指南/权限管理/授权管理/RAM 授权.md#)。

    -   如果需要更细粒度的授权，可根据下述授权样例创建相应的自定义策略并授予相应 RAM 用户。

        详情请参考：[权限策略管理](../../../../intl.zh-CN/用户指南/权限管理/权限策略管理.md#)。


## ActionTrail 相关系统策略 {#section_yty_gmm_xgb .section}

ActionTrail 常见的系统策略如下所示：

|系统策略名称|说明|
|:-----|:-|
|AliyunActionTrailFullAccess|ActionTrail 完全管理权限|
|AliyunActionTrailReadOnlyAccess|ActionTrail 只读权限|

## 授权样例 {#section_xqm_lnm_xgb .section}

-   **示例 1：**授予 RAM 用户只读权限。

    ```language-json
    {
        "Version": "1",
        "Statement": [{
            "Effect": "Allow",
            "Action": [
                "actiontrail:LookupEvents", 
                "actiontrail:Describe*", 
                "actiontrail:Get*"
            ],
            "Resource": "*"
        }]
    }
    					
    ```

-   **示例 2：**仅允许 RAM 用户从指定的 IP 地址发起的只读操作。

    ```language-json
    {
        "Version": "1",
        "Statement": [{
            "Effect": "Allow",
            "Action": [
                "actiontrail:LookupEvents", 
                "actiontrail:Describe*", 
                "actiontrail:Get*"
            ],
            "Resource": "*",
            "Condition":{
                "IpAddress": {
                    "acs:SourceIp": "42.120.XX.X/24"
                }
            }
        }]
    }
    					
    ```


