# AddUserToGroup {#doc_api_Ram_AddUserToGroup .reference}

调用AddUserToGroup接口将RAM用户添加到指定的用户组。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ram&api=AddUserToGroup&type=RPC&version=2015-05-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddUserToGroup|系统规定参数。取值：AddUserToGroup。

 |
|GroupName|String|是|Dev-Team|用户组名称。

 |
|UserName|String|是|zhangq\*\*\*\*|用户名称。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|1B968853-B423-63A6-FE1F-45E81BC2AD61|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=AddUserToGroup
&UserName=zhangq****
&GroupName=Dev-Team
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AddUserToGroupResponse>
      <RequestId>1B968853-B423-63A6-FE1F-45E81BC2AD61</RequestId>
</AddUserToGroupResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"1B968853-B423-63A6-FE1F-45E81BC2AD61"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/Ram)查看更多错误码。

