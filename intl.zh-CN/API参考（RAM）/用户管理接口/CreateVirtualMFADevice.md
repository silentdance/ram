# CreateVirtualMFADevice {#doc_api_Ram_CreateVirtualMFADevice .reference}

调用CreateVirtualMFADevice接口创建多因素认证设备。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=CreateVirtualMFADevice)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateVirtualMFADevice|系统规定参数。取值：CreateVirtualMFADevice

 |
|VirtualMFADeviceName|String|是|device001|指定设备名称, 最大长度64个字符。

 限制：`[a-zA-Z0-9-]*`。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|请求ID。

 |
|VirtualMFADevice| | |多因素认证设备。

 |
|└Base32StringSeed|String|DSF98HAD982KJA9SDFNAS9D8FU839B8ADHBGS\*\*\*\*|多因素认证设备密钥。

 |
|└QRCodePNG|String|YXNkZmFzZDlmeW5hc2Q5OGZoODd4bXJmcThhaGU5aSBmYXNkZiBzYWRmIGFGIDRxd2VjIGEgdHEz\*\*\*\*|密钥二维码PNG，使用Base64编码。

 |
|└SerialNumber|String|acs:ram::123456789012\*\*\*\*:mfa/device001|设备序列号。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=CreateVirtualMFADevice
&VirtualMFADeviceName=device001
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateVirtualMFADeviceResponse>
  <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
  <VirtualMFADevice>
    <SerialNumber>acs:ram::123456789012****:mfa/device001</SerialNumber>
    <Base32StringSeed>DSF98HAD982KJA9SDFNAS9D8FU839B8ADHBGS****</Base32StringSeed>
    <QRCodePNG>YXNkZmFzZDlmeW5hc2Q5OGZoODd4bXJmcThhaGU5aSBmYXNkZiBzYWRmIGFGIDRxd2VjIGEgdHEz****</QRCodePNG>
  </VirtualMFADevice>
</CreateVirtualMFADeviceResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"VirtualMFADevice":{
		"SerialNumber":"acs:ram::123456789012****:mfa/device001",
		"QRCodePNG":"YXNkZmFzZDlmeW5hc2Q5OGZoODd4bXJmcThhaGU5aSBmYXNkZiBzYWRmIGFGIDRxd2VjIGEgdHEz****",
		"Base32StringSeed":"DSF98HAD982KJA9SDFNAS9D8FU839B8ADHBGS****"
	},
	"RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ram)

