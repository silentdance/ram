# SAML assertions for role-based SSO {#concept_snl_vkq_bhb .concept}

This topic describes the mandatory attribute elements in SAML assertions issued by your identity provider \(IdP\) for role-based SSO.

## Scenario {#section_wdm_dbl_2hb .section}

During SAML 2.0-based SSO, after the identity of a user is verified, your IdP generates an authentication response and sends it to Alibaba Cloud through a browser or a program. This response contains an SAML assertion that complies with the HTTP POST Binding for SAML 2.0 standard.

Alibaba Cloud uses the SAML assertion to determine the logon status and identity of the user. Therefore, the SAML assertion must contain elements that are required by Alibaba Cloud.

## Common elements in SAML 2.0 {#section_jks_j2l_2hb .section}

-   `Issuer` 

    The value of the `Issuer` element must match the `EntityID` in the IdP metadata file uploaded in the IdP created in Alibaba Cloud.

-   `Signature` 

    The SAML assertion in Alibaba Cloud must be used as a signature. The `Signature` element must contain information such as the signature value and signature algorithm.

-   `Subject` 

    The `Subject` element must contain the following sub-elements:

    -   Only one `NameID` sub-element. You must specify the value of `NameID` according to SAML 2.0. But note that Alibaba Cloud does not determine a logon identity according to the value of `NameID`.
    -   Only one `SubjectConfirmation` sub-element with a `SubjectConfirmationData` sub-element. The `SubjectConfirmationData` sub-element must contain the following attributes:

        -   `NotOnOrAfter`: specifies the validity of an SAML assertion.
        -   `Recipient`: Alibaba Cloud checks whether it is the recipient of the SAML assertion according to the value of the `Recipient` element. Therefore, you must set `Recipient` to .
        The following is an example of the `Subject` element:

-   `Conditions` 

    The `Conditions` element must contain an `AudienceRestriction` sub-element. The `AudienceRestriction` sub-element can contain multiple `Audience` sub-elements, and the value of an `Audience` sub-element must be .

    The following is an example of the `Conditions` element:


## Custom elements required by Alibaba Cloud {#section_aq3_yll_2hb .section}

The `AttributeStatement` element in an SAML assertion must contain the following `Attribute` sub-elements required by Alibaba Cloud:

-   A mandatory `Attribute` element with the `Name` attribute set to `https://www.aliyun.com/SAML-Role/Attributes/Role` 

    This element contains one or more `AttributeValue` sub-elements that list the role can be assumed by the user in your IdP. The value of the `AttributeValue` sub-element is a comma-delimited pair of role ARN and IdP ARN. You can obtain the role ARN and IdP ARN in the RAM console.

    -   To obtain the role ARN, go to the RAM Roles page and click the name of the target RAM role.
    -   To obtain the IdP ARN, go to the SSO page. On the **Role-based SSO** tab, click the name of the target IdP.
    If the sub-element contains multiple pairs, the user is asked to select which role to assume during logon through the console.

    The following is an example of the `Role` sub-element:

    ``` {#codeblock_wng_9pk_8fe}
    <Attribute Name="https://www.aliyun.com/SAML-Role/Attributes/Role">      
      <AttributeValue>acs:ram::$account_id:role/role1,acs:ram::$account_id:saml-provider/provider1</AttributeValue>
      <AttributeValue>acs:ram::$account_id:role/role2,acs:ram::$account_id:saml-provider/provider1</AttributeValue>
    </Attribute>
    ```

    **Note:** The value of `$account_id` is the Alibaba Cloud account ID that defines the RAM role and IdP.

-   A mandatory `Attribute` element with the `Name` attribute set to `https://www.aliyun.com/SAML-Role/Attributes/RoleSessionName` 

    This element contains only one `AttributeValue` sub-element that is used to display user information in the RAM console and ActionTrail logs. If you want multiple users to assume one role, use a unique `RoleSessionName` value, such as the user ID and email address for different users.

    The value in the `AttributeValue` sub-element must be 2 to 64 characters in length, and include only letters, digits, commas \(,\), periods \(.\), hyphens \(-\), underscores \(\_\), plus signs \(+\), equal signs \(=\), and at signs \(@\).

    The following is an example of the `RoleSessionName` sub-element:

    ``` {#codeblock_kcb_i1l_14k}
    <Attribute Name="https://www.aliyun.com/SAML-Role/Attributes/RoleSessionName">
      <AttributeValue>user_id</AttributeValue>
    </Attribute>
    ```

-   Optional, an `Attribute` element with the `Name` attribute set to `https://www.aliyun.com/SAML-Role/Attributes/SessionDuration` 

    This element contains only one `AttributeValue` sub-element that specifies the logon duration. If the logon is initiated through the console, the `AttributeValue` sub-element represents the number of seconds for the session. If the logon is initiated through the program, the `AttributeValue` sub-element represents the STS token validity.

    The value of `AttributeValue` is an integer representing the logon duration, in seconds. The value can range from 900 seconds \(15 minutes\) to 3600 seconds \(1 hour\). If this sub-element does not exist, the logon duration is one hour.

    The following is an example of the `SessionDuration` sub-element:

    ``` {#codeblock_9ot_n1b_9w7}
    <Attribute Name="https://www.aliyun.com/SAML-Role/Attributes/SessionDuration">
      <AttributeValue>1800</AttributeValue>
    </Attribute>
    ```


