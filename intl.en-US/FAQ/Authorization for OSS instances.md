# Authorization for OSS instances {#concept_ohn_ypx_ydb .concept}

## Questions {#section_x1f_w4x_ydb .section}

-   [View OSS permission definitions](#section_mzy_x4x_ydb)
-   [Assign the OSS read-only permission to a RAM user](#section_jft_y4x_ydb)
-   [Assign the full OSS management permission to a RAM user](#section_fnn_z4x_ydb)
-   [Authorize a RAM user to list and read resources in a bucket](#section_jpq_1px_ydb)
-   [Authorize a RAM user full management of a bucket](#section_a1c_cpx_ydb)

## View OSS permission definitions {#section_mzy_x4x_ydb .section}

See [Access control](../../../../intl.en-US/Developer Guide/Access and control/Access control.md) in OSS documentation. 

## Assign the OSS read-only permission to a RAM user {#section_jft_y4x_ydb .section}

Create a RAM user in the RAM console and add the system authorization policy AliyunOSSReadOnlyAccess to the user.  For more information about how to add an authorization policy, see [Authorization](../../../../intl.en-US/User Guide/Authorization/Authorization.md). 

## Assign the full OSS management permission to a RAM user {#section_fnn_z4x_ydb .section}

Add the system authorization policy AliyunOSSFullAccess to the RAM user in the RAM console. 

## Authorize a RAM user to list and read resources in a bucket {#section_jpq_1px_ydb .section}

If it is necessary to authorize a RAM user \(for example, an application that represents you\) to list and read the resources in a bucket using the OSS SDK or OSS CMD, you must create an authorization policy. 

Assume that your bucket is named "myphotos." Create the authorization policy as follows: 

```

    "Version": "1",
    "Statement": [
        
            "Effect": "Allow",
            "Action": "oss:ListObjects",
            "Resource": "acs:oss:*:*:myphotos"
        
        
            "Effect": "Allow",
            "Action": "oss:GetObject",
            "Resource": "ACS: OSS: *: myphotos /*"
        
    

```

If you want the authorized RAM user to perform operations in the OSS console, add the GetBucketAcl and GetObjectAcl permissions to the authorization policy. \(The console needs to call additional OSS APIs to optimize the operation experience.\)  The following provides an example of the authorization policy that allows the RAM user to perform operations in the OSS console:

```

    "Version": "1",
    "Statement": [
        
            "Effect": "Allow",
            "Action": "oss:ListBuckets",
            "Resource": "acs:oss:*:*:*"
        
        
            "Effect": "Allow",
            "Action ":[
                "oss:ListObjects",
                "oss:GetBucketAcl"
            
            "Resource": "acs:oss:*:*:myphotos"
        
        
            "Effect": "Allow",
            "Action ":[
                "oss:GetObject",
                "oss:GetObjectAcl"
            
            "Resource": "ACS: OSS: *: myphotos /*"
        
    

```

## Authorize a RAM user full management of a bucket {#section_a1c_cpx_ydb .section}

You must create an authorization policy first.  Assume that your bucket is named "myphotos."  Create the authorization policy as follows:

```

    "Version": "1",
    "Statement ":[
        
            "Effect": "Allow",
            "Action": "oss:*",
            "Resource ":[
                "acs:oss:*:*:myphotos",
                "acs:oss:*:*:myphotos/*"
            
        
    

```

