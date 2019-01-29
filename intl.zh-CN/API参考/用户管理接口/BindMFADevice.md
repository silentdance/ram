# BindMFADevice {#doc_api_977671 .reference}

绑定多因素认证设备。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ram&api=BindMFADevice)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|SerialNumber|String|是|acs:ram::1234567890123:mfa/device002|指定MFA设备的序列号。

 |
|UserName|String|是|zhangqiang|指定用户名。

 |
|AuthenticationCode1|String|是|111222|验证第一组动态密码。

 |
|AuthenticationCode2|String|是|333444|验证第二组动态密码。

 |
|Action|String|是|BindMFADevice|系统规定参数。取值：BindMFADevice

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ram.aliyuncs.com/?Action=BindMFADevice
&SerialNumber=acs:ram::1234567890123:mfa/device002
&UserName=zhangqiang
&AuthenticationCode1=111222
&AuthenticationCode2=333444
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<BindMFADeviceResponse>
  <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
</BindMFADeviceResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ram)

