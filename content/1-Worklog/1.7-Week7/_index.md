---
title: "Week 7 Worklog"
date: 2026-11-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives:

- Build the knowledge base in DynamoDB.
- Configure IAM with least privilege for Lambda.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Review the AWS Budget alert and current Free Tier usage <br> - Confirm the Region used for all project resources <br> - **Practice:** <br>&emsp; + Create the DynamoDB table `LegalArticles` | 26/10/2026 | 26/10/2026 | AWS Docs: DynamoDB |
| 3 | - Summarize the selected legal articles and add keywords <br> - Check the content against the official text | 27/10/2026 | 27/10/2026 | <https://hcm-rules.awsfcaj.com/> |
| 4 | - **Practice:** <br>&emsp; + Write the seed script with `boto3` `batch_writer` and load the items <br>&emsp; + Verify the items with Explore table items | 28/10/2026 | 28/10/2026 | AWS Docs: DynamoDB |
| 5 | - **Practice:** <br>&emsp; + Create the IAM policy: read-only access to `LegalArticles` plus CloudWatch log permissions <br>&emsp; + Create the Lambda execution role `legal-ai-chat-role` and attach the policy | 29/10/2026 | 29/10/2026 | AWS Docs: IAM |
| 6 | - **Practice:** <br>&emsp; + Test reading the table with the AWS CLI or `boto3` <br> - Review the permissions and remove anything unnecessary | 30/10/2026 | 30/10/2026 | AWS Docs: IAM |

### Week 7 Achievements:

- Successfully created the `LegalArticles` table in Amazon DynamoDB.
- Loaded and verified the summarized legal articles and keywords using a `boto3` seed script.
- Created a least-privilege IAM policy and attached it to the `legal-ai-chat-role` Lambda execution role.