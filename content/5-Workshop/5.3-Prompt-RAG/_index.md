---
title: "5.3 Phase 1: Prompt Design and RAG Mechanism"
date: 2026-11-24
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

### Overview
| Item | Details |
|---|---|
| Purpose | Define how the language model receives and processes legal data before writing any code. |
| AWS service | None (design phase; tested in the Groq Playground) |
| Output | System prompt and prompt template used in Lambda |

### 5.3.1 Build a role-oriented System Prompt
**Goal:** Make the model act as a legal advisor specializing in Vietnamese regulations, such as Decree 13/2023/ND-CP.

**Steps**
1. Write a role definition (an expert in Vietnamese personal data law).
2. Require the answer to be written in Vietnamese and to cite the legal provisions used.
3. Add a disclaimer: the answer is preliminary and not official legal advice.

**Check:** the model responds with the intended role and tone.

### 5.3.2 Set context constraints
**Goal:** Force the model to answer only from legal texts retrieved from the database.

**Steps**
1. Add a strict rule: answer only from the provided legal texts, and do not fabricate or infer beyond that source.
2. Add a fallback: if the provided text is insufficient, state clearly that there is not enough basis.
3. Test with an out-of-scope question, such as a tax question.

**Check:** an out-of-scope question returns "insufficient basis" instead of a fabricated answer.

### 5.3.3 Define the input data structure
**Goal:** Decide how Lambda injects DynamoDB data into the outgoing prompt.

**Steps**
1. Format each retrieved provision as a labeled block (article number and content).
2. Place the legal context before the user's question in the message.
3. Limit the number and length of provisions so the prompt stays within the model's rate and token limits.

*[Image placeholder: Prompt structure with system prompt, legal context, and question]*

**Check:** the printed prompt contains all three parts in the correct order.
