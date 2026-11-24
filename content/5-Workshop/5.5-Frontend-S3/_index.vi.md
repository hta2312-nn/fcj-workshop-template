---
title: "5.5 Frontend: S3 static website"
date: 2026-11-24
weight: 5
chapter: false
pre: " <b> 5.5. </b> "
---

### Tổng quan
| Mục | Nội dung |
|---|---|
| Mục đích | Trang chat để người dùng đặt câu hỏi và đọc câu trả lời. |
| Dịch vụ AWS | Amazon S3 (static website hosting) |
| Đầu vào | Câu hỏi của người dùng |
| Đầu ra | Câu trả lời hiển thị trong khung chat |
| Phụ thuộc | URL của Backend API |

### 5.5.1 Dựng giao diện chat (index.html)
**Mục tiêu:** Một trang tĩnh duy nhất gọi backend bằng fetch.

**Các bước**
1. Dựng bố cục chat: tiêu đề, badge trạng thái, lời chào, danh sách tin nhắn, ô nhập và nút gửi.
2. Khi gửi, gọi fetch bằng HTTP POST tới URL API và hiển thị trạng thái đang xử lý.
3. Hiển thị thông báo rõ ràng cho các lỗi 400, 429 và 502/504.
4. Khuyến nghị: thêm disclaimer cho biết câu trả lời chỉ mang tính sơ bộ, không phải tư vấn pháp lý.

*[Hình: Giao diện khung chat index.html]*

**Kiểm tra:** mở index.html trên máy, thấy trang chat và lời chào.

### 5.5.2 Host trang trên S3
**Mục tiêu:** Công khai index.html dưới dạng static website.

**Các bước**
1. Tạo bucket **ai-legal-assistant-frontend-hau** ở region ap-southeast-2.
2. Tải index.html lên bucket.
3. Bật **Static website hosting**, với index.html làm index document.
4. Cho phép đọc công khai riêng cho bucket này: tắt Block Public Access của bucket và thêm bucket policy chỉ cho phép đọc.
5. Mở website endpoint.

**Tạo bucket**
1. Tạo bucket ở region ap-southeast-2, loại General purpose, đặt tên ai-legal-assistant-frontend-hau.

*[Hình: Tạo bucket S3 ở region ap-southeast-2]*

2. Bỏ chọn **Block all public access** cho riêng bucket này và xác nhận cảnh báo.

*[Hình: Bỏ chọn Block all public access]*

3. Giữ mã hóa mặc định SSE-S3 và chọn **Create bucket**.

*[Hình: Mã hóa mặc định SSE-S3]*

4. Bucket đã được tạo, danh sách Objects đang trống.

*[Hình: Bucket mới tạo với danh sách Objects trống]*

5. Vào trang Upload để tải file index.html lên bucket.

*[Hình: Trang Upload file index.html]*

**Bật static website hosting**
1. Tab Properties của bucket hiển thị Region, ARN và ngày tạo.

*[Hình: Tab Properties của bucket]*

2. Mục **Static website hosting** đang ở trạng thái Disabled. Chọn **Edit**.

*[Hình: Mục Static website hosting đang Disabled]*

3. Bật Static website hosting, chọn **Host a static website** và đặt **Index document** là index.html.

*[Hình: Bật Static website hosting, Index document là index.html]*

**Kiểm tra:** endpoint `http://ai-legal-assistant-frontend-hau.s3-website-ap-southeast-2.amazonaws.com/` mở được trang.

### 5.5.3 Nối API và kiểm thử end-to-end
**Mục tiêu:** Cho trang đã deploy gọi backend thật.

**Các bước**
1. Đặt URL gọi API trong index.html, rồi tải lại file lên S3.
2. Mở website và hỏi một câu hỏi mẫu.
3. Mở console của trình duyệt và kiểm tra không có lỗi CORS.
4. Kiểm tra request trong CloudWatch Logs.

*[Hình: Kết quả câu hỏi mẫu trên website]*

**Kiểm tra:** câu hỏi nhận được câu trả lời có căn cứ trên trang, kèm một dòng log tương ứng.
