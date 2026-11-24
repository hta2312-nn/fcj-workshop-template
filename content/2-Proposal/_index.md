---
title: "Proposal"
date: 2026-11-24
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Legal RAG Platform: Automated Legal Advisory System for Decree 13/2023/ND-CP
## A Unified AWS Serverless Solution with LLM for Real-Time Legal Research and Analysis

### 1. Executive Summary
The Legal RAG Platform is an automated advisory system that helps users and team members quickly look up and analyze complex Vietnamese legal regulations. It focuses on Decree 13/2023/ND-CP on personal data protection. The platform is built on a fully serverless architecture on AWS and uses a large language model (LLM) from the Groq API (qwen/qwen3.8-27b). Answers are grounded in the actual legal text, which reduces the risk of AI hallucination. The platform also keeps operating costs at $0 by staying within the AWS Free Tier.

### 2. Problem Statement
#### The Problem
- Legal documents such as Decree 13/2023/ND-CP are long, dense, and difficult for non-experts to search manually.
- General-purpose AI tools, such as the free version of ChatGPT, often lack in-depth knowledge of Vietnamese law. They tend to give generic answers without an accurate legal basis.
- Building a self-hosted AI system is expensive in hardware and complex to operate.

#### The Solution
The platform uses an automated RAG (Retrieval-Augmented Generation) pipeline. When a user submits a question, the system searches the database for the most relevant legal provisions and injects them into a System Prompt. The LLM then generates an answer that cites those provisions clearly.
- **Amazon DynamoDB** stores the extracted legal provisions in the LegalArticles table.
- **AWS Lambda** handles the backend logic, and **Amazon API Gateway** exposes a stable API endpoint.
- **Groq API** with the qwen/qwen3.8-27b model generates clear, coherent answers.
- **Amazon S3 Static Website** hosts the web interface, where users interact through a chat window.

#### Benefits and Return on Investment (ROI)
- **High accuracy:** Answers stay close to the provided legal text and are transparent and well-supported.
- **Cost efficiency:** The serverless design runs within the AWS Free Tier, with monthly costs close to $0.
- **Scalability:** The decoupled architecture makes it easy to add new legal documents, such as the Law on Network Information Security or the Law on Information Technology, to DynamoDB in the future.

### 3. Solution Architecture
The system follows a serverless architecture that connects the frontend, backend, and external LLM in a closed loop.

#### AWS Services and Technologies
- **Amazon S3 Static Website:** Hosts and serves the static web interface (index.html, CSS, and JavaScript).
- **Amazon API Gateway:** Provides a public HTTP/REST API, handles CORS, and forwards client requests to Lambda.
- **AWS Lambda (Python):** Runs the RAG logic, queries DynamoDB, and calls the Groq API.
- **Amazon DynamoDB (LegalArticles):** Stores legal provisions and supports fast keyword-based lookup.
- **Groq API (qwen/qwen3.8-27b):** Generates and analyzes natural language based on the legal context provided.

#### Component Design
- **Frontend:** Users open the website hosted on S3 and enter a question in the chat window. The browser sends an HTTP POST request containing the question over HTTPS to API Gateway.
- **API Gateway:** Receives the request, validates CORS settings, and forwards the payload to the Lambda function.
- **Data Retrieval (DynamoDB):** The `retrieve_legal_context` function searches the LegalArticles table for relevant provisions. For example, it can retrieve rules on handling violations involving citizen identity numbers (CCCD) and personal data under Decree 13.
- **Augmentation and Generation (Groq API):** Lambda combines the user's question with the retrieved legal context into a System Prompt with strict constraints, which require answers to be based only on the provided context. It then calls the Groq API.
- **Response Flow:** Groq returns the result to Lambda. Lambda formats a standard JSON response and sends it back through API Gateway to display in the chat window.

### 4. Technical Implementation
#### Implementation Phases
- **Phase 1, Prompt Design and RAG Mechanism:** Write a System Prompt that defines the role of a legal expert and sets a context constraint that prohibits fabricated information.
- **Phase 2, Backend and Database:**
    - Create the DynamoDB LegalArticles table.
    - Write the Python code for AWS Lambda, including the retrieval function and the Groq API integration.
    - Configure API Gateway, enable CORS headers, and implement standardized error handling. This covers codes 400 and 502/504, as well as code 429 when the Groq API rate limit is exceeded.
- **Phase 3, Testing and Refinement:** Send HTTP POST requests with curl and test directly in the web interface. Monitor logs in Amazon CloudWatch.

### 5. Timeline & Milestones
- **Research and Design:** Define the legal scope (Decree 13/2023/ND-CP) and design the RAG data flow.
- **Development and Deployment:** Build the DynamoDB database, complete the Lambda function, and configure API Gateway.
- **Integration and Testing:** Connect the S3 static website to API Gateway, test the accuracy of answers from the Groq LLM, and refine error handling.

### 6. Budget Estimation
#### AWS Infrastructure
- **Amazon S3:** Free within Free Tier limits.
- **Amazon API Gateway:** Free for the first 1 million requests per month.
- **AWS Lambda:** Free for up to 1 million requests per month.
- **Amazon DynamoDB:** Free within 25 GB of storage and 25 WCU and 25 RCU.

**Total AWS cost:** $0.00 per month.

#### Groq API
The project uses the free tier for the open-source model (qwen/qwen3.8-27b).

**Total project investment:** VND 0 ($0).

### 7. Risk Assessment
#### Risk Matrix
- **API overload (Groq API rate limit, error 429):** Implement error handling and display a clear, user-friendly message in the chat interface when the request limit is temporarily exceeded.
- **Inaccurate AI answers (hallucination):** Strengthen the System Prompt so the model uses only the legal context retrieved from DynamoDB and does not infer beyond that source.
- **CORS errors in the browser:** Configure full CORS headers (Access-Control-Allow-Origin: *, POST, OPTIONS) directly in API Gateway.

### 8. Expected Outcomes
#### Technical Achievements
A complete serverless backend that scales automatically, runs reliably, and operates at $0 cost.

#### Practical Value
A standardized API gateway and an intuitive chat interface that enable fast, accurate lookup of the core provisions of Decree 13/2023/ND-CP. The platform supports both study and research.