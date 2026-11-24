---
title: "5.8 Resource Cleanup"
date: 2026-11-24
weight: 8
chapter: false
pre: " <b> 5.8. </b> "
---

Delete the resources in the following order to avoid dependency errors and ongoing charges:

1. **S3 bucket** (delete the objects first, then the bucket).

![Deleting the S3 bucket](/images/5-Workshop/5.8/5-8-01.png)

2. **API in API Gateway** (LegalChatAPI).

![Deleting the LegalChatAPI API](/images/5-Workshop/5.8/5-8-02.png)

3. **Lambda function** legal-ai-chat-lambda and its **CloudWatch log group**.

![Deleting the Lambda function](/images/5-Workshop/5.8/5-8-03.png)
![Deleting the CloudWatch log group](/images/5-Workshop/5.8/5-8-04.png)

4. **DynamoDB table** LegalArticles.

![Deleting the LegalArticles DynamoDB table](/images/5-Workshop/5.8/5-8-05.png)

5. **IAM role** legal-ai-chat-role created for Lambda.

![Deleting the legal-ai-chat-role IAM role (blur sensitive information before inserting the image)](/images/5-Workshop/5.8/5-8-06.png)

6. **Revoke the Groq API key** in the Groq Console. Disable or delete the key created in section 5.2.

![Revoking the Groq API key (blur sensitive information before inserting the image)](/images/5-Workshop/5.8/5-8-07.png)
