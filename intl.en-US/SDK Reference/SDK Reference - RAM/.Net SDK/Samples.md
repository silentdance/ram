# Samples {#reference_s1y_dvv_xdb .reference}

``` {#codeblock_gxv_w6x_uud}
using System;
using Aliyun.Acs.Core;
using Aliyun.Acs.Core.Profile;
using Aliyun.Acs.Ram.Model.V20150501;

namespace ram_net_sdk_sample

    class Program

        static void Main(string[] args)

            // Construct an Aliyun Client for initiating a request
            // Set AccessKeyID and AccessKeySecret when constructing the Aliyun Client
            // RAM is a Global Service, and its API ingress is located in the East China 1 (Hangzhou) region. Enter "cn-hangzhou" in "Region"
            IClientProfile profile = DefaultProfile.GetProfile("cn-hangzhou", "<access-key-id>", "<access-key-secret>");
            DefaultAcsClient client = new DefaultAcsClient(profile);


            // Construct a "CreateUser" request
            CreateUserRequest request = new CreateUserRequest();

            //Set the parameter - UserName
            request.UserName = "alice";

            // Initiate a request and obtain the response
            try

                CreateUserResponse response = client.GetAcsResponse(request);

                Console.WriteLine("UserName: " + response.User.UserName);
                Console.WriteLine("CreateTime: " + response.User.CreateDate);

            catch (Exception ex)

                Console.Write(ex.ToString());

            Console.ReadLine();



			
```

