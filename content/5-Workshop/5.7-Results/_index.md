---
title: "Final Results and Future Development"
date: 2026-11-24
weight: 7
chapter: false
pre: " <b> 5.7. </b> "
---

### Results
- A complete serverless backend that scales automatically and, according to the team's records, costs $0 under the AWS Free Tier.
- A working RAG pipeline: each request retrieves legal provisions from DynamoDB and combines them with the LLM to produce a grounded answer.
- A stable API endpoint, ready for the static website and for team testing.

### Known limitations
- Keyword-based lookup may miss relevant provisions.
- Answers are plain text and do not yet include a structured risk level.
- The LLM runs outside AWS, and the API has no authentication yet.

### Future development
- Structured responses with a risk level (Low / Medium / High / Insufficient evidence), provisions, evidence, and sources.
- Incident reporting with human review, plus email alerts through Amazon SNS (summaries only, with no sensitive data).
- Conversation history stored in DynamoDB with a TTL.
- Evaluate Amazon Bedrock and Bedrock Knowledge Bases to keep all data within AWS (check current pricing and supported regions before deploying).
