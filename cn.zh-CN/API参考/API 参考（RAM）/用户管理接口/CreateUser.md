# CreateUser {#reference_lmj_ftk_xdb .reference}

## 接口描述 {#section_whn_4tk_xdb .section}

创建RAM子用户

## 请求参数 {#section_k2y_ptk_xdb .section}

**Action**

-   类型：String
-   必须：是
-   描述：操作接口名，系统规定参数，取值：CreateUser

**UserName**

-   类型：String
-   必须：是
-   描述：指定用户名，最多包含64个字符
-   格式：

    ```
    ^[a-zA-Z0-9\.@\-_]+$
    ```


**DisplayName**

-   类型：String
-   必须：否
-   描述：显示名称，最多包含128个字符或汉字
-   格式：

    ```
    ^[a-zA-Z0-9\.@\-\u4e00-\u9fa5]+$
    ```


**MobilePhone**

-   类型：String
-   必须：否
-   描述：RAM用户手机号
-   格式：国际区号-号码；例如：86-18600008888

**Email**

-   类型：String
-   必须：否
-   描述：RAM用户的邮箱

**Comments**

-   类型：String
-   必须：否
-   描述：备注, 最大长度128个字符。

## 需要的权限 {#section_g22_rtk_xdb .section}

**Action**

```
ram:CreateUser
```

**Resource**

```
acs:ram:*:${AccountId}:user/*
```

## 返回参数 {#section_svf_5tk_xdb .section}

**User**

-   类型：[User](intl.zh-CN/API参考/API 参考（RAM）/数据类型/User.md) Type
-   描述：用户信息

## 错误信息 {#section_zjv_5tk_xdb .section}

**InvalidParameter.UserName.InvalidChars**

-   HTTP Status：400
-   Error Message：The parameter - "UserName" contains invalid chars.

**InvalidParameter.UserName.Length**

-   HTTP Status：400
-   Error Message：The parameter - "UserName" beyond the length limit.

**InvalidParameter.DisplayName.InvalidChars**

-   HTTP Status：400
-   Error Message：The parameter - "DisplayName" contains invalid chars.

**InvalidParameter.DisplayName.Length**

-   HTTP Status：400
-   Error Message：The parameter - "DisplayName" beyond the length limit.

**InvalidParameter.Comments.Length**

-   HTTP Status：400
-   Error Message：The parameter - "Comments" beyond the length limit.

**InvalidParameter.MobilePhone.Format**

-   HTTP Status：400
-   Error Message：The format of the parameter - "MobilePhone" is incorrect.

**InvalidParameter.Email.Format**

-   HTTP Status：400
-   Error Message：The format of the parameter - "Email" is incorrect.

**EntityAlreadyExists.User**

-   HTTP Status：409
-   Error Message：The user does already EXIST.

**LimitExceeded.User**

-   HTTP Status：409
-   Error Message：The count of users beyond the current limits.

## 操作示例 {#section_pwp_vtk_xdb .section}

**请求示例**

**说明：** 为了便于阅读，以下各请求示例均不对参数进行编码\(Percent Encode\)

```
https://ram.aliyuncs.com/?Action=CreateUser
&UserName=zhangqiang
&DisplayName=zhangqiang
.&MobilePhone=86-18688888888
&Email=zhangqiang@example.com
&Comments=This is a cloud computing engineer.
&<Public request parameters>https://ram.aliyuncs.com/?Action=CreateUser&UserName=zhangqiang&DisplayName=zhangqiang&MobilePhone=86-18688888888&Email=zhangqiang@example.com&Comments=This is a cloud computing engineer.&
```

**返回示例**

-   XML格式

    ```
    <CreateUserResponse>
        <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
        <User>
            <UserId>1227489245380721</UserId>
            <UserName>zhangqiang</UserName>
            <DisplayName>zhangqiang</DisplayName>
            <MobilePhone>86-18600008888</MobilePhone>
            <Email>zhangqiang@example.com</Email>
           <Comments>This is a cloud computing engineer.</Comments>
           <CreateDate>2015-01-23T12:33:18Z</CreateDate>
        </User>
    </CreateUserResponse>
    ```

-   JSON格式

    ```
    {
        "RequestId": "04F0F334-1335-436C-A1D7-6C044FE73368",
        "User": {
            "UserId": "1227489245380721",
            "UserName": "zhangqiang",
            "DisplayName": "张强",
            "MobilePhone": "86-18600008888",
            "Email": "zhangqiang@example.com",
            "Comments": "这是一位云计算工程师",
            "CreateDate": "2015-01-23T12:33:18Z"
        }
    }
    ```


