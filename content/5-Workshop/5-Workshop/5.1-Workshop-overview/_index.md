---
title: "5.1 Introduction"
date: 2026-11-24
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

### Concepts
- **RAG (Retrieval-Augmented Generation):** retrieve the relevant passages first (Retrieval), add them to the prompt (Augmentation), and then have the model answer based only on those passages (Generation).
- **Knowledge base on DynamoDB:** legal provisions are stored as items in a DynamoDB table and searched by keyword. This approach is simple and fits within the AWS Free Tier, but it does not understand meaning the way vector search does.
- **Serverless:** Lambda, API Gateway, and DynamoDB scale automatically and charge based on usage, which suits low-budget projects.
- **Groq API:** an external inference service that runs the language model (qwen/qwen3.8-27b), called by Lambda over HTTPS.

### Problem and goal
Staff need quick answers about personal data regulations, for example whether they can use a customer's citizen ID (CCCD) data for marketing. Public chatbots may invent legal provisions or cite them incorrectly. The goal is for answers to rely only on the legal texts the team provides, running on AWS at near-zero cost.

### Architecture and data flow
*[Image placeholder: Architecture diagram and data flow]*

**Data flow:**
1. The user opens the website on S3, types a question into the chat window, and sends it. index.html sends an HTTP POST over HTTPS to API Gateway.
2. API Gateway checks CORS and passes the payload to the Lambda function.
3. Lambda queries the LegalArticles DynamoDB table for provisions related to the question (function `retrieve_legal_context`).
4. DynamoDB returns the matching provisions to Lambda as legal context.
5. Lambda builds the complete prompt (system prompt, legal context, and question) and calls the Groq API.
6. Groq returns the answer as text to Lambda.
7. Lambda formats a standard JSON response, including an error code if applicable, and returns it to API Gateway.
8. API Gateway returns the result, and the chat window displays it. Lambda logs are written to Amazon CloudWatch throughout the process.

### Components
| Component | AWS service / resource |
|---|---|
| Prompt and RAG logic | Lambda (Python) |
| Knowledge base | DynamoDB, LegalArticles table |
| Backend API | API Gateway + Lambda |
| Frontend | S3 static website, index.html |
| Security and operations | CloudWatch, Budgets, IAM |

### Implemented vs. planned
The implemented system differs from the original design in several areas. The table below shows what is currently in place.

| Item | Original design | Current implementation |
|---|---|---|
| Knowledge base | S3 + Bedrock Knowledge Bases | DynamoDB LegalArticles table (keyword lookup) |
| LLM | Amazon Bedrock | Groq API (outside AWS) |
| Frontend | AWS Amplify | S3 static website |
| Authentication | Cognito | Not yet (public API) |
| Response format | Structured: risk level, provisions, evidence | Text answer wrapped in JSON |
| Conversation history | DynamoDB | Not yet implemented |
| Incident reporting and alerts | SNS | Not yet implemented |

### AI safety principles
- This is a preliminary assessment, not an official legal conclusion.
- Answers rely only on the provided legal provisions. The system must not invent provisions or citations.
- If the database has no supporting basis, the system must say so.
