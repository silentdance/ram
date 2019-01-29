# UnbindMFADevice {#doc_api_977697 .reference}

解绑多因素认证设备。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=UnbindMFADevice)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UnbindMFADevice|系统规定参数。取值：UnbindMFADevice

 |
|UserName|String|是|zhangqiang|指定用户名。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|MFADevice| | |MFA设备信息。

 |
|└SerialNumber|String|acs:ram::1234567890123:mfa/device002|设备序列号。

 |
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=UnbindMFADevice
&UserName=zhangqiang
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<UnbindMFADeviceResponse>
  <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
  <MFADevice>
    <SerialNumber>acs:ram::1234567890123:mfa/device002</SerialNumber>
  </MFADevice>
</UnbindMFADeviceResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368",
	"MFADevice":{
		"SerialNumber":"acs:ram::1234567890123:mfa/device002"
	}
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ram)

