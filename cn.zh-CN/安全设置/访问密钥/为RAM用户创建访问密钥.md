# 为RAM用户创建访问密钥 {#task_188766 .task}

访问密钥（AccessKey）是RAM用户的长期凭证。如果为RAM用户创建了访问密钥，RAM用户可以通过API或其他开发工具访问阿里云资源。

1.  云账号登录[RAM控制台](https://ram.console.aliyun.com/)。
2.  在左侧导航栏的**人员管理**菜单下，单击**用户**。
3.  在**用户登录名称/显示名称**列表下，单击目标RAM用户名称。
4.  在**用户AccessKey** 区域下，单击**创建新的AccessKey**。 

    **说明：** 首次创建时需填写手机验证码。

5.  单击**确认**。 

    **说明：** 

    -   AccessKeySecret只在创建时显示，不提供查询，请妥善保管。
    -   若AccessKey泄露或丢失，则需要创建新的AccessKey，最多可以创建2个AccessKey。

**相关文档**  


[CreateAccessKey](../../../../cn.zh-CN/API参考（RAM）/用户管理接口/CreateAccessKey.md#)

