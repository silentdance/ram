# What should I do if the relevant permissions of one or some RAM users are missing after I have tagged RDS instances into groups and granted permissions? {#concept_wgy_223_tgb .concept}

To troubleshoot this problem, we recommend that you follow these steps:

1.  Check whether the tags are attached to correct instances.
2.  Check whether the policy is using the correct tag key and value in the instances.

    **Note:** The tag key and value of an RDS instance cannot contain uppercase letters. If you enter an uppercase letter, it is automatically converted into a lowercase letter when you save the tag key and value.

3.  Check whether you have attached the target policy to the RAM user logging on to the **RDS console**.
4.  Check whether the region displayed in the console is the target region.
5.  Check whether you have selected the target tag value. The system can filter corresponding resources only after you have selected the target value.
6.  Ask the RAM user to close the error message window after logging on to the **RDS console**.

    **Note:** In many cases, the error message "You do not have permission to perform this operation." occurs because the console displays all resources by default, but the user does not have the permission to view all the resources.


