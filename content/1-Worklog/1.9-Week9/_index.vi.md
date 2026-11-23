---
title: "Worklog Tuần 9"
date: 2026-11-15
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu Tuần 9:

- Gia cố hệ thống (hardening) và thiết lập cơ chế giám sát (monitoring).
- Kiểm tra chất lượng câu trả lời và độ chính xác của nội dung pháp lý.

### Các công việc cần triển khai trong tuần:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - **Thực hành:** <br>&emsp; + Cấu hình giới hạn lưu lượng (throttling) trên stage `v1` <br>&emsp; + Gửi request với tần suất cao để xác nhận mã lỗi HTTP `429` | 09/11/2026 | 09/11/2026 | AWS Docs: API Gateway |
| 3 | - **Thực hành:** <br>&emsp; + Thiết lập thời gian lưu giữ log (log retention) trên CloudWatch là 7 ngày <br>&emsp; + Kiểm tra các chỉ số (metrics) của Lambda và tạo cảnh báo (alarm) cho lỗi Lambda | 10/11/2026 | 10/11/2026 | AWS Docs: CloudWatch |
| 4 | - **Thực hành:** <br>&emsp; + Kiểm thử các tình huống prompt injection và câu hỏi ngoài phạm vi <br> - Tinh chỉnh lại system prompt và danh sách từ khóa (keywords) | 11/11/2026 | 11/11/2026 | Groq Docs |
| 5 | - Đối chiếu các điều khoản pháp lý với văn bản gốc chính thức <br> - Kiểm tra các văn bản luật mới hơn, chẳng hạn như Luật Bảo vệ Dữ liệu Cá nhân 2025, và ghi nhận các tác động | 12/11/2026 | 12/11/2026 | <https://hcm-rules.awsfcaj.com/> |
| 6 | - Lập bảng ước tính chi phí bằng AWS Pricing Calculator <br> - Liệt kê các biện pháp tối ưu hóa chi phí | 13/11/2026 | 13/11/2026 | AWS Pricing Calculator |

### Kết quả đạt được Tuần 9:

- Cấu hình thành công API throttling trên stage `v1` và kiểm chứng cơ chế giới hạn tốc độ trả về mã `429`.
- Thiết lập thời gian lưu giữ log CloudWatch (7 ngày), theo dõi metrics và tạo cảnh báo cho các lỗi của Lambda.
- Kiểm thử an toàn các kịch bản prompt injection, câu hỏi ngoài phạm vi, đồng thời tối ưu lại system prompt và từ khóa.
- Xác minh độ chính xác của nội dung pháp lý và ghi nhận tác động từ các quy định mới như Luật Bảo vệ Dữ liệu Cá nhân 2025.
- Hoàn thành bảng dự toán chi phí trên AWS Pricing Calculator kèm danh sách các phương án tối ưu chi phí.