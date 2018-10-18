# Error reported when STS is used {#concept_wsg_bsx_ydb .concept}

## Questions {#section_x1f_w4x_ydb .section}

[Error reported when STS uses Java SDK to generate an on-demand account password](#)

## Error reported when STS uses Java SDK to generate an on-demand account password {#section_01 .section}

Error reported when STS uses Java SDK to generate an on-demand account password The following error message is returned:

```
Error message: You are not authorized to do this action. You should be authorized by RAM
```

This problem occurs because the “AliyunSTSAssumeRoleAccess” permission is not assigned to the account for authorization.

