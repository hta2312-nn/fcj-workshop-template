---
title: "Worklog Tuần 4"
date: 2026-10-11
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu Tuần 4:

- Rèn luyện kỹ năng thực hành với Lambda, API Gateway, CloudWatch và DynamoDB.
- Xây dựng hoàn chỉnh một serverless API nhỏ từ đầu đến cuối.

### Các công việc cần triển khai trong tuần:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu sâu về Lambda: <br>&emsp; + Python runtime, handler, biến môi trường (environment variables), bộ nhớ (memory) và timeout <br> - **Thực hành:** <br>&emsp; + Đọc log của Lambda | 05/10/2026 | 05/10/2026 | AWS Docs: Lambda |
| 3 | - So sánh REST API và HTTP API trong API Gateway <br> - Tìm hiểu về routes, stages và CORS <br> - **Thực hành:** <br>&emsp; + Tạo một HTTP API tích hợp với Lambda | 06/10/2026 | 06/10/2026 | AWS Docs: API Gateway |
| 4 | - Tìm hiểu các khái niệm cơ bản của CloudWatch: <br>&emsp; + Log groups, log retention, metrics và alarms <br> - Kiểm tra các chỉ số (metrics) của Lambda như Invocations, Errors và Duration | 07/10/2026 | 07/10/2026 | AWS Docs: CloudWatch |
| 5 | - Áp dụng nguyên tắc đặc quyền tối thiểu (least-privilege) khi cấp quyền truy cập DynamoDB <br> - **Thực hành:** <br>&emsp; + Tạo bảng DynamoDB <br>&emsp; + Thực hành các thao tác put, get, scan và query trên console và với `boto3` | 08/10/2026 | 08/10/2026 | AWS Docs: DynamoDB |
| 6 | - **Thực hành:** <br>&emsp; + Xây dựng mini lab: Lambda + API Gateway + DynamoDB <br>&emsp; + Kiểm thử API bằng `curl`, sau đó dọn dẹp tài nguyên | 09/10/2026 | 09/10/2026 | AWS Docs: API Gateway |

### Kết quả đạt được Tuần 4:

- Cấu hình được các thiết lập và biến môi trường cho AWS Lambda.
- Tạo được HTTP API trên API Gateway kết nối với AWS Lambda.
- Đọc và theo dõi được logs cũng như metrics trong Amazon CloudWatch.
- Đọc và ghi thành công dữ liệu trên DynamoDB bằng `boto3`.
- Hoàn thành mini lab xây dựng serverless API end-to-end và dọn dẹp sạch tài nguyên sau khi thực hành.