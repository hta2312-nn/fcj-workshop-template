---
title: "Week 6 Worklog"
date: 2026-10-25
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives:

- Design the system prompt and the RAG context rules.
- Design the data schema for the legal knowledge base.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Read the structure of Decree 13/2023/ND-CP <br> - Select the key articles: <br>&emsp; + Personal data <br>&emsp; + Consent <br>&emsp; + Data subject rights <br>&emsp; + Marketing <br>&emsp; + Violations | 19/10/2026 | 19/10/2026 | <https://hcm-rules.awsfcaj.com/> |
| 3 | - Create a Groq account and API key and explore the Playground <br> - Write a role-based system prompt: <br>&emsp; + Answer in Vietnamese <br>&emsp; + Cite articles <br>&emsp; + Add a disclaimer | 20/10/2026 | 20/10/2026 | Groq Docs |
| 4 | - Add strict context constraints and a fallback answer for insufficient legal basis <br> - **Practice:** <br>&emsp; + Test with an out-of-scope question such as tax | 21/10/2026 | 21/10/2026 | Groq Docs |
| 5 | - Design the `LegalArticles` schema: <br>&emsp; + `id`, `law_name`, `article_number`, `content`, `keywords` <br> - Define the prompt assembly: <br>&emsp; + System prompt + legal context + question, with limits on article count and length | 22/10/2026 | 22/10/2026 | AWS Docs: DynamoDB |
| 6 | - **Practice:** <br>&emsp; + Test sample questions in the Playground (e.g., using a customer ID card number for advertising) <br> - Refine and record the final prompt template | 23/10/2026 | 23/10/2026 | Groq Docs |

### Week 6 Achievements:

- Understood the main structure and key articles of Decree 13/2023/ND-CP.
- Designed the role-based system prompt along with strict context constraints and a fallback answer for out-of-scope queries.
- Designed the `LegalArticles` data schema for the legal knowledge base.
- Defined, tested, and finalized the prompt assembly template and context limits.