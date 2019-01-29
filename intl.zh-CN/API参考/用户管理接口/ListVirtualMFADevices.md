# ListVirtualMFADevices {#doc_api_977679 .reference}

列出虚拟多因素认证设备。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=ListVirtualMFADevices)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListVirtualMFADevices|系统规定参数。取值：ListVirtualMFADevices

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|请求ID。

 |
|VirtualMFADevices| | |虚拟MFA设备列表。

 |
|└ActivateDate|String|2015-02-18T17:22:08Z|激活日期。

 |
|└SerialNumber|String|acs:ram::1234567890123:mfa/device002|设备序列号。

 |
|└User| | |绑定用户的基本信息。

 |
|└DisplayName|String|张强|显示名称。

 |
|└UserId|String|1227489245380721|用户唯一标识。

 |
|└UserName|String|zhangqiang|用户名称。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=ListVirtualMFADevices
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ListVirtualMFADevicesResponse>
    <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
    <VirtualMFADevices>
        <VirtualMFADevice>
            <SerialNumber>acs:ram::1234567890123:mfa/device001</SerialNumber>
        </VirtualMFADevice>
        <VirtualMFADevice>
            <SerialNumber>acs:ram::1234567890123:mfa/device002</MFASerialNumber>
            <ActivateDate>2015-02-18T17:22:08Z<Activate>
            <User>
                <UserId>1227489245380721</UserId>
                <UserName>zhangqiang</UserName>
                <DisplayName>张强</DisplayName>
            </User>
        </VirtualMFADevice>
    <VirtualMFADevicess>
</ListVirtualMFADevicesResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368",
	"VirtualMFADevices":{
		"VirtualMFADevice":[
			{
				"SerialNumber":"acs:ram::1234567890123:mfa/device001"
			},
			{
				"User":{
					"UserName":"zhangqiang",
					"UserId":"1227489245380721",
					"DisplayName":"张强"
				},
				"SerialNumber":"acs:ram::1234567890123:mfa/device002",
				"ActivateDate":"2015-02-18T17:22:08Z"
			}
		]
	}
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ram)

