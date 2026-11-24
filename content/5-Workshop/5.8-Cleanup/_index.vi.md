---
title: "Dọn dẹp tài nguyên"
date: 2026-11-24
weight: 8
chapter: false
pre: " <b> 5.8. </b> "
---

Xóa tài nguyên theo thứ tự sau để tránh lỗi phụ thuộc và chi phí phát sinh:

1. **S3 bucket** (xóa object trước, sau đó xóa bucket).

![Xóa S3 bucket](../../images/5-Workshop/5.8/5-8-01.png)

2. **API trong API Gateway** (LegalChatAPI).

![Xóa API LegalChatAPI](../../images/5-Workshop/5.8/5-8-02.png)

3. **Hàm Lambda** legal-ai-chat-lambda và **log group CloudWatch** của hàm.

![Xóa hàm Lambda](../../images/5-Workshop/5.8/5-8-03.png)
![Xóa log group CloudWatch](../../images/5-Workshop/5.8/5-8-04.png)

4. **Bảng DynamoDB** LegalArticles.

![Xóa bảng DynamoDB LegalArticles](../../images/5-Workshop/5.8/5-8-05.png)

5. **IAM role** legal-ai-chat-role đã tạo cho Lambda.

![Xóa IAM role legal-ai-chat-role (che thông tin nhạy cảm trước khi chèn ảnh)](../../images/5-Workshop/5.8/5-8-06.png)

6. **Thu hồi Groq API key** trong Groq Console. Vô hiệu hóa hoặc xóa key đã tạo ở mục 5.2.

![Thu hồi Groq API key (che thông tin nhạy cảm trước khi chèn ảnh)](../../images/5-Workshop/5.8/5-8-07.png)
