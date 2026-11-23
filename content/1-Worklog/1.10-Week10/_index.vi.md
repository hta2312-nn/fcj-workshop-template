---
title: "Worklog Tuần 10"
date: 2026-11-22
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Mục tiêu Tuần 10:

- Xây dựng giao diện người dùng (frontend) và chạy kiểm thử toàn trình (end-to-end).
- Hoàn thiện các tài liệu Proposal, Workshop và Worklog.
- Dọn dẹp toàn bộ tài nguyên đã triển khai.

### Các công việc cần triển khai trong tuần:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - **Thực hành:** <br>&emsp; + Xây dựng `index.html`: bố cục chat, tuyên bố miễn trừ trách nhiệm (disclaimer), status badge và thông báo lỗi <br>&emsp; + Gọi API bằng `fetch` | 16/11/2026 | 16/11/2026 | AWS Docs: API Gateway |
| 3 | - **Thực hành:** <br>&emsp; + Tạo S3 bucket và bật tính năng static website hosting kèm public read-only bucket policy <br>&emsp; + Tải `index.html` lên, cấu hình API URL và kiểm thử end-to-end <br>&emsp; + Chụp ảnh màn hình và quay video demo | 17/11/2026 | 17/11/2026 | AWS Docs: S3 |
| 4 | - Viết tài liệu Workshop: <br>&emsp; + Các bước hướng dẫn có thể tái lập (reproducible steps) <br>&emsp; + Lý do lựa chọn từng dịch vụ <br>&emsp; + Đối chiếu với Well-Architected Framework <br> - Che mờ account ID, keys và các URL nhạy cảm trong ảnh chụp màn hình | 18/11/2026 | 18/11/2026 | AWS Docs: Well-Architected Framework |
| 5 | - Hoàn thiện Proposal và Workshop, đồng thời khắc phục các điểm chưa nhất quán như Region và tên tài nguyên <br> - Hoàn tất Worklog và rà soát các yêu cầu cho Self-Assessment và Blog | 19/11/2026 | 19/11/2026 | <https://hcm-rules.awsfcaj.com/> |
| 6 | - **Thực hành:** <br>&emsp; + Dọn dẹp tài nguyên theo thứ tự: S3 bucket, API Gateway, Lambda cùng log group, bảng DynamoDB, IAM role và policy, Groq API key <br>&emsp; + Kiểm tra Cost Explorer và Billing để xác nhận không phát sinh chi phí | 20/11/2026 | 20/11/2026 | AWS Docs: Cost Explorer and Billing |

### Kết quả đạt được Tuần 10:

- Xây dựng và triển khai thành công giao diện chat frontend (`index.html`) trên Amazon S3.
- Hoàn tất kiểm thử end-to-end kèm bộ ảnh chụp màn hình và video demo.
- Hoàn thiện và đồng bộ đầy đủ các tài liệu Proposal, Workshop và Worklog.
- Dọn dẹp sạch sẽ toàn bộ tài nguyên theo đúng trình tự và xác nhận không phát sinh chi phí trên Cost Explorer và Billing.