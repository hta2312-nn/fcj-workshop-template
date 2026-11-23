---
title: "Worklog Tuần 11"
date: 2026-11-29
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu Tuần 11:

- Hoàn thiện Proposal và Workshop với bảng ước tính từ AWS Pricing Calculator và cơ sở lý luận kiến trúc.
- Viết và xuất bản các bài blog kỹ thuật dựa trên dự án.

### Các công việc cần triển khai trong tuần:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Cập nhật Proposal: <br>&emsp; + Bổ sung sơ đồ kiến trúc, bảng dịch vụ kèm lý do lựa chọn và bảng rủi ro mở rộng <br>&emsp; + Bổ sung bảng ước tính AWS Pricing Calculator (Sydney, 10.000 requests/tháng) kèm đường dẫn và bảng tổng hợp <br> - Chỉnh sửa cách diễn đạt về chi phí trong phần Executive Summary, ROI và Expected Outcomes | 23/11/2026 | 23/11/2026 | AWS Pricing Calculator |
| 3 | - Cập nhật Workshop: <br>&emsp; + Bổ sung phần đối chiếu Well-Architected, mục tối ưu hóa chi phí và bảng dự toán chi phí <br>&emsp; + Bổ sung minh chứng CloudWatch (logs, metrics, alarm) và kiểm tra khả năng tái lập của từng bước <br> - Khắc phục các điểm chưa nhất quán về Region, tên tài nguyên và ảnh chụp màn hình | 24/11/2026 | 24/11/2026 | AWS Docs: Well-Architected Framework |
| 4 | - Viết Blog 1: Xây dựng trợ lý RAG serverless với Lambda, API Gateway và DynamoDB <br> - Trình bày kiến trúc, luồng dữ liệu và các quyết định thiết kế chính | 25/11/2026 | 25/11/2026 | <https://hcm-rules.awsfcaj.com/> |
| 5 | - Viết Blog 2: Ước tính chi phí AWS bằng Pricing Calculator <br> - Chia sẻ các bài học kinh nghiệm: <br>&emsp; + Nhầm lẫn đơn vị tính trong API Gateway <br>&emsp; + Chọn nhầm reserved capacity trong DynamoDB | 26/11/2026 | 26/11/2026 | AWS Pricing Calculator |
| 6 | - Rà soát, biên tập cả hai bài blog và xuất bản lên AWS Study Group <br> - Thu thập phản hồi từ mentor và các thành viên cùng nhóm để ghi nhận các điểm cần cải thiện | 27/11/2026 | 27/11/2026 | <https://hcm-rules.awsfcaj.com/> |

### Kết quả đạt được Tuần 11:

- Hoàn thiện Proposal với đầy đủ sơ đồ kiến trúc, lý do chọn dịch vụ, bảng rủi ro và dự toán từ AWS Pricing Calculator.
- Hoàn thiện Workshop với phần đối chiếu Well-Architected, tối ưu hóa chi phí và minh chứng giám sát CloudWatch.
- Nắm vững cách tránh các lỗi nhập liệu phổ biến trên AWS Pricing Calculator (đơn vị API Gateway và reserved capacity của DynamoDB).
- Viết, biên tập và xuất bản thành công hai bài blog kỹ thuật lên AWS Study Group cùng việc tiếp thu góp ý từ mentor và đồng đội.