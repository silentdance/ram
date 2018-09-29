# Authorization for RDS instances {#concept_zqh_gqx_ydb .concept}

## Questions {#section_x1f_w4x_ydb .section}

-   [View RDS permission definitions](#section_mzy_x4x_ydb)
-   [Assign the RDS read-only permission to a RAM user](#section_jft_y4x_ydb)
-   [Assign full RDS service management permissions to a RAM user](#section_fnn_z4x_ydb)
-   [Authorize a RAM user to manage two specified RDS instances](#section_jpq_1px_ydb)
-   [Access the content of the DMS management database as a RAM user](#section_a1c_cpx_ydb)

## View RDS permission definitions {#section_mzy_x4x_ydb .section}

See RDS resource authorization.

## Assign the RDS read-only permission to a RAM user {#section_jft_y4x_ydb .section}

Create a RAM user in the RAM console and add the system authorization policy ”AliyunRDSReadOnlyAccess” to the user. For more information about how to add an authorization policy, see [Authorization](../../../../reseller.en-US/User Guide/Authorization/Authorization.md).

## Assign full RDS service management permissions to a RAM user {#section_fnn_z4x_ydb .section}

Add the system authorization policy “AliyunRDSFullAccess” to the RAM user in the RAM console.

## **Authorize a RAM user to manage two specified RDS instances** {#section_jpq_1px_ydb .section}

You must use the function of customizing authorization policies. For example, you have two instances and the IDs are i-001 and i-002:

First, you must create a custom authorization policy that includes permissions for managing i-001 and i-002 and viewing all RDS resources:

```

  "Statement": [
    
      "Action": "rds:*",
      "Effect": "Allow",
      "Resource": [
                  "acs:rds:*:*:dbinstance/i-001",
                  "acs:rds:*:*:dbinstance/i-002"
                  
    
    
      "Action": "rds:Describe*",
      "Effect": "Allow",
      "Resource": "*"
    
  
  "Version": "1"

```

Then, add the custom authorization policy for this user.

## Access the content of the DMS management database as a RAM user {#section_a1c_cpx_ydb .section}

Access ApsaraDB for RDS through DMS. The corresponding authorization action is  “dms:LoginDatabase”.

**Authorize the RAM user to log on to the specified RDS instance**

Authorization policy example:

```

  "Statement": [
    
      "Action": "dms:LoginDatabase",
      "Effect": "Allow",
      "Resource": "acs:rds:*:*:dbinstance/rds783a0639ks5k7328y"
    
  
  "Version": "1"

```

Replace `rds783a0639ks5k7328y` with the ID of the RDS instance to be accessed.

**Authorize the RAM user to log on to all RDS instances**

Authorization policy example:

```

  "Statement": [
    
      "Action": "dms:LoginDatabase",
      "Effect": "Allow",
      "Resource": "acs:rds:*:*:*"
    
  
  "Version": "1"

```

