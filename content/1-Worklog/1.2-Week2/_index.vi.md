---
title: "Worklog Tuần 2"
date: 2026-09-27
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu Tuần 2:

- Hiểu về AWS IAM và áp dụng nguyên tắc đặc quyền tối thiểu (least-privilege).
- Hiểu về Amazon S3 và cách lưu trữ website tĩnh (static website hosting).
- Hiểu các kiến thức cơ bản về Amazon EC2.
- Thực hành dọn dẹp tài nguyên lab và theo dõi mức sử dụng Free Tier.

### Các công việc cần triển khai trong tuần:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu kiến thức nền tảng về IAM: <br>&emsp; + Users, groups, roles và policies <br> - Hiểu nguyên tắc đặc quyền tối thiểu (least-privilege) và thiết lập MFA cho root user <br> - Xem lại các khuyến nghị bảo mật cho tài khoản root | 21/09/2026 | 21/09/2026 | AWS Docs: IAM |
| 3 | - Hiểu về roles và chứng thực tạm thời (temporary credentials) <br> - **Thực hành:** <br>&emsp; + Tạo IAM user, group và gán managed policy <br>&emsp; + Viết một custom JSON policy đơn giản và kiểm thử phân quyền | 22/09/2026 | 22/09/2026 | AWS Docs: IAM |
| 4 | - Tìm hiểu kiến thức nền tảng về S3: <br>&emsp; + Buckets, objects, storage classes, versioning và Block Public Access <br> - **Thực hành:** <br>&emsp; + Tạo bucket, tải tệp lên và xem lại bucket policies <br>&emsp; + Triển khai một website tĩnh đơn giản trên S3 | 23/09/2026 | 23/09/2026 | AWS Docs: S3 |
| 5 | - Tìm hiểu kiến thức cơ bản về EC2: <br>&emsp; + Instance types, AMI, key pairs, security groups và EBS <br> - **Thực hành:** <br>&emsp; + Khởi chạy và kết nối tới một EC2 instance thuộc gói Free Tier <br>&emsp; + Xóa (terminate) instance sau khi thực hành để tránh phát sinh chi phí | 24/09/2026 | 24/09/2026 | AWS Docs: EC2 |
| 6 | - Tổng hợp lại ghi chú của cả tuần <br> - Kiểm tra mức sử dụng Free Tier và cảnh báo AWS Budget <br> - Dọn dẹp toàn bộ tài nguyên lab đã tạo trong tuần | 25/09/2026 | 25/09/2026 | Youtube: AWS Study Group |
| 7 | - Tham dự talkshow "The Thinking Behind Building The Bot" (09:00, Tầng 26, Tòa nhà Bitexco, TP.HCM) <br> - Chủ đề: Tư duy và cách tiếp cận thiết kế đằng sau việc xây dựng bot <br> - Ghi chép các bài học chính có thể áp dụng cho dự án chatbot của nhóm | 26/09/2026 | 26/09/2026 | Event: Talkshow "The Thinking Behind Building The Bot" |

### Kết quả đạt được Tuần 2:

- Hiểu rõ về IAM users, groups, roles và policies.
- Áp dụng được nguyên tắc đặc quyền tối thiểu khi viết và kiểm thử custom JSON policy.
- Tạo được S3 bucket và triển khai thành công website tĩnh trên Amazon S3.
- Khởi chạy, kết nối và xóa EC2 instance an toàn, tránh phát sinh chi phí.
- Dọn dẹp sạch tài nguyên lab và theo dõi tốt mức sử dụng Free Tier cùng cảnh báo AWS Budget.
- Tham dự talkshow về tư duy xây dựng bot và đúc kết được các ý tưởng áp dụng cho dự án chatbot của nhóm.