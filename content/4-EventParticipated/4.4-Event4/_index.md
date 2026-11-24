---
title: "Event 4"
date: 2026-11-24
weight: 4
chapter: false
pre: " <b> 4.4. </b> "
---

**Event name:** FCAJ Community Day

**Date & Time:** 08:30, October 31, 2026

**Location:** 26th Floor, Bitexco Tower, 02 Hai Trieu Street, Saigon Ward, Ho Chi Minh City

**Role:** Attendee

# Summary Report: “AWS Cloud Architecture, Software Factories, and Career Growth”

## Event Objectives

The event aimed to provide participants with a comprehensive understanding of modern cloud architecture, focusing on serverless computing and asynchronous systems. Instead of just covering theoretical concepts, the sessions introduced real-world lessons from building software factories at scale. The event also provided an opportunity to learn from experienced professionals about preparing for a career in the cloud industry, bridging the gap between universities and businesses, and navigating technical internships and open-source contributions.

## Speakers

* Thinh Nguyen - SYL Solution
* Henry Duc Bui - CloudThinker
* Hung Tran - NAB
* Dao Luong - FCAJ
* Khang Duong - FCAJ
* Tuan Tran - FCAJ

## Key Highlights

### Building Software Factories at Scale

The event started with practical lessons on building "software factories." The discussion helped me understand the common pitfalls teams face when scaling software development. It highlighted that building at scale requires not just good code, but standardized processes, automation, and practical insights from teams who have successfully done it in enterprise environments.

### Bridging the Education and Industry Gap

The education session provided a valuable perspective on what students need to prepare before entering the cloud industry. It emphasized that academic knowledge must be paired with hands-on technical skills to bridge the gap between university expectations and actual business requirements.

### Rethinking Serverless with AWS Lambda

One of the most technical and interesting parts of the event was the deep dive into AWS Lambda Web Functions. The session explained how native HTTP support and 128-request multi-concurrency are redefining Serverless compute. It showed how eliminating adapter overhead and leveraging Active CPU Billing can maximize cost efficiency, providing compelling live performance benchmarks comparing Serverless with Docker on EC2/ECS.

### Building Asynchronous Systems with Amazon SQS

The event connected architectural concepts with practical system design by exploring Amazon SQS. I learned why modern systems heavily rely on asynchronous processing to decouple services and scale effectively. The session provided concrete design patterns and practical tips for implementing SQS in real-world applications.

### Career Growth: Internships and Open Source

The latter half of the event focused on career development. Hearing about a real 3-month AWS internship journey—specifically how AWS services were applied to actual projects—provided actionable advice. Furthermore, the session on open-source contributing broke down how to make a first contribution from scratch, build a steady habit, and leverage this to accelerate skill and career growth.

## Key Takeaways

Technical Perspective

* Serverless architecture is evolving rapidly. Features like multi-concurrency and Active CPU Billing in AWS Lambda drastically improve performance and cost-efficiency.
* Modern, scalable cloud applications require decoupled architectures, making tools like Amazon SQS essential for handling asynchronous workflows smoothly.
* Building scalable software requires standardized practices ("software factories") rather than just writing standalone code.

### System Design Mindset

The biggest lesson I gained from the architectural sessions was the importance of choosing the right compute and messaging models. Before deploying an API or a processing job, developers must consider if the task should be synchronous (using optimized Lambda functions) or asynchronous (decoupled via SQS queues) to prevent bottlenecks and ensure system reliability.

### Career Perspective

The event showed me that entering the cloud industry requires proactive preparation. Technical skills are crucial, but real-world experience—gained through internships, applying AWS to practical projects, and consistently contributing to open-source communities—is what truly differentiates a candidate.

### Applying to My FCAJ Project

The knowledge from this event can be directly and immediately applied to my FCAJ project, where I am building an AWS Serverless Legal RAG Assistant.

Before this event, I had already set up the core infrastructure using Amazon Bedrock Knowledge Bases, API Gateway, DynamoDB, and a React frontend hosted on S3. However, the sessions on AWS Lambda and Amazon SQS gave me new ideas for optimizing my architecture:

* Applying AWS Lambda Optimizations: My legal-ai-chat-lambda currently handles requests from API Gateway. Learning about Lambda's multi-concurrency and Active CPU Billing helps me understand how to optimize my function's execution time and manage costs more effectively when multiple users query the legal assistant simultaneously.
* Applying Amazon SQS for Document Processing: Currently, legal documents are stored in my fcaj-raw-docs S3 bucket before being processed into chunks. The SQS session inspired me to decouple this data pipeline. I can implement an Amazon SQS queue between S3 and the processing service to handle document ingestion asynchronously. This ensures that if the system receives a massive batch of legal documents, the architecture can scale gracefully without throttling or crashing.

This event helped me shift my mindset from just "making the API work" to "designing a highly scalable, decoupled, and cost-effective serverless architecture."

## Event Experience

### Learning from Experienced Speakers

The event allowed me to learn from professionals who have built massive systems in practice. Their perspectives helped me better understand how AWS services like Lambda and SQS are utilized in real enterprise environments, beyond basic tutorials.

### Understanding Real-World Architecture

Instead of just learning what a service does, the live benchmarks and architectural design patterns showed me how and why these technologies are chosen to solve scalability and cost issues in production.

### Career Motivation

The sessions on the internship journey and open-source contributions were highly motivating. They encouraged me to not only focus on my FCAJ project but also to start building a public portfolio of contributions, improving my ability to collaborate and work effectively in the tech industry.

## Lessons Learned

The most important lesson I gained from the event is that building robust cloud software requires a balance of optimal compute (Lambda) and reliable communication (SQS). A successful cloud engineer must not only master the technical implementation of these services but also cultivate a strong habit of continuous learning through real-world projects and open-source contributions. This holistic mindset will guide me as I continue to refine my legal RAG assistant and advance my career.

## Event Photos

![Event 4 photo 1](../../images/4-EventParticipated/4.4-Event4/event4-01.png)

![Event 4 photo 2](../../images/4-EventParticipated/4.4-Event4/event4-02.jpeg)
