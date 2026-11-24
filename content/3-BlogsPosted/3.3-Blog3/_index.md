---
title: "Blog 3"
date: 2026-11-24
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# AWS LEARNING CORNER: BUILDING A SIMPLE, SECURE STATIC WEBSITE WITH S3 + CLOUDFRONT + ROUTE 53

Once you have finished a static website (plain HTML/CSS/JS, or a build from React, Vue or Next.js), the next question is how to host it and deliver it to the internet. The usual goals are low cost, fast access, secure HTTPS and no server to manage.

The combination of Amazon S3, Amazon CloudFront and Amazon Route 53 is a standard architecture that addresses these goals well.

### Step 1: Store files with Amazon S3
* Create an S3 bucket to hold all the built files of your website.
* Configure the S3 bucket policy and grant access appropriately.
* Enable Static website hosting and set the default files, for example index.html and 404.html.

### Step 2: Speed up and secure delivery with Amazon CloudFront (CDN)
* Create a CloudFront distribution and set the S3 bucket as its origin.
* **Faster delivery:** Website content is cached at edge locations around the world, which reduces latency for users.
* **Security:** Use a free SSL/TLS certificate from AWS Certificate Manager (ACM) to enable HTTPS. Also configure Origin Access Control (OAC) to block direct access to the S3 bucket, so traffic can only come through CloudFront.

### Step 3: Route your domain with Amazon Route 53
* Create a hosted zone for your domain in Route 53.
* Create an A record (alias type) that points your root domain or subdomain to the CloudFront distribution.

### Technical value and lessons learned
* **Cost optimization:** A serverless architecture has no server maintenance costs (Nginx or Apache). For low traffic or personal projects, the monthly cost is close to zero.
* **Scalability:** CloudFront's CDN network absorbs sudden traffic spikes automatically, without infrastructure upgrades.
* **Simpler operations:** There is no need to patch operating systems or renew SSL certificates manually.

### Conclusion
This classic hands-on exercise is important because it teaches you how to combine basic AWS services into a complete, secure, industry-standard system.

![AWS static website architecture](../../images/3-BlogsPosted/3.3-Blog3/blog3-01.jpeg)

[Link to the post on AWS Study Group](https://www.facebook.com/groups/awsstudygroupfcj/?multi_permalinks=2317669882331304)
