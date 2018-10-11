# SLB authorization policy samples {#concept_e1s_1tx_ydb .concept}

-   Use Case \#1

    Suppose your tenant account has 10 Server Load Balancer instances. As a RAM administrator, you want to grant only two Server Load Balancer instances to a RAM user. Then, you can create a policy as follows:

    **Note:** One RAM user with this policy can view all Server Load Balancer instances, but can only operate \(for example, DeleteLoadBalancer\) the granted two Server Load Balancer instances. Currently, RAM does not support to view only the authorized Server Load Balancer instances.

    ```
    
      "Statement ":[
        
          "Effect": "Allow",
          "Action": "slb:*",
          "Resource ":[
                      "acs:slb:*:*:loadbalancer/i-001",
                      "acs:slb:*:*:loadbalancer/i-002"
                      
        
        
          "Effect": "Allow",
          "Action": "slb:Describe*",
          "Resource": "*"
        
      
      "Version": "1"
    
    ```

-   Use Case \#2

    A RAM user adds a backend ECS server \(for example, i-001\) to a Server Load Balancer instance \(for example, slb-001\). The detailed policy is allows:

    ```
    
      "Statement": [
        
          "Effect": "Allow",
          "Action": "slb:AddBackendServers",
          "Resource": ["acs:slb:*:*:loadbalancer/slb-001"]
        
        
          "Effect": "Allow",
          "Action": "slb:AddBackendServers",
          "Resource": "acs:ecs:*:*:instance/i-001"
        
      
      "Version": "1"
    
    ```

-   Use Case \#3

    A RAM user adds any backend ECS server in your tenant account to a Server Load Balancer instance \(for example, slb-001\). The detailed policy is allows:

    ```
    
      "Statement": [
        
          "Effect": "Allow",
          "Action": "slb:*",
          "Resource": ["acs:slb:*:*:loadbalancer/slb-001"]
        
        
          "Effect": "Allow",
          "Action": "slb:Describe*",
          "Resource": "*"
        
        
          "Effect": "Allow",
          "Action": "slb:*",
          "Resource": "acs:ecs:*:*:*"
        
      
      "Version": "1"
    
    ```


