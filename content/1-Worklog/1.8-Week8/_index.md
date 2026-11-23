---
title: "Week 8 Worklog"
date: 2026-11-08
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives:

- Build and test the backend: Lambda, Groq API, API Gateway.
- Standardize error handling.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - **Practice:** <br>&emsp; + Create the Lambda function `legal-ai-chat-lambda` (Python 3.12) with the execution role <br>&emsp; + Set the timeout to 30 seconds and configure the `GROQ_API_KEY` environment variable <br>&emsp; + Write `retrieve_legal_context` | 02/11/2026 | 02/11/2026 | AWS Docs: Lambda |
| 3 | - **Practice:** <br>&emsp; + Implement prompt assembly and the Groq API call <br>&emsp; + Create the HTTP API `LegalChatAPI` with route `POST /chat`, configure CORS, and deploy stage `v1` | 03/11/2026 | 03/11/2026 | AWS Docs: API Gateway |
| 4 | - **Practice:** <br>&emsp; + Test with `curl`: a sample question, an empty question (`400`), and an out-of-scope question <br>&emsp; + Review the CloudWatch logs of each request | 04/11/2026 | 04/11/2026 | AWS Docs: CloudWatch |
| 5 | - Add input validation and standardized HTTP error responses: <br>&emsp; + `400`, `429`, `502`, `504`, and `500` <br> - Fix the issues found during testing | 05/11/2026 | 05/11/2026 | AWS Docs: Lambda |
| 6 | - Review security practices: <br>&emsp; + Do not log user questions <br>&emsp; + Protect the API key <br>&emsp; + Maintain least privilege <br> - Note the improvements for the next steps | 06/11/2026 | 06/11/2026 | AWS Docs: Well-Architected Framework |

### Week 8 Achievements:

- Completed the Lambda RAG retrieval and prompt assembly logic (`legal-ai-chat-lambda`).
- Successfully integrated and called the Groq API from AWS Lambda.
- Exposed the backend through Amazon API Gateway (`LegalChatAPI`, `POST /chat`, stage `v1`) with CORS configured.
- Standardized input validation and error handling (`400`, `429`, `502`, `504`, `500`), and verified both success and error cases using `curl` and CloudWatch logs.