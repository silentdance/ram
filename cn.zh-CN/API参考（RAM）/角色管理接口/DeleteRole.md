# DeleteRole {#doc_api_Ram_DeleteRole .reference}

调用DeleteRole接口删除指定的角色。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ram&api=DeleteRole&type=RPC&version=2015-05-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteRole|系统规定参数。取值：DeleteRole

 |
|RoleName|String|是|ECSAdmin|指定角色名称。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|898FAB24-7509-43EE-A287-086FE4C44394|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=DeleteRole
&RoleName=ECSAdmin
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteRoleResponse>
      <RequestId>898FAB24-7509-43EE-A287-086FE4C44394</RequestId>
</DeleteRoleResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"898FAB24-7509-43EE-A287-086FE4C44394"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/Ram)查看更多错误码。

