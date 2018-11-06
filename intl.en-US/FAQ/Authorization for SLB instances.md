# Authorization for SLB instances {#concept_qhc_xqx_ydb .concept}

## Questions {#section_x1f_w4x_ydb .section}

-   [View SLB permission definitions](#)
-   [Assign the SLB read-only permission to a RAM user](#)
-   [Assign the SLB full access permission to a RAM user](#)
-   [Authorize a RAM user to manage two specified SLB instances](#)
-   [A RAM user authorized to manage an SLB instance is notified of no operation permission when the user adds or removes ECS servers in the instance or sets weights](#)

## View SLB permission definitions {#section_mzy_x4x_ydb .section}

See [RAM authentication](../../../../reseller.en-US/Developer Guide/RAM authentication.md) in the SLB OpenAPI document.

## Assign the SLB read-only permission to a RAM user {#section_jft_y4x_ydb .section}

Create a RAM user in the RAM console and add the system authorization policy “AliyunSLBReadOnlyAccess” to the user. For more information about how to add an authorization policy, see [Authorization](../../../../reseller.en-US/User Guide/Authorization/Authorization.md).

## Assign the SLB full access permission to a RAM user {#section_fnn_z4x_ydb .section}

Add the system authorization policy  “AliyunSLBFullAccess” to the RAM user in the RAM console.

## **Authorize a RAM user to manage two specified SLB instances** {#section_jpq_1px_ydb .section}

You must use the function of customizing authorization policies. For example, you have two instances and the IDs are i-001 and i-002:

First, you must create a custom authorization policy that includes permissions for managing i-001 and i-002 and viewing all SLB resources:

```

  "Statement": [
    
      "Effect": "Allow",
      "Action": "slb:*",
      "Resource": [
                  "acs:slb:*:*:loadbalancer/i-001",
                  "acs:slb:*:*:loadbalancer/i-002"
                  
    
    
      "Effect": "Allow",
      "Action": "slb:Describe*",
      "Resource": "*"
    
  
  "Version": "1"

```

Then, add the authorization policy for this user.

## A RAM user authorized to manage an SLB instance is notified of no operation permission when the user adds or removes ECS servers in the instance or sets weights {#section_a1c_cpx_ydb .section}

In the SLB, ECS server operation interfaces check not only the permissions for SLB resources, but also the permissions for ECS servers. This eliminates the situations in which a RAM user arbitrarily adds servers to an SLB instance after obtaining the permission for the instance.

For example, if you want to add the i-001 ECS server to the slb-001 SLB, you must grant the following permissions to your account:

```

  "Statement": [
    
      "Effect": "Allow",
      "Action": "slb:AddBackendServers",
      "Resource": ["acs:slb:*:*:loadbalancer/slb-001"]
    
    
      "Effect": "Allow",
      "Action": "slb:AddBackendServers",
      "Resource": ["acs:ecs:*:*:instance/i-001"]
    
    
        "Effect": "Allow",
        "Action": "slb:DescribeLoadBalancers",
        "Resource": "acs:slb:*:*:loadbalancer/*"
    
  
  "Version": "1"

```

You can make the authorization process more efficient so that you can grant management permissions for one SLB instance. This allows a user to add any servers to the instance and set the weight of any instances. See the following authorization policy. This authorization policy adds permissions for operations on all the SLB instances to the ECS resource.

```

  "Statement": [
    
      "Effect": "Allow",
      "Action": "slb:*",
      "Resource": [
                  "acs:slb:*:*:loadbalancer/i-001",
                  "acs:slb:*:*:loadbalancer/i-002"
                  
    
    
      "Effect": "Allow",
      "Action": "slb:Describe*",
      "Resource": "*"
    
    
      "Effect": "Allow",
      "Action": "slb:*",
      "Resource": "acs:ecs:*:*:*"
    
  
  "Version": "1"

```

