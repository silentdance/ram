# AttachPolicyToRole {#doc_api_Ram_AttachPolicyToRole .reference}

调用AttachPolicyToRole接口为指定角色添加权限。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ram&api=AttachPolicyToRole&type=RPC&version=2015-05-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AttachPolicyToRole|系统规定参数。取值：AttachPolicyToRole

 |
|PolicyName|String|是|OSS-Administrator|指定权限策略名称。

 |
|PolicyType|String|是|Custom|指定权限策略的类型, 取值为：`System`或`Custom`。

 |
|RoleName|String|是|OSSAdminRole|指定角色名。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|697852FB-50D7-44D9-9774-530C31EAC572|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=AttachPolicyToRole
&PolicyType=Custom
&PolicyName=OSS-Administrator
&RoleName=OSSAdminRole
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AttachPolicyToRoleResponse>
      <RequestId>697852FB-50D7-44D9-9774-530C31EAC572</RequestId>
</AttachPolicyToRoleResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"697852FB-50D7-44D9-9774-530C31EAC572"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/Ram)查看更多错误码。

