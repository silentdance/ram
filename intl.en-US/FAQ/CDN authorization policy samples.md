# CDN authorization policy samples {#concept_n3d_2tx_ydb .concept}

The following policy allows a RAM user to perform READ, Push, and Refresh operations on CDN resources. 

```

  "Version": "1",
  "Statement": [
    
      "Action": [
        "cdn:Describe*",
        "cdn:PushObjectCache",
        "cdn:RefreshObjectCaches"
      
      "Resource": "acs:cdn:*:*:*",
      "Effect": "allow"
    
  

```

