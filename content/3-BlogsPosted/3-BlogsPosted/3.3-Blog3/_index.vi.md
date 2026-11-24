---
title: "Blog 3"
date: 2026-11-24
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# AWS LEARNING CORNER: XÂY DỰNG WEBSITE TĨNH ĐƠN GIẢN VÀ AN TOÀN VỚI S3 + CLOUDFRONT + ROUTE 53

Sau khi hoàn thành một website tĩnh (HTML/CSS/JS thuần, hoặc bản build từ React, Vue hay Next.js), câu hỏi tiếp theo là cách đưa website lên internet. Các mục tiêu thường gặp là chi phí thấp, truy cập nhanh, HTTPS an toàn và không phải quản lý máy chủ.

Bộ ba Amazon S3, Amazon CloudFront và Amazon Route 53 là một kiến trúc tiêu chuẩn, đáp ứng tốt các mục tiêu này.

### Bước 1: Lưu trữ file với Amazon S3
* Tạo một S3 bucket để chứa toàn bộ file của website đã build.
* Cấu hình S3 bucket policy và cấp quyền truy cập phù hợp.
* Bật Static website hosting và đặt file mặc định, ví dụ index.html và 404.html.

### Bước 2: Tăng tốc và bảo mật phân phối với Amazon CloudFront (CDN)
* Tạo một CloudFront distribution và đặt S3 bucket làm origin.
* **Phân phối nhanh hơn:** Nội dung website được lưu đệm (cache) tại các edge location trên toàn cầu, giúp giảm độ trễ cho người dùng.
* **Bảo mật:** Sử dụng chứng chỉ SSL/TLS miễn phí từ AWS Certificate Manager (ACM) để bật HTTPS. Đồng thời cấu hình Origin Access Control (OAC) để chặn truy cập trực tiếp vào S3 bucket, chỉ cho phép lưu lượng đi qua CloudFront.

### Bước 3: Trỏ tên miền với Amazon Route 53
* Tạo hosted zone cho tên miền của bạn trong Route 53.
* Tạo bản ghi A (loại alias) trỏ tên miền gốc hoặc subdomain tới CloudFront distribution.

### Giá trị kỹ thuật và bài học rút ra
* **Tối ưu chi phí:** Kiến trúc serverless không có chi phí bảo trì máy chủ (Nginx hoặc Apache). Với lưu lượng thấp hoặc dự án cá nhân, chi phí hàng tháng gần như bằng 0.
* **Khả năng mở rộng:** Mạng CDN của CloudFront tự xử lý các đợt tăng lưu lượng đột biến mà không cần nâng cấp hạ tầng.
* **Vận hành đơn giản hơn:** Không cần tự vá lỗi hệ điều hành hay gia hạn chứng chỉ SSL thủ công.

### Kết luận
Bài thực hành kinh điển này quan trọng vì nó dạy bạn cách kết hợp các dịch vụ AWS cơ bản thành một hệ thống hoàn chỉnh, an toàn và đạt chuẩn công nghiệp.

![Sơ đồ kiến trúc website tĩnh trên AWS](../../images/3-BlogsPosted/3.3-Blog3/blog3-01.jpeg)

[Liên kết bài đăng trên AWS Study Group](https://www.facebook.com/groups/awsstudygroupfcj/?multi_permalinks=2317669882331304)
