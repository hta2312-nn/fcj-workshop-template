---
title: "Security and Operations"
date: 2026-11-24
weight: 6
chapter: false
pre: " <b> 5.6. </b> "
---

### Overview
| Item | Details |
|---|---|
| Purpose | Review the current security posture, monitor activity and costs, and plan improvements. |
| AWS services | CloudWatch, AWS Budgets, IAM |

### 5.6.1 Current security posture
| Area | Current state | Risk | Recommendation |
|---|---|---|---|
| API Gateway | Rate and burst limits set on stage v1 | Anyone with the URL can call the API and exhaust the Groq quota | Throttling, usage plan, or API key; add Cognito later |
| CORS | Access-Control-Allow-Origin: * | Any website can call the API from a browser | Restrict to the S3 site's origin after the demo |
| Groq API key | Stored as a Lambda environment variable | Exposed if committed to code or shown in a screenshot | Move to SSM Parameter Store (SecureString); rotate the key if exposed |
| S3 website | Public read, HTTP only | Traffic is not encrypted | Place CloudFront in front for HTTPS if needed |
| Data sent to Groq | Questions leave AWS | Real customer data could leave the account | Use only sample questions; review Groq's data policy; consider Bedrock |
| CloudWatch | Lambda logging enabled | Logs may contain user questions | Set a 7 to 14 day retention period; avoid logging sensitive content |

### 5.6.2 Monitoring and cost control
**Goal:** Detect errors and unusual costs early.

**Steps**
1. Set a retention period for the Lambda log group.
2. Create an alarm for Lambda errors (optional).
3. Regularly review Free Tier usage in Billing and keep the Budget alert configured in section 5.2.

**View logs in CloudWatch**
1. Open the CloudWatch overview page and select **Logs** to view the Lambda logs.

![CloudWatch overview, Logs section](../../images/5-Workshop/5.6/5-6-01.png)

2. In the **Log groups** list, select the Lambda function's log group, which Lambda creates automatically.

![Log groups list](../../images/5-Workshop/5.6/5-6-02.png)

3. In the **Log streams** list, each stream records the function's requests along with the time of the latest log entry.

![Log streams list](../../images/5-Workshop/5.6/5-6-03.png)

**Check:** test requests appear in the logs, and the Budget alert is active.

### 5.6.3 Security hardening roadmap
1. Add throttling and a usage plan to the API to protect the Groq quota. This is a high priority and does not require frontend changes.
2. Move the Groq key to SSM Parameter Store, and grant Lambda read access only to that specific parameter.
3. Restrict CORS to the website's origin.
4. Add Cognito sign-in if the system moves beyond demo mode.
5. Testing: send high-rate requests to confirm throttling, try prompt injection questions, and scan the repository for secrets.

**Set stage throttling limits**
1. The stage Throttling page shows the limits in effect. Select the stage in the upper-right corner. The screenshot shows the $default stage. Each stage has its own throttling settings.
   - **Selected route throttling:** limits for a specific route, overriding the default. This section is empty because no route is selected.
   - **Default route throttling:** limits applied to every route in the stage. Burst and Rate limits both show "Not configured," which means no limit is set.
   - **Account throttling:** the account-wide ceiling for the region (Burst 5000, Rate 10000), shared by all APIs. This is a system-level limit and cannot be changed here.

![Stage Throttling page](../../images/5-Workshop/5.6/5-6-04.png)

2. Select **Edit** in the Default route throttling section and set:
   - **Rate limit:** 5, the maximum average number of requests per second.
   - **Burst limit:** 2, the maximum number of requests processed concurrently during a sudden spike.
3. Select **Save**, then select **Deploy** to apply the changes.

*[Image placeholder: Burst limit = 2 and Rate limit = 5 set on the default route]*

Requests that exceed the limit receive a 429 Too Many Requests error from API Gateway, before they reach Lambda or Groq.
