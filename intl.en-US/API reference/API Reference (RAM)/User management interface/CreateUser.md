# CreateUser {#reference_lmj_ftk_xdb .reference}

## Interface description {#section_whn_4tk_xdb .section}

Creates an RAM user.

## Request parameters {#section_k2y_ptk_xdb .section}

**Action**

-   Type: String
-   Required: Yes
-   Description: Operation interface, required. The parameter value is “CreateUser”.

**UserName**

-   Type: String
-   Required: Yes
-   Description: User name. It consists of a maximum of 64 characters.
-   Format:

    ```
    ^[a-zA-Z0-9\. @\\-_]+$
    ```


**DisplayName**

-   Type: String
-   Required: No
-   Description: Display name. It consists of a maximum of 128 characters.
-   Format:

    ```
    ^[a-zA-Z0-9\.@\-\u4e00-\u9fa5]+$
    ```


**MobilePhone**

-   Type: String
-   Required: No
-   Description: An RAM user’s mobile number.
-   Format: International area code-number such as 86-18600008888

**E-mail**

-   Type: String
-   Required: No
-   Description: An RAM user’s email address.

**Comments**

-   Type: String
-   Required: No
-   Description: Remark information. It consists of a maximum of 128 characters.

## Required permissions {#section_g22_rtk_xdb .section}

**Action**

```
ram:CreateUser
```

**Resource**

```
ACS: Ram: *: $ {accountant}: User /*
```

## 返回参数 {#section_svf_5tk_xdb .section}

**User**

-   类型：[User](intl.en-US/API reference/API Reference (RAM)/Data types/User.md) Type
-   Description: user information

## Error messages {#section_zjv_5tk_xdb .section}

**InvalidParameter.UserName.InvalidChars**

-   HTTP Status：400
-   Error Message：The parameter - "UserName" contains invalid chars.

**InvalidParameter.UserName.Length**

-   HTTP status: 400
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

## Operation examples {#section_pwp_vtk_xdb .section}

**Request example**

**Note:** To facilitate reading, parameters are not encoded in the following request examples.

```
https://ram.aliyuncs.com/?Action=CreateUser
&UserName=zhangqiang
&DisplayName=zhangqiang
&MobilePhone=86-18688888888
&Email=zhangqiang@example.com
&Comments=This is a cloud computing engineer.
&<Public request parameters>
```

**Response example**

-   XML format

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

-   JSON format

    ```
    {
        "RequestId": "04F0F334-1335-436C-A1D7-6C044FE73368",
        "User": {
            "UserId": "1227489245380721",
            "UserName": "zhangqiang",
            "DisplayName": "zhangqiang",
            "MobilePhone": "86-18600008888",
            "Email": "maid ",
            "Comments": "This is a cloud computing engineer".
            "CreateDate": "2015-01-23T12:33:18Z"
        }
    }
    ```


