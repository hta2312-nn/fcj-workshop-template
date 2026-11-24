---
title: "5.8 Resource Cleanup"
date: 2026-11-24
weight: 8
chapter: false
pre: " <b> 5.8. </b> "
---

Delete the resources in the following order to avoid dependency errors and ongoing charges:

1. **S3 bucket** (delete the objects first, then the bucket).

*[Image placeholder: Deleting the S3 bucket]*

2. **API in API Gateway** (LegalChatAPI).

*[Image placeholder: Deleting the LegalChatAPI API]*

3. **Lambda function** legal-ai-chat-lambda and its **CloudWatch log group**.

*[Image placeholder: Deleting the Lambda function]*
*[Image placeholder: Deleting the CloudWatch log group]*

4. **DynamoDB table** LegalArticles.

*[Image placeholder: Deleting the LegalArticles DynamoDB table]*

5. **IAM role** legal-ai-chat-role created for Lambda.

*[Image placeholder: Deleting the legal-ai-chat-role IAM role (blur sensitive information before inserting the image)]*

6. **Revoke the Groq API key** in the Groq Console. Disable or delete the key created in section 5.2.

*[Image placeholder: Revoking the Groq API key (blur sensitive information before inserting the image)]*
