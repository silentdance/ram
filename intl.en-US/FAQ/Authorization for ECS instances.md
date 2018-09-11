# Authorization for ECS instances {#concept_k1k_r4x_ydb .concept}

## Questions {#section_x1f_w4x_ydb .section}

-   [View ECS permission definitions](#section_mzy_x4x_ydb)
-   [Assign full ECS service management permissions to a subaccount](#section_jft_y4x_ydb)
-   [Assign the ECS read-only permission to a subaccount](#section_fnn_z4x_ydb)
-   [Allow a RAM user to view ECS instances in the Qingdao region but disallow the user to view disk or snapshot information](#section_jpq_1px_ydb)
-   [Authorize a RAM user to manage two specified ECS instances](#section_a1c_cpx_ydb)
-   [Authorize a RAM user to create snapshots](#section_ecc_2px_ydb)

## View ECS permission definitions {#section_mzy_x4x_ydb .section}

See [Authorization rules](../../../../intl.en-US/API Reference/Authorization rules.md) in the ECS OpenAPI document.

## Assign full ECS service management permissions to a subaccount {#section_jft_y4x_ydb .section}

Add the system authorization policy “AliyunECSFullAccess” to the subaccount \(or the group to which the subaccount belongs\) on the RAM console. 

## Assign the ECS read-only permission to a subaccount {#section_fnn_z4x_ydb .section}

Create a subaccount on the RAM console and add the system authorization policy “AliyunECSReadOnlyAccess” to the subaccount. 

For more information about how to add an authorization policy, see [Authorization](../../../../intl.en-US/User Guide/Authorization/Authorization.md). 

## Allow a RAM user to view ECS instances in the Qingdao region but disallow the user to view disk or snapshot information {#section_jpq_1px_ydb .section}

The permission for viewing ECS resource lists can be assigned based on region and resource type. 

The following example describes how to authorize a subaccount to view only ECS instance information in the Qingdao region.

```

  "Statement": [
    
      "Effect": "Allow",
      "Action": "ecs:DescribeRegions",
      "Resource": "*"
    
    
      "Effect": "Allow",
      "Action": "ecs:Describe*",
      "Resource": "acs:ecs:cn-qingdao:*:instance/*"
    
  
  "Version": "1"

```

## Authorize a RAM user to manage two specified ECS instances {#section_a1c_cpx_ydb .section}

Assume that 10 ECS instances have been bought under your tenant account.  As a RAM administrator, you want to authorize a RAM user to use only two of the ECS instances.  In this case, you can create the following authorization policy:

**Note:** he authorized RAM user can view all the ECS instances but can perform operations \(such as the StopInstance operation\) on only two of them.  Currently, you cannot authorize a RAM user to view only the ECS  instances that the user can operate. 

Assume that the IDs of your ECS instances are i-001 and i-002. You must first create an authorization policy, which includes the permissions for managing i-001 and i-002 and viewing  all ECS resources. 

```

  "Statement": [
    
      "Action": "ecs:*",
      "Effect": "Allow",
      "Resource": [
                  "acs:ecs:*:*:instance/i-001",
                  "acs:ecs:*:*:instance/i-002"
                  
    
    
      "Action": "ecs:Describe*",
      "Effect": "Allow",
      "Resource": "*"
    
  
  "Version": "1"

```

Then, add the authorization policy for the user.

## Authorize a RAM user to create snapshots {#section_ecc_2px_ydb .section}

If a RAM user cannot create disk snapshots after being assigned the ECS administrator permissions, you must assign disk permissions to the user because snapshots are created based on disks. 

Assume that you want to authorize the RAM user to manage the ECS instance whose ID is inst-01, and  to create snapshots for the disk whose ID is dist-01.  In this case, you can create the following authorization policy:

```

  "Statement": [
    
      "Action": "ecs:*",
      "Effect": "Allow",
      "Resource": [
        "acs:ecs:*:*:instance/inst-01"
      
    
    
      "Action": "ecs:CreateSnapshot",
      "Effect": "Allow",
      "Resource": [
        "acs:ecs:*:*:disk/dist-01",
        "acs:ecs:*:*:snapshot/*"
      
    
    
      "Action": [
        "ecs:Describe*"
      
      "Effect": "Allow",
      "Resource": "*"
    
  
  "Version": "1"

```

Then, add the authorization policy for the user.

