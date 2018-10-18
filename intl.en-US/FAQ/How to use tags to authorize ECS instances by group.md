# How to use tags to authorize ECS instances by group {#concept_acb_stx_ydb .concept}

Suppose you have 10 ECS instances. You want to authorize 5 of them to the dev team and another 5 to the ops team.  You want each team to see only authorized instances. 

## Authorize ECS instances by group {#section_ckj_gtx_ydb .section}

You can implement this function with RAM.  Specific operations are as follows: 

1.  Tag ECS instances by group.  For example, tag 5 of them with the key as team and the value as dev;  tag another 5 with the key as team and the value as ops. 

    Tag one instance as follows:

    1.  In the ECS console, choose an instance and click the corresponding drop-down menu **More** on the Instances sub-page. 

        ![](images/4446_en-US.png "Select an instance")

    2.  Select **Edit Tag** from the drop-down menu.

        ![](images/4447_en-US.png "Edit a tag")

    3.  In the **Edit Tag** dialog box, click Create and then set key and value.  Here, we set key to team and value to dev. 

         ![](images/4449_en-US.png "Replace the tag key and tag value") 

2.  Create two user groups, such as dev and ops.  Then create corresponding user accounts for your employees and add different user accounts to different user groups. 
3.  Create two custom authorization policies and assign them to different user groups. 

    For example, the name of the custom authorization policy assigned to the dev group is policyForDevTeam. The policy content is as follows:

    ```
    
        "Statement": [
        
            "Action": "ecs:*",
            "Effect": "Allow",
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "ecs:tag/team": "dev"
                }
            
        
        
            "Action": "ecs:DescribeTag*",
            "Effect": "Allow",
            "Resource": "*"
        
        
        "Version": "1"
    
    ```

    **Note:** If your custom tag is different from the one in the preceding example, replace the description of the tag conditions in the example accordingly.

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/67912/cn_zh/1520426257196/4.png)


## Display authorized instances {#section_lkt_ktx_ydb .section}

1.  If no instance is displayed after you log on to the ECS console, click **Tag** on the Instances sub-page. 
2.  Select the specified Tag Key to display authorized instances.

