# RDS authorization policy samples {#concept_e4d_ssx_ydb .concept}

If your tenant account has 10 RDS instances,  but as a RAM administrator, you would like to grant only two instances to a RAM user. You can create a policy as follows:

**Note:** One RAM user with this policy can view all RDS instances, but can only operate \(for example, DeleteDBInstance\) the granted two instances.  Currently, RAM does not support to view only the authorized RDS instances.

```

  "Statement ":[
    
      "Action": "RDS :*",
      "Effect": "allow ",
      "Resource ":[
                  "ACS: RDS: *: dbinstance/i-001 ",
                  "ACS: RDS: *: dbinstance/i-002"
                  
    
    
      "Action": "RDS: Describe *",
      "Effect": "allow ",
      "Resource ":"*"
    
  
  "Version": "1"

```

