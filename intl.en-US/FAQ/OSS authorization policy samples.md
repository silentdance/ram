# OSS authorization policy samples {#concept_z1z_jsx_ydb .concept}

-   Use Case \#1

    The following policy sample allows a RAM user to do READ operations on a specified OSS bucket \(for example, myphotos\) through the OSS  web console. 

    ```
    
        "Version": "1",
        "Statement": [
        
            "Effect": "Allow",
            "Action": "oss:ListBuckets",
            "Resource": "acs:oss:*:*:*"
        
        
            "Effect": "Allow",
            "Action": [
                "oss:ListObjects",
                "oss:GetBucketAcl"
            
            "Resource": "acs:oss:*:*:myphotos"
        
        
            "Effect": "Allow",
            "Action": [
                "oss:GetObject",
                "oss:GetObjectAcl"
            
            "Resource": "acs:oss:*:*:myphotos/*"
        
      
    
    ```

-   Use Case \#2

    The following policy sample allows a RAM user to do READ operations on a specified OSS bucket \(for example, myphotos\) through the OSS SDK, where the Source IP address of an HTTP request must be “42.120.88.18” or "42.120.66.0/24 ".

    ```
    
        "Version": "1",
        "Statement": [
            
                "Effect": "Allow",
                "Action": [
                    "oss:ListBuckets"
                
                "Resource": [
                    "acs:oss:*:*:*"
                
            
            
                "Effect": "Allow",
                "Action": [
                    "oss:ListObjects",
                    "oss:GetObject"
                
                "Resource": [
                    "acs:oss:*:*:myphotos",
                    "acs:oss:*:*:myphotos/*"
                
                "Condition":{
                    "IpAddress": {
                        "acs:SourceIp": ["42.120.88.18", "42.120.66.0/24"]
                    
                
            
        
    
    ```

-   Use Case \#3

    The following policy sample allows a RAM user to do READ operations on a specified OSS path \(for example, myphotos/hangzhou/2015/\) through the OSS web console. 

    ```
    
        "Version": "1",
        "Statement": [
            
                "Effect": "Allow",
                "Action": [
                    "oss:ListBuckets",
                    "oss:GetBucketAcl"
                
                "Resource": [
                    "acs:oss:*:*:*"
                
            
            
                "Effect": "Allow",
                "Action": [
                    "oss:GetObject",
                    "oss:GetObjectAcl"
                
                "Resource": [
                    "acs:oss:*:*:myphotos/hangzhou/2015/*"
                
            
            
                "Effect": "Allow",
                "Action ":[
                    "oss:ListObjects"
                
                "Resource": [
                    "acs:oss:*:*:myphotos"
                
                "Condition": {
                    "StringLike": {
                        "oss:Delimiter": "/",
                        "oss:Prefix": [
                            
                            "hangzhou/",
                            "hangzhou/2015/*"
                        
                    
                
            
        
    
    ```


