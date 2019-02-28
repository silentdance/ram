# Error messages {#reference_a3q_rtv_xdb .reference}

## HTTP Status 400 {#section_g2r_3tv_xdb .section}

**InvalidParameter****InvalidParameter.RoleArn**

-   HTTP Status: 400
-   ErrorMessage: The parameter RoleArn is wrongly formed.
-   Solution: Use the correct role Arn.

**InvalidParameter.RoleSessionName**

-   HTTP Status: 400
-   ErrorMessage: The parameter RoleSessionName is wrongly formed.
-   Solution: Modify the value of RoleSessionName. The value must be 2 to 32 characters in length and can contain letters, numbers, and special characters.

**InvalidParameter.DurationSeconds**

-   HTTP Status: 400
-   ErrorMessage: The Min/Max value of DurationSeconds is 15min/1hr.
-   Solution: Modify the value of DurationSeconds. The value must be in the range of 900 and 3600.

**InvalidParameter.PolicyGrammar**

-   HTTP Status: 400
-   ErrorMessage: The parameter Policy has not passed grammar check.
-   Solution: Modify the policy content.

**InvalidParameter.PolicySize**

-   HTTP Status: 400
-   ErrorMessage: The size of Policy must be smaller than 1024 bytes.
-   Solution: Modify the size of Policy. The size cannot exceed 1,024 bytes.

## HTTP Status 403 {#section_pcn_ttv_xdb .section}

**NoPermission**

-   HTTP Status: 403
-   ErrorMessage: You are not authorized to do this action. You should be authorized by RAM.
-   Solution: Grant relevant permissions to the STS token.

## HTTP Status 500 {#section_tdg_5tv_xdb .section}

**InternalError**

-   HTTP Status: 500
-   ErrorMessage: STS Server Internal Error happened.
-   Solution: Open a ticket.

