# Create a custom policy \(optional\) {#concept_xnr_xf2_qy .concept}

At present, Alibaba Cloud offers a variety of system authorization policies for users. These authorization policies only provide coarse-grained access control capabilities, for example, read-only permissions or all permissions at a cloud product level.

If you have more fine-grained authorization requirements, for example, to authorize the user Bob to perform read-only operations on all objects only in `oss://samplebucket/bob/` and to prevent access by IP addresses from outside your company network \(your company network IP address can be acquired by searching “My IP” using the search engine\), then you can perform access control by creating a custom authorization policy.

This document describes, taking user Bob for example, how to create a custom authorization policy, helping you better understand and use RAM for fine-grained access control.

The limit for log groups is: a maximum of 4096 logs or 10 MB space

## Prerequisite {#section_ert_t2f_xdb .section}

Before creating custom authorization policies, you must understand the basic structure and syntax of the authorization policy language. For more details, see [Syntax](https://www.alibabacloud.com/help/doc-detail/28664.htm).

RAM supports the authorization of the API granularity, at the finest. That is, the operation permissions in the authorization policy can be as fine as each API. Before creating custom authorization policies, you must understand the authorization granularity and method supported by related products. For more details, see [Cloud services supporting RAM](https://www.alibabacloud.com/help/doc-detail/28630.htm).

## Operation steps {#section_ayv_v2f_xdb .section}

1.  In the RAM console, click **Policies** from the left-side navigation pane. On the **Policy Management** page, you can view the existing systems and custom policies through the **System Policy** and **Custom Policy** subpages, respectively.

    ![](images/3536_en-US.png "Custom authorization policy")

2.  Click **Create Authorization Policy** to go to the **Create Authorization Policy** page.
3.  Select the policy template.

    **Note:** You can select a blank template, but it is recommended that you use a similar existing system policy as a template for editing. The policy AliyunOSSReadOnlyAccess \(the read-only permission for all OSS resources under the account\) is used as the template here.

    ![](images/3539_en-US.png "Create an authorization policy")

4.  Edit your policy based on the selected template.
5.  Once finishing all the settings, click **New Authorization Policy** to complete creating the custom authorization policy.

    ![](images/3541_en-US.png "New authorization policy")


Here, the **Authorization policy name**, **Remarks**, and **Policy content** are modified. The highlighted part of the **Policy content** is the added fine-grained authorization content. The code sample is:

```

```json
{
"Version": "1",
"Statement": [
{
"Effect": "Allow",
"Action": [
"oss:Get*",
"oss:List*"
],
"Resource": [
"acs:oss:*:*:samplebucket/bob/*"
],
"Condition": {
"IpAddress": {
"acs:SourceIp": "121.0.27.1"
}
}
}
]
}

```

```

## Subsequent operation {#section_cfx_w2f_xdb .section}

Next, simply authorize the policy created in this document to user Bob, and Bob will have the read-only permission for the objects in  `oss://samplebucket/bob/`, allowing access of the IP address \(121.0.27.1\) only from your company network.

Assign the authorization policy to the RAM user. For details, see [Attach policies to a RAM user](intl.en-US/Quick Start/Attach policies to a RAM user.md).

