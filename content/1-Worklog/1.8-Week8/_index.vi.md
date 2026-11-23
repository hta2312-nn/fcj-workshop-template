---
title: "Worklog Tuần 8"
date: 2026-11-08
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu Tuần 8:

- Xây dựng và kiểm thử phần backend: Lambda, Groq API, API Gateway.
- Chuẩn hóa cơ chế xử lý lỗi (error handling).

### Các công việc cần triển khai trong tuần:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - **Thực hành:** <br>&emsp; + Tạo Lambda function `legal-ai-chat-lambda` (Python 3.12) gắn với execution role đã tạo <br>&emsp; + Thiết lập timeout 30 giây và cấu hình biến môi trường `GROQ_API_KEY` <br>&emsp; + Viết hàm `retrieve_legal_context` | 02/11/2026 | 02/11/2026 | AWS Docs: Lambda |
| 3 | - **Thực hành:** <br>&emsp; + Triển khai phần ghép prompt (prompt assembly) và gọi Groq API <br>&emsp; + Tạo HTTP API `LegalChatAPI` với route `POST /chat`, cấu hình CORS và triển khai stage `v1` | 03/11/2026 | 03/11/2026 | AWS Docs: API Gateway |
| 4 | - **Thực hành:** <br>&emsp; + Kiểm thử bằng `curl`: câu hỏi mẫu, câu hỏi rỗng (`400`) và câu hỏi ngoài phạm vi <br>&emsp; + Kiểm tra CloudWatch logs cho từng request | 04/11/2026 | 04/11/2026 | AWS Docs: CloudWatch |
| 5 | - Bổ sung kiểm tra dữ liệu đầu vào (input validation) và chuẩn hóa các mã lỗi: <br>&emsp; + `400`, `429`, `502`, `504` và `500` <br> - Sửa các lỗi phát sinh trong quá trình kiểm thử | 05/11/2026 | 05/11/2026 | AWS Docs: Lambda |
| 6 | - Rà soát bảo mật: <br>&emsp; + Không ghi log câu hỏi của người dùng <br>&emsp; + Bảo vệ API key <br>&emsp; + Duy trì nguyên tắc đặc quyền tối thiểu (least privilege) <br> - Ghi chú các điểm cần cải thiện cho các bước tiếp theo | 06/11/2026 | 06/11/2026 | AWS Docs: Well-Architected Framework |

### Kết quả đạt được Tuần 8:

- Hoàn thiện logic RAG truy xuất ngữ cảnh và ghép prompt trên AWS Lambda (`legal-ai-chat-lambda`).
- Tích hợp và gọi thành công Groq API từ Lambda.
- Công khai (expose) backend thông qua Amazon API Gateway (`LegalChatAPI`, `POST /chat`, stage `v1`) có cấu hình CORS.
- Chuẩn hóa kiểm tra đầu vào cùng các mã lỗi (`400`, `429`, `502`, `504`, `500`) và kiểm thử thành công cả trường hợp hợp lệ lẫn ngoại lệ bằng `curl` kết hợp theo dõi CloudWatch logs.