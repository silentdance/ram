# Samples {#reference_zlx_mzy_xdb .concept}

This topic provides an operation example.

``` {#codeblock_slg_1n3_oav}
using System;
using Aliyun.Acs.Core;
using Aliyun.Acs.Core.Profile;
using Aliyun.Acs.Core.Http;
using Aliyun.Acs.Sts.Model.V20150401;
namespace StsNetSdkDemo

    class Program

        static void Main(string[] args)

            const string REGIONID = "cn-shanghai";
            const string ENDPOINT = "sts.cn-shanghai.aliyuncs.com";
            // Construct an Aliyun Client for initiating a request
            // Set AccessKeyID and AccessKeySevcret when constructing the Aliyun Client
            DefaultProfile.AddEndpoint(REGIONID, REGIONID, "Sts", ENDPOINT);
            IClientProfile profile = DefaultProfile.GetProfile(REGIONID, "<access-key-id>", "<access-key-secret>");
            DefaultAcsClient client = new DefaultAcsClient(profile);
            // Construct an "AssumeRole" request
            AssumeRoleRequest request = new AssumeRoleRequest();
            request.AcceptFormat = FormatType.JSON;
            // Specify the role Arn
            request.RoleArn = "<role-arn>";
            request.RoleSessionName = "<role-session-name>";
            // Set the Token's period of validity. It is an optional parameter with a default value of 3,600s.
            // request.DurationSeconds = 3600;
            // Set an additional policy for the Token so as to further limit the Token permission when obtaining the token.
            // request.Policy="<policy-content>"
            try

                AssumeRoleResponse response = client.GetAcsResponse(request);
                Console.WriteLine("AccessKeyId: " + response.Credentials.AccessKeyId);
                Console.WriteLine("AccessKeySecret: " + response.Credentials.AccessKeySecret);
                Console.WriteLine("SecurityToken: " + response.Credentials.SecurityToken);
                // Token expiration time, and time for the server to return UTC, which is displayed in Beijing Time.
                Console.WriteLine("Expiration: " + DateTime.Parse(response.Credentials.Expiration). ToLocalTime());

            catch (Exception ex)

                Console.Write(ex.ToString());

            Console.ReadLine();


		
```

**Note:** 

-   For information about STS endpoints, see [Endpoints](../../../../reseller.en-US/API Reference (STS)/Calling method/Endpoints.md#).
-   For information about the AssumeRole action, see [AssumeRole](../../../../reseller.en-US/API Reference (STS)/Operation interfaces/AssumeRole.md#).

