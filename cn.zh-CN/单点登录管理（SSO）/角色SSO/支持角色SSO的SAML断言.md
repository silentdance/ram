# 支持角色SSO的SAML断言 {#concept_snl_vkq_bhb .concept}

本文介绍在进行角色SSO时，您的IdP颁发的SAML断言必须具备的属性元素。

## 背景信息 {#section_gc3_vkv_chb .section}

在基于SAML 2.0的SSO流程中，当企业用户在IdP登录后，IdP将根据SAML 2.0 HTTP-POST绑定的要求生成包含SAML断言的认证响应，并由浏览器（或程序）自动转发给阿里云。

这个SAML断言会被用来确认用户登录状态并从中解析出登录的主体。因此，断言中必须包含阿里云要求的元素，否则登录用户的身份将无法被确认，导致SSO失败。

## SAML 2.0协议的通用元素 {#section_y1n_xts_bhb .section}

-   `Issuer` 

    `Issuer`的值必须与您在阿里云创建的**身份提供商**实体中上传的IdP元数据文件中的`EntityID`匹配。

-   `Signature` 

    阿里云要求SAML断言必须被签名以确保没有篡改，`Signature`及其包含的元素必须包含签名值、签名算法等信息。

-   `Subject` 

    `Subject`必须包含以下元素：

    -   有且仅有一个`NameID`元素。您必须按照SAML 2.0协议的定义来给出`NameID`的值，但阿里云不会依赖该元素的值来确认登录主体。
    -   有且仅有一个`SubjectConfirmation`元素，其中包含一个`SubjectConfirmationData`元素。`SubjectConfirmationData`必须有如下两个属性：

        -   `NotOnOrAfter`：规定SAML断言的有效期。
        -   `Recipient`：阿里云通过检查该元素的值来确保阿里云是该断言的目标接收方，其取值必须为 `https://signin.aliyun.com/saml-role/sso`。
        如下是一个`Subject`元素的示例：

        ``` {#codeblock_a1k_ppe_h09 .lanuage-xml}
        <Subject>
          <NameID Format="urn:oasis:names:tc:SAML:2.0:nameid-format:persistent">administrator</NameID>        
          <SubjectConfirmation Method="urn:oasis:names:tc:SAML:2.0:cm:bearer">   
            <SubjectConfirmationData NotOnOrAfter="2019-01-01T00:01:00.000Z" Recipient="https://signin.aliyun.com/saml-role/sso"/>    
          </SubjectConfirmation>
        </Subject>
        ```

-   `Conditions` 

    在`Conditions`元素中，必须包含一个`AudienceRestriction`元素，其中可包含一至多个`Audience`元素，但必须有一个`Audience`元素的取值为 `urn:alibaba:cloudcomputing`。

    如下是一个`Conditions`元素的示例：

    ``` {#codeblock_4q4_wgn_r4h .lanuage-xml}
    <Conditions>
      <AudienceRestriction>
        <Audience>urn:alibaba:cloudcomputing</Audience>
      </AudienceRestriction>
    </Conditions>          
    ```


## 阿里云要求的自定义属性 {#section_nd3_zts_bhb .section}

在SAML断言的`AttributeStatement`元素中，必须包含如下阿里云要求的`Attribute`元素：

-   `Name`属性值为`https://www.aliyun.com/SAML-Role/Attributes/Role`的`Attribute`元素

    该元素为必选，可以有多个。其包含的`AttributeValue`元素取值代表允许当前用户扮演的角色，取值的格式是由角色ARN与身份提供商ARN组合而成的，中间用英文逗号（,）隔开。这两个ARN您可以在控制台获取：

    -   角色ARN：在RAM角色管理页面，单击RAM角色名称后，基本信息页面可以查看对应的ARN。
    -   身份提供商ARN：在SSO管理页面的**角色SSO**页签下, 单击身份提供商名称后，身份提供商信息页面可以查看对应的ARN。
    **说明：** 如果是多个，当使用控制台登录时，将会在界面上列出所有角色供用户选择。

    如下是一个Role Attribute元素示例：

    ``` {#codeblock_aiw_gvv_hl4 .lanuage-xml}
    <Attribute Name="https://www.aliyun.com/SAML-Role/Attributes/Role">      
      <AttributeValue>acs:ram::$account_id:role/role1,acs:ram::$account_id:saml-provider/provider1</AttributeValue>
      <AttributeValue>acs:ram::$account_id:role/role2,acs:ram::$account_id:saml-provider/provider1</AttributeValue>
    </Attribute>               
    ```

    **说明：** `$account_id`是定义角色和身份提供商的阿里云账号ID。

-   `Name`属性值为`https://www.aliyun.com/SAML-Role/Attributes/RoleSessionName`的`Attribute`元素

    该元素为必选且只能有一个。其包含的`AttributeValue`元素取值将被用来作为登录用户信息的一部分显示在控制台上和操作审计日志中。如果您有多个用户使用同一个角色，请确保使用可以唯一标识用户的`RoleSessionName`值，以区分不同的用户，如员工ID、email地址等。

    其`AttributeValue`元素取值要求：长度不少于2个字符且不超过32个字符，只能是英文字母、数字和以下特殊字符：`-_.@=,+`。

    如下是一个RoleSessionName Attribute元素示例：

    ``` {#codeblock_kmj_7ly_ylx .lanuage-xml}
    <Attribute Name="https://www.aliyun.com/SAML-Role/Attributes/RoleSessionName">
      <AttributeValue>user_id</AttributeValue>
    </Attribute>                     
    ```

-   `Name`属性值为`https://www.aliyun.com/SAML-Role/Attributes/SessionDuration`的`Attribute`元素

    该元素为可选，且最多只能有一个。在通过控制台登录的情况下，其包含的`AttributeValue`元素取值将会被作为用户会话的有效时长。在通过程序登录的情况下，其包含的`AttributeValue`元素取值无效。

    其`AttributeValue`元素取值要求：整数，单位为秒，最小900秒（15分钟），最大3600秒（1小时）。若此元素不存在，则取默认值3600秒。

    如下是一个SessionDuration Attribute元素示例：

    ``` {#codeblock_qa9_q4v_2tq .lanuage-xml}
    <Attribute Name="https://www.aliyun.com/SAML-Role/Attributes/SessionDuration">
      <AttributeValue>1800</AttributeValue>
    </Attribute>                  
    ```


