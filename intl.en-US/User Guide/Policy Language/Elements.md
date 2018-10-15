# Elements {#concept_xg5_51g_xdb .concept}

RAM uses an authorization policy to describe the content of authorization. The basic elements in an authorization policy include Effect, Resource, Action, and Condition.

## Effect {#section_inm_v1g_xdb .section}

Effects can be categorized into two types: Allow and Deny.

## Resource {#section_jnm_v1g_xdb .section}

Resources are specific authorized objects.

For example, in the authorization policy “User A is allowed to perform the GetBucket operation on the resource SampleBucket”, the resource is “SampleBucket”.

## Action {#section_knm_v1g_xdb .section}

Actions are operations performed on specific resources.

For example, in the authorization policy “User A is allowed to perform the GetBucket operation on the resource SampleBucket”, the action is “GetBucket”.

## Condition {#section_lnm_v1g_xdb .section}

Condition are the circumstances under which the authorization takes effect.

For example, in the authorization policy “User A is allowed to perform the GetBucket operation on the resource SampleBucket before 2011-12-31”, the condition is “before 2011-12-31”.

## Example {#section_mnm_v1g_xdb .section}

This example authorization policy can be explained as follows: read-only operations on the OSS bucket samplebucket are allowed on the condition that the source IP address of the requester is 42.160.1.0.

```


      "Version": "1",
      "Statement":
        
          "Effect": "Allow",
            "Action": ["oss:List*", "oss:Get*"],
            "Resource": ["acs:oss:*:*:samplebucket", "acs:oss:*:*:samplebucket/*"],
            "Condition":
             
                "IpAddress":
                 
                    "acs:SourceIp": "42.160.1.0"
                  }
              
         

```

