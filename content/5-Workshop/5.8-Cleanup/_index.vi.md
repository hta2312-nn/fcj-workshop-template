---
title: "5.8 Dọn dẹp tài nguyên"
date: 2026-11-24
weight: 8
chapter: false
pre: " <b> 5.8. </b> "
---

Xóa tài nguyên theo thứ tự sau để tránh lỗi phụ thuộc và chi phí phát sinh:

1. **S3 bucket** (xóa object trước, sau đó xóa bucket).

*[Hình: Xóa S3 bucket]*

2. **API trong API Gateway** (LegalChatAPI).

*[Hình: Xóa API LegalChatAPI]*

3. **Hàm Lambda** legal-ai-chat-lambda và **log group CloudWatch** của hàm.

*[Hình: Xóa hàm Lambda]*
*[Hình: Xóa log group CloudWatch]*

4. **Bảng DynamoDB** LegalArticles.

*[Hình: Xóa bảng DynamoDB LegalArticles]*

5. **IAM role** legal-ai-chat-role đã tạo cho Lambda.

*[Hình: Xóa IAM role legal-ai-chat-role (che thông tin nhạy cảm trước khi chèn ảnh)]*

6. **Thu hồi Groq API key** trong Groq Console. Vô hiệu hóa hoặc xóa key đã tạo ở mục 5.2.

*[Hình: Thu hồi Groq API key (che thông tin nhạy cảm trước khi chèn ảnh)]*
