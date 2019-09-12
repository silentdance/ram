# What can I do if the permissions of RAM users are missing after I have attached tags to a group of RDS instances and granted permissions to RAM users? {#concept_wgy_223_tgb .concept}

This topic describes how to troubleshoot the problem if RAM users cannot access a group of tagged RDS instances on which the users are granted the permissions.

## Problem {#section_is4_lmn_tgb .section}

After you use tags to group the target RDS instances and grant relevant permissions to an RAM user, the following problem occurs. When you log on to the **ApsaraDB for RDS console** as the RAM user, an error message appears and shows that you are not authorized to perform any operations.

## Troubleshooting {#section_dzf_kmn_tgb .section}

1.  Check whether tags are attached to correct instances.
2.  Check whether tag keys and values specified in permission policies are the same with those attached to the instances.

    **Note:** Tag keys and values attached to the instances cannot contain uppercase letters. If you enter uppercase letters, they are automatically converted to lowercase letters when saved.

3.  Check whether you have been granted the required permissions before logging on to the **ApsaraDB for RDS console**.
4.  Check whether the current region displayed in the console is the expected region.
5.  Check whether you have selected the corresponding tag value to filter the intended resources.
6.  If the problem persists and an error message shows that you are not authorized to perform operations in the **ApsaraDB for RDS console**, close the error message.

    **Note:** The message is "You do not have permission for this operation. Please go to the RAM console for authorization." This message appears because all resources are displayed in the console, and the current RAM user is not authorized to view all resources.


