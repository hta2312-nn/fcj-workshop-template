---
title: "Worklog Tuần 7"
date: 2026-11-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu Tuần 7:

- Xây dựng cơ sở tri thức (knowledge base) trên DynamoDB.
- Cấu hình IAM theo nguyên tắc đặc quyền tối thiểu (least privilege) cho Lambda.

### Các công việc cần triển khai trong tuần:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Kiểm tra cảnh báo AWS Budget và mức sử dụng Free Tier hiện tại <br> - Xác nhận Region thống nhất cho toàn bộ tài nguyên dự án <br> - **Thực hành:** <br>&emsp; + Tạo bảng DynamoDB `LegalArticles` | 26/10/2026 | 26/10/2026 | AWS Docs: DynamoDB |
| 3 | - Tóm tắt các điều khoản pháp lý đã chọn và bổ sung từ khóa (keywords) <br> - Đối chiếu lại nội dung với văn bản pháp luật chính thức | 27/10/2026 | 27/10/2026 | <https://hcm-rules.awsfcaj.com/> |
| 4 | - **Thực hành:** <br>&emsp; + Viết seed script bằng `boto3` `batch_writer` và nạp dữ liệu vào bảng <br>&emsp; + Kiểm tra lại các bản ghi bằng tính năng Explore table items | 28/10/2026 | 28/10/2026 | AWS Docs: DynamoDB |
| 5 | - **Thực hành:** <br>&emsp; + Tạo IAM policy: cấp quyền chỉ đọc (read-only) tới bảng `LegalArticles` kèm quyền ghi log lên CloudWatch <br>&emsp; + Tạo Lambda execution role `legal-ai-chat-role` và gán policy vừa tạo | 29/10/2026 | 29/10/2026 | AWS Docs: IAM |
| 6 | - **Thực hành:** <br>&emsp; + Kiểm thử đọc dữ liệu từ bảng bằng AWS CLI hoặc `boto3` <br> - Rà soát lại các quyền đã cấp và loại bỏ những quyền không cần thiết | 30/10/2026 | 30/10/2026 | AWS Docs: IAM |

### Kết quả đạt được Tuần 7:

- Tạo thành công bảng `LegalArticles` trên Amazon DynamoDB.
- Nạp và xác minh thành công dữ liệu các điều khoản pháp lý bằng seed script viết với `boto3`.
- Tạo được IAM policy và execution role `legal-ai-chat-role` tuân thủ nguyên tắc đặc quyền tối thiểu.