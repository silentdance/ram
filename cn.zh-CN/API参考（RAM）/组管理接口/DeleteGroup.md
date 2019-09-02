# DeleteGroup {#doc_api_Ram_DeleteGroup .reference}

调用DeleteGroup接口删除指定的用户组。

-   删除用户组前，需要确保用户组没有绑定任何权限策略。
-   删除用户组前，需要确保用户组内没有用户。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ram&api=DeleteGroup&type=RPC&version=2015-05-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteGroup|系统规定参数。取值：DeleteGroup

 |
|GroupName|String|是|Dev-Team|指定用户组名称。

 格式：`^[a-zA-Z0-9\-]+$`。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|FCF40AB5-881C-A0F9-334C-B0AD423AA69D|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=DeleteGroup
&GroupName=Dev-Team
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteGroupResponse>
      <RequestId>FCF40AB5-881C-A0F9-334C-B0AD423AA69D</RequestId>
</DeleteGroupResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"FCF40AB5-881C-A0F9-334C-B0AD423AA69D"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ram)查看更多错误码。

