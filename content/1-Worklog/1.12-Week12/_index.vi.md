---
title: "Worklog Tuần 12"
date: 2026-12-06
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Mục tiêu Tuần 12:

- Nghiên cứu các hướng cải tiến tiếp theo về bảo mật, truy xuất dữ liệu (retrieval) và giám sát (monitoring).
- Chuẩn bị bản demo cuối cùng và hoàn thiện toàn bộ sản phẩm bàn giao của kỳ thực tập.

### Các công việc cần triển khai trong tuần:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu AWS Systems Manager Parameter Store (`SecureString`) để lưu trữ Groq API key <br> - Tìm hiểu về API keys, usage plans và giới hạn CORS theo đúng origin của website <br> - Tìm hiểu Amazon Cognito để bổ sung tính năng xác thực (authentication) | 30/11/2026 | 30/11/2026 | AWS Docs: Systems Manager Parameter Store |
| 3 | - Tìm hiểu Amazon Bedrock và Bedrock Knowledge Bases, so sánh với phương pháp tìm kiếm theo từ khóa (keyword retrieval) <br> - Tìm hiểu cảnh báo qua email với SNS và DynamoDB TTL để quản lý lịch sử hội thoại <br> - Viết mục định hướng phát triển (future work) cho tài liệu Workshop | 01/12/2026 | 01/12/2026 | AWS Docs: Amazon Bedrock |
| 4 | - Viết Blog 3: Bài học về bảo mật và chi phí từ dự án: <br>&emsp; + Nguyên tắc đặc quyền tối thiểu (least privilege) <br>&emsp; + Giới hạn lưu lượng (throttling) <br>&emsp; + Phòng chống prompt injection <br>&emsp; + Quản lý API key <br> - Quay video demo cuối cùng, chuẩn bị bài thuyết trình và phần hỏi đáp (Q&A) | 02/12/2026 | 02/12/2026 | <https://hcm-rules.awsfcaj.com/> |
| 5 | - Hoàn thành bài Tự đánh giá (Self-Assessment) <br> - Rà soát danh mục kiểm tra thực tập (checklist): <br>&emsp; + Điểm danh chuyên cần <br>&emsp; + Các sự kiện kèm ảnh check-in <br>&emsp; + Các bài blog và Worklog <br> - Nhờ mentor rà soát lại Proposal và Workshop | 03/12/2026 | 03/12/2026 | <https://hcm-rules.awsfcaj.com/> |
| 6 | - Kiểm tra lần cuối toàn bộ sản phẩm bàn giao: <br>&emsp; + Worklog (Tuần 1–12) <br>&emsp; + Proposal & Workshop <br>&emsp; + Đường dẫn các bài blog & Self-Assessment <br> - Kiểm tra mục Billing và Free Tier để xác nhận không còn tài nguyên nào đang chạy | 04/12/2026 | 04/12/2026 | AWS Docs: Cost Explorer and Billing |

### Kết quả đạt được Tuần 12:

- Hiểu rõ cách bảo vệ thông tin nhạy cảm (Parameter Store `SecureString`) và kiểm soát truy cập API (API keys, usage plans, CORS, Amazon Cognito).
- Nắm được các phương án nâng cấp khả năng truy xuất (Amazon Bedrock & Knowledge Bases) và giám sát/lưu trữ (SNS, DynamoDB TTL), đồng thời cập nhật vào mục định hướng phát triển của Workshop.
- Hoàn thành và xuất bản bài blog kỹ thuật thứ 3 về các bài học bảo mật và tối ưu chi phí.
- Hoàn thiện video demo cuối kỳ, bài thuyết trình, Self-Assessment và nhận đánh giá từ mentor.
- Xác nhận không còn tài nguyên phát sinh chi phí trên Billing/Free Tier và hoàn tất nộp toàn bộ sản phẩm thực tập.