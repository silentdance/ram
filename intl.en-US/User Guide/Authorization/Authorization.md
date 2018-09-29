# Authorization {#concept_vyr_mzf_xdb .concept}

In Ram, authorization is the process of attaching one or more authorization policies to a user, user group, or role. Wherein,

-   Grant the user or user group authorization for the ram user under the current cloud account.

-   Give Role authorization, both for the current cloud account, under the ram user license, also used on, other cloud accounts, under the ram user or service role Authorization; the difference is, the authorized object needs to act as a role to obtain the identity and permissions of the role.


## Grant authorization to users or user groups {#section_q3j_nzf_xdb .section}

Ram under the current cloud account When users authorize, you can choose to authorize specific users, or you can authorize users to their user groups. The difference is that authorization to a user group applies to all users under the user group, users with similar requirements for resource access \(created and added to the same group\) conduct unified authorization.

## Give the user authorization {#section_r3j_nzf_xdb .section}

The procedure is as follows:

1.  Log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram).
2.  Click User management.
3.  Users who require authorization can be found via user name/display name \(fuzzy query can be used \), click the authorization button that is listed in its corresponding action.
4.  On the Edit personal authorization policy page,
    -   From the optional Authorization Policy Name on the left, find the permissions that you want to grant to the current user \(you can query using the keyword\), check the policy and click the right arrow, you can add the policy to the right under the selected Authorization Policy Name.
    -   Under Authorization Policy Name selected on the right, select a policy and click the left arrow, you can undo the policy.
5.  After adding the Authorization Policy, click confirm to complete the authorization.


At this point, you have completed the authorization to the user.

## Grant authorization to user groups {#section_v3j_nzf_xdb .section}

The procedure is as follows:

1.  Log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram).
2.  Click group management.
3.  The group name is used to locate the user groups that require authorization \(Fuzzy queries are available \), click the authorization that is listed in its corresponding action Button.
4.  On Edit Group Authorization Policy, page
    -   Find the permissions that need to be granted to the current group from the name of the optional Authorization Policy on the left \(you can query using the keyword\), check the policy and click the right arrow, you can add the policy to the right under the selected Authorization Policy Name.
    -   Under Authorization Policy Name selected on the right, select a policy and click the left arrow, you can undo the policy.
5.  After adding the Authorization Policy, click confirm to complete the authorization.

So far, you have completed authorization to the user group.

## Give Role authorization {#section_y3j_nzf_xdb .section}

When you create a new role, you can choose to create a new user role \(including using the current cloud account and other cloud accounts as trusted cloud accounts\) or a service role, and you need to select the corresponding trusted cloud account or cloud service \(that is, allow it to use the roles created. visit your cloud resources \).

-   For the current cloud account user role, authorization, then the ram users under the current cloud account can play a role and access the authorized cloud resources.
-   Yes, other cloud account user roles, authorization, ram users under other designated cloud accounts can play a role and access authorized cloud resources..
-   For service roles, authorization, A trusted cloud service can play a role and access authorized cloud resources.

## Operation Steps {#section_ajj_nzf_xdb .section}

1.  Log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram).
2.  Click role management.
3.  Roles that require authorization are found by role name \(fuzzy query can be used \), click the authorization button that is listed in its corresponding action.
4.  On the Edit Role authorization policy page,
    -   From the left, the optional Authorization Policy Name The policy is selected by finding permissions that need to be granted to the current role \(you can use the keyword query, and click the right arrow to add the policy to the right under the selected Authorization Policy Name.
    -   Under Authorization Policy Name selected on the right, select a policy and click the left arrow, you can undo the policy.
5.  After adding the Authorization Policy, click confirm to complete the authorization.

At this point, you have completed the authorization to the role.

