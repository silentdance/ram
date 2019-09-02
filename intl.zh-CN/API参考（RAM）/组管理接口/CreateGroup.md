# CreateGroup {#doc_api_Ram_CreateGroup .reference}

调用CreateGroup接口创建用户组。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ram&api=CreateGroup&type=RPC&version=2015-05-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateGroup|系统规定参数。取值：CreateGroup

 |
|Comments|String|否|开发团队|备注信息，最大长度128个字符。

 |
|GroupName|String|否|Dev-Team|用户组名称，最大长度64个字符。

 格式：`^[a-zA-Z0-9\-]+$`。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Group| | |用户组信息。

 |
|Comments|String|开发团队|备注信息。

 |
|CreateDate|String|2015-01-23T12:33:18Z|创建时间。

 |
|GroupName|String|Dev-Team|用户组名称。

 |
|RequestId|String|D3F0679E-9757-95DB-AF2D-04D5188C69C5|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=CreateGroup
&GroupName=Dev-Team
&Comments=开发团队
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateGroupResponse>
      <RequestId>D3F0679E-9757-95DB-AF2D-04D5188C69C5</RequestId>
      <Group>
            <GroupName>Dev-Team</GroupName>
            <Comments>开发团队</Comments>
            <CreateDate>2015-01-23T12:33:18Z</CreateDate>
      </Group>
</CreateGroupResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"D3F0679E-9757-95DB-AF2D-04D5188C69C5",
	"Group":{
		"Comments":"开发团队",
		"GroupName":"Dev-Team",
		"CreateDate":"2015-01-23T12:33:18Z"
	}
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ram)查看更多错误码。

