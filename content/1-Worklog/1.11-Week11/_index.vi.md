---
title: "Worklog Tuần 11"
date: 2026-11-24
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu Tuần 11:

- Hoàn thiện Proposal và Workshop với bảng ước tính AWS Pricing Calculator, cơ sở lý luận kiến trúc và mục định hướng phát triển.
- Nghiên cứu các hướng cải tiến tiếp theo về bảo mật, truy xuất dữ liệu (retrieval) và giám sát (monitoring).
- Viết và xuất bản các bài blog kỹ thuật dựa trên dự án.
- Chuẩn bị bản demo cuối kỳ, hoàn thành Self-Assessment và nộp toàn bộ sản phẩm thực tập.

### Các công việc cần triển khai trong tuần:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Cập nhật Proposal: <br>&emsp; + Bổ sung sơ đồ kiến trúc, bảng dịch vụ kèm lý do lựa chọn và bảng rủi ro mở rộng <br>&emsp; + Bổ sung bảng ước tính AWS Pricing Calculator (Sydney, 10.000 requests/tháng) kèm đường dẫn và bảng tổng hợp <br> - Chỉnh sửa cách diễn đạt về chi phí trong phần Executive Summary, ROI và Expected Outcomes | 23/11/2026 | 23/11/2026 | AWS Pricing Calculator |
| 3 | - Cập nhật Workshop: <br>&emsp; + Bổ sung phần đối chiếu Well-Architected, mục tối ưu hóa chi phí và bảng dự toán chi phí <br>&emsp; + Bổ sung minh chứng CloudWatch (logs, metrics, alarm) và kiểm tra khả năng tái lập của từng bước <br>&emsp; + Khắc phục các điểm chưa nhất quán về Region, tên tài nguyên và ảnh chụp màn hình <br> - Nghiên cứu hướng cải tiến và viết mục định hướng phát triển (future work) cho Workshop: <br>&emsp; + AWS Systems Manager Parameter Store (`SecureString`), API keys & usage plans, giới hạn CORS và Amazon Cognito <br>&emsp; + Amazon Bedrock & Knowledge Bases so với keyword retrieval, cảnh báo email SNS và DynamoDB TTL | 24/11/2026 | 24/11/2026 | AWS Docs: Well-Architected Framework, Parameter Store, Amazon Bedrock |
| 4 | - Viết Blog 1: Xây dựng trợ lý RAG serverless với Lambda, API Gateway và DynamoDB (kiến trúc, luồng dữ liệu và các quyết định thiết kế chính) <br> - Viết Blog 2: Ước tính chi phí AWS bằng Pricing Calculator (bài học kinh nghiệm: nhầm lẫn đơn vị API Gateway và chọn nhầm reserved capacity trong DynamoDB) | 25/11/2026 | 25/11/2026 | AWS Pricing Calculator, <https://hcm-rules.awsfcaj.com/> |
| 5 | - Viết Blog 3: Bài học về bảo mật và chi phí từ dự án: <br>&emsp; + Nguyên tắc đặc quyền tối thiểu, throttling, phòng chống prompt injection và quản lý API key <br> - Rà soát, biên tập và xuất bản cả 3 bài blog lên AWS Study Group <br> - Thu thập phản hồi từ mentor và các thành viên cùng nhóm để ghi nhận các điểm cần cải thiện | 26/11/2026 | 26/11/2026 | <https://hcm-rules.awsfcaj.com/> |
| 6 | - Quay video demo cuối kỳ, chuẩn bị bài thuyết trình và phần hỏi đáp (Q&A) <br> - Hoàn thành bài Tự đánh giá (Self-Assessment) <br> - Nhờ mentor rà soát lại Proposal và Workshop | 27/11/2026 | 27/11/2026 | <https://hcm-rules.awsfcaj.com/> |
| 7 | - Rà soát danh mục kiểm tra thực tập (checklist): chuyên cần, các sự kiện kèm ảnh check-in, blogs và Worklog <br> - Kiểm tra lần cuối toàn bộ sản phẩm bàn giao: Worklog (Tuần 1–11), Proposal, Workshop, đường dẫn Blog và Self-Assessment <br> - Kiểm tra Billing và Free Tier để xác nhận không còn tài nguyên nào đang chạy và hoàn tất nộp bài | 28/11/2026 | 29/11/2026 | AWS Docs: Cost Explorer and Billing |

### Kết quả đạt được Tuần 11:

- Hoàn thiện Proposal với đầy đủ sơ đồ kiến trúc, lý do chọn dịch vụ, bảng rủi ro và dự toán từ AWS Pricing Calculator.
- Hoàn thiện Workshop với phần đối chiếu Well-Architected, tối ưu hóa chi phí, minh chứng CloudWatch và mục định hướng phát triển về bảo mật (Parameter Store, Cognito, CORS, usage plans), truy xuất (Amazon Bedrock) và giám sát/lưu trữ (SNS, DynamoDB TTL).
- Nắm vững cách tránh các lỗi nhập liệu phổ biến trên AWS Pricing Calculator.
- Viết, biên tập và xuất bản thành công 3 bài blog kỹ thuật lên AWS Study Group.
- Hoàn thiện video demo cuối kỳ, bài thuyết trình, Self-Assessment và nhận đánh giá từ mentor.
- Xác nhận không còn tài nguyên phát sinh chi phí trên Billing/Free Tier và hoàn tất nộp toàn bộ sản phẩm thực tập.