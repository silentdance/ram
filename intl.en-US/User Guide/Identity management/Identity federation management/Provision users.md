# Provision users {#concept_ylq_jjc_mfb .concept}

This topic describes how to provision users and how to use the RAM user synchronization tool to quickly synchronize the RAM users from Microsoft Active Directory \(AD\) or an LDAP directory to RAM.

You can migrate or synchronize user data from an enterprise IdP to Alibaba Cloud RAM using one of the following methods:

-   Log on to the RAM console and manually create the RAM users that match the enterprise IdP.
-   Use a RAM SDK to write a program or use aliyuncli to customize a solution.
-   Use the Alibaba Cloud RAM user synchronization tool to synchronize users from the enterprise IdP to Alibaba Cloud RAM.

    **Note:** To use the RAM user synchronization tool for a trial, contact your account manager.


## Install and configure the RAM user synchronization tool {#section_x1b_q2n_4fb .section}

-   The synchronization tool must run on a Microsoft Windows server.
-   After installing the tool, perform the following steps:
    1.  Configure the local IdP service address.
    2.  Configure a user account and a password for the synchronization tool to read IdP directory data.

        **Notice:** You must grant the user the permission to read AD.

    3.  Configure an AccessKey for the synchronization tool to call Alibaba Cloud RAM APIs.

        **Notice:** We recommend that you use the AccessKey of a RAM user that has obtained relevant RAM API permissions.


