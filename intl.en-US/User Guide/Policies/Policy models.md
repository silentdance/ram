# Policy models {#concept_cpz_ltc_mfb .concept}

Alibaba Cloud allows you to grant permission for an Alibaba Cloud account or for a resource group. You can select an appropriate model according to your specific requirements.

## Grant permission for an Alibaba Cloud account {#section_fpg_ymv_4fb .section}

Granting permission for an Alibaba Cloud account means that when you attach a policy to a RAM identity, all Alibaba Cloud resources under the account are included within the scope of the policy permissions.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23766/156155265814311_en-US.png)

## Grant permission for a target resource group {#section_iw3_xmv_4fb .section}

Granting permission for a resource group means that when you attach a policy to a RAM identity, only the Alibaba Cloud resources within the target resource group are included within the scope of the policy permissions.

In detail, the RAM user with the `AdministratorAccess` system policy in a resource group is called administrator. By default, the resource group creator is assigned as administrator. The administrator is the entity that can add RAM users to the resource group and grant permission to the users in the resource group.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23766/156155265814312_en-US.png)

