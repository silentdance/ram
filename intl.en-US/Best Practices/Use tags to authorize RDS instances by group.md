# Use tags to authorize RDS instances by group {#concept_msq_pmm_qfb .concept}

This topic describes how to use tags to authorize resources \(such as RDS instances\) by group so that RAM users can only view and operate on the tagged resources.

## Scenario {#section_lsl_wq5_qgb .section}

You have 10 RDS instances. You want your dev team to manage 5 of them, and your ops team to manage the other 5. However, you want each team to see only their authorized instances \(not the authorized resources of the other team\).

## Preparations {#section_jqp_tmm_qfb .section}

For more information, see [EN-US\_TP\_12553.md\#](reseller.en-US/Best Practices/Use tags to authorize ECS instances by group.md#).

The following is an example of the custom policy relevant to RDS:

```

{
  "Statement": [
    {
      "Action": "rds:*",
      "Effect": "Allow",
      "Resource": "*",
      "Condition": {
        "StringEquals": {
          "rds:ResourceTag/team": "dev"
         }
       }
     },
    {
       "Action": "rds:DescribeTag*",
       "Effect": "Allow",
       "Resource": "*"
     }
  ],
  "Version": "1"
}


```

In the preceding policy,

-   The `"Action": "rds:*"` element with "Condition" is used to filter the instances tagged as `"team": "dev"`. The keyword of "Condition" is `rds:ResourceTag`.
-   The `"Action": "rds:DescribeTag*"` element is used to display all tags. When a user performs operations in the **RDS console**, the system displays all the tags for the user to select, and then filters the instances according to the tag key and value selected by the user.

## What to do next {#section_csr_3hn_tgb .section}

If the relevant permissions of a RAM user are missing after you have tagged RDS instances into groups and granted permissions, see [../../../../../dita-oss-bucket/SP\_65/DNRAM19100116/EN-US\_TP\_123599.md\#](../../../../../reseller.en-US/FAQ/What should I do if the relevant permissions of one or some RAM users are missing after I have tagged RDS instances into groups and granted permissions?.md#).

