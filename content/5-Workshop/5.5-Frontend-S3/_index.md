---
title: "5.5 Frontend: S3 Static Website"
date: 2026-11-24
weight: 5
chapter: false
pre: " <b> 5.5. </b> "
---

### Overview
| Item | Details |
|---|---|
| Purpose | A chat page where users ask questions and read answers. |
| AWS service | Amazon S3 (static website hosting) |
| Input | The user's question |
| Output | The answer displayed in the chat window |
| Dependencies | The backend API URL |

### 5.5.1 Build the chat interface (index.html)
**Goal:** A single static page that calls the backend using fetch.

**Steps**
1. Build the chat layout: title, status badge, greeting, message list, input field, and send button.
2. When the user sends a message, call fetch with an HTTP POST to the API URL and show a processing status.
3. Display clear messages for errors 400, 429, and 502/504.
4. Recommendation: add a disclaimer stating that answers are preliminary and not legal advice.

*[Image placeholder: The index.html chat interface]*

**Check:** opening index.html locally shows the chat page and greeting.

### 5.5.2 Host the page on S3
**Goal:** Publish index.html as a static website.

**Steps**
1. Create the bucket **ai-legal-assistant-frontend-hau** in ap-southeast-2.
2. Upload index.html to the bucket.
3. Enable **Static website hosting** with index.html as the index document.
4. Allow public read access for this bucket only: turn off Block Public Access for the bucket and add a read-only bucket policy.
5. Open the website endpoint.

**Create the bucket**
1. Create a General purpose bucket in ap-southeast-2 and name it ai-legal-assistant-frontend-hau.

*[Image placeholder: Creating the S3 bucket in ap-southeast-2]*

2. Clear **Block all public access** for this bucket only and confirm the warning.

*[Image placeholder: Clearing Block all public access]*

3. Keep the default SSE-S3 encryption and select **Create bucket**.

*[Image placeholder: Default SSE-S3 encryption]*

4. The bucket is created, and the Objects list is empty.

*[Image placeholder: Newly created bucket with an empty Objects list]*

5. Go to the Upload page to upload the index.html file to the bucket.

*[Image placeholder: Upload page for index.html]*

**Enable static website hosting**
1. The bucket's Properties tab shows the Region, ARN, and creation date.

*[Image placeholder: Bucket Properties tab]*

2. The **Static website hosting** section is Disabled. Select **Edit**.

*[Image placeholder: Static website hosting shown as Disabled]*

3. Enable static website hosting, select **Host a static website**, and set **Index document** to index.html.

*[Image placeholder: Enabling static website hosting with index.html as the index document]*

**Check:** the endpoint `http://ai-legal-assistant-frontend-hau.s3-website-ap-southeast-2.amazonaws.com/` loads the page.

### 5.5.3 Connect the API and test end to end
**Goal:** Make the deployed page call the live backend.

**Steps**
1. Set the API URL in index.html, then upload the file to S3 again.
2. Open the website and ask a sample question.
3. Open the browser console and confirm there are no CORS errors.
4. Check the request in CloudWatch Logs.

*[Image placeholder: Sample question and answer on the website]*

**Check:** the question receives a grounded answer on the page, along with a matching log entry.
