---
title: "Workshop"
date: 2026-11-24
weight: 5
chapter: true
pre: " <b> 5. </b> "
---

# AI Legal & Security Assistant
## RAG Serverless tra cứu pháp lý và bảo vệ dữ liệu trên AWS

Ngày: 2026-11-24

### Tổng quan
AI Legal & Security Assistant là trợ lý tư vấn pháp lý sơ bộ cho doanh nghiệp, tập trung vào Nghị định 13/2023/NĐ-CP (bảo vệ dữ liệu cá nhân). Người dùng nhập câu hỏi hoặc một tình huống thực tế. Hệ thống tra cứu các điều luật liên quan trong cơ sở dữ liệu, sau đó mô hình ngôn ngữ lớn chỉ phân tích câu hỏi dựa trên các điều luật đó.

Hệ thống không phải luật sư và không đưa ra kết luận pháp lý chính thức. Nếu cơ sở dữ liệu thiếu căn cứ, hệ thống phải nói rõ điều này.

Hệ thống được xây dựng trên kiến trúc serverless với các thành phần:
- **Giao diện:** trang web tĩnh (index.html) host trên Amazon S3 (static website hosting).
- **Cổng API:** Amazon API Gateway (CORS và chuẩn hóa lỗi).
- **Backend:** AWS Lambda (Python), truy xuất điều luật và gọi LLM.
- **Cơ sở tri thức:** Amazon DynamoDB (bảng LegalArticles).
- **LLM:** Groq API (qwen/qwen3.8-27b), dịch vụ bên ngoài AWS.
- **Giám sát:** Amazon CloudWatch.

![Sơ đồ kiến trúc và luồng dữ liệu](../images/5-Workshop/_index/_index-01.png)

### Nội dung
- 5.1 Giới thiệu
- 5.2 Chuẩn bị
- 5.3 Giai đoạn 1: Thiết lập Prompt và cơ chế RAG
- 5.4 Giai đoạn 2: Backend, từ Database đến Lambda và API
- 5.5 Frontend: S3 static website
- 5.6 Bảo mật và vận hành
- 5.7 Thành quả cuối cùng và hướng phát triển
- 5.8 Dọn dẹp tài nguyên
