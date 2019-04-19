# Manage CDN permissions by using RAM {#concept_g2m_jrx_ydb .concept}

This topic describes how to manage CDN permissions of RAM users by creating policies in RAM.

## Common policies {#section_z0z_j1e_501 .section}

The following table lists some common policies that can be created in RAM to manage CDN permissions.

|Policy|Description|
|:-----|:----------|
|AliyunCDNFullAccess|Grants a RAM user full management permissions for CDN instances.|
|AliyunCDNReadOnlyAccess|Grants a RAM user read-only permission for CDN instances.|

**Note:** For more information about CDN permissions, see [API authentication rules](../../../../reseller.en-US/API Reference/RAM Resource Authorization/API authentication rules.md#).

## Authorize a RAM user to perform the read-only, cache refresh, and push operations on CDN instances {#section_abd_dzq_e5i .section}

1.  Create a custom policy.

    ```
    {
      "Version": "1",
      "Statement": [
        {
          "Action": [
            "cdn:Describe*",
            "cdn:PushObjectCache",
            "cdn:RefreshObjectCaches"
          ],
          "Resource": "acs:cdn:*:*:*",
          "Effect": "Allow"
        }
      ]
    }
    ```

    For more information, see [Policy management](../../../../reseller.en-US/User Guide/Permission management/Policy management.md#).

2.  Locate the target policy and click the policy name.
3.  On the **References** tab, click **Grant Permission**.
4.  In the **Principal** field, enter the ID or name of the target RAM user.
5.  Click **OK**.

    **Note:** You can also attach policies to a RAM user or a RAM user group as needed. For more information, see [Permission granting in RAM](../../../../reseller.en-US/User Guide/Permission management/Permission granting/Permission granting in RAM.md#).


