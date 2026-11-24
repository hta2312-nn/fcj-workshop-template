---
title: "Week 11 Worklog"
date: 2026-11-24
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Week 11 Objectives:

- Finalize the Proposal and Workshop with the Pricing Calculator estimate, architecture rationale, and future-work improvements.
- Study next-step improvements for security, retrieval, and monitoring.
- Write and publish technical blog posts based on the project.
- Prepare the final demo, complete the Self-Assessment, and submit all internship deliverables.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Update the Proposal: <br>&emsp; + Add the architecture diagram, the service table with reasons, and an expanded risk table <br>&emsp; + Add the AWS Pricing Calculator estimate (Sydney, 10,000 requests/month) with the link and the summary table <br> - Fix the cost wording in the Executive Summary, ROI, and Expected Outcomes | 23/11/2026 | 23/11/2026 | AWS Pricing Calculator |
| 3 | - Update the Workshop: <br>&emsp; + Add the Well-Architected mapping, the cost-optimization section, and the cost estimate <br>&emsp; + Add CloudWatch evidence (logs, metrics, alarm) and check that every step can be reproduced <br>&emsp; + Fix inconsistencies in Region, resource names, and screenshots <br> - Study future improvements and write the future-work section for the Workshop: <br>&emsp; + AWS Systems Manager Parameter Store (`SecureString`), API keys & usage plans, CORS restriction, and Amazon Cognito <br>&emsp; + Amazon Bedrock & Knowledge Bases vs. keyword retrieval, SNS email alerts, and DynamoDB TTL | 24/11/2026 | 24/11/2026 | AWS Docs: Well-Architected Framework, Parameter Store, Amazon Bedrock |
| 4 | - Write Blog 1: building a serverless RAG assistant with Lambda, API Gateway, and DynamoDB (architecture, data flow, and main design decisions) <br> - Write Blog 2: estimating AWS costs with the Pricing Calculator (lessons learned: unit mistakes in API Gateway and unintended reserved capacity in DynamoDB) | 25/11/2026 | 25/11/2026 | AWS Pricing Calculator, <https://hcm-rules.awsfcaj.com/> |
| 5 | - Write Blog 3: security and cost lessons from the project: <br>&emsp; + Least privilege, throttling, prompt injection, and API key handling <br> - Review, edit, and publish all three blog posts to the AWS Study Group <br> - Collect feedback from mentors and peers and note the improvements | 26/11/2026 | 26/11/2026 | <https://hcm-rules.awsfcaj.com/> |
| 6 | - Record the final demo video and prepare the presentation and Q&A <br> - Complete the Self-Assessment <br> - Ask a mentor to review the Proposal and the Workshop | 27/11/2026 | 27/11/2026 | <https://hcm-rules.awsfcaj.com/> |
| 7 | - Check the internship checklist: attendance, events with check-in photos, blogs, and Worklog <br> - Final check of all deliverables: Worklog (Weeks 1–11), Proposal, Workshop, Blog links, and Self-Assessment <br> - Verify in Billing and Free Tier usage that no resources are still running and submit all deliverables | 28/11/2026 | 29/11/2026 | AWS Docs: Cost Explorer and Billing |

### Week 11 Achievements:

- Completed the Proposal with the architecture diagram, service rationale, expanded risk table, and AWS Pricing Calculator estimate.
- Completed the Workshop with Well-Architected mapping, cost optimization, CloudWatch monitoring evidence, and a future-work section covering security (Parameter Store, Cognito, CORS, usage plans), retrieval (Amazon Bedrock), and monitoring/storage (SNS, DynamoDB TTL).
- Learned to identify and avoid common AWS Pricing Calculator input mistakes.
- Wrote, edited, and published three technical blog posts to the AWS Study Group.
- Completed the final demo video, presentation, Self-Assessment, and mentor review.
- Verified zero running resources in Billing/Free Tier and submitted all internship deliverables.