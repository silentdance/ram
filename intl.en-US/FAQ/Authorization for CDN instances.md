# Authorization for CDN instances {#concept_g2m_jrx_ydb .concept}

## Questions {#section_x1f_w4x_ydb .section}

[Authorize a RAM user to perform the cache refresh and push operations](#)

## Authorize a RAM user to perform the cache refresh and push operations {#section_mzy_x4x_ydb .section}

You can create the following authorization policy for the user, which includes the permissions for reading content from CDN, refreshing the cache, and performing the push operation.

```

  "Version": "1",
  "Statement": [
    
      "Action": [
        "cdn:Describe*",
        "cdn:PushObjectCache",
        "cdn:RefreshObjectCaches"
      
      "Resource": "acs:cdn:*:*:*",
      "Effect": "Allow"
    
  

```

Then, assign the authorization policy to this user.

